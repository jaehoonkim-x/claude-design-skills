---
name: design-ux-dark-pattern-review
review-level: L2 Structure
description: "[L2 Structure] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임(또는 flow 시퀀스)을 Harry Brignull deceptive.design 12 카테고리 + 규제 리스크(GDPR/CPRA/한국 e-privacy) 기준으로 윤리 audit하여 한국어 마크다운 리포트를 생성. Ethics Health Grade(A-F) 헤드라인 + 12 패턴 ✅/❌ + 위반 시 자동 critical + 규제 매핑. design-ux-flow-review Lens D(6항목)를 12항목으로 확장한 전용 dark pattern 전문 스킬. stat-front 셀러 dashboard → 셀러 신뢰 = 핵심 → dark pattern 0건 필수. 사용자가 \"다크패턴 점검\", \"dark pattern audit\", \"dark pattern 리뷰\", \"기만 패턴 검사\", \"윤리 리뷰\", \"deceptive.design 검토\", \"/design-ux-dark-pattern-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 dark pattern 전용 audit을 요청할 때 사용."
---

# design-ux-dark-pattern-review

**Review Level**: L2 Structure — 윤리 audit 전용 (Harry Brignull deceptive.design 12 카테고리 + 규제 리스크).

Harry Brignull의 deceptive.design 12 카테고리 rubric으로 디자인 프레임/flow를 정적 분석하여 Ethics Health Grade(A-F)와 규제 리스크를 리포트로 생성한다. design-ux-flow-review Lens D(6항목)를 12항목으로 확장한 전용 스킬. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 `annotate-design` 책임.

평가 렌즈 = "이 디자인이 사용자를 의도적으로 오도하거나 자율성을 침해하는가? 규제 위반 리스크가 존재하는가?"

stat-front 셀러 dashboard 컨텍스트: **셀러 신뢰 = 핵심 자산**. dark pattern 0건이 목표. 1건 발견 = 즉시 critical.

## 평가 항목 (12 패턴)

Brignull 2023 카탈로그 기준 12개. 각 항목 ✅(위반 없음) / ❌(위반 감지) / N/A(정적 분석 불가).

| # | Pattern | 정의 | 정적 검증 |
|---|---------|------|----------|
| 1 | Comparison Prevention | 대안 비교를 어렵게 만들어 더 비싼 옵션 선택 유도 (패키지 구조 모호화, 기능 항목 누락, 가격 단위 불일치) | Yes |
| 2 | Confirmshaming | 거절 옵션 문구를 죄책감/수치심 유발로 작성 (예: "아니요, 나는 돈을 절약하고 싶지 않아요") | Yes |
| 3 | Disguised Ads | 광고/스폰서 콘텐츠를 일반 콘텐츠·네비게이션·검색 결과처럼 위장 | Yes |
| 4 | Fake Scarcity | 재고/잔여 수량을 조작 또는 과장 표시 ("단 2개 남음!", 실제 재고 무관) | Yes |
| 5 | Fake Social Proof | 조작된 리뷰·평점·"N명이 보고 있음"·구매 알림 팝업 | Yes |
| 6 | Fake Urgency | 가짜 카운트다운 타이머·"오늘만 특가"(반복 갱신)·마감 조작 | Yes |
| 7 | Forced Action | 목적 외 행동 강제 — 부가 계정·뉴스레터·앱 설치·소셜 공유 강제 등록 | Yes |
| 8 | Hard to Cancel (Roach Motel) | 가입·구독·설정 진입은 쉽고 해지·삭제·탈퇴는 의도적으로 어렵게 설계 | Yes |
| 9 | Hidden Costs | 체크아웃 마지막 단계에서 배송비·수수료·세금 등 추가 비용 노출 | Yes |
| 10 | Hidden Subscription | 무료 체험·일회성 결제로 위장하여 자동 정기구독 전환 | Yes |
| 11 | Nagging | 거절한 요청을 반복적으로 팝업·배너·알림으로 재시도 | Yes |
| 12 | Obstruction / Pre-selection / Sneaking / Trick Wording | 계정 삭제 방해(Obstruction) · 기본 동의 체크(Pre-selection) · 동의 없는 카트 추가(Sneaking) · 오해 유도 문구(Trick Wording) 복합 | Yes |

