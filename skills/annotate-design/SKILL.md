---
name: annotate-design
description: 디자인 리뷰 마크다운 파일(design-{ux,ui}-{rubric}-review 등의 출력)을 읽어 Pencil(.pen) 또는 Figma 디자인 파일에 직접 코멘트 패널 + 번호 마커 + 각 finding 별 "After 예시" mockup 까지 시각적으로 주석(annotate) 부착하는 스킬. 사용자가 "디자인에 코멘트 달기", "리뷰 결과 디자인에 적용", "annotate-design", "디자인 주석", "리뷰 .md 디자인에 시각화" 등을 요청할 때 사용.
---

# annotate-design

리뷰 마크다운(findings 구조)을 입력으로 받아 디자인 파일(.pen 또는 Figma)에 시각적 코멘트를 직접 부착한다.

생성물 3종:
1. **코멘트 패널/네이티브 코멘트** — Pencil: 캔버스 우측 finding 카드 컬럼. Figma: 노드 좌표에 핀된 네이티브 코멘트 + 우측 Section 안 mockup 카드 컬럼
2. **번호 마커** — 화면 위 해당 노드 위치에 핀처럼 떠 있는 원형 번호 배지 (Pencil 한정. Figma 는 네이티브 코멘트 핀이 마커 역할 대체)
3. **After 예시 mockup** — 각 카드 하단(Pencil) 또는 우측 Section 카드 안(Figma)에 fix 적용 후 모습 시각화

## When to Use

- 사용자가 `design-{ux,ui}-{rubric}-review` 패밀리 (예: `design-ux-lawsofux-review`, `design-ui-polish-review`) 또는 `nielsen-heuristics-audit` 같은 리뷰 스킬이 생성한 마크다운을 들고 와서 "이걸 디자인 파일에 코멘트로 달아줘" 요청
- 디자이너가 리뷰 결과를 텍스트가 아닌 디자인 캔버스 위에서 보고 싶을 때
- 리뷰 → 시각화 → 실제 수정 워크플로의 중간 단계

## Do Not Use

- 리뷰 자체를 생성해야 할 때 → `design-{ux,ui}-{rubric}-review` (또는 다른 리뷰 스킬) 먼저 실행
- 디자인 파일 코드를 직접 수정해야 할 때 → 별도 작업
- 리뷰 마크다운이 아닌 일반 텍스트로 코멘트 달기 → 이 스킬은 구조화된 findings 만 처리

## Prerequisites — MCP 연결 체크

| 출력 타겟 | 허용 MCP prefix (둘 중 하나) | 미연결 시 안내 |
|----------|---------------------|---------------|
| `.pen` 파일 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱 + MCP 연동 활성화 후 재시도." |
| Figma URL | `mcp__claude_ai_Figma__*` (Dev Mode MCP) **또는** `mcp__figma-console__*` (Desktop Bridge) | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 중 하나 활성화 후 재시도." |

체크 방법: ToolSearch 로 두 prefix 모두 조회. 어느 하나라도 결과 있으면 진행. 둘 다 비어 있으면 안내 출력 후 종료.

**Figma 도구 매핑 (양 MCP 동일 기능):**

| 작업 | claude_ai_Figma | figma-console |
|------|----------------|---------------|
| 메타데이터 | `get_metadata` | `figma_get_file_data(verbosity:summary)` |
| Deep tree | `get_design_context` | `figma_get_component_for_development_deep` |
| 스크린샷 | `get_screenshot` | `figma_capture_screenshot` |
| 코멘트 작성 | (없음) | `figma_post_comment` ⭐ |
| 캔버스 임의 노드 생성 | (없음) | `figma_execute` ⭐ |

→ figma-console 이 작성 도구 풀세트. claude_ai_Figma 만 있으면 읽기 전용으로만 동작, 코멘트는 사용자에게 수동 안내.

## 인자

```
/annotate-design <리뷰.md 경로> [<디자인 파일 경로 또는 Figma URL>]
```

- **위치 1 (필수)**: 리뷰 마크다운 파일 경로. `design-{ux,ui}-{rubric}-review` 출력 포맷 따라야 함 (아래 파싱 규약 참조)
- **위치 2 (선택)**: 코멘트를 부착할 디자인 파일.
  - 생략 시: 리뷰 마크다운의 `메타 > 입력 소스` 줄에서 자동 추출
  - `figma.com/design/...` URL 또는 `.pen` 경로

## Workflow

### Step 1 — 입력 파싱

