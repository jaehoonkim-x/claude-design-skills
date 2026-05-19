---
name: design-ui-tufte-dataviz-review
review-level: L0 Surface
description: "[L0 Surface] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 Edward Tufte 사상 기반 데이터 시각화 + AG Grid 테이블 전용 렌즈로 정적 분석하여 한국어 마크다운 리뷰 보고서를 생성. stat-front(쿠팡 셀러 통계 플랫폼)의 AG Grid 35+ 페이지 및 차트 컴포넌트와 직접 매칭. Tufte 10 원칙(Data-Ink Ratio·Chartjunk·Lie Factor·Small Multiples·Sparklines·Direct Labeling·Data Density·Comparison·Truncated Y-axis·Color Encoding) + 보조 lens 5(Chart-type Fit·Pre-attentive·Storytelling·Annotation·Axis & Scale) + AG Grid Table 10(Column Ordering·Number Alignment·Conditional Formatting·Density·Sparkline·Sticky/Freeze·Sortable/Filterable·Totals·Zebra·Empty/Loading/Error) = 최대 25항목 평가. chart 타입과 table 타입 자동 분류. Dataviz Health Grade(A-F) + Top-3 Action 출력. 사용자가 \"Tufte 리뷰\", \"dataviz 평가\", \"차트 리뷰\", \"AG Grid 리뷰\", \"테이블 시각화 점검\", \"데이터 시각화 감사\", \"/design-ui-tufte-dataviz-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 데이터 시각화·차트·테이블 리뷰를 요청할 때 사용."
---

# design-ui-tufte-dataviz-review

**Review Level**: L0 Surface — 데이터 시각화 + Table 전용 (chart / AG Grid 이중 분류).

Edward Tufte 사상 기반 데이터 시각화 전용 리뷰 스킬. **stat-front = 쿠팡 셀러 통계 플랫폼**, AG Grid 35+ 페이지 + 차트가 핵심 도메인이므로 기존 11종 UI 리뷰 스킬이 커버하지 못하는 데이터 시각화·표 전용 품질 진단을 담당한다. 리포트만 생성한다 — Figma/Pencil 코멘트 게시는 별도 스킬(`annotate-design`) 책임.

평가 렌즈 = "데이터가 잉크 낭비 없이 정직하게 전달되고 있는가? 독자가 비교·추론·의사결정을 할 수 있는가? AG Grid 테이블은 셀러가 빠르게 스캔·정렬·분석할 수 있는가?"

## 평가 항목

### Lens A. Tufte 10 원칙

| # | 원칙 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 1 | Data-Ink Ratio | 데이터를 전달하는 잉크 비율. 비-데이터 잉크(격자·테두리·장식) 최소화 | Yes |
| 2 | Chartjunk 제거 | gradient·3D·shadow·불필요 격자선·장식 패턴·바이브레이팅 컬러 부재 | Yes |
| 3 | Lie Factor | 시각적 크기 변화 / 실제 데이터 변화 비율. 1.0 = 정직. > 1.05 또는 < 0.95 = 왜곡 | Yes |
| 4 | Small Multiples | 동일 스케일·포맷으로 복수 패널 비교 가능 여부 | Yes |
| 5 | Sparklines | 문맥 내 미니 차트로 추세 전달 (셀 내 포함) | Yes |
| 6 | Direct Labeling | 데이터 포인트 직접 라벨링으로 범례 의존 최소화 | Yes |
| 7 | Data Density | 단위 면적당 데이터 양. 너무 희소하거나 과밀하지 않은가 | Yes |
| 8 | Comparison | 나란히 비교, 동일 스케일, 시각적 비교 구조 지원 | Yes |
| 9 | Truncated Y-axis | Y축 0 기준선 절단 여부. 오해 유발 가능성 평가 | Yes |
| 10 | Color Encoding | 카테고리(질적)·순서(서열)·정량(연속) 스케일 구분 적절성 | Yes |

### Lens B. 보조 원칙 (FT + Few + Knaflic)

