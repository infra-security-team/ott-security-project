# 파일은 어디에 넣나요?
[처음 화면](../README.md) · [작성 방법](WORK_GUIDE.md)

처음에는 **내 Notion 기술서, 내 작업 Issue, 내 파일 폴더**만 찾으면 됩니다.
Notion에는 코드·설명·결과까지 기록하며, 나중에 팀 최종 문서로 합칩니다.

| 이름 | 실제 설정·스크립트 파일 위치 |
|---|---|
| 유용수 | [infrastructure/m1-hq-network](../infrastructure/m1-hq-network/README.md) |
| 윤서영 | [infrastructure/m2-hq-security](../infrastructure/m2-hq-security/README.md) |
| 홍은서 | [infrastructure/m3-service](../infrastructure/m3-service/README.md) |
| 박진혁 | [infrastructure/m4-backup-dr](../infrastructure/m4-backup-dr/README.md) |
| 유은혜 | [infrastructure/m5-canada](../infrastructure/m5-canada/README.md) |

앱 코드는 [화면 frontend](../frontend/README.md), [서버 backend](../backend/README.md), [AI ai-service](../ai-service/README.md)에 둡니다.
설계 초안은 Notion에서 작성할 수 있습니다. 단계 검토 때 필요한 공통 구성도·결과 요약은 아래 상세 위치에 저장하고 상세 기술서를 연결합니다.
실제 DB 백업·VM 이미지·비밀번호·키는 공개 저장소에 넣지 않습니다.

<details>
<summary>설계·보안·시험·최종보고 등 전체 폴더가 필요할 때 펼치세요</summary>

## 지금 만들려는 파일로 찾기
| 만들 것 | 위치·예시 |
|---|---|
| M1 주소·통신 설계 | `docs/03-architecture/network/m1-network.md` |
| S01 개선 전 진단 | `docs/04-security/assessment/s01-m1.md` |
| S01 개선안 / 재검증 | `docs/04-security/remediation/s01-m1.md` / `validation/s01-m1.md` |
| M1 실제 설정 원본 | `infrastructure/m1-hq-network/configs/` 아래 파일 |
| DB 복원 결과 | `docs/06-testing/test-dr-001.md` |
| 상세 설치 과정·스크린샷·로그 | Notion 기술서, GitHub에서 해당 구간 링크 |
| 재현에 필요한 그림 | 해당 문서 옆 `assets/`에 저장 후 상대 링크 |
| 비밀번호·개인키·대용량 백업·VM 이미지 | GitHub 업로드 대상 아님. 승인된 별도 보관소 사용 |

예시 파일과 `configs/`, `scripts/`, `assets/`는 실제 내용이 생길 때 만듭니다. 빈 폴더를 채우기 위한 문서는 만들지 않습니다.

