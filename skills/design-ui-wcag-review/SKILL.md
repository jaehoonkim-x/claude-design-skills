---
name: design-ui-wcag-review
review-level: L0 Surface
description: "[L0 Surface] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 WCAG 2.2 4 원칙 × 13 가이드라인 × 78 Success Criteria 기준으로 정적 a11y 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. 정적 검증 가능한 핵심 SC 집중 (contrast, target size, alt text, focus visible, ARIA, status messages, reflow, text spacing). WCAG 2.2 신규 9 SC(2.4.11·2.4.12·2.5.7·2.5.8·3.2.6·3.3.7·3.3.8·3.3.9·2.4.13) 별도 surface. Compliance Level(A/AA/AAA) 헤드라인 + 4 원칙 점수 + 정량 지표(contrast 평균·touch target 평균·ARIA 사용률). 사용자가 \"WCAG 리뷰\", \"a11y 리뷰\", \"접근성 리뷰\", \"WCAG 2.2 평가\", \"wcag audit\", \"accessibility audit\", \"/design-ui-wcag-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 WCAG 2.2 기반 접근성 리뷰를 요청할 때 사용."
---

# design-ui-wcag-review

**Review Level**: L0 Surface — WCAG 2.2 a11y 전용 (단일 프레임 정적 분석).

WCAG 2.2 4 원칙(Perceivable·Operable·Understandable·Robust) × 13 가이드라인 × 78 Success Criteria 를 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다. 정적 도구(Figma/Pencil)로 검증 가능한 SC 에 집중한다. 리포트만 생성한다 — 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "이 화면이 시각·인지·운동·기술 장애를 가진 사용자에게 동등한 접근성을 제공하는가? 어느 SC 에서 실패하는가?"

## 4 원칙 rubric (78 SC)

### Principle 1. Perceivable — 지각 가능성

| 가이드라인 | 핵심 SC | 정적 검증 |
|-----------|---------|----------|
| 1.1 Text Alternatives | 1.1.1 Alt Text | Yes |
| 1.2 Time-based Media | 1.2.1~1.2.9 캡션·오디오 설명 | Partial |
| 1.3 Adaptable | 1.3.1 Info & Relationships, 1.3.2 Meaningful Sequence, 1.3.3 Sensory Characteristics, 1.3.4 Orientation, 1.3.5 Identify Input Purpose | Yes |
| 1.4 Distinguishable | **1.4.3 Contrast (Minimum) 4.5:1**, 1.4.4 Resize Text, 1.4.5 Images of Text, **1.4.10 Reflow 320px**, **1.4.11 Non-text Contrast 3:1**, **1.4.12 Text Spacing**, 1.4.13 Content on Hover | Yes/Partial |

### Principle 2. Operable — 조작 가능성

| 가이드라인 | 핵심 SC | 정적 검증 |
|-----------|---------|----------|
| 2.1 Keyboard | 2.1.1 Keyboard, 2.1.2 No Keyboard Trap, 2.1.4 Character Key Shortcuts | Partial |
| 2.2 Enough Time | 2.2.1 Timing Adjustable, 2.2.2 Pause·Stop·Hide | Partial |
| 2.3 Seizures | 2.3.1 Three Flashes | Partial |
| 2.4 Navigable | **2.4.7 Focus Visible**, **2.4.11 Focus Not Obscured (★ 2.2)**, 2.4.1 Bypass Blocks, 2.4.3 Focus Order, 2.4.6 Headings & Labels | Yes/Partial |
| 2.5 Input Modalities | **2.5.5 Target Size (AA) 24px / (AAA) 44px**, **2.5.8 Target Size Minimum 24×24 (★ 2.2)**, 2.5.1 Pointer Gestures, 2.5.3 Label in Name | Yes |

### Principle 3. Understandable — 이해 가능성

