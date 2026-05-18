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

## 15. Empty / Loading / Error State

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:12,gap:6,fill:"#F8FAFC",cornerRadius:8,alignItems:"center"})
icon=I(ex,{type:"frame",width:36,height:36,fill:"#E2E8F0",cornerRadius:18,alignItems:"center",justifyContent:"center"})
I(icon,{type:"icon_font",iconFontName:"inbox",iconFontFamily:"lucide",width:18,height:18,fill:"#94A3B8"})
I(ex,{type:"text",content:"{empty headline}",fontSize:11,fontWeight:"700",fill:"#0F172A"})
I(ex,{type:"text",content:"{empty body 한 줄}",fontSize:9,fill:"#64748B"})
cta=I(ex,{type:"frame",layout:"horizontal",padding:[4,10,4,10],fill:"#3B82F6",cornerRadius:6})
I(cta,{type:"text",content:"+ {recovery 액션}",fontSize:9,fontWeight:"700",fill:"#FFFFFF"})
```

---

## 16. Primary CTA 추가 — Topbar 미니

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:8,gap:6,fill:"#FFFFFF",cornerRadius:6,stroke:{thickness:1,fill:"#E2E8F0"},alignItems:"center"})
search=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[4,8,4,8],gap:4,fill:"#F8FAFC",cornerRadius:4,alignItems:"center"})
I(search,{type:"icon_font",iconFontName:"search",iconFontFamily:"lucide",width:10,height:10,fill:"#94A3B8"})
I(search,{type:"text",content:"검색...",fontSize:9,fill:"#94A3B8"})
bell=I(ex,{type:"frame",width:24,height:24,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"},alignItems:"center",justifyContent:"center"})
I(bell,{type:"icon_font",iconFontName:"bell",iconFontFamily:"lucide",width:11,height:11,fill:"#64748B"})
av=I(ex,{type:"frame",width:24,height:24,fill:"#3B82F6",cornerRadius:999,alignItems:"center",justifyContent:"center"})
I(av,{type:"text",content:"KJ",fontSize:8,fontWeight:"700",fill:"#FFFFFF"})
cta=I(ex,{type:"frame",layout:"horizontal",padding:[5,10,5,10],fill:"#3B82F6",cornerRadius:5,alignItems:"center"})
I(cta,{type:"text",content:"+ 리포트 내보내기",fontSize:9,fontWeight:"700",fill:"#FFFFFF"})
```

---

