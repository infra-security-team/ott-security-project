# OTT 인프라·보안 프로젝트 WBS · 일정 수정 검토안 (2026-10-19~11-16)

[프로젝트 첫 화면](README.md) · [계획서 v0.2 (팀 검토안)](plans/project-plan-v0.2.pdf) · [GitHub Projects](https://github.com/orgs/infra-security-team/projects/4) · [전체 Issue](https://github.com/infra-security-team/ott-security-project/issues)

> **상태: PM 수정 제안 / 10월 19일 팀 기술 검토 전.** 아래 날짜는 계획이며 실제 구축·시험 완료가 아니다. PM은 일정·우선순위·병목을 조정하고, M3(PL) 및 관련 망 담당자가 설계/시험의 기술 타당성을 검토한다. 기존 38개 Issue 번호·담당자를 유지한다.

## 1. 주차별 목표·검토 기준

| 기간 | 이번 단계 목표 | 실제 확인할 기준 |
|---|---|---|
| **W1 10/19~23** | 10/19~21 오전 **4망·AWS·Docker/K8s·보안 배치 포함 AS-IS 도면/장비 명세**, **10/21 오후 AS-IS 구축 착수(늦어도 10/22)**, 강사 v0.2 피드백 반영 여유 | 10/19 강사 검토·도면 초안, 10/20 도면·TO-BE 방향/보안 통신 검토, **10/21 오전 도면 기준선**, 수 오후~금 검토된 VM·라우팅·컨테이너 기반부터 실제 구축/초기 통신 증거. W1 전체망 구축 완료 필수 아님 |
| **W2 10/26~30** | 4망 AS-IS·격리 시험 환경 통합, Docker→K8s 앱 최소 배포, 승인된 공격 **5건 목표**(현실적 지연 시 11/02 보완) | 10/28 VPN 허용/차단·리턴 경로, **10/28 로컬 OTT 최소 기능**, **10/30 M3 배포 환경 로그인·권한·목록·영상 확인** 후 종속된 공격 시험. 10/30 5건은 v0.2 목표이고 **11/02는 PM 완충일**, 10/30에 최소 3건 중간 점검 |
| **W3 11/02~06** | W2 미재현 공격 보완(11/02), **11/03 TO-BE 적용안 확정**, 11/03~06 개선·AI/관제/AWS/복원 통합 | 개선 전 AS-IS 정상 서비스·로그 결과 확보 뒤 정책 적용. **11/06** 실제 30~60초 한영 자막 생성·React 표시/관제·AWS 웹/API·S3 복원 1차를 개별 판정. 첫 OTT 최소 배포 목표는 **11/03이 아닌 10/30** |
| **W4 11/09~13** | 동일 조건 재검증, 서비스·복원/장애 확인, 보고·리허설 | 11/10 기능·보안·복구 시험, 11/11 증거·잔여 위험 마감, 11/12 최종 자료, 11/13 전원 리허설 |
| 11/14~15 | 선택적 완충 | 주말 근무를 전제로 필수 업무를 배치하지 않음 |
| **11/16** | 최종 발표 | 신규 핵심 구축 없이 환경 사전 점검·발표 |

## 2. 공동 설계 의사결정 — 모든 망 담당 참석

| 시점 | 논의와 승인 주체 | 남길 산출물 및 다음 단계 진입 조건 |
|---|---|---|
| **10/19 월** | **강사 v0.2 피드백 및 PM 짧은 회의** → 4망 AS-IS 도면 초안, VMware/vSphere·Docker/K8s·AWS·각 망 보안/중앙로그 위치 동시에 결정 시작 | 라우터/VM/클라이언트/컨테이너·클러스터 노드·AWS 서비스·각 망 보안 구성 및 M2 수집 경로 초안, 수정 요구와 담당/기한. 설치 완료 요구 없음 |
| **10/20 화** | 4망 AS-IS 도면 공동 리뷰, VLAN/IP/VPN, **Docker 이미지 빌드·K8s 노드/서비스·AWS 공개/백업 경로**, 각 망 보안정책과 TO-BE 방향 검토 | 연결 충돌/누락 수정, S01~S05 정상·취약 경로 및 정책 초안, 온프레미스·AWS 배치 차이와 자원/비용 문제 목록 |
| **10/21 수 오전** | M1/PL 중심 최종 도면 통합 검토, NIC/가상 스위치·VPN·VLAN·Docker/K8s·AWS·중앙 로그/망별 보안 배치 확인 | **AS-IS 설계·구축 자산 목록 기준선**, 강사 추가 변경 부분은 미확정/대안/재검토 날짜 명시 |
| **10/21 수 오후~10/23 금** | **승인된 영역부터 AS-IS 실제 구축 시작**: VM·VyOS·스위치/서버, 컨테이너 런타임/K8s 기반과 각 망 방화벽·로그 수집 구성(단계별). 늦어도 목요일 착수 목표 | 첫 장비/서비스 기동, IP·게이트웨이 통신 결과, 막힌 설정과 선행 의존성 기록. W1 전체망·K8s·보안 정책 완료 요구 안 함 |
| **10/23 금** | PM/PL **실제 1차 구축 결과 점검**, 다음 주 4망 VPN·DB·OTT·보안 연동 선행조건 확인 | 각자 설치/미수행/정상/실패 분리, 초기 통신·로그 증거, 강사 수정 항목·미해결 건의 담당과 다음 일정 |
| **11/02 월** | 각 담당 개선 전 시험 결과·원인 공유 | 실제 공격/로그/정상 경로 결과, 미재현 사항, 개선 우선순위 |
| **11/03 화 오전** | PL/담당자와 개선 적용안 공동 결정 | **TO-BE 최종 적용 기준선**: 변경할 규칙·대상·순서·복구 방법·정상 기능 기준을 결정하고 기존 개선 Issue(#16·#21·#26·#31·#36)에 연결 |

**구분:** 10/20 개선망 *방향과 설계 초안*을 검토하고 **10/21 오전 AS-IS 기본 설계 기준선**을 정해 오후부터 구축한다. 10/23은 실제 초기 구축 진도 점검이다. 11/03은 11/02 실제 재현 결과를 반영한 *최종 적용안* 확정일이다. 공격 재현 전 TO-BE 통제를 미리 적용해 실험 조건을 바꾸지 않는다. 합의는 기존 공통 [#6](https://github.com/infra-security-team/ott-security-project/issues/6) 및 팀 회의록에서 기록하며 별도 Issue를 늘리지 않는다.

**보안 책임은 전원 분담:** M1은 본사 VLAN·VPN·방화벽/접근통제, M2는 중앙 Wazuh·Suricata 등 관제/로그 통합과 본사 시험, M3는 DMZ·APP·DB·K8s 관리/RBAC·보안 로그, M4는 DR·백업/S3 접근제어·로그, M5는 캐나다 방화벽/VPN·DB 직접 접근 통제·로그를 담당한다. **중앙 관제는 M2가 총괄해도 각 망 정책/로그 에이전트/시험 증거는 망 담당자가 구축·검증한다.** 장비별 별도 보안 VM 수는 자원·관찰 경로 확인 후 결정한다.

**강사 피드백 변경 관리:** 10/19 검토에서 필수 기능·망 구조·클라우드 배치가 바뀌면 영향을 받는 도면·Issue·일정을 표시해 PM이 조정하고 PL/망 담당자가 기술 타당성을 확인한다. 승인되지 않은 취약 구성은 구축하지 않고, 승인된 독립 구역부터 21일 오후/22일 구축한다.

## 3. 담당별 WBS — 업무명·기간·Issue 한번에 보기

**19~21일 도면 작업·구축 착수용 문서:** [하이브리드 배치·망별 장비/역할과 도면 표준](design/network-guides/README.md) 및 [draw.io 작성 방법](design/network-guides/01-drawio-diagram-guide.md). 이 문서는 구축 전 **설계 명세**이며, 실제 결과는 Notion/Issue에서 검증한다.

표의 날짜는 계획이고, **Issue는 실행 기록, Notion은 실제 기술 기록, Projects의 Status는 현재 진행 상태**다. 다음 단계에 영향이 있는 작업은 선행 조건을 먼저 확인한다.

| 담당 | 설계·공동 검토 | AS-IS 구축 | 개선 전 시험 | TO-BE 적용 | 재검증 | 보고·시연 |
|---|---|---|---|---|---|---|
| M1 유용수 | 본사 VLAN·IP·VPN 허브/관리 경로 설계<br>**10/19~23 · [#1](https://github.com/infra-security-team/ott-security-project/issues/1)** | 본사 VLAN·라우팅·VPN AS-IS 구축 및 정상 경로<br>**10/21 오후~10/28 · [#14](https://github.com/infra-security-team/ott-security-project/issues/14)** | S01 직원망→관리망 비인가 경로 재현<br>**10/29~11/02 · [#15](https://github.com/infra-security-team/ott-security-project/issues/15)** | 접근통제·Bastion 경로 개선 적용<br>**11/03~06 · [#16](https://github.com/infra-security-team/ott-security-project/issues/16)** | S01 동일 조건 재시험·정상 통신 확인<br>**11/09~10 · [#17](https://github.com/infra-security-team/ott-security-project/issues/17)** | 본사 설계/변경/검증 결과·시연 정리<br>**11/11~13 · [#18](https://github.com/infra-security-team/ott-security-project/issues/18)** |
| M2 윤서영 | 본사 보안·SSH·관제/탐지 설계<br>**10/19~23 · [#2](https://github.com/infra-security-team/ott-security-project/issues/2)** | 실험 Linux·SSH 로그/센서 수집 경로 구축<br>**10/21 오후~10/28 · [#19](https://github.com/infra-security-team/ott-security-project/issues/19)** | S02 반복 인증 실패 관측·원본 로그 확보<br>**10/29~30 · [#20](https://github.com/infra-security-team/ott-security-project/issues/20)** | 인증·관제 정책 개선 및 정상 로그인 확인<br>**11/03~06 · [#21](https://github.com/infra-security-team/ott-security-project/issues/21)** | S02 재시험·중앙 로그 대조<br>**11/09~10 · [#22](https://github.com/infra-security-team/ott-security-project/issues/22)** | 탐지·한계·증거·시연 정리<br>**11/11~13 · [#23](https://github.com/infra-security-team/ott-security-project/issues/23)** |
| M3 홍은서 (PL) | 서비스망 DMZ/APP/DATA·DB·자원/K8s 범위 합의<br>**10/19~23 · [#3](https://github.com/infra-security-team/ott-security-project/issues/3)** | 기본 서버·DB·런타임/관리 경로 구축; 전체 앱 배포와 구별<br>**10/21 오후~10/28 · [#24](https://github.com/infra-security-team/ott-security-project/issues/24)** | S03 관리 포트 노출 재현·원인 분석<br>**10/29~30 · [#25](https://github.com/infra-security-team/ott-security-project/issues/25)** | 서비스망 노출·관리 접근 개선; M5 배포 협업<br>**11/03~06 · [#26](https://github.com/infra-security-team/ott-security-project/issues/26)** | S03 재시험·앱 정상 동작 확인<br>**11/09~10 · [#27](https://github.com/infra-security-team/ott-security-project/issues/27)** | 서비스망 구축·배포·PL 통합 결과 정리<br>**11/11~13 · [#28](https://github.com/infra-security-team/ott-security-project/issues/28)** |
| M4 박진혁 | DR망·백업/복제·복원 목표 설계<br>**10/19~23 · [#4](https://github.com/infra-security-team/ott-security-project/issues/4)** | 백업 접근용 격리 환경·테스트 파일/권한·첫 백업 준비 (복원 합격 아님)<br>**10/21 오후~10/28 · [#29](https://github.com/infra-security-team/ott-security-project/issues/29)** | S04 테스트 백업 비인가 접근 재현<br>**10/29~30 · [#30](https://github.com/infra-security-team/ott-security-project/issues/30)** | 백업 접근 제어 개선·복원 준비 협업<br>**11/03~06 · [#31](https://github.com/infra-security-team/ott-security-project/issues/31)** | S04 재시험·#10 실제 복구 결과 대조<br>**11/09~10 · [#32](https://github.com/infra-security-team/ott-security-project/issues/32)** | 백업/복원 증거·RPO/RTO·시연 정리<br>**11/11~13 · [#33](https://github.com/infra-security-team/ott-security-project/issues/33)** |
| M5 유은혜 (PM) | 캐나다 VLAN/VPN 설계 + 앱 ERD·API 계약 초안<br>**10/19~23 · [#5](https://github.com/infra-security-team/ott-security-project/issues/5)** | 캐나다 VLAN·VPN·정상 경로 구축 전담; 앱 기능 완성과 구별<br>**10/21 오후~10/28 · [#34](https://github.com/infra-security-team/ott-security-project/issues/34)** | S05 VPN 경유 한국 DB 접근 재현<br>**10/29~11/02 · [#35](https://github.com/infra-security-team/ott-security-project/issues/35)** | DB 직접 접근 제한·캐나다 정책 개선; 앱 개발 병행<br>**11/03~06 · [#36](https://github.com/infra-security-team/ott-security-project/issues/36)** | S05 재시험·OTT/API 정상 접근 확인<br>**11/09~10 · [#37](https://github.com/infra-security-team/ott-security-project/issues/37)** | 캐나다/앱/PM 일정·결과·시연 정리<br>**11/11~13 · [#38](https://github.com/infra-security-team/ott-security-project/issues/38)** |

**1주차 겹침 안내:** 개인 설계 Issue #1~#5의 검토 기간(10/19~23)과 구축 Issue #14/#19/#24/#29/#34의 시작(10/21 오후~)은 **의도적으로 겹칩니다**. 10/21 오전 승인된 구역만 먼저 구축하고, 설계가 미확정인 부분은 보류합니다. 10/28은 기본망 통합 검증 마감 목표이며 10/21은 전체망 구축 완료 마감이 아닙니다.

**선행 순서:** 10/19 강사 피드백·도면 초안 → 10/20 도면/정책 초안 합의 → **10/21 오전 설계 기준선·오후 AS-IS 구축 착수**(늦어도 10/22) → 공통 기준선([#6](https://github.com/infra-security-team/ott-security-project/issues/6)) 확인·AS-IS 구축/정상 기능(-02) → 승인 시험·근거(-03) → 11/03 개선 기준선/적용(-04) → 동일 입력 재시험(-05) → 결과(-06). 각 개인 WBS ID와 Issue 번호는 유지한다.

## 4. 중복 업무를 제거하는 담당 경계와 개발 일정

- **M5 개발:** React/Spring Boot/MySQL 연동 코드·FastAPI/STT/번역·SRT/VTT 생성, 캐나다망/VPN, PM 일정 관리. **M1·M2·M4에게 앱 개발 코드를 재배정하지 않는다.**
- **M3 운영:** 한국 서비스망/DB 실행 환경, vSphere/ESXi·vCenter 가능 범위 및 **v0.2 Kubernetes Control Plane 1+Worker 2·Spring 복제본 2개/로드밸런서 기본 제안**, M5 코드 수령/배포·서비스 가용성 검증, PL 기술 통합. **M3에게 앱 기능 구현을 전가하지 않는다.**
- **M4 백업:** **DB Replica/복제는 v0.2 기본 계획**이고, 10/28은 백업 파일/시험 계정/격리 복원 환경 *준비*. 실제 별도 DB 복원과 앱 조회 검증은 공동 [#10](https://github.com/infra-security-team/ott-security-project/issues/10)에서 11/04~10 수행한다. 복제 연결만으로 복원 성공 판정 금지.
- **M5 VPN 집중:** 10/26~28 캐나다 직원/관리 VLAN·라우팅·VPN 정상/비인가 경로 우선. 이 기간에 *로컬 OTT 전체 기능 완료*를 개인 [#34](https://github.com/infra-security-team/ott-security-project/issues/34)의 완료 기준으로 요구하지 않는다.
- **M3 K8s 난이도:** **10/19~20 도면에 Docker/K8s 노드·서비스/이미지 경로·클러스터 관리망을 우선 배치**, **v0.2 기본 제안은 CP 1대+Worker 2대, Spring 2 Pod 다른 Worker 분산/LB**. 10/21 오전 CPU/RAM·라이선스·CNI 및 K8s API 6443 시험 가능 여부를 검토한다. 21일 오후부터 구축을 단계적으로 시작한다. 실제 K8s가 구성되지 않으면 S03 시험 대상을 팀 기술 승인으로 조정하고, 가상의 K8s 포트 검증을 완료라고 쓰지 않는다. APP 자동 재시작과 전체 HA는 구분한다.

| 날짜 | M5 앱 개발 (별도 [#8](https://github.com/infra-security-team/ott-security-project/issues/8)의 실행 기준) | M3 인계·배포/공동 검증 |
|---|---|---|
| **10/19~21 오전** | 캐나다 VLAN/VPN·AWS 고객 웹/한국 API 경로·자체 방화벽/중앙 로그 연동 **설계 먼저**, ERD·앱 요구는 간단히 목록화 | 서비스 DMZ/APP/DATA와 **Docker 이미지/실행 위치, K8s Control Plane/Worker/Service·Ingress, DB/보안 로그** 위치를 설계. 최초 도면이 먼저 |
| **10/21 오후~10/23** | 캐나다망 착수와 병행해 M3와 API·DB 계약 합의, **ERD/Class/API 초안 목표를 10/22~23**으로 배치. 개발 골격은 실제 시간에 맞춰 조정 | **21일 오후/22일부터** 기본 Linux/DB·컨테이너 런타임·K8s 노드 가용자원 확인·초기 구축 착수. 전체 APP 배포 완료와 구별 |
| **10/26~28** | **캐나다 VLAN/VPN 연결을 우선하며 별도 개발 시간을 확보해**, 기존 코드 골격에서 로컬 로그인·권한 허용/거부·목록·샘플 영상 재생을 10/28까지 한 흐름으로 확인 목표. 캐나다 VLAN/VPN과 병행해 작업 시간을 분리 | M3가 K8s 1 CP + 2 Worker 및 LB/Service, Spring 2개 복제본(가용 자원 조건) 기반 APP/DB/프록시 통신·기본 코드 인계 확인 |
| **10/29~30** | M3와 합동으로 기본 OTT 기능을 **AS-IS 배포 환경에서 10/30까지 실요청/응답 검증 목표**. S05는 정상 서비스/DB 경로 증거 확인 후 격리 시험 진행 | 배포된 로그인/목록/샘플 영상·API·DB 요청/응답, 기본 LB 경유 통신 확인. 10/30 지연 시 S03·S05 정상 기능 연동 검증은 '미수행'으로 표시 |
| **11/02~03** | 10/30 배포 결함 수정·S05 AS-IS 결과 공유, 11/03 TO-BE 적용안 공동 검토 후 캐나다 정책 개선 적용 | 배포 환경 OTT 회귀검증, 앱 로그·기본 LB 및 K8s 노드·정책 변경 영향 확인 |
| **11/04~06** | **한 개 30~60초 시험 영상**으로 실제 음성 인식 → 한영 번역 → 타임스탬프 있는 SRT/VTT → React 표시 | FastAPI/Spring 실행 경로·파일 접근·오류·타임아웃·API 상한, 배포 환경에서 교차 검증 |
| **11/09~10** | 새 기능 추가 중단, S05 재시험 및 OTT 정상 기능 영향 검증 | APP 장애/복구 검증, 최종 실행 절차·실패 시 대안 확정 |

**필수 범위:** 로그인/권한, 한국·캐나다 서비스 구분, 목록, 샘플 영상 재생, 실제 생성한 한영 자막 **한 흐름**. 일정 단축이 필요하면 *현재 필수 목표 안에서* 표본 영상 1개·수동 자막 생성 시작·최소 UI·API 수 축소·K8s 배치 규모 축소(기술 검토 후) 등을 먼저 결정한다. 챗봇·프랑스어·결제·DRM은 이미 계획에서 제외되어 있어 다시 제외해도 시간을 줄이지 못한다. 핵심 5개 공격/4망 검증의 축소는 PM 단독 결정이 아니라 팀/강사 합의를 거친다.

## 5. 공동 통합 업무 (개인 작업과 중복 완료 처리 금지)

| 공동 Issue | 담당·협업 | 계획 기간 | 확인할 산출물·완료 기준 |
|---|---|---|---|
| [#6](https://github.com/infra-security-team/ott-security-project/issues/6) | M5 취합·M3 PL 통합·전원 결정 | 10/19~23 | **19일 강사 피드백/전체 설계 초안 → 20일 보안·AS-IS/TO-BE·하이브리드 배치 검토 → 21일 오전 도면 기준선·오후 구축 개시 → 23일 초기 결과 점검** |
| [#7](https://github.com/infra-security-team/ott-security-project/issues/7) | M1 주담당 / M3·M4·M5 협력, M2 관리 경로 확인 | 10/26~28 | 4개 망 VPN·라우팅·허용/금지 통신 검증 |
| [#8](https://github.com/infra-security-team/ott-security-project/issues/8) | M5 코드 / M3 서버·DB·배포 | 10/19~11/06 | 19~21 오전 Docker·K8s 배치 설계, 22~23일 ERD/API·개발 골격, **10/28 로컬 최소 기능**, **10/30 AS-IS 환경 실제 배포/기본 기능·정상 서비스 증거**(S03·S05 선행), 11/06 실제 AI 자막 통합 목표. M5 캐나다 VPN과 중복 업무라 고위험 |
| [#9](https://github.com/infra-security-team/ott-security-project/issues/9) | M2 주담당 / 각 망 담당 로그 제공 | 10/26~11/06 | 중앙 로그·센서 통합: 원본과 수집 결과·가시성 확인 |
| [#10](https://github.com/infra-security-team/ott-security-project/issues/10) | M4 주담당 / M3 DB 협업 | 10/26~11/10 | DB 복제·백업·S3 사본·격리 복원: 10/28 파일/환경 준비, 10/30 첫 백업, 11/04 첫 복원, 11/06 S3 1차, 11/10 최종 검증 |
| [#11](https://github.com/infra-security-team/ott-security-project/issues/11) | M3 주담당 / M5 서비스 검증 | 11/02~11/10 | APP 장애·복구 시험: Pod 재시작과 전체 HA 구분 |
| [#12](https://github.com/infra-security-team/ott-security-project/issues/12) | M5 주담당 / M3·M1 협업 | 10/21~11/06 | AWS 캐나다 웹·한국 API 경로: 비용/권한·HTTPS·CORS 검증 |
| [#13](https://github.com/infra-security-team/ott-security-project/issues/13) | 전원 / M5 일정 취합·M3 기술 검토 | 11/09~11/16 | 최종 보고·5인 리허설·발표 |

[#29](https://github.com/infra-security-team/ott-security-project/issues/29)는 **시험 가능한 백업 파일/접근 권한을 확보하는 업무**이고 [#10](https://github.com/infra-security-team/ott-security-project/issues/10)은 **실제 복제·S3 백업·격리 DB 복원과 앱 대조**다. [#24](https://github.com/infra-security-team/ott-security-project/issues/24)는 **기본 서비스 런타임 준비**이고 [#8](https://github.com/infra-security-team/ott-security-project/issues/8)은 **실제 OTT 기능 배포·AI 통합**이다.

## 6. PM 날짜별 점검 및 지연 대응

| 날짜 | PM이 확인할 사실 / 지연 시 행동 |
|---|---|
| 10/19 | **강사 계획서 검토 및 4망+AWS·Docker/K8s·보안 배치 초안**, 장비·자원 목록 및 담당자의 수정 요청. 최종 도면·실제 구축 완료 요구 없음 |
| 10/20~21 | **20일** AS-IS/TO-BE·보안정책·컨테이너/클러스터/클라우드 배치 공동 검토, **21일 오전** 도면 구축 기준선, **오후** 가능한 부분부터 VM/망 구축 시작. ERD/API 초안은 22~23일 |
| 10/23 | 실제 AS-IS 초기 장비/망·컨테이너/K8s 환경·각 망 보안/로그 수집 **착수·첫 테스트 범위** 점검, 남은 오류와 강사 변경 영향, 다음 주 VPN 연동 선행조건 |
| 10/28 | 각 망 정상/비인가 통신·반환 경로·로그, 테스트 백업 파일/격리 환경 **준비**, M5 VPN 확인 |
| 10/30 | **v0.2 목표: 승인된 공격 5건·기본 OTT AS-IS 배포**. PM 점검선은 **원본 증거 3건 이상**과 5건 지연 원인, 11/02 보완 담당·시각 명시. 로컬 10/28·배포 10/30 목표를 구분, 미수행을 완료로 쓰지 않음 |
| 11/02 | v0.2 W2 재현 5건 목표의 **PM 완충 마감(계획서와 1근무일 차이)**. 실제 AS-IS 정상 경로와 승인 공격·원본 로그를 교차 확인하고 미완료 범위는 기록, 11/03 정책 변경 대상 승인 준비 |
| 11/03 오전 | TO-BE **최종 적용안** 승인·적용 순서/롤백 결정 |
| 11/06 | 개선 정책 적용 결과, AI 한영 자막의 **실제 생성 및 재생**, 배포·로그·S3 복원 1차는 각각 독립 판정 |
| 11/10 | 동일 조건 재시험 + 정상 기능, 최종 격리 DB 복원/앱 조회, APP 장애 시험과 잔여 SPOF |
| 11/11~13 | 증거·잔여 위험 확정(11일), 발표물(12일), 전원 리허설(13일) |

**일정이 지연되면:** 그날 Issue 댓글에 증상·실제 결과·영향받는 후속 Issue·지원 요청·다음 작업을 남긴다. PM은 다음 근무일에 담당·우선순위를 조정한다. 10/28 통신 미완성 시 해당 경로의 공격 결과를 만들어내지 않고 독립 시나리오를 먼저 시험한다. 11/02 미재현 시 조건·대안의 기술 타당성을 PL/담당자에게 검토받는다. 11/06부터 기능 추가보다 최소 필수 경로·검증·결함수정에 집중한다. AWS 크레딧은 요금 상한 보장이 아니므로 알림·호출 제한·자원 정리 책임을 정한다.

## 7. 문서/상태 단일 기준 및 팀원 시작 순서

1. **WBS:** 계획상 작업·담당·기한 및 선행 의존성. 매일 완료율을 중복 입력하지 않는다.
2. **GitHub Projects:** 현재 진행 상태 `Todo → In progress → Blocked / In review → Done`와 일정 확인. Issue 본문에 과거 `상태: 할 일` 문구가 남아 있으면 *더 이상 최신 상태로 사용하지 않는다*. 팀 검토 후 관련 Issue 안내를 정리한다.
3. **GitHub Issue:** 작업 체크박스, 일일 댓글(진행·Notion URL·막힘·다음 행동), 기술 검토 링크. Close는 실제 검토 근거 확인 후 수행한다.
4. **Notion 개인 기술서:** 팀 공용 [양식](https://app.notion.com/p/3fd1b198732a81cf9c44fb58dfcb8567?pvs=204)을 **한 번 복제** → `M1 유용수 — 본사 네트워크 구축·보안 기록`처럼 본인 이름/분야로 변경 → 팀원/PM에게 공유 → 첫 Issue의 '개인 Notion 기술서'에 해당 링크 연결 → 이후 동일 개인 페이지에 실습·설정·로그·재현·개선·재시험 누적 기록. **공유 링크가 있다는 사실만으로 타인의 열람 가능을 확정하지 않는다.**
5. **GitHub 저장소 파일:** 계획·WBS·설계 합의·회의록·최종 요약·**앱 원본 코드**(frontend/backend/ai-service). 상세 인프라 명령·시험 로그는 Notion. 공개 파일/노션에 암호·VPN PSK·API 키 등 비밀값 저장 금지.

**v0.2와 WBS 일정 차이:** 계획서 28쪽은 **W2 종료(10/30)까지 공격 5건 AS-IS 증거 목표**다. 이 WBS는 10/30 목표를 유지하되 초보 팀의 통합 지연 위험으로 **11/02 하루를 보완 마감**으로 별도 둔 PM 조정안이며, 팀/강사 검토 전 공식 확정이 아니다. 10/30까지 완료하지 않은 건수는 성공으로 기재하지 않는다. 추가 언어·챗봇은 원래 제외이므로 일정 절감 방안으로 재사용하지 않는다. 꼭 필요한 경우 앱 화면/표본 콘텐츠/API 수·복잡한 배포 구현 깊이를 변경 영향과 함께 기술 검토한다.

**최대 일정 병목:** M5는 10/21~30에 캐나다망+React/Spring/MySQL+PM을 병행하고 M3는 VMware/vSphere+K8s+LB+PL+배포를 병행한다. **10/23(설계·코드 골격), 10/28(로컬+망), 10/30(배포+공격)**를 고위험 검문점으로 지정한다. 선행 작업이 미완료면 해당 종속 시험을 완료 처리하지 않으며 당일 PM이 범위·대체안·지원 일정을 팀과 재협의한다.

**버전 주의:** `plans/project-plan-v0.2.pdf`는 팀 검토 중인 기획서로, 30쪽의 옛 GitHub/Notion 기록 위치 안내와 현재 운영 규칙이 다르다. 이 WBS/README의 운영 안내를 실습 때 우선 참조하되, PDF 수정/버전 확정은 팀 리뷰 후 진행한다. 보고서에서 미검증 항목을 완료로 표현하지 않는다.
