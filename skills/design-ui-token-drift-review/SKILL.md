---
name: design-ui-token-drift-review
review-level: L0 Surface
description: "[L0 Surface] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 대상으로 디자인 시스템 토큰 drift 를 7개 렌즈(Color·Typography·Spacing·Border Radius·Shadow·Component Instance·Code Mapping)로 정적 분석하여 DS Compliance % + per-lens 점수 + Drift Findings + Auto-fix 후보를 한국어 마크다운 보고서로 생성. Figma 변수·Pencil 변수와 노드 raw 값을 비교하여 hard-coded value 를 검출하고 Tailwind ds-* 클래스 매핑 힌트 제공. FigmaLint·Design Lint·aficat/design-linter 룰셋 기반. 사용자가 \"토큰 드리프트\", \"DS 일관성\", \"token drift\", \"design token audit\", \"하드코딩 색상 검출\", \"shadcn/Tailwind 클래스 매핑\", \"/design-ui-token-drift-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 디자인 시스템 토큰 일관성 점검을 요청할 때 사용."
---

# design-ui-token-drift-review

**Review Level**: L0 Surface — Design System token drift 검출 (단일 프레임).

Figma/Pencil 파일의 변수(variable) 정의와 노드의 실제 fill·typography·spacing 값을 비교하여 variable reference 없이 raw 값이 직접 입력된 **drift** 를 검출한다. FigmaLint(Southleft)·Design Lint·aficat/design-linter 룰셋을 참조 기준으로 삼는다. 리포트 + Auto-fix 후보 집계만 수행한다 — 파일 직접 수정은 `replace_all_matching_properties` 제안에 그친다.

평가 렌즈 = "이 화면의 색상·타이포·간격·반경·그림자·컴포넌트·코드 매핑이 디자인 시스템 토큰과 얼마나 일치하는가? hard-coded raw 값이 얼마나 남아 있는가?"

## 7 Lens Rubric

| # | Lens | 검출 대상 | 정적 검증 |
|---|------|----------|----------|
| 1 | **Color** | hex/rgb 직접값 vs variable reference (fill·stroke·bg) | Yes |
| 2 | **Typography** | font-size·line-height·font-weight raw 값 vs typo 토큰 | Yes |
| 3 | **Spacing** | padding·gap·margin 이 8pt grid 배수 여부 + variable 참조 | Yes |
| 4 | **Border Radius** | radius raw 값 vs radius 토큰 variable | Yes |
| 5 | **Shadow** | box-shadow·drop-shadow raw 값 vs elevation 토큰 | Yes |
| 6 | **Component Instance** | main component detach 여부 + overridden prop 과잉 | Yes |
| 7 | **Code Mapping** | Figma 토큰 ↔ ds-*/Tailwind 클래스 매핑 정합성 | Partial |

### Lens 1. Color

- **variable reference 없음** = drift (hex·rgb·hsl raw 값이 fill 에 직접 입력)
- 동일한 hex 가 DS 변수에 존재하는데 참조 없이 복사한 경우도 drift 로 분류
- 브랜드 팔레트 외 임의 색상 사용은 severity: critical
- 1-2px 차이의 색상 근사값 사용은 severity: warning

### Lens 2. Typography

- DS typo scale 밖의 font-size (예: 13px, 15px, 22px 등 8pt grid 미달) = drift
- font-weight 가 DS 토큰(400/500/600/700) 외 임의값 = drift
- line-height 미설정 또는 DS 배수 외 = warning
- font-family 혼용(DS 외 폰트) = critical

### Lens 3. Spacing

- **8pt grid 규칙**: padding·gap·margin 이 4·8·12·16·20·24·32·40·48·64·80·96 의 배수여야 함
- 임의값(14·18·22·26·30 등) = drift
- Tailwind 매핑 힌트: `padding: 14px` → p-3.5 회피, `p-3(12px)` 또는 `p-4(16px)` 권장
- variable 참조 없이 raw 간격 직접 입력 = warning (값 자체가 grid 배수이더라도)