## 17. Search Scope + Shortcut

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:8,gap:0,fill:"#FFFFFF",cornerRadius:6,stroke:{thickness:1,fill:"#3B82F6"},alignItems:"center"})
chip=I(ex,{type:"frame",layout:"horizontal",padding:[3,6,3,6],gap:2,fill:"#EFF6FF",cornerRadius:4,alignItems:"center"})
I(chip,{type:"text",content:"주문 ▾",fontSize:9,fontWeight:"700",fill:"#1D4ED8"})
ic=I(ex,{type:"frame",layout:"horizontal",padding:[0,6,0,6]})
I(ic,{type:"icon_font",iconFontName:"search",iconFontFamily:"lucide",width:11,height:11,fill:"#94A3B8"})
I(ex,{type:"text",content:"주문·고객·제품 검색",fontSize:10,fill:"#64748B"})
sp=I(ex,{type:"frame",layout:"horizontal",width:"fill_container"})
kbd=I(ex,{type:"frame",layout:"horizontal",padding:[2,5,2,5],fill:"#F1F5F9",cornerRadius:3,stroke:{thickness:1,fill:"#E2E8F0"}})
I(kbd,{type:"text",content:"⌘K",fontSize:9,fontWeight:"600",fill:"#64748B"})
```

---

## 18. Status Pill — 색 + 라벨 + 아이콘

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
beforeR=I(ex,{type:"frame",layout:"horizontal",gap:4,alignItems:"center"})
I(beforeR,{type:"text",content:"Before",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
b1=I(beforeR,{type:"frame",width:14,height:14,fill:"#DCFCE7",cornerRadius:999})
b2=I(beforeR,{type:"frame",width:14,height:14,fill:"#FEF3C7",cornerRadius:999})
b3=I(beforeR,{type:"frame",width:14,height:14,fill:"#DBEAFE",cornerRadius:999})
b4=I(beforeR,{type:"frame",width:14,height:14,fill:"#FEE2E2",cornerRadius:999})
afterR=I(ex,{type:"frame",layout:"horizontal",gap:4,alignItems:"center",layoutWrap:"WRAP"})
I(afterR,{type:"text",content:"After",fontSize:8,fontWeight:"600",fill:"#10B981"})
a1=I(afterR,{type:"frame",layout:"horizontal",padding:[2,6,2,6],gap:3,fill:"#DCFCE7",cornerRadius:999,alignItems:"center"})
I(a1,{type:"icon_font",iconFontName:"check",iconFontFamily:"lucide",width:9,height:9,fill:"#15803D"})
I(a1,{type:"text",content:"완료",fontSize:9,fontWeight:"700",fill:"#15803D"})
a2=I(afterR,{type:"frame",layout:"horizontal",padding:[2,6,2,6],gap:3,fill:"#FEF3C7",cornerRadius:999,alignItems:"center"})
I(a2,{type:"icon_font",iconFontName:"clock",iconFontFamily:"lucide",width:9,height:9,fill:"#B45309"})
I(a2,{type:"text",content:"대기",fontSize:9,fontWeight:"700",fill:"#B45309"})
a3=I(afterR,{type:"frame",layout:"horizontal",padding:[2,6,2,6],gap:3,fill:"#FEE2E2",cornerRadius:999,alignItems:"center"})
I(a3,{type:"icon_font",iconFontName:"x",iconFontFamily:"lucide",width:9,height:9,fill:"#B91C1C"})
I(a3,{type:"text",content:"환불",fontSize:9,fontWeight:"700",fill:"#B91C1C"})
```

---

## 19. Table 효율 컨트롤 — sort + checkbox + 페이지네이션

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:4,fill:"#F8FAFC",cornerRadius:8})
head=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[4,6,4,6],gap:6,fill:"#FFFFFF",cornerRadius:3,stroke:{thickness:1,fill:"#E2E8F0"},alignItems:"center"})
cb=I(head,{type:"frame",width:10,height:10,fill:"#FFFFFF",cornerRadius:2,stroke:{thickness:1,fill:"#94A3B8"}})
I(head,{type:"text",content:"주문 ID ▲",fontSize:9,fontWeight:"700",fill:"#0F172A"})
I(head,{type:"text",content:"고객 ▼",fontSize:9,fontWeight:"500",fill:"#64748B"})
I(head,{type:"text",content:"금액 ▼",fontSize:9,fontWeight:"500",fill:"#64748B"})
r1=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[4,6,4,6],gap:6,fill:"#FFFFFF",cornerRadius:3,alignItems:"center"})
I(r1,{type:"frame",width:10,height:10,fill:"#3B82F6",cornerRadius:2})
I(r1,{type:"text",content:"#ORD-1284",fontSize:9,fill:"#0F172A"})
I(r1,{type:"text",content:"김민지",fontSize:9,fill:"#64748B"})
I(r1,{type:"text",content:"₩48K",fontSize:9,fill:"#0F172A"})
pag=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",gap:4,alignItems:"center",justifyContent:"end"})
I(pag,{type:"text",content:"1-5 of 1,284",fontSize:8,fill:"#64748B"})
b1=I(pag,{type:"frame",width:14,height:14,fill:"#3B82F6",cornerRadius:3,alignItems:"center",justifyContent:"center"})
I(b1,{type:"text",content:"1",fontSize:8,fontWeight:"700",fill:"#FFFFFF"})
b2=I(pag,{type:"frame",width:14,height:14,fill:"#FFFFFF",cornerRadius:3,stroke:{thickness:1,fill:"#E2E8F0"},alignItems:"center",justifyContent:"center"})
I(b2,{type:"text",content:"2",fontSize:8,fill:"#64748B"})
```

---

## 20. Notification Badge

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:8,fill:"#F8FAFC",cornerRadius:8,alignItems:"center"})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:4,alignItems:"center"})
I(before,{type:"text",content:"Before",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
bb=I(before,{type:"frame",width:28,height:28,fill:"#FFFFFF",cornerRadius:6,stroke:{thickness:1,fill:"#E2E8F0"},alignItems:"center",justifyContent:"center"})
I(bb,{type:"icon_font",iconFontName:"bell",iconFontFamily:"lucide",width:14,height:14,fill:"#64748B"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:4,alignItems:"center"})
I(after,{type:"text",content:"After",fontSize:8,fontWeight:"600",fill:"#10B981"})
ab=I(after,{type:"frame",width:28,height:28,fill:"#FFFFFF",cornerRadius:6,stroke:{thickness:1,fill:"#E2E8F0"},alignItems:"center",justifyContent:"center"})
I(ab,{type:"icon_font",iconFontName:"bell",iconFontFamily:"lucide",width:14,height:14,fill:"#64748B"})
dot=I(ab,{type:"frame",width:12,height:12,fill:"#EF4444",cornerRadius:999,alignItems:"center",justifyContent:"center"})
I(dot,{type:"text",content:"3",fontSize:8,fontWeight:"800",fill:"#FFFFFF"})
```