1. 리뷰 .md 를 Read tool 로 읽음
2. 다음 섹션 추출 (헤더 정규식):
   - `## 메타` 블록에서 `입력 소스`, `프레임 ID`, `프레임 이름`
   - `## 종합 점수` 블록에서 평균/critical/warning/info 개수
   - `## Findings` 의 각 `### {법칙명} — score: {N}` 서브섹션 → finding 배열
   - 각 finding: severity, evidence, fix, 참고 링크
   - `## Top-3 우선순위` 블록 (선택)
3. 디자인 파일 경로 결정:
   - 위치 인자 2 > 메타 `입력 소스` > 에러 출력 후 종료

### Step 2 — MCP 체크 + 디자인 파일 오픈

- `.pen` 경로면 `mcp__pencil__open_document(path=...)` + `get_editor_state(include_schema:true)` → 활성 편집기 확인
- Figma URL 이면:
  1. 우선 figma-console 의 `figma_get_status(probe:true)` 로 데스크탑 연결 확인. 이미 같은 fileKey 연결되어 있으면 navigate 생략 (사용자 거부 가능)
  2. 같지 않으면 `figma_navigate(url)` 시도
  3. 좌표 정보 수집: `figma_get_file_data(verbosity:summary, depth:1, nodeIds:[targetNode])` 로 frame bounds (x/y/width/height) 확보
  4. Deep tree 가 필요한 경우 `figma_get_component_for_development_deep(depth:15)` 호출. **응답이 1M chars 초과 가능** — 초과 시 폴백:
     - 스크린샷만으로 평가 진행 (이미 review .md 가 finding 을 다 포함하므로 트리 재파싱 불필요)
     - 또는 `figma_get_component_for_development(depth:4)` 얕은 트리로 축약

### Step 3 — 코멘트 패널 빌드 (Pencil 경로)

`find_empty_space_on_canvas` 로 디자인 프레임 우측에 380×{auto} 영역 확보.

#### Card / Marker ID 스킴 (필수)

여러 review session 누적 시 카드-마커 추적 가능하도록 ID 박는다. ID 는 **review-type + timestamp** 기반 자기 설명적 식별자 — 매번 session# 계산 불필요, chip 만 봐도 출처 즉시 파악.

**session-key 계산:**

- `{type-prefix}` = 입력 .md 파일명의 review-type segment 약자
  - `critic-*` → `crit`
  - `lawsofux-*` → `lawsofux`
  - `nielsen-*` → `nielsen`
  - `ui-design-polish-*` → `polish`
  - `ux-audit-*` → `uxaudit`
  - 기타 → 첫 segment 그대로 (소문자, 8자 이내)
- `{HHmm}` = 입력 .md 파일명 또는 메타에서 추출한 시간 토큰 (4자리). 없으면 현재 시각 KST.
- `{session-key}` = `{type-prefix}-{HHmm}` (예: `crit-1310`, `lawsofux-1430`)
- **동시 충돌 처리**: 같은 캔버스에 `{session-key}` 가 이미 존재 (panel name 검색) → suffix `a/b/c/...` 자동 부여 (`crit-1310a`)

**ID 포맷:**

- **카드 ID** = `{session-key}.c{N}` (예: `crit-1310.c5`) — N=1..카드수
- **마커 ID** = `{session-key}.m{M}` (예: `crit-1310.m1`) — M=1..마커수, finding 순서대로 누적

`batch_design` 으로 다음을 한 번에 생성:

