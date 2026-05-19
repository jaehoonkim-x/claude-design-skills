---
name: design-ux-form-review
review-level: L1 Skeleton
description: "[L1 Skeleton] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 폼 디자인 전용 12 lens rubric으로 정적 분석하여 한국어 마크다운 리뷰 보고서를 생성. Adam Silver \"Form Design Patterns\" + Caroline Jarrett \"Forms that Work\" + Luke Wroblewski \"Web Form Design\" 통합 기반. 12 lens: One thing per page · Label position · Label clarity · Required field · Help text · Validation timing · Error message · Error summary · Input type · Autocomplete · Progress indicator · Submit button. Form UX Health Grade(A-F) 헤드라인 + 12 lens 점수 + Top-3 Friction. stat-front login·signup·account·store-manage 폼 직격. 사용자가 \"폼 UX 리뷰\", \"form 디자인 평가\", \"폼 접근성 점검\", \"입력 필드 UX\", \"form review\", \"회원가입 폼 분석\", \"로그인 UX 평가\", \"/design-ux-form-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 폼 전용 UX 리뷰를 요청할 때 사용."
---

# design-ux-form-review

**Review Level**: L1 Skeleton — 폼 디자인 전용 12 lens rubric.

Adam Silver "Form Design Patterns" · Caroline Jarrett "Forms that Work" · Luke Wroblewski "Web Form Design" · GOV.UK Design System · Baymard Institute form research 를 통합한 폼 전용 평가 스킬. 리포트만 생성한다 — 코멘트 게시는 `annotate-design` 책임.

평가 렌즈 = "이 폼이 사용자로 하여금 최소 마찰로 올바른 정보를 입력하고 제출할 수 있게 하는가? 인지 부담·오류·불안·이탈 관점에서 어디가 구멍인가?"

## 추상화 위치

Garrett 5 Planes 의 **Skeleton** 레이어. 개별 입력 필드·레이블·에러 메시지·버튼 등 폼 구성 요소 단위 평가. User Flow(L2) 아래, Surface/Visual(L0) 위.

## 12 Lens Rubric

### Lens 1. One thing per page

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 1 | One thing per page | 화면당 질문 1개(또는 논리적으로 연관된 최소 묶음) 원칙. 관계없는 필드 혼재, 과도한 필드 밀집 여부 | Yes |

> **출처**: Adam Silver "Form Design Patterns" — Ch.1 "A Registration Form" (one question per page principle)

### Lens 2. Label position

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 2 | Label position | 레이블이 입력 필드 **위(top)** 에 위치하는가. placeholder 를 레이블 대용으로 사용하는지 여부 | Yes |

> **출처**: Luke Wroblewski "Web Form Design" — Top-aligned labels maximize completion rates. Caroline Jarrett "Forms that Work" — Never use placeholder as label substitute.

### Lens 3. Label clarity

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 3 | Label clarity | 레이블이 사용자 언어로 작성되었는가. 기술 용어·내부 코드·약어 배제. 질문형 레이블(예: "이메일 주소는?") 또는 명사형 중 명확한 것 사용 | Yes |

> **출처**: Caroline Jarrett "Forms that Work" — Ch.5 "Deciding what to ask". GOV.UK Design System — Label best practices.

### Lens 4. Required field

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 4 | Required field | 필수/선택 필드를 명시적으로 구분하는가. 선택이 소수면 "(선택)" 표시, 필수가 소수면 별표(*) + 범례 | Yes |

> **출처**: Adam Silver "Form Design Patterns" — Ch.1. GOV.UK — Mark optional, not required.

### Lens 5. Help text

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 5 | Help text | 힌트/설명 텍스트가 레이블 아래(필드 위) 에 위치하는가. `aria-describedby` 또는 hint id 연결 여부 (코드 힌트). 과도하거나 불필요한 힌트 배제 | Partial |

> **출처**: Adam Silver "Form Design Patterns" — hint text placement. GOV.UK — Hint text pattern.

### Lens 6. Validation timing

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 6 | Validation timing | onBlur(필드 이탈 후) 또는 onSubmit(제출 시) 검증. onKeyUp(입력 중) 즉시 에러 표시는 불안 유발 — 금지. 인라인 성공 상태(체크 아이콘) 표현 여부 | Partial |

