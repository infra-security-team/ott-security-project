# OTT 인프라·보안 프로젝트 WBS · 2026-10-19~11-16
[프로젝트 첫 화면](README.md) · [팀 검토 계획서](plans/project-plan-v0.2.pdf)


## 전체 일정
| 기간 | 목표 | 검토 시점·결과 |
|---|---|---|
| W1 · 10/19~23 | 망·보안 시험·앱 연동 설계, 개발 골격 | 10/21 ERD·Class Diagram·API 초안, 10/23 주소·통신·배포 기준선과 React/Spring/DB 기본 실행 |
| W2 · 10/26~30 | AS-IS 4망 연결, OTT 최소 기능 개발·배포, 공격 재현 시작 | 10/28 망별 정상 경로와 앱 로컬 로그인·목록·샘플 재생, 10/30 배포 기본 경로와 공격 3건 이상 |
| W3 · 11/02~06 | 11/02 공격 5건 마감, TO-BE 적용, AI·관제·복원·AWS 통합 | 11/06 개선 구성, 실제 생성 한영 자막·재생, 중앙 로그·S3 복원 1차 및 첫 통합 시험 |
| W4 · 11/09~13 | 동일 조건 검증·보고·리허설 | 11/10 보안·복원·앱 장애 시험, 11/11 증거 마감, 11/12 보고서·발표자료, 11/13 리허설 |
| 11/14~15 | 선택 완충 기간 | 필수 작업·주말 근무를 전제로 배치하지 않음 |
| 11/16 | 발표 | 사전 점검·발표. 신규 핵심 구축 배치 금지 |

## 담당별 작업 · 번호를 눌러 시작
각 셀의 Issue 번호를 누르면 작업 내용과 현재 진행 상태를 볼 수 있습니다. 기술 세부 내용과 설정·시험 근거는 개인 Notion 기술서에 기록합니다.

