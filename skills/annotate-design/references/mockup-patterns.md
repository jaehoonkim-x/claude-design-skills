# Mockup Patterns — finding 별 After 예시 생성 카탈로그

각 법칙(또는 fix 패턴)마다 코멘트 카드 안에 삽입할 mockup 구조 정의.

기본 컨테이너:
```
exContainer (frame name:"Ex{N}" layout:vertical width:fill_container height:fit_content padding:10 gap:8 fill:#F8FAFC cornerRadius:8 stroke:{thickness:1, fill:#E2E8F0})
```

mockup 폰트 사이즈: 8-13px 범위 (실제 디자인보다 작게 → mockup 임을 시각 구분)

---

## 1. Fitts's Law — Before/After 버튼 비교

```javascript
ex=I(parentCard,{type:"frame",name:"Ex",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8,stroke:{thickness:1,fill:"#E2E8F0"}})
before=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",gap:8,alignItems:"center"})
beforeL=I(before,{type:"text",content:"Before",fontSize:9,fontWeight:"600",fill:"#94A3B8"})
// 작은 버튼 (padding 부족)
bBtn=I(before,{type:"text",content:"{버튼라벨}",fontSize:11,fontWeight:"600",fill:"#3B82F6"})
after=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",gap:8,alignItems:"center"})
afterL=I(after,{type:"text",content:"After",fontSize:9,fontWeight:"600",fill:"#10B981"})
// 큰 버튼 (padding 보강)
aBtnFrame=I(after,{type:"frame",layout:"horizontal",padding:[10,14,10,14],fill:"#EFF6FF",cornerRadius:6})
aBtnText=I(aBtnFrame,{type:"text",content:"{버튼라벨}",fontSize:11,fontWeight:"600",fill:"#1D4ED8"})
```

---