| # | 원칙 | 출처 | 평가 기준 | 정적 검증 |
|---|------|------|----------|----------|
| 11 | Chart-type Fit | FT Visual Vocabulary | 데이터 관계(비교·분포·흐름·상관·부분-전체)에 맞는 차트 타입 선택 | Yes |
| 12 | Pre-attentive Attributes | Few | hue·size·position 중 단 1가지로 핵심 인사이트 즉각 전달 | Yes |
| 13 | Storytelling Hierarchy | Knaflic | 1 message per viz. 제목이 인사이트를 진술하는가 (descriptive vs declarative) | Yes |
| 14 | Annotation | Tufte + Few | reference line·callout·threshold·목표선 등 맥락 정보 존재 | Yes |
| 15 | Axis & Scale | NN/g + Few | 축 라벨·단위·눈금·스케일 일관성 + 로그/선형 선택 적절성 | Yes |

### Lens C. AG Grid Table 10 (stat-front 핵심 — table 타입 시만 적용)

| # | 원칙 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| T1 | Column Ordering | 좌=식별자(상품명·ID), 우=측정값(매출·전환율). 인식 흐름 좌→우 | Yes |
| T2 | Number Alignment | 숫자 우정렬, 소수점 수직 정렬, 통화/퍼센트 단위 일관성 | Yes |
| T3 | Conditional Formatting | 음수 빨강·양수 초록·임계값 강조. 방향성 색상 인코딩 | Yes |
| T4 | Density | row height 적절성. 정보 밀도 vs 가독성 균형 (≤36px dense, ≤48px comfortable) | Yes |
| T5 | Sparkline in Cell | 셀 내 추세 스파크라인 존재 여부 (stat-front 핵심 패턴) | Yes |
| T6 | Sticky / Freeze | 헤더 고정·식별 컬럼 freeze. 스크롤 시 맥락 유지 | Yes |
| T7 | Sortable / Filterable | 정렬·필터 UI 신호 존재 여부 | Yes |
| T8 | Totals / Subtotals | footer 합계·소계 행 존재 여부 (AG Grid pinnedBottomRowData) | Yes |
| T9 | Zebra Striping | 교번 행 색상으로 시선 추적 지원 | Yes |
| T10 | Empty / Loading / Error State | 빈 데이터·로딩·에러 상태 디자인 존재 여부 | Partial |

> AG Grid Table 10 은 Classifier 가 **TABLE** 로 분류한 경우에만 적용. **CHART** 분류 시 T1-T10 생략.

## When to Use

- 데이터 시각화(차트·그래프·KPI 카드), AG Grid 테이블, 대시보드 프레임을 리뷰할 때
- stat-front 셀러 통계 페이지(매출·노출·전환·재고 등)의 Figma URL 또는 .pen 파일을 받고 Tufte 원칙 기반 진단이 필요할 때
- AG Grid 35+ 페이지의 컬럼 설계·숫자 정렬·조건부 서식 품질을 점검할 때
- "Data-Ink Ratio가 낮다", "Chartjunk가 너무 많다", "Y축 절단 문제"를 진단할 때

## Do Not Use

- 일반 UI/UX 레이어 평가 (감성·브랜드·폼 UX·네비게이션) → `design-ui-ixdf-review` / `design-ux-nielsen-review`
- 인터랙션 흐름·flow 구조 → `design-ux-flow-review`
- 접근성 평가 → `design-ui-wcag-review`
- 이커머스 UI → `design-ui-ecommerce-review`
- 디자인 파일 코멘트 직접 게시 → `annotate-design`
- 라이브 사이트 audit / 실측 → gstack `/design-review`
- 데이터가 없는 순수 인터페이스 프레임 (비어있는 레이아웃, 온보딩 화면)

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
- `--lens A,B,C`: 사용할 lens 명시 (A=Tufte 10, B=보조 5, C=AG Grid Table 10). 미지정 시 Classifier 기반 자동 라우팅.

### Step 2 — MCP 사전 체크

Prerequisites 표 기준으로 ToolSearch 실행. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 로 프레임 구조 파악
   - nodeId 미지정 시 현재 선택 프레임 사용. 멀티 프레임 자동 감지
2. 각 frame 에 대해:
   - `mcp__claude_ai_Figma__get_design_context(fileKey, nodeId=frame.id)` 로 deep 트리 + 노드 속성 수집
   - `mcp__claude_ai_Figma__get_screenshot(fileKey, nodeId=frame.id)` 로 시각 참고 이미지 1장 확보
   - figma-console 연결 시 `mcp__figma-console__figma_get_file_data` 로 보완 가능

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 현재 선택 노드 식별 → 멀티 프레임 자동 감지
   - 선택이 비어 있으면: "Pencil 편집기에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id])` 로 deep 노드 트리 수집
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(node_id=frame_id)` 로 이미지 1장 확보
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property=...)` 로 컬러·폰트·사이즈 팔레트 추출

