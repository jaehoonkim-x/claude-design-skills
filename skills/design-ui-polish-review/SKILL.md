---
name: design-ui-polish-review
description: Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 10개 시각 디자인 차원(Visual Hierarchy·Typography·Color Palette·Spacing & White Space·Visual Consistency·Imagery & Graphics·Layout & Grid·Component Design·Branding & Personality·Modern Standards)으로 깊이 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. 종합 0-100 점수 + Grade A-F + Design Quality Level L1-L5 헤드라인. 사용자가 "UI 시각 폴리시 10 차원 리뷰", "디자인 완성도 점수", "시각 디자인 평가", "/design-ui-polish-review" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 시각 폴리시/완성도 리뷰를 요청할 때 사용.
---

# design-ui-polish-review

시각 디자인 폴리시·완성도 관점으로 정적 디자인 프레임을 평가한다. 라이브 사이트가 아닌 **디자인 파일**(`.pen`, Figma) 대상. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "industry-leading product 와 비교해 시각 폴리시 어디까지 왔나?"
- 10개 시각 차원 정량 점수 (0-10)
- 종합 0-100 + A-F 등급
- Design Quality Level (L1 Bootstrap Template → L5 Award-Worthy)
- Refactoring UI / Material / HIG / Laws of UX 기준 best practice 대조

## 평가 항목 (10)

1. **Visual Hierarchy** — 명확한 1차/2차/3차 위계, size·color·position 으로 attention 가이드, 1차 CTA dominate, F/Z-pattern 의도, squint test, 60-30-10 비율
2. **Typography** — font family ≤ 3, type scale 비율 (1.25/1.333), 본문 ≥ 16px, line-height 1.5-1.6, line length 50-75자, weight ≥ 2종, 블랙리스트 폰트 없음, 곡선 따옴표·말줄임표
3. **Color Palette** — primary/secondary/accent/neutral 정의, 9-shade 팔레트, WCAG AA contrast, 의도적 컬러 사용, 뉴트럴 웜/쿨 일관, color-blind 접근성, pure black/white 회피
4. **Spacing & White Space** — 일관 스페이싱 스케일 (4px/8px base), 임의값 없음, 의도된 negative space, 컴포넌트 padding 충분, breathing room, 엣지 터칭 없음
5. **Visual Consistency** — 버튼·카드·아이콘 스타일 통일, border-radius 일관/계층적, shadow elevation 시스템, 폼 스타일 표준화, 동일 액션에 동일 비주얼
6. **Imagery & Graphics** — 고해상도·픽셀화 없음, 스타일 일관 (사진/일러스트 톤 통일), 콘텐츠 관련성, 적절한 aspect ratio, 아이콘 명확·인식 가능, 제너릭 stock photo 회피
7. **Layout & Grid** — 명확한 그리드 시스템 (12-column 등), 정렬 일관, 균형 잡힌 컴포지션, 반응형 breakpoint, 시각 흐름 자연스러움, 최대 콘텐츠 너비 설정
8. **Component Design** — 버튼 affordance, 폼 인풋 명확, 카드 well-defined, 상태 표현 (hover/focus/active/disabled), 인터랙티브 요소 식별, 컴포넌트 variant 일관, 터치 타겟 ≥ 44px
9. **Branding & Personality** — 브랜드 컬러 prominent, 타이포그래피가 브랜드 보이스 반영, 개성 명확 (playful/serious/premium), 차별화, 톤 일관, 기억에 남는 디자인 요소
10. **Modern Design Standards** — 컨템포러리 (2026 기준), subtle shadow, rounded corners 6-8px, soft color palette, 큰 typography, 충분한 white space, platform 컨벤션, deprecated 패턴 회피

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "UI 시각 폴리시 10 차원 리뷰", "디자인 완성도 점수", "시각 디자인 평가" 등을 요청할 때
- 출시 전 시각 폴리시 audit 또는 디자인 시스템 일관성·완성도를 0-100 점수로 진단하고 싶을 때
- 경쟁사 대비 시각 수준 정량 비교가 필요할 때

## Do Not Use

- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design` 스킬
- AI Slop / 디자이너 비평 관점 평가 → `design-ui-critic-review`
- Laws of UX 시각·게슈탈트 법칙 기준 평가 → `design-ui-lawsofux-review`
- Nielsen Aesthetic 휴리스틱 → `design-ui-nielsen-review`
- IxDF UI 5 항목 (Desirable·Visual Rep·Physical Space·Time·Engagement) → `design-ui-ixdf-review`
- 이커머스 UI (Product Card·PDP·PLP) → `design-ui-ecommerce-review`
- UX 행동·인지 평가 → `design-ux-*` 시리즈
- 라이브 웹사이트 audit (Core Web Vitals, 인터랙션, perf) → gstack `/design-review`
- 인터랙션 흐름/애니메이션/성능 측정 — 단일 프레임 정적 분석 한정

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동을 활성화하거나 Figma 데스크탑 앱의 Dev Mode MCP 를 설치한 뒤 다시 시도해주세요." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: 첫 단계에서 ToolSearch 로 prefix 의 도구를 조회. 결과가 비어 있으면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + 타입 라우팅

사용자 인자에서 입력 타입을 자동 감지:

- `figma.com/design/:fileKey/...?node-id=:nodeId` 또는 `figma.com/board/...` → **Figma 경로**
- `*.pen` 로컬 경로 → **Pencil 경로**
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

Figma URL 파싱:
- fileKey = path 의 `/design/` 다음 세그먼트
- nodeId = `?node-id=` 쿼리. `-` → `:` 로 변환

### Step 2 — MCP 사전 체크

위 Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 종료.

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
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 폰트/컬러/사이즈/스페이싱 팔레트 추출 (font, color, fontSize, fontWeight, cornerRadius, padding)

### Step 4 — Classifier (디자인 타입 판별)

수집된 프레임 1장을 보고 분류:

- **MARKETING/LANDING** — hero 섹션, 브랜드 강조, 컨버전 중심
- **APP UI** — 워크스페이스, 데이터 dense, 태스크 중심
- **HYBRID** — 마케팅 + 앱 섹션 혼재

카테고리별 finding 강조점 다름:
- 마케팅: 위계·이미지·브랜딩·모더니티 우선
- 앱 UI: 타이포·스페이싱·컴포넌트·일관성 우선

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 본 직후, 분석 시작 전에 첫 반응 작성:

```
- 즉각 인상: [Professional / Dated / Playful / Generic / Premium / Trustworthy / Cheap 등]
- 가장 두드러진 시각 요소 3개: [1], [2], [3]
- 가장 거슬리는 이슈 1개: [...]
- Trust Level: High / Medium / Low
- 첫인상 점수: 1-10
```

### Step 6 — Inferred Design System (Phase 2)

수집된 노드 트리 + 속성에서 다음 추출 (보고서 메타로 기록):

- **Fonts**: font family 목록 + 출현 빈도. 3종 초과 시 flag
- **Colors**: 전체 컬러 팔레트(text, fill, stroke). non-gray 12종 초과 시 flag. 단일 색상 shade 수 (1 shade = 평면적)
- **Type Scale**: fontSize 분포 + 비율 추정 (1.125 / 1.25 / 1.333 / 1.5)
- **Spacing Scale**: padding/gap 값 분포. 4px / 8px 그리드 일치율
- **Radius**: cornerRadius 분포. 균일/계층 여부
- **Shadow/Elevation**: dropShadow 사용 + 단계 수

### Step 7 — 10-Dimension Evaluation (Phase 3)

각 차원마다 0-10 점수 + finding 작성. 각 finding 마다 **severity** (critical / warning / info), **evidence** (노드 경로/이름/수치), **fix** (구체 액션) 기록.

정적 디자인에 적용 불가한 항목은 N/A 처리.

#### 1. Visual Hierarchy (10%)
- 명확한 1차/2차/3차 위계
- size, color, position 으로 attention 가이드
- 1차 CTA 가 시각적으로 dominate
- F-pattern / Z-pattern 의도
- Squint test (블러) 시 위계 유지
- 60-30-10 dominant/secondary/accent 비율

**Red flags**: 모든 요소 동일 visual weight, CTA 가 secondary 와 구별 안 됨, 헤딩과 본문 사이즈 차 < 1.25x

#### 2. Typography (10%)
- font family ≤ 3
- type scale 비율 따름 (1.25 / 1.333)
- 본문 ≥ 16px, 캡션 ≥ 12px
- line-height: 본문 1.5-1.6, 헤딩 1.15-1.25
- line length 50-75자
- font weight ≥ 2종 의도적 사용
- 블랙리스트 폰트 없음 (Comic Sans, Papyrus, Impact 디스플레이 용도)
- 곡선 따옴표·말줄임표 사용

**Red flags**: 본문 < 14px, 4개 이상 font family, line-height < 1.3, 5종 이상 임의 fontSize

#### 3. Color Palette (10%)
- primary/secondary/accent/neutral 정의됨
- 각 컬러 9-shade 팔레트 (50-900) 또는 충분한 shade
- WCAG AA contrast (본문 4.5:1, 큰 텍스트 3:1)
- 의도적 컬러 사용 (decorative ≠ semantic)
- 뉴트럴 웜/쿨 일관
- color-blind 접근성 (red/green only 금지)
- pure black (#000) on pure white (#FFF) 회피

**Red flags**: rainbow palette, 단일 shade, low contrast, 클래시 조합

#### 4. Spacing & White Space (10%)
- 일관 스페이싱 스케일 (4px / 8px base)
- 임의값 없음 (13px, 17px, 23px 같은 random)
- 생성한 여백 (의도된 negative space)
- 컴포넌트 padding 충분
- 요소 간 breathing room
- 엣지 터칭 없음

**Red flags**: random 픽셀 값, 엣지에 텍스트 붙음, 컴포넌트 내부 4px 미만 패딩

#### 5. Visual Consistency (10%)
- 버튼 스타일 통일
- 카드 디자인 통일
- 아이콘 스타일 통일 (outline vs filled 혼용 금지)
- border-radius 일관 또는 계층적
- shadow elevation 시스템
- 폼 스타일 표준화
- 동일 액션에 동일 비주얼

**Red flags**: 같은 액션에 다른 버튼 스타일, 아이콘 outline/filled 혼용, radius 임의 변동

#### 6. Imagery & Graphics (10%)
- 고해상도, 픽셀화 없음
- 스타일 일관 (사진 / 일러스트 톤 통일)
- 콘텐츠와 관련성
- 적절한 aspect ratio
- 아이콘 명확·인식 가능
- 장식이 아닌 콘텐츠 보조
- 제너릭 stock photo 회피

**Red flags**: 저해상도, 일러스트 스타일 혼용, 제너릭 stock, 의미 없는 장식 그래픽

#### 7. Layout & Grid (10%)
- 명확한 그리드 시스템 (12-column 등)
- 정렬 일관
- 균형 잡힌 컴포지션
- 반응형 breakpoint
- 시각 흐름 자연스러움
- 페이지 템플릿 일관
- 최대 콘텐츠 너비 설정

**Red flags**: misalign 요소, 그리드 부재, 컴포지션 unbalanced, full-bleed 본문 텍스트

#### 8. Component Design (10%)
- 버튼 affordance (클릭 가능 보임)
- 폼 인풋 명확
- 카드 well-defined
- 상태 표현 (hover/focus/active/disabled — variant 로 표현되어 있으면 평가)
- 인터랙티브 요소 즉시 식별
- 컴포넌트 variant 일관
- 터치 타겟 ≥ 44px (모바일)

**Red flags**: flat 버튼 affordance 부족, 상태 누락, 인풋 경계 불명확

#### 9. Branding & Personality (10%)
- 브랜드 컬러 prominent
- 타이포그래피가 브랜드 보이스 반영
- 개성 명확 (playful / serious / premium 등)
- 차별화 (제너릭 아님)
- 톤 일관
- 기억에 남는 디자인 요소
- 경쟁사와 구별

**Red flags**: Bootstrap 룩, 개성 부재, 브랜드 적용 inconsistent, cookie-cutter SaaS

#### 10. Modern Design Standards (10%)
- 컨템포러리 (2026 기준)
- subtle shadow (flat 아님, harsh 아님)
- rounded corners 6-8px
- soft color palette
- 큰 typography
- 충분한 white space
- platform 컨벤션 준수
- deprecated 패턴 회피 (carousel, splash, harsh gradient)

**Red flags**: Web 2.0 gloss, bevel, extreme flat, 작은 텍스트, 캐러셀, 거대 그라데이션 stripe

#### N/A (정적 분석 한정)
- Motion & Animation
- Performance (LCP, CLS)
- 실시간 인터랙션 응답성

### Step 8 — Scoring

**차원별 0-10**:
- 9-10: Exceptional, industry-leading
- 7-8: Strong, professional
- 5-6: Adequate, room for improvement
- 3-4: Below par, needs attention
- 0-2: Poor, requires major redesign

**Grade 계산:**
- 차원별 점수 시작 = 10
- critical finding 1개당 -3
- warning 1개당 -1.5
- info 1개당 -0.5
- 최저 0

**종합 점수 = 10개 차원 평균 × 10 (0-100 스케일)**

**Grade:**
- 90-100: A+ (Exceptional)
- 80-89: A (Excellent)
- 70-79: B (Good)
- 60-69: C (Acceptable)
- 50-59: D (Needs Work)
- 0-49: F (Poor)

**Design Quality Level:**
- L1 Bootstrap Template (40-50): 제너릭, off-the-shelf
- L2 Customized Framework (60-70): 일부 브랜드 적용, 불일치 다수
- L3 Professional Design (70-80): 견고한 디자인 시스템
- L4 Design Excellence (80-90): exceptional craft
- L5 Award-Worthy (90-100): 트렌드 세팅

### Step 9 — Top-3 Quick Wins

30분~4시간 내 수정 가능한 high-impact 3개 선정:
1. critical 우선
2. critical 부족하면 warning 으로 채움
3. 1차 CTA / 진입 직후 마주치는 요소 / 위반 항목 수 순

### Step 10 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-polish-review-{frame-slug}-{YYYYMMDD-HHmm}.md` (cwd 기준. 디렉터리 없으면 생성)
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)

