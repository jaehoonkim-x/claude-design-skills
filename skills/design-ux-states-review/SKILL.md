---
name: design-ux-states-review
review-level: L1 Skeleton
description: "[L1 Skeleton] Figma URL 또는 Pencil(.pen) 파일의 선택된 단일 프레임(또는 프레임 세트)을 non-happy path state 전용으로 정적 분석하여 한국어 마크다운 리뷰 보고서를 생성. 7 state × 3 sub = 21 항목 rubric — Loading(3) + Empty(3) + Error(3) + Success(3) + Offline(3) + Permission(3) + Stale(3). State Coverage Score(covered/21) + 7 state 별 점수 + Top-3 Missing State 헤드라인. design-ux-flow-review Lens C(7항목)의 단일 프레임 깊이 확장 전용 스킬. 사용자가 \"state 리뷰\", \"상태 리뷰\", \"빈 상태 점검\", \"에러 상태 검토\", \"로딩 상태 평가\", \"non-happy path 리뷰\", \"edge state audit\", \"states review\", \"/design-ux-states-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 L1 Skeleton 단위 state 전용 UX 리뷰를 요청할 때 사용."
---

# design-ux-states-review

**Review Level**: L1 Skeleton — non-happy path state 전용 단일 프레임 깊이 분석.

design-ux-flow-review Lens C(Edge State 7항목)가 flow 시퀀스 수준에서만 훑는 것을 단일 프레임(또는 컴포넌트 세트) 레벨로 21항목까지 깊게 확장한다. Loading·Empty·Error·Success·Offline·Permission·Stale 7가지 state 각 3 sub-항목으로 단일 화면의 state completeness 를 체계적으로 평가한다.

평가 렌즈 = "이 화면은 happy path 외 7가지 state 를 얼마나 완전하게 설계했는가? 빠진 state 는 어디이며 사용자 경험에 어떤 구멍을 만드는가?"

## 추상화 위치

Garrett 5 Planes 의 **Skeleton** / Spool 5 Resolutions 의 **Screen** / Miller Service Levels 의 **UX** / NN/g Granularity 의 **Component + Screen State**. design-ux-flow-review(L2 Structure) 아래, design-ux-nielsen-review(L1 휴리스틱 종합) 와 동일 추상화 단계이나 state coverage 전용.

## 21 항목 Rubric

### State 1. Loading (3항목)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 1.1 | Skeleton | placeholder shape 이 실제 콘텐츠 구조와 유사한가 (spinner 단순 대비 skeleton 설계) | Yes |
| 1.2 | Progress | determinate %(progress bar) 또는 indeterminate(pulsing) 표시 존재 | Yes |
| 1.3 | Cancellable | 10s+ 작업에 취소 가능 액션 제공 | Yes |

**채점 기준 (1.1 Skeleton):**
- 10 — 콘텐츠 레이아웃을 정확히 반영한 skeleton (텍스트 줄·카드·이미지 영역 형태)
- 8-9 — 대략 일치하는 skeleton, 세부 형태 minor mismatch
- 6-7 — 단순 spinner 존재하나 skeleton 없음
- 4-5 — 로딩 표시 있으나 레이아웃 피드백 전혀 없음
- 0-3 — 로딩 state 자체 부재 또는 빈 화면만

**채점 기준 (1.2 Progress):**
- 10 — 진행 단계 표시(% 또는 step indicator) + pulsing animation 힌트
- 8-9 — 진행 표시 있으나 단계 구분 없음
- 6-7 — generic spinner 만 존재
- 4-5 — 매우 작거나 눈에 띄지 않는 표시
- 0-3 — 진행 표시 부재

**채점 기준 (1.3 Cancellable):**
- 10 — 취소 버튼 명시 + 취소 후 상태 처리 설계
- 8-9 — 취소 버튼 존재하나 취소 후 상태 불명
- 6-7 — 10s 미만 작업에 취소 없음 (합리적)
- 0-3 — 10s+ 명백한 작업에 취소 경로 없음

### State 2. Empty (3항목)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 2.1 | First Use | 첫 진입 시 빈 화면에 onboarding illustration + primary CTA 존재 | Yes |
| 2.2 | No Results | 검색·필터 결과 0건 시 회복 경로(검색어 수정·필터 해제 등) 제공 | Yes |
| 2.3 | Cleared | 사용자가 콘텐츠를 직접 비운 상태에 다음 행동 안내 | Yes |

