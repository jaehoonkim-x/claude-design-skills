---
name: design-ux-microcopy-review
review-level: L1 Skeleton
description: "[L1 Skeleton] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임 내 모든 TEXT 노드를 정적 추출하여 UX writing 8 lens rubric — Button Copy · Error Message · Empty State · Form Label · Voice & Tone · Reading Level · CTA Hierarchy · i18n Readiness — 으로 마이크로카피 품질을 분석하고 한국어 마크다운 리뷰 보고서를 생성. Microcopy Health Grade(A-F) 헤드라인 + per-lens 점수 + Top-3 Findings 출력. 기존 11종 리뷰 스킬 중 마이크로카피 전용 스킬이 없어 신설. design-ui-critic-review 의 1 lens 부분 커버 → stat-front 의 모든 form/error/empty 페이지에 직접 적용 가능. 사용자가 \"마이크로카피 리뷰\", \"UX writing 평가\", \"버튼 카피 검토\", \"에러 메시지 리뷰\", \"빈 상태 카피\", \"폼 라벨 점검\", \"CTA 카피 리뷰\", \"i18n 텍스트 점검\", \"microcopy audit\", \"ux writing review\", \"/design-ux-microcopy-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 텍스트/카피 품질 분석을 요청할 때 사용."
---

# design-ux-microcopy-review

**Review Level**: L1 Skeleton — UX writing / microcopy 정적 분석 (단일 프레임 기준).

프레임 내 모든 TEXT 노드를 추출하고 UX writing 8 lens rubric 으로 마이크로카피 품질을 평가한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 화면의 텍스트가 사용자에게 명확하고 행동을 이끌며 일관성 있게 쓰여 있는가? 고쳐야 한다면 어떤 카피부터?"

## 평가 항목 — 8 Lens

### Lens 1. Button Copy

| 기준 | 세부 |
|------|------|
| Action verb 시작 | 첫 단어가 동사인가 ("저장", "시작하기", "다운로드", "Get started") |
| Benefit-first | 버튼 자체가 행동 결과/혜택을 암시하는가 |
| ≤ 4 단어 | 5단어 이상이면 warning |
| "OK / Cancel" 회피 | 모달·다이얼로그에서 컨텍스트 없는 OK·Cancel 금지 |

### Lens 2. Error Message

| 기준 | 세부 |
|------|------|
| Blame X | "당신이 틀렸습니다" 류의 사용자 책임 전가 어조 금지 |
| Cause 명시 | 무슨 일이 일어났는지 구체적으로 설명 |
| Recovery action | 사용자가 다음에 해야 할 행동 제시 |
| Plain language | 기술 용어·에러 코드 노출 금지 |

### Lens 3. Empty State

| 기준 | 세부 |
|------|------|
| Clarity | 왜 비어 있는지 설명 |
| Tone | 실망감 최소화, 긍정적·격려적 어조 |
| Action | 빈 상태를 해소할 primary CTA 제공 |

Clarity + Tone + Action = "3-force" 모두 갖춰야 합격.

### Lens 4. Form Label

| 기준 | 세부 |
|------|------|
| 위 배치 | 라벨이 input 위에 위치 (placeholder-only 금지) |
| Placeholder ≠ Label | placeholder 가 라벨 역할 대체 금지 |
| Required mark | 필수 필드에 * 또는 "(필수)" 표시 |
| Help text | 형식 예시·제약 안내 존재 여부 |

### Lens 5. Voice & Tone

| 기준 | 세부 |
|------|------|
| 페이지 일관성 | 존댓말/반말 혼용, 브랜드 톤 일탈 없음 |
| 상황별 적응 | 에러는 공감, 성공은 축하, 경고는 차분 — 상황 감정 톤 매칭 |

### Lens 6. Reading Level

| 기준 | 세부 |
|------|------|
| Hemingway grade 6-8 | 가독성 지수 (영문 기준; 한국어는 문장 길이·어휘 단순성으로 대체 평가) |
| 문장 ≤ 20 단어 | 한 문장 단어 수 초과 시 warning |
| Passive ≤ 10% | 수동태 문장 비율 (영문) |