> **출처**: Luke Wroblewski "Web Form Design" — Inline validation research. Baymard — Validation timing best practices.

### Lens 7. Error message

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 7 | Error message | 에러 메시지가 원인 + 해결 방법을 평어(plain language)로 제공하는가. 필드 가까이(아래 또는 인라인) 위치. "필수 항목입니다" 같은 무의미한 메시지 배제. 빨간 테두리 단독 의존 금지 | Yes |

> **출처**: Caroline Jarrett "Forms that Work" — Error messages. GOV.UK — Error messages pattern. Baymard — Error message clarity.

### Lens 8. Error summary

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 8 | Error summary | 제출 실패 시 폼 **상단**에 에러 요약(summary) 박스가 나타나는가. 각 에러 항목이 해당 필드로 이동하는 앵커 링크를 제공하는가 (GOV.UK 패턴) | Yes |

> **출처**: GOV.UK Design System — Error summary pattern. Adam Silver "Form Design Patterns" — Ch.2 error handling.

### Lens 9. Input type

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 9 | Input type | 이메일 → `type="email"`, 전화 → `type="tel"`, 숫자 → `type="number"` 또는 `inputmode="numeric"`, 날짜 → `type="date"` 또는 전용 date picker. 모바일 키보드 최적화 여부 (디자인 힌트 기반 추론) | Partial |

> **출처**: Luke Wroblewski "Web Form Design" — input types. GOV.UK — Text input pattern. Baymard — Mobile form input types.

### Lens 10. Autocomplete

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 10 | Autocomplete | 이름·이메일·주소·카드번호 등 개인정보 필드에 `autocomplete` 속성 또는 브라우저 자동완성 힌트 신호가 있는가. 자동완성을 의도적으로 막는 패턴(`autocomplete="off"` 남용) 배제 | Partial |

> **출처**: Adam Silver "Form Design Patterns" — autocomplete. Baymard — Autofill research. WCAG 1.3.5 Identify Input Purpose.

### Lens 11. Progress indicator

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 11 | Progress indicator | 멀티 스텝 폼에서 진행률 표시(step indicator / progress bar) 가 있는가. 현재 스텝·전체 스텝 수 명시. "저장 후 나중에 계속" (save & return) 기능 제공 여부 | Yes |

> **출처**: Luke Wroblewski "Web Form Design" — multi-step forms. GOV.UK — Question pages pattern. Adam Silver "Form Design Patterns" — Ch.8 progress.

### Lens 12. Submit button

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 12 | Submit button | 제출 버튼 텍스트가 행동 동사(action verb)인가. "확인", "제출", "Submit" 같은 무의미한 레이블 금지. 폼 결과를 명시하는 레이블 사용 (예: "계정 만들기", "결제하기", "비밀번호 변경"). 단일 주 버튼 원칙 | Yes |

> **출처**: Caroline Jarrett "Forms that Work" — button labels. Adam Silver "Form Design Patterns" — Ch.1 submit button. GOV.UK — Button pattern.

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일을 주고 "폼 UX 리뷰", "form 디자인 평가", "입력 필드 분석", "회원가입 / 로그인 / 설정 폼 점검", "접근성 폼 감사" 등을 요청할 때
- stat-front login · signup · account-setting · store-manage 화면처럼 입력 필드가 핵심인 단일 화면 폼 평가
- 신규 폼 출시 전 friction · 에러 UX · 레이블 품질 종합 점검이 필요할 때
- 폼 전환율 저하 또는 사용자 이탈 원인 진단이 필요할 때

## Do Not Use

- 폼이 아닌 일반 UI 화면 평가 → 각 전용 스킬 사용
  - 단일 화면 휴리스틱 → `design-ux-nielsen-review` / `design-ux-ixdf-review`
  - multi-frame user flow → `design-ux-flow-review`
  - 인지 법칙 → `design-ux-lawsofux-review`
- 시각·감성 UI 레이어 평가 → `design-ui-*-review`
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 라이브 사이트 audit → gstack `/design-review`
- 자동 수정 / 코드 변경 — 리뷰 + 제안만

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

Figma URL 파싱:
- fileKey = path 의 `/design/` 다음 세그먼트
- nodeId = `?node-id=` 쿼리, `-` → `:` 로 변환

