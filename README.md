# OTT 인프라·보안 팀 프로젝트

**상태:** 팀 검토 및 설계 준비 · **발표:** 2026-11-16

## 팀 작업 경로

| 순서 | 열 곳 | 확인·작성 내용 |
|---|---|---|
| 1 | [WBS](WBS.md) | 이번 주 목표·담당·기한, 해당 Issue 번호 확인 |
| 2 | [내 Issue](https://github.com/infra-security-team/ott-security-project/issues) | 오늘 할 작업과 완료 기준 확인 |
| 3 | 개인 Notion 기술서 | 설계, 실습 과정, 명령어·설정 코드, 오류, 보안 시험, 화면과 결과 기록 |
| 4 | 같은 Issue | 퇴근 전 진행 요약·Notion 링크·막힌 점·다음 작업 댓글 작성 |
| 5 | PM 확인 | 매일 기록·일정·지원 요청 확인. 기술 결과는 PL·연동 담당자와 검토 |

**한 줄 규칙:** WBS는 일정, Issue는 진행 현황, Notion은 실제 기술세부내역서.
매일 WBS를 수정하거나 GitHub에 인프라·보안 설정 파일을 만들 필요 없음.

## 프로젝트 자료

| 자료 | 위치 | 내용 |
|---|---|---|
| 현재 계획서 | [v0.2 PDF](plans/project-plan-v0.2.pdf) | 팀 검토안. 확정본 아님 |
| 이전 계획서 | [v0.1 PDF](plans/project-plan-v0.1.pdf) | 변경 전 자료 |
| WBS | [WBS](WBS.md) | 주차·담당·작업 번호 |
| 회의록 | [meetings](meetings/README.md) | 실제 회의 내용과 결정 |
| 계획 설계 | [design](design/README.md) | 전체 구성도, Class Diagram, ERD 등의 팀 합의 자료 |
| 앱 코드 | [frontend](frontend/README.md) · [backend](backend/README.md) · [ai-service](ai-service/README.md) | M5 개발, M3 등 연동 팀원이 내려받을 원본 |
| 팀 Notion 템플릿 | **링크 등록 대기** | PM이 공개 템플릿을 만든 뒤 실제 접근 확인 후 연결 |

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

## 담당

| 담당 | 주요 범위 | 첫 Issue |
|---|---|---|
| M1 유용수 | 본사 네트워크·VPN | [#1](https://github.com/infra-security-team/ott-security-project/issues/1) |
| M2 윤서영 | 보안·로그·관제 | [#2](https://github.com/infra-security-team/ott-security-project/issues/2) |
| M3 홍은서(PL) | 서비스망·서버·앱 배포 | [#3](https://github.com/infra-security-team/ott-security-project/issues/3) |
| M4 박진혁 | 백업·복원·DR | [#4](https://github.com/infra-security-team/ott-security-project/issues/4) |
| M5 유은혜(PM) | 캐나다망·OTT/AI 앱 개발 | [#5](https://github.com/infra-security-team/ott-security-project/issues/5) |

세부 역할과 일정은 계획서와 WBS의 팀 검토안 기준. 확정·변경 사항은 회의록에 기록.
