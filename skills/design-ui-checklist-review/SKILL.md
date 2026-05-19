---
name: design-ui-checklist-review
review-level: L0 Surface
description: "[L0 Surface] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Checklist Design 56 카탈로그 기반 구체 항목 체크리스트로 정적 평가하여 한국어 마크다운 리뷰 보고서를 생성. 5 카테고리 rubric — Website Pages(9+) + Components(10+) + User Flows(6+) + Topics(3) + Brand Elements(3). 페이지 타입(Login/Signup/Pricing/Cart 등) 자동 분류 → 해당 체크리스트 로드 → 항목별 ✅/❌/⚠️ 평가 → Coverage % + Present/Missing/Partial 분류 + Top Missing (HIGH/MED). 기존 11종 스킬(Nielsen·IxDF·Laws)이 \"WHY(왜 좋은 UI)\"를 다룬다면 이 스킬은 \"WHAT(무엇이 있어야 하는가)\"를 다루는 직교 보완재. 사용자가 \"체크리스트 리뷰\", \"항목 체크\", \"checklist review\", \"무엇이 있어야 하는지\", \"Login 페이지 항목\", \"/design-ui-checklist-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 구체 항목 체크를 요청할 때 사용."
---

# design-ui-checklist-review

**Review Level**: L0 Surface — Checklist Design 56 카탈로그 기반 구체 항목 체크리스트 (단일 프레임 또는 컴포넌트).

Checklist Design(checklist.design) 의 56개 카탈로그 항목을 rubric 으로 사용하여 디자인 프레임이 **반드시 포함해야 하는 요소**를 항목별로 ✅/❌/⚠️ 평가한다. 기존 `design-ui-ixdf-review` 등 11종의 휴리스틱 스킬이 "왜 좋은 UI인가(WHY)"를 평가한다면, 이 스킬은 "무엇이 있어야 하는가(WHAT)"를 평가하는 **직교 보완재**다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 `annotate-design` 책임.

평가 렌즈 = "이 페이지·컴포넌트·플로우에 반드시 있어야 하는 구체 UI 요소가 모두 존재하는가? 빠진 항목 중 가장 중요한 것은 무엇인가?"

## 5 카테고리 rubric

### Category 1. Website Pages (9+ 페이지 타입)

각 페이지 타입별 구체 항목 체크리스트. 자동 분류 후 해당 목록만 적용.

| 페이지 타입 | 대표 체크 항목 (예시) |
|------------|----------------------|
| **Login** | 이메일 필드, 비밀번호 필드 + show/hide, 비밀번호 찾기 링크, 회원가입 링크, 소셜 로그인, Remember me, 인라인 에러 메시지, 로딩 상태, CAPTCHA, 키보드 접근성, 클라이언트 validation, 성공 redirect |
| **Sign Up** | 이름 필드, 이메일 필드, 비밀번호 + 강도 표시, 비밀번호 확인, 이용약관 동의, 소셜 가입, 이미 계정 있는 경우 링크, 이메일 인증 안내, 인라인 에러, 로딩 상태 |
| **Pricing** | 요금제 비교 표, 가격 강조(연간/월간 토글), 가장 인기 있는 플랜 배지, CTA 버튼(플랜별), FAQ 섹션, 기능 비교 체크마크, 환불 정책, 연락처/영업 CTA, 신뢰 배지(카드 아이콘 등) |
| **Cart** | 상품 목록(이름·이미지·수량·가격), 수량 변경, 항목 삭제, 소계·총계, 할인 코드 입력, 결제하기 CTA, 쇼핑 계속하기 링크, 빈 카트 상태, 배송비 추정 |
| **Billing** | 현재 요금제 표시, 청구 주기, 결제 수단(카드 정보·변경), 청구서 내역, 다음 결제일, 구독 취소 링크, 영수증 다운로드, 세금 정보 |
| **Blog** | 게시글 목록, 카테고리/태그 필터, 날짜·작성자, 썸네일, 검색, 페이지네이션, RSS/뉴스레터 구독, 소셜 공유, 관련 글 |
| **Careers** | 채용 공고 목록, 부서/위치 필터, 채용 상세 페이지 링크, 지원 CTA, 회사 문화 섹션, 복지 요약, 채용 문의 연락처 |
| **Contact Us** | 연락처 폼(이름·이메일·메시지), 전송 CTA, 지도/주소, 전화번호, 이메일 주소, 소셜 링크, 영업시간, 성공/실패 메시지 |
| **FAQ** | 질문-답변 아코디언, 카테고리 필터, 검색 기능, 관련 질문 링크, 추가 도움 CTA(고객센터 연결) |