**채점 기준 (2.1 First Use):**
- 10 — illustration + 헤드카피 + primary CTA + 서브카피 전부
- 8-9 — illustration + CTA 있으나 헤드카피 빈약
- 6-7 — 텍스트 안내 + CTA 만 (illustration 없음)
- 4-5 — CTA 만 존재
- 0-3 — 빈 화면 / "데이터 없음" 텍스트만

**채점 기준 (2.2 No Results):**
- 10 — 0건 메시지 + 원인 설명 + 회복 CTA(예: 필터 초기화, 다른 검색어 시도)
- 8-9 — 0건 메시지 + 회복 CTA 있으나 설명 부족
- 6-7 — 0건 메시지만 (회복 경로 없음)
- 4-5 — 빈 목록만 렌더링
- 0-3 — 검색 결과 0건 state 자체 부재

**채점 기준 (2.3 Cleared):**
- 10 — 비워진 상태 인지 + 되돌리기(undo) 또는 재추가 CTA
- 8-9 — 재추가 CTA 있으나 undo 없음
- 6-7 — "비어있음" 메시지만
- 0-3 — Cleared 상태 설계 부재

### State 3. Error (3항목)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 3.1 | Validation | 인라인 에러 메시지 위치·구체성·plain language 사용 | Yes |
| 3.2 | System | 시스템·네트워크 에러에 사용자 책임 아님 톤 + retry 제공 | Yes |
| 3.3 | Recovery | 에러 후 입력값 보존, undo 경로, 원래 상태 복귀 가능 | Yes |

**채점 기준 (3.1 Validation):**
- 10 — 필드 인접 인라인 표시 + 구체 수정 방법 + 아이콘 + 색상
- 8-9 — 인라인이나 메시지 일반적 ("필수 항목입니다")
- 6-7 — 폼 상단 집합 에러 (인라인 아님)
- 4-5 — 에러 있으나 위치·원인 불명확
- 0-3 — Validation error state 설계 부재

**채점 기준 (3.2 System):**
- 10 — 사용자 책임 아님 명시 + 원인 설명 + retry button + 지원 연락 경로
- 8-9 — retry 있으나 원인 설명 부족
- 6-7 — 일반 에러 메시지 + retry 만
- 4-5 — "오류가 발생했습니다" 텍스트만
- 0-3 — System error state 설계 부재

**채점 기준 (3.3 Recovery):**
- 10 — 에러 후 입력값 100% 보존 + undo/back 경로 명시
- 8-9 — 입력값 보존이나 undo 없음
- 6-7 — 일부 입력값 보존
- 4-5 — 에러 후 폼 초기화
- 0-3 — Recovery 설계 부재

### State 4. Success (3항목)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 4.1 | Confirmation | 완료 명시 — Shneiderman Closure 원칙 (사용자가 task 완료를 명확히 인지) | Yes |
| 4.2 | Next Step | 완료 후 후속 액션 CTA 제공 | Yes |
| 4.3 | Celebration | micro-delight 요소 존재 (선택 항목, 높은 감성 가치) | Partial |

**채점 기준 (4.1 Confirmation):**
- 10 — 완료 아이콘 + 헤드카피 + 세부 내용 요약 (영수증·확인 번호 등)
- 8-9 — 완료 아이콘 + 메시지 있으나 요약 없음
- 6-7 — 완료 메시지만
- 4-5 — 완료 여부 불명확 (redirect 만)
- 0-3 — Success state 설계 부재

**채점 기준 (4.2 Next Step):**
- 10 — 맥락에 맞는 next step CTA 1-2개 (예: "주문 확인하기", "계속 쇼핑하기")
- 8-9 — next step CTA 있으나 맥락 연결 약함
- 6-7 — "홈으로 돌아가기" 같은 generic CTA 만
- 0-3 — Next step 설계 부재

**채점 기준 (4.3 Celebration):**
- 10 — animation·confetti·sound hint·emotionally resonant illustration 등 delight 요소
- 6-7 — 정적 일러스트 또는 아이콘 수준의 micro-delight
- 0-5 — Celebration 요소 없음 (선택 항목이므로 0점 = 감점 아님, info 처리)

### State 5. Offline (3항목)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 5.1 | Detection | connection lost 즉시 표시 (배너·아이콘·색상 변화) | Yes |
| 5.2 | Cached Fallback | offline 모드 UI — 캐시 콘텐츠 접근 가능 여부 표시 | Yes |
| 5.3 | Sync | 온라인 복귀 시 자동 sync 표시 또는 manual refresh 안내 | Yes |

