# OTT 인프라·보안 프로젝트

가상의 한국·캐나다 OTT 서비스 환경을 대상으로 보안 문제를 확인하고 개선 결과를 시험하는 5인 팀 프로젝트.

**현재 상태:** 설계 준비. 실제 구축·시험 결과는 아직 미검증. **발표:** 2026-11-16.

## 바로가기

| 찾는 내용 | 위치 |
|---|---|
| 팀 작업 시작·작성 방법·용어 | [팀 안내](guide/README.md) |
| 전체 작업 일정과 담당별 작업 | [일정표](docs/01-planning/wbs.md) |
| 내가 할 작업과 진행 상황 | [전체 작업 목록](https://github.com/infra-security-team/ott-security-project/issues) |
| 계획·설계·보안·시험 자료 | [프로젝트 문서](docs/README.md) |

## 담당과 첫 작업

| 담당 | 영역 | 첫 작업 |
|---|---|---|
| 유용수 | [본사 네트워크](docs/01-planning/team-roles/m1.md) | [#1](https://github.com/infra-security-team/ott-security-project/issues/1) |
| 윤서영 | [보안·로그](docs/01-planning/team-roles/m2.md) | [#2](https://github.com/infra-security-team/ott-security-project/issues/2) |
| 홍은서 | [서비스 서버·DB / PL](docs/01-planning/team-roles/m3.md) | [#3](https://github.com/infra-security-team/ott-security-project/issues/3) |
| 박진혁 | [백업·복원](docs/01-planning/team-roles/m4.md) | [#4](https://github.com/infra-security-team/ott-security-project/issues/4) |
| 유은혜 | [캐나다망·앱 / PM](docs/01-planning/team-roles/m5.md) | [#5](https://github.com/infra-security-team/ott-security-project/issues/5) |

## 프로젝트 흐름

보안 문제·시험 조건 결정 → 개선 전 환경 구축 → 문제 재현 → 개선안·개선 환경 적용 → 같은 조건의 재시험 → 결과 보고

상세 순서와 단계별 확인 기준: [프로젝트 흐름](guide/FLOW.md).

## 기록 위치

| 위치 | 기록 내용 |
|---|---|
| **Notion 개인 기술서** | 설계 과정, 사용한 코드·설정과 이유, 오류·해결, 시험 화면과 결과 |
| **GitHub 파일** | 팀이 실제로 사용할 코드·설정 원본, 공통 설계와 시험 결과 요약 |
| **GitHub 작업 페이지(Issue)** | 담당·진행 상태, 완료 항목, Notion·파일·시험 결과 링크, 막힌 점 |

비밀번호·접속 키·실제 개인정보·DB 백업 파일은 공개 저장소에 등록하지 않음.
