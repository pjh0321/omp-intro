# omp 웹검색 provider 비교

## omp 웹검색 provider 14종 비교 (2026-06-22 조사)

> 주의: '서비스 무료티어/요금제'는 외부 서비스 실제 가격(2026-06 기준, **변동 가능**)이며 내가 조사함. '인증 모드'는 omp 내장문서 기준 확정 사실(재조사 안 함). 출처는 실제로 읽은 URL만 기재.

| Provider | 서비스 무료티어/요금제 (2026, 변동가능) | 인증 모드 (omp) | 검색 성격 | 출처 URL (실제 열람) |
|---|---|---|---|---|
| **tavily** (1순위·기설정) | Free(Researcher) **1,000 credits/월, 카드 불필요**; PAYG **$0.008/credit(=$8/1k)**; Project(유료) 월 4,000 credits~ | API 키 | **소스-검색형** (에이전트/RAG용 실시간 검색, 랭크된 소스 URL 반환; answer 옵션 별도) | https://www.tavily.com/pricing |
| **exa** | Free **월 20,000 req 무료**(공식 페이지 2026-06-22 확인); Search **$7/1k**, Deep Search $12–15/1k, Contents $1/1k pages, Answer $5/1k. (변동주의: 과거 ~1,000/mo로 알려졌으나 공식 페이지는 현재 20,000) | API 키 (키 없는 공개 MCP는 '명시 단독'만, **자동폴백 자격 아님**) | **소스-검색형** (뉴럴 검색, 다수 소스 URL+하이라이트; 코딩/리서치 최적. Deep/Answer는 합성) | https://exa.ai/pricing |
| **perplexity** | **공식 API 무료티어 없음**(사용량 과금·크레딧 선구매, 티어=전체구매액). Sonar 토큰 $1/1M(in)+$1/1M(out) + 요청료 $5/$8/$12 per 1k(컨텍스트 low/med/high); 단독 Search API **$5/1k**; Agent API web_search 툴 $0.005/call. (Pro 구독 월 $5 크레딧설은 공식문서 미기재→**확인불가**) | 쿠키/OAuth/키 (익명은 '명시 단독'만, **자동폴백 자격 아님**) | **답변-합성형** (Sonar=LLM 답변+인용); raw Search API(소스형)도 존재 | https://docs.perplexity.ai/docs/getting-started/pricing , https://docs.perplexity.ai/docs/resources/faq |
| **brave** | **2026-02 무료티어 폐지.** Search **$5/1k req + 월 $5 크레딧(≈1,000 queries, 단 공개 attribution 필수)**, 초과 시 카드 청구(상한 미표기). (이전 무료: 2023년 2,000/월→2025-08 5,000/월→폐지) | API 키 | **소스-검색형** (독립 30B 인덱스, URL/스니펫; LLM Context API는 chunk 반환) | https://www.implicator.ai/brave-drops-free-search-api-tier-puts-all-developers-on-metered-billing/ (2026-06-08, 공식 pricing/blog 인용) |
| **jina** | **무료 풍부**: Reader(r.jina.ai) 20 RPM 무키/500 RPM 무료키; Search(s.jina.ai) 무키 불가·무료키 100 RPM; **신규 API키마다 1,000만(10M) 무료 토큰**; s.jina.ai는 요청당 최소 ~10,000 토큰(≈10M으로 ~1,000 검색). 이후 토큰 충전식 | API 키 | **소스-검색형** (s.jina.ai=상위 5개 결과 URL+정제 콘텐츠; r.jina.ai=URL→마크다운; DeepSearch는 합성) | https://jina.ai/reader/ |
| **kimi** (Moonshot) | Web Search **$0.004/호출**(토큰과 별도) + 모델 토큰 과금. 무료티어/가입 크레딧은 공식 페이지 미기재→**확인불가** | API 키 | **답변-합성형** (Kimi 모델의 $web_search 내장도구 → 모델 답변) | https://www.kimi.com/help/kimi-api/api-pricing |
| **kagi** | **무료티어 없음**(계정 충전식, 확인범위 내). Search **$12/1k req**, Extract $4/1k pages | API 키 | **소스-검색형** (실시간 Kagi 결과: web/images/news/videos/podcasts) | https://kagi.com/api/pricing |
| **parallel** | 공식 가격표에 **무료티어 명시 없음**(사용량 과금). Search **$5/1k req**(기본 10결과)+$1/1k 추가결과; Extract $1/1k URLs; Chat(speed) $5/1k. (가입 무료 크레딧→확인불가) | API 키 | **소스-검색형** (page+excerpt 반환, LLM/에이전트용) | https://docs.parallel.ai/getting-started/pricing |
| **synthetic** | 구독제 **$1/일(=$30/월), 500 req/5hr, 전 모델 포함** 또는 사용량제. **/v2/search는 별도이며 단가 미공개**(API 개발중)→검색 단가 **확인불가**; 무료티어 명시 없음 | API 키 | **소스-검색형** (zero-data-retention 웹검색 API; results[] url/title/text/published — 코딩 에이전트용 raw 소스) | https://synthetic.new/pricing , https://dev.synthetic.new/docs/synthetic/search |
| **zai** (Z.AI·Zhipu GLM) | Web Search 내장도구 **$0.01/use**. 일부 GLM 모델 무료(GLM-4.7-Flash, GLM-4.5-Flash 등 토큰 무료). 웹검색 자체 무료티어 없음 | API 키 | **소스-검색형**(웹검색 결과 반환; GLM과 결합 시 답변 합성) | https://docs.z.ai/guides/overview/pricing |
| **anthropic** | **API 무료티어 없음**(사용량 과금). Web search **$10/1,000 searches** + 표준 토큰 비용 | **기존 Claude OAuth 재사용**(또는 검색 API 키) — *사용자 OAuth 보유 → 새 키 없이 자동폴백 가능* | **답변-합성형** (Claude 답변+인용 URL; raw 응답엔 url/title 포함되나 omp `auto`에선 '답변 위주·소스 적음'으로 관측) | https://platform.claude.com/docs/en/agents-and-tools/tool-use/web-search-tool |
| **gemini** | 기본 API엔 Free tier(토큰 무료·제한 rate) 있으나 **Grounding은 Free tier 불가**. Paid tier에서 **월 5,000 prompts 무료**(Gemini 3 공유), 이후 **$14/1,000 search queries** | Google Gemini-CLI/Antigravity OAuth 재사용 — *사용자 미로그인 → 현재 불가* | **답변-합성형** (Gemini 답변 + groundingChunks 인용 URL) | https://ai.google.dev/gemini-api/docs/pricing , https://ai.google.dev/gemini-api/docs/google-search |
| **codex** (OpenAI) | **API 무료티어 없음**(사용량 과금). Web search 툴 **$10/1k calls**(추론 모델 gpt-5/o-series) + 검색 콘텐츠 토큰(모델 단가); 비추론 모델 $25/1k(콘텐츠 토큰 무료) | OpenAI/ChatGPT(codex) OAuth 재사용 — *로그인 시에만 가능* | **답변-합성형** (모델 답변 + 인용) | https://developers.openai.com/api/docs/pricing |
| **searxng** | **완전 무료·오픈소스**(self-host). 호스티드 상용 서비스 없음; 공개 인스턴스(searx.space) 다수. 최대 276개 엔진 메타검색 | self-hosted endpoint URL | **소스-검색형** (메타검색 JSON API, 합성 없음·추적 없음) | https://docs.searxng.org/ |

