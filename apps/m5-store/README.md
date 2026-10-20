# M5 | Store 웹

**팀명 Team Blocks · 보안 컨설팅 회사 NetBlocks · 가상 OTT 고객사 OTTer**

**프로젝트명:** OTTer Shield — 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅

**상태: 실행 코드 등록 전 · 코드 개발·AWS 배포: M5 유은혜**

캐나다 고객용 Store 코드를 이 폴더에 등록합니다. OTT 메인과 별도의 앱으로 구분하며, 캐나다 사내 업무망과도 구분합니다.

| 구성 | 코드 위치 | 실행·배포 대상 |
|---|---|---|
| Store React 화면 | [frontend](frontend/README.md) | 캐나다 EKS |
| Store Spring Boot API | [backend](backend/README.md) | 캐나다 EKS·비공개 RDS 연동 |

GitHub Actions에서 빌드·검사·이미지 저장 후 배포 설정을 갱신하고, 기존 EKS 내부 Argo CD가 반영하는 계획입니다. 고객은 공개 ALB로 접속하며 사내 VPN을 사용하지 않습니다.

실행 코드 등록 후 실제 버전·명령어·환경변수 이름·DB 준비·상품 조회·모의 주문·접근 권한·배포 결과를 기록합니다. 현재 코드나 CI/CD가 구현 완료된 상태는 아닙니다.

[서비스별 코드 안내](../README.md) · [프로젝트 첫 화면](../../README.md)

**복구 검증:** [AWS 연결 #12](https://github.com/team-blocks-lab/otter-shield/issues/12)에서 11/09–11/10 RDS 백업/스냅샷을 별도 DB로 복원하고 데이터를 확인합니다. 임시 복원 리소스의 비용·정리도 기록합니다. S05는 한국 격리 Test DB 접근 시험이며 Store RDS와 구분합니다.
