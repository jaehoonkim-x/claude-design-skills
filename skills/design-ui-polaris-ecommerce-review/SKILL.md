---
name: design-ui-polaris-ecommerce-review
review-level: L0 Surface
description: "[L0 Surface] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Shopify Polaris Design System 의 7개 카테고리(Information Architecture·Navigation·Data Display·Forms·Actions & Buttons·Feedback·Content)로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. 쿠팡 셀러 통계 대시보드(stat-front) 같은 셀러·관리자용 ecommerce admin 도메인 직격. AG Grid→IndexTable, shadcn Banner→Polaris Banner 4 tone, EmptyState, FormLayout 패턴 매핑 제공. 사용자가 \"Polaris ecommerce admin 리뷰\", \"셀러 admin UI 평가\", \"Polaris 컴플라이언스 검토\", \"polaris review\", \"/design-ui-polaris-ecommerce-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 셀러/관리자 admin UI 리뷰를 요청할 때 사용."
---

# design-ui-polaris-ecommerce-review

**Review Level**: L0 Surface — Shopify Polaris ecommerce admin (단일 프레임 표면).

Shopify Polaris Design System 의 셀러·관리자용 ecommerce admin 패턴을 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다.

**평가 렌즈** = "이 admin 화면이 Polaris 7개 카테고리 기준에서 셀러가 빠르게 데이터를 파악·조작할 수 있도록 설계되어 있는가? AG Grid·shadcn 컴포넌트를 Polaris 패턴으로 얼마나 잘 매핑하고 있는가?"

리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

> **stat-front 도메인 직결**: 쿠팡 셀러 통계 대시보드는 쇼퍼 대상 프론트엔드가 아닌 셀러·관리자 admin 이다. Baymard Institute 기반 `design-ui-ecommerce-review` 가 커버하지 못하는 admin 패턴(IndexTable, FormLayout, Banner tone, EmptyState, Page header)을 이 스킬이 담당한다.

---

## 평가 항목 (Polaris 7 카테고리)

### 1. Information Architecture

| # | 패턴 | 평가 기준 |
|---|------|----------|
| IA1 | Sidebar Nav | 1단계·2단계 항목 구분, 활성 상태 강조, 아이콘 + 라벨 조합 |
| IA2 | Breadcrumb | 현재 위치 표시, 3단계 이상 시 트런케이션 |
| IA3 | Page Header | 페이지 제목 + 부제 + 주요 액션(primary/secondary) 일관 배치 |
| IA4 | Section grouping | 관련 정보 Card 또는 Box 로 그루핑, 섹션 헤더 위계 |

### 2. Navigation & Wayfinding

| # | 패턴 | 평가 기준 |
|---|------|----------|
| NW1 | Primary nav 선택 상태 | 현재 섹션 시각 강조 (bg-surface-selected 토큰 또는 동등) |
| NW2 | Secondary nav / Tab | 하위 섹션 전환 Tab 컴포넌트, 현재 탭 언더라인/배경 |
| NW3 | Contextual link | 셀 내 상세보기 링크, 호버 밑줄, 색 일관성 |
| NW4 | Back navigation | 브레드크럼 또는 뒤로 버튼 항상 노출, 경로 손실 방지 |

### 3. Data Display

| # | 패턴 | 평가 기준 |
|---|------|----------|
| DD1 | IndexTable rows | 행 선택 체크박스, hover 배경, 클릭 영역 충분 (≥ 44px 행 높이) |
| DD2 | IndexTable columns | 헤더 정렬 아이콘, 컬럼 라벨 truncate 방지 |
| DD3 | Bulk actions | 1개 이상 행 선택 시 bulk action 바 노출, 선택 수 표시 |
| DD4 | Filters & Search | 필터 Popover + Applied Filters 태그, 검색 TextField 인라인 |
| DD5 | Sort | 정렬 드롭다운 또는 컬럼 헤더 클릭, 현재 정렬 시각 표시 |
| DD6 | DataTable numeric | 숫자 컬럼 우측 정렬, 단위 표기, 컬럼 너비 고정 |
| DD7 | Card layout | 데이터 카드 내 타이틀·메트릭·추세 배치 일관성 |

