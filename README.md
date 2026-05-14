# claude-design-skills

Claude Code 디자인 리뷰 + 어노테이션 스킬 모음. **Pencil(.pen)** 파일과 **Figma** URL 모두 지원. 11개 스킬, 1 command 설치.

## 무엇을 하나

| 카테고리 | 스킬 수 | 용도 |
|---|---|---|
| 디자인 리뷰 (정적 분석) | 10 | 프레임을 rubric 기반으로 분석 → 한국어 마크다운 리뷰 보고서 생성 |
| 어노테이션 | 1 | 리뷰 .md → 캔버스에 코멘트 패널 + 번호 마커 + After mockup 자동 부착 |

## 설치

```
/plugin marketplace add jaehoonkim-x/claude-design-skills
/plugin install claude-design-skills@claude-design-skills
```

11개 스킬 자동 등록 → 슬래시 명령으로 즉시 사용 가능.

## 사용 흐름

```
1. 리뷰 생성
   /design-ux-nielsen-review <figma-url-or-.pen>
   → .md 보고서 출력

2. 캔버스에 부착
   /annotate-design ./reviews/nielsen-output.md
   → Pencil/Figma 캔버스에 코멘트 패널 + 마커 + mockup 부착
```

## 리뷰 스킬 (10)

### UX 5종

| Skill | Rubric | 출처 |
|---|---|---|
| `design-ux-lawsofux-review` | 23 행동·인지 UX 법칙 | [lawsofux.com](https://lawsofux.com) |
| `design-ux-nielsen-review` | 9 UX 사용성 휴리스틱 | Jakob Nielsen |
| `design-ux-ixdf-review` | 12항목 (5 Factors + 4 Usability + 2 Interaction Dim) | IxDF |
| `design-ux-ecommerce-review` | 5 카테고리 (Form/Filter/Checkout/Cart/Trust) | Baymard Institute |

### UI 6종

| Skill | Rubric | 출처 |
|---|---|---|
| `design-ui-lawsofux-review` | 7 시각·게슈탈트 UI 법칙 | [lawsofux.com](https://lawsofux.com) |
| `design-ui-nielsen-review` | Aesthetic & Minimalist 시각 휴리스틱 | Jakob Nielsen |
| `design-ui-ixdf-review` | 5항목 (Desirable + Engagement + 3 Interaction Dim) | IxDF |
| `design-ui-ecommerce-review` | 3 카테고리 (Product Card / PDP / Homepage·PLP visual) | Baymard Institute |
| `design-ui-polish-review` | 10 시각 디자인 차원 (Hierarchy·Typography·Color·Spacing 등) | 자체 |
| `design-ui-critic-review` | 디자이너 비평 관점 (AI slop 판별 포함) | 자체 |

## 어노테이션 스킬 (1)

### `annotate-design`

리뷰 .md → 디자인 캔버스에 시각화. 생성물 3종:

1. **코멘트 패널** — finding 카드 컬럼 (severity 색·점수·근거·fix·참고 링크)
2. **번호 마커** — 노드 위치에 핀처럼 떠 있는 원형 배지 (Pencil 한정. Figma 는 네이티브 코멘트 핀이 마커 역할)
3. **After 예시 mockup** — 각 카드 안에 fix 적용 후 모습 (Fitts·Selective Attention·Cognitive Bias 등 패턴별 카탈로그)

session-key 기반 ID 추적 (`{rubric}-{HHmm}.c{N}`, `.m{M}`) — 같은 캔버스에 여러 리뷰 누적해도 카드↔마커 양방향 탐색 가능.

## 요구 사항

| 출력 타겟 | MCP |
|---|---|
| `.pen` 파일 | Pencil MCP (`mcp__pencil__*`) |
| Figma URL | figma-console MCP (`mcp__figma-console__*`) — 쓰기 가능. claude.ai Figma MCP 는 읽기 전용 |

## 출력 언어

리뷰 마크다운·코멘트 패널 텍스트는 **한국어**. 법칙명·원어 표기는 영어 유지.

## 라이선스

MIT
