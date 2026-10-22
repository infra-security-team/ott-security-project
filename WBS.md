# OTTer Shield | WBS

Team Blocks · 2026.10.19–11.16 · 최종 발표 11/16

[업무 보드](https://github.com/orgs/team-blocks-lab/projects/4/views/2) · [팀 기술서](README.md#팀원별-기술서) · [댓글 작성 방법](README.md#issue-진행-댓글-작성) · [Topology](design/topology/README.md)

관리용: [전체 WBS·담당별 일정·인계 조건 Excel](plans/wbs/otter-shield-wbs-master.xlsx)

칠판 게시용 인쇄본: [A3 가로 2장 엑셀 WBS](plans/wbs/otter-shield-wbs-print-a3-2pages.xlsx) · 수행한 작업의 날짜 칸을 색칠해 진행 상황을 표시합니다.

담당 업무의 날짜를 확인한 뒤 Issue에서 세부 작업·완료 기준을 확인합니다. 아래 일정은 목표이며, 실제 진행 상태는 업무 보드와 Issue에서 관리합니다.

## 현재 상태 · 2026.10.22 개정

| 항목 | 확인된 현황 | 남은 확인 |
|---|---|---|
| AS-IS 토폴로지 | Issue #1~#5 종료·등록 확인 | M1/M3/M4/M5는 작성자 성공 보고. M2는 일부 성공·IP 변경 가능으로 기술 검토 유지 |
| 전체 IP·연결 | 10/21 IP 배정, M1–M3 일반 라우팅 결정 | PL 통합 기술 검토·실제 양방향 통신 결과 확인 |
| WBS·계획서 | 10/21 제출 완료 | 기술 검토 결과에 따라 필요한 부분만 개정 |
| M4 기본망 | #29 댓글: UTM 설치·Windows 연결 성공 | 전체 서비스·VPN·백업 환경 완료는 미확인 |

토폴로지 등록 완료는 전체 망 기술 검증 완료를 뜻하지 않습니다. 세부 진행은 Issue의 최신 결과로 판단하며 미확인 작업을 미착수로 단정하지 않습니다. [10/21 회의록](meetings/2026-10-21-ip-and-routing.md)

## 1. 주요 일정·마감

| 기간 | 작업 | 마감·확인 |
|---|---|---|
| 10/20–10/21 목표 | AS-IS 네트워크 토폴로지 작성·등록 | #1~#5 등록 확인, PL 기술 검토는 별도 |
| 10/21–10/23 | 가상 장비·OS·기본 통신 구축, 자원·권한 확인 | 10/23 환경·공수 확인·기술 검토 반영 [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) |
| 10/26–10/28 | 기본 서비스·VPN·망 간 연결 | 10/28 기본망·시험 대상 준비 |
| 10/29–10/30 | M1·M2·M4 공격·분석, 게시판·OTT 배포 | 10/30 시험 기록·배포 확인·Store 최소 기능 점검 |
| 11/02 | M3·M5 공격·원인 분석 | 11/02 개선 요구 정리 |
| 11/03 | TO-BE(개선 후) 설계·검토 | 11/03 변경 토폴로지·정책 확정 |
| 11/04–11/05 | 보안 개선·이중화·배포 적용 | 11/05 구현 목표 |
| 11/06 | 망·앱·AI·CI/CD 통합 확인 | 11/06 통합·재시험 준비 |
| 11/09–11/10 | 재공격·정상 기능·장애·복원 시험 | 11/10 검증 결과 정리 |
| 11/11–11/12 | 오류 보완·보고서·발표자료 | 11/11 잔여 오류 검토, 11/12 자료 취합 |
| 11/13 | 전원 리허설·담당별 결과 정리 | 11/13 발표 준비 |
| 11/16 | 최종 발표 | 11/16 |

각 망 IP/NIC·자원이 확인된 구간부터 장비 생성·OS 설치를 진행합니다. M1–M3는 일반 라우팅, 나머지 VPN 구간은 기존 계획을 유지합니다. 공격 분석 후 TO-BE를 설계·적용하며, 개발은 인프라와 병행합니다.

## 2. 담당별 업무·Issue

| 담당·업무 | 설계·기본 구현 | 시험·연동 | 개선·통합 | 재검증·결과 |
|---|---|---|---|---|
| M1 유용수 | 토폴로지 등록 확인 [#1](https://github.com/team-blocks-lab/otter-shield/issues/1)<br>기본망 10/21–28 [#14](https://github.com/team-blocks-lab/otter-shield/issues/14) | 공격 10/29–30 [#15](https://github.com/team-blocks-lab/otter-shield/issues/15) | 설계·개선·통합 11/03–06 [#16](https://github.com/team-blocks-lab/otter-shield/issues/16) | 재검증 11/09–10 [#17](https://github.com/team-blocks-lab/otter-shield/issues/17)<br>결과 정리 11/11–13 [#18](https://github.com/team-blocks-lab/otter-shield/issues/18) |
| M2 윤서영 | 토폴로지 등록 확인 [#2](https://github.com/team-blocks-lab/otter-shield/issues/2)<br>기본망 10/21–28 [#19](https://github.com/team-blocks-lab/otter-shield/issues/19) | 공격 10/29–30 [#20](https://github.com/team-blocks-lab/otter-shield/issues/20) | 설계·개선·통합 11/03–06 [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) | 재검증 11/09–10 [#22](https://github.com/team-blocks-lab/otter-shield/issues/22)<br>결과 정리 11/11–13 [#23](https://github.com/team-blocks-lab/otter-shield/issues/23) |
| M3 홍은서(PL) | 토폴로지 등록 확인 [#3](https://github.com/team-blocks-lab/otter-shield/issues/3)<br>기본망 10/21–28 [#24](https://github.com/team-blocks-lab/otter-shield/issues/24) | 공격 11/02 [#25](https://github.com/team-blocks-lab/otter-shield/issues/25) | 설계·개선·통합 11/03–06 [#26](https://github.com/team-blocks-lab/otter-shield/issues/26) | 재검증 11/09–10 [#27](https://github.com/team-blocks-lab/otter-shield/issues/27)<br>결과 정리 11/11–13 [#28](https://github.com/team-blocks-lab/otter-shield/issues/28) |
| M4 박진혁 | 토폴로지 등록 확인 [#4](https://github.com/team-blocks-lab/otter-shield/issues/4)<br>기본망 10/21–28 [#29](https://github.com/team-blocks-lab/otter-shield/issues/29) | 공격 10/29–30 [#30](https://github.com/team-blocks-lab/otter-shield/issues/30) | 설계·개선·통합 11/03–06 [#31](https://github.com/team-blocks-lab/otter-shield/issues/31) | 재검증 11/09–10 [#32](https://github.com/team-blocks-lab/otter-shield/issues/32)<br>결과 정리 11/11–13 [#33](https://github.com/team-blocks-lab/otter-shield/issues/33) |
| M5 유은혜(PM)<br>인프라 | 토폴로지 등록 확인 [#5](https://github.com/team-blocks-lab/otter-shield/issues/5)<br>기본망 10/21–28 [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) | 공격 11/02 [#35](https://github.com/team-blocks-lab/otter-shield/issues/35) | 설계·개선·통합 11/03–06 [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) | 재검증 11/09–10 [#37](https://github.com/team-blocks-lab/otter-shield/issues/37)<br>결과 정리 11/11–13 [#38](https://github.com/team-blocks-lab/otter-shield/issues/38) |
| M5 유은혜(PM)<br>개발 | D1 실행 규격 10/21–23<br>D2 게시판 10/22–23<br>D3 OTT 10/24·26–28<br>[#8](https://github.com/team-blocks-lab/otter-shield/issues/8) | D4 게시판·OTT 배포 10/29–30<br>D5 Store·AWS 10/29–11/06<br>[#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) | D6 CI/CD 준비 10/28–30, 한국 11/04·Store 11/05<br>D7 AI 11/02–04<br>통합 11/06<br>[#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) | D8 기능·배포 복구 11/09–10<br>[#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |

- M5: 기본망 마감은 10/28, 개발·배포 마감은 11/06, 기능 재검증은 11/09–10입니다.
- 코드 개발은 M5, 서버 배포는 M1·M2(게시판), M3(OTT·AI), M5(Store)가 맡습니다.
- 개발 중간 목표: 10/22 ERD·클래스 다이어그램 초안 → 10/23 검토 → 10/28 OTT 로컬 기능 → 10/30 Store 최소 기능 → 10/31 Store 최초 배포 → 11/03 AI 자막 파일 → 11/04 웹 연동.

## 3. 공동·전문 업무

아래 업무는 담당별 작업과 연결되며 별도 중복 작업이 아닙니다.

| 담당 | 업무·주요 기한 | Issue |
|---|---|---|
| M5 유은혜(PM)·M3 홍은서(PL) / 각 망 확인 | 10/21 제출 완료·IP 배정·라우팅 결정, 10/22~23 PL 기술 검토·환경·공수 확인 | [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) |
| M1 유용수 주관·전원 | 10/22–23 연결 사전 확인 → 10/26–28 전체 연결·VPN | [#7](https://github.com/team-blocks-lab/otter-shield/issues/7) |
| M2 윤서영 | 10/26–28 Wazuh 준비 → 11/03 설계 → 11/04–05 적용 → 11/06 연동 확인 | [#9](https://github.com/team-blocks-lab/otter-shield/issues/9) · [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) |
| M4 박진혁·M3 홍은서 | 10/23 DB·복구 목표 합의 → 10/26–30 준비 → 11/04 초기 복원 → 11/05 오전 초기 복제 → 11/06 S3 복원 → 11/09–10 검증 | [#10](https://github.com/team-blocks-lab/otter-shield/issues/10) |
| M3 홍은서·M5 유은혜 | 11/02–03 장애 시험 준비 → 11/06·11/09–10 장애·복구 시험 | [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) |
| M5 유은혜·M3 홍은서·M1 유용수 | 10/23 AWS 권한·예산·API 경로 확인 → 11/06 AWS·Store 연동 → 11/09–10 RDS 복원 | [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |
| M3 홍은서(적용)·M5 유은혜(시험) | 11/03 S05 개선 설계 → 11/04 정책 적용 → 11/06 통합 확인 | [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) |
| 전원 / M5 유은혜(PM) 취합·M3 홍은서(PL) 검토 | 11/11–12 보고서·발표자료 → 11/13 리허설 → 11/16 발표 | [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) |

공동 작업 시간: 11/04 오후 M3·M5 한국 CD·AI 배포, 11/05 오전 M3·M4 DB 복제, 11/05 오후 M3 Nginx·VIP 구성. 준비 상태·예상 공수는 10/23·10/30에 [#6](https://github.com/team-blocks-lab/otter-shield/issues/6)에서 점검합니다.

## 인계 조건·집중 구간 관리

| WBS ID | 시작·인계 조건 | 확인 시점 |
|---|---|---|
| C6.1 → I14/I19/I24/I29/I34 | 해당 망 IP/NIC·자원 확인 후 독립 구간부터 착수. C6.1 전체 종료를 기다리지 않음 | 10/22~23 |
| D1 → D2 | 게시판 API·DB·실행 조건 확인 후 병행 | 10/23 |
| I14/I19/I24/I29/I34 → C7 | 대표 장비와 해당 경로부터 부분 검증. 전체 서비스 완료 조건은 별도 | 대표 10/22~23·전체 10/28 |
| D3 → D6.1 | 빌드 가능한 코드부터 CI 준비 병행 | 10/28~30 |
| I26.2·D7 → D6.2 | 11/04 오전 정책·자막/API 인계 후 오후 배포. 최종 재생은 C8 | 11/04·11/06 |
| I26.1 → I26.3 | 기술 선행은 설계 확인. DB 협업 후 VIP 순서는 M3의 시간 제약 | 11/05 |
| I18/I23/I28/I33/I38 → C13.1 | 검토된 자료부터 순차 취합하고 11/12 전 전원 자료 대조 | 11/11~12 |

M5의 기본망·개발·AWS·PM 업무와 M3의 11/04~05 정책·배포·DB·VIP 작업은 공수 확인이 필요합니다. 기존 담당·목표일을 유지하되 다음 기준으로 점검합니다.

- **10/23:** 설치·설정·테스트·오류 대응의 남은 예상시간과 가용시간 제출. 값이 없으면 미확인으로 유지.
- **10/28:** D3 OTT 로컬 기능·D6.1 CI 준비·배포 인계 가능 여부 확인.
- **10/30:** D4 배포·D5.1 Store 최소 기능·C12.2 AWS 준비와 M3/M4 DB 인계 확인.
- 미달이면 해당 Issue와 #6에 영향·새 예상 완료일·지원/범위 조정안을 남기고 PM/PL이 조정합니다. 새 기능보다 필수 기능 연결·오류 수정을 우선하며 앱 개발 담당은 M5로 유지합니다.

D1~D8 및 세부 ID별 상태·결과 링크는 #8, AWS 세부 작업은 #12에서 기록합니다. 같은 작업을 여러 Issue에 중복 수행하지 않고 동일 증거를 연결합니다.

## 4. 진행 기록·일정 변경

- 매일: WBS 확인 → Notion 기술 기록 → 작업한 Issue에 결과·막힌 점·다음 작업 댓글 → 업무 보드 갱신.
- 지연 예상 시: 해당 Issue에 영향·예상 완료일을 남기고 PM·관련 담당과 조정합니다. 합의 후 WBS를 변경하며, 미수행 작업은 완료로 표시하지 않습니다.
- 계획서 PDF는 10/21 제출·등록했습니다. PL 기술 검토에서 오류가 확인되면 개정 이력을 남깁니다. 상세 환경·위험·완료 조건은 [#6](https://github.com/team-blocks-lab/otter-shield/issues/6)과 각 작업 Issue, 설계 결정은 [회의록](meetings/2026-10-20-design-decisions.md)에서 확인합니다.

<details>
<summary>계획 변경 이력</summary>

- 10/22 · 용어·Issue/Excel 작업명 통일, 등록 상태와 PL 기술 검토 분리, 일반 라우팅·제출 완료 반영, 부분 착수·공수 점검 기준 보완. 기존 역할·목표일 유지.
- 10/20 · AS-IS 토폴로지: 기존 10/20 → 10/21 오전 완료 예상(팀 확인 전). 실제 환경 검토로 조정, 10/21 구축 착수 목표 유지.
- 10/20 · 기존 Issue에 필수 구축·공동 책임·AWS 재생성 및 종료 확인 업무 보완. 단계별 일정 유지.
- 10/20 · 집중 업무 분산: CI 준비 10/28–30, AI 파일 11/03·웹 11/04, 한국 CD 11/04·Store CD 11/05, DB 협업 11/05 오전. 통합 11/06·재시험 11/09–10 유지.

</details>
