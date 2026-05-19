---
name: design-ux-heart-review
review-level: L2 Structure
description: "[L2 Structure] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Google HEART Framework(Happiness·Engagement·Adoption·Retention·Task Success) + GSM(Goals-Signals-Metrics) 기준으로 정적 분석하여 한국어 마크다운 리뷰 보고서를 생성. UI 요소에서 정량 metric 신호를 정적으로 추출 — success state·CTA·reward·progress indicator·onboarding step·notification 등을 HEART 5 카테고리에 매핑하고 각 카테고리를 0-10 점수로 평가. HEART Health Grade(A-F) 헤드라인 + 5 metric 점수 + GSM 맵 + Top-3 Metric Risk. 정성 휴리스틱(Nielsen/IxDF/Laws) 이 잡지 못하는 정량 KPI 신호 공백을 잡는다. stat-front 같은 셀러 KPI 대시보드에서 UX 신호 ↔ 비즈니스 KPI 연결 lens 로 직격. 사용자가 \"HEART 리뷰\", \"metric UX 리뷰\", \"참여율 진단\", \"온보딩 평가\", \"리텐션 신호 점검\", \"task success 분석\", \"/design-ux-heart-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 정량 metric 관점 UX 리뷰를 요청할 때 사용."
---

# design-ux-heart-review

**Review Level**: L2 Structure — Google HEART Framework + GSM metric 신호 정적 분석.

Kerry Rodden(Google, 2010)이 제안한 HEART Framework 와 GSM(Goals-Signals-Metrics) 방법론을 정적 디자인 분석에 적용한 스킬. 정성 휴리스틱(Nielsen·IxDF·Laws of UX)이 "사용성 문제"를 잡는다면, 이 스킬은 "어떤 metric이 이 디자인 결정의 성패를 판단하는가"를 정적으로 추정한다. 리포트만 생성한다 — 코멘트 게시는 `annotate-design` 책임.

평가 렌즈 = "이 화면에서 Happiness·Engagement·Adoption·Retention·Task Success 각 metric을 측정할 수 있는 UI 신호가 존재하는가? 신호가 없거나 역방향이면 어떤 KPI가 위험한가?"

## HEART 5 + GSM 정의

### Rubric A — HEART 5 Categories

| Category | 측정 대상 | 대표 metric | UI 신호 (정적 분석 대상) |
|----------|----------|------------|--------------------------|
| **Happiness** | 만족도·감성 | NPS, CSAT, App Store rating | success state, micro-delight, brand emotion, empty state tone, error message tone |
| **Engagement** | 활동 빈도·강도·깊이 | DAU/WAU, session depth, feature adoption rate | variable reward, hook pattern, content depth, gamification, feed/carousel, social proof |
| **Adoption** | 신규 사용자 첫 활동 | 첫 핵심 action 완료율, feature discovery rate | onboarding step, empty state CTA, 첫 화면 primary CTA visibility, progressive disclosure |
| **Retention** | 재방문·이탈 방어 | D1/D7/D30 retention, churn rate | notification trigger, habit loop, value reminder, streak/badge, re-engagement CTA |
| **Task Success** | 완료율·정확도·효율 | task completion rate, error rate, time-to-complete | progress indicator, error recovery, undo, confirmation state, form clarity |

### Rubric B — GSM Map (화면 단위)

| 항목 | 정의 | 정적 분석 적용 |
|------|------|--------------|
| **Goal** | 이 화면이 달성해야 할 사용자·비즈니스 목표 | 화면 구조·CTA·헤드라인에서 추정 |
| **Signal** | 목표 달성 여부를 알 수 있는 UI 행동 신호 | 클릭 가능 요소·state 변화·feedback 유무로 평가 |
| **Metric** | 신호를 정량화할 수 있는 지표 정의 | 정적 분석 추정 + 측정 가능성 평가 |

### HEART × UI 신호 매핑 (정적 분석 기준)

