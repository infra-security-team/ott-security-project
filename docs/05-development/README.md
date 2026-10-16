# 05 · 애플리케이션 설계 (M5)
- `class-diagram/`: Spring 도메인/서비스/컨트롤러의 핵심 클래스와 책임
- `erd/`: 실제 DB 테이블과 PK/FK·제약조건
- `api-spec/`: React↔Spring Boot↔FastAPI/LLM REST 연동·권한·오류 응답
- 실제 코드: 루트 `frontend/`, `backend/`, `ai-service/`

M5 코드 소유, M3 Linux/MySQL/K8s 운영 및 배포. 공유 API와 런타임 계약을 먼저 합의하고 M3·M5 공동 통합 검증합니다.
