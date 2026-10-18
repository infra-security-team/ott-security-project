# M1 유용수 · 본사 네트워크/4망 VPN 허브

**Issue:** [설계 #1](https://github.com/infra-security-team/ott-security-project/issues/1) · [AS-IS #14](https://github.com/infra-security-team/ott-security-project/issues/14) · [공동 VPN #7](https://github.com/infra-security-team/ott-security-project/issues/7)
**망 역할:** 한국 본사의 직원·관리 VLAN을 만들고 VPN 허브로 서비스·DR·캐나다 연결을 조율. 각 망의 실제 라우터 설정은 **그 망 담당자가 수행**합니다.

## 사용할 프로그램·환경
- **도면:** diagrams.net(draw.io)
- **가상 환경:** 학원 VMware Workstation/vSphere 중 확정된 플랫폼
- **라우터:** VyOS (버전·이미지/라이선스/가상 NIC 종류 확인)
- **클라이언트/시험:** Ubuntu/Linux 또는 사용 가능한 Windows VM
- **통신 확인:** ping, ip addr, ip route, traceroute/tracepath, tcpdump, ssh; VMware 가상 스위치/포트그룹 설정 확인

## 장비·기능 명세 (제안 / 구성 확정 전)
| 구성 요소 | 시작 수량 | 위치/기능 | 선택 이유·조건 |
|---|---:|---|---|
| HQ-VyOS | 1 VM | VLAN 간 라우팅, 정책 방화벽, Site-to-Site IPsec 허브, 필요한 DHCP/NAT | 같은 VM에서 여러 기능 수행, 독립 서버 5개 아님 |
| HQ-Employee-Client | 1 VM | 직원 VLAN DHCP 수신·업무 접근 시험 | '직원 PC 여러 대' 필요 없음, 출발지 1대로 우선 검증 |
| HQ-Admin-Client | 1 VM | 관리 VLAN에서 승인된 Bastion 접근 | 정당한 관리자 경로 증거 확보 |
| 본사 Bastion·SSH 대상 | M2 문서 참조 | 정상 관리/비인가 접근 대상 | M1이 중복 생성하지 않음 |
| 가상 스위치/포트그룹 | VLAN/물리 호스트 조건으로 결정 | 직원/관리/보안/WAN 또는 transit 연결 | VMnet 구분과 802.1Q VLAN 태깅은 다름 |
| 본사 DNS/NTP·DHCP 기능 | 서비스로 1개 이상 구성 가능 | DHCP는 직원 VLAN 중심, 시간 동기화는 전 서버 | 서버 VM 별도 강제 안 함 |

## AS-IS 기본 도면에 반드시 넣기
- 직원 VLAN, 관리 VLAN, 보안/시험망 위치와 IP CIDR(미확정이면 TBD).
- HQ-VyOS의 인터페이스와 외부/WAN·VPN 허브·서비스/DR/캐나다 각각의 **피어**.
- 직원 PC, 관리 PC, M2 Bastion, SSH 시험 대상과 정상 통신 경로.
- AS-IS S01: **격리된 직원망 → 관리 대상**의 비인가 경로가 성립할 설계 조건(실제 외부 공개 금지).
- TO-BE 초안: 직원망 직접 관리 연결 차단, 승인된 관리자→Bastion→관리 서버 경로 유지.
- VPN 보호 대역, 양단 라우트, 상대쪽 반환 경로, 필요한 NAT 예외 목록.
- WAN/학원 인터넷 조건. 사설 주소망 예시는 실제 구성 확정 전에 공통 대역표에서 충돌 검사.

## 10/19 산출물·그다음 순서
- [ ] `M1-HQ-ASIS.drawio` 원본·PNG, VM/네트워크 수량과 예상 CPU/RAM, 네트워크 연동 요구사항 목록.
- [ ] M3/M4/M5의 CIDR/피어/포트/리턴 라우트 요청을 **하나의 통신표로 취합**.
- [ ] 10/20 오전 회의에서 대역 충돌·VPN 종단/허용 정책 검토; TO-BE 설계 초안 승인 요청.
- [ ] 10/21 이후 승인된 가상 장비 생성 → NIC/VLAN 라우팅 → 직원 DHCP→기본 게이트웨이 통신 확인.
- [ ] 10/26~28 M3/M4/M5와 실제 VPN 보호 트래픽의 허용·차단 및 반환 경로 검증.

## 성공 증거 / 막힐 때
**증거:** 도면 버전·가상 스위치 설정, VyOS 인터페이스·라우팅/VPN 상태, 직원 DHCP 임대/IP, 정상·실패 통신 시각과 패킷/방화벽 로그. VPN 터널 'up'만으로 통합 성공 판정 금지.

**주요 오류:** 다른 망 중복 CIDR, 잘못된 NIC/포트그룹, DHCP 미수신, 정책/라우트 비대칭, NAT가 VPN 대상에 적용됨, VPN 피어/보호 대역 불일치. [공통 진단](troubleshooting.md)에 실패 시각·출발지·목적지·양단 설정 확인 결과 남기기.
