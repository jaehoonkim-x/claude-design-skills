---
name: design-ui-gestalt-review
review-level: L0 Surface
description: "[L0 Surface] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Gestalt 6 핵심 원칙 + 확장 4 원칙 (총 10개)으로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. 사용자가 \"Gestalt 리뷰\", \"게슈탈트 원칙 평가\", \"시각 그룹화 분석\", \"gestalt ui\", \"/design-ui-gestalt-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 Gestalt 원칙 기반 시각 그룹화 리뷰를 요청할 때 사용."
---

# design-ui-gestalt-review

**Review Level**: L0 Surface — Gestalt 6 핵심 원칙 + 확장 4 원칙 (단일 프레임 표면).

1920년대 독일 심리학 학파(Wertheimer, Köhler, Koffka)에서 비롯된 **Gestalt 지각 원칙 10개**를 평가 rubric 으로 사용하여 디자인 프레임의 시각 그룹화 품질을 정적 분석한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 화면의 시각적 요소들이 인간의 지각 원리에 따라 올바르게 그룹화되어 있는가? 뇌가 정보를 가장 자연스럽게 처리할 수 있도록 구성되어 있는가?"

> **Gap 노트**: `design-ui-lawsofux-review` 는 Proximity·Common Region 2개만 다루고 (Gestalt 6 핵심 원칙의 33%), `design-ux-bastien-scapin-review` 의 1.2.1/1.2.2(그루핑·차별화) 기준과 일부 겹친다. 본 스킬은 6 핵심 + 확장 4 를 전체 커버한다. stat-front 폼(Proximity), 사이드바(Continuity), AG Grid(Common Region), 모달(Figure/Ground) 진단에 직결.

## 평가 항목 (10개)

### Rubric A — 6 핵심 원칙 (Wertheimer 1923)

| # | 원칙 | 핵심 질문 | 정적 검증 |
|---|------|----------|----------|
| 1 | Proximity | 가까운 요소끼리 그룹으로 인식되는가? (라벨-입력 간격, 카드 gap 등) | Yes |
| 2 | Similarity | 같은 색·형태·크기 = 같은 역할로 인식되는가? (동일 액션 → 동일 스타일) | Yes |
| 3 | Closure | 불완전한 도형이 완성된 것으로 인식되는가? (아이콘 단순화, 선 생략) | Yes |
| 4 | Continuity | 연속된 선·경로 = 같은 그룹으로 인식되는가? (정렬축, breadcrumb, stepper) | Yes |
| 5 | Figure/Ground | 전경 요소와 배경이 명확히 분리되는가? (모달 overlay, focus ring) | Yes |
| 6 | Common Fate | 함께 움직이는 요소 = 같은 그룹으로 인식되는가? (캐러셀, 동시 애니메이션 힌트) | Partial |

### Rubric B — 확장 4 원칙

| # | 원칙 | 핵심 질문 | 정적 검증 |
|---|------|----------|----------|
| 7 | Common Region | 같은 테두리·배경 영역 = 같은 그룹으로 인식되는가? (카드 컨테이너, AG Grid 행) | Yes |
| 8 | Symmetry & Order | 대칭과 시각적 질서가 안정감을 주는가? (레이아웃 균형, 정렬 일관성) | Yes |
| 9 | Past Experience | 사용자의 과거 경험 기반 패턴을 따르는가? (관습적 아이콘, 기대 레이아웃) | Yes |
| 10 | Pragnanz (단순성) | 가장 단순한 시각 해석이 가능하도록 디자인되었는가? (시각 노이즈 최소화) | Yes |

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "Gestalt 리뷰", "게슈탈트 원칙 평가", "시각 그룹화 분석", "gestalt ui audit" 등을 요청할 때
- 폼 레이아웃(Proximity), 내비게이션(Continuity), 데이터 테이블(Common Region), 모달/드로어(Figure/Ground), 사이드바 계층(Similarity) 등 시각 그룹화 품질이 핵심인 화면을 진단할 때
- `design-ui-lawsofux-review` 로 Proximity·Common Region 2개만 다루어 Gestalt 전체 커버가 필요할 때
- Gestalt Health Grade + 10 원칙 개별 점수를 받고 싶을 때

