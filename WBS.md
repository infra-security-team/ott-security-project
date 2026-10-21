# OTTer Shield | WBS

Team Blocks · 2026.10.19–11.16 · 최종 발표 11/16

[업무 보드](https://github.com/orgs/team-blocks-lab/projects/4/views/2) · [팀 기술서](README.md#팀원별-기술서) · [댓글 작성 방법](README.md#issue-진행-댓글-작성) · [Topology](design/topology/README.md)

칠판 게시용 인쇄본: [A3 가로 2장 엑셀 WBS](plans/wbs/otter-shield-wbs-print-a3-2pages.xlsx) · 수행한 작업의 날짜 칸을 색칠해 진행 상황을 표시합니다.

담당 업무의 날짜를 확인한 뒤 Issue에서 세부 작업·완료 기준을 확인합니다. 아래 일정은 목표이며, 실제 진행 상태는 업무 보드와 Issue에서 관리합니다.

## 1. 주요 일정·마감

| 기간 | 업무 주제 | 마감·확인 |
|---|---|---|
| 10/20–10/21 오전 | AS-IS(개선 전) 도면 작성·연결 검토 | 10/21 오전 완료 예상·팀 확인 전 |
| 10/21–10/23 | 가상 장비·OS·기본 통신 구축, 자원·권한 확인 | 10/23 실행 환경 판정·개정 계획서 검토본 [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) |
| 10/26–10/28 | 기본 서비스·VPN·망 간 연결 | 10/28 기본망·시험 대상 준비 |
| 10/29–10/30 | M1·M2·M4 공격·분석, 게시판·OTT 배포 | 10/30 시험 기록·배포 확인·Store 최소 기능 점검 |
| 11/02 | M3·M5 공격·원인 분석 | 11/02 개선 요구 정리 |
| 11/03 | TO-BE(개선 후) 설계·검토 | 11/03 변경 도면·정책 확정 |
| 11/04–11/05 | 보안 개선·이중화·배포 적용 | 11/05 구현 목표 |
| 11/06 | 망·앱·AI·CI/CD 통합 확인 | 11/06 통합·재시험 준비 |
| 11/09–11/10 | 재공격·정상 기능·장애·복원 시험 | 11/10 검증 결과 정리 |
| 11/11–11/12 | 오류 보완·보고서·발표자료 | 11/11 잔여 오류 판정, 11/12 자료 취합 |
| 11/13 | 전원 리허설·담당별 결과 정리 | 11/13 발표 준비 |
| 11/16 | 최종 발표 | 11/16 |

10/21은 도면·연결 확인 후 장비 생성·OS 설치부터 시작합니다. 공격 분석 후 TO-BE를 설계·적용하며, 개발은 인프라와 병행합니다.

## 2. 담당별 업무·Issue

| 담당·업무 | 설계·기본 구현 | 시험·연동 | 개선·통합 | 재검증·결과 |
|---|---|---|---|---|
| M1 유용수 | 도면 10/21 오전 [#1](https://github.com/team-blocks-lab/otter-shield/issues/1)<br>기본망 10/21–28 [#14](https://github.com/team-blocks-lab/otter-shield/issues/14) | 공격 10/29–30 [#15](https://github.com/team-blocks-lab/otter-shield/issues/15) | 설계·개선·통합 11/03–06 [#16](https://github.com/team-blocks-lab/otter-shield/issues/16) | 재검증 11/09–10 [#17](https://github.com/team-blocks-lab/otter-shield/issues/17)<br>결과 정리 11/11–13 [#18](https://github.com/team-blocks-lab/otter-shield/issues/18) |
| M2 윤서영 | 도면 10/21 오전 [#2](https://github.com/team-blocks-lab/otter-shield/issues/2)<br>기본망 10/21–28 [#19](https://github.com/team-blocks-lab/otter-shield/issues/19) | 공격 10/29–30 [#20](https://github.com/team-blocks-lab/otter-shield/issues/20) | 설계·개선·통합 11/03–06 [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) | 재검증 11/09–10 [#22](https://github.com/team-blocks-lab/otter-shield/issues/22)<br>결과 정리 11/11–13 [#23](https://github.com/team-blocks-lab/otter-shield/issues/23) |
| M3 홍은서(PL) | 도면 10/21 오전 [#3](https://github.com/team-blocks-lab/otter-shield/issues/3)<br>기본망 10/21–28 [#24](https://github.com/team-blocks-lab/otter-shield/issues/24) | 공격 11/02 [#25](https://github.com/team-blocks-lab/otter-shield/issues/25) | 설계·개선·통합 11/03–06 [#26](https://github.com/team-blocks-lab/otter-shield/issues/26) | 재검증 11/09–10 [#27](https://github.com/team-blocks-lab/otter-shield/issues/27)<br>결과 정리 11/11–13 [#28](https://github.com/team-blocks-lab/otter-shield/issues/28) |
| M4 박진혁 | 도면 10/21 오전 [#4](https://github.com/team-blocks-lab/otter-shield/issues/4)<br>기본망 10/21–28 [#29](https://github.com/team-blocks-lab/otter-shield/issues/29) | 공격 10/29–30 [#30](https://github.com/team-blocks-lab/otter-shield/issues/30) | 설계·개선·통합 11/03–06 [#31](https://github.com/team-blocks-lab/otter-shield/issues/31) | 재검증 11/09–10 [#32](https://github.com/team-blocks-lab/otter-shield/issues/32)<br>결과 정리 11/11–13 [#33](https://github.com/team-blocks-lab/otter-shield/issues/33) |
| M5 유은혜(PM)<br>인프라 | 도면 10/21 오전 [#5](https://github.com/team-blocks-lab/otter-shield/issues/5)<br>기본망 10/21–28 [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) | 공격 11/02 [#35](https://github.com/team-blocks-lab/otter-shield/issues/35) | 설계·개선·통합 11/03–06 [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) | 재검증 11/09–10 [#37](https://github.com/team-blocks-lab/otter-shield/issues/37)<br>결과 정리 11/11–13 [#38](https://github.com/team-blocks-lab/otter-shield/issues/38) |
| M5 유은혜(PM)<br>개발 | D1 실행 규격 10/21–23<br>D2 게시판 10/22–23<br>D3 OTT 10/24·26–28<br>[#8](https://github.com/team-blocks-lab/otter-shield/issues/8) | D4 게시판·OTT 배포 10/29–30<br>D5 Store·AWS 10/29–11/06<br>[#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) | D6 CI/CD 준비 10/28–30, 한국 11/04·Store 11/05<br>D7 AI 11/02–04<br>통합 11/06<br>[#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) | D8 기능·배포 복구 11/09–10<br>[#8](https://github.com/team-blocks-lab/otter-shield/issues/8) · [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) · [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |

- M5: 기본망 마감은 10/28, 개발·배포 마감은 11/06, 기능 재검증은 11/09–10입니다.
- 코드 개발은 M5, 현지 배포는 M1·M2(게시판), M3(OTT·AI), M5(Store)가 맡습니다.
- 개발 중간 목표: 10/22 ERD·Class 초안 → 10/23 검토 → 10/28 OTT 로컬 기능 → 10/30 Store 최소 기능 → 10/31 Store 첫 배포 → 11/03 AI 자막 파일 → 11/04 웹 연동.

## 3. 공동·전문 업무

아래 업무는 담당별 작업과 연결되며 별도 중복 작업이 아닙니다.

| 담당 | 업무·주요 기한 | Issue |
|---|---|---|
| M5 유은혜(PM)·M3 홍은서(PL) / 각 망 확인 | 10/21–23 도면·환경·공수 확인, 10/23 개정 계획서 검토본 | [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) |
| M1 유용수 주관·전원 | 10/22–23 연결 사전 확인 → 10/26–28 전체 연결·VPN | [#7](https://github.com/team-blocks-lab/otter-shield/issues/7) |
| M2 윤서영 | 10/26–28 Wazuh 준비 → 11/03 설계 → 11/04–05 적용 → 11/06 연동 확인 | [#9](https://github.com/team-blocks-lab/otter-shield/issues/9) · [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) |
| M4 박진혁·M3 홍은서 | 10/23 DB·복구 목표 합의 → 10/26–30 준비 → 11/04 첫 복원 → 11/05 오전 첫 복제 → 11/06 S3 복원 → 11/09–10 검증 | [#10](https://github.com/team-blocks-lab/otter-shield/issues/10) |
| M3 홍은서·M5 유은혜 | 11/02–03 장애 시험 준비 → 11/06·11/09–10 장애·복구 시험 | [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) |
| M5 유은혜·M3 홍은서·M1 유용수 | 10/23 AWS 권한·예산·API 경로 확인 → 11/06 AWS·Store 연동 → 11/09–10 RDS 복원 | [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |
| M3 홍은서(적용)·M5 유은혜(시험) | 11/03 S05 개선 설계 → 11/04 정책 적용 → 11/06 통합 확인 | [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) |
| 전원 / M5 유은혜(PM) 취합·M3 홍은서(PL) 검토 | 11/11–12 보고서·발표자료 → 11/13 리허설 → 11/16 발표 | [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) |

공동 작업 시간: 11/04 오후 M3·M5 한국 CD·AI 배포, 11/05 오전 M3·M4 DB 복제, 11/05 오후 M3 Nginx·VIP 구성. 준비 상태·예상 공수는 10/23·10/30에 [#6](https://github.com/team-blocks-lab/otter-shield/issues/6)에서 점검합니다.

## 4. 진행 기록·일정 변경

- 매일: WBS 확인 → Notion 기술 기록 → 작업한 Issue에 결과·막힌 점·다음 작업 댓글 → 업무 보드 갱신.
- 지연 예상 시: 해당 Issue에 영향·예상 완료일을 남기고 PM·관련 담당과 조정합니다. 합의 후 WBS를 변경하며, 미수행 작업은 완료로 표시하지 않습니다.
- 계획서 PDF는 검토 후 공개합니다. 상세 환경·위험·완료 조건은 [#6](https://github.com/team-blocks-lab/otter-shield/issues/6)과 각 작업 Issue, 설계 결정은 [회의록](meetings/2026-10-20-design-decisions.md)에서 확인합니다.

<details>
<summary>계획 변경 이력</summary>

- 10/20 · AS-IS 도면: 기존 10/20 → 10/21 오전 완료 예상(팀 확인 전). 실제 환경 검토로 조정, 10/21 구축 착수 목표 유지.
- 10/20 · 기존 Issue에 필수 구축·공동 책임·AWS 재생성 및 종료 확인 업무 보완. 단계별 일정 유지.
- 10/20 · 집중 업무 분산: CI 준비 10/28–30, AI 파일 11/03·웹 11/04, 한국 CD 11/04·Store CD 11/05, DB 협업 11/05 오전. 통합 11/06·재시험 11/09–10 유지.

</details>
