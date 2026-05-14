---
name: design-ux-ixdf-review
description: Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 IxDF "The Basics of User Experience Design" 의 UX 12개 항목(5 UX Factors + 4 Usability Characteristics + 2 Interaction Dimensions: Words·Behavior)으로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. UX Health Grade(A-F) 헤드라인 + Top-3 Rethink 재설계 제안. 사용자가 "IxDF UX 12 항목 리뷰", "IxDF UX 평가", "UX ixdf 리뷰", "/design-ux-ixdf-review" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 IxDF UX 기반 리뷰를 요청할 때 사용.
---

# design-ux-ixdf-review

Interaction Design Foundation 의 "The Basics of User Experience Design" 방법론에서 **UX 카테고리 12개 항목**을 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 화면이 사용자의 목적 달성·학습·신뢰·접근성·행동 예측 관점에서 가치를 전달하는가? 재설계한다면 어떻게?"

## 평가 항목 (12개)

### A. 5 UX Factors (Peter Morville Honeycomb — UX 담당)

| # | Factor | 평가 기준 | 정적 검증 |
|---|--------|----------|----------|
| 1 | Useful | 실제 사용자 문제 해결 신호 (가치 제안 명확, 핵심 기능 가시) | Partial |
| 2 | Usable | 직관적 인터페이스, 인지 부하, 일관된 패턴 | Yes |
| 3 | Findable | 정보 구조 / 탐색 / 검색 / 라벨링 / 가시성 | Yes |
| 4 | Credible | 전문적 비주얼, 신뢰 신호(보안·연락처·정책), 깨진 요소 없음 | Yes |
| 5 | Accessible | 색대비 4.5:1, 텍스트 16px+, 키보드 hint, alt-text 가시 | Yes |

> **참고:** Valuable 은 UX/UI 공통 가치를 포함하므로 본 스킬에서 분리 평가함. Desirable 은 시각·감성 항목으로 `design-ui-ixdf-review` 담당.

### B. 4 Usability Characteristics (ISO 9241-11 — UX 담당)

| # | Characteristic | 평가 기준 | 정적 검증 |
|---|----------------|----------|----------|
| 6 | Effectiveness | 1차 목표 달성 가능 (1차 CTA + 진입 경로 명확) | Yes |
| 7 | Efficiency | 단계 수 / 클릭 수 / 단축 경로 / 자동완성 / 스마트 디폴트 | Partial |
| 8 | Error Tolerance | 검증·확인·취소·되돌리기·에러 메시지 구체성 | Yes |
| 9 | Ease of Learning | 첫 사용 친화성·온보딩·관행 부합·진보적 노출 | Yes |

> **참고:** Engagement 는 시각·미세 인터랙션 만족도 항목으로 `design-ui-ixdf-review` 담당.

### C. 2 Interaction Dimensions (Crampton Smith & Silver — UX 담당)

| # | Dimension | 평가 기준 | 정적 검증 |
|---|-----------|----------|----------|
| 10 | Words | 마이크로카피·라벨 구체성·일관성·전문 용어 제거·말투 일관 | Yes |
| 11 | Behavior | 액션 결과 예측 가능·상태 가시성·피드백 신호·일관된 패턴 | Yes |

> **참고:** Visual Representations·Physical Space·Time 은 `design-ui-ixdf-review` 담당.

### D. Valuable (공통 기준 — 양쪽 포함)

| # | Factor | 평가 기준 | 정적 검증 |
|---|--------|----------|----------|
| 12 | Valuable | 사용자 가치 + 비즈니스 가치 (CTA·전환 경로 명확) | Partial |

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "IxDF UX 리뷰", "UX 12항목 평가", "ixdf ux audit", "UX rethink", "종합 UX 진단" 등을 요청할 때
- Words(마이크로카피), Behavior(액션 결과 예측), Findable(정보 구조), Accessible(접근성) 등 사용성·탐색성 중심 진단이 필요할 때
- 리디자인 전 UX Health 점수 + 재설계 방향을 받고 싶을 때

## Do Not Use

- 시각·감성·UI 레이어 평가(Desirable·Engagement·Visual Representations·Physical Space·Time) → `design-ui-ixdf-review`
- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 단일 휴리스틱 평가:
  - Nielsen 9 휴리스틱 → `design-ux-nielsen-review`
  - UX 23 행동·인지 법칙 → `design-ux-lawsofux-review`
  - 이커머스 UX → `design-ux-ecommerce-review`
- 라이브 사이트 audit → gstack `/design-review`

**Do-Not-Use 항목 명확화 (양쪽 IxDF 스킬 교차 참조):**
Words(microcopy)·Behavior(액션 결과 예측 가능성) 은 design-ux-ixdf-review 책임. Visual Representations·Physical Space·Time 은 design-ui-ixdf-review 책임. 헷갈리면 spec 매핑 참조.

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동을 활성화하거나 Figma 데스크탑 앱의 Dev Mode MCP 를 설치한 뒤 다시 시도해주세요." |
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

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

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
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 폰트/컬러/사이즈 팔레트 추출