## Do Not Use

- 행동·인지 법칙 평가 (Hick's, Fitts's, Miller's 등) → `design-ux-lawsofux-review`
- 사용성·탐색성 평가 → `design-ux-ixdf-review` 또는 `design-ux-nielsen-review`
- IxDF UI 5항목 평가 → `design-ui-ixdf-review`
- 시각 폴리시 10 차원 → `design-ui-polish-review`
- Figma/Pencil 코멘트 직접 게시 → `annotate-design`
- 인터랙션·애니메이션 실측 분석 (정적 단일 프레임 한정)
- 라이브 사이트 audit → gstack `/design-review`

**Cross-Reference:**
- Proximity(#1) ↔ `design-ui-lawsofux-review` Law of Proximity, Bastien-Scapin 1.2.1
- Common Region(#7) ↔ `design-ui-lawsofux-review` Law of Common Region, Bastien-Scapin 1.2.2
- Similarity(#2) ↔ `design-ui-lawsofux-review` Law of Similarity (겹치는 3개 법칙만 부분 중복)

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` | "Figma MCP 가 연결되어 있지 않습니다. https://claude.ai 의 Figma 연동을 활성화하거나 Figma 데스크탑 앱의 Dev Mode MCP 를 설치한 뒤 다시 시도해주세요." |
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

### Step 3 — 디자인 데이터 수집

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 로 프레임 구조 파악 + 멀티 프레임 자동 감지
2. 각 frame 에 대해:
   - `mcp__claude_ai_Figma__get_design_context(fileKey, nodeId=frame.id)` 로 deep 트리 + 간격·색·테두리 힌트 수집
   - `mcp__claude_ai_Figma__get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고 이미지 1장 확보

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별 → 멀티 프레임 자동 감지
   - 선택이 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id])` 로 deep 노드 트리 수집
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(node_id=frame_id)` 로 이미지 1장 확보
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 gap·padding·color·border 팔레트 추출

### Step 4 — Classifier (디자인 타입 + 추정 페르소나)

수집된 프레임을 보고 분류:

- **MARKETING/LANDING** — hero·컨버전 중심
- **APP UI** — 워크스페이스·데이터 dense·태스크 중심
- **ONBOARDING/FORM** — 가입·결제·설정 흐름의 단일 스텝
- **CONTENT/READER** — 본문 소비형 (블로그·뉴스·문서)
- **HYBRID** — 위 카테고리 혼재

분류 결과 + 추정 페르소나 1-2명(역할·목적·기기 컨텍스트)을 보고서 메타에 기록. Gestalt 관점 타입별 가중 원칙:
- 폼/온보딩: Proximity · Figure/Ground 가중↑
- 앱 UI/데이터 테이블: Common Region · Continuity · Similarity 가중↑
- 내비게이션/사이드바: Continuity · Common Fate · Symmetry & Order 가중↑
- 마케팅/랜딩: Pragnanz · Figure/Ground · Closure 가중↑

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 화면의 시각 그룹화 첫 인상: [한 문장]
- 시선이 가장 먼저 포착하는 그룹 3개: [1], [2], [3]
- 그룹 경계가 모호하게 느껴지는 영역: [있으면 구체적으로, 없으면 "없음"]
- 한 단어 요약: [단어]
- 인상 메모: [시각 그룹화 관점에서 무엇이 두드러지는가 — 긍정/부정 구체적으로]
```

이 섹션은 의견을 강하게 적는다. 진단가는 헤지하지 않는다.

### Step 6 — Inferred Visual Grouping (Phase 2)

수집된 노드 트리 + 레이아웃 스냅샷에서 Gestalt 관련 속성을 추출:

- **Gap / Spacing**: 요소 간 간격 분포 (내부 그룹 gap vs 그룹 간 gap 대비 비율)
- **Alignment axes**: 수평·수직 정렬축 수 및 일관성 (Continuity 기반)
- **Color clusters**: 동일 역할 요소의 색 일관성 (Similarity 기반)
- **Border / Background groups**: 테두리·배경으로 묶인 영역 (Common Region 기반)
- **Z-depth / Overlay signals**: 모달·드롭다운·툴팁의 전경-배경 분리 신호 (Figure/Ground 기반)
- **Symmetry indicators**: 좌우·상하 균형 측정 (Symmetry & Order 기반)
- **Icon simplicity**: 아이콘 내 선 수·복잡도 (Closure · Pragnanz 기반)

### Step 7 — 10 원칙 평가 (Phase 3)

각 원칙마다 0-10 점수. Common Fate(#6) 는 정적에서 Partial(애니메이션 힌트 신호 존재 여부만). 위반/개선점은 finding 1개로 작성:

- **severity**: critical | warning | info
- **원칙**: 해당 Gestalt 원칙명
- **evidence**: 노드 경로/이름/수치
- **fix**: 구체 액션
- **참고**: 출처 링크

**점수 기준:**
- 10 — exemplary, 원칙을 모범적으로 적용
- 8-9 — solid, 사소한 polish 만 필요
- 6-7 — 기능적이나 개선 여지 있음
- 4-5 — 눈에 띄는 위반, 사용자 혼란 유발
- 0-3 — 원칙 적극 위반, 지각 오류 유발
- N/A — 정적 분석으로 검증 불가 (Common Fate 실측 부분)

**Severity 가이드:**
- critical: -3 ~ -4 (한 finding 당)
- warning: -1 ~ -2
- info: 점수 영향 X, 노트만

**원칙별 핵심 체크포인트:**

**1. Proximity:**
- 라벨 ↔ 입력 필드 간격 (< 8px 권장, 라벨과 필드 사이 > 라벨 위 여백)
- 관련 버튼 그룹 내/외 간격 대비 (내부 gap ≤ 외부 gap 의 50%)
- 카드 내부 요소 vs 카드 간 여백 비율
- 관련 없는 요소가 가깝게 배치되어 오해 유발하는지

**2. Similarity:**
- 동일 역할 버튼 스타일 통일 (variant 일관성)
- 클릭 가능/불가 요소 시각 구분 (disabled, ghost, primary 위계)
- 네비게이션 항목 스타일 일관성
- 인터랙티브 vs 정적 요소 구분 가능성

**3. Closure:**
- 아이콘 내 선 생략이 전체 형태를 여전히 인식 가능하게 하는지
- 잘린 카드 콘텐츠가 "더 있음"을 암시하는지 (스크롤 단서)
- 불완전 테두리·진행 표시기가 완성 경로를 암시하는지

**4. Continuity:**
- 정렬축 일관성 (요소들이 공통 수직/수평축에 정렬되는지)
- Breadcrumb · Stepper · Tab 의 선형 흐름 표현
- 시선 흐름을 방해하는 불규칙 정렬 존재 여부
- 리스트·그리드에서 시각 흐름 유지 여부

**5. Figure/Ground:**
- 모달·오버레이의 배경 딤 처리 (전경/배경 분리)
- 포커스 상태 링·하이라이트의 전경 강조
- 배경 이미지·패턴이 텍스트 가독성 방해 여부
- 드롭다운·툴팁의 elevation/shadow 로 전경 분리 여부

**6. Common Fate:**
- 동시 애니메이션 힌트 신호 (정적에서 arrow/chevron 방향 일치 등)
- 캐러셀 · 탭 전환 시 같이 슬라이드할 요소 그룹 구분
- 토글/체크박스 그룹이 한 단위로 묶여 있는지

**7. Common Region:**
- 카드 컨테이너가 관련 정보만 묶는지
- AG Grid / 테이블 행 구분 (배경 또는 테두리로 그루핑)
- 사이드바 섹션 구분 (배경 영역 또는 구분선)
- 무관한 요소가 같은 컨테이너에 혼입되었는지

**8. Symmetry & Order:**
- 페이지 레이아웃 좌우 균형
- 그리드 기반 정렬 일관성
- 헤더·푸터·사이드바의 시각 무게감 균형
- 비대칭이 의도적인지 우발적인지 (의도적이면 info 처리)

**9. Past Experience:**
- 관습적 아이콘 사용 (햄버거 메뉴, 돋보기 = 검색, X = 닫기)
- 기대 레이아웃 패턴 준수 (헤더 상단, 내비게이션 좌측/상단)
- 낯선 패턴 도입 시 명확한 시각 단서 제공 여부
- 산업 표준 컴포넌트 형태 일치 (로그인 폼, 체크아웃 플로우 등)

**10. Pragnanz (단순성):**
- 시각 요소 최소화 (장식적 노이즈 제거)
- 아이콘·일러스트의 인지 가능 단순성
- 한 화면에서 전달하려는 정보 계층이 즉시 파악되는지
- 불필요한 그라디언트·그림자·테두리 제거 여부

### Step 8 — Gestalt Health Grade 산출

**평균 환산** = (N/A 제외 원칙 점수 합) / (적용 원칙 수) → 0-10

**Grade 환산:**
- 9.0-10 = **A** (Excellent — Gestalt 원칙 모범 적용)
- 7.5-8.9 = **B** (Good — 사소한 조정 필요)
- 6.0-7.4 = **C** (Acceptable — 그룹화 개선 필요)
- 4.0-5.9 = **D** (Poor — 지각 혼란 유발, 재구성 필요)
- 0-3.9 = **F** (Critical — Gestalt 원칙 전면 재설계 필요)

**추가 헤드라인:**
- **Grouping Quality 공식**: Proximity({N}) + Common Region({N}) + Similarity({N}) 평균 = **그룹화 핵심 3원칙 한 줄 평가**
- **Figure Clarity 공식**: Figure/Ground({N}) + Pragnanz({N}) 평균 = **전경 명확도 한 줄 평가**

### Step 9 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-gestalt-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 10 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 Gestalt Health Grade + 평균 점수 + critical/warning 개수 한 줄 요약
- Grouping Quality 3원칙 평균 + Figure Clarity 2원칙 평균 병기
- `design-ui-lawsofux-review` 와 중복 3개 법칙이 있으므로 비교가 필요하면 병행 권장 안내

### Step 11 — (선택) Top-3 Rethink

finding 이 3건 이상이면 high-impact 상위 3개를 픽업하여 개선 제안 카드 작성. 우선순위 기준:
1. critical severity 우선
2. 동일 severity 내: 진입 직후 마주치는 요소 > 1차 CTA/컨버전 경로 > 위반 원칙 수

각 카드 포맷:
- **현재 문제**: 원칙 + evidence
- **지각 영향**: 사용자가 받는 혼란/인지 오류
- **제안 솔루션**: 구체 컴포넌트/간격/색 변경
- **기대 점수 변화**: 원칙 N → N'
- **노력 규모**: Low/Medium/High

### Step 12 — Cross-reference 노트 (보고서 말미)

lawsofux 및 Bastien-Scapin 와 겹치는 원칙을 명시:

| 본 스킬 원칙 | 겹치는 스킬 | 겹치는 항목 |
|------------|------------|------------|
| Proximity (#1) | `design-ui-lawsofux-review` | Law of Proximity |
| Proximity (#1) | `design-ux-bastien-scapin-review` | 1.2.1 Grouping/Distinction of Items |
| Common Region (#7) | `design-ui-lawsofux-review` | Law of Common Region |
| Common Region (#7) | `design-ux-bastien-scapin-review` | 1.2.2 Grouping/Distinction of Items |
| Similarity (#2) | `design-ui-lawsofux-review` | Law of Similarity |

## 보고서 구조 (한국어)

```markdown
# Gestalt 시각 그룹화 리뷰: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 디자인 타입: {MARKETING/LANDING | APP UI | ONBOARDING/FORM | CONTENT/READER | HYBRID}
- 추정 페르소나: {역할·목적·기기}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: Gestalt 지각 원칙 10개 (6 핵심 + 확장 4) — Wertheimer 1923 기반

## 헤드라인
- **Gestalt Health Grade: {A-F}** ({평균}/10)
- **Grouping Quality**: Proximity ({N}/10) + Common Region ({N}/10) + Similarity ({N}/10) = {한 줄 평가}
- **Figure Clarity**: Figure/Ground ({N}/10) + Pragnanz ({N}/10) = {한 줄 평가}
- 적용 원칙: {applied}/10 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 화면의 시각 그룹화 첫 인상: {...}
- 시선이 가장 먼저 포착하는 그룹 3개: {1}, {2}, {3}
- 그룹 경계가 모호하게 느껴지는 영역: {...}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Inferred Visual Grouping
- **Gap/Spacing**: {내부 그룹 gap vs 그룹 간 gap 대비 평가}
- **Alignment axes**: {수평·수직 정렬축 일관성}
- **Color clusters**: {동일 역할 색 일관성}
- **Border/Background groups**: {테두리·배경 그루핑 현황}
- **Z-depth/Overlay signals**: {전경-배경 분리 신호}
- **Symmetry indicators**: {좌우·상하 균형 평가}
- **Icon simplicity**: {아이콘 단순도}

## 점수표 (10 원칙)

### Rubric A — 6 핵심 원칙

| # | 원칙 | 점수 | 비고 |
|---|------|------|------|
| 1 | Proximity | - | - |
| 2 | Similarity | - | - |
| 3 | Closure | - | - |
| 4 | Continuity | - | - |
| 5 | Figure/Ground | - | - |
| 6 | Common Fate | - | - |

### Rubric B — 확장 4 원칙

| # | 원칙 | 점수 | 비고 |
|---|------|------|------|
| 7 | Common Region | - | - |
| 8 | Symmetry & Order | - | - |
| 9 | Past Experience | - | - |
| 10 | Pragnanz | - | - |

## Findings

### {원칙명} — score: {N}
- **severity**: critical | warning | info
- **원칙**: {원칙명 + 번호}
- **evidence**: {노드 경로/이름/수치}
- **fix**: {구체 액션}
- **참고**: {출처 URL}

{위반/개선점이 있는 원칙만 나열}

## 개선 제안 (Top-3, finding 3건 이상 시)

### Proposal 1 — {원칙명} 개선
- **현재 문제**: {원칙 + evidence}
- **지각 영향**: {...}
- **제안 솔루션**: {...}
- **기대 점수 변화**: {원칙} {N} → {N'}
- **노력**: {Low/Medium/High}

## N/A 항목
- Common Fate (#6): 실제 애니메이션 동시 이동 실측 불가 (정적에서는 방향 힌트·그룹 구분 신호만 평가)

## Cross-reference 노트
| 본 스킬 원칙 | 겹치는 스킬 | 겹치는 항목 |
|------------|------------|------------|
| Proximity (#1) | `design-ui-lawsofux-review` | Law of Proximity |
| Proximity (#1) | `design-ux-bastien-scapin-review` | 1.2.1 Grouping/Distinction of Items |
| Common Region (#7) | `design-ui-lawsofux-review` | Law of Common Region |
| Common Region (#7) | `design-ux-bastien-scapin-review` | 1.2.2 Grouping/Distinction of Items |
| Similarity (#2) | `design-ui-lawsofux-review` | Law of Similarity |

## 다음 단계 (권장 후속)
- `design-ui-lawsofux-review` 병행 시 Laws of UX 시각 7 항목 전체 커버 (Aesthetic-Usability·Von Restorff·Uniform Connectedness 추가 획득)
- `design-ux-bastien-scapin-review` 병행 시 1.2.x 그루핑 기준 교차 검증
- `annotate-design` 으로 Findings 를 Figma/Pencil 에 시각 코멘트 부착
```

## 인자

```
/design-ui-gestalt-review <Figma URL | .pen path>
```

- 위치 인자 1개만 필수
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- 옵션 인자 없음

## 예시

### 예시 1 — Figma URL (단일 프레임, 폼 화면)

```
/design-ui-gestalt-review https://www.figma.com/design/abc123XYZ/EasySeller?node-id=42-1024
```

→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → 분류(ONBOARDING/FORM) → First Impression → Visual Grouping 추출 → 10 원칙 평가 (Proximity·Figure/Ground 가중) → `./design-reviews/design-ui-gestalt-review-signup-form-20260518-1430.md` 생성

### 예시 2 — Pencil 멀티 프레임 (사이드바 + AG Grid)

```
/design-ui-gestalt-review ~/Documents/stat-front.pen
```

→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택된 2개 프레임 감지 → 각 프레임 평가 (사이드바: Continuity·Common Fate 가중 / AG Grid: Common Region·Similarity 가중) → 2개 파일 생성

### 예시 3 — 모달 오버레이 진단 (Figure/Ground 집중)

```
/design-ui-gestalt-review https://www.figma.com/design/abc123XYZ/EasySeller?node-id=88-2048
```

→ Figure/Ground(#5) · Pragnanz(#10) · Common Region(#7) 집중 분석 → 모달 딤 처리·포커스 링·오버레이 elevation 진단

### 예시 4 — MCP 미연결

→ ToolSearch 결과 0건 → "Figma MCP 가 연결되어 있지 않습니다." 안내 출력 후 종료

### 예시 5 — 전체 시각 그룹화 풀세트 진단

```
/design-ui-gestalt-review <URL>       # Gestalt 10원칙
/design-ui-lawsofux-review <URL>      # Laws of UX 시각 7개 (중복 3개 + 추가 4개)
/design-ux-bastien-scapin-review <URL> # 1.2.x 그루핑 기준 교차 검증
```

→ 3 스킬 병행 시 시각 그룹화 전체 커버

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 원칙명은 영어 원어 유지 (Proximity, Similarity, Closure, Continuity, Figure/Ground, Common Fate, Common Region, Symmetry & Order, Past Experience, Pragnanz)
- finding 의 evidence/fix 는 구체적 노드명·수치·액션 명시
- finding 헤더 포맷 `### {원칙명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / 원칙 / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)
- 보고서는 한 프레임당 한 파일
- N/A 항목은 반드시 사유 명시

## annotate-design 호환성

본 스킬의 출력 `.md` 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-gestalt-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 라이브 사이트 audit / 인터랙션 / perf 실측 — gstack `/design-review` 책임
- 행동·인지 법칙 평가 (Hick's, Fitts's, Miller's 등) — `design-ux-lawsofux-review` 책임
- 사용성·탐색성 평가 — `design-ux-ixdf-review` · `design-ux-nielsen-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인 (별도 references 디렉터리 없음)
- 방법론 원전: Wertheimer, M. (1923). *Untersuchungen zur Lehre von der Gestalt II* — 6 핵심 원칙 최초 기술
- IxDF Gestalt 개요: https://www.interaction-design.org/literature/topics/gestalt-principles
- Smashing Magazine 심층 가이드: https://www.smashingmagazine.com/2014/03/design-principles-visual-perception-and-the-principles-of-gestalt/
- NN/g Gestalt 원칙: https://www.nngroup.com/articles/gestalt-principles-of-human-perception/
- 겹치는 스킬 (부분 중복):
  - `design-ui-lawsofux-review` — Proximity·Common Region·Similarity 3개 중복
  - `design-ux-bastien-scapin-review` — 1.2.1/1.2.2 Grouping/Distinction 기준 중복
- 코멘트 게시: `annotate-design`
