# OTT 보안 프로젝트

가상의 한국·캐나다 OTT 회사 환경을 만들고, 보안 문제를 개선한 뒤 시험으로 확인하는 5인 교육 프로젝트입니다.

> 현재 문서 기준: 설계 준비 단계입니다. 실제 구축과 시험 결과는 아직 확인되지 않았습니다. 발표일은 **2026년 11월 16일**입니다.

## 처음 오셨나요?

먼저 **[팀 안내서](guide/README.md)**를 열어 주세요. 필요한 항목을 눌러 보면 됩니다. 모든 문서를 처음부터 읽을 필요는 없습니다.

| 팀원 | 맡은 영역 | 내 작업 |
|---|---|---|
| 유용수 | [본사 네트워크](docs/01-planning/team-roles/m1.md) | [작업 1](https://github.com/infra-security-team/ott-security-project/issues/1) |
| 윤서영 | [보안·기록 수집](docs/01-planning/team-roles/m2.md) | [작업 2](https://github.com/infra-security-team/ott-security-project/issues/2) |
| 홍은서 | [서비스 서버·데이터베이스 / PL](docs/01-planning/team-roles/m3.md) | [작업 3](https://github.com/infra-security-team/ott-security-project/issues/3) |
| 박진혁 | [백업·복원](docs/01-planning/team-roles/m4.md) | [작업 4](https://github.com/infra-security-team/ott-security-project/issues/4) |
| 유은혜 | [캐나다 지사·화면·AI 기능 / PM](docs/01-planning/team-roles/m5.md) | [작업 5](https://github.com/infra-security-team/ott-security-project/issues/5) |

## 매일 하는 일

1. 내 작업 페이지(Issue)에서 오늘 할 일과 마감일을 확인합니다.
2. 실습한 내용과 코드·설정·시험 결과를 팀 Notion에 기록합니다.
3. 작업 페이지에 진행 상태, 결과 링크, 막힌 점을 남깁니다. 실제 결과를 확인한 일만 완료로 표시합니다.

[팀 안내서](guide/README.md)에는 각 항목을 어디서 볼지 모아 두었습니다.

## 프로젝트 순서

보안 문제 정하기 → 개선 전 환경 만들기 → 문제가 있는지 시험하기 → 보완하기 → 같은 방법으로 다시 시험하기 → 결과를 보고하기

개선 전 환경과 개선 후 환경을 각각 **AS-IS(현재 상태)**, **TO-BE(개선 목표 상태)**라고 부릅니다. 시험은 팀이 승인한 실습 환경에서만 합니다.

## Notion과 GitHub는 무슨 차이인가요?

- **Notion:** 각자 실습한 상세 내용, 코드·설정 이유, 화면과 결과를 차근차근 기록합니다. 팀원 기록은 최종 보고서 작성에 활용합니다.
- **GitHub 파일:** 팀이 함께 쓸 코드·설정 파일과 최종적으로 확인한 결과를 보관합니다.
- **작업 페이지(Issue):** 누가 어떤 일을 하고 있는지, 현재 어디까지 했는지, 결과가 어디 있는지 알려 줍니다. 번호는 사람 번호가 아니라 작업 번호입니다.

비밀번호·접속 키·실제 개인정보는 올리지 않습니다. 백업 파일 자체도 공개 저장소에 올리지 않습니다.
