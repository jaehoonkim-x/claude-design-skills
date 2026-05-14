# Ecommerce Conversion Rubric

Baymard Institute UX 리서치 기반 6개 차원 × 7개 화면 타입 평가 rubric. 정적 디자인 프레임 분석용.

## Severity 가이드

- **critical** — cart abandonment 직접 유발. Baymard 리서치에서 abandonment top-10 원인.
- **warning** — conversion 측정 가능한 마찰. 사용자 task 완료율 저하.
- **info** — best practice 미충족. 즉시 conversion 영향은 작지만 폴리시 영향.

## 점수 가이드 (차원별 0-10)

- 10 — 모든 체크리스트 통과
- 8-9 — info 위반만
- 6-7 — warning 1-2건
- 4-5 — warning 3+ 또는 critical 1건
- 0-3 — critical 2+건

## 화면 타입 × 적용 차원 매트릭스

| 화면 \ 차원 | Form | Filter | Checkout | Cart | Trust | Structure |
|------------|------|--------|----------|------|-------|-----------|
| Homepage   | -    | -      | -        | -    | ✓     | ✓         |
| PLP        | -    | ✓      | -        | -    | -     | ✓         |
| PDP        | -    | -      | -        | ✓(cta) | ✓   | ✓         |
| Cart       | -    | -      | ✓(handoff) | ✓ | ✓     | ✓         |
| Checkout   | ✓    | -      | ✓        | -    | ✓     | ✓         |
| Form       | ✓    | -      | -        | -    | -     | -         |
| Confirmation | -  | -      | -        | -    | ✓     | ✓         |

N/A 차원: 화면 타입에 해당 안 되면 점수표 `N/A`.

---

## 차원 1 — Form Usability

**적용**: Checkout, Form

### 체크리스트

| ID | 항목 | 통과 기준 | severity |
|----|-----|---------|---------|
| F1 | 필드 최소화 | 결제 단계 전체 필드 ≤ 7개 (이름·이메일·주소·결제). Baymard 평균은 23.48 으로 과다. | critical (12+ 시) |
| F2 | 라벨 영구 노출 | placeholder 단독 X. float-label 또는 위/외부 라벨. | warning |
| F3 | 입력 타입 정확 | email/tel/number 타입 (모바일 키보드). 우편번호 numeric. | warning |
| F4 | 자동완성 속성 | `autocomplete="given-name"` 등 표준 토큰. 주소 자동완성 가능. | warning |
| F5 | 인라인 검증 | blur 시 검증 + 명확한 에러 메시지. submit 시 오류 필드 스크롤. | critical (검증 없음 시) |
| F6 | 옵션/필수 명시 | (선택) 라벨 명시. 별표(*)만으로 부족. | info |
| F7 | 단일 칼럼 | 데스크톱도 폼은 단일 칼럼 (이름·성 분리는 예외). | warning |
| F8 | 라디오/체크박스 영역 | 라벨 전체 클릭 가능. 터치 영역 ≥ 44×44px. | warning |
| F9 | 비밀번호 정책 노출 | 입력 전부터 규칙 표시. 보기 토글 제공. | info |
| F10 | 주소 = 배송지 default 체크 | 결제지 = 배송지 기본 체크박스. | warning |

### Baymard 참고
- https://baymard.com/blog/checkout-flow-average-form-fields
- https://baymard.com/blog/inline-form-validation

---

## 차원 2 — Product Filtering

**적용**: PLP

### 체크리스트

| ID | 항목 | 통과 기준 | severity |
|----|-----|---------|---------|
| FL1 | 카테고리별 필터 노출 | 카테고리 진입 시 해당 facet 자동 노출 (예: 신발 → 사이즈). | critical (없음 시) |
| FL2 | 다중 선택 facet | 한 facet 내 여러 값 동시 선택 가능 (브랜드 A+B). | warning |
| FL3 | 적용 필터 결과 수 | facet 옆 (n) 카운트. 0건은 비활성/회색. | info |
| FL4 | 적용된 필터 가시화 | 결과 상단에 적용 필터 칩(chip) + 개별 해제. | warning |
| FL5 | "전체 해제" | 적용된 필터 전체 해제 1클릭. | info |
| FL6 | 가격 범위 슬라이더 | 슬라이더 + 직접 입력 2-way. min/max 명시. | info |
| FL7 | 카테고리-aware 정렬 | 정렬 옵션 카테고리에 맞춤 (인기·신상·가격·리뷰). | info |
| FL8 | 결과 0건 안내 | "결과 없음" + 필터 완화 제안 + CTA. | warning |
| FL9 | 모바일 필터 sticky CTA | 필터 시트 닫기 + "n개 결과 보기" 버튼 sticky. | warning |
| FL10 | 적용 즉시 반영 | "적용" 버튼 없이 클릭 즉시 반영 (또는 명시적 토글). | info |

