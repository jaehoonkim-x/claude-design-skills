# Laws of UX — 평가 Rubric (30개 법칙)

각 법칙별로:
- **정의**: 한 줄 요약
- **정적 검증**: 정적 디자인(스크린샷/노드 트리)에서 검증 가능 여부 (Yes / Partial / N/A)
- **체크리스트**: AI가 평가 시 확인할 구체 항목
- **Severity 가이드**: critical / warning / info 판단 기준
- **링크**: `https://lawsofux.com/{slug}`

> Severity 정의:
> - **critical**: 구조적 위반. 명확한 사용성/접근성 차단.
> - **warning**: 개선 권장. 사용성 저하 위험은 있으나 차단은 아님.
> - **info**: 참고/관찰. 더 나은 선택지가 있을 수 있음.
> - **pass**: 해당 법칙 기준을 충족. (점수표에만 표시)
> - **na**: 정적 디자인에서 검증 불가. (점수표에만 표시)

> 점수표 점수(0-10):
> - 9-10: 모범적
> - 7-8: 양호 (info 1-2개 가능)
> - 5-6: 보통 (warning 1-2개)
> - 3-4: 미흡 (warning 다수 또는 critical 1개)
> - 0-2: 심각 (critical 다수)
> - N/A: 정적 디자인에서 검증 불가 → 점수 자리에 `N/A` + 한 줄 사유

---

## 1. Aesthetic-Usability Effect
- **slug**: `aesthetic-usability-effect`
- **정의**: 미적으로 만족스러운 디자인은 더 사용성이 좋다고 인식됨.
- **정적 검증**: Yes
- **체크리스트**:
  - 시각적 균형(정렬/대칭/여백) 유지되는가?
  - 폰트/컬러/간격에 일관된 디자인 시스템 적용되었는가?
  - 노이즈(불필요 장식, 충돌 컬러, 불정렬) 없는가?
  - 페이지/프레임 첫인상이 잘 다듬어진 느낌인가?
- **Severity 가이드**:
  - critical: 시각적 균형이 명백히 무너짐(겹침, 잘림, 미정렬 다수)
  - warning: 디자인 시스템 외 임의 스타일 사용, 컬러/타이포 충돌
  - info: 마이크로 정렬/마무리 개선 여지
- **링크**: https://lawsofux.com/aesthetic-usability-effect

## 2. Choice Overload
- **slug**: `choice-overload`
- **정의**: 선택지가 많을수록 압도되어 결정이 어려워짐.
- **정적 검증**: Yes
- **체크리스트**:
  - 한 화면의 1차 액션 버튼/링크 개수 ≤ 5 인가?
  - 메뉴/리스트 항목이 7±2 범위를 크게 벗어나지 않는가?
  - 디폴트/추천 선택지가 강조되어 있는가?
- **Severity 가이드**:
  - critical: 단일 뷰에 동등 가중치 액션 10개 이상
  - warning: 디폴트/추천 없는 6-9개 선택지
  - info: 그루핑/카테고리화 여지
- **링크**: https://lawsofux.com/choice-overload

## 3. Chunking
- **slug**: `chunking`
- **정의**: 정보를 의미 있는 단위로 묶으면 인지 부담이 줄어듦.
- **정적 검증**: Yes
- **체크리스트**:
  - 긴 텍스트가 단락/리스트/소제목으로 분할되었는가?
  - 폼 입력 필드가 섹션(개인정보/배송/결제)으로 그룹화되었는가?
  - 전화번호/카드번호처럼 숫자 시퀀스가 시각적으로 청크화되었는가?
- **Severity 가이드**:
  - critical: 10개 이상 폼 필드가 그룹 없이 연속 나열
  - warning: 긴 본문에 시각적 청크 구분 없음
  - info: 청크 사이 간격 조정 여지
- **링크**: https://lawsofux.com/chunking

## 4. Cognitive Bias
- **slug**: `cognitive-bias`
- **정의**: 사고에 영향을 주는 체계적 편향(앵커링, 손실회피 등).
- **정적 검증**: Partial
- **체크리스트**:
  - 가격 표시에 앵커(원가 → 할인가)가 활용되는가?
  - 손실/잔여 강조(예: "3개 남음")가 적절히 사용되는가? (과도하면 다크패턴)
  - 사회적 증명(리뷰/사용자 수)이 신뢰성 있게 노출되는가?
