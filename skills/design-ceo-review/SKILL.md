---
name: design-ceo-review
review-level: L5 Strategy
description: "[L5 Strategy] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 CEO/founder 시각의 10개 전략 항목(Premise·Existing Leverage·Dream State·First-class KPI·Scope Intentionality·IA Identity·State Coverage·Brand Token Alignment·Next-step Affordance·Hygiene)으로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. Strategy Health Grade(A-F) 헤드라인 + Mode Selection(PIVOT/HOLD/SCRAP) + Implementation Approaches A/B/C + Top-3 Rethink 재설계 제안. 사용자가 \"CEO 리뷰\", \"디자인 CEO 리뷰\", \"전략 리뷰\", \"design ceo review\", \"/design-ceo-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 전략/scope/정체성 기반 디자인 리뷰를 요청할 때 사용."
---

# design-ceo-review

**Review Level**: L5 Strategy — CEO/founder 전략 10항목 (Premise·Dream State·KPI·Scope·Identity).

`/plan-ceo-review` 의 핵심 패턴(Premise Challenge · Existing Leverage · Dream State · Implementation Alternatives · Top-3 Rethink) 을 디자인 파일 정적 분석용으로 압축한 스킬. 디자이너 시각의 micro polish 가 아닌 **CEO/founder 시각의 전략 진단** 을 한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 화면이 누구의 무슨 결정을 돕는가? 이미 존재하는 자산을 쓰고 있는가? 12개월 후 vision 으로 향하는가? 진짜 product 인가 placeholder 인가?"

## 평가 항목 (10개)

### A. Strategy (4)

| # | Item | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 1 | Premise | 사용자 1명·결정 1개 명시. 도구 의도 한 줄 가시. placeholder 브랜드/제목/카피 부재 | Yes |
| 2 | Existing Leverage | 프로젝트 내 도메인 자산(DESIGN.md·spec·user-story·prior screen) 재사용 신호. 차용 가능한데 무시 0 | Yes |
| 3 | Dream State | 명시·암묵적 12개월 후 vision 으로 향하는 vector. 옆 방향 polish 0 | Partial |
| 4 | First-class KPI | KPI/headline 이 도메인 차별화. generic SaaS 80% 기본값 회피. 결정 도구지 정보 디스플레이 아님 | Yes |

### B. Execution (3)

| # | Item | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 5 | Scope Intentionality | 화면 안 요소 모두 의도 있음. 채우기·장식·미사용 영역 0. 7±2 정보 청크 | Yes |
| 6 | IA Identity | 네비/메뉴/탭 라벨이 도메인 단어. Dashboard/Analytics/Settings 같은 generic SaaS 템플릿 회피 | Yes |
| 7 | State Coverage | Empty·Loading·Error·Partial·Null state 디자인 존재. 첫 진입 0데이터 대비 | Yes |

### C. Identity (2)

| # | Item | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 8 | Brand Token Alignment | 프로젝트 DESIGN.md / token 명시 색·폰트·spacing 1:1 적용. near-miss(예: slate vs Toss grey) 회피 | Yes |
| 9 | Next-step Affordance | 결정 도구로서 다음 액션 신호(hover/CTA/chevron/drill-down) 가시. dead-end 0 | Yes |

### D. Hygiene (1)

| # | Item | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 10 | Cleanup | stray text·burst 흔적·미사용 노드·예전 실험 잔존 0. 캔버스 일관 | Yes |

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "CEO 리뷰", "전략 리뷰", "정체성 리뷰", "scope 진단", "이 디자인 진짜 product 인가" 등을 요청할 때
- micro UX/UI polish (laws/nielsen/ixdf) 이미 돌렸는데 점수 안 오를 때 → 위 layer 정체성/scope 문제 의심
- 신규 디자인 vision/scope/identity 잠금 전 한 번 체크
- placeholder/generic SaaS 템플릿 위 polish 중인지 의심될 때

## Do Not Use