옵션 인자 처리:
- `--form "{form name}"`: 폼 이름/목적 명시 (없으면 추정)
- `--step {n}/{total}`: 멀티 스텝 폼의 현재 스텝 위치 명시

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집

**Figma 경로:**

1. `get_metadata(fileKey, nodeId)` 로 프레임 구조 파악. nodeId 미지정 시 현재 선택 프레임 사용
2. 각 frame 에 대해:
   - `get_design_context(fileKey, nodeId=frame.id, depth=8)` 로 deep 노드 트리 수집
   - `get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고 이미지 확보
3. 폼 구성 요소 자동 추출: 입력 필드·레이블·hint text·에러 상태·버튼·progress indicator·required 마커

**Pencil 경로:**

1. `open_document(path=...)` (필요 시)
2. `get_editor_state()` 로 선택 frame 식별. 비어 있으면 안내 출력 후 종료
3. 각 frame 마다:
   - `batch_get(node_ids=[frame_id], readDepth=4)` 로 deep 노드 트리
   - `snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `get_screenshot(node_id=frame_id)` 로 이미지 확보
   - `search_all_unique_properties(node_id=frame_id, property=...)` 로 텍스트·폰트·컬러 추출

멀티 프레임: 선택된 복수 frame 을 각각 평가 → 동일 폼 스텝 시퀀스로 간주하고 Lens 11(Progress indicator) 집중 분석.

### Step 4 — Classifier (폼 타입 + 추정 페르소나)

수집된 화면을 분류:

- **AUTH FORM** — 로그인·회원가입·비밀번호 재설정 (stat-front: login, signup)
- **ACCOUNT/PROFILE FORM** — 개인정보·계정 설정 (stat-front: account-setting)
- **BUSINESS FORM** — 사업자·스토어 관리·제품 등록 (stat-front: store-manage)
- **MULTI-STEP WIZARD** — step 분할 폼 (진행률 표시 필수)
- **SEARCH/FILTER FORM** — 검색 조건·필터 패널
- **HYBRID** — 위 혼재

분류 결과 + 추정 페르소나(역할·목적·기기)를 보고서 메타에 기록.

폼 타입별 가중치 조정:
- AUTH FORM: Lens 2(Label position) · 3(Label clarity) · 6(Validation timing) · 12(Submit button) 가중↑
- ACCOUNT/PROFILE FORM: Lens 4(Required field) · 5(Help text) · 9(Input type) · 10(Autocomplete) 가중↑
- BUSINESS FORM: Lens 1(One thing per page) · 8(Error summary) · 11(Progress indicator) 가중↑
- MULTI-STEP WIZARD: Lens 11(Progress indicator) · 8(Error summary) · 6(Validation timing) 가중↑

### Step 5 — First Impression (Phase 1)

