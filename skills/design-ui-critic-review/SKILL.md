---
name: design-ui-critic-review
description: Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 디자이너 비평 관점(Visual Hierarchy & Composition·Typography·Color & Contrast·Spacing & Layout·Interaction States·Content & Microcopy·AI Slop)으로 깊이 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. Design Score A-F + AI Slop Score A-F 듀얼 헤드라인. 사용자가 "디자이너 비평 + AI Slop 리뷰", "디자인 critic", "AI slop 검사", "디자인 폴리시 검토", "/design-ui-critic-review" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 디자이너 눈으로 정적 디자인 리뷰를 요청할 때 사용.
---

# design-ui-critic-review

디자이너 비평 관점으로 정적 디자인 프레임을 평가한다. 라이브 사이트가 아닌 **디자인 파일**(`.pen`, Figma) 대상. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "respected studio 디자이너가 이거 ship 할까?"
- 의도성·폴리시·일관성
- AI Slop 색출 (보라 그라데이션, 3-column feature grid, 컬러 원 아이콘 등)
- 시각 위계가 의도한 메시지를 전달하는가
- Krug 의 사용자 행동 원칙 (스캔 가능성, 자명함)

## 평가 항목 (7 카테고리, 서술형)

1. **Visual Hierarchy & Composition** (가중치 20%) — focal point, 시선 흐름, 시각 노이즈, 정보 밀도, z-index, 3초 목적 전달, squint test, 의도된 여백
2. **Typography** (가중치 20%) — font family ≤ 3, 스케일 비율, line-height, measure, 헤딩 계층, 굵기 대비, 블랙리스트 폰트, generic flag, 곡선 따옴표, 말줄임표, 본문 ≥ 16px, letter-spacing, system-ui PRIMARY
3. **Color & Contrast** (가중치 15%) — 팔레트 coherent, WCAG AA contrast, semantic colors, color-only encoding, 다크모드, 색약 접근성, 뉴트럴 웜/쿨 일관
4. **Spacing & Layout** (가중치 20%) — 그리드 일관, 스페이싱 스케일 (4px/8px), 정렬, 리듬, border-radius 계층, 중첩 radius, 최대 콘텐츠 너비
5. **Interaction States** (가중치 5%) — hover/focus/active variant 존재 시 평가, 비활성 상태, 로딩/빈/에러 상태, 터치 타겟 ≥ 44px
6. **Content & Microcopy** (가중치 10%) — 빈 상태 디자인, 에러 메시지 구체성, 버튼 라벨 구체성, placeholder/lorem ipsum 제거, 잘림 처리, 능동태, Happy talk 색출, Instructions 색출
7. **AI Slop** (가중치 10%) — 보라/인디고 그라데이션, 3-column 컬러 원 아이콘 그리드, 장식 blob, 이모지 디자인 요소, generic hero 카피, cookie-cutter 섹션 리듬, system-ui PRIMARY, 카드 컬러 좌측 보더, 전체 center 정렬, bubbly border-radius

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "디자인 비평", "AI slop 검사", "디자이너 눈으로 봐줘", "디자인 폴리시 검토" 등을 요청할 때
- 출시 전 디자인 audit 또는 마케팅/랜딩/앱 UI 의 완성도를 A-F 점수로 진단하고 싶을 때
- AI 도구로 생성한 디자인의 슬롭 패턴을 찾아내고 싶을 때

## Do Not Use

- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design` 스킬
- 10개 시각 차원 정량 폴리시 평가 (0-100 점수) → `design-ui-polish-review`
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
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 폰트/컬러 팔레트 추출 (font, color, fontSize, fontWeight)

### Step 4 — Classifier (디자인 타입 판별)

수집된 프레임 1장을 보고 분류:

- **MARKETING/LANDING** — hero 섹션, 브랜드 강조, 컨버전 중심 (CTA 큰 버튼, feature 그리드, testimonial)
- **APP UI** — 워크스페이스, 데이터 dense, 태스크 중심 (대시보드, 어드민, 설정, 폼)
- **HYBRID** — 마케팅 + 앱 섹션 혼재

분류 결과를 보고서 메타에 기록. 카테고리 가중치는 동일하나 finding 강조점 다름:
- 마케팅: AI Slop, 콘텐츠/마이크로카피, 시각 위계 우선
- 앱 UI: 정보 밀도, 인터랙션 상태 가시성, 타이포 가독성 우선

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 화면이 전달하는 것: [한 문장]
- 내 시선이 가장 먼저 가는 3개: [1], [2], [3]
- 한 단어로 요약: [단어]
- 인상 메모: [무엇이 두드러지는가 — 긍정/부정 구체적으로]
```

이 섹션은 의견을 강하게 적는다. 디자이너는 헤지하지 않는다.

### Step 6 — Inferred Design System (Phase 2)