### Lens 4. Border Radius

- DS radius 토큰(예: radius-sm/md/lg/full) 없이 raw px 사용 = drift
- Tailwind 매핑: 2px→`rounded-sm`, 4px→`rounded`, 6px→`rounded-md`, 8px→`rounded-lg`, 12px→`rounded-xl`, 16px→`rounded-2xl`, 9999px→`rounded-full`
- 비표준 값(3px·5px·7px·9px 등 홀수) = warning

### Lens 5. Shadow

- DS elevation 토큰 없이 raw `box-shadow` 값 = drift
- Tailwind 매핑: `shadow-sm`, `shadow`, `shadow-md`, `shadow-lg`, `shadow-xl`, `shadow-2xl`, `shadow-inner`, `shadow-none`
- 커스텀 shadow 가 DS elevation 단계와 시각적으로 일치해도 토큰 미참조면 warning

### Lens 6. Component Instance

- main component detach = critical (컴포넌트가 frame 또는 group 으로 변환된 경우)
- instance prop override 3개 이상 = warning (over-customization 신호)
- 외부 라이브러리 컴포넌트가 local DS 컴포넌트 대신 사용된 경우 = warning

### Lens 7. Code Mapping

- Figma 변수명 `color/brand/primary` ↔ Tailwind `ds-brand-primary` 매핑 불일치
- DS 변수 존재 but 코드에 hard-coded hex 사용 = critical
- Tailwind `arbitrary value` 사용([#FF0000], [14px] 등) = warning (DS 클래스로 교체 권장)
- 정적 분석으로 코드 파일을 직접 열람하지 않으므로 Partial 검증; Figma 변수명 기반으로 매핑 힌트만 제공

## When to Use

- Figma/Pencil 파일에서 **토큰 drift 정량화**가 필요할 때
- DS 마이그레이션 전후 compliance % 측정 시
- shadcn/ui 또는 Tailwind DS 클래스 매핑 검증이 필요할 때
- 디자인 핸드오프 전 "hard-coded value zero" 체크리스트 통과 여부 확인
- FigmaLint / Design Lint 플러그인 실행 없이 유사 검출을 에이전트로 수행할 때

## Do Not Use

- 시각적 미학·브랜드 감성 평가 → `design-ui-ixdf-review`
- UX 흐름·정보 구조 평가 → `design-ux-flow-review`
- Nielsen 휴리스틱 평가 → `design-ui-nielsen-review`
- 접근성(WCAG) 검토 → `design-ui-wcag-review`
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 라이브 사이트 audit → gstack `/design-review`
- 실제 코드 파일의 Tailwind 클래스 검사(소스 grep 기반) → 별도 코드 리뷰 스킬

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__figma-console__*` 또는 `mcp__claude_ai_Figma__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 중 하나 활성화 후 재시도해주세요." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: Step 2 에서 ToolSearch 로 prefix 의 도구를 조회. 결과가 비어 있으면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + 타입 라우팅

사용자 인자에서 입력 타입을 자동 감지:

- `figma.com/design/:fileKey/...?node-id=:nodeId` → **Figma 경로**
- `*.pen` 로컬 경로 → **Pencil 경로**
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

Figma URL 파싱:
- fileKey = path 의 `/design/` 다음 세그먼트
- nodeId = `?node-id=` 쿼리 파라미터. `-` → `:` 변환

옵션 인자 처리:
- `--lens 1,3,7`: 평가할 lens 번호 명시 (1-7 콤마 구분). 미지정 시 7개 전부 적용.
- `--strict`: grid 배수 외 모든 raw 간격 값을 critical 로 상향 처리.

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

### Step 3 — 변수/토큰 정의 추출

**Figma 경로:**

1. `mcp__figma-console__figma_get_variables(fileKey)` 로 파일 전체 variable collection 수집
   - color·typo·spacing·radius·shadow 변수 목록 + 각 값(raw value) 추출
   - variable alias(참조) 관계 매핑
2. `mcp__figma-console__figma_get_styles(fileKey)` 로 text style·color style 추가 수집
3. 결과를 DS token map 으로 정규화:
   - `{ variableId, name, collection, type, resolvedValue }[]`

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_variables()` 로 파일 전체 변수 컬렉션 수집
3. 결과를 DS token map 으로 정규화

### Step 4 — 노드 속성 추출 (deep)

**Figma 경로:**

1. `mcp__figma-console__figma_get_file_data(fileKey, nodeId)` 로 대상 프레임 deep 트리 수집
2. 모든 하위 노드 순회:
   - fill (color raw value vs variable binding)
   - fontSize / fontFamily / fontWeight / lineHeight (raw vs style token)
   - padding / itemSpacing / gap (raw px)
   - cornerRadius / cornerRadiusTopLeft 등 (raw px)
   - effects[].type=DROP_SHADOW / INNER_SHADOW (raw vs effect style)
   - type=INSTANCE → mainComponent 참조 유효성 + overrides 개수
3. 각 노드의 `boundVariables` 필드로 variable binding 여부 확인

**Pencil 경로:**

1. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 확인
   - 선택 없으면: "Pencil 에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
2. 각 선택 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id])` 로 deep 트리 수집
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property="fill")` 로 fill 팔레트
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property="fontSize")` 로 typo 팔레트
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property="padding")` 로 간격 팔레트
   - property="cornerRadius", "shadow" 도 동일 패턴으로 추출

### Step 5 — Drift 분류

Step 3 의 DS token map 과 Step 4 의 노드 속성을 비교:

**분류 기준:**
- `variable reference 있음` + `resolvedValue 일치` → **COMPLIANT** (토큰 준수)
- `variable reference 없음` + `DS token map 에 동일 값 존재` → **DRIFT (alias missing)** — 값은 같으나 참조 없음 (warning)
- `variable reference 없음` + `DS token map 에 없는 값` → **DRIFT (raw value)** — 완전 이탈 (critical 후보)
- `component detach` → **DRIFT (detach)** — critical
- `instance override 3+` → **DRIFT (over-override)** — warning

8pt grid 검사 (Spacing lens):
- `value % 4 === 0` 이면서 DS spacing 토큰 참조 있음 → COMPLIANT
- `value % 4 === 0` 이지만 참조 없음 → DRIFT (alias missing)
- `value % 4 !== 0` → DRIFT (raw value) — `--strict` 시 critical, 기본 warning

### Step 6 — 7 Lens 평가

각 lens 마다 0-10 점수 산출. 정적 분석 불가 항목은 `N/A` + 사유.

**점수 공식 (lens 별):**
```
lens_score = 10 × (COMPLIANT 노드 수) / (전체 해당 노드 수)
```
critical drift 1건 당 -1.5, warning drift 1건 당 -0.5 추가 감점 (최저 0).

**Severity 가이드:**
- critical: DS 와 완전 이탈 raw value, detach component, DS 외 font-family
- warning: alias missing (값은 일치하나 참조 없음), 8pt grid 배수이지만 variable 미참조, instance over-override
- info: 개선 권장이지만 점수 영향 없음 (예: arbitrary Tailwind value 사용 힌트)

**점수 기준:**
- 10 — 모든 노드 토큰 준수 (drift 0건)
- 8-9 — 소수 alias missing, critical 없음
- 6-7 — warning 다수 또는 critical 1-2건
- 4-5 — critical 3건 이상 또는 전반적 raw value 사용
- 0-3 — 토큰 거의 미사용, DS 와 전면 이탈
- N/A — 해당 lens 노드 없음 (예: shadow 없는 flat design)

### Step 7 — DS Compliance % 산출

```
DS Compliance % = (전체 COMPLIANT 노드 수) / (전체 검사 노드 수) × 100
```

**등급 환산:**
- 95-100% = **A** (Excellent — DS token-complete)
- 85-94%  = **B** (Good — minor drift)
- 70-84%  = **C** (Acceptable — alias missing 다수)
- 50-69%  = **D** (Poor — raw value 광범위 사용)
- 0-49%   = **F** (Critical — DS 토큰 거의 미사용)

**추가 헤드라인:**
- **Auto-fix 가능 비율**: DRIFT (alias missing) 노드는 `replace_all_matching_properties` 로 자동 교체 가능 → auto-fixable % 별도 표기
- **Critical Drift**: `DRIFT (raw value)` + `DRIFT (detach)` 합계 건수

### Step 8 — Auto-fix 후보 집계

**Auto-fix 대상 조건**: DRIFT (alias missing) — 값이 DS 토큰에 존재하는데 참조만 없는 경우.

Pencil 경로에서는 `mcp__pencil__replace_all_matching_properties` 적용 가능 여부를 검증:
- 동일 raw 값을 가진 노드 N개가 있으면 일괄 교체 가능 → **batch auto-fix 후보**
- 각 후보에 대해: `{ property, rawValue, targetVariable, nodeCount, estimatedImpact }` 형태로 목록화

Figma 경로에서는 `mcp__figma-console__figma_batch_update_variables` 적용 가능 여부 힌트 제공 (실제 실행은 사용자 확인 후).

### Step 9 — Tailwind 클래스 매핑 힌트 생성

DS 변수명과 검출된 raw 값을 기반으로 권장 Tailwind 클래스 대응표 생성:

**Color:**
- `color/brand/primary` → `text-brand-primary` / `bg-brand-primary` (ds-* prefix 규칙 따름)
- raw `#3B82F6` → DS variable 검색 → 매핑 있으면 `bg-blue-500` 또는 `ds-blue-500` 제안

