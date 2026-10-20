# OTTer Shield | 업무·일정 (WBS)

**Team Blocks · NetBlocks → OTTer / 운영 2026.10.19~11.16 / 발표 11.16**

[프로젝트](README.md) · [계획서 v0.3](plans/project-plan-v0.3.pdf) · [10/20 회의록](meetings/2026-10-20-design-decisions.md)

[팀 업무 보드](https://github.com/orgs/team-blocks-lab/projects/4/views/2) · [토폴로지 업로드](design/토폴로지/README.md)

## 1. 오늘·내일 먼저 할 일

| 언제 | 전원 할 일 | 어디에 남기나요? |
|---|---|---|
| **10/20(화) 오늘** | 담당 망의 개선 전/후 도면을 draw.io로 만들고 원본·이미지 업로드 | **design/토폴로지** + #1~#5 댓글에 파일 링크 |
| **10/21(수) 내일부터** | 그 도면대로 가상 장비 생성 → 연결 → OS 설치 → IP·기본 통신 확인 | #14·#19·#24·#29·#34 + Notion |

오늘 제출할 것은 도면입니다. 내일 하루에 모든 서버를 완성하는 뜻은 아닙니다. 실제 버전·자원·남은 연결 질문은 구축하면서 10/23까지 확인하고, 막힌 구간 외 준비 가능한 작업은 진행합니다.

## 2. 담당별 시작 위치

| 담당 | 오늘 도면 작업 | 내일부터 망 구축 | 구축할 것 |
|---|---|---|---|
| M1 유용수 | [#1](https://github.com/team-blocks-lab/otter-shield/issues/1) | [#14](https://github.com/team-blocks-lab/otter-shield/issues/14) | 한국 본사 GNS3·UTM·업무 서버·직원/관리 PC |
| M2 윤서영 | [#2](https://github.com/team-blocks-lab/otter-shield/issues/2) | [#19](https://github.com/team-blocks-lab/otter-shield/issues/19) | M1과 같은 독일 업무망·게시판. Wazuh는 개선 단계 추가 |
| M3 홍은서 · PL | [#3](https://github.com/team-blocks-lab/otter-shield/issues/3) | [#24](https://github.com/team-blocks-lab/otter-shield/issues/24) | 한국 OTT 웹·가상화·Kubernetes·DB |
| M4 박진혁 | [#4](https://github.com/team-blocks-lab/otter-shield/issues/4) | [#29](https://github.com/team-blocks-lab/otter-shield/issues/29) | 백업·복제·S3·별도 복원 환경 |
| M5 유은혜 · PM | [#5](https://github.com/team-blocks-lab/otter-shield/issues/5) | [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) | 캐나다 UTM·직원/관리망·VPN. 앱/AI·Store 개발 병행 |

## 3. 전체 진행 순서

| 목표일 | 할 일 | 끝났는지 확인할 것 |
|---|---|---|
| **10/20** | 각자 draw.io 도면 업로드·서로 연결 확인 | 원본·개선 전/후 이미지·질문을 본인 Issue에 연결 |
| **10/21~23** | 가상 장비 생성·연결·OS 설치·IP 설정 | 장비 켜짐, 기본 통신·DNS·시간·설치 인터넷 확인 |
| 10/26~28 | 업무 서버 설치·망 간 연결·VPN | 게시판·관리·DB·백업 등 필요한 정상 업무 확인 |
| 10/29~30 | M1·M2·M4 개선 전 시험 / M3·M5 배포·준비 | 시험3건 증거, OTT 기본 배포·최소 Store 가능 여부 확인 |
| 11/02 | M3·M5 개선 전 시험 | 시험 총5건의 실제 화면·로그·원인 기록 |
| 11/03~06 | 보안 개선·독일 Wazuh·앱/AI·복제/복원 | 바꾼 설정과 정상 업무 확인. 11/05 첫 복제 목표 |
| 11/09~10 | 같은 시험 다시 하기·장애/복원 확인 | 개선 전후 비교 + 정상 업무 + 실제 복원 결과 |
| 11/11~13 | 결과·발표자료·리허설 | 11/11 증거, 11/12 발표자료, 11/13 전원 리허설 |
| 11/16 | 최종 발표 | 사전 점검·시연·담당 기여 설명 |

## 4. 담당별 다음 작업

| 담당 | 개선 전 시험 | 보안 설정 개선 ~11/06 | 재시험 ~11/10 | 결과 정리 ~11/13 |
|---|---|---|---|---|
| M1 유용수 | 10/29~30 [#15](https://github.com/team-blocks-lab/otter-shield/issues/15) | [#16](https://github.com/team-blocks-lab/otter-shield/issues/16) | [#17](https://github.com/team-blocks-lab/otter-shield/issues/17) | [#18](https://github.com/team-blocks-lab/otter-shield/issues/18) |
| M2 윤서영 | 10/29~30 [#20](https://github.com/team-blocks-lab/otter-shield/issues/20) | [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) | [#22](https://github.com/team-blocks-lab/otter-shield/issues/22) | [#23](https://github.com/team-blocks-lab/otter-shield/issues/23) |
| M3 홍은서 | 11/02 [#25](https://github.com/team-blocks-lab/otter-shield/issues/25) | [#26](https://github.com/team-blocks-lab/otter-shield/issues/26) | [#27](https://github.com/team-blocks-lab/otter-shield/issues/27) | [#28](https://github.com/team-blocks-lab/otter-shield/issues/28) |
| M4 박진혁 | 10/29~30 [#30](https://github.com/team-blocks-lab/otter-shield/issues/30) | [#31](https://github.com/team-blocks-lab/otter-shield/issues/31) | [#32](https://github.com/team-blocks-lab/otter-shield/issues/32) | [#33](https://github.com/team-blocks-lab/otter-shield/issues/33) |
| M5 유은혜 | 11/02 [#35](https://github.com/team-blocks-lab/otter-shield/issues/35) | [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) | [#37](https://github.com/team-blocks-lab/otter-shield/issues/37) | [#38](https://github.com/team-blocks-lab/otter-shield/issues/38) |

| 망 | 시험할 문제 | 개선 후 확인 |
|---|---|---|
| M1 | 직원이 본사 WAS에 SSH로 관리 접속 | UTM 차단·관리자 접속 유지 |
| M2 | 독일 직원 시험 PC의 반복 SSH 로그인 실패 | Wazuh 탐지·선정 자동 대응·차단 해제·관리자 정상 |
| M3 | M1 직원이 K8s 관리 API에 접속 | UTM 차단·승인 관리자 정상. 접속과 인증 우회는 구분 |
| M4 | 시험 계정이 가짜 백업 파일 읽기 | 파일 권한 거부·기록·정상 백업/복원 |
| M5 | 캐나다 직원이 VPN·본사를 거쳐 한국 시험 DB 직접 조회 | UTM3 차단·정상 웹 유지. 운영 DB/RDS는 시험 제외 |

## 5. 함께 할 일

| 작업 | 담당·기간 | Issue |
|---|---|---|
| 전체 도면 연결 확인·내일 구축 준비 | PM 취합·PL 기술 검토·전원 / 도면 취합 10/20 / 설치 준비 확인 10/21~23 | [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) |
| 각 망 연결·VPN 통신 확인 | M1 주관·M2/M3/M4/M5 협업 / 10/26~28 | [#7](https://github.com/team-blocks-lab/otter-shield/issues/7) |
| 게시판·OTT·Store 코드 개발·배포 | M5 코드 / M1·M2 게시판 배포 / M3 OTT 배포 / 10/21~11/06 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) |
| 독일 Wazuh 로그 수집·탐지·자동 대응 확인 | M2 주관·M1 비교 조건 확인 / 준비 10/26~28 / 적용 11/03~06 | [#9](https://github.com/team-blocks-lab/otter-shield/issues/9) |
| DB 복제·백업·S3·실제 복원 | M4·M3 / 준비 10/26~30 / 적용·검증 11/03~10 | [#10](https://github.com/team-blocks-lab/otter-shield/issues/10) |
| 앱 장애를 내고 복구되는지 확인 | M3·M5 / 11/02~10 | [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) |
| AWS OTT 웹·한국 API·캐나다 Store 연결 | M5·M3 / M1 외부 경로 협업 / 10/21~11/06 | [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |
| 최종 보고서·리허설·발표 | 전원 / PM 취합·PL 기술 검토 / 11/09~16 | [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) |

앱 개발은 M5, 게시판 배포는 M1·M2, 한국 OTT 배포는 M3입니다. **10/22~23 코드 골격 → 10/28 로컬 기능 → 10/30 기본 배포 → 11/06 실제 AI 자막·CI/CD 통합**을 목표로 합니다. 지연되면 관련 시험도 미수행으로 남기고 지원·범위를 팀에서 조정합니다.

## 6. 바뀌지 않는 설계·기록 원칙

- M1·M2: GNS3·UTM·동일한 업무 자산. 서버10·직원6·관리2·스위치10을 보존하고 같은 대표 규모부터 기동. 서버/관리는 독립 가상망, 직원/공통만 VLAN 사용.
- M2: 독일 별도 IP·DB·계정, Wazuh는 독일만 감시. 비교할 때 OS·앱·계정·횟수/간격·SSH 허용 조건을 한국과 맞추고 M1 차단 시험과 별도 상태 저장.
- M3: Suricata 없이 UTM을 각 서버망에 직접 연결. 나머지 서버 구성 유지. 개선 전 Spring 앱1개, 후2개·Nginx B/VIP. vCenter는 자원 확인 후 후속 기동.
- M4·M5: 기존 구역 유지. 별도 가상망에 불필요한 VLAN을 붙이지 않음. M5는 UTM 외부/운영/콘텐츠/관리 카드4개.
- M2·M3 Suricata 제외, 타국의 구 M2 Agent·로그 송신·관리 경로는 각 담당이 제거 여부 확인. 설계 변경과 실제 해제 완료는 구분.
- M3·M5는 Actions(빌드/검사)+Argo CD(배포), 기존 K8s/EKS 사용. S3 정적 배포는 별도. 새 로컬 CI VM 없음. 게시판 배포 방법은 실행 환경에 맞춰 결정.
- 10/23까지 본사–서비스 VPN 여부, 본사–백업 허용 업무, 한국 API 외부 공개, 캐나다 시간대·리전, AWS 예산·이미지 저장소를 관련 담당이 확인. 값이 미정이면 사람·기한을 적음.
- 정상 업무가 된 뒤 가짜 데이터로 시험. 설정·로그·스냅샷을 남기고 같은 조건으로 재시험. 32GB에서 전체 VM 동시 가동은 실제 자원 확인 후 판단.
- WBS=일정 / 업무 보드=상태 / Issue=작업 결과 / Notion=기술 기록. 현재 상태·체크·담당자를 문서 수정으로 완료 처리하지 않음.
- 토폴로지는 팀 작성본만 업로드. 비밀값·실제 교실 IP표는 팀 기술서에서 관리. M1 후속 실장비 간소화는 윤서영 주담당·박진혁 보조, 착수일 별도 협의.