- **Severity 가이드**:
  - critical: 다크패턴(허위 희소성, 강제 동의)
  - warning: 편향 활용이 과해 신뢰 저해 우려
  - info: 편향 활용 여지가 있는데 미사용
- **링크**: https://lawsofux.com/cognitive-bias

## 5. Cognitive Load
- **slug**: `cognitive-load`
- **정의**: 인터페이스 이해/조작에 드는 정신적 자원.
- **정적 검증**: Yes
- **체크리스트**:
  - 1차 정보 위계가 한눈에 들어오는가?
  - 동시에 처리해야 할 시각 요소가 7±2 이하인가?
  - 불필요한 텍스트/아이콘/배지 제거되었는가?
  - 사용자 결정 지점 수가 최소화되었는가?
- **Severity 가이드**:
  - critical: 첫 시야에 우선순위 식별 불가
  - warning: 시각 요소 과밀(20+ 인터랙티브 요소)
  - info: 마이크로 단순화 여지
- **링크**: https://lawsofux.com/cognitive-load

## 6. Doherty Threshold
- **slug**: `doherty-threshold`
- **정의**: 응답이 400ms 이내일 때 생산성 향상.
- **정적 검증**: **N/A** (응답 시간/성능 측정 필요)
- **체크리스트**: (해당 없음)
- **N/A 사유**: 정적 디자인 파일로 응답 시간 측정 불가. 다만 로딩/스켈레톤 UI가 디자인되어 있으면 info 로 별도 기록 가능.
- **링크**: https://lawsofux.com/doherty-threshold

## 7. Fitts's Law
- **slug**: `fittss-law`
- **정의**: 타겟 획득 시간은 거리와 크기의 함수.
- **정적 검증**: Yes
- **체크리스트**:
  - 1차 액션 버튼 최소 터치 영역 ≥ 44×44pt (모바일) / 32×32px (데스크탑)?
  - 인접 인터랙티브 요소 간 간격 ≥ 8px?
  - 자주 쓰는 액션이 화면 엣지/코너/엄지 도달 영역에 위치하는가?
  - 작은 클릭 타겟(아이콘만)에 충분한 hit area 확보되었는가?
- **Severity 가이드**:
  - critical: 1차 액션 < 32×32px 또는 터치 타겟 < 32pt
  - warning: 인접 타겟 간격 < 8px, 또는 잦은 액션이 손가락 도달 어려운 영역
  - info: 마이크로 크기 조정
- **링크**: https://lawsofux.com/fittss-law

## 8. Flow
- **slug**: `flow`
- **정의**: 몰입 상태. 도전과 능력의 균형.
- **정적 검증**: **N/A** (시간/인터랙션 흐름 필요)
- **N/A 사유**: 단일 프레임에서 몰입 상태 평가 불가. 단, 진행률 표시/시각 피드백이 디자인되어 있으면 info 로 메모.
- **링크**: https://lawsofux.com/flow

## 9. Goal-Gradient Effect
- **slug**: `goal-gradient-effect`
- **정의**: 목표에 가까워질수록 동기 증가.
- **정적 검증**: Partial (진행률 UI 가 있는 경우만)
- **체크리스트** (진행률 UI 있을 때):
  - 진행률 바/스텝 인디케이터가 보이는가?
  - 시작 시점에 일부 진행이 이미 채워진(endowed progress) 디자인인가?
  - 남은 스텝 수가 명시되는가?
- **Severity 가이드**:
  - critical: 멀티 스텝 폼인데 진행 표시 전무
  - warning: 진행률이 보이지만 위치/크기가 인지하기 어려움
  - info: endowed progress 적용 여지
- **링크**: https://lawsofux.com/goal-gradient-effect

## 10. Hick's Law
- **slug**: `hicks-law`
- **정의**: 결정 시간은 선택지의 수/복잡도에 비례.
- **정적 검증**: Yes
- **체크리스트**:
  - 동시에 노출된 동등 가중치 선택지 ≤ 5?
  - 카테고리/필터로 선택지가 점진적으로 좁혀지는가?
  - 디폴트값/추천 선택지가 명확한가?
  - 진입 화면에서 메인 액션이 단일하게 식별되는가?