폼 스크린샷 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 폼이 달성하려는 목표: [한 문장]
- 추정 사용자의 진입 동기: [한 문장]
- 폼을 봤을 때 첫인상: [한 문장]
- 가장 위태로워 보이는 부분: [구체 요소 + 이유]
- 가장 잘 된 부분: [구체 요소 + 이유]
- 한 단어 요약: [단어]
- 인상 메모: [구체적 긍정/부정]
```

진단가는 헤지하지 않는다.

### Step 6 — Form Inventory (Phase 2)

수집된 노드 트리에서 폼 구성 요소 목록화:

| # | 필드명(레이블) | 타입 | 필수여부 | Hint text | 에러 상태 | 비고 |
|---|--------------|------|---------|----------|---------|------|
| 1 | 이메일 | text | 필수 | 없음 | 있음 | placeholder = 레이블 의심 |
| 2 | 비밀번호 | password | 필수 | "8자 이상" | 있음 | |
| ... | | | | | | |

추가 항목:
- **Submit button label**: {텍스트}
- **Progress indicator**: {있음/없음, 형태}
- **Error summary**: {있음/없음, 위치}
- **Help text 연결 방식**: {aria-describedby 신호 / inline / 없음}

### Step 7 — 12 Lens 평가 (Phase 3)

각 lens 마다 0-10 점수. 정적 검증 불가능한 항목은 `N/A` + 사유. 위반/개선점은 finding 1개로 작성.

**점수 기준:**
- 10 — exemplary, best practice 완전 준수
- 8-9 — solid, 사소한 개선 여지
- 6-7 — 기능적이나 개선 필요
- 4-5 — 눈에 띄는 friction, 사용자 이탈 위험
- 0-3 — 폼 완성 심각하게 저해
- N/A — 정적 분석으로 검증 불가

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding 당) — 폼 완성을 직접 방해
- warning: -1 ~ -2 — 혼란·불안·마찰 유발
- info: 점수 영향 X — 추가 개선 여지

finding 1개당: **severity** · **lens** · **evidence**(노드명·위치·수치) · **fix**(구체 액션) · **form-출처**(방법론 출처).

### Step 8 — Form UX Health Grade 산출

**평균 환산** = (적용 lens 점수 합) / (적용 lens 수) → 0-10

**Grade 환산:**
- 9.0-10 = **A** (Excellent — form friction-free)
- 7.5-8.9 = **B** (Good — minor polish)
- 6.0-7.4 = **C** (Acceptable — needs rework)
- 4.0-5.9 = **D** (Poor — form redesign)
- 0-3.9  = **F** (Critical — 즉시 재설계 필요)

**추가 헤드라인:**
- **Completion Risk**: critical finding 개수 + 가장 심각한 lens 조합 = "어느 필드에서 이탈 확률이 가장 높은지" 한 줄
- **Accessibility Signal**: Lens 5(Help text) · 9(Input type) · 10(Autocomplete) 평균 — WCAG 1.3.1/1.3.5 연관

### Step 9 — 보고서 작성 (각 폼/프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ux-form-review-{form-slug}-{YYYYMMDD-HHmm}.md`
- `{form-slug}`: 폼 이름 kebab-case (예: `login-form`, `signup-form`, `account-setting`)
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 10 — Top-3 Friction 제안

폼 이탈/오류 위험순으로 3개 friction 선정. 단순 스타일 fix 가 아닌 **구조적 개선 방향**.

