---
name: design-ux-ecommerce-review
description: Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Baymard Institute 이커머스 UX 원칙 5개 카테고리(Form Usability / Product Filtering / Checkout Flow / Cart UX / Trust Signals)로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. Conversion Risk Score(A-F) + Cart Abandonment 위험도 헤드라인 포함. 사용자가 "Baymard 이커머스 UX (Form/Filter/Checkout/Cart/Trust) 리뷰", "이커머스 UX 검토", "체크아웃 UX 리뷰", "폼 usability 평가", "/design-ux-ecommerce-review" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 이커머스 UX 기반 리뷰를 요청할 때 사용.
---

# design-ux-ecommerce-review

Baymard Institute 의 이커머스 UX 리서치(cart abandonment, checkout flow, form usability, product filtering, trust signals)를 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 화면이 이커머스 conversion 을 막는 UX 패턴을 포함하는가? cart abandonment 위험 어디?"

## 평가 항목 (5개 카테고리)

### 1. Form Usability
필드 수·검증 UX·라벨 위치·에러 회복에 관한 10개 체크리스트 항목:
- **F1** 필드 최소화 — 결제 단계 전체 필드 ≤ 7개. 12개 이상은 critical.
- **F2** 라벨 영구 노출 — placeholder 단독 금지. float-label 또는 위치 고정 라벨.
- **F3** 입력 타입 정확 — email/tel/number 타입 (모바일 키보드 최적화). 우편번호 numeric.
- **F4** 자동완성 속성 — `autocomplete="given-name"` 등 표준 토큰. 주소 자동완성 지원.
- **F5** 인라인 검증 — blur 시 검증 + 명확한 에러 메시지. submit 시 오류 필드 스크롤. 검증 없음 = critical.
- **F6** 옵션/필수 명시 — (선택) 라벨 명시. 별표(*) 단독 부족.
- **F7** 단일 칼럼 — 데스크톱도 폼은 단일 칼럼 (이름·성 분리는 예외).
- **F8** 라디오/체크박스 영역 — 라벨 전체 클릭 가능. 터치 영역 ≥ 44×44px.
- **F9** 비밀번호 정책 노출 — 입력 전부터 규칙 표시. 보기 토글 제공.
- **F10** 주소 = 배송지 default 체크 — 결제지 = 배송지 기본 체크박스.

### 2. Product Filtering
facet 노출·다중 선택·결과 수 표시에 관한 10개 체크리스트 항목:
- **FL1** 카테고리별 필터 노출 — 카테고리 진입 시 해당 facet 자동 노출. 없음 = critical.
- **FL2** 다중 선택 facet — 한 facet 내 여러 값 동시 선택 가능.
- **FL3** 적용 필터 결과 수 — facet 옆 (n) 카운트. 0건은 비활성/회색.
- **FL4** 적용된 필터 가시화 — 결과 상단에 적용 필터 칩(chip) + 개별 해제.
- **FL5** "전체 해제" — 적용된 필터 전체 해제 1클릭.
- **FL6** 가격 범위 슬라이더 — 슬라이더 + 직접 입력 2-way. min/max 명시.
- **FL7** 카테고리-aware 정렬 — 정렬 옵션 카테고리에 맞춤 (인기·신상·가격·리뷰).
- **FL8** 결과 0건 안내 — "결과 없음" + 필터 완화 제안 + CTA.
- **FL9** 모바일 필터 sticky CTA — 필터 시트 닫기 + "n개 결과 보기" 버튼 sticky.
- **FL10** 적용 즉시 반영 — "적용" 버튼 없이 클릭 즉시 반영 (또는 명시적 토글).