### 4. Forms

| # | 패턴 | 평가 기준 |
|---|------|----------|
| FM1 | FormLayout | 관련 필드 그루핑, 라벨 위치(상단), 필드 간 space-400 이상 |
| FM2 | TextField | 플레이스홀더 vs 라벨 구분, 포커스 링, 문자 수 제한 힌트 |
| FM3 | Select / Combobox | 옵션 수 ≤ 7 이면 Select, 초과 시 Combobox (검색 가능) |
| FM4 | Checkbox / Toggle | 라벨 우측 배치, 체크 영역 44×44px 이상 |
| FM5 | Validation & Error inline | 에러 메시지 필드 바로 아래, 빨간색(text-critical), 아이콘 병기 |
| FM6 | Required indicator | 필수 필드 asterisk(*) + 폼 상단 범례 |

### 5. Actions & Buttons

| # | 패턴 | 평가 기준 |
|---|------|----------|
| AB1 | Primary button 단독 | 페이지·섹션당 primary button 1개 원칙 |
| AB2 | Destructive variant | 삭제·취소 액션 destructive tone (빨간), secondary/plain 혼용 금지 |
| AB3 | Plain / subtle hierarchy | 3차 이하 액션은 plain 또는 monochrome-plain |
| AB4 | Button group | 관련 액션 ButtonGroup 으로 묶기, gap 일관 |
| AB5 | ActionList / Popover | 드롭다운 액션 목록 ActionList 패턴, 구분선으로 그루핑 |
| AB6 | Loading state | 비동기 제출 시 버튼 loading prop, 이중 클릭 방지 |

### 6. Feedback

| # | 패턴 | 평가 기준 |
|---|------|----------|
| FB1 | Banner — info | 정보성 메시지 info tone (파란), 아이콘 CircleInformationMajor |
| FB2 | Banner — warning | 경고 메시지 warning tone (노란), 아이콘 AlertMinor |
| FB3 | Banner — critical | 에러/위험 메시지 critical tone (빨간), 아이콘 CircleAlertMajor |
| FB4 | Banner — success | 성공 메시지 success tone (초록), 아이콘 CircleTickMajor |
| FB5 | Toast | 단기 피드백 Toast (3-5초 자동 닫힘), 에러 toast 는 dismissible |
| FB6 | Spinner / Skeleton | 로딩 Spinner 또는 SkeletonPage/SkeletonBodyText, 레이아웃 시프트 방지 |

### 7. Content

| # | 패턴 | 평가 기준 |
|---|------|----------|
| CN1 | Page title | heading-2xl 토큰, 간결 명사구(동사 금지) |
| CN2 | EmptyState | 일러스트 + heading + body 안내문 + primary action CTA 세트 |
| CN3 | Error pages | 404/500 전용 EmptyState, 복구 액션(홈으로/다시 시도) 포함 |
| CN4 | Section subheading | body-md bold, 섹션 간 공백 space-800 이상 |

---

## Polaris 디자인 토큰 매핑 힌트

| 역할 | Polaris 토큰 | 주요 사용처 |
|------|-------------|-----------|
| 앱 배경 | `--p-color-bg-app` | 전체 페이지 배경 |
| 카드 표면 | `--p-color-bg-surface` | Card, Modal, Popover 배경 |
| 선택 행 배경 | `--p-color-bg-surface-selected` | IndexTable 선택 행 |
| 성공 텍스트 | `--p-color-text-success` | 양수 수치, 성공 상태 |
| 위험 텍스트 | `--p-color-text-critical` | 에러, 음수 수치 |
| 기본 간격 단위 | `--p-space-400` (16px) | 카드 내부 패딩 기준 |
| 섹션 간 간격 | `--p-space-800` (32px) | 섹션 분리 gap |
| 페이지 제목 | `--p-font-size-heading-2xl` | Page title |
| 본문 | `--p-font-size-body-md` | 일반 텍스트 |
| 캡션 | `--p-font-size-caption` | 보조 메타 정보 |

---

## stat-front 컴포넌트 매핑

