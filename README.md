# OTT Infrastructure & Security Consulting
> 한국·캐나다 OTT 인프라 구축 및 보안 컨설팅 · 5인 / 4주 / 가상 고객사 격리 실습  
> **현재: 설계 준비.** 계획서 v0.2는 팀 검토안이며 실제 구축·보안 시험 완료를 뜻하지 않습니다. 프로젝트·고객사 명칭은 가칭입니다.

## 처음 왔다면 여기부터
**[① 시작 안내](docs/START_HERE.md) → 아래에서 내 역할 선택 → 내 시작 Issue 열기**

| 담당 | 역할·다음 작업 | 지금 시작할 Issue |
|---|---|---|
| M1 유용수 | [본사 네트워크](docs/01-planning/team-roles/m1.md) | [#1 · W1 설계 준비](https://github.com/infra-security-team/ott-security-project/issues/1) |
| M2 윤서영 | [본사 보안·중앙 관제](docs/01-planning/team-roles/m2.md) | [#2 · W1 설계 준비](https://github.com/infra-security-team/ott-security-project/issues/2) |
| M3 홍은서 | [한국 서비스 인프라 · PL](docs/01-planning/team-roles/m3.md) | [#3 · W1 설계 준비](https://github.com/infra-security-team/ott-security-project/issues/3) |
| M4 박진혁 | [백업·DR](docs/01-planning/team-roles/m4.md) | [#4 · W1 설계 준비](https://github.com/infra-security-team/ott-security-project/issues/4) |
| M5 유은혜 | [캐나다망·OTT/AI 개발 · PM](docs/01-planning/team-roles/m5.md) | [#5 · W1 설계 준비](https://github.com/infra-security-team/ott-security-project/issues/5) |

**매일:** 내 Issue의 다음 미체크 항목 확인 → 실습하며 Notion 기록 → 설정·공식 결과를 GitHub에 저장 → Issue에 결과 링크와 다음 행동 기록.  
**막히면:** 기다리지 말고 Issue에 `막힘 / 시도 / 필요한 도움`을 남깁니다. [작성 예시](docs/examples/README.md)

## 프로젝트 흐름
시나리오 설계 → AS-IS 구축·정상 기능 확인 → 공격 재현·증거 확보 → 개선안 작성 → TO-BE 적용 → 동일 조건 재시험·정상 기능 확인 → 결과보고·발표.

[단계별 시작·완료 기준](docs/PROJECT_FLOW.md) · [4주 WBS](docs/01-planning/wbs/README.md)  
보안 개선의 결과는 차단·탐지·정상 기능을 나누어 판정합니다. 공격 실패 한 번으로 전체 안전성을 단정하지 않습니다.

## 필요한 자료 바로 찾기
| 찾는 것 | 바로가기 |
|---|---|
| GitHub에서 어디를 눌러 작성하는지 | [실행·작성 가이드](docs/WORK_GUIDE.md) |
| 파일을 어디에 넣는지 | [전체 폴더 지도](docs/FOLDER_GUIDE.md) |
| 계획서 / 포트폴리오 안내 | [계획서 PDF](docs/01-planning/project-plan/README.md) / [별도 가이드](docs/guides/README.md) |
| Notion / 팀 계정 / 실제 일정 | [공용 링크 등록부](docs/TEAM_LINKS.md) |
| 월요일 설명 순서·확인 항목 | [오리엔테이션 진행안](docs/02-meetings/monday-orientation.md) |
| 문서 양식·작성 품질 | [템플릿](docs/templates/README.md) / [문서 표준](docs/DOCUMENTATION_GUIDE.md) |
| 설계 / 보안 / 테스트 / 최종보고 | [설계](docs/03-architecture/README.md) / [보안](docs/04-security/README.md) / [테스트](docs/06-testing/README.md) / [결과](docs/07-reports/README.md) |
| 코드·인프라 설정 | [인프라](infrastructure/README.md) / [React](frontend/README.md) / [Spring](backend/README.md) / [AI](ai-service/README.md) |

## 협업 원칙
- **Issue가 최신 작업 상태의 기준입니다.** WBS는 순서·담당·완료 기준을 정하는 계획표입니다. 별도 일일 보고표를 만들지 않습니다.
- 체크리스트는 작업자가 갱신합니다. 주요 산출물은 연동 담당자의 검토 후 완료 처리합니다. PM이 모든 기술 작업을 승인하는 구조가 아닙니다.
- M1~M5 모두 자기 영역의 설계·구축·보안 개선·검증을 담당합니다. M2는 공통 관제, M3는 기술 통합, M5는 일정 조율을 맡습니다.
- 앱 코드는 M5, 서버·DB 실행 환경과 배포는 M3가 담당합니다. 통합 검증은 함께 수행합니다.
- 비밀번호·VPN 키·API 키·실제 개인정보는 저장소에 올리지 않습니다. 취약 환경은 승인된 격리 랩에서만 운영합니다.
- GitHub Projects 보드는 아직 구성하지 않았습니다. 현재는 아래 Issue 목록과 본문 상태만 사용합니다.

[전체 열린 작업](https://github.com/infra-security-team/ott-security-project/issues) · [공통 착수 준비 #6](https://github.com/infra-security-team/ott-security-project/issues/6) · [기존 킥오프 기록](docs/02-meetings/2026-10-16-kickoff.md)
