# Blocks | OTTer 하이브리드 인프라·보안 컨설팅

Blocks 팀이 가상의 보안 컨설팅 회사 NetBlocks의 역할로 OTTer의 한국·캐나다 하이브리드 인프라를 구축하고 보안 개선 효과를 검증하는 프로젝트입니다.

| 구분 | 명칭 |
|---|---|
| 팀 | **Blocks** |
| 보안 컨설팅 회사 | **NetBlocks** |
| 가상 OTT 고객사 | **OTTer** |
| 프로젝트 제목 | 한국·캐나다 OTTer 하이브리드 인프라 구축 및 보안 컨설팅 |

프로젝트 고유명은 아직 미확정이며, 위 설명형 제목을 사용합니다.

**기간** 2026.10.19~11.16 · **인원** 5명 · **발표** 11.16 · **계획 기준** v0.3 · **최근 안내 갱신** 2026.10.20

**[최신 계획서 v0.3 PDF · 14쪽](plans/project-plan-v0.3.pdf)** · [전체 계획서 이력](plans/)

## START HERE — 팀원 작업 안내

| 순서 | 작업 위치 | 실행 내용 |
|---|---|---|
| 1 | [GitHub Projects — 팀 업무 보드](https://github.com/orgs/infra-security-team/projects/4) | 내 담당 카드 선택 → 연결된 Issue의 작업·완료 기준 확인 |
| 2 | [Notion 기술서 양식](https://app.notion.com/p/3fd1b198732a81cf9c44fb58dfcb8567?pvs=204) | 개인 기술서 복제·팀 공유 → 첫 Issue에 개인 페이지 링크 등록 |
| 3 | 해당 Issue 및 Projects | 실습 증거·Notion 링크·문제·다음 작업 댓글 → Projects 상태 갱신 |

**관리 기준:** [WBS](WBS.md) = 업무·일정 / Projects = 진행 상태 / Issue = 체크리스트·결과 / Notion = 실제 설정·오류·검증 근거

## 담당 업무 및 첫 Issue

| 담당 | 책임 영역 | 시작 Issue |
|---|---|---|
| M1 유용수 | 한국 본사 GNS3 라우터·VLAN 스위치·UTM·VPN | [#1](https://github.com/infra-security-team/ott-security-project/issues/1) |
| M2 윤서영 | 본사 보안·Wazuh/Suricata 중앙 관제 | [#2](https://github.com/infra-security-team/ott-security-project/issues/2) |
| M3 홍은서 (PL) | 한국 서비스망·vSphere·Docker/K8s·DB·Argo CD 배포 | [#3](https://github.com/infra-security-team/ott-security-project/issues/3) |
| M4 박진혁 | 백업·DB 복제·DR·AWS S3 원격 백업 | [#4](https://github.com/infra-security-team/ott-security-project/issues/4) |
| M5 유은혜 (PM) | 캐나다망·VPN·React/Spring Boot/FastAPI·AI·AWS 웹·CI/CD | [#5](https://github.com/infra-security-team/ott-security-project/issues/5) |

## 프로젝트 문서

| 문서 | 바로가기 |
|---|---|
| 전체 업무 및 일정 | [WBS.md](WBS.md) · [Projects](https://github.com/orgs/infra-security-team/projects/4) |
| 프로젝트 계획서 | **[최신 v0.3 PDF · 14쪽](plans/project-plan-v0.3.pdf)** · [v0.2 PDF](plans/project-plan-v0.2.pdf) · [v0.1 PDF](plans/project-plan-v0.1.pdf) |
| AS-IS/TO-BE 구성도·ERD·Class Diagram | [설계 문서](design/README.md) |
| 망별 필요 장비·프로그램·보안 구성·구축 안내 | [M1~M5 구축 가이드](design/network-guides/README.md) |
| 회의 및 결정사항 | [회의록](meetings/README.md) |
| OTT 애플리케이션 코드 | [React](frontend/README.md) · [Spring Boot](backend/README.md) · [FastAPI](ai-service/README.md) |

## 10/20 현재 설계·배포 방향

- M1: 별도 VyOS 없이 GNS3 내부 라우터·L2 VLAN 스위치와 UTM으로 구성합니다. M2·M3의 VyOS는 유지합니다.
- M3·M5: GitHub Actions로 빌드·검사하고, 기존 한국 Kubernetes·캐나다 EKS 내부 Argo CD로 배포합니다. 별도 CI/CD 전용 VM을 기본안에 추가하지 않습니다.
- 최신 팀 공유 토폴로지는 기존 AS-IS/TO-BE 도면 12쪽과 CI/CD 상세도 3쪽을 포함한 15쪽입니다. [구성도 안내](design/architecture.md)에서 범위를 확인합니다.
- 이름·CI/CD 결정은 이 안내에 반영했습니다. 저장소의 v0.3 PDF에 해당 결정이 모두 반영됐다는 의미는 아니며, PDF 내용 개정은 별도로 진행합니다.
- 설계·도입 결정과 실제 구축·검증 완료는 구분합니다.

## 프로젝트 진행 및 기록 원칙

**공격 시나리오 선정 → AS-IS 전체망 구축·정상 기능 확인 → 격리 환경 공격 재현 → TO-BE 보안 개선 → 동일 조건 재검증**

- 앱 개발: M5 / 서버·DB·Docker/K8s 배포: M3 / 각 망 보안 설정·시험: 담당자 / 중앙 로그·관제 총괄: M2
- 작업 상태: `Todo → In progress → In review → Done` / 진행 불가 시 `Blocked`
- 일일 Issue 댓글: **진행 결과 / Notion 증거 링크 / 막힌 점 / 다음 작업**
- 공개 GitHub·Notion의 비밀번호, API 키, VPN PSK, 개인키 및 개인정보 노출 금지
- **실제 구축·검증된 결과만 완료 처리**, 강사 피드백에 따른 설계·일정 확정사항은 회의록과 WBS에 기록
