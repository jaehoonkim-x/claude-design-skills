---
name: design-ui-lawsofux-review
description: Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 lawsofux.com 의 7개 시각·게슈탈트 UI 법칙으로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. 사용자가 "Laws of UX 시각·게슈탈트 리뷰", "lawsofux UI 평가", "게슈탈트 법칙 검토", "/design-ui-lawsofux-review" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 Laws of UX 시각·게슈탈트 기반 리뷰를 요청할 때 사용.
---

# design-ui-lawsofux-review

lawsofux.com 의 시각·게슈탈트 카테고리 7개 UI 법칙을 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

## 평가 항목 (7)

1. Aesthetic-Usability Effect — 미적으로 만족스러운 디자인은 더 사용성이 좋다고 인식됨
2. Von Restorff Effect — 다른 항목과 구별되는 항목이 더 잘 기억됨
3. Law of Common Region — 공통 경계 안에 있는 요소는 그룹으로 인식
4. Law of Proximity — 가까이 있는 요소는 한 그룹으로 인식
5. Law of Similarity — 유사한 요소는 한 그룹으로 인식
6. Law of Prägnanz — 모호한 이미지는 가장 단순한 형태로 지각됨
7. Law of Uniform Connectedness — 시각적으로 연결된 요소는 더 관련 있게 보임

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "Laws of UX 시각·게슈탈트 리뷰", "lawsofux UI 평가", "게슈탈트 법칙 검토", "시각 그루핑 리뷰" 등을 요청할 때
- 화면의 시각적 그루핑·강조·정렬·연결성·미적 완성도를 점수+개선 액션으로 진단하고 싶을 때
- 컴포넌트 레이아웃·카드 구조·아이콘 시스템·CTA 강조 등 시각 구성이 중심인 화면을 검토할 때

## Do Not Use

- **행동·인지 법칙 평가** (Hick's, Fitts's, Miller's, Goal-Gradient, Doherty Threshold, Jakob's, Pareto, Parkinson's, Postel's, Tesler's, Serial Position, Peak-End, Zeigarnik, Chunking, Cognitive Bias, Cognitive Load, Selective Attention, Choice Overload, Flow, Mental Model, Occam's Razor, Paradox of Active User, Working Memory) → `design-ux-lawsofux-review` 사용
- 다른 rubric 평가 (Nielsen, IxDF, Baymard 등) → 해당 skill 사용
- Figma/Pencil 코멘트 직접 게시 → `annotate-design` 사용
- 인터랙션·애니메이션 분석 (정적 단일 프레임 한정)

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` | "Figma MCP 가 연결되어 있지 않습니다. https://claude.ai 의 Figma 연동을 활성화하거나 Figma 데스크탑 앱의 Dev Mode MCP 를 설치한 뒤 다시 시도해주세요." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: 첫 단계에서 ToolSearch 로 해당 prefix 도구 조회. 결과가 비어 있으면 안내 출력 후 종료.

## Workflow

### Step 1 — 입력 파싱 + 타입 라우팅

- `figma.com/design/:fileKey/...?node-id=:nodeId` → Figma 경로 (nodeId: `-` → `:` 변환)
- `*.pen` 로컬 경로 → Pencil 경로
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 후 종료.

### Step 3 — 디자인 데이터 수집

**Figma:**
1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 로 프레임 구조 파악 + 멀티 프레임 자동 감지
2. 각 frame: `get_design_context(fileKey, nodeId=frame.id)` + `get_screenshot(fileKey, nodeId=frame.id)`

**Pencil:**
1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 선택 frame 감지 (비어 있으면 선택 요청 후 종료)
3. 각 frame: `mcp__pencil__batch_get(node_ids=[frame_id])` + `mcp__pencil__get_screenshot(node_id=frame_id)`

### Step 4 — Rubric 적용 (7개 법칙 순회)

모든 7개 법칙은 정적 검증 Yes — N/A 항목 없음. 각 법칙마다:

- 체크리스트 항목을 deep 노드 트리·스크린샷에 대해 평가
- 위반/개선점 발견 시 finding 작성 (severity + evidence + fix + lawsofux.com 링크)
- 점수 0–10 산출 (위반 없으면 점수만 기록)

**법칙별 핵심 체크포인트:**

| 법칙 | 핵심 체크 |
|------|----------|
| Aesthetic-Usability Effect | 시각 균형·정렬·여백·디자인 시스템 일관성·노이즈 여부 |
| Von Restorff Effect | 1차 CTA 구별 강조 여부, 강조 과다(3+) 여부, 배지/알림 적정 빈도 |
| Law of Common Region | 관련 정보 카드/패널 그루핑, 무관 정보 혼입 여부, 컨테이너 경계 명확성 |
| Law of Proximity | 라벨↔필드 간격(< 8px), 그룹 내/외 간격 대비, 관련 액션 인접 배치 |
| Law of Similarity | 동일 역할 컴포넌트 스타일 통일, 클릭 가능/불가 시각 구분, 변형 일관성 |
| Law of Prägnanz | 아이콘·일러스트 단순성·인지 가능성, 배경/장식의 본문 방해 여부 |
| Law of Uniform Connectedness | 관련 요소 라인/배경/박스 연결, 메뉴 활성 상태 연결, 폼 그룹 단위 표현 |

점수 기준: 9–10 모범 / 7–8 양호 / 5–6 보통 / 3–4 미흡 / 0–2 심각

### Step 5 — Top-3 우선순위 산출

1. 모든 critical 우선
2. critical 부족 시 warning 으로 채움
3. 동일 severity 내: 진입 직후 마주치는 요소 > 1차 CTA/컨버전 경로 > 위반 항목 수
4. 정확히 3개 (부족하면 그만큼만)

### Step 6 — 보고서 작성 + 사용자 요약 출력

- frame-slug: frame.name 을 kebab-case 소문자화 (한글이면 음역 또는 nodeId 끝 8자)
- 날짜 토큰: `YYYYMMDD-HHmm` (KST)
- 출력 경로: `./design-reviews/design-ui-lawsofux-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- 디렉터리 없으면 생성 후 보고서 작성
- 완료 시 경로 목록 + 각 프레임 종합 점수·critical 수·warning 수 한 줄 요약 출력

