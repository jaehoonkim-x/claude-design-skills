---
name: design-ui-ecommerce-review
description: Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Baymard Institute 이커머스 UI 시각 폴리시 3개 카테고리(Product Card visual / PDP visual / Homepage·PLP visual)로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. conversion 보다 시각 폴리시 관점(제품 카드 레이아웃·이미지 비율·CTA 위계). 사용자가 "Baymard 이커머스 UI (Product Card/PDP/PLP) 리뷰", "제품 카드 UI 평가", "PDP 시각 폴리시 검토", "이커머스 UI 리뷰", "/design-ui-ecommerce-review" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 이커머스 UI 시각 기반 리뷰를 요청할 때 사용.
---

# design-ui-ecommerce-review

Baymard Institute 의 이커머스 UI 시각 가이드라인을 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다. 평가 렌즈 = "conversion 보다 시각 폴리시 — 이 화면의 제품 카드 레이아웃, 이미지 비율, CTA 위계, 정보 그루핑이 쇼핑 맥락에서 적절한가?" 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

## 평가 항목 (3개 카테고리)

### 1. Product Card visual
밀도·이미지 비율·가격 위계에 관한 체크리스트:
- **PC1** 이미지 비율 고정 — 카드 이미지 비율 일관성 (3:4 또는 1:1 권장). 혼합 비율은 그리드 리듬 파괴.
- **PC2** 가격 위계 명확 — 정가/할인가 시각 분리 (취소선·컬러). 할인율 표시 위치 일관성.
- **PC3** 정보 밀도 적정 — 카드 내 요소: 이미지·제품명·가격·평점·CTA. 5개 이상은 과잉.
- **PC4** 제품명 줄 수 고정 — 카드 정렬을 위한 2줄 클램프(clamp). 가변 높이로 그리드 틀어짐 방지.
- **PC5** CTA 가시성 — "장바구니" 버튼: hover/tap 시 노출 또는 항상 노출. 숨김은 discoverability 저하.
- **PC6** 배지(badge) 계층 — "신상" / "SALE" / "품절" 배지 1개 우선. 다중 배지 충돌 방지.
- **PC7** 색상 스와치 — 변형 색 있을 시 카드 내 스와치 미리보기. 3개 초과는 "+n" 처리.
- **PC8** 평점 시각화 — 별점 아이콘 + 숫자(리뷰 수). 별점 단독 부족.
- **PC9** 카드 그림자/경계 — 카드 구분: 그림자 또는 border 또는 배경 대비. 혼용 금지.
- **PC10** 로딩 스켈레톤 — 이미지 영역 aspect-ratio 유지 스켈레톤 표현 (이미지 로드 전 레이아웃 시프트 방지).

### 2. PDP visual
히어로·갤러리·CTA 위계·정보 그루핑에 관한 체크리스트:
- **PD1** 히어로 이미지 크기 — 뷰포트 대비 50% 이상. 소형 썸네일 메인 노출은 신뢰 저하.
- **PD2** 갤러리 구성 — 서브 썸네일 ≥ 3장. 다각도·착용샷·디테일 포함. 썸네일 클릭 시 메인 전환.
- **PD3** CTA 위계 단일 — "장바구니 담기" 1차. "바로 구매" 있을 시 2차로 시각 분리 (면 vs 선 버튼).
- **PD4** 제품명 + 가격 상단 그루핑 — 이미지 우측 또는 이미지 아래 즉시 노출. 스크롤 없이 확인 가능.
- **PD5** 변형 선택 레이블 — 현재 선택된 색/사이즈 텍스트로 명시 (예: "색상: 네이비"). 아이콘 단독 부족.
- **PD6** 재고 상태 시각화 — "재고 있음" / "품절" 선택 UI 내 시각화. 품절 옵션 회색 처리.
- **PD7** 정보 그루핑 섹션화 — 상세 설명·사이즈가이드·반품정책·리뷰를 섹션 헤더로 분리. 연속 텍스트 지양.
- **PD8** 리뷰 섹션 위치 — 상세 설명 아래 배치. 스크롤 없이 평점 요약 확인 가능 (앵커 또는 요약 위치).
- **PD9** 추천 제품 위치 — "함께 구매" / "관련 제품" 섹션 하단 배치. CTA 영역 침범 금지.
- **PD10** 모바일 sticky CTA — 스크롤 시 "장바구니 담기" 하단 고정 바. 갤러리 탐색 중 CTA 접근 유지.

