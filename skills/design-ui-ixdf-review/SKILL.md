---
name: design-ui-ixdf-review
review-level: L0 Surface
description: "[L0 Surface] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 IxDF \"The Basics of User Experience Design\" 의 UI 5개 항목(1 UX Factor: Desirable + 1 Usability: Engagement + 3 Interaction Dimensions: Visual Representations·Physical Space·Time)으로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. 사용자가 \"IxDF UI 5 항목 리뷰\", \"IxDF UI 평가\", \"ixdf ui 리뷰\", \"/design-ui-ixdf-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 IxDF UI 기반 리뷰를 요청할 때 사용."
---

# design-ui-ixdf-review

**Review Level**: L0 Surface — IxDF UI 5항목 (단일 프레임 표면).

Interaction Design Foundation 의 "The Basics of User Experience Design" 방법론에서 **UI 카테고리 5개 항목**을 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 화면이 시각적 매력·공간 구조·시간 상태 표현·감성 인게이지먼트 관점에서 UI 품질을 전달하는가? 재설계한다면 어떻게?"

## 평가 항목 (5개)

### A. 1 UX Factor (UI 담당 — Desirable)

| # | Factor | 평가 기준 | 정적 검증 |
|---|--------|----------|----------|
| 1 | Desirable | 미학적 매력, 감정적 임팩트, 브랜드 표현, 모던함 | Yes |

> **참고:** Useful/Usable/Findable/Credible/Accessible/Valuable 은 `design-ux-ixdf-review` 담당.

### B. 1 Usability Characteristic (UI 담당 — Engagement)

| # | Characteristic | 평가 기준 | 정적 검증 |
|---|----------------|----------|----------|
| 2 | Engagement | 만족스러운 시각·미세 인터랙션 신호 (정적 표현 한정) | Partial |

> **참고:** Effectiveness/Efficiency/Error Tolerance/Ease of Learning 은 `design-ux-ixdf-review` 담당.

### C. 3 Interaction Dimensions (UI 담당)

| # | Dimension | 평가 기준 | 정적 검증 |
|---|-----------|----------|----------|
| 3 | Visual Representations | 아이콘 명확성·타이포 위계·이미지 의미·정보 시각화 | Yes |
| 4 | Physical Space | 터치 타겟 44×44px·모바일 대응·한 손 도달·반응형 신호 | Yes |
| 5 | Time | 진행 표시·skeleton·로딩 상태 디자인 존재 (애니메이션 시간 실측은 N/A) | Partial |

> **참고:** Words(마이크로카피)·Behavior(액션 결과 예측) 는 `design-ux-ixdf-review` 담당.

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "IxDF UI 리뷰", "UI 5항목 평가", "ixdf ui audit", "시각 디자인 평가" 등을 요청할 때
- Desirable(브랜드·감성), Visual Representations(아이콘·타이포 위계), Physical Space(터치 타겟·레이아웃), Time(로딩 상태·진행 표시) 등 UI 레이어 진단이 필요할 때
- 시각 완성도 + UI Health 점수를 받고 싶을 때

## Do Not Use

- 사용성·탐색성·행동 예측·마이크로카피 평가(Useful·Usable·Findable·Credible·Accessible·Valuable·Effectiveness·Efficiency·Error Tolerance·Ease of Learning·Words·Behavior) → `design-ux-ixdf-review`
- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 단일 휴리스틱 평가:
  - Nielsen 1 Aesthetic 휴리스틱 → `design-ui-nielsen-review`
  - Laws of UX 시각·게슈탈트 7법칙 → `design-ui-lawsofux-review`
  - 이커머스 UI → `design-ui-ecommerce-review`
  - 시각 폴리시 10 차원 → `design-ui-polish-review`
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

