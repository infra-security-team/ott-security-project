# 실행 환경·버전 기준과 장비 명세

**2026.10.20 설계 단계 · Team Blocks / OTTer Shield**

이 문서는 실제 설치 정보를 꾸며 채우지 않습니다. **확인**은 사용자 제공 정보, **설계/제안**은 적용할 배치, **미확인/미선정**은 설치 증거·선택이 없는 항목입니다. 참고한 Suricata 7.0.15 문서는 실제 설치 버전 확정값이 아닙니다. Sophos UTM은 사용자 표기 **9.0**까지만 확인했으며 정확한 `9.xxx-build`와 라이선스는 확인이 필요합니다.

독자는 연결도에서 장비 ID를 찾고 아래 명세에서 수량·실행 환경·OS/제품·버전 상태·실제 기능을 확인합니다. 내부 주소·NIC MAC·세부 설정·원본 증거는 팀 공유 PDF와 권한 있는 기술서에 둡니다.

## 실제로 어디에서 실행되는가

| 구역 | 실행 계층 | 배치 경계 |
|---|---|---|
| M1 | Windows → Workstation → GNS3 VM → R1·내장 L2 스위치·QEMU Linux 단말 제안 | UTM1은 별도 appliance VM. GNS3 이미지·서버 OS·중첩 실행은 미확정 |
| M2 | Windows → Workstation → R2·UTM2·센서·Wazuh·시험/관리 VM | Wazuh 중앙 한 세트, 대상별 Agent. M2가 원격 모든 패킷을 수집하는 구성 아님 |
| M3 | Windows → Workstation → R3·UTM3·센서·Nginx·DB / nested ESXi → CP·Worker | 앱·Argo CD는 K8s Pod. vCenter는 후속 관리 학습용, 정확 build·호환성 확인 필요 |
| M4 | Windows → Workstation → UTM4·백업·복제·단말 / AWS S3·EC2 | S3는 VM이 아닌 관리형 저장소. 독립 복원 EC2는 AMI·비용·리전 확인 필요 |
| M5 | Windows 개발 → GitHub Actions → 이미지·배포 Git → M3 K8s·AWS EKS의 Argo CD | 사내 UTM5·직원/관리 VM과 AWS Store 분리. 로컬 CI/CD VM 추가 없음 |

## 문서와 실제 설정을 연결하는 필수 기록

각 자산은 **장비 ID / 담당 / 설계·설치·가동·검증 상태 / 실행 호스트 / 이미지 파일명·SHA256 또는 AMI ID / OS 릴리스·kernel / 제품 버전·build / vCPU·RAM·디스크 / NIC 개수·MAC·VMnet 또는 포트그룹 / IP·GW·DNS / 허용 포트 / 설정 파일 경로·백업 revision / 정상·보안 시험 증거**를 한 기록으로 연결합니다.

현재 자료에서 실제 vCPU·RAM·디스크 할당과 정확한 OS·제품 build가 확인되지 않았습니다. 호스트 RAM 각 32GB를 모든 VM 동시 기동 보장으로 해석하지 않습니다. 버전 미정인 장비는 최종 설정 완료로 표시하지 않습니다.

## 실행 환경·버전 | 확인된 정보와 아직 없는 정보