**채점 기준 (5.1 Detection):**
- 10 — 배너 + 아이콘 + "오프라인 상태" 텍스트 + 색상 변화
- 8-9 — 배너 또는 아이콘만
- 6-7 — 미묘한 인디케이터 (쉽게 놓침)
- 0-3 — Offline 감지 state 부재

**채점 기준 (5.2 Cached Fallback):**
- 10 — 오프라인 가능 기능 명시 + 불가 기능 grey-out + 캐시 시각 표시
- 8-9 — 일부 기능 표시이나 범위 불명
- 6-7 — "오프라인" 표시만 (캐시 활용 안내 없음)
- 0-3 — Cached fallback 설계 부재

**채점 기준 (5.3 Sync):**
- 10 — 복귀 시 자동 sync 애니메이션 + 완료 토스트
- 8-9 — 복귀 감지 후 refresh 버튼 유도
- 6-7 — 온라인 복귀 후 manual reload 필요
- 0-3 — Sync state 설계 부재

### State 6. Permission (3항목)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 6.1 | No Access | 권한 없음 명시 (무엇을 볼 수 없고 왜인지) | Yes |
| 6.2 | Upgrade Prompt | 상위 권한·플랜 안내 (무엇을 잠금 해제할 수 있는지) | Yes |
| 6.3 | Request Flow | 권한 요청 경로 제공 (관리자에게 요청·플랜 업그레이드 CTA) | Yes |

**채점 기준 (6.1 No Access):**
- 10 — "접근 권한이 없습니다" + 원인 + 어디에 접근 가능한지 대안 안내
- 8-9 — 권한 없음 명시이나 원인 없음
- 6-7 — 빈 화면 + 텍스트만
- 0-3 — Permission state 설계 부재 (콘텐츠 없이 crash)

**채점 기준 (6.2 Upgrade Prompt):**
- 10 — 잠금 기능 가시화 + 업그레이드 혜택 명시 + CTA
- 8-9 — 업그레이드 CTA 있으나 혜택 설명 부족
- 6-7 — "Pro 기능입니다" 텍스트만
- 0-3 — Upgrade prompt 설계 부재

**채점 기준 (6.3 Request Flow):**
- 10 — 한 화면에서 권한 요청 완료 (관리자 알림 전송 CTA 등)
- 8-9 — 요청 경로 있으나 다른 화면으로 이탈 필요
- 6-7 — "관리자에게 문의하세요" 텍스트만
- 0-3 — Request flow 설계 부재

### State 7. Stale (3항목)

| # | 항목 | 평가 기준 | 정적 검증 |
|---|------|----------|----------|
| 7.1 | Outdated | 데이터 stale 표시 (배너·뱃지·색상 변화) | Yes |
| 7.2 | Refresh | pull-to-refresh 또는 refresh button 존재 | Yes |
| 7.3 | Timestamp | "마지막 업데이트" last updated 명시 | Yes |

**채점 기준 (7.1 Outdated):**
- 10 — stale 배너 + 경과 시간 + 색상 변화(주의색)
- 8-9 — 배너 있으나 색상 변화 없음
- 6-7 — 뱃지 또는 텍스트 힌트만
- 0-3 — Stale 표시 부재

**채점 기준 (7.2 Refresh):**
- 10 — 1회 탭으로 즉시 refresh + 갱신 중 skeleton 전환
- 8-9 — refresh button 있으나 skeleton 없음
- 6-7 — pull-to-refresh 만 (desktop 미지원)
- 0-3 — Refresh 경로 부재

**채점 기준 (7.3 Timestamp):**
- 10 — relative time("5분 전") + absolute time 툴팁 모두
- 8-9 — relative time 만
- 6-7 — absolute time 만
- 0-3 — Timestamp 부재

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일에서 **단일 프레임** 또는 **컴포넌트 세트**를 선택하고 "state 리뷰", "상태 점검", "빈 상태 점검", "에러 상태 검토", "로딩 상태 평가", "non-happy path 리뷰", "edge state audit" 등을 요청할 때
- design-ux-flow-review Lens C 7항목으로 부족하여 단일 프레임의 21항목 state completeness 를 깊이 분석할 때
- AG Grid 대시보드·데이터 테이블·폼 등 state 종류가 많은 단일 화면의 completeness 검증이 필요할 때
- 신규 화면 출시 전 state coverage 체크리스트로 활용할 때

## Do Not Use

