# OTTer Shield | WBS

**팀명 Team Blocks · 보안 컨설팅 회사 NetBlocks · 가상 OTT 고객사 OTTer**

**프로젝트명:** OTTer Shield — 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅

> **공개용:** 실제 IP와 세부 설정은 팀내 토폴로지·주소표·기술서에서 확인합니다.

**개정** v0.3 · 2026.10.20 표현·최신 계획서 링크 정리 (담당·일정 유지) · **설계 기준** 토폴로지 v1.2 (구축 검증 전)

**기간** 2026.10.19~11.16 · **기본 작업시간** 평일 09:00~18:00(점심 1시간 제외) · **발표** 11.16

[START HERE](README.md) · [계획서 v0.3](plans/project-plan-v0.3.pdf) · 토폴로지 v1.2(팀내 공유) · [Projects 업무 보드](https://github.com/orgs/team-blocks-lab/projects/4) · [망별 구축 가이드](design/network-guides/README.md)

> **읽는 순서:** 계획서 v0.3 → 이 WBS → 담당 Issue → 토폴로지·Notion 기술서. 기존 상세 가이드는 이전 배치가 남아 있을 수 있으므로 최신 계획서·토폴로지와 대조합니다.

## 1. 주요 일정 및 완료 기준

| 일정 | 작업 | 확인 기준 |
|---|---|---|
| **10/19 월** | 강사 피드백 반영·PC별 설계 개정 | M1 GNS3 라우터+UTM / M2·M3 VyOS+UTM, M1만 GNS3 VLAN, M2/M3/M5 네트워크 카드(NIC)별 망 분리. 완료가 아닌 설계 개정 |
| **10/20 화** | 교실망 실측·두 PC 브리지 시험·전체 도면 검토 | 교실 게이트웨이(주소는 팀 기술서 확인), 실제 마스크·고유 IP, 두 VM 왕복 통신. 장비별 교실망 IP는 확인 후 배정 |
| **10/21 수 오전** | IP/NIC/VMnet·시나리오 설계 기준 검토 | 32GB 자원표, 전용망·trunk, 정상/시험 경로, 미확정 담당·기한 확정 |
| **10/21 수 오후~23 금** | 승인된 망 AS-IS 구축·설치용 인터넷·AWS 사전 조건 확인 | VM→UTM→출구→교실 GW, DNS·저장소 HTTPS·다운로드. API 외부 공개·센서 미러·Store 비용/예상 작업량 판정 |
| **10/26~28** | 5개 담당 구역 라우팅·선택 VPN·서비스 통합 | M1 GNS3 라우터·M2·M3 VyOS의 교실망 연결, M1–M4·M1–M5·M3–M4 VPN 양단·반환 경로·NAT 예외, K8s·로컬 OTT 최소 기능 |
| **10/29~30** | M1·M2·M4 AS-IS 공격, M3·M5 정상 서비스 배포·시험 준비 | 격리 시험 **3건** 로그·원인, **10/30 실제 OTT 배포 환경** 정상 동작 |
| **11/02 월** | M3·M5 AS-IS 공격·시험 결과 취합 | 격리 시험 총 **5건**·개선 대상·정상 기능 비교 기준 |
| **11/03~06** | TO-BE 적용·AI/클라우드/DR 통합 | 11/03 개선안 확정, 11/05 Replica 초기 검증, 11/06 한영 VTT·CDN/API·S3 복원 1차 |
| **11/09~10** | 동일 조건 재공격·장애·복구 시험 | 5명 개선 전후 비교, APP 장애·DB 복원·정상 기능 검증 |
| **11/11~13** | 보고·산출물 정리·리허설 | 11/11 증거 정리, 11/12 발표자료, 11/13 전원 리허설 |
| **11/16 월** | 최종 발표 | 환경 사전 점검·시연 |

## 2. 담당별 작업

| 담당 | 업무·완료 기준 | 기간 | Issue |
|---|---|---|---|
| **M1 유용수** | 본사 GNS3 라우터·VLAN 스위치·UTM·기존 전체 장비·S01 설계 | 10/19~23 | [#1](https://github.com/team-blocks-lab/otter-shield/issues/1) |
|  | 본사 전용 LAN·eth3 trunk·라우팅·VPN·DNS/설치 출구 구축 | 10/21 오후~10/28 | [#14](https://github.com/team-blocks-lab/otter-shield/issues/14) |
|  | S01 직원망→관리망 비인가 접근 재현 | 10/29~30 | [#15](https://github.com/team-blocks-lab/otter-shield/issues/15) |
|  | 관리 접근·방화벽·Bastion 경로 개선 | 11/03~06 | [#16](https://github.com/team-blocks-lab/otter-shield/issues/16) |
|  | S01 동일 조건 재시험·정상 경로 확인 | 11/09~10 | [#17](https://github.com/team-blocks-lab/otter-shield/issues/17) |
|  | 네트워크 설계·보안 전후 결과·시연 | 11/11~13 | [#18](https://github.com/team-blocks-lab/otter-shield/issues/18) |
| **M2 윤서영** | 독립 VyOS/UTM·SOC/TEST/MGMT NIC 4개·S02 설계 (VLAN 없음) | 10/19~23 | [#2](https://github.com/team-blocks-lab/otter-shield/issues/2) |
|  | 독립 VMnet·Wazuh·SSH 시험 서버·센서 가시성 확인 (Bastion은 TO-BE) | 10/21 오후~10/28 | [#19](https://github.com/team-blocks-lab/otter-shield/issues/19) |
|  | S02 반복 SSH 인증 실패·탐지 로그 확보 | 10/29~30 | [#20](https://github.com/team-blocks-lab/otter-shield/issues/20) |
|  | 인증·탐지/대응 정책 개선 | 11/03~06 | [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) |
|  | S02 동일 조건 재시험·중앙 로그 대조 | 11/09~10 | [#22](https://github.com/team-blocks-lab/otter-shield/issues/22) |
|  | 관제·탐지 근거·시연 | 11/11~13 | [#23](https://github.com/team-blocks-lab/otter-shield/issues/23) |
| **M3 홍은서 (PL)** | VyOS/UTM·DMZ/APP/DATA VMnet·AWS React/CDN·S03 설계 | 10/19~23 | [#3](https://github.com/team-blocks-lab/otter-shield/issues/3) |
|  | VLAN 없는 네트워크 카드(NIC)별 망 분리·vSphere·Docker/K8s·DB·Nginx 기반 구축 | 10/21 오후~10/28 | [#24](https://github.com/team-blocks-lab/otter-shield/issues/24) |
|  | S03 관리 포트 과다 노출 재현·원인 분석 | 11/02 | [#25](https://github.com/team-blocks-lab/otter-shield/issues/25) |
|  | 서비스망 관리 접근·방화벽/K8s 보안 개선 | 11/03~06 | [#26](https://github.com/team-blocks-lab/otter-shield/issues/26) |
|  | S03 재시험·APP/관리 정상 동작 검증 | 11/09~10 | [#27](https://github.com/team-blocks-lab/otter-shield/issues/27) |
|  | 서비스 배포·PL 통합 결과·시연 | 11/11~13 | [#28](https://github.com/team-blocks-lab/otter-shield/issues/28) |
| **M4 박진혁** | DR·DB 복제·S3 백업·S04 설계 | 10/19~23 | [#4](https://github.com/team-blocks-lab/otter-shield/issues/4) |
|  | UTM/독립 백업망·시험 파일·복원 구역·인터넷 출구 확인 | 10/21 오후~10/28 | [#29](https://github.com/team-blocks-lab/otter-shield/issues/29) |
|  | S04 비인가 백업 파일 접근 재현 | 10/29~30 | [#30](https://github.com/team-blocks-lab/otter-shield/issues/30) |
|  | 백업 권한·방화벽·저장소 접근 개선 | 11/03~06 | [#31](https://github.com/team-blocks-lab/otter-shield/issues/31) |
|  | S04 재시험·실제 DB 복원 결과 대조 | 11/09~10 | [#32](https://github.com/team-blocks-lab/otter-shield/issues/32) |
|  | DB 복제·백업·DR 증거·시연 | 11/11~13 | [#33](https://github.com/team-blocks-lab/otter-shield/issues/33) |
| **M5 유은혜 (PM)** | **인프라·개발 병행 설계:** 캐나다 UTM 네트워크 카드(NIC)별 망 분리/VPN·S05 / OTT API·DB·AWS 경로 | 10/19~23 | [#5](https://github.com/team-blocks-lab/otter-shield/issues/5) · [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
|  | 캐나다 UTM 운영/콘텐츠/관리 독립 VMnet·M1–M5 VPN·인터넷 출구 구축 | 10/21 오후~10/28 | [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) |
|  | **개발 병행:** ERD·Class/API·React/Spring/FastAPI 기본 골격 | **10/22~23** | [#5](https://github.com/team-blocks-lab/otter-shield/issues/5) · [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
|  | **개발 병행:** 로컬 로그인·권한·목록·샘플 영상 / 캐나다 VPN 검증 | **10/26~28** | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) |
|  | **개발 병행:** M3 AS-IS 최소 앱 배포·정상 기능 확인 / AWS 웹 경로 준비 | **10/29~30** | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |
|  | S05 허용 OTT 웹 경로의 SQLi 패턴 전달·탐지 재현 | 11/02 | [#35](https://github.com/team-blocks-lab/otter-shield/issues/35) |
|  | 캐나다 DB 접근 제한·VPN 정책 개선 | 11/03~06 | [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) |
|  | **개발·인프라 병행:** 실제 STT·한영 SRT/VTT·React 표시, AWS HTTPS/API / S05 TO-BE | **11/03~06** | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) · [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) |
|  | S05 재시험·정상 OTT/API 접근 확인 | 11/09~10 | [#37](https://github.com/team-blocks-lab/otter-shield/issues/37) |
|  | **검증 병행:** 캐나다 보안 재시험 + OTT/AI 정상 요청 회귀 검증 | **11/09~10** | [#37](https://github.com/team-blocks-lab/otter-shield/issues/37) · [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
|  | 캐나다/앱/PM 결과 취합·시연 | 11/11~13 | [#38](https://github.com/team-blocks-lab/otter-shield/issues/38) |

## 3. 공동 통합 업무

| Issue | 작업 | 주관·협업 | 기간 |
|---|---|---|---|
| [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) | 전체 설계 설계 기준·강사 피드백·5개 PC 연결·NIC/VMnet·설치 출구 기준 검토 | M5(PM)·M3(PL)·전원 | 10/19~23 |
| [#7](https://github.com/team-blocks-lab/otter-shield/issues/7) | M1 GNS3 라우터·M2·M3 VyOS 라우팅·M1–M4·M1–M5·M3–M4 VPN·정상/차단 경로 통합 | M1·각 망 담당 | 10/26~28 |
| [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) | React/Spring/MySQL/FastAPI 설계·개발·배포·한영 자막 | M5 코드·M3 배포 | 10/19~11/06 |
| [#9](https://github.com/team-blocks-lab/otter-shield/issues/9) | Wazuh/Suricata 중앙 로그·각 망 수집 연동 | M2 총괄·전원 로그 제공 | 10/26~11/06 |
| [#10](https://github.com/team-blocks-lab/otter-shield/issues/10) | MySQL Replica·백업·S3·격리 복원 | M4·M3 | 10/26~11/10 |
| [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) | APP 2 Pod 분산·복구/Worker 장애 검증 | M3·M5 | 11/02~10 |
| [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) | OTT S3/CloudFront 영상·React·한국 API + 캐나다 Store EKS/RDS | M5·M3 | 10/21~11/06 |
| [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) | 최종 보고서·발표자료·5인 리허설·발표 | 전원 | 11/09~16 |

**M5 병행 일정:** 캐나다 인프라(#5·#34~#38)와 개발(#8·#12)을 동일 기간 병행. 각 Issue는 다른 성과물 기준으로 검증하며, VPN 정상·앱 정상·AI 완료를 하나의 완료 상태로 합산하지 않음.

**앱·인프라 연계 일정:** 10/22~23 M5 ERD·Class/API 명세·개발 골격 착수 → 10/28 로컬 로그인·권한·목록·샘플 영상 → **10/30 M3 AS-IS 배포 환경** 기본 기능 확인 → 11/06 실제 STT·한영 번역·SRT/VTT·React 재생 검증. **코드 개발 M5 / 서버·DB·Docker/K8s 배포 M3**.

## 4. 선행조건 및 진행 기준

- **AS-IS 공격 선행조건:** 격리 환경, 승인된 시험 범위, 정상 업무 통신·해당 서비스 동작·원본 로그 확보. 공격 재현 뒤 TO-BE 정책 적용
- **기술 배치:** M1 GNS3 VLAN / M2 독립 UTM NIC 4개 / M3의 vSphere·Docker 이미지·Kubernetes 기본 목표(Control Plane 1+Worker 2, Spring 2개 Pod/LB), M4의 MySQL Primary→Replica·격리 복원, OTT S3·CloudFront/OAC·영상 업로드/재생·한국 API와 캐나다 Store(ALB/EKS/RDS). 상세 설치 사양은 [담당 가이드](design/network-guides/README.md) 참조
- **보안 책임:** M1/M3/M4/M5 담당망 방화벽·접근통제·로그 설정 및 시험 수행 / M2 Wazuh·Suricata 중앙 관제·연동 총괄
- **일정 위험:** M3(K8s·DB·LB·PL)와 M5(캐나다 VPN·앱·AI·PM) 업무 집중. 10/28·10/30 선행 기능 미완료 시 종속 시험 상태 `Blocked`, 범위·지원·일정 재협의
- **개정 일정안:** AS-IS 공격은 10/29~30 M1·M2·M4, 11/02 M3·M5로 유지. v0.2의 10/30 5건 일괄 목표는 현재 일정안으로 대체하며 팀 검토가 필요함. Replica는 TO-BE 11/03~06 적용, 11/05 첫 복제·11/10 최종 검증 목표.
- **업무 관리:** [Projects](https://github.com/orgs/team-blocks-lab/projects/4) = Status, Issue = 체크리스트·일일 결과, Notion = 명령어·설정·스크린샷·검증 증거. Projects의 날짜 필드는 WBS와 별도 관리
- **기록·보안:** 구축 전 상태 `미수행`·미확정 결정 `미확정` 표기. 승인된 격리 환경에서만 취약점 재현, 공개 저장소의 비밀번호·API 키·VPN PSK 등록 금지

## 5. 이번 변경 기준과 초기 검증 작업

> 계획 개정 승인은 실제 구축 완료·팀 전원 기술 검토 완료와 다릅니다. 아래 날짜는 실행 목표이며 결과 확인 전 체크하지 않습니다.

| 확인 항목 / 연결 Issue | 기한 | 작업·담당 | 통과 기준 / 실패 시 처리 |
|---|---|---|---|
| 교실망 연결 · #6 | 10/20 | 전원 실제 IPv4·마스크·교실 추가 IP·브리지 연결 확인 / M1 취합 | 두 PC의 VM 간 왕복 TCP/패킷 확인. 실패 시 교실망/가상 NIC 조건부터 확인 |
| 설계·자원 확인 · #1~#5·#6 | 10/21 오전 | 본인 NIC·VMnet·GNS3 포트·대역·자원표 확정 / 각 담당·PL | 각 내부망 게이트웨이와 시험 경로 명세, 32GB 내 동시 실행안. 교실망 IP와 M1 R1–UTM / M2·M3 VyOS–UTM 연결망 주소는 확인 후 확정 |
| 설치 인터넷 · #14·#19·#24·#29·#34 | 10/23 | 각 망 설치용 인터넷 / 전원 | VM→GW, DNS 조회, 저장소 HTTP(S), 실제 패키지 다운로드·시간동기화. ping만으로 완료 금지 |
| 외부 공개·수집·비용 · #6·#9·#12 | 10/23 | API 외부 공개·미러링·AWS 예산·Store 예상 작업량 판정 / M1·M2·M3·M5·계정 담당 | 선택 방식·근거·담당·기한 기록. 불가 시 공개 CDN/내부 API 증거 분리, 미러 미확인 상태로 탐지 완료 표시 금지 |
| 내부·VPN 연결 · #7 | 10/28 | M1 R1·각 VyOS/UTM의 왕복 경로·NAT 예외·VPN / M1+전원 | 요청/응답 양방향 확인 및 정상/차단 기록. 시험 실패가 라우트 오류인지 먼저 구분 |
| 서비스 배포 · #8·#12 | 10/30 → 11/06 | M5 코드·AWS/Store, M3 한국 배포 / 상호 검토 | 10/30 기본 배포·CDN MP4, 11/06 실제 AI VTT·API 통합. 조건부 외부 API는 별도 판정 |

### 담당별 연결 원칙

NIC는 네트워크 카드, VMnet은 VMware 안의 가상망입니다. VLAN은 스위치에서 망을 나누는 기능입니다. AS-IS는 보안 개선 전, TO-BE는 개선 후 환경입니다. SSH는 서버 원격 관리 접속, Bastion은 승인 관리자용 중계 서버입니다.
- M1: GNS3 라우터 R1 + UTM-1 + GNS3 L2 VLAN 스위치. 별도 VyOS VM 없음. 서버 10·직원 PC 6·관리 PC 2·스위치 10은 설계에 보존. 동시 기동 수는 자원표로 조절. R1은 상위 연결, UTM1은 VLAN 게이트웨이·방화벽·VPN 담당. L2 스위치에서 망 간 라우팅하지 않음.
- M2: VyOS-2 + UTM-2. 외부 포함 NIC 4개, SOC/TEST/MGMT 독립 VMnet. VLAN 및 UTM 바로 아래 통합 스위치 없음.
- M3: VyOS-3 + UTM-3. DMZ/APP/DATA는 NIC별 VMnet, TO-BE MGMT 추가 시 외부 포함 NIC 5개. React/MP4/VTT는 AWS S3+CloudFront.
- M4: 기존 백업·DR 책임 유지. UTM4의 교실 Bridged 직결 출구는 제안, 10/23 확정. VLAN/직결 방식은 실제 가상 L2 조건과 함께 결정.
- M5: UTM-5 외부+운영+콘텐츠+관리 NIC 4개. VLAN 미사용, M1–M5 VPN 업무 VPN. 교실 Bridged 직결 출구는 제안.
- 교실 게이트웨이 주소를 M1 R1 또는 M2·M3 VyOS에 중복 배정하지 않음. M1 R1–UTM1 및 M2·M3 VyOS–UTM 연결망 주소는 제안값이며 실제 배정 전 확인. 내부·VPN 트래픽은 인터넷 NAT와 구분.
- 고객은 S3 업로드가 아니라 CloudFront에서 영상을 재생. 관리자가 S3에 업로드하고 DB는 제목·URL·자막 작업 메타데이터 보관.

### M5 과부하 및 변경 관리
- M5는 캐나다 인프라+OTT/AI+Store 코드·AWS+PM을 병행. M3에게 앱 코드를 임의 이관하지 않음.
- 10/23 Store EKS/RDS의 비용·예상 예상 작업량를 확인하고 10/30 최소 Store(상품 조회·모의 주문) 배포 가능 여부를 판정. 불가하면 배치 단순화/지원/범위 변경안을 팀이 결정하며 임의로 완료·제외 처리하지 않음.
- 우선순위는 5개 보안 전후 증거·기본 OTT/CDN·실제 AI 자막·DB 복원. 추가 언어·챗봇·고급 HA는 이후.
- 기존 Issue 번호·기한·진행 상태는 보존. 문서 갱신은 실습 완료가 아니며 Projects Status/날짜는 별도 확인 대상.

**10/20 S05 변경:** M5→업무 VPN·M1→M3 Nginx TLS 종료→APP Suricata→HTTP API. AS-IS 전달·탐지 / TO-BE 동일 요청 IPS 차단·정상 요청 유지. [시험 계약](design/scenarios/s05-web-ips.md). 담당·기한은 유지하며 M3가 센서/프록시, M2가 중앙 증거를 협업합니다.