| 가이드라인 | 핵심 SC | 정적 검증 |
|-----------|---------|----------|
| 3.1 Readable | 3.1.1 Language of Page, 3.1.2 Language of Parts | Partial |
| 3.2 Predictable | 3.2.1 On Focus, 3.2.2 On Input, **3.2.6 Consistent Help (★ 2.2)** | Yes/Partial |
| 3.3 Input Assistance | 3.3.1 Error Identification, 3.3.2 Labels or Instructions, **3.3.7 Redundant Entry (★ 2.2)**, **3.3.8 Accessible Authentication (★ 2.2 AA)** | Yes |

### Principle 4. Robust — 견고성

| 가이드라인 | 핵심 SC | 정적 검증 |
|-----------|---------|----------|
| 4.1 Compatible | 4.1.1 Parsing, 4.1.2 Name·Role·Value, **4.1.3 Status Messages** | Yes/Partial |

## 핵심 SC (정적 검증 집중)

| SC ID | 이름 | Level | WCAG 2.2 신규 |
|-------|------|-------|--------------|
| 1.1.1 | Non-text Content (Alt Text) | A | — |
| 1.4.3 | Contrast Minimum 4.5:1 | AA | — |
| 1.4.10 | Reflow 320px | AA | — |
| 1.4.11 | Non-text Contrast 3:1 | AA | — |
| 1.4.12 | Text Spacing | AA | — |
| 2.4.7 | Focus Visible | AA | — |
| 2.4.11 | Focus Not Obscured | AA | ★ |
| 2.5.5 | Target Size (Minimum 24px AA / 44px AAA) | AA/AAA | — |
| 2.5.8 | Target Size Minimum 24×24 | AA | ★ |
| 3.2.6 | Consistent Help | A | ★ |
| 3.3.7 | Redundant Entry | A | ★ |
| 3.3.8 | Accessible Authentication Minimum | AA | ★ |
| 4.1.3 | Status Messages | AA | — |

## WCAG 2.2 신규 9 SC (별도 surface)

| SC ID | 이름 | Level | 평가 내용 |
|-------|------|-------|---------|
| 2.4.11 | Focus Not Obscured (Minimum) | AA | 포커스 요소가 sticky 헤더·고정 요소에 완전히 가려지지 않는가 |
| 2.4.12 | Focus Not Obscured (Enhanced) | AAA | 포커스 요소가 어떤 컴포넌트에도 가려지지 않는가 |
| 2.4.13 | Focus Appearance | AAA | 포커스 인디케이터 면적·두께·대비 기준 |
| 2.5.7 | Dragging Movements | AA | 드래그 없는 대체 입력 존재 여부 |
| 2.5.8 | Target Size (Minimum) | AA | 모든 인터랙티브 요소 최소 24×24px |
| 3.2.6 | Consistent Help | A | 여러 화면에서 도움 메커니즘 위치 일관성 |
| 3.3.7 | Redundant Entry | A | 동일 세션 내 이미 입력한 정보 재입력 요구 금지 |
| 3.3.8 | Accessible Authentication (Minimum) | AA | 인지 기능 테스트(CAPTCHA 등) 없는 인증 대안 |
| 3.3.9 | Accessible Authentication (Enhanced) | AAA | 인지 기능 테스트 완전 배제 |

## Compliance Level 정의

| Level | 기준 |
|-------|------|
| **A** | A(30) SC 전체 통과 |
| **AA** | A + AA(50) SC 전체 통과 (대부분 법적 기준) |
| **AAA** | A + AA + AAA(78) SC 전체 통과 |
| **Non-compliant** | A 또는 AA SC 1건 이상 실패 |

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "WCAG 리뷰", "a11y audit", "접근성 검토", "색상 대비 검사", "터치 타겟 검사", "포커스 가시성 검사", "ARIA 검토" 등을 요청할 때
- 엔터프라이즈 제품의 법적 접근성 요건(WCAG 2.2 AA) 충족 여부 확인이 필요할 때
- 디자인 시스템의 컴포넌트 레벨 a11y 품질 검증이 필요할 때
- `design-ui-polish-review` / `design-ui-nielsen-review` 등 일반 UI 리뷰 후 a11y 특화 심층 진단이 필요할 때

