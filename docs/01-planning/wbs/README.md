# 4주 WBS · 작업 순서와 완료 기준
[프로젝트 흐름](../../PROJECT_FLOW.md) · [역할 목록](../team-roles/README.md) · [작성 방법](../../WORK_GUIDE.md)

**WBS는 계획표, Issue는 현재 상태입니다.** 이 표에 매일 체크하거나 별도 완료율을 입력하지 않습니다. 실제 시작·마감일은 착수/발표일 합의 후 Issue에 등록합니다. W1~W4는 상대 주차입니다.

| WBS | 담당 | 주차 | 선행·완료 기준 | Issue |
|---|---|---|---|---|
| M1-01 | M1 유용수 | W1 | 설계·시나리오·정상 경로·자원 확인, 연동 검토 | [#1](https://github.com/infra-security-team/ott-security-project/issues/1) |
| M2-01 | M2 윤서영 | W1 | 설계·시나리오·정상 경로·자원 확인, 연동 검토 | [#2](https://github.com/infra-security-team/ott-security-project/issues/2) |
| M3-01 | M3 홍은서 | W1 | 설계·시나리오·정상 경로·자원 확인, 연동 검토 | [#3](https://github.com/infra-security-team/ott-security-project/issues/3) |
| M4-01 | M4 박진혁 | W1 | 설계·시나리오·정상 경로·자원 확인, 연동 검토 | [#4](https://github.com/infra-security-team/ott-security-project/issues/4) |
| M5-01 | M5 유은혜 | W1 | 설계·시나리오·정상 경로·자원 확인, 연동 검토 | [#5](https://github.com/infra-security-team/ott-security-project/issues/5) |
| COMMON-01 | 전원 / PM 취합·PL 기술 통합 | W1 | 5명 초안 통합, 범위·주소·자원·일정·시험 기준선 합의 | [#6](https://github.com/infra-security-team/ott-security-project/issues/6) |

## 이어서 생성할 담당별 작업
아래 `Mn`은 M1~M5 각각입니다. 예: `M4-03` = M4의 개선 전 재현·분석 작업. 현재 미생성 작업이며 완료로 간주하지 않습니다.

| WBS 패턴 | 담당·주차 | 선행 | 수행·완료 기준 |
|---|---|---|---|
| Mn-02 | 각 담당 / W2 | Mn-01 + COMMON-01 | AS-IS 구축, 통신·정상 기능·격리 확인 |
| Mn-03 | 각 담당 / W2 | Mn-02 | 승인 시험 재현, 관찰 증거·원인·영향 확보 |
| Mn-04 | 각 담당 / W3 | Mn-03 | 개선안 검토 후 적용, 설정 차이·정상 기능·롤백 기록 |
| Mn-05 | 각 담당 / W4 | Mn-04 | 동일 조건 전후 비교·정상 기능·남은 위험 교차 검토 |
| Mn-06 | 각 담당 / W4 | Mn-05 및 관련 통합 시험 | 결과 요약·담당 기여·시연·인수인계 |

## 공동 통합 작업 (선행 정보 합의는 W1부터)
| WBS | 주담당·협업 | 주차 | 선행·완료 기준 |
|---|---|---|---|
| COMMON-02 | M1 + M3/M4/M5, M2 | W2 | 각 망 기본 환경 → 4망 왕복 통신·허용/비허용 경로 확인 |
| COMMON-03 | M3 + M5 | W2 기본 / W3 완성 | 실행 계약·기본 앱·런타임 → 로그인·권한·목록·재생·실제 AI 한영 자막 통합 |
| COMMON-04 | M2 + 전원 | W2–W3 | 시간 동기화·수집 경로 → 원본 로그·중앙 경보 대조·센서 가시성 |
| COMMON-05 | M4 + M3 | W3–W4 | 테스트 DB·백업·격리 복원 환경 → 복제·S3 사본 복원·데이터 대조·복구 시간 |
| COMMON-06 | M3 + M5 | W3–W4 | 기본 서비스 정상 → APP 장애 후 정상 요청·복구 시간·단일 장애점 |
| COMMON-07 | M5 + M3/M1 | W3–W4 | AWS·비용·TLS/API 경로 합의 → 웹 HTTPS·API 연동·정상 서비스 |
| COMMON-08 | 전원 / PM·PL 취합 | W4 | 망별 검증+통합 결과 → 최종보고·5인 설명·리허설 |

공동 작업도 착수 전에 주담당이 Issue를 만들고 위 ID를 연결합니다. 개별 작업 Issue에서 같은 통합 시험을 다시 작성하지 말고 공동 Issue를 연결합니다.
검토자는 해당 기능의 연동 담당으로 지정합니다. 범위·기한 변경은 이유와 의존 작업 영향을 Issue에 남깁니다.
W2 말 통합 지연 시 선택 기능을 보류하고 필수 범위 변경은 팀 합의합니다. W4 마지막 2일은 결과 정리·발표에 확보합니다.