```
Happiness  ← success state 존재 / error message tone / micro-animation 신호
              brand emotion 일관성 / onboarding 환영 메시지
Engagement ← variable reward 요소 (배지·streak·콘텐츠 알림)
              content depth (scroll depth 유발 요소) / gamification
              social proof (리뷰·공유·활동 feed)
Adoption   ← empty state first-use CTA 가시성 / onboarding step 명확성
              primary CTA 첫 화면 노출 / feature discovery 진입점
Retention  ← notification 진입점 / habit loop trigger
              value reminder (마지막 활동·성과 요약) / re-engagement 유도
Task Success ← progress indicator / error recovery path
               undo/cancel / confirmation 완료 state / form validation UX
```

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일에서 "HEART 리뷰", "metric 관점 UX 평가", "Engagement 진단", "온보딩 점검", "리텐션 신호 분석", "task completion 진단" 등을 요청할 때
- 정성 휴리스틱(Nielsen·IxDF·Laws) 이미 돌렸으나 비즈니스 KPI 연결 관점 보완이 필요할 때
- KPI 대시보드·셀러 도구·SaaS 제품에서 UX 신호 ↔ 비즈니스 metric 연결이 필요할 때
- 신규 기능 출시 전 Adoption 신호 공백 점검 또는 리텐션 트리거 진단
- A/B 테스트 설계 전 "어떤 UI 요소가 어떤 metric에 영향을 주는가" 가설 정립

## Do Not Use

- 단일 frame micro 휴리스틱 평가:
  - Nielsen 10 → `design-ux-nielsen-review`
  - IxDF 12 → `design-ux-ixdf-review`
  - Laws of UX 23 → `design-ux-lawsofux-review`
- User flow / task journey 구조 평가 → `design-ux-flow-review`
- 전략·정체성·scope 진단 → `design-ceo-review`
- 이커머스 funnel 전용 → `design-ux-ecommerce-review`
- 시각·감성 UI 레이어 → `design-ui-*-review`
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 라이브 사이트 실측 analytics → gstack `/design-review`
- 발산형 UX 재설계 → `ux-reimagine` / `design-shotgun`

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 중 하나 활성화 후 재시도." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: 첫 단계에서 ToolSearch 로 prefix 의 도구를 조회. 결과가 비어 있으면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + 타입 라우팅

사용자 인자에서 입력 타입을 자동 감지:

- `figma.com/design/:fileKey/...?node-id=:nodeId` → **Figma 경로**
- `*.pen` 로컬 경로 → **Pencil 경로**
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

옵션 인자 처리:
- `--goal "{product goal}"`: 평가 기준 목표 명시
- `--context "{domain context}"`: 도메인 컨텍스트 보강 (예: "셀러 KPI 대시보드", "이커머스 앱")
- `--heart H,E,A,R,T`: 특정 HEART 카테고리만 평가 (대문자 이니셜, 미지정 시 전체)

### Step 2 — MCP 사전 체크

Prerequisites 표 기준 ToolSearch. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집

**Figma 경로:**
1. `get_metadata(fileKey, nodeId)` 또는 `figma_get_file_data(verbosity:summary)`
2. 각 frame 마다:
   - deep tree (`get_design_context` 또는 `figma_get_component_for_development_deep`)
   - 스크린샷 1장 (`get_screenshot` 또는 `figma_capture_screenshot`)
3. 컴포넌트 목록 추출: CTA 버튼·input·notification badge·progress bar·empty state·success state·error state 노드 식별

**Pencil 경로:**
1. `open_document(path=...)` (필요 시)
2. `get_editor_state()` → 선택 frame 목록
   - 선택이 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `batch_get(node_ids=[frame_id], depth:4)` → deep 노드 트리
   - `snapshot_layout(node_id=frame_id)` → 레이아웃 스냅샷
   - `get_screenshot(nodeId=frame_id)` → 이미지 1장
   - `search_all_unique_properties(node_id=frame_id, property=...)` → 컬러·폰트·컴포넌트 팔레트

### Step 4 — Classifier (화면 타입 + 추정 도메인 + HEART 우선순위)

수집된 frame 을 분류:

- **DASHBOARD** — KPI 카드·차트·table 중심 → Task Success·Engagement 가중 ↑
- **ONBOARDING/SIGNUP** — 회원가입·첫 설정 흐름 → Adoption·Happiness 가중 ↑
- **FEED/BROWSE** — 콘텐츠 나열·검색 → Engagement·Retention 가중 ↑
- **TASK/FORM** — 특정 작업 수행 → Task Success·Adoption 가중 ↑
- **PROFILE/SETTINGS** — 계정·설정 → Retention·Happiness 가중 ↑
- **NOTIFICATION/TRIGGER** — 알림·뱃지·이메일 유사 화면 → Retention·Engagement 가중 ↑
- **MIXED** — 혼재