## 2. Selective Attention — KPI 강조 + CTA

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8})
// CTA 추가
top=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",justifyContent:"end"})
cta=I(top,{type:"frame",layout:"horizontal",padding:[4,8,4,8],fill:"#3B82F6",cornerRadius:6})
ctaT=I(cta,{type:"text",content:"+ {1차 액션}",fontSize:9,fontWeight:"700",fill:"#FFFFFF"})
// KPI 4종, 중간 1개만 액센트
row=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",gap:4,alignItems:"end"})
k1=I(row,{type:"frame",layout:"vertical",width:"fill_container",padding:6,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(k1,{type:"text",content:"KPI1",fontSize:8,fill:"#64748B"})
I(k1,{type:"text",content:"값",fontSize:11,fontWeight:"700",fill:"#0F172A"})
k2=I(row,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:2,fill:"#EFF6FF",cornerRadius:4,stroke:{thickness:2,fill:"#3B82F6"}})
I(k2,{type:"text",content:"{핵심KPI} ★",fontSize:9,fontWeight:"700",fill:"#1D4ED8"})
I(k2,{type:"text",content:"값",fontSize:13,fontWeight:"800",fill:"#0F172A"})
k3=I(row,{type:"frame",layout:"vertical",width:"fill_container",padding:6,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(k3,{type:"text",content:"KPI3",fontSize:8,fill:"#64748B"})
I(k3,{type:"text",content:"값",fontSize:11,fontWeight:"700",fill:"#0F172A"})
k4=I(row,{type:"frame",layout:"vertical",width:"fill_container",padding:6,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(k4,{type:"text",content:"KPI4",fontSize:8,fill:"#64748B"})
I(k4,{type:"text",content:"값",fontSize:11,fontWeight:"700",fill:"#0F172A"})
```

---

## 3. Paradox of the Active User — 라벨 ⓘ + 툴팁

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8})
card=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:10,gap:4,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
head=I(card,{type:"frame",layout:"horizontal",width:"fit_content",gap:4,alignItems:"center"})
I(head,{type:"text",content:"{KPI 라벨}",fontSize:10,fontWeight:"500",fill:"#64748B"})
I(head,{type:"icon_font",iconFontName:"info",iconFontFamily:"lucide",width:11,height:11,fill:"#94A3B8"})
I(card,{type:"text",content:"{KPI 값}",fontSize:14,fontWeight:"700",fill:"#0F172A"})
tip=I(ex,{type:"frame",layout:"horizontal",padding:[6,10,6,10],fill:"#0F172A",cornerRadius:4})
I(tip,{type:"text",content:"{KPI 정의 한 줄}",fontSize:9,fontWeight:"500",fill:"#FFFFFF"})
```

---

## 4. Aesthetic-Usability — Before/After 텍스트 weight

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:2})
I(before,{type:"text",content:"Before · weight {기존}",fontSize:9,fontWeight:"600",fill:"#94A3B8"})
I(before,{type:"text",content:"{샘플 텍스트}",fontSize:11,fontWeight:"{기존}",fill:"#64748B"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:2})
I(after,{type:"text",content:"After · weight {제안}",fontSize:9,fontWeight:"600",fill:"#10B981"})
I(after,{type:"text",content:"{샘플 텍스트}",fontSize:11,fontWeight:"{제안}",fill:"#64748B"})
```

---

## 5. Cognitive Bias / 접근성 — 변화율 칩

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8})
row=I(ex,{type:"frame",layout:"horizontal",width:"fit_content",gap:10,alignItems:"center"})
pos=I(row,{type:"frame",layout:"horizontal",padding:[3,8,3,8],gap:3,fill:"#DCFCE7",cornerRadius:999,alignItems:"center"})
I(pos,{type:"icon_font",iconFontName:"arrow-up",iconFontFamily:"lucide",width:11,height:11,fill:"#15803D"})
I(pos,{type:"text",content:"+12.5%",fontSize:11,fontWeight:"800",fill:"#15803D"})
neg=I(row,{type:"frame",layout:"horizontal",padding:[3,8,3,8],gap:3,fill:"#FEE2E2",cornerRadius:999,alignItems:"center"})
I(neg,{type:"icon_font",iconFontName:"arrow-down",iconFontFamily:"lucide",width:11,height:11,fill:"#B91C1C"})
I(neg,{type:"text",content:"−2.1%",fontSize:11,fontWeight:"600",fill:"#B91C1C",underline:true})
I(ex,{type:"text",content:"아이콘 + 굵기/밑줄로 색 의존 해제",fontSize:9,fill:"#94A3B8"})
```

---

## 6. Cognitive Load — Before/After 명도

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(before,{type:"text",content:"Before",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
I(before,{type:"text",content:"{라벨}",fontSize:11,fontWeight:"500",fill:"#64748B"})
I(before,{type:"text",content:"{값}",fontSize:14,fontWeight:"700",fill:"#0F172A"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:6,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(after,{type:"text",content:"After",fontSize:8,fontWeight:"600",fill:"#10B981"})
I(after,{type:"text",content:"{라벨}",fontSize:10,fontWeight:"500",fill:"#94A3B8"})
I(after,{type:"text",content:"{값}",fontSize:14,fontWeight:"700",fill:"#0F172A"})
```

---

## 7. Von Restorff Effect — 사이드바 활성 액센트

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#0F172A",cornerRadius:8})
active=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[6,10,6,10],gap:8,alignItems:"center",fill:"#1E40AF40",cornerRadius:4,stroke:{thickness:{left:4},fill:"#3B82F6"}})
I(active,{type:"icon_font",iconFontName:"layout-dashboard",iconFontFamily:"lucide",width:12,height:12,fill:"#FFFFFF"})
I(active,{type:"text",content:"{활성 메뉴명}",fontSize:11,fontWeight:"700",fill:"#FFFFFF"})
inactive=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[6,10,6,10],gap:8,alignItems:"center"})
I(inactive,{type:"icon_font",iconFontName:"users",iconFontFamily:"lucide",width:12,height:12,fill:"#94A3B8"})
I(inactive,{type:"text",content:"{다른 메뉴}",fontSize:11,fontWeight:"500",fill:"#94A3B8"})
```

---

## 8. Jakob's Law — 위치 관행 비교

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8})
// Before: 비관행
before=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",height:32,padding:[4,8,4,8],fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#FCA5A5"},justifyContent:"end",alignItems:"center"})
I(before,{type:"text",content:"{요소명}",fontSize:10,fontWeight:"600",fill:"#0F172A"})
// After: 관행
after=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",height:32,padding:[4,8,4,8],fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#86EFAC"},alignItems:"center"})
I(after,{type:"text",content:"{요소명}",fontSize:10,fontWeight:"600",fill:"#0F172A"})
I(ex,{type:"text",content:"Before(우) → After(좌) · 표준 위치 적용",fontSize:9,fill:"#94A3B8"})
```

---

## 9. Hick's Law — 메뉴 정리

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8})
// Before: 평면 긴 리스트
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:6,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(before,{type:"text",content:"Before",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
{"옵션1","옵션2","옵션3","옵션4","옵션5","옵션6","옵션7","옵션8"}.forEach 로 표시 — 실제 코드는 8회 I() 호출
// After: 카테고리화
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:6,gap:4,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(after,{type:"text",content:"After · 그룹화",fontSize:8,fontWeight:"600",fill:"#10B981"})
g1=I(after,{type:"frame",layout:"vertical",width:"fill_container",gap:2})
I(g1,{type:"text",content:"▾ 그룹 A",fontSize:9,fontWeight:"600",fill:"#0F172A"})
I(g1,{type:"text",content:"  옵션1·2·3",fontSize:9,fill:"#64748B"})
g2=I(after,{type:"frame",layout:"vertical",width:"fill_container",gap:2})
I(g2,{type:"text",content:"▸ 그룹 B (3)",fontSize:9,fontWeight:"600",fill:"#0F172A"})
```

---

