# 03_DESIGN_SYSTEM.md
# 타임아카이브 — Design System

> 두 시안(다크룸/아카이브)을 하나의 테마 토큰 시스템으로 관리합니다.

---

## 1. 테마 토큰 (theme.js)

```js
// 시안 A — 다크룸
export const THEME_DARKROOM = {
  name: "darkroom",
  bg: "#0D0D0F",          // 메인 배경
  bgAlt: "#15131A",       // 서브 배경
  surface: "#1A1820",     // 카드 배경
  text: "#D4D2CC",        // 메인 텍스트
  textDim: "rgba(212,210,204,0.65)",
  accent: "#C8483C",      // safelight red (액센트)
  accentSoft: "rgba(200,72,60,0.15)",
  gold: "#C9A84C",        // 서브 포인트
  line: "rgba(212,210,204,0.12)",
  lightBg: "#15131A",     // 다크 섹션 내 대비용
  lightText: "#D4D2CC",
  lightTextDim: "rgba(212,210,204,0.6)",
  lightSurface: "#1F1C26",
  lightLine: "rgba(212,210,204,0.1)",
  fontDisplay: "'Pretendard', -apple-system, sans-serif",
  fontBody: "'Pretendard', -apple-system, 'Apple SD Gothic Neo', sans-serif",
  displayWeight: 800,
  radius: "2px",
  eyebrowTransform: "uppercase",
  eyebrowSpacing: "0.3em",
};

// 시안 B — 아카이브
export const THEME_ARCHIVE = {
  name: "archive",
  bg: "#EDEAE3",          // 종이 배경
  bgAlt: "#E4E0D6",
  surface: "#FFFFFF",
  text: "#1A1815",        // 잉크 블랙
  textDim: "rgba(26,24,21,0.6)",
  accent: "#2C4A47",      // deep teal (액센트)
  accentSoft: "rgba(44,74,71,0.1)",
  gold: "#9A7B4F",        // sepia (서브 포인트)
  line: "rgba(26,24,21,0.12)",
  lightBg: "#1A1815",     // 어두운 섹션용
  lightText: "#EDEAE3",
  lightTextDim: "rgba(237,234,227,0.6)",
  lightSurface: "#252019",
  lightLine: "rgba(237,234,227,0.12)",
  fontDisplay: "'Noto Serif KR', 'Nanum Myeongjo', Georgia, serif",
  fontBody: "'Pretendard', -apple-system, 'Apple SD Gothic Neo', sans-serif",
  displayWeight: 700,
  radius: "0px",
  eyebrowTransform: "none",
  eyebrowSpacing: "0.15em",
};
```

---

## 2. 타이포그래피

| 역할 | 다크룸 | 아카이브 |
|---|---|---|
| Display | Pretendard 800 | Noto Serif KR 700 |
| Headline | Pretendard 700 | Noto Serif KR 700 |
| Body | Pretendard 400 | Pretendard 400 |
| Eyebrow | uppercase + 0.3em | italic + 0.15em |

**폰트 CDN:**
```html
<!-- Pretendard (공통) -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css">
<!-- Noto Serif KR (시안 B만) -->
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@500;700&display=swap" rel="stylesheet">
```

---

## 3. 14개 섹션 순서 (확정)

```
1.  TopBanner        띠배너 (개강 공지 + 닫기)
2.  Hero             풀스크린 + 핵심 메시지
3.  GalleryShowcase  카테고리 회전 쇼케이스 (Hero 직후)
4.  TrustBar         1999 · 1:1 · 100%
5.  MosaicPortfolio  12장 모자이크 그리드
6.  Instructor       강사 소개 (27년 + 1:1 직강)
7.  InterviewVideos  수료생 인터뷰 영상 3종
8.  WhyNow           사진업계 변화 3가지
9.  Curriculum       기초→심화 2트랙 토글
10. InstaGallery     인스타그램 자동 피드
11. ForYou           타겟별 카드 3종
12. Consult          1:1 상담 신청 폼
13. FAQ              탭 + 아코디언 (SAPPA 벤치마킹)
14. NoticeBoard      개강·모집 공지
15. Footer           + 플로팅 CTA
```

---

## 4. 공통 컴포넌트

### Eyebrow
```jsx
<span style={{
  color: t.gold, fontSize: 13, fontWeight: 600,
  letterSpacing: t.eyebrowSpacing,
  textTransform: t.eyebrowTransform,
  fontStyle: t.name === "archive" ? "italic" : "normal",
  fontFamily: t.name === "archive" ? t.fontDisplay : t.fontBody,
}}>{children}</span>
```

### useInView (스크롤 진입 애니메이션)
```jsx
function useInView(threshold = 0.15) {
  const ref = useRef(null);
  const [seen, setSeen] = useState(false);
  useEffect(() => {
    const io = new IntersectionObserver(
      ([e]) => e.isIntersecting && setSeen(true), { threshold }
    );
    io.observe(ref.current);
    return () => io.disconnect();
  }, [threshold]);
  return [ref, seen];
}
```

### rise (등장 애니메이션)
```jsx
function rise(seen, delay) {
  return {
    opacity: seen ? 1 : 0,
    transform: seen ? "translateY(0)" : "translateY(22px)",
    transition: `opacity 0.7s ease ${delay}ms, transform 0.7s cubic-bezier(0.2,0.8,0.2,1) ${delay}ms`,
  };
}
```

---

## 5. 버튼 시스템

```jsx
// Primary (액센트 색)
<button style={{ background: t.accent, color: "#fff", minHeight: 56, borderRadius: t.radius }}>

// Ghost
<button style={{ border: `1px solid ${t.line}`, background: "transparent", color: t.text }}>

// CTA 최소 높이: 56px (5060 터치 배려)
```

---

## 6. 모바일 반응형 원칙

- 폰트 최소 18px
- 터치 타겟 최소 56px
- 그리드: 데스크탑 다열 → 모바일 1열
- 커리큘럼 화살표: → 가로 → ↓ 세로 전환
- 플로팅 버튼: 모바일에서 텍스트 숨김 (아이콘만)
