---
name: design-ux-toss-distilled-review
review-level: L1-L3 Hybrid
description: "[L1-L3 Hybrid] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 토스 가이드 + tossinvest.com 실측에서 distill 한 21 추상 UX 원칙으로 정적 분석하여 한국어 마크다운 리뷰 보고서를 생성. design-ux-toss-review (구체 5+5 룰) 의 abstract counterpart. Toss Distilled Health Grade(A-F) 헤드라인 + 14 카테고리(TYPO/SPACE/COLOR/RADIUS/TONE/WRITE/DP/UNIT/IA/AMBIENT/FILTER/STATE/LAYOUT/PROCESS) sub-grade + 21 항목 ✅/❌/⚠️ + 위반 자동 critical + Top-3 Fix. 사용자가 \"toss distilled 리뷰\", \"토스 추출 원칙 리뷰\", \"toss axiom 리뷰\", \"21 원칙 리뷰\", \"distilled UX\", \"/design-ux-toss-distilled-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 추상화된 토스 원칙 기반 리뷰를 요청할 때 사용."
---

# design-ux-toss-distilled-review

**Review Level**: L1-L3 Hybrid — Toss 공식 가이드 + tossinvest.com 실측에서 distill 한 21 추상 UX 원칙 audit.

토스가 외부 개발자에게 공개한 「Apps in Toss」 가이드 (consumer-ux-guide.html · ux-writing.html) + tossinvest.com 의 정적 관측 (CSS 변수 707, 텍스트 3,808 노드, 32 keyframe, 778 FontFace 인스턴스 등) 에서 추출 → universalize 한 21 원칙을 정적 분석 rubric 으로 변환하여 Figma/Pencil 프레임을 평가한다.

평가 렌즈 = **"이 디자인이 universal UX 원칙 (Toss DNA 추출본) 을 따르는가?"** — 구체 5+5 룰 (design-ux-toss-review) 가 「토스 입점 컴플라이언스」 라면, 본 스킬은 「토스 DNA 의 abstract pattern audit」.

## 21 평가 항목 (14 카테고리)

각 항목 ✅(준수) / ❌(위반) / ⚠️(경계) / N/A(정적 검증 불가).

### TYPO (2)

| # | 원칙 |
|---|------|
| 1 | 한글 본문은 영문 대비 weight +1 / size -1px 로 광학 무게 균형 맞춤 |
| 2 | 모든 폰트 사이즈에 동일 modular ratio 의 line-height 적용 (vertical rhythm) |

### SPACE (2)

| # | 원칙 |
|---|------|
| 3 | component self-margin 금지, spacing ownership = parent layout container |
| 5 | dense layout 에서 수직 vs 수평 padding 비대칭 (row 높이 압축) |

### COLOR (1)

| # | 원칙 |
|---|------|
| 4 | 3 단 명도 위계로 정보 단계 분리 (동일 hue / luminance step) |

### RADIUS (1)

| # | 원칙 |
|---|------|
| 6 | border-radius = component hierarchy level 의 visual signal |

### TONE (3)

| # | 원칙 |
|---|------|
| 7 | CTA 라벨 = 다음 action 결과를 직접 표현하는 명사+동사 |
| 10 | binary state 전환 UI = source + target 모두 노출 |
| 12 | 같은 영역에서도 메시지 종류별 voice (formal vs peer) 의도적 전환 |

### WRITE (2)

| # | 원칙 |
|---|------|
| 8 | 중요 고지 = 사용자 의사결정 시점·위치에 inline 노출 |
| 9 | 외부 출처 정보 = origin 명시로 책임 boundary 분리 |

### DP (2)

| # | 원칙 |
|---|------|
| 11 | interruption 으로 사용자가 의도한 task 시작 가로채지 않음 |
| 14 | reject path = accept 와 동등한 가시성 보장 |

### UNIT (1)

| # | 원칙 |
|---|------|
| 13 | 숫자 + 단위 = 공백 없는 atomic visual token (만/억/조 magnitude 포함) |

### IA (2)

