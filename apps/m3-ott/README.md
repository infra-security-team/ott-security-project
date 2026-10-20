# M3 | OTT 메인 웹·AI

**팀명 Team Blocks · 보안 컨설팅 회사 NetBlocks · 가상 OTT 고객사 OTTer**

**프로젝트명:** OTTer Shield — 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅

**상태: 실행 코드 등록 전 · 코드 개발: M5 유은혜 · 한국 앱·DB 배포: M3 홍은서 · AWS 정적 웹 배포: M5**

| 구성 | 코드 위치 | 실행·배포 대상 |
|---|---|---|
| OTT React 화면 | [frontend](frontend/README.md) | AWS S3·CloudFront |
| Spring Boot API | [backend](backend/README.md) | M3 한국 Kubernetes·MySQL 연동 |
| FastAPI·AI 자막 | [ai-service](ai-service/README.md) | M3 앱 환경·STT/LLM 연동 |

M3 담당자는 한국 앱·AI 연동에 필요한 백엔드와 AI 코드를 확인합니다. OTT React 정적 화면은 M5가 AWS에 배포합니다. 사내 게시판과 Store 코드는 각각 별도 서비스 폴더를 사용합니다.

## 배포·검증 계획

GitHub Actions에서 빌드·검사·이미지 저장 후 배포 설정을 갱신하고, M3 기존 Kubernetes 내부 Argo CD가 이를 반영합니다. React 정적 빌드는 S3 배포 경로를 사용합니다. 현재 파이프라인 구현 완료를 뜻하지 않습니다.

실행 코드 등록 후 실제 빌드·실행 명령, 환경변수 이름, DB 준비, 로그인·목록·영상·자막 통합 결과와 복구 절차를 기록합니다.

[서비스별 코드 안내](../README.md) · [프로젝트 첫 화면](../../README.md)

**S05 연계:** Nginx가 HTTPS를 종료하고 내부 HTTP API 요청을 APP Suricata 경유로 전달합니다. [시험 API·규칙·증거 계약](../../design/scenarios/s05-web-ips.md)을 먼저 확인합니다.
