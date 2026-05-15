---
name: design-ux-flow-review
review-level: L2 Structure
description: "[L2 Structure] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임 시퀀스(또는 flow entry hub 단일 프레임)를 user flow / task journey 단위로 정적 분석하여 한국어 마크다운 리뷰 보고서를 생성. 6 lens 모듈 rubric — Flow(8) + IA(6) + Edge State(7) + Dark Pattern(6) + Conversion(5) + Habit(4) = 36 항목. flow 타입(Checkout/Onboarding/Dashboard/Form/Browse/Task) 자동 분류로 lens on/off, --lens 옵션으로 수동 override. Structure Health Grade(A-F) 헤드라인 + per-lens sub-grade + Top-3 Friction(drop-off 위험순) + 재설계 제안. 단일 프레임 리뷰(design-ux-nielsen/ixdf/lawsofux-review)와 달리 macro / multi-frame / app-wide 구조 단위. 사용자가 \"user flow 리뷰\", \"유저 흐름 리뷰\", \"journey 평가\", \"task flow 분석\", \"step transition 리뷰\", \"flow review\", \"IA 리뷰\", \"네비게이션 리뷰\", \"빈상태/에러상태 검토\", \"다크패턴 점검\", \"전환율 리뷰\", \"습관 루프 평가\", \"/design-ux-flow-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 L2 Structure 단위 UX 리뷰를 요청할 때 사용."
---

# design-ux-flow-review

**Review Level**: L2 Structure/UX — multi-frame flow + IA + edge state + dark pattern + conversion + habit.

L2 Structure 추상화 단계의 통합 리뷰 스킬. 6 lens 모듈 rubric 으로 단일 화면 휴리스틱(L0/L1)이 잡지 못하는 macro 구조 friction 을 잡는다. flow 타입 자동 분류로 lens on/off, `--lens` 옵션으로 수동 override. 리포트만 생성한다 — 코멘트 게시는 `annotate-design` 책임.

평가 렌즈 = "사용자가 목표 달성까지 step → step 이동하면서 어디서 막히는가? 정보 구조·빈상태·다크패턴·전환·습관 측면에서 어디가 구멍인가?"

## 추상화 위치

Garrett 5 Planes 의 **Structure** / Spool 5 Resolutions 의 **App-wide** / Miller Service Levels 의 **UX** / NN/g Granularity 의 **User Flow + Task Flow + IA**. Skeleton(요소·레이아웃) 아래, Service Experience(멀티 채널·service blueprint) 위.

## 입력 단위 — flow

본 스킬은 **flow 1개 = 보고서 1개**. flow 정의:

- **Multi-frame flow**: 사용자가 선택한 frame 시퀀스 2+ → step 0 → step 1 → ... → goal frame
- **Hub flow**: 단일 frame(Dashboard, Home 등) 가 여러 task 의 entry → 추론 가능한 outbound flow N개를 각 sub-flow 로 평가
- **End-to-end task flow**: 시작 → 완료까지 모든 frame (예: 회원가입 frame 5장, 체크아웃 frame 7장)

사용자가 명시적으로 flow goal 을 인자로 주거나 frame 선택 순서로 시퀀스가 결정된다.

## 6 Lens × 36 항목

### Lens A. Flow (8항목) — happy path 행위·인지

NN/g Cognitive Walkthrough + Norman Action Cycle + NN/g Journey 핵심 압축.

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| A1 | Q1 Right Result | 사용자가 이 step 에서 올바른 결과를 시도하는가 (goal 정합) | Yes |
| A2 | Q2 Notice Action | 올바른 액션이 표면화·가시화되는가 (affordance) | Yes |
| A3 | Q3 Associate Action | 라벨·아이콘이 결과와 연관되는가 (label clarity) | Yes |
| A4 | Q4 Progress Feedback | 액션 후 진행 신호가 있는가 (feedback) | Yes |
| A5 | Gulf of Execution | "어떻게 할지" 불명 — affordance·mapping·visibility 부재 step | Yes |
| A6 | Gulf of Evaluation | "됐는지" 불명 — feedback·state·결과 가시성 부재 step | Yes |
| A7 | Friction / Low Point | 가장 큰 pain step (인지 부담·입력 부담·결정 부담) | Yes |
| A8 | Moment of Truth | flow 성패 가르는 결정 step (첫 5초·결제 직전·에러 직후) | Yes |