### 3. Homepage/PLP visual
그리드·카테고리 카드·시각 가중치에 관한 체크리스트:
- **HP1** 그리드 컬럼 일관성 — 데스크톱 4컬럼 / 모바일 2컬럼 권장. 홀수 컬럼은 마지막 행 여백 발생.
- **HP2** 카테고리 카드 이미지 — 카테고리 그리드 이미지 비율 통일. 라이프스타일 이미지 + 카테고리명 오버레이.
- **HP3** 시각 가중치 계층 — 히어로 > 카테고리 그리드 > 제품 그리드 순 크기/대비 위계. 역전 금지.
- **HP4** 검색 진입 노출 — 헤더 검색바 항상 노출. 아이콘 전용이면 탭 즉시 입력 전환.
- **HP5** 프로모션 배너 밀도 — 히어로 영역 내 CTA ≤ 2개. 배너 중첩은 주의 분산.
- **HP6** PLP 정렬 컨트롤 위치 — 필터/정렬 바 그리드 상단 sticky. 스크롤 후 접근 불편 방지.
- **HP7** 카드 행간 여백 — 카드 사이 gap ≥ 12px (모바일 8px 최소). 밀집 그리드는 선택 오류 유발.
- **HP8** 타이포그래피 계층 — 페이지 제목 > 섹션 헤더 > 카드 제목 > 메타 정보. 동일 크기 혼용 금지.
- **HP9** 카테고리 메뉴 1차 항목 수 — 5-7개. 8개 이상은 선택 오버로드. 모바일은 가로 스크롤 허용.
- **HP10** 빈 상태 시각화 — PLP 검색 결과 0건: 일러스트 + 안내 문구 + 대안 CTA. 빈 레이아웃 금지.

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 이커머스 시각 폴리시 리뷰(제품 카드·PDP·홈페이지·PLP)를 요청할 때
- 제품 카드 레이아웃, 이미지 비율, CTA 위계, 정보 그루핑 등 시각 품질 진단이 필요할 때
- 그리드 일관성, 카테고리 카드 비율, 시각 가중치 계층 등 UI 폴리시 점검이 필요할 때

## Do Not Use

- **UX conversion 평가** (Form Usability·Product Filtering·Checkout Flow·Cart UX·Trust Signals) → `design-ux-ecommerce-review`
- 일반 시각 폴리시(타이포·컬러·스페이싱·브랜딩) → `design-ui-polish-review`
- 게슈탈트·시각 법칙(Proximity·Similarity 등) → `design-ui-lawsofux-review`
- Nielsen Aesthetic 휴리스틱 → `design-ui-nielsen-review`
- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 이커머스가 아닌 SaaS/콘텐츠 사이트 — 본 스킬 rubric 부적합
- 인터랙션/애니메이션 분석 — 단일 프레임 정적 분석 한정

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

- **Homepage** — 히어로 + 카테고리 그리드 + 검색 진입
- **PLP** (Product Listing Page) — 그리드 + 필터 사이드바 + 정렬
- **PDP** (Product Detail Page) — 제품 이미지 갤러리 + 변형 선택 + Add to Cart
- **Other** — 위에 해당 없음 (본 스킬의 3개 카테고리 중 일부만 적용)

분류 근거를 보고서 메타에 기록 (예: "PLP — 좌측 facet 필터 + 2×4 제품 카드 그리드 + 정렬 드롭다운 검출").

> **N/A 처리**: Cart/Checkout/Form/Confirmation 타입은 본 스킬의 UI 카테고리(Product Card, PDP, PLP)와 직접 매핑되지 않음. 해당 화면의 UX 검토가 필요하면 `design-ux-ecommerce-review` 사용.

### Step 5 — 평가 rubric 로드

`references/ecommerce-rubric.md` 를 Read tool 로 읽는다. 3개 UI 카테고리(Product Card visual, PDP visual, Homepage/PLP visual) 체크리스트를 컨텍스트에 적재. UX 차원(Form, Filter, Checkout, Cart, Trust)은 본 스킬 범위 외.

### Step 6 — 프레임별 평가 + 보고서 생성 (각 프레임마다 반복)

각 frame 마다:

1. **frame-slug 계산**: frame.name kebab-case. 한글이면 음역 또는 nodeId 끝 8자
2. **날짜 토큰**: `YYYYMMDD-HHmm` (KST 24H)
3. **출력 경로**: `./design-reviews/design-ui-ecommerce-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
4. **화면 타입별 rubric 적용**: 분류된 타입에 해당하는 UI 카테고리 체크리스트 평가
   - 각 항목: 통과/위반/N/A 판정 + 위반 시 severity (critical/warning/info) + evidence(노드 경로, 수치) + fix
   - 카테고리별 점수 0-10
5. **UI 폴리시 점수 산출**:
   - 적용된 카테고리 평균 → 0-100 변환 → A(90+)/B(75+)/C(60+)/D(45+)/F(<45)
   - critical 1건 = 자동 D 이하
6. **Top-3 우선순위 산출**:
   - PDP visual > Product Card visual > Homepage/PLP visual 순 가중치 (쇼핑 결정 단계 근접도)
   - critical 우선, 동률 시 사용자 시선 집중 영역 우선
7. **보고서 작성** (아래 구조)

### Step 7 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들)
- 각 프레임: 화면 타입, UI 폴리시 점수(A-F), critical/warning 건수

## 보고서 구조 (한국어)

```markdown
# 이커머스 UI 리뷰: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 화면 타입 추론: {Homepage | PLP | PDP | Other}
- 분류 근거: {짧은 설명}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로}
- 평가 스킬: design-ui-ecommerce-review (Baymard UI 3개 카테고리)