수집된 노드 트리 + 속성에서 다음 추출:

- **Fonts**: 사용된 font family 목록 + 출현 빈도. 3종 초과 시 flag
- **Colors**: 전체 컬러 팔레트(text, fill, stroke). non-gray 컬러 12종 초과 시 flag. 웜/쿨/혼합 분류
- **Heading scale**: 텍스트 노드의 fontSize 분포. 스케일 비율 추정 (1.25 major third / 1.333 perfect fourth)
- **Spacing patterns**: 자주 등장하는 padding/gap 값. 4px / 8px 스케일 벗어난 값 flag
- **Border radius**: cornerRadius 값 분포. 단일 값 전체 적용 시 "uniform bubbly radius" 의심

### Step 7 — Design Audit Checklist (Phase 3)

각 프레임마다 아래 카테고리를 적용. 각 finding 마다 **severity** (critical / warning / info), **evidence** (노드 경로/이름/수치), **fix** (구체 액션) 기록.

정적 디자인에 적용 불가한 항목은 N/A 처리.

#### 1. Visual Hierarchy & Composition (가중치 20%)
- 명확한 focal point + 1차 CTA 한 개?
- 시선이 자연스럽게 흐르는가? (좌상 → 우하 또는 의도된 흐름)
- 시각 노이즈 — 경쟁하는 요소들이 attention 분산?
- 정보 밀도가 콘텐츠 타입에 맞는가?
- z-index 명확 — 예상치 못한 겹침?
- 첫 화면(혹은 hero)에서 목적 3초 내 전달?
- Squint test (블러 시) 위계 유지?
- 여백이 의도적 (남은 공간이 아닌 디자인된 공간)?

#### 2. Typography (가중치 20%)
- 폰트 패밀리 ≤ 3 (초과 시 flag)
- 스케일이 비율 따름 (1.25 / 1.333)
- line-height: 본문 1.5x, 헤딩 1.15-1.25x
- 본문 measure 45-75자/행 (66 이상적)
- 헤딩 계층 — h1→h3 스킵 없음
- 굵기 대비 ≥ 2종 사용
- 블랙리스트 폰트 없음 (Papyrus, Comic Sans, Lobster, Impact, Jokerman)
- 메인 폰트가 Inter/Roboto/Open Sans/Poppins 인 경우 → "generic" flag (info)
- 곡선 따옴표 사용 (`"..."` 아닌 `"..."`)
- 말줄임표 `…` 사용 (`...` 아님)
- 본문 ≥ 16px, 캡션 ≥ 12px
- 소문자에 letter-spacing 없음
- system-ui / -apple-system 가 PRIMARY 디스플레이 폰트 → critical (AI slop 신호)

