---
name: annotate-design
description: 디자인 리뷰 마크다운 파일(design-{ux,ui}-{rubric}-review 출력의 개별 리뷰 또는 design-review-all 출력의 집계 .md)을 읽어 Pencil(.pen) 또는 Figma 디자인 파일 옆에 코멘트 패널을 부착하는 스킬. 패널은 severity 3개 컬럼(Critical/HIGH · Warning/MED · Info/LOW)으로 분리되어 있으며, 각 finding 카드는 해당 severity 컬럼에만 배치된다. 집계 .md 입력 시 각 카드 Head 에 출처(source) chip rail (예: `[ui-lawsofux][ceo]`) 을 시각화하여 어떤 리뷰가 같은 finding 을 동시에 지적했는지 한눈에 보여준다. 디자인 노드 위에 직접 번호 마커 핀이나 Figma 네이티브 코멘트는 찍지 않는다(캔버스 옆 패널만 생성). 사용자가 "디자인에 코멘트 패널 달기", "리뷰 결과 디자인에 적용", "annotate-design", "리뷰 .md 시각화", "집계 리뷰 코멘트" 등을 요청할 때 사용.
---

# annotate-design

리뷰 마크다운(findings 구조)을 입력으로 받아 디자인 파일(.pen 또는 Figma) 옆 빈 공간에 코멘트 패널을 부착한다.

**비목표**: 디자인 노드 위 핀처럼 떠 있는 번호 마커 frame, Figma 네이티브 코멘트(`figma_post_comment`) — 캔버스 위에 직접 찍히는 것은 생성하지 않는다.

생성물 2종:

1. **코멘트 패널 / mockup Section** — Pencil: 캔버스 우측 severity 3컬럼 패널(Critical/HIGH · Warning/MED · Info/LOW). Figma: 우측 Section 안 동일 3컬럼 구조. 각 카드는 해당 severity 컬럼에만 배치.
2. **After 예시 mockup** — 각 카드 하단에 fix 적용 후 모습 시각화.

각 카드 Head 에는 finding 번호 배지(시각적 카드 번호)가 포함되지만, 그 번호는 **카드 내 식별용**이지 노드 위 핀이 아니다.

## When to Use

- 사용자가 `design-{ux,ui}-{rubric}-review` 패밀리 (예: `design-ux-lawsofux-review`, `design-ui-polish-review`) 또는 `nielsen-heuristics-audit` 같은 리뷰 스킬이 생성한 마크다운을 들고 와서 "이걸 디자인 파일 옆에 코멘트 패널로 달아줘" 요청
- **`design-review-all` 이 생성한 집계 .md (dedupe + source tag 포함) 를 입력으로 받아 통합 코멘트 패널 부착** (집계 모드)
- 디자이너가 리뷰 결과를 텍스트가 아닌 디자인 캔버스 옆 카드 컬럼에서 보고 싶을 때
- 리뷰 → 시각화 → 실제 수정 워크플로의 중간 단계

## 입력 모드 자동 감지

| 모드 | 감지 조건 | 카드 출력 |
|------|----------|----------|
| **개별 모드** (default) | `## Findings` 헤더 존재 | severity/evidence/fix/link + After mockup |
| **집계 모드** | 파일명 `design-review-all-*` **또는** 본문에 `## 통합 finding 목록` 헤더 존재 | severity/summary + **source tag chip 들** + After mockup |

감지 우선순위: 집계 신호 > 개별 신호. 둘 다 없으면 에러 종료.

## Do Not Use

- 리뷰 자체를 생성해야 할 때 → `design-{ux,ui}-{rubric}-review` (또는 다른 리뷰 스킬) 먼저 실행
- 디자인 노드 위에 직접 마커 핀 / 네이티브 코멘트를 부착해야 할 때 → 이 스킬에서 제거됨. 수동 처리 또는 다른 도구 사용
- 디자인 파일 코드를 직접 수정해야 할 때 → 별도 작업
- 리뷰 마크다운이 아닌 일반 텍스트로 코멘트 달기 → 이 스킬은 구조화된 findings 만 처리

## Prerequisites — MCP 연결 체크

| 출력 타겟 | 허용 MCP prefix (둘 중 하나) | 미연결 시 안내 |
|----------|---------------------|---------------|
| `.pen` 파일 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱 + MCP 연동 활성화 후 재시도." |
| Figma URL | `mcp__claude_ai_Figma__*` (Dev Mode MCP) **또는** `mcp__figma-console__*` (Desktop Bridge) | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 중 하나 활성화 후 재시도." |

체크 방법: ToolSearch 로 두 prefix 모두 조회. 어느 하나라도 결과 있으면 진행. 둘 다 비어 있으면 안내 출력 후 종료.