### Step 4 — Classifier (디자인 타입 + 추정 페르소나)

수집된 프레임 1장을 보고 분류:

- **MARKETING/LANDING** — hero·컨버전 중심
- **APP UI** — 워크스페이스·데이터 dense·태스크 중심
- **ONBOARDING/FORM** — 가입·결제·설정 흐름의 단일 스텝
- **CONTENT/READER** — 본문 소비형 (블로그·뉴스·문서)
- **HYBRID** — 위 카테고리 혼재

분류 결과 + 추정 페르소나 1-2명(역할·목적·기기 컨텍스트)을 보고서 메타에 기록. UX 관점 카테고리별 가중치 미세 조정:
- 마케팅: Useful / Words / Credible 가중↑
- 앱 UI: Effectiveness / Efficiency / Behavior 가중↑
- 폼: Error Tolerance / Words / Ease of Learning 가중↑
- 콘텐츠: Findable / Ease of Learning / Accessible 가중↑

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 화면이 전달하는 것: [한 문장]
- 추정 사용자 목적: [한 문장]
- 내 시선이 가장 먼저 가는 3개: [1], [2], [3]
- 한 단어 요약: [단어]
- 인상 메모: [무엇이 두드러지는가 — 긍정/부정 구체적으로]
```

이 섹션은 의견을 강하게 적는다. 진단가는 헤지하지 않는다.

### Step 6 — Inferred Design System (Phase 2)

수집된 노드 트리 + 속성에서 다음 추출:

- **Fonts**: font family 목록 + 출현 빈도
- **Colors**: 전체 컬러 팔레트 + semantic 사용 여부
- **Type scale**: fontSize 분포 + 스케일 비율
- **Spacing**: 자주 등장 padding/gap + 스케일 일치
- **Touch targets**: 버튼/링크 최소 크기 (44×44px 기준)
- **Components**: 식별 가능한 반복 컴포넌트 목록

### Step 7 — IxDF UX 12항목 평가 (Phase 3)

각 항목마다 0-10 점수. 정적 검증 불가능한 항목은 `N/A` + 사유. 위반/개선점은 finding 1개로 작성: **severity** (critical / warning / info), **evidence** (노드 경로/이름/수치), **fix** (구체 액션), **참고** (IxDF 문서/장 참조).

**점수 기준:**
- 10 — exemplary, 업계 best-in-class
- 8-9 — solid, 사소한 polish 만
- 6-7 — 기능적이나 개선 여지
- 4-5 — 눈에 띄는 문제
- 0-3 — 사용자 경험을 적극 해침
- N/A — 정적 분석으로 검증 불가

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding 당)
- warning: -1 ~ -2
- info: 점수 영향 X, 노트만

### Step 8 — UX Health Grade 산출

**평균 환산** = (적용 항목 점수 합) / (적용 항목 수) → 0-10

**Grade 환산:**
- 9.0-10 = **A** (Excellent — best-in-class)
- 7.5-8.9 = **B** (Good — minor polish)
- 6.0-7.4 = **C** (Acceptable — needs work)
- 4.0-5.9 = **D** (Poor — significant redesign)
- 0-3.9  = **F** (Critical — overhaul needed)

**추가 헤드라인:**
- **Utility + Usability 공식**: "right features 존재(추정)" + "4 Usability Characteristics 평균" = **Usefulness 한 줄 평가**

### Step 9 — Top-3 Rethink 제안

전체 finding 중에서 high-impact 3개를 골라 Rethink 카드로 작성. 단순 fix 가 아닌 **재설계 방향**.

각 카드 포맷:
- **현재 문제** (frameworks violated + evidence)
- **사용자 영향** + **비즈니스 영향**
- **제안 솔루션** (구체 컴포넌트/레이아웃 변경)
- **기대 점수 변화** (항목 N → N')
- **노력 규모** (Low/Medium/High, 1-4 weeks 단위 추정)

선정 우선순위:
1. critical 우선
2. critical 부족하면 warning 으로 채움
3. 1차 CTA / 진입 직후 마주치는 요소 / 위반 항목 수 순

### Step 10 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ux-ixdf-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 11 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 UX Health Grade + 평균 점수 + critical/warning 개수 한 줄 요약

## 보고서 구조 (한국어)

```markdown
# IxDF UX Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 디자인 타입: {MARKETING/LANDING | APP UI | ONBOARDING/FORM | CONTENT/READER | HYBRID}
- 추정 페르소나: {역할·목적·기기}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: IxDF "The Basics of User Experience Design" — UX 12항목 (5 Factors + 4 Usability + 2 Interaction Dimensions)

