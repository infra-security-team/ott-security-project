# M3 홍은서 (PL) · 한국 OTT 서비스망·DB·앱 배포

> **v1.2 우선 확인:** [최신 토폴로지·보안 연결·검증 범위](../architecture.md)를 먼저 읽으세요. 아래 상세 내용에는 이전 설계·제안이 남아 있을 수 있으며, 실제 배선·센서·관제 경로는 v1.2 및 팀 확정값과 대조합니다.

**Issue:** [설계 #3](https://github.com/team-blocks-lab/otter-shield/issues/3) · [AS-IS #24](https://github.com/team-blocks-lab/otter-shield/issues/24) · [앱/AI 통합 #8](https://github.com/team-blocks-lab/otter-shield/issues/8)

**역할 경계:** M5가 React/Spring Boot/FastAPI 앱 코드를 개발·GitHub 등록. **M3는 앱 구현이 아니라 서버/DB 환경 구성·코드 수령·Docker/K8s 배포·서비스 운영·검증**을 수행합니다.

## 사용할 프로그램과 서비스
- 도면: diagrams.net / 가상화: 학원 VMware Workstation·vSphere/ESXi 사용 가능 범위 확인
- OS: Linux / 웹 진입: Nginx 등 프록시·로드밸런서 / APP: Java 런타임·Spring Boot, Python 런타임·FastAPI
- DB: MySQL / 배포: **Docker 이미지 빌드 + Kubernetes 클러스터 배포**(v0.2 기본안). vSphere/ESXi·vCenter 또는 강사 승인 대체 환경을 사용하고, 실제 자원/라이선스에 맞게 조정.
- 테스트: curl/HTTP 클라이언트, 브라우저, MySQL 클라이언트, 네트워크/서버 로그
- 공개 고객 웹 AWS 진입점은 **M5와 협의**하며, 한국 서비스망의 내부 웹/프록시와 역할이 겹치지 않게 구성.

## 장비·기능 명세 (VM 개수는 확인 전 예시)
| 논리 자산·구역 | 시작 수량 | 역할 | 필수/조건 |
|---|---:|---|---|
| KR-VyOS (망 경계) | 1 VM | DMZ/APP/DATA 라우팅·방화벽·VPN 본사 연동 | 해당 기능을 이미 공용 L3/방화벽이 담당한다면 중복 VM 검토 |
| KR-WEB (DMZ) | 1 VM/컨테이너 호스트 | Nginx 리버스 프록시, HTTPS/API 진입 경로 | 고객 진입점과 내부 앱 관리 포트 구분 |
| KR-APP (APP) | 1 VM/컨테이너 호스트 | Spring Boot·필요 시 FastAPI 기동 | 개발/운영 역할 분리. 처음부터 여러 APP VM 필수 아님 |
| KR-DB (DATA) | 1 VM | MySQL Primary, DB 인증·접근 제한 | DB는 직원/외부·캐나다 단말에서 일반적으로 직접 접근 금지 |
| KR-Test-Client | 조건부 1 | API·관리 포트·정상 재생 요청 검증 | M5·M1 관리/시험 클라이언트로 대체 가능하면 생략 |
| Kubernetes Control Plane/Worker | **1+2 노드 제안** | Control Plane 1, Worker 2. Docker로 빌드한 Spring 컨테이너 이미지 배포·복구 시험 | **v0.2 26쪽 기본안.** 자원 부족 시 1+1 등 변경은 강사/팀 승인 후 제한사항 표시. 기존 KR-APP 호스트를 중복 계산하지 않음 |
| Spring APP 복제본 및 로드밸런서 | **기본 목표: 2개 Pod + LB/프록시** | 서로 다른 Worker에 Spring Boot 2개 복제본 분산, Service/Ingress(또는 승인된 LB)로 요청 분배 | **v0.2 26쪽 기본안.** Pod 삭제·Worker 장애 테스트는 각각 별도 수행. 노드 실패 후 모든 기능의 HA가 보장되는 것으로 해석하지 않음 |
| DNS/DHCP/NTP | 제공자 확인 | 서비스 주소 조회/시간 동기화 | 서버는 고정 IP 권장, 별도 DHCP 서버 VM 강제 불필요 |

## Docker와 Kubernetes를 도면에 **별도로** 표시할 대상
- **Docker:** M5가 전달한 React/Spring Boot/FastAPI 코드로 누가 어디에서 컨테이너 이미지를 빌드하는지, 이미지 저장 경로(레지스트리/전달 방식), 테스트용 단일 Docker 실행 호스트를 명시. Docker는 이미지 빌드·기본 컨테이너 배포 검증에 사용한다.
- **Kubernetes:** **기본 목표 Control Plane 1대 + Worker 2대**, APP **Spring 2개 Pod를 서로 다른 Worker에 분산**, 노드 VLAN/IP·vSphere 자원, Pod·Service·Ingress/로드밸런서, API Server 관리 포트·RBAC를 구분한다. CNI의 NetworkPolicy 지원을 확인한다. 자원 부족으로 노드 수를 조정한다면 변경 근거와 포기한 장애 시험을 별도 표시한다.
- **실행 구조 차이:** Kubernetes 노드에 Docker Engine을 반드시 설치하는 것은 아니다(일반적으로 containerd 등 CRI 호환 런타임). Docker 이미지 빌드/로컬 실험과 Kubernetes 클러스터 배포를 구분해 설계하고, VM 수를 이중 계산하지 않는다.
- **보안·관제:** M3가 직접 관리 포트/DB 접근·컨테이너/Pod 보안 정책·로그 제공을 구성하고, M2의 Wazuh/Suricata와 관측/로그 경로를 합의한다. 모든 망 보안 분담표는 [보안 책임 매트릭스](02-security-deployment-matrix.md)를 참고한다.

## 망도면에서 필수 표시
- DMZ / APP / DATA 구역과 각 VLAN ID·게이트웨이·방화벽 정책 방향.
- **공개 정상 흐름:** 사용자 브라우저 → CloudFront(OAC·비공개 S3) → React 파일 응답 / 별도로 **사용자 브라우저 → 승인된 공개 HTTPS API 진입점 → 프록시·Spring → MySQL**. 공개 API의 DNS·TLS·CORS·경계 정책은 M5와 합의. 취약한 AS-IS 관리/DB 시험망은 인터넷에 공개하지 않음.
- APP ↔ DB MySQL(3306 기본 포트, 최종 확인) 및 백업/복제 M4와의 허용 경로.
- M1 본사 VPN 허브와 라우팅/정책 경계, M2 Wazuh/Suricata 수집 지점.
- AS-IS 격리 시험 S03: 관리 포트 과다 노출의 실제 대상·정상 기능과 보안 검증 조건. K8s 6443을 예로 들더라도 **실제 클러스터가 있어야** 해당 공격 재현 가능.
- TO-BE 초안: 허용된 관리 구역만 관리 포트 접속, 고객 공개 경로의 정상 서비스 유지.
- **기본 제안:** Worker 간 Spring 2개 Pod 분산+Service/LB, readiness/liveness 상태 검사와 실제 요청 분산 확인. APP 복제본 2개 ≠ 전체 시스템 HA. **Pod 삭제 시험과 Worker 장애/복구 시험을 분리**한다.

## 일정과 완료 기준
- **10/19:** 강사 v0.2 피드백과 함께 서비스망·Docker/K8s 노드/서비스·AWS 공개 웹 API 경로·보안 배치 **도면 초안 착수**. 전체 도면 완성/설치 요구 없음.
- **10/20:** AS-IS 도면·TO-BE 방향/정책 공동 검토. Docker/K8s, vSphere, AWS와 M2 보안 연계/자원·S03 실제 대상 가능 여부 확인.
- **10/21 오전:** 설계도·클러스터 노드/런타임·자원 기준선 완료 목표. **21일 오후부터** 승인된 DMZ/APP/DATA VM·네트워크·컨테이너 기반 구축 시작(늦어도 22일). 23일은 실제 초기 결과 확인. *전체 앱/K8s 완료와 구별.*
- **10/26~28:** DMZ/APP/DATA·K8s 기본 네트워크, 정상 관리자 경로와 테스트 서비스/API 연결 확인. **10/28 로컬 기본 앱, 10/30 배포 환경 기본 기능 확인은 M5 코드 인계에 따라 M3 공동 #8에서 별도 검증**한다.
- **10/29~30:** S03 시험 대상(K8s API 6443 등)의 실제 포트/라우팅·로그/관찰 경로 준비. M5 코드 수령 후 **10/30 AS-IS 배포 환경 최소 OTT 정상 요청·응답 확인**.
- **11/02:** **S03 승인된 격리 환경 공격 재현** 및 원인·원본 로그 확보(정상 서비스·시험 범위 확인 후). **11/03** 실제 결과 기반 TO-BE 정책 확정·적용.
- **11/04~06:** AI 자막 연동·서비스 배포·로그/시간초과 검증(연동 결과를 실제로 확인한 만큼만 보고).
- **11/09~10:** S03 재시험·Pod/Worker 범위 내 승인 장애 시험 및 정상 기능/복구 결과.

## 실패 시 점검 포인트
브라우저→CloudFront 정적 파일과 브라우저→HTTPS API 진입점→프록시/Spring→DB 경로를 **별도로** 확인합니다. NIC/포트그룹, 보안 ACL, 바인드 주소, 방화벽, CORS·TLS, DB 권한, 컨테이너 포트·Pod Service 연결, 환경 변수의 '값 존재 여부'(비밀값 공개 금지)를 서로 분리해 봅니다. [공통 진단 템플릿](troubleshooting.md)에 실제 결과 기록.