| stat-front 패턴 | 대응 Polaris 패턴 | 리뷰 관점 |
|----------------|------------------|----------|
| AG Grid 테이블 | IndexTable | DD1-DD7 전 항목 적용 |
| shadcn Toast | Polaris Toast / Banner | FB5 + FB1-FB4 tone 준수 |
| shadcn Alert | Polaris Banner 4 tone | FB1-FB4 tone 색상·아이콘 매핑 |
| 빈 데이터 상태 | Polaris EmptyState | CN2 일러스트+heading+action 세트 |
| store-manage 폼 | Polaris FormLayout | FM1-FM6 전 항목 적용 |
| 페이지 레이아웃 | Polaris Page + Card | IA3 + IA4 헤더·섹션 구조 |

---

## design-ui-ecommerce-review 와의 차이

| 구분 | design-ui-ecommerce-review | design-ui-polaris-ecommerce-review |
|------|--------------------------|----------------------------------|
| 대상 사용자 | 쇼퍼 (구매자) | 셀러·관리자 (판매자) |
| 평가 기준 | Baymard Institute 쇼핑 UI | Shopify Polaris admin 패턴 |
| 핵심 화면 | Product Card / PDP / PLP | IndexTable / FormLayout / Dashboard |
| stat-front 적합도 | 낮음 (쇼퍼 렌즈 부적합) | **높음 (셀러 admin 직결)** |
| 주요 rubric | 이미지 비율·CTA 위계·카드 그리드 | Bulk actions·Banner tone·EmptyState |

---

## When to Use

- Figma URL 또는 `.pen` 파일을 주고 셀러·관리자 admin UI 리뷰를 요청할 때
- stat-front 와 같은 쿠팡/Shopify 셀러 대시보드 UI 품질 진단이 필요할 때
- AG Grid→IndexTable, shadcn→Polaris 패턴 매핑 준수 여부를 확인할 때
- Banner tone 4종(info/warning/critical/success) 올바른 사용 여부 점검 시
- FormLayout, EmptyState, Page header 패턴 적합성 검토 시

## Do Not Use

- **쇼퍼 대상 이커머스 UI** (Product Card·PDP·PLP·Cart) → `design-ui-ecommerce-review`
- UX conversion 평가 (Checkout Flow·Trust Signals) → `design-ux-ecommerce-review`
- 일반 시각 폴리시 (타이포·컬러·스페이싱 체계) → `design-ui-polish-review`
- Nielsen Aesthetic 휴리스틱 → `design-ui-nielsen-review`
- 게슈탈트·시각 법칙 → `design-ui-lawsofux-review`
- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 인터랙션·애니메이션 분석 — 단일 프레임 정적 분석 한정

---

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동을 활성화하거나 Figma 데스크탑 앱의 Dev Mode MCP 를 설치한 뒤 다시 시도해주세요." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: 첫 단계에서 ToolSearch 로 해당 prefix 의 도구를 조회. 결과가 비어 있으면 위 안내를 출력하고 즉시 종료. 어떤 코드도 작성하지 않는다.

---

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
   - nodeId 미지정 시 현재 선택 프레임 자동 감지. 멀티 프레임 자동 처리
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
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 폰트·컬러·사이즈 팔레트 추출

### Step 4 — Classifier (admin 페이지 타입 분류)

수집된 프레임을 보고 admin 페이지 타입을 분류:

- **DASHBOARD** — KPI 카드 + 차트 + 개요 테이블
- **INDEX TABLE** — 목록 + 필터·검색·정렬 + 벌크 액션
- **DETAIL VIEW** — 단일 레코드 상세, 섹션 카드 그루핑
- **FORM** — 생성·편집 폼, FormLayout 패턴
- **SETTINGS** — 계정·스토어 설정, 카테고리 사이드바 + 폼 세트
- **EMPTY / ERROR** — EmptyState 또는 에러 페이지
- **HYBRID** — 위 카테고리 혼재

분류 결과 + 추정 셀러 페르소나(예: "일매출 모니터링 셀러, 데스크탑, 통계 확인 목적")를 보고서 메타에 기록.