| # | 원칙 |
|---|------|
| 15 | clickable element = 행위 의미별 native semantic primitive 사용 |
| 18 | progressive disclosure — 초기 화면 minimum, 추가 정보 user-initiated reveal |

### AMBIENT (1)

| # | 원칙 |
|---|------|
| 16 | 핵심 정보 = 단일 surface 외 peripheral 채널에도 redundant 노출 |

### FILTER (1)

| # | 원칙 |
|---|------|
| 17 | 영향 큰 action 직전 영향 범위 inline 예고 |

### STATE (1)

| # | 원칙 |
|---|------|
| 19 | empty state = dead-end 아닌 next action reroute surface |

### LAYOUT (1)

| # | 원칙 |
|---|------|
| 20 | 시각 위계 = pre-attentive variable (size > position > color) 우선순위 매핑 |

### PROCESS (1)

| # | 원칙 |
|---|------|
| 21 | 디자인 결정 = designer preference 아닌 user scenario + evidence justify |

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일에서 "toss distilled 리뷰", "21 추상 원칙", "토스 axiom", "/design-ux-toss-distilled-review" 요청 시
- 구체 5+5 룰 (design-ux-toss-review) 가 아닌 abstract pattern 단위 audit 필요할 때
- Toss DNA 를 차용한 셀러·admin·B2B 같은 비-Toss 도메인에 토스 원칙 적용도 평가
- 디자인 시스템 신규 구축 시 토스 추출 원칙으로 sanity check
- design-ux-toss-review 와 보완 audit (구체 컴플라이언스 + abstract pattern 동시)

## Do Not Use

- 토스 입점 심사 컴플라이언스 → `design-ux-toss-review` (구체 5+5)
- Brignull 12 전수 윤리 → `design-ux-dark-pattern-review`
- UX writing 8 lens → `design-ux-microcopy-review`
- 단일 프레임 휴리스틱 → `design-ux-nielsen-review`
- 다중 프레임 flow → `design-ux-flow-review`
- 시각 UI 레이어 → `design-ui-*-review`
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 |
|----------|---------------------|---------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP 미연결. 활성화 후 재시도." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 미연결. Pencil 앱 실행 + MCP 활성화 후 재시도." |

체크 방법: Step 1 에서 ToolSearch 로 prefix 도구 조회. 결과 비면 안내 출력 후 종료.

## Workflow

### Step 1 — 입력 파싱 + MCP 사전 체크

사용자 인자에서 입력 타입 자동 감지:
- `figma.com/design/:fileKey/...?node-id=:nodeId` → Figma 경로
- `*.pen` 로컬 경로 → Pencil 경로
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

ToolSearch 로 Prerequisites 표 MCP 확인. 미연결이면 안내 후 종료.

옵션 인자:
- `--scope "{범위}"`: 특정 영역/flow 집중
- `--category {prefix}` (반복 가능): 특정 카테고리만 평가 (예: `--category TYPO --category COLOR`)
- `--strict` : ⚠️ 경계 항목을 ❌ 로 강격 판정

### Step 2 — 디자인 데이터 수집

**Figma:**
1. `get_metadata(fileKey, nodeId)` — 프레임/flow 구조
2. 프레임마다:
   - `get_design_context(fileKey, nodeId, depth:8)` — 깊은 트리 + 텍스트
   - `get_screenshot(fileKey, nodeId)` — 시각 참고
   - `get_variable_defs(fileKey)` — 디자인 토큰 인벤토리
3. 21 원칙 매핑에 필요한 정보:
   - typography (font-family·size·weight·line-height) — 1, 2
   - spacing (padding·gap·margin) — 3, 5
   - color (text·bg·border) — 4
   - radius (border-radius) — 6
   - 텍스트 (button·heading·body) — 7, 10, 12
   - 면책·고지·외부 출처 텍스트 — 8, 9
   - 모달·sheet·banner 구조 — 11, 14
   - 숫자·단위 표기 — 13
   - 클릭 가능 element 구분 — 15
   - 초기 노출 vs disclosure — 18
   - peripheral surface (title·favicon·badge) — 16
   - 사전 안내·warning 노출 — 17
   - empty/loading/error state — 19
   - size·position·color hierarchy — 20
   - design rationale (메모·코멘트) — 21

