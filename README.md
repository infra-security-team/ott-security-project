# OTTer Shield

**한국·캐나다 OTT 하이브리드 인프라 구축 및 보안 컨설팅**

Team Blocks가 보안 컨설팅 회사 NetBlocks의 역할로 가상 고객사 OTTer의 인프라를 설계·구축하고, 보안 취약점을 진단·개선하는 팀 프로젝트입니다.

**기간:** 2026.10.19~11.16 · **인원:** 5명 · **현재 단계:** 설계·구축 준비

## 프로젝트 목표

온프레미스와 AWS를 연결한 OTT 환경에서 취약점 재현 → 보안 개선 → 동일 조건 재검증을 수행합니다. 웹·AI 자막 서비스와 백업·복구도 함께 검증합니다.

**주요 기술·도입 계획:** GNS3, VMware/vSphere, UTM(Sophos), VyOS, Wazuh, Suricata, Kubernetes, AWS, React, Spring Boot, FastAPI, GitHub Actions, Argo CD

## 팀 구성

| 담당 | 역할 |
|---|---|
| M1 유용수 | 본사 네트워크·GNS3·VPN |
| M2 윤서영 | 보안 관제·탐지·로그 통합 |
| M3 홍은서 · PL | 한국 서비스망·가상화·K8s·DB·배포 |
| M4 박진혁 | 백업·DB 복제·재해 복구 |
| M5 유은혜 · PM | 캐나다망·웹/AI 개발·AWS·프로젝트 관리 |

## 자료

- [프로젝트 계획서](plans/project-plan-v0.3.pdf)
- [설계 자료](design/README.md)
- [개발 코드](apps/README.md) — M1 사내 게시판 / M3 OTT·AI / M5 Store
- [업무·일정](WBS.md) · [업무 보드](https://github.com/orgs/team-blocks-lab/projects/4)
- [회의록](meetings/README.md)

실제 설정·실습 과정·검증 증거는 Notion 기술서에 기록합니다. 구축·검증 결과는 수행 후 반영합니다.