> 위반 1건 = 자동 **critical**. 12패턴 전부 ✅ = Ethics Health Grade A.

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일에서 "다크패턴 점검", "dark pattern audit", "기만 패턴", "윤리 리뷰", "deceptive.design", "/design-ux-dark-pattern-review" 를 요청할 때
- design-ux-flow-review Lens D 결과가 미흡하여 12항목 전수 audit이 필요할 때
- 신규 체크아웃·구독·가입·결제 flow 출시 전 윤리 점검이 필요할 때
- 셀러 dashboard에서 신뢰 손상 요소 전수 검사가 필요할 때
- GDPR/CPRA/한국 e-privacy 규제 준수 여부를 사전 확인해야 할 때

## Do Not Use

- 단일 프레임 UX 휴리스틱 전반 → `design-ux-nielsen-review` / `design-ux-ixdf-review`
- 다중 프레임 flow 전체 구조(IA·전환·습관) → `design-ux-flow-review`
- 시각 UI 레이어 → `design-ui-*-review`
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP가 연결되어 있지 않습니다. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 중 하나 활성화 후 재시도." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: Step 1에서 ToolSearch로 prefix 도구를 조회. 결과가 비어 있으면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + MCP 사전 체크

사용자 인자에서 입력 타입을 자동 감지:

- `figma.com/design/:fileKey/...?node-id=:nodeId` → **Figma 경로**
- `*.pen` 로컬 경로 → **Pencil 경로**
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

ToolSearch로 Prerequisites 표 기준 MCP 확인. 미연결이면 안내 출력 후 종료.

옵션 인자 처리:
- `--scope "{범위}"`: 특정 패턴 또는 섹션에 집중 (예: `--scope "결제 플로우"`)
- `--context "{비즈니스 맥락}"`: 서비스 성격 명시 (기본값: "셀러 dashboard B2B SaaS")

### Step 2 — 디자인 데이터 수집

**Figma 경로:**
1. `get_metadata(fileKey, nodeId)` 로 프레임/flow 구조 파악
2. 각 frame에 대해:
   - `get_design_context(fileKey, nodeId=frame.id, depth:8)` 로 깊은 트리 + 텍스트 노드 수집
   - `get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고 이미지 확보
3. 특히 텍스트 노드(CTA 문구·라벨·가격·알림 문구)와 체크박스·토글 기본값 집중 추출

**Pencil 경로:**
1. `open_document(path=...)` (필요 시)
2. `get_editor_state()` 로 선택 프레임 목록 확인
   - 선택 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame마다:
   - `batch_get(node_ids=[frame_id], readDepth:4)` 로 노드 트리 수집
   - `snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `get_screenshot(node_id=frame_id)` 로 이미지 확보
   - `search_all_unique_properties(node_id=frame_id, property="text")` 로 전체 텍스트 팔레트 추출

### Step 3 — 컨텍스트 분류

수집 데이터 기반 서비스 성격 분류:

- **CHECKOUT/PAYMENT**: 결제·구독·요금제 선택 flow
- **ONBOARDING/SIGNUP**: 가입·설정·동의 flow
- **DASHBOARD HUB**: 메인 대시보드·KPI·관리 화면
- **SUBSCRIPTION MANAGEMENT**: 플랜 변경·해지·갱신 flow
- **CONTENT/LISTING**: 상품·콘텐츠·광고 목록 화면
- **HYBRID**: 혼재

분류에 따른 패턴 집중도 조정:
- Checkout/Payment: Hidden Costs·Hidden Subscription·Fake Urgency·Fake Scarcity 가중↑
- Onboarding/Signup: Forced Action·Pre-selection·Confirmshaming·Nagging 가중↑
- Dashboard Hub: Disguised Ads·Fake Social Proof·Obstruction 가중↑
- Subscription Management: Hard to Cancel·Hidden Subscription·Nagging 가중↑

