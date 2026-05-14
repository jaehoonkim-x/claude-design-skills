# Nielsen Heuristics — 평가 Rubric (10개 휴리스틱)

각 휴리스틱별로:
- **정의**: Nielsen Norman Group 의 공식 정의 한 줄 요약
- **정적 검증**: 정적 디자인(스크린샷/노드 트리)에서 검증 가능 여부 (Yes / Partial / N/A)
- **체크리스트**: AI가 평가 시 확인할 구체 항목
- **Common Violations**: 자주 발견되는 위반 패턴
- **Severity 가이드**: catastrophic / major / minor / cosmetic 판단 기준
- **링크**: `https://www.nngroup.com/articles/ten-usability-heuristics/#{slug}`

> Severity 정의:
> - **catastrophic** (critical): 작업 완료 불가, 데이터 손실, 보안 이슈. 출시 전 필수 수정.
> - **major** (critical): 핵심 태스크에 빈번한 문제, 사용자 좌절. 높은 우선순위.
> - **minor** (warning): 부차 기능 또는 가끔 불편. 중간 우선순위.
> - **cosmetic** (info): 기능 영향 없음. 여유 시 수정.
> - **pass**: 해당 휴리스틱 기준을 충족. (점수표에만 표시)
> - **na**: 정적 디자인에서 검증 불가. (점수표에만 표시)

> 점수표 점수(0-10):
> - 9-10: 모범적 (positive example 있음)
> - 7-8: 양호 (cosmetic 1-2개 가능)
> - 5-6: 보통 (minor 1-2개 또는 major 1개)
> - 3-4: 미흡 (major 다수 또는 catastrophic 1개)
> - 0-2: 심각 (catastrophic 다수)
> - N/A: 정적 디자인에서 검증 불가 → 점수 자리에 `N/A` + 한 줄 사유

---

## H1. Visibility of System Status
- **slug**: `visibility-of-system-status`
- **정의**: 디자인은 항상 적절한 시간 내 적절한 피드백으로 사용자에게 무슨 일이 일어나는지 알려야 한다.
- **정적 검증**: Partial (현재 상태 표시 UI 는 검증 가능, 실시간 피드백 타이밍은 N/A)
- **체크리스트**:
  - 현재 위치 표시 (breadcrumb / active nav / page title)?
  - 선택/활성/비활성/hover 상태 시각화 (있다면)?
  - 진행률 표시 (multi-step form, upload, checkout)?
  - 폼 제출 후 확인 메시지/스크린 디자인 존재?
  - 백그라운드 작업 상태 표시 (notification, badge)?
  - 로딩/skeleton 상태 디자인 존재?
- **Common Violations**:
  - 액션 후 피드백 없음
  - 현재 페이지/섹션 불명확
  - multi-step 진행률 부재
  - 로딩 인디케이터 미디자인
- **Severity 가이드**:
  - catastrophic: 결제/저장 등 critical 액션 후 확인 없음 → 사용자가 중복 시도 → 데이터 손상 가능
  - major: 현재 위치 모호, 진행률 부재로 사용자가 길을 잃음
  - minor: hover/active 상태가 약함
  - cosmetic: 트랜지션 미세 조정
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#visibility-of-system-status

---

## H2. Match Between System and the Real World
- **slug**: `match-system-real-world`
- **정의**: 디자인은 사용자의 언어를 써야 한다. 친숙한 단어/구문/개념을 사용하고 실세계 관행을 따라야 한다.
- **정적 검증**: Yes
- **체크리스트**:
  - 모든 텍스트가 평이한 사용자 언어인가 (기술 용어/내부 jargon 없음)?
  - 아이콘이 보편적 메타포 (집=홈, 톱니=설정, 돋보기=검색) 사용?
  - 정보 순서가 사용자의 멘탈 모델 따름 (예: 주소 = 국가→시도→상세, 한국식)?
  - 날짜/시간/통화 형식이 로케일 적합?
  - 산업 표준 용어 사용 (예: "장바구니" vs "Cart Repository")?
  - 에러/안내 메시지가 한국어 자연어?
- **Common Violations**:
  - 기술적 에러 메시지 ("ERR_403_FORBIDDEN")
  - 개발자/내부 용어 노출 ("Entity", "Resource", "ID")
  - 라벨 없는 unfamiliar 아이콘
  - 영문/한글 혼용 비일관