### Step 11 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 종합 점수 + Grade + Level + critical/warning 개수 한 줄 요약

## 보고서 구조 (한국어)

```markdown
# UI Design Polish 리뷰: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 디자인 타입: {MARKETING/LANDING | APP UI | HYBRID}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}

## 헤드라인 점수
- **종합 점수: {0-100}/100**
- **Grade: {A+ ~ F}**
- **Design Quality Level: {L1-L5} ({label})**
- critical: {n}건 / warning: {n}건 / info: {n}건

## First Impression
- 즉각 인상: {Professional / Dated / ...}
- 가장 두드러진 요소 3개: {1}, {2}, {3}
- 가장 거슬리는 이슈: {...}
- Trust Level: {High/Medium/Low}
- 첫인상 점수: {1-10}

## Inferred Design System
- **Fonts** ({n}종): {목록 + 사용 빈도}
- **Colors** (non-gray {n}종): {팔레트 + 웜/쿨/혼합 + shade 수}
- **Type Scale**: {fontSize 분포, 비율}
- **Spacing Scale**: {분포, 4px/8px 일치율}
- **Radius**: {분포, 계층 여부}
- **Shadow/Elevation**: {단계 수}

## 차원별 점수표

| # | Dimension | Score | critical | warning | info |
|---|-----------|-------|----------|---------|------|
| 1 | Visual Hierarchy | 7/10 | 0 | 1 | 1 |
| 2 | Typography | 4/10 | 1 | 2 | 0 |
| 3 | Color Palette | 8/10 | 0 | 1 | 0 |
| 4 | Spacing & White Space | 6/10 | 0 | 2 | 1 |
| 5 | Visual Consistency | 5/10 | 1 | 1 | 0 |
| 6 | Imagery & Graphics | N/A | - | - | - |
| 7 | Layout & Grid | 7/10 | 0 | 1 | 0 |
| 8 | Component Design | 6/10 | 0 | 2 | 0 |
| 9 | Branding & Personality | 5/10 | 1 | 0 | 0 |
| 10 | Modern Standards | 7/10 | 0 | 1 | 0 |

## Findings

### Visual Hierarchy — score: {N}
- **severity**: {critical / warning / info}
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **참고**: {Refactoring UI / HIG / Material 등 출처}

### Typography — score: {N}
- **severity**: critical
- **evidence**: `Body > Paragraph` (fontSize 12px, 본문 전반)
- **fix**: 본문 fontSize 12 → 16px. line-height 1.5 적용. 가독성 + 프로페셔널리즘 즉시 향상
- **참고**: Refactoring UI ch.4 — Body 최소 16px 기준

### Visual Consistency — score: {N}
- **severity**: critical
- **evidence**: `Primary CTA` (`border-radius: 4px`) vs `Card` (`border-radius: 12px`) vs `Input` (`border-radius: 8px`)
- **fix**: radius 스케일 정립 (sm 4 / md 8 / lg 12). 동일 elevation 컴포넌트는 동일 radius
- **참고**: 디자인 토큰 도입

{... 위반/개선점이 있는 finding 만 ...}

## Top-3 Quick Wins

1. **Typography (critical)** — 본문 12px → 16px 글로벌 적용. 즉시 폴리시 상승.
2. **Visual Consistency (critical)** — border-radius 스케일 (sm 4 / md 8 / lg 12) 도입.
3. **Branding & Personality (critical)** — 브랜드 컬러 prominent 적용 + 의도된 typeface 교체.

## Phase별 개선 로드맵

### Phase 1: Critical Fixes (1주, ~20h)
- {위 Top-3 + 추가 critical}

### Phase 2: Design System Foundation (2-3주, ~80h)
- 디자인 토큰 (color/spacing/type scale/shadow/radius)
- 컴포넌트 라이브러리
- 가이드라인 문서화

### Phase 3: Visual Enhancement (1-2개월)
- 브랜드 refresh
- 커스텀 일러스트
- 마이크로 인터랙션

## N/A 항목 (정적 분석 한정)
- Motion & Animation: 인터랙션 흐름 없음
- Performance: 라이브 측정 필요
- Interaction States: variant 부재 (있으면 Component Design 에 포함)
```