### Step 4 — First Impression (윤리 관점)

스크린샷 직후, 분석 전 1인칭 즉시 반응:

```
- 이 화면/flow의 전반적인 신뢰 인상: [한 문장]
- 즉시 의심이 가는 요소: [최대 3개 또는 "없음"]
- 셀러(B2B) 관점에서 가장 걱정되는 부분: [한 문장]
- 한 단어 윤리 요약: [단어]
- 인상 메모: [구체적 우려/안심 근거]
```

진단가는 헤지하지 않는다.

### Step 5 — 12 패턴 전수 평가

각 패턴마다 정밀 검사. 평가 기준 및 판정:

**판정 기준:**
- ✅ **위반 없음**: 해당 패턴 증거 없음 → score 10
- ⚠️ **경계**: 단정하기 어려우나 잠재 위험 → score 5-7, warning
- ❌ **위반 감지**: 명확한 증거 → score 0-4, **자동 critical**
- N/A: 해당 flow에 관련 UI 요소 없음 → 적용 제외

**패턴별 검사 포인트:**

**1. Comparison Prevention**
- 요금제/플랜 비교표에서 기능 행 의도적 누락 여부
- 가격 단위 불일치 (월 vs 연간, 사용자당 vs 전체)
- 경쟁 비교 차단 문구·법적 고지

**2. Confirmshaming**
- 팝업·모달의 "거절" 버튼 문구 감성 조작 여부
- "아니요, 나는 [부정적 자기서술]입니다" 패턴
- 동의/거절 버튼 계층 역전 (거절이 더 작거나 숨김)

**3. Disguised Ads**
- 광고/스폰서 배지 존재 여부 및 가시성
- 유료 노출 항목을 자연 검색/추천처럼 배치
- "추천", "인기" 라벨의 실제 기준 명시 여부

**4. Fake Scarcity**
- "N개 남음" 표시의 실시간 데이터 연결 근거
- 재고 표시 없이 시각적 희소성 암시 (빨간 텍스트, 바 그래프)
- 반복 방문 시 동일 수치 고정 패턴

**5. Fake Social Proof**
- 리뷰 수·별점 출처 및 검증 방법 명시 여부
- "N명이 보고 있음" / "방금 N명 구매" 실시간 데이터 여부
- 유저 생성 콘텐츠 vs 큐레이션 구분 명시 여부

**6. Fake Urgency**
- 카운트다운 타이머의 만료 후 행동 (리셋되는지 확인)
- "오늘만 특가" / "한정 기간" 의 날짜 고정 vs 롤링
- FOMO 문구 빈도 및 맥락 정합성

**7. Forced Action**
- 핵심 기능 사용에 부가 정보 입력 강제 여부
- 뉴스레터·마케팅 동의 없이 진행 불가 구조
- 소셜 계정 연동 강제

**8. Hard to Cancel (Roach Motel)**
- 구독 취소·계정 삭제·서비스 해지 경로 클릭 수
- 해지 전 추가 확인 단계 수 (3단계 초과 = 위반 신호)
- 해지 버튼 위치·크기·색상 hierarchy 비대칭

**9. Hidden Costs**
- 최종 결제 화면 도달 전 총 비용 표시 여부
- 수수료·VAT·배송비 노출 단계
- "무료" 라벨 사용 후 추후 비용 발생 구조

**10. Hidden Subscription**
- "무료 체험" 종료 후 자동 결제 안내 명시 여부
- 구독 전환 시 명시적 동의 (double opt-in) 존재 여부
- 취소 방법 사전 안내 여부

**11. Nagging**
- 사용자가 닫거나 거절한 팝업·배너 재등장 구조
- 알림 권한 거절 후 재요청 횟수
- 동일 CTA의 화면 내 반복 배치 (3회 이상 = 경계)

