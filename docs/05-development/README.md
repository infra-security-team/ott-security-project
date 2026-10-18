# 05 · 앱 연결 설계

**설계 자료:** React 웹 화면 → Spring Boot 서버 → MySQL 데이터베이스·FastAPI/AI 기능의 요청 흐름. **실제 코드:** 저장소 첫 화면의 [frontend](../../frontend/README.md), [backend](../../backend/README.md), [ai-service](../../ai-service/README.md).

| 파일 | 기록 내용 |
|---|---|
| [API 요청·응답](api-spec.md) | 화면과 서버 간 주소·입력·출력·권한·오류 |
| [DB 표 관계](erd.md) | 테이블·키·데이터 연결과 제약 |
| [주요 코드 구조](class-diagram.md) | 핵심 클래스와 책임. 실제 코드에 맞춰 작성 |

M5 앱 코드 담당, M3 서버·DB 실행 환경 담당. 양쪽 실행 조건은 [앱 실행 합의](../../infrastructure/m3-service/deployment/runtime-contract.md)에 기재. 아직 설계만 했다면 실제 연동 완료로 표시하지 않음.