| 장비·수량 / 상태 | OS·제품·버전 상태 | 기능·필수 설정·검증 |
|---|---|---|
| HOST-M1~M5 / 물리 PC 5대 | 확인: Windows PC·RAM 각 32GB<br>미확인: Windows 에디션·빌드, CPU·SSD | Windows 시스템 정보로 CPU 가상화·OS 빌드 기록. 기존 PC 간 웹 접속과 새 내부망 왕복 시험은 구분. |
| HYP-M1~M5 / 외부 가상화 | VMware Workstation 사용 전제<br>정확한 제품판·버전·build 미확인 | About 화면으로 버전 기록. 내부 DHCP·호스트 어댑터 해제, NIC MAC·브리지 대상 고정. |
| M1-GNS3 / 1세트 | 설계: GNS3 GUI·server·GNS3 VM<br>각 구성요소의 정확 버전·이미지 미확인 | GUI/server 호환 확인. QEMU 중첩 실행·태그 전달·다중 MAC·교실 Cloud 연결을 먼저 시험. |
| M1-R1 / 1대<br>M1-SW / 10대 | R1: 라우터 OS·이미지·버전 미선정<br>SW: GNS3 내장 Ethernet switch 설계 | R1 이미지가 정적 라우팅·NAT를 지원해야 함. 스위치는 IOS 장비로 표기하지 않으며 GNS3 버전을 참조. |
| UTM1~UTM5 / 각 1대 | 확인: 사용자 명칭 Sophos UTM 9.0<br>정확한 9.xxx·build·라이선스 미확인 | UTM 대시보드에서 버전·라이선스·인터페이스 이름 기록. 9.7 참고 메뉴가 9.0에 같다고 단정하지 않음. |
| M2-R2·M3-R3 / 2대 | VyOS appliance VM<br>릴리스·build·이미지 형식 미확인 | show version·show interfaces 기록. 원격 사설망 정적 경로·인터넷 SNAT와 내부 NAT 예외 구분. |
| M3-ESXi / 1대<br>M3-vCenter / 후속 1대 | ESXi·vCenter 제품판·정확 build 미확인<br>호환성·가용 라이선스 확인 필요 | ESXi CPU 가상화 노출·APP/MGMT uplink 검증. vCenter는 선택 학습/RBAC 관리용, 단일 ESXi 운영의 필수 조건은 아님. |

## 소프트웨어 기준 | 버전·의존성을 확정해야 설정도 확정됨

| 장비·수량 / 상태 | OS·제품·버전 상태 | 기능·필수 설정·검증 |
|---|---|---|
| Linux 서버·단말 / M1~M5 | 배포판·릴리스·kernel 미선정/미확인 | /etc/os-release·uname·이미지 이름/SHA 기록. 패키지 설치법·NIC 이름·로그 경로가 OS에 따라 달라짐. |
| Suricata / M2·M3 | 실제 버전 미확인<br>7.0.15는 이번 문법 참고 문서 | suricata -V / --build-info·suricata -T 출력, 실제 config·rules 파일 hash와 NIC/MAC·모드 기록. |
| Wazuh / 중앙·Agent | 4.x 포트 기준 설계<br>Manager/Indexer/Dashboard/Agent 정확 버전 미확인 | 구성요소 버전 호환·실수신 포트·decoder/rule ID 기록. raw log 도착·alert 발생·차단을 별도 증명. |
| Nginx·TLS·Keepalived / M3 | 각 패키지·TLS library 버전 미확인 | nginx -V·패키지 버전·nginx -T·인증서/프록시/로그·VRRP 상태 기록. 비밀키는 공개 저장소 금지. |
| K8s·containerd·CNI / M3 | 서버/클라이언트·runtime·CNI 버전 미확인 | kubeadm/kubelet/kubectl·runtime·CNI 호환과 실행 포트/NetworkPolicy 지원 검증. 네트워크 대역을 명시적으로 지정. |
| MySQL / M3·M4·RDS | 서버/client/Replica/RDS engine 버전 미확인 | SELECT VERSION()·client 버전·dump 옵션·복제 호환·문자셋·TLS·실제 복원 결과를 함께 기록. |
| 앱 실행 / M1·M3·M5 | M1 게시판 stack 미선정<br>M3/M5 Java·Spring·Node/React·Python/FastAPI 미확정 | 의존성 lockfile·JDK/Python/Node·base image digest·환경변수 이름·포트·실행 명령·health/로그 계약 필요. |
| CI/CD / Actions·Argo CD | hosted runner image·action SHA<br>Argo CD 버전·Helm chart 미확정 | workflow·이미지 digest·Git SHA·Chart 버전·동기화 revision·Pod image를 연결. mutable latest만으로 결과 기록 금지. |
| 자원·구축 상태 / 모든 자산 | vCPU/RAM/디스크 실제 할당 미확인<br>Windows 호스트 RAM32GB만 확인 | 버전·이미지·NIC·자원 누락을 숨기지 않음. 대표 기능부터 기동하고 측정 후 HA·vCenter·전체 단말을 확장. |

## M1 장비 명세 | 서버 10·직원 6·관리 2·스위치 10 유지

