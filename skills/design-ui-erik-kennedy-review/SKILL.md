---
name: design-ui-erik-kennedy-review
review-level: L0 Surface
description: "[L0 Surface] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Erik Kennedy (learnui.design) 의 7 핵심 룰(Hierarchy·Spacing·Color·Typography·Alignment·Contrast·White Space)로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. Erik Kennedy Score 0-100 + 7 룰 scores + Top-3 Fix 헤드라인. 사용자가 \"erik kennedy 리뷰\", \"learnui design 평가\", \"7룰 UI 점검\", \"신규 페이지 sanity check\", \"/design-ui-erik-kennedy-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 Kennedy 7룰 기반 리뷰를 요청할 때 사용."
---

# design-ui-erik-kennedy-review

**Review Level**: L0 Surface — Erik Kennedy 7 핵심 룰 (단일 프레임 표면).

[learnui.design](https://www.learnui.design/) 의 "Learn UI Design" 코스에서 추출한 **7 핵심 룰**을 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다. 입문자도 이 7 룰만 마스터하면 80% UI 품질에 도달한다는 것이 Kennedy 의 핵심 메시지다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 7 룰을 얼마나 잘 지키고 있는가? 가장 빠르게 고칠 수 있는 3가지는 무엇인가?"

## 평가 항목 — 7 핵심 룰

| # | Rule | 한 줄 기준 |
|---|------|-----------|
| 1 | **Hierarchy** | 가장 중요한 요소가 contrast·size·color·spacing 으로 가장 돋보인다 |
| 2 | **Spacing** | 8px 그리드, related items 좁게 — unrelated 넓게 |
| 3 | **Color** | saturation·brightness 일관, 60-30-10 비율, ≤3 brand color |
| 4 | **Typography** | 16px+ body, 1.5 line-height, 단일 font family 권장 |
| 5 | **Alignment** | left·center·right 일관, optical alignment |
| 6 | **Contrast** | 텍스트 4.5:1 이상, hierarchy contrast |
| 7 | **White Space** | 답답함 없음, breathing room 확보 |

> **핵심 메시지**: 7 룰 마스터 = 80% UI 품질 도달 — "The Step-By-Step Guide to UI Design" (Erik Kennedy, learnui.design)

## When to Use

- 신규 페이지·화면의 빠른 sanity check 가 필요할 때 (Kennedy 7룰 = 빠른 진단)
- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "erik kennedy 리뷰", "learnui design 평가", "7룰 점검", "UI sanity check" 등을 요청할 때
- 입문 수준 7룰 기준으로 0-100 점수를 받고 싶을 때
- refactoring-ui 보다 가볍고 빠른 1차 진단이 필요할 때

## Do Not Use

- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 시각 폴리시 10 차원 심층 평가 → `design-ui-polish-review`
- Refactoring UI (Schoger) 전체 기준 평가 → `design-ui-refactoring-review`
- IxDF UI 5 항목 → `design-ui-ixdf-review`
- Laws of UX 시각·게슈탈트 → `design-ui-lawsofux-review`
- Nielsen Aesthetic 휴리스틱 → `design-ui-nielsen-review`
- 이커머스 UI → `design-ui-ecommerce-review`
- UX 행동·인지 평가 → `design-ux-*` 시리즈
- 라이브 사이트 audit → gstack `/design-review`

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동을 활성화하거나 Figma 데스크탑 앱의 Dev Mode MCP 를 설치한 뒤 다시 시도해주세요." |
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

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 로 프레임 구조 파악
   - nodeId 미지정 시 현재 선택 프레임 사용. 멀티 프레임 자동 감지
2. 각 frame 에 대해:
   - `mcp__claude_ai_Figma__get_design_context(fileKey, nodeId=frame.id)` 로 deep 트리 + 토큰 힌트 수집
   - `mcp__claude_ai_Figma__get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고 이미지 1장 확보

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별 → 멀티 프레임 자동 감지
   - 선택이 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id])` 로 deep 노드 트리 수집
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(node_id=frame_id)` 로 이미지 1장 확보
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 폰트/컬러/사이즈/스페이싱 팔레트 추출 (font, color, fontSize, fontWeight, padding, gap, lineHeight)

### Step 4 — Classifier (디자인 타입 판별)

수집된 프레임 1장을 보고 분류:

- **MARKETING/LANDING** — hero 섹션, 브랜드 강조, 컨버전 중심
- **APP UI** — 워크스페이스, 데이터 dense, 태스크 중심
- **ONBOARDING/FORM** — 가입·결제·설정 흐름의 단일 스텝
- **CONTENT/READER** — 본문 소비형 (블로그·뉴스·문서)
- **HYBRID** — 위 카테고리 혼재

분류 결과를 보고서 메타에 기록. Kennedy 7룰 관점 카테고리별 강조점:
- 마케팅: Hierarchy / Color / White Space 가중↑
- 앱 UI: Spacing / Alignment / Contrast 가중↑
- 폼: Alignment / Spacing / Typography 가중↑
- 콘텐츠: Typography / White Space / Hierarchy 가중↑

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 화면이 전달하는 시각적 인상: [한 문장]
- 시선이 가장 먼저 가는 3곳: [1], [2], [3]
- 가장 눈에 거슬리는 이슈 1개: [...]
- 7룰 위반 중 즉각 포착되는 것: [룰명 + 한 줄]
- 한 단어 요약: [단어]
```

이 섹션은 의견을 강하게 적는다. 진단가는 헤지하지 않는다.

### Step 6 — Inferred Design System (Phase 2)

수집된 노드 트리 + 속성에서 7룰 관련 항목 추출:

- **Fonts**: font family 목록 + 출현 빈도 + 단일 family 여부
- **Colors**: 전체 컬러 팔레트 + brand color 수 + saturation/brightness 분포 + 60-30-10 추정 비율
- **Type Scale**: fontSize 분포 + 16px 기준 body 통과 여부 + line-height 분포
- **Spacing**: padding/gap 값 분포 + 8px 그리드 일치율 + random 값 여부
- **Alignment**: 정렬 축 혼용 여부 (left·center·right)
- **Contrast Hints**: 텍스트 컬러와 배경 컬러 쌍 목록 (실측 대비율은 approximate)

### Step 7 — 7 룰 평가 (Phase 3)

각 룰마다 0-10 점수. 정적 검증 불가능한 항목은 `N/A` + 사유. 위반/개선점은 finding 1개로 작성.

**점수 기준:**
- 10 — exemplary, 교과서 수준
- 8-9 — solid, 사소한 polish 만
- 6-7 — 기능적이나 개선 여지
- 4-5 — 눈에 띄는 위반
- 0-3 — 룰을 명백히 어김

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding 당)
- warning: -1 ~ -2
- info: 점수 영향 X, 노트만