타입별 카테고리 가중치:
- DASHBOARD: Data Display / Feedback 가중↑
- INDEX TABLE: Data Display 전 항목 집중
- FORM: Forms / Actions 가중↑
- SETTINGS: Forms / Information Architecture 가중↑

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 admin 화면이 전달하는 시각적 인상: [한 문장]
- Polaris 패턴 준수 느낌: [즉각적 감상 — 네이티브/이질적/혼재]
- 내 시선이 가장 먼저 가는 3개: [1], [2], [3]
- 한 단어 요약: [단어]
- 인상 메모: [셀러가 이 화면에서 첫 5초 내에 무엇을 할 수 있는가 — 긍정/부정 구체적으로]
```

이 섹션은 의견을 강하게 적는다. 진단가는 헤지하지 않는다.

### Step 6 — Inferred Admin Pattern Inventory (Phase 2)

수집된 노드 트리 + 속성에서 admin UI 관련 항목 추출:

- **Navigation structure**: sidebar 레이어 수 + 활성 상태 처리
- **Table / Grid pattern**: IndexTable 또는 AG Grid 사용 여부 + 행 높이·체크박스·bulk 바
- **Form fields**: TextField/Select/Checkbox 출현 + 라벨·에러 위치
- **Button hierarchy**: primary/secondary/destructive/plain 분포
- **Banner usage**: 4 tone 중 사용된 tone + 아이콘 일치 여부
- **Toast pattern**: 존재 여부 + 자동 닫힘 디자인 표현
- **EmptyState**: 일러스트·heading·body·CTA 세트 완성 여부
- **Token hints**: bg-app·bg-surface·text-critical·text-success 사용 패턴

### Step 7 — Polaris 7 카테고리 평가 (Phase 3)

각 카테고리마다 0-10 점수. 정적 검증 불가능한 패턴은 `N/A` + 사유. 위반/개선점은 finding 1개로 작성:
- **severity**: critical / warning / info
- **category**: 7개 카테고리 중 해당
- **evidence**: 노드 경로/이름/수치
- **fix**: Polaris 패턴 후보 (컴포넌트명 포함)
- **참고**: Polaris 공식 문서 링크

**점수 기준:**
- 10 — Polaris 네이티브 수준, 패턴 완전 준수
- 8-9 — 대부분 준수, 사소한 토큰·간격 조정만 필요
- 6-7 — 기능적이나 Polaris 패턴과 괴리 존재
- 4-5 — 주요 패턴 위반, 셀러 작업 흐름 저해
- 0-3 — Polaris 패턴 무시, admin 경험 적극 훼손
- N/A — 해당 admin 페이지 타입에 적용 불가

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding 당)
- warning: -1 ~ -2
- info: 점수 영향 없음, 개선 노트만

### Step 8 — Polaris Compliance Grade 산출

**평균 환산** = (적용 카테고리 점수 합) / (적용 카테고리 수) → 0-10

**Grade 환산:**
- 9.0-10 = **A** (Polaris Native — 패턴 완전 준수)
- 7.5-8.9 = **B** (Polaris Aligned — 사소한 polish)
- 6.0-7.4 = **C** (Partial Compliance — 주요 패턴 개선 필요)
- 4.0-5.9 = **D** (Non-compliant — 셀러 워크플로 저해)
- 0-3.9  = **F** (Critical Non-compliance — admin 패턴 전면 재설계)

**추가 헤드라인:**
- **Admin Efficiency 공식**: Data Display({N}) + Actions & Buttons({N}) 평균 = **셀러 작업 효율 한 줄 평가**

### Step 9 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-polaris-ecommerce-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 10 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임: admin 페이지 타입, Polaris Compliance Grade (A-F), 평균 점수, critical/warning 건수 한 줄 요약
- Polaris 미커버 항목 리뷰가 필요하면 `design-ui-polish-review` 또는 `design-ux-ecommerce-review` 병행 권장

### Step 11 — Top-3 Pattern Fix 제안

finding 이 3건 이상이면 Polaris 패턴 위반 중 impact 상위 3개를 픽업하여 제안 카드 작성:

각 카드 포맷:
- **현재 패턴**: (비준수 컴포넌트/토큰 + evidence)
- **Polaris 권장 패턴**: (대응 컴포넌트명 + props)
- **셀러 영향**: (작업 흐름에 미치는 구체적 영향)
- **stat-front 매핑**: (AG Grid/shadcn → Polaris 대응 힌트)
- **기대 점수 변화**: (카테고리 N → N')
- **노력 규모**: Low / Medium / High

### Step 12 — Polaris Token Mapping Hints 표 작성

보고서 내 "Polaris Token Mapping" 섹션 추가. 현재 프레임에서 감지된 색·간격·타이포 값과 가장 가까운 Polaris 토큰을 매핑:

| 현재 값 | 역할 추정 | Polaris 토큰 권장 | 비고 |
|--------|---------|-----------------|------|
| `#F4F6F8` | 앱 배경 | `--p-color-bg-app` | Polaris surface-subdued 동등 |
| `#E4E5E7` | 카드 구분선 | `--p-color-border-subdued` | - |
| `16px` padding | 카드 내부 | `--p-space-400` | 4px 그리드 ×4 |