A1-A4 는 step 평균, A5-A8 은 flow 전체 평가.

### Lens B. IA (6항목) — 정보 구조 (Rosenfeld Polar Bear + NN/g)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| B1 | Organization System | 분류 체계(계층·사전식·하이브리드) 일관성, mutually exclusive | Yes |
| B2 | Labeling System | 라벨 텍스트·아이콘 의미 통일, 중복·충돌 없음 | Yes |
| B3 | Navigation System | global / local / contextual / breadcrumb nav 적절성 | Yes |
| B4 | Search System | 검색 진입·결과·필터 (해당 flow 가 검색 포함 시) | Yes |
| B5 | Findability | 목표 정보·기능 도달 경로 가시성 (3-click 절대 X, scent 우선) | Yes |
| B6 | Information Scent | 각 link·CTA 가 다음 step 내용을 예측 가능하게 하는가 | Yes |

### Lens C. Edge State (7항목) — 비-happy path

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| C1 | Empty — First Use | 첫 진입 시 빈 화면에 안내·illustration·primary CTA | Yes |
| C2 | Empty — No Results / Cleared | 검색 결과 0건·사용자가 비운 상태에 회복 경로 | Yes |
| C3 | Error — Validation | 폼 검증 에러 메시지 위치·구체성·plain language | Yes |
| C4 | Error — System / Network | 시스템·네트워크 에러에 사용자 책임 아님 톤 + retry | Yes |
| C5 | Error — Recovery Path | 에러 후 사용자가 어디로 가는가, 입력값 보존, undo | Yes |
| C6 | Loading — Skeleton vs Spinner | 1s+ 표시 / skeleton 적절성 / reflow 방지 | Yes |
| C7 | Loading — Long / Cancellable | 10s+ progress·취소 가능 | Yes |

### Lens D. Dark Pattern (6항목) — 윤리 (Brignull deceptive.design)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| D1 | Sneaking | 결제 막판 숨겨진 항목 추가, 동의 없는 add-on | Yes |
| D2 | Roach Motel | 가입·구독은 쉽고 해지·삭제는 어려운 비대칭 | Yes |
| D3 | Forced Action | 부가 정보·계정·뉴스레터 강제 등록 | Yes |
| D4 | Hidden Cost | 체크아웃 막판 배송비·수수료 노출 | Yes |
| D5 | Fake Urgency / Scarcity | 가짜 카운트다운·"3명이 보고 있음" 등 조작 | Yes |
| D6 | Preselection | 기본 동의 체크·뉴스레터 opt-in default | Yes |

> 검증: 모두 ✅ 위반 없음 = lens D 만점. 위반 1건당 critical.

### Lens E. Conversion (5항목) — MECLABS Conversion Sequence Heuristic

C = 4m + 3v + 2(i − f) − 2a

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| E1 | Motivation (m) | 사용자가 이 flow 에 진입한 동기·맥락 정합 | Partial |
| E2 | Value Proposition (v) | 헤드라인·CTA·subhead 가 제공 가치 명확히 전달 | Yes |
| E3 | Incentive (i) | 보상·할인·무료 trial 등 당근 명시 | Yes |
| E4 | Friction (f) | 입력 부담·step 수·decision load 등 마찰 | Yes |
| E5 | Anxiety (a) | 신뢰 부재·보안 우려·환불 정책 불명 등 불안 | Yes |

### Lens F. Habit (4항목) — Hooked Model (Nir Eyal)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| F1 | Trigger | 외부(알림·이메일)·내부(감정·상황) 재진입 trigger | Partial |
| F2 | Action | Fogg 단순화(시간·비용·인지·물리·사회·루틴) | Yes |
| F3 | Variable Reward | Tribe(소셜)·Hunt(콘텐츠·자원)·Self(완성·숙달) | Yes |
| F4 | Investment | 데이터 입력·팔로우·저장 등 사용자 투자 → 다음 trigger 강화 | Yes |

## 자동 lens 라우팅