분류 결과 + 추정 페르소나 1-2명(역할·목적·기기 컨텍스트)을 보고서 메타에 기록. UI 관점 카테고리별 가중치 미세 조정:
- 마케팅: Desirable / Visual Representations 가중↑
- 앱 UI: Physical Space / Time / Engagement 가중↑
- 폼: Physical Space / Time 가중↑
- 콘텐츠: Visual Representations / Desirable 가중↑

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 화면이 전달하는 시각적 인상: [한 문장]
- 브랜드 감성 키워드: [2-3 단어]
- 내 시선이 가장 먼저 가는 3개: [1], [2], [3]
- 한 단어 요약: [단어]
- 인상 메모: [시각적으로 무엇이 두드러지는가 — 긍정/부정 구체적으로]
```

이 섹션은 의견을 강하게 적는다. 진단가는 헤지하지 않는다.

### Step 6 — Inferred Design System (Phase 2)

수집된 노드 트리 + 속성에서 UI 관련 항목 추출:

- **Fonts**: font family 목록 + 출현 빈도 + 타이포 위계 일관성
- **Colors**: 전체 컬러 팔레트 + semantic 사용 여부 + 브랜드 색상 일치
- **Type scale**: fontSize 분포 + 스케일 비율 + 시각 위계
- **Spacing**: 자주 등장 padding/gap + 스케일 일치 + 레이아웃 리듬
- **Touch targets**: 버튼/링크 최소 크기 (44×44px 기준) + 모바일 적합성
- **Icons**: 아이콘 패밀리 일관성 + 의미 명확성
- **Loading states**: skeleton / progress / spinner 디자인 존재 여부

### Step 7 — IxDF UI 5항목 평가 (Phase 3)

각 항목마다 0-10 점수. 정적 검증 불가능한 항목은 `N/A` + 사유. 위반/개선점은 finding 1개로 작성: **severity** (critical / warning / info), **evidence** (노드 경로/이름/수치), **fix** (구체 액션), **참고** (IxDF 문서/장 참조).

**점수 기준:**
- 10 — exemplary, 업계 best-in-class
- 8-9 — solid, 사소한 polish 만
- 6-7 — 기능적이나 개선 여지
- 4-5 — 눈에 띄는 문제
- 0-3 — 시각적으로 사용자 경험을 적극 해침
- N/A — 정적 분석으로 검증 불가

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding 당)
- warning: -1 ~ -2
- info: 점수 영향 X, 노트만

**항목별 심층 기준:**

**Desirable:**
- 브랜드 아이덴티티 일관성 (컬러·폰트·톤)
- 감정적 공명 (따뜻함/신뢰/흥분 등 의도된 감성 전달)
- 시각적 모더니티 (클리셰, 구식 패턴 부재)
- 이미지/일러스트 품질 + 맥락 적합성

**Engagement:**
- 마이크로 인터랙션 신호 존재 (hover state, 애니메이션 힌트 — 정적 표현만)
- 빈 상태(empty state) / 성공 상태 디자인 존재
- 시각적 피드백 단서 (버튼 pressed 상태, 폼 포커스 링 등)

**Visual Representations:**
- 아이콘 패밀리 일관성 + 직관성 (라벨 없이도 의미 전달 가능한가)
- 타이포그래피 위계 (H1-H3-body-caption 단계 명확)
- 정보 시각화 (차트·그래프·배지 — 수치 맥락 제공 여부)
- 이미지가 텍스트 대신 정보를 전달하는가

**Physical Space:**
- 터치 타겟 44×44px 기준 통과
- 모바일 한 손 도달 영역 (하단 72% 이내 주요 액션)
- 반응형 레이아웃 신호 (Grid/Auto-layout 사용)
- 인접 액션 간 충분한 간격 (≥ 8px)

**Time:**
- 진행 표시기 존재 (step indicator, progress bar)
- Skeleton screen 또는 placeholder 디자인 존재
- 로딩 상태 / 에러 상태 디자인 존재
- 애니메이션 시간 실측 — 정적 분석으로 N/A 처리, 존재 여부만 평가

### Step 8 — UI Health Grade 산출

**평균 환산** = (적용 항목 점수 합) / (적용 항목 수) → 0-10

**Grade 환산:**
- 9.0-10 = **A** (Excellent — best-in-class UI)
- 7.5-8.9 = **B** (Good — minor polish)
- 6.0-7.4 = **C** (Acceptable — needs work)
- 4.0-5.9 = **D** (Poor — significant visual redesign)
- 0-3.9  = **F** (Critical — UI overhaul needed)

**추가 헤드라인:**
- **Visual Quality 공식**: Desirable({N}) + Visual Representations({N}) 평균 = **시각 완성도 한 줄 평가**

### Step 9 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-ixdf-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 10 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 UI Health Grade + 평균 점수 + critical/warning 개수 한 줄 요약
- UI 전용 스킬이므로 UX 항목 리뷰가 필요하면 `design-ux-ixdf-review` 병행 권장

### Step 11 — (선택) Top-3 개선 제안

finding 이 3건 이상이면 high-impact 상위 3개를 픽업하여 간결한 제안 카드 작성. UX Top-3 Rethink 의 경량 버전 (5항목이므로 재설계보다 polish/fix 성격이 강할 수 있음):

각 카드 포맷:
- **현재 문제** (항목 + evidence)
- **사용자 영향**
- **제안 솔루션** (구체 컴포넌트/토큰 변경)
- **기대 점수 변화** (항목 N → N')
- **노력 규모** (Low/Medium/High)

## 보고서 구조 (한국어)

```markdown
# IxDF UI Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 디자인 타입: {MARKETING/LANDING | APP UI | ONBOARDING/FORM | CONTENT/READER | HYBRID}
- 추정 페르소나: {역할·목적·기기}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: IxDF "The Basics of User Experience Design" — UI 5항목 (Desirable + Engagement + Visual Representations + Physical Space + Time)

## 헤드라인
- **UI Health Grade: {A-F}** ({평균}/10)
- **Visual Quality**: Desirable ({N}/10) + Visual Representations ({N}/10) = {한 줄 평가}
- 적용 항목: {applied}/5 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건
- UX 항목(Words·Behavior·Findable 등) 평가가 필요하면 → `design-ux-ixdf-review` 병행