## 헤드라인
- **UX Health Grade: {A-F}** ({평균}/10)
- **Usefulness**: Utility ({Y/Partial/N}) + Usability ({평균}/10) = {한 줄 평가}
- 적용 항목: {applied}/12 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 화면이 전달하는 것: {...}
- 추정 사용자 목적: {...}
- 내 시선이 가장 먼저 가는 3개: {1}, {2}, {3}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Inferred Design System
- **Fonts** ({n}종): {목록 + 빈도}
- **Colors** ({n}종): {팔레트 + semantic 사용 여부}
- **Type scale**: {분포 + 비율}
- **Spacing**: {자주 등장 값 + 스케일}
- **Touch targets**: {최소/평균 크기 + 44px 기준 통과 여부}
- **Components**: {반복 컴포넌트 목록}

## 점수표 (12 항목)

### A. 5 UX Factors

| # | Factor | 점수 | 비고 |
|---|--------|------|------|
| 1 | Useful | - | - |
| 2 | Usable | - | - |
| 3 | Findable | - | - |
| 4 | Credible | - | - |
| 5 | Accessible | - | - |

### B. 4 Usability Characteristics

| # | Characteristic | 점수 | 비고 |
|---|----------------|------|------|
| 6 | Effectiveness | - | - |
| 7 | Efficiency | - | - |
| 8 | Error Tolerance | - | - |
| 9 | Ease of Learning | - | - |

### C. 2 Interaction Dimensions (UX)

| # | Dimension | 점수 | 비고 |
|---|-----------|------|------|
| 10 | Words | - | - |
| 11 | Behavior | - | - |

### D. Valuable

| # | Factor | 점수 | 비고 |
|---|--------|------|------|
| 12 | Valuable | - | - |

## Findings

### {항목명} — score: {N}
- **severity**: critical | warning | info
- **evidence**: {노드 경로/이름/수치}
- **fix**: {구체 액션}
- **참고**: IxDF "The Basics of User Experience Design" — {챕터/섹션}

{위반/개선점이 있는 항목만 나열}

## Top-3 Rethink 제안

### Proposal 1 — {항목명} 재설계
- **현재 문제**: {frameworks violated + evidence}
- **사용자 영향**: {...}
- **비즈니스 영향**: {...}
- **제안 솔루션**: {...}
- **기대 점수 변화**: {항목} {N} → {N'}
- **노력**: {Low/Medium/High} ({n} weeks)

### Proposal 2 — ...
### Proposal 3 — ...

## N/A 항목 (정적 분석 한정)
- Useful (1) 일부: 실제 사용자 검증·analytics 필요 (정적 검증은 가치 제안 가시성 한정)
- Efficiency (7) 일부: 실제 태스크 완료 시간 측정 불가
- Valuable (12) 일부: 비즈니스 KPI 정합성은 별도 데이터 필요

## 다음 단계 (권장 후속 리서치)
- 5-8명 사용성 테스트 (Top-3 Rethink 가설 검증)
- 카드 소팅 (정보 구조 재설계 입력)
- 분석: 진입 클릭 분포 / 에러 발생 지점 / 태스크 완료율
```

## 인자

```
/design-ux-ixdf-review <Figma URL | .pen path>
```

- 위치 인자 1개만 필수
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- 옵션 인자 없음 (간결 디폴트 우선)

## 예시

### 예시 1 — Figma URL (단일 프레임)
```
/design-ux-ixdf-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → 분류 → First Impression → Design System 추출 → UX 12항목 평가 → Top-3 Rethink → `./design-reviews/design-ux-ixdf-review-checkout-screen-20260514-1130.md` 생성

### 예시 2 — Pencil 멀티 프레임
```
/design-ux-ixdf-review ~/Documents/myapp.pen
```
→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택된 3개 프레임 감지 → 각 프레임 평가 → 3개 파일 생성

### 예시 3 — MCP 미연결
```
/design-ux-ixdf-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → 안내 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 항목명은 영어 원어 유지 (Findable, Error Tolerance, Words, Behavior 등)
- finding 의 evidence/fix 는 구체적 노드명·수치·액션 명시
- 보고서는 한 프레임당 한 파일
- finding 헤더 포맷 `### {항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)
- Top-3 Rethink Proposal 은 별도 섹션 (annotate-design 파싱 범위 밖)

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ux-ixdf-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 라이브 사이트 audit / 인터랙션 / perf 실측 — gstack `/design-review` 책임
- 시각·감성 UI 레이어 평가 (Desirable, Engagement, Visual Representations, Physical Space, Time) — `design-ui-ixdf-review` 책임
- 단일 휴리스틱 평가 — 각 전용 스킬 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인 (별도 references 디렉터리 없음)
- 방법론 출처: Interaction Design Foundation — "The Basics of User Experience Design"
- 5 UX Factors (UX 담당): Peter Morville — User Experience Honeycomb (Useful/Usable/Findable/Credible/Accessible/Valuable)
- 4 Usability Characteristics (UX 담당): ISO 9241-11 (Effectiveness/Efficiency/Error Tolerance/Ease of Learning)
- 2 Interaction Dimensions (UX 담당): Gillian Crampton Smith & Kevin Silver (Words/Behavior)
- 대응 UI 스킬: `design-ui-ixdf-review` (Desirable/Engagement/Visual Representations/Physical Space/Time)