**Figma 도구 매핑 (양 MCP 동일 기능, 쓰기 도구 한정):**

| 작업 | claude_ai_Figma | figma-console |
|------|----------------|---------------|
| 메타데이터 | `get_metadata` | `figma_get_file_data(verbosity:summary)` |
| Deep tree | `get_design_context` | `figma_get_component_for_development_deep` |
| 스크린샷 | `get_screenshot` | `figma_capture_screenshot` |
| 캔버스 임의 노드 생성 | (없음) | `figma_execute` ⭐ |

→ figma-console 만 캔버스 패널/카드 생성 가능. **`figma_post_comment` 는 사용하지 않음 (제거됨).** claude_ai_Figma 단독이면 읽기 전용 — 종료 안내.

## 인자

```
/annotate-design <리뷰.md 경로> [<디자인 파일 경로 또는 Figma URL>]
```

- **위치 1 (필수)**: 리뷰 마크다운 파일 경로. `design-{ux,ui}-{rubric}-review` 출력 포맷 따라야 함 (아래 파싱 규약 참조)
- **위치 2 (선택)**: 코멘트 패널을 부착할 디자인 파일.
  - 생략 시: 리뷰 마크다운의 `메타 > 입력 소스` 줄에서 자동 추출
  - `figma.com/design/...` URL 또는 `.pen` 경로

## Workflow

### Step 1 — 입력 파싱

1. 리뷰 .md 를 Read tool 로 읽음
2. **모드 감지** (위 표):
   - 집계 신호 (`## 통합 finding 목록` 헤더 또는 파일명 `design-review-all-*`) 발견 시 → **집계 모드**, 아래 1b 분기
   - 아니면 → **개별 모드**, 1a 분기

#### 1a. 개별 모드 파싱

다음 섹션 추출 (헤더 정규식):
- `## 메타` 블록에서 `입력 소스`, `프레임 ID`, `프레임 이름`
- `## 종합 점수` 블록에서 평균/critical/warning/info 개수
- `## Findings` 의 각 `### {법칙명} — score: {N}` 서브섹션 → finding 배열
- 각 finding: severity, evidence, fix, 참고 링크
- `## Top-3 우선순위` 블록 (선택)

#### 1b. 집계 모드 파싱 (design-review-all 출력)

`references/findings-parser.md` 의 "Aggregate Mode" 규약 따름. 요점:

- `## 메타` 에서 `입력 소스`, `프레임`, `원본 finding 수 → dedupe 후 수` 추출
- `## 통합 finding 목록` 안의 `### HIGH (n건)`, `### MID (n건)`, `### LOW (n건)` 섹션 순회
- 각 finding 라인 정규식: `^(\d+)\.\s+\[(HIGH|MID|LOW)\]\[([^\]]+)\]\s+(.+?)\s+((?:\[[^\]]+\])+)\s*$`
  - 그룹: number / severityCode / title / summary / sourcesRaw
- `sourcesRaw` 에서 `\[([^\]]+)\]` 반복 매칭 → source 배열
- severity 역매핑: `HIGH→critical`, `MID→warning`, `LOW→info`
- 개별 모드와 달리 `evidence`/`fix`/`link` 분리 본문 없음 — `summary` 한 줄을 카드 Body 로 사용

3. 디자인 파일 경로 결정:
   - 위치 인자 2 > 메타 `입력 소스` > 에러 출력 후 종료

### Step 2 — MCP 체크 + 디자인 파일 오픈

- `.pen` 경로면 `mcp__pencil__open_document(path=...)` + `get_editor_state(include_schema:true)` → 활성 편집기 확인
- Figma URL 이면:
  1. 우선 figma-console 의 `figma_get_status(probe:true)` 로 데스크탑 연결 확인. 이미 같은 fileKey 연결되어 있으면 navigate 생략 (사용자 거부 가능)
  2. 같지 않으면 `figma_navigate(url)` 시도
  3. 좌표 정보 수집: `figma_get_file_data(verbosity:summary, depth:1, nodeIds:[targetNode])` 로 frame bounds (x/y/width/height) 확보. 패널 Section 위치 계산용
  4. Deep tree 조회는 일반적으로 불필요 (리뷰 .md 가 finding 을 다 포함). 필요 시 `figma_get_component_for_development(depth:4)` 얕은 트리만

### Step 3 — 코멘트 패널 빌드 (Pencil 경로)

`find_empty_space_on_canvas` 로 디자인 프레임 우측에 380×{auto} 영역 확보.

#### Card ID 스킴 (필수)

여러 review session 누적 시 카드 추적 가능하도록 ID 박는다. ID 는 **review-type + timestamp** 기반 자기 설명적 식별자 — 매번 session# 계산 불필요, chip 만 봐도 출처 즉시 파악.