### Step 4 — Classifier (chart 타입 또는 table 타입 자동 분류)

수집된 프레임 스크린샷 + 노드 트리를 분석하여 분류:

**CHART** 분류 기준 (하나라도 해당):
- SVG path / `<path>` 노드 + 데이터 바인딩 힌트 존재 (bar·line·area·pie·scatter·funnel)
- 컴포넌트 이름에 `Chart`, `Graph`, `KPI`, `Trend`, `Spark` 패턴
- X/Y축 라벨 + 눈금선 조합 노드
- 파이·도넛 모양의 원형 세그먼트 그룹

**TABLE** 분류 기준 (하나라도 해당):
- 그리드 행/열 반복 구조 (`Row`, `Cell`, `ag-row`, `Column` 노드 패턴)
- 헤더 행 + 다수의 데이터 행 (3행+) 반복
- 컴포넌트 이름에 `Table`, `Grid`, `AG`, `DataGrid` 패턴
- 숫자/텍스트 셀 격자 구조

**DASHBOARD** (chart + table 혼합):
- CHART와 TABLE 기준 모두 탐지 시 → DASHBOARD 로 분류 → Lens A + B + C 모두 적용

**UNKNOWN**:
- 분류 불가 → "이 프레임에서 차트 또는 테이블 구조를 감지하지 못했습니다. 데이터 시각화 컴포넌트가 포함된 프레임을 선택해주세요." 출력 후 종료

분류 결과 + 추정 도메인 (예: "쿠팡 셀러 매출 대시보드", "상품별 전환율 테이블") 을 보고서 메타에 기록.

**lens 자동 라우팅:**

| 분류 | Lens A (Tufte 10) | Lens B (보조 5) | Lens C (Table 10) | 적용 항목 |
|------|:-----------------:|:---------------:|:-----------------:|:--------:|
| CHART | ✓ | ✓ | — | 15 |
| TABLE | ✓ (1·2·6·7·9·10) | ✓ (12·14·15) | ✓ | 19 |
| DASHBOARD | ✓ | ✓ | ✓ | 25 |

수동 override: `--lens A,B,C` (콤마 구분).

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 1장 본 직후, 분석 시작 전에 **첫 반응**을 1인칭으로 작성:

```
- 이 시각화가 전달하려는 핵심 데이터: [한 문장]
- 첫눈에 무엇이 보이는가: [2-3 단어]
- 내 시선이 가장 먼저 가는 3개: [1], [2], [3]
- 가장 큰 정직성/왜곡 리스크: [한 문장]
- 한 단어 요약: [단어]
- 인상 메모: [dataviz 품질 관점에서 구체적 긍정/부정]
```

진단가는 헤지하지 않는다.

### Step 6 — Inferred Data Display Inventory (Phase 2)

수집된 노드 트리에서 데이터 시각화 관련 항목 추출:

**CHART 타입:**
- **차트 종류**: 감지된 차트 타입 목록 (bar / line / area / pie / scatter / funnel / …)
- **Axes**: X축 라벨·단위·범위 / Y축 라벨·단위·기준선 / 0 포함 여부
- **Legend**: 범례 위치·항목 수·직접 라벨 존재 여부
- **Colors**: 사용 컬러 팔레트 + 카테고리/순서/정량 구분 여부
- **Annotation**: reference line·callout·threshold 존재 여부
- **Sparklines**: 셀 또는 헤더 내 미니 차트 존재 여부
- **Chartjunk**: gradient·3D·shadow·장식 패턴 감지 결과

**TABLE 타입 (추가):**
- **Columns**: 총 컬럼 수 + 식별자 컬럼 위치 + 측정값 컬럼 목록
- **Number formatting**: 통화·퍼센트·소수점 자릿수 일관성
- **Conditional formatting**: 색상 강조 규칙 감지 결과
- **Row count (추정)**: 화면에 표시된 행 수 + 페이지네이션 신호
- **States**: 빈 상태·로딩·에러 디자인 존재 여부

### Step 7 — Tufte 10 + 보조 Lens 5 평가 (Phase 3)

