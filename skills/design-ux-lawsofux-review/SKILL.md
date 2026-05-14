---
name: design-ux-lawsofux-review
description: Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 lawsofux.com 의 23개 행동·인지 UX 법칙으로 정적 분석하여 프레임당 한국어 마크다운 리뷰 보고서를 생성. 사용자가 "Laws of UX 행동·인지 리뷰", "lawsofux UX 평가", "UX 법칙 인지 검토", "/design-ux-lawsofux-review" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 Laws of UX 행동·인지 기반 리뷰를 요청할 때 사용.
---

# design-ux-lawsofux-review

lawsofux.com 의 행동·인지 카테고리 23개 UX 법칙을 평가 rubric 으로 사용하여 디자인 프레임을 정적 분석한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

## 평가 항목 (23)

1. Hick's Law — 결정 시간은 선택지 수/복잡도에 비례
2. Fitts's Law — 타겟 획득 시간은 거리와 크기의 함수
3. Miller's Law — 평균 작업 기억 용량 7±2
4. Goal-Gradient Effect — 목표에 가까울수록 동기 증가
5. Doherty Threshold — 400ms 이내 응답 시 생산성 향상 (정적 N/A 다수)
6. Jakob's Law — 사용자는 익숙한 패턴으로 작동하길 원함
7. Pareto Principle — 80% 효과는 20% 원인에서
8. Parkinson's Law — 작업은 주어진 시간만큼 늘어남 (정적 N/A 다수)
9. Postel's Law — 입력은 관대하게, 출력은 보수적으로
10. Tesler's Law — 환원 불가능한 최소 복잡도는 시스템이 흡수
11. Serial Position Effect — 리스트 첫·끝 항목이 가장 잘 기억됨
12. Peak-End Rule — 경험 평가는 정점·끝 순간에 좌우됨 (정적 N/A 다수)
13. Zeigarnik Effect — 미완료 작업이 완료보다 잘 기억됨
14. Chunking — 정보를 의미 단위로 묶으면 인지 부담 감소
15. Cognitive Bias — 앵커링·손실회피·사회적 증명 등 체계적 편향
16. Cognitive Load — 인터페이스 이해·조작에 드는 정신적 자원
17. Selective Attention — 목표 관련 자극에 집중, 나머지 무시
18. Choice Overload — 선택지가 많을수록 결정이 어려워짐
19. Flow — 몰입 상태: 도전과 능력의 균형 (정적 N/A 다수)
20. Mental Model — 사용자가 시스템 작동에 대해 가진 압축된 이해
21. Occam's Razor — 가장 단순한 해결이 최선
22. Paradox of the Active User — 사용자는 매뉴얼 없이 바로 사용
23. Working Memory — 인지 시스템이 작업 관련 정보를 임시 보관

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일 경로를 주고 "Laws of UX 행동·인지 리뷰", "lawsofux UX 평가", "UX 법칙 검토", "인지/행동 UX 리뷰" 등을 요청할 때
- 화면의 정보 구조·선택지 구성·인지 부담·사용자 관행 준수 여부를 점수+개선 액션으로 진단하고 싶을 때
- 멀티 스텝 폼·결제 플로우·내비게이션 구조 등 행동 패턴이 중심인 화면을 검토할 때

## Do Not Use

- **시각·게슈탈트 법칙 평가** (Aesthetic-Usability, Von Restorff, Common Region, Proximity, Similarity, Prägnanz, Uniform Connectedness) → `design-ui-lawsofux-review` 사용
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

### Step 4 — Rubric 적용 (23개 법칙 순회)