## Do Not Use

- 런타임 a11y 검증(실제 DOM·AT 동작 테스트) → axe-core / Deque axe DevTools 책임
- 라이브 사이트 a11y audit → gstack `/design-review` 책임
- 코멘트를 디자인 파일에 직접 달아야 할 때 → `annotate-design`
- 일반 UI 시각 품질 평가 → `design-ui-polish-review` / `design-ui-nielsen-review`
- UX 흐름·정보구조 평가 → `design-ux-flow-review`
- WCAG 외 a11y 표준(ARIA Authoring Practices·WAI-ARIA 1.2 상세 패턴) 단독 검토 → 별도 리서치

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
- `--level A|AA|AAA`: 목표 Compliance Level 명시 (미지정 시 AA 기본)
- `--sc 1.4.3,2.5.8,...`: 특정 SC 만 집중 평가

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집 (deep)

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 로 프레임 구조 파악
   - nodeId 미지정 시 현재 선택 프레임 사용. 멀티 프레임 자동 감지
2. 각 frame 에 대해:
   - `mcp__claude_ai_Figma__get_design_context(fileKey, nodeId=frame.id)` 로 deep 트리 + 색상·폰트·레이아웃 토큰 수집
   - `mcp__claude_ai_Figma__get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고 이미지 1장 확보

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별 → 멀티 프레임 자동 감지
   - 선택이 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id])` 로 deep 노드 트리 수집
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(node_id=frame_id)` 로 이미지 1장 확보
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 컬러·폰트·사이즈 팔레트 추출

### Step 4 — Classifier (디자인 타입 + a11y 위험 프로파일)

수집된 프레임을 분류:

- **FORM/AUTH** — 로그인·회원가입·인증·결제 입력 (SC 3.3.x·3.2.x 가중↑)
- **CONTENT/READER** — 본문·기사·문서 소비형 (SC 1.1.1·1.4.3·1.4.12 가중↑)
- **APP UI / DASHBOARD** — 데이터 dense·인터랙티브 컨트롤 (SC 2.4.x·2.5.x·4.1.x 가중↑)
- **MARKETING/LANDING** — hero·배너·전환 중심 (SC 1.4.3·1.4.11·1.1.1 가중↑)
- **HYBRID** — 위 카테고리 혼재

분류 결과 + 예상 장애 유형별 위험 프로파일(시각·청각·운동·인지)을 보고서 메타에 기록.

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **접근성 첫 반응**을 1인칭으로 작성:

```
- 이 화면의 접근성 첫인상: [한 문장]
- 가장 우려되는 a11y 위험 3가지: [1], [2], [3]
- 가장 잘 된 a11y 요소: [한 문장]
- 시각 장애 사용자 관점 한 단어: [단어]
- 인상 메모: [구체적 긍정/부정 — 수치 예측 포함]
```

진단가는 헤지하지 않는다.

### Step 6 — Inferred a11y Inventory (Phase 2)

수집된 노드 트리 + 속성에서 a11y 관련 항목 추출:

**Contrast 측정:**
- 모든 텍스트 요소: foreground/background 색상 추출 → 상대 휘도 공식으로 대비율 계산
  - `L = 0.2126R + 0.7152G + 0.0722B` (linearized)
  - `CR = (L1 + 0.05) / (L2 + 0.05)` (L1 > L2)
- 텍스트 크기 분류: 일반 텍스트(<18pt / <14pt bold) → 4.5:1 기준, 큰 텍스트(≥18pt / ≥14pt bold) → 3:1 기준
- UI 컴포넌트(아이콘·버튼 테두리·포커스 링) → Non-text Contrast 3:1 기준 (SC 1.4.11)
- 결과: 요소별 대비율 목록 + 통과/실패 판정 + **Contrast 평균** 산출

**Touch Target 측정:**
- 모든 인터랙티브 요소(버튼·링크·체크박스·토글·입력 필드 등) 크기(W×H) 추출
- SC 2.5.8 기준: 최소 24×24px 통과 여부
- SC 2.5.5 기준: AA 24px 이상 / AAA 44×44px 이상
- **Touch target 평균** (W+H)/2 산출 + 통과율

**ARIA 사용률:**
- 노드 트리에서 ARIA 관련 속성(aria-label·aria-labelledby·aria-describedby·role·aria-live 등) 출현 여부
- 이미지 노드 중 alt text 속성 보유 비율
- 폼 입력 요소 중 label 연결 비율
- **ARIA 사용률** = ARIA 속성 보유 인터랙티브 요소 / 전체 인터랙티브 요소

**구조 분석:**
- 헤딩 위계(H1-H6) 존재 여부 + 논리적 순서
- 포커스 인디케이터 디자인 존재 여부 (포커스 상태 레이어)
- 색상만으로 정보를 전달하는 요소 존재 여부 (아이콘·텍스트 병행 여부)
- 에러·성공·경고 상태 디자인에 비색상 신호(아이콘·텍스트) 존재 여부

### Step 7 — SC 평가 (Phase 3)

핵심 SC 각각 Pass / Fail / Partial / N/A 판정 + 0-10 점수. 정적 분석 불가 SC 는 `N/A` + 사유.

**점수 기준:**
- 10 — 완전 통과, best-in-class 구현
- 8-9 — 통과, 사소한 개선 여지
- 6-7 — 부분 통과, 일부 요소 실패
- 4-5 — 주요 실패, 즉각 수정 권장
- 0-3 — 완전 실패, 사용 불가 수준
- N/A — 정적 분석으로 검증 불가

**Severity 가이드:**
- `AA FAIL` — AA level SC 실패 (법적 요건, 즉각 수정)
- `A FAIL` — A level SC 실패 (기본 접근성 차단)
- `AAA FAIL` — AAA level SC 실패 (향상된 접근성 미충족)
- `warning` — 실패는 아니나 개선 권장
- `info` — 점수 영향 X, 긍정적 관찰 또는 참고 사항

**원칙별 가중치 (flow type 미세 조정):**
- Form/Auth: SC 3.3.x·3.2.x 가중↑ (Understandable 원칙 비중 35%)
- Content: SC 1.1.1·1.4.3·1.4.12 가중↑ (Perceivable 원칙 비중 40%)
- App UI: SC 2.4.x·2.5.x·4.1.x 가중↑ (Operable·Robust 비중 40%)
- Marketing: SC 1.4.3·1.4.11·1.1.1 가중↑ (Perceivable 비중 45%)

### Step 8 — Compliance Level 산출 (Phase 4)

1. A level SC 전체 통과 → Level A 충족
2. A + AA level SC 전체 통과 → Level AA 충족 (목표 기본값)
3. A + AA + AAA level SC 전체 통과 → Level AAA 충족
4. A 또는 AA 실패 → Non-compliant

**Grade 환산 (평균 점수 기반):**
- 9.0-10 = **Excellent** (AA+ 충족, 모범 사례)
- 7.5-8.9 = **Good** (AA 거의 충족, minor fix)
- 6.0-7.4 = **Acceptable** (부분 충족, 개선 필요)
- 4.0-5.9 = **Poor** (AA 미충족, 다수 수정)
- 0-3.9 = **Critical** (기본 접근성 불가, 전면 개선)

**추가 헤드라인:**
- **WCAG 2.2 신규 SC 통과율**: 9 SC 중 통과 개수 / 9 (정적 평가 가능 항목만)
- **Contrast 평균**: 전체 텍스트 요소 대비율 평균 + 4.5:1 기준 통과율
- **Touch target 평균**: 전체 인터랙티브 요소 평균 크기 + 24px 기준 통과율
- **ARIA 사용률**: 인터랙티브 요소 중 ARIA 속성 보유 비율

### Step 9 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-wcag-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 10 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 Compliance Level + 평균 점수 + AA FAIL / A FAIL / warning 개수 한 줄 요약
- WCAG 2.2 신규 SC 통과율 한 줄
- 정량 지표 3개 (Contrast 평균 / Touch target 평균 / ARIA 사용률) 한 줄
- 런타임 검증이 필요하면 axe-core / Deque axe DevTools 병행 권장

### Step 11 — (선택) Top Critical SC 제안

AA FAIL / A FAIL 이 1건 이상이면 impact 높은 상위 5개 SC 를 픽업하여 수정 카드 작성:

각 카드 포맷:
- **SC ID + 이름** (Level)
- **현재 상태** (evidence — 노드명·수치·색상값)
- **사용자 영향** (어떤 장애를 가진 사용자에게 어떤 영향인가)
- **수정 방향** (구체 토큰·컴포넌트·속성 변경)
- **기대 판정 변화** (Fail → Pass / Partial → Pass)
- **노력 규모** (Low / Medium / High)

## 보고서 구조 (한국어)

```markdown
# WCAG 2.2 a11y Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 디자인 타입: {FORM/AUTH | CONTENT/READER | APP UI/DASHBOARD | MARKETING/LANDING | HYBRID}
- a11y 위험 프로파일: {시각·청각·운동·인지 장애 유형별 주요 위험}
- 목표 Compliance Level: {A | AA | AAA} (기본: AA)
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: WCAG 2.2 4 원칙 × 13 가이드라인 × 78 SC (정적 분석 가능 SC 집중)