- **Severity 가이드**:
  - critical: 진입 화면에 10+ 동등 액션
  - warning: 카테고리/그루핑 없는 긴 메뉴
  - info: 디폴트/추천 강조 여지
- **링크**: https://lawsofux.com/hicks-law

## 11. Jakob's Law
- **slug**: `jakobs-law`
- **정의**: 사용자는 익숙한 사이트와 같은 방식으로 작동하길 원함.
- **정적 검증**: Yes
- **체크리스트**:
  - 로고 위치(좌상단), 검색(우상단), 카트(우상단), 햄버거 메뉴(좌상단) 등 관행 따르는가?
  - 폼의 라벨/필드/CTA 배치가 익숙한 패턴인가?
  - 아이콘 의미(하트=좋아요, 휴지통=삭제 등)가 통념에 맞는가?
  - 색상 컨벤션(빨강=오류/위험, 초록=성공) 따르는가?
- **Severity 가이드**:
  - critical: 핵심 컴포넌트(내비, CTA, 폼)가 도메인 관행을 완전 위반
  - warning: 아이콘/색상 컨벤션 위반으로 오해 가능성
  - info: 마이크로 패턴 정합성 개선
- **링크**: https://lawsofux.com/jakobs-law

## 12. Law of Common Region
- **slug**: `law-of-common-region`
- **정의**: 공통 경계 안에 있는 요소는 그룹으로 인식.
- **정적 검증**: Yes
- **체크리스트**:
  - 관련 정보가 카드/패널/구분선으로 감싸져 있는가?
  - 무관한 정보가 같은 카드 안에 섞여 있지 않은가?
  - 컨테이너 보더/배경/그림자가 그룹을 명확히 표현하는가?
- **Severity 가이드**:
  - critical: 명확히 다른 도메인의 정보가 같은 카드에 포함
  - warning: 그룹 경계가 모호함(구분선/여백 부족)
  - info: 컨테이너 스타일 일관성 개선
- **링크**: https://lawsofux.com/law-of-common-region

## 13. Law of Proximity
- **slug**: `law-of-proximity`
- **정의**: 가까이 있는 요소는 한 그룹으로 인식.
- **정적 검증**: Yes
- **체크리스트**:
  - 라벨과 입력 필드 간 간격 < 8px (밀접)?
  - 그룹 간 간격이 그룹 내 간격보다 명백히 큰가?
  - 관련 액션 버튼(예: 저장/취소)이 인접 배치되는가?
- **Severity 가이드**:
  - critical: 라벨과 필드가 너무 떨어져 매칭 혼란
  - warning: 그룹 내/외 간격이 비슷해 그룹화 인식 어려움
  - info: 마이크로 간격 조정
- **링크**: https://lawsofux.com/law-of-proximity

## 14. Law of Prägnanz
- **slug**: `law-of-pr%C3%A4gnanz`
- **정의**: 모호한 이미지는 가장 단순한 형태로 지각됨.
- **정적 검증**: Yes
- **체크리스트**:
  - 일러스트/아이콘이 단순하고 인지 가능한 형태인가?
  - 복잡한 도형이 분해 가능한 단순 도형으로 구성되는가?
  - 배경/장식이 메인 콘텐츠를 방해하지 않는가?
- **Severity 가이드**:
  - critical: 핵심 아이콘/일러스트가 의미 불명
  - warning: 장식 요소가 본문 가독성 방해
  - info: 아이콘 단순화 여지
- **링크**: https://lawsofux.com/law-of-pr%C3%A4gnanz

## 15. Law of Similarity
- **slug**: `law-of-similarity`
- **정의**: 유사한 요소는 한 그룹으로 인식.
- **정적 검증**: Yes
- **체크리스트**:
  - 같은 역할 요소(예: 모든 1차 CTA)가 동일 스타일을 공유하는가?
  - 클릭 가능 요소와 비클릭 요소가 시각적으로 구분되는가?
  - 동일 컴포넌트 변형(primary/secondary/destructive)이 일관 스타일인가?