### Lens 7. CTA Hierarchy

| 기준 | 세부 |
|------|------|
| Primary 1개 | 화면당 primary CTA 가 단 1개인가 |
| Secondary 명확 | secondary action 텍스트가 primary 와 혼동되지 않는가 |
| Verb 강도 매칭 | primary 는 강한 행동 동사, secondary 는 소극적 동사 |

### Lens 8. i18n Readiness

| 기준 | 세부 |
|------|------|
| 길이 변동 여유 | 텍스트 컨테이너 여유 공간 ≥ 30% (영→독 최대 35% 길어짐) |
| 직역 risk | 관용어·축약어·문화 특정 참조 존재 여부 |
| 단수·복수 | 하드코딩된 "1개의 항목" 류의 복수형 미고려 패턴 |

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일을 주고 "마이크로카피 리뷰", "버튼 카피 점검", "에러 메시지 평가", "UX writing audit", "i18n 텍스트 리뷰" 등을 요청할 때
- form / error / empty state 페이지의 텍스트 품질 진단이 필요할 때
- 신규 화면 출시 전 UX writing 체크리스트 검토가 필요할 때
- 기존 11종 리뷰(design-ui-critic-review 1개 lens 제외)에서 마이크로카피 전용 분석이 부족할 때

## Do Not Use

- 시각 레이아웃·색상·타이포 위계 평가 → `design-ui-*-review`
- 사용성·IA·flow 구조 평가 → `design-ux-{ixdf,nielsen,flow}-review`
- 멀티 프레임 user flow 단위 평가 → `design-ux-flow-review`
- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 라이브 사이트 전체 audit → gstack `/design-review`

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
- `--lang ko|en|...`: 주 언어 명시 (미지정 시 텍스트 내용에서 자동 감지)
- `--lens 1,2,3,...`: 적용 lens 명시 (1-8 콤마 구분). 미지정 시 전체 8 lens 적용.

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 로 프레임 구조 파악
   - nodeId 미지정 시 현재 선택 프레임 사용. 멀티 프레임 자동 감지
2. 각 frame 에 대해:
   - `mcp__claude_ai_Figma__get_design_context(fileKey, nodeId=frame.id)` 로 deep 트리 + 모든 TEXT 노드 수집
   - `mcp__claude_ai_Figma__get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고 이미지 1장 확보

figma-console 사용 시:
- `mcp__figma-console__figma_get_file_data(fileKey)` 로 파일 구조 파악
- `mcp__figma-console__figma_execute(...)` 로 TEXT 노드 트리 순회 + 내용 추출

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별 → 멀티 프레임 자동 감지
   - 선택이 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id])` 로 deep 노드 트리 + TEXT 노드 수집
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷 (라벨 위치 확인용)
   - `mcp__pencil__get_screenshot(node_id=frame_id)` 로 이미지 1장 확보
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property="text")` 로 텍스트 팔레트 추출

### Step 4 — Classifier (화면 타입 + 추정 페르소나)

수집된 프레임과 TEXT 노드 목록을 보고 화면 타입 분류:

- **FORM** — 입력 필드·라벨·submit CTA 중심 (로그인·회원가입·설정·결제)
- **ERROR / FEEDBACK** — 에러·경고·알림·toast·validation 중심
- **EMPTY STATE** — 데이터 없음·첫 방문·검색 결과 0건 화면
- **DASHBOARD / DATA** — 지표·표·통계 중심, 액션 CTA 보조
- **ONBOARDING / MARKETING** — hero copy·value proposition·설명 중심
- **HYBRID** — 위 카테고리 혼재

분류 결과 + 추정 페르소나 1-2명(역할·목적·기기 컨텍스트)을 보고서 메타에 기록.

**lens 가중치 미세 조정:**
- FORM: Lens 4(Form Label)·Lens 2(Error Message)·Lens 7(CTA Hierarchy) 가중↑
- ERROR/FEEDBACK: Lens 2(Error Message)·Lens 5(Voice & Tone) 가중↑
- EMPTY STATE: Lens 3(Empty State)·Lens 1(Button Copy) 가중↑
- DASHBOARD/DATA: Lens 7(CTA Hierarchy)·Lens 6(Reading Level) 가중↑
- ONBOARDING/MARKETING: Lens 1(Button Copy)·Lens 7(CTA Hierarchy)·Lens 8(i18n) 가중↑

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 화면의 텍스트가 전달하는 전체 톤: [한 문장]
- 카피 감성 키워드: [2-3 단어]
- 가장 눈에 띄는 텍스트 3개: [1], [2], [3]
- 한 단어 요약: [단어]
- 인상 메모: [카피 관점에서 무엇이 두드러지는가 — 긍정/부정 구체적으로]
```

