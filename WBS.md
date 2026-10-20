# OTTer Shield | 업무·일정 (WBS)

**Team Blocks · NetBlocks → OTTer**  
**프로젝트:** OTTer Shield — 한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅  
**운영:** 2026.10.19~11.16 · **킥오프:** 10.16 · **기본 작업:** 평일 09:00~18:00(점심 제외) · **발표:** 11.16

[프로젝트](README.md) · [계획서 v0.3](plans/project-plan-v0.3.pdf) · [10/20 결정사항](meetings/2026-10-20-design-decisions.md) · [업무 보드](https://github.com/orgs/team-blocks-lab/projects/4)

**10/20 개정 기준:** M2는 독일 본사·GNS3·독일 전용 Wazuh로 변경. M2·M3 Suricata 제외. M1·M4·M5 구성과 M3의 나머지 서버 구성은 유지합니다. 기존 Issue 번호·담당자·목표일·실제 진행 상태는 유지하며, 아래 날짜는 완료 실적이 아닌 목표입니다.

## 1. 전체 일정과 통과 기준

| 목표일 | 작업 | 완료 기준 |
|---|---|---|
| 10/19~20 | 설계 검토·명칭·M2 변경 반영 | 회의 결정·역할·변경 영향 정리. 이전 중앙 관제 의존성 제거 목록 |
| 10/21 오전 | 구축 가능한 팀 도면·환경 기준 확정 | NIC/VMnet·IP·자원·제품 버전·필요 통신·반환 경로·시험 범위·미확정 담당 확인 |
| 10/21 오후~23 | 승인 구역 AS-IS 구축·출구 확인 | VM→UTM→상위망, DNS·시간 동기화·실제 패키지 다운로드. 한국 API 공개·AWS 비용 판정 |
| 10/26~28 | 5개 망 정상 통신·선택 VPN·서비스 연결 | 한국–독일·본사–DR·한국–캐나다·서비스–DR VPN, 왕복 경로·NAT 예외·게시판·K8s/DB 확인 |
| 10/29~30 | M1·M2·M4 개선 전 시험 / M3·M5 배포·시험 준비 | S01·S02·S04 증거 3건, 10/30 OTT 기본 배포·Store 최소 기능 가용성 판정 |
| 11/02 | M3·M5 개선 전 시험·결과 취합 | S03·S05 포함 총 5건. 정상 기능·원인·미시험 범위 기록 |
| 11/03~06 | TO-BE·독일 Wazuh·AI·클라우드·DR 통합 | 11/03 개선안 검토, 11/05 첫 DB 복제 목표, 11/06 AI 자막·배포·S3 복원 1차 |
| 11/09~10 | 같은 조건 재시험·장애·복구·정상 업무 | 5건 전후 대조, 독일 Wazuh 경보/자동 대응, APP 장애·DB 복원 검증 |
| 11/11~13 | 보고·발표 준비 | 11/11 증거 정리 → 11/12 발표자료 → 11/13 전원 리허설 |
| 11/16 | 최종 발표 | 사전 환경 점검·시연·기여 설명 |

## 2. 담당별 작업과 Issue

각 행의 Issue를 순서대로 진행합니다. 상세 체크리스트·선행조건은 Issue, 설정·실험 증거는 담당 Notion 기술서에 기록합니다.

| 담당 | 설계 ~10/23 | AS-IS ~10/28 | 개선 전 시험 | TO-BE ~11/06 | 재시험 ~11/10 | 결과 ~11/13 |
|---|---|---|---|---|---|---|
| **M1 유용수** | 한국 본사·GNS3·UTM·직원 VLAN [#1](https://github.com/team-blocks-lab/otter-shield/issues/1) | 정상 통신·서비스 [#14](https://github.com/team-blocks-lab/otter-shield/issues/14) | 10/29~30 [#15](https://github.com/team-blocks-lab/otter-shield/issues/15) | 개선안·적용 [#16](https://github.com/team-blocks-lab/otter-shield/issues/16) | 전후·정상 업무 [#17](https://github.com/team-blocks-lab/otter-shield/issues/17) | 증거·시연 [#18](https://github.com/team-blocks-lab/otter-shield/issues/18) |
| **M2 윤서영** | 독일 본사·GNS3·공통 게시판·독일 Wazuh [#2](https://github.com/team-blocks-lab/otter-shield/issues/2) | 정상 통신·서비스 [#19](https://github.com/team-blocks-lab/otter-shield/issues/19) | 10/29~30 [#20](https://github.com/team-blocks-lab/otter-shield/issues/20) | 개선안·적용 [#21](https://github.com/team-blocks-lab/otter-shield/issues/21) | 전후·정상 업무 [#22](https://github.com/team-blocks-lab/otter-shield/issues/22) | 증거·시연 [#23](https://github.com/team-blocks-lab/otter-shield/issues/23) |
| **M3 홍은서·PL** | 한국 서비스·가상화·K8s·DB·배포 [#3](https://github.com/team-blocks-lab/otter-shield/issues/3) | 정상 통신·서비스 [#24](https://github.com/team-blocks-lab/otter-shield/issues/24) | 11/02 [#25](https://github.com/team-blocks-lab/otter-shield/issues/25) | 개선안·적용 [#26](https://github.com/team-blocks-lab/otter-shield/issues/26) | 전후·정상 업무 [#27](https://github.com/team-blocks-lab/otter-shield/issues/27) | 증거·시연 [#28](https://github.com/team-blocks-lab/otter-shield/issues/28) |
| **M4 박진혁** | 백업·Replica·S3·격리 복원 [#4](https://github.com/team-blocks-lab/otter-shield/issues/4) | 정상 통신·서비스 [#29](https://github.com/team-blocks-lab/otter-shield/issues/29) | 10/29~30 [#30](https://github.com/team-blocks-lab/otter-shield/issues/30) | 개선안·적용 [#31](https://github.com/team-blocks-lab/otter-shield/issues/31) | 전후·정상 업무 [#32](https://github.com/team-blocks-lab/otter-shield/issues/32) | 증거·시연 [#33](https://github.com/team-blocks-lab/otter-shield/issues/33) |
| **M5 유은혜·PM** | 캐나다·VPN·앱/AI·Store·PM [#5](https://github.com/team-blocks-lab/otter-shield/issues/5) | 정상 통신·서비스 [#34](https://github.com/team-blocks-lab/otter-shield/issues/34) | 11/02 [#35](https://github.com/team-blocks-lab/otter-shield/issues/35) | 개선안·적용 [#36](https://github.com/team-blocks-lab/otter-shield/issues/36) | 전후·정상 업무 [#37](https://github.com/team-blocks-lab/otter-shield/issues/37) | 증거·시연 [#38](https://github.com/team-blocks-lab/otter-shield/issues/38) |

| 망 | 실제 작업 범위·확인 기준 |
|---|---|
| M1 | GNS3 R1·L2 스위치·UTM. 업무 서버10·직원6·관리2·스위치10 보존. DMZ/서버/관리 독립 VMnet, 직원·공통만 VLAN trunk. 게시판·DNS·DHCP·공유·백업·VPN 정상 확인 |
| M2 | M1과 같은 업무 자산·연결 구조·게시판, 독일 별도 IP/DB/계정. AS-IS 정상 업무·원본 로그 확보, TO-BE Wazuh1 추가·독일 Agent 대상18. 양국 같은 대표 자산부터 단계 기동 |
| M3 | R3(VyOS)·UTM→DMZ/APP/DATA/MGMT VMnet 직접 연결. Nginx·ESXi·K8s CP1/Worker2·Primary/Test DB 유지. AS-IS Spring1 Pod, TO-BE 2 Pod·Nginx B/VIP. vCenter는 자원 확인 후 후속 기동 |
| M4 | UTM·백업/복제 독립 VMnet, 백업·복제 계정·TLS·권한·읽기 감사. M3 DB dump→해시→S3→격리 EC2 복원·데이터 비교. 복제와 백업/복원은 각각 증거 확보 |
| M5 | UTM 외부+운영+콘텐츠+관리 NIC4, VLAN 없음. 본사 VPN·게시판·DNS·AWS Store 유지. 전체 앱 코드 개발 담당. 인프라·개발·PM 결과를 별도로 검증 |

## 3. 공동 업무

| Issue | 작업 | 주관·협업 | 기간 |
|---|---|---|---|
| [#6](https://github.com/team-blocks-lab/otter-shield/issues/6) | 설계·교실망·NIC·정확 버전·자원·필요 통신·미확정 정리 | PM 취합·PL 기술 통합·전원 | 10/19~23 |
| [#7](https://github.com/team-blocks-lab/otter-shield/issues/7) | 5개 망 라우팅·선택 VPN·DNS·정상/금지 경로 통합 | M1·각 망 담당(M2 독일 포함) | 10/26~28 |
| [#8](https://github.com/team-blocks-lab/otter-shield/issues/8) | M1·M2 공통 게시판 / OTT·AI / Store 코드·실행 계약·배포 | M5 개발·M1/M2 게시판 배포·M3 OTT 배포 | 10/19~11/06 |
| [#9](https://github.com/team-blocks-lab/otter-shield/issues/9) | 독일 Wazuh·Agent·동일 조건 비교·선정 자동 대응 | M2 주관·M1 비교 조건 대조 | 10/26~11/06 |
| [#10](https://github.com/team-blocks-lab/otter-shield/issues/10) | MySQL Replica·백업·S3·격리 복원 | M4·M3 | 10/26~11/10 |
| [#11](https://github.com/team-blocks-lab/otter-shield/issues/11) | Spring 2 Pod 분산·APP/Worker 장애·복구 | M3·M5 | 11/02~10 |
| [#12](https://github.com/team-blocks-lab/otter-shield/issues/12) | OTT S3/CloudFront·한국 API / 캐나다 Store ALB/EKS/RDS | M5·M3·M1 외부 경로 | 10/21~11/06 |
| [#13](https://github.com/team-blocks-lab/otter-shield/issues/13) | 최종 보고·발표자료·리허설·발표 | 전원 | 11/09~16 |

## 4. 공격·개선·정상 기능 기준

| 번호 | 개선 전 시험 | 개선 후 검증 | 함께 유지할 정상 업무 |
|---|---|---|---|
| S01 M1 | 직원→본사 WAS SSH 접근 | UTM1 거부·로그 | 관리 PC SSH·게시판 |
| S02 M2 | 독일 직원 시험 PC→독일 WAS 반복 SSH 인증 실패 | Wazuh 경보·선정 자동 대응·실제 호스트 차단·해제 | 관리자 SSH·독일 게시판 |
| S03 M3 | M1 직원 시험 PC→K8s API 관리 포트 | UTM3 거부. 포트 도달과 인증/RBAC 결과 구분 | 승인 관리자·클러스터·Argo CD |
| S04 M4 | 시험 계정의 가짜 백업 파일 읽기 | owner/group/mode 거부·읽기 감사 | 승인 백업·복제·복원 |
| S05 M5 | 캐나다 직원→업무 VPN·M1→M3 격리 Test DB | UTM3 거부·로그. 운영 DB/RDS 취약화 없음 | 게시판·OTT API·Store·백업 |

**한국·독일 비교 조건:** 같은 OS·앱·계정 정책·시험 횟수/간격·동시 기동 규모·UTM SSH 허용. S01 차단 상태와 분리된 스냅샷으로 S02를 비교합니다. Wazuh 설치 자체를 차단 성공으로 판단하지 않습니다.

## 5. 개발·배포 병행 일정

| 목표 | M5 코드·AWS | 배포·협업 |
|---|---|---|
| 10/22~23 | 공통 게시판·OTT·Store의 최소 기능/API/ERD·Class·실행 골격, Store 작업량·AWS 비용 판정 | M1/M2 게시판 실행 환경, M3 앱·DB·컨테이너 실행 계약 |
| 10/26~28 | 로컬 로그인·권한·목록·샘플 영상, 국가별 게시판 설정 분리 | 각 망 기본 연결, M3 K8s/DB·캐나다 VPN과 병행 |
| 10/29~30 | OTT 기본 배포·샘플 영상, 최소 Store 상품 조회/모의 주문 가용성 점검 | 정상 업무 확인 후 S03·S05 준비. 미완료면 시험 의존성 차단 기록 |
| 11/03~06 | 실제 STT·한영 SRT/VTT·React 표시, Actions→이미지/배포 Git→Argo CD | M3 OTT/AI·M5 EKS 배포, S3 정적 배포 별도. 게시판 배포 방식 확정 필요 |
| 11/09~10 | 정상 요청·보안 재시험·배포 되돌리기 | 서비스별 결과·이미지/커밋·증거 대조 |

별도 로컬 CI VM은 추가하지 않습니다. M5 업무를 M3에게 임의 이관하지 않습니다. 10/23·10/28·10/30 점검에서 지연 시 지원·범위·일정을 팀이 재협의합니다.

## 6. 구축 전 확인·변경 관리

- **10/21 오전 / 전원·PL:** 교실 경계 IP, NIC/MAC/VMnet, 게이트웨이·정적 경로·NAT 예외, 정확 제품 버전·이미지·자원표. 서버·내부 단말의 우회 Bridged/NAT NIC 제거. VMnet 번호는 PC 내부에서만 의미가 있음.
- **10/21 오전 / M2·전원:** 구 M2 원격 Agent·등록키·Syslog·허용 규칙·라우트·관리 중계 의존성 대조. 독일 외 망은 현지 로그 보관. 설계 수정과 실제 해제 완료를 구분.
- **10/23 / 각 망 담당:** DNS·시간 동기화·인증서·인터넷 설치·실제 다운로드. 한국/독일 시간대와 UTC 증거 대조, 캐나다 도시/시간대·AWS 리전 확정.
- **10/23 / M1·M3·M4:** 본사–서비스 구간 VPN 여부, 본사–DR VPN의 정확한 허용 업무·포트 확정. 기존 허용을 무조건 전체 개방으로 바꾸지 않음.
- **10/23 / M1·M3·M5·계정 담당:** 한국 API 외부 공개를 위한 상위 NAT/DNS/TLS, AWS 예산·출구/NAT·IAM·SSM 관리·이미지 저장소 확인. API 공개 불가면 CDN과 내부 API의 검증 증거를 분리.
- **10/28 / M1+전원:** 한국–독일·본사–DR·한국–캐나다·서비스–DR VPN의 보호 대역·인증·왕복 경로·NAT 예외 일치. 도면에는 T14 같은 약어 대신 연결 대상 이름 사용.
- **시험 선행조건:** 승인 범위·가짜 데이터·정상 업무·원본 로그·복구 스냅샷 확보. AS-IS 증거 전에 TO-BE로 덮어쓰지 않음. 연결 실패는 라우팅 오류와 정책 차단을 구분.
- **기록:** WBS=일정, Projects=상태, Issue=작업/결과, Notion=설정/증거. 기존 Projects 상태·날짜는 실적을 확인하여 담당자가 갱신하며 문서 개정으로 완료 처리하지 않음.
- **공개 범위:** 비밀값·실제 내부 IP표는 비공개 기술서에서 관리. 계획서 v0.1~v0.3은 당시 기록으로 보존. 팀 작성 토폴로지만 설계 폴더에 등록.
- **후속 업무:** M1 실장비 간소화 설계 주담당 윤서영·보조 박진혁. 본 실습의 선행조건으로 추가하지 않고 실장비 조건 확인 후 착수일 협의.
