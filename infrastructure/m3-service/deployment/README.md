# 서비스 배포 연동 (M3 + M5)
- M5: React/Spring/FastAPI 코드·앱 환경변수 목록·API 계약 제공
- M3: 이미지 실행, Linux/MySQL 서버, 런타임 환경변수, LB/K8s 배포
- 공동: API·DB·LLM 통합 스모크 테스트, 보안 회귀 테스트

**비밀값은 서버·Secret Manager에서 별도 관리하며 저장소에 등록하지 않습니다.**

먼저 [앱 실행 계약](runtime-contract.md)을 M3·M5가 함께 채웁니다. 설정 값·명령을 추정하여 배포 완료로 표시하지 않습니다.