- **Severity 가이드**:
  - critical: 같은 역할 컴포넌트가 화면마다 다른 스타일
  - warning: 클릭 가능/불가 요소 시각 구분 모호
  - info: 컴포넌트 변형 일관성 개선
- **링크**: https://lawsofux.com/law-of-similarity

## 16. Law of Uniform Connectedness
- **slug**: `law-of-uniform-connectedness`
- **정의**: 시각적으로 연결된 요소는 더 관련 있게 보임.
- **정적 검증**: Yes
- **체크리스트**:
  - 관련 요소가 라인/배경/박스로 명시적으로 연결되는가?
  - 메뉴와 그 활성 상태가 시각적으로 연결되는가?
  - 폼 그룹의 라벨-필드-도움말 텍스트가 한 단위로 보이는가?
- **Severity 가이드**:
  - critical: 관련 요소 간 연결성 부재로 페어링 인식 불가
  - warning: 연결성 표현이 약함(미세 보더만)
  - info: 명시적 연결 추가 여지
- **링크**: https://lawsofux.com/law-of-uniform-connectedness

## 17. Mental Model
- **slug**: `mental-model`
- **정의**: 사용자가 시스템 작동에 대해 가진 압축된 이해.
- **정적 검증**: Yes
- **체크리스트**:
  - 인터페이스의 메타포(폴더, 휴지통, 장바구니)가 실제 동작과 일치하는가?
  - 용어/레이블이 사용자 언어(전문 용어 회피)인가?
  - 핵심 액션의 결과가 미리 예측 가능한가?
- **Severity 가이드**:
  - critical: 메타포 위반으로 액션 결과 예측 불가
  - warning: 도메인 전문 용어가 일반 사용자에 불친절
  - info: 레이블 명확화
- **링크**: https://lawsofux.com/mental-model

## 18. Miller's Law
- **slug**: `millers-law`
- **정의**: 평균 작업 기억 용량은 7±2.
- **정적 검증**: Yes
- **체크리스트**:
  - 1차 내비게이션 항목 ≤ 7?
  - 한 화면의 카테고리/탭 수 ≤ 9?
  - 사용자가 동시에 기억해야 할 정보(예: 입력한 값) 항목 ≤ 7?
- **Severity 가이드**:
  - critical: 1차 메뉴/탭 10+ 개
  - warning: 화면 정보가 9개 초과 그룹으로 노출
  - info: 청크화/그룹화 여지
- **링크**: https://lawsofux.com/millers-law

## 19. Occam's Razor
- **slug**: `occams-razor`
- **정의**: 가장 단순한 설명/해결이 최선.
- **정적 검증**: Yes
- **체크리스트**:
  - 같은 목적을 달성하는 더 단순한 디자인 대안이 있는가?
  - 장식적 요소가 핵심 메시지를 가리지 않는가?
  - 화면당 1차 목적이 단일한가?
- **Severity 가이드**:
  - critical: 화면에 동등 목적이 3개 이상 충돌
  - warning: 장식적 요소 과다
  - info: 마이크로 단순화 여지
- **링크**: https://lawsofux.com/occams-razor

## 20. Paradox of the Active User
- **slug**: `paradox-of-the-active-user`
- **정의**: 사용자는 매뉴얼을 읽지 않고 바로 사용함.
- **정적 검증**: Partial (온보딩/툴팁 UI 가 있는 경우)
- **체크리스트**:
  - 핵심 액션이 별도 설명 없이 추측 가능한가?
  - 첫 사용자를 위한 인라인 가이드/툴팁이 있는가?
  - 빈 상태(empty state)가 다음 액션을 안내하는가?
- **Severity 가이드**:
  - critical: 핵심 액션이 매뉴얼 없이는 발견 불가
  - warning: 빈 상태에 가이드 없음
  - info: 툴팁/온보딩 추가 여지
- **링크**: https://lawsofux.com/paradox-of-the-active-user

## 21. Pareto Principle
- **slug**: `pareto-principle`
- **정의**: 약 80%의 효과가 20%의 원인에서 나옴.
- **정적 검증**: Yes
- **체크리스트**:
  - 가장 자주 쓰일 기능(상위 20%)이 시각적 우선순위 1순위에 놓였는가?
  - 부차 기능이 메인 동선을 침범하지 않는가?
  - 사용 빈도 낮은 옵션은 접힘/메뉴 안에 숨겨졌는가?