---

## 보고서 구조 (한국어)

```markdown
# Polaris Ecommerce Admin Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- Admin 페이지 타입: {DASHBOARD | INDEX TABLE | DETAIL VIEW | FORM | SETTINGS | EMPTY/ERROR | HYBRID}
- 추정 셀러 페르소나: {역할·목적·기기}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 평가 스킬: design-ui-polaris-ecommerce-review (Shopify Polaris 7개 카테고리)

## 헤드라인
- **Polaris Compliance Grade: {A-F}** ({평균}/10)
- **Admin Efficiency**: Data Display ({N}/10) + Actions & Buttons ({N}/10) = {한 줄 평가}
- 적용 카테고리: {applied}/7 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 admin 화면이 전달하는 시각적 인상: {...}
- Polaris 패턴 준수 느낌: {...}
- 내 시선이 가장 먼저 가는 3개: {1}, {2}, {3}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Inferred Admin Pattern Inventory
- **Navigation structure**: {...}
- **Table / Grid pattern**: {...}
- **Form fields**: {...}
- **Button hierarchy**: {...}
- **Banner usage**: {...}
- **Toast pattern**: {...}
- **EmptyState**: {...}
- **Token hints**: {...}

## 카테고리별 점수

| # | 카테고리 | 점수 | 비고 |
|---|----------|------|------|
| 1 | Information Architecture | -/10 | - |
| 2 | Navigation & Wayfinding | -/10 | - |
| 3 | Data Display | -/10 | - |
| 4 | Forms | -/10 | - |
| 5 | Actions & Buttons | -/10 | - |
| 6 | Feedback | -/10 | - |
| 7 | Content | -/10 | - |

## Findings

### {카테고리}.{패턴코드} — score: {N}
- **severity**: critical | warning | info
- **category**: {카테고리명}
- **evidence**: `{노드 경로}` — {구체 수치/관찰}
- **fix**: {Polaris 컴포넌트명 + props 포함 1-2문장 액션}
- **참고**: {https://polaris.shopify.com/components/...}

{위반/개선점이 있는 항목만 나열}

## Top-3 Pattern Fix

### Fix 1 — {카테고리}.{패턴코드} ({severity})
- **현재 패턴**: {...}
- **Polaris 권장 패턴**: {...}
- **셀러 영향**: {...}
- **stat-front 매핑**: {...}
- **기대 점수 변화**: {카테고리} {N} → {N'}
- **노력**: {Low/Medium/High}

### Fix 2 — ...
### Fix 3 — ...

## Polaris Token Mapping Hints

| 현재 값 | 역할 추정 | Polaris 토큰 권장 | 비고 |
|--------|---------|-----------------|------|
| {...} | {...} | {...} | {...} |

## N/A 항목 (적용 보류)
- {카테고리}: {admin 페이지 타입에 해당 없음 등 이유}

## 다음 단계 (권장 후속)
- `annotate-design` — 이 보고서 .md 를 파싱하여 디자인 파일에 코멘트 부착
- `design-ui-polish-review` — 타이포·컬러·스페이싱 일반 폴리시 추가 검토
- `design-ux-ecommerce-review` — 셀러 UX conversion (폼 흐름·필터 UX) 검토
```

---

## 인자

```
/design-ui-polaris-ecommerce-review <Figma URL | .pen path>
```

