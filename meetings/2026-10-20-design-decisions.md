# 2026-10-20 | 명칭·M1 구성·배포·설계 기준

**팀: Team Blocks · 프로젝트: OTTer Shield — 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅**

[첫 화면](../README.md) · [WBS](../WBS.md) · [토폴로지 v1.2](../design/architecture.md) · [개발 코드 안내](../apps/README.md)

## 결정 내용

| 항목 | 내용 |
|---|---|
| 팀·조직 | Team Blocks / GitHub 조직 `team-blocks-lab` |
| 프로젝트·저장소 | OTTer Shield / `team-blocks-lab/otter-shield` |
| 보안 컨설팅 회사·고객사 | NetBlocks / OTTer |
| M1 현재 실습망 | 별도 VyOS 대신 GNS3 R1, GNS3 L2 VLAN 스위치, UTM1(Sophos UTM 9). UTM이 VLAN 게이트웨이·보안 통제·VPN 담당 |
| M1 후속 실장비 간소화 설계 | 주담당 윤서영 / 보조 박진혁. 현재 가상 M1의 자산 보존 조건과 구분 |
| M3·M5 CI/CD | GitHub Actions로 빌드·검사, 기존 Kubernetes·EKS 내부 Argo CD로 배포. 별도 로컬 CI/CD 전용 VM은 기본안에서 제외 |
| 앱 개발 폴더 | M1 사내 게시판 / M3 OTT 메인·AI / M5 Store를 `apps/` 아래 배포 대상별로 구분. 앱 개발 담당 M5 유지 |
| IP 배정 | 세부 배정표는 팀 공유 자료에서 관리. 공개 GitHub에는 내부 주소표를 게시하지 않음. 실제 경계 IP·도면 기호·NIC를 대조해 적용 |

## v1.2 수정 설계안·구축 전 검토

- 장비·프로그램별 존재 이유, 연결, 보호 범위, 실제 완료 증거를 명시합니다.
- UTM 명칭은 `UTM1(Sophos UTM 9)`~`UTM5(Sophos UTM 9)`로 통일합니다.
- M2 SOC와 M3 DMZ·APP·DATA의 센서는 실제 통신 경로에 배치합니다. 탐지와 IPS 차단, 방화벽 차단, 서버 권한 통제를 구분합니다.
- 각 망의 Wazuh Agent·UTM 로그·센서 이벤트를 M2에 수집하며, 관제 경로는 업무 VPN과 구분한 직접 라우팅으로 설계합니다.
- M1 QEMU 단말 배치, 중첩 가상화·센서 전달, 설치 버전, 외부 API 공개, AWS SSM 관리 EC2·비용은 구축 전 확인할 항목입니다.

기존 WBS 날짜·담당·Issue 상태는 유지합니다. 위 설계안의 문서화는 팀 전원의 기술 검토나 실제 통신·차단 시험 완료를 의미하지 않습니다.

## 추가 결정 · S05 Suricata 역할 강화

사용자가 S05 변경을 승인했습니다. 기존 직원→DB 직접 접근 시연을 **허용 OTT HTTPS 경로의 SQLi 패턴 요청 탐지·차단**으로 바꿉니다. Nginx TLS 종료 뒤 APP Suricata가 HTTP 내용을 검사하며 AS-IS 전달·경보, TO-BE 동일 요청 drop·정상 요청 통과를 비교합니다. T15 보호 대상·UTM 웹 허용·왕복 경로·중앙 증거도 함께 조정합니다. 직원→DB 직접 접근은 기본 차단 정책으로 유지합니다. M1 포트폴리오 자산과 5개 시나리오 번호·담당·기한은 유지합니다. [구현 계약](../design/scenarios/s05-web-ips.md). 구축·실제 차단 시험은 아직 수행 전입니다.