---

#### Rule 1. Hierarchy — 시각적 중요도 위계

**평가 기준:**
- 가장 중요한 요소(CTA, 헤딩)가 size·color·contrast·weight 로 가장 돋보이는가
- 1차/2차/3차 위계 단계가 명확한가 (squint test: 블러해도 위계 유지)
- 60-30-10 dominant/secondary/accent 분포
- 모든 요소가 동일 visual weight 이면 위계 없음

**Red flags:** 동일 크기 동일 색 나열, CTA 가 secondary 와 구별 안 됨, 헤딩-본문 사이즈 차 < 1.25x

**learnui.design 출처:** "Learn UI Design" Module 1 — Visual Hierarchy; "The Step-By-Step Guide to UI Design" Section 2

---

#### Rule 2. Spacing — 간격 시스템

**평가 기준:**
- 8px / 16px 그리드 기반 일관 스케이싱
- 관련 항목(label-input, icon-text)은 좁게, 무관한 섹션은 넓게 (근접성 법칙과 연동)
- 임의 픽셀값 없음 (13px, 17px, 23px 같은 random gap)
- 컴포넌트 내부 padding 충분
- 요소가 엣지에 붙지 않음

**Red flags:** random px 값, 엣지에 텍스트 붙음, 관련 항목과 무관 항목 간격 동일