> 추가 페이지 타입(Product Detail, Search Results, Dashboard, Profile, 404, Onboarding 등)은 frame 내용에서 추론하여 체크리스트 확장 적용.

### Category 2. Components (10+ 컴포넌트 타입)

단일 컴포넌트 또는 컴포넌트 집합 프레임에 대한 항목 체크.

| 컴포넌트 | 체크 항목 |
|---------|-----------|
| **Button** | 레이블 명확성, 아이콘(좌/우) 정렬, hover/active/disabled 상태, 로딩 상태, 충분한 터치 타겟(44×44px), 색상 대비 |
| **Card** | 이미지/썸네일, 제목, 부제목/설명, CTA, 메타 정보(날짜·카테고리), hover 상태, 클릭 영역 명확성 |
| **Checkbox** | 기본/체크/중간(indeterminate)/비활성 상태, 레이블 텍스트, 포커스 링, 오류 상태, 터치 타겟 |
| **Modal** | 제목, 닫기(×) 버튼, 배경 overlay, 주요 액션 CTA, 취소/보조 액션, ESC 닫기 신호, 스크롤 가능 내용 처리, 포커스 트랩 힌트 |
| **Navigation** | 로고, 주요 메뉴 항목, 현재 페이지 활성 상태, 모바일 햄버거/드로어, CTA 버튼, 로그인/로그아웃 링크, 검색 |
| **Tabs** | 활성/비활성/disabled 상태, 언더라인/배경 표시, 아이콘+레이블 조합, 오버플로우(더보기/스크롤) 처리 |
| **Toast** | 성공/에러/경고/정보 타입, 아이콘, 메시지 텍스트, 닫기 버튼, 자동 사라짐 진행 바, 위치(우상단 등) |
| **Tooltip** | 화살표(방향), 최대 너비, 지연 표시, 트리거 요소 명확성, 어두운/밝은 테마 |
| **Slider** | 트랙, 썸, 최소/최대 레이블, 현재 값 표시, 비활성 상태, 키보드 조작 힌트, 범위(range) 슬라이더 |
| **Table** | 헤더 행, 정렬 기능(오름/내림), 행 hover 상태, 체크박스 선택, 빈 상태, 로딩 skeleton, 페이지네이션, 열 너비 조정 힌트 |

> 추가 컴포넌트(Input, Select, Datepicker, Badge, Avatar, Breadcrumb, Pagination, Progress Bar, Accordion 등)는 프레임 감지 시 자동 확장.

### Category 3. User Flows (6+ 플로우 타입)

플로우 단위 필수 상태·화면 체크. 각 단계별 화면 존재 여부 평가.

| 플로우 | 체크 항목 |
|--------|-----------|
| **Add to Cart** | 상품 상세 → 수량 선택 → 카트 추가 CTA → 카트 아이콘 업데이트/피드백 → 카트 페이지 이동 또는 슬라이드아웃 |
| **Password Reset** | 이메일 입력 → 발송 완료 안내 → 이메일 링크 → 새 비밀번호 입력 → 확인 → 성공 메시지 + 로그인 리다이렉트 |
| **Account Delete** | 설정 내 삭제 옵션 → 경고/확인 다이얼로그 → 비밀번호 재인증 → 최종 확인 → 로그아웃 + 완료 메시지 |
| **Subscription Cancel** | 해지 진입 → 이유 선택 → 혜택 유지 제안(오퍼) → 최종 확인 → 해지 완료 + 잔여 기간 안내 |
| **Form Submit** | 입력 → 클라이언트 validation → 제출 CTA → 로딩 상태 → 성공 화면 or 에러 + 재시도 |
| **Payment** | 결제 방법 선택 → 카드/계좌 입력 → 보안 배지 → 주문 요약 → 최종 결제 CTA → 로딩 → 성공 영수증 or 실패 안내 |

