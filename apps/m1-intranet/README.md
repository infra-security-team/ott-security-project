# M1·M2 | 한국·독일 공통 사내 게시판 웹

개발: M5 유은혜 · 배포: M1 유용수 / M2 윤서영

## 사용 환경

| 항목 | 기준 |
|---|---|
| OS | Rocky Linux — 세부 버전은 서버 구축 시 기록 |
| Java | **21** — 개발 PC는 Temurin JDK 21 |
| Spring Boot | **4.1.1** — 생성한 프로젝트 기준 |
| DB 접근 | Spring Data JPA |
| DB | **MySQL** — 세부 버전 미정 |
| 화면 | React — 버전은 프론트 프로젝트 생성 후 기록 |
| 웹 서버 | Nginx |
| 백엔드 전달 형식 | 실행 가능한 Jar 기준, 최종 배포 방식은 인계 시 기록 |
| 로그인 | 게시판 전용 세션. OTT·Store 세션과 분리 |

한국·독일은 같은 코드를 사용하며 DB·계정·DNS·사진 저장 경로를 각각 분리합니다.

## 설치·준비 대상

| 서버 역할 | 필요한 프로그램·파일 |
|---|---|
| 웹 | Nginx, React 빌드 결과물 |
| 앱 | Java 21, 게시판 Jar |
| DB | MySQL, DB 생성 SQL·초기 직원 계정 데이터 |

배포만 하는 서버에는 IntelliJ가 필요하지 않습니다. React 빌드 결과물을 받는 경우 Node.js도 필요하지 않습니다. Spring Boot·JPA·MySQL Driver는 앱 의존성에 포함됩니다.

## 포트

| 구간 | 기준 포트 |
|---|---|
| 직원 브라우저 → 웹 | HTTP 80 / HTTPS 443 |
| 웹 → Spring Boot | TCP 8080 |
| Spring Boot → MySQL | TCP 3306 |

## 환경변수

| 환경변수 | 설정값 |
|---|---|
| `SERVER_PORT` | `8080` |
| `SPRING_DATASOURCE_URL` | `jdbc:mysql://<DB주소>:3306/<DB명>` |
| `SPRING_DATASOURCE_USERNAME` | 서비스 전용 DB 계정 |
| `SPRING_DATASOURCE_PASSWORD` | DB 비밀번호 — 저장소에 등록하지 않음 |

DB 주소·DB명·계정은 M1·M2에서 각각 지정합니다. 사진 저장 경로·허용 프론트 주소 관련 설정은 코드 작성 시 추가합니다.

## 전달 예정

현재 실행 코드 등록 전입니다. 위 포트·환경변수는 구현 기준이며 아직 실행 검증 전입니다. DB 생성 SQL·정확한 파일명·실행 명령·사진 저장 설정은 코드와 함께 추가합니다.

## 설계 자료

[사내 게시판 ERD](../../design/erd/intranet/README.md) · [사내 게시판 클래스 다이어그램](../../design/classdiagram/intranet/README.md)

[서비스별 코드 안내](../README.md) · [프로젝트 첫 화면](../../README.md)
