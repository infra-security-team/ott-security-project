# 팀 토폴로지 업로드

**AS-IS 제출: 2026.10.20(화) / 구축 시작: 10.21(수) / TO-BE 설계: 공격 분석 후 11.03**

## 올릴 파일

오늘은 각자 **AS-IS(개선 전)만** draw.io로 만듭니다. TO-BE는 실제 공격 결과를 분석한 후 AS-IS 원본을 복사해 작성합니다.

| 담당 | draw.io 원본 이름 | 연결된 작업 |
|---|---|---|
| M1 유용수 | `M1_한국 본사.drawio` | [#1](https://github.com/team-blocks-lab/otter-shield/issues/1) |
| M2 윤서영 | `M2_독일 본사.drawio` | [#2](https://github.com/team-blocks-lab/otter-shield/issues/2) |
| M3 홍은서 | `M3_한국 서비스망.drawio` | [#3](https://github.com/team-blocks-lab/otter-shield/issues/3) |
| M4 박진혁 | `M4_백업·DR망.drawio` | [#4](https://github.com/team-blocks-lab/otter-shield/issues/4) |
| M5 유은혜 | `M5_캐나다망.drawio` | [#5](https://github.com/team-blocks-lab/otter-shield/issues/5) |

오늘 파일은 같은 기본 이름에 `_AS-IS.drawio`, `_AS-IS.png`를 붙입니다. 이미 올린 원본은 유지하고 필요한 이름·내용만 맞춥니다.

**11/03:** 공격 결과를 반영한 `_TO-BE.drawio`, `_TO-BE.png`와 변경표를 추가합니다. AS-IS 파일을 덮어쓰지 않습니다. 검토 후 11/04~05 기존 환경을 수정하고 11/06 실제 설정과 도면을 대조합니다.

## 업로드 순서

1. draw.io에서 원본을 저장하고 각 페이지를 PNG로 내보냅니다.
2. GitHub의 이 폴더에서 **Add file → Upload files**를 누릅니다.
3. 본인 원본과 이미지 파일을 올리고 **Commit changes**로 저장합니다.
4. 본인 Issue에 업로드한 파일 링크·남은 질문을 적고 팀 검토를 요청합니다.

## 도면에 보여야 하는 것

- 장비 이름·역할과 어느 망에 있는지
- 장비끼리 연결선과 다른 망으로 나가는 길
- 직원/고객의 정상 업무와 관리자 접속 경로
- 예정된 공격 시험 경로와 관찰할 로그 위치. 개선안 확정은 공격 결과 분석 후 진행
- 미정인 값과 다른 담당에게 확인할 질문

실제 교실 IP·비밀번호·개인키 등 비공개 값은 팀 기술서에서 관리합니다. 팀 작성본을 올리며, 업로드 자체가 실제 구축 완료를 뜻하지 않습니다.

[설계 자료](../README.md) · [WBS](../../WBS.md)
