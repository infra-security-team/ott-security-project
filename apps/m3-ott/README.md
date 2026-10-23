# M3 | OTT 메인 웹·AI

개발: M5 유은혜 · 한국 앱·DB 배포: M3 홍은서 · AWS 정적 웹 배포: M5

## 사용 환경

| 항목 | 기준 |
|---|---|
| OS | Rocky Linux — 세부 버전은 서버 구축 시 기록 |
| Java | **21** — 컨테이너 이미지 내부 런타임 |
| Spring Boot | **4.1.1 기준 개발 예정** |
| DB 접근 | Spring Data JPA |
| DB | **MySQL** — 세부 버전 미정 |
| 화면 | React — AWS S3·CloudFront 배포, 버전은 프로젝트 생성 후 기록 |
| API 배포 | M3 Kubernetes |
| 로그인 | OTT·Store 공통 Redis 세션 |
| CI/CD | GitHub Actions + Argo CD 계획 |

## 설치·준비 대상

| 대상 | 필요한 프로그램·파일 |
|---|---|
| Kubernetes 노드 | Kubernetes, 호환 컨테이너 런타임 |
| API | Java 21 포함 앱 컨테이너 이미지, 배포 매니페스트 |
| DB 서버 | MySQL, DB 생성 SQL·초기 데이터 |
| 공통 세션 | Redis — 버전·설치 위치·M3/Store 연결 경로 미정 |
| 프론트 | M5가 React 정적 빌드를 S3·CloudFront에 배포 |
| AI | FastAPI·STT/LLM 구성 예정 — Python 버전·이미지·포트 미정 |

노드에 앱 실행용 Java·IntelliJ를 별도로 설치할 필요는 없습니다. Java는 앱 이미지 안에 포함합니다. Kubernetes·런타임 버전은 인프라 담당자가 호환성을 맞춰 선정합니다.

## 포트

| 구간 | 기준 포트 |
|---|---|
| 사용자 → API 진입점 | HTTPS 443 |
| 내부 Service → Spring Boot 컨테이너 | TCP 8080 |
| Spring Boot → MySQL | TCP 3306 |
| OTT·Store → Redis | TCP 6379 |

Service·Ingress·NodePort 설정은 Kubernetes 구성에 맞춰 지정합니다. DB·Redis는 백엔드 접근용입니다.

## 환경변수

| 환경변수 | 설정값 |
|---|---|
| `SERVER_PORT` | `8080` |
| `SPRING_DATASOURCE_URL` | `jdbc:mysql://<DB주소>:3306/<DB명>` |
| `SPRING_DATASOURCE_USERNAME` | 서비스 전용 DB 계정 |
| `SPRING_DATASOURCE_PASSWORD` | DB 비밀번호 — 저장소에 등록하지 않음 |

| 추가 환경변수 | 설정값 |
|---|---|
| `SPRING_DATA_REDIS_HOST` | 공통 Redis 주소 |
| `SPRING_DATA_REDIS_PORT` | `6379` |
| `SPRING_DATA_REDIS_PASSWORD` | Redis 인증 구성에 따른 비밀번호 |
| `SPRING_SESSION_REDIS_NAMESPACE` | OTT·Store에서 동일한 값 — 값 미정 |
| `SERVER_SERVLET_SESSION_COOKIE_NAME` | OTT·Store 공통 쿠키 이름 — 값 미정 |
| `SERVER_SERVLET_SESSION_COOKIE_PATH` | `/` |
| `SERVER_SERVLET_SESSION_TIMEOUT` | OTT·Store 공통 만료 시간 — 값 미정 |

비밀번호는 Kubernetes Secret으로 주입하고 저장소에 등록하지 않습니다. Redis 직렬화·쿠키 보안·CDN·허용 프론트 주소 설정은 코드 인계 시 추가합니다.

## 코드 위치·전달 예정

| 구성 | 위치 |
|---|---|
| React | [frontend](frontend/README.md) |
| Spring Boot | [backend](backend/README.md) |
| FastAPI·AI | [ai-service](ai-service/README.md) |

현재 실행 코드·이미지 등록 전입니다. 위 포트·환경변수는 구현 기준이며 아직 실행 검증 전입니다. 이미지 레지스트리·태그·DB SQL·상태 확인 경로·배포 매니페스트는 코드와 함께 추가합니다.

## 설계 자료

[OTT 메인 ERD](../../design/erd/ott/README.md) · [OTT 메인 클래스 다이어그램](../../design/classdiagram/ott/README.md)

[서비스별 코드 안내](../README.md) · [프로젝트 첫 화면](../../README.md)