---

## 21. WCAG 대비

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(before,{type:"text",content:"Before · 2.85:1 fail",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
I(before,{type:"text",content:"vs 지난주",fontSize:11,fill:"#CBD5E1"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(after,{type:"text",content:"After · 5.74:1 pass",fontSize:8,fontWeight:"600",fill:"#10B981"})
I(after,{type:"text",content:"vs 지난주",fontSize:11,fontWeight:"500",fill:"#475569"})
```

---

## 22. Token Contract — variable 호출

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#FCA5A5"}})
I(before,{type:"text",content:"Before · hardcoded",fontSize:8,fontWeight:"700",fill:"#B91C1C"})
I(before,{type:"text",content:"fill: #3B82F6",fontSize:10,fontWeight:"500",fill:"#0F172A",fontFamily:"monospace"})
I(before,{type:"text",content:"font: Inter",fontSize:10,fontWeight:"500",fill:"#0F172A",fontFamily:"monospace"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:2,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#86EFAC"}})
I(after,{type:"text",content:"After · variables",fontSize:8,fontWeight:"700",fill:"#15803D"})
I(after,{type:"text",content:"fill: $brand",fontSize:10,fontWeight:"500",fill:"#0F172A",fontFamily:"monospace"})
I(after,{type:"text",content:"font: $font-sans",fontSize:10,fontWeight:"500",fill:"#0F172A",fontFamily:"monospace"})
```

---

## 23. 도메인 KPI — First-class KPI

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:4,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#FCA5A5"}})
I(before,{type:"text",content:"Generic",fontSize:8,fontWeight:"700",fill:"#B91C1C"})
I(before,{type:"text",content:"전체 사용자",fontSize:9,fontWeight:"500",fill:"#64748B"})
I(before,{type:"text",content:"24,521",fontSize:14,fontWeight:"800",fill:"#0F172A"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:4,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:2,fill:"#3B82F6"}})
I(after,{type:"text",content:"Domain ★",fontSize:8,fontWeight:"700",fill:"#1D4ED8"})
I(after,{type:"text",content:"광고전환 순이익",fontSize:9,fontWeight:"700",fill:"#1D4ED8"})
I(after,{type:"text",content:"-128,400원",fontSize:14,fontWeight:"800",fill:"#B91C1C"})
```

---

## 24. KPI Sparkline / Baseline

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:10,gap:4,fill:"#F8FAFC",cornerRadius:8})
card=I(ex,{type:"frame",layout:"vertical",width:"fill_container",padding:8,gap:3,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(card,{type:"text",content:"매출",fontSize:9,fontWeight:"500",fill:"#64748B"})
I(card,{type:"text",content:"₩48.2M",fontSize:14,fontWeight:"800",fill:"#0F172A"})
spark=I(card,{type:"frame",layout:"horizontal",width:"fill_container",height:12,gap:2,alignItems:"end"})
I(spark,{type:"frame",width:4,height:4,fill:"#93C5FD",cornerRadius:1})
I(spark,{type:"frame",width:4,height:6,fill:"#93C5FD",cornerRadius:1})
I(spark,{type:"frame",width:4,height:5,fill:"#93C5FD",cornerRadius:1})
I(spark,{type:"frame",width:4,height:9,fill:"#3B82F6",cornerRadius:1})
I(spark,{type:"frame",width:4,height:7,fill:"#3B82F6",cornerRadius:1})
I(spark,{type:"frame",width:4,height:11,fill:"#1D4ED8",cornerRadius:1})
I(spark,{type:"frame",width:4,height:8,fill:"#3B82F6",cornerRadius:1})
base=I(card,{type:"frame",layout:"horizontal",gap:4,alignItems:"center"})
I(base,{type:"text",content:"+8.2%",fontSize:9,fontWeight:"700",fill:"#15803D"})
I(base,{type:"text",content:"vs 지난주 ₩44.6M · 목표 92%",fontSize:8,fill:"#94A3B8"})
```

---

## 25. Chart Context — y축 + 단위 + 툴팁

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
yax=I(ex,{type:"frame",layout:"vertical",width:24,height:60,gap:0,justifyContent:"space_between",alignItems:"end"})
I(yax,{type:"text",content:"60M",fontSize:7,fill:"#94A3B8"})
I(yax,{type:"text",content:"40M",fontSize:7,fill:"#94A3B8"})
I(yax,{type:"text",content:"20M",fontSize:7,fill:"#94A3B8"})
I(yax,{type:"text",content:"0",fontSize:7,fill:"#94A3B8"})
plot=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:2})
bars=I(plot,{type:"frame",layout:"horizontal",width:"fill_container",height:50,gap:3,alignItems:"end"})
I(bars,{type:"frame",width:"fill_container",height:25,fill:"#93C5FD",cornerRadius:2})
I(bars,{type:"frame",width:"fill_container",height:32,fill:"#93C5FD",cornerRadius:2})
I(bars,{type:"frame",width:"fill_container",height:18,fill:"#93C5FD",cornerRadius:2})
I(bars,{type:"frame",width:"fill_container",height:42,fill:"#1D4ED8",cornerRadius:2})
I(bars,{type:"frame",width:"fill_container",height:28,fill:"#93C5FD",cornerRadius:2})
xax=I(plot,{type:"frame",layout:"horizontal",width:"fill_container",gap:3,justifyContent:"space_between"})
I(xax,{type:"text",content:"월",fontSize:7,fill:"#94A3B8"})
I(xax,{type:"text",content:"화",fontSize:7,fill:"#94A3B8"})
I(xax,{type:"text",content:"수",fontSize:7,fill:"#94A3B8"})
I(xax,{type:"text",content:"목",fontSize:7,fontWeight:"700",fill:"#0F172A"})
I(xax,{type:"text",content:"금",fontSize:7,fill:"#94A3B8"})
tip=I(plot,{type:"frame",layout:"vertical",padding:[3,6,3,6],fill:"#0F172A",cornerRadius:3})
I(tip,{type:"text",content:"목 · ₩12.4M",fontSize:8,fontWeight:"600",fill:"#FFFFFF"})
```

---

## 26. Sidebar IA + Nav Badge

```javascript
ex=I(parentCard,{type:"frame",layout:"vertical",width:"fill_container",height:"fit_content",padding:8,gap:3,fill:"#0F172A",cornerRadius:8})
n1=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[4,8,4,8],gap:6,fill:"#1E293B",cornerRadius:4,alignItems:"center"})
I(n1,{type:"icon_font",iconFontName:"layout-dashboard",iconFontFamily:"lucide",width:11,height:11,fill:"#FFFFFF"})
I(n1,{type:"text",content:"정산현황",fontSize:10,fontWeight:"700",fill:"#FFFFFF"})
n2=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[4,8,4,8],gap:6,alignItems:"center"})
I(n2,{type:"icon_font",iconFontName:"chart-column",iconFontFamily:"lucide",width:11,height:11,fill:"#94A3B8"})
I(n2,{type:"text",content:"광고비 내역",fontSize:10,fontWeight:"500",fill:"#CBD5E1"})
sp=I(n2,{type:"frame",layout:"horizontal",width:"fill_container"})
b2=I(n2,{type:"frame",width:14,height:14,fill:"#EF4444",cornerRadius:999,alignItems:"center",justifyContent:"center"})
I(b2,{type:"text",content:"3",fontSize:7,fontWeight:"800",fill:"#FFFFFF"})
n3=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:[4,8,4,8],gap:6,alignItems:"center"})
I(n3,{type:"icon_font",iconFontName:"truck",iconFontFamily:"lucide",width:11,height:11,fill:"#94A3B8"})
I(n3,{type:"text",content:"밀크런",fontSize:10,fontWeight:"500",fill:"#CBD5E1"})
```

---

## 27. Touch Target — 44px 보강

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:10,fill:"#F8FAFC",cornerRadius:8,alignItems:"center"})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:3,alignItems:"center"})
I(before,{type:"text",content:"Before · 35h",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
bch=I(before,{type:"frame",layout:"horizontal",padding:[3,6,3,6],fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(bch,{type:"text",content:"필터",fontSize:9,fill:"#0F172A"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:3,alignItems:"center"})
I(after,{type:"text",content:"After · 44h",fontSize:8,fontWeight:"600",fill:"#10B981"})
ach=I(after,{type:"frame",layout:"horizontal",padding:[10,14,10,14],fill:"#FFFFFF",cornerRadius:6,stroke:{thickness:1,fill:"#3B82F6"}})
I(ach,{type:"text",content:"필터",fontSize:10,fontWeight:"700",fill:"#1D4ED8"})
```