| 장비·수량 / 상태 | OS·제품·버전 상태 | 기능·필수 설정·검증 |
|---|---|---|
| M1-WEB / 1대 | Linux OS·웹서버 종류/버전 미선정<br>사내 게시판 앱 코드 준비 전 | 직원·M5의 게시판 진입. WEB→WAS만 지정 허용, TLS 인증서·실행 포트·로그 확정 필요. |
| M1-DNS / 1대 | Linux OS·DNS daemon/버전 미선정 | 내부 포털·승인 시험 이름 조회. 내부 클라이언트만 허용, 외부 오픈 리졸버 금지. |
| M1-SFTP / 1대 | Linux OS·OpenSSH 버전 미확인 | 승인 서비스 파일 전달. 앱/운영 계정·업로드 경로·권한·인증 로그로 사용 증거 확보. |
| M1-WAS / 1대 | Linux OS·앱 런타임/버전 미선정 | 게시판 로직·권한 처리. WEB→WAS→DB 왕복. 구현 언어를 정한 뒤 포트를 확정해야 함. |
| M1-DB / 1대 | Linux OS·DB 엔진/버전 미선정 | 게시판 데이터 저장. 직원 직접 접속 차단, 앱 계정·백업 계정·복원 검증 분리. |
| M1-BACKUP / 1대 | Linux OS·백업 도구/버전 미선정 | 본사 데이터·설정 사본. 대상·주기·보존·M4 전달 방식을 정하고 실제 복원 결과 기록. |
| M1-LOG / 1대 | Linux OS·syslog 도구/버전 미선정 | 본사 로컬 운영 로그 보관. M2 Wazuh는 중앙 보안 분석. 중복 수집·이중 경보 방지 정책 필요. |
| M1-NFS / 1대 | Linux OS·NFS 버전 미확인 | 승인 Linux 서비스 파일 공유. 사용 클라이언트·export·NFS 버전을 정해 필요한 RPC 포트만 허용. |
| M1-SAMBA / 1대 | Linux OS·Samba 버전 미확인 | 부서 공유 자료·권한 분리. 실제 Windows/Linux 클라이언트와 사용자별 허용/거부 검사. |
| M1-DHCP / 1대 | Linux OS·DHCP 구현/버전 미선정 | 부서별 주소·GW·DNS 임대. 서버/관리 주소와 풀 중복 금지. VMware DHCP는 내부에서 끔. |
| 직원 PC / 6대 | Linux QEMU 배치 제안<br>기존 OS·이미지·정확 버전 미확인 | 부서 권한·포털·공유 시험. S01은 마케팅 PC1. SSH 필요 단말을 VPCS로 대체하지 않음. |
| 관리 PC / 2대 | 관리 OS·정확 버전 미확인 | 승인 관리·역할 분담·장애 시 접근. 두 단말 각각 관리 권한·사용 목적을 기록. |

## M2 장비 명세 | 보안 관제·SSH·시험·관리 역할 분리

| 장비·수량 / 상태 | OS·제품·버전 상태 | 기능·필수 설정·검증 |
|---|---|---|
| R2 / 1대 | VyOS / 정확 릴리스·build 미확인 | 교실·팀 내부망 라우팅. 인터넷 SNAT와 내부 주소 유지, M4·M5 관제 반환은 K4·K5 직접. |
| UTM2 / 1대 | Sophos UTM 9.0 사용자 표기<br>정확 build·라이선스 미확인 | S01 직원 SSH 경계 통제·승인 관리·SOC 진입. Suricata와 UTM IPS 차단을 구분. |
| WAZUH / 1대·중앙 1세트 | Linux OS 미선정 / Wazuh 4.x 설계<br>Manager·Indexer·Dashboard 버전 미확인 | 전 망 로그 수집·분석. Agent 등록·원문 수신·분석 경보를 각각 확인. 인덱서 외부 공개 금지. |
| SURICATA / 1대 | Linux OS 미선정 / 실제 버전 미확인<br>7.0.15는 문법 참고값 | SOC 통과 트래픽 IDS/IPS. SSH 비밀번호 실패 해독 불가. S02는 auth 로그로 분석. |
| SSH / 1대 | Linux OS·OpenSSH·Fail2ban 버전 미확인 | S01 로그인 경로 시험. S02 인증 실패 로그→Wazuh, Fail2ban 출발지 제한. |
| 승인 시험 PC / 1대 | Linux OS·시험 도구 버전 미확인 | S02 인증 실패·S03 API 노출 시험. 지정 계정·출발지·입력·횟수만 사용. |
| 관제 PC / 2대 | 클라이언트 OS·브라우저 버전 미확인 | Dashboard 관제. 2번은 교차 검토·시연용 목적을 부여할 때 기동하며 경계 보안 기능으로 과장하지 않음. |
| BASTION / TO-BE 1대 | Linux OS·OpenSSH 버전 미확인 | 승인 SSH 관리 중계. 관제 PC의 웹 화면 이용 역할과 구분. 접근·감사·개인 계정 필요. |

