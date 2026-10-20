# OTTer Shield | 프로젝트 업무·일정

**Team Blocks · 2026.10.19–11.16 · 발표 11/16 · 10/20 개정**

[업무 보드](https://github.com/orgs/team-blocks-lab/projects/4/views/2) · [토폴로지](design/토폴로지/README.md) · [회의록](meetings/2026-10-20-design-decisions.md) · [계획서 v0.3](plans/project-plan-v0.3.pdf)

**현재:** AS-IS 설계. **기존 목표 10/20 → 현재 10/21 오전 완료 예상(팀 확인 전).** 도면·연결 확인 후 10/21 구축을 시작합니다. 오늘 TO-BE 도면은 제출하지 않습니다.

아래 날짜는 수행 목표·예상이며 완료 실적이 아닙니다. 기간은 개인별 투입 공수가 아니며, 개발과 인프라의 병행 업무는 별도 결과로 확인합니다.

## 1. 전체 일정

| 단계·ID | 일정 | 주관 | 주요 산출물·종료 기준 | 선행조건 |
|---|---|---|---|---|
| A1 AS-IS 설계 | 10/20–10/21 오전 예상 | 각 망·PL 연결 검토 | draw.io·PNG·장비/연결·시험 경로 | 실제 환경 검토 |
| A2 기본망 구축 | 10/21–10/23 | 각 망 | 장비·OS·IP·DNS·시간·설치 인터넷 | 해당 A1 도면 확인 |
| A3 서비스·망 간 연결 | 10/26–10/28 | 각 망·M1 통합 | 게시판·DB·관리·VPN 정상 기능·원본 로그 | 해당 A2·필요 앱 |
| A4 공격·원인 분석 | 10/29–10/30 M1/M2/M4, 11/02 M3/M5 | 각 망·PL 취합 | 시험5건·원인·개선 요구·AS-IS 보존 | 대상 서비스 정상·시험 준비 |
| T1 TO-BE 설계·검토 | 11/03 | 각 망·관련 담당·PL | 개선 도면·정책·추가 자원·롤백 | A4 해당 분석 |
| T2 개선 구현 | 11/04–11/05 | 각 망 | 기존 환경 재사용·설정/설치 증거 | 해당 T1 검토 |
| T3 통합 확인 | 11/06 | PL·각 망 | 정상 업무·실제 설정과 도면 일치 | T2 |
| V1 재공격·장애·복원 | 11/09–11/10 | 각 망·연계 담당 | 전후 비교·정상 업무·복구 증거 | 해당 T3 |
| V2 오류 보완·보고서 | 11/11–11/12 | 해당 담당·PM 취합 | 수정 영향 확인·증거·발표자료 | 검증 결과; 초안 병행 가능 |
| P1 리허설·발표 | 11/13 리허설, 11/16 발표 | 전원 | 시연·대체 자료·본인 기여 | 결과 정리 |

AS-IS 구축은 약6평일을 확보합니다. TO-BE는 기존 기반에 변경을 적용하는 **구현2일+통합1일 목표**입니다. Wazuh·Replica·이중화의 설치/연동은 단순 방화벽 규칙 변경과 구분합니다. 11/11 오류 보완 시간을 남기며 주말은 필수 일정에 넣지 않습니다.

## 2. 수요일 10/21 담당별 착수 계획

오전에는 각자 AS-IS 도면을 마무리·업로드하고 연결 상대를 확인합니다. 이후 아래 장비 생성·연결·설치를 시작합니다. 오전 완료는 현재 예상이며 실제 결과로 확인합니다.

| 담당 | 첫 구축 작업 | 당일 남길 결과 | 작업 Issue |
|---|---|---|---|
| M1 유용수 | GNS3에 R1·L2 스위치를 만들고 UTM1 가상 장비를 준비합니다. DMZ·서버·관리와 직원/공통 연결을 도면대로 연결합니다. | 도면 링크·만든 장비·OS 설치 상태·기본 연결 결과·문제 | [#14](https://github.com/team-blocks-lab/otter-shield/issues/14) |
| M2 윤서영 | M1과 자산·연결 구조를 맞춘 GNS3 R2·L2 스위치·UTM2를 준비합니다. 독일 IP를 넣을 대표 업무 서버·PC를 만듭니다. Wazuh는 아직 적용하지 않습니다. | 도면 링크·만든 장비·OS 설치 상태·기본 연결 결과·문제 | [#19](https://github.com/team-blocks-lab/otter-shield/issues/19) |
| M3 홍은서 | R3·UTM3와 웹/앱/DB/관리 가상망을 만들고 직접 연결합니다. CPU 중첩 가상화 가능 여부를 확인하고 웹·DB·ESXi 설치를 시작합니다. | 도면 링크·만든 장비·OS 설치 상태·기본 연결 결과·문제 | [#24](https://github.com/team-blocks-lab/otter-shield/issues/24) |
| M4 박진혁 | UTM4·백업 가상망·백업 서버·운영/시험 PC를 만들고 OS 설치·기본 연결을 시작합니다. 복제 DB 설치는 TO-BE 단계입니다. | 도면 링크·만든 장비·OS 설치 상태·기본 연결 결과·문제 | [#29](https://github.com/team-blocks-lab/otter-shield/issues/29) |
| M5 유은혜 | UTM5의 외부·운영·콘텐츠·관리 NIC4개와 각 가상망/대표 PC를 만듭니다. OS·IP·기본 연결을 시작하고 앱 실행 조건·개발 환경도 준비합니다. | 도면 링크·만든 장비·OS 설치 상태·기본 연결 결과·문제 | [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) |

PM은 도면 제출/예상 변경을 취합하고, PL은 망 간 연결·가상화 가능 여부를 검토합니다. 전원의 첫날 목표는 장비 생성·연결·설치 착수이며 업무 서비스 전체 완성이 아닙니다.


## 3. 개발·배포 일정 — 인프라와 병행

**코드 개발: M5 유은혜.** 게시판 현지 배포는 M1·M2, 한국 OTT/AI 런타임·DB·배포는 M3, 캐나다 Store·AWS는 M5입니다. M3에게 앱 개발을 임의 이관하지 않습니다.

| ID·대상 | 일정 | 구현·인계할 결과물 | 개발·배포 책임 | 연결 |
|---|---|---|---|---|
| D1 실행 규격·개발 환경 | 10/21 | 서비스별 최소 기능·API/DB·실행 버전·환경변수 이름·배포 위치 합의 | M5 개발·M3/M1/M2 실행 조건 확인 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
| D2 공통 게시판 | 10/22–10/23 | 기본 게시판·계정/권한 코드 우선 구현, 한국/독일 설정 분리. 나머지 앱은 실행 골격 준비 | M5 코드·M1/M2 인계 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
| D3 OTT 최소 기능 | 10/26–10/28 | 로그인·권한·목록·샘플 영상, React–Spring–DB 로컬 연결 | M5 코드·M3 DB/런타임 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
| D4 게시판·OTT 배포 | 10/29–10/30 | M1/M2 게시판·M3 OTT 정상 요청 확인, 공격 시험용 앱 기준 확보 | M1/M2 게시판·M3 OTT·M5 지원 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
| D5 Store 최소 기능·AWS | 10/29–11/06 | 10/30 상품 조회·모의 주문의 최소 구현/배포 가용성 판정, 11/06 ALB–EKS–RDS 정상 연동 목표 | M5 코드·AWS | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |
| D6 CI/CD | 준비10/29–10/30, 연동11/03–11/06 | Actions 빌드/검사·이미지/배포 Git → Argo CD 배포, 버전·되돌리기 증거. S3 정적 배포 별도 | M5 workflow·M3 K8s 대상·M5 EKS 대상 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |
| D7 AI 자막·웹 연동 | 11/03–11/06 | 11/04 짧은 영상 실제 음성인식·한영 SRT/VTT, 11/06 배포 웹 자막 재생·오류/비용 확인 | M5 코드·M3 실행 환경 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
| D8 앱 회귀·배포 복구 | 11/09–11/10 | 보안 개선 뒤 게시판·OTT·Store·AI 정상 요청·배포 되돌리기 확인 | M5 앱 확인·각 배포 담당 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) |

**개발 일정 점검:** M5는 지사망·코드·AI·AWS·PM을 병행하므로 위 목표를 전부 독립된 전일 작업으로 계산하지 않습니다. 10/23 최소 기능/Store 공수·예산, 10/28 로컬 기능, 10/30 기본 배포를 점검합니다. 지연 시 어떤 기능·시험이 영향을 받는지 기록하고 팀이 지원·범위·일정을 결정합니다. 실물 코드·진척 미확인 상태에서 전체 개발의 기한 달성을 보장하지 않습니다.

## 4. 담당별 업무·Issue

| 담당 | AS-IS 설계·구축 | 공격·분석 | TO-BE 설계·구현 | 재검증·결과 |
|---|---|---|---|---|
| **M1 유용수** | [#1](https://github.com/team-blocks-lab/otter-shield/issues/1) · [#14](https://github.com/team-blocks-lab/otter-shield/issues/14) | [#15](https://github.com/team-blocks-lab/otter-shield/issues/15) | [#16](https://github.com/team-blocks-lab/otter-shield/issues/16) | [#17](https://github.com/team-blocks-lab/otter-shield/issues/17) · [#18](https://github.com/team-blocks-lab/otter-shield/issues/18) |
| **M2 윤서영** | [#2](https://github.com/team-blocks-lab/otter-shield/issues/2) · [#19](https://github.com/team-blocks-lab/otter-shield/issues/19) | [#20](https://github.com/team-blocks-lab/otter-shield/issues/20) | [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) | [#22](https://github.com/team-blocks-lab/otter-shield/issues/22) · [#23](https://github.com/team-blocks-lab/otter-shield/issues/23) |
| **M3 홍은서·PL** | [#3](https://github.com/team-blocks-lab/otter-shield/issues/3) · [#24](https://github.com/team-blocks-lab/otter-shield/issues/24) | [#25](https://github.com/team-blocks-lab/otter-shield/issues/25) | [#26](https://github.com/team-blocks-lab/otter-shield/issues/26) | [#27](https://github.com/team-blocks-lab/otter-shield/issues/27) · [#28](https://github.com/team-blocks-lab/otter-shield/issues/28) |
| **M4 박진혁** | [#4](https://github.com/team-blocks-lab/otter-shield/issues/4) · [#29](https://github.com/team-blocks-lab/otter-shield/issues/29) | [#30](https://github.com/team-blocks-lab/otter-shield/issues/30) | [#31](https://github.com/team-blocks-lab/otter-shield/issues/31) | [#32](https://github.com/team-blocks-lab/otter-shield/issues/32) · [#33](https://github.com/team-blocks-lab/otter-shield/issues/33) |
| **M5 유은혜·PM** | [#5](https://github.com/team-blocks-lab/otter-shield/issues/5) · [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) | [#35](https://github.com/team-blocks-lab/otter-shield/issues/35) | [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) | [#37](https://github.com/team-blocks-lab/otter-shield/issues/37) · [#38](https://github.com/team-blocks-lab/otter-shield/issues/38) |

상세 체크리스트는 Issue에 두고 여기에는 일정·담당·산출물만 연결합니다. 설계·구현을 같은 Issue 안에서 구분하며 설치를 공동/전문 작업과 중복 공수로 세지 않습니다.

## 5. 공동·전문 작업 책임

| 구분·작업 | 주담당 | 공동 수행·지원 | 배정 원칙 | 연결 |
|---|---|---|---|---|
| 공동 조정: 도면·착수 | PM 유은혜 | PL 홍은서 / 전원 도면 제출 | PM·PL 배정 | [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) |
| 공동: 망 연결·VPN | M1 유용수 | M2·M3·M4·M5 | 실제 연결 수행5명 배정 | [#7](https://github.com/team-blocks-lab/otter-shield/issues/7) |
| 공동: 코드·OTT 배포 | M5 유은혜 | M3 홍은서 / M1·M2 현지 인계 | M5·M3, 현지 배포는 각 구축 Issue | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
| **M2 전문: Wazuh 검증** | **윤서영** | M1 비교 조건 제공 | **M2만 배정, 공통 표기 제거** | [#9](https://github.com/team-blocks-lab/otter-shield/issues/9) |
| 공동: 복제·S3·복원 | M4 박진혁 | M3 홍은서 | M4·M3 배정 | [#10](https://github.com/team-blocks-lab/otter-shield/issues/10) |
| 공동: 앱/노드 장애 | M3 홍은서 | M5 유은혜 | M3·M5 배정 | [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) |
| 공동: AWS·API·Store | M5 유은혜 | M3 한국 API·M1 진입 경로 | M5·M3·M1 배정 | [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |
| 전원: 보고·발표 | PM 취합 | PL 기술 검토·전원 발표 | 5명 배정 | [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) |

## 6. 종료 기준·위험 관리

- **공격 전:** 정상 업무·격리 시험 대상·원본 로그·초기 스냅샷 확보. 가짜 데이터·승인 계정만 사용합니다.
- **TO-BE 설계:** 공격 근거 → 개선 도면·정책 → 검증 방법·롤백이 연결되어야 합니다. 연결선이 같으면 규칙·권한·로그 흐름 차이를 표시합니다.
- **구현·재검증:** 도면·실제 설정 일치, 정상 업무와 동일 조건 공격 전후 결과를 각각 확인합니다. 경보·차단·복원은 별도 증거입니다.
- **자원:** 각 PC RAM32GB, 실제 동시 실행은 확인 필요. M1/M2 같은 대표 규모, Wazuh 전체18대는 단계 등록. Nginx·Replica·Wazuh의 설치/연동 실패는 남은 영향과 재계획을 기록합니다.
- **10/23 미정 확인:** 실제 IP·버전/자원, 본사–서비스 VPN 여부·본사–DR 허용 업무, 한국 API 공개, 캐나다 도시/리전·AWS 비용·이미지 저장소는 관련 담당이 확인합니다.
- **설계 유지:** M1·M2 GNS3·동등 업무 자산, 독일만 Wazuh, M2/M3 Suricata 제외. M3 나머지 서버·M1/M4/M5 범위 유지. M1 실장비 간소화는 윤서영 주담당·박진혁 보조, 착수일 별도 협의.
- **상태 관리:** 문서 개정으로 Issue를 닫거나 완료 체크하지 않습니다. WBS=일정, 보드=상태, Issue=작업 결과, Notion=기술 상세·증거입니다.

## 7. 계획 변경 기록

| 변경일 | 항목 | 기존 기준 | 현재 예상·변경 내용 | 이유·영향·다음 확인 | 상태 |
|---|---|---|---|---|---|
| 10/20 | AS-IS 도면 1.1·1.2 | 10/20 제출·연결 확인 | 10/21 오전 완료 예상 | 실제 PC·가상화·UTM·연결 조건 검토 지속. 10/21 구축 목표는 유지하고 실제 시작/진척을 당일 확인. 10/28 이후 목표 영향은 아직 미확정 | 예상 변경·팀 확인 전 |

변경 사유·결정은 회의록, 업무별 실제 지연·진척은 Issue, 기술 원인·시험 증거는 Notion에 기록합니다. 합의 후 WBS를 확정 개정하고 기존 목표·변경일·이유를 남깁니다. 예정일을 조용히 덮어쓰거나 예상 완료를 실적으로 기록하지 않습니다.
