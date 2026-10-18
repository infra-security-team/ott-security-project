# OTT 인프라·보안 팀 프로젝트

**상태:** 팀 검토 및 설계 준비 · **발표:** 2026-11-16 · WBS 수정 검토안

## 팀원 첫 시작 및 매일 작업 순서

| 순서 | 위치 | 할 일 |
|---|---|---|
| 1 | [WBS](WBS.md) | 자기 업무명·기간·Issue와 선행 작업 확인 |
| 2 | [Projects 보드](https://github.com/orgs/infra-security-team/projects/4) | Status 변경: Todo / In progress / Blocked / In review / Done |
| 3 | [Notion 팀 기술서 양식](https://app.notion.com/p/3fd1b198732a81cf9c44fb58dfcb8567?pvs=204) | 한 번 복제 → 이름을 'M1 유용수 — 본사 네트워크 구축·보안 기록' 형식으로 수정 → 팀/PM과 공유 → 첫 Issue의 '개인 Notion 기술서'에 링크 입력. 같은 페이지에 이후 기록 누적 |
| 4 | 자기 Issue | 완료한 체크박스만 체크. 퇴근 전 '오늘 한 일 / Notion 링크 / 막힌 점 / 다음 작업' 댓글 |
| 5 | 검토자 및 PM | 관련 담당·PL이 기술 결과를 검토; PM은 일정/지원 점검. 검토 후 Close 및 Projects Done 확인 |

**관리 기준:** WBS는 계획과 마감일, Projects Status는 최신 진행 상황, Issue는 작업·일일 기록·검토 링크, Notion은 인프라/보안 설정과 시험 근거. 본문에 남아 있는 옛 '상태: 할 일'은 진행 상태 기준으로 사용하지 않음.

**공동 의사결정:** **10/19 AS-IS 도면·장비 목록 작성(설치 완료 요구 없음)** → **10/20 AS-IS 도면 검토·보안정책·TO-BE 방향 초안 합의** → 10/21~23 기본 환경 준비/구축 착수 및 10/23 기준선 재검토 → 11/02 시험 결과 공유 → 11/03 오전 TO-BE 최종 적용안 확정. [WBS](WBS.md) 및 [공동 Issue #6](https://github.com/infra-security-team/ott-security-project/issues/6) 참고. 날짜는 팀 검토 예정안.

## 프로젝트 자료

| 자료 | 위치 | 내용 |
|---|---|---|
| 현재 계획서 | [v0.2 PDF](plans/project-plan-v0.2.pdf) | 팀 검토안. 확정본 아님 |
| 이전 계획서 | [v0.1 PDF](plans/project-plan-v0.1.pdf) | 변경 전 자료 |
| WBS | [WBS](WBS.md) | 공동 설계 검토·업무명·기간·Issue |
| Projects | [팀 업무 보드](https://github.com/orgs/infra-security-team/projects/4) | 현재 상태와 담당자 |
| 회의록 | [meetings](meetings/README.md) | 실제 회의 내용과 결정 |
| 계획 설계 | [design](design/README.md) | 전체 구성도, Class Diagram, ERD 등의 팀 합의 자료 |
| **망별 설치·장비 안내** | **[network-guides](design/network-guides/README.md)** | **M1~M5 장비·서버·PC·VPN/DHCP/NAT·AWS 배치, draw.io 도면/막힘 해결 안내** |
| 앱 코드 | [frontend](frontend/README.md) · [backend](backend/README.md) · [ai-service](ai-service/README.md) | M5 개발, M3 등 연동 팀원이 내려받을 원본 |
| 팀 Notion 템플릿 | [개인별 인프라·보안 기록서 복제하기](https://app.notion.com/p/3fd1b198732a81cf9c44fb58dfcb8567?pvs=204) | 팀원마다 한 번 복제해 본인 페이지에 구축·설정·검증 내용을 기록 |

## 10/19 설계도 준비 완료 기준

- 개인 담당 망의 draw.io AS-IS 논리도 + VM/서버/클라이언트/클라우드 목록 초안
- 정상 통신·보안 시험 출발지/대상 및 본사 VPN 허브 연결 요청 정리
- 확정되지 않은 IP·장비·AWS 자원은 **미확정**으로 표시하고 10/20 회의 질문 목록 작성
- 도면 원본(`.drawio`)과 PNG를 개인 Notion에 기록, 팀 합의된 구조는 design에 연결
- 10/19는 **망 실제 구축 완료를 요구하지 않음**, 실습·검증 결과를 만들어 쓰지 않음

## 매일 Issue 댓글 예시

```text
날짜: 10/19
진행: 캐나다 직원망 주소 설계 초안 작성. VPN 상대 주소는 M1 확인 대기.
Notion 기록: [내 기술서의 해당 부분 링크]
막힌 점: 본사 VPN 대역 미확정
다음 작업: M1과 대역 확정 후 구성도 수정
```

PM은 각 댓글에 `확인: 일정·기록 확인 / 지원 사항: ...`처럼 답합니다. **PM 확인은 기술 시험 통과 판정이 아닙니다.**

### 기록할 때

- Issue 체크는 실제 완료 항목만. 아직 안 한 것은 `미수행`, 정하지 않은 것은 `미확정`.
- Notion 링크는 팀원이 열 수 있는 공유 권한 확인. 공개 템플릿과 개인 기술서의 공개 범위는 따로 확인.
- 공개 GitHub와 공개 Notion에 비밀번호, API 키, VPN PSK, 개인키, 실제 개인정보를 쓰지 않음.
- 인프라·보안 명령과 코드도 Notion 기술서에 기록하고, 마지막에 코드 포함 최종 문서로 취합.
- 개발 중인 앱 코드는 GitHub 세 폴더에서 관리. Issue에는 해당 코드 변경 링크만 간단히 연결.

### 첫 작업 바로가기

| 담당 | 첫 Issue |
|---|---|
| 유용수 | [#1 · 본사 네트워크](https://github.com/infra-security-team/ott-security-project/issues/1) |
| 윤서영 | [#2 · 보안·로그](https://github.com/infra-security-team/ott-security-project/issues/2) |
| 홍은서 | [#3 · 서비스망·서버](https://github.com/infra-security-team/ott-security-project/issues/3) |
| 박진혁 | [#4 · 백업·복원](https://github.com/infra-security-team/ott-security-project/issues/4) |
| 유은혜 | [#5 · 캐나다망·앱](https://github.com/infra-security-team/ott-security-project/issues/5) |

첫 Issue가 끝나면 WBS에서 다음 단계의 Issue 번호를 클릭합니다.
