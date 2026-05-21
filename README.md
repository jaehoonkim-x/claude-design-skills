# claude-design-skills

Claude Code 디자인 리뷰 + 어노테이션 스킬 모음. **Pencil(.pen)** 파일과 **Figma** URL 모두 지원. **25개 스킬**, 1 command 설치.

## 무엇을 하나

| 카테고리 | 스킬 수 | 용도 |
|---|---|---|
| 디자인 리뷰 (정적 분석) | 23 | 프레임을 rubric 기반으로 분석 → 한국어 마크다운 리뷰 보고서 생성 (L0 UI 10 / L1 UX 6 / L2 UX 5 / L5 Strategy 2) |
| 멀티 레벨 wrapper | 2 | `design-review-all` (24개 rubric 5×N wave · rate limit 0건 · ~21분) · `design-review-essential` (14개 검증 rubric · ~10분 sanity check) |
| 어노테이션 | 1 | 리뷰 .md (개별/집계) → 캔버스 옆 severity 3컬럼 코멘트 패널 + SourceRail chip + After 시각 mockup 자동 부착 |

## v2.0.1 핵심 변경 (2026-05-21)

- **스킬 +1**: `design-ux-toss-review` 추가 (L2 Structure) — Toss 「Apps in Toss」 가이드 직격
- **wrapper +1**: `design-review-essential` 추가 — 14개 검증 스킬 (review-all 1/3 버전, ~10분 sanity check)
- **출처**: [Apps in Toss · Consumer UX Guide](https://developers-apps-in-toss.toss.im/design/consumer-ux-guide.html) · [UX Writing Guide](https://developers-apps-in-toss.toss.im/design/ux-writing.html)
- **rubric**: Consumer UX Dark Pattern 5룰 (DP-1~5) + UX Writing 5원칙+보조 (W-1~5 + W-Aux) = 10 항목
- **헤드라인**: Toss Compliance Grade (A-F) + Dark Pattern Health + Writing Health + Toss Approval Likelihood
- **활용**: 토스 입점 미니앱 / 토스 결제 연동 / 토스 톤 차용 셀러 화면 컴플라이언스 사전 audit

## v2.0 핵심 변경 (2026-05-19)

- **스킬 수**: 12 → 24 (+12, L0 +4 / L1 +3 / L2 +5 / L5 +1) — v2.0.1 에서 L2 +1 (Toss)
- **wrapper 최적화 8개**: Wave dispatch 5×N · Conditional pre-skip · Snapshot 캐싱 · Schema 1x · 보고서 250라인 cap · Heavy 우선 wave · Caveman 프롬프트 · 180s timeout
- **wall-clock**: ~28분 (병렬 23 + retry) → ~21분 (5 wave)
- **rate limit fail**: 평균 5건 → **0건** (100% 해소)
- **토큰**: -55% (snapshot 캐싱 + 프롬프트 압축 + cap)

## 설치

```
/plugin marketplace add jaehoonkim-x/claude-design-skills
/plugin install claude-design-skills@claude-design-skills
```

25개 스킬 자동 등록 → 슬래시 명령으로 즉시 사용 가능.

## 사용 흐름

```
1. 리뷰 생성 (단일 rubric)
   /design-ux-nielsen-review <figma-url-or-.pen>
   → .md 보고서 출력

2. 캔버스에 부착
   /annotate-design ./reviews/nielsen-output.md
   → Pencil/Figma 캔버스 옆에 코멘트 패널 + After 시각 mockup 부착

3. (선택) 멀티 레벨 일괄
   /design-review-all <design 파일>
   /annotate-design ./design-reviews/design-review-all-*.md
   → 23개 rubric 집계 finding 을 dedupe + SourceRail chip 으로 시각화
```

## 리뷰 스킬 (24)

### L0 Surface — UI 10종

| Skill | Rubric | 출처 |
|---|---|---|
| `design-ui-critic-review` | 디자이너 비평 + AI Slop | gstack `/design-review` 기반 |
| `design-ui-ixdf-review` | 5항목 (Desirable + Engagement + 3 Interaction Dim) | IxDF |
| `design-ui-polish-review` | 10 시각 디자인 차원 | gstack `/ui-design-review` 기반 |
| `design-ui-checklist-review` | Checklist Design 56 카탈로그 (5 카테고리) | checklist.design |
| `design-ui-token-drift-review` | Figma/Pencil 변수 vs hard-coded drift + Tailwind ds-* 매핑 | FigmaLint·Design Lint |
| `design-ui-tufte-dataviz-review` | Tufte 10 + AG Grid 10 dataviz 전용 | Edward Tufte |
| `design-ui-gestalt-review` | Gestalt 6+4 시각 그룹화 원칙 | Gestalt Psychology |
| `design-ui-wcag-review` | WCAG 2.2 78 SC a11y 전용 | W3C |
| `design-ui-polaris-ecommerce-review` | Shopify Polaris 셀러 admin 7 카테고리 | Shopify Polaris |
| `design-ui-erik-kennedy-review` | Learn UI Design 7 핵심 룰 | learnui.design |

### L1 Skeleton — UX 6종

| Skill | Rubric | 출처 |
|---|---|---|
| `design-ux-lawsofux-review` | 23 행동·인지 UX 법칙 | [lawsofux.com](https://lawsofux.com) |
| `design-ux-nielsen-review` | 9 UX 사용성 휴리스틱 | Jakob Nielsen |
| `design-ux-microcopy-review` | UX writing 8 lens (Hemingway + Maria Guide) | NN/g·MailChimp |
| `design-ux-norman-review` | Don Norman 6 개념 + 7 Stages + Gulf 측정 | The Design of Everyday Things |
| `design-ux-form-review` | Adam Silver Form Design Patterns 12 lens (conditional) | Adam Silver |
| `design-ux-states-review` | Loading/Empty/Error/Success/Offline/Permission/Stale 7 state × 3 sub = 21 | NN/g |

### L2 Structure — UX Flow / Eval 6종

| Skill | Rubric | 출처 |
|---|---|---|
| `design-ux-flow-review` | 6 Lens × 36 항목 (Flow / IA / Edge State / Dark Pattern / Conversion / Habit) | NN/g·Norman·Brignull·Hooked |
| `design-ux-dark-pattern-review` | Brignull 12 dark pattern + 규제 매핑 (GDPR/CPRA/한국 e-privacy) | deceptive.design |
| `design-ux-cognitive-walkthrough-review` | Lewis & Polson 1990 CW 4Q + Streamlined CW + Gulf (conditional, 2+ frame) | Lewis & Polson |
| `design-ux-pure-review` | NN/g PURE Method task usability 정량 점수 | NN/g |
| `design-ux-heart-review` | Google HEART Framework + GSM (Goals-Signals-Metrics) | Google Research |
| `design-ux-toss-review` | Toss 「Apps in Toss」 가이드 10룰 (DP 5 + Writing 5) — L1-L2 hybrid | [Apps in Toss · Consumer UX](https://developers-apps-in-toss.toss.im/design/consumer-ux-guide.html) · [UX Writing](https://developers-apps-in-toss.toss.im/design/ux-writing.html) |

### L5 Strategy — CEO + JTBD 2종

| Skill | Rubric | 출처 |
|---|---|---|
| `design-ceo-review` | CEO/founder 10 전략 항목 (Premise·Leverage·Dream·KPI·Scope·자산 등) | gstack `/plan-ceo-review` 기반 |
| `design-ux-jtbd-review` | Jobs-To-Be-Done 5 lens + 4 Forces of Progress | Clayton Christensen |

## 멀티 레벨 wrapper (2)

### `design-review-all`

24개 rubric (UI 10 + UX 6 + UX Flow 6 + Strategy 2) 을 **5×N wave dispatch** 로 분할 실행 → L0 Surface + L1 Skeleton + L2 Structure + L5 Strategy 동시 진단. 개별 보고서 N개 + 집계 보고서 1개 (`design-review-all-{frame-slug}-{ts}.md`) 생성.

**v2.0 최적화 8개**:

| # | 최적화 | 효과 |
|---|--------|------|
| 1 | Wave dispatch 5×N | rate limit 0건 보장 |
| 2 | Conditional pre-skip (form / CW) | ~6분 절약 |
| 3 | Pencil/Figma snapshot 1회 캐싱 | 중복 fetch 제거 → 토큰 -25% |
| 4 | Schema 1회 inject (`include_schema: false`) | 토큰 -8k×23 |
| 5 | 보고서 250라인 / 25 finding cap | 출력 토큰 -30% |
| 6 | Heavy 우선 wave 배치 | critical path 단축 |
| 7 | Caveman 프롬프트 압축 (1500자 → 450자) | 입력 토큰 -30% |
| 8 | 180s hard timeout | hung skill 차단 |

**Wave 구성 예시 (N=21, 5 wave)**:

```
Wave 1 (heavy 1): ui-token-drift · ux-flow · ceo · ui-tufte-dataviz · ux-lawsofux
Wave 2 (heavy 2): ui-wcag · ux-norman · ux-dark-pattern · ux-jtbd · ui-critic
Wave 3 (heavy 1): ui-checklist · ux-pure · ux-heart · ui-polaris · ux-nielsen
Wave 4 (heavy 1): ui-polish · ux-states · ui-gestalt · ui-ixdf · ux-microcopy
Wave 5 (light): ui-erik-kennedy
```

**옵션**:
- `--skip <skill1,skill2,...>` — 특정 rubric 제외
- `--only <skill1,...>` — 지정 rubric 만 실행
- `--goal "{task}"` / `--lens A,B,C` — `design-ux-flow-review` 인자 전달

```
/design-review-all ~/myapp.pen
/design-review-all https://figma.com/design/abc?node-id=42-1024 --skip design-ui-tufte-dataviz-review
/design-review-all ~/myapp.pen --only design-ui-wcag-review,design-ui-polaris-ecommerce-review
```

### `design-review-essential`

14개 핵심 스킬만 선별한 **review-all 1/3 버전**. broad coverage + validated quality 기준으로 신규/niche 제외, 검증된 광범위 rubric 만 사용. L0 UI(5) + L1 UX(3) + L2 UX(2) + L5 Strategy(1) + 도메인 특화(3, Polaris·Checklist·Toss 포함) 총 14개 병렬 dispatch + 통합 요약.

언제 써:
- 빠른 다층 sanity check (~10분, review-all 의 1/3 wall-clock)
- 검증된 rubric 만 — 실험적·niche 스킬 제외 원할 때
- 프레임 review milestone 직전 standard pass

```
/design-review-essential ~/myapp.pen
/design-review-essential https://figma.com/design/abc?node-id=42-1024
```

## 어노테이션 스킬 (1)

### `annotate-design`

리뷰 .md → 디자인 캔버스 **옆** 에 시각화 (캔버스 위 핀·네이티브 코멘트 부착 안 함). 생성물 2종:

1. **severity 3컬럼 코멘트 패널** — Pencil/Figma 우측 (CRITICAL/HIGH · WARNING/MED · INFO/LOW). 각 카드 = 번호 배지 + 카드 ID chip + Title + Body + (집계 모드) SourceRail chip
2. **After 시각 mockup** — 각 카드 안에 fix 적용 후 모습. **Iron Rule**: 텍스트 2줄 폴백 금지, 항상 시각 요소 1개 이상. 32+ 패턴 카탈로그 (Empty/Loading·CTA·Search scope·Status pill·Table 효율·Notification·WCAG·Token contract·도메인 KPI·Sparkline·Chart context·Sidebar IA·Touch target·Card elevation·Avatar·Tabular nums·Responsive·Brand swap·Fitts·Von Restorff·Cognitive Bias 등)

#### 입력 모드 자동 감지

| 모드 | 트리거 | 카드 |
|---|---|---|
| 개별 | `### 법칙명 — score: N` 패턴 .md | severity·점수·evidence·fix·link + After mockup |
| 집계 | `design-review-all-*.md` 또는 `## 통합 finding 목록` 헤더 | HIGH/MID/LOW · **SourceRail chip** (어떤 리뷰가 같은 finding 을 잡았는지 시각화) + After mockup |

session-key 기반 ID 추적 (`{type-prefix}-{HHmm}.c{N}`) — `crit-1310.c5`, `lawsofux-1430.c3`, `revall-1605.c12` 등 자기 설명적. 같은 캔버스에 여러 리뷰 누적해도 출처 즉시 파악.

## 요구 사항

| 출력 타겟 | MCP |
|---|---|
| `.pen` 파일 | Pencil MCP (`mcp__pencil__*`) |
| Figma URL | figma-console MCP (`mcp__figma-console__*`) — 쓰기 가능. claude.ai Figma MCP 는 읽기 전용 |

## 출력 언어

리뷰 마크다운·코멘트 패널 텍스트는 **한국어**. 법칙명·원어 표기는 영어 유지.

## 라이선스

MIT