**Typography:**
- raw `font-size: 12px` → `text-xs`
- raw `font-size: 14px` → `text-sm`
- raw `font-size: 16px` → `text-base`
- raw `font-size: 18px` → `text-lg`
- arbitrary `text-[13px]` → `text-xs(12)` 또는 `text-sm(14)` 중 가까운 값으로 교체 권장

**Spacing — 8pt grid 매핑:**
- 4px → `p-1` / `gap-1`
- 8px → `p-2` / `gap-2`
- 12px → `p-3` / `gap-3`
- 14px → **p-3.5 회피** → `p-3(12px)` 또는 `p-4(16px)` 권장
- 16px → `p-4` / `gap-4`
- 20px → `p-5` / `gap-5`
- 24px → `p-6` / `gap-6`
- 32px → `p-8` / `gap-8`
- 40px → `p-10` / `gap-10`
- 48px → `p-12` / `gap-12`

**Border Radius:**
- 2px → `rounded-sm`
- 4px → `rounded`
- 6px → `rounded-md`
- 8px → `rounded-lg`
- 12px → `rounded-xl`
- 16px → `rounded-2xl`
- 9999px / 50% → `rounded-full`

**Shadow:**
- `0 1px 2px rgba(0,0,0,0.05)` → `shadow-sm`
- `0 4px 6px rgba(0,0,0,0.1)` → `shadow-md`
- `0 10px 15px rgba(0,0,0,0.1)` → `shadow-lg`
- `0 20px 25px rgba(0,0,0,0.15)` → `shadow-xl`