각 항목마다 0-10 점수. 정적 검증 불가능한 항목은 `N/A` + 사유. finding 1개:
**severity** (critical / warning / info) · **lens** (A Tufte / B 보조 / C Table) · **evidence** (노드 경로/이름/수치) · **fix** (구체 액션) · **참고** (Tufte/Few/Knaflic/FT 출처).

**점수 기준:**
- 10 — exemplary, Tufte 기준 best-in-class
- 8-9 — solid, 사소한 polish 만
- 6-7 — 기능적이나 개선 여지
- 4-5 — 데이터 왜곡 또는 인지 비용 상승
- 0-3 — 데이터를 적극적으로 오해하게 만듦
- N/A — 정적 분석으로 검증 불가 (동적 데이터·인터랙션 필요)

**Severity 가이드:**
- critical: Lie Factor 위반·Y축 절단 오해·Chartjunk 심각 (-3 ~ -4)
- warning: 범례 과의존·Data Density 극단 (-1 ~ -2)
- info: 개선 제안 (점수 영향 X)

**항목별 심층 기준:**

**Data-Ink Ratio (1):**
- 데이터 잉크 = 지우면 데이터 손실이 생기는 잉크
- 비-데이터 잉크: 두꺼운 테두리·배경 색상·불필요 격자선·3D 면·그림자
- 목표: 비-데이터 잉크 최소화 → ratio 최대화

**Chartjunk (2):**
- gradient fill on bars/areas (Tufte: "데이터 잉크를 낭비하는 장식")
- 3D perspective (파이/도넛/막대 3D)
- 배경 그림자·글로우
- moiré/vibrating 패턴
- 불필요한 격자선 (major + minor grid lines 모두)

**Lie Factor (3):**
- Lie Factor = (시각적 효과 크기) / (데이터 크기)
- 정적 분석: Y축 기준선 절단 + 비선형 스케일 사용 여부로 추정
- 면적·부피 오용 (1D 데이터에 2D/3D 도형 사용)

**Truncated Y-axis (9):**
- Y축 0 기준선 생략 시 변화 폭 과장
- 예외: 값 범위가 0과 멀리 떨어진 경우 (예: 주가 지수) → 절단 정당성 명시 필요

**Color Encoding (10):**
- 카테고리: 구분 가능한 최대 7-8색 (Few의 색상 팔레트)
- 순서: Sequential (단일 hue 밝기 변화)
- 정량: Diverging (중간값 기준 양방향)
- 적색-녹색 동시 사용 시 색맹 접근성 경고

**Chart-type Fit (11):**
- FT Visual Vocabulary 9 관계 유형: Comparison·Deviation·Ranking·Distribution·Flow·Magnitude·Part-to-whole·Spatial·Correlation
- 잘못된 매핑 예: 시간 데이터에 파이차트 / 연속 데이터에 bar gap

### Step 8 — AG Grid Table 10 평가 (Phase 4) — TABLE / DASHBOARD 타입만

T1-T10 각 항목 0-10 점수. finding 포맷 동일. stat-front 도메인 특화 기준 적용:

**T2 Number Alignment 상세:**
- 통화(₩): 우정렬 + 천 단위 콤마
- 퍼센트(%): 소수점 1자리 통일
- 음수: 부호(-) 또는 괄호 () 중 일관성