---

## 28. Card Elevation — Stroke vs Shadow

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:10,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:4})
I(before,{type:"text",content:"Before",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
bc=I(before,{type:"frame",layout:"vertical",padding:8,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#E2E8F0"}})
I(bc,{type:"text",content:"flat",fontSize:9,fill:"#64748B"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:4})
I(after,{type:"text",content:"After · shadow",fontSize:8,fontWeight:"600",fill:"#10B981"})
ac=I(after,{type:"frame",layout:"vertical",padding:8,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#F1F5F9"},dropShadow:{offsetY:1,blur:3,color:"#0F172A14"}})
I(ac,{type:"text",content:"elevated",fontSize:9,fontWeight:"500",fill:"#0F172A"})
```

---

## 29. Avatar Initial

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:10,fill:"#F8FAFC",cornerRadius:8,alignItems:"center",justifyContent:"center"})
before=I(ex,{type:"frame",width:32,height:32,fill:"#3B82F6",cornerRadius:999})
arrow=I(ex,{type:"text",content:"→",fontSize:14,fontWeight:"700",fill:"#94A3B8"})
after=I(ex,{type:"frame",width:32,height:32,fill:"#3B82F6",cornerRadius:999,alignItems:"center",justifyContent:"center"})
I(after,{type:"text",content:"KJ",fontSize:11,fontWeight:"700",fill:"#FFFFFF"})
```

---

## 30. Tabular Nums

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:10,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:2,alignItems:"end"})
I(before,{type:"text",content:"Before",fontSize:8,fontWeight:"600",fill:"#94A3B8"})
I(before,{type:"text",content:"24,521",fontSize:13,fontWeight:"700",fill:"#0F172A"})
I(before,{type:"text",content:"1,284",fontSize:13,fontWeight:"700",fill:"#0F172A"})
I(before,{type:"text",content:"₩48.2M",fontSize:13,fontWeight:"700",fill:"#0F172A"})
after=I(ex,{type:"frame",layout:"vertical",width:"fill_container",gap:2,alignItems:"end"})
I(after,{type:"text",content:"After · tnum",fontSize:8,fontWeight:"600",fill:"#10B981"})
I(after,{type:"text",content:"24,521",fontSize:13,fontWeight:"700",fill:"#0F172A",fontFeatureSettings:"tnum"})
I(after,{type:"text",content:" 1,284",fontSize:13,fontWeight:"700",fill:"#0F172A",fontFeatureSettings:"tnum"})
I(after,{type:"text",content:"₩48.2M",fontSize:13,fontWeight:"700",fill:"#0F172A",fontFeatureSettings:"tnum"})
```

---

## 31. Responsive — Sidebar Collapsed

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:6,fill:"#F8FAFC",cornerRadius:8})
exp=I(ex,{type:"frame",layout:"vertical",width:80,padding:6,gap:3,fill:"#0F172A",cornerRadius:4})
I(exp,{type:"text",content:"240w",fontSize:7,fontWeight:"600",fill:"#94A3B8"})
e1=I(exp,{type:"frame",layout:"horizontal",gap:4,alignItems:"center"})
I(e1,{type:"icon_font",iconFontName:"layout-dashboard",iconFontFamily:"lucide",width:10,height:10,fill:"#FFFFFF"})
I(e1,{type:"text",content:"대시보드",fontSize:9,fontWeight:"700",fill:"#FFFFFF"})
e2=I(exp,{type:"frame",layout:"horizontal",gap:4,alignItems:"center"})
I(e2,{type:"icon_font",iconFontName:"users",iconFontFamily:"lucide",width:10,height:10,fill:"#94A3B8"})
I(e2,{type:"text",content:"고객",fontSize:9,fill:"#CBD5E1"})
col=I(ex,{type:"frame",layout:"vertical",width:36,padding:6,gap:6,fill:"#0F172A",cornerRadius:4,alignItems:"center"})
I(col,{type:"text",content:"64w",fontSize:7,fontWeight:"600",fill:"#94A3B8"})
I(col,{type:"icon_font",iconFontName:"layout-dashboard",iconFontFamily:"lucide",width:14,height:14,fill:"#FFFFFF"})
I(col,{type:"icon_font",iconFontName:"users",iconFontFamily:"lucide",width:14,height:14,fill:"#94A3B8"})
```

---

## 32. Brand / Identity Swap

```javascript
ex=I(parentCard,{type:"frame",layout:"horizontal",width:"fill_container",height:"fit_content",padding:10,gap:10,fill:"#F8FAFC",cornerRadius:8})
before=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:8,gap:4,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#FCA5A5"},alignItems:"center"})
bsq=I(before,{type:"frame",width:14,height:14,fill:"#3B82F6",cornerRadius:3})
I(before,{type:"text",content:"Acme",fontSize:11,fontWeight:"700",fill:"#0F172A"})
after=I(ex,{type:"frame",layout:"horizontal",width:"fill_container",padding:8,gap:4,fill:"#FFFFFF",cornerRadius:4,stroke:{thickness:1,fill:"#86EFAC"},alignItems:"center"})
asq=I(after,{type:"frame",width:14,height:14,fill:"#3182F6",cornerRadius:4})
I(after,{type:"text",content:"STATSY",fontSize:11,fontWeight:"800",fill:"#191F28"})
```

---

## 매핑 우선순위

1. **법칙명 / 패턴명 정확 일치** (예: "Fitts's Law", "Empty/Loading/Error", "Search scope") → 해당 패턴 사용
2. **법칙명 키워드 매칭** (예: "Cognitive Bias / 접근성" → Cognitive Bias 패턴)
3. **fix/title 키워드 매칭** (예: "padding 보강" → Fitts, "툴팁" → Paradox, "변수 호출" → Token Contract)
4. **가장 가까운 패턴 적용** (컬러/공간/타입/컴포넌트/상태/인터랙션 중 어느 축인지 식별 후 카탈로그 중 1개 선택)

**텍스트 2줄 폴백 금지**. 카탈로그에 없으면 가장 가까운 패턴을 변형해 적용한다. mockup 안에는 항상 최소 1개 시각 요소(frame fill / chip / 아이콘 / 미니 input / 비교 박스 등) 포함.

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
