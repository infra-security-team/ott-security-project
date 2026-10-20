# 2026-10-20 | 명칭·M1 구성·배포·설계 기준

**팀: Team Blocks · 프로젝트: OTTer Shield — 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅**

[첫 화면](../README.md) · [WBS](../WBS.md) · [개발 코드 안내](../apps/README.md)

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

## 보안 시나리오

- S05는 허용된 OTT 웹 경로의 SQLi 패턴 요청을 탐지·차단하는 시험으로 변경합니다. Nginx TLS 종료 뒤 APP Suricata의 전후 동작을 비교하고 정상 요청은 유지합니다.
- 직원의 DB 직접 접근은 기본 차단 정책으로 유지합니다. 구체적인 시험 설정·로그·증거는 담당 기술서에 기록합니다.

## M1 망 분리 표기

- DMZ·SERVER·ADMIN은 전용 VMnet·UTM 포트로 분리하며 VLAN110·120·140 표기를 제거합니다.
- 직원·공통 구간은 하나의 trunk에 여러 망을 전달하므로 VLAN130·131·132·150을 유지합니다.
- M1의 서버·단말·스위치 수와 역할은 유지합니다. 팀원이 실제 도면·설정을 대조해 반영합니다.