**Pencil:**
1. `open_document(path)` (필요 시)
2. `get_editor_state()` — 선택 프레임 확인
   - 선택 비면: "Pencil 편집기에서 리뷰할 프레임 1개 이상 선택 후 재시도." 출력 후 종료
3. 프레임마다:
   - `batch_get(node_ids=[frame_id], readDepth:4)` — 노드 트리
   - `snapshot_layout(node_id)` — 레이아웃
   - `get_screenshot(node_id)` — 이미지
   - `get_variables()` — 토큰 인벤토리
   - `search_all_unique_properties(node_id, property="text")` — 텍스트 팔레트
   - `search_all_unique_properties(node_id, property="fontSize")` — typography 팔레트
   - `search_all_unique_properties(node_id, property="cornerRadius")` — radius 팔레트

### Step 3 — 컨텍스트 분류

화면 성격 자동 분류:
- **ENTRY/HUB**: 진입 화면 (DP 11, 14 / TONE 12 집중)
- **DATA-DENSE**: 표·리스트 화면 (TYPO 1·2 / SPACE 5 / RADIUS 6 / UNIT 13 / DATA 집중)
- **FORM/INPUT**: 입력·동의·결제 화면 (WRITE 8 / DP 14 / STATE 19 / FILTER 17 집중)
- **NOTIFICATION/SHEET**: 모달·바텀시트·토스트 (DP 11·14 / TONE 10·12 / WRITE 8 집중)
- **DETAIL**: 상세 페이지 (AMBIENT 16 / IA 18 / WRITE 8·9 집중)
- **HYBRID**: 혼재

### Step 4 — First Impression (Toss DNA 관점)

스크린샷 직후 1인칭 즉시 반응:

```
- Toss DNA 부합 첫인상: [한 문장]
- 즉시 위반 의심 원칙: [최대 3개 또는 "없음"]
- 가장 거슬리는 부분 (universal UX 관점): [한 문장]
- 한 단어 distilled 요약: [단어]
- 인상 메모: [구체 우려/안심 근거]
```

진단가는 헤지하지 않는다.

### Step 5 — 21 원칙 평가

각 원칙마다 정밀 검사:

**판정 기준:**
- ✅ 준수: 위반 증거 없음 → score 10
- ⚠️ 경계: 단정 어려우나 잠재 위험 → score 5-7, warning
- ❌ 위반: 명확한 증거 → score 0-4, critical
- N/A: 해당 UI 요소 없음 → 집계 제외

**원칙별 검사 포인트:**

**1. 한글 base typography 광학 보정**
- font-size 기본값 = 14-15px (영문 16 보다 -1)
- font-weight 기본값 = 500 (영문 400 보다 +1)
- 영문 inline 시 별도 처리 여부 (`:lang(en)` 또는 분기)

**2. line-height modular ratio 고정**
- 모든 size 에서 lh ÷ size = 동일 비율 (예: 1.45)
- 일부 size 만 ratio 어긋나면 ⚠️

**3. component self-margin 금지**
- child component 가 outer margin 갖는지
- layout spacing = parent container gap 으로만 처리되는지

**4. 3단 명도 위계**
- 텍스트 색 = 동일 hue 안 3-4 luminance 단계로 구성되는지
- 위계마다 다른 hue 사용하면 ⚠️ ~ ❌

**5. 수직-수평 padding 비대칭 dense**
- table·list 행 padding 이 vertical < horizontal 인지
- 행 높이 충분히 압축됐는지 (44px 이하 권장)

**6. radius hierarchy signal**
- component 역할별 다른 radius (chip / button / card / modal / avatar)
- 임의 radius 산재 = ❌

**7. CTA = 명사+동사**
- 「확인 / 다음 / OK / 닫기」 단독 = ❌
- 「추가하기 / 로그인하기 / 신청하기」 = ✅

**8. 중요 고지 inline**
- 면책·주의가 footer 페이지 link 가 아닌 데이터/CTA 옆 inline
- footer 만 사용 = ❌

