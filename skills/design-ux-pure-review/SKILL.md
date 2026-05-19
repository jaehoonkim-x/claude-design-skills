---
name: design-ux-pure-review
review-level: L2 Structure
description: "[L2 Structure] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임 시퀀스를 NN/g PURE Method(Pragmatic Usability Rating by Experts)로 분석하여 task 정량 점수를 산출. 각 step 을 Green(1.0) · Yellow(0.5) · Red(0.0) 3등급으로 평가 → PURE Score(0-100) + step별 분포 + Top-3 Red Step. 사용자가 \"PURE 리뷰\", \"task usability 점수\", \"step 정량 평가\", \"PURE score 측정\", \"task completion 점수\", \"/design-ux-pure-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 task step 정량 점수를 요청할 때 사용."
---

# design-ux-pure-review

**Review Level**: L2 Structure — NN/g PURE Method, task usability 정량 점수.

NN/g PURE(Pragmatic Usability Rating by Experts) Method 를 평가 rubric 으로 사용하여 task flow 의 각 step 을 3등급으로 정량 평가한다. 11종 정성 리뷰 스킬이 잡지 못하는 **task 완료 가능성을 숫자로 게이팅**하는 것이 핵심 목적이다. 신규 페이지·flow 출시 전 PURE Score 기준점(예: ≥ 70)을 통과 조건으로 활용한다. 리포트만 생성한다 — 코멘트 게시는 `annotate-design` 책임.

평가 렌즈 = "사용자가 이 task 의 각 step 을 얼마나 쉽게 완료할 수 있는가? 실패 확률을 0-100%로 추정하여 정량화한다."

## 3등급 rubric

| 등급 | 점수 | 정의 | 실패 확률 |
|------|------|------|----------|
| **Green** | 1.0 | Easy — 명확하고 자연스러운 step. 훈련 없이도 완료 가능 | ≤ 5% |
| **Yellow** | 0.5 | Moderate friction — 주저하거나 실수할 수 있으나 결국 완료 가능 | 5–50% |
| **Red** | 0.0 | Major friction — 상당수 사용자가 이 step 에서 실패하거나 포기 | > 50% |

## 6가지 평가 기준 (각 step 판정 시 종합 고려)

| 기준 | 설명 | Red 신호 |
|------|------|----------|
| **Difficulty of step** | step 자체의 인지·조작 난이도 | 전문 지식 요구, 비직관적 인터랙션 |
| **Required reading** | step 완료에 필요한 텍스트 읽기 부담 | 긴 설명, 작은 글씨, 전문 용어 |
| **Click count** | 해당 step 에서 요구되는 클릭/탭 수 | 3+ 클릭, 숨겨진 드롭다운, 중첩 메뉴 |
| **Decisions required** | 사용자가 선택·판단해야 하는 분기 수 | 2+ 선택지 동시 노출, 선택 결과 불명 |
| **Memory load** | 이전 step 정보를 기억해야 하는 정도 | 다른 화면에서 본 값 입력, 페이지 간 컨텍스트 유지 |
| **Error likelihood** | 잘못된 입력·액션이 발생할 구조적 가능성 | 비가역 액션 무확인, validation 없는 자유 입력 |

## PURE Score 공식

```
PURE Score = Σ(step scores) / N × 100
```

- N = 평가 대상 step 수
- step score ∈ {0.0, 0.5, 1.0}
- 결과 범위: 0–100

### 점수 해석

| 범위 | 등급 | 해석 |
|------|------|------|
| 85–100 | **A** | Excellent — 출시 가능, 미세 polish 수준 |
| 70–84  | **B** | Good — 권장 출시 최저선. 주요 Yellow step 개선 |
| 55–69  | **C** | Fair — Red step 해소 전 출시 보류 권고 |
| 40–54  | **D** | Poor — flow 재설계 필요 |
| 0–39   | **F** | Critical — 전면 재설계 |

## When to Use

- 신규 페이지·task flow 출시 전 **정량 게이트**가 필요할 때 (예: PURE Score ≥ 70 통과 기준)
- 정성 리뷰(Nielsen·IxDF·Laws of UX 등)를 마쳤으나 **객관적 수치**로 우선순위 설정이 필요할 때
- A/B 디자인 대안의 **task usability 비교**가 필요할 때
- 재설계 전후 delta 측정으로 **개선 효과 검증**이 필요할 때

## Do Not Use