**session-key 계산:**

- `{type-prefix}` = 입력 .md 파일명의 review-type segment 약자
  - `critic-*` → `crit`
  - `lawsofux-*` → `lawsofux`
  - `nielsen-*` → `nielsen`
  - `ui-design-polish-*` → `polish`
  - `ux-audit-*` → `uxaudit`
  - **`design-review-all-*` (집계 모드) → `revall`**
  - 기타 → 첫 segment 그대로 (소문자, 8자 이내)
- `{HHmm}` = 입력 .md 파일명 또는 메타에서 추출한 시간 토큰 (4자리). 없으면 현재 시각 KST.
- `{session-key}` = `{type-prefix}-{HHmm}` (예: `crit-1310`, `lawsofux-1430`, `revall-1605`)
- **동시 충돌 처리**: 같은 캔버스에 `{session-key}` 가 이미 존재 (panel name 검색) → suffix `a/b/c/...` 자동 부여 (`crit-1310a`)

**카드 ID 포맷**: `{session-key}.c{N}` (예: `crit-1310.c5`) — N=1..카드수 (finding 출현 순서)

**마커 ID(`.m{M}`) 는 사용하지 않음** — 노드 위 마커가 제거되었으므로 마커 시퀀스 카운터 자체가 없다.

#### 패널 구조

`batch_design` 으로 다음을 한 번에 생성:

```
commentPanel (frame name:"Comment Panel [{session-key}] {review-slug}",
              x=screen.x+screen.width+80, y=screen.y,
              horizontal, padding:24, gap:0, fill:#FFFBEB, stroke:#FCD34D)
  ├─ panelHeader (frame, vertical, layoutAlign:STRETCH, padding:[0,0,16,0], gap:4)
  │   ├─ commentTitle (text 18/700: "{review-type} 리뷰 코멘트 · 프레임명")
  │   ├─ sourceLine (text 10/500 #64748B: "📄 source: {입력 .md 파일명 풀}")
  │   └─ commentMeta (text 11/500 #64748B:
  │         - 개별 모드: "점수 N/10 · critical C · warning M · info K · session-key: {session-key}"
  │         - 집계 모드: "통합 {unique}건 (원본 {raw}건, 병합률 {pct}%) · HIGH H · MID M · LOW L · session-key: {session-key}")
  │
  └─ columnsRow (frame, horizontal, gap:0, layoutAlign:STRETCH, padding:0)
      ├─ colCritical (frame, vertical, width:380, padding:[0,16,16,16], gap:12,
      │               fill:#FFF5F5, stroke right:1 #FCA5A5)
      │   ├─ colHeader (frame horizontal, gap:6, padding:[8,0], alignItems:center)
      │   │   ├─ colLabel (text 13/700 #B91C1C: "CRITICAL")   ← 집계 모드: "HIGH"
      │   │   └─ colCount (frame padding:[2,8] cornerRadius:999 fill:#FECACA,
      │   │                text 11/700 #B91C1C: "{C건}")
      │   └─ [critical/HIGH finding 카드들 — cN, 아래 카드 구조 참조]
      │
      ├─ colWarning (frame, vertical, width:380, padding:[0,16,16,16], gap:12,
      │              fill:#FFFBEB, stroke right:1 #FCD34D)
      │   ├─ colHeader (frame horizontal, gap:6, padding:[8,0], alignItems:center)
      │   │   ├─ colLabel (text 13/700 #B45309: "WARNING")    ← 집계 모드: "MED"
      │   │   └─ colCount (frame padding:[2,8] cornerRadius:999 fill:#FEF3C7,
      │   │                text 11/700 #B45309: "{M건}")
      │   └─ [warning/MED finding 카드들 — cN]
      │
      └─ colInfo (frame, vertical, width:380, padding:[0,16,16,16], gap:12,
                  fill:#F0F7FF, stroke:none)
          ├─ colHeader (frame horizontal, gap:6, padding:[8,0], alignItems:center)
          │   ├─ colLabel (text 13/700 #1D4ED8: "INFO")       ← 집계 모드: "LOW"
          │   └─ colCount (frame padding:[2,8] cornerRadius:999 fill:#DBEAFE,
          │                text 11/700 #1D4ED8: "{K건}")
          └─ [info/LOW finding 카드들 — cN]

※ 컬럼 간 구분선: colCritical·colWarning 우측 stroke right:1 (Critical=#FCA5A5, Warning=#FCD34D).
   colInfo 는 우측 보더 없음 (패널 끝).
※ N/A severity 카드: 4번째 컬럼 colNA (width:200 fill:#F8FAFC stroke right:1 #E2E8F0,
   헤더 "N/A ({N건})" text #64748B) 를 colInfo 우측에 추가. N/A 건이 0건이면 컬럼 생성 생략.
```