```
commentPanel (frame name:"Comment Panel [{session-key}] {review-slug}", x=screen.x+screen.width+80, y=screen.y, width:380, vertical, padding:24, gap:16, fill:#FFFBEB, stroke:#FCD34D)
  ├─ commentTitle (text 18/700: "{review-type} 리뷰 코멘트 · 프레임명")
  ├─ sourceLine (text 10/500 #64748B: "📄 source: {입력 .md 파일명 풀}")  ← 추적용 풀 파일명
  ├─ commentMeta (text 11/500 #64748B: "점수 N/10 · warning M · info K · session-key: {session-key}")
  └─ 각 finding 마다 cN (frame, fill:#FFFFFF, cornerRadius:10, padding:14, gap:6, stroke left:4 severity-color)
      ├─ Head (frame, horizontal, gap:8, alignItems:center)
      │   ├─ 번호 배지 (frame 24×24, severity color, cornerRadius:12, 흰색 숫자 text "{N}")
      │   ├─ severity chip (frame, padding:[2,8], severity bg, cornerRadius:999, 텍스트 severity 영문 대문자)
      │   ├─ 점수 text "N/10"
      │   ├─ 카드 ID chip (frame, padding:[2,6], severity bg, stroke 1 severity color, cornerRadius:9, text "{session-key}.c{N}" fontSize:9 weight:600 fill severity-dark)
      │   └─ (있을 때만) 마커 list chip (frame, padding:[2,6], severity bg, stroke 1 severity color, cornerRadius:9, text "{session-key}.m{a} · {session-key}.m{b} · ..." fontSize:9 weight:600 fill severity-dark)
      ├─ Title (text 14/700, finding 항목명)
      ├─ Target (text 11/500 #64748B, "대상: {evidence 요약} [{session-key}.m{a}, {session-key}.m{b}, ...]")
      ├─ Body (text 12/400 #334155, fix 텍스트, textGrowth fixed-width fill_container, lineHeight 1.4)
      ├─ Link (text 10/500 #3B82F6 underline, 참고 링크 — 있을 때만)
      ├─ Divider (rectangle width fill_container height 1 fill #E2E8F0)
      ├─ ExLabel (frame horizontal, 번호 배지 18×18 + "After 예시" text 11/700)
      └─ Example mockup (frame padding:10 gap:8 fill:#F8FAFC stroke #E2E8F0) — fix 텍스트로부터 AI 생성
```

마커 ID 참조 list 는 finding 이 evidence 에서 노드를 1개 이상 참조할 때만 표기 (Target 줄 + Head 의 마커 list chip).

Severity 색 매핑:
- `critical` → 좌측 보더 #DC2626, 배지 bg #FECACA, 배지 text/severity-dark #B91C1C
- `warning` → 좌측 보더 #F59E0B, 배지 bg #FEF3C7, 배지 text/severity-dark #B45309
- `info` → 좌측 보더 #3B82F6, 배지 bg #DBEAFE, 배지 text/severity-dark #1D4ED8
- 번호 배지 색은 좌측 보더와 동일

### Step 4 — 번호 마커 부착 (Pencil 경로)

각 finding 의 `evidence` 텍스트에서 노드 ID(괄호 안 백틱 패턴 `(\`nodeId\`)`)를 정규식으로 추출.

`{session-key}` 는 Step 3 에서 계산된 값 그대로 사용 (예: `crit-1310`).

#### 마커 + 라벨 chip 부착

각 finding 마다 마커 시퀀스 카운터를 `M=1` 부터 review session 전체에서 누적 증가.

각 노드에 대해:

1. `snapshot_layout(parentId=대상 노드)` 로 절대 좌표 계산 (부모 체인 누적)
2. `find_empty_space_on_canvas` 로 그 좌표 근처 빈 공간 확보 안 되면 노드 우상단 코너 위에 오버레이
3. **마커** = 대상 노드의 최상위 design frame (예: Dashboard frame) 의 child 로 배치. `layoutPosition: "absolute"` 필수 (부모가 flex layout 일 때 좌표 적용을 위해):
   ```
   frame name:"Marker [{session-key}.m{M}] ({nodeId})"
     x:절대X y:절대Y width:28 height:28
     layoutPosition:"absolute"
     fill: severity color
     cornerRadius:14
     stroke: thickness:2 fill:#FFFFFF
     effect: shadow outer offset(0,2) blur 6 color #00000040
     layout:horizontal justifyContent:center alignItems:center
     └─ text content:"{N}" fontSize:13 fontWeight:700 fill:#FFFFFF
        (N = finding 번호 = 카드 번호. 마커 ID 의 m{M} 과는 다름 — M 은 마커 일련번호)
   ```
4. **라벨 chip** = 마커 우상단 인접 위치에 가로 chip 부착:
   ```
   frame name:"Label [{session-key}.m{M}] ({nodeId})"
     x:marker.x+33 y:marker.y-4 height:18
     width:fit_content padding:[2,6]
     layoutPosition:"absolute"
     fill:#FFFFFF
     stroke: thickness:1 fill:severity color
     cornerRadius:9
     effect: shadow outer offset(0,1) blur 3 color #00000026
     layout:horizontal alignItems:center
     └─ text content:"{session-key}.m{M}" fontSize:9 fontWeight:600 fill:severity-dark color
   ```
   severity-dark: critical=#B91C1C, warning=#B45309, info=#1D4ED8