이 섹션은 의견을 강하게 적는다. 진단가는 헤지하지 않는다.

### Step 6 — Inferred Microcopy Inventory (Phase 2)

수집된 TEXT 노드 전체를 카테고리별로 분류·목록화:

| 카테고리 | 텍스트 샘플 | 노드 수 | 비고 |
|---------|------------|--------|------|
| Button / CTA | "저장", "다음으로" | N | - |
| Error / Validation | "이메일 형식이 올바르지 않습니다" | N | - |
| Empty State | "아직 데이터가 없습니다" | N | - |
| Form Label | "이메일", "비밀번호 *" | N | - |
| Placeholder | "이메일을 입력하세요" | N | - |
| Heading / Sub-heading | "로그인", "계정 설정" | N | - |
| Help Text / Tooltip | "8자 이상, 영문+숫자 조합" | N | - |
| Body / Description | "서비스 약관에 동의합니다" | N | - |
| Toast / Alert | "저장되었습니다", "연결 실패" | N | - |
| Navigation / Tab | "대시보드", "설정" | N | - |
| 기타 | ... | N | - |

- 총 TEXT 노드 수 기록
- 언어 감지 결과 기록 (한국어/영문/혼용)
- i18n 대상 여부 판단

### Step 7 — 8 Lens 평가 (Phase 3)

각 lens 마다 0-10 점수. 해당 카테고리 텍스트가 0건이면 `N/A` + 사유. 위반/개선점은 finding 1개로 작성.

**점수 기준:**
- 10 — exemplary, UX writing best-in-class
- 8-9 — solid, 사소한 카피 개선만 필요
- 6-7 — 기능적이나 일부 위반 존재
- 4-5 — 눈에 띄는 카피 문제, 사용자 혼란 유발
- 0-3 — 카피가 사용자 경험을 적극 해침
- N/A — 해당 텍스트 카테고리가 화면에 없음

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding 당)
- warning: -1 ~ -2
- info: 점수 영향 X, 노트만

**Lens별 심층 평가 기준:**

**Lens 1 — Button Copy:**
- 동작 동사 시작 여부를 모든 button/CTA 텍스트에 대해 검증
- "확인", "OK", "예", "아니오" 등 컨텍스트 없는 단어 = critical
- 5단어 이상 = warning
- 혜택/결과 미암시 = warning

**Lens 2 — Error Message:**
- "잘못된 입력입니다" 류의 blame 어조 = critical
- 원인 없이 결과만 서술 ("오류가 발생했습니다") = warning
- 복구 방법 미제시 = warning
- 에러 코드(ERR_500, null pointer 등) 노출 = critical

**Lens 3 — Empty State:**
- 3-force(Clarity + Tone + Action) 모두 없으면 critical
- 1개 빠질 때마다 warning 1건
- "데이터가 없습니다" 단독 = Clarity만 = critical (Tone·Action 결여)

**Lens 4 — Form Label:**
- placeholder 가 라벨 역할 대체 시 critical (포커스 시 라벨 사라짐)
- 라벨이 input 아래 배치 = critical
- 필수 필드 * 미표시 = warning
- help text 부재로 format 불명확 = warning (날짜·전화번호 등)

