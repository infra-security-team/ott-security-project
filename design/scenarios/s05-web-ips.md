# S05 · 허용된 OTT 웹 경로의 SQLi 패턴 요청 탐지·차단

**2026.10.20 사용자 승인 개정 · 구축 전 설계 · 담당 M5 / 구현 협업 M3 / 관제 검증 M2 / VPN M1**

기존 S05의 직원→DB 직접 접근 시험을 변경합니다. UTM(Sophos UTM 9)이 허용한 웹 경로에서 **M3 Suricata가 요청 내용을 검사해 직접 차단하는 것**을 입증합니다. S01~S04, 담당자와 WBS 일정은 유지합니다. 직원→DB 직접 접근은 전후 모두 차단하는 기본 정책·회귀 검사로 남깁니다.

## 경로와 검사 위치

1. M5 승인 운영 PC → UTM5 → T15 → UTM1 → R1 → 교실 연결망 → R3 → UTM3 → DMZ 검사 쌍 → NginxA HTTPS443.
2. **NginxA에서 TLS 종료**, 원래 경로·쿼리를 보존해 HTTP/1.1로 프록시합니다.
3. NginxA → UTM3 → **APP Suricata 검사 쌍** → 고정 Worker TCP30080 → Spring 시험 API.
4. 웹 응답은 역방향으로 돌아가며 M3→M5는 M1·T15를 경유합니다. 중앙 관제는 센서 관리 NIC→UTM3→R3→R2→UTM2→Wazuh로 별도 전송합니다.

HTTPS 외부 구간의 센서가 암호문에서 SQL 구문을 읽는다고 설명하지 않습니다. Nginx 뒤의 평문 HTTP 구간이 검사 대상입니다. 이 구간을 TLS/mTLS로 바꾸면 현재 URI 검사 방식도 다시 설계해야 합니다. 실습 내부 구간만 최소 허용합니다.

## 구현 계약과 먼저 통과할 조건

- 팀 내부 주소표로 T15 양쪽 보호 대상에 **NginxA와 정상 VIP**를 반영합니다. 이전 S05 전용 시험 DB 목적지는 제거하되 다른 승인 업무 대역은 유지합니다. 실제 주소는 공개 저장소에 쓰지 않습니다.
- UTM3는 승인 M5 출발지→NginxA TCP443, NginxA→지정 Worker TCP30080을 **전후 모두 허용**합니다. AS-IS도 Any→Any 허용으로 만들지 않습니다.
- 두 단계 모두 NginxA와 같은 Worker를 고정합니다. VIP 전환·다른 Pod/버전·WAF·앱 자체 거부가 결과를 바꾸지 않도록 시험 조건을 고정·기록합니다. 일반 VIP/HA 검증은 별도 수행합니다.
- 시험 DNS `api.otter.test`를 내부 NginxA로 해석하고 신뢰할 실습 CA 인증서를 구성합니다. `blocks-lab-ca.pem`은 공개 인증서 경로 예시이며 CA 개인키는 공유하지 않습니다.
- Spring의 **실습 전용** `GET /api/lab/search?q=...`를 준비합니다. 정상·패턴 입력 모두 더미 응답 HTTP200과 요청 ID를 반환하고, 실제 SQL을 구성·실행하지 않습니다. AS-IS의 의미는 **패턴 요청이 백엔드까지 도착함**이지 DB 침해 성공이 아닙니다.
- Nginx는 `/api` 경로와 쿼리를 그대로 보존합니다. `proxy_pass`에 경로를 붙여 `/api`를 잘라내지 않습니다. 시험 중 캐시·재시도·다른 Worker failover는 끕니다. 정상·패턴 요청 모두 실제 백엔드에 전달되는지 먼저 확인합니다.
- Nginx는 `X-Request-ID`를 전달하고 접근 로그에 요청 ID·시간·URI·upstream 주소/상태를 남깁니다. 백엔드도 동일 ID·URI·시간을 기록합니다. 실제 토큰/비밀값은 로그에 남기지 않습니다.
- **APP 센서의 패킷 출발지는 원래 M5 PC가 아니라 NginxA**입니다. 헤더·로그의 원래 클라이언트 주소는 프록시에서 신뢰 범위를 정하고 센서 출발 IP와 구분합니다. 임의 클라이언트 헤더만 믿지 않습니다.

## 고정 시험 입력과 규칙 예시

아래 명령은 팀이 소유한 격리 실습 API에만 사용합니다. 먼저 위 API·DNS·인증서·라우팅을 구현해야 하며 현재 실행 완료를 뜻하지 않습니다. 두 단계에서 요청 자체를 동일하게 반복하고 시험 단계·시각을 별도 기록합니다.

