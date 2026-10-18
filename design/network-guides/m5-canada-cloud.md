# M5 유은혜(PM) · 캐나다 지사망·AWS OTT 공개 웹·앱 개발

**Issue:** [설계 #5](https://github.com/infra-security-team/ott-security-project/issues/5) · [AS-IS #34](https://github.com/infra-security-team/ott-security-project/issues/34) · [통합 AWS #12](https://github.com/infra-security-team/ott-security-project/issues/12) · [OTT·AI 통합 #8](https://github.com/infra-security-team/ott-security-project/issues/8)

**경계:** 캐나다 **논리적 지사망**을 온프레미스 실습용 VMware/VyOS로 만들고, 고객용 **공개 HTTPS 웹**은 AWS로 배치하는 방안. 캐나다라는 이름만으로 AWS 물리 Region이 캐나다가 되거나 AWS까지 자동으로 VPN이 연결되는 것은 아닙니다.

## 사용할 프로그램/클라우드
- 망도: draw.io / 가상화: 학원 VMware/vSphere / 라우터: VyOS
- 지사 클라이언트: Ubuntu/Linux 또는 Windows VM
- VPN 검증: VyOS 인터페이스/라우팅/IPsec 상태, ping/tracepath, tcpdump, 서비스 포트 응답
- AWS: **v0.2 기본 제안은 캐나다 리전 S3 일반 비공개 버킷(React 빌드)+CloudFront HTTPS 및 OAC**, IAM 최소 권한·리전/권한/비용/인증서/API 공개 가능성 확인. 별도 백업 S3는 M4 담당. 필요 시 EC2 대안은 승인 후 검토(비용 승인 전 생성 금지).
- 앱 개발: React, Spring Boot, MySQL 연동 코드, FastAPI·음성 인식·번역, 한영 SRT/VTT 생성; 배포·DB 실행 환경은 **M3 담당**

## 구성 요소와 수량 구분
| 구성 | 시작 수량 | 역할 | 주의 |
|---|---:|---|---|
| CA-VyOS | 1 VMware VM | 직원/관리 VLAN 게이트웨이, 방화벽·필요 DHCP/NAT, 본사 VPN 종단 | 인터넷 출구와 VPN 보호 대역의 NAT 구분 |
| CA-Employee-PC | 1 VM | 직원망 DHCP/서비스 접근 및 S05 승인 공격 출발지 | 직원 PC를 여러 대 둘 필요 없음 |
| CA-Admin-PC | 1 VM | 관리망 승인 통신 시험 | 본사 관리망 Bastion 정책과 연결 확인 |
| CA-Web-Entry | 조건부 1 VM | 현지 사설 프록시/진입망 기능을 실제로 요구하는 경우 | AWS 공개 웹과 중복이면 설치 안 함 |
| AWS 웹 배포 | **S3 비공개 일반 버킷(캐나다 리전)+CloudFront+OAC 계획** | React 빌드/정적 리소스와 HTTPS | **v0.2 25쪽 제안**; 계정/비용/TLS/DNS 제약 시 승인 대체. S3 웹사이트 엔드포인트와 OAC 혼용 금지. CloudFront는 글로벌 CDN이므로 캐나다 내 데이터 처리 보장 뜻 아님 |
| AWS EC2 | 조건부 0~n | 서버 실행이 실제 필요한 경우에만 | 비용·권한·Region·보안그룹·종료 계획 확인 |
| AI/STT/LLM | 한국 APP 실행/외부 API | FastAPI와 실제 인식/번역·자막 생성 | 서비스 배치와 키 관리·시간 정보·비용 확인 |

## 10/19~21 오전 망도/설계에 넣을 것
1. 직원 VLAN·관리 VLAN·필요할 때만 서비스 진입 VLAN, 각 게이트웨이·CIDR·DHCP 범위.
2. CA-VyOS WAN·본사(M1) IPsec VPN 피어 및 VPN 보호 대역·라우트·리턴 경로.
3. 승인된 직원/관리 정상 경로(HTTPS 고객 웹 및 API, 관리 접속).
4. **AS-IS S05 격리 시험:** 캐나다 직원 → VPN → 한국 MySQL 직접 접근. 격리된 실습 DB에만 허용하고 인터넷 공개 금지. 포트 연결만으로 DB 인증 성공을 단정하지 않음.
5. **TO-BE 방향:** 직원 VLAN→한국 DB 직접 경로 차단, 정상 웹→API→DB 경로 유지.
6. **AWS 영역 별도:** 공개 웹(HTTPS) → 한국 API, 백업은 M4→S3. 인터넷 공개 경로와 **내부 VPN 터널**을 구분해 표시.
7. **캐나다 리전 S3 일반 비공개 버킷 → CloudFront(OAC) → HTTPS**, 한국 API 공개 종단/TLS·CORS·브라우저 경로와 M4 별도 S3 백업 경로를 표시. 가능 여부/비용/리전은 **미확정**으로 표시.

## M5가 과부하되지 않도록 순서를 분리
| 시점 | 캐나다망·보안 | 앱·AWS |
|---|---|---|
| **10/19** | draw.io AS-IS·자원·VPN 요청 도면 (구축 완료 아님) | 별도 1차 ERD·API 계약에 필요한 요구 파악 |
| **10/20** | AS-IS 설계 검토·TO-BE 방향 합의 | M3와 DB/런타임·API 계약 확인 |
| **10/21 오전** | M1과 VPN/IP·방화벽·중앙 로그·AWS 경로를 도면에서 최종 통합 검토 | M3와 Docker/K8s 배포 대상·API·DB 계약 협의 |
| **10/21 오후~23** | **확정된 CA-VyOS/직원·관리 클라이언트 VM부터 AS-IS 구축 착수**, 늦어도 10/22 시작 | ERD/Class/API 초안을 10/22~23 목표로 병행; 앱 골격·인계는 실제 가용시간에 따라 조정 |
| **10/26~28** | 캐나다 VLAN/VPN과 허용/비허용 통신 검증 **우선** | 가능한 범위에서 독립 개발. 로그인·영상 전체 동작 동시 마감 금지 |
| **10/29~11/02** | S05 공격 재현·로그/원인 검토 | 로컬 최소 기능 → M3 첫 배포와 요청/응답 확인 |
| **11/03~06** | TO-BE 정책 적용·VPN/관리 경로 영향 검사 | 실제 한영 자막 1개 흐름 및 AWS HTTPS·API 배포 경로 검증 |
| **11/09~10** | S05 재검증, 정상 서비스 유지 확인 | AI/OTT 회귀 시험·새 기능 중단 |

## 마무리 검증
클라이언트 IP/DHCP→CA-VyOS Gateway→본사 VPN 터널→한국 보호 대역의 TCP/라우트와, 별도의 AWS 고객 HTTPS→API 경로를 각각 확인합니다. DB 직접 포트 차단을 확인할 때는 정상 API 이용이 유지되는지도 반드시 검사합니다. 실패하면 [공통 점검](troubleshooting.md) 기록을 첨부합니다.