## 인자

```
/design-ui-polish-review <Figma URL | .pen path>
```

- 위치 인자 1개만 필수. 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- 옵션 인자 없음 (간결 디폴트 우선)

## 예시

### 예시 1 — Figma URL (단일 프레임)
```
/design-ui-polish-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → 분류 → First Impression → Design System 추출 → 10 차원 평가 → `./design-reviews/design-ui-polish-review-checkout-screen-20260514-1130.md` 생성

### 예시 2 — Pencil 멀티 프레임
```
/design-ui-polish-review ~/Documents/myapp.pen
```
→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택된 3개 프레임 감지 → 각 프레임 평가 → 3개 파일 생성

### 예시 3 — MCP 미연결
```
/design-ui-polish-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → 안내 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 차원명은 영어 원어 유지 (Typography, Visual Hierarchy 등)
- finding 의 evidence/fix 는 구체적 노드명·수치·액션 명시
- 보고서는 한 프레임당 한 파일
- finding 헤더 포맷 `### {항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / evidence / fix / 참고 필드 동일 (annotate-design 호환)
- 출력 파일 경로: `./design-reviews/design-ui-polish-review-{frame-slug}-{YYYYMMDD-HHmm}.md`

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커 + After mockup 을 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-polish-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## 다른 디자인 리뷰 스킬과의 차이

| 스킬 | 관점 | 핵심 출력 |
|------|------|----------|
| `design-ui-polish-review` (본 스킬) | 10개 시각 차원 정량 폴리시 평가 | 0-100 + Grade A-F + L1-L5 Level |
| `design-ui-critic-review` | 디자이너 비평·AI Slop 색출 | Design Grade A-F + AI Slop Grade A-F |
| `design-ui-lawsofux-review` | Laws of UX 시각·게슈탈트 법칙 7개 | 법칙별 0-10 점수표 |
| `design-ui-nielsen-review` | Nielsen Aesthetic and Minimalist Design | 1 휴리스틱 심층 평가 |
| `design-ui-ixdf-review` | IxDF UI 5 항목 (Desirable·Visual Rep·Physical Space·Time·Engagement) | 항목별 평가 |
| `design-ui-ecommerce-review` | Baymard 이커머스 UI (Product Card·PDP·PLP) | 3 카테고리 평가 |
| `design-ux-*` 시리즈 | 행동·인지·사용성 관점 | UX 카테고리별 평가 |

본 스킬은 **폴리시·완성도·디자인 시스템 성숙도** 정량 진단에 특화. AI Slop / UX 법칙 / 사용성 휴리스틱은 별도 스킬 사용.

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 라이브 사이트 audit / 인터랙션 / perf — gstack `/design-review` 책임
- AI Slop 색출 — `design-ui-critic-review` 책임
- UX 법칙 기반 평가 — `design-ux-lawsofux-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰만
- 코드 생성 — 디자인 파일만

## 참고 자료

- 10개 차원 출처: ui-design-polish-review skill (visual design polish framework)
- 평가 철학: Refactoring UI (Adam Wathan & Steve Schoger), Material Design Guidelines, Apple HIG, Laws of UX (Jon Yablonski)
- Design Quality Levels: Refactoring UI 의 "Bootstrap → Professional → Award-Worthy" 진화 모델