**카드 구조 (각 컬럼 안 cN — 공통)**:

```
cN (frame, vertical, fill:#FFFFFF, cornerRadius:10, padding:14, gap:6,
    stroke left:4 severity-color, layoutAlign:STRETCH)
  ├─ Head (frame, horizontal, gap:8, alignItems:center, layoutWrap:WRAP)
  │   ├─ 번호 배지 (frame 24×24, severity color, cornerRadius:12, 흰색 숫자 text "{N}")
  │   ├─ severity chip 생략 — 컬럼 자체가 severity 구분이므로 카드에 severity 색·칩 중복 표기 안 함
  │   ├─ 점수 text "N/10"  ← 개별 모드만 (집계 모드는 점수 없음, 생략)
  │   └─ 카드 ID chip (frame, padding:[2,6], severity bg, stroke 1 severity color,
  │                    cornerRadius:9, text "{session-key}.c{N}" fontSize:9 weight:600
  │                    fill severity-dark)
  ├─ SourceRail (frame horizontal, gap:4, alignItems:center, padding:[0,2]) — 집계 모드 전용
  │   ├─ rail prefix text 9/600 #64748B: "출처:"
  │   └─ source chip 들 (각 frame padding:[6,2], cornerRadius:6, fill:#EEF2F7,
  │                       stroke 1 #CBD5E1, text 9/700 #475569 "{src}")
  │       severity-tinted variant: HIGH 컬럼 → fill:#FEE2E2 stroke:#FCA5A5 text:#B91C1C
  │                                  MED 컬럼  → fill:#FEF3C7 stroke:#FCD34D text:#B45309
  │                                  LOW 컬럼  → fill:#DBEAFE stroke:#93C5FD text:#1D4ED8
  ├─ Title (text 14/700, finding 항목명)
  ├─ Target (text 11/500 #64748B, "대상: {evidence 요약}") — 개별 모드 전용 (집계 모드는 생략)
  ├─ Body (text 12/400 #334155, 본문, textGrowth fixed-width fill_container, lineHeight 1.4)
  │       - 개별 모드 = fix 텍스트
  │       - 집계 모드 = summary 한 줄 (evidence+fix 통합)
  ├─ Link (text 10/500 #3B82F6 underline, 참고 링크 — 개별 모드만, 집계 모드는 생략)
  ├─ Divider (rectangle width fill_container height 1 fill #E2E8F0)
  ├─ ExLabel (frame horizontal, 번호 배지 18×18 + "After 예시" text 11/700)
  └─ Example mockup (frame padding:10 gap:8 fill:#F8FAFC stroke #E2E8F0) — Body 텍스트로부터 AI 생성
```

Target 줄은 evidence 요약 텍스트만 표기. **마커 list chip / `[{session-key}.m{...}]` 참조는 제거** (마커가 없으므로).

**SourceRail (집계 모드 전용)**: source 배열을 chip rail 로 나열. 각 chip = 어떤 review 스킬이 같은 finding 을 잡았는지 표시. chip 색은 카드가 속한 컬럼의 severity 톤과 일치 (위 표 참조). source 가 1개면 chip 1개, 11개면 11개 모두 나열 (자동 wrap).

번호 배지의 `{N}` 은 finding 전체 순서 (컬럼 간 연속). 노드 위 핀과는 무관 (이 스킬은 그 핀을 만들지 않음).

Severity 색 매핑 (카드 좌측 보더 + 배지):
- `critical / HIGH` → 좌측 보더 #DC2626, 배지 bg #FECACA, 배지 text/severity-dark #B91C1C
- `warning / MED`  → 좌측 보더 #F59E0B, 배지 bg #FEF3C7, 배지 text/severity-dark #B45309
- `info / LOW`     → 좌측 보더 #3B82F6, 배지 bg #DBEAFE, 배지 text/severity-dark #1D4ED8
- 번호 배지 색은 좌측 보더와 동일

### Step 4 — After 예시 mockup 생성 (Pencil 경로)

각 finding 마다 fix 텍스트를 분석해 1개의 작은 **시각 mockup** 을 코멘트 카드 안 ExLabel 다음에 삽입.

**원칙 (Iron Rule)**: 카드는 **무조건 시각 mockup** 을 생성한다. **텍스트 2줄(Before/After 라벨 + 본문) 만의 폴백은 금지**. 항상 최소 1개 이상의 시각 요소(컬러 박스, 칩, 보더, 아이콘, 배지, 진행 바, 미니 차트, 미니 input, 다이어그램 화살표 등)를 포함해야 한다.

mockup 생성 패턴 카탈로그 (`references/mockup-patterns.md` 참조):