- 위치 인자 1개만 필수
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- 옵션 인자 없음 (간결 디폴트 우선)

---

## 예시

### 예시 1 — Figma URL (IndexTable 화면)
```
/design-ui-polaris-ecommerce-review https://www.figma.com/design/abc123XYZ/StatFront?node-id=10-2048
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → 타입 "INDEX TABLE" 분류 → First Impression → Admin Pattern Inventory → 7 카테고리 평가 → `./design-reviews/design-ui-polaris-ecommerce-review-order-list-20260518-1430.md` 생성

### 예시 2 — Pencil 멀티 프레임 (Dashboard + Form)
```
/design-ui-polaris-ecommerce-review ~/Documents/stat-front.pen
```
→ Pencil MCP 체크 → 선택된 2 프레임 자동 분류:
- `./design-reviews/design-ui-polaris-ecommerce-review-dashboard-20260518-1430.md`
- `./design-reviews/design-ui-polaris-ecommerce-review-store-manage-form-20260518-1430.md`

### 예시 3 — stat-front 전체 진단 세트
```
/design-ui-polaris-ecommerce-review <URL>   # Polaris admin 7카테고리
/design-ui-polish-review <URL>              # 타이포·컬러·스페이싱
/design-ux-ecommerce-review <URL>           # 셀러 UX conversion
```
→ 세 스킬 병행으로 stat-front admin 전체 UI/UX 커버

### 예시 4 — MCP 미연결
```
/design-ui-polaris-ecommerce-review ~/Documents/stat-front.pen
```
→ ToolSearch 로 `mcp__pencil__*` 0건 → 안내 메시지 출력 후 종료

### 예시 5 — Banner tone 집중 리뷰 (Feedback 카테고리)
```
/design-ui-polaris-ecommerce-review https://www.figma.com/design/abc123XYZ/StatFront?node-id=30-4096
```
→ FB1-FB6 finding 상세 분석 → shadcn Alert → Polaris Banner 4 tone 매핑 힌트 포함

---

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- Polaris 컴포넌트명은 영어 원어 유지 (IndexTable, FormLayout, Banner, EmptyState, Toast 등)
- finding 헤더 포맷 `### {카테고리}.{패턴코드} — score: {N}` (annotate-design 스킬 파싱 호환)
- finding 의 severity / category / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)
- evidence/fix 는 구체적 노드명·수치·Polaris 컴포넌트 props 명시
- 보고서는 한 프레임당 한 파일
- 출력 경로: `./design-reviews/design-ui-polaris-ecommerce-review-{frame-slug}-{YYYYMMDD-HHmm}.md`

---

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-polaris-ecommerce-review <design 파일>  → 리뷰 .md 생성
/annotate-design <리뷰 .md>                        → 디자인 파일에 시각 코멘트 부착
```

---

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 라이브 사이트 audit / 인터랙션 / perf 실측 — gstack `/design-review` 책임
- 쇼퍼 대상 이커머스 UI (Product Card·PDP·PLP) — `design-ui-ecommerce-review` 책임
- UX conversion 평가 (Checkout·Cart·Trust Signals) — `design-ux-ecommerce-review` 책임
- 일반 시각 폴리시 (타이포·컬러·스페이싱 체계) — `design-ui-polish-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 / 컴포넌트 구현 — 디자인 파일만

---

## 참고 자료

- Polaris Design System: https://polaris.shopify.com/
- Polaris Patterns: https://polaris.shopify.com/patterns
- Polaris Components: https://polaris.shopify.com/components
- Polaris Tokens: https://polaris.shopify.com/tokens/color
- IndexTable 패턴: https://polaris.shopify.com/components/lists/index-table
- FormLayout 패턴: https://polaris.shopify.com/components/layout-and-structure/form-layout
- Banner 4 tone: https://polaris.shopify.com/components/feedback-indicators/banner
- EmptyState: https://polaris.shopify.com/components/layout-and-structure/empty-state
- Shopify Engineering Blog: https://shopify.engineering/
- 대응 전문 스킬: `design-ui-ecommerce-review` (Baymard 쇼퍼 UI), `design-ui-polish-review` (시각 폴리시), `design-ux-ecommerce-review` (UX conversion)
