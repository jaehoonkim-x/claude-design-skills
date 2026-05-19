---
name: design-ux-jtbd-review
review-level: L5 Strategy
description: "[L5 Strategy] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Clayton Christensen Jobs-To-Be-Done 프레임워크로 정적 분석하여 한국어 마크다운 리뷰 보고서를 생성. \"사용자는 product를 사지 않고 job을 hire한다\" 원칙에 따라 디자인이 사용자 progress를 막거나 돕는지를 5 lens(Job Statement · Functional Job · Emotional Job · Social Job · Forces of Progress)로 진단. JTBD Health Grade(A-F) 헤드라인 + 5 lens 점수 + Job Statement 명확성 + 4 Forces 분석 + Top-3 Misalignment 재설계 제안. stat-front 셀러 핵심 job(매출 보고 → 통제감 → 데이터 기반 의사결정)을 내장 도메인 컨텍스트로 활용. 사용자가 \"JTBD 리뷰\", \"job 분석\", \"jobs to be done\", \"job hire\", \"forces 분석\", \"고용 해고 분석\", \"셀러 job 진단\", \"/design-ux-jtbd-review\"를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 job 관점 UX 진단을 요청할 때 사용."
---

# design-ux-jtbd-review

**Review Level**: L5 Strategy — Jobs-To-Be-Done 5 lens (Job Statement · Functional · Emotional · Social · Forces of Progress).

Clayton Christensen의 "사용자는 product를 사지 않고 job을 hire한다" 원칙을 정적 디자인 분석에 적용하는 스킬. 디자인 표면(시각·UX·flow)이 아닌 **job 층위**—사용자가 어떤 progress를 달성하려는가, 디자인이 그 progress를 가속하는가 저해하는가—를 진단한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 디자인이 사용자가 hire하려는 job을 완수하게 해주는가? 아니면 job 완수를 방해하는 마찰을 만드는가? 4 Forces 중 무엇이 hire/fire 결정을 만드는가?"

## JTBD 핵심 개념

| 개념 | 정의 |
|------|------|
| **Job** | 사용자가 특정 상황에서 달성하고 싶은 progress. product가 아닌 맥락·목적 중심 |
| **Hire** | 사용자가 job을 완수하기 위해 product/feature를 선택하는 행위 |
| **Fire** | 기존 솔루션(습관·경쟁제품)을 포기하고 새로운 것으로 전환하는 행위 |
| **Job Statement** | "When ___, I want to ___, so I can ___" 형식으로 job을 명확하게 표현 |
| **Forces of Progress** | Push(현재 불만) · Pull(새로운 매력) · Anxiety(전환 불안) · Habit(현재 습관 관성) |
| **Functional Job** | 실용적 task 완수 — 빠르게, 정확하게, 효율적으로 |
| **Emotional Job** | 자기인식·자존감·안심 — "내가 유능한 사람으로 느끼고 싶다" |
| **Social Job** | 타인에게 보이는 모습 — "동료에게 데이터 기반 의사결정자로 보이고 싶다" |

## stat-front 내장 도메인 컨텍스트

stat-front(EasySeller) 사용자의 핵심 job 맵:

| Job 유형 | Job Statement | 현재 경쟁 솔루션 |
|---------|--------------|----------------|
| **Functional** | 쿠팡 셀러가 바쁜 운영 중에 매출·광고·재고 현황을 빠르게 파악하여 다음 운영 결정을 내릴 수 있다 | 쿠팡 셀러센터 (느리고 분산됨) |
| **Emotional** | 쿠팡 셀러가 복잡한 데이터를 보면서도 자신이 상황을 통제하고 있다는 자신감과 안심을 느낀다 | 엑셀 수작업 (통제감은 있으나 느림) |
| **Social** | 쿠팡 셀러가 파트너·직원·투자자에게 데이터 기반으로 의사결정하는 전문적인 셀러로 보인다 | 구두 보고 / 직감 의사결정 |

