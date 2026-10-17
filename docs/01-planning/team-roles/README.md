# 내 역할 선택
[처음 화면](../../../README.md) · [작업 방법](../../WORK_GUIDE.md)

| 담당 | 상세 작업 안내 | 첫 Issue | 주된 교차 확인 |
|---|---|---|---|
| M1 유용수 | [본사 네트워크](m1.md) | [#1](https://github.com/infra-security-team/ott-security-project/issues/1) | M2 (관리 경로), 각 망 담당 (VPN) |
| M2 윤서영 | [본사 보안·중앙 관제](m2.md) | [#2](https://github.com/infra-security-team/ott-security-project/issues/2) | M1 (관리·수집 경로), 해당 서버 담당 (로그 대조) |
| M3 홍은서 | [한국 서비스 인프라 · PL](m3.md) | [#3](https://github.com/infra-security-team/ott-security-project/issues/3) | M5 (앱 통합), M4 (DB 복원), M2 (보안 증거) |
| M4 박진혁 | [백업·DR](m4.md) | [#4](https://github.com/infra-security-team/ott-security-project/issues/4) | M3 (DB 일관성·복원), M2 (접근 감사) |
| M5 유은혜 | [캐나다망·OTT/AI 개발 · PM](m5.md) | [#5](https://github.com/infra-security-team/ott-security-project/issues/5) | M1 (VPN), M3 (배포·서비스 통합), M2 (보안 증거) |

각자는 자기 영역의 **설계·구축·보안 개선·검증·기술 기록**을 담당합니다.
M2는 전체 팀의 보안 작업을 대신하지 않습니다. M3(PL)는 기술 통합을, M5(PM)는 일정·의존성·결정 기록을 조율합니다.
애플리케이션 코드는 M5가 작성하고 M3는 서버·DB 운영 및 배포를 담당합니다. M1~M4에게 앱 코드 작성을 배정하지 않습니다.

검토자는 작업별 연동 확인자입니다. 모든 일을 PM에게 승인받지 않습니다. 범위 변경·공통 정책 변경은 영향을 받는 담당과 PL·PM이 조율하고 팀 결정으로 남깁니다.
