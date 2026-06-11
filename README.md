# my-stock-team

한국 주식(KOSPI/KOSDAQ) **협업형 리서치 팀** Claude Code 플러그인입니다. 역할별 애널리스트 서브에이전트 5종과 디자인된 PPTX 리포트 생성 스킬, 오케스트레이션 커맨드를 묶었습니다. **가치·펀더멘털 중심**, 학습·참고용입니다.

## 구성

| 종류 | 이름 | 역할 |
|------|------|------|
| Agent | `fundamental-analyst` | 재무·밸류에이션·내재가치·경제적 해자 (리드, 산업·거시 흡수) |
| Agent | `chart-market-analyst` | 주가 추이·이동평균·거래량·추세 (FinanceDataReader) |
| Agent | `news-sentiment-analyst` | 뉴스·공시 이슈·시장 심리 (WebSearch) |
| Agent | `risk-manager-analyst` | 핵심 리스크 3가지·유동성/규모 (pykrx) |
| Agent | `report-verification-analyst` | 출고 직전 정확성·일관성·완결성·근거/형식 검수 |
| Skill | `report-pptx` | 리서치 .md → 디자인된 PPTX (KB 옐로우 톤, 맑은 고딕) |
| Command | `/my-stock-team:analyze <종목>` | 데이터 수집→협업 분석→검수까지 전체 흐름 |
| Command | `/my-stock-team:export-pptx <종목>` | reports/{종목}.md → reports/{종목}.pptx |

## 설치

### 마켓플레이스로 추가
```
/plugin marketplace add <이 저장소 경로 또는 git URL>
/plugin install my-stock-team@my-stock-team
```

## 사전 준비 (사용자별 설정)

이 플러그인에는 **API 키·비밀값이 포함되어 있지 않습니다.** 사용자가 직접 설정합니다.

1. **OpenDART API 키** — 프로젝트 루트의 `.env`에 본인 키를 넣습니다(저장소에 커밋하지 마세요):
   ```
   DART_KEY=발급받은_본인_키
   ```
   키 발급: https://opendart.fss.or.kr (무료, 공개 데이터)
2. **파이썬 의존성** — PPTX 생성용:
   ```
   pip install python-pptx
   ```
   애널리스트가 사용하는 데이터 라이브러리(선택): `pip install finance-datareader pykrx`

## 사용

```
/my-stock-team:analyze 삼성전자
/my-stock-team:export-pptx 삼성전자
```

## 가드레일 (모든 리포트 상시 적용)

- 모든 수치 옆 **(출처: 데이터명, 연도/날짜)** — 출처 없는 수치는 쓰지 않습니다.
- 데이터를 못 구하면 **"확인 불가"**, 출처 없는 뉴스·루머는 **"미확인"**.
- 매수·매도·보유·목표가·비중 확대/축소 등 **투자 행동 단정 표현 금지** — 판단 근거(의사결정 지원)까지만, 최종 판단은 사람.
- 리포트 첫머리 "무료 공개 데이터 기반 학습용" 한 줄, 끝에 데이터 출처·기준일 목록.

본 플러그인의 모든 산출물은 **학습·참고용이며 투자 권유가 아닙니다.**