**4 Forces (stat-front 맥락):**
- **Push** (현재 불만): 쿠팡 셀러센터가 느리고, 광고/매출/재고 데이터가 분산되어 종합 파악이 어려움
- **Pull** (새로운 매력): stat-front가 통합 대시보드로 즉각 현황 파악 + 분석 시간 단축을 제공
- **Anxiety** (전환 불안): "새 도구 배우는 시간이 더 걸리지 않을까", "데이터가 정확한가", "유료 전환 비용"
- **Habit** (현재 관성): 쿠팡 셀러센터 + 엑셀 조합이 이미 손에 익음

## 5 Lens Rubric

### Lens 1. Job Statement (명확성)

JTBD 원칙: job은 "When ___, I want to ___, so I can ___" 형식으로 1개의 progress로 표현되어야 한다. 디자인이 이 job을 인식하고 지원하는가?

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| JS1 | Situation Clarity | 화면이 특정 상황(when) 맥락을 반영하는가. generic dashboard 회피 | Yes |
| JS2 | Job Scope | 1화면 1 core job. job 과부하(여러 job 동시 경쟁) 없음 | Yes |
| JS3 | Progress Signal | 사용자가 job 진행 상태를 파악할 수 있는가 (완료/미완 신호) | Yes |
| JS4 | Job Outcome Visibility | job 완수 결과(outcome)가 가시적인가. 완료 후 "됐다" 신호 | Yes |

### Lens 2. Functional Job (실용적 task 완수)

Tony Ulwick ODI(Outcome-Driven Innovation): 사용자의 Functional job outcome을 빠르게·정확하게·효율적으로 달성시키는가?

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| FJ1 | Speed to Insight | 핵심 수치/정보에 도달하는 step 수. 3 click 이내 핵심 도달 | Yes |
| FJ2 | Accuracy Signal | 데이터 신뢰도·출처·최신성 표시. 사용자가 수치를 믿을 수 있는가 | Yes |
| FJ3 | Decision Support | 화면이 결정을 돕는가 vs 단순 정보 표시인가. 비교·추세·기준 제공 | Yes |
| FJ4 | Task Completion Path | 화면에서 job 완수까지 명확한 경로. dead-end 없음 | Yes |

### Lens 3. Emotional Job (자기인식·자존감·안심)

Bob Moesta JTBD Interview: 사용자가 "내가 유능하다", "상황을 통제하고 있다", "불안하지 않다"고 느끼게 해주는가?

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| EJ1 | Competence Signal | 사용자가 숙달된 느낌. 복잡성 적절 노출, overload 없음 | Yes |
| EJ2 | Control & Trust | 예측 가능한 결과. 데이터 신뢰성·일관성. 깜짝 동작 없음 | Yes |
| EJ3 | Anxiety Reduction | 오류·경고·이상값에 안도 톤(blame-free). 복구 경로 명확 | Yes |
| EJ4 | Progress & Ownership | 사용자가 성장·진전 느낌. 어제 대비 성과, 달성 강조 | Yes |

### Lens 4. Social Job (타인에게 보이는 모습)

Christensen Social Dimension: 사용자가 타인(동료·파트너·투자자)에게 어떻게 보이고 싶은지—디자인이 그 이미지를 지원하는가?

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| SJ1 | Shareable Output | 데이터를 외부 공유·보고하기 좋은 형태(export·스냅샷·요약) | Yes |
| SJ2 | Professional Framing | 전문가 의사결정자 이미지를 강화하는 언어·시각 | Yes |
| SJ3 | Expertise Amplification | 도구 사용이 사용자를 "데이터 전문가"처럼 보이게 해주는가 | Yes |
| SJ4 | Social Proof Signal | 벤치마크·업계 평균·순위 등 외부 비교 맥락 | Partial |

### Lens 5. Forces of Progress (Push·Pull·Anxiety·Habit)