flow 타입 자동 분류(Step 4) → lens on/off:

| Flow Type | A Flow | B IA | C State | D Dark | E Conv | F Habit | 적용 항목 |
|-----------|:------:|:----:|:-------:|:------:|:------:|:-------:|:--------:|
| CHECKOUT / PAYMENT | ✓ | ✓ | ✓ | ✓ | ✓ | — | 32 |
| ONBOARDING / SIGNUP | ✓ | — | ✓ | — | ✓ | ✓ | 24 |
| DASHBOARD HUB | ✓ | ✓ | ✓ | — | — | ✓ | 25 |
| MULTI-STEP FORM | ✓ | — | ✓ | — | ✓ | — | 20 |
| CONTENT BROWSE | ✓ | ✓ | ✓ | — | — | — | 21 |
| TASK COMPLETION | ✓ | — | ✓ | — | — | — | 15 |
| HYBRID | ✓ | ✓ | ✓ | △ | △ | △ | 21~36 |

수동 override: `--lens A,B,C` (콤마 구분, A-F).

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일에서 **2+ frame 시퀀스** 또는 **hub frame** 을 선택하고 "user flow 리뷰", "유저 흐름 평가", "journey 분석", "task flow 검토", "IA 리뷰", "네비게이션 평가", "빈상태/에러상태 점검", "다크패턴 audit", "전환율 진단", "습관 루프 평가", "drop-off 진단" 등을 요청할 때
- 단일 화면 휴리스틱(Nielsen·IxDF·Laws) 이미 돌렸으나 macro 구조 관점 보완이 필요할 때
- 신규 flow 출시 전 friction · dead-end · Moment of Truth · 윤리·전환·리텐션 종합 점검이 필요할 때
- 체크아웃·회원가입·온보딩·결제 등 conversion-critical flow 의 step economy 평가

## Do Not Use

- 단일 프레임 micro 휴리스틱 평가:
  - Nielsen 9 → `design-ux-nielsen-review`
  - IxDF 12 → `design-ux-ixdf-review`
  - Laws of UX 23 인지법칙 → `design-ux-lawsofux-review`
  - 이커머스 funnel(폼·필터·체크아웃 5 카테고리) → `design-ux-ecommerce-review`
- 시각·감성 UI 레이어 평가 → `design-ui-*-review`
- 멀티 채널 service blueprint / backstage → `design-ux-service-review` (L3)
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 발산형 UX 재해석 / 시안 생성 → `ux-reimagine` / `ux-burst` / `ux-ray`
- 라이브 사이트 audit → gstack `/design-review`
- 단일 frame 만 선택된 상태에서 hub flow 추론이 불가능한 경우 → `design-ux-ixdf-review` 권장

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 중 하나 활성화 후 재시도." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: 첫 단계에서 ToolSearch 로 prefix 의 도구를 조회. 결과가 비어 있으면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + flow 모드 라우팅

사용자 인자에서 입력 타입을 자동 감지:

- `figma.com/design/:fileKey/...?node-id=:nodeId` → **Figma 경로**
- `*.pen` 로컬 경로 → **Pencil 경로**
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

flow 모드 자동 감지:

- frame 2+ 선택 → **Multi-frame mode** (시퀀스 = 선택 순서)
- frame 1개 선택 → **Hub mode** (해당 frame 의 outbound flow N개 추론)
- 선택 없음 → "Pencil/Figma 에서 리뷰할 flow 의 frame(들)을 선택해주세요. 1개면 hub 모드, 2+개면 시퀀스 모드로 분석합니다." 출력 후 종료

옵션 인자 처리:
- `--goal "{task goal}"`: 평가 렌즈에 user goal 명시
- `--lens A,B,C`: 사용할 lens 명시(A-F 콤마 구분). 미지정 시 flow type 기반 자동 라우팅.

### Step 2 — MCP 사전 체크

Prerequisites 표 기준 ToolSearch. 미연결이면 안내 출력 후 종료.

### Step 3 — flow 데이터 수집

**Multi-frame mode (Figma):**
1. 선택 frame 마다 `get_metadata` + `get_design_context(depth:8)` + `get_screenshot`
2. frame 시퀀스 = 선택 순서
3. frame 간 추정 transition trigger 식별 (각 frame 의 CTA·link·primary button 추출)