## M3 장비 명세 | 프록시·클러스터·DB·센서 실행 위치

| 장비·수량 / 상태 | OS·제품·버전 상태 | 기능·필수 설정·검증 |
|---|---|---|
| R3 / UTM3 / 각 1대 | VyOS / Sophos UTM 9.0 사용자 표기<br>정확 릴리스·build 미확인 | UTM은 구역 GW·T34·접근 정책. R3는 교실/내부 경로·인터넷 SNAT. M5 반환은 K1 경유. |
| SURICATA / 1대 | Linux OS 미선정 / 버전 미확인<br>7.0.15 문법 참고 | 독립 3쌍으로 전달. S05는 Nginx TLS 종료 뒤 APP HTTP를 직접 검사·drop. 다른 구역을 합치지 않음. |
| NGINX-A / 1대 | Linux OS·Nginx·TLS 라이브러리 버전 미확인 | React 실습 화면·/api·TLS 종료. S05는 A·Worker 고정, 쿼리·요청 ID 전달·upstream 로그. |
| NGINX-B / TO-BE 1대<br>VIP / 가상 주소 1개 | Linux OS·Nginx·Keepalived 버전 미확인 | VRRP 웹 진입점 전환. S05 전후 비교 중 HA 전환은 별도 시험. TCP443과 VRRP 통신 검증. |
| ESXi / 1대<br>vCenter / 후속 1대 | 정확 버전·build·상호 호환 미확인 | CP·Worker VM 운영. CPU 가상화·다중 MAC 전달·포트그룹 검증. vCenter 기능 학습은 자원 확보 후. |
| K8s CP / 1대<br>Worker / 2대 | Linux OS·K8s·containerd·CNI 버전 미확인 | CP API6443·노드 네트워크. 앱은 NodePort30080. Docker로 빌드해도 K8s 런타임을 Docker라고 단정하지 않음. |
| Spring·FastAPI·Argo CD / Pod | Java/Spring·Python/FastAPI·Argo CD<br>실제 이미지 태그·digest·Chart 버전 미확인 | OTT API·AI 처리·Git 배포. 앱 의존성/실행 포트·Secret·probe·요청 로그를 배포 계약으로 고정. |
| PRIMARY DB / 1대 | Linux OS·MySQL 정확 버전 미확인 | 앱 데이터·M4 백업·복제. 서비스 계정·TLS·스키마·복구 권한을 구분. |
| INTEGRATION DB / 1대 | Linux OS·MySQL 정확 버전 미확인 | 개발·스키마·통합 시험용, 운영 데이터와 분리. S05 대상 DB가 아니며 M5 직원 직접 접속을 열지 않음. |

## M4 장비 명세 | 백업·복제·격리 복원을 구분

| 장비·수량 / 상태 | OS·제품·버전 상태 | 기능·필수 설정·검증 |
|---|---|---|
| UTM4 / 1대 | Sophos UTM 9.0 사용자 표기<br>정확 build·라이선스 미확인 | T14 본사 업무·T34 Primary DB 접근. 관제는 K2 직접. 내부 NAT 예외·반환과 인터넷 NAT 구분. |
| BACKUP / 1대 | Linux OS·MySQL client·AWS CLI<br>백업 도구·auditd 버전 미확인 | 일관된 DB dump·파일 보관·S3 업로드. S04 가짜 파일 읽기 감사. 복원 결과·보존 주기 증거 확보. |
| REPLICA / TO-BE 1대 | Linux OS·MySQL 버전 미확인<br>Primary와 복제 호환 확인 필요 | 복제 지연·권한·read-only 동작 확인. 복제는 백업 파일·독립 복원을 대체하지 않음. |
| 운영 단말 / 2대 | 클라이언트 OS·정확 버전 미확인 | 승인 운영·복원 검증 담당. 서로 다른 권한·실습 역할을 기록한 단말만 기동. |
| 시험 단말 / 1대 | Linux OS·OpenSSH client 버전 미확인 | S04 기존 시험 계정 SSH 후 가짜 파일 읽기. 같은 L2라 UTM·네트워크 센서가 파일 읽기를 차단하지 않음. |
| AWS S3 / 버킷·객체 | 관리형 서비스: VM OS 없음<br>버킷 설정·리전·객체 버전 기록 | 원격 사본·암호화·버전/보존. 업로드 성공 외 실제 다운로드·복원·해시/데이터 비교 필요. |
| AWS EC2 / 격리 복원 시험 | AMI ID·OS·MySQL 버전 미확인<br>인스턴스 유형·리전·비용 미확정 | 운영 DB를 덮지 않고 복원·조회. 보안그룹·IAM·접근 경로·삭제/비용 종료 절차를 기록. |