## 10. Choice Overload — 추천 강조

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
rec=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[6,10,6,10],gap:8,alignItems:"center",fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:2,fill:"#3B82F6"}})
recBadge=I(rec,{type:"frame",layout:"horizontal",padding:[2,6,2,6],fill:"#DBEAFE",cornerRadius:999})
I(recBadge,{type:"text",content:"추천",fontSize:9,fontWeight:"700",fill:"#1D4ED8"})
I(rec,{type:"text",content:"{추천 옵션}",fontSize:11,fontWeight:"700",fill:"#0F172A"})
oth1=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[4,10,4,10],fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(oth1,{type:"text",content:"{기타1}",fontSize:10,fontWeight:"500",fill:"#64748B"})
oth2=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[4,10,4,10],fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(oth2,{type:"text",content:"{기타2}",fontSize:10,fontWeight:"500",fill:"#64748B"})
```

---

## 11. Miller's Law — 7±2 청크화

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
I(ex,{type:"text",content:"숫자 시퀀스 청크화",fontSize:9,fontWeight:"600",fill:"#94A3B8"})
I(ex,{type:"text",content:"Before: 01012345678",fontSize:11,fill:"#64748B"})
I(ex,{type:"text",content:"After: 010 1234 5678",fontSize:11,fontWeight:"600",fill:"#0F172A",letterSpacing:1})
```

---

## 12. Common Region / Proximity / Similarity — 그룹화 비교

공통 패턴: Before(경계 없음/멀리 떨어짐/제각각 스타일) vs After(카드/근접/동일 스타일).

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:8})
I(before,{type:"text",content:"Before",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
// Before: 그룹 경계 모호
I(before,{type:"text",content:"항목 1",fontSize:10,fill:"#0F172A"})
I(before,{type:"text",content:"항목 2",fontSize:10,fill:"#0F172A"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:4,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#3B82F6"}})
I(after,{type:"text",content:"After · 공통 경계",fontSize:8,fontWeight:"600",fill:"#10B981"})
I(after,{type:"text",content:"항목 1",fontSize:10,fill:"#0F172A"})
I(after,{type:"text",content:"항목 2",fontSize:10,fill:"#0F172A"})
```

---

## 13. Postel's Law — 입력 허용 안내

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
input=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(input,{type:"text",content:"전화번호",fontSize:9,fontWeight:"500",fill:"#64748B"})
I(input,{type:"text",content:"010-1234-5678",fontSize:11,fontWeight:"500",fill:"#0F172A"})
I(input,{type:"text",content:"하이픈 / 공백 / 숫자만 — 모두 허용",fontSize:8,fontWeight:"400",fill:"#94A3B8"})
```

---

## 14. Tesler's Law — 기본값 자동화

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
input=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(input,{type:"text",content:"국가",fontSize:9,fontWeight:"500",fill:"#64748B"})
I(input,{type:"text",content:"대한민국 (자동 감지)",fontSize:11,fontWeight:"500",fill:"#0F172A"})
I(input,{type:"text",content:"IP 기반 합리적 기본값",fontSize:8,fill:"#94A3B8"})
```

---

## 폴백 — 매핑되지 않는 fix

위 패턴에 정확히 매핑되지 않는 fix 텍스트는 다음 간단한 Before/After 텍스트 박스로 폴백:

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
I(ex,{type:"text",content:"Before",fontSize:9,fontWeight:"600",fill:"#94A3B8"})
I(ex,{type:"text",content:"{현재 상태 요약}",fontSize:11,fill:"#64748B",textGrowth:"fixed-width",width:"fill_container",lineHeight:1.4})
I(ex,{type:"text",content:"After",fontSize:9,fontWeight:"600",fill:"#10B981"})
I(ex,{type:"text",content:"{fix 텍스트 첫 줄}",fontSize:11,fontWeight:"500",fill:"#0F172A",textGrowth:"fixed-width",width:"fill_container",lineHeight:1.4})
```

---

## 매핑 우선순위

1. **법칙명 정확 일치** (예: "Fitts's Law") → 해당 패턴 사용
2. **법칙명 키워드 매칭** (예: "Cognitive Bias / 접근성" → Cognitive Bias 패턴)
3. **fix 텍스트 키워드 매칭** (예: "padding 보강" → Fitts 패턴, "툴팁" → Paradox 패턴, "범례" → Cognitive Bias 패턴)
4. **폴백** (Before/After 텍스트 박스)

## 공통 가이드

- mockup 의 텍스트 라벨은 finding 의 `fix` 또는 `evidence` 에서 핵심 키워드를 그대로 가져온다 (사용자가 자기 디자인과 mockup 을 즉시 연결 가능)
- 색상은 디자인 시스템 토큰이 있으면 그것을 따르되, 없으면 본 카탈로그의 hex 사용
- 모든 mockup 은 reusable component 가 아니라 1회용 ad-hoc 인스턴스 — 코멘트 카드에 직접 삽입

## 향후 확장

다음 패턴 추가 후보:
- Working Memory (sticky header)
- Pareto Principle (히트맵 시각화)
- Serial Position Effect (리스트 순서 비교)
- Mental Model (메타포 충돌 표시)