- micro UX 휴리스틱 평가 → `design-ux-nielsen-review` / `design-ux-lawsofux-review` / `design-ux-ixdf-review` / `design-ux-ecommerce-review`
- micro UI 시각 폴리시 → `design-ui-polish-review` / `design-ui-ixdf-review` / `design-ui-critic-review` / `design-ui-nielsen-review` / `design-ui-lawsofux-review` / `design-ui-ecommerce-review`
- 코드 plan/PR 리뷰 → `/plan-ceo-review` (이 스킬의 코드 도메인 원본)
- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 라이브 사이트 audit → gstack `/design-review`

**Do-Not-Use 명확화:** 이 스킬은 **전략 layer** (정체성·scope·도메인 자산 활용). 시각 폴리시 layer 와 직교. micro polish 후 점수가 막힐 때 위 layer 가 원인일 수 있다는 의심 진단용.

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동 또는 Figma 데스크탑 Dev Mode MCP / figma-console Desktop Bridge 중 하나를 활성화한 뒤 다시 시도해주세요." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: 첫 단계에서 ToolSearch 로 prefix 의 도구를 조회. 결과가 비어 있으면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + 타입 라우팅

사용자 인자에서 입력 타입을 자동 감지:

- `figma.com/design/:fileKey/...?node-id=:nodeId` → **Figma 경로**
- `*.pen` 로컬 경로 → **Pencil 경로**
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

