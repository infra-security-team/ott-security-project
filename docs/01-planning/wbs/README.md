# 발표일까지의 WBS · 2026-10-19~11-16
[처음 시작](../../START_HERE.md) · [역할 목록](../team-roles/README.md) · [PM·PL 운영](../team-roles/pm-pl.md)

**발표일은 2026-11-16입니다.** 10/19 월요일 착수와 아래 내부 마감일은 그에 맞춘 운영 일정안이며, 10/19 팀 검토 후 #6에 합의 내용을 남깁니다. 이미 합의·완료했다고 표시한 일정이 아닙니다.

WBS는 계획과 작업 순서, **Issue 본문은 현재 상태**입니다. WBS에 매일 체크하지 않습니다. 작업자는 자기 Issue를 갱신하고 검토자는 결과를 확인합니다. 선행 조건을 충족하지 못하면 날짜만 보고 다음 단계로 넘어가지 않습니다.

## 전체 일정
| 기간 | 목표 | 검토 시점·결과 |
|---|---|---|
| W1 · 10/19~23 | 범위·자원·설계·시나리오 합의, 앱 초안 개발 병행 | 10/21 초안, 10/23 기준선 검토 |
| W2 · 10/26~30 | AS-IS 정상 기능·4망 통합·개선 전 재현 | 10/28 기본 연동, 10/30 5개 시나리오 증거 |
| W3 · 11/02~06 | 개선 적용·실제 AI·관제·복원·클라우드 연동 | 11/06 개선 구성과 첫 통합 시험 |
| W4 · 11/09~13 | 동일 조건 검증·보고·리허설 | 11/10 복구, 11/11 보안 검증 마감, 11/12 보고, 11/13 리허설 |
| 11/14~15 | 선택 완충 기간 | 필수 작업·주말 근무를 전제로 배치하지 않음 |
| 11/16 | 발표 | 사전 점검·발표. 신규 핵심 구축 배치 금지 |

## 담당별 작업 · 번호를 눌러 시작
모든 후속 Issue를 생성했습니다. 한 사람당 한 단계씩 진행하되 독립적인 준비·공동 작업은 병행합니다.