**T3 Conditional Formatting 상세:**
- 음수 = 빨강(#D92D20 계열), 양수 = 초록(#039855 계열)
- stat-front 패턴: `ConversionRevenue`, `ClickThrough` 등 방향성 있는 KPI

**T5 Sparkline in Cell 상세:**
- AG Grid `agSparklineCellRenderer` 패턴
- 주간/월간 추세를 셀 내 line/bar sparkline 으로 표현
- stat-front 핵심 차별화 기능

**T10 Empty/Loading/Error State 상세:**
- 빈 상태: "데이터가 없습니다" 메시지 + 안내 액션
- 로딩: skeleton row overlay 또는 spinner
- 에러: 에러 메시지 + retry CTA

### Step 9 — Dataviz Health Grade 산출

**렌즈별 평균:**
- Lens A (Tufte 10) 평균 → 0-10
- Lens B (보조 5) 평균 → 0-10
- Lens C (Table 10) 평균 → 0-10 (적용 시)

**전체 Dataviz Health Grade** = 적용 항목 전체 평균 (가중치: Lie Factor·Truncated Y-axis·T3 는 1.5x):
- 9.0-10 = **A** (Excellent — Tufte 기준 exemplary)
- 7.5-8.9 = **B** (Good — minor polish)
- 6.0-7.4 = **C** (Acceptable — dataviz 개선 필요)
- 4.0-5.9 = **D** (Poor — 데이터 왜곡 위험)
- 0-3.9  = **F** (Critical — 독자 오해 유발 수준)

**추가 헤드라인:**
- **Integrity Flag**: Lie Factor 또는 Truncated Y-axis critical 위반 시 ⚠️ 별도 경고
- **Chartjunk Score**: Tufte 2번 단독 점수 별도 표시
- **Table Scanability** (TABLE 분류 시): T1+T2+T3 평균 = "셀러 스캔 효율" 한 줄 평가

### Step 10 — 보고서 작성 (각 프레임마다 한 파일)

**파일 경로**: `./design-reviews/design-ui-tufte-dataviz-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name kebab-case + 소문자. 한글이면 음역 또는 nodeId 끝 8자
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

### Step 11 — 사용자에게 결과 요약 출력

- 생성된 보고서 파일 경로(들) 나열
- 각 프레임의 Dataviz Health Grade + 평균 점수 + critical/warning 개수 한 줄 요약
- Integrity Flag 해당 시 별도 강조
- 데이터 왜곡 위험이 있으면 우선 수정 촉구

### Step 12 — Top-3 Action

finding 이 3건 이상이면 data integrity 영향순으로 상위 3개를 픽업하여 액션 카드 작성:

선정 우선순위:
1. Lie Factor 또는 Truncated Y-axis critical (데이터 정직성 최우선)
2. Chartjunk critical (Data-Ink Ratio 심각)
3. T3 Conditional Formatting 부재 (AG Grid 판독성)
4. Color Encoding 오류
5. 나머지 warning 순

각 카드 포맷:
- **현재 문제** (lens·항목번호 + evidence)
- **데이터 신뢰도 영향** (독자 오해 시나리오)
- **제안 솔루션** (구체 컴포넌트/디자인 토큰/AG Grid 속성)
- **기대 점수 변화** (항목 N → N')
- **노력 규모** (Low/Medium/High)

## 보고서 구조 (한국어)

```markdown
# Tufte Dataviz Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 시각화 타입: {CHART | TABLE | DASHBOARD}
- 추정 도메인: {예: 쿠팡 셀러 매출 대시보드 / 상품별 전환율 AG Grid}
- 적용 lens: {A Tufte 10 / B 보조 5 / C AG Grid Table 10}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 "MCP get_screenshot 결과 인라인"}
- 방법론: Tufte VDQI(1983) + Envisioning Information(1990) + Few "Now You See It" + Knaflic "Storytelling with Data" + FT Visual Vocabulary

## 헤드라인
- **Dataviz Health Grade: {A-F}** ({평균}/10)
- **Per-Lens Sub-Grade**:
  - Tufte 10 (A): {n}/10
  - 보조 Lens (B): {n}/10
  - AG Grid Table 10 (C): {n}/10 또는 N/A
- **Integrity Flag**: {⚠️ Lie Factor / Truncated Y-axis 위반 시 표시 | ✅ 이상 없음}
- **Chartjunk Score**: {n}/10
- **Table Scanability** (TABLE 시): {한 줄 평가}
- 적용 항목: {applied}/25 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression
- 이 시각화가 전달하려는 핵심 데이터: {...}
- 첫눈에 무엇이 보이는가: {...}
- 내 시선이 가장 먼저 가는 3개: {1}, {2}, {3}
- 가장 큰 정직성/왜곡 리스크: {...}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Inferred Data Display Inventory

### CHART 인벤토리 (chart 타입 시)
- **차트 종류**: {감지된 타입 목록}
- **Axes**: X={라벨·단위·범위} / Y={라벨·단위·0 포함 여부}
- **Legend**: {위치·항목 수·직접 라벨 여부}
- **Colors**: {팔레트·카테고리/순서/정량 구분}
- **Annotation**: {reference line·callout·threshold 존재 여부}
- **Sparklines**: {존재 여부}
- **Chartjunk**: {gradient·3D·shadow 감지 결과}