5. 한 finding 이 evidence 에서 2+ 노드 참조하면 노드마다 마커 + 라벨 chip 1쌍씩 생성. 각각 다른 `M` 부여. 카드 Target 줄 + Head 의 마커 list chip 에 해당 카드의 모든 마커 ID list 표기 (예: `[crit-1310.m1, crit-1310.m2, crit-1310.m3, crit-1310.m4]`).

#### 부모 선택 규칙

마커/라벨을 어디 child 로 둘지 결정:

- **권장**: 대상 노드의 최상위 design frame (Dashboard, Home, Login 등 사용자가 frame 으로 캡처할 영역) 의 child.
  - 장점: `get_screenshot(frameId)` 로 마커 포함 캡처 가능.
  - 주의: 그 frame 이 flex layout (horizontal/vertical) 이면 자식 x/y 가 무시됨 → 모든 마커/라벨에 `layoutPosition: "absolute"` 명시.
- **대안**: document 의 top-level child. design frame 외부에 마커 떠 있음. `get_screenshot(designFrame)` 에는 안 잡힘 — 캔버스 전체 또는 별도 frame 캡처 필요.

기본값은 권장 (design frame child + absolute).

#### 식별 경로 (3중)

한 캔버스에 여러 review session 의 마커가 누적되어도 다음 세 곳에서 식별 가능:

1. **Frame name** (메타데이터): `Marker [{session-key}.m{M}] ({nodeId})`, `Label [{session-key}.m{M}] ({nodeId})`, `Comment Panel [{session-key}] {review-slug}`
2. **라벨 chip 텍스트** (시각, 마커 옆): `{session-key}.m{M}` (예: `crit-1310.m1`)
3. **카드 Head ID chip + 마커 list chip** (시각, 패널 안): `{session-key}.c{N}` + `[{session-key}.m{a}, ...]`

패널 상단의 `sourceLine` 에 풀 .md 파일명까지 명시되어 추적 완결.

### Step 5 — After 예시 mockup 생성 (Pencil 경로)

각 finding 마다 fix 텍스트를 분석해 1개의 작은 mockup 을 코멘트 카드 안 ExLabel 다음에 삽입.

mockup 생성 패턴 (references/mockup-patterns.md 참조):
- **Fitts's Law** → Before/After 비교: 작은 버튼 → padding 보강 후
- **Selective Attention** → KPI 카드 4개 중 1개만 액센트 보더 + CTA 버튼 추가
- **Paradox of Active User** → KPI 라벨에 ⓘ 아이콘 + 다크 툴팁
- **Aesthetic-Usability** → Before/After 텍스트 weight 비교
- **Cognitive Bias** → 양수 칩(굵게 + 화살표) / 음수 칩(밑줄 + 화살표)
- **Cognitive Load** → Before/After 카드 명도 차이
- **Von Restorff** → 다크 사이드바 nav 항목, 활성 항목에 4px 좌측 액센트 바
- **Jakob's Law** → 관행 위반 위치 → 표준 위치 (예: 로고 우→좌)
- **Hick's Law** → 긴 메뉴 → 카테고리/접힘 형태
- **Choice Overload** → N 개 옵션 → 추천 강조 + 나머지 secondary

mockup 크기 가이드: 카드 안에서 width:fill_container (≈ 300px), height fit_content. 내부 요소 폰트 사이즈 8-13px 범위 (mockup 임을 시각적으로 구분).

fix 텍스트가 위 패턴 매핑에 없으면: Before/After 텍스트 2줄로 폴백 (fix 텍스트를 그대로 "After" 라벨 옆에 표기).

### Step 6 — Figma 경로 (figma-console MCP)

figma-console MCP 가 있으면 Pencil 과 동등한 풀세트 가능. **Step 3 의 session-key + ID 스킴(`{session-key}.c{N}`, `{session-key}.m{M}`)을 Figma 에서도 그대로 적용** — 코멘트·마커·카드 추적성을 Pencil 과 동일하게 유지.

#### Figma ID 매핑 (Step 3 와 1:1 대응)

| Pencil 산출물 | Figma 산출물 | name / 본문 포맷 |
|--------------|-------------|-----------------|
| `Comment Panel [{session-key}] {slug}` | Section name | `Laws of UX — After Mockups [{session-key}] {slug}` |
| 카드 `cN` (Head ID chip `{session-key}.c{N}`) | Section 안 카드 frame | name=`Mock [{session-key}.c{N}] {title}`, Head 에 ID chip 동일 |
| 마커 `Marker [{session-key}.m{M}]` (frame name) | `figma_post_comment` 코멘트 | message 본문 첫 줄에 `[{session-key}.m{M} → {session-key}.c{N}]` chip 텍스트 |
| 마커 라벨 chip (시각) | 코멘트 핀 자체가 시각 마커 | (별도 frame 불필요) |