### Baymard 참고
- https://baymard.com/blog/ecommerce-filtering-ui-design
- https://baymard.com/research/category-navigation

---

## 차원 3 — Checkout Flow

**적용**: Cart(handoff), Checkout

### 체크리스트

| ID | 항목 | 통과 기준 | severity |
|----|-----|---------|---------|
| C1 | 게스트 결제 | "게스트로 계속" 1차 액션. 강제 가입 금지. | **critical** (없음 시) — Baymard #2 abandonment 원인 |
| C2 | 단계 명시 | 진행 표시(stepper) 또는 단일 페이지. 현재 단계 강조. | warning |
| C3 | 단계 수 합리 | 정보 입력 → 배송 → 결제 → 검토 ≤ 4 단계. 단일 페이지도 OK. | warning |
| C4 | 뒤로 가기 가능 | 이전 단계 수정 가능. 데이터 보존. | critical |
| C5 | 주문 요약 sticky | 우측/하단 주문 요약(품목·소계·배송·세금·총액) 항상 노출. | warning |
| C6 | 가격 분해 투명 | 소계·배송비·세금·할인·총액 각 라인. 숨겨진 비용 X. | **critical** — Baymard #1 abandonment 원인 (48%) |
| C7 | 쿠폰/포인트 자리 | 적용 필드 항상 노출 또는 토글. 적용 후 즉시 반영. | info |
| C8 | 카드 입력 UX | 카드번호 4자리 자동 분리. CVC 도움말. 카드 종류 아이콘. | warning |
| C9 | 에러 후 데이터 보존 | 결제 실패 시 입력값 유지. 카드 정보 제외. | critical |
| C10 | 결제 버튼 라벨 | "결제 진행" 보다 "₩42,000 결제하기" 명시 라벨. | info |

### Baymard 참고
- https://baymard.com/lists/cart-abandonment-rate
- https://baymard.com/blog/checkout-usability

---

## 차원 4 — Cart UX

**적용**: PDP(Add CTA), Cart

### 체크리스트

| ID | 항목 | 통과 기준 | severity |
|----|-----|---------|---------|
| CT1 | Add to Cart 명확 | PDP 1차 CTA 단일·고대비. "장바구니 담기" 명시. | warning |
| CT2 | 추가 후 피드백 | 미니카트 슬라이드 또는 명시적 토스트. 자동 페이지 이동 신중. | warning |
| CT3 | 수량 ±/직접 입력 | 카트에서 수량 조정 ±/직접 입력 둘 다. | info |
| CT4 | 항목 제거 1클릭 | × 또는 "삭제" 1클릭. 실수 시 실행취소(undo). | warning |
| CT5 | 항목 썸네일 | 카트 라인에 제품 이미지·변형(색/사이즈) 표시. | info |
| CT6 | 추정 배송비 노출 | 카트 단계에서 우편번호 입력 → 배송비 추정. 결제 직전까지 숨김 X. | **critical** — Baymard top-3 abandonment 원인 |
| CT7 | 재고/배송 일정 | 라인별 "재고 있음" / 예상 도착일. | info |
| CT8 | 빈 카트 안내 | 빈 카트 상태에 추천 제품/카테고리 CTA. | info |
| CT9 | 저장(찜) | "나중에 구매" 또는 위시리스트 이동. 게스트도 가능 (세션). | info |
| CT10 | 체크아웃 진입 명확 | 1차 CTA "결제하기" 단일. 보조 액션과 시각 분리. | warning |

### Baymard 참고
- https://baymard.com/lists/cart-abandonment-rate
- https://baymard.com/research/checkout-flow