## M5 장비 명세 | 개발 PC·사내망·AWS Store 분리

| 장비·수량 / 상태 | OS·제품·버전 상태 | 기능·필수 설정·검증 |
|---|---|---|
| HOST-M5 / 개발 PC 1대 | Windows OS·build·개발 도구 버전 미확인 | M1 게시판·M3 OTT/AI·M5 Store 코드 작성. 개발 위치와 배포 목적지 폴더를 구분. |
| UTM5 / 1대 | Sophos UTM 9.0 사용자 표기<br>정확 build·라이선스 미확인 | T15 본사 업무·S05 웹 경로. M2 관제 직접 경로·인터넷 NAT·VPN 보호 대상·반환 구분. |
| OPS 직원 / 2대 | 클라이언트 OS·버전 미확인 | 정상 OTT 업무. S05는 .101 고정, 지정 HTTPS 요청만 사용. 직원→DB 직접 접속은 전후 차단. |
| CONTENT 직원 / 2대 | 클라이언트 OS·버전 미확인 | 본사 DNS·게시판·콘텐츠 업무. OPS와 같은 권한을 무조건 주지 않고 정상 업무 검증. |
| 관리 단말 / 1대 | 관리 OS·SSH/AWS 도구 버전 미확인 | UTM·승인 Bastion·AWS 설정을 수행하는 사람의 단말. CI runner나 CD 서버로 기재하지 않음. |
| AWS EKS·ALB / 관리형+Worker | EKS K8s·Worker AMI·containerd 버전 미확인<br>Argo CD/Chart·앱 이미지 버전 미확인 | Store React/Spring Pod 배포. 리전 코드·노드 수·인스턴스·IAM·NAT·실제 비용을 확정해야 함. |
| AWS RDS / DB 인스턴스 | 관리형 MySQL 정확 engine version<br>인스턴스·파라미터그룹 미확정 | Store 상품·모의 주문 저장. M3 한국 MySQL과 별개 DB. 백업·복원·계정·암호화 설정 필요. |
| AWS 관리 EC2 / 추가 제안 1대 | AMI·OS·SSM Agent 버전 미확인<br>예산·IAM·출구 승인 전 미구현 | EKS private API 관리·Argo CD port-forward. 사내 VPN이 AWS로 자동 연결된다고 표시하지 않음. |
| GitHub Actions / Argo CD | Actions runner image·action commit SHA<br>Argo CD 이미지/Chart 버전 미확정 | 빌드→이미지 digest→배포 Git→동기화→실제 앱 확인. 별도 물리 PC·로컬 CI VM 추가 없음. |

## 변경과 인수 기준

- 연결도는 목표 구성을 표시하고 같은 쌍의 명세표에 AS-IS와 TO-BE에서 기동·허용·차단이 바뀌는 부분을 적습니다. 장비 자산 수와 VM·Pod·VIP·관리형 서비스 수를 구분합니다.
- M1의 서버 10·직원 6·관리 2·스위치 10은 포트폴리오 자산으로 보존합니다. 각 서버의 정상 기능 시험을 제출하고 32GB 제약은 단계별 기동·실측으로 관리합니다.
- S05는 [허용 웹 경로의 Suricata 직접 차단](scenarios/s05-web-ips.md)입니다. 실제 SQL 실행 없는 더미 API로 지정 패턴의 전달·탐지·차단을 비교합니다.
- 정확 버전·이미지·NIC·자원·핵심 설정을 기록하고 대표 정상 기능이 통과해야 해당 장비의 구축 기준선으로 승인합니다. 설치 버전을 알 수 없는 상태는 문서상 미해결 항목입니다.

[토폴로지 구성 안내](architecture.md) · [망별 가이드](network-guides/README.md) · [10/20 결정](../meetings/2026-10-20-design-decisions.md)