## 헤드라인
- **UI 폴리시 점수**: {A | B | C | D | F} ({score}/100)
- critical: {n}건, warning: {n}건, info: {n}건

## 카테고리별 점수

| # | 카테고리 | 점수 | 비고 |
|---|----------|------|------|
| 1 | Product Card visual | 8/10 | warning 1건 (이미지 비율 비일관) |
| 2 | PDP visual | 5/10 | critical 1건 (히어로 이미지 소형), warning 1건 |
| 3 | Homepage/PLP visual | N/A | PDP 라 미적용 |

## Findings

### {카테고리명} — {finding 제목} — score: {N}
- **severity**: critical | warning | info
- **dimension**: {Product Card visual | PDP visual | Homepage/PLP visual}
- **evidence**: `{노드 경로}` — {구체 수치/관찰}
- **baymard insight**: {Baymard 시각 가이드라인 근거}
- **fix**: {즉시 적용 가능한 1-2문장 액션}
- **참고**: {https://baymard.com/...}

{위반/개선점이 있는 항목만 나열}

## Top-3 우선순위

1. **{카테고리} — {항목 제목} (critical)** — {한 줄 액션}
2. **{카테고리} — {항목 제목} (warning)** — {한 줄 액션}
3. **{카테고리} — {항목 제목} (info)** — {한 줄 액션}

## N/A 항목 (적용 보류)

- {카테고리명}: {이유}
```

## 인자

```
/design-ui-ecommerce-review <Figma URL | .pen path>
```

- 위치 인자 1개. 멀티 프레임은 Figma/Pencil **현재 선택** 자동 감지
- 옵션 인자 없음 (디폴트 우선)

## 예시

### 예시 1 — Figma URL (PDP 단일 프레임)
```
/design-ui-ecommerce-review https://www.figma.com/design/abc123XYZ/ShopApp?node-id=55-2048
```

→ Figma MCP 체크 → metadata + design_context + screenshot → 화면 타입 "PDP" 자동 분류 → UI rubric 적용 → `./design-reviews/design-ui-ecommerce-review-pdp-20260514-1430.md`

### 예시 2 — Pencil 멀티 프레임 (Homepage + PLP)
```
/design-ui-ecommerce-review ~/Documents/shop.pen
```

→ Pencil MCP 체크 → 선택된 2 프레임 자동 분류 → 2개 파일 생성:
- `./design-reviews/design-ui-ecommerce-review-homepage-20260514-1430.md`
- `./design-reviews/design-ui-ecommerce-review-plp-20260514-1430.md`

### 예시 3 — MCP 미연결
```
/design-ui-ecommerce-review ~/Documents/shop.pen
```

→ ToolSearch 로 `mcp__pencil__*` 0건 → 안내 후 종료

## 출력 규약

- 사용자 텍스트: **한국어**
- 카테고리·화면 타입 이름: 영어 원어 (Product Card, PDP, PLP, Homepage 등)
- finding 헤더: `### {카테고리명} — {finding 제목} — score: {N}` (annotate-design 호환)
- finding 의 evidence/fix: 구체 노드명·수치·액션 (예: `ProductCard > Image` height 200px → 3:4 비율 기준 240px 필요)
- Baymard 참고 링크는 각 finding 의 카테고리에 1회 첨부
- 보고서: 한 프레임당 한 파일
- 출력 경로: `./design-reviews/design-ui-ecommerce-review-{frame-slug}-{YYYYMMDD-HHmm}.md`

## Non-Goals

- Figma/Pencil 안 코멘트 직접 게시 — 별도 스킬
- 인터랙션/애니메이션 분석 — 정적 한정
- 자동 수정/리팩터 — 리뷰만
- **UX conversion 평가** (Form Usability, Checkout Flow, Cart UX 등) — `design-ux-ecommerce-review` 사용
- 이커머스 아닌 화면 — rubric 부적합 명시 후 부분 적용
- 일반 시각 폴리시(타이포·컬러·스페이싱·브랜딩 체계) — `design-ui-polish-review` 사용

## References

- 평가 rubric 전문: `references/ecommerce-rubric.md`
- 원본 출처: https://baymard.com/learn/ux-design-principles, https://baymard.com/research
- UX conversion 평가: `design-ux-ecommerce-review`