---

## 차원 5 — Trust Signals

**적용**: Homepage, PDP, Cart, Checkout, Confirmation

### 체크리스트

| ID | 항목 | 통과 기준 | severity |
|----|-----|---------|---------|
| T1 | 보안 시그널 | 결제 단계 SSL/카드 브랜드 보안 배지. 자물쇠 아이콘. | warning |
| T2 | 반품/환불 정책 | PDP·카트·체크아웃 어디서나 1-2 클릭 접근. 기간·조건 명시. | warning |
| T3 | 배송 정책 | 배송 기간·비용·국제 배송 여부 PDP 가시화. | info |
| T4 | 고객 리뷰 | PDP 평균 별점·리뷰 수·정렬. 별점 단독 부족. | warning |
| T5 | 연락처 노출 | 푸터 또는 도움말에 전화/이메일/채팅. 결제 단계에서도 접근. | info |
| T6 | 회사 정보 | 회사명·주소·사업자번호 푸터. (KR: 통신판매업 신고번호) | info |
| T7 | FAQ/도움말 | 결제·배송·반품 FAQ 1-2 클릭. | info |
| T8 | 결제 수단 다양성 | 카드 외 간편결제(카카오·네이버·페이팔 등). PDP 아래 결제 옵션 미리보기. | info |
| T9 | 가격 신뢰 | 정가/할인가 명시. 가격 변동 시 이력. 최저가 보장 등. | info |
| T10 | 주문 확인 명료 | Confirmation 에 주문번호·결제 내역·다음 단계(배송 추적·이메일 발송) 명시. | warning (Confirmation 한정) |

### Baymard 참고
- https://baymard.com/research/checkout-usability
- https://baymard.com/blog/site-seal-trust

---

## 차원 6 — Page Structure

**적용**: 전체

### 체크리스트

| ID | 항목 | 통과 기준 | severity |
|----|-----|---------|---------|
| S1 | 검색 진입 | 헤더 상단 검색바 항상 노출. 모바일은 검색 아이콘 → 즉시 입력. | warning (Homepage/PLP 필수) |
| S2 | 카테고리 메뉴 | 메가메뉴 또는 카테고리 그리드. 5-7개 1차 카테고리. | warning |
| S3 | 빵부스러기(breadcrumb) | PLP/PDP 에 breadcrumb 노출. 클릭 가능. | info |
| S4 | 로고 → 홈 | 로고 클릭 시 홈. 좌측 상단 관행. | info |
| S5 | 장바구니 아이콘 | 헤더 우측 항상 노출 + 수량 배지. | warning |
| S6 | PDP 이미지 갤러리 | 다각도·줌·변형(색)별 이미지 전환. | warning |
| S7 | PDP 변형 선택 명확 | 사이즈/색 선택 시 시각 피드백. 재고 없음 회색. | warning |
| S8 | PDP "관련 제품" | 상세 아래 관련/함께 구매. 비추천 자동 무관 제품 X. | info |
| S9 | 페이지 1차 CTA 단일 | 한 페이지 위 1차 CTA 1개 (위계 명확). | warning |
| S10 | 푸터 정보 밀도 | 푸터에 도움말·정책·연락처·SNS·결제 수단 그룹화. | info |

### Baymard 참고
- https://baymard.com/learn/ux-design-principles
- https://baymard.com/research/homepage-design

---

## Top-N 우선순위 알고리즘

1. 모든 critical 우선 (차원 가중치: checkout > form > cart > filter > trust > structure)
2. critical 부족 시 warning 으로 채움
3. 동률 시: 결제 경로 상 화면 우선 (Cart > Checkout > Form > PLP > PDP > Homepage > Confirmation)
4. Top-5 까지. 5개 미만이면 발견 만큼만.

## 보고서 출력 규약

- finding 1건 = 1 항목 ID 대응. 1 항목 = 1 finding 한도.
- evidence 는 노드 경로 + 측정 수치 (예: "Header > SearchInput height 28px")
- fix 는 즉시 적용 가능한 1-2문장. "검토 필요" 같은 모호 액션 금지.
- Baymard 출처 링크는 각 finding 의 차원에 1회 첨부 (위 표 참조).