### Step 10 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-token-drift-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 11 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 DS Compliance % + Grade + critical/warning 건수 한 줄 요약
- Auto-fix 후보 카운트 (Pencil: 즉시 실행 가능 여부 포함)
- 상위 3개 drift 항목 이름 + 건수

### Step 12 — (선택) Top Drift 개선 제안

critical/warning finding 이 3건 이상이면 impact 순 상위 3개를 픽업하여 제안 카드 작성:

각 카드 포맷:
- **Drift 위치** (lens + 노드 경로)
- **현재 값** (raw value)
- **권장 토큰** (DS variable 이름 + Tailwind 클래스)
- **영향 범위** (동일 패턴 노드 수)
- **Fix 방법** (Pencil: replace_all / Figma: batch update / 수동)
- **노력 규모** (Low/Medium/High)

## 보고서 구조 (한국어)

```markdown
# DS Token Drift Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 적용 Lens: {1-7 중 적용된 것}
- 방법론: FigmaLint(Southleft) + Design Lint + aficat/design-linter 룰셋 기반 7 Lens DS Token Drift 분석

## 헤드라인
- **DS Compliance: {N}%** — Grade: {A-F}
- **Auto-fix 가능**: {N}건 ({M}% of drift) — alias missing → variable 재연결로 해결
- **Critical Drift**: {N}건 (raw value 이탈 + detach)
- critical: {n}건 · warning: {n}건 · info: {n}건
- 검사 노드 수: {total} (COMPLIANT: {c} / DRIFT: {d})

## Per-Lens 점수표

| # | Lens | 점수 | COMPLIANT | DRIFT | Critical | Warning |
|---|------|------|-----------|-------|----------|---------|
| 1 | Color | -/10 | - | - | - | - |
| 2 | Typography | -/10 | - | - | - | - |
| 3 | Spacing | -/10 | - | - | - | - |
| 4 | Border Radius | -/10 | - | - | - | - |
| 5 | Shadow | -/10 | - | - | - | - |
| 6 | Component Instance | -/10 | - | - | - | - |
| 7 | Code Mapping | -/10 (Partial) | - | - | - | - |

## DS Variable Map (수집된 토큰)

| Collection | Variable | Type | Resolved Value |
|------------|----------|------|----------------|
| {collection} | {name} | color/typo/spacing/... | {value} |

## Drift Findings

### {Lens명} — score: {N}
- **severity**: critical | warning | info
- **lens**: Color | Typography | Spacing | Border Radius | Shadow | Component Instance | Code Mapping
- **evidence**: 노드 `{경로/이름}` · 값 `{raw value}` · 존재 토큰 `{variable name}` (또는 "DS 토큰 없음")
- **fix**: `{권장 variable 참조}` 또는 Tailwind `{class}` — {교체 이유}
- **참고**: {FigmaLint rule | Design Lint check | aficat/design-linter rule | 8pt grid | Tailwind 매핑 힌트}

{위반 항목만 나열}

## Auto-fix 후보

| Property | Raw Value | 권장 Variable | 대상 노드 수 | Fix 방법 |
|----------|-----------|--------------|------------|---------|
| fill | {hex} | {variable name} | {n} | replace_all_matching_properties |
| fontSize | {px} | {variable name} | {n} | batch_update / 수동 |
| padding | {px} | {variable name} | {n} | replace_all_matching_properties |

## Top Drift 개선 제안 (critical/warning 3건 이상 시)

### Proposal 1 — {Lens명} drift 해소
- **Drift 위치**: {노드 경로} (lens: {Lens명})
- **현재 값**: `{raw value}`
- **권장 토큰**: `{variable name}` → Tailwind `{class}`
- **영향 범위**: 동일 패턴 {N}개 노드
- **Fix 방법**: {Pencil replace_all / Figma batch update / 수동}
- **노력**: {Low/Medium/High}

### Proposal 2 — ...
### Proposal 3 — ...

## N/A 항목 (정적 분석 한정)
- Code Mapping (7): 실제 코드 파일 열람 없이 Figma 변수명 기반 힌트만 제공 (Partial)
- Shadow (5): flat design 프레임에 shadow 노드 없을 경우 N/A

## 다음 단계 (권장 후속)
- `annotate-design` 스킬로 finding 을 디자인 파일에 시각 코멘트로 부착
- Pencil: `replace_all_matching_properties` 로 alias missing 항목 일괄 교체
- Figma: `figma_batch_update_variables` 로 variable binding 복원
- DS 마이그레이션 완료 후 동일 rubric 재평가 (delta Compliance % 측정)
- FigmaLint / Design Lint 플러그인 연동으로 CI 자동화 구성 검토
```