- **Fitts's Law / Touch target** → Before/After 비교: 작은 버튼 → padding 보강 후 더 큰 hit area
- **Selective Attention / Pareto / Von Restorff** → KPI 카드 4개 그리드 중 1개만 액센트 보더 + 진한 fill + CTA 버튼
- **Paradox of Active User / Help/Onboarding** → KPI 라벨 옆 ⓘ 아이콘 + 다크 툴팁 박스
- **Aesthetic-Usability / Typography** → Before/After 텍스트 weight + size 비교 박스
- **Cognitive Bias / Goal-Gradient** → progress bar + 양수/음수 칩 + 화살표
- **Cognitive Load / Chart context** → Before 막대만 / After y축 tick + 단위 라벨 + 툴팁
- **Jakob's Law / IA** → 관행 위반 위치 → 표준 위치 비교 (사이드바 항목 + badge)
- **Hick's Law / Sidebar IA** → 긴 메뉴 → 카테고리 분리 + 접힘 indicator
- **Choice Overload / Button system** → 4 variant 그리드 (Primary/Secondary/Tertiary/Icon)
- **Empty/Loading/Error state** → 회색 illustration placeholder + headline + CTA 버튼
- **Primary CTA 부재** → Topbar 우측 mini-mockup: 검색 input + 알림 + 아바타 + **파란 솔리드 버튼** 추가
- **Search scope** → input + scope chip "주문 ▾" + placeholder + ⌘K hint badge
- **Status pill color-only** → Before 색 fill 5종 / After 색 + 텍스트 라벨 + 아이콘 이중 단서
- **Notification badge** → bell icon + red dot count "3"
- **WCAG 대비** → Before 회색 (희미한 텍스트 박스) / After 진한 회색 (선명한 텍스트 박스)
- **Brand placeholder / Token contract** → Before "Acme + Inter + #3B82F6" 박스 / After "{Domain} + Pretendard + $brand" 박스 with code-style 변수 호출
- **도메인 KPI / First-class KPI** → Before 추상 KPI 카드 / After 도메인 워딩 KPI 카드 (예: "광고전환 순이익 -128,400원")
- **Table 효율 컨트롤** → 미니 테이블 헤더 + sort caret + 좌측 checkbox 컬럼 + 하단 페이지네이션 dots
- **Card elevation** → 박스 2개 비교: stroke only vs stroke + subtle shadow
- **Avatar 이니셜** → Before 색 원 only / After "KJ" 텍스트 원
- **Responsive / Sidebar collapsed** → 240w expanded sidebar 미니 + 64w icon-only sidebar 미니 나란히
- **Tabular nums** → Before 들쭉날쭉 숫자 column / After tabular 정렬 column

mockup 크기 가이드: 카드 안에서 width:fill_container (≈ 360px 내부), height fit_content. 내부 요소 폰트 사이즈 8-13px 범위 (mockup 임을 시각적으로 구분). 색은 실제 디자인 톤 (slate + blue) 또는 권장 변경 톤.

**카탈로그에 없는 finding 처리**: 폴백 대신 finding 의 핵심 키워드(컬러/공간/타입/컴포넌트/상태/인터랙션 중 어디에 속하는가) 기준으로 카탈로그 패턴 중 가장 가까운 1개 선택 후 적용. 그래도 매칭 어려우면 Before/After **시각 박스** 2개 비교 (각 박스 안에 색 fill + 작은 라벨, 텍스트 단독 금지). 한 카드라도 텍스트 2줄로만 끝내면 SKILL 위반.

### Step 5 — Figma 경로 (figma-console MCP)

figma-console MCP 가 있으면 Pencil 과 동등하게 코멘트 패널(=Section + 카드들)을 캔버스 옆에 생성. **카드 ID 스킴(`{session-key}.c{N}`)은 Figma 에서도 동일 적용** — review session 추적성을 Pencil 과 동일하게 유지.

**`figma_post_comment` 호출 / 노드 위 마커 frame 생성은 모두 하지 않는다.** 캔버스 위 핀·오버레이 부착은 이 스킬의 비목표.

#### Figma 패널 Section 구조

위치: 대상 frame 의 `x + width + 80`, `y` 부터. 패널 전체 폭 = 3컬럼(각 380px) + 컬럼 간 divider = 약 1180px (N/A 컬럼 있으면 +200px).

**Section name**: `Comment Panel [{session-key}] {frame-slug}` (review-type prefix 가 필요하면 앞에 추가, 예: `Laws of UX — Comment Panel [lawsofux-1400] Dashboard`).

**Section 내부 구조** (Pencil Step 3 과 동일한 3컬럼 레이아웃):

