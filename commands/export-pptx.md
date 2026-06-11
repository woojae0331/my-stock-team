---
description: reports/{종목명}.md 리서치를 디자인된 PPTX 리포트로 내보냅니다.
argument-hint: <종목명>
---

`$ARGUMENTS` 종목의 완성된 리서치(`reports/$ARGUMENTS.md`)를 **report-pptx** 스킬로 디자인된 PPTX로 내보냅니다.

1. `report-pptx` 스킬을 사용합니다. (스킬 지침에 따라 .md를 슬라이드별 구조화 spec(JSON)으로 정리한 뒤 렌더러로 그립니다.)
2. 출력은 `reports/$ARGUMENTS.pptx`입니다.
3. spec 작성 시 가드레일을 그대로 적용합니다 — 모든 수치 옆 출처/기준일, 출처 없는 수치 제외, 투자 행동 단정 표현 금지, 표 행수 제한.

리포트 파일이 없으면 먼저 `/my-stock-team:analyze $ARGUMENTS`로 리서치를 생성하도록 안내합니다.