## First Impression
- 이 화면이 전달하는 시각적 인상: {...}
- 브랜드 감성 키워드: {...}
- 내 시선이 가장 먼저 가는 3개: {1}, {2}, {3}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Inferred Design System
- **Fonts** ({n}종): {목록 + 빈도 + 위계 평가}
- **Colors** ({n}종): {팔레트 + semantic 사용 + 브랜드 일치}
- **Type scale**: {분포 + 비율 + 시각 위계}
- **Spacing**: {자주 등장 값 + 리듬 평가}
- **Touch targets**: {최소/평균 크기 + 44px 기준 통과 여부}
- **Icons**: {패밀리 + 일관성 평가}
- **Loading states**: {skeleton/progress/spinner 존재 여부}

## 점수표 (5 항목)

### A. UX Factor (UI 담당)

| # | Factor | 점수 | 비고 |
|---|--------|------|------|
| 1 | Desirable | - | - |

### B. Usability Characteristic (UI 담당)

| # | Characteristic | 점수 | 비고 |
|---|----------------|------|------|
| 2 | Engagement | - | - |

### C. 3 Interaction Dimensions (UI 담당)

| # | Dimension | 점수 | 비고 |
|---|-----------|------|------|
| 3 | Visual Representations | - | - |
| 4 | Physical Space | - | - |
| 5 | Time | - | - |

## Findings

### {항목명} — score: {N}
- **severity**: critical | warning | info
- **evidence**: {노드 경로/이름/수치}
- **fix**: {구체 액션}
- **참고**: IxDF "The Basics of User Experience Design" — {챕터/섹션}

{위반/개선점이 있는 항목만 나열}

## 개선 제안 (Top-3, finding 3건 이상 시)

### Proposal 1 — {항목명} 개선
- **현재 문제**: {evidence}
- **사용자 영향**: {...}
- **제안 솔루션**: {...}
- **기대 점수 변화**: {항목} {N} → {N'}
- **노력**: {Low/Medium/High} ({n} weeks)

## N/A 항목 (정적 분석 한정)
- Engagement (2) 일부: 실제 애니메이션·마이크로 인터랙션 시간 측정 불가 (정적에서는 상태 디자인 존재 여부만)
- Time (5): 실제 로딩 시간 실측 불가 (skeleton/progress 디자인 존재 여부만 평가)

## 다음 단계 (권장 후속)
- `design-ux-ixdf-review` 병행 실행 (UX 12항목 — Words·Behavior·Findable 등)
- A/B 테스트: Desirable 개선안 시각 비교
- 실 디바이스 Physical Space 검증 (터치 정확도 테스트)
```

## 인자

```
/design-ui-ixdf-review <Figma URL | .pen path>
```

- 위치 인자 1개만 필수
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- 옵션 인자 없음 (간결 디폴트 우선)

## 예시

### 예시 1 — Figma URL (단일 프레임)
```
/design-ui-ixdf-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → 분류 → First Impression → Design System 추출 → UI 5항목 평가 → `./design-reviews/design-ui-ixdf-review-checkout-screen-20260514-1130.md` 생성

### 예시 2 — Pencil 멀티 프레임
```
/design-ui-ixdf-review ~/Documents/myapp.pen
```
→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택된 2개 프레임 감지 → 각 프레임 평가 → 2개 파일 생성

### 예시 3 — UX + UI 풀세트 진단
```
/design-ux-ixdf-review <URL>   # UX 12항목
/design-ui-ixdf-review <URL>   # UI 5항목
```
→ 두 스킬 병행 시 IxDF 17항목 전체 커버 (구 `ui-rethink-review` 동등)

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 항목명은 영어 원어 유지 (Desirable, Engagement, Visual Representations, Physical Space, Time)
- finding 의 evidence/fix 는 구체적 노드명·수치·액션 명시
- 보고서는 한 프레임당 한 파일
- finding 헤더 포맷 `### {항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-ixdf-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 라이브 사이트 audit / 인터랙션 / perf 실측 — gstack `/design-review` 책임
- UX 레이어 평가 (Useful/Usable/Findable/Credible/Accessible/Valuable/Effectiveness/Efficiency/Error Tolerance/Ease of Learning/Words/Behavior) — `design-ux-ixdf-review` 책임
- 단일 휴리스틱 평가 — 각 전용 스킬 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인 (별도 references 디렉터리 없음)
- 방법론 출처: Interaction Design Foundation — "The Basics of User Experience Design"
- 1 UX Factor (UI 담당): Peter Morville — User Experience Honeycomb (Desirable)
- 1 Usability Characteristic (UI 담당): ISO 9241-11 (Engagement)
- 3 Interaction Dimensions (UI 담당): Gillian Crampton Smith & Kevin Silver (Visual Representations / Physical Space / Time)
- 모바일 Physical Space 기준: IxDF Chapter 8 — Mobile UX (44×44px touch target)
- 대응 UX 스킬: `design-ux-ixdf-review` (Useful/Usable/Findable/Credible/Accessible/Valuable/Effectiveness/Efficiency/Error Tolerance/Ease of Learning/Words/Behavior)
