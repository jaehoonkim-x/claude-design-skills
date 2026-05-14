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

1. **evidence 에 nodeId 없음**: targetNodeIds 빈 배열 → 마커 생략, 코멘트 패널 카드만 생성
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