## 2순위 폴백 추천 (1순위=Tavily, 무료+품질+omp 자동폴백 기준)

전제: omp 자동폴백은 **자격증명(키/OAuth/endpoint)이 resolvable한 provider만** 체인에 포함. 따라서 후보는 (a) 사용자가 이미 가진 자격증명을 쓰거나 (b) 새 키 1개만 넣으면 되는 것 위주. 폴백을 쓰려면 단일 고정이 아니라 `auto` 모드여야 함(단일 고정 시 폴백 없이 즉시 에러).

### ① Exa — 종합 추천 (무료 한도·품질 최상, 새 키 1개 필요)
- **필요 자격증명: 새 `EXA_API_KEY` 1개**(무료 가입). ⚠️ 키 없는 공개 MCP는 '명시 단독'에서만 동작하고 **자동폴백 자격이 아니므로 반드시 키를 넣어야** 폴백 체인에 잡힘.
- **무료**: 공식 페이지상 **월 20,000 req 무료**(최소치로 봐도 넉넉). 초과분도 $7/1k로 저렴.
- **품질**: **소스-검색형**으로 raw 소스 URL 다수 반환 → 코딩/리서치에 강하고, 소스형인 Tavily와 결이 같아 1↔2순위 결과 일관성이 좋음.
- 한 줄: "무료티어가 가장 크고 소스 품질이 가장 좋다. 키 발급 1회만 감수하면 최선."

### ② Anthropic — '새 키 0, 지금 바로' 최강 (단 답변형)
- **필요 자격증명: 새 키 0개** — 사용자가 보유한 **기존 Claude OAuth를 그대로 재사용** → 설정 변경 없이 즉시 자동폴백 자격 충족.
- **비용**: 구독 OAuth 재사용이라 별도 검색 API 결제 불필요(별도 키로 API 직접 쓸 경우 $10/1k searches + 토큰).
- **품질**: **답변-합성형**(인용 URL은 주지만 raw 소스 수가 적음; omp `auto`에서도 '답변 위주'로 관측). 소스 다수가 필요한 리서치/코딩엔 Exa보다 약함.
- 한 줄: "가입·키·결제 0으로 당장 켜지는 폴백. 품질은 '답변형'이라 소스 수집형 작업엔 차선."

### ③ Jina — 보조 대안 (새 키 1개, 소스형, 무료 적당)
- **필요 자격증명: 새 `JINA_API_KEY` 1개**(무료 가입).
- **무료**: 신규 키당 **10M 무료 토큰(≈s.jina.ai 검색 ~1,000회)** + 무료키 100 RPM.
- **품질**: **소스-검색형**(상위 결과 URL + 정제 콘텐츠까지 반환). Exa보다 무료량은 적지만 소스형 일관성은 동일.
- 한 줄: "Exa 대안. 소스형 + 무료 10M 토큰으로 충분, 키 1개 필요."

### 추천 결론
- **소스 품질·무료 한도 우선** → **Exa**(새 무료 키 1개). 1순위 Tavily와 같은 소스-검색형이라 폴백 일관성도 최고.
- **추가 가입/키/비용 0으로 즉시** → **Anthropic**(기존 Claude OAuth 재사용). 단 답변-합성형 한계 인지.
- 가장 견고한 셋업: `auto` 모드 + Tavily 키 + (Exa 키 또는 Claude OAuth)를 함께 resolvable 상태로 두기.
- 참고 제외: gemini(현재 OAuth 미로그인→불가, 로그인 시 월 5,000 무료 grounding로 강력 후보), codex(로그인 시만), brave(무료티어 폐지), kagi/parallel/perplexity/kimi/zai/synthetic(새 키 필요 또는 무료 빈약/미확인).