### Category 4. Topics (3)

페이지·컴포넌트를 가로지르는 크로스커팅 관심사.

| Topic | 체크 항목 |
|-------|-----------|
| **Responsiveness** | 모바일(375px) 레이아웃 존재, 태블릿(768px) 중간 브레이크포인트, 텍스트 잘림 없음, 이미지 비율 유지, 터치 타겟 44×44px, 하단 safe area 여백 |
| **UX Copy** | 에러 메시지 plain language(사용자 탓 없음), CTA 레이블 행동 지향(동사+명사), 빈 상태 안내 텍스트, 성공 메시지, 마이크로카피 일관성(경어체/반말 혼용 없음) |
| **Dark Mode** | 배경색 전환, 텍스트 대비 유지(WCAG AA), 아이콘 색상 전환, 이미지 overlay 처리, 입력 필드 border 가시성, 그림자 → 강한 border 전환 |

### Category 5. Brand Elements (3)

| Element | 체크 항목 |
|---------|-----------|
| **Logo** | 위치(좌상단 또는 중앙), 최소 크기(32px 이상), 클릭 시 홈 이동 힌트, SVG/벡터 품질, 다크모드 변형 존재 |
| **Typography** | 폰트 패밀리 일관성(최대 2종), 타이포 스케일(H1→H2→H3→body→caption 단계), 줄간격(1.4-1.6), 최소 본문 크기(16px 이상), 강조 처리(bold/color) 일관성 |
| **Tone of Voice** | 브랜드 키워드 일관성(친근함/전문성 등), 문장 길이 적절성, 수동태 회피, 전문용어 설명 여부, 긍정적 프레이밍 |

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일을 주고 "체크리스트 리뷰", "항목 체크", "무엇이 있어야 하는지", "Login 페이지 검토", "필수 요소 확인" 등을 요청할 때
- 신규 페이지 개발 전 "빠진 요소"를 조기 발견하고 싶을 때
- stat-front login/signup/store-manage/AG Grid 테이블 페이지의 구체 항목 점검이 필요할 때
- 디자인 QA 전 체크리스트 기반 통과/실패 기준이 필요할 때
- 기존 WHY(Nielsen·IxDF·Laws) 스킬 결과를 보완하여 WHAT 관점 커버리지를 확보하고 싶을 때

## Do Not Use

- "왜 좋은/나쁜 UI인가" 평가 → `design-ui-ixdf-review`, `design-ui-nielsen-review`, `design-ui-lawsofux-review`
- 시각 폴리시(컬러·간격·타이포 위계 점수) → `design-ui-polish-review`
- user flow step-by-step 구조 분석 → `design-ux-flow-review`
- 이커머스 funnel 특화 UX → `design-ux-ecommerce-review`
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 라이브 사이트 audit → gstack `/design-review`
- 발산형 UI 재해석 → `ux-audit-rethink`

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동을 활성화하거나 Figma 데스크탑 앱의 Dev Mode MCP 를 설치한 뒤 다시 시도해주세요." |
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
- `--category {Pages|Components|Flows|Topics|Brand}`: 평가 카테고리 수동 지정. 미지정 시 자동 분류.
- `--type {Login|Signup|Pricing|Cart|Button|Modal|...}`: 페이지/컴포넌트 타입 수동 지정. 미지정 시 자동 분류.

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 로 프레임 구조 파악
   - nodeId 미지정 시 현재 선택 프레임 사용