**Multi-frame mode (Pencil):**
1. `open_document` + `get_editor_state` → 선택 frame 목록
2. 각 frame `batch_get(readDepth:4)` + `snapshot_layout` + `get_screenshot`
3. 시퀀스 = 선택 순서 또는 frame name 패턴 (`Step 1`, `Step 2` 등) 자동 정렬

**Hub mode:**
1. 단일 frame 정보 수집
2. frame 내 outbound trigger 식별 (sidebar nav, KPI card, button, table row → flow F: Nav / Drill-down N)
3. 사용자 goal 추정 (frame name + 추출된 CTA 패턴 기반)

### Step 4 — Classifier (flow 타입 + 추정 페르소나 + lens 라우팅)

수집된 flow 를 분류:

- **CHECKOUT/PAYMENT** — 카트→결제→완료 (Conversion-critical, error tolerance ↑)
- **ONBOARDING/SIGNUP** — 가입→온보딩→첫 활동 (Ease of Learning ↑, Habit trigger ↑)
- **DASHBOARD HUB** — 단일 화면 entry → 다수 task flow 분기 (Affordance ↑, IA ↑)
- **MULTI-STEP FORM** — 폼 step 분할 (Progress · Validation ↑)
- **CONTENT BROWSE** — 검색·필터·상세 (Findable · Step Economy ↑, IA ↑)
- **TASK COMPLETION** — 특정 작업 수행 (Effectiveness · Efficiency ↑)
- **HYBRID** — 위 혼재

분류 결과 + 추정 페르소나 1-2명을 보고서 메타에 기록.

**lens 자동 라우팅**: 위 라우팅 표 기준 적용 lens 결정. `--lens` 인자 있으면 그것이 우선.

가중치 미세 조정:
- Checkout: D(Dark)·E(Conv)·C(State) 가중↑
- Onboarding: F(Habit)·E(Conv)·C(State) 가중↑
- Dashboard Hub: A(Flow Q2)·B(IA)·F(Habit) 가중↑
- Multi-step Form: C(State Error·Validation)·A(Flow Q4) 가중↑
- Content Browse: B(IA Findability·Scent)·A(Flow) 가중↑

### Step 5 — First Impression (Phase 1)

flow 전체 스크린샷 시퀀스 본 직후 1인칭 작성:

```
- 이 flow 가 달성하려는 목표: [한 문장]
- 추정 사용자 시작 동기: [한 문장]
- 첫 step 진입 시 첫인상: [한 문장]
- 가장 위태로워 보이는 step: [step 번호 + 이유]
- 가장 매끄러워 보이는 step: [step 번호 + 이유]
- 한 단어 요약: [단어]
- 인상 메모: [구체적 긍정/부정]
```

진단가는 헤지하지 않는다.

### Step 6 — Inferred Task Flow Map (Phase 2)

수집된 frame 트리·CTA·link 에서 추출:

- **Flow goal**: 사용자가 이 flow 로 달성하려는 것
- **Entry point**: 시작 frame + 진입 trigger 추정
- **Step list**: step 1..N 표 (frame name / 핵심 액션 / 핵심 CTA / 예상 다음 step)
- **Branch points**: 분기 지점 (선택지 2+ 등장 step)
- **Exit points**: 성공 종료 / 중단 가능 위치
- **Dead-end risks**: 다음 step 추론 불가능한 frame

표 형식:

| Step | Frame | Action | Primary CTA | Next |
|------|-------|--------|-------------|------|
| 1 | Cart | 카트 검토 | "결제하기" | 2 |
| 2 | Address | 주소 입력 | "다음" | 3 |
| ... | ... | ... | ... | ... |

### Step 7 — Per-Step Cognitive Walkthrough (Phase 3) — Lens A 적용 시

각 step 마다 A1-A4 평가. 답: ✅ / ⚠️ / ❌ / N/A. 메모 1-2줄.

| Step | A1 | A2 | A3 | A4 | Verdict | 메모 |
|------|----|----|----|----|---------|------|
| 1 | ✅ | ❌ | ✅ | N/A | **FAIL** | CTA affordance 없음 |
| 2 | ✅ | ✅ | ⚠️ | ✅ | PARTIAL | 라벨 ambiguous |

