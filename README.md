# OTT Infrastructure & Security Consulting (가칭)

> **문서 상태:** 프로젝트 설계 중 · 2026-10-16 킥오프 이후 강사 피드백을 반영하는 단계
>
> **Organization `infra-security-team`, Repository `ott-security-project`는 임시 이름입니다.** 회사/고객사 브랜드명은 팀 회의에서 확정한 뒤 변경합니다.

## 프로젝트 개요

한국과 캐나다에서 서비스를 제공하는 **가상 OTT 고객사**를 대상으로, 가상의 인프라·보안 컨설팅 조직이 4개 주요 망의 취약한 초기 환경(AS-IS)을 설계·재현하고, 진단·개선·검증(TO-BE)을 수행하는 **4주 팀 프로젝트**입니다. 최종 발표까지 포함합니다.

- **AS-IS:** 실습을 위해 의도적으로 재현한 취약하거나 미흡한 초기 구성. 실제 고객사 침해 사실이 아닙니다.
- **TO-BE:** 개선 대상 구성에 보안·가용성·복구 대책을 적용한 목표 상태.
- **주요 목표:** 4망 VLAN/VPN, 한국·캐나다 OTT 서비스, 망별 보안 검증, 인프라 운영, 백업·복원. AWS·vSphere·Kubernetes는 강사 피드백에 따라 구현 범위와 장비 가능성을 구체화합니다.

## 팀 및 담당 영역

| ID | 담당 | 주요 업무 |
|---|---|---|
| M1 | 유용수 | 본사 네트워크·VPN·라우팅·이중화 |
| M2 | 윤서영 | 본사 보안·Wazuh 등 중앙 관제·보안 공통 기준 |
| M3 | 홍은서 (PL) | 서비스망, Linux·MySQL 서버, Docker/K8s 배포, LB·APP 이중화 |
| M4 | 박진혁 | 백업·DR망, 복제·백업·복원·AWS 원격 백업 검토 |
| M5 | 유은혜 (PM) | 캐나다망·VPN 및 React/Spring Boot/MySQL 연동 코드/FastAPI·LLM 개발 |

**모든 구성원**은 담당 영역의 AS-IS 구축 → 위험 진단 → TO-BE 보안 적용 → 동일 조건 재검증을 직접 기록합니다. M2는 전체 보안을 대신 수행하지 않고 중앙 보안 기준·관제를 총괄합니다.

M5는 **전체 애플리케이션 코드**를 담당하고 M3는 **서버/DB 실행 인프라 및 배포**를 담당합니다. 통합 배포 검증은 M3·M5 공동 수행합니다.

> 위 세부 기술 배치는 **팀 협의용 제안안**이며, 아직 확정된 작업 결과가 아닙니다.

## 프로젝트 운영 링크

| 자료 | 위치 |
|---|---|
| [문서 작성 표준](docs/DOCUMENTATION_GUIDE.md) | 문서 상태, 파일명, 보안 유의사항, 작성·검토 규칙 |
| [기획·계획·WBS](docs/01-planning/README.md) | 기획 버전, 범위, 일정, 담당 |
| [회의록·결정 로그](docs/02-meetings/README.md) | 회의 확정/제안 사항 구분 |
| [AS-IS·TO-BE 아키텍처](docs/03-architecture/README.md) | 전체/망별 구성도 |
| [보안 컨설팅](docs/04-security/README.md) | 취약점 분석·개선·증빙 |
| [개발 설계](docs/05-development/README.md) | Class Diagram·ERD·API 명세 |
| [통합 테스트](docs/06-testing/README.md) | 케이스별 테스트 결과 |
| [결과 보고](docs/07-reports/README.md) | 컨설팅 결과 및 최종 발표 |
| [문서 템플릿](docs/templates/README.md) | 새 문서 생성 시 복제 |
| [망별 인프라 설정](infrastructure/README.md) | 버전 관리 가능한 설정·스크립트 |
| [Notion 기술세부내역서](docs/DOCUMENTATION_GUIDE.md#notion-기술세부내역서) | 팀 Notion 링크는 개설 후 등록 |
| GitHub Issues / Projects | 업무 분담·담당·마감·완료 증빙 (후속 설정) |

## 팀 협업 기준

1. **계획/제안과 확정된 결정, 실제 구축 및 테스트 결과를 구분**합니다.
2. 각 작업을 GitHub Issue로 추적하고, Notion의 상세 기술서와 연결합니다.
3. 소스코드·설정은 GitHub에, 실행 화면·실습 과정·트러블슈팅은 Notion에 상세 기록합니다.
4. 구성 변경 시 설계도와 기술서를 함께 수정합니다.
5. 팀원 실명 공개 범위, IP·계정·키·토큰·비밀번호·로그 내 개인정보는 외부 공개 전 별도 검토합니다. **실제 비밀값은 커밋하지 않습니다.**

## 현재 단계

- [x] 2026-10-16 팀 구성, PL/PM 지정, OTT 인프라·보안 컨설팅 주제 설정
- [x] 강사 피드백 수령: AWS 구체화, 보안 솔루션 보강, vSphere/Kubernetes 검토
- [ ] 팀원별 최종 구축 범위·실제 장비 자원 확정
- [ ] 기획서 v0.1/v0.2 원본 업로드 및 v1.0 확정
- [ ] GitHub Issues/Projects 및 Notion 기술서 공간 연동
- [ ] 실제 구축·검증 시작