- 멀티 프레임 flow 수준 분석 → `design-ux-flow-review` (L2 Structure, Lens C 포함)
- 단일 프레임 종합 UX 휴리스틱 평가 → `design-ux-nielsen-review` / `design-ux-ixdf-review`
- 시각·감성 UI 레이어 평가 → `design-ui-*-review`
- 다크 패턴 전용 점검 → `design-ux-dark-pattern-review`
- 라이브 사이트 audit → gstack `/design-review`
- 코멘트를 디자인 파일에 직접 게시 → `annotate-design`
- 발산형 UX 대안 생성 → `ux-audit-rethink` / `freeform-burst`

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 메시지 |
|----------|---------------------|---------------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP 가 연결되어 있지 않습니다. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 중 하나 활성화 후 재시도." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 가 연결되어 있지 않습니다. Pencil 앱을 실행하고 MCP 연동을 활성화한 뒤 다시 시도해주세요." |

체크 방법: 첫 단계에서 ToolSearch 로 prefix 의 도구를 조회. 결과가 비어 있으면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + 프레임 모드 라우팅

사용자 인자에서 입력 타입을 자동 감지:

- `figma.com/design/:fileKey/...?node-id=:nodeId` → **Figma 경로**
- `*.pen` 로컬 경로 → **Pencil 경로**
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

프레임 모드 자동 감지:

- 프레임 1개 선택 → **Single-frame mode** (해당 프레임의 21항목 전체 평가)
- 프레임 2+ 선택 → **Multi-frame mode** (각 프레임에 동일 21항목 평가 후 비교 테이블 추가)
- 선택 없음 → "Pencil/Figma 에서 리뷰할 프레임을 1개 이상 선택해주세요." 출력 후 종료

옵션 인자 처리:
- `--state Loading,Empty,Error` : 특정 state 만 평가 (콤마 구분, 1-7 또는 이름)
- `--context "{페이지 컨텍스트}"` : 프레임의 제품 맥락 명시 (예: "AG Grid 매출 현황 대시보드")

### Step 2 — MCP 사전 체크

Prerequisites 표 기준 ToolSearch. 미연결이면 안내 출력 후 종료.

### Step 3 — 디자인 데이터 수집 (deep)

**Figma 경로:**

1. `mcp__claude_ai_Figma__get_metadata(fileKey, nodeId)` 또는 `mcp__figma-console__figma_get_file_data` 로 프레임 구조 파악
2. 각 frame 에 대해:
   - `get_design_context(depth:8)` 로 deep 트리 + 컴포넌트 힌트 수집
   - `get_screenshot(frame.id)` 로 시각 참고 이미지 1장 확보
3. 프레임 이름·레이어 구조에서 state variant 패턴 자동 탐지:
   - `/Loading`, `/Empty`, `/Error`, `/Success`, `/Offline`, `/Permission`, `/Stale` 레이어 또는 컴포넌트 variant 명
   - 실제로 구현된 state 목록을 "발견된 state" 섹션에 기록

**Pencil 경로:**

1. `mcp__pencil__open_document(path=...)` (필요 시)
2. `mcp__pencil__get_editor_state()` 로 선택 프레임 목록 확인
3. 각 frame 마다:
   - `mcp__pencil__batch_get(node_ids=[frame_id], readDepth:6)` 로 deep 노드 트리
   - `mcp__pencil__snapshot_layout(node_id=frame_id)` 로 레이아웃 스냅샷
   - `mcp__pencil__get_screenshot(node_id=frame_id)` 로 이미지 확보
   - `mcp__pencil__search_all_unique_properties(node_id=frame_id, property="name")` 로 레이어명 패턴 추출

### Step 4 — Classifier (화면 타입 + 상태 variant 인벤토리)

수집된 프레임을 분류:

- **DATA TABLE / GRID** — AG Grid·테이블·목록 뷰 (Empty·Loading·Stale 가중↑)
- **FORM / INPUT** — 폼·검색·필터 (Error Validation·Success Confirmation 가중↑)
- **DASHBOARD HUB** — KPI 카드·차트·멀티 데이터소스 (Loading·Stale·Offline 가중↑)
- **DETAIL / PROFILE** — 상세 보기·프로필 (Loading·Permission·Error 가중↑)
- **CHECKOUT / TRANSACTION** — 결제·주문·계약 (Success·Error Recovery 가중↑)
- **SETTINGS / CONFIG** — 설정·권한 관리 (Permission 가중↑)
- **HYBRID** — 위 카테고리 혼재

분류 결과를 보고서 메타에 기록. 발견된 state variant 목록 ("발견된 state 인벤토리") 작성.

### Step 5 — First Impression (Phase 1)

프레임 스크린샷 본 직후 1인칭 작성:

```
- 이 화면의 primary purpose: [한 문장]
- 가장 먼저 눈에 띄는 state 설계: [state 이름 + 이유]
- 명백히 빠져 보이는 state: [state 이름 또는 "없음"]
- happy path 대비 non-happy path 설계 완성도: [한 문장]
- 한 단어 요약: [단어]
- 인상 메모: [구체적 긍정/부정]
```

### Step 6 — State Variant Inventory (Phase 2)

수집된 레이어 구조 + 스크린샷에서 추출한 state 인벤토리 표:

| State | Sub | 발견 여부 | 레이어/컴포넌트명 | 비고 |
|-------|-----|----------|----------------|------|
| Loading | Skeleton | ✅ / ❌ / ⚠️ | `Loading/Skeleton` | - |
| Loading | Progress | ✅ / ❌ / ⚠️ | - | - |
| Loading | Cancellable | ✅ / ❌ / ⚠️ | - | - |
| Empty | First Use | ✅ / ❌ / ⚠️ | - | - |
| ... | ... | ... | ... | ... |

✅ = 발견 및 적절 / ⚠️ = 발견이나 미흡 / ❌ = 미발견

### Step 7 — 21항목 평가 (Phase 3)

각 항목 0-10 점수. 레이어 구조 또는 스크린샷에서 확인 불가한 항목은 `N/A` + 사유. `--state` 옵션으로 지정된 state 만 평가.

**점수 기준:**
- 10 — exemplary, 해당 state 완전 설계
- 8-9 — solid, 사소한 polish
- 6-7 — 기능적이나 개선 여지
- 4-5 — 불완전 state 설계 (사용자 혼란 가능)
- 0-3 — state 부재 또는 심각한 결함
- N/A — 정적 분석으로 검증 불가

**Severity 가이드:**
- critical: 점수 0-3, drop-off 또는 작업 실패 직결
- warning: 점수 4-6, 사용자 혼란·friction 유발
- info: 점수 7+, 개선 가능하나 긴급하지 않음
- 4.3 Celebration — 0점이어도 info (선택 항목)
- 5.x Offline, 6.x Permission — 해당 기능이 없는 화면이면 N/A 허용

### Step 8 — State Coverage Score 산출

**State Coverage Score** = covered / 21

covered 조건: 해당 항목 점수 ≥ 6 (기능적 수준 이상)

**7 State 별 점수** = 각 state 3 sub-항목 평균 (N/A 제외)

| State | Sub 항목 점수 합 | N/A 제외 평균 | Coverage |
|-------|----------------|-------------|----------|
| 1. Loading | - | - | {n}/3 |
| 2. Empty | - | - | {n}/3 |
| 3. Error | - | - | {n}/3 |
| 4. Success | - | - | {n}/3 |
| 5. Offline | - | - | {n}/3 |
| 6. Permission | - | - | {n}/3 |
| 7. Stale | - | - | {n}/3 |
| **전체** | - | **{avg}/10** | **{covered}/21** |

**State Health Grade:**
- 19-21 covered = **A** (State-complete — non-happy path 완전 설계)
- 15-18 covered = **B** (Good — minor gap)
- 10-14 covered = **C** (Partial — state rework 필요)
- 5-9 covered = **D** (Poor — 주요 state 누락)
- 0-4 covered  = **F** (Critical — state 설계 전면 재작업)

### Step 9 — Top-3 Missing State 선정

누락 또는 critical 항목 중 사용자 영향 기준 상위 3개 선정.