2. 각 frame 에 대해:
   - `mcp__claude_ai_Figma__get_design_context(fileKey, nodeId=frame.id)` 로 deep 트리 수집
   - `mcp__claude_ai_Figma__get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고 이미지 확보

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별
   - 선택이 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id])` 로 deep 노드 트리 수집
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(node_id=frame_id)` 로 시각 이미지 확보
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 텍스트·컴포넌트명 추출

### Step 4 — 페이지/컴포넌트 타입 자동 분류 (Classifier)

수집된 프레임의 레이어 이름, 텍스트 내용, 컴포넌트 목록을 분석하여 분류:

**Website Pages 분류 신호:**
- "login", "sign in", "로그인" 텍스트 → **Login**
- "sign up", "register", "회원가입" 텍스트 → **Sign Up**
- "pricing", "plan", "요금", "price" 텍스트 → **Pricing**
- "cart", "basket", "장바구니" 텍스트 → **Cart**
- "billing", "invoice", "청구", "결제 내역" 텍스트 → **Billing**
- "blog", "article", "post", "글" 텍스트 → **Blog**
- "careers", "jobs", "채용" 텍스트 → **Careers**
- "contact", "연락처", "문의" 텍스트 → **Contact Us**
- "faq", "자주 묻는", "질문" 텍스트 → **FAQ**

**Components 분류 신호:**
- 단일 버튼 레이어 집합 → **Button**
- 카드 반복 패턴 → **Card**
- modal/dialog 레이어 → **Modal**
- nav/sidebar 레이어 → **Navigation**
- tab/탭 레이어 → **Tabs**
- toast/snackbar 레이어 → **Toast**
- table/그리드 레이어 → **Table**
- slider/range 레이어 → **Slider**
- tooltip 레이어 → **Tooltip**
- checkbox 레이어 집합 → **Checkbox**

**Topics 분류 신호:**
- 375px / 390px / 320px 프레임 너비 → **Responsiveness**
- 다크 배경(#000000 ~ #1f1f1f) 프레임 → **Dark Mode**
- 텍스트 노드 집중, UI 요소 적음 → **UX Copy**

**Brand Elements 분류 신호:**
- 로고 레이어만 포함 → **Logo**
- 폰트/텍스트 스타일 가이드 → **Typography**
- 카피/문구 샘플 집중 → **Tone of Voice**

분류 결과가 복수이면 가장 높은 신호 강도 타입으로 결정. 불분명하면 사용자에게 확인 요청.

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 본 직후, 분석 시작 전 **첫 반응**을 1인칭으로 작성:

```
- 이 화면/컴포넌트의 목적: [한 문장]
- 첫눈에 확인되는 주요 요소: [3개]
- 첫눈에 빠져 보이는 것: [2개]
- 전반적 완성도 인상: [한 단어]
- 인상 메모: [구체적 긍정/부정 — 헤지 없이]
```

진단가는 헤지하지 않는다.

### Step 6 — 체크리스트 로드 + 항목 목록 확정

Step 4 분류 결과에 맞는 카테고리의 체크리스트를 본 SKILL.md 에서 로드.

- 분류된 타입의 항목 수 = 전체 체크 항목(Total)
- `--type` 수동 지정이면 해당 타입 목록만 사용
- Topic(Responsiveness·UX Copy·Dark Mode) + Brand Elements 는 모든 페이지 타입에 선택적으로 추가 가능 (`--category Topics` 또는 `--category Brand` 옵션 시 강제 포함)

각 항목에 **Priority** 사전 지정:
- **HIGH**: 핵심 기능 동작에 직결(비밀번호 필드, CTA 버튼, 에러 메시지 등)
- **MED**: 사용성 향상(소셜 로그인, Remember me, 키보드 접근성 등)
- **LOW**: 보완적 요소(CAPTCHA, 로딩 스피너 세부 스타일 등)

### Step 7 — 항목별 평가 (Phase 3)

각 항목을 ✅ / ❌ / ⚠️ / N/A 로 판정:

- ✅ **Present**: 프레임 노드 트리에서 해당 요소 확인됨
- ❌ **Missing**: 해당 요소가 프레임에 없음
- ⚠️ **Partial**: 요소는 있으나 불완전(레이블 없음, 상태 누락 등)
- N/A: 해당 타입에 적용 불가

판정 기준:
- 노드 이름, 컴포넌트 타입, 텍스트 내용, 레이어 계층 구조로 존재 여부 추론
- 요소 이름이 명확하지 않아도 시각 스크린샷 + 레이아웃 스냅샷으로 보완 판단
- ⚠️ 판정 시 구체 근거 명시 (예: "비밀번호 show/hide 토글 버튼 레이어 없음, input 필드만 존재")

finding 1개당 포맷:
- **severity**: critical (HIGH Priority + Missing) | warning (MED Priority + Missing 또는 HIGH + Partial) | info (LOW Priority 또는 Partial 개선 사항)
- **lens**: Category 1 Pages | Category 2 Components | Category 3 Flows | Category 4 Topics | Category 5 Brand
- **evidence**: 노드 경로/이름 또는 "해당 레이어 없음" + 스크린샷 좌표 힌트
- **fix**: 구체 추가 액션 (예: "Input 우측에 eye 아이콘 버튼 추가, 클릭 시 type=text 전환")
- **참고**: Checklist Design checklist.design/{타입} 또는 관련 가이드라인

### Step 8 — Coverage 산출 (Phase 4)

```
Coverage % = (✅ Present 수 + ⚠️ Partial 수 × 0.5) / (Total - N/A 수) × 100
```

**등급 환산:**
- 90-100% = **A** (Excellent — 거의 완전한 구현)
- 75-89% = **B** (Good — 소수 항목 보완 필요)
- 60-74% = **C** (Acceptable — 주요 항목 일부 누락)
- 40-59% = **D** (Poor — 핵심 요소 다수 누락)
- 0-39%  = **F** (Critical — 재설계 수준 누락)

**추가 헤드라인:**
- **Present**: ✅ 항목 수 (HIGH/MED/LOW 분류)
- **Missing**: ❌ 항목 수 (HIGH/MED/LOW 분류)
- **Partial**: ⚠️ 항목 수

### Step 9 — 보고서 작성

**파일 경로**: `./design-reviews/design-ui-checklist-review-{type-slug}-{YYYYMMDD-HHmm}.md`
- `{type-slug}`: 분류 타입 kebab-case (예: `login-page`, `modal-component`, `password-reset-flow`)
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 10 — Top Missing 제안 (Phase 5)

Missing(❌) 항목 중 **HIGH Priority** 우선, 동순위면 **MED Priority** 순으로 상위 항목을 뽑아 개선 카드 작성.

각 카드 포맷:
- **누락 항목명** (Priority: HIGH | MED)
- **이유**: 해당 항목이 없으면 발생하는 구체 사용자 문제
- **추가 방법**: 컴포넌트명/레이어 구조/상태 정의 수준의 구체 제안
- **노력**: Low (디자인 1시간 이내) | Med (하루 이내) | High (여러 화면 변경)

### Step 11 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로
- 분류 타입 + Coverage % + 등급
- Present / Missing / Partial 개수 (HIGH/MED/LOW 브레이크다운)
- critical / warning / info 개수
- Top Missing HIGH 항목 이름 나열 (최대 5개)
- 다음 단계 제안 (annotate-design / 휴리스틱 보완 스킬)

## 보고서 구조 (한국어)

```markdown
# Checklist Review: {페이지/컴포넌트 타입}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 분류 타입: {Login | Sign Up | Pricing | Cart | Billing | Blog | Careers | Contact Us | FAQ | Button | Card | Checkbox | Modal | Navigation | Tabs | Toast | Tooltip | Slider | Table | Add to Cart | Password Reset | Account Delete | Subscription Cancel | Form Submit | Payment | Responsiveness | UX Copy | Dark Mode | Logo | Typography | Tone of Voice}
- 카테고리: {Website Pages | Components | User Flows | Topics | Brand Elements}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: Checklist Design (checklist.design) 56 카탈로그 — WHAT 기반 구체 항목 체크리스트