- 단일 frame 미관·레이아웃 평가 → `design-ui-*-review`
- 전체 flow 구조·IA 분석(6 lens) → `design-ux-flow-review`
- Nielsen 9 휴리스틱 정성 평가 → `design-ux-nielsen-review`
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 라이브 사이트 실측 → gstack `/design-review`

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 중 하나 활성화 후 재시도." |
| `*.pen` 로컬 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: Step 1 에서 ToolSearch 로 prefix 의 도구를 조회. 결과가 비어 있으면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + MCP 사전 체크

사용자 인자에서 입력 타입을 자동 감지:

- `figma.com/design/:fileKey/...?node-id=:nodeId` → **Figma 경로**
- `*.pen` 로컬 경로 → **Pencil 경로**
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 즉시 종료.

옵션 인자 처리:
- `--task "{task goal}"`: 평가 대상 task 목표 명시 (없으면 frame 이름에서 추정)
- `--threshold {N}`: PURE Score 통과 기준점 설정 (기본값 70)

### Step 2 — flow 데이터 수집

**Multi-frame mode (Figma):**
1. 선택 frame 마다 `get_metadata` + `get_design_context(depth:6)` + `get_screenshot`
2. frame 시퀀스 = 선택 순서 또는 `?node-id` 순서
3. frame 간 추정 transition trigger 식별 (각 frame 의 primary CTA·button·link 추출)

**Multi-frame mode (Pencil):**
1. `open_document` + `get_editor_state` → 선택 frame 목록
2. 각 frame `batch_get(readDepth:4)` + `snapshot_layout` + `get_screenshot`
3. 시퀀스 = 선택 순서 또는 frame name 패턴(`Step 1`, `Step 2` 등) 자동 정렬

**단일 frame:**
- flow 전체를 단일 frame 안의 step-by-step 인터랙션으로 추정
- 가시적인 CTA 순서를 step 으로 분해 (최대 12 step)

선택이 없으면: "Figma/Pencil 에서 리뷰할 flow 의 frame(들)을 선택해주세요." 출력 후 종료.

### Step 3 — Task Goal + 추정 페르소나 정의

수집된 frame 이름·CTA·콘텐츠에서 추론:

- **Task Goal**: 사용자가 이 flow 로 달성하려는 단일 목표 (예: "상품 등록 완료", "비밀번호 변경")
- **Entry Point**: 사용자가 task 를 시작하는 첫 frame + 진입 맥락
- **Success Criterion**: 마지막 frame 에서 task 완료를 판단하는 기준 (확인 메시지, 상태 변경 등)
- **추정 페르소나**: 이 task 를 수행할 사용자 유형 1-2명 (역할·숙련도·기기)

`--task` 인자 있으면 Task Goal 로 직접 사용.

### Step 4 — Step Decomposition

수집된 frame 시퀀스를 평가 단위 step 으로 분해:

| Step | Frame | 사용자 행동 | Primary CTA / 입력 | 완료 신호 |
|------|-------|-----------|-------------------|----------|
| 1 | ... | ... | ... | ... |
| 2 | ... | ... | ... | ... |

분해 규칙:
- frame 1개 = 원칙적으로 step 1개. 단, frame 내 2+ 독립 액션은 sub-step 으로 분할
- 정보 확인만 하는 frame(스크린, 완료 확인 화면)도 step 으로 포함
- 최소 3 step, 최대 20 step 으로 제한 (초과 시 논리 단위로 그루핑)

### Step 5 — First Impression

step 목록을 확정한 직후, 평가 전 1인칭 직관 기록:

```
- task goal: [한 문장]
- 가장 위태로운 step 예감: [step 번호 + 이유]
- 가장 매끄러운 step 예감: [step 번호 + 이유]
- 전체 인상 한 단어: [단어]
- 주목할 패턴: [긍정 또는 부정 관찰 1-2줄]
```

진단가는 헤지하지 않는다.

### Step 6 — Per-Step PURE Evaluation

각 step 을 6가지 평가 기준으로 종합 판정. 각 기준을 Low/Medium/High 로 먼저 평가한 뒤 등급 결정:

**판정 로직:**
- 6개 기준 중 **High 가 2+ 개** 또는 **Error likelihood = High** → **Red(0.0)**
- 6개 기준 중 **High 가 1개** 또는 **Medium 이 3+** → **Yellow(0.5)**
- 나머지 → **Green(1.0)**

각 step 에 대해 finding 블록 작성 (Green 도 포함, Yellow/Red 는 필수):

