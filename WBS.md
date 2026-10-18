# OTT 하이브리드 인프라·보안 컨설팅 | WBS

**기간** 2026.10.19~11.16 · **기본 작업시간** 평일 09:00~18:00(점심 1시간 제외) · **발표** 11.16

[START HERE](README.md) · [계획서 v0.2](plans/project-plan-v0.2.pdf) · [Projects 업무 보드](https://github.com/orgs/infra-security-team/projects/4) · [망별 구축 가이드](design/network-guides/README.md)

## 1. 주요 일정 및 완료 기준

| 일정 | 작업 | 확인 기준 |
|---|---|---|
| **10/19 월** | 강사 피드백·4망 AS-IS 설계 착수 | VMware/vSphere·Docker/K8s·AWS·망별 보안/중앙 관제 배치 초안 |
| **10/20 화** | 전체 도면·보안 시나리오·TO-BE 방향 공동 검토 | IP/VLAN/VPN·서버/클라이언트·정상/시험 경로·미확정 사항 |
| **10/21 수 오전** | 도면·장비 명세 통합 검토 | 구축 가능한 AS-IS 설계 기준선 및 자원·비용 검토 |
| **10/21 수 오후~23 금** | 승인된 망부터 AS-IS 구축 착수 | 각 담당 첫 장비 기동·기본 IP/게이트웨이 통신 증거 |
| **10/26~28** | 4망 VPN·서비스 기반 통합 | 허용/차단 경로·반환 라우트, Docker/K8s 기본 구동, 로컬 OTT 최소 기능 |
| **10/29~30** | M1·M2·M4 AS-IS 공격, M3·M5 앱 배포 통합 | 격리 시험 **3건** 로그·원인, **10/30 실제 OTT 배포 환경** 정상 동작 |
| **11/02 월** | M3·M5 AS-IS 공격·시험 결과 취합 | 격리 시험 총 **5건**·개선 대상·정상 기능 비교 기준 |
| **11/03~06** | TO-BE 적용·AI/클라우드/DR 통합 | 11/03 개선안 확정, 11/06 한영 SRT/VTT·CloudFront/API·S3 복원 1차 |
| **11/09~10** | 동일 조건 재공격·장애·복구 시험 | 5명 개선 전후 비교, APP 장애·DB 복원·정상 기능 검증 |
| **11/11~13** | 보고·산출물 정리·리허설 | 11/11 증거 정리, 11/12 발표자료, 11/13 전원 리허설 |
| **11/16 월** | 최종 발표 | 환경 사전 점검·시연 |

## 2. 담당별 작업

| 담당 | 업무·완료 기준 | 기간 | Issue |
|---|---|---|---|
| **M1 유용수** | 본사 VLAN·IP/VPN 허브·S01 설계 | 10/19~23 | [#1](https://github.com/infra-security-team/ott-security-project/issues/1) |
|  | 본사 VLAN·라우팅·VPN·정상 경로 구축 | 10/21 오후~10/28 | [#14](https://github.com/infra-security-team/ott-security-project/issues/14) |
|  | S01 직원망→관리망 비인가 접근 재현 | 10/29~30 | [#15](https://github.com/infra-security-team/ott-security-project/issues/15) |
|  | 관리 접근·방화벽·Bastion 경로 개선 | 11/03~06 | [#16](https://github.com/infra-security-team/ott-security-project/issues/16) |
|  | S01 동일 조건 재시험·정상 경로 확인 | 11/09~10 | [#17](https://github.com/infra-security-team/ott-security-project/issues/17) |
|  | 네트워크 설계·보안 전후 결과·시연 | 11/11~13 | [#18](https://github.com/infra-security-team/ott-security-project/issues/18) |
| **M2 윤서영** | 중앙 관제·시험 구역·S02 설계 | 10/19~23 | [#2](https://github.com/infra-security-team/ott-security-project/issues/2) |
|  | Wazuh·Suricata·Bastion·시험 서버 준비 | 10/21 오후~10/28 | [#19](https://github.com/infra-security-team/ott-security-project/issues/19) |
|  | S02 반복 SSH 인증 실패·탐지 로그 확보 | 10/29~30 | [#20](https://github.com/infra-security-team/ott-security-project/issues/20) |
|  | 인증·탐지/대응 정책 개선 | 11/03~06 | [#21](https://github.com/infra-security-team/ott-security-project/issues/21) |
|  | S02 동일 조건 재시험·중앙 로그 대조 | 11/09~10 | [#22](https://github.com/infra-security-team/ott-security-project/issues/22) |
|  | 관제·탐지 근거·시연 | 11/11~13 | [#23](https://github.com/infra-security-team/ott-security-project/issues/23) |
| **M3 홍은서 (PL)** | 서비스 DMZ/APP/DATA·K8s·S03 설계 | 10/19~23 | [#3](https://github.com/infra-security-team/ott-security-project/issues/3) |
|  | vSphere·Docker/K8s·DB·LB 기반 구축 | 10/21 오후~10/28 | [#24](https://github.com/infra-security-team/ott-security-project/issues/24) |
|  | S03 관리 포트 과다 노출 재현·원인 분석 | 11/02 | [#25](https://github.com/infra-security-team/ott-security-project/issues/25) |
|  | 서비스망 관리 접근·방화벽/K8s 보안 개선 | 11/03~06 | [#26](https://github.com/infra-security-team/ott-security-project/issues/26) |
|  | S03 재시험·APP/관리 정상 동작 검증 | 11/09~10 | [#27](https://github.com/infra-security-team/ott-security-project/issues/27) |
|  | 서비스 배포·PL 통합 결과·시연 | 11/11~13 | [#28](https://github.com/infra-security-team/ott-security-project/issues/28) |
| **M4 박진혁** | DR·DB 복제·S3 백업·S04 설계 | 10/19~23 | [#4](https://github.com/infra-security-team/ott-security-project/issues/4) |
|  | DR VLAN·백업 서버·시험 파일/복원 구역 준비 | 10/21 오후~10/28 | [#29](https://github.com/infra-security-team/ott-security-project/issues/29) |
|  | S04 비인가 백업 파일 접근 재현 | 10/29~30 | [#30](https://github.com/infra-security-team/ott-security-project/issues/30) |
|  | 백업 권한·방화벽·저장소 접근 개선 | 11/03~06 | [#31](https://github.com/infra-security-team/ott-security-project/issues/31) |
|  | S04 재시험·실제 DB 복원 결과 대조 | 11/09~10 | [#32](https://github.com/infra-security-team/ott-security-project/issues/32) |
|  | DB 복제·백업·DR 증거·시연 | 11/11~13 | [#33](https://github.com/infra-security-team/ott-security-project/issues/33) |
| **M5 유은혜 (PM)** | 캐나다 VLAN/VPN·AWS·S05·앱 구조 설계 | 10/19~23 | [#5](https://github.com/infra-security-team/ott-security-project/issues/5) |
|  | 캐나다 VyOS·직원/관리 VLAN·VPN 구축 | 10/21 오후~10/28 | [#34](https://github.com/infra-security-team/ott-security-project/issues/34) |
|  | S05 캐나다 직원→한국 DB 직접 접근 재현 | 11/02 | [#35](https://github.com/infra-security-team/ott-security-project/issues/35) |
|  | 캐나다 DB 접근 제한·VPN 정책 개선 | 11/03~06 | [#36](https://github.com/infra-security-team/ott-security-project/issues/36) |
|  | S05 재시험·정상 OTT/API 접근 확인 | 11/09~10 | [#37](https://github.com/infra-security-team/ott-security-project/issues/37) |
|  | 캐나다/앱/PM 결과 취합·시연 | 11/11~13 | [#38](https://github.com/infra-security-team/ott-security-project/issues/38) |

## 3. 공동 통합 업무

| Issue | 작업 | 주관·협업 | 기간 |
|---|---|---|---|
| [#6](https://github.com/infra-security-team/ott-security-project/issues/6) | 전체 설계 기준선·강사 피드백·4망 연결 검토 | M5(PM)·M3(PL)·전원 | 10/19~23 |
| [#7](https://github.com/infra-security-team/ott-security-project/issues/7) | 4망 Site-to-Site VPN·정상/차단 경로 통합 | M1·각 망 담당 | 10/26~28 |
| [#8](https://github.com/infra-security-team/ott-security-project/issues/8) | React/Spring/MySQL/FastAPI 개발·배포·한영 자막 | M5 코드·M3 배포 | 10/22~11/06 |
| [#9](https://github.com/infra-security-team/ott-security-project/issues/9) | Wazuh/Suricata 중앙 로그·각 망 수집 연동 | M2 총괄·전원 로그 제공 | 10/26~11/06 |
| [#10](https://github.com/infra-security-team/ott-security-project/issues/10) | MySQL Replica·백업·S3·격리 복원 | M4·M3 | 10/26~11/10 |
| [#11](https://github.com/infra-security-team/ott-security-project/issues/11) | APP 2 Pod 분산·복구/Worker 장애 검증 | M3·M5 | 11/02~10 |
| [#12](https://github.com/infra-security-team/ott-security-project/issues/12) | 캐나다 S3·CloudFront(OAC)·한국 API HTTPS | M5·M3 | 10/21~11/06 |
| [#13](https://github.com/infra-security-team/ott-security-project/issues/13) | 최종 보고서·발표자료·5인 리허설·발표 | 전원 | 11/09~16 |

**앱·인프라 연계 일정:** 10/22~23 M5 ERD·Class/API 계약·개발 골격 착수 → 10/28 로컬 로그인·권한·목록·샘플 영상 → **10/30 M3 AS-IS 배포 환경** 기본 기능 확인 → 11/06 실제 STT·한영 번역·SRT/VTT·React 재생 검증. **코드 개발 M5 / 서버·DB·Docker/K8s 배포 M3**.

## 4. 선행조건 및 진행 기준

- **AS-IS 공격 선행조건:** 격리 환경, 승인된 시험 범위, 정상 업무 통신·해당 서비스 동작·원본 로그 확보. 공격 재현 뒤 TO-BE 정책 적용
- **기술 배치:** M3의 vSphere·Docker 이미지·Kubernetes 기본 목표(Control Plane 1+Worker 2, Spring 2개 Pod/LB), M4의 MySQL Primary→Replica·격리 복원, M5의 캐나다 S3·CloudFront/OAC·한국 API. 상세 설치 사양은 [담당 가이드](design/network-guides/README.md) 참조
- **보안 책임:** M1/M3/M4/M5 담당망 방화벽·접근통제·로그 설정 및 시험 수행 / M2 Wazuh·Suricata 중앙 관제·연동 총괄
- **일정 위험:** M3(K8s·DB·LB·PL)와 M5(캐나다 VPN·앱·AI·PM) 업무 집중. 10/28·10/30 선행 기능 미완료 시 종속 시험 상태 `Blocked`, 범위·지원·일정 재협의
- **계획 검토 사항:** v0.2의 10/30 공격 5건 목표와 본 WBS의 10/30 3건·11/02 2건 분산 일정. 10/19 강사·팀 검토 시 확인 대상
- **업무 관리:** [Projects](https://github.com/orgs/infra-security-team/projects/4) = Status, Issue = 체크리스트·일일 결과, Notion = 명령어·설정·스크린샷·검증 증거. Projects의 날짜 필드는 WBS와 별도 관리
- **기록·보안:** 구축 전 상태 `미수행`·미확정 결정 `미확정` 표기. 승인된 격리 환경에서만 취약점 재현, 공개 저장소의 비밀번호·API 키·VPN PSK 등록 금지