도메인 추정 (Step 1 `--context` 우선, 없으면 frame 노드 트리 기반 추정).

`--heart` 인자 있으면 해당 카테고리만 평가. 미지정 시 Classifier 기반 가중치 조정.

### Step 5 — First Impression (Phase 1)

스크린샷 본 직후 1인칭 작성:

```
- 이 화면이 달성하려는 비즈니스 목표: [한 문장]
- 추정 사용자 유형 + 핵심 동기: [한 문장]
- HEART 5 중 가장 강해 보이는 신호: [카테고리 + 이유]
- HEART 5 중 가장 취약해 보이는 신호: [카테고리 + 이유]
- 현재 화면이 어떤 metric 개선에 직결되는가: [한 문장]
- 한 단어 요약: [단어]
- 인상 메모: [정량 신호 관점 구체 관찰]
```

진단가는 헤지하지 않는다.

### Step 6 — Inferred Metric Signals 추출 (Phase 2)

노드 트리 + 스크린샷에서 HEART 신호 요소를 추출한다. 다음 4 signal 유형을 우선 탐색:

**① Success State 신호**
- 완료 화면·완료 메시지·체크마크 애니메이션 존재 여부
- 빈 success state = Task Success metric 공백

**② Primary CTA 신호**
- 첫 화면 노출 위치·라벨 명확성·시각 hierarchy
- CTA 부재 또는 묻힘 = Adoption metric 위험

**③ Variable Reward / Hook 신호**
- 배지·streak·achievement·new content indicator·social proof 요소
- Engagement·Retention Hook Model(Nir Eyal) 신호 여부

**④ Progress Indicator 신호**
- step indicator·progress bar·loading state·percent 표시
- 부재 = Task Success·Adoption metric 저하 위험

결과를 HEART × Signal 매핑 표로 정리:

| HEART | 신호 요소 | 노드/위치 | 신호 강도 (Strong/Weak/Missing) |
|-------|---------|----------|-------------------------------|
| Happiness | success state | ... | ... |
| Engagement | variable reward | ... | ... |
| Adoption | empty state CTA | ... | ... |
| Retention | notification trigger | ... | ... |
| Task Success | progress indicator | ... | ... |

### Step 7 — HEART 5 평가 (Phase 3)

각 카테고리 0-10 점수. 정적 분석 불가 항목 `N/A` + 사유.

**점수 기준:**
- 10 — 해당 metric 을 뒷받침하는 UI 신호 exemplary
- 8-9 — 신호 존재, minor 보강 여지
- 6-7 — 신호 있으나 약하거나 일부 누락
- 4-5 — 신호 불명확, metric 측정 어려움
- 0-3 — 신호 부재 또는 metric 역방향 작용
- N/A — 정적 분석으로 판단 불가 (실측 데이터 필요)

**Severity 가이드:**
- critical: 신호 완전 부재 또는 metric 역방향 (-3 ~ -4)
- warning: 신호 약함 또는 주요 요소 누락 (-1 ~ -2)
- info: 개선 여지, 점수 영향 X

finding 1개당: **severity** · **HEART category** · **evidence**(노드 경로·수치) · **fix** · **참고**(HEART 출처).

#### H1. Happiness (0-10)

평가 기준:
- 성공 상태(success state)·완료 메시지 존재 여부
- 에러 메시지 tone (사용자 비난 vs 친근한 안내)
- 브랜드 감성 일관성 (색·일러스트·아이콘 톤)
- micro-delight 신호 (애니메이션·이모지·인격화)
- 빈 상태(empty state) 톤이 환영·격려 vs 냉담

#### H2. Engagement (0-10)

평가 기준:
- variable reward 요소 (배지·streak·랭킹·achievement)
- content depth 유발 요소 (scroll trigger·더보기·feed)
- gamification 신호 (progress bar·레벨·포인트)
- social proof / activity signal (공유·댓글·좋아요)
- hook 트리거 가시성 (알림 유도·앱 재진입 유인)