## 헤드라인
- **Compliance Level: {A | AA | AAA | Non-compliant}**
- **a11y Grade: {Excellent | Good | Acceptable | Poor | Critical}** ({평균}/10)
- **WCAG 2.2 신규 SC 통과율**: {n}/9 ({통과 SC ID 목록})
- **정량 지표**:
  - Contrast 평균: {X.X}:1 (4.5:1 기준 통과율 {n}%)
  - Touch target 평균: {W}×{H}px (24×24px 기준 통과율 {n}%)
  - ARIA 사용률: {n}% ({m}/{total} 인터랙티브 요소)
- A FAIL: {n}건 · AA FAIL: {n}건 · AAA FAIL: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 화면의 접근성 첫인상: {...}
- 가장 우려되는 a11y 위험 3가지: {1}, {2}, {3}
- 가장 잘 된 a11y 요소: {...}
- 시각 장애 사용자 관점 한 단어: {...}
- 인상 메모: {...}

## Inferred a11y Inventory

### Contrast 분석
| 요소 | 전경색 | 배경색 | 대비율 | 기준 | 판정 |
|------|--------|--------|--------|------|------|
| {노드명} | #{hex} | #{hex} | {X.X}:1 | {4.5:1 / 3:1} | {Pass / Fail} |

### Touch Target 분석
| 요소 | 크기 | SC 2.5.8 (24×24) | SC 2.5.5 AA (24px) | SC 2.5.5 AAA (44px) |
|------|------|-----------------|-------------------|-------------------|
| {노드명} | {W}×{H}px | {Pass/Fail} | {Pass/Fail} | {Pass/Fail} |