4 Forces Switch Interview (Bob Moesta): 현재 디자인이 hire를 가속하는 Push/Pull을 강화하고, hire를 막는 Anxiety/Habit을 줄이는가?

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| FP1 | Push Amplification | 현재 솔루션(셀러센터·엑셀)의 불만을 환기하는 대비 신호 | Partial |
| FP2 | Pull Clarity | stat-front만의 가치(통합·속도·직관)가 화면에서 명확한가 | Yes |
| FP3 | Anxiety Neutralization | 전환 불안(정확도·러닝커브·비용) 해소 장치 존재하는가 | Yes |
| FP4 | Habit Bridging | 기존 워크플로(셀러센터 패턴)와 인터페이스 유사성·이관 용이성 | Partial |

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일을 주고 "JTBD 리뷰", "job 분석", "jobs to be done", "hire/fire 분석", "셀러 job 진단", "forces 분석", "고용 해고 분석" 등을 요청할 때
- micro UX/UI polish 이미 돌렸는데 "디자인이 왜 안 쓰이는지" 원인을 job 층위에서 찾을 때
- 신규 feature/flow의 job fit 검증 전 진단
- 사용자 인터뷰 전 가설 수집: 어떤 Forces가 전환을 막는지 정적 추정
- stat-front 셀러 job 얼라인먼트 체크 (내장 도메인 컨텍스트 자동 적용)

## Do Not Use

- micro UX 휴리스틱 평가 → `design-ux-nielsen-review` / `design-ux-ixdf-review` / `design-ux-lawsofux-review`
- micro UI 시각 폴리시 → `design-ui-*-review`
- user flow/step 구조 분석 → `design-ux-flow-review`
- 전략 정체성/scope/vision → `design-ceo-review`
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 라이브 사이트 audit → gstack `/design-review`
- 사용자 인터뷰 대체 — 이 스킬은 정적 추론. 실 JTBD 인터뷰(Switch Interview)는 별도 리서치 필요

**Do-Not-Use 명확화:** 이 스킬은 **job 층위** — "사용자가 무엇을 달성하려 하는가, 디자인이 그 job을 hire하게 만드는가". 시각·구조·flow polish 와 직교. JTBD 관점 gap이 "사용 저조"의 원인일 때 진단용.

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

옵션 인자 처리:
- `--job "{job statement}"`: 사용자가 직접 job을 명시. 없으면 Step 4에서 추론
- `--persona "{persona}"`: 평가 대상 사용자 페르소나 명시. 없으면 추정
- `--domain stat-front`: stat-front 내장 도메인 컨텍스트 강제 적용 (기본값: 자동 감지)

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 또는 `mcp__figma-console__figma_get_file_data(verbosity:summary)`
2. 각 frame 마다:
   - deep tree (`get_design_context` 또는 `figma_get_component_for_development_deep`)
   - 스크린샷 1장 (`get_screenshot` 또는 `figma_capture_screenshot`)

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별
   - 선택이 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id], depth:3)` 로 deep 노드 트리
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(nodeId=frame_id)` 로 이미지 1장
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 텍스트·라벨 팔레트 추출

### Step 4 — 프로젝트 컨텍스트 + Job 가설 수집

JTBD 리뷰는 **사용자 job 컨텍스트**가 핵심. 프로젝트 루트에서 다음을 수집:

1. `AGENTS.md` / `CLAUDE.md` / `DESIGN.md` → 제품 목적·타겟 사용자·도메인 명세
2. `*.spec.md` / `STAT-*.md` / `docs/designs/*.md` → 사용자 스토리·문제 정의
3. `user-stories-*.md` → 사용자 행동 모델
4. 기존 `design-reviews/*.md` → 이전 리뷰 결과
5. 프로젝트 파일명/경로에서 도메인 키워드 추출 (`stat-front` 감지 시 내장 컨텍스트 자동 적용)

**stat-front 자동 감지**: 프로젝트 경로에 `stat-front` / `easyseller` / `coupang-seller` 가 포함되거나 CLAUDE.md에 "EasySeller" / "쿠팡 셀러" 가 있으면 내장 도메인 컨텍스트(위 Job 맵 + 4 Forces) 자동 적용.

수집 실패해도 진행 (정적 분석 한계 명시). 컨텍스트 없으면 frame에서 추론 + 라벨링.

### Step 5 — Job Statement 추출 (Phase 1)

수집된 디자인 데이터 + 프로젝트 컨텍스트에서 **Job Statement를 최대 3개** 추론:

각 Job Statement 후보:
```
When [상황/맥락],
I want to [달성하고 싶은 것],
So I can [궁극적 결과/progress].
```

평가:
- **Primary Job**: 이 화면이 주로 지원하는 1개 job
- **Secondary Jobs**: 보조적으로 등장하는 job (최대 2개)
- **Job Clarity Score**: 0-10 (10 = 한 문장으로 명확, 0 = job 불명)
- **Job Overload 여부**: 화면에 경쟁하는 job이 3개 이상이면 경고