```
Section "Comment Panel [...]"
  └─ panelHeader   (frame HORIZONTAL layoutAlign:STRETCH, padding:[24,24,16,24], gap:12)
  └─ columnsRow    (frame HORIZONTAL layoutAlign:STRETCH, padding:[0,24,24,24], gap:0)
      ├─ colCritical  (width:380, fill:#FFF5F5, stroke right:1 #FCA5A5)
      │   ├─ colHeader  "CRITICAL ({C})"  또는  "HIGH ({C})"
      │   └─ [카드들]
      ├─ colWarning   (width:380, fill:#FFFBEB, stroke right:1 #FCD34D)
      │   ├─ colHeader  "WARNING ({M})"  또는  "MED ({M})"
      │   └─ [카드들]
      └─ colInfo      (width:380, fill:#F0F7FF, stroke:none)
          ├─ colHeader  "INFO ({K})"  또는  "LOW ({K})"
          └─ [카드들]
      (N/A 카드 있으면 colNA width:200 fill:#F8FAFC stroke right:1 #E2E8F0 추가)
```

**각 카드 name**: `Card [{session-key}.c{N}] {title}` (예: `Card [lawsofux-1400.c5] Law of Uniform Connectedness`).

**카드 Head 구조** (Pencil Step 3 의 `cN` Head 와 동일):

- 번호 배지 (severity color, 28×28, 흰색 숫자 `{N}`)
- **severity chip 생략** — 컬럼 헤더가 severity 를 이미 나타내므로 카드 내 중복 표기 안 함
- 점수 text `{score}/10` (개별 모드만)
- **카드 ID chip** `{session-key}.c{N}` (severity bg, stroke 1 severity color, fontSize 9 weight 600)
- **SourceRail** (집계 모드 전용) — `출처: [src1][src2]...` chip rail. 카드가 속한 컬럼 severity 톤 적용:
  - HIGH/CRITICAL 컬럼: fill #FEE2E2 / stroke #FCA5A5 / text #B91C1C
  - MED/WARNING 컬럼: fill #FEF3C7 / stroke #FCD34D / text #B45309
  - LOW/INFO 컬럼: fill #DBEAFE / stroke #93C5FD / text #1D4ED8