각 카드 포맷:
- **누락 state** (state.sub 번호 + 이름)
- **사용자 영향** (어떤 상황에서 사용자가 막히는가)
- **비즈니스 영향** (신뢰·전환·리텐션 영향)
- **설계 방향** (구체 컴포넌트·패턴 제안)
- **기대 점수 변화** (항목 N → N', Coverage +{n})
- **노력 규모** (Low/Medium/High)

선정 우선순위:
1. 0점(완전 부재) state — 특히 Error·Loading·Empty (가장 흔한 critical)
2. 화면 타입 가중 우선 state (Data Table → Empty/Loading, Form → Error, Dashboard → Loading/Stale)
3. 다중 항목에서 critical 이 겹치는 state

### Step 10 — 보고서 작성

**파일 경로**: `./design-reviews/design-ux-states-review-{frame-slug}-{YYYYMMDD-HHmm}.md`
- `{frame-slug}`: frame.name 을 kebab-case + 소문자 (한글이면 음역 또는 nodeId 끝 8자)
- `{YYYYMMDD-HHmm}`: 현재 시각 (24H, KST)
- 디렉터리 없으면 자동 생성

Multi-frame 모드: 프레임당 1파일 + 비교 요약 1파일 (`-comparison-{YYYYMMDD-HHmm}.md`)

### Step 11 — 사용자에게 결과 요약

- 생성된 보고서 파일 경로
- State Health Grade + State Coverage Score ({covered}/21) + critical/warning 개수
- 7 state 별 점수 한 줄 요약 (covered/3 + 평균 점수)
- Top-3 Missing State 이름 + 한 줄 설명
- 다음 액션 제안 (annotate-design / 디자인 작업 / flow-review 연계)

### Step 12 — (선택) Flow Review 연계 안내

화면 타입이 FORM / CHECKOUT / ONBOARDING 이거나 multi-frame 모드일 때:
"state 설계 보완 후 `design-ux-flow-review --lens C` 로 flow 레벨 edge state 를 재확인하면 단일 프레임(states-review) + 흐름 전체(flow-review) 이중 검증이 완성됩니다."

## 보고서 구조 (한국어)

```markdown
# States Review: {frame.name}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID: {nodeId}
- 프레임 이름: {frame.name}
- 화면 타입: {DATA TABLE/GRID | FORM/INPUT | DASHBOARD HUB | DETAIL/PROFILE | CHECKOUT/TRANSACTION | SETTINGS/CONFIG | HYBRID}
- 컨텍스트: {--context 인자 또는 추정}
- 평가 state: {All | 지정 state 목록}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 인라인}
- 방법론: NN/g Empty State · NN/g Error Messages · NN/g Progress Indicators · Vitaly Friedman state catalog · Setproduct Empty State · Shneiderman Closure (Success) · design-ux-flow-review Lens C 확장

## 헤드라인
- **State Health Grade: {A-F}** ({avg}/10)
- **State Coverage Score: {covered}/21** ({%}%)
- critical: {n}건 · warning: {n}건 · info: {n}건
- **Top-3 Missing State**: {state.sub 이름} · {state.sub 이름} · {state.sub 이름}

## First Impression
- 이 화면의 primary purpose: {...}
- 가장 먼저 눈에 띄는 state 설계: {...}
- 명백히 빠져 보이는 state: {...}
- happy path 대비 non-happy path 설계 완성도: {...}
- 한 단어 요약: {...}
- 인상 메모: {...}

## State Variant Inventory

| State | Sub | 발견 여부 | 레이어/컴포넌트명 | 비고 |
|-------|-----|----------|----------------|------|
| Loading | Skeleton | ✅/❌/⚠️ | - | - |
| Loading | Progress | ✅/❌/⚠️ | - | - |
| Loading | Cancellable | ✅/❌/⚠️ | - | - |
| Empty | First Use | ✅/❌/⚠️ | - | - |
| Empty | No Results | ✅/❌/⚠️ | - | - |
| Empty | Cleared | ✅/❌/⚠️ | - | - |
| Error | Validation | ✅/❌/⚠️ | - | - |
| Error | System | ✅/❌/⚠️ | - | - |
| Error | Recovery | ✅/❌/⚠️ | - | - |
| Success | Confirmation | ✅/❌/⚠️ | - | - |
| Success | Next Step | ✅/❌/⚠️ | - | - |
| Success | Celebration | ✅/❌/⚠️ | - | - |
| Offline | Detection | ✅/❌/⚠️ | - | - |
| Offline | Cached Fallback | ✅/❌/⚠️ | - | - |
| Offline | Sync | ✅/❌/⚠️ | - | - |
| Permission | No Access | ✅/❌/⚠️ | - | - |
| Permission | Upgrade Prompt | ✅/❌/⚠️ | - | - |
| Permission | Request Flow | ✅/❌/⚠️ | - | - |
| Stale | Outdated | ✅/❌/⚠️ | - | - |
| Stale | Refresh | ✅/❌/⚠️ | - | - |
| Stale | Timestamp | ✅/❌/⚠️ | - | - |

## 점수표 (21 항목)

### State 1. Loading

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| 1.1 | Skeleton | - | - |
| 1.2 | Progress | - | - |
| 1.3 | Cancellable | - | - |
| **평균** | | **-** | covered: {n}/3 |

### State 2. Empty

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| 2.1 | First Use | - | - |
| 2.2 | No Results | - | - |
| 2.3 | Cleared | - | - |
| **평균** | | **-** | covered: {n}/3 |

### State 3. Error

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| 3.1 | Validation | - | - |
| 3.2 | System | - | - |
| 3.3 | Recovery | - | - |
| **평균** | | **-** | covered: {n}/3 |

### State 4. Success

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| 4.1 | Confirmation | - | - |
| 4.2 | Next Step | - | - |
| 4.3 | Celebration | - | - |
| **평균** | | **-** | covered: {n}/3 |

### State 5. Offline

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| 5.1 | Detection | - | - |
| 5.2 | Cached Fallback | - | - |
| 5.3 | Sync | - | - |
| **평균** | | **-** | covered: {n}/3 |

### State 6. Permission

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| 6.1 | No Access | - | - |
| 6.2 | Upgrade Prompt | - | - |
| 6.3 | Request Flow | - | - |
| **평균** | | **-** | covered: {n}/3 |

### State 7. Stale

| # | 항목 | 점수 | 비고 |
|---|------|------|------|
| 7.1 | Outdated | - | - |
| 7.2 | Refresh | - | - |
| 7.3 | Timestamp | - | - |
| **평균** | | **-** | covered: {n}/3 |

### 전체 State Coverage

| State | 평균 점수 | covered/3 |
|-------|---------|-----------|
| Loading | - | - |
| Empty | - | - |
| Error | - | - |
| Success | - | - |
| Offline | - | - |
| Permission | - | - |
| Stale | - | - |
| **전체** | **-/10** | **{covered}/21** |

## Findings

### {state}.{sub} — score: {N}
- **severity**: critical | warning | info
- **state**: Loading | Empty | Error | Success | Offline | Permission | Stale
- **evidence**: 프레임 `{nodeId}` · 레이어 `{layerName}` · {구체 근거}
- **fix**: {구체 컴포넌트·패턴·텍스트 수정 액션}
- **참고**: {NN/g 출처 URL 또는 방법론 — NN/g Empty State https://www.nngroup.com/articles/empty-state-interface/ | NN/g Error Messages https://www.nngroup.com/articles/error-message-guidelines/ | NN/g Progress Indicators https://www.nngroup.com/articles/progress-indicators/ | Vitaly Friedman state catalog | Setproduct Empty State https://www.setproduct.com/blog/empty-state-ui-design | Shneiderman Closure}

{위반/개선점이 있는 항목만 나열 — 점수 낮은 순}

## Top-3 Missing State

### Missing 1 — {state}.{sub} · {항목명}
- **누락 state**: {state 번호}.{sub 번호} {이름}
- **사용자 영향**: {어떤 상황에서 사용자가 막히는가}
- **비즈니스 영향**: {신뢰·전환·리텐션 영향}
- **설계 방향**: {구체 컴포넌트·패턴 제안}
- **기대 점수 변화**: {항목} {N} → {N'}, Coverage +{n}
- **노력**: {Low/Medium/High} ({n} weeks)

### Missing 2 — ...
### Missing 3 — ...

## N/A 항목 (정적 분석 한정)
- {항목 번호}: {검증 불가 사유}
- 4.3 Celebration: 정적 분석에서 animation 실측 불가, 정적 일러스트 존재 여부만 평가
- 5.x Offline, 6.x Permission: 해당 화면이 offline/permission 시나리오에 노출되지 않는 경우 N/A

## 다음 단계 (권장 후속)
- Top-3 Missing State 를 디자인 작업 backlog 에 추가
- `annotate-design` 스킬로 finding 을 디자인 파일에 시각화
- state 보완 후 `design-ux-flow-review --lens C` 로 flow 레벨 edge state 재확인
- 사용성 테스트에서 Error Recovery(3.3)·Empty First Use(2.1) 시나리오 우선 검증
```

## 인자

```
/design-ux-states-review <Figma URL | .pen path> [--state Loading,Empty,Error,...] [--context "{페이지 컨텍스트}"]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- 옵션 `--state Loading,Empty,Error` : 평가할 state 이름 또는 번호 (1-7, 콤마 구분). 미지정 시 전체 21항목.
- 옵션 `--context "{...}"` : 화면 컨텍스트 명시 (예: "EasySeller AG Grid 매출 현황 대시보드")
- 프레임 선택은 Figma/Pencil **현재 선택** 으로 자동 감지

## 예시

### 예시 1 — Figma 단일 프레임 전체 평가
```
/design-ux-states-review https://www.figma.com/design/abc123/EasySeller?node-id=42-1024 --context "AG Grid 매출 현황 대시보드"
```
→ Figma MCP 체크 → 단일 프레임 수집 → 화면 타입 = DASHBOARD HUB → 21항목 전체 평가 → State Coverage Score 산출 → `./design-reviews/design-ux-states-review-sales-dashboard-20260518-1400.md` 생성

### 예시 2 — Pencil 특정 state 만 평가
```
/design-ux-states-review ~/Desktop/projects/design/easyseller.pen --state Error,Empty
```
→ Pencil MCP 체크 → 선택 프레임 수집 → Error(3항목) + Empty(3항목) = 6항목만 평가 → Coverage {covered}/6 보고

### 예시 3 — Multi-frame 비교
```
/design-ux-states-review https://www.figma.com/design/abc123/EasySeller --context "주문 관리 페이지 vs 정산 페이지"
```
→ 선택된 2개 프레임 각각 21항목 평가 → 2개 파일 + 비교 요약 파일 생성

### 예시 4 — MCP 미연결
```
/design-ux-states-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 가 연결되어 있지 않습니다." 안내 후 종료

### 예시 5 — flow-review 와 연계
```
/design-ux-states-review <URL>   # 단일 프레임 21항목 state completeness
/design-ux-flow-review <URL> --lens C   # flow 레벨 Lens C 7항목
```
→ 두 스킬 병행 시 단일 화면 깊이 + flow 전체 폭 이중 검증 완성

## 출력 규약

- 모든 사용자 대상 텍스트는 **한국어**
- State 이름은 영어 원어 유지 (Loading, Empty, Error, Success, Offline, Permission, Stale)
- sub 항목명도 영어 원어 유지 (Skeleton, First Use, Validation, Confirmation, Detection 등)
- finding 의 evidence/fix 는 프레임 nodeId·레이어명·구체 액션 명시
- finding 헤더 포맷 `### {state}.{sub} — score: {N}` (annotate-design 스킬 파싱 호환)
- severity / state / evidence / fix / 참고 필드 동일 순서 유지
- Top-3 Missing State 는 별도 섹션
- 4.3 Celebration 은 0점이어도 severity = info (강제 critical/warning 금지)
- 5.x Offline / 6.x Permission 은 해당 화면에 무관하면 N/A 허용 (0점 강제 금지)

## annotate-design 호환성

본 스킬의 출력 .md 는 `annotate-design` 스킬이 파싱하여 디자인 파일에 코멘트 패널 + 번호 마커를 부착할 수 있도록 동일한 finding 포맷을 사용한다.

워크플로:
```
/design-ux-states-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md> → 디자인 파일에 시각 코멘트 부착
```

## design-ux-flow-review Lens C 와의 차이

| 기준 | design-ux-flow-review Lens C | design-ux-states-review |
|------|------------------------------|------------------------|
| 추상화 단계 | L2 Structure (flow 시퀀스) | L1 Skeleton (단일 프레임) |
| 평가 단위 | flow 전체에서 edge state 7항목 | 단일 프레임 21항목 |
| 평가 깊이 | shallow — 존재 여부 + 1줄 | deep — sub 3항목 × 채점 기준 5단계 |
| Coverage 지표 | Lens C sub-grade (0-10) | State Coverage Score ({n}/21) |
| 입력 | 2+ frame 시퀀스 또는 hub frame | 단일 frame 또는 variant set |
| 보완 관계 | flow 폭 | 단일 화면 깊이 |

## Non-Goals

- 디자인 파일 코멘트 직접 게시 — `annotate-design` 책임
- 멀티 프레임 flow 수준 edge state 평가 — `design-ux-flow-review` 책임
- 단일 프레임 종합 UX 휴리스틱 — `design-ux-nielsen-review` / `design-ux-ixdf-review` 책임
- 시각·감성 UI 평가 — `design-ui-*-review` 책임
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만
- 코드 생성 — 디자인 파일만
- 라이브 사이트 audit — gstack `/design-review` 책임

## 참고 자료

- 평가 rubric 은 본 SKILL.md 내 인라인
- 방법론 출처:
  - **Empty State** — NN/g https://www.nngroup.com/articles/empty-state-interface/ · Setproduct https://www.setproduct.com/blog/empty-state-ui-design
  - **Error Messages** — NN/g https://www.nngroup.com/articles/error-message-guidelines/
  - **Progress Indicators** — NN/g https://www.nngroup.com/articles/progress-indicators/
  - **State Catalog** — Vitaly Friedman "Designing for Edge Cases" (Smashing Magazine)
  - **Success / Closure** — Ben Shneiderman *Designing the User Interface* 8 Golden Rules (Rule 6: Closure)
  - **Lens C 확장** — `design-ux-flow-review` Lens C (7항목) 단일 프레임 깊이 확장
- 짝 스킬: `design-ux-flow-review` (L2 Structure Lens C · flow 수준) · `design-ux-nielsen-review` (L1 종합 휴리스틱) · `annotate-design` (코멘트 부착)