| 담당 | 설계 10/21→23 | AS-IS 10/28 | 재현 10/29→11/02 | 개선 11/03→06 | 재검증 11/09→10 | 보고 11/11→13 |
|---|---|---|---|---|---|---|
| M1 유용수 | [M1-01 #1](https://github.com/infra-security-team/ott-security-project/issues/1) | [M1-02 #14](https://github.com/infra-security-team/ott-security-project/issues/14) | [M1-03 #15](https://github.com/infra-security-team/ott-security-project/issues/15) | [M1-04 #16](https://github.com/infra-security-team/ott-security-project/issues/16) | [M1-05 #17](https://github.com/infra-security-team/ott-security-project/issues/17) | [M1-06 #18](https://github.com/infra-security-team/ott-security-project/issues/18) |
| M2 윤서영 | [M2-01 #2](https://github.com/infra-security-team/ott-security-project/issues/2) | [M2-02 #19](https://github.com/infra-security-team/ott-security-project/issues/19) | [M2-03 #20](https://github.com/infra-security-team/ott-security-project/issues/20) | [M2-04 #21](https://github.com/infra-security-team/ott-security-project/issues/21) | [M2-05 #22](https://github.com/infra-security-team/ott-security-project/issues/22) | [M2-06 #23](https://github.com/infra-security-team/ott-security-project/issues/23) |
| M3 홍은서 | [M3-01 #3](https://github.com/infra-security-team/ott-security-project/issues/3) | [M3-02 #24](https://github.com/infra-security-team/ott-security-project/issues/24) | [M3-03 #25](https://github.com/infra-security-team/ott-security-project/issues/25) | [M3-04 #26](https://github.com/infra-security-team/ott-security-project/issues/26) | [M3-05 #27](https://github.com/infra-security-team/ott-security-project/issues/27) | [M3-06 #28](https://github.com/infra-security-team/ott-security-project/issues/28) |
| M4 박진혁 | [M4-01 #4](https://github.com/infra-security-team/ott-security-project/issues/4) | [M4-02 #29](https://github.com/infra-security-team/ott-security-project/issues/29) | [M4-03 #30](https://github.com/infra-security-team/ott-security-project/issues/30) | [M4-04 #31](https://github.com/infra-security-team/ott-security-project/issues/31) | [M4-05 #32](https://github.com/infra-security-team/ott-security-project/issues/32) | [M4-06 #33](https://github.com/infra-security-team/ott-security-project/issues/33) |
| M5 유은혜 | [M5-01 #5](https://github.com/infra-security-team/ott-security-project/issues/5) | [M5-02 #34](https://github.com/infra-security-team/ott-security-project/issues/34) | [M5-03 #35](https://github.com/infra-security-team/ott-security-project/issues/35) | [M5-04 #36](https://github.com/infra-security-team/ott-security-project/issues/36) | [M5-05 #37](https://github.com/infra-security-team/ott-security-project/issues/37) | [M5-06 #38](https://github.com/infra-security-team/ott-security-project/issues/38) |

각 단계의 작업 항목·검토자는 Issue에 있다. -03 공격은 해당 AS-IS 환경과 정상 경로 확인 후, -04 개선은 재현 결과와 원인 확인 후, -05 재시험은 개선 적용 후 진행한다. 준비 작업은 병행할 수 있으나 선행 시험을 생략하고 완료 처리하지 않는다.

## M5 앱 개발·M3 배포 일정

앱 개발은 **M5**, 서비스망·DB·배포 운영은 **M3** 담당이다. M1·M2·M4에게 앱 개발 코드를 배정하지 않는다. 원본 코드는 GitHub의 앱 폴더에, 개발 과정·시험 근거는 Notion에 기록한다. 아래 날짜는 캐나다망 담당 업무와 병행하는 **최소 기능 일정**이다.

| 기간 | M5 개발 결과 | M3 인계·공동 확인 |
|---|---|---|
| **10/19~21** | 로그인·권한, 한국/캐나다 진입, 목록·재생·자막 최소 요구 정의. ERD·Class Diagram·API 초안 | MySQL 버전·스키마, API 주소·포트, 환경변수 이름, 배포 대상 합의 |
| **10/22~23** | React 화면 골격, Spring Boot·MySQL 연결과 표본 데이터, FastAPI 실행 골격. **실제 AI 완성 마감 아님** | 새 환경의 실행 명령·DB 초기화·버전 확인, 첫 코드 인계 |
| **10/26~28** | 로컬 로그인·권한 허용/거부·목록·샘플 영상 재생 연결 | M3 DB/서버 배포 준비 및 기본 API 연결. 로컬 성공과 배포 성공을 구분 |
| **10/29~30** | 기본 기능 오류 수정·배포 지원. 캐나다 VPN과 S05 개선 전 시험 병행 | 배포 환경에서 로그인·목록·영상의 실제 요청/응답 확인 |
| **11/02~04** | 30~60초 영상의 음성 인식 → 한영 번역 → 시간 정보가 있는 SRT/VTT 생성 | FastAPI·Spring 연결, 파일 위치·오류·시간초과·API 호출 상한 확인 |
| **11/05~06** | React 플레이어 자막 표시, 정상/실패 입력 시험. AWS 웹·HTTPS/API 경로 확인 | 실행 버전 고정, 배포 환경의 요청·로그·자막 결과 교차 확인 |
| **11/09~10** | S05 재시험, OTT·AI 정상 기능 영향 확인, 새 기능 추가 중단 | M3와 APP 장애·복구 시험 및 최종 실행 절차 확인 |

**앱 필수 범위:** 로그인·권한, 한국/캐나다 진입, 콘텐츠 목록, 샘플 영상 재생, 실제 생성한 한영 자막 한 흐름. 추가 챗봇·프랑스어·두 번째 웹 화면·결제·DRM은 이 일정에 포함하지 않는다.

## 공동 작업
| ID·Issue | 주담당·협업 | 기간 | 핵심 완료 조건 |
|---|---|---|---|
| [COMMON-01 #6](https://github.com/infra-security-team/ott-security-project/issues/6) | PM 취합·PL 기술 통합·전원 결정 | 10/19~23 | 범위·주소·자원·계약·비용·시험 기준선 |
| [COMMON-02 #7](https://github.com/infra-security-team/ott-security-project/issues/7) · 4망 통합 | M1 + 각 망 담당·M2 | 10/26~28 | 허용·금지·반환 경로 및 양쪽 설정·로그 대조 |
| [COMMON-03 #8](https://github.com/infra-security-team/ott-security-project/issues/8) · OTT·AI 앱 개발·배포 통합 | M5 개발 / M3 배포·DB | 10/19~11/06 | 10/23 골격, 10/28 로컬 기본 기능, 10/30 배포 기본 기능, 11/06 실제 AI 자막. 모의 응답은 최종 증거 아님 |
| [COMMON-04 #9](https://github.com/infra-security-team/ott-security-project/issues/9) · 중앙 로그·센서 통합 | M2 / 전원 원본 로그 제공 | 10/26~11/06 | 해당 서버 담당이 원본과 중앙 로그를 대조. 수집 누락·지연·탐지 한계를 기록. |
| [COMMON-05 #10](https://github.com/infra-security-team/ott-security-project/issues/10) · DB 복제·S3 백업·격리 복원 | M4 / M3 | 10/26~11/10 | 복제 상태만으로 복원 성공 판정 금지. 시작/종료 시각·명령 결과·데이터 대조 및 목표 충족 여부. |
| [COMMON-06 #11](https://github.com/infra-security-team/ott-security-project/issues/11) · APP 장애·복구 시험 | M3 / M5 | 11/02~11/10 | Pod 자동 재시작을 전체 고가용성으로 표현하지 않음. 실제 범위와 결과를 M5가 교차 검토. |
| [COMMON-07 #12](https://github.com/infra-security-team/ott-security-project/issues/12) · AWS 캐나다 웹·한국 API 연동 | M5 / M3·M1 | 10/21~11/06 | 실제 브라우저 요청/응답과 배포 설정. 로컬 실행만으로 AWS 연동 완료 처리하지 않음. |
| [COMMON-08 #13](https://github.com/infra-security-team/ott-security-project/issues/13) · 최종 결과보고·리허설·11/16 발표 | 전원 / PM 일정 취합·PL 기술 검토 | 11/09~11/16 | 11/11 증거 마감, 11/12 보고·발표자료, 11/13 리허설. 발표 시간·제출 형식·시각은 10/19 확인 |

## 날짜별 PM 확인점

| 날짜 | 확인할 내용 |
|---|---|
| **10/19** | 준비된 실습 장비의 자원·주소, AWS 계정 권한·크레딧과 사용 범위, Notion 접근, 발표·제출 조건 확인 |
| **10/21** | 망 주소·VPN 초안과 S01~S05 조건, M5 ERD·Class Diagram·API 초안과 M3 DB 조건 대조 |
| **10/23** | 주소 중복·허용 통신·시험 범위·앱 실행 계약·AWS HTTPS 경로 확인. 미확정 사항은 담당·기한 지정 |
| **10/28** | 망별 정상 경로와 VPN 허용 통신, OTT **로컬** 로그인·권한·목록·영상 확인. AI 자막은 이 날짜의 완료 조건이 아님 |
| **10/30** | OTT **배포 환경** 기본 요청/응답, 개선 전 공격 최소 3건의 원본 증거. 미재현 건은 원인·다음 시각 기록 |
| **11/02** | 공격 5건의 개선 전 시험 마감. 실패·미수행은 사실대로 표시하고 개선 조건 조정 |
| **11/06** | 개선 설정, 실제 AI 한영 자막·재생, 중앙 로그, AWS 웹/API·S3 복원의 확인 범위와 미완료 항목 구분 |
| **11/10** | 동일 조건 재시험, OTT·AI 정상 기능 영향, 격리 DB 복원·APP 장애 범위 확인 |
| **11/11~13** | 11/11 증거·잔여 위험 확정, 11/12 보고서·발표자료 취합, 11/13 전원 리허설 |


## 일정이 밀릴 때
- 당일 Issue에 막힌 이유·영향받는 작업·지원 요청·다음 행동을 남깁니다. PM은 다음 근무일까지 담당·해결 시점을 조정합니다.
- PL은 기술 의존성과 가능한 대안을 확인하고, 각 담당이 자기 영역을 수정합니다. PL에게 모든 구축을 넘기지 않습니다.
- 10/23 실제 장비의 가용 자원, K8s 배치, AWS 계정 권한·비용 및 TLS 경로를 확인합니다. 장비가 준비됐다는 사실만으로 모든 기술이 검증됐다고 표시하지 않습니다.
- 10/28 정상 통신이 연결되지 않으면 그 경로에 의존하는 공격은 미수행으로 두고, 독립적인 시나리오부터 진행합니다.
- 10/30 기본 앱·4망 연결이 지연되면 PM은 추가 챗봇·프랑스어·두 번째 웹 화면 등 선택 기능을 보류합니다. 핵심 기능·시험 범위를 바꿔야 한다면 이유와 영향을 회의록에 남깁니다.
- 11/02 재현하지 못한 시나리오는 결과를 만들지 않고 원인·대체 시각·강사 확인이 필요한 범위를 기록합니다.
- 11/06 이후 새로운 기능을 추가하기보다 필수 검증과 결함 수정에 집중합니다. 실패 결과도 실제 근거와 제약을 보고합니다.
- AWS 크레딧 잔액과 별도로 비용 알림·호출 제한·자원 종료 책임을 기록합니다. 크레딧은 자동 과금 중단 장치가 아닙니다.

## 기록 기준
- WBS: 계획 일정과 담당. 실제 진행 상황은 Issue에서 확인.
- Notion: 개인별 구축·설정·코드·보안 재현·개선·재시험 및 근거.
- 퇴근 전 Issue 댓글: 진행 요약, Notion 링크, 막힌 점, 다음 작업. PM은 기록과 일정을 확인.
- 일정·범위 변경: 회의록에 합의 내용 기록 후 WBS 수정.

계획서 PDF v0.2의 W1~W4는 상대 주차다. W2 공격 5건 완료 목표와 이 WBS의 11/02 마감 차이는 PM의 선행 작업·업무량 조정이다. 범위·날짜 변경은 이유와 영향받은 Issue를 함께 기록한다.