**12. Obstruction / Pre-selection / Sneaking / Trick Wording**
- 체크박스 기본값(Pre-selection): 마케팅 동의·뉴스레터·유료 부가서비스 기본 체크
- 카트 자동 추가(Sneaking): 명시적 선택 없이 카트 항목 추가
- 계정 삭제 방해(Obstruction): 고객센터 통해서만 삭제 가능
- 오해 유도 문구(Trick Wording): "무료 업그레이드", "취소하지 않으면", 이중 부정 문구

### Step 6 — 규제 매핑

위반 감지(❌) 또는 경계(⚠️) 패턴에 대해 자동 규제 리스크 태깅:

| 패턴 | GDPR (EU) | CPRA (CA) | 한국 e-privacy |
|------|-----------|-----------|---------------|
| Comparison Prevention | — | — | 전자상거래법 §21 (소비자 오인 유발) |
| Confirmshaming | GDPR Recital 32 (자유로운 동의) | CPRA §1798.120 | 개인정보보호법 §22 (동의 자유성) |
| Disguised Ads | DSA Art.26 (광고 투명성) | FTC 가이드라인 | 표시광고법 §3 (기만적 표시) |
| Fake Scarcity | — | CA false advertising | 전자상거래법 §21 |
| Fake Social Proof | DSA Art.37 (추천 시스템 투명성) | FTC Endorsement Guide | 표시광고법 §3 |
| Fake Urgency | — | CA false advertising | 전자상거래법 §21 |
| Forced Action | GDPR Art.7 §4 (조건부 동의 금지) | CPRA §1798.121 | 개인정보보호법 §22 (최소 수집) |
| Hard to Cancel | GDPR Art.17 (삭제권) · DSA Art.14 | CPRA §1798.125 | 개인정보보호법 §36 (정정·삭제) |
| Hidden Costs | EU CRD Art.6 (정보 제공 의무) | CA auto-renewal law | 전자상거래법 §13 (청약 전 정보) |
| Hidden Subscription | EU CRD Art.22 (선택지 명시) | CA auto-renewal law §17601 | 전자상거래법 §14 (자동 결제 고지) |
| Nagging | GDPR Recital 32 | CCPA opt-out | 정보통신망법 §50 (스팸 규제) |
| Pre-selection | GDPR Recital 32 · Art.7 | CPRA | 개인정보보호법 §22 (명시적 동의) |

규제 리스크 등급:
- **HIGH**: GDPR Art.7/17/22 위반 → 과징금 최대 전 세계 매출 4% 또는 2천만 유로
- **MEDIUM**: DSA Art.26/37 · CA auto-renewal law → 행정 제재 + 집단 소송 위험
- **LOW**: 국내 전자상거래법 · 표시광고법 → 시정 명령 + 과태료

### Step 7 — Ethics Health Grade 산출

**패턴별 점수 집계:**
- ✅ 위반 없음: 10점
- ⚠️ 경계: 5-7점 (평가자 판단)
- ❌ 위반: 0-4점 (자동 critical)
- N/A: 집계 제외

**전체 Ethics Health Grade** = 적용 패턴 점수 평균 (0-10):
- 9.5-10 = **A** (Excellent — dark pattern 제로, 완전 신뢰)
- 8.0-9.4 = **B** (Good — 경미한 경계 패턴 1-2건)
- 6.0-7.9 = **C** (Caution — ⚠️ 다수 또는 ❌ 1건)
- 4.0-5.9 = **D** (Poor — ❌ 2-3건, 즉시 수정 필요)
- 0-3.9 = **F** (Critical — ❌ 4건 이상, 서비스 신뢰 붕괴 위험)

**추가 헤드라인:**
- **Regulation Risk**: 가장 높은 규제 리스크 등급 + 조항 한 줄 요약
- **Trust Impact**: 셀러 신뢰에 미치는 예상 영향 (High/Medium/Low)

### Step 8 — Finding 작성

위반(❌) 또는 경계(⚠️) 패턴마다 finding 1개:

```markdown
### {Pattern Name} — score: {N}
- **severity**: critical | warning | info
- **pattern**: {Brignull 12 패턴 번호 + 이름}
- **evidence**: frame `{nodeId}` · {구체적 UI 요소·텍스트·위치}
- **fix**: {구체적 수정 방향}
- **규제 리스크**: {해당 규제 조항 + 등급(HIGH/MEDIUM/LOW)} 또는 "해당 없음"
```

### Step 9 — 보고서 작성

**파일 경로**: `./design-reviews/design-ux-dark-pattern-review-{screen-slug}-{YYYYMMDD-HHmm}.md`
- `{screen-slug}`: frame.name kebab-case 소문자 또는 flow 목표 기반
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 10 — 수정 우선순위 제안 (Top-3 Fix)

❌ critical 위반 우선, 동수일 때 규제 리스크 등급 높은 순으로 최대 3개 선정:

각 카드 포맷:
- **패턴**: {번호 + 이름}
- **위치**: frame `{nodeId}` · {UI 요소}
- **사용자 영향**: {셀러 신뢰 손상 시나리오}
- **규제 리스크**: {HIGH/MEDIUM/LOW + 조항}
- **수정 방향**: {구체 변경사항}
- **기대 점수 변화**: {N} → {N'}
- **노력**: {Low/Medium/High} ({n} weeks)

### Step 11 — 사용자에게 결과 요약

- 생성된 보고서 파일 경로
- Ethics Health Grade + 평균 점수
- 12 패턴 ✅/❌/⚠️/N/A 현황 표
- critical/warning 개수 + 규제 리스크 요약
- Top-3 Fix 한 줄 요약
- 다음 액션 제안

### Step 12 — annotate-design 연동 안내 (위반 있을 때)

finding이 1건 이상이면:
```
리뷰 파일: {경로}
다음 명령으로 Figma/Pencil에 finding 마커 부착 가능:
/annotate-design {경로}
```

## 보고서 구조 (한국어)

```markdown
# Dark Pattern Audit: {화면/flow 이름}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID(s): {nodeId(s)}
- 프레임 이름(s): {frame.name(s)}
- 화면 컨텍스트: {CHECKOUT | ONBOARDING | DASHBOARD | SUBSCRIPTION | CONTENT | HYBRID}
- 서비스 성격: {비즈니스 맥락}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 방법론: Harry Brignull deceptive.design 12 카테고리 (2023) + GDPR/CPRA/한국 e-privacy 규제 매핑
- 참고: deceptive.design/types · FTC dark pattern report · EU DSA Art.26·37 · GDPR Recital 32

## 헤드라인
- **Ethics Health Grade: {A-F}** ({평균}/10)
- **Regulation Risk**: {HIGH/MEDIUM/LOW} — {가장 높은 리스크 조항 한 줄}
- **Trust Impact**: {High/Medium/Low} — {셀러 신뢰 영향 한 줄}
- 적용 패턴: {applied}/12 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression (윤리 관점)
- 이 화면/flow의 전반적인 신뢰 인상: {...}
- 즉시 의심이 가는 요소: {...}
- 셀러(B2B) 관점에서 가장 걱정되는 부분: {...}
- 한 단어 윤리 요약: {...}
- 인상 메모: {...}

## 12 패턴 체크리스트

| # | Pattern | 판정 | 점수 | 규제 리스크 |
|---|---------|------|------|-----------|
| 1 | Comparison Prevention | ✅/❌/⚠️/N/A | - | - |
| 2 | Confirmshaming | ✅/❌/⚠️/N/A | - | - |
| 3 | Disguised Ads | ✅/❌/⚠️/N/A | - | - |
| 4 | Fake Scarcity | ✅/❌/⚠️/N/A | - | - |
| 5 | Fake Social Proof | ✅/❌/⚠️/N/A | - | - |
| 6 | Fake Urgency | ✅/❌/⚠️/N/A | - | - |
| 7 | Forced Action | ✅/❌/⚠️/N/A | - | - |
| 8 | Hard to Cancel (Roach Motel) | ✅/❌/⚠️/N/A | - | - |
| 9 | Hidden Costs | ✅/❌/⚠️/N/A | - | - |
| 10 | Hidden Subscription | ✅/❌/⚠️/N/A | - | - |
| 11 | Nagging | ✅/❌/⚠️/N/A | - | - |
| 12 | Obstruction / Pre-selection / Sneaking / Trick Wording | ✅/❌/⚠️/N/A | - | - |

## Findings

### {Pattern Name} — score: {N}
- **severity**: critical | warning | info
- **pattern**: {번호} {Pattern Name}
- **evidence**: frame `{nodeId}` · {구체적 UI 요소·텍스트·좌표}
- **fix**: {구체 수정 방향}
- **규제 리스크**: {조항 + HIGH/MEDIUM/LOW}

{위반/경계 패턴만 나열}

## Top-3 Fix

### Fix 1 — {Pattern Name}
- **패턴**: {번호 + 이름}
- **위치**: frame `{nodeId}` · {UI 요소}
- **사용자 영향**: {셀러 신뢰 손상 시나리오}
- **규제 리스크**: {HIGH/MEDIUM/LOW + 조항}
- **수정 방향**: {구체 변경사항}
- **기대 점수 변화**: {N} → {N'}
- **노력**: {Low/Medium/High} ({n} weeks)

### Fix 2 — ...
### Fix 3 — ...

## N/A 항목 (해당 UI 없음)
- {패턴 번호} {이름}: {사유}

## 다음 단계
- Top-3 Fix 즉시 수정 후 재audit
- `/annotate-design {보고서 경로}` 로 디자인 파일에 finding 마커 부착
- 법무 검토 필요 시 HIGH 규제 리스크 항목 우선 에스컬레이션
- design-ux-flow-review `--lens D` 로 flow 단위 재검증 (수정 후)
```

## 인자

```
/design-ux-dark-pattern-review <Figma URL | .pen path> [--scope "{범위}"] [--context "{비즈니스 맥락}"]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- `--scope "{...}"`: 특정 영역 집중 (예: `--scope "구독 결제 플로우"`)
- `--context "{...}"`: 서비스 성격 명시 (기본값: "셀러 dashboard B2B SaaS")
- 프레임 선택은 Figma/Pencil 현재 선택으로 자동 감지

## 예시

### 예시 1 — Figma 결제 flow dark pattern 전수 audit
```
/design-ux-dark-pattern-review https://www.figma.com/design/abc/EasySeller?node-id=42-1024 --scope "요금제 선택 및 결제"
```
→ Figma MCP 체크 → 결제 관련 frame 데이터 수집 → 컨텍스트: CHECKOUT → 12패턴 전수 평가 → Hidden Costs(❌ critical, GDPR EU CRD Art.6 HIGH) + Pre-selection(❌ critical, GDPR Art.7 HIGH) 2건 발견 → Ethics Health Grade D → `./design-reviews/design-ux-dark-pattern-review-payment-flow-20260518-1430.md` 생성

### 예시 2 — Pencil 가입 flow onboarding audit
```
/design-ux-dark-pattern-review ~/Desktop/projects/design/onboarding.pen
```
→ Pencil MCP 체크 → 3 frame 수집 (Step1/Step2/Step3) → 컨텍스트: ONBOARDING/SIGNUP → Forced Action(⚠️ warning), Confirmshaming(✅), Pre-selection(⚠️ warning) → Ethics Health Grade B → 보고서 생성

### 예시 3 — Dashboard 화면 신뢰 점검
```
/design-ux-dark-pattern-review https://www.figma.com/design/abc/EasySeller?node-id=10-200 --context "셀러 통계 대시보드 B2B"
```
→ 컨텍스트: DASHBOARD HUB → Disguised Ads·Fake Social Proof·Nagging 집중 검사 → 전체 ✅ → Ethics Health Grade A → "dark pattern 0건 확인" 보고서 생성

### 예시 4 — 구독 관리 해지 flow Hard to Cancel 집중
```
/design-ux-dark-pattern-review ~/Documents/subscription.pen --scope "구독 취소 플로우" --context "월간 구독 SaaS"
```
→ Hard to Cancel(❌ critical) + Hidden Subscription(⚠️ warning) → Ethics Grade D → CA auto-renewal law MEDIUM + GDPR Art.17 HIGH 규제 매핑 → 즉시 수정 권고

### 예시 5 — MCP 미연결
```
/design-ux-dark-pattern-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 패턴 이름은 영어 원어 유지 (Confirmshaming, Roach Motel, Nagging 등)
- finding 헤더 포맷 `### {Pattern Name} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / pattern / evidence / fix / 규제리스크 5 필드 동일 순서 유지
- ❌ 위반 = 자동 critical, 예외 없음
- Top-3 Fix · 규제 매핑 섹션은 annotate-design 파싱 범위 밖 별도 섹션
- N/A 항목은 보고서 말미 별도 기재

## annotate-design 호환성

본 스킬의 출력 `.md`는 `annotate-design` 스킬이 그대로 파싱하여 Figma/Pencil 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다. evidence의 `frame \`{nodeId}\`` 패턴에서 nodeId를 추출해 해당 frame 위에 마커 배치.

```
/design-ux-dark-pattern-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md>              → 디자인 파일에 시각 코멘트 부착
```

## design-ux-flow-review와의 관계

| 항목 | design-ux-flow-review Lens D | design-ux-dark-pattern-review |
|------|------------------------------|-------------------------------|
| 패턴 수 | 6개 (Sneaking·Roach Motel·Forced·Hidden Cost·Fake Urgency·Preselection) | 12개 (Brignull 2023 전체) |
| 목적 | flow 전체 구조 중 윤리 lens 1개 | 윤리 audit 전용 심층 분석 |
| 규제 매핑 | 없음 | GDPR/CPRA/한국 e-privacy 자동 태깅 |
| 점수 체계 | 0-10 수치 | ✅/❌/⚠️ + Ethics Health Grade |
| 용도 | flow 리뷰 중 빠른 dark pattern 스캔 | 전수 윤리 audit + 법무 대비 |

두 스킬은 상호 보완: flow-review 후 Lens D에서 ⚠️/❌ 발견 시 이 스킬로 심층 drill-down 권장.

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- flow 전체 구조(IA·전환·습관) 평가 — `design-ux-flow-review` 책임
- 시각 UI 레이어 — `design-ui-*-review` 책임
- 법률 자문 제공 — 규제 리스크 표시는 참고용, 법무팀 검토 필수
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만

## 참고 자료

- **Harry Brignull deceptive.design** — https://www.deceptive.design/types (12 카테고리 카탈로그)
- **Brignull, H. (2023)** — *Deceptive Patterns: Expose, Understand, Avoid* (ROSENFELD MEDIA)
- **FTC** — "Bringing Dark Patterns to Light" (2022) — https://www.ftc.gov/reports/dark-patterns
- **EU DSA** — Digital Services Act Art.13 (투명성), Art.26 (광고 표시), Art.37 (추천 시스템 감사)
- **GDPR** — Recital 32 (동의 자유성·명확성), Art.7 §4 (조건부 동의 금지), Art.17 (삭제권)
- **CPRA** — California Privacy Rights Act §1798.120, §1798.121, §1798.125
- **한국 개인정보보호법** — §22 (동의), §36 (정정·삭제)
- **전자상거래법** — §13 (청약 전 정보), §14 (자동 결제 고지), §21 (소비자 오인 금지)
- **표시광고법** — §3 (기만적 표시·광고 금지)
- **정보통신망법** — §50 (스팸·반복 알림 규제)
- **짝 스킬**: `design-ux-flow-review` (Lens D 6항목 통합 flow 리뷰) · `annotate-design` (finding 시각화)