#### 3. Color & Contrast (가중치 15%)
- 팔레트 coherent (non-gray ≤ 12종)
- 본문 텍스트 contrast 4.5:1, 큰 텍스트 3:1, UI 컴포넌트 3:1 (WCAG AA)
- semantic colors 일관 (success=green, error=red, warning=amber)
- color-only encoding 없음 (라벨/아이콘/패턴 동반)
- 다크모드 (있다면): off-white 텍스트(~#E0E0E0), pure white 금지
- 다크모드: primary accent 10-20% 채도 낮춤
- red/green only 조합 없음 (색약 8%)
- 뉴트럴 팔레트 웜/쿨 일관 (혼합 X)

#### 4. Spacing & Layout (가중치 20%)
- 그리드 일관 (모든 프레임에서 동일 그리드)
- 스페이싱 스케일 (4px 또는 8px base) — 임의값 flag
- 정렬 일관 — 그리드 벗어난 요소 없음
- 리듬: 관련 항목 가까이, 다른 섹션 멀리
- border-radius 계층 (모든 요소 동일 radius 금지)
- 중첩 radius: 안쪽 = 바깥 - gap
- 최대 콘텐츠 너비 설정 (full-bleed 본문 텍스트 금지)

#### 5. Interaction States (가중치 5% — 가시 상태만)
- hover/focus/active 상태가 별도 프레임 또는 variant 로 표현되어 있는가? (있으면 평가, 없으면 N/A)
- 비활성 상태 표현 (opacity / cursor 표시)
- 로딩 / 빈 상태 / 에러 상태 디자인 존재?
- 터치 타겟 ≥ 44px (모바일 프레임이면 critical 기준)

#### 6. Content & Microcopy (가중치 10%)
- 빈 상태가 따뜻하게 디자인 (메시지 + 액션 + 일러스트)
- 에러 메시지 구체적 (무엇이 / 왜 / 다음에 무엇)
- 버튼 라벨 구체적 ("Save API Key" > "Continue" / "Submit")
- placeholder / lorem ipsum 가 프로덕션 텍스트로 남아 있지 않음
- 잘림 처리 표현 (말줄임 / 줄바꿈)
- 능동태 ("Install the CLI" > "The CLI will be installed")
- **Happy talk 색출**: "Welcome to...", "Unlock the power of...", "Your all-in-one solution for..." → critical
- **Instructions 색출**: 한 문장 초과하는 설명 문구 → warning + 설명 필요하게 만든 인터랙션도 함께 flag

#### 7. AI Slop (가중치 10%) — 즉시 fail 가능

발견 시 critical. 한 항목이라도 ≥ 2개 동시 발견되면 AI Slop Score = D 이하.

- 보라/바이올렛/인디고 그라데이션 배경 또는 blue→purple 스킴
- **3-column feature 그리드**: 컬러 원 안 아이콘 + 굵은 제목 + 2줄 설명, 3회 대칭 반복 (가장 인식 쉬운 AI 레이아웃)
- 섹션 장식으로 컬러 원 안 아이콘 (SaaS starter 룩)
- 전체 center 정렬 (모든 헤딩/설명/카드 가운데)
- 모든 요소에 동일한 큰 bubbly border-radius
- 장식 blob / 떠다니는 원 / 물결 SVG 디바이더
- 디자인 요소로 이모지 (헤딩에 로켓, 불릿으로 이모지)
- 카드에 컬러 좌측 보더 (`border-left: 3px solid <accent>`)
- generic hero 카피 ("Welcome to [X]", "Unlock the power of...", "Your all-in-one solution for...")
- cookie-cutter 섹션 리듬 (hero → 3 features → testimonials → pricing → CTA, 모두 같은 높이)
- system-ui / -apple-system 가 PRIMARY 디스플레이/본문 폰트 (타이포 포기 신호)

#### N/A (정적 분석 한정)
- Motion & Animation
- Performance (LCP, CLS)
- 실시간 인터랙션 응답성

### Step 8 — Scoring

**Per-category 점수 (A-F)**:
- A — 의도적, 폴리시드, 디자인 사고 보임
- B — 기본기 견고, 사소한 불일치만
- C — 기능적이나 generic, 디자인 관점 없음
- D — 눈에 띄는 문제, 미완성/부주의 느낌
- F — 사용자 경험을 적극 해침

**Grade 계산:**
- 각 카테고리 A 시작
- High-impact (critical) finding 1개당 한 글자 하락
- Medium-impact (warning) 1개당 반 글자 하락
- Polish (info) 는 노트만, 점수 영향 X
- 최저 F

**듀얼 헤드라인 점수:**
- **Design Score (A-F)** — 위 카테고리 가중평균
- **AI Slop Score (A-F)** — 카테고리 7번만 독립 평가 + pithy verdict 한 줄

### Step 9 — Top-3 Quick Wins

전체 finding 중에서 30분 내 수정 가능한 high-impact 3개 선정:
1. severity critical 우선
2. critical 부족하면 warning 으로 채움
3. 1차 CTA / 진입 직후 마주치는 요소 / 위반 항목 수 순

### Step 10 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-critic-review-{frame-slug}-{YYYYMMDD-HHmm}.md` (cwd 기준. 디렉터리 없으면 생성)
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)

### Step 11 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 Design Score + AI Slop Score + critical/warning 개수 한 줄 요약

## 보고서 구조 (한국어)