Figma URL 파싱:
- fileKey = path 의 `/design/` 다음 세그먼트
- nodeId = `?node-id=` 쿼리. `-` → `:` 로 변환

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집 (deep)

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 또는 `mcp__figma-console__figma_get_file_data(verbosity:summary)`
2. 각 frame 마다:
   - deep tree (`get_design_context` 또는 `figma_get_component_for_development_deep`)
   - 스크린샷 1장 (`get_screenshot` 또는 `figma_capture_screenshot`)

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별 → 멀티 프레임 자동 감지
   - 선택이 비어 있으면: 최상위 frame 중 user visible 한 첫 frame 자동 선택. 그것도 0개면 "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id], depth:3)` 로 deep 노드 트리
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(nodeId=frame_id)` 로 이미지 1장
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 폰트/컬러/사이즈 팔레트 추출

### Step 4 — 프로젝트 컨텍스트 수집 (CEO 핵심)

CEO 리뷰는 **프로젝트 자산** 과 비교가 핵심. 디자인 파일 디렉터리 또는 프로젝트 루트에서 다음을 수집:

1. `DESIGN.md` / `design-system.md` / 기타 디자인 시스템 문서 → brand token / 컬러 / 폰트 / spacing 명세 추출
2. `*.spec.md` / `STAT-*.md` / `docs/designs/*.md` → 도메인 명세 / 사용자 / 문제 정의
3. `user-stories-*.md` / `user-story-*.md` → 사용자 행동 모델
4. 기존 review .md (같은 디렉터리 `design-reviews/`) → 이미 돌린 rubric 결과
5. `git log --oneline -30` 가능하면 → 최근 작업 방향

수집 실패해도 진행 (정적 분석 한계 명시).

### Step 5 — Classifier (디자인 타입 + 추정 도메인)

수집된 프레임 1장 + 프로젝트 컨텍스트 보고 분류:

- **DOMAIN MATCH** — 프로젝트 컨텍스트와 일치 (예: STAT-152 광고 분석 프로젝트 + 광고 KPI dashboard)
- **DOMAIN MISMATCH** — 프로젝트 컨텍스트와 불일치 (예: Toss/쿠팡 fintech 프로젝트 + generic Acme SaaS dashboard)
- **GREENFIELD** — 프로젝트 컨텍스트 빈약, 비교 기준 부재
- **PLACEHOLDER** — Acme/Lorem/그래픽 더미 신호 강함

분류 결과를 보고서 메타에 기록. **DOMAIN MISMATCH** + **PLACEHOLDER** 는 자동으로 Premise/Leverage 점수 -3 시드.

### Step 6 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 화면 누구를 위한 어떤 도구로 보이는가: [한 문장]
- 이 화면을 처음 본 사용자가 5초 내 할 수 있는 행동: [한 문장 — 없으면 "없음"]
- placeholder/실 product 신호 ratio: [예: 7:3 placeholder 우세 / 또는 9:1 product 우세]
- "이거 sample 인가요?" 라고 물어볼 가능성: [Low/Med/High]
- 한 단어 요약: [단어]
- 인상 메모: [정체성 신호 / vision 신호 / placeholder 흔적]
```

이 섹션은 진단가 1인칭. 헤지하지 않는다.

### Step 7 — Inferred Design System vs Project Design System

수집된 노드 트리 vs Step 4 의 `DESIGN.md` 명세 diff:

- **Fonts**: 실제 사용 폰트 vs DESIGN.md 명세 → 매칭/불일치
- **Colors**: 실제 컬러 vs token 명세 → near-miss 식별 (예: `#0F172A` slate vs Toss `#191F28`)
- **Type scale**: 실제 fontSize 분포 vs 명세 hierarchy
- **Spacing**: 실제 padding/gap vs 명세 scale

`DESIGN.md` 없으면: 일관성만 평가 (자체 일관성).

### Step 8 — Premise Challenge (Phase 2)

`/plan-ceo-review` 의 0A 패턴 적용. 다음 3개 질문 답 작성:

1. 누가 본다? (구체적 페르소나, "사용자" 같은 일반어 거부)
2. 어떤 결정 돕는다? (한 문장 결정. "현황 파악" 같은 vague 거부)
3. 안 하면? (현 디자인 사라지면 실 사용자 영향 0이면 placeholder)

답이 vague / 불명 / placeholder 면 Premise 항목 점수 0-3.

### Step 9 — Existing Leverage 매핑 (Phase 3)

Step 4 에서 수집한 도메인 자산을 Dashboard 요소와 1:1 매핑 표 작성:

| 현 디자인 요소 | 매핑 가능 자산 | 현재 사용? |
|---------------|---------------|-----------|
| KPI 카드 | STAT-XXX / user-story | Y/N |
| 메뉴 | spec navigation | Y/N |
| 차트 | spec data model | Y/N |
| (각 요소) | (자산) | Y/N |

미사용 자산이 많을수록 Existing Leverage 항목 점수 낮음 (0-5).

### Step 10 — Dream State Delta

12개월 후 vision 명시 (Step 4 자산에서 추정 가능하면 추출, 안 되면 inference + 라벨링):

```
CURRENT                THIS DESIGN          12-MO IDEAL
[describe]   ─────▶   [delta]    ─────▶   [target]
```

vector 방향이 ideal 로 향하면 Dream State 점수 7-10. 옆 방향 polish 면 3-6. 반대 방향이면 0-2.

### Step 11 — CEO 10항목 평가 (Phase 4)

각 항목마다 0-10 점수. 정적 검증 불가능한 항목은 `N/A` + 사유. 위반/개선점은 finding 1개로 작성:
- **severity** (critical / warning / info)
- **evidence** (노드 경로/이름/수치)
- **fix** (구체 액션)
- **참고** (방법론 출처 — CEO Review framework / Bezos / Munger / Jobs / Toss DESIGN.md 등)

**점수 기준:**
- 10 — exemplary, 도메인 정체성/leverage/vision 모두 강함
- 8-9 — solid, 사소한 polish 만
- 6-7 — 기능적이나 위 layer 개선 여지
- 4-5 — 정체성·자산 활용 눈에 띄는 문제
- 0-3 — placeholder / wrong-problem / 도메인 미스매치
- N/A — 정적 분석으로 검증 불가

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding 당)
- warning: -1 ~ -2
- info: 점수 영향 X, 노트만

### Step 12 — Strategy Health Grade 산출

**평균 환산** = (적용 항목 점수 합) / (적용 항목 수) → 0-10

**Grade 환산:**
- 9.0-10 = **A** (Excellent — vision clear, leverage strong, identity locked)
- 7.5-8.9 = **B** (Good — minor strategy polish)
- 6.0-7.4 = **C** (Acceptable — strategy gaps)
- 4.0-5.9 = **D** (Poor — identity/scope significant rework)
- 0-3.9  = **F** (Critical — wrong problem / placeholder / overhaul)

**추가 헤드라인:**
- **Identity Verdict**: domain match + brand token align + first-class KPI = "product vs placeholder" 한 줄
- **Leverage Score**: 도메인 자산 사용률 % (Step 9 매핑 표 기준)
- **Vector Direction**: 12-mo ideal 로 가는가 (Forward / Sideways / Backward / Unknown)

### Step 13 — Implementation Alternatives A/B/C (필수)

`/plan-ceo-review` 0C-bis 패턴. 다음 3개 노선 각각 제시:

**APPROACH A — PIVOT (정체성 회수)**
- Summary: 도메인 자산 적용해 재캐스팅
- Effort: S/M/L (human 일 / CC 분)
- Risk: Low/Med/High
- Pros / Cons / Reuses

**APPROACH B — HOLD (현 노선 polish only)**
- Summary: 현 scope 유지, micro UX/UI 리뷰 결과만 적용
- Effort / Risk / Pros / Cons

**APPROACH C — SCRAP (재시작)**
- Summary: 폐기 + `/ux-burst` 또는 `/design-shotgun` 으로 발산→수렴
- Effort / Risk / Pros / Cons

**RECOMMENDATION**: 보통 A (도메인 자산 있는데 안 쓰면 낭비). 단 PLACEHOLDER + sample 의도 명시면 D (no-op).

### Step 14 — Top-3 Rethink 제안

전체 finding 중 high-impact 3개를 골라 Rethink 카드. 단순 fix 가 아닌 **재설계 방향**.

각 카드 포맷:
- **현재 문제** (frameworks violated + evidence)
- **사용자 영향** + **비즈니스 영향**
- **제안 솔루션** (구체 컴포넌트/레이아웃/도메인 KPI 변경)
- **기대 점수 변화** (항목 N → N')
- **노력 규모** (Low/Medium/High, human days / CC min 양 scale)

선정 우선순위:
1. critical 우선 (특히 Premise / Existing Leverage / First-class KPI)
2. critical 부족하면 warning 으로 채움
3. domain-match → identity → scope 순

### Step 15 — Failure Modes Registry (디자인 관점)

다음 시나리오에 대한 현 디자인 대응 매핑:

| 시나리오 | 현 디자인 대응 | 사용자 영향 | RESCUED |
|---------|---------------|------------|---------|
| 첫 방문, "이게 뭐 하는 도구지?" | ? | ? | Y/N |
| KPI 0 데이터 / null | ? | ? | Y/N |
| 차트 로딩 3초+ | ? | ? | Y/N |
| Activity dead-end | ? | ? | Y/N |
| table 0건 | ? | ? | Y/N |
| 사용자가 잘못된 도구 진입 | ? | ? | Y/N |

RESCUED=N + USER SEES=Silent 행은 **CRITICAL GAP** 로 카운트.

### Step 16 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ceo-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 17 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 Strategy Health Grade + 평균 + critical/warning + Identity Verdict 한 줄 요약
- Recommended Approach (A/B/C/D)

## 보고서 구조 (한국어)

```markdown
# CEO Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 디자인 타입: {DOMAIN MATCH | DOMAIN MISMATCH | GREENFIELD | PLACEHOLDER}
- 프로젝트 컨텍스트 수집: {DESIGN.md ✓ / spec ✓ / user-stories ✓ / 기존 review N개}
- 추정 페르소나: {역할·목적·기기}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: CEO Review framework — Premise·Leverage·Dream·KPI·Scope·IA·State·Brand·Affordance·Hygiene (10 항목)
- 모델: `/plan-ceo-review` (Garry's framework) + Bezos one-way/two-way door + Munger inversion + Jobs focus-as-subtraction

## 헤드라인
- **Strategy Health Grade: {A-F}** ({평균}/10)
- **Identity Verdict**: {product | placeholder | ambiguous} — {한 줄}
- **Leverage Score**: {N}% 도메인 자산 사용
- **Vector Direction**: {Forward | Sideways | Backward | Unknown} (12-mo ideal 기준)
- 적용 항목: {applied}/10 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건
- Failure Mode CRITICAL GAPS: {n}건

## First Impression
- 이 화면 누구를 위한 어떤 도구로 보이는가: {...}
- 5초 내 할 수 있는 행동: {...}
- placeholder/product ratio: {...}
- "sample 인가요?" 가능성: {Low/Med/High}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Premise Challenge

| Q | 답 |
|---|---|
| 누가 본다? | {구체 페르소나 또는 "불명"} |
| 어떤 결정 돕는다? | {한 문장 또는 "없음"} |
| 안 하면? | {실 영향 또는 "0"} |

## Existing Leverage 매핑

| 현 디자인 요소 | 매핑 가능 자산 | 현재 사용? |
|---------------|---------------|-----------|
| ... | ... | Y/N |

## Dream State Delta

```
CURRENT                THIS DESIGN          12-MO IDEAL
[describe]   ─────▶   [delta]    ─────▶   [target]
```

## Inferred Design System vs Project Design System

| 토큰 | 실제 사용 | DESIGN.md 명세 | 일치 |
|------|----------|----------------|------|
| Primary color | ... | ... | ✓/✗ |
| Font | ... | ... | ✓/✗ |
| Charcoal | ... | ... | ✓/✗ |
| Spacing scale | ... | ... | ✓/✗ |

## 점수표 (10 항목)

### A. Strategy

| # | Item | 점수 | 비고 |
|---|------|------|------|
| 1 | Premise | - | - |
| 2 | Existing Leverage | - | - |
| 3 | Dream State | - | - |
| 4 | First-class KPI | - | - |

### B. Execution

| # | Item | 점수 | 비고 |
|---|------|------|------|
| 5 | Scope Intentionality | - | - |
| 6 | IA Identity | - | - |
| 7 | State Coverage | - | - |

### C. Identity

| # | Item | 점수 | 비고 |
|---|------|------|------|
| 8 | Brand Token Alignment | - | - |
| 9 | Next-step Affordance | - | - |

### D. Hygiene

| # | Item | 점수 | 비고 |
|---|------|------|------|
| 10 | Cleanup | - | - |

## Findings

### {항목명} — score: {N}
- **severity**: critical | warning | info
- **evidence**: {노드 경로/이름/수치}
- **fix**: {구체 액션}
- **참고**: CEO Review framework — {Premise/Leverage/Dream/...} + {Bezos/Munger/Jobs/Toss DESIGN.md 등 적용}

{위반/개선점이 있는 항목만 나열}

## Implementation Alternatives

### APPROACH A — PIVOT (recommended/not)
- Summary: ...
- Effort: {S/M/L} (human: ~{N}일 / CC: ~{N}분)
- Risk: {Low/Med/High}
- Pros: ...
- Cons: ...
- Reuses: ...

### APPROACH B — HOLD
- Summary: ...
- Effort / Risk / Pros / Cons

### APPROACH C — SCRAP
- Summary: ...
- Effort / Risk / Pros / Cons

**RECOMMENDATION**: {A/B/C/D} — {한 줄 이유}

## Top-3 Rethink 제안

### Proposal 1 — {항목명} 재설계
- **현재 문제**: {framework violated + evidence}
- **사용자 영향**: {...}
- **비즈니스 영향**: {...}
- **제안 솔루션**: {...}
- **기대 점수 변화**: {항목} {N} → {N'}
- **노력**: {Low/Medium/High} (human: ~{N}일 / CC: ~{N}분)

### Proposal 2 — ...
### Proposal 3 — ...

## Failure Modes Registry

| 시나리오 | 현 디자인 대응 | 사용자 영향 | RESCUED | TEST | LOGGED |
|---------|---------------|------------|---------|------|--------|
| ... | ... | ... | Y/N | Y/N | Y/N |

CRITICAL GAPS (RESCUED=N + USER SEES=Silent): {n}건

## NOT in scope
- {본 리뷰에서 다루지 않는 영역 — micro UX/UI polish 등}

## What already exists (자산 매핑)
- {프로젝트 컨텍스트에서 수집한 자산 목록}

## Dream state delta
- {현 위치 → 이상향까지 vector 거리}

## N/A 항목 (정적 분석 한정)
- Premise (1) 일부: 실제 사용자 인터뷰 / analytics 필요
- Dream State (3) 일부: 12-mo 로드맵 비공개 시 inference
- 일부 항목: 비즈니스 KPI / 실 사용자 행동 데이터 별도 필요

## 다음 단계 (권장 후속)
- Approach A 채택 시: 도메인 자산 매핑 표 기준 KPI/메뉴/state 재정의
- Approach B 채택 시: micro UX/UI 리뷰 결과(`/design-ux-*-review`, `/design-ui-*-review`) finding fix
- Approach C 채택 시: `/ux-burst` 또는 `/design-shotgun` 으로 발산→수렴
- 공통: 5-8명 사용성 테스트 (Premise 가설 검증)
```

## 인자

```
/design-ceo-review <Figma URL | .pen path>
```

- 위치 인자 1개만 필수
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- 옵션 인자 없음 (간결 디폴트 우선)

## 예시

### 예시 1 — Pencil 단일 프레임
```
/design-ceo-review ~/Desktop/projects/design/test.pen
```
→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택 frame 감지 → 프로젝트 디렉터리 `DESIGN.md` / `STAT-*.md` / `user-stories-*.md` 수집 → 분류(DOMAIN MATCH/MISMATCH/PLACEHOLDER) → First Impression → Design System diff → Premise/Leverage/Dream → 10항목 평가 → Approaches A/B/C → Top-3 Rethink → `./design-reviews/design-ceo-review-dashboard-20260515-1230.md` 생성

### 예시 2 — Figma URL
```
/design-ceo-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```
→ Figma MCP 체크 → metadata + deep tree + screenshot → 프로젝트 컨텍스트(`docs/` / `DESIGN.md`) 수집 → 동일 흐름

### 예시 3 — MCP 미연결
```
/design-ceo-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → 안내 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 항목명은 영어 원어 유지 (Premise, Existing Leverage, Dream State, First-class KPI 등)
- finding 의 evidence/fix 는 구체적 노드명·수치·도메인 자산 매핑 명시
- 보고서는 한 프레임당 한 파일
- finding 헤더 포맷 `### {항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)
- Approaches / Top-3 Rethink / Failure Modes / Implementation Alternatives 는 annotate-design 파싱 범위 밖 (CEO 리뷰 고유 섹션)

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다. session-key prefix 는 `ceo` 로 자동 결정 (annotate-design 의 review-type 매핑 규약 기준).

워크플로:
```
/design-ceo-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md>     → 디자인 파일에 시각 코멘트 부착 (session-key: ceo-{HHmm})
```

## 다른 리뷰 스킬과의 관계

CEO 리뷰는 **위 layer** — 다른 리뷰들이 micro polish 면, 이건 정체성/scope/vision. 보통 micro 리뷰 결과 점수가 6~7 에서 막힐 때 위 layer 진단이 필요.

| Layer | 스킬 | 평가 대상 |
|-------|------|----------|
| 전략 | **design-ceo-review** (이 스킬) | 정체성·scope·도메인 자산·vision |
| UX 휴리스틱 | design-ux-nielsen / lawsofux / ixdf / ecommerce | 사용성·인지·휴리스틱 |
| UI 시각 | design-ui-polish / critic / ixdf / nielsen / lawsofux / ecommerce | 시각·타이포·컬러·hierarchy |
| 코멘트 부착 | annotate-design | 위 모든 리뷰의 시각화 |

이상적 순서: **design-ceo-review → 노선 결정(A/B/C) → micro UX/UI 리뷰 → annotate-design** .

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- micro UX 휴리스틱 / micro UI 시각 평가 — 각 전용 스킬 책임
- 라이브 사이트 audit / 인터랙션 / perf 실측 — gstack `/design-review` 책임
- 코드 PR / plan 리뷰 — `/plan-ceo-review` 책임 (이 스킬의 코드 원본)
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일 진단만

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인 (별도 references 디렉터리 없음)
- 방법론 출처: `/plan-ceo-review` (Garry's framework, CEO/founder cognitive patterns)
- 사상 출처: Jeff Bezos one-way/two-way doors · Charlie Munger inversion · Steve Jobs focus as subtraction · Andy Grove paranoid scanning · Ben Horowitz wartime CEO · Brian Chesky founder mode · Sam Altman willfulness as strategy · Dieter Rams "as little design as possible"
- 코드 원본 차이: `/plan-ceo-review` 는 코드 plan/PR 대상 11 section 풀 리뷰. 본 스킬은 정적 디자인 frame 대상 10 항목 압축
- 도메인 자산 입력: 프로젝트 루트의 `DESIGN.md` / `STAT-*.md` / `user-stories-*.md` / `docs/designs/*.md` / 기존 `design-reviews/*.md`