- Title (16/700)
- Target (`🎯 {evidence 요약}`) — 개별 모드만 (집계 모드는 생략, summary 가 Body 로 직접)
- Body (개별: fix / 집계: summary 한 줄)
- ExLabel + Example mockup — **Step 4 Iron Rule 동일 적용** (텍스트 2줄 폴백 금지, 항상 시각 요소 1개 이상)
- 참고 링크 (개별 모드만)
- `📄 source: {입력 .md 파일명}` (최하단, 11/500 #64748B)

#### figma_execute 실행 규약 (필수)

이 규약을 지키지 않으면 width 가 0 으로 무너지거나, getNodeById 가 실패하거나, 폰트 로드 누락으로 텍스트가 생성되지 않음.

1. **반드시 `getNodeByIdAsync`** — 현 Figma plugin runtime 이 dynamic-page 모드. `figma.getNodeById` 호출 시 즉시 throw `Cannot call with documentAccess: dynamic-page`.

2. **폰트 사전 로드** — 모든 weight 별 `loadFontAsync` 선행. 텍스트 노드 생성 전 4종 (Regular / Medium / Semi Bold / Bold) 로드.
   ```js
   await figma.loadFontAsync({ family:'Inter', style:'Regular' });
   await figma.loadFontAsync({ family:'Inter', style:'Medium' });
   await figma.loadFontAsync({ family:'Inter', style:'Semi Bold' });
   await figma.loadFontAsync({ family:'Inter', style:'Bold' });
   ```

3. **Auto-Layout 사이징 함정 (필독)** — 가장 자주 잘못되는 부분.
   - `frame.resize(W, H)` 호출 후 `counterAxisSizingMode = 'AUTO'` 를 설정하면 resize 가 **무시되고 content fit 으로 덮어쓰임**.
   - 폭 고정이 필요한 경우 명시적으로:
     - VERTICAL frame: `primaryAxisSizingMode = 'AUTO'` (높이 fit), `counterAxisSizingMode = 'FIXED'` (폭 고정) + `frame.resize(W, 1)`
     - HORIZONTAL frame: `primaryAxisSizingMode = 'FIXED'` (폭 고정), `counterAxisSizingMode = 'AUTO'` (높이 fit) + `frame.resize(W, 1)`
   - 자식이 부모 폭을 채우려면 자식에 `layoutAlign = 'STRETCH'` 또는 자식 자체에 고정 width 명시.

4. **헬퍼 함수 권장 패턴**
   ```js
   function F(name, o = {}) {
     const f = figma.createFrame();
     f.name = name;
     f.layoutMode = o.dir || 'VERTICAL';
     f.itemSpacing = o.gap ?? 8;
     const p = o.pad ?? 12;
     f.paddingTop = p; f.paddingBottom = p; f.paddingLeft = p; f.paddingRight = p;
     f.cornerRadius = o.radius ?? 8;
     f.fills = o.fill ? fill(o.fill) : [];
     if (o.stroke) { f.strokes = fill(o.stroke); f.strokeWeight = o.strokeW ?? 1; }
     if (o.align) f.counterAxisAlignItems = o.align;
     if (o.justify) f.primaryAxisAlignItems = o.justify;
     if (o.w) {
       f.resize(o.w, 1);
       f.primaryAxisSizingMode = o.dir === 'HORIZONTAL' ? 'FIXED' : 'AUTO';
       f.counterAxisSizingMode = o.dir === 'HORIZONTAL' ? 'AUTO' : 'FIXED';
     } else {
       f.primaryAxisSizingMode = 'AUTO';
       f.counterAxisSizingMode = 'AUTO';
     }
     return f;
   }
   ```

5. **Section 사용** — Figma 의 `figma.createSection()` 으로 카드들을 그룹화. Section 은 부모 layout 영향 없이 절대 좌표 사용 가능.
   ```js
   const sec = figma.createSection();
   sec.name = 'Comment Panel [lawsofux-1400]';
   sec.x = baseX; sec.y = baseY;
   sec.resizeWithoutConstraints(cardW + 80, 1000);
   figma.currentPage.appendChild(sec);
   ```
   카드는 `sec.appendChild(card)` 후 `card.x = 40; card.y = curY;` 명시. Section 내부에서는 absolute 좌표 사용.

6. **응답 데이터 반환** — `figma_execute` 의 반환값이 직렬화 불가 (예: figma 객체)이면 result 가 비어 보임. 명시적으로 `return { id: x.id, ... }` 식으로 primitive 만 반환.

7. **검증 루프** — 생성 직후 `figma_capture_screenshot(sectionId)` 로 시각 확인. 카드 width 가 cardW (예: 420) 와 일치하는지 별도 query 로 확인:
   ```js
   const sec = figma.currentPage.children.find(n => n.name.includes('Comment Panel'));
   return sec.children.map(c => c.name + ' ' + c.width + 'x' + c.height);
   ```
   width 가 들쭉날쭉하면 Auto-Layout 함정 (위 #3) 재점검.

#### claude_ai_Figma 만 있는 경우 (읽기 전용 폴백)

`figma_execute` 가 없음. 다음으로 안내:

> "현재 Figma MCP 에 쓰기 도구가 없어 코멘트 패널 부착이 불가능합니다. figma-console MCP (Desktop Bridge) 를 설치하거나 Pencil 경로를 사용하세요. 리뷰 .md 는 그대로 유지됩니다."

종료.

### Step 6 — 검증 + 요약

1. **Pencil**: `get_screenshot(commentPanel id)` 로 패널 확인
2. **Figma**: `figma_capture_screenshot(sectionId, scale:0.5)` + 카드 width 일관성 query
3. 사용자에게 요약:
   - 부착된 finding 개수 (카드 N장)
   - 패널 / Section ID
   - 디자인 파일 경로
   - 알려진 한계 (예: claude_ai_Figma 단독이면 읽기 전용)

### 멀티 프레임 처리

리뷰 마크다운 1개 = 프레임 1개 가정 (lawsofux-review 및 design-review-all 동일 — 한 번에 한 프레임). 여러 프레임을 코멘트하려면 사용자가 각 .md 를 순차 호출.

### 모드 차이 요약

| 항목 | 개별 모드 | 집계 모드 |
|------|----------|----------|
| 입력 .md | `lawsofux-*.md`, `polish-*.md` 등 | `design-review-all-*.md` |
| **패널 컬럼** | **3컬럼: CRITICAL · WARNING · INFO** | **3컬럼: HIGH · MED · LOW** |
| 카드 배치 | 해당 severity 컬럼에만 배치 | 해당 severity 컬럼에만 배치 |
| 카드 내 severity chip | **생략** (컬럼 헤더가 대신함) | **생략** (컬럼 헤더가 대신함) |
| 점수 chip | 있음 | 없음 |
| Target 줄 | evidence 요약 | 생략 |
| Body | fix 본문 | summary 한 줄 (evidence+fix 통합) |
| Link | 참고 URL | 없음 |
| **SourceRail** | **없음** | **있음 — `출처: [src1][src2]`** |
| session-key prefix | `lawsofux`/`crit`/... | `revall` |
| commentMeta | 점수·warning·info 합계 | 통합/원본/병합률·HIGH·MID·LOW 합계 |

## 출력 규약

- 코멘트 패널/mockup 텍스트는 **한국어**
- 법칙명은 원본 .md 의 표기 그대로 (영어 원어 유지)
- mockup 의 라벨/숫자는 fix 텍스트에서 그대로 가져오거나 일반화 ("KPI 1", "₩48.2M" 등)
- 참고 링크는 카드의 Link 필드에 1회

## 파싱 규약 (입력 .md 포맷)

`references/findings-parser.md` 에 정규식 + 토큰 명세 (개별 + 집계 모드).

**개별 모드** 요점:
- `### {법칙명} — score: {N}` 헤더로 finding 시작
- `- **severity**: critical|warning|info`
- `- **evidence**: ...` (백틱 안의 nodeId 패턴이 있더라도 이 스킬은 자연어 요약만 카드에 표기. 노드 매칭/마커는 만들지 않음)
- `- **fix**: ...` (자유 텍스트)
- `- **참고**: https://lawsofux.com/...`

**집계 모드** 요점:
- `## 통합 finding 목록` 헤더 아래 `### HIGH (n건)` / `### MID (n건)` / `### LOW (n건)` 섹션
- 각 라인: `{N}. [{HIGH|MID|LOW}][{title}] {summary} [{src1}][{src2}]...`
- 정규식: `^(\d+)\.\s+\[(HIGH|MID|LOW)\]\[([^\]]+)\]\s+(.+?)\s+((?:\[[^\]]+\])+)\s*$`
- severity 역매핑: `HIGH→critical`, `MID→warning`, `LOW→info`
- `sourcesRaw` 에서 `\[([^\]]+)\]` 반복 매칭 → SourceRail chip 들

## 예시

### 예시 1 — Pencil 자동 라우팅
```
/annotate-design ./design-reviews/lawsofux-dashboard-20260514-1230.md
```
→ .md 의 `입력 소스: ./test.pen` 추출 → Pencil MCP 체크 → test.pen 오픈 → 7개 finding 파싱 → **severity 3컬럼 패널** (CRITICAL·WARNING·INFO) + 카드 7장 각 해당 컬럼 배치 (Head 번호 배지 1..7 포함) → 요약 출력. **노드 위 마커 부착 단계 없음.**

### 예시 2 — 명시적 디자인 파일
```
/annotate-design ./reviews/foo.md ~/Projects/myapp.pen
```
→ 2번째 인자 우선 → myapp.pen 오픈 → 동일 흐름

### 예시 3 — Figma + figma-console MCP
```
/annotate-design ./design-reviews/lawsofux-page-ad-analysis-20260514-1400.md https://www.figma.com/design/abc/MyApp?node-id=2-10969
```
→ figma-console `figma_get_status` → 연결 확인 → frame 2:10969 bounds 확보 → `figma_execute` 1회로 우측 Section + **3컬럼(CRITICAL·WARNING·INFO)** + 11 카드(각 해당 컬럼 배치) + mockup 생성 → 스크린샷 검증 → 요약. **`figma_post_comment` 호출 없음.**

### 예시 4 — claude_ai_Figma 단독 (읽기 전용)
```
/annotate-design ./reviews/foo.md https://figma.com/design/abc/MyApp
```
→ claude_ai_Figma 만 감지 → 쓰기 도구 부재 안내 → 종료 (리뷰 .md 는 그대로)

### 예시 5 — 집계 모드 (design-review-all 출력)
```
/annotate-design ./design-reviews/design-review-all-dashboard-20260518-1605.md
```
→ 파일명 `design-review-all-*` 감지 → 집계 모드 진입 → `## 메타 > 입력 소스` 에서 디자인 파일 자동 추출 → 통합 finding 목록 파싱 (HIGH/MID/LOW 섹션, source tag 배열) → session-key `revall-1605` → **severity 3컬럼 패널 생성**: 좌(HIGH) · 중(MED) · 우(LOW), 각 컬럼 헤더에 건수 표기 (예: "HIGH (5)") → 각 finding 카드는 해당 severity 컬럼에만 배치 → 각 카드 Head 에 **SourceRail chip 들** (예: `출처: [ui-critic][ui-lawsofux][ceo]`) → Body = summary 한 줄 + After mockup → 컬럼 간 구분선: HIGH↔MED = #FCA5A5, MED↔LOW = #FCD34D → 스크린샷 검증 → 요약. 같은 finding 을 잡은 리뷰가 많을수록 chip 수가 많아 시각적으로 "여러 rubric 이 동의한 high-priority 이슈" 가 한눈에 드러남. N/A severity 가 있으면 우측에 4번째 컬럼(LOW 우측) 자동 추가.

## 참고

- finding 파싱 명세: `references/findings-parser.md`
- mockup 패턴 카탈로그: `references/mockup-patterns.md`
- 리뷰 .md 출처: `lawsofux-review` 스킬
