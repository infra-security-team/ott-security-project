# OTT 인프라·보안 팀 프로젝트
가상의 한국·캐나다 OTT 회사 환경을 만들고, 보안 문제를 개선한 뒤 실제 시험으로 확인하는 5인 교육 프로젝트입니다.

**현재 문서 기준: 설계 준비. 구축·시험 결과는 아직 미검증입니다. 발표일은 2026년 11월 16일입니다.**

## 처음 왔다면 내 이름부터 찾으세요
처음부터 모든 문서를 읽지 않아도 됩니다. **내 역할 안내 → 내 첫 작업** 순서로 엽니다.
Issue(이슈)는 버그만 뜻하지 않습니다. 여기서는 **해야 할 작업 한 건을 기록하는 페이지**입니다.

| 이름 | 맡은 일과 첫 행동 | 첫 작업 |
|---|---|---|
| 유용수 | [본사 네트워크](docs/01-planning/team-roles/m1.md) | [작업 #1](https://github.com/infra-security-team/ott-security-project/issues/1) |
| 윤서영 | [보안·로그 수집](docs/01-planning/team-roles/m2.md) | [작업 #2](https://github.com/infra-security-team/ott-security-project/issues/2) |
| 홍은서 | [서비스 서버·DB / PL](docs/01-planning/team-roles/m3.md) | [작업 #3](https://github.com/infra-security-team/ott-security-project/issues/3) |
| 박진혁 | [백업·복원](docs/01-planning/team-roles/m4.md) | [작업 #4](https://github.com/infra-security-team/ott-security-project/issues/4) |
| 유은혜 | [캐나다망·앱 개발 / PM](docs/01-planning/team-roles/m5.md) | [작업 #5](https://github.com/infra-security-team/ott-security-project/issues/5) |

## 매일 할 일은 세 가지
1. **확인:** 내 현재 Issue에서 오늘 할 항목과 필요한 정보를 확인합니다.
2. **작업·기록:** 실습하면서 Notion 개인 기술서에 설계·코드·설정·화면·결과를 기록합니다.
3. **공유:** Issue에 한 일, 자료 링크, 남은 일이나 필요한 도움을 남깁니다. 끝낸 항목만 체크합니다.

[첫날 따라 하기](docs/START_HERE.md) · [무엇을 어디에 쓰는지](docs/WORK_GUIDE.md) · [Notion 작성 양식](docs/templates/technical-detail-template.md)

## 전체 진행 순서
**시험할 보안 문제 정하기 → 개선 전 환경 만들기 → 문제 확인 → 개선하기 → 같은 시험과 정상 서비스 재확인 → 보고·발표**

개선 전 환경을 AS-IS, 개선 후 환경을 TO-BE라고 부릅니다. 실험은 팀이 승인한 격리 환경에서만 합니다.

## Notion과 GitHub의 차이
- **Notion:** 코드·설정·설명·시험 화면을 포함한 개인 상세 기술서. 다섯 명의 내용을 모아 최종 보고서를 만듭니다.
- **GitHub 파일:** 실제 사용할 코드·설정 파일, 공통 구성도와 공식 결과 요약. Notion 전체를 다시 복사하지 않습니다.
- **Issue:** 현재 상태와 위 자료의 링크. 번호는 사람 번호가 아니라 작업 번호입니다.

백업 파일을 만들었다고 복원까지 완료한 것은 아닙니다. 결과를 기록하고 검토받은 뒤 작업을 완료합니다.

<details>
<summary>전체 일정·계획서·폴더·PM/PL 자료 보기</summary>

- [계획서 PDF와 버전 안내](docs/01-planning/project-plan/README.md)
- [전체 작업 일정표(WBS)](docs/01-planning/wbs/README.md): 10/23 설계 → 10/30 개선 전 시험 → 11/06 개선·연결 → 11/11 검증 → 11/13 리허설. 중간 날짜는 10/19 팀 검토안입니다.
- [전체 폴더 안내](docs/FOLDER_GUIDE.md)
- [진행 단계의 완료 기준](docs/PROJECT_FLOW.md)
- [공용 Notion·계정 링크](docs/TEAM_LINKS.md)
- [월요일 설명 순서](docs/02-meetings/monday-orientation.md)
- [착수 전에 확인할 사항](docs/01-planning/readiness.md)
- [PM·PL 역할](docs/01-planning/team-roles/pm-pl.md)
- [문서 작성 기준](docs/DOCUMENTATION_GUIDE.md)
- [최종 보고·발표 준비](docs/07-reports/final-delivery.md)
- [포트폴리오 작성 가이드](docs/guides/README.md)
- [전체 작업 목록](https://github.com/infra-security-team/ott-security-project/issues)

현재 진행 상태는 Issue 본문에서 관리합니다. 별도 Projects 보드는 아직 구성하지 않았습니다.
</details>

비밀번호·토큰·VPN 키·실제 개인정보는 올리지 않습니다. 팀원마다 자기 영역을 구축·검증하고, PM은 일정과 막힘을 조율하며 PL은 기술 연결을 검토합니다.