**N** = 카드 번호 (= finding 순번 1..total). **M** = 마커 일련번호 — finding 이 evidence 에서 노드 2+ 참조 시 카드 1개에 마커 다수. 한 카드 = 한 코멘트가 기본이지만 evidence 2+ 노드면 같은 카드(`.c{N}`) 에 대한 코멘트를 노드별로 다중 게시 (각각 다른 `.m{M}`).

**6a. 네이티브 코멘트 핀 (`figma_post_comment`)**

각 finding 1개당 `figma_post_comment` 1회 (evidence 2+ 노드면 노드 수만큼).

```
emoji = critical:🔴 / warning:🟡 / info:🔵
message =
"{emoji} [{session-key}.m{M} → {session-key}.c{N}] {SEVERITY} · {법칙명} ({score}/10)

🎯 대상: {evidence 요약}
❗ 문제: {finding 설명, 1-2줄}
✅ Fix: {fix 텍스트}
🔗 {참고 링크}
📄 source: {입력 .md 파일명}"

node_id = 리뷰 메타의 프레임 ID (예: "2:10969")
x, y    = **node_id 기준 상대 오프셋** (절대 캔버스 좌표 아님). 0..frame.width / 0..frame.height 범위.
          finding evidence 에서 추정한 영역의 frame 내부 좌표 사용.
```

session-key 첫 줄 chip 패턴 `[{session-key}.m{M} → {session-key}.c{N}]` 가 **추적 핵심**:
- `.m{M}` = 코멘트 자체 식별자 (Pencil 마커와 동일 시퀀스)
- `.c{N}` = 어느 mockup 카드와 짝지어지는지
- 사용자가 코멘트 → mockup 또는 mockup → 코멘트 양방향 탐색 가능

좌표 계산 팁:
- 프레임 bounds 미리 확보 후, evidence 텍스트의 키워드(예: "Header", "Footer", "Sidebar", "Filter")를 기준으로 영역 추정
- 헤더 ≈ y 0..80, 콘텐츠 영역 ≈ y 80..(h-100), 푸터/페이지네이션 ≈ y (h-100)..h
- 사이드바 좌측 ≈ x 0..240, 본문 ≈ x 240..(w-100), 우측 액션 ≈ x (w-200)..w

코멘트 핀 자체가 마커 역할 — 별도 마커 frame 생성 불필요.

**6b. After 예시 mockup Section (`figma_execute`)**

Figma 코멘트는 텍스트만 → mockup 은 캔버스 우측에 Section 신규 생성하여 시각화.

위치: 대상 frame 의 `x + width + 80`, `y` 부터 수직 스택.

**Section name**: `Laws of UX — After Mockups [{session-key}] {frame-slug}` (review-type 에 따라 prefix 교체).

**각 카드 name**: `Mock [{session-key}.c{N}] {title}` (예: `Mock [lawsofux-1400.c5] Law of Uniform Connectedness`).