## 보고서 구조 (한국어)

```markdown
# Laws of UX 시각·게슈탈트 리뷰: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {참고 경로 또는 인라인}

## 종합 점수
- 전체 평균: {average}/10
- critical: {n}건
- warning: {n}건
- info: {n}건
- 검증 적용 법칙: 7/7 (N/A: 0)

## 점수표 (7개 법칙)

| # | 법칙 (Law) | 점수 | 비고 |
|---|-----------|------|------|
| 1 | Aesthetic-Usability Effect | 8 | - |
| 2 | Von Restorff Effect | 5 | warning 1건 |
| 3 | Law of Common Region | 9 | - |
| 4 | Law of Proximity | 7 | - |
| 5 | Law of Similarity | 4 | warning 1건 |
| 6 | Law of Prägnanz | 8 | - |
| 7 | Law of Uniform Connectedness | 6 | warning 1건 |

## Findings

### Von Restorff Effect — score: 5
- **severity**: warning
- **evidence**: `Frame > Actions > PrimaryButton, SecondaryButton, TertiaryButton` — 3개 버튼이 동일 컬러/크기로 강조, 차별화 효과 분산
- **fix**: 1차 CTA 만 filled primary, 2차 이하는 ghost/text 버튼으로 위계 단순화
- **참고**: https://lawsofux.com/von-restorff-effect

{위반/개선점이 있는 법칙만}

## Top-3 우선순위

1. **Law of Similarity (warning)** — 역할 다른 버튼이 동일 스타일. primary/secondary 변형 적용.
2. **Von Restorff Effect (warning)** — 강조 과다로 CTA 희석. 1개만 강조 유지.
3. **Law of Uniform Connectedness (warning)** — 폼 라벨-필드 연결 표현 약함. 배경 그루핑 추가.
```

## 출력 포맷

- **경로**: `./design-reviews/design-ui-lawsofux-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- **finding 헤더**: `### {법칙명} — score: {N}` (annotate-design 호환)
- **finding 필드**: severity / evidence / fix / 참고 (lawsofux.com 링크)
- evidence: 노드 이름·트리 경로·수치 명시
- fix: 한 줄 액션 문구 (구체 수치 포함)
- N/A 항목 없음 (7개 법칙 모두 정적 검증 가능)
- 보고서는 프레임당 1파일, 모든 텍스트 한국어 (법칙 이름은 영어 원어 유지)

## 인자

```
/design-ui-lawsofux-review <Figma URL | .pen path>
```

위치 인자 1개 필수. 멀티 프레임은 Figma/Pencil 의 현재 선택으로 자동 감지.

## 예시

### 예시 1 — Figma URL

```
/design-ui-lawsofux-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```

→ Figma MCP 체크 → metadata + design_context + screenshot 수집 → 7개 UI 법칙 평가 → `./design-reviews/design-ui-lawsofux-review-checkout-screen-20260514-1130.md` 생성

### 예시 2 — Pencil 멀티 프레임

```
/design-ui-lawsofux-review ~/Documents/myapp.pen
```

→ Pencil MCP 체크 → 선택 3 frame 감지 → 각 frame 평가 → 3개 파일 생성

### 예시 3 — MCP 미연결

→ ToolSearch 결과 0건 → 안내 메시지 출력 후 종료

## Non-Goals

- 행동·인지 법칙 23개 평가 → `design-ux-lawsofux-review`
- Figma/Pencil 코멘트 직접 게시 → `annotate-design`
- 인터랙션·애니메이션 분석
- Nielsen/IxDF/Baymard 등 다른 rubric → 해당 skill

## References

- 평가 rubric 원본: `~/.claude/skills/lawsofux-review/references/laws-rubric.md` (UI 7개 항목: Aesthetic-Usability, Von Restorff, Common Region, Proximity, Similarity, Prägnanz, Uniform Connectedness)
- 원본 법칙 출처: https://lawsofux.com/
- UX 행동·인지 variant: `design-ux-lawsofux-review`
- 코멘트 게시: `annotate-design`