**Lens 5 — Voice & Tone:**
- 동일 화면에서 존댓말/반말 혼용 = critical
- 에러 상태에서 축하 어조 / 성공 상태에서 경고 어조 = critical
- 브랜드 가이드 일탈 (딱딱함 vs 친근함 혼재) = warning

**Lens 6 — Reading Level:**
- 한국어: 문장 20단어 초과 = warning; 30단어 초과 = critical
- 영어: Hemingway grade 9+ = warning; 12+ = critical
- 한 문장 내 수식절 3+ 겹침 = warning
- 수동태 집중 사용 = warning

**Lens 7 — CTA Hierarchy:**
- primary CTA 가 화면에 2개 이상 = critical
- secondary 와 primary 가 동일 강도 동사 = warning
- CTA 없는 화면(dead-end) = critical

**Lens 8 — i18n Readiness:**
- 컨테이너 여유 공간 < 30% = warning (영→독 팽창 대비)
- 하드코딩된 단수형("1개의 알림") = warning
- 문화 특정 관용어·축약어 = warning
- 직역 risk 높은 고유명사 혼재 = info

### Step 8 — Microcopy Health Grade 산출

**평균 환산** = (적용 lens 점수 합) / (적용 lens 수) → 0-10

**Grade 환산:**
- 9.0-10 = **A** (Excellent — UX writing best-in-class)
- 7.5-8.9 = **B** (Good — minor copy polish)
- 6.0-7.4 = **C** (Acceptable — copy rework needed)
- 4.0-5.9 = **D** (Poor — significant UX writing redesign)
- 0-3.9  = **F** (Critical — copy overhaul, 사용자 혼란 위험)

**추가 헤드라인:**
- **Copy Clarity 공식**: Button Copy(1) + Error Message(2) + CTA Hierarchy(7) 평균 = **Action Clarity 한 줄 평가**
- **Tone Consistency**: Voice & Tone(5) 단독 점수 = **브랜드 톤 일관성 한 줄 평가**

### Step 9 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ux-microcopy-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 10 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 Microcopy Health Grade + 평균 점수 + critical/warning 개수 한 줄 요약
- Action Clarity + Tone Consistency 한 줄 평가
- microcopy 이외 UX 평가가 필요하면 `design-ux-ixdf-review` 또는 `design-ux-flow-review` 병행 권장

### Step 11 — Top-3 Findings (finding 3건 이상 시)

critical → warning 순서로, 사용자 혼란 영향이 가장 큰 finding 3개를 픽업하여 제안 카드 작성:

각 카드 포맷:
- **현재 카피** (lens + evidence + 실제 텍스트)
- **문제 원인** (어떤 UX writing 원칙 위반)
- **사용자 영향** (혼란·이탈·신뢰 손실 시나리오)
- **개선 카피 제안** (구체 대안 문장)
- **기대 점수 변화** (lens N → N')
- **노력 규모** (Low/Medium/High)

선정 우선순위:
1. Error Message blind (사용자가 복구 방법을 알 수 없는 경우)
2. Placeholder-only label (폼 포커스 시 정보 손실)
3. OK/Cancel 모달 (컨텍스트 없는 확인/취소)
4. primary CTA 2개 이상 (선택 마비)
5. 그 외 critical → warning 순

### Step 12 — (선택) 언어별 Hemingway 간이 분석

`--lang en` 이거나 영문 텍스트 ≥ 50% 인 경우, 주요 body 문장을 샘플링하여 Hemingway 지표 간이 계산:
- 문장 평균 단어 수
- 복잡 단어 비율 (3음절 이상)
- 수동태 비율
- 추정 Hemingway grade (계산식: 0.39×평균문장단어수 + 11.8×평균음절수 − 15.59 근사)
- 권장 grade 대비 평가

## 보고서 구조 (한국어)

```markdown
# Microcopy Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 화면 타입: {FORM | ERROR/FEEDBACK | EMPTY STATE | DASHBOARD/DATA | ONBOARDING/MARKETING | HYBRID}
- 주 언어: {한국어 | 영문 | 혼용}
- 추정 페르소나: {역할·목적·기기}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: UX Writing 8 Lens Rubric (Button Copy · Error Message · Empty State · Form Label · Voice & Tone · Reading Level · CTA Hierarchy · i18n Readiness)

## 헤드라인
- **Microcopy Health Grade: {A-F}** ({평균}/10)
- **Action Clarity**: Button Copy ({N}/10) + Error Message ({N}/10) + CTA Hierarchy ({N}/10) = {한 줄 평가}
- **Tone Consistency**: Voice & Tone ({N}/10) = {한 줄 평가}
- 적용 lens: {applied}/8 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 화면의 텍스트가 전달하는 전체 톤: {...}
- 카피 감성 키워드: {...}
- 가장 눈에 띄는 텍스트 3개: {1}, {2}, {3}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Microcopy Inventory

| 카테고리 | 텍스트 샘플 | 노드 수 | 비고 |
|---------|------------|--------|------|
| Button / CTA | ... | - | - |
| Error / Validation | ... | - | - |
| Empty State | ... | - | - |
| Form Label | ... | - | - |
| Placeholder | ... | - | - |
| Heading / Sub-heading | ... | - | - |
| Help Text / Tooltip | ... | - | - |
| Body / Description | ... | - | - |
| Toast / Alert | ... | - | - |
| Navigation / Tab | ... | - | - |
| 기타 | ... | - | - |
| **합계** | - | **{N}** | - |

## 점수표 (8 Lens)

| # | Lens | 점수 | 비고 |
|---|------|------|------|
| 1 | Button Copy | - | - |
| 2 | Error Message | - | - |
| 3 | Empty State | - | - |
| 4 | Form Label | - | - |
| 5 | Voice & Tone | - | - |
| 6 | Reading Level | - | - |
| 7 | CTA Hierarchy | - | - |
| 8 | i18n Readiness | - | - |

## Findings

### {항목명} — score: {N}
- **severity**: critical | warning | info
- **lens**: {1 Button Copy | 2 Error Message | 3 Empty State | 4 Form Label | 5 Voice & Tone | 6 Reading Level | 7 CTA Hierarchy | 8 i18n Readiness}
- **evidence**: {노드 경로/이름 · 실제 텍스트 · 수치}
- **fix**: {구체 카피 수정 액션 또는 대안 문장}
- **참고**: {출처 — Hemingway App / Microcopy Complete UX Writing Guide / Checklist Design / Supercharge Microcopy / Setproduct Empty State}

{위반/개선점이 있는 lens 만 나열}

## Top-3 Findings (finding 3건 이상 시)

### Finding 1 — {lens + 항목명}
- **현재 카피**: "{실제 텍스트}" (lens: {N})
- **문제 원인**: {위반 원칙}
- **사용자 영향**: {...}
- **개선 카피 제안**: "{대안 문장}"
- **기대 점수 변화**: Lens {N} → {N'}
- **노력**: {Low/Medium/High}

### Finding 2 — ...
### Finding 3 — ...

## N/A 항목 (해당 텍스트 카테고리 없음)
- {lens 번호 + 이름}: 해당 화면에 {카테고리} 텍스트 없음

## 다음 단계 (권장 후속)
- `annotate-design` 스킬로 finding 을 디자인 파일에 시각 코멘트 부착
- `design-ux-flow-review` 로 flow 단위 마이크로카피 흐름 진단
- `design-ux-ixdf-review` 로 UX 12항목(Words·Behavior 포함) 보완 평가
- 실 사용자 5-명 모더레이션 테스트: 에러 복구 행동 관찰
- Hemingway App (https://hemingwayapp.com/) 에 주요 body copy 붙여넣기 검증
```

## 인자

```
/design-ux-microcopy-review <Figma URL | .pen path> [--lang ko|en|...] [--lens 1,2,...,8]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- 옵션 `--lang ko|en|...`: 주 언어 명시 (미지정 시 자동 감지)
- 옵션 `--lens 1,2,...`: 적용 lens 번호 콤마 구분 (미지정 시 전체 8 lens)
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Figma URL (단일 프레임, 전체 lens)
```
/design-ux-microcopy-review https://www.figma.com/design/abc123XYZ/EasySeller?node-id=42-1024
```
→ Figma MCP 체크 → `get_design_context` 로 TEXT 노드 전체 추출 → 화면 타입 = FORM → 8 lens 평가 → `./design-reviews/design-ux-microcopy-review-login-form-20260518-1430.md` 생성

### 예시 2 — Pencil 멀티 프레임, 에러/폼 lens 집중
```
/design-ux-microcopy-review ~/Documents/myapp.pen --lens 2,4,5
```
→ Pencil MCP 체크 → `get_editor_state` 로 3개 프레임 감지 → Lens 2(Error)·4(Form Label)·5(Voice & Tone) 만 평가 → 3개 파일 생성

### 예시 3 — 영문 카피, Reading Level 중심
```
/design-ux-microcopy-review https://www.figma.com/design/xyz/LandingPage?node-id=10-200 --lang en --lens 1,6,7,8
```
→ Figma MCP 체크 → 영문 텍스트 감지 → Hemingway 간이 분석 포함 → Lens 1·6·7·8 평가 → 보고서 생성

### 예시 4 — 빈 상태 화면 전용
```
/design-ux-microcopy-review ~/Desktop/empty-states.pen --lens 3,1,5
```
→ Pencil MCP 체크 → 화면 타입 = EMPTY STATE → 3-force(Clarity·Tone·Action) 점검 → Top-3 Findings 중 empty state 카피 개선 우선

### 예시 5 — MCP 미연결
```
/design-ux-microcopy-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 가 연결되어 있지 않습니다. ..." 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- lens 명은 영어 원어 유지 (Button Copy, Error Message, Empty State, Form Label, Voice & Tone, Reading Level, CTA Hierarchy, i18n Readiness)
- finding 의 evidence 에는 **실제 텍스트 문자열** 반드시 포함 (노드명만으로 부족)
- fix 는 추상 방향이 아닌 **구체 대안 카피 또는 수정 액션** 명시
- 보고서는 한 프레임당 한 파일
- finding 헤더 포맷 `### {항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / lens / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다. evidence 필드의 노드 경로/이름에서 nodeId 를 추출해 해당 TEXT 노드 위에 마커 배치.

워크플로:
```
/design-ux-microcopy-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 시각 레이아웃·색상·타이포 위계 평가 — `design-ui-*-review` 책임
- UX flow 구조·IA·dark pattern 평가 — `design-ux-flow-review` 책임
- 라이브 사이트 audit / 인터랙션 실측 — gstack `/design-review` 책임
- 카피 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만
- 번역(localization) 실행 — i18n readiness 정적 진단만

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인 (별도 references 디렉터리 없음)
- **Hemingway App** — 가독성 지수 기준 https://hemingwayapp.com/
- **Microcopy: The Complete UX Writing Guide** — Maria Rosala, Figma Community https://www.figma.com/community/file/1172924220833346044/
- **Checklist Design — UX Copy** — checklist.design 의 카피 체크리스트 https://www.checklist.design/
- **Supercharge Microcopy** — Supercharge Design Blog https://supercharge.design/blog/how-to-write-microcopy-in-ui
- **Empty State UI Design** — Setproduct Blog https://www.setproduct.com/blog/empty-state-ui-design
- 짝 micro 스킬: `design-ux-nielsen-review` (H4 Consistency & Standards 교차), `design-ux-ixdf-review` (Words lens 교차)
- 짝 flow 스킬: `design-ux-flow-review` (Lens C Edge State 교차 — Error/Empty flow 단위)
- 짝 UI 스킬: `design-ui-critic-review` (1 lens 교차 — 본 스킬로 전담 이관)
- annotate-design 연동: finding 포맷 공유로 즉시 파싱 가능