```
### Step {n} — score: {0.0 | 0.5 | 1.0}
- **severity**: Red=critical | Yellow=warning | Green=info
- **step**: {frame 이름 + 사용자 행동 요약}
- **evidence**: frame `{nodeId}` · {구체 근거: 기준별 High/Medium 사유}
- **fix**: {step 을 Green 으로 올리기 위한 구체 액션}
- **PURE-criteria**: Difficulty={L/M/H} · Reading={L/M/H} · Clicks={L/M/H} · Decisions={L/M/H} · Memory={L/M/H} · Error={L/M/H}
```

Green step 은 fix 를 "없음 — 현재 상태 유지" 로 기록.

### Step 7 — PURE Score 산출

```
PURE Score = Σ(step scores) / N × 100
```

분포 집계:
- Green step 수 / Yellow step 수 / Red step 수
- Green 비율(%) / Yellow 비율(%) / Red 비율(%)

점수 등급 판정 (85-100=A, 70-84=B, 55-69=C, 40-54=D, 0-39=F).

**임계값 판정**: `--threshold` 기준(기본 70)과 비교 → PASS / FAIL 표시.

### Step 8 — Top-3 Red Step 선정

Red step 이 3개 미만이면 Yellow step 으로 채운다. 선정 우선순위:

1. Red(0.0) step — Error likelihood High 우선
2. Red(0.0) step — task flow 에서 회피 불가능한 step(mandatory)
3. Yellow(0.5) step — Decisions + Memory 복합 부담

각 카드 포맷:
- **step 위치**: step 번호 + frame 이름
- **등급**: Red / Yellow
- **주요 마찰 기준**: 6가지 중 High 항목 나열
- **사용자 영향**: 실패 시나리오 (구체적, 1-2문장)
- **재설계 방향**: step 제거 / 단순화 / 분할 / 라벨 교체 / 자동화 / 기본값 제공 / 확인 추가
- **기대 점수 변화**: Red→Yellow(+0.5) 또는 Red/Yellow→Green(+0.5/+1.0)
- **노력 규모**: Low / Medium / High (1-2 weeks / 2-4 weeks / 4+ weeks)

### Step 9 — Step Distribution Chart (텍스트 기반)

ASCII bar chart 형태로 step 분포를 시각화:

```
Step  1  ██████████ Green  (1.0)
Step  2  █████      Yellow (0.5)
Step  3             Red    (0.0)
Step  4  ██████████ Green  (1.0)
...
```

### Step 10 — PURE Score 해석 + 개선 로드맵

전체 점수에 대한 해석:
- **현재 상태**: 점수·등급·통과 여부 한 줄 요약
- **병목 패턴**: 반복되는 마찰 기준 (예: "Decisions 부담이 전체 step 의 60% 에서 Yellow 이상")
- **빠른 승리(Quick Win)**: 노력 Low 로 Yellow→Green 전환 가능한 step (2-3개)
- **구조적 개선**: 노력 Medium/High 이지만 PURE Score 를 10+ 올릴 step (1-2개)

### Step 11 — 보고서 작성

**파일 경로**: `./design-reviews/design-ux-pure-review-{task-slug}-{YYYYMMDD-HHmm}.md`
- `{task-slug}`: task goal kebab-case (예: `product-register`, `password-change`)
- goal 미지정이면 entry frame name 사용
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 12 — 사용자에게 결과 요약

- 생성된 보고서 파일 경로
- PURE Score + 등급 + PASS/FAIL (임계값 기준)
- step 분포: Green {n}개 / Yellow {n}개 / Red {n}개
- Top-3 Red Step 번호 + 한 줄 마찰 요약
- 빠른 승리 step 번호 + 예상 점수 상승폭
- 다음 액션 제안 (fix 구현 → 재평가 / annotate-design 으로 파일에 마커 부착)

## 보고서 구조 (한국어)