`--job` 인자 있으면 해당 statement를 Primary Job으로 고정, 나머지 추론.

### Step 6 — First Impression (Phase 2)

프레임 스크린샷 1장 본 직후, job 관점 첫 반응을 1인칭으로 작성:

```
- 이 화면이 지원하는 job (한 문장): [...]
- 사용자가 이 화면에서 "hire"할 만한 이유: [...]
- 사용자가 이 화면을 "fire"할 만한 이유: [...]
- job 완수까지 예상 장벽 (한 문장): [...]
- Functional / Emotional / Social job 중 가장 약한 층위: [...]
- 한 단어 요약: [...]
- 인상 메모: [job 지원 신호 / job 마찰 신호]
```

진단가는 헤지하지 않는다.

### Step 7 — 4 Forces 분석 (Phase 3)

화면에서 정적으로 추론 가능한 4 Forces 매핑:

**Push (현재 불만 신호):**
- 현재 솔루션 대비 불편함을 환기하는 UI 요소 있는가?
- 경쟁 솔루션(셀러센터·엑셀)의 pain point를 대비하는 copy/UX 신호

**Pull (새로운 매력 신호):**
- stat-front 고유 가치(통합·속도·직관)가 화면에서 명확한가?
- 첫 5초 내 사용자가 "이게 내 job을 도와준다"를 느낄 수 있는가?

**Anxiety (전환 불안 신호):**
- 데이터 정확도 신뢰 장치 (출처·최신성·검증 배지)
- 러닝커브 완화 장치 (온보딩·툴팁·빈 상태 안내)
- 비용/리스크 투명성

**Habit (현재 관성 마찰):**
- 기존 셀러센터 패턴과의 인터페이스 유사성
- 기존 워크플로 이관 용이성 신호

각 Force: **강도(High/Med/Low)** + **근거(노드/copy/구조 증거)** + **개선 방향**

### Step 8 — 5 Lens 평가 (Phase 4)

각 항목 0-10 점수. 정적 분석 불가 항목 `N/A` + 사유. 위반/개선점은 finding 1개:
- **severity** (critical / warning / info)
- **lens** (Job Statement / Functional / Emotional / Social / Forces)
- **evidence** (노드 경로·텍스트·구조 증거)
- **fix** (구체 액션)
- **JTBD-출처** (Christensen / Bob Moesta / Tony Ulwick ODI / jobs-to-be-done.com / Strategyn 중 적용)

**점수 기준:**
- 10 — job과 완벽 얼라인. hire 장벽 0
- 8-9 — solid, minor job polish
- 6-7 — functional이나 job 마찰 존재
- 4-5 — job 지원 눈에 띄게 부족
- 0-3 — job mismatch / 사용자가 fire할 가능성 높음
- N/A — 정적 분석 불가

**Severity 가이드:**
- critical: job 완수를 직접 막는 마찰 (-3 ~ -4 per finding)
- warning: job 완수를 늦추거나 불안을 키우는 요소 (-1 ~ -2)
- info: 점수 영향 X, 개선 기회 메모

### Step 9 — JTBD Health Grade 산출

**Per-Lens Sub-Grade** (각 lens 평균):
- Job Statement(JS1-4): 0-10
- Functional Job(FJ1-4): 0-10
- Emotional Job(EJ1-4): 0-10
- Social Job(SJ1-4): 0-10
- Forces of Progress(FP1-4): 0-10

**전체 Grade** = 5 lens 평균 (0-10):
- 9.0-10 = **A** (Excellent — job 완벽 얼라인, hire 마찰 없음)
- 7.5-8.9 = **B** (Good — minor job polish)
- 6.0-7.4 = **C** (Acceptable — job gap 존재, 개선 필요)
- 4.0-5.9 = **D** (Poor — job mismatch 또는 Forces 불균형 심각)
- 0-3.9  = **F** (Critical — 사용자가 fire할 가능성 높음, job 재정의 필요)