각 카드 포맷:
- **friction 위치** (필드명 + frame)
- **위반 lens** (lens 번호 + lens명 조합)
- **사용자 영향** (오류·이탈 시나리오)
- **비즈니스 영향** (전환율·완성률)
- **개선 방향** (레이블 교체 / 필드 분리 / 에러 메시지 재작성 / hint 추가 / 버튼 레이블 변경 / 스텝 분리)
- **기대 점수 변화** (lens N → N')
- **노력 규모** (Low/Medium/High)

선정 우선순위:
1. Lens 7(Error message) · 8(Error summary) critical — 에러 후 이탈 직결
2. Lens 2(Label position) critical — placeholder=레이블 패턴
3. Lens 12(Submit button) warning+ — 행동 동사 부재
4. Lens 6(Validation timing) warning+ — onKeyUp 즉시 에러
5. 나머지 critical → warning 순

### Step 11 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로
- Form UX Health Grade + 평균 점수 + critical/warning 개수
- 12 lens 점수 한 줄 요약 (낮은 순 3개 강조)
- Top-3 Friction 필드명 + 한 줄 설명
- Accessibility Signal (Lens 5·9·10 평균)
- 다음 액션 제안 (annotate-design / 사용성 테스트 / 재설계)

### Step 12 — annotate-design 호환 메타 태그 삽입

finding 헤더에 `### {lens명} — score: {N}` 포맷 준수. evidence 에 노드 경로 또는 필드 인덱스 명시하여 `annotate-design` 파싱 가능하게 유지.

## 보고서 구조 (한국어)

```markdown
# Form UX Review: {form name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 폼 타입: {AUTH FORM | ACCOUNT/PROFILE FORM | BUSINESS FORM | MULTI-STEP WIZARD | SEARCH/FILTER FORM | HYBRID}
- 폼 목적: {사용자 인자 또는 추정}
- 추정 페르소나: {역할·목적·기기}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 인라인}
- 방법론: Adam Silver "Form Design Patterns" + Caroline Jarrett "Forms that Work" + Luke Wroblewski "Web Form Design" + GOV.UK Design System + Baymard Institute form research

## 헤드라인
- **Form UX Health Grade: {A-F}** ({평균}/10)
- **Completion Risk**: {가장 위험한 필드 + 원인 한 줄}
- **Accessibility Signal**: Lens 5·9·10 평균 = {n}/10
- 적용 lens: 12 / 12 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 폼이 달성하려는 목표: {...}
- 추정 사용자의 진입 동기: {...}
- 폼을 봤을 때 첫인상: {...}
- 가장 위태로워 보이는 부분: {...}
- 가장 잘 된 부분: {...}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Form Inventory

| # | 필드명(레이블) | 타입 | 필수여부 | Hint text | 에러 상태 | 비고 |
|---|--------------|------|---------|----------|---------|------|
| 1 | ... | ... | ... | ... | ... | ... |

- **Submit button label**: {...}
- **Progress indicator**: {...}
- **Error summary**: {...}
- **Help text 연결 방식**: {...}

## 점수표 (12 Lens)

| # | Lens | 점수 | 비고 |
|---|------|------|------|
| 1 | One thing per page | - | - |
| 2 | Label position | - | - |
| 3 | Label clarity | - | - |
| 4 | Required field | - | - |
| 5 | Help text | - | - |
| 6 | Validation timing | - | - |
| 7 | Error message | - | - |
| 8 | Error summary | - | - |
| 9 | Input type | - | - |
| 10 | Autocomplete | - | - |
| 11 | Progress indicator | - | - |
| 12 | Submit button | - | - |

## Findings

### {lens명} — score: {N}
- **severity**: critical | warning | info
- **lens**: {번호}. {lens명}
- **evidence**: {필드명 · 노드 경로 · 구체 근거}
- **fix**: {구체 액션}
- **form-출처**: {Adam Silver / Caroline Jarrett / Luke Wroblewski / GOV.UK / Baymard — 챕터/섹션}

{위반/개선점이 있는 항목만 나열}

## Top-3 Friction

### Friction 1 — {필드명} · {lens명}
- **위치**: {필드명} (frame `{nodeId}`)
- **위반 lens**: {번호}. {lens명}
- **사용자 영향**: {오류·이탈 시나리오}
- **비즈니스 영향**: {전환율·완성률 영향}
- **개선 방향**: {레이블 교체 / 필드 분리 / 에러 재작성 / hint 추가 / 버튼 레이블 변경 / 스텝 분리}
- **기대 점수 변화**: Lens {n} {N} → {N'}
- **노력**: {Low/Medium/High} ({n} weeks)

### Friction 2 — ...
### Friction 3 — ...

## Accessibility Signal

- **Lens 5 (Help text)**: {n}/10 — {aria-describedby 연결 현황}
- **Lens 9 (Input type)**: {n}/10 — {모바일 키보드 최적화 현황}
- **Lens 10 (Autocomplete)**: {n}/10 — {자동완성 지원 현황}
- WCAG 연관: 1.3.1 Info and Relationships · 1.3.5 Identify Input Purpose

## N/A 항목 (정적 분석 한정)
- Lens 6 (Validation timing) 일부: onBlur/onKeyUp 실제 트리거 타이밍은 런타임 실측 필요
- Lens 10 (Autocomplete) 일부: `autocomplete` 속성 값은 코드 접근 없이 완전 확인 불가 (디자인 힌트 기반 추론)

## 다음 단계 (권장 후속)
- 5-8명 사용성 테스트 (Top-3 Friction 가설 검증, 특히 에러 메시지 이해도)
- 분석: form abandonment rate / field-level error rate / time-to-complete per field
- `annotate-design` 스킬로 finding 을 디자인 파일에 시각화
- 재설계 후 동일 12 lens rubric 으로 재평가 (delta 측정)
- 멀티 스텝 폼: `design-ux-flow-review` 로 step 간 flow 추가 평가 권장
```

## 인자

```
/design-ux-form-review <Figma URL | .pen path> [--form "{form name}"] [--step {n}/{total}]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- 옵션 `--form "{...}"`: 폼 이름/목적 명시 (없으면 추정)
- 옵션 `--step {n}/{total}`: 멀티 스텝 폼에서 현재 스텝 위치 (예: `--step 2/4`)
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Figma URL, 로그인 폼
```
/design-ux-form-review https://www.figma.com/design/abc123/EasySeller?node-id=10-200 --form "로그인"
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → 폼 타입 = AUTH FORM → 12 lens 평가 → `./design-reviews/design-ux-form-review-login-form-20260518-1400.md` 생성

### 예시 2 — Pencil, 회원가입 멀티 스텝 (스텝 2)
```
/design-ux-form-review ~/Documents/easyseller.pen --form "회원가입" --step 2/4
```
→ Pencil MCP 체크 → 현재 선택 frame 감지 → 폼 타입 = MULTI-STEP WIZARD → Lens 11(Progress indicator) 집중 → 12 lens 평가 → 보고서 생성

### 예시 3 — Pencil, 계정 설정 폼
```
/design-ux-form-review ~/Documents/easyseller.pen --form "계정 설정"
```
→ Pencil MCP 체크 → 폼 타입 = ACCOUNT/PROFILE FORM → Lens 4·5·9·10 가중 평가 → 보고서 생성

### 예시 4 — MCP 미연결
```
/design-ux-form-review https://www.figma.com/design/abc/EasySeller?node-id=10-200
```
→ ToolSearch 결과 0건 → "Figma MCP 가 연결되어 있지 않습니다." 출력 후 종료

### 예시 5 — stat-front store-manage 폼
```
/design-ux-form-review ~/Documents/easyseller.pen --form "스토어 관리"
```
→ 폼 타입 = BUSINESS FORM → Lens 1·8·11 가중 → 12 lens 평가 → 보고서 생성

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- lens 명은 영어 원어 유지 (One thing per page, Label position, Label clarity, Required field, Help text, Validation timing, Error message, Error summary, Input type, Autocomplete, Progress indicator, Submit button)
- finding 의 evidence/fix 는 필드명·노드 경로·구체 액션 명시
- 보고서는 폼/프레임당 한 파일
- finding 헤더 포맷 `### {lens명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / lens / evidence / fix / form-출처 필드 동일 순서 유지
- Top-3 Friction · Accessibility Signal 은 별도 섹션

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다. evidence 의 필드명 또는 노드 경로에서 위치를 추출해 마커 배치.

워크플로:
```
/design-ux-form-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일 코멘트 직접 게시 — `annotate-design` 책임
- 비폼 화면 UX 평가 — `design-ux-{nielsen,ixdf,lawsofux}-review` 책임
- User flow / step 간 전환 평가 — `design-ux-flow-review` 책임
- 시각·감성 UI 평가 — `design-ui-*-review` 책임
- 라이브 사이트 audit / 실측 — gstack `/design-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만

## 추상화 단계 비교 (폼 관련 스킬)

| 스킬 | 추상화 단계 | 평가 단위 | 폼 coverage |
|------|-----------|----------|------------|
| `design-ux-form-review` | **L1 Skeleton / 폼 전용** | **단일 폼 프레임** | **12 lens 완전** |
| `design-ux-flow-review` | L2 Structure | multi-step flow | C3(Error validation) 부분만 |
| `design-ux-nielsen-review` | L1 Skeleton | 단일 frame | Error prevention·Help 부분만 |
| `design-ux-ixdf-review` | L1 Skeleton-Structure | 단일 frame | Words·Behavior 부분만 |

## 참고 자료

- **Adam Silver "Form Design Patterns"** — https://www.smashingmagazine.com/printed-books/form-design-patterns/
  - Lens 1(One thing per page), 2(Label position), 4(Required field), 5(Help text), 8(Error summary), 10(Autocomplete), 12(Submit button)
- **Caroline Jarrett "Forms that Work"** — Jarrett & Gaffney, Morgan Kaufmann 2009
  - Lens 2(Label position), 3(Label clarity), 7(Error message), 12(Submit button)
- **Luke Wroblewski "Web Form Design"** — Rosenfeld Media 2008, https://www.lukew.com/resources/web_form_design.asp
  - Lens 2(Label position), 6(Validation timing), 9(Input type), 11(Progress indicator)
- **GOV.UK Design System — Forms** — https://design-system.service.gov.uk/patterns/question-pages/
  - Lens 3(Label clarity), 4(Required field), 7(Error message), 8(Error summary), 12(Submit button)
- **Baymard Institute Form Research** — https://baymard.com/blog/form-field-usability
  - Lens 6(Validation timing), 7(Error message), 9(Input type), 10(Autocomplete)
- **WCAG 2.1** — 1.3.1 Info and Relationships · 1.3.5 Identify Input Purpose
  - Lens 5(Help text), 9(Input type), 10(Autocomplete)