## 헤드라인
- **Coverage: {%}** (등급: {A-F})
- **Present**: ✅ {n}개 (HIGH {n} / MED {n} / LOW {n})
- **Missing**: ❌ {n}개 (HIGH {n} / MED {n} / LOW {n})
- **Partial**: ⚠️ {n}개
- **N/A**: {n}개
- 전체 체크 항목: {Total}개
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 화면/컴포넌트의 목적: {...}
- 첫눈에 확인되는 주요 요소: {1}, {2}, {3}
- 첫눈에 빠져 보이는 것: {1}, {2}
- 전반적 완성도 인상: {...}
- 인상 메모: {...}

## 체크리스트 평가표

| # | 항목 | Priority | 판정 | 비고 |
|---|------|----------|------|------|
| 1 | 이메일 필드 | HIGH | ✅ | Input 레이어 "email-input" 확인 |
| 2 | 비밀번호 필드 + show/hide | HIGH | ⚠️ | Input 있으나 눈 아이콘 버튼 없음 |
| 3 | 비밀번호 찾기 링크 | MED | ❌ | 해당 텍스트 링크 없음 |
| 4 | 회원가입 링크 | MED | ✅ | "계정이 없으신가요?" 텍스트 확인 |
| ... | ... | ... | ... | ... |