**9. 외부 출처 origin 명시**
- 외부 데이터 인용 시 source 명시 ("출처: X")
- 명시 없음 = ❌

**10. binary state 전환 = source+target 노출**
- toggle / mode switch 라벨이 「현재→대상」 또는 양쪽 동시 표시
- 다음 상태만 표시 = ⚠️

**11. interruption 으로 entry 가로채지 않음**
- 진입 직후 modal/sheet/광고 강제 노출 여부
- 헤더 배너 + 닫기 = OK / 강제 sheet = ❌

**12. voice formal vs peer 의도적 전환**
- 정의문은 합니다체, 안내문은 해요체 hybrid 사용 여부
- 한 voice 강제 통일 시 정의문 사적·면책 차가움 부작용

**13. 숫자+단위 atomic token**
- 「292,500 원」 (공백) = ❌
- 「292,500원」 = ✅
- 「만원/억원/조원」 magnitude 변환 활용

**14. reject path 동등 가시성**
- 모달/sheet 에 닫기/취소 옵션 가시성
- accept 만 highlight, reject hidden = ❌

**15. clickable = native semantic primitive**
- routable nav = anchor, state mutation = button
- div+onclick 으로 통일 = ❌

**16. 핵심 정보 peripheral 노출**
- 페이지 title / favicon / badge 에 실시간 핵심 정보 노출
- 페이지 내부에만 정보 존재 = ⚠️

**17. 영향 큰 action 사전 inline 예고**
- destructive / cross-scope action 직전 영향 범위 inline notice
- 미예고 = ❌

**18. progressive disclosure**
- 초기 화면 minimum + expand/drill-in 으로 reveal
- 모든 정보 평탄 노출 = ⚠️

**19. empty state = next action reroute**
- empty 가 「없음」 만 알리고 끝나는지
- 원인 진단 + 해결 path 제공 시 ✅

**20. pre-attentive hierarchy = size > position > color**
- 가장 중요한 정보가 가장 큰 size
- size 작은데 가장 중요한 정보 = ⚠️

**21. design 결정 = scenario + evidence**
- 디자인 메모/코멘트에 「어떤 사용자 시나리오 / 어떤 evidence」 justify 존재
- designer preference 만 = ⚠️ (정적 검증 한계, N/A 가능)

### Step 6 — Toss Distilled Health Grade 산출

**카테고리별 sub-grade (14 카테고리):**
- TYPO (1+2) / SPACE (3+5) / COLOR (4) / RADIUS (6) / TONE (7+10+12) / WRITE (8+9) / DP (11+14) / UNIT (13) / IA (15+18) / AMBIENT (16) / FILTER (17) / STATE (19) / LAYOUT (20) / PROCESS (21)
- 각 카테고리 점수 평균
- 9.5-10 = A · 8.0-9.4 = B · 6.0-7.9 = C · 4.0-5.9 = D · 0-3.9 = F

**Toss Distilled Health Grade (TDH):**
- 21 항목 점수 평균
- 동일 grade 기준

**Critical Cap:**
- ❌ critical 1건 = TDH 최대 C
- ❌ critical 3건 이상 = 자동 F

**추가 헤드라인:**
- **Top Risk**: 가장 심각한 단일 위반 한 줄
- **Top Strength**: 가장 잘 준수된 원칙 한 줄
- **Distilled Pattern Alignment**: High / Medium / Low (토스 DNA 정성 정렬도)

### Step 7 — Finding 작성

위반(❌) 또는 경계(⚠️) 원칙마다 finding 1개:

```markdown
### {N} {원칙 제목} — score: {점수}
- **severity**: critical | warning | info
- **category**: {TYPO/SPACE/COLOR/...}
- **principle**: {원칙 1줄 진술}
- **evidence**: frame `{nodeId}` · {구체 UI 요소·텍스트·위치}
- **why this matters**: {원칙의 이유 (보고서 v2 의 「이유」 1-2줄)}
- **fix**: {구체 수정 방향}
```

### Step 8 — 보고서 작성