- **Severity 가이드**:
  - catastrophic: 핵심 액션 라벨이 사용자가 이해 불가
  - major: 다수 jargon, 메타포 부적합
  - minor: 일부 일관성 결여 (영문/한글 혼용)
  - cosmetic: 마이크로카피 톤 조정
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#match-system-real-world

---

## H3. User Control and Freedom
- **slug**: `user-control-and-freedom`
- **정의**: 사용자는 실수로 액션을 수행한다. 추가 절차 없이 원치 않는 액션에서 빠져나갈 수 있는 명확한 "비상구"가 필요하다.
- **정적 검증**: Partial (취소/뒤로/닫기 버튼 존재 검증 가능, undo 동작은 N/A)
- **체크리스트**:
  - 모달/오버레이에 닫기(X) 버튼 또는 ESC 안내?
  - 다단계 폼에 뒤로/취소 버튼 매 단계 존재?
  - destructive 액션에 undo 옵션 또는 확인 단계?
  - 네비게이션 back 경로 명확?
  - "내 정보 수정 중 저장 안 하고 나가기" 같은 emergency exit?
- **Common Violations**:
  - 모달 트랩 (닫기 버튼 없음)
  - 다단계 플로우 뒤로가기 불가
  - 강제 완료 (skip 옵션 없음)
  - destructive 액션 undo 부재
- **Severity 가이드**:
  - catastrophic: destructive 액션 (계정 삭제, 결제) 중단 불가
  - major: 다단계 플로우 중간 이탈 불가
  - minor: 모달 ESC 미지원 (X 버튼은 있음)
  - cosmetic: 취소 버튼 위치 부자연
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#user-control-and-freedom

---

## H4. Consistency and Standards
- **slug**: `consistency-and-standards`
- **정의**: 사용자는 다른 단어/상황/액션이 같은 의미인지 의심하지 않아야 한다. 플랫폼과 산업 관행을 따라라.
- **정적 검증**: Yes
- **체크리스트**:
  - 같은 액션을 가리키는 용어가 일관 (예: "저장" vs "Save" vs "Submit")?
  - 1차/2차 버튼 스타일이 화면 전체 일관?
  - 동일 컴포넌트 (카드, 입력 필드)가 동일 시각 패턴?
  - 플랫폼 관행 준수 (iOS HIG / Material / Web)?
  - 디자인 시스템 토큰 (컬러, spacing, typo) 일관 적용?
  - 아이콘 사용 일관 (같은 아이콘 = 같은 의미)?
  - 로고/네비/CTA 위치 화면별 일관?
- **Common Violations**:
  - 동일 액션을 다른 단어로 표현
  - 버튼 스타일 비일관
  - 동일 정보 패턴 다른 레이아웃
  - 플랫폼 관행 위반
- **Severity 가이드**:
  - catastrophic: 핵심 액션이 화면마다 다른 위치/스타일 → 사용자 혼동
  - major: 디자인 시스템 외 임의 스타일 다수
  - minor: 마이크로 일관성 결여 (radius 한두 곳 다름)
  - cosmetic: spacing 미세 차이
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#consistency-and-standards

---

## H5. Error Prevention
- **slug**: `error-prevention`
- **정의**: 좋은 에러 메시지보다 더 좋은 것은 에러를 처음부터 막는 디자인이다.
- **정적 검증**: Yes
- **체크리스트**:
  - 입력 필드에 형식 가이드 (placeholder, mask, helper text)?
  - 입력 제약 시각화 (max length, allowed chars)?
  - destructive 액션에 확인 다이얼로그 디자인?
  - 자동 저장 indicator 또는 draft 상태 표시?
  - 비활성 상태 (disabled) 가 invalid 입력 차단?
  - smart default 값 제공 (예: 오늘 날짜, 가장 흔한 선택지)?
  - 비파괴 vs 파괴 액션의 시각 위계 차이?
- **Common Violations**:
  - 제출 시점까지 validation 없음
  - destructive 액션 즉시 실행
  - invalid 입력 허용
  - 위험 작업 경고 부재