#### H3. Adoption (0-10)

평가 기준:
- empty state first-use 안내·CTA 명확성
- onboarding step 가시성·진행 표시
- primary CTA 첫 화면 노출 위치·크기·라벨
- feature discovery 진입점 (새 기능 배너·tooltip)
- progressive disclosure (복잡성 단계별 노출)

#### H4. Retention (0-10)

평가 기준:
- notification 진입점 (bell icon·badge·permission prompt)
- habit loop 신호 (streak·last-visit reminder·목표 달성률)
- value reminder (KPI 요약·성과 하이라이트)
- re-engagement CTA (돌아오세요·새 활동 알림)
- 이탈 방어 신호 (저장 안내·작업 중 이탈 확인)

#### H5. Task Success (0-10)

평가 기준:
- progress indicator / step counter 명확성
- error recovery path (에러 후 다음 액션 가이드)
- undo / cancel / back 제공
- confirmation state (작업 완료 명시)
- form validation UX (실시간 vs 제출 후)
- time-to-complete 단축 신호 (자동완성·단축키·기본값)

### Step 8 — GSM Map 작성 (Phase 4)

화면 단위 GSM 표:

| HEART | Goal | Signal (UI 요소) | Metric (추정) | 현재 UI 지원 여부 |
|-------|------|-----------------|--------------|-----------------|
| Happiness | 사용자 만족감 유지 | success state 노출 | CSAT / App rating | ✅/⚠️/❌ |
| Engagement | 재방문·세션 깊이 증가 | variable reward 클릭 | DAU ratio, feature depth | ✅/⚠️/❌ |
| Adoption | 신규 사용자 첫 핵심 action 완료 | empty state CTA | Feature adoption rate | ✅/⚠️/❌ |
| Retention | D7/D30 재방문 | notification trigger | Churn rate | ✅/⚠️/❌ |
| Task Success | 목표 task 완료율 향상 | progress indicator | Task completion rate | ✅/⚠️/❌ |

`현재 UI 지원 여부`: ✅ 신호 명확 / ⚠️ 신호 약함 / ❌ 신호 없음

### Step 9 — HEART Health Grade 산출

**Per-Category 점수**: H1-H5 각 0-10

**전체 Grade** = Classifier 가중치 적용 평균:

| 화면 타입 | H | E | A | R | T |
|---------|---|---|---|---|---|
| DASHBOARD | 1 | 2 | 1 | 1 | 3 |
| ONBOARDING | 2 | 1 | 3 | 1 | 2 |
| FEED/BROWSE | 1 | 3 | 1 | 2 | 1 |
| TASK/FORM | 2 | 1 | 2 | 1 | 3 |
| NOTIFICATION | 1 | 2 | 1 | 3 | 1 |
| MIXED | 1 | 1 | 1 | 1 | 1 |

가중 평균 = Σ(카테고리점수 × 가중치) / Σ(가중치)

**Grade 환산:**
- 9.0-10 = **A** (Excellent — metric 신호 풍부, KPI 연결 명확)
- 7.5-8.9 = **B** (Good — 대부분 신호 존재, minor 보강)
- 6.0-7.4 = **C** (Acceptable — 일부 카테고리 신호 약함)
- 4.0-5.9 = **D** (Poor — 복수 카테고리 metric 공백)
- 0-3.9  = **F** (Critical — metric 측정 불가, 전면 재설계)

**추가 헤드라인:**
- **Metric Coverage**: GSM 표에서 ✅ 비율 (예: 3/5 = 60%)
- **Weakest Signal**: 가장 낮은 카테고리 + 한 줄 원인
- **Strongest Signal**: 가장 높은 카테고리 + 한 줄 근거

### Step 10 — 보고서 작성