## Findings

### {항목명} — score: {✅/❌/⚠️}
- **severity**: critical | warning | info
- **lens**: Category {1 Pages | 2 Components | 3 Flows | 4 Topics | 5 Brand}
- **evidence**: {노드 경로/이름 또는 "해당 레이어 없음" + 구체 근거}
- **fix**: {구체 추가/수정 액션}
- **참고**: Checklist Design checklist.design/{type} — {항목명}

{Missing(❌) 및 Partial(⚠️) 항목만 나열}

## Top Missing

### [HIGH] {항목명}
- **이유**: {없으면 발생하는 구체 사용자 문제}
- **추가 방법**: {컴포넌트명/레이어 구조/상태 정의 수준의 구체 제안}
- **노력**: {Low | Med | High}

### [HIGH] {항목명}
- **이유**: {...}
- **추가 방법**: {...}
- **노력**: {...}

### [MED] {항목명}
- ...

## N/A 항목 (해당 타입 미적용)
- {항목명}: {N/A 이유}

## 다음 단계 (권장 후속)
- `annotate-design` 스킬로 Finding 을 디자인 파일에 시각 코멘트 부착
- WHY 관점 보완: `design-ui-ixdf-review` (시각 매력·공간·상태) 병행 권장
- 사용성 원칙 보완: `design-ux-nielsen-review` (Nielsen 10 휴리스틱) 병행 권장
- Missing HIGH 항목 해소 후 동일 스킬 재실행 (delta Coverage 측정)
```

## 인자

```
/design-ui-checklist-review <Figma URL | .pen path> [--category {Pages|Components|Flows|Topics|Brand}] [--type {타입명}]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- 옵션 `--category`: 평가 카테고리 수동 지정. 미지정 시 자동 분류.
- 옵션 `--type`: 페이지/컴포넌트/플로우 타입 수동 지정. 미지정 시 자동 분류.
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Figma Login 페이지 (자동 분류)
```
/design-ui-checklist-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → "로그인" 텍스트 감지 → Login 타입 분류 → 25항목 체크리스트 로드 → 항목별 ✅/❌/⚠️ 평가 → Coverage 68% (C등급) → `./design-reviews/design-ui-checklist-review-login-page-20260518-1030.md` 생성

### 예시 2 — Pencil Modal 컴포넌트 (수동 타입 지정)
```
/design-ui-checklist-review ~/Documents/myapp.pen --type Modal
```
→ Pencil MCP 체크 → `get_editor_state` → 선택 프레임 1개 감지 → Modal 체크리스트 로드 → 8항목 평가 → Coverage 75% → 보고서 생성

### 예시 3 — Figma Pricing 페이지 + Topic 추가
```
/design-ui-checklist-review https://www.figma.com/design/abc/Shop?node-id=10-5 --category Topics
```
→ Pricing 자동 분류 + Responsiveness·UX Copy·Dark Mode 항목 추가 포함 → 확장 체크리스트 평가 → 보고서 생성

### 예시 4 — stat-front Signup 페이지
```
/design-ui-checklist-review https://www.figma.com/design/xyz/EasySeller?node-id=20-100
```
→ "회원가입" 텍스트 감지 → Sign Up 타입 분류 → 20항목 체크 → Missing HIGH: 비밀번호 강도 표시, 이메일 인증 안내 → Coverage 60% (C등급) → 보고서 생성

### 예시 5 — Pencil AG Grid Table 컴포넌트
```
/design-ui-checklist-review ~/Desktop/projects/design/easyseller.pen --type Table
```
→ Table 체크리스트 로드 → 9항목 평가 (헤더 행·정렬·hover·체크박스·빈상태·skeleton·페이지네이션·열 너비·선택 상태) → Coverage 산출 → 보고서 생성

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 항목명은 영어 원어 유지 (show/hide, Remember me, CAPTCHA, skeleton 등)
- finding 의 evidence/fix 는 구체적 노드명·수치·액션 명시
- 보고서는 한 프레임당 한 파일 (멀티 프레임 시 타입별 1파일)
- finding 헤더 포맷 `### {항목명} — score: {✅/❌/⚠️}` (annotate-design 스킬 파싱 호환)
- severity / lens / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)
- Missing(❌) 및 Partial(⚠️) 항목만 Findings 섹션에 나열 (Present 항목은 평가표에만)

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-checklist-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- "왜 좋은/나쁜 UI인가" 평가 (Nielsen·IxDF·Laws·폴리시) — 각 전용 스킬 책임
- 라이브 사이트 audit / 인터랙션 / perf 실측 — gstack `/design-review` 책임
- user flow step-by-step 구조 분석 (Gulf of Execution·dark pattern·conversion) — `design-ux-flow-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만
- 신규 체크리스트 카탈로그 항목 추가 제안 — SKILL.md 편집 대상, 런타임에서 확장 불가

## 다른 design-* 스킬과의 관계 (직교 보완재)

| 스킬 | 평가 관점 | 질문 |
|------|----------|------|
| `design-ui-nielsen-review` | WHY — Nielsen 10 휴리스틱 | 이 UI가 사용성 원칙을 따르는가? |
| `design-ui-ixdf-review` | WHY — IxDF UI 5항목 | 이 UI가 시각·공간·시간 품질을 갖추는가? |
| `design-ui-lawsofux-review` | WHY — Laws of UX 인지법칙 | 이 UI가 인지 법칙을 활용하는가? |
| `design-ui-polish-review` | WHY — 시각 폴리시 10차원 | 이 UI의 시각 완성도가 충분한가? |
| **`design-ui-checklist-review`** | **WHAT — 구체 항목 존재 여부** | **이 페이지에 반드시 있어야 할 것이 모두 있는가?** |

권장 조합: `design-ui-checklist-review` (WHAT) → `design-ui-ixdf-review` (WHY UI) → `design-ux-nielsen-review` (WHY UX) 순으로 실행 시 가장 넓은 커버리지 확보.

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인 (별도 references 디렉터리 없음)
- 방법론 출처:
  - **Checklist Design** — https://www.checklist.design/ (56 카탈로그 기반 항목)
  - **UX/UI Audit Design Review Template** — Figma Community File 1571820850139389284 https://www.figma.com/community/file/1571820850139389284/
  - **Maze 7-step UX Audit** — https://maze.co/collections/ux-ui-design/ux-audit/
- stat-front 적용 대상 페이지: login, signup, store-manage, account-setting, AG Grid 테이블 컴포넌트
- 짝 WHY 스킬: `design-ui-ixdf-review` · `design-ui-nielsen-review` · `design-ui-lawsofux-review` · `design-ui-polish-review`
- 짝 flow 스킬: `design-ux-flow-review` (step-level 구조 분석)
- 코멘트 부착: `annotate-design`