```markdown
# PURE Review: {task goal}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID(s): {nodeId 시퀀스}
- 프레임 이름(s): {frame.name 시퀀스}
- task goal: {사용자 인자 또는 추정}
- 추정 페르소나: {역할·숙련도·기기}
- 평가 step 수: {N}
- 임계값: {threshold} (기본 70)
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 방법론: NN/g PURE Method (Christian Rohrer) — https://www.nngroup.com/articles/pure-method/

## 헤드라인
- **PURE Score: {score}/100** — 등급: {A/B/C/D/F}
- **판정: {PASS ✅ | FAIL ❌}** (임계값 {threshold} 기준)
- Green: {n}개 ({%}) · Yellow: {n}개 ({%}) · Red: {n}개 ({%})
- Top Red Step: Step {n}, Step {n}, Step {n}

## Task 정의
- **Task Goal**: {한 문장}
- **Entry Point**: {첫 frame + 진입 맥락}
- **Success Criterion**: {완료 판단 기준}
- **추정 페르소나**: {역할·숙련도·기기}

## First Impression
- task goal: {...}
- 가장 위태로운 step 예감: {...}
- 가장 매끄러운 step 예감: {...}
- 전체 인상 한 단어: {...}
- 주목할 패턴: {...}

## Step Decomposition

| Step | Frame | 사용자 행동 | Primary CTA / 입력 | 완료 신호 |
|------|-------|-----------|-------------------|----------|
| 1 | ... | ... | ... | ... |
| 2 | ... | ... | ... | ... |

## Step Distribution Chart

```
Step  1  ██████████ Green  (1.0)
Step  2  █████      Yellow (0.5)
Step  3             Red    (0.0)
...
```

PURE Score: {score}/100 (Green {n} · Yellow {n} · Red {n})

## Per-Step Findings

### Step 1 — score: 1.0
- **severity**: info
- **step**: {frame 이름} · {사용자 행동}
- **evidence**: frame `{nodeId}` · 모든 기준 Low, 직관적 단일 클릭
- **fix**: 없음 — 현재 상태 유지
- **PURE-criteria**: Difficulty=L · Reading=L · Clicks=L · Decisions=L · Memory=L · Error=L

### Step 2 — score: 0.5
- **severity**: warning
- **step**: {frame 이름} · {사용자 행동}
- **evidence**: frame `{nodeId}` · Decisions=M (2가지 옵션이 동시 노출, 선택 결과 불명)
- **fix**: 기본값 선택 + 권장 옵션 강조 배지 추가. 선택 결과 preview 제공
- **PURE-criteria**: Difficulty=M · Reading=L · Clicks=M · Decisions=M · Memory=L · Error=L

### Step {n} — score: 0.0
- **severity**: critical
- **step**: {frame 이름} · {사용자 행동}
- **evidence**: frame `{nodeId}` · Error=H (비가역 삭제 액션 확인 없음) · Decisions=H (4가지 선택지 동시 노출)
- **fix**: 삭제 확인 다이얼로그 추가 + 선택지 순차 노출(wizard 패턴)
- **PURE-criteria**: Difficulty=H · Reading=M · Clicks=H · Decisions=H · Memory=M · Error=H

{... 모든 step 나열 ...}

## Top-3 Red Step

### Red Step 1 — Step {n} · {frame 이름}
- **등급**: Red (0.0)
- **주요 마찰 기준**: Error=H · Decisions=H
- **사용자 영향**: {실패 시나리오 1-2문장}
- **재설계 방향**: {step 제거 / 단순화 / 분할 / 기본값 제공 / 확인 추가 등}
- **기대 점수 변화**: Step {n}: 0.0 → 0.5 (+0.5) → PURE Score +{delta}
- **노력**: {Low / Medium / High} ({n} weeks)

### Red Step 2 — ...
### Red Step 3 — ...

## PURE Score 해석 + 개선 로드맵

- **현재 상태**: {점수·등급·통과 여부}
- **병목 패턴**: {반복되는 마찰 기준 분석}
- **빠른 승리(Quick Win)**: Step {n} ({기대 +delta}) · Step {n} ({기대 +delta})
- **구조적 개선**: Step {n} ({기대 +delta}, {노력 규모})

## N/A 항목 (정적 분석 한정)
- {정적 분석으로 판정 불가한 step 또는 기준 + 사유}

## 다음 단계
- Red Step fix 구현 후 동일 rubric 으로 재평가 (delta 측정)
- annotate-design 스킬로 디자인 파일에 finding 마커 부착
- 5-8명 사용성 테스트로 PURE 예측치 검증
- A/B 대안 디자인 동일 rubric 비교 평가
```

## 인자

