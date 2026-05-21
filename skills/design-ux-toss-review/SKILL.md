---
name: design-ux-toss-review
review-level: L1-L2 Hybrid
description: "[L1-L2 Hybrid] Figma URL 또는 Pencil(.pen) 파일의 선택된 프레임을 토스 Apps in Toss 디자인 가이드(Consumer UX Dark Pattern 5 룰 + UX Writing 5 원칙) 기준으로 정적 분석하여 한국어 마크다운 리뷰 보고서를 생성. Toss Compliance Grade(A-F) 헤드라인 + Dark Pattern Health sub-grade + Writing Health sub-grade + 10 항목 ✅/❌/⚠️ + 위반 자동 critical + Top-3 Fix. 토스 가이드 출처(developers-apps-in-toss.toss.im/design)에 직접 매핑. 사용자가 \"toss 가이드 리뷰\", \"토스 UX 리뷰\", \"Apps in Toss 리뷰\", \"토스 라이팅 점검\", \"토스 다크패턴 점검\", \"토스 컴플라이언스\", \"/design-ux-toss-review\" 를 말하거나 figma.com/design URL 또는 .pen 파일을 가지고 토스 가이드 기반 리뷰를 요청할 때 사용."
---

# design-ux-toss-review

**Review Level**: L1-L2 Hybrid — Toss 「Apps in Toss」 디자인 가이드 컴플라이언스 audit.