**추가 헤드라인:**
- **Job Fit Verdict**: Primary Job 얼라인 수준 한 줄 ("셀러 통제감 job 강하게 지원 / Emotional job 공백")
- **Hire Probability**: High/Med/Low — Forces 분석 종합 (Pull > Anxiety + Habit = hire 가능)
- **Weakest Job Layer**: Functional / Emotional / Social 중 가장 낮은 lens

### Step 10 — Forces Balance 시각화

```
PUSH  ████████░░  [강도: High/Med/Low] — [핵심 근거]
PULL  ██████░░░░  [강도: High/Med/Low] — [핵심 근거]
ANXI  ████░░░░░░  [강도: High/Med/Low] — [핵심 근거]
HABIT ██████░░░░  [강도: High/Med/Low] — [핵심 근거]

hire 가능성 = Push + Pull > Anxiety + Habit → {YES / MARGINAL / NO}
```

### Step 11 — Top-3 Misalignment 제안

전체 finding 중 job 얼라인 관점 high-impact 3개. 단순 fix가 아닌 **job 층위 재설계 방향**.

각 카드 포맷:
- **Misalignment 위치** (lens + 항목번호 + frame 노드)
- **Job Gap** (어떤 job progress를 막는가)
- **Forces Impact** (Push/Pull/Anxiety/Habit 중 어느 Force를 악화시키는가)
- **사용자 영향** (hire 포기 시나리오)
- **재설계 방향** (job 중심 구체 변경)
- **기대 점수 변화** (항목 N → N')
- **노력 규모** (Low/Medium/High)
- **JTBD-출처** (근거 방법론)

선정 우선순위:
1. critical finding (job 완수 직접 차단)
2. Emotional Job + Forces Anxiety 교차 (hire 이탈 가장 직접)
3. Primary Job Statement 불명 또는 Job Overload
4. critical 부족하면 warning으로 채움

### Step 12 — 보고서 작성

**파일 경로**: `./design-reviews/design-ux-jtbd-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

## 보고서 구조 (한국어)

```markdown
# JTBD Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 추정 페르소나: {역할·목적·상황}
- 도메인 컨텍스트: {stat-front 내장 / 프로젝트 수집 / 추론}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 인라인}
- 방법론: JTBD — Christensen "Competing Against Luck" · Bob Moesta Switch Interview · Tony Ulwick ODI · jobs-to-be-done.com · Strategyn

## 헤드라인
- **JTBD Health Grade: {A-F}** ({평균}/10)
- **Job Fit Verdict**: {한 줄}
- **Hire Probability**: {High/Med/Low}
- **Weakest Job Layer**: {Functional | Emotional | Social}
- Per-Lens Sub-Grade:
  - Job Statement(JS): {n}/10
  - Functional Job(FJ): {n}/10
  - Emotional Job(EJ): {n}/10
  - Social Job(SJ): {n}/10
  - Forces of Progress(FP): {n}/10
- 적용 항목: {applied}/20 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression (Job 관점)
- 이 화면이 지원하는 job: {...}
- hire할 만한 이유: {...}
- fire할 만한 이유: {...}
- job 완수까지 예상 장벽: {...}
- 가장 약한 job 층위: {...}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Job Statement 분석

| # | Job Statement | Clarity Score | 비고 |
|---|--------------|---------------|------|
| Primary | When ___, I want to ___, so I can ___ | {0-10} | {...} |
| Secondary 1 | ... | {0-10} | {...} |
| Secondary 2 | ... | {0-10} | {...} |

- **Job Overload**: {있음/없음} — {경쟁 job 목록 또는 "해당 없음"}
- **Job 명확성 종합**: {한 줄}

## 4 Forces 분석

```
PUSH  ████████░░  {High/Med/Low} — {핵심 근거}
PULL  ██████░░░░  {High/Med/Low} — {핵심 근거}
ANXI  ████░░░░░░  {High/Med/Low} — {핵심 근거}
HABIT ██████░░░░  {High/Med/Low} — {핵심 근거}

hire 가능성 = Push + Pull > Anxiety + Habit → {YES / MARGINAL / NO}
```

**Push 상세**: {화면에서 발견한 Push 강화/약화 요소}
**Pull 상세**: {화면에서 발견한 Pull 강화/약화 요소}
**Anxiety 상세**: {화면에서 발견한 Anxiety 유발/해소 요소}
**Habit 상세**: {화면에서 발견한 Habit 마찰/브릿지 요소}