**파일 경로**: `./design-reviews/design-ux-heart-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name kebab-case (한글이면 음역 또는 nodeId 끝 8자)
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 11 — 사용자에게 결과 요약

- 생성된 보고서 파일 경로
- HEART Health Grade + 가중 평균 점수 + Metric Coverage
- Per-Category 점수 한 줄 요약 (H/E/A/R/T: N/N/N/N/N)
- Top-3 Metric Risk 제목 + 한 줄 설명
- 다음 액션 제안 (annotate-design / A/B 테스트 가설 / 후속 디자인 수정)

### Step 12 — Top-3 Metric Risk 도출

전체 finding 중 비즈니스 KPI 영향이 가장 큰 3개 선정.

각 카드:
- **HEART 카테고리** + **metric 위험**
- **UI 신호 공백** (어떤 요소가 없는가)
- **예상 metric 영향** (구체 KPI 하락 시나리오)
- **비즈니스 영향** (이 metric이 왜 이 product에서 중요한가)
- **권장 UI 수정** (최소 viable 신호 추가)
- **노력 규모** (Low/Medium/High)

선정 우선순위:
1. ❌ (신호 없음) + 화면 타입 핵심 가중 카테고리
2. critical finding 누적 多 카테고리
3. GSM Goal 불명확 (Goal 자체가 추정 불가) 항목

## 보고서 구조 (한국어)

```markdown
# HEART Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 화면 타입: {DASHBOARD | ONBOARDING | FEED/BROWSE | TASK/FORM | NOTIFICATION | MIXED}
- 추정 도메인: {셀러 KPI 대시보드 | 이커머스 앱 | SaaS 등}
- 추정 페르소나: {역할·동기·기기}
- 적용 HEART: {H·E·A·R·T 중 평가한 것 — 전체 또는 --heart 필터}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 인라인}
- 방법론: Google HEART Framework (Rodden, Hutchinson, Fu 2010) + GSM (Goals-Signals-Metrics)

## 헤드라인
- **HEART Health Grade: {A-F}** (가중 평균 {N}/10)
- **Metric Coverage**: {N}/5 카테고리 신호 명확 ({%})
- **Weakest Signal**: {카테고리} — {한 줄 원인}
- **Strongest Signal**: {카테고리} — {한 줄 근거}
- Per-Category: H:{n} · E:{n} · A:{n} · R:{n} · T:{n}
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 비즈니스 목표: {...}
- 추정 사용자: {...}
- 가장 강한 HEART 신호: {...}
- 가장 취약한 HEART 신호: {...}
- metric 연결 한 줄: {...}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Inferred Metric Signals

| HEART | 신호 요소 | 노드/위치 | 신호 강도 |
|-------|---------|----------|---------|
| Happiness | success state | ... | Strong/Weak/Missing |
| Engagement | variable reward | ... | Strong/Weak/Missing |
| Adoption | empty state CTA | ... | Strong/Weak/Missing |
| Retention | notification trigger | ... | Strong/Weak/Missing |
| Task Success | progress indicator | ... | Strong/Weak/Missing |

## HEART 5 점수표

| Category | 점수 | 핵심 관찰 |
|----------|------|---------|
| H. Happiness | {n}/10 | {...} |
| E. Engagement | {n}/10 | {...} |
| A. Adoption | {n}/10 | {...} |
| R. Retention | {n}/10 | {...} |
| T. Task Success | {n}/10 | {...} |

## Findings

### {항목명}.{signal} — score: {N}
- **severity**: critical | warning | info
- **HEART category**: Happiness | Engagement | Adoption | Retention | Task Success
- **evidence**: frame `{nodeId}` · {구체 UI 요소 · 신호 공백 설명}
- **fix**: {최소 viable UI 수정 — 구체 컴포넌트·복사 방향}
- **참고**: {HEART paper (Rodden 2010) | dscout HEART | NN/g GSM | Hooked Model (Nir Eyal)}

{위반/공백이 있는 항목만 나열}

## GSM Map

| HEART | Goal | Signal (UI 요소) | Metric (추정) | 현재 UI 지원 |
|-------|------|-----------------|--------------|------------|
| Happiness | ... | ... | CSAT / NPS | ✅/⚠️/❌ |
| Engagement | ... | ... | DAU ratio | ✅/⚠️/❌ |
| Adoption | ... | ... | Adoption rate | ✅/⚠️/❌ |
| Retention | ... | ... | D7 retention | ✅/⚠️/❌ |
| Task Success | ... | ... | Task completion | ✅/⚠️/❌ |

## Top-3 Metric Risk