```bash
# 정상 대조 요청: AS-IS와 TO-BE 모두 HTTP200 + 백엔드 도착
curl --http1.1 --cacert blocks-lab-ca.pem --max-time 15 \
  -H 'X-Request-ID: s05-normal-001' \
  'https://api.otter.test/api/lab/search?q=blocks'

# SQLi 형태의 고정 문자열: 실제 SQL 실행 없는 더미 API
curl --http1.1 --cacert blocks-lab-ca.pem --max-time 15 \
  -H 'X-Request-ID: s05-pattern-001' \
  'https://api.otter.test/api/lab/search?q=%27%20OR%201%3D1--'
```

Suricata 7.0.15 문법을 참고한 **좁은 범위의 실습 규칙 예시**입니다. `S05_PROXY`는 NginxA 한 대, `S05_WORKERS`는 시험 중 고정 Worker 한 대로 `vars.address-groups`에 정의합니다. 기존 SID와 충돌하지 않는지 확인합니다. HTTP 분석기가 실제 TCP30080 요청을 HTTP로 인식하는지 먼저 확인합니다.

```text
alert http $S05_PROXY any -> $S05_WORKERS 30080 (msg:"BLOCKS S05 lab SQLi pattern"; flow:established,to_server; http.uri; content:"/api/lab/search?"; startswith; content:"OR 1=1"; nocase; sid:1000005; rev:1;)
```

AS-IS는 APP 쌍 `copy-mode: tap`과 위 `alert` 규칙으로 전달·탐지를 확인합니다. TO-BE는 APP 쌍 양방향 `copy-mode: ips`와 같은 SID·같은 매칭 조건의 **`drop` 규칙 하나**를 적용합니다. `alert`와 `drop` 두 개를 같은 SID로 동시에 적재하지 않습니다. 수정 후 `suricata -T -c <실제 설정 경로>`로 검증하고 실제 프로세스가 새 규칙을 읽었는지 확인합니다. 다른 검사 쌍의 정책·자산 배치는 유지합니다.

`http.uri`는 정규화된 URI를 검사합니다. 규칙은 위 고정 패턴을 검증하는 예시이므로 모든 SQLi 우회·변종을 막는 범용 규칙으로 발표하지 않습니다. 무해한 표식 규칙은 전달·차단 사전 점검용으로 사용할 수 있으며 실제 SQLi 패턴 시험과 증거를 구분합니다.

## 전후 합격 기준

| 확인 항목 | AS-IS | TO-BE |
|---|---|---|
| 정상 요청 | HTTP200, 백엔드 로그 존재 | HTTP200, 백엔드 로그 존재 |
| 고정 패턴 요청 | HTTP200, 백엔드 도착, 센서 SID 경보 | APP 센서의 해당 SID 차단 기록, 백엔드 미도착 |
| UTM 정책 | 지정 443·30080 allow | 같은 allow 유지 |
| 중앙 Wazuh | 센서 이벤트 수집·분석 경보 | 센서 차단 이벤트 수집·분석 경보 |
| 정상 업무·수집 | 포털·DNS·OTT·관제·백업 성공 | 같은 정상 기능 성공 |

M3 센서의 `eve.json`을 Agent가 JSON으로 수집하고 M2에서 SID·시간·출발/목적지·action을 대조합니다. 원문 수집만 되고 경보가 없으면 Wazuh decoder/rule을 확인합니다. 설치 버전의 `alert.action`·drop 이벤트·카운터와 APP 쌍 패킷 증거로 실제 차단 여부를 판단합니다.

Nginx가 upstream 응답을 못 받아 timeout·502·504를 낼 수 있습니다. HTTP 오류만으로 차단 성공이라 하지 않습니다. **UTM allow + 센서 차단 + 중앙 경보 + 프록시/백엔드 로그**를 함께 제출합니다. 백엔드 미도착 판정은 같은 구간의 정상 요청·로그 수집이 작동하고 관련 모든 Pod 로그를 조회한 상태여야 합니다.

시험 API는 실습 프로필·승인 출발지에 한정하고 종료 후 비활성화합니다. 운영 Primary DB·앱 통합 시험 DB·M1 포트폴리오 장비는 유지합니다. 단순 통신 단절·센서 장애는 IPS 성공으로 처리하지 않습니다.

## 담당과 근거

- **M5:** 더미 API 개발·고정 요청·전후 비교·정상 OTT 회귀 검사.
- **M3:** Nginx TLS/HTTP 전달, UTM3 허용, APP 센서·규칙·백엔드 로그·고정 배포.
- **M2:** eve.json 수집·Wazuh 분석/경보 및 차단 증거 교차 확인.
- **M1·M5:** T15 보호 대상·왕복 경로·NAT 예외 대조.

공식 참고: [Suricata HTTP URI 규칙](https://docs.suricata.io/en/suricata-7.0.15/rules/http-keywords.html), [AF_PACKET inline IPS](https://docs.suricata.io/en/suricata-7.0.15/setting-up-ipsinline-for-linux.html), [Wazuh Suricata 연동](https://documentation.wazuh.com/current/proof-of-concept-guide/integrate-network-ids-suricata.html).

[토폴로지 v1.2](../architecture.md) · [WBS](../../WBS.md) · [M3 API 개발 폴더](../../apps/m3-ott/backend/README.md)