### 3. Checkout Flow
게스트 결제·단계 수·진행 표시·보안 시그널에 관한 10개 체크리스트 항목:
- **C1** 게스트 결제 — "게스트로 계속" 1차 액션. 강제 가입 금지. 없음 = critical (Baymard #2 abandonment 원인).
- **C2** 단계 명시 — 진행 표시(stepper) 또는 단일 페이지. 현재 단계 강조.
- **C3** 단계 수 합리 — 정보 입력 → 배송 → 결제 → 검토 ≤ 4단계.
- **C4** 뒤로 가기 가능 — 이전 단계 수정 가능. 데이터 보존. 없음 = critical.
- **C5** 주문 요약 sticky — 우측/하단 주문 요약(품목·소계·배송·세금·총액) 항상 노출.
- **C6** 가격 분해 투명 — 소계·배송비·세금·할인·총액 각 라인. 숨겨진 비용 금지. 없음 = critical (Baymard #1 abandonment 원인, 48%).
- **C7** 쿠폰/포인트 자리 — 적용 필드 항상 노출 또는 토글. 적용 후 즉시 반영.
- **C8** 카드 입력 UX — 카드번호 4자리 자동 분리. CVC 도움말. 카드 종류 아이콘.
- **C9** 에러 후 데이터 보존 — 결제 실패 시 입력값 유지. 카드 정보 제외. 없음 = critical.
- **C10** 결제 버튼 라벨 — "결제 진행" 보다 "₩42,000 결제하기" 명시 라벨.

### 4. Cart UX
가격 투명성·배송비/세금 노출·수정 가능성에 관한 10개 체크리스트 항목:
- **CT1** Add to Cart 명확 — PDP 1차 CTA 단일·고대비. "장바구니 담기" 명시.
- **CT2** 추가 후 피드백 — 미니카트 슬라이드 또는 명시적 토스트.
- **CT3** 수량 ±/직접 입력 — 카트에서 수량 조정 ±/직접 입력 둘 다.
- **CT4** 항목 제거 1클릭 — × 또는 "삭제" 1클릭. 실수 시 실행취소(undo).
- **CT5** 항목 썸네일 — 카트 라인에 제품 이미지·변형(색/사이즈) 표시.
- **CT6** 추정 배송비 노출 — 카트 단계에서 우편번호 입력 → 배송비 추정. 없음 = critical (Baymard top-3 abandonment 원인).
- **CT7** 재고/배송 일정 — 라인별 "재고 있음" / 예상 도착일.
- **CT8** 빈 카트 안내 — 빈 카트 상태에 추천 제품/카테고리 CTA.
- **CT9** 저장(찜) — "나중에 구매" 또는 위시리스트 이동. 게스트도 가능 (세션).
- **CT10** 체크아웃 진입 명확 — 1차 CTA "결제하기" 단일. 보조 액션과 시각 분리.

### 5. Trust Signals
보안 배지·리뷰·반품 정책·연락처에 관한 10개 체크리스트 항목:
- **T1** 보안 시그널 — 결제 단계 SSL/카드 브랜드 보안 배지. 자물쇠 아이콘.
- **T2** 반품/환불 정책 — PDP·카트·체크아웃 어디서나 1-2 클릭 접근. 기간·조건 명시.
- **T3** 배송 정책 — 배송 기간·비용·국제 배송 여부 PDP 가시화.
- **T4** 고객 리뷰 — PDP 평균 별점·리뷰 수·정렬. 별점 단독 부족.
- **T5** 연락처 노출 — 푸터 또는 도움말에 전화/이메일/채팅. 결제 단계에서도 접근.
- **T6** 회사 정보 — 회사명·주소·사업자번호 푸터. (KR: 통신판매업 신고번호)
- **T7** FAQ/도움말 — 결제·배송·반품 FAQ 1-2 클릭.
- **T8** 결제 수단 다양성 — 카드 외 간편결제(카카오·네이버·페이팔 등). PDP 아래 결제 옵션 미리보기.
- **T9** 가격 신뢰 — 정가/할인가 명시. 가격 변동 시 이력. 최저가 보장 등.
- **T10** 주문 확인 명료 — Confirmation 에 주문번호·결제 내역·다음 단계(배송 추적·이메일 발송) 명시.

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 이커머스 UX 리뷰(폼·필터·체크아웃·카트·신뢰 시그널)를 요청할 때
- 출시 전 이커머스 사이트/앱의 cart abandonment 위험 진단이 필요할 때
- Checkout Flow, Form Usability, Cart UX 등 conversion 핵심 UX 화면을 정량 진단하고 싶을 때

## Do Not Use

- **시각 폴리시 평가** (제품 카드 레이아웃·이미지 비율·CTA 위계 등) → `design-ui-ecommerce-review`
- 일반 UX 법칙 평가(Hick's Law, Fitts's Law 등) → `design-ux-lawsofux-review`
- Nielsen 10 휴리스틱 → `design-ux-nielsen-review`
- IxDF UX factors → `design-ux-ixdf-review`
- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 이커머스가 아닌 SaaS/콘텐츠 사이트 — 본 스킬 rubric 부적합
- 인터랙션 흐름/애니메이션/성능 측정 — 단일 프레임 정적 분석 한정

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` | "Figma MCP 가 연결되어 있지 않습니다. https://claude.ai 의 Figma 연동을 활성화하거나 figma 데스크탑 앱의 Dev Mode MCP 를 설치한 뒤 다시 시도해주세요." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: 첫 단계에서 ToolSearch 로 해당 prefix 의 도구를 조회. 결과가 비어 있으면 위 안내를 출력하고 즉시 종료. 어떤 코드도 작성하지 않는다.

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

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 종료.

### Step 3 — 디자인 데이터 수집 (deep)

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 로 프레임 구조 파악
   - nodeId 미지정 시: 현재 선택된 프레임 자동 감지
2. 각 frame 에 대해:
   - `mcp__claude_ai_Figma__get_design_context(fileKey, nodeId=frame.id)` 호출
   - `mcp__claude_ai_Figma__get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별
   - 선택 비어있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 선택 frame:
   - `mcp__pencil__batch_get(node_ids=[frame_id])` deep 노드 트리
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(node_id=frame_id)` 이미지 1장

### Step 4 — 프레임 타입 자동 분류

각 frame 의 노드 트리/이름/스크린샷으로부터 이커머스 화면 타입 자동 추론:

- **Homepage** — 헤로 + 카테고리 그리드 + 검색 진입
- **PLP** (Product Listing Page) — 그리드 + 필터 사이드바 + 정렬
- **PDP** (Product Detail Page) — 제품 이미지 + 변형 선택 + Add to Cart
- **Cart** — 항목 리스트 + 수량/가격 + 체크아웃 진입
- **Checkout** — 폼 (배송/결제) + 단계 표시 + 주문 요약
- **Form** (회원가입/로그인/주소 입력 단일 화면) — 폼 중심
- **Confirmation** — 주문 완료 + 영수증 + 다음 액션
- **Other** — 위에 해당 없음 (review 가능하지만 rubric 일부만 적용)

분류 근거를 보고서 메타에 기록 (예: "PLP — 좌측 facet 필터 + 그리드 12개 + 정렬 드롭다운 검출").

### Step 5 — 평가 rubric 로드

`references/ecommerce-rubric.md` 를 Read tool 로 읽는다. 5개 UX 차원(Form Usability, Product Filtering, Checkout Flow, Cart UX, Trust Signals) × 화면 타입별 체크리스트 + severity 가이드를 컨텍스트에 적재. UI 차원(Product Card, PDP visual, PLP visual)은 본 스킬 범위 외.

### Step 6 — 프레임별 평가 + 보고서 생성 (각 프레임마다 반복)

각 frame 마다:

1. **frame-slug 계산**: frame.name kebab-case. 한글이면 음역 또는 nodeId 끝 8자
2. **날짜 토큰**: `YYYYMMDD-HHmm` (KST 24H)
3. **출력 경로**: `./design-reviews/design-ux-ecommerce-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
4. **화면 타입별 rubric 적용**: 분류된 타입의 체크리스트 항목 평가
   - 각 항목: 통과/위반/N/A 판정 + 위반 시 severity (critical/warning/info) + evidence(노드 경로) + fix
   - 차원별 점수 0-10
5. **Conversion Risk Score 산출**:
   - 5개 UX 차원 평균 → 0-100 변환 → A(90+)/B(75+)/C(60+)/D(45+)/F(<45)
   - critical 1건 = 자동 D 이하
6. **Cart Abandonment 위험도** 한 줄 헤드라인:
   - "높음" — critical 2건+ 또는 Checkout 차원 D/F
   - "중간" — warning 다수
   - "낮음" — 통과 위주
7. **Top-5 우선순위 산출**:
   - checkout > form > cart > filter > trust 순 가중치
   - critical 우선, 동률 시 conversion 영향 큰 항목
8. **보고서 작성** (아래 구조)

### Step 7 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들)
- 각 프레임: 화면 타입, Conversion Risk Score(A-F), Cart Abandonment 위험도, critical/warning 건수

## 보고서 구조 (한국어)

```markdown
# 이커머스 UX 리뷰: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 화면 타입 추론: {Homepage | PLP | PDP | Cart | Checkout | Form | Confirmation | Other}
- 분류 근거: {짧은 설명}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로}
- 평가 스킬: design-ux-ecommerce-review (Baymard UX 5개 카테고리)

## 헤드라인
- **Conversion Risk Score**: {A | B | C | D | F} ({score}/100)
- **Cart Abandonment 위험도**: {높음 | 중간 | 낮음}
- critical: {n}건, warning: {n}건, info: {n}건

## 차원별 점수

| # | 차원 | 점수 | 비고 |
|---|------|------|------|
| 1 | Form Usability | 7/10 | warning 2건 |
| 2 | Product Filtering | N/A | PDP 라 미적용 |
| 3 | Checkout Flow | 4/10 | critical 1건 (게스트 결제 부재) |
| 4 | Cart UX | 8/10 | - |
| 5 | Trust Signals | 6/10 | warning 1건 |

## Findings

### {차원명} — {finding 제목} — score: {N}
- **severity**: critical | warning | info
- **dimension**: {Form Usability | Product Filtering | Checkout Flow | Cart UX | Trust Signals}
- **evidence**: `{노드 경로}` — {구체 수치/관찰}
- **baymard insight**: {Baymard 리서치 근거}
- **fix**: {즉시 적용 가능한 1-2문장 액션}
- **참고**: {https://baymard.com/...}

{위반/개선점이 있는 항목만 나열}

## Top-5 우선순위

1. **{차원} — {항목 제목} (critical)** — {한 줄 액션}
2. **{차원} — {항목 제목} (warning)** — {한 줄 액션}
...

## N/A 항목 (적용 보류)

- {차원명}: {이유}
```

## 인자

```
/design-ux-ecommerce-review <Figma URL | .pen path>
```

- 위치 인자 1개. 멀티 프레임은 Figma/Pencil **현재 선택** 자동 감지
- 옵션 인자 없음 (디폴트 우선)

## 예시

### 예시 1 — Figma URL (Checkout 단일 프레임)
```
/design-ux-ecommerce-review https://www.figma.com/design/abc123XYZ/ShopApp?node-id=42-1024
```

→ Figma MCP 체크 → metadata + design_context + screenshot → 화면 타입 "Checkout" 자동 분류 → UX rubric 적용 → `./design-reviews/design-ux-ecommerce-review-checkout-20260514-1430.md`

### 예시 2 — Pencil 멀티 프레임 (PLP + Cart)
```
/design-ux-ecommerce-review ~/Documents/shop.pen
```

→ Pencil MCP 체크 → 선택된 2 프레임 자동 분류 → 2개 파일 생성:
- `./design-reviews/design-ux-ecommerce-review-plp-20260514-1430.md`
- `./design-reviews/design-ux-ecommerce-review-cart-20260514-1430.md`

### 예시 3 — MCP 미연결
```
/design-ux-ecommerce-review ~/Documents/shop.pen
```

→ ToolSearch 로 `mcp__pencil__*` 0건 → 안내 후 종료

## 출력 규약

- 사용자 텍스트: **한국어**
- 차원·화면 타입 이름: 영어 원어 (Checkout Flow, PLP, PDP 등)
- finding 헤더: `### {차원명} — {finding 제목} — score: {N}` (annotate-design 호환)
- finding 의 evidence/fix: 구체 노드명·수치·액션
- Baymard 참고 링크는 각 finding 의 차원에 1회 첨부
- 보고서: 한 프레임당 한 파일
- 출력 경로: `./design-reviews/design-ux-ecommerce-review-{frame-slug}-{YYYYMMDD-HHmm}.md`

## Non-Goals

- Figma/Pencil 안 코멘트 직접 게시 — 별도 스킬
- 인터랙션/애니메이션 분석 — 정적 한정
- 자동 수정/리팩터 — 리뷰만
- 라이브 사이트 측정 (실제 abandonment 률) — 별도 분석 도구
- 이커머스 아닌 화면 — rubric 부적합 명시 후 부분 적용
- **시각 폴리시 평가** (Product Card 밀도·이미지 비율·CTA 위계 등) — `design-ui-ecommerce-review` 사용

## References

- 평가 rubric 전문: `references/ecommerce-rubric.md`
- 원본 출처: https://baymard.com/learn/ux-design-principles, https://baymard.com/research
- UI 시각 폴리시 평가: `design-ui-ecommerce-review`