### TABLE 인벤토리 (table 타입 추가)
- **Columns**: {총 수·식별자 위치·측정값 목록}
- **Number formatting**: {통화·퍼센트·소수점 일관성}
- **Conditional formatting**: {색상 강조 규칙}
- **Row count**: {추정 행 수·페이지네이션 신호}
- **States**: {빈 상태·로딩·에러 디자인 존재 여부}

## 점수표

### Lens A. Tufte 10

| # | 원칙 | 점수 | 비고 |
|---|------|------|------|
| 1 | Data-Ink Ratio | - | - |
| 2 | Chartjunk 제거 | - | - |
| 3 | Lie Factor | - | - |
| 4 | Small Multiples | - | - |
| 5 | Sparklines | - | - |
| 6 | Direct Labeling | - | - |
| 7 | Data Density | - | - |
| 8 | Comparison | - | - |
| 9 | Truncated Y-axis | - | - |
| 10 | Color Encoding | - | - |

### Lens B. 보조 (FT + Few + Knaflic)

| # | 원칙 | 점수 | 비고 |
|---|------|------|------|
| 11 | Chart-type Fit | - | - |
| 12 | Pre-attentive Attributes | - | - |
| 13 | Storytelling Hierarchy | - | - |
| 14 | Annotation | - | - |
| 15 | Axis & Scale | - | - |

### Lens C. AG Grid Table 10 (TABLE / DASHBOARD 타입 시)

| # | 원칙 | 점수 | 비고 |
|---|------|------|------|
| T1 | Column Ordering | - | - |
| T2 | Number Alignment | - | - |
| T3 | Conditional Formatting | - | - |
| T4 | Density | - | - |
| T5 | Sparkline in Cell | - | - |
| T6 | Sticky / Freeze | - | - |
| T7 | Sortable / Filterable | - | - |
| T8 | Totals / Subtotals | - | - |
| T9 | Zebra Striping | - | - |
| T10 | Empty / Loading / Error State | - | - |

## Findings

### {원칙명} — score: {N}
- **severity**: critical | warning | info
- **lens**: A Tufte | B 보조 | C AG Grid Table
- **evidence**: {노드 경로/이름/수치}
- **fix**: {구체 액션}
- **참고**: {Tufte VDQI p.{n} | Few "Now You See It" Ch.{n} | Knaflic Ch.{n} | FT Visual Vocabulary | edwardtufte.com}

{위반/개선점이 있는 항목만 나열}

## Top-3 Action