**learnui.design 출처:** "Learn UI Design" Module 3 — Spacing & Layout; learnui.design blog "4 Rules for Intuitive UX"

---

#### Rule 3. Color — 컬러 시스템

**평가 기준:**
- brand color ≤ 3종
- saturation 과 brightness 가 일관 (palette 내 harmonious)
- 60-30-10 비율: dominant 60% / secondary 30% / accent 10%
- 의도 없는 rainbow palette 없음
- 뉴트럴 웜/쿨 일관

**Red flags:** ≥4 brand color, saturation 들쭉날쭉, 클래시 조합, accent 남용

**learnui.design 출처:** "Learn UI Design" Module 4 — Color; learnui.design blog "The HSB Color System"

---

#### Rule 4. Typography — 타이포그래피

**평가 기준:**
- body font ≥ 16px
- line-height ≥ 1.5 (본문), 헤딩 1.1-1.3
- font family 단일 또는 최대 2종 (display + body)
- type scale 비율 일관 (1.25 / 1.333 권장)
- weight ≥ 2종 의도적 사용 (regular + semibold/bold)

**Red flags:** body < 14px, font family ≥ 3, line-height < 1.3, 임의 fontSize 5종 이상

**learnui.design 출처:** "Learn UI Design" Module 2 — Typography; learnui.design blog "The Fastest Way to Improve Your UI Designs"

---

#### Rule 5. Alignment — 정렬

**평가 기준:**
- 정렬 축 일관 (left-aligned 또는 center — 혼용 최소화)
- optical alignment: 아이콘·이미지·텍스트 시각 중심 맞춤
- 그리드 기반 정렬 신호 (Auto-layout / Grid 사용 여부)
- 요소 간 misalign 없음

**Red flags:** left·center 혼용 무원칙, 아이콘-텍스트 baseline 불일치, 요소 1-2px 어긋남

**learnui.design 출처:** "Learn UI Design" Module 3 — Layout & Alignment; "The Step-By-Step Guide to UI Design" Section 3

---

#### Rule 6. Contrast — 대비

**평가 기준:**
- 텍스트 대 배경 대비율 ≥ 4.5:1 (WCAG AA, 본문)
- 큰 텍스트 (≥ 18px bold 또는 ≥ 24px regular) ≥ 3:1
- hierarchy contrast: 1차 요소가 2차 요소보다 눈에 띔
- 버튼·CTA 가 배경과 충분히 구별됨

**Red flags:** low contrast 텍스트, CTA 버튼이 배경에 묻힘, 아이콘 + 배경 구별 불가

**learnui.design 출처:** "Learn UI Design" Module 5 — Contrast & Color; learnui.design blog "The 60-30-10 Rule in UI Design"

---

#### Rule 7. White Space — 여백

**평가 기준:**
- 답답함 없음 — breathing room 충분
- 의도된 negative space (여백이 레이아웃의 일부)
- 컴포넌트 내부 padding 여유 있음
- 섹션 간 충분한 separation

**Red flags:** 모든 영역에 요소가 빽빽이 채워짐, 컴포넌트 내부 4px 미만 패딩, 섹션 분리 불명확

**learnui.design 출처:** "Learn UI Design" Module 3 — White Space; learnui.design blog "The Most Overlooked Factor in UI Design"

### Step 8 — Erik Kennedy Score 산출

**룰별 0-10 점수 → 종합 0-100:**
- 종합 점수 = 7개 룰 점수 합산 × (100/70) → 0-100 스케일
- N/A 항목 있을 시 적용 룰 수로 나눠 환산