### Risk 1 — {HEART 카테고리}: {metric 위험 제목}
- **HEART 카테고리**: {...}
- **UI 신호 공백**: {어떤 요소가 없는가}
- **예상 metric 영향**: {구체 KPI 하락 시나리오}
- **비즈니스 영향**: {이 product에서 중요한 이유}
- **권장 UI 수정**: {최소 viable 신호 추가 방향}
- **노력**: {Low/Medium/High}

### Risk 2 — ...
### Risk 3 — ...

## N/A 항목 (정적 분석 한정)
- {실측 데이터(analytics·사용자 인터뷰) 없이 판단 불가한 항목 + 사유}
- 모든 Metric 수치: 실제 측정값은 analytics 도구 필요

## 다음 단계 (권장 후속)
- Top-3 Metric Risk 기반 UI 수정 후 `annotate-design` 로 finding 시각화
- A/B 테스트 가설 수립 (Risk 1·2 기반 변수 정의)
- 실측: analytics 이벤트 설계 (GSM Map의 Signal → tracking event)
- 5-8명 사용성 테스트 (Adoption·Task Success 가설 검증)
- 정성 리뷰 연계: `design-ux-flow-review` (flow 구조) · `design-ceo-review` (전략)
```

## design-ceo-review 와의 관계

두 스킬은 서로 다른 추상화 레이어에서 상호 보완한다:

| 관점 | `design-ceo-review` | `design-ux-heart-review` (이 스킬) |
|------|--------------------|------------------------------------|
| 레이어 | L5 전략 — 정체성·scope·vision | L2 Structure — metric 신호·KPI 연결 |
| 질문 | "이 화면이 12개월 vision으로 향하는가?" | "이 화면의 어떤 요소가 어떤 KPI를 움직이는가?" |
| 출력 | Identity Verdict + Approach A/B/C | HEART Health Grade + GSM Map + Metric Risk |
| 순서 | 전략 방향 결정 먼저 | 방향 결정 후 metric 신호 검증 |

이상적 순서: **design-ceo-review (방향 잠금) → design-ux-heart-review (metric 신호 진단) → micro UX/UI 리뷰 → annotate-design**

## 인자

```
/design-ux-heart-review <Figma URL | .pen path> [--goal "{product goal}"] [--context "{domain}"] [--heart H,E,A,R,T]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- `--goal "{...}"`: 화면의 비즈니스/사용자 목표 명시 (없으면 추정)
- `--context "{...}"`: 도메인 컨텍스트 (예: "셀러 KPI 대시보드") — GSM Goal 추정 정확도 향상
- `--heart H,E,A,R,T`: 평가할 카테고리 이니셜 콤마 구분. 미지정 시 전체 5개
- frame 선택은 Figma/Pencil **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Pencil 대시보드 전체 평가
```
/design-ux-heart-review ~/Desktop/projects/design/easyseller.pen --context "쿠팡 셀러 KPI 대시보드"
```
→ Pencil MCP 체크 → 선택 frame 감지 → Classifier: DASHBOARD → H/E/A/R/T 전체 평가, T(Task Success)·E(Engagement) 가중 ↑ → GSM Map 작성 → HEART Health Grade → 보고서 생성

### 예시 2 — Figma 온보딩 화면, Adoption·Happiness 집중
```
/design-ux-heart-review https://www.figma.com/design/abc123/App?node-id=10-200 --goal "신규 셀러 첫 상품 등록 완료" --heart H,A,T
```
→ Figma MCP 체크 → Classifier: ONBOARDING → H·A·T 3개 카테고리만 평가 → empty state CTA 집중 분석 → Top-3 Metric Risk (Adoption 공백 중심) → 보고서

### 예시 3 — Pencil 알림/리텐션 화면
```
/design-ux-heart-review ~/Documents/design/notification.pen --heart E,R
```
→ Pencil MCP 체크 → Classifier: NOTIFICATION → E(Engagement)·R(Retention) 2개 평가 → Hook Model 신호 + notification trigger 중심 분석 → 보고서

### 예시 4 — Figma task 완료 flow, 전체 + context 보강
```
/design-ux-heart-review https://www.figma.com/design/xyz/Checkout?node-id=5-100 --goal "광고 캠페인 생성 완료" --context "셀러 광고 관리 SaaS"
```
→ Figma MCP 체크 → Classifier: TASK/FORM → T(Task Success) 가중 ↑ → progress indicator·error recovery·success state 집중 → GSM Map 광고 KPI 연결 → 보고서