```markdown
# Design Critic 리뷰: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 디자인 타입: {MARKETING/LANDING | APP UI | HYBRID}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}

## 헤드라인 점수
- **Design Score: {A-F}**
- **AI Slop Score: {A-F}** — {pithy verdict 한 줄}

## First Impression
- 이 화면이 전달하는 것: {...}
- 내 시선이 가장 먼저 가는 3개: {1}, {2}, {3}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Inferred Design System
- **Fonts** ({n}종): {목록 + 사용 빈도}
- **Colors** (non-gray {n}종): {팔레트 + 웜/쿨/혼합}
- **Heading Scale**: {h1 ... h6 사이즈, 비율 분석}
- **Spacing**: {자주 등장 값, 스케일 일치 여부}
- **Radius**: {분포, uniform 여부}

## 카테고리 점수표

| 카테고리 | 점수 | critical | warning | info | 가중치 |
|---------|------|---------|---------|------|--------|
| Visual Hierarchy & Composition | A | 0 | 1 | 0 | 20% |
| Typography | C | 1 | 2 | 1 | 20% |
| Color & Contrast | B | 0 | 1 | 0 | 15% |
| Spacing & Layout | B | 0 | 2 | 0 | 20% |
| Interaction States | N/A | - | - | - | 5% |
| Content & Microcopy | C | 1 | 0 | 1 | 10% |
| AI Slop | D | 2 | 1 | 0 | 10% |

## Findings

### Visual Hierarchy & Composition — score: {N}
- **severity**: {critical / warning / info}
- **evidence**: `{노드 경로 / 이름 / 수치}`
- **fix**: {구체 액션}
- **참고**: {디자이너 노트}

### Typography — score: {N}
- **severity**: critical
- **evidence**: `Hero > Headline` (font-family: system-ui, 메인 디스플레이 폰트)
- **fix**: Inter 도 generic flag 대상이지만 system-ui 보다 우선. 진지하게 의도 보이려면 Söhne / Untitled Sans / GT America 같은 실제 typeface 선택
- **참고**: (디자이너 노트)

### AI Slop — score: {N}
- **severity**: critical
- **evidence**: `Section "Features"` — 컬러 원 안 아이콘 + 굵은 제목 + 2줄 설명, 3회 대칭 반복
- **fix**: 3-column 그리드 해체. 각 feature 마다 시각 변주(스크린샷, 일러스트, 다른 레이아웃) 또는 narrative scroll
- **참고**: (디자이너 노트)

{... 위반/개선점이 있는 finding 만 ...}

## Top-3 Quick Wins

1. **AI Slop (critical)** — Features 섹션의 3-column 컬러 원 아이콘 그리드 해체. 시각 변주 도입.
2. **Typography (critical)** — system-ui 메인 폰트 교체. 의도된 typeface 선택 (Söhne / Untitled Sans 등).
3. **Content & Microcopy (critical)** — Hero 의 "Unlock the power of..." 카피 교체. 구체적 가치 제안으로.

## N/A 항목 (정적 분석 한정)
- Motion: 인터랙션 흐름 없음
- Performance: 라이브 측정 필요
```

## 인자

```
/design-ui-critic-review <Figma URL | .pen path>
```

- 위치 인자 1개만 필수. 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- 옵션 인자 없음 (간결 디폴트 우선)

## 예시

### 예시 1 — Figma URL (단일 프레임)
```
/design-ui-critic-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → 분류 → First Impression → Design System 추출 → 7 카테고리 평가 → `./design-reviews/design-ui-critic-review-checkout-screen-20260514-1130.md` 생성

### 예시 2 — Pencil 멀티 프레임
```
/design-ui-critic-review ~/Documents/myapp.pen
```
→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택된 3개 프레임 감지 → 각 프레임 평가 → 3개 파일 생성

### 예시 3 — MCP 미연결
```
/design-ui-critic-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → 안내 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 카테고리명은 영어 원어 유지 (Typography, AI Slop 등)
- finding 의 evidence/fix 는 구체적 노드명·수치·액션 명시
- 보고서는 한 프레임당 한 파일
- finding 헤더 포맷 `### {항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / evidence / fix / 참고 필드 동일 (annotate-design 호환)
- 출력 파일 경로: `./design-reviews/design-ui-critic-review-{frame-slug}-{YYYYMMDD-HHmm}.md`

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커 + After mockup 을 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-critic-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## 다른 디자인 리뷰 스킬과의 차이

| 스킬 | 관점 | 핵심 출력 |
|------|------|----------|
| `design-ui-critic-review` (본 스킬) | 디자이너 비평·AI Slop 색출 | Design Score A-F + AI Slop Score A-F 듀얼 헤드라인 |
| `design-ui-polish-review` | 10개 시각 차원 정량 폴리시 평가 | 0-100 + Grade A-F + L1-L5 Level |
| `design-ui-lawsofux-review` | Laws of UX 시각·게슈탈트 법칙 7개 | 법칙별 0-10 점수표 |
| `design-ui-nielsen-review` | Nielsen Aesthetic and Minimalist Design | 1 휴리스틱 심층 평가 |
| `design-ui-ixdf-review` | IxDF UI 5 항목 (Desirable·Visual Rep·Physical Space·Time·Engagement) | 항목별 평가 |
| `design-ui-ecommerce-review` | Baymard 이커머스 UI (Product Card·PDP·PLP) | 3 카테고리 평가 |
| `design-ux-*` 시리즈 | 행동·인지·사용성 관점 | UX 카테고리별 평가 |

본 스킬은 **디자이너 비평·AI Slop 색출·직관적 폴리시 판단** 에 특화. 정량 점수 체계는 `design-ui-polish-review`, UX 법칙 / 사용성 휴리스틱은 별도 스킬 사용.

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 라이브 사이트 audit / 인터랙션 / perf — gstack `/design-review` 책임
- UX 법칙 30개 기반 평가 — `design-ux-lawsofux-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰만
- 코드 생성 — 디자인 파일만

## 참고 자료

- 카테고리 체크리스트는 본 SKILL.md 내 인라인 (별도 references 디렉터리 없음)
- 평가 철학 출처: Steve Krug "Don't Make Me Think", gstack `/design-review` 의 10 카테고리 모델
- AI Slop 블랙리스트: gstack `/design-review` Phase 3 카테고리 9