**Grade 환산:**
- 90-100: **A** (Excellent — 7룰 거의 완벽)
- 75-89: **B** (Good — 소수 룰 polish 필요)
- 60-74: **C** (Acceptable — 개선 여지 있음)
- 40-59: **D** (Needs Work — 다수 룰 위반)
- 0-39: **F** (Critical — 룰 전반 재점검 필요)

**Kennedy Quote 연계:** 점수 60 이상이면 "80% UI 품질 도달 목전" 멘트 추가. 60 미만이면 "7룰 기초부터 다시" 권고.

### Step 9 — Top-3 Fix 선정

finding 중 high-impact 상위 3개를 선정:
1. severity=critical 우선
2. critical 부족 시 warning 으로 채움
3. 수정 난이도 Low 우선 (빠른 개선 효과)

각 Fix 카드:
- **현재 문제** (룰명 + evidence)
- **사용자 영향** (시각적으로 어떻게 나빠 보이는지)
- **제안 솔루션** (구체 수치·토큰·액션)
- **기대 점수 변화** (룰 N → N')
- **노력** (Low / Medium / High)

### Step 10 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-erik-kennedy-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 11 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 Erik Kennedy Score + Grade + critical/warning 개수 한 줄 요약
- 7룰 마스터 상태 한 줄 평가 ("80% 품질 도달" 여부)

### Step 12 — Refactoring UI 비교 노트 (선택)

finding 이 5건 이상이면 보고서 하단에 "Refactoring UI 와의 겹침 분석" 섹션 추가:
- Kennedy 7룰 ↔ Refactoring UI (Schoger) 겹치는 항목 매핑
- Kennedy 전용 진단 포인트 (겹치지 않는 부분) 강조
- 더 깊은 분석이 필요하면 `design-ui-refactoring-review` 병행 권장

## 보고서 구조 (한국어)

```markdown
# Erik Kennedy UI Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 디자인 타입: {MARKETING/LANDING | APP UI | ONBOARDING/FORM | CONTENT/READER | HYBRID}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: Erik Kennedy "Learn UI Design" 7 핵심 룰 (learnui.design)

## 헤드라인

- **Erik Kennedy Score: {0-100}/100**
- **Grade: {A ~ F}**
- 7룰 마스터 상태: {80% 품질 도달 / 기초 재점검 필요}
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 화면이 전달하는 시각적 인상: {...}
- 시선이 가장 먼저 가는 3곳: {1}, {2}, {3}
- 가장 눈에 거슬리는 이슈: {...}
- 7룰 위반 즉각 포착: {룰명 + 한 줄}
- 한 단어 요약: {...}

## Inferred Design System
- **Fonts** ({n}종): {목록 + 빈도 + 단일 family 여부}
- **Colors** ({n}종): {팔레트 + brand color 수 + 60-30-10 추정}
- **Type Scale**: {분포 + body ≥16px 여부 + line-height}
- **Spacing**: {분포 + 8px 그리드 일치율 + random 값 여부}
- **Alignment**: {정렬 축 혼용 여부}
- **Contrast Hints**: {텍스트-배경 쌍 + 예상 대비율}

## 7룰 점수표

| # | Rule | Score | critical | warning | info |
|---|------|-------|----------|---------|------|
| 1 | Hierarchy | -/10 | - | - | - |
| 2 | Spacing | -/10 | - | - | - |
| 3 | Color | -/10 | - | - | - |
| 4 | Typography | -/10 | - | - | - |
| 5 | Alignment | -/10 | - | - | - |
| 6 | Contrast | -/10 | - | - | - |
| 7 | White Space | -/10 | - | - | - |
| — | **종합** | **{합산}/70 → {환산}/100** | | | |

## Findings

### Rule 1. Hierarchy — score: {N}
- **severity**: {critical / warning / info}
- **rule**: Hierarchy
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **learnui-출처**: learnui.design "Learn UI Design" Module 1 — Visual Hierarchy

### Rule 2. Spacing — score: {N}
- **severity**: {critical / warning / info}
- **rule**: Spacing
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **learnui-출처**: learnui.design "Learn UI Design" Module 3 — Spacing & Layout

### Rule 3. Color — score: {N}
- **severity**: {critical / warning / info}
- **rule**: Color
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **learnui-출처**: learnui.design "Learn UI Design" Module 4 — Color; "The HSB Color System"

### Rule 4. Typography — score: {N}
- **severity**: {critical / warning / info}
- **rule**: Typography
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **learnui-출처**: learnui.design "Learn UI Design" Module 2 — Typography

### Rule 5. Alignment — score: {N}
- **severity**: {critical / warning / info}
- **rule**: Alignment
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **learnui-출처**: learnui.design "Learn UI Design" Module 3 — Layout & Alignment

### Rule 6. Contrast — score: {N}
- **severity**: {critical / warning / info}
- **rule**: Contrast
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **learnui-출처**: learnui.design "Learn UI Design" Module 5 — Contrast & Color

### Rule 7. White Space — score: {N}
- **severity**: {critical / warning / info}
- **rule**: White Space
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **learnui-출처**: learnui.design "Learn UI Design" Module 3 — White Space

{위반/개선점이 있는 룰만 나열. 위반 없으면 해당 룰 finding 생략}

## Top-3 Fix

### Fix 1 — {룰명} ({severity})
- **현재 문제**: {evidence}
- **사용자 영향**: {...}
- **제안 솔루션**: {...}
- **기대 점수 변화**: Rule {n} {현재} → {목표}
- **노력**: {Low / Medium / High}

### Fix 2 — {룰명} ({severity})
- **현재 문제**: {...}
- **사용자 영향**: {...}
- **제안 솔루션**: {...}
- **기대 점수 변화**: Rule {n} {현재} → {목표}
- **노력**: {Low / Medium / High}

### Fix 3 — {룰명} ({severity})
- **현재 문제**: {...}
- **사용자 영향**: {...}
- **제안 솔루션**: {...}
- **기대 점수 변화**: Rule {n} {현재} → {목표}
- **노력**: {Low / Medium / High}

## Refactoring UI 와의 비교 (finding ≥5건 시)

| Kennedy 7룰 | Refactoring UI (Schoger) 대응 항목 | 겹침 정도 |
|-------------|-----------------------------------|----------|
| Hierarchy | Visual Hierarchy, Using Color — not just for decoration | 높음 |
| Spacing | Spacing and Sizing — a linear scale won't work | 높음 |
| Color | Working with Color (HSB, saturation shift) | 중간 |
| Typography | Working with Typescale, font size, line-height | 높음 |
| Alignment | Layout — working with space | 중간 |
| Contrast | Accessible color (WCAG AA contrast) | 높음 |
| White Space | Hierarchy through spacing, not just size | 중간 |

**Kennedy 전용 진단 포인트 (Refactoring UI 에 없거나 약한 부분):**
- 7룰 체크리스트로 즉각 sanity check — 입문자 진입 장벽 낮음
- 60-30-10 컬러 비율 기준 명시
- optical alignment 명시적 점검
- "80% 품질 도달" 달성 여부를 단일 숫자로 확인

더 깊은 폴리시 분석: `design-ui-refactoring-review` 또는 `design-ui-polish-review` 병행 권장.

## N/A 항목 (정적 분석 한정)
- Contrast (Rule 6) 실측 불가: 트리에서 컬러 쌍 추출 후 approximate 계산. 정확한 4.5:1 검증은 라이브 환경 필요
- Motion / Micro-interaction: 정적 프레임에서 평가 불가 (상태 디자인 존재 여부만)

## 다음 단계 (권장 후속)
- Top-3 Fix 적용 후 재평가로 80% 품질 도달 확인
- `design-ui-refactoring-review` — Kennedy 7룰 통과 후 심층 폴리시
- `design-ui-polish-review` — 10 차원 시각 폴리시 전체 진단
- `annotate-design` — 본 리뷰 .md 를 Figma/Pencil 파일에 코멘트로 부착
```

## 인자

```
/design-ui-erik-kennedy-review <Figma URL | .pen path>
```

- 위치 인자 1개만 필수
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- 옵션 인자 없음 (간결 디폴트 우선)

## 예시

### 예시 1 — Figma URL (단일 프레임)
```
/design-ui-erik-kennedy-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → 분류 → First Impression → Design System 추출 → 7룰 평가 → `./design-reviews/design-ui-erik-kennedy-review-checkout-screen-20260518-1430.md` 생성

### 예시 2 — Pencil 멀티 프레임
```
/design-ui-erik-kennedy-review ~/Documents/myapp.pen
```
→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택된 2개 프레임 감지 → 각 프레임 평가 → 2개 파일 생성

### 예시 3 — MCP 미연결
```
/design-ui-erik-kennedy-review https://www.figma.com/design/abc123/App?node-id=1-1
```
→ ToolSearch 결과 0건 → "Figma MCP 가 연결되어 있지 않습니다." 안내 출력 후 종료

### 예시 4 — 신규 페이지 sanity check
```
/design-ui-erik-kennedy-review ~/Desktop/new-dashboard.pen
```
→ 7룰 빠른 진단 → Score 72/100 (Grade B) → Top-3 Fix: Typography body 12→16px, Spacing random → 8px grid, Contrast CTA 버튼 배경 대비 향상 → 80% 품질 도달 가이드

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 룰명은 영어 원어 유지 (Hierarchy, Spacing, Color, Typography, Alignment, Contrast, White Space)
- finding 의 evidence/fix 는 구체적 노드명·수치·액션 명시
- finding 헤더 포맷: `### Rule {n}. {name} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / rule / evidence / fix / learnui-출처 5 필드 동일 순서 유지 (annotate-design 호환)
- 보고서는 한 프레임당 한 파일
- 출력 파일 경로: `./design-reviews/design-ui-erik-kennedy-review-{frame-slug}-{YYYYMMDD-HHmm}.md`

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 finding 포맷을 맞춘다.

워크플로:
```
/design-ui-erik-kennedy-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Refactoring UI 와의 차이

| 관점 | Kennedy 7룰 (본 스킬) | Refactoring UI (Schoger) |
|------|----------------------|--------------------------|
| 대상 | 입문~중급 — 빠른 sanity check | 중급~고급 — 심층 폴리시 |
| 룰 수 | 7룰 압축 | 다수 챕터 (타이포·컬러·레이아웃·컴포넌트 등) |
| 출력 | Score 0-100 + Top-3 Fix | 챕터별 심층 가이드 |
| 속도 | 빠름 (7룰 체크) | 느림 (전체 시스템 분석) |
| 진단 키워드 | "80% 품질 도달" 여부 | "디자인 시스템 성숙도" |
| 겹침 | Hierarchy·Spacing·Typography·Contrast 80% 공통 | — |
| Kennedy 전용 | 60-30-10 비율 명시, optical alignment, 단일 숫자 Grade | — |

**권장 조합**: Kennedy 7룰 → 빠른 1차 진단 → 통과 후 `design-ui-refactoring-review` 로 심층 분석.

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 라이브 사이트 audit / 인터랙션 / perf — gstack `/design-review` 책임
- UX 행동·인지 평가 — `design-ux-*` 시리즈 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인 (별도 references 디렉터리 없음)
- 방법론 출처: Erik Kennedy — learnui.design "Learn UI Design" 코스
- 7룰 원 출처: learnui.design "The Step-By-Step Guide to UI Design"; Erik Kennedy Medium articles
- 60-30-10 컬러 비율: learnui.design blog "The 60-30-10 Rule in UI Design"
- HSB 컬러 시스템: learnui.design blog "The HSB Color System"
- 타이포그래피: learnui.design blog "The Fastest Way to Improve Your UI Designs"
- WCAG AA Contrast: https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum
- 대응 심층 스킬: `design-ui-refactoring-review` (Refactoring UI 전체 기준), `design-ui-polish-review` (10 차원 폴리시)