### ARIA 및 구조 분석
- **헤딩 위계**: {H1-H6 분포 + 논리적 순서 평가}
- **이미지 alt text**: {보유 비율 + 미보유 목록}
- **폼 요소 label 연결**: {연결 비율 + 미연결 목록}
- **ARIA 속성 사용**: {aria-label/aria-live/role 등 출현 목록}
- **포커스 인디케이터**: {존재 여부 + 디자인 평가}
- **색상 단독 정보 전달**: {위험 요소 목록}

## 점수표 — 4 원칙

### Principle 1. Perceivable

| SC ID | 이름 | Level | 점수 | 판정 | 비고 |
|-------|------|-------|------|------|------|
| 1.1.1 | Non-text Content (Alt Text) | A | - | - | - |
| 1.4.3 | Contrast Minimum 4.5:1 | AA | - | - | - |
| 1.4.10 | Reflow 320px | AA | - | - | - |
| 1.4.11 | Non-text Contrast 3:1 | AA | - | - | - |
| 1.4.12 | Text Spacing | AA | - | - | - |

### Principle 2. Operable

| SC ID | 이름 | Level | 점수 | 판정 | 비고 |
|-------|------|-------|------|------|------|
| 2.4.7 | Focus Visible | AA | - | - | - |
| 2.4.11 | Focus Not Obscured ★ | AA | - | - | - |
| 2.5.5 | Target Size (24px AA / 44px AAA) | AA/AAA | - | - | - |
| 2.5.8 | Target Size Minimum 24×24 ★ | AA | - | - | - |

