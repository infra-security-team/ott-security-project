# OTTer Shield

### 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅

**Team Blocks**가 보안 컨설팅 회사 **NetBlocks**의 역할로 가상 OTT 고객사 **OTTer**의 인프라를 구축하고, 취약점 진단·개선·재검증을 수행하는 5인 팀 프로젝트입니다.

**프로젝트 운영:** 2026.10.19~11.16 · **킥오프:** 10.16 · **최종 발표:** 11.16 · **현재 단계:** 설계·구축 준비

한국·독일 온프레미스 본사, 한국 OTT 서비스, 백업·DR, 캐나다 지사와 AWS Store를 구성합니다. 한국·독일은 같은 업무 구성을 기반으로 독일 전용 Wazuh의 탐지·대응 효과를 비교합니다.

## 프로젝트 자료

| 자료 | 바로가기 | 확인할 내용 |
|---|---|---|
| 프로젝트 계획서 | [v0.3 PDF](plans/project-plan-v0.3.pdf) | 프로젝트 배경·목표·기본 범위 |
| 업무·일정 | [WBS](WBS.md) · [팀 업무 보드](https://github.com/orgs/team-blocks-lab/projects/4/views/2) | 담당별 작업·기한·진행 상태 |
| 회의·결정사항 | [회의록](meetings/README.md) · [10/20 설계 변경](meetings/2026-10-20-design-decisions.md) | M2 독일 본사 전환·보안 범위·배포 결정 |
| 팀 설계 자료 | [토폴로지·ERD·Class Diagram](design/README.md) | 팀원이 작성·검토한 도면과 앱 설계 |
| 개발 코드 | [사내 게시판](apps/m1-intranet/README.md) · [OTT·AI](apps/m3-ott/README.md) · [Store](apps/m5-store/README.md) | 서비스별 코드·실행·배포 안내 |
| 기술 기록 | [Notion 기술서 양식](https://app.notion.com/p/3fd1b198732a81cf9c44fb58dfcb8567?pvs=204) | 담당별 실제 설정·오류·시험 증거 기록 |

계획서 v0.3 이후의 M2 역할·보안 구성 변경은 **10/20 회의록과 WBS**에 반영했습니다. PDF는 작성 당시 계획으로 보존하며 구축 완료를 뜻하지 않습니다. 개발 폴더는 현재 실행 코드 등록 전입니다.

## 팀 구성 및 담당

| 구역 | 담당 | 책임 영역 | 시작 Issue |
|---|---|---|---|
| M1 한국 본사 | 유용수 | GNS3·UTM·부서망·게시판 배포·VPN | [#1](https://github.com/team-blocks-lab/otter-shield/issues/1) |
| M2 독일 본사 | 윤서영 | M1과 같은 업무망·게시판 배포·독일 전용 Wazuh | [#2](https://github.com/team-blocks-lab/otter-shield/issues/2) |
| M3 한국 서비스 | 홍은서 · PL | 가상화·Kubernetes·DB·OTT/AI 배포·통합 검토 | [#3](https://github.com/team-blocks-lab/otter-shield/issues/3) |
| M4 백업·DR | 박진혁 | DB 복제·백업·S3·격리 복원 | [#4](https://github.com/team-blocks-lab/otter-shield/issues/4) |
| M5 캐나다 | 유은혜 · PM | 지사망·VPN·전체 앱 코드·AI·AWS Store·프로젝트 관리 | [#5](https://github.com/team-blocks-lab/otter-shield/issues/5) |

앱 코드는 M5가 개발합니다. M1·M2는 같은 게시판 코드를 사용하되 DB·계정·환경설정은 분리합니다. M1 후속 실장비 간소화 설계는 **주담당 윤서영 / 보조 박진혁**입니다.

## 구현·검증 방향

**AS-IS 설계 → 구축·정상 업무 확인 → 공격·원인 분석 → TO-BE 설계·검토 → 구현 → 재시험·정상 업무 확인**

| 구역 | 검증 주제 |
|---|---|
| M1 | 직원의 서버 관리 접근을 UTM으로 제한 |
| M2 | 반복 SSH 인증 실패를 Wazuh로 탐지하고 선정한 자동 대응 검증 |
| M3 | Kubernetes 관리 API 노출 제한·승인 관리자 접근 유지 |
| M4 | 백업 파일 접근 권한 개선·실제 DB 복원 |
| M5 | 업무 VPN을 통한 한국 격리 Test DB 직접 접근 제한·웹 업무 유지 |

**주요 도입 기술:** GNS3, VMware/vSphere, UTM(Sophos UTM 9), VyOS(M3), Wazuh(M2 전용), Kubernetes, AWS, React, Spring Boot, FastAPI, GitHub Actions, Argo CD. 정확한 버전·실할당 자원·시험 결과는 구축 시 기술서에 기록합니다.

## 오늘·내일 먼저 할 일

- **10/20(화) 오늘:** 각자 담당 망의 AS-IS(개선 전) 도면을 draw.io로 만들어 [design/토폴로지](design/토폴로지/README.md)에 원본·미리보기 이미지를 업로드합니다.
- **10/21(수) 내일:** 도면을 보고 가상 장비 생성·연결·OS 설치부터 망 구축을 시작합니다.

## 팀원 작업 순서

1. [WBS](WBS.md)에서 이번 작업과 기한을 확인하고 연결된 Issue를 엽니다.
2. 본인 Notion 기술서에 실제 설정·명령어·오류·검증 결과를 기록합니다.
3. Issue 댓글에 **오늘 한 일 / 증거 링크 / 막힌 점 / 다음 작업**을 남깁니다.
4. 업무 보드의 진행 상태를 갱신하고, 검토 후 완료 처리합니다.

**WBS = 일정 · Projects = 진행 상태 · Issue = 작업·결과 · Notion = 기술 상세·증거**

토폴로지는 팀 작성본을 등록합니다. 공개 저장소에는 비밀번호·API 키·VPN 비밀키·실제 내부 주소표를 올리지 않습니다.