| 담당 | 설계 10/21→23 | AS-IS 10/28 | 재현 10/30 | 개선 11/06 | 재검증 11/11 | 보고 11/13 |
|---|---|---|---|---|---|---|
| M1 유용수 | [M1-01 #1](https://github.com/infra-security-team/ott-security-project/issues/1) | [M1-02 #14](https://github.com/infra-security-team/ott-security-project/issues/14) | [M1-03 #15](https://github.com/infra-security-team/ott-security-project/issues/15) | [M1-04 #16](https://github.com/infra-security-team/ott-security-project/issues/16) | [M1-05 #17](https://github.com/infra-security-team/ott-security-project/issues/17) | [M1-06 #18](https://github.com/infra-security-team/ott-security-project/issues/18) |
| M2 윤서영 | [M2-01 #2](https://github.com/infra-security-team/ott-security-project/issues/2) | [M2-02 #19](https://github.com/infra-security-team/ott-security-project/issues/19) | [M2-03 #20](https://github.com/infra-security-team/ott-security-project/issues/20) | [M2-04 #21](https://github.com/infra-security-team/ott-security-project/issues/21) | [M2-05 #22](https://github.com/infra-security-team/ott-security-project/issues/22) | [M2-06 #23](https://github.com/infra-security-team/ott-security-project/issues/23) |
| M3 홍은서 | [M3-01 #3](https://github.com/infra-security-team/ott-security-project/issues/3) | [M3-02 #24](https://github.com/infra-security-team/ott-security-project/issues/24) | [M3-03 #25](https://github.com/infra-security-team/ott-security-project/issues/25) | [M3-04 #26](https://github.com/infra-security-team/ott-security-project/issues/26) | [M3-05 #27](https://github.com/infra-security-team/ott-security-project/issues/27) | [M3-06 #28](https://github.com/infra-security-team/ott-security-project/issues/28) |
| M4 박진혁 | [M4-01 #4](https://github.com/infra-security-team/ott-security-project/issues/4) | [M4-02 #29](https://github.com/infra-security-team/ott-security-project/issues/29) | [M4-03 #30](https://github.com/infra-security-team/ott-security-project/issues/30) | [M4-04 #31](https://github.com/infra-security-team/ott-security-project/issues/31) | [M4-05 #32](https://github.com/infra-security-team/ott-security-project/issues/32) | [M4-06 #33](https://github.com/infra-security-team/ott-security-project/issues/33) |
| M5 유은혜 | [M5-01 #5](https://github.com/infra-security-team/ott-security-project/issues/5) | [M5-02 #34](https://github.com/infra-security-team/ott-security-project/issues/34) | [M5-03 #35](https://github.com/infra-security-team/ott-security-project/issues/35) | [M5-04 #36](https://github.com/infra-security-team/ott-security-project/issues/36) | [M5-05 #37](https://github.com/infra-security-team/ott-security-project/issues/37) | [M5-06 #38](https://github.com/infra-security-team/ott-security-project/issues/38) |

각 단계의 상세 수행 항목·작성 파일·검토자는 Issue에 있습니다. -02는 -01과 COMMON-01 검토 후, -03은 정상 기능 확인 후, -04는 개선 전 증거 확보 후, -05는 개선 적용 후 진행합니다. -06 초안은 미리 작성하되 최종 결과로 마무리합니다.

## 공동 작업
| ID·Issue | 주담당·협업 | 기간 | 핵심 완료 조건 |
|---|---|---|---|
| [COMMON-01 #6](https://github.com/infra-security-team/ott-security-project/issues/6) | PM 취합·PL 기술 통합·전원 결정 | 10/19~23 | 범위·주소·자원·계약·비용·시험 기준선 |
| [COMMON-03 #8](https://github.com/infra-security-team/ott-security-project/issues/8) · OTT·AI 앱 개발·배포 통합 | M5 앱 코드 / M3 배포·DB | 10/19~11/06 | 정상·실패 입력의 실제 결과. 모의 응답은 최종 AI 동작 증거가 아님. |
| [COMMON-04 #9](https://github.com/infra-security-team/ott-security-project/issues/9) · 중앙 로그·센서 통합 | M2 / 전원 원본 로그 제공 | 10/26~11/06 | 해당 서버 담당이 원본과 중앙 로그를 대조. 수집 누락·지연·탐지 한계를 기록. |
| [COMMON-05 #10](https://github.com/infra-security-team/ott-security-project/issues/10) · DB 복제·S3 백업·격리 복원 | M4 / M3 | 10/26~11/10 | 복제 상태만으로 복원 성공 판정 금지. 시작/종료 시각·명령 결과·데이터 대조 및 목표 충족 여부. |
| [COMMON-06 #11](https://github.com/infra-security-team/ott-security-project/issues/11) · APP 장애·복구 시험 | M3 / M5 | 11/02~11/10 | Pod 자동 재시작을 전체 고가용성으로 표현하지 않음. 실제 범위와 결과를 M5가 교차 검토. |
| [COMMON-07 #12](https://github.com/infra-security-team/ott-security-project/issues/12) · AWS 캐나다 웹·한국 API 연동 | M5 / M3·M1 | 10/21~11/06 | 실제 브라우저 요청/응답과 배포 설정. 로컬 실행만으로 AWS 연동 완료 처리하지 않음. |
| [COMMON-08 #13](https://github.com/infra-security-team/ott-security-project/issues/13) · 최종 결과보고·리허설·11/16 발표 | 전원 / PM 일정 취합·PL 기술 검토 | 11/09~11/16 | 5인 기여와 실제 근거 연결. 발표 시간·제출 형식·제출 시각은 10/19 확인. 11/14~15는 선택 완충일, 필수 근무일 아님. |

[COMMON-02 #7 · 4망 통합](https://github.com/infra-security-team/ott-security-project/issues/7): M1 + 각 망 담당, 10/26~28. 정상·금지 경로와 반환 경로를 확인합니다.

## 일정이 밀릴 때
- 당일 Issue에 막힌 이유·영향받는 작업·지원 요청·다음 행동을 남깁니다. PM은 다음 근무일까지 담당·해결 시점을 조정합니다.
- PL은 기술 의존성과 가능한 대안을 확인하고, 각 담당이 자기 영역을 수정합니다. PL에게 모든 구축을 넘기지 않습니다.
- 10/23 장비·K8s·AWS·TLS 가능 여부를 결정합니다. 선택 확장(예: 게이트웨이 이중화)은 필수 시험보다 앞세우지 않습니다.
- 10/30 기본 앱·4망 연결이 지연되면 PM·PL이 범위 축소안을 제시하고 팀이 결정합니다. 핵심 기능·시험 변경은 결정 기록과 계획서 변경 사항에 남깁니다.
- 11/06 이후 새로운 기능을 추가하기보다 필수 검증과 결함 수정에 집중합니다. 실패 결과도 실제 근거와 제약을 보고합니다.

## 운영 자료
[착수 확인표](../readiness.md) · [시험 기준표](../../06-testing/test-matrix.md) · [최종 산출물](../../07-reports/final-delivery.md)

PDF v0.2의 W1~W4는 상대 주차입니다. 구체 날짜와 실행 작업 연결은 이 WBS를 참고하며, 최종 팀 승인 시 일정 변경·승인 기록을 함께 남깁니다.
