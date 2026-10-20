# M1 유용수 · 본사 네트워크

> **v1.2 우선 확인:** [최신 토폴로지·보안 연결·검증 범위](../architecture.md)를 먼저 읽으세요. 아래 상세 내용에는 이전 설계·제안이 남아 있을 수 있으며, 실제 배선·센서·관제 경로는 v1.2 및 팀 확정값과 대조합니다.

**2026.10.20 수정 · 구축 전 계획**

[계획서 v0.3](../../plans/project-plan-v0.3.pdf) · [WBS](../../WBS.md) · [구성도 안내](../architecture.md)

## 이번 변경

M1은 별도 VyOS VM을 사용하지 않습니다. **GNS3 안의 라우터 R1**이 기존 VyOS의 상위 연결 역할을 맡습니다. M2·M3의 VyOS는 유지합니다.

| 구성 요소 | 담당 역할 |
|---|---|
| GNS3 라우터 R1 | 교실망 연결 |
| UTM1 | 내부망 접근 통제와 업무 VPN |
| GNS3 L2 스위치 | 부서별 VLAN 분리 |

GNS3는 가상 장비를 실행·연결하는 프로그램입니다. 그 안에 라우터와 스위치를 각각 구성합니다. 내부망 통신이 보안 장비를 우회하지 않도록 검토합니다.

## 유지할 장비

기존 **서버 10대·직원 PC 6대·관리 PC 2대·스위치 10대**를 유지합니다. 장비를 한두 대로 축소하지 않습니다. RAM 32GB 내에서 단계별 동시 실행량을 확인합니다. M2 관제망은 별도 PC로 유지합니다.

## 작업 순서

1. [설계 #1](https://github.com/team-blocks-lab/otter-shield/issues/1): GNS3 라우터와 스위치, UTM의 역할을 도면에 구분합니다.
2. [구축 #14](https://github.com/team-blocks-lab/otter-shield/issues/14): 선택한 라우터 이미지·실행 환경·VMware 연동을 확인하고 기본망을 구축합니다.
3. [연결 통합 #7](https://github.com/team-blocks-lab/otter-shield/issues/7): 상대 담당과 요청·응답 및 정상 업무 통신을 확인합니다.
4. 기존 보안 시나리오의 개선 전후 결과와 정상 업무 유지 여부를 기록합니다.

**일정·담당·Issue 진행 상태는 이번 수정으로 바꾸지 않습니다.** 실제 시험 후 근거를 등록하고 검토자가 확인해야 완료입니다.

## 상세 설정과 증거

팀에서 공유하는 토폴로지 v1.2과 담당 Notion 기술서에서 실제 장비 배선·주소·설정·시험 조건을 확인합니다. 라우터 이미지와 UTM 제품은 확인 후 선정하며, 문서 수정만으로 설치·연결 완료를 표시하지 않습니다.

GNS3 장비·연결 화면, 설정 변경, 예상/실제 결과, 오류, 검증 증거와 다음 작업을 남깁니다. 비밀번호·API 키·VPN 키는 공개 저장소에 올리지 않습니다.

## 공식 참고

[GNS3 VLAN 스위치](https://docs.gns3.com/docs/using-gns3/advanced/hubs-and-switches) · [외부망 연결](https://docs.gns3.com/docs/using-gns3/advanced/connect-gns3-internet) · [VMware 연동](https://docs.gns3.com/docs/emulators/adding-vmware-vms-to-gns3-topologies)