### Action 1 — {원칙명}
- **현재 문제**: {lens·항목번호 + evidence}
- **데이터 신뢰도 영향**: {독자 오해 시나리오}
- **제안 솔루션**: {구체 컴포넌트/디자인 토큰/AG Grid 속성}
- **기대 점수 변화**: {항목} {N} → {N'}
- **노력**: {Low/Medium/High}

### Action 2 — ...
### Action 3 — ...

## Integrity Flag 상세 (위반 시만)

- Lie Factor 위반: {위반 시각화 노드 경로} · Lie Factor ≈ {추정값} · 수정: {Y축 기준선 복원/스케일 교정}
- Truncated Y-axis: {노드 경로} · 절단 기준값 {n} · 수정: {0 기준선 복원 또는 절단 사유 명시}

## N/A 항목 (정적 분석 한정)
- Small Multiples (4): 복수 패널 컨텍스트가 단일 프레임에 없으면 N/A
- Sparklines (5): 셀 내 동적 데이터 렌더링은 정적 분석 불가 (존재 여부만 평가)
- T10 Empty/Loading/Error (10): 실제 빈 데이터·로딩 트리거는 정적 분석 불가 (상태 디자인 존재 여부만)

## 다음 단계 (권장 후속)
- `annotate-design` 스킬로 finding 을 Figma/Pencil 파일에 시각 마커로 부착
- AG Grid 속성 구현: `cellClassRules`, `agSparklineCellRenderer`, `pinnedBottomRowData`
- Lie Factor / Truncated Y-axis 수정 후 동일 rubric 재평가 (delta 측정)
- chart 컴포넌트 교체 시 FT Visual Vocabulary 9 관계 유형 재매핑
```

## 인자

```
/design-ui-tufte-dataviz-review <Figma URL | .pen path> [--lens A,B,C]
```

- 위치 인자 1개만 필수
- 멀티 프레임은 Figma/Pencil 의 **현재 선택** 으로 자동 감지
- `--lens A,B,C`: 적용 lens 수동 지정 (A=Tufte 10, B=보조 5, C=AG Grid Table 10). 미지정 시 Classifier 자동 라우팅.

## 예시

### 예시 1 — Figma URL (매출 차트 프레임)
```
/design-ui-tufte-dataviz-review https://www.figma.com/design/abc123/EasySeller?node-id=42-1024
```
→ Figma MCP 체크 → `get_metadata` + `get_design_context` + `get_screenshot` → Classifier: CHART (line chart + bar chart 감지) → Lens A+B 15항목 평가 → Integrity Flag 체크 → `./design-reviews/design-ui-tufte-dataviz-review-sales-chart-20260518-1130.md` 생성

### 예시 2 — Pencil, AG Grid 테이블 프레임
```
/design-ui-tufte-dataviz-review ~/Documents/stat-front.pen
```
→ Pencil MCP 체크 → `open_document` → `get_editor_state` 로 선택 프레임 감지 → Classifier: TABLE (ag-row 패턴 감지) → Lens A(6항목)+B(3항목)+C(Table 10) = 19항목 평가 → Table Scanability 산출 → 보고서 생성

### 예시 3 — DASHBOARD (차트 + 테이블 혼합)
```
/design-ui-tufte-dataviz-review https://www.figma.com/design/abc/EasySeller?node-id=99-2048
```
→ Classifier: DASHBOARD (KPI 차트 4개 + AG Grid 1개 감지) → Lens A+B+C 25항목 전부 평가 → Grade + Integrity Flag + Table Scanability 모두 출력

### 예시 4 — 수동 lens override
```
/design-ui-tufte-dataviz-review ~/Documents/stat-front.pen --lens A,C
```
→ Tufte 10 + AG Grid Table 10 만 평가. 보조 Lens B 생략.

### 예시 5 — MCP 미연결
```
/design-ui-tufte-dataviz-review ~/Documents/stat-front.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 가 연결되어 있지 않습니다." 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- 원칙명·렌즈 용어는 영어 원어 유지 (Data-Ink Ratio, Chartjunk, Lie Factor, Small Multiples, Sparklines, Direct Labeling, Data Density, Comparison, Truncated Y-axis, Color Encoding, Pre-attentive Attributes, Storytelling Hierarchy, Annotation, Chart-type Fit, Axis & Scale)
- finding 의 evidence/fix 는 구체적 노드명·수치·액션 명시
- 보고서는 한 프레임당 한 파일
- finding 헤더 포맷 `### {원칙명} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / lens / evidence / fix / 참고 필드 동일 순서 유지

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 그대로 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ui-tufte-dataviz-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## Non-Goals

- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 일반 UI/UX 레이어 평가 — `design-ui-*-review` / `design-ux-*-review` 책임
- 라이브 사이트 audit / 인터랙션 실측 — gstack `/design-review` 책임
- AG Grid 코드 구현 — 리뷰 + 제안만
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 비-데이터 프레임 평가 (온보딩·마케팅·폼 등)

## 참고 자료

- **Tufte VDQI**: Edward Tufte "The Visual Display of Quantitative Information" (1983) — Data-Ink Ratio, Chartjunk, Lie Factor, Small Multiples, Data Density
- **Tufte EI**: Edward Tufte "Envisioning Information" (1990) — Color, Layering, Separation
- **edwardtufte.com**: https://www.edwardtufte.com/
- **Tufte Sparklines**: https://www.edwardtufte.com/tufte/sparkline
- **Stephen Few**: "Now You See It" (2009) — Pre-attentive Attributes, Color for Categorical/Sequential/Diverging
- **Cole Nussbaumer Knaflic**: "Storytelling with Data" — https://www.storytellingwithdata.com/ — 1 message, declarative title, annotation
- **FT Visual Vocabulary**: https://ft-interactive.github.io/visual-vocabulary/ — 9 chart-type relationship categories
- **Datawrapper Academy**: https://academy.datawrapper.de/ — practical dataviz checklist
- **AG Grid Docs**: https://www.ag-grid.com/react-data-grid/ — `cellClassRules`, `agSparklineCellRenderer`, `pinnedBottomRowData`
- 짝 스킬: `annotate-design` (finding 시각화) · `design-ui-wcag-review` (색맹 접근성) · `design-ui-ixdf-review` (일반 UI 레이어)
