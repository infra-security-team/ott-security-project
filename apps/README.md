# OTTer Shield | 개발 코드 안내

팀명 Team Blocks · 보안 컨설팅 회사 NetBlocks · 가상 OTT 고객사 OTTer

프로젝트명: OTTer Shield — 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅

세 웹 서비스의 코드를 배포 대상별로 구분합니다. 모든 앱 코드 개발은 M5 유은혜가 담당하며, M1·M3·M5 표기는 개발자가 아닌 배포 대상입니다.

| 서비스 | 폴더 | 포함할 코드 | 배포 담당·범위 |
|---|---|---|---|
| M1·M2 사내 게시판 | [m1-intranet](m1-intranet/README.md) | 한국·독일 공통 게시판 앱 | M1 한국·M2 독일 배포, M5 개발·연동 지원 |
| M3 OTT 메인 | [m3-ott](m3-ott/README.md) | React·Spring Boot·FastAPI/AI | M3 한국 앱·DB 배포, M5 코드·AWS 정적 웹 |
| M5 Store | [m5-store](m5-store/README.md) | Store React·Spring Boot | M5 캐나다 AWS/EKS 배포 |

게시판 코드는 기존 `m1-intranet` 폴더를 M1·M2가 공유합니다. 독일용 앱 사본은 만들지 않으며, 국가별 DB·계정·환경변수·DNS를 분리합니다. 폴더 이름의 M1은 기존 경로를 유지한 것입니다.

## 내려받은 뒤 확인할 위치

1. 저장소 첫 화면의 Code → Download ZIP으로 전체 파일을 내려받습니다.
2. 압축 해제 후 `otter-shield-main/apps` 폴더에서 배포할 서비스 폴더를 선택합니다.
3. 그 서비스의 README에서 필요한 구성 요소와 실행 방법을 확인합니다.
4. 현재는 안내 문서만 있으며, 실행 코드는 아직 등록되지 않았습니다. 빈 폴더를 실행 가능한 앱으로 판단하지 않습니다.

OTT의 `frontend/`, `backend/`, `ai-service/`는 `apps/m3-ott/` 아래에서 확인합니다.

## 코드 등록·배포 시 기록할 내용

서비스별 README에 실제 버전, 실행·빌드 명령, 환경변수 이름, DB 준비, 검증된 커밋·이미지 버전을 기록합니다. 비밀값은 등록하지 않습니다.

M3·M5는 GitHub Actions + Argo CD 배포 계획을 사용합니다. CI 경로 조건·빌드 위치와 Argo CD 대상 앱을 서비스별로 분리하여, Store 변경이 한국 OTT 배포를 잘못 실행하지 않도록 설정·시험합니다. S3 정적 React 배포는 Kubernetes 배포와 구분합니다. M1·M2 게시판의 배포 방식은 앱 실행 환경을 확인한 뒤 정합니다.

## 인계 기준

실제 버전·빌드/실행 명령·DB 스키마/가짜 초기 데이터·환경변수 이름·건강 확인 경로·커밋/이미지·되돌리기 절차를 서비스 README에 채운 뒤 상대 배포 담당이 확인합니다. 10/23까지 게시판 실행 방식·이미지 저장소·Git/이미지 출구·승인 관리 경로를 결정합니다.

[프로젝트 첫 화면](../README.md)