Verdict: 4Q ✅ = **PASS** / ⚠️1+ ❌없음 = **PARTIAL** / ❌1+ = **FAIL** / N/A 제외.

### Step 8 — 36항목 평가 (Phase 4) — 적용 lens 만

각 항목 0-10 점수. 정적 분석 불가능 항목 `N/A` + 사유. 비적용 lens 항목은 평가 생략(점수표 표시 X).

**점수 기준:**
- 10 — exemplary, friction zero
- 8-9 — solid, minor polish
- 6-7 — functional, 개선 여지
- 4-5 — 눈에 띄는 friction
- 0-3 — 사용자가 step 진입조차 어려움
- N/A — 정적 분석으로 검증 불가

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding)
- warning: -1 ~ -2
- info: 점수 영향 X
- **Dark Pattern lens 위반 1건 = 자동 critical**

finding 1개당: **severity** · **lens** · **evidence**(step·frame 노드 경로·수치) · **fix** · **참고**(방법론 출처).

### Step 9 — Structure Health Grade 산출

**Per-lens sub-grade** (적용 lens 만):
- lens 별 평균 점수 → 0-10

**전체 Grade** = 적용 lens 가중 평균 (가중치 = Step 4 flow type 미세 조정 적용):
- 9.0-10 = **A** (Excellent — friction-free, well-structured)
- 7.5-8.9 = **B** (Good — minor step polish)
- 6.0-7.4 = **C** (Acceptable — step rework)
- 4.0-5.9 = **D** (Poor — flow redesign)
- 0-3.9  = **F** (Critical — flow 전면 재설계)

**추가 헤드라인:**
- **Drop-off Risk**: critical step 개수 + Gulf of Execution 점수 = "어디서 사용자가 이탈할 확률 가장 높은지" 한 줄
- **Moment of Truth**: flow 성패 가르는 step 1-2개
- **Ethics Flag**: Lens D 위반 있으면 별도 경고

### Step 10 — Top-3 Friction 제안

drop-off 위험순으로 3개 friction 선정. 단순 fix 가 아닌 **step-level 재설계 방향**.