- **Severity 가이드**:
  - catastrophic: 데이터 손실 가능 액션 확인 없음 (계정 삭제, 결제, bulk delete)
  - major: 폼 제출 후 통째로 에러 (필드별 검증 부재)
  - minor: placeholder 부재 / helper text 부재
  - cosmetic: 입력 형식 hint 위치
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#error-prevention

---

## H6. Recognition Rather Than Recall
- **slug**: `recognition-rather-than-recall`
- **정의**: 사용자의 기억 부담을 최소화하라. 요소/액션/옵션을 보이게 만들어 사용자가 한 부분에서 다른 부분의 정보를 기억할 필요가 없게 하라.
- **정적 검증**: Yes
- **체크리스트**:
  - 메뉴/네비가 항상 visible (hamburger 만 의존하지 않음)?
  - 입력 필드에 autocomplete/suggestion 디자인?
  - 최근 사용 항목 / 자주 쓰는 항목 표시?
  - 아이콘에 라벨 (또는 tooltip) 동반?
  - 필요한 정보가 사용 시점에 가까이 표시 (다른 화면 기억 강요 X)?
  - 폼에 필드 라벨 영구 표시 (placeholder-only 아님)?
  - 인증 코드/주문 번호 등 복사 가능?
- **Common Violations**:
  - 라벨 없는 아이콘만 사용
  - 모바일에서 햄버거 메뉴만 노출
  - placeholder 가 라벨 대체
  - 정보가 한 번 보이고 사라짐
- **Severity 가이드**:
  - catastrophic: 핵심 액션이 숨겨져 발견 불가
  - major: 라벨 없는 아이콘 다수, placeholder-only 폼
  - minor: tooltip 부재
  - cosmetic: 보조 정보 위치
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#recognition-rather-than-recall

---

## H7. Flexibility and Efficiency of Use
- **slug**: `flexibility-and-efficiency-of-use`
- **정의**: 단축키 같은 가속기는 초보자에게는 보이지 않지만 전문가 사용자의 인터랙션을 빠르게 한다. 디자인은 양쪽 모두를 만족시켜야 한다.
- **정적 검증**: Partial (단축키 표시, bulk action UI, 필터 UI 는 검증 가능)
- **체크리스트**:
  - 키보드 단축키 hint 표시 (메뉴, 툴팁)?
  - bulk action UI (다중 선택 → 일괄 처리)?
  - 고급 필터/검색 옵션?
  - 사용자 customization (즐겨찾기, 핀, 정렬)?
  - 빠른 액션 (swipe, right-click, hover action)?
  - personalization (최근 / 추천 / 저장된 검색)?
- **Common Violations**:
  - one-size-fits-all 접근
  - 키보드 네비 미지원
  - 반복 작업 단축 없음
  - workflow customization 없음
- **Severity 가이드**:
  - catastrophic: 핵심 power-user 작업이 불가능할 정도로 비효율
  - major: bulk action 부재로 반복 클릭 강요
  - minor: 단축키 hint 부재
  - cosmetic: 가속기 발견성 개선
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#flexibility-and-efficiency-of-use

---

## H8. Aesthetic and Minimalist Design
- **slug**: `aesthetic-and-minimalist-design`
- **정의**: 인터페이스는 관련 없거나 거의 필요 없는 정보를 포함해서는 안 된다. 추가 정보는 관련 정보와 경쟁하여 가시성을 떨어뜨린다.
- **정적 검증**: Yes
- **체크리스트**:
  - 깔끔하고 비혼잡한 레이아웃?
  - progressive disclosure (필요 시 노출, 평소 숨김)?
  - 적절한 여백 (cramped 느낌 X)?
  - 시각 위계 명확 (focal point 단일)?
  - 1차 액션이 시각적으로 두드러짐?
  - 불필요 장식 (장식 SVG, 의미 없는 일러스트) 제거?
  - 정보 밀도가 콘텐츠 타입에 적합?
- **Common Violations**:
  - 정보 과부하
  - 한 화면에 너무 많은 옵션
  - 시각적 노이즈
  - 약한 시각 위계
  - 산만한 장식 요소
- **Severity 가이드**:
  - catastrophic: 핵심 메시지가 노이즈에 묻혀 전달 실패
  - major: 시각 위계 부재로 1차 액션 불명확
  - minor: 일부 섹션 cramped
  - cosmetic: 여백 미세 조정
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#aesthetic-and-minimalist-design

---