**파일 경로**: `./design-reviews/design-ux-toss-distilled-review-{screen-slug}-{YYYYMMDD-HHmm}.md`

### Step 9 — Top-3 Fix

❌ critical 우선, 그 다음 ⚠️ warning 순으로 최대 3개:

각 카드:
- **원칙**: {N + 제목}
- **카테고리**: {prefix}
- **위치**: frame `{nodeId}` · {UI 요소}
- **사용자 영향**: {신뢰·인지 부담·a11y 영향 시나리오}
- **수정 방향**: {구체 변경}
- **기대 점수 변화**: {N} → {N'}
- **노력**: Low / Medium / High ({n} weeks)

### Step 10 — 사용자에게 결과 요약

- 보고서 파일 경로
- Toss Distilled Health Grade + 14 카테고리 sub-grade
- 21 원칙 ✅/❌/⚠️/N/A 현황
- critical/warning 개수
- Distilled Pattern Alignment
- Top-3 Fix 한 줄 요약
- 다음 액션

### Step 11 — annotate-design 연동 안내

finding 1건 이상이면:
```
리뷰 파일: {경로}
Figma/Pencil 코멘트 패널 부착: /annotate-design {경로}
```

## 보고서 구조 (한국어)

```markdown
# Toss Distilled UX Review: {화면/flow 이름}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID(s): {nodeId(s)}
- 프레임 이름(s): {frame.name(s)}
- 화면 컨텍스트: {ENTRY/HUB | DATA-DENSE | FORM/INPUT | NOTIFICATION/SHEET | DETAIL | HYBRID}
- 서비스 성격: {비즈니스 맥락}
- 실행 모드: {--category filter} · {--strict on/off}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 방법론: Toss 가이드 + tossinvest.com 실측에서 distill 한 21 추상 UX 원칙
- 참고: design-reviews/toss-principles-v2-20260522-1211.md

## 헤드라인
- **Toss Distilled Health Grade: {A-F}** ({TDH}/10)
  - TYPO: {grade} ({n}/10) · SPACE: {grade} · COLOR: {grade} · RADIUS: {grade}
  - TONE: {grade} · WRITE: {grade} · DP: {grade} · UNIT: {grade}
  - IA: {grade} · AMBIENT: {grade} · FILTER: {grade} · STATE: {grade}
  - LAYOUT: {grade} · PROCESS: {grade}
- **Distilled Pattern Alignment**: {High/Medium/Low}
- **Top Risk**: {가장 심각한 단일 위반 한 줄}
- **Top Strength**: {가장 잘 준수된 원칙 한 줄}
- 적용 원칙: {applied}/21 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression (Toss DNA 관점)
- Toss DNA 부합 첫인상: {...}
- 즉시 위반 의심: {...}
- 가장 거슬리는 부분: {...}
- 한 단어 distilled 요약: {...}
- 인상 메모: {...}

## 21 원칙 평가

| # | 원칙 | 카테고리 | 판정 | 점수 | 비고 |
|---|------|---------|------|------|------|
| 1 | 한글 base 광학 보정 | TYPO | ✅/❌/⚠️/N/A | - | - |
| 2 | line-height modular ratio 고정 | TYPO | ✅/❌/⚠️/N/A | - | - |
| 3 | component self-margin 금지 | SPACE | ✅/❌/⚠️/N/A | - | - |
| 4 | 3 단 명도 위계 | COLOR | ✅/❌/⚠️/N/A | - | - |
| 5 | 수직-수평 padding 비대칭 | SPACE | ✅/❌/⚠️/N/A | - | - |
| 6 | radius hierarchy signal | RADIUS | ✅/❌/⚠️/N/A | - | - |
| 7 | CTA = 명사+동사 | TONE | ✅/❌/⚠️/N/A | - | - |
| 8 | 중요 고지 inline | WRITE | ✅/❌/⚠️/N/A | - | - |
| 9 | 외부 출처 origin 명시 | WRITE | ✅/❌/⚠️/N/A | - | - |
| 10 | binary state source+target 노출 | TONE | ✅/❌/⚠️/N/A | - | - |
| 11 | interruption 회피 | DP | ✅/❌/⚠️/N/A | - | - |
| 12 | voice formal/peer hybrid | TONE | ✅/❌/⚠️/N/A | - | - |
| 13 | 숫자+단위 atomic token | UNIT | ✅/❌/⚠️/N/A | - | - |
| 14 | reject path 동등 가시성 | DP | ✅/❌/⚠️/N/A | - | - |
| 15 | clickable native semantic | IA | ✅/❌/⚠️/N/A | - | - |
| 16 | 핵심 정보 peripheral 노출 | AMBIENT | ✅/❌/⚠️/N/A | - | - |
| 17 | 영향 큰 action 사전 inline 예고 | FILTER | ✅/❌/⚠️/N/A | - | - |
| 18 | progressive disclosure | IA | ✅/❌/⚠️/N/A | - | - |
| 19 | empty state next action reroute | STATE | ✅/❌/⚠️/N/A | - | - |
| 20 | pre-attentive hierarchy | LAYOUT | ✅/❌/⚠️/N/A | - | - |
| 21 | design 결정 evidence justify | PROCESS | ✅/❌/⚠️/N/A | - | - |

## Findings

### {N} {원칙 제목} — score: {점수}
- **severity**: critical | warning | info
- **category**: {prefix}
- **principle**: {원칙 1줄 진술}
- **evidence**: frame `{nodeId}` · {UI 요소·텍스트}
- **why this matters**: {원칙의 이유}
- **fix**: {수정 방향}

{위반/경계 원칙만 나열}

## Top-3 Fix

### Fix 1 — {N + 원칙 제목}
- **원칙**: {N + 제목}
- **카테고리**: {prefix}
- **위치**: frame `{nodeId}` · {UI 요소}
- **사용자 영향**: {시나리오}
- **수정 방향**: {구체 변경}
- **기대 점수 변화**: {N} → {N'}
- **노력**: Low/Medium/High ({n} weeks)

### Fix 2 — ...
### Fix 3 — ...

## N/A 항목 (해당 UI 없음 또는 정적 검증 불가)
- {N} {원칙 제목}: {사유}

## Distilled Pattern Cheat Sheet (참고)

| Anti-pattern | Distilled 권장 |
|-------------|---------------|
| 영문 base 16/400 한글 그대로 적용 | 한글 15/500 광학 보정 |
| size 마다 다른 lh ratio | 1.45 fixed ratio |
| child 컴포넌트 외부 margin | parent gap |
| 정보 단계별 다른 hue | 동일 hue 명도 단계 |
| "확인" 단독 CTA | "확인하기" 명사+동사 |
| footer 만 면책 link | inline 면책 |
| "다크" 토글 라벨 | "라이트에서 다크로" |
| "292,500 원" 공백 | "292,500원" 붙임 |
| accept 만 강조 | reject 동등 가시성 |
| div+onclick clickable | anchor / button 분리 |
| 모든 정보 평탄 노출 | progressive disclosure |
| "데이터 없음" dead-end | 원인 + 해결 path |

## 다음 단계
- Top-3 Fix 즉시 수정 후 재audit
- `/annotate-design {경로}` 로 디자인 파일 코멘트 패널 부착
- 구체 컴플라이언스 점검 필요 시 `/design-ux-toss-review` (5+5 룰)
- Brignull 12 전수 audit 필요 시 `/design-ux-dark-pattern-review`
- 한국어 마이크로카피 8 lens 평가 필요 시 `/design-ux-microcopy-review`
```

## 인자

```
/design-ux-toss-distilled-review <Figma URL | .pen path> [--scope "{범위}"] [--category {prefix}]* [--strict]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- `--scope`: 특정 영역 집중
- `--category`: 특정 카테고리만 평가 (반복 가능, 예: `--category TYPO --category COLOR`)
- `--strict`: ⚠️ 경계 = ❌ 강격 판정

## 예시

### 예시 1 — Figma 종목 상세 페이지 distilled audit
```
/design-ux-toss-distilled-review https://www.figma.com/design/abc/Stock?node-id=42-1024
```
→ Figma MCP 체크 → 데이터 수집 → 컨텍스트: DATA-DENSE → 21 원칙 평가 → TYPO(✅✅) + UNIT(❌ "292,500 원" 공백) + LAYOUT(⚠️ 위계 모호) → TDH B (8.4/10) → Top-3 Fix → 보고서 생성

### 예시 2 — Pencil 결제 모달 typography·color 집중
```
/design-ux-toss-distilled-review ~/Desktop/projects/design/checkout.pen --category TYPO --category COLOR
```
→ Pencil MCP 체크 → 4 원칙만 평가 (1, 2, 4) → TYPO sub-grade + COLOR sub-grade → 일부 보고서

### 예시 3 — strict 모드 신규 디자인 시스템 sanity check
```
/design-ux-toss-distilled-review https://www.figma.com/design/abc/DS?node-id=10-200 --strict
```
→ 21 원칙 strict 평가 → ⚠️ 경계 모두 ❌ 로 → TDH 보수적 → 디자인 시스템 신규 구축 시 안전망

### 예시 4 — MCP 미연결
```
/design-ux-toss-distilled-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 미연결" 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트 한국어
- 원칙 번호 (1, 2, …, 21) 유지 (보고서 v2 와 매핑 호환)
- finding 헤더 포맷 `### {N} {원칙 제목} — score: {점수}` 고정
- severity / category / principle / evidence / why this matters / fix 6 필드 동일 순서
- ❌ critical = 자동 critical
- ⚠️ warning = warning
- N/A 항목 보고서 말미 별도 기재
- Distilled Pattern Cheat Sheet 항상 첨부

## annotate-design 호환성

본 스킬 출력 `.md` 는 `annotate-design` 스킬이 그대로 파싱하여 Figma/Pencil 파일에 코멘트 패널 부착. evidence 의 `frame \`{nodeId}\`` 패턴에서 nodeId 추출.

```
/design-ux-toss-distilled-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md>                   → 디자인 파일에 시각 코멘트 부착
```

## 관련 스킬과의 관계

| 항목 | design-ux-toss-distilled-review | design-ux-toss-review |
|------|--------------------------------|----------------------|
| 출처 | Toss 가이드 + tossinvest.com 실측 distill | Toss 공식 가이드 (5+5) |
| 추상화 수준 | High (universalized 21 원칙) | Low (구체 룰) |
| 영역 | typography·color·spacing·tone·a11y·process 등 14 카테고리 | Dark Pattern + UX Writing 2 영역 |
| 적용 도메인 | 모든 product (Toss DNA 차용) | 토스 입점 / 토스 톤 한정 |
| 용도 | 디자인 시스템 sanity check / abstract pattern audit | 토스 입점 심사 사전 컴플라이언스 |
| 한국어 특화 | 한글 광학 보정 + 해요체 | 해요체·돼요·~시 한국어 특화 |

두 스킬 보완 관계 — **distilled = abstract pattern, toss-review = concrete compliance**.

## Non-Goals

- 21 원칙을 절대 진리로 강요 — context 별 trade-off 인정
- 토스 SDK / 결제 API / 입점 컴플라이언스 — 디자인만
- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 자동 카피 재작성 / 디자인 변경 — 리뷰 + 제안만
- 법률 자문 — design 영향 평가만

## 참고 자료

- **원본 21 원칙** — `design-reviews/toss-principles-v2-20260522-1211.md`
- **distill 출처 1 (Toss 가이드)** — https://developers-apps-in-toss.toss.im/design
- **distill 출처 2 (tossinvest.com 실측)** — `.playwright-mcp/toss-*.json` 22+ raw 데이터
- **distill 출처 3 (세션 통합 보고서)** — `design-reviews/toss-securities-live-ux-principles-20260522-1009.md`, `toss-unified-ux-principles-20260522-1146.md`
- **짝 스킬**: `design-ux-toss-review` (구체 5+5) · `design-ux-dark-pattern-review` (Brignull 12) · `design-ux-microcopy-review` (UX writing 8 lens) · `annotate-design` (finding 시각화)