각 카드 포맷:
- **friction 위치** (step 번호 + frame)
- **위반 항목** (lens + 항목번호 조합, 예: A2·E4·D1)
- **사용자 영향** (drop-off 시나리오)
- **비즈니스 영향** (conversion·retention)
- **재설계 방향** (step 합치기 / 제거 / 순서 변경 / feedback 추가 / 분할 / 라벨 교체 / state 추가)
- **기대 점수 변화** (항목 N → N')
- **노력 규모** (Low/Medium/High, 1-4 weeks)

선정 우선순위:
1. Lens D (Dark Pattern) 위반 우선 (자동 critical)
2. Lens A: Gulf of Execution + A2(notice action) FAIL step
3. Moment of Truth step
4. critical finding 가장 많이 걸린 step
5. critical 부족하면 warning 으로 채움

### Step 11 — 보고서 작성

**파일 경로**: `./design-reviews/design-ux-flow-review-{flow-slug}-{YYYYMMDD-HHmm}.md`
- `{flow-slug}`: flow goal kebab-case (예: `checkout-completion`, `dashboard-hub`)
- goal 미지정이면 entry frame name 사용
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 12 — 사용자에게 결과 요약

- 생성된 보고서 파일 경로
- Structure Health Grade + 평균 점수 + 적용 lens 목록 + critical/warning 개수
- per-lens sub-grade 한 줄 요약
- Top-3 Friction step 번호 + 한 줄 설명
- Ethics Flag (해당 시)
- 다음 액션 제안 (annotate-design / 사용성 테스트 / 재설계)

## 보고서 구조 (한국어)

```markdown
# Structure Review: {flow goal}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID(s): {nodeId 시퀀스}
- 프레임 이름(s): {frame.name 시퀀스}
- flow 모드: {Multi-frame | Hub}
- flow 타입: {CHECKOUT/PAYMENT | ONBOARDING/SIGNUP | DASHBOARD HUB | MULTI-STEP FORM | CONTENT BROWSE | TASK COMPLETION | HYBRID}
- flow goal: {사용자 인자 또는 추정}
- 추정 페르소나: {역할·동기·기기}
- 적용 lens: {A·B·C·D·E·F 중 적용된 것}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 인라인 시퀀스}
- 방법론: NN/g CW + Norman + NN/g Journey + Rosenfeld IA + NN/g empty/error/loading + Brignull deceptive.design + MECLABS CSH + Hooked Model

## 헤드라인
- **Structure Health Grade: {A-F}** ({평균}/10)
- **Per-Lens Sub-Grade**:
  - Flow(A): {n}/10
  - IA(B): {n}/10 또는 N/A
  - Edge State(C): {n}/10
  - Dark Pattern(D): {n}/10 또는 N/A
  - Conversion(E): {n}/10 또는 N/A
  - Habit(F): {n}/10 또는 N/A
- **Drop-off Risk**: {한 줄 — 가장 위험한 step + 원인}
- **Moment of Truth**: {step 번호 + 이유}
- **Ethics Flag**: {Lens D 위반 시 ⚠️ 표시, 없으면 ✅}
- 적용 항목: {applied}/36 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 flow 가 달성하려는 목표: {...}
- 추정 사용자 시작 동기: {...}
- 첫 step 진입 시 첫인상: {...}
- 가장 위태로워 보이는 step: {...}
- 가장 매끄러워 보이는 step: {...}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Inferred Task Flow Map

| Step | Frame | Action | Primary CTA | Next |
|------|-------|--------|-------------|------|
| 1 | ... | ... | ... | ... |

- **Entry**: {...}
- **Branch points**: {...}
- **Exit points**: {성공·중단}
- **Dead-end risks**: {...}

## Per-Step Cognitive Walkthrough (Lens A 적용 시)

| Step | A1 | A2 | A3 | A4 | Verdict | 메모 |
|------|----|----|----|----|---------|------|
| 1 | ✅ | ❌ | ✅ | N/A | FAIL | ... |

A1: 올바른 결과 시도 / A2: 액션 노출 / A3: 라벨-결과 연관 / A4: 진행 피드백

## 점수표 (적용 lens)

### Lens A. Flow (8)

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| A1 | Q1 right result | - | - |
| A2 | Q2 notice action | - | - |
| A3 | Q3 associate action | - | - |
| A4 | Q4 progress feedback | - | - |
| A5 | Gulf of Execution | - | - |
| A6 | Gulf of Evaluation | - | - |
| A7 | Friction / Low Point | - | - |
| A8 | Moment of Truth | - | - |

### Lens B. IA (6) — 적용 시

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| B1 | Organization System | - | - |
| B2 | Labeling System | - | - |
| B3 | Navigation System | - | - |
| B4 | Search System | - | - |
| B5 | Findability | - | - |
| B6 | Information Scent | - | - |

### Lens C. Edge State (7) — 적용 시

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| C1 | Empty — First Use | - | - |
| C2 | Empty — No Results / Cleared | - | - |
| C3 | Error — Validation | - | - |
| C4 | Error — System / Network | - | - |
| C5 | Error — Recovery Path | - | - |
| C6 | Loading — Skeleton vs Spinner | - | - |
| C7 | Loading — Long / Cancellable | - | - |

### Lens D. Dark Pattern (6) — 적용 시

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| D1 | Sneaking | - | - |
| D2 | Roach Motel | - | - |
| D3 | Forced Action | - | - |
| D4 | Hidden Cost | - | - |
| D5 | Fake Urgency / Scarcity | - | - |
| D6 | Preselection | - | - |

### Lens E. Conversion (5) — 적용 시

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| E1 | Motivation | - | - |
| E2 | Value Proposition | - | - |
| E3 | Incentive | - | - |
| E4 | Friction | - | - |
| E5 | Anxiety | - | - |

### Lens F. Habit (4) — 적용 시

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| F1 | Trigger | - | - |
| F2 | Action | - | - |
| F3 | Variable Reward | - | - |
| F4 | Investment | - | - |

## Findings

### {항목명} — score: {N}
- **severity**: critical | warning | info
- **lens**: A Flow | B IA | C Edge State | D Dark Pattern | E Conversion | F Habit
- **evidence**: step {n} · frame `{nodeId}` · {구체 근거}
- **fix**: {구체 step-level 액션}
- **참고**: {방법론 출처 — Cognitive Walkthrough / Norman / NN/g Journey / Rosenfeld / NN/g state / Brignull / MECLABS / Hooked}

{위반/개선점이 있는 항목만 나열}

## Top-3 Friction

### Friction 1 — step {n} · {항목명}
- **위치**: step {n} (frame `{nodeId}`)
- **위반 항목**: {lens·항목번호 조합, 예: A2·E4·D1}
- **사용자 영향**: {drop-off 시나리오}
- **비즈니스 영향**: {conversion 영향}
- **재설계 방향**: {step 합치기 / 제거 / 순서 변경 / feedback 추가 / 분할 / 라벨 교체 / state 추가}
- **기대 점수 변화**: {항목} {N} → {N'}
- **노력**: {Low/Medium/High} ({n} weeks)

### Friction 2 — ...
### Friction 3 — ...

## Moments of Truth

- step {n} ({이유}): {왜 이 step 이 flow 성패를 가르는가}

## Ethics Flag (Lens D 적용 + 위반 시만)

- {위반 항목 (D1-D6)} at step {n}: {구체 패턴} · 규제 리스크: {GDPR/CPRA/한국 e-privacy 관련 시 명시}

## N/A 항목 (정적 분석 한정)
- {적용했으나 검증 불가한 항목 + 사유}

## 다음 단계 (권장 후속 리서치)
- 5-8명 사용성 테스트 (Top-3 Friction 가설 검증)
- 분석: step transition click-through rate / step별 abandonment / time-to-completion
- annotate-design 스킬로 디자인 파일에 finding 시각화
- 재설계 후 동일 rubric 재평가 (delta 측정)
```

## 인자

```
/design-ux-flow-review <Figma URL | .pen path> [--goal "{task goal}"] [--lens A,B,C,...]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- 옵션 `--goal "{...}"`: 사용자 task goal 명시 (없으면 추정)
- 옵션 `--lens A,B,C`: 적용 lens 명시 (A=Flow, B=IA, C=Edge State, D=Dark Pattern, E=Conversion, F=Habit). 미지정 시 flow type 기반 자동 라우팅.
- frame 시퀀스는 Figma/Pencil **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Pencil multi-frame, 자동 라우팅 (회원가입 시퀀스)
```
/design-ux-flow-review ~/Documents/myapp.pen --goal "회원가입 완료"
```
→ Pencil MCP 체크 → 5개 frame 감지 (Signup → Email → Verify → Profile → Welcome) → Multi-frame mode → flow type = ONBOARDING/SIGNUP → lens A·C·E·F 적용 (B·D off) → 24항목 평가 → 보고서 생성

### 예시 2 — Pencil hub mode (Dashboard entry)
```
/design-ux-flow-review ~/Desktop/projects/design/test.pen
```
→ 단일 Dashboard frame 감지 → Hub mode → flow type = DASHBOARD HUB → lens A·B·C·F 적용 (D·E off) → 25항목 → 보고서 생성

### 예시 3 — Figma multi-frame, 수동 lens override
```
/design-ux-flow-review https://www.figma.com/design/abc/Shop?node-id=42-1024 --goal "결제 완료" --lens A,C,D,E
```
→ Figma MCP 체크 → 5 step (Cart → Address → Payment → Review → Confirm) → flow type = CHECKOUT/PAYMENT 이지만 --lens override 로 B(IA)·F(Habit) 제외 → 26항목 평가 → 보고서

### 예시 4 — Hybrid 전체 적용
```
/design-ux-flow-review ~/Documents/myapp.pen --lens A,B,C,D,E,F
```
→ 36항목 전부 평가

### 예시 5 — MCP 미연결
```
/design-ux-flow-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → 안내 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 항목명은 영어 원어 유지 (Clarity, Gulf of Execution, Findability, Roach Motel, Variable Reward 등)
- finding 의 evidence/fix 는 step 번호·frame nodeId·구체 액션 명시
- 보고서는 한 flow 당 한 파일
- finding 헤더 포맷 `### {항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / lens / evidence / fix / 참고 필드 동일 순서 유지
- Top-3 Friction · Ethics Flag 는 별도 섹션 (annotate-design 파싱 범위 밖)
- Per-Step Walkthrough 표는 annotate-design 마커 매핑 hint 로 활용 가능
- 비적용 lens 의 점수표는 보고서에서 생략 (헤드라인의 Per-Lens Sub-Grade 에는 N/A 표기)

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다. evidence 의 `step {n} · frame \`{nodeId}\`` 패턴에서 nodeId 를 추출해 해당 frame 위에 마커 배치.

워크플로:
```
/design-ux-flow-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일 코멘트 직접 게시 — `annotate-design` 책임
- 단일 frame micro 휴리스틱 평가 — `design-ux-{nielsen,ixdf,lawsofux,ecommerce}-review` 책임
- 시각·감성 UI 평가 — `design-ui-*-review` 책임
- 발산형 UX 대안 생성 — `ux-reimagine` / `ux-burst` / `ux-ray` 책임
- 라이브 사이트 audit / 실측 — gstack `/design-review` 책임
- 멀티 채널 service blueprint / backstage process — `design-ux-service-review` (L3) 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만

## 추상화 단계 비교 (다른 design-ux-* 스킬과의 차이)

| 스킬 | 추상화 단계 | 평가 단위 | 입력 |
|------|-----------|----------|------|
| `design-ux-nielsen-review` | L1 Skeleton / Screen | 단일 frame | frame 1개 |
| `design-ux-ixdf-review` | L1 Skeleton-Structure / Screen | 단일 frame | frame 1개 |
| `design-ux-lawsofux-review` | L1 Skeleton / Microinteraction | 단일 frame | frame 1개 |
| `design-ux-ecommerce-review` | L3 Service / 이커머스 funnel | 단일 frame (이커머스) | frame 1개 |
| `ux-audit-rethink` | L0-L2 holistic | product | product |
| **`design-ux-flow-review`** | **L2 Structure / App / 6 Lens** | **flow 시퀀스 또는 hub** | **frame 시퀀스 또는 hub frame** |
| `design-ux-service-review` | L3 Service Experience | multi-channel + backstage | service map |
| `design-ceo-review` | L5 Strategy | product strategy | product |

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인
- 방법론 출처:
  - **Lens A (Flow)** — NN/g Cognitive Walkthrough https://www.nngroup.com/articles/cognitive-walkthroughs/ · Don Norman *The Design of Everyday Things* (Two Gulfs) · NN/g Journey Analysis https://www.nngroup.com/articles/analyze-customer-journey-map/
  - **Lens B (IA)** — Rosenfeld·Morville·Arango *Information Architecture* 4th ed. (Polar Bear, O'Reilly 2015) · NN/g IA articles https://www.nngroup.com/articles/ia-vs-navigation/ · Information Scent https://www.nngroup.com/articles/information-scent/
  - **Lens C (Edge State)** — NN/g Empty State https://www.nngroup.com/articles/empty-state-interface/ · NN/g Error Messages https://www.nngroup.com/articles/error-message-guidelines/ · NN/g Progress Indicators https://www.nngroup.com/articles/progress-indicators/
  - **Lens D (Dark Pattern)** — Harry Brignull deceptive.design https://www.deceptive.design/types
  - **Lens E (Conversion)** — MECLABS Conversion Sequence Heuristic (C = 4m + 3v + 2(i−f) − 2a) · WiderFunnel LIFT Model (보조)
  - **Lens F (Habit)** — Nir Eyal *Hooked* (Trigger → Action → Variable Reward → Investment) · BJ Fogg Behavior Model (B=MAT, https://behaviormodel.org/) 보조
- 짝 micro 스킬: `design-ux-nielsen-review` · `design-ux-ixdf-review` · `design-ux-lawsofux-review`
- 짝 L3 스킬: `design-ux-service-review` · `design-ux-ecommerce-review`
- 짝 UI 스킬: 본 스킬에 직접 대응 UI 스킬 없음 (Structure 는 UX 고유 추상화 단계)