- **Severity 가이드**:
  - critical: 핵심 기능이 부차 기능에 가려짐
  - warning: 모든 기능이 동등 노출되어 위계 부재
  - info: 사용 빈도 기반 정렬 개선
- **링크**: https://lawsofux.com/pareto-principle

## 22. Parkinson's Law
- **slug**: `parkinsons-law`
- **정의**: 작업은 주어진 시간만큼 늘어남.
- **정적 검증**: **N/A** (시간/태스크 흐름 필요)
- **N/A 사유**: 단일 디자인 프레임으로 작업 시간 평가 불가. 단, 마감 타이머/제한 시간 UI 가 있으면 info.
- **링크**: https://lawsofux.com/parkinsons-law

## 23. Peak-End Rule
- **slug**: `peak-end-rule`
- **정의**: 경험의 평가는 정점과 끝 순간에 좌우됨.
- **정적 검증**: **N/A** (시간적 흐름 필요)
- **N/A 사유**: 단일 프레임에서 정점/종료 순간 평가 불가. 단, 결제 성공/완료 화면이 대상이면 끝점 디자인 별도 평가 가능.
- **링크**: https://lawsofux.com/peak-end-rule

## 24. Postel's Law
- **slug**: `postels-law`
- **정의**: 입력은 관대하게, 출력은 보수적으로.
- **정적 검증**: Partial (폼/입력 UI)
- **체크리스트**:
  - 폼이 다양한 입력 포맷(공백, 하이픈 포함 전화번호 등) 허용하는 듯이 보이는가?
  - 에러 메시지가 명확하고 친화적인가?
  - 입력 힌트/플레이스홀더가 다양한 형식을 안내하는가?
- **Severity 가이드**:
  - critical: 단일 포맷만 허용하는 엄격한 패턴 강요
  - warning: 에러 메시지가 모호함
  - info: 허용 포맷 안내 추가
- **링크**: https://lawsofux.com/postels-law

## 25. Selective Attention
- **slug**: `selective-attention`
- **정의**: 목표 관련 자극에 집중, 나머지 무시.
- **정적 검증**: Yes
- **체크리스트**:
  - 1차 CTA 가 시각적으로 가장 두드러지는가?
  - 사용자가 다음 액션을 자연스럽게 찾을 수 있는가?
  - 광고/프로모션이 핵심 액션을 가리지 않는가?
- **Severity 가이드**:
  - critical: 1차 CTA 가 시각적으로 다른 요소에 묻힘
  - warning: 시각 우선순위 충돌 다수
  - info: 강조 보강 여지
- **링크**: https://lawsofux.com/selective-attention

## 26. Serial Position Effect
- **slug**: `serial-position-effect`
- **정의**: 리스트의 첫 항목과 끝 항목이 가장 잘 기억됨.
- **정적 검증**: Yes
- **체크리스트**:
  - 가장 중요한 메뉴/항목이 리스트의 처음 또는 끝에 위치하는가?
  - 액션 순서(저장/취소)가 관습(우선순위 항목을 끝 또는 강조 위치)에 부합?
  - 핵심 정보가 길 본문의 중간에 묻혀 있지 않은가?
- **Severity 가이드**:
  - critical: 가장 중요한 항목이 중간에 위치해 발견 어려움
  - warning: 강조 위치 활용 부족
  - info: 순서 재배치 여지
- **링크**: https://lawsofux.com/serial-position-effect

## 27. Tesler's Law (Law of Conservation of Complexity)
- **slug**: `teslers-law`
- **정의**: 모든 시스템은 환원 불가능한 최소 복잡도가 있음.
- **정적 검증**: Partial
- **체크리스트**:
  - 시스템의 본질적 복잡도가 사용자 측이 아닌 시스템 측에서 흡수되는가?
  - 입력 양식이 자동 추론/제안으로 사용자 부담을 줄이는가?
  - 디폴트값이 합리적으로 선설정되어 있는가?
- **Severity 가이드**:
  - critical: 시스템이 처리 가능한 일을 사용자에 떠넘김
  - warning: 디폴트 부재로 매번 같은 입력 요구
  - info: 자동 추론 추가 여지
