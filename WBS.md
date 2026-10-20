# OTTer Shield | WBS 및 수행 일정

**프로젝트:** OTTer Shield — 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅  
**팀:** Team Blocks · **운영:** 2026.10.19~11.16 · **최종 발표:** 11.16  
**개정 기준:** 2026.10.20 — AS-IS 설계·구축, 공격·분석, TO-BE 설계·구현, 재검증 단계 분리

[계획서 v0.3](plans/project-plan-v0.3.pdf) · [회의록](meetings/2026-10-20-design-decisions.md) · [팀 업무 보드](https://github.com/orgs/team-blocks-lab/projects/4/views/2) · [토폴로지](design/토폴로지/README.md)

## 1. 수행 기준

- **10/20:** 각자 AS-IS(개선 전) 도면만 작성·업로드. **10/21:** 망 구축 시작.
- TO-BE(개선 후)는 실제 공격 결과·원인 분석 후 설계합니다. 현재 논의한 보안 기술은 개선 후보이며 상세 도면·정책 확정본이 아닙니다.
- 기존 AS-IS 기반을 재사용합니다. 정책·권한 변경과 Wazuh/Replica/이중화 신규 설치를 구분하며, 구현2일·통합1일을 목표로 배정합니다.
- 날짜·기간은 **계획값**이며 완료 실적이 아닙니다. 기간은 평일 기준 경과 일수로 개인별 투입 공수가 아닙니다. 같은 날/기간의 작업은 병행 또는 순차 검토합니다.

## 2. 단계별 일정·산출물·선행조건

| WBS ID | 작업 | 시작 | 종료 | 기간 | 주관 | 선행조건 | 산출물·종료 기준 | Issue |
|---|---|---|---|---|---|---|---|---|
| 1.1 | AS-IS 토폴로지 작성 | 10/20 | 10/20 | 1일 | 각 망 담당 | 기존 합의 | draw.io·PNG, 장비/구역·정상/시험 경로 | [#1](https://github.com/team-blocks-lab/otter-shield/issues/1)~[#5](https://github.com/team-blocks-lab/otter-shield/issues/5) |
| 1.2 | 망 간 연결·시험 범위 검토 | 10/20 | 10/20 | 1일 | PL·각 망 담당 | 1.1 초안 | 연결 상대·필요 통신·미정 담당 기록 | [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) |
| 2.1 | 가상 장비·기본망 구축 | 10/21 | 10/23 | 3일 | 각 망 담당 | 1.1·1.2 해당 구간 | 장비/OS·IP·DNS·시간·설치 인터넷 확인 | [#14](https://github.com/team-blocks-lab/otter-shield/issues/14)/[#19](https://github.com/team-blocks-lab/otter-shield/issues/19)/[#24](https://github.com/team-blocks-lab/otter-shield/issues/24)/[#29](https://github.com/team-blocks-lab/otter-shield/issues/29)/[#34](https://github.com/team-blocks-lab/otter-shield/issues/34) |
| 2.2 | 업무 서비스·망 간 연결 | 10/26 | 10/28 | 3일 | 각 망 담당·M1 통합 | 2.1 | 게시판·관리·DB·VPN 등 정상 업무·원본 로그 | [#7](https://github.com/team-blocks-lab/otter-shield/issues/7)·구축 이슈 |
| 2.3 | 앱 기본 기능·배포 | 10/22 | 10/30 | 7일 | M5 개발·M1/M2/M3 배포 | 실행 조건 합의; 서버 준비와 병행 | 10/28 로컬 기능, 10/30 배포·정상 요청 증거 | [#8](https://github.com/team-blocks-lab/otter-shield/issues/8)/[#12](https://github.com/team-blocks-lab/otter-shield/issues/12) |
| 3.1 | AS-IS 공격 S01·S02·S04 | 10/29 | 10/30 | 2일 | M1·M2·M4 | 해당 2.2 정상 기능 | 입력·원본 로그·결과·원인 기록 | [#15](https://github.com/team-blocks-lab/otter-shield/issues/15)/[#20](https://github.com/team-blocks-lab/otter-shield/issues/20)/[#30](https://github.com/team-blocks-lab/otter-shield/issues/30) |
| 3.2 | AS-IS 공격 S03·S05 | 11/02 | 11/02 | 1일 | M3·M5·M1 경로 협업 | 해당 2.2·2.3 | 관리 API·격리 Test DB 시험 증거 | [#25](https://github.com/team-blocks-lab/otter-shield/issues/25)/[#35](https://github.com/team-blocks-lab/otter-shield/issues/35) |
| 3.3 | 취약점 분석·개선요구 정리 | 11/02 | 11/02 | 1일 | 각 망 담당·PL 취합 | 각 시나리오 공격 결과 | 문제/원인/영향/개선 요구·우선순위 | 공격 이슈5건 |
| 4.1 | TO-BE 토폴로지·정책 설계 | 11/03 | 11/03 | 1일 | 각 망 담당 | 3.3 해당 분석 | AS-IS 재사용/추가/설정 변경이 표시된 도면·변경표 | [#16](https://github.com/team-blocks-lab/otter-shield/issues/16)/[#21](https://github.com/team-blocks-lab/otter-shield/issues/21)/[#26](https://github.com/team-blocks-lab/otter-shield/issues/26)/[#31](https://github.com/team-blocks-lab/otter-shield/issues/31)/[#36](https://github.com/team-blocks-lab/otter-shield/issues/36) |
| 4.2 | 변경 검토·구현 준비 | 11/03 | 11/03 | 1일 | 관련 망 담당·PL | 4.1 초안부터 순차 | 허용/차단·자원·적용 순서·롤백 검토 | 동일 개선 이슈 |
| 4.3 | TO-BE 구현 | 11/04 | 11/05 | 2일 | 각 망 담당 | 해당 4.1·4.2 검토 | 설정/설치 증거·정상 기능·AS-IS 보존 | 개선 이슈·[#9](https://github.com/team-blocks-lab/otter-shield/issues/9)/[#10](https://github.com/team-blocks-lab/otter-shield/issues/10) |
| 4.4 | 통합 확인·실제 도면 반영 | 11/06 | 11/06 | 1일 | PL·각 망 담당 | 4.3 | 교차 연결·정상 업무·실제 도면 일치·재시험 준비 | 개선 이슈·[#7](https://github.com/team-blocks-lab/otter-shield/issues/7) |
| 5.1 | 동일 조건 재공격·장애/복구 | 11/09 | 11/10 | 2일 | 각 망 담당 | 해당 4.4 | 전후 비교5건·정상 업무·차단/탐지·복원 증거 | [#17](https://github.com/team-blocks-lab/otter-shield/issues/17)/[#22](https://github.com/team-blocks-lab/otter-shield/issues/22)/[#27](https://github.com/team-blocks-lab/otter-shield/issues/27)/[#32](https://github.com/team-blocks-lab/otter-shield/issues/32)/[#37](https://github.com/team-blocks-lab/otter-shield/issues/37)·[#10](https://github.com/team-blocks-lab/otter-shield/issues/10)/[#11](https://github.com/team-blocks-lab/otter-shield/issues/11) |
| 5.2 | 오류 수정·영향 범위 재확인 | 11/11 | 11/11 | 1일 | 해당 담당·PL | 5.1 | 남은 오류 판정·관련 시험 재확인·제약 기록 | 재시험 이슈 |
| 6.1 | 보고서·발표자료 취합 | 11/11 | 11/12 | 2일 | PM 취합·전원 | 검증 결과; 초안은 선행 가능 | 도면·구축·전후 증거·기여·한계 연결 | [#13](https://github.com/team-blocks-lab/otter-shield/issues/13)·담당 결과 이슈 |
| 6.2 | 전체 리허설 | 11/13 | 11/13 | 1일 | 전원 | 6.1 | 시간·연결·시연·대체 증거 확인 | [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) |
| 6.3 | 최종 발표 | 11/16 | 11/16 | 1일 | 전원 | 6.2 | 환경 점검·발표·시연 | [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) |

3.3은 각 담당이 자기 공격 결과부터 분석하고 11/02 취합합니다. 4.1·4.2는 같은 날 초안별 순차 검토하며 별도 이틀 공수로 합산하지 않습니다. 미검토 구간은 구현하지 않고 독립된 준비 작업을 진행합니다.

## 3. 담당별 업무 패키지

| 담당·범위 | AS-IS 설계 10/20 | 구축 ~10/28 | 공격·분석 | TO-BE 설계 11/03·구현 11/04~06 | 재검증 ~11/10 | 결과 ~11/13 |
|---|---|---|---|---|---|---|
| **M1 유용수** / 한국 본사·GNS3·UTM·VPN | [#1](https://github.com/team-blocks-lab/otter-shield/issues/1) | [#14](https://github.com/team-blocks-lab/otter-shield/issues/14) | 10/29~30 [#15](https://github.com/team-blocks-lab/otter-shield/issues/15) | [#16](https://github.com/team-blocks-lab/otter-shield/issues/16) | [#17](https://github.com/team-blocks-lab/otter-shield/issues/17) | [#18](https://github.com/team-blocks-lab/otter-shield/issues/18) |
| **M2 윤서영** / 독일 본사·공통 게시판·독일 보안 | [#2](https://github.com/team-blocks-lab/otter-shield/issues/2) | [#19](https://github.com/team-blocks-lab/otter-shield/issues/19) | 10/29~30 [#20](https://github.com/team-blocks-lab/otter-shield/issues/20) | [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) | [#22](https://github.com/team-blocks-lab/otter-shield/issues/22) | [#23](https://github.com/team-blocks-lab/otter-shield/issues/23) |
| **M3 홍은서·PL** / 한국 서비스·가상화·K8s·DB | [#3](https://github.com/team-blocks-lab/otter-shield/issues/3) | [#24](https://github.com/team-blocks-lab/otter-shield/issues/24) | 11/02 [#25](https://github.com/team-blocks-lab/otter-shield/issues/25) | [#26](https://github.com/team-blocks-lab/otter-shield/issues/26) | [#27](https://github.com/team-blocks-lab/otter-shield/issues/27) | [#28](https://github.com/team-blocks-lab/otter-shield/issues/28) |
| **M4 박진혁** / 백업·복제·S3·격리 복원 | [#4](https://github.com/team-blocks-lab/otter-shield/issues/4) | [#29](https://github.com/team-blocks-lab/otter-shield/issues/29) | 10/29~30 [#30](https://github.com/team-blocks-lab/otter-shield/issues/30) | [#31](https://github.com/team-blocks-lab/otter-shield/issues/31) | [#32](https://github.com/team-blocks-lab/otter-shield/issues/32) | [#33](https://github.com/team-blocks-lab/otter-shield/issues/33) |
| **M5 유은혜·PM** / 캐나다·전체 앱/AI·Store·PM | [#5](https://github.com/team-blocks-lab/otter-shield/issues/5) | [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) | 11/02 [#35](https://github.com/team-blocks-lab/otter-shield/issues/35) | [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) | [#37](https://github.com/team-blocks-lab/otter-shield/issues/37) | [#38](https://github.com/team-blocks-lab/otter-shield/issues/38) |

각 단계의 체크리스트·증거는 연결된 기존 Issue를 사용합니다. TO-BE 설계와 구현을 같은 Issue 안에서 별도 구간으로 관리하며 동일 작업을 공동 Issue와 중복 실적으로 세지 않습니다.

## 4. 공동 작업·병행 일정

| 작업·Issue | 책임 | 일정·종료 기준 |
|---|---|---|
| AS-IS 연결 검토·실행 환경 확인 [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) | PM 취합·PL 통합·전원 | 10/20 도면, 10/21~23 실제 버전·자원·설치 출구 |
| 망 간 통신·VPN 통합 [#7](https://github.com/team-blocks-lab/otter-shield/issues/7) | M1·전원 | 10/26~28 정상 연결, TO-BE 적용 후 11/06 영향 확인 |
| 공통 게시판·OTT·AI·Store 개발/배포 [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) | M5 코드·M1/M2/M3 배포 | 10/22~23 골격 → 10/28 로컬 기능 → 10/30 기본 배포 → 11/06 AI·CI/CD 통합 |
| 독일 Wazuh 도입·비교 [#9](https://github.com/team-blocks-lab/otter-shield/issues/9) | M2·M1 비교 검토 | 사양·로그 확인은 AS-IS와 병행, 공격 후11/03 설계·11/04~05 설치·11/06 통합 |
| DB 복제·S3·복원 [#10](https://github.com/team-blocks-lab/otter-shield/issues/10) | M4·M3 | 10/30 백업·복원 준비, 11/03 설계, 11/04~05 복제/첫 복원, 11/06 S3 복원·11/10 최종 검증 |
| 앱·노드·Nginx 장애 시험 [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) | M3·M5 | 11/02~03 절차 준비, 이중화 구현 후11/06 사전 확인·11/09~10 최종 시험 |
| AWS 웹/API·캐나다 Store [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) | M5·M3·M1 경로 | 10/23 비용·공개 경로 판정, 10/30 기본 기능 목표, 11/06 연동 |
| 보고·발표 [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) | PM 취합·PL 기술 검토·전원 | 11/11~12 취합, 11/13 리허설, 11/16 발표 |

## 5. 단계 종료 기준

| 단계 | 다음 단계로 넘어가기 위한 조건 |
|---|---|
| AS-IS 설계 | 장비·구역·연결·정상/시험 경로와 미정 담당이 도면에 표시됨 |
| AS-IS 구축 | 해당 서비스 정상 동작·시험 대상 준비·원본 로그·초기 스냅샷 확보. 실제 구성에 맞춰 AS-IS 도면 갱신 |
| 공격·분석 | 승인된 가짜 데이터로 실제 결과·원인·영향·개선 요구 기록. 단순 연결과 인증 우회는 구분 |
| TO-BE 설계 | 각 취약점에 대응하는 도면·정책 변경표·추가 장비·자원·롤백·검증 방법을 관련 담당과 PL이 검토 |
| TO-BE 구현 | 기존 기반에 검토한 변경 적용·정상 업무 확인·실제 도면/설정 일치 |
| 재검증 | 동일 조건 공격 전후 비교·정상 업무·장애/복원 증거와 잔여 위험 확인 |

TO-BE 도면은 연결선이 같을 수 있습니다. 이때도 **접근 정책·로그 수집·변경 설정**이 어떻게 달라졌는지 표기하며, 의미 없는 장비를 추가하지 않습니다.

## 6. 자원·일정 위험 및 운영

- **M2 신규 설치:** Wazuh·Agent·규칙·자동 대응은 방화벽 규칙 한 줄 변경과 다릅니다. 11/04~05 대표 장비에서 설치/탐지/대응을 검증하고 11/06 통합합니다. 전체18대 등록은 자원·시간을 보고 단계 확대하며 미수행 대상을 적습니다.
- **M3·M4 신규 구성:** Nginx VIP·앱 분산·Replica는 기존 OS/망을 재사용해도 연결·장애·복원 시험이 필요합니다. 단순 설정 변경과 별도 산출물로 확인합니다.
- **M5 병행 부하:** 캐나다 구축·게시판/OTT/Store·AI·AWS·PM이 집중됩니다. 10/23 기능 범위/비용, 10/28 로컬 기능, 10/30 배포 실적을 점검합니다. 지연 시 지원·우선순위·범위를 팀이 결정하며 미완료를 완료로 표시하지 않습니다.
- **선행 지연:** 서비스가 안 되면 해당 공격 시험은 대기합니다. 선행 미완료를 숨겨 TO-BE를 먼저 적용하지 않고, 전체 구축과 무관한 독립 준비는 진행합니다.
- **완충:** 11/06은 통합, 11/11은 오류 수정·증거 확정 시간을 확보합니다. 추가 수정 후에는 영향받은 시험만 다시 확인합니다. 주말11/14~15는 필수 작업일로 잡지 않습니다.
- **기록:** WBS=작업·일정, 업무 보드=진행 상태, Issue=체크·결과, Notion=실제 설정/증거. 기존 Issue 번호·담당자·체크·진행 상태는 유지합니다.
- **설계 유지:** M1·M2 동등 업무 자산/GNS3, 독일만 Wazuh, M2·M3 Suricata 제외, M3 나머지 서버·M1/M4/M5 유지. 국가별 DB·계정·IP는 분리합니다. 세부 배치·실제 주소·버전은 팀 기술서에 기록합니다.
- **미정 확인 ~10/23:** 실제 교실 경계 IP·32GB 자원, 본사–서비스 VPN 여부·본사–DR 허용 업무, 한국 API 공개, 캐나다 도시/리전·AWS 예산·이미지 저장소를 관련 담당이 확인합니다.
- **후속 범위:** M1 실장비 간소화는 윤서영 주담당·박진혁 보조이며 별도 착수일 협의. 현재 가상망의 임의 축소 작업으로 바꾸지 않습니다.