### Principle 3. Understandable

| SC ID | 이름 | Level | 점수 | 판정 | 비고 |
|-------|------|-------|------|------|------|
| 3.2.6 | Consistent Help ★ | A | - | - | - |
| 3.3.7 | Redundant Entry ★ | A | - | - | - |
| 3.3.8 | Accessible Authentication ★ | AA | - | - | - |

### Principle 4. Robust

| SC ID | 이름 | Level | 점수 | 판정 | 비고 |
|-------|------|-------|------|------|------|
| 4.1.3 | Status Messages | AA | - | - | - |

## WCAG 2.2 신규 9 SC 통과율

| SC ID | 이름 | Level | 판정 | 근거 |
|-------|------|-------|------|------|
| 2.4.11 | Focus Not Obscured (Minimum) | AA | {Pass/Fail/N/A} | - |
| 2.4.12 | Focus Not Obscured (Enhanced) | AAA | {Pass/Fail/N/A} | - |
| 2.4.13 | Focus Appearance | AAA | {Pass/Fail/N/A} | - |
| 2.5.7 | Dragging Movements | AA | {Pass/Fail/N/A} | - |
| 2.5.8 | Target Size (Minimum) | AA | {Pass/Fail/N/A} | - |
| 3.2.6 | Consistent Help | A | {Pass/Fail/N/A} | - |
| 3.3.7 | Redundant Entry | A | {Pass/Fail/N/A} | - |
| 3.3.8 | Accessible Authentication (Min) | AA | {Pass/Fail/N/A} | - |
| 3.3.9 | Accessible Authentication (Enh) | AAA | {Pass/Fail/N/A} | - |

## Findings

### {SC ID} {항목명} — score: {N}
- **severity**: AA FAIL | A FAIL | AAA FAIL | warning | info
- **SC ID**: {SC ID}
- **evidence**: {노드 경로/이름/수치/색상값}
- **fix**: {구체 액션 — 색상 토큰·크기·속성 변경}
- **참고**: {출처 — WCAG 2.2 / Stark / axe / a11y Project / WebAIM / Heydon}

{위반/개선점이 있는 SC 만 나열}

## Top Critical SC 수정 제안 (AA FAIL / A FAIL 1건 이상 시)

### Proposal 1 — {SC ID} {이름} ({Level})
- **현재 상태**: {evidence — 노드명·수치·색상값}
- **사용자 영향**: {어떤 장애 유형·어떤 영향}
- **수정 방향**: {구체 토큰·컴포넌트·속성 변경}
- **기대 판정 변화**: {Fail → Pass / Partial → Pass}
- **노력**: {Low/Medium/High}

## N/A 항목 (정적 분석 한정)
- SC 1.2.x Time-based Media: 동영상·오디오 캡션·대본 실측 불가
- SC 2.1.x Keyboard: 실제 키보드 탐색 시뮬레이션 불가 (포커스 디자인 존재 여부만 평가)
- SC 2.3.1 Seizures: 실제 애니메이션 주파수 실측 불가
- SC 3.1.1/3.1.2 Language: HTML lang 속성은 코드 레이어 검증 필요