```
/design-ux-pure-review <Figma URL | .pen path> [--task "{task goal}"] [--threshold {N}]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- 옵션 `--task "{...}"`: 평가할 task 목표 명시 (없으면 frame 이름에서 추정)
- 옵션 `--threshold {N}`: PURE Score 통과 기준점 (기본값 70, 범위 0-100)
- frame 시퀀스는 Figma/Pencil **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Figma multi-frame, task 명시
```
/design-ux-pure-review https://www.figma.com/design/abc/EasySeller?node-id=42-1024 --task "상품 등록 완료"
```
→ Figma MCP 체크 → 6개 frame 감지 → Step 1-6 분해 → 6 기준 per-step 판정 → PURE Score 산출 → `./design-reviews/design-ux-pure-review-product-register-20260518-1430.md` 생성

### 예시 2 — Pencil multi-frame, 임계값 변경
```
/design-ux-pure-review ~/Documents/myapp.pen --task "비밀번호 변경" --threshold 80
```
→ Pencil MCP 체크 → 4개 frame 감지 → Step 1-4 분해 → PURE Score 산출 → 임계값 80 기준 PASS/FAIL 판정 → 보고서 생성

### 예시 3 — 단일 frame (인터랙션 추정)
```
/design-ux-pure-review https://www.figma.com/design/abc/EasySeller?node-id=10-200
```
→ 단일 frame → CTA 순서로 step 분해(최대 12) → PURE 평가 → 보고서 생성

### 예시 4 — MCP 미연결
```
/design-ux-pure-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 가 연결되어 있지 않습니다." 안내 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 등급명은 영어 원어 유지 (Green / Yellow / Red)
- 평가 기준명은 영어 원어 유지 (Difficulty, Required reading, Click count, Decisions required, Memory load, Error likelihood)
- finding 헤더 포맷 `### Step {n} — score: {0.0 | 0.5 | 1.0}` (annotate-design 스킬 파싱 호환)
- severity / step / evidence / fix / PURE-criteria 5 필드 동일 순서 유지
- Green step 도 finding 블록 필수 작성 (severity=info, fix="없음 — 현재 상태 유지")
- Top-3 Red Step · 개선 로드맵은 별도 섹션
- 보고서는 task 당 한 파일

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다. evidence 의 `frame \`{nodeId}\`` 패턴에서 nodeId 를 추출해 해당 frame 위에 마커 배치.

워크플로:
```
/design-ux-pure-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## 다른 스킬과의 관계

| 스킬 | 추상화 단계 | 평가 단위 | 출력 |
|------|-----------|----------|------|
| `design-ux-nielsen-review` | L1 Skeleton | 단일 frame | 정성 (0-10점) |
| `design-ux-flow-review` | L2 Structure | flow 시퀀스 | 정성 (A-F 등급, 6 lens) |
| **`design-ux-pure-review`** | **L2 Structure** | **task step 시퀀스** | **정량 (PURE Score 0-100)** |
| `design-ux-cognitive-walkthrough-review` | L2 Structure | task step | 정성 (PASS/FAIL per step) |
| `ux-audit-rethink` | L0-L2 holistic | product | 정성 (종합) |

**`design-ux-flow-review` 와의 차이**: flow-review 는 6 lens(IA·다크패턴·전환·습관 포함) 정성 구조 분석, pure-review 는 task step 실패 확률에만 집중하는 **정량 단일 지표** 산출.

**`design-ux-cognitive-walkthrough-review` 와의 차이**: cognitive walkthrough 는 4Q(올바른 결과·액션 노출·라벨 연관·피드백) 이분법(PASS/FAIL), pure-review 는 6 기준 3등급 **연속 수치**.

## Non-Goals

- 시각·미적 평가 — `design-ui-*-review` 책임
- IA / 다크패턴 / 전환 / 습관 평가 — `design-ux-flow-review` 책임
- 디자인 파일 코멘트 직접 게시 — `annotate-design` 책임
- 라이브 사이트 실측 / 성능 — gstack `/design-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 사용자 테스트 대체 — PURE 는 전문가 예측치. 실제 검증은 사용자 테스트 필요

## 참고 자료

- **NN/g PURE Method**: Christian Rohrer, "Pragmatic Usability Rating by Experts (PURE)" — https://www.nngroup.com/articles/pure-method/
- **PURE 원본 논문**: Rohrer, C. (NN/g) — 6 criteria rubric, 3-point scale (Green/Yellow/Red)
- **짝 정성 스킬**: `design-ux-flow-review` (L2 Structure 6 lens), `design-ux-cognitive-walkthrough-review` (L2 4Q)
- **짝 정량 활용**: stat-front 신규 페이지 출시 전 PURE Score ≥ 70 게이트로 활용