토스가 외부 개발자/디자이너에게 공개한 「Apps in Toss」 컨슈머 UX + UX writing 가이드 (https://developers-apps-in-toss.toss.im/design) 의 핵심 10 룰을 정적 분석 rubric 으로 변환하여 Figma/Pencil 프레임을 평가한다. Toss Compliance Grade(A-F) 헤드라인 + Dark Pattern Health sub-grade + Writing Health sub-grade.

평가 렌즈 = "이 디자인이 토스 가이드(예측 가능 · 자율성 존중 · 명확한 CTA · 해요체 · 능동 · 긍정 · 캐주얼 경어 · 명사 풀어쓰기)를 따르는가?"

stat-front 셀러 dashboard 컨텍스트: 토스 입점 미니앱 / 토스 결제 연동 / 토스 톤 차용 셀러 화면에서 컴플라이언스 = 신뢰 자산.

## 평가 항목 (10 룰)

토스 가이드 2 영역 직접 매핑. 각 항목 ✅(준수) / ❌(위반 감지) / ⚠️(경계) / N/A(정적 검증 불가).

### Part A — Consumer UX Dark Pattern (5 룰) · L2 Structure

| # | Rule | 토스 원문 요약 | 정적 검증 |
|---|------|--------------|----------|
| DP-1 | 진입 시 즉시 바텀시트 노출 금지 | 사용자가 의도한 목적을 바로 수행해야 함. 광고/알림 동의 바텀시트 즉시 노출 금지 | Yes |
| DP-2 | 뒤로 가기 시 알림 동의 바텀시트 노출 금지 | 이탈 방지용 인터럽트 = 자율성 침해. 뒤로가기 = 사용자 의지 존중 | Yes |
| DP-3 | 거절 불가능한 설계 금지 | CTA 단일 선택지 = 강제. 거절/닫기/나중에 옵션 필수 | Yes |
| DP-4 | 예상 외 전면 광고 노출 금지 | 사용 흐름 일관성. 메뉴/CTA 선택 후 갑작스런 광고 인터스티셜 금지 | Yes |
| DP-5 | 모호한 CTA 버튼 금지 | 버튼 라벨로 다음 화면/행동 명확히 예측 가능해야 함. 반복 설명·과장 보조 텍스트 금지 | Yes |

### Part B — UX Writing (5 원칙 + 보조 규칙) · L1 Skeleton

| # | Rule | 토스 원문 요약 | 정적 검증 |
|---|------|--------------|----------|
| W-1 | 해요체 통일 | 모든 상황·맥락에서 '해요체' 일관 적용. 합니다체·반말 혼용 금지 | Yes |
| W-2 | 능동적 말하기 | "됐어요"→"했어요". '~었' 제거. 동사 바꿔쓰기. 예외: 서비스 종료/만료/사용자 영향 설명은 수동 허용 | Yes |
| W-3 | 긍정적 말하기 | "없어요"→"있어요". 에러도 긍정 대체. 다이얼로그 버튼 "닫기"(취소 금지). 혜택 제약은 긍정 안내. 예외: 정책상 명확한 부정 필요 시 허용 | Yes |
| W-4 | 캐주얼한 경어 | '~시' 제거. "계시다"→"있다". "여쭈다"→"확인하다/묻다". "께"→"에게". 예외: 사용자 맥락 활용/상황 추정/선의 필요 시 "~시나요?/~셨나요?" 허용 | Yes |
| W-5 | 명사 중복 제거 | 한자어를 동사형으로 풀어쓰기. 불가 시 "{명사}가 {명사}해서" 형태 | Yes |
| W-Aux | 보조 통일 — "되어요"→"돼요" | 모바일 화면 공간 고려 축약형 강제 | Yes |

> Part A 위반 1건 = 자동 critical (토스 가이드 명시적 금지 사항). Part B 위반은 sub-grade 에 누적.

## When to Use

- 사용자가 Figma URL 또는 `.pen` 파일에서 "토스 가이드 리뷰", "Apps in Toss 리뷰", "토스 UX writing 점검", "토스 다크패턴 점검", "토스 컴플라이언스", "/design-ux-toss-review" 를 요청할 때
- 토스 미니앱 / 토스 결제 연동 / 토스 톤 차용 셀러 화면 출시 전 컴플라이언스 점검
- design-ux-dark-pattern-review (Brignull 12) 와 별개로 토스 한정 5 룰 + 한국어 UX writing 5 원칙 동시 점검이 필요할 때
- 토스 입점 심사 사전 셀프 audit
- 한국어 마이크로카피 톤 통일성 확인 (해요체·능동·긍정·캐주얼 경어·명사 풀어쓰기)

## Do Not Use

- Brignull 12 카테고리 전수 윤리 audit → `design-ux-dark-pattern-review`
- 일반 한국어/영어 마이크로카피 8 lens 평가 → `design-ux-microcopy-review`
- 단일 프레임 UX 휴리스틱 전반 → `design-ux-nielsen-review`
- 다중 프레임 flow IA·전환·습관 → `design-ux-flow-review`
- 시각 UI 레이어 → `design-ui-*-review`
- 코멘트 디자인 파일 직접 게시 → `annotate-design`
- 자동 수정 / 디자인 변경 — 리뷰 + 제안만

## Prerequisites — MCP 연결 체크 (필수)

| 입력 타입 | 필수 MCP 도구 prefix | 미연결 시 안내 |
|----------|---------------------|---------------|
| `figma.com/design/...` URL | `mcp__claude_ai_Figma__*` 또는 `mcp__figma-console__*` | "Figma MCP 미연결. claude.ai Figma 연동, Dev Mode MCP, 또는 figma-console Desktop Bridge 활성화 후 재시도." |
| `*.pen` 경로 | `mcp__pencil__*` | "Pencil MCP 미연결. Pencil 앱 실행 + MCP 연동 활성화 후 재시도." |

체크 방법: Step 1에서 ToolSearch 로 prefix 도구 조회. 결과 비면 안내 출력 후 즉시 종료.

## Workflow

### Step 1 — 입력 파싱 + MCP 사전 체크

사용자 인자에서 입력 타입 자동 감지:
- `figma.com/design/:fileKey/...?node-id=:nodeId` → Figma 경로
- `*.pen` 로컬 경로 → Pencil 경로
- 둘 다 아니면: "입력은 figma.com URL 또는 .pen 파일 경로여야 합니다." 출력 후 종료

ToolSearch 로 Prerequisites 표 MCP 확인. 미연결이면 안내 출력 후 종료.

옵션 인자:
- `--scope "{범위}"`: 특정 영역/flow 집중
- `--part dp|writing|both` (기본 both): Part A/B 선택 실행
- `--context "{비즈니스 맥락}"` (기본값: "토스 입점 미니앱 / 토스 톤 셀러 화면")
- `--strict` : Part B 예외 조항 무시하고 모든 수동/부정/'~시' 패턴을 ❌ 로 판정 (가이드 보수적 해석)

### Step 2 — 디자인 데이터 수집

**Figma:**
1. `get_metadata(fileKey, nodeId)` — 프레임/flow 구조
2. 프레임마다:
   - `get_design_context(fileKey, nodeId, depth:8)` — 깊은 트리 + 텍스트 노드
   - `get_screenshot(fileKey, nodeId)` — 시각 참고
3. 특히 다음 집중 추출:
   - 바텀시트 / 모달 / 다이얼로그 노드 (DP-1·DP-2·DP-3 검증)
   - CTA 버튼 라벨 (DP-5·W-1·W-2·W-3·W-Aux)
   - 광고 / 배너 / 인터스티셜 노드 (DP-4)
   - 에러 / 빈 상태 / 알림 텍스트 (W-2·W-3)
   - 폼 라벨 / placeholder / helper text (W-1·W-4·W-5)

**Pencil:**
1. `open_document(path)` (필요 시)
2. `get_editor_state()` — 선택 프레임 확인
   - 선택 비면: "Pencil 편집기에서 리뷰할 프레임 1개 이상 선택 후 재시도." 출력 후 종료
3. 프레임마다:
   - `batch_get(node_ids=[frame_id], readDepth:4)` — 노드 트리
   - `snapshot_layout(node_id)` — 레이아웃
   - `get_screenshot(node_id)` — 이미지
   - `search_all_unique_properties(node_id, property="text")` — 전체 텍스트 팔레트

### Step 3 — 컨텍스트 분류

수집 데이터 기반 화면 성격 분류:
- **ENTRY/HUB**: 앱/미니앱 진입 화면 (DP-1·DP-2 집중)
- **MID-FLOW**: 작업 중간 단계 (DP-3·DP-4·DP-5 집중)
- **FORM/INPUT**: 입력·동의·결제 화면 (W-1~W-5 + DP-3 집중)
- **NOTIFICATION/SHEET**: 바텀시트·모달·토스트 (DP-1·DP-2·DP-3·DP-5·W-3 집중)
- **HYBRID**: 혼재

### Step 4 — First Impression (토스 톤 관점)

스크린샷 직후 1인칭 즉시 반응:

```
- 토스 가이드 부합 첫인상: [한 문장]
- 즉시 위반 의심 요소: [최대 3개 또는 "없음"]
- 토스 톤(예측가능·자율성·명확) 관점 가장 거슬리는 부분: [한 문장]
- 한 단어 컴플라이언스 요약: [단어]
- 인상 메모: [구체 우려/안심 근거]
```

진단가는 헤지하지 않는다.

### Step 5 — Part A · Dark Pattern 5 룰 평가

각 룰마다 정밀 검사:

**판정 기준:**
- ✅ 준수: 위반 증거 없음 → score 10
- ⚠️ 경계: 단정 어려우나 잠재 위험 → score 5-7, warning
- ❌ 위반: 명확한 증거 → score 0-4, **자동 critical**
- N/A: 해당 UI 요소 없음 → 집계 제외

**룰별 검사 포인트:**

**DP-1 진입 시 즉시 바텀시트 노출 금지**
- 진입 frame 의 onMount/onEnter 바텀시트·모달·다이얼로그 존재
- 광고 배너 / 알림 동의 / 이벤트 안내 즉시 노출 패턴
- 사용자 첫 액션 차단 여부 (3초 이내 자동 노출 = ❌)
- 합법 예외: 필수 약관 동의 (최초 1회) / 보안 경고 / 시스템 점검 공지

**DP-2 뒤로 가기 시 알림 동의 바텀시트 노출 금지**
- 뒤로가기 trigger 시 인터럽트 시트 존재
- "잠깐! 알림 받으시면…" / "이대로 나가시겠어요? + 알림 동의" 패턴
- 종료 확인 다이얼로그에 부가 동의 항목 끼워넣기 (= ❌ Sneaking)
- 합법 예외: 데이터 손실 경고 / 결제 중단 확인 (부가 동의 없을 때만)

**DP-3 거절 불가능한 설계 금지**
- 모달/바텀시트에 CTA 1개만 존재 (닫기/취소/나중에 옵션 0)
- 닫기 X 버튼 부재 / 백드롭 탭 차단
- 거절 옵션이 hidden·작은 텍스트·낮은 대비
- 시스템 권한 요청 시 거절 경로 안내 부재
- 합법 예외: 보안 경고 강제 확인 / 약관 동의 (이 경우 닫기 = 앱 종료 명시)

**DP-4 예상 외 전면 광고 노출 금지**
- 메뉴/탭/CTA 선택 후 도착 화면 직전 인터스티셜
- 작업 완료/확인 직후 광고 전면 노출
- 광고 노출 빈도 무제한 (회당 1회 제한 표시 없음)
- 광고/스폰서 배지 가시성 (DP-4 ∩ Brignull Disguised Ads)
- 합법 예외: 자연스러운 광고 슬롯(피드 내 인라인) / 사용자 명시 동의 광고 시청 보상

**DP-5 모호한 CTA 버튼 금지**
- 버튼 라벨이 "확인", "다음", "OK" 만 단독
- 라벨이 행위·결과 명시 부재 ("계속하기" vs "5,000원 결제하기")
- 라벨 + 보조 텍스트 중복 ("결제하기" 위에 "결제를 진행하려면 누르세요")
- 라벨 과장 / 클릭 후 결과 불일치 ("무료로 시작" → 결제 카드 요구)
- 동일 화면 내 CTA hierarchy 모호 (primary 2개 이상)

### Step 6 — Part B · UX Writing 5 원칙 평가

수집 텍스트 노드 전체를 룰별 패턴 매칭:

**W-1 해요체 통일**
- 합니다체 ("입니다", "합니다", "됩니다") 빈도 카운트
- 반말 ("이야", "할게", "해줘") 빈도
- 해요체 ("이에요/예요", "해요", "돼요") 비율
- 평가: 해요체 비율 < 90% = ⚠️ , 합니다체 또는 반말 1건 이상 = ❌ (예외: 법적 고지·약관)

**W-2 능동적 말하기**
- "됐어요" / "되었어요" / "되어요" 패턴 검출
- '~었' 과거 수동형 ("등록되었어요" → "등록했어요")
- 합법 예외: 서비스 종료/기간 만료/사용자 영향 설명 (`--strict` 시 무시)
- 평가: 수동 1건 = ⚠️, 3건 이상 = ❌

**W-3 긍정적 말하기**
- "없어요" / "불가능" / "할 수 없" 패턴
- 에러 메시지: "잘못된 입력" → "다시 확인해주세요"
- 다이얼로그 "취소" 버튼 존재 (→ "닫기" 권장)
- 혜택 제약 표현 "받을 수 없" → "받으려면 …필요해요"
- 합법 예외: 정책상 명확 부정 ("법령상 불가") (`--strict` 시 무시)
- 평가: 부정 1건 = ⚠️, 3건 이상 또는 "취소" 버튼 = ❌

**W-4 캐주얼한 경어**
- '~시' 어미 ("하시면", "누르시면") 검출
- "계시다", "여쭈다", "께" 단어 검출
- 합법 예외: 사용자 맥락 활용/상황 추정/선의 필요 시 "~시나요?/~셨나요?" 허용 (`--strict` 시 무시)
- 평가: 1건 = ⚠️, 3건 이상 = ❌

**W-5 명사 중복 제거**
- "{명사}+{명사}+{명사}" 3연속 한자어 패턴 ("결제정보 입력 화면 안내")
- "~의 ~의 ~" 조사 사슬
- 동사형 풀어쓰기 후보: "안내" → "알려드려요", "확인" → "확인해주세요"
- 평가: 3연속 명사 1건 = ⚠️, 3건 이상 = ❌

**W-Aux 보조 통일**
- "되어요" 검출 = 즉시 ❌ ("돼요" 강제)
- 줄바꿈 직전 조사 끊김 (예: "결제를\n" → "결제를 진행해요\n") 보조 검사

### Step 7 — Toss Compliance Grade 산출

**Part A · Dark Pattern Health (DPH):**
- DP-1~DP-5 점수 평균 (0-10)
- 9.5-10 = A · 8.0-9.4 = B · 6.0-7.9 = C · 4.0-5.9 = D · 0-3.9 = F

**Part B · Writing Health (WH):**
- W-1~W-5 + W-Aux 점수 평균 (0-10)
- 동일 grade 기준

**Toss Compliance Grade (TCG):**
- DPH 와 WH 가중 평균 (DPH 60% + WH 40% — dark pattern 이 토스 가이드 핵심 강조)
- ❌ Part A critical 1건 이상 시 TCG 최대 C 로 캡 (자동 critical = 가이드 명시 금지)
- ❌ Part A critical 3건 이상 시 자동 F

**추가 헤드라인:**
- **Toss Approval Likelihood**: High/Medium/Low (입점 심사 통과 가능성 정성 추정)
- **Top Risk**: 가장 심각한 단일 위반 한 줄 요약

### Step 8 — Finding 작성

위반(❌) 또는 경계(⚠️) 룰마다 finding 1개:

```markdown
### {Rule ID} {Rule Name} — score: {N}
- **severity**: critical | warning | info
- **part**: A · Dark Pattern | B · Writing
- **rule**: {DP-N 또는 W-N} {Rule Name}
- **evidence**: frame `{nodeId}` · {구체 UI 요소·텍스트·위치}
- **toss-guide**: {원문 출처 URL · 해당 섹션}
- **fix**: {구체 수정 방향 + 토스 톤 예시 문구}
```

### Step 9 — 보고서 작성

**파일 경로**: `./design-reviews/design-ux-toss-review-{screen-slug}-{YYYYMMDD-HHmm}.md`

### Step 10 — Top-3 Fix

❌ critical Part A 우선, 동수일 때 Part B ❌ critical, 그 다음 ⚠️ warning 순으로 최대 3개:

각 카드:
- **룰**: {Rule ID + Name}
- **위치**: frame `{nodeId}` · {UI 요소}
- **사용자 영향**: {토스 사용자 신뢰/입점 심사 영향 시나리오}
- **수정 방향**: {구체 변경 + 토스 톤 예시}
- **기대 점수 변화**: {N} → {N'}
- **노력**: Low/Medium/High ({n} weeks)

### Step 11 — 사용자에게 결과 요약

- 보고서 파일 경로
- Toss Compliance Grade + DPH/WH sub-grade
- 10 룰 ✅/❌/⚠️/N/A 현황 표
- critical/warning 개수
- Toss Approval Likelihood
- Top-3 Fix 한 줄 요약
- 다음 액션

### Step 12 — annotate-design 연동 안내

finding 1건 이상이면:
```
리뷰 파일: {경로}
Figma/Pencil 코멘트 패널 부착: /annotate-design {경로}
```

## 보고서 구조 (한국어)

```markdown
# Toss Compliance Review: {화면/flow 이름}

## 메타
- 입력 소스: {Figma URL | .pen path}
- 프레임 ID(s): {nodeId(s)}
- 프레임 이름(s): {frame.name(s)}
- 화면 컨텍스트: {ENTRY/HUB | MID-FLOW | FORM/INPUT | NOTIFICATION/SHEET | HYBRID}
- 서비스 성격: {비즈니스 맥락}
- 실행 모드: {--part both/dp/writing} · {--strict on/off}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 방법론: 토스 「Apps in Toss」 디자인 가이드 (Consumer UX Dark Pattern 5 룰 + UX Writing 5 원칙)
- 참고: https://developers-apps-in-toss.toss.im/design/consumer-ux-guide.html · https://developers-apps-in-toss.toss.im/design/ux-writing.html

## 헤드라인
- **Toss Compliance Grade: {A-F}** ({TCG}/10)
  - Dark Pattern Health: {A-F} ({DPH}/10)
  - Writing Health: {A-F} ({WH}/10)
- **Toss Approval Likelihood**: {High/Medium/Low}
- **Top Risk**: {가장 심각한 단일 위반 한 줄}
- 적용 룰: {applied}/10 (N/A: {na})
- critical: {n}건 · warning: {n}건 · info: {n}건

## First Impression (토스 톤 관점)
- 토스 가이드 부합 첫인상: {...}
- 즉시 위반 의심 요소: {...}
- 가장 거슬리는 부분: {...}
- 한 단어 요약: {...}
- 인상 메모: {...}

## Part A · Dark Pattern 5 룰

| # | Rule | 판정 | 점수 | 비고 |
|---|------|------|------|------|
| DP-1 | 진입 시 즉시 바텀시트 노출 금지 | ✅/❌/⚠️/N/A | - | - |
| DP-2 | 뒤로 가기 시 알림 동의 바텀시트 금지 | ✅/❌/⚠️/N/A | - | - |
| DP-3 | 거절 불가능한 설계 금지 | ✅/❌/⚠️/N/A | - | - |
| DP-4 | 예상 외 전면 광고 노출 금지 | ✅/❌/⚠️/N/A | - | - |
| DP-5 | 모호한 CTA 버튼 금지 | ✅/❌/⚠️/N/A | - | - |

## Part B · UX Writing 5 원칙 + 보조

| # | Rule | 판정 | 점수 | 검출 빈도 |
|---|------|------|------|----------|
| W-1 | 해요체 통일 | ✅/❌/⚠️/N/A | - | 합니다체 {n}건 / 반말 {n}건 |
| W-2 | 능동적 말하기 | ✅/❌/⚠️/N/A | - | 수동 {n}건 |
| W-3 | 긍정적 말하기 | ✅/❌/⚠️/N/A | - | 부정 {n}건 / "취소" 버튼 {n}건 |
| W-4 | 캐주얼한 경어 | ✅/❌/⚠️/N/A | - | '~시' {n}건 / 격식 단어 {n}건 |
| W-5 | 명사 중복 제거 | ✅/❌/⚠️/N/A | - | 3연속 명사 {n}건 |
| W-Aux | "되어요"→"돼요" | ✅/❌/⚠️/N/A | - | "되어요" {n}건 |

## Findings

### {Rule ID} {Rule Name} — score: {N}
- **severity**: critical | warning | info
- **part**: A · Dark Pattern | B · Writing
- **rule**: {Rule ID} {Rule Name}
- **evidence**: frame `{nodeId}` · {UI 요소·텍스트}
- **toss-guide**: {URL · 섹션}
- **fix**: {수정 + 토스 톤 예시 문구}

{위반/경계 룰만 나열}

## Top-3 Fix

### Fix 1 — {Rule ID Rule Name}
- **룰**: {Rule ID + Name}
- **위치**: frame `{nodeId}` · {UI 요소}
- **사용자 영향**: {토스 신뢰/입점 영향 시나리오}
- **수정 방향**: {구체 변경 + 토스 톤 예시}
- **기대 점수 변화**: {N} → {N'}
- **노력**: Low/Medium/High ({n} weeks)

### Fix 2 — ...
### Fix 3 — ...

## N/A 항목 (해당 UI 없음 또는 정적 검증 불가)
- {Rule ID} {Name}: {사유}

## 토스 톤 예시 사전 (참고)

| 안티패턴 | 토스 톤 권장 |
|---------|-------------|
| "결제가 완료되었습니다" | "결제했어요" |
| "오류가 발생하였습니다" | "다시 확인해주세요" |
| "취소" (다이얼로그 버튼) | "닫기" |
| "받으실 수 없습니다" | "받으려면 …필요해요" |
| "확인하세요" | "확인해주세요" |
| "되어요" | "돼요" |
| "결제정보 입력 화면" | "결제 정보를 입력하는 화면" |

## 다음 단계
- Top-3 Fix 즉시 수정 후 재audit
- `/annotate-design {경로}` 로 디자인 파일 코멘트 패널 부착
- Brignull 12 전수 audit 필요 시 `/design-ux-dark-pattern-review`
- 한국어 외 마이크로카피 톤 평가 필요 시 `/design-ux-microcopy-review`
- 입점 심사 직전이면 `--strict` 모드로 재실행 권장
```

## 인자

```
/design-ux-toss-review <Figma URL | .pen path> [--scope "{범위}"] [--part dp|writing|both] [--context "{비즈니스 맥락}"] [--strict]
```

- 위치 인자 1개 필수: Figma URL 또는 .pen 경로
- `--scope`: 특정 영역 집중 (예: `--scope "결제 바텀시트"`)
- `--part`: `dp` (Part A만), `writing` (Part B만), `both` (기본)
- `--context`: 기본값 "토스 입점 미니앱 / 토스 톤 셀러 화면"
- `--strict`: Part B 예외 조항 무시. 모든 수동/부정/'~시' = ❌

## 예시

### 예시 1 — Figma 진입 화면 토스 다크패턴 점검
```
/design-ux-toss-review https://www.figma.com/design/abc/MiniApp?node-id=42-1024 --part dp
```
→ Figma MCP 체크 → 진입 frame 데이터 수집 → 컨텍스트: ENTRY/HUB → DP-1~DP-5 평가 → DP-1(❌ critical, 진입 즉시 광고 바텀시트) + DP-5(⚠️ "확인" 단독 CTA) → DPH D → TCG C (Part A critical 1건 캡) → 보고서 생성

### 예시 2 — Pencil 결제 flow writing 점검 strict
```
/design-ux-toss-review ~/Desktop/projects/design/checkout.pen --part writing --strict
```
→ Pencil MCP 체크 → 3 frame 수집 → 컨텍스트: FORM/INPUT → Part B 전수 평가 → W-1(✅) + W-2(❌ 수동 5건) + W-3(❌ "취소" 버튼 3개) + W-4(⚠️ '~시' 2건) + W-5(✅) + W-Aux(❌ "되어요" 2건) → WH F → 보고서 + 토스 톤 예시 사전 첨부

### 예시 3 — Figma 통합 컴플라이언스 입점 심사 사전 점검
```
/design-ux-toss-review https://www.figma.com/design/abc/SellerApp?node-id=10-200 --context "토스 입점 미니앱 v1"
```
→ Part A + B 전체 평가 → DP 0건 위반 + W-2 1건 ⚠️ → DPH A + WH B → TCG A- (TCG 9.2) → Approval Likelihood: High → 보고서 + Top-3 Fix 1건만

### 예시 4 — Pencil 바텀시트 단독 점검
```
/design-ux-toss-review ~/Documents/notification-sheet.pen --scope "알림 동의 바텀시트"
```
→ DP-1·DP-2·DP-3·DP-5·W-3 집중 → DP-3(❌ 단일 CTA "허용") + W-3(⚠️ "거절") → 즉시 수정 권고

### 예시 5 — MCP 미연결
```
/design-ux-toss-review ~/Documents/myapp.pen
```
→ ToolSearch 결과 0건 → "Pencil MCP 미연결. Pencil 앱 실행 + MCP 연동 활성화 후 재시도." 출력 후 종료

## 출력 규약

- 모든 사용자 대상 텍스트 한국어
- Rule ID (DP-1, W-1 등) 영문 ID 유지 (annotate-design 파싱 호환)
- finding 헤더 포맷 `### {Rule ID} {Rule Name} — score: {N}` 고정
- severity / part / rule / evidence / toss-guide / fix 6 필드 동일 순서
- Part A ❌ = 자동 critical (예외 없음)
- Part B ❌ = critical (W-Aux "되어요" 포함)
- Part B ⚠️ = warning
- N/A 항목은 보고서 말미 별도 기재
- 토스 톤 예시 사전 항상 첨부

## annotate-design 호환성

본 스킬 출력 `.md` 는 `annotate-design` 스킬이 그대로 파싱하여 Figma/Pencil 파일에 코멘트 패널 + 번호 마커 부착. evidence 의 `frame \`{nodeId}\`` 패턴에서 nodeId 추출.

```
/design-ux-toss-review <design 파일> → 리뷰 .md 생성
/annotate-design <리뷰 .md>          → 디자인 파일에 시각 코멘트 부착
```

## 관련 스킬과의 관계

| 항목 | design-ux-toss-review | design-ux-dark-pattern-review | design-ux-microcopy-review |
|------|----------------------|------------------------------|---------------------------|
| 출처 | 토스 가이드 5+5 | Brignull 12 + 규제 | UX writing 8 lens |
| 영역 | DP + 한국어 writing | DP 윤리 전수 | 카피 톤 전반 |
| 규제 매핑 | 없음 (토스 입점 심사 기준) | GDPR/CPRA/한국 e-privacy | 없음 |
| 언어 특화 | 한국어 (해요체·돼요) | 언어 중립 | 한·영 양쪽 |
| 용도 | 토스 입점 심사 사전 | 윤리 audit + 법무 대비 | 일반 마이크로카피 품질 |

세 스킬 보완 관계 — 토스 입점이면 design-ux-toss-review 우선, 글로벌 윤리 audit 은 dark-pattern-review, 일반 마이크로카피 톤은 microcopy-review.

## Non-Goals

- 토스 SDK / 결제 API 통합 검증 — 디자인만
- 디자인 파일에 코멘트 직접 게시 — `annotate-design` 책임
- 자동 카피 재작성 / 디자인 변경 — 리뷰 + 제안만
- 법률 자문 — 토스 입점 심사 결정은 토스 공식 심사팀 권한
- 코드 생성 — 디자인 파일만

## 참고 자료

- **토스 Consumer UX 가이드** — https://developers-apps-in-toss.toss.im/design/consumer-ux-guide.html (다크패턴 5 룰)
- **토스 UX Writing 가이드** — https://developers-apps-in-toss.toss.im/design/ux-writing.html (5 원칙 + 보조)
- **토스 디자인 메인** — https://developers-apps-in-toss.toss.im/design
- **짝 스킬**: `design-ux-dark-pattern-review` (Brignull 12) · `design-ux-microcopy-review` (UX writing 8 lens) · `annotate-design` (finding 시각화)