## H9. Help Users Recognize, Diagnose, and Recover from Errors
- **slug**: `help-users-recognize-diagnose-and-recover-from-errors`
- **정의**: 에러 메시지는 평이한 언어로 표현하고(에러 코드 없이), 정확히 문제를 지적하며, 건설적으로 해결책을 제시해야 한다.
- **정적 검증**: Partial (에러 상태 프레임이 있을 때만 검증, 없으면 N/A)
- **체크리스트**:
  - 에러 메시지가 사용자 언어 (코드 노출 X)?
  - 문제를 구체적으로 지적 ("이메일 형식이 잘못되었습니다" > "Invalid input")?
  - 해결 액션 제시 ("예: name@example.com")?
  - 인라인 validation (필드 옆 즉시 표시)?
  - 에러 상태 시각화 (color + icon, color-only X)?
  - 복구 옵션 (다시 시도, 도움말, 지원 연락)?
  - 404 / 500 페이지 디자인?
- **Common Violations**:
  - 제네릭 에러 ("Error 500", "Something went wrong")
  - 에러 코드만 노출
  - 해결 가이드 없음
  - 인라인 검증 부재
- **Severity 가이드**:
  - catastrophic: 결제/주문 실패 시 복구 경로 없음
  - major: 에러 코드만 표시, 해결 가이드 부재
  - minor: 메시지 톤 개선 여지
  - cosmetic: 에러 아이콘 위치
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#error-recovery

---

## H10. Help and Documentation
- **slug**: `help-and-documentation`
- **정의**: 추가 설명 없이도 시스템이 사용 가능한 것이 가장 좋다. 그러나 사용자가 태스크를 완료할 수 있도록 도움 문서가 필요할 수 있다.
- **정적 검증**: Partial (인앱 도움말 UI / tooltip / onboarding 디자인 검증 가능)
- **체크리스트**:
  - contextual help (필드 옆 ? 아이콘, tooltip)?
  - 첫 사용 onboarding 또는 empty state 가이드?
  - 도움말 검색 가능?
  - FAQ 또는 도움말 페이지 진입점?
  - 지원 연락처 (chat, email) 명시?
  - in-app guidance (coach mark, walkthrough)?
  - empty state 가 액션 가이드?
- **Common Violations**:
  - 도움말 없음
  - 도움말이 일반적 (태스크 맥락 없음)
  - empty state 가 정보만 (액션 안내 부재)
  - onboarding 부재
- **Severity 가이드**:
  - catastrophic: 핵심 기능 사용법 안내 부재로 사용 불가
  - major: 신규 사용자 onboarding 부재
  - minor: contextual tooltip 부재
  - cosmetic: 도움말 진입점 위치
- **링크**: https://www.nngroup.com/articles/ten-usability-heuristics/#help-and-documentation

---

## Cross-Heuristic Analysis 가이드

여러 휴리스틱이 동일 이슈로 위반되는 패턴이 자주 발견된다. 분석 시 다음 조합 주의:

| 패턴 | 동시 위반 휴리스틱 |
|------|-------------------|
| 폼 validation 부재 | H1 (피드백) + H5 (예방) + H9 (복구) |
| 라벨 없는 아이콘 다수 | H2 (실세계) + H6 (인식) |
| 모달 트랩 | H3 (통제) + H1 (가시성) |
| 정보 과부하 + 시각 위계 부재 | H8 (미니멀) + H1 (가시성) |
| 디자인 시스템 외 임의 스타일 | H4 (일관성) + H8 (미적) |

동시 위반 발견 시 root cause 1개로 묶어 fix 제안. 단, 각 휴리스틱 점수에는 모두 반영.

---

## Top-3 우선순위 산정 규칙

1. **catastrophic 우선** — severity catastrophic 인 finding 부터 채움
2. **catastrophic 부족하면 major 로 채움** — major 중 동일 이슈가 여러 휴리스틱 위반 시 우선
3. **진입 직후 마주치는 요소 우선** — hero, 첫 화면, 1차 CTA 관련 finding
4. **위반 항목 수 많은 휴리스틱 우선** — 한 휴리스틱에 finding 다수면 systemic issue

Top-3 형식:
```
1. **H{N} {휴리스틱명} ({severity})** — {evidence 한 줄}. {fix 한 줄}.
```