## 인자

```
/design-ui-token-drift-review <Figma URL | .pen path> [--lens 1,2,3,...] [--strict]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- 옵션 `--lens 1,3,7`: 평가할 lens 번호 명시 (1=Color, 2=Typography, 3=Spacing, 4=Border Radius, 5=Shadow, 6=Component Instance, 7=Code Mapping). 미지정 시 7개 전부.
- 옵션 `--strict`: 8pt grid 배수 외 간격 값을 critical 로 상향
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Figma URL, 전체 lens 평가
```
/design-ui-token-drift-review https://www.figma.com/design/abc123XYZ/EasySeller?node-id=42-1024
```
→ Figma MCP 체크 → `figma_get_variables` + `figma_get_styles` → `figma_get_file_data` deep 트리 → 7 lens drift 분류 → DS Compliance % 산출 → `./design-reviews/design-ui-token-drift-review-product-list-20260518-1430.md` 생성

### 예시 2 — Pencil, Color + Spacing만 점검
```
/design-ui-token-drift-review ~/Desktop/projects/design/easyseller.pen --lens 1,3
```
→ Pencil MCP 체크 → `get_variables` + `search_all_unique_properties` → lens 1(Color)·3(Spacing) 만 평가 → alias missing auto-fix 후보 목록 + replace_all_matching_properties 실행 가능 여부 제시

### 예시 3 — Pencil, strict 모드 (8pt grid 엄격 적용)
```
/design-ui-token-drift-review ~/Documents/myapp.pen --strict
```
→ 8pt grid 배수 외 모든 spacing 을 critical 처리 → DS Compliance 더 엄격하게 산출 → CI merge gate 기준으로 활용

### 예시 4 — Figma, Component Instance + Code Mapping 단독 점검
```
/design-ui-token-drift-review https://www.figma.com/design/abc/Shop?node-id=99-200 --lens 6,7
```
→ detach component 검출 + DS variable ↔ Tailwind class 매핑 힌트만 생성

### 예시 5 — MCP 미연결
```
/design-ui-token-drift-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 가 연결되어 있지 않습니다." 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- lens·token name 은 영어 원어 유지 (Color, Typography, Spacing, Border Radius, Shadow, Component Instance, Code Mapping)
- finding 의 evidence 는 노드 경로·raw 값·존재 토큰명을 구체적으로 명시
- finding 의 fix 는 권장 variable 참조 + Tailwind 클래스 후보를 함께 제시
- finding 헤더 포맷 `### {Lens명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / lens / evidence / fix / 참고 필드 동일 순서 유지 (annotate-design 호환)
- 보고서는 한 프레임당 한 파일

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-token-drift-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 drift finding 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 실제 코드 파일(tsx·css) Tailwind 클래스 grep 기반 검사 — 코드 리뷰 스킬 책임
- UX 레이어 평가 (flow·IA·heuristics) — `design-ux-*-review` 스킬 책임
- 시각 미학·감성 평가 — `design-ui-ixdf-review` 등 책임
- 라이브 사이트 audit / 실측 — gstack `/design-review` 책임
- 자동 수정 실행 — 후보 제안만 (실행은 사용자 확인 후 별도)
- 새 DS 토큰 정의 / 네이밍 컨벤션 설계 — 디자인 시스템 설계 스킬 책임

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인
- **FigmaLint (Southleft)**: https://www.figma.com/community/plugin/1521241390290871981/ · https://southleft.com/insights/design-systems/designing-for-developers-introducing-figmalint/
- **Design Lint**: https://www.figma.com/community/plugin/801195587640428208
- **aficat/design-linter**: https://github.com/aficat/design-linter
- 8pt Grid System: Elliot Dahl — "8-Point Grid" https://spec.fm/specifics/8-pt-grid
- Tailwind CSS spacing scale: https://tailwindcss.com/docs/customizing-spacing
- Tailwind CSS border-radius: https://tailwindcss.com/docs/border-radius
- shadcn/ui DS token 규칙: https://ui.shadcn.com/docs/theming
- Figma Variables API: https://www.figma.com/plugin-docs/api/api-overview/
- 대응 스킬: `design-ui-polish-review` (Visual Consistency 차원 부분 커버) — token drift 전문 감지는 본 스킬 전담