## 점수표 (5 Lens)

### Lens 1. Job Statement (4항목)

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| JS1 | Situation Clarity | - | - |
| JS2 | Job Scope | - | - |
| JS3 | Progress Signal | - | - |
| JS4 | Job Outcome Visibility | - | - |

### Lens 2. Functional Job (4항목)

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| FJ1 | Speed to Insight | - | - |
| FJ2 | Accuracy Signal | - | - |
| FJ3 | Decision Support | - | - |
| FJ4 | Task Completion Path | - | - |

### Lens 3. Emotional Job (4항목)

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| EJ1 | Competence Signal | - | - |
| EJ2 | Control & Trust | - | - |
| EJ3 | Anxiety Reduction | - | - |
| EJ4 | Progress & Ownership | - | - |

### Lens 4. Social Job (4항목)

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| SJ1 | Shareable Output | - | - |
| SJ2 | Professional Framing | - | - |
| SJ3 | Expertise Amplification | - | - |
| SJ4 | Social Proof Signal | - | - |

### Lens 5. Forces of Progress (4항목)

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| FP1 | Push Amplification | - | - |
| FP2 | Pull Clarity | - | - |
| FP3 | Anxiety Neutralization | - | - |
| FP4 | Habit Bridging | - | - |

## Findings

### {lens}.{항목명} — score: {N}
- **severity**: critical | warning | info
- **lens**: Job Statement | Functional Job | Emotional Job | Social Job | Forces of Progress
- **evidence**: {노드 경로/텍스트/구조 증거}
- **fix**: {구체 job 중심 액션}
- **JTBD-출처**: {Christensen "Competing Against Luck" | Bob Moesta Switch Interview | Tony Ulwick ODI | Strategyn | jobs-to-be-done.com}

{위반/개선점이 있는 항목만 나열}

## Top-3 Misalignment

