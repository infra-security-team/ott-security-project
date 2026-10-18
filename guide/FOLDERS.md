# 폴더와 파일 위치

**먼저 파일 종류 결정:** 개인 실습의 자세한 기록 → Notion. 팀이 재사용할 설정·코드 → 담당 GitHub 폴더. 팀이 함께 확인할 설계·시험 결과 → `docs/`.

## 저장소 첫 화면의 폴더

| 위치 | 내용 | 예 |
|---|---|---|
| [guide](README.md) | 사용 안내와 작성 예시 | 시작 순서, 매일 기록법 |
| [docs](../docs/README.md) | 계획·역할·공통 설계·보안·시험·보고 자료 | 일정표, 구성도, 시험 결과표 |
| [infrastructure](../infrastructure/README.md) | 실제 구축에 쓰는 네트워크·서버·백업 설정 | 방화벽 규칙, 백업 스크립트 |
| [frontend](../frontend/README.md) | OTT 웹 화면 코드 | React 프로젝트 |
| [backend](../backend/README.md) | 서비스 API 코드 | Spring Boot 프로젝트 |
| [ai-service](../ai-service/README.md) | AI 기능 코드 | FastAPI 프로젝트 |
| `.github` | GitHub가 작업·변경 요청 화면에 표시하는 양식 | 새 작업·보안 시험 양식 |

## 개인 담당 폴더

| 담당 | 실제 파일 저장 위치 | 파일 예 |
|---|---|---|
| 유용수 | [본사 네트워크](../infrastructure/m1-hq-network/README.md) | 주소·VPN·라우터 설정 |
| 윤서영 | [보안·기록](../infrastructure/m2-hq-security/README.md) | 탐지·로그 수집 설정 |
| 홍은서 | [서비스 서버](../infrastructure/m3-service/README.md) | 배포·DB 실행 설정 |
| 박진혁 | [백업·복원](../infrastructure/m4-backup-dr/README.md) | 백업 스크립트·복원 절차 |
| 유은혜 | [캐나다망](../infrastructure/m5-canada/README.md) 및 위 앱 폴더 | 지사 VPN 설정·화면·API 코드 |

**작성 예:** S01 개선 전 시험 → `docs/04-security/s01-m1-assessment.md`. 같은 시험의 개선안 → `s01-m1-remediation.md`. 재시험 → `s01-m1-validation.md`. 문서 안에는 담당·관련 작업 번호·시험 환경·관찰 결과·Notion 상세 구간 링크.

폴더는 실제 자료가 생길 때 사용. 아직 실행 전이면 “계획”, 시험 전이면 “미수행” 표시. DB 백업 데이터·VM 이미지·비밀번호·개인키·실제 개인정보는 공개 저장소 밖의 승인된 장소에 보관.