### 예시 5 — MCP 미연결
```
/design-ux-heart-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 가 연결되어 있지 않습니다." 안내 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- HEART 카테고리명은 영어 원어 유지 (Happiness, Engagement, Adoption, Retention, Task Success, GSM, Goals-Signals-Metrics 등)
- finding 의 evidence/fix 는 노드명·수치·구체 UI 요소 명시
- 보고서는 한 프레임(또는 선택 프레임 세트) 당 한 파일
- finding 헤더 포맷 `### {항목명}.{signal} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / HEART category / evidence / fix / 참고 필드 동일 순서 유지
- Top-3 Metric Risk · GSM Map 은 별도 섹션 (annotate-design 파싱 범위 밖)
- N/A 항목은 반드시 이유 명시 (정적 분석 한계 투명화)

## annotate-design 호환성

본 스킬 출력 `.md` 는 `annotate-design` 스킬이 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷 사용. session-key prefix 는 `heart` 로 자동 결정.

워크플로:
```
/design-ux-heart-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md>          → 디자인 파일에 시각 코멘트 부착 (session-key: heart-{HHmm})
```

evidence 의 `frame \`{nodeId}\`` 패턴에서 nodeId 추출 → 해당 frame 위에 마커 배치.

## Non-Goals

- 디자인 파일 코멘트 직접 게시 — `annotate-design` 책임
- 단일 frame micro 휴리스틱 — `design-ux-{nielsen,ixdf,lawsofux}-review` 책임
- User flow / task journey 구조 분석 — `design-ux-flow-review` 책임
- 전략·정체성·scope 진단 — `design-ceo-review` 책임
- 시각·감성 UI 레이어 — `design-ui-*-review` 책임
- 라이브 사이트 실측 analytics — gstack `/design-review` 책임
- 발산형 UX 대안 생성 — `design-shotgun` / `ux-burst` 책임
- 실제 metric 수치 수집 / analytics 구현 — 리뷰 + 신호 진단만
- 코드 생성 — 디자인 파일 진단만

## 추상화 단계 비교 (design-ux-* 스킬과의 차이)

| 스킬 | 추상화 단계 | 평가 단위 | 주요 관점 |
|------|-----------|----------|----------|
| `design-ux-nielsen-review` | L1 Skeleton / Screen | 단일 frame | 사용성 10 휴리스틱 |
| `design-ux-ixdf-review` | L1 Skeleton-Structure | 단일 frame | IxDF 12 원칙 |
| `design-ux-lawsofux-review` | L1 Skeleton / Micro | 단일 frame | 인지 법칙 23 |
| `design-ux-flow-review` | L2 Structure | flow 시퀀스 | 흐름·IA·변환·습관 |
| **`design-ux-heart-review`** | **L2 Structure** | **단일 frame** | **정량 metric 신호·KPI 연결** |
| `design-ceo-review` | L5 Strategy | 제품 | 정체성·scope·vision |

## 참고 자료

- **Google HEART paper**: Rodden, Hutchinson, Fu — *Measuring the User Experience on a Large Scale: User-Centered Metrics for Web Applications* (CHI 2010)
- **dscout HEART 가이드**: https://dscout.com/people-nerds/heart-framework
- **GV (Google Ventures) HEART 실무**: https://library.gv.com/how-to-choose-the-right-ux-metrics-for-your-product-5f46359ab5be
- **NN/g GSM (Goals-Signals-Metrics)**: https://www.nngroup.com/articles/ux-metrics/
- **Hooked Model** (Engagement·Retention 신호): Nir Eyal *Hooked* (Trigger → Action → Variable Reward → Investment)
- **BJ Fogg Behavior Model** (Adoption 신호): B=MAT https://behaviormodel.org/
- 짝 flow 스킬: `design-ux-flow-review` (L2 구조·흐름)
- 짝 전략 스킬: `design-ceo-review` (L5 전략)
- 짝 micro 스킬: `design-ux-nielsen-review` · `design-ux-ixdf-review` · `design-ux-lawsofux-review`