**카드 Head 구조** (Pencil Step 3 의 `cN` Head 와 동일):
- 번호 배지 (severity color, 28×28, 흰색 숫자 `{N}`)
- severity chip (CRITICAL / WARNING / INFO)
- 점수 text `{score}/10`
- **카드 ID chip** `{session-key}.c{N}` (severity bg, stroke 1 severity color, fontSize 9 weight 600)
- (있을 때만) **마커 list chip** `[{session-key}.m{a} · {session-key}.m{b} · ...]` — 코멘트 다수 시
- Title (16/700)
- Target (`🎯 {evidence 요약} [{session-key}.m{a}, ...]`)
- Fix 본문
- ExLabel + Example mockup
- 참고 링크
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
   sec.name = 'Laws of UX — After Mockups [lawsofux-1400]';
   sec.x = baseX; sec.y = baseY;
   sec.resizeWithoutConstraints(cardW + 80, 1000);  // 초기 높이 임의, 마지막에 재조정
   figma.currentPage.appendChild(sec);
   ```
   카드는 `sec.appendChild(card)` 후 `card.x = 40; card.y = curY;` 명시. Section 내부에서는 absolute 좌표 사용.

6. **응답 데이터 반환** — `figma_execute` 의 반환값이 직렬화 불가 (예: figma 객체)이면 result 가 비어 보임. 명시적으로 `return { id: x.id, ... }` 식으로 primitive 만 반환.

7. **검증 루프** — 생성 직후 `figma_capture_screenshot(sectionId)` 로 시각 확인. 카드 width 가 cardW (예: 420) 와 일치하는지 별도 query 로 확인:
   ```js
   const sec = figma.currentPage.children.find(n => n.name.includes('After Mockups'));
   return sec.children.map(c => c.name + ' ' + c.width + 'x' + c.height);
   ```
   width 가 들쭉날쭉하면 Auto-Layout 함정 (위 #3) 재점검.

**6c. claude_ai_Figma 만 있는 경우 (읽기 전용 폴백)**

`figma_post_comment` 와 `figma_execute` 가 없음. 다음으로 안내:

> "현재 Figma MCP 에 쓰기 도구가 없어 코멘트/캔버스 부착이 불가능합니다. figma-console MCP (Desktop Bridge) 를 설치하거나 Pencil 경로를 사용하세요. 리뷰 .md 는 그대로 유지됩니다."

종료.

### Step 7 — 검증 + 요약

1. **Pencil**: `get_screenshot(commentPanel id)` + `get_screenshot(screen id)` 로 패널/마커 확인
2. **Figma**: `figma_capture_screenshot(sectionId, scale:0.5)` + 코멘트 ID 목록 + 카드 width 일관성 query
3. 사용자에게 요약:
   - 부착된 finding 개수 (코멘트 핀 / 카드 / 마커)
   - 패널 / Section ID, 코멘트 ID 첫-끝
   - 디자인 파일 경로
   - 알려진 한계 (예: claude_ai_Figma 단독이면 읽기 전용)

### 멀티 프레임 처리

리뷰 마크다운 1개 = 프레임 1개 가정 (lawsofux-review 출력 규약). 여러 프레임을 코멘트하려면 사용자가 각 .md 를 순차 호출.

## 출력 규약

- 코멘트 패널/마커/mockup 텍스트는 **한국어**
- 법칙명은 원본 .md 의 표기 그대로 (영어 원어 유지)
- mockup 의 라벨/숫자는 fix 텍스트에서 그대로 가져오거나 일반화 ("KPI 1", "₩48.2M" 등)
- lawsofux.com 링크는 카드의 Link 필드에 1회

## 파싱 규약 (입력 .md 포맷)

`references/findings-parser.md` 에 정규식 + 토큰 명세.

요점:
- `### {법칙명} — score: {N}` 헤더로 finding 시작
- `- **severity**: critical|warning|info`
- `- **evidence**: ...` (백틱 안의 nodeId 패턴 `\`[A-Za-z0-9]+\`` 추출 — Figma 경로는 evidence 가 자연어 영역 설명일 수도 있음)
- `- **fix**: ...` (자유 텍스트)
- `- **참고**: https://lawsofux.com/...`

## 예시

### 예시 1 — Pencil 자동 라우팅
```
/annotate-design ./design-reviews/lawsofux-dashboard-20260514-1230.md
```
→ .md 의 `입력 소스: ./test.pen` 추출 → Pencil MCP 체크 → test.pen 오픈 → 7개 finding 파싱 → 패널/마커/mockup 부착 → 요약 출력

### 예시 2 — 명시적 디자인 파일
```
/annotate-design ./reviews/foo.md ~/Projects/myapp.pen
```
→ 2번째 인자 우선 → myapp.pen 오픈 → 동일 흐름

### 예시 3 — Figma + figma-console MCP
```
/annotate-design ./design-reviews/lawsofux-page-ad-analysis-20260514-1400.md https://www.figma.com/design/abc/MyApp?node-id=2-10969
```
→ figma-console `figma_get_status` → 연결 확인 → frame 2:10969 bounds 확보 → finding 11개에 대해 `figma_post_comment` 11회 (severity 이모지 + 라벨 본문, node_id="2:10969", x/y 는 frame 내부 추정 영역) → `figma_execute` 1회로 우측 Section + 11 카드 + mockup 생성 → 스크린샷 검증 → 요약

### 예시 4 — claude_ai_Figma 단독 (읽기 전용)
```
/annotate-design ./reviews/foo.md https://figma.com/design/abc/MyApp
```
→ claude_ai_Figma 만 감지 → 쓰기 도구 부재 안내 → 종료 (리뷰 .md 는 그대로)

## 참고

- finding 파싱 명세: `references/findings-parser.md`
- mockup 패턴 카탈로그: `references/mockup-patterns.md`
- 리뷰 .md 출처: `lawsofux-review` 스킬