## 전체 폴더별 역할
| 위치 | 넣을 내용 | 주담당 |
|---|---|---|
| [docs/01-planning](../docs/01-planning/README.md) | 계획·범위·일정의 기준 | PM·PL + 전원 |
| [docs/01-planning/project-plan](../docs/01-planning/project-plan/README.md) | 현재 계획서 PDF와 승인 상태 | PM |
| [docs/01-planning/archive](../docs/01-planning/archive/README.md) | 이전 계획안·피드백·변경 이유 | PM |
| [docs/01-planning/team-roles](../docs/01-planning/team-roles/README.md) | 5명 역할과 단계별 작업 안내 | 각 담당 |
| [docs/01-planning/wbs](../docs/01-planning/wbs/README.md) | 작업 순서·주차·의존 관계·완료 기준 | PM·PL |
| [docs/02-meetings](../docs/02-meetings/README.md) | 회의 안건·회의록·담당/기한 | 회의 기록자 |
| [docs/02-meetings/decision-log](../docs/02-meetings/decision-log/README.md) | 기술·범위 선택 이유와 승인 기록 | 결정 담당·PL |
| [docs/03-architecture](../docs/03-architecture/README.md) | 전체 아키텍처 안내 | PL·전원 |
| [docs/03-architecture/network](../docs/03-architecture/network/README.md) | 주소·VLAN·VPN·필요 통신표 | M1 취합·각 망 |
| [docs/03-architecture/as-is](../docs/03-architecture/as-is/README.md) | 개선 전 구성도와 시험 환경 | 각 망 |
| [docs/03-architecture/to-be](../docs/03-architecture/to-be/README.md) | 개선 후 구성도와 변경 경계 | 각 망 |
| [docs/03-architecture/cloud](../docs/03-architecture/cloud/README.md) | AWS·vSphere 배치·자원·비용 전제 | M3/M4/M5 |
| [docs/04-security](../docs/04-security/README.md) | 시나리오·보안 산출물 안내 | M2·전원 |
| [docs/04-security/assessment](../docs/04-security/assessment/README.md) | 시험 설계·AS-IS 재현·원인/영향 | S01~S05 각 담당 |
| [docs/04-security/remediation](../docs/04-security/remediation/README.md) | 개선 권고·정책·설정 차이·롤백 | S01~S05 각 담당 |
| [docs/04-security/validation](../docs/04-security/validation/README.md) | 동일 조건 전후 비교·정상 기능·잔여 위험 | 각 담당·검토자 |
| [docs/05-development](../docs/05-development/README.md) | 애플리케이션 설계 안내 | M5·M3 연동 |
| [docs/05-development/api-spec](../docs/05-development/api-spec/README.md) | API·권한·입출력·오류 계약 | M5 |
| [docs/05-development/erd](../docs/05-development/erd/README.md) | DB 테이블·관계·제약 | M5·M3 확인 |
| [docs/05-development/class-diagram](../docs/05-development/class-diagram/README.md) | 주요 클래스 책임·관계 | M5 |
| [docs/06-testing](../docs/06-testing/README.md) | 통신·서비스·AI·장애·복원 시험 결과 | 시험 담당 |
| [docs/07-reports](../docs/07-reports/README.md) | 최종 컨설팅 결과·발표·5인 기여 | 전원 |
| [docs/templates](../docs/templates/README.md) | 복제할 빈 문서 양식 | PM·전원 개선 |
| [docs/examples](../docs/examples/README.md) | 작성된 형태를 보여주는 학습 예시 | 전원 참고 |
| [docs/guides](../docs/guides/README.md) | 계획서와 분리된 포트폴리오 작성 가이드 | 전원 참고 |
| [infrastructure](../infrastructure/README.md) | 재현 가능한 설정·스크립트 안내 | 전원 |
| [infrastructure/m1-hq-network](../infrastructure/m1-hq-network/README.md) | 본사 VLAN·라우팅·VPN·방화벽 설정 | M1 |
| [infrastructure/m2-hq-security](../infrastructure/m2-hq-security/README.md) | Wazuh·Suricata·Bastion·수집 정책 | M2 |
| [infrastructure/m3-service](../infrastructure/m3-service/README.md) | 서버·DB·서비스 실행 환경 | M3 |
| [infrastructure/m3-service/deployment](../infrastructure/m3-service/deployment/README.md) | 앱 실행 계약·배포·롤백 절차 | M3·M5 |
| [infrastructure/m3-service/kubernetes](../infrastructure/m3-service/kubernetes/README.md) | K8s 매니페스트·상태 검사·권한 정책 | M3 |
| [infrastructure/m4-backup-dr](../infrastructure/m4-backup-dr/README.md) | 복제·백업·복원 스크립트·운영 절차 | M4 |
| [infrastructure/m5-canada](../infrastructure/m5-canada/README.md) | 지사 VLAN·VPN·방화벽 설정 | M5 |
| [infrastructure/shared](../infrastructure/shared/README.md) | 공통 통신·인계 계약·비밀값 없는 변수 예시 | 연동 담당 |
| [frontend](../frontend/README.md) | React 코드와 실행법 | M5 |
| [backend](../backend/README.md) | Spring Boot·DB 연동 코드와 실행법 | M5 |
| [ai-service](../ai-service/README.md) | FastAPI·STT/LLM 코드와 실행법 | M5 |

## 루트·운영 파일
- `README.md`: 팀원이 매일 출발하는 화면.
- `docs/START_HERE.md`, `WORK_GUIDE.md`, `PROJECT_FLOW.md`: 시작·작성·진행 기준.
- `docs/TEAM_LINKS.md`: 공용 Notion·계정·일정의 등록 위치.
- `.github/ISSUE_TEMPLATE/`: New issue에서 고르는 작업·보안 양식.
- `.github/pull_request_template.md`: PR의 변경 목적·검증·검토 양식.
- `.env.example`: 비밀값 없는 환경변수 예시. 실제 `.env`를 대신 올리지 않습니다.
- `.gitignore`: 불필요한 파일 제외 규칙. 비밀정보 유출을 자동으로 모두 막아주는 장치는 아닙니다.

## 실행 준비·검증 자료 바로가기
- [착수 확인표](01-planning/readiness.md): 실제 계정·자원·합의가 필요한 항목.
- [PM·PL 업무](01-planning/team-roles/pm-pl.md): 일정 조율·기술 통합·팀원 검토의 역할.
- [시험 기준표](06-testing/test-matrix.md): 시험별 판정 기준과 작성할 결과 위치.
- [최종 산출물](07-reports/final-delivery.md): 보고·시연·리허설 일정.

## 파일을 추가할 때
담당 ID·시험 ID로 이름을 붙이고 문서 첫머리에 상태·담당·관련 Issue를 적습니다. 여러 사람이 쓰는 하나의 공통 파일은 PR로 변경을 합칩니다.
정식 결과에는 **환경·시각·기대/실제·판정·증거 URL**이 필요합니다. 실험하지 않은 내용은 계획 또는 예시로 표시합니다.

</details>