- **링크**: https://lawsofux.com/teslers-law

## 28. Von Restorff Effect
- **slug**: `von-restorff-effect`
- **정의**: 다른 항목과 구별되는 항목이 더 잘 기억됨.
- **정적 검증**: Yes
- **체크리스트**:
  - 1차 CTA 가 컬러/크기/형태로 명백히 구별되는가?
  - 강조 요소가 너무 많아 강조 효과가 분산되지 않는가? (1-2개만 강조)
  - 알림/배지/뱃지가 적정 빈도로 사용되는가?
- **Severity 가이드**:
  - critical: 1차 CTA 가 주변과 시각 구분 없음
  - warning: 강조 요소 과다(3+ 동시 강조)로 효과 분산
  - info: 마이크로 강조 보강
- **링크**: https://lawsofux.com/von-restorff-effect

## 29. Working Memory
- **slug**: `working-memory`
- **정의**: 인지 시스템이 작업 관련 정보를 임시 보관.
- **정적 검증**: Yes
- **체크리스트**:
  - 사용자가 다른 화면으로 이동했다가 돌아와도 컨텍스트가 보존되는가? (예: 입력값, 필터)
  - 멀티 스텝 폼에서 이전 입력값이 시각적으로 보이는가?
  - 핵심 정보가 작업 중 화면에서 사라지지 않는가? (sticky 헤더/요약 등)
- **Severity 가이드**:
  - critical: 멀티 스텝 작업 중 핵심 컨텍스트가 사라짐
  - warning: 입력값 요약이 노출되지 않음
  - info: sticky 영역 추가 여지
- **링크**: https://lawsofux.com/working-memory

## 30. Zeigarnik Effect
- **slug**: `zeigarnik-effect`
- **정의**: 중단된 작업이 완료된 작업보다 더 잘 기억됨.
- **정적 검증**: Partial (진행 상태 UI 가 있는 경우)
- **체크리스트** (해당 UI 있을 때):
  - 미완료 작업(작성 중 폼, 장바구니, 저장된 초안)이 가시적으로 노출되는가?
  - 다음 단계 액션이 강조되어 미완료 상태를 인지하게 하는가?
  - 진행률 인디케이터가 미완료를 알려주는가?
- **Severity 가이드**:
  - critical: 미완료 상태 추적 UI 가 전무
  - warning: 미완료 노출이 약함
  - info: 미완료 강조 보강
- **링크**: https://lawsofux.com/zeigarnik-effect

---

## 사용 가이드

AI는 리뷰 시 위 30개 법칙을 순회한다. 각 법칙마다:

1. **정적 검증**이 `N/A` 인 법칙은 점수표에 `N/A` + 사유 한 줄만 기록하고 finding 섹션은 생성하지 않는다.
2. **정적 검증**이 `Yes` 또는 `Partial` 인 법칙은:
   - 체크리스트 항목을 디자인에 대해 평가
   - 발견된 위반/개선점을 finding 으로 기록 (severity + evidence + fix + 링크)
   - 위반/개선점이 없으면 점수표에 점수만 기록, finding 섹션은 생략
3. 점수는 0-10. 9-10 = 모범, 7-8 = 양호, 5-6 = 보통, 3-4 = 미흡, 0-2 = 심각.
4. evidence 에는 노드 이름(Figma 레이어명 또는 Pencil 노드명)과 노드 트리 경로를 기록.
5. fix 는 한 줄 액션 문구. 예: "1차 CTA 버튼 높이를 36px → 48px 로 증가하여 Fitts's Law 모바일 가이드 충족".

## Top-3 우선순위 산출 규칙

리포트 말미 `## Top-3 우선순위` 섹션은 다음 가중치로 산출:

1. **모든 critical 우선** (severity=critical)
2. critical 이 부족하면 warning 으로 채움
3. 같은 severity 내에서는 다음 우선순위:
   - 사용자가 화면 진입 직후 마주치는 요소
   - 1차 CTA 또는 핵심 컨버전 경로에 위치한 요소
   - 위반 정도(체크리스트 위반 항목 수)
4. 정확히 3개만 (3개 미만이면 그만큼만)