## 다음 단계 (권장 후속)
- axe-core / Deque axe DevTools 로 런타임 DOM a11y 검증
- 스크린리더(NVDA / VoiceOver / TalkBack) 실 디바이스 테스트
- `annotate-design` 스킬로 디자인 파일에 finding 시각화
- 수정 후 동일 rubric 재평가 (delta 측정)
- WCAG 2.2 공식 이해 문서: https://www.w3.org/WAI/WCAG22/Understanding/
```

## 인자

```
/design-ui-wcag-review <Figma URL | .pen path> [--level A|AA|AAA] [--sc 1.4.3,2.5.8,...]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- 옵션 `--level A|AA|AAA`: 목표 Compliance Level (기본: AA)
- 옵션 `--sc {SC ID,}`: 특정 SC 만 집중 평가 (전체 평가 후 해당 SC 강조)
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Figma URL (단일 프레임, AA 기본)
```
/design-ui-wcag-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → Classifier → First Impression → a11y Inventory(contrast·target·ARIA) → 핵심 SC 13개 평가 → Compliance Level AA 산출 → `./design-reviews/design-ui-wcag-review-checkout-screen-20260518-1130.md` 생성

### 예시 2 — Pencil 멀티 프레임
```
/design-ui-wcag-review ~/Documents/myapp.pen
```
→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택된 3개 프레임 감지 → 각 프레임 평가 → 3개 파일 생성

### 예시 3 — AAA 목표 레벨 지정
```
/design-ui-wcag-review https://www.figma.com/design/abc123/DS?node-id=10-200 --level AAA
```
→ AAA SC 전체 평가 + WCAG 2.2 신규 AAA SC(2.4.12·2.4.13·3.3.9) 중점 포함

### 예시 4 — 특정 SC 집중 평가
```
/design-ui-wcag-review ~/Desktop/login.pen --sc 1.4.3,2.5.8,3.3.8
```
→ 전체 평가 후 Contrast(1.4.3)·Target Size(2.5.8)·Accessible Authentication(3.3.8) 집중 분석 카드 우선 출력

### 예시 5 — MCP 미연결
```
/design-ui-wcag-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 가 연결되어 있지 않습니다..." 안내 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- SC ID 및 이름은 영어 원어 유지 ("1.4.3 Contrast Minimum", "2.5.8 Target Size Minimum" 등)
- finding 의 evidence/fix 는 구체적 노드명·수치·색상값·액션 명시
- 보고서는 한 프레임당 한 파일
- finding 헤더 포맷 `### {SC ID} {항목명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / SC ID / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)
- 대비율은 소수점 1자리까지 표기 (예: 4.6:1)

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-wcag-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 런타임 DOM a11y 검증 (axe-core·AT 실 동작) — 별도 도구 책임
- 라이브 사이트 audit / 인터랙션 실측 — gstack `/design-review` 책임
- WCAG 외 표준 단독 평가 (ARIA APG 상세 패턴·Section 508·EN 301 549) — 별도 스킬 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 레이어 ARIA 구현 검증 — 코드 리뷰 책임

## 참고 자료

- **WCAG 2.2**: https://www.w3.org/WAI/WCAG22/quickref/
- **WCAG 2.2 이해 문서**: https://www.w3.org/WAI/WCAG22/Understanding/
- **Stark (색상 대비·접근성 도구)**: https://www.getstark.co/
- **axe (Deque)**: https://www.deque.com/axe/
- **a11y Project Checklist**: https://www.a11yproject.com/checklist/
- **WebAIM Contrast Checker**: https://webaim.org/resources/contrastchecker/
- **WebAIM 접근성 가이드**: https://webaim.org/
- **Heydon Inclusive Components**: https://inclusive-components.design/
- 대응 런타임 도구: axe-core / Deque axe DevTools / NVDA / VoiceOver / TalkBack
- 짝 UI 스킬: `design-ui-polish-review` (시각 polish) · `design-ui-nielsen-review` (H8 Aesthetic 포함)
- 짝 UX 스킬: `design-ux-flow-review` (L2 flow level edge state 포함)