각 법칙마다:
- **정적 검증 N/A** (Doherty Threshold, Parkinson's Law, Peak-End Rule, Flow): 점수표에 `N/A` + 사유 한 줄. finding 없음. 단, 관련 UI(스켈레톤/타이머/완료화면/진행률)가 디자인되어 있으면 info 로 별도 기록 가능.
- **정적 검증 Yes/Partial**: 체크리스트 항목을 deep 노드 트리·스크린샷에 대해 평가 → 위반/개선점 발견 시 finding 작성 (severity + evidence + fix + lawsofux.com 링크), 점수 0–10 산출. 위반 없으면 점수만 기록.

점수 기준: 9–10 모범 / 7–8 양호 / 5–6 보통 / 3–4 미흡 / 0–2 심각

### Step 5 — Top-3 우선순위 산출

1. 모든 critical 우선
2. critical 부족 시 warning 으로 채움
3. 동일 severity 내: 진입 직후 마주치는 요소 > 1차 CTA/컨버전 경로 > 위반 항목 수
4. 정확히 3개 (부족하면 그만큼만)

### Step 6 — 보고서 작성 + 사용자 요약 출력

- frame-slug: frame.name 을 kebab-case 소문자화 (한글이면 음역 또는 nodeId 끝 8자)
- 날짜 토큰: `YYYYMMDD-HHmm` (KST)
- 출력 경로: `./design-reviews/design-ux-lawsofux-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- 디렉터리 없으면 생성 후 보고서 작성
- 완료 시 경로 목록 + 각 프레임 종합 점수·critical 수·warning 수 한 줄 요약 출력

## 보고서 구조 (한국어)

```markdown
# Laws of UX 행동·인지 리뷰: {frame.name}

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
- 검증 적용 법칙: {applied}/23 (N/A: {na})

## 점수표 (23개 법칙)

| # | 법칙 (Law) | 점수 | 비고 |
|---|-----------|------|------|
| 1 | Hick's Law | 8 | - |
| 5 | Doherty Threshold | N/A | 응답 시간 측정 불가 |
| ... | ... | ... | ... |

## Findings

### Fitts's Law — score: 4
- **severity**: critical
- **evidence**: `Frame > Footer > BuyButton` (높이 28px, 인접 버튼과 4px 간격)
- **fix**: 1차 CTA 높이 28px → 48px 로 증가, 인접 버튼 간격 8px+ 확보
- **참고**: https://lawsofux.com/fittss-law

{위반/개선점이 있는 법칙만}

## Top-3 우선순위

1. **Fitts's Law (critical)** — 1차 CTA 터치 영역 부족. 48px 이상으로 증가.
2. **Jakob's Law (warning)** — 로고 위치 비관행. 좌측 상단으로 이동.
3. **Cognitive Load (warning)** — 시각 요소 과밀. 핵심 정보 우선 정리.

## N/A 항목 (검증 보류)

- Doherty Threshold: 응답 시간 측정 필요
- Flow: 인터랙션 흐름 필요
- Parkinson's Law: 시간 흐름 필요
- Peak-End Rule: 시간적 흐름 필요
```

## 출력 포맷

- **경로**: `./design-reviews/design-ux-lawsofux-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- **finding 헤더**: `### {법칙명} — score: {N}` (annotate-design 호환)
- **finding 필드**: severity / evidence / fix / 참고 (lawsofux.com 링크)
- evidence: 노드 이름·트리 경로·수치 명시
- fix: 한 줄 액션 문구 (구체 수치 포함)
- 보고서는 프레임당 1파일, 모든 텍스트 한국어 (법칙 이름은 영어 원어 유지)

## 인자

```
/design-ux-lawsofux-review <Figma URL | .pen path>
```

위치 인자 1개 필수. 멀티 프레임은 Figma/Pencil 의 현재 선택으로 자동 감지.

## 예시

### 예시 1 — Figma URL

```
/design-ux-lawsofux-review https://www.figma.com/design/abc123XYZ/MyApp?node-id=42-1024
```

→ Figma MCP 체크 → metadata + design_context + screenshot 수집 → 23개 UX 법칙 평가 → `./design-reviews/design-ux-lawsofux-review-checkout-screen-20260514-1130.md` 생성

### 예시 2 — Pencil 멀티 프레임

```
/design-ux-lawsofux-review ~/Documents/myapp.pen
```

→ Pencil MCP 체크 → 선택 3 frame 감지 → 각 frame 평가 → 3개 파일 생성

### 예시 3 — MCP 미연결

→ ToolSearch 결과 0건 → 안내 메시지 출력 후 종료

## Non-Goals

- 시각·게슈탈트 법칙 7개 평가 → `design-ui-lawsofux-review`
- Figma/Pencil 코멘트 직접 게시 → `annotate-design`
- 인터랙션·애니메이션 분석
- Nielsen/IxDF/Baymard 등 다른 rubric → 해당 skill

## References

- 평가 rubric 원본: `~/.claude/skills/lawsofux-review/references/laws-rubric.md` (UX 23개 항목 참조)
- 원본 법칙 출처: https://lawsofux.com/
- UI 시각·게슈탈트 variant: `design-ui-lawsofux-review`
- 코멘트 게시: `annotate-design`