### Misalignment 1 — {lens}.{항목명}
- **위치**: {lens + 항목번호 + 노드}
- **Job Gap**: {어떤 job progress를 막는가}
- **Forces Impact**: {Push/Pull/Anxiety/Habit 중 악화 Force}
- **사용자 영향**: {hire 포기 시나리오}
- **재설계 방향**: {job 중심 구체 변경}
- **기대 점수 변화**: {항목} {N} → {N'}
- **노력**: {Low/Medium/High}
- **JTBD-출처**: {방법론}

### Misalignment 2 — ...
### Misalignment 3 — ...

## N/A 항목 (정적 분석 한정)
- Forces(FP1, FP4): 실제 사용자 인터뷰(Switch Interview) 없이 정적 추론만 가능
- Emotional Job(EJ4): 장기 사용 데이터·리텐션 분석 필요
- Social Job(SJ4): 업계 벤치마크 데이터 없이 부분 추론

## 다음 단계 (권장 후속)
- **Switch Interview 실시**: 5-8명 셀러 대상 Bob Moesta 4 Forces 인터뷰 — 실제 hire/fire 순간 재현
- **Job Statement 검증**: 추론한 Primary Job Statement를 사용자와 직접 확인
- **Anxiety 해소 우선**: critical Anxiety finding부터 디자인 수정 → Forces 재평가
- **annotate-design**: finding을 디자인 파일에 시각 코멘트로 부착
- **재평가**: 수정 후 동일 rubric으로 delta 측정
```

## 인자

```
/design-ux-jtbd-review <Figma URL | .pen path> [--job "{job statement}"] [--persona "{persona}"] [--domain stat-front]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- `--job "{...}"`: Primary Job Statement 직접 명시 (없으면 추론)
- `--persona "{...}"`: 평가 대상 페르소나 명시 (없으면 추정)
- `--domain stat-front`: 내장 도메인 컨텍스트 강제 적용 (자동 감지되지 않을 때)

## 예시

### 예시 1 — Pencil 단일 프레임, 자동 stat-front 감지
```
/design-ux-jtbd-review ~/Desktop/projects/stat-front/design/dashboard.pen
```
→ Pencil MCP 체크 → stat-front 자동 감지 → 내장 Job 맵 + 4 Forces 적용 → 프레임 수집 → Job Statement 추론 → 4 Forces 분석 → 20항목 평가 → `./design-reviews/design-ux-jtbd-review-dashboard-20260518-1400.md` 생성

### 예시 2 — Figma URL, job 직접 명시
```
/design-ux-jtbd-review https://www.figma.com/design/abc123/EasySeller?node-id=42-1024 --job "바쁜 운영 중에 매출 현황을 30초 내에 파악하여 당일 광고비 조정 결정을 내릴 수 있다"
```
→ Figma MCP 체크 → job statement 고정 → 나머지 추론 → Forces 분석 → 보고서 생성

### 예시 3 — Pencil, 페르소나 명시
```
/design-ux-jtbd-review ~/Documents/store-report.pen --persona "월 매출 3천만 원 규모 생활용품 셀러, 혼자 운영, 모바일 위주"
```
→ 해당 페르소나 기준 job 추론 → 평가

### 예시 4 — MCP 미연결
```
/design-ux-jtbd-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → 안내 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- lens 명은 영어 원어 유지 (Functional Job, Emotional Job, Social Job, Forces of Progress, Job Statement 등)
- finding 헤더 포맷 `### {lens}.{항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / lens / evidence / fix / JTBD-출처 5 필드 동일 순서 유지 (annotate-design 호환)
- finding 의 evidence는 노드 경로·텍스트 copy·구조 근거를 구체적으로 명시
- Top-3 Misalignment · N/A 항목 · 다음 단계는 annotate-design 파싱 범위 밖 (JTBD 리뷰 고유 섹션)
- 4 Forces 시각화 블록 항상 포함

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다. session-key prefix 는 `jtbd` 로 자동 결정.

워크플로:
```
/design-ux-jtbd-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md>          → 디자인 파일에 시각 코멘트 부착 (session-key: jtbd-{HHmm})
```

## 다른 리뷰 스킬과의 관계

JTBD 리뷰는 **job 층위** — 다른 리뷰들이 화면/flow/전략을 다루는 동안, 이 스킬은 "사용자가 왜 이 제품을 hire하는가"를 묻는다.

| Layer | 스킬 | 평가 대상 |
|-------|------|----------|
| 전략 | `design-ceo-review` | 정체성·scope·도메인 자산·vision |
| **Job** | **design-ux-jtbd-review** (이 스킬) | **job 얼라인·4 Forces·hire/fire** |
| Flow | `design-ux-flow-review` | user flow·IA·edge state·conversion |
| UX 휴리스틱 | `design-ux-nielsen/lawsofux/ixdf` | 단일 화면 사용성 |
| UI 시각 | `design-ui-*-review` | 시각·타이포·컬러 |
| 코멘트 부착 | `annotate-design` | 위 모든 리뷰 시각화 |

이상적 순서: **design-ceo-review → design-ux-jtbd-review → design-ux-flow-review → micro UX/UI 리뷰 → annotate-design**

## Non-Goals

- 실제 사용자 인터뷰 (Switch Interview) 진행 — 정적 추론만
- 디자인 파일 코멘트 직접 게시 — `annotate-design` 책임
- micro UX 휴리스틱 — 각 전용 스킬 책임
- flow 구조 분석 — `design-ux-flow-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일 진단만

## 참고 자료

- **Clayton Christensen** — *Competing Against Luck* (2016). JTBD 원형 이론. "사람들은 product를 사지 않고 job을 hire한다"
- **Bob Moesta** — Switch Interview 4 Forces methodology. *Demand-Side Sales 101* (2020). jobs-to-be-done.com
- **Tony Ulwick** — Outcome-Driven Innovation (ODI), Strategyn. *Jobs to Be Done: Theory to Practice* (2016). Functional job outcome 측정 체계
- **Strategyn** — strategyn.com. ODI 프레임워크 실무 적용 레퍼런스
- **jobs-to-be-done.com** — 커뮤니티 케이스 스터디 + Job Statement 포맷 레퍼런스
- 짝 전략 스킬: `design-ceo-review` (scope·vision·identity)
- 짝 flow 스킬: `design-ux-flow-review` (macro 구조·step economy)
- 짝 micro 스킬: `design-ux-nielsen-review` · `design-ux-ixdf-review` · `design-ux-lawsofux-review`
