# Findings Parser — 입력 .md 포맷 명세

`annotate-design` 이 입력 .md 를 파싱할 때 따르는 규약. `design-{ux,ui}-{rubric}-review` 패밀리 (10개) 출력과 일치.

## 전체 구조

```markdown
# Laws of UX 리뷰: {프레임명}

## 메타
- 입력 소스: {path 또는 URL}
- 프레임 ID: `{nodeId}`
- 프레임 이름: {이름}
- 프레임 크기: {W} × {H}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 스크린샷: {경로 또는 메모}

## 종합 점수
- 전체 평균: {avg}/10
- critical: {n}건
- warning: {n}건
- info: {n}건
- 검증 적용 법칙: {applied}/{total} (N/A: {na})

## 점수표 (...)
| ... 점수표 (스킵 가능) ... |

## Findings

### {법칙명} — score: {N}
- **severity**: critical|warning|info
- **evidence**:
  - `{ParentName} > {ChildName}` (`{nodeId}`): 추가 설명
  - 추가 evidence 라인 (선택)
- **fix**:
  1. fix 액션 1
  2. fix 액션 2
  자유 텍스트 가능
- **참고**: https://lawsofux.com/{slug}

(... 반복 ...)

## Top-3 우선순위
1. **{법칙명} ({severity})** — 한 줄 요약
2. ...
3. ...

## N/A 항목 (검증 보류)
- ...
```

## 파싱 토큰

### 메타 추출
- 정규식: `^- 입력 소스: (.+)$` → 1그룹 = 디자인 파일 경로/URL
- `^- 프레임 ID: \`([^`]+)\`` → nodeId
- `^- 프레임 이름: (.+)$` → 프레임명
- `^- 리뷰 일시: (.+)$` → 타임스탬프

### 종합 점수 추출
- `^- 전체 평균: ([\d.]+)/10`
- `^- critical: (\d+)건`
- `^- warning: (\d+)건`
- `^- info: (\d+)건`

### Findings 블록 추출

전체 Findings 영역: `## Findings\n` 부터 다음 `^## ` 헤더 직전까지.

각 finding 시작:
```
### {law} — score: {score}
```
정규식: `^### (.+?) — score: ([\d.]+)$` → law, score

finding 블록 내부 라인:
- `- **severity**: (critical|warning|info)` → severity
- `- **evidence**:` 다음의 들여쓰기 라인(`  - ` 또는 본문)들 → evidence 배열
  - 각 evidence 라인에서 `` `([A-Za-z0-9_]+)` `` 패턴 추출 → 그 finding 의 target nodeId 들
- `- **fix**:` 다음의 들여쓰기 라인 + 번호 매김 라인(`  1.`, `  2.`) → fix 텍스트(원문 그대로 보존)
- `- **참고**: (https?://\S+)` → 링크

다음 finding 시작(`^### `) 또는 다음 섹션 헤더(`^## `) 직전까지가 한 finding 범위.

### Top-3 추출 (선택)

`## Top-3 우선순위` 블록에서 `^(\d+)\. \*\*(.+?) \((critical|warning|info)\)\*\* — (.+)$` 으로 순위/법칙/severity/요약 추출.

순위에 따른 코멘트 카드 정렬 가능 (default: 마크다운 출현 순서).

## 산출 데이터 구조

```typescript
interface ParsedReview {
  meta: {
    title: string;          // "Laws of UX 리뷰: Dashboard"
    designSource: string;   // "./test.pen" 또는 figma URL
    frameId: string;        // "lNsTZ"
    frameName: string;      // "Dashboard"
    timestamp: string;      // "2026-05-14 12:30 KST"
  };
  summary: {
    average: number;        // 7.4
    critical: number;
    warning: number;
    info: number;
  };
  findings: Finding[];
  top3?: Top3Item[];
}

interface Finding {
  law: string;              // "Selective Attention"
  score: number;            // 5
  severity: "critical" | "warning" | "info";
  evidence: string;         // 원본 텍스트(노드 ID 포함)
  targetNodeIds: string[];  // ["ZIsOt"] (evidence 에서 추출)
  fix: string;              // 원본 fix 텍스트(번호 매김 포함)
  link: string;             // "https://lawsofux.com/..."
  number?: number;          // 출현 순서 또는 top3 순위
}

interface Top3Item {
  rank: number;
  law: string;
  severity: string;
  summary: string;
}
```

## 에지 케이스

1. **evidence 에 nodeId 없음**: targetNodeIds 빈 배열 → 카드 Target 줄은 자연어 요약만 표기 (이 스킬은 노드 위 마커를 생성하지 않으므로 nodeId 자체가 카드 출력에 영향 없음)
2. **fix 가 비어 있음**: mockup 폴백 (Before/After 라벨만, 본문은 "fix 미정")
3. **severity 누락**: `info` 로 폴백 + 경고 메시지
4. **링크 누락**: 카드의 Link 필드 생략
5. **법칙명에 슬래시 포함**: 그대로 유지 (예: `Cognitive Bias / 접근성`)
6. **score 가 정수가 아님 (예: 7.5)**: float 그대로 표시

## 비-finding 섹션

다음 섹션은 무시:
- `## 점수표 (...)`
- `## N/A 항목 (검증 보류)`
- `## Top-3 우선순위` (선택적 활용)

`## Findings` 외 다른 헤더는 finding 으로 해석하지 않는다.

---

## Aggregate Mode — design-review-all 집계 .md 입력

`design-review-all` 스킬이 생성하는 단일 집계 .md 도 입력으로 받을 수 있다. 개별 review .md 와 구조가 달라 별도 파서 분기 필요.

### 모드 감지

다음 중 **하나라도 참**이면 집계 모드:

1. 파일명이 `design-review-all-*.md` 패턴
2. 본문에 `^## 통합 finding 목록` 헤더 존재
3. 본문에 `^### HIGH \(`, `^### MID \(`, `^### LOW \(` 헤더 중 하나 이상 존재

집계 모드 감지 시 개별 모드 파서를 사용하지 않는다.

### 집계 .md 전체 구조 (요약)

```markdown
# Design Review All — Aggregate Report

## 메타
- 입력 소스: {path 또는 URL}
- 프레임: {nodeId / frame.name}
- 리뷰 일시: {YYYY-MM-DD HH:mm KST}
- 실행 스킬: {N}/11
- 원본 finding 수: {raw}건 → dedupe 후 {unique}건 (병합률 {pct}%)

## 레벨별 종합 헤드라인
(테이블 — 파싱 제외, 카드 카운트용 메타만 활용 가능)

## 통합 finding 목록 (dedupe + source tag)

### HIGH ({n}건)
1. [HIGH][{title}] {요약 한 줄} [{src1}][{src2}]
2. ...

### MID ({n}건)
1. [MID][{title}] {요약} [{src1}]

### LOW ({n}건)
1. [LOW][{title}] {요약} [{src1}]

## 중복도 Top 5
(테이블 — 파싱 제외)

## 개별 보고서 링크
- L0 UI:
  - {경로}
  ...
```

### 통합 finding 라인 정규식

```
^(\d+)\.\s+\[(HIGH|MID|LOW)\]\[([^\]]+)\]\s+(.+?)\s+((?:\[[^\]]+\])+)\s*$
```

캡처 그룹:

1. `number` — severity 섹션 안 1-based 번호
2. `severityCode` — `HIGH | MID | LOW`
3. `title` — finding 항목명 (예: `Fitts's Law`, `Visual Hierarchy`)
4. `summary` — evidence/fix 통합 한 줄 요약 (raw text, 마지막 source tag 직전까지)
5. `sourcesRaw` — 연속된 `[src]` 토큰들 (예: `[ui-critic][ui-lawsofux][ceo]`)

`sourcesRaw` 에서 `\[([^\]]+)\]` 반복 매칭으로 source 배열 추출.

### severity 역매핑

집계 .md 의 `HIGH/MID/LOW` 는 원본 severity 의 통합 표기. 카드 색상 매핑 시 원본 severity 로 환원:

| 집계 코드 | 원본 severity | 카드 색 |
|----------|--------------|--------|
| HIGH | critical | #DC2626 / bg #FECACA / dark #B91C1C |
| MID | warning | #F59E0B / bg #FEF3C7 / dark #B45309 |
| LOW | info | #3B82F6 / bg #DBEAFE / dark #1D4ED8 |

### 섹션 헤더 처리

`^### (HIGH|MID|LOW) \((\d+)건\)` 으로 섹션 시작 감지 후, 다음 `^### ` 또는 `^## ` 직전까지를 해당 severity 의 finding 영역.

### Aggregate Finding 데이터 구조

```typescript
interface AggregateFinding {
  number: number;           // 섹션 안 1-based
  severityCode: "HIGH" | "MID" | "LOW";
  severity: "critical" | "warning" | "info"; // 역매핑
  title: string;            // "Fitts's Law"
  summary: string;          // 한 줄 요약 (evidence + fix 통합)
  sources: string[];        // ["ui-critic","ui-lawsofux","ceo"] — 알파벳순
  globalIndex: number;      // 전체 finding 안 출현 순서 (1..total)
}

interface AggregateReview {
  meta: {
    title: string;          // "Design Review All — Aggregate Report"
    designSource: string;   // 입력 소스
    frameLabel: string;     // "{nodeId} / {frame.name}"
    timestamp: string;
    rawCount?: number;      // 원본 finding 수
    uniqueCount?: number;   // dedupe 후 수
  };
  findings: AggregateFinding[]; // HIGH → MID → LOW 순으로 누적
}
```

### 카드 출력 매핑

- 카드 1장 = AggregateFinding 1건
- 카드 Head 에 `severity chip` + `점수 표기 자리` 대신 **source chip 들** 표시 (severity bg 와 동일 톤, 작은 폰트 8-9px)
- Title = `title`
- Body = `summary` 그대로 표시 (이미 한 줄 요약이므로 추가 가공 불요)
- evidence/fix 분리된 본문은 없으므로 `Target:` 줄 생략 가능 → "출처:" 라인이 그 자리를 대신
- 참고 링크는 집계 .md 에 없음 → Link 필드 생략

### 에지 케이스

1. **source 토큰 0개**: 라인 매칭 실패 → 스킵 + 경고
2. **summary 안에 `[xxx]` 같은 대괄호 포함**: 마지막 연속 `[src]` 토큰 그룹만 source 로 인식. 정규식의 lazy `(.+?)` 가 가장 짧게 매칭하므로 source 가 항상 끝.
3. **severity 섹션 누락 (HIGH 만 있고 MID/LOW 없음)**: 정상. 없는 섹션은 그냥 건너뜀.
4. **번호 중복 (HIGH 1, MID 1, LOW 1)**: 정상. `globalIndex` 로 전체 번호 매김 가능.

## 모드 분기 요약

| 입력 .md | 감지 신호 | 파서 | 출력 |
|---------|----------|-----|------|
| 개별 review (`lawsofux-*` 등) | `## Findings` 헤더 | 위 "Findings 블록 추출" 규약 | severity/evidence/fix/link 카드 |
| 집계 (`design-review-all-*`) | `## 통합 finding 목록` 헤더 | Aggregate Mode 규약 | severity/summary/sources 카드 |
