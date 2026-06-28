# 05_COMPONENT_GUIDE.md
# 타임아카이브 — Component Guide

> 모든 컴포넌트는 `theme` prop을 받아 두 시안을 모두 지원합니다.

---

## 1. 파일 구조

```
src/
├── site/
│   ├── theme.js              ← 테마 토큰 (THEME_DARKROOM / THEME_ARCHIVE)
│   ├── Sections1.jsx         ← TopBanner, TrustBar, GalleryShowcase, 공통 유틸
│   ├── Sections2.jsx         ← MosaicPortfolio, Instructor, InterviewVideos, WhyNow, Curriculum
│   ├── Sections3.jsx         ← InstaGallery, ForYou, Consult, FAQ, NoticeBoard, Footer, FloatingCTA
│   ├── HeroDarkroom.jsx      ← 시안 A 전용 Hero
│   ├── HeroArchive.jsx       ← 시안 B 전용 Hero
│   └── TimeArchiveSite.jsx   ← 전체 조립 (테마 주입)
```

---

## 2. 시안별 빌드 방법

```bash
# 시안 A (다크룸)
# entryA.jsx
import TimeArchiveSite from "./TimeArchiveSite.jsx";
import { THEME_DARKROOM } from "./theme.js";
createRoot(document.getElementById("root")).render(
  <TimeArchiveSite theme={THEME_DARKROOM} />
);

# 시안 B (아카이브)
# entryB.jsx
import TimeArchiveSite from "./TimeArchiveSite.jsx";
import { THEME_ARCHIVE } from "./theme.js";
createRoot(document.getElementById("root")).render(
  <TimeArchiveSite theme={THEME_ARCHIVE} />
);

# esbuild로 번들
./node_modules/.bin/esbuild entryA.jsx --bundle --outfile=siteA.js --loader:.jsx=jsx --jsx=automatic
./node_modules/.bin/esbuild entryB.jsx --bundle --outfile=siteB.js --loader:.jsx=jsx --jsx=automatic
```

---

## 3. TimeArchiveSite 조립 순서

```jsx
export default function TimeArchiveSite({ theme }) {
  const Hero = theme.name === "archive" ? HeroArchive : HeroDarkroom;
  return (
    <main style={{ background: t.bg }}>
      <TopBanner t={t} />
      <Hero />
      <GalleryShowcase t={t} />
      <TrustBar t={t} />
      <MosaicPortfolio t={t} />
      <Instructor t={t} />
      <InterviewVideos t={t} />
      <WhyNow t={t} />
      <Curriculum t={t} />
      <InstaGallery t={t} />
      <ForYou t={t} />
      <Consult t={t} />
      <FAQ t={t} />
      <NoticeBoard t={t} />
      <Footer t={t} />
      <FloatingCTA t={t} />
      <GlobalStyle t={t} />
    </main>
  );
}
```

---

## 4. 각 컴포넌트 요약

| 컴포넌트 | 파일 | 핵심 기능 |
|---|---|---|
| TopBanner | Sections1 | 개강 공지, 닫기 버튼 |
| TrustBar | Sections1 | 1999·1:1·100% 카운터 |
| GalleryShowcase | Sections1 | 4개 카테고리 자동 전환, 카피 |
| MosaicPortfolio | Sections2 | 12장 타일 그리드 |
| Instructor | Sections2 | 원장 프로필, 27년, 전문분야 태그 |
| InterviewVideos | Sections2 | 3종 영상 카드 |
| WhyNow | Sections2 | 시장 변화 3가지 + 타임의 대답 |
| Curriculum | Sections2 | 기초→심화 2트랙 토글 |
| InstaGallery | Sections3 | 인스타 자동 연동 (현재 플레이스홀더) |
| ForYou | Sections3 | 타겟 3종 카드 (창업/쇼핑몰/영상) |
| Consult | Sections3 | 3필드 폼 + Supabase 연동 지점 |
| FAQ | Sections3 | 3탭 + 아코디언 |
| NoticeBoard | Sections3 | 개강 공지 (구글 시트 연동 예정) |
| Footer | Sections3 | 링크 + 연락처 |
| FloatingCTA | Sections3 | 스크롤 600px 후 등장, 전화+상담 |
| HeroDarkroom | HeroDarkroom | 현상 효과, safelight red |
| HeroArchive | HeroArchive | 도록 Fig. 캡션, 명조체 |

---

## 5. Supabase 상담 폼 연동 지점

`Sections3.jsx`의 `Consult` 컴포넌트 내:

```jsx
// 현재 (데모 - 완료 화면만 표시)
await new Promise((r) => setTimeout(r, 800));
setStatus("done");

// 실제 배포 시 교체
const res = await fetch("/api/consultation", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(form),
});
if (!res.ok) throw new Error();
setStatus("done");
```

**Supabase 테이블:**
```sql
create table consultations (
  id uuid default gen_random_uuid() primary key,
  name text not null,
  phone text not null,
  course text,
  created_at timestamptz default now(),
  status text default '신규'
);
```

---

## 6. 인스타그램 자동 연동 지점

`Sections3.jsx`의 `InstaGallery` 컴포넌트:

```jsx
const INSTA_FEED_URL = ""; // "/api/instagram" 입력 시 활성화
// 미입력 시 FALLBACK_POSTS(샘플 6개) 노출
```

Next.js API 라우트 (`app/api/instagram/route.ts`):
```ts
const token = process.env.INSTAGRAM_ACCESS_TOKEN;
const userId = process.env.INSTAGRAM_USER_ID;
// Instagram Graph API → 최근 8개 이미지 반환
// 1시간 캐시 (revalidate: 3600)
```

---

## 7. 구글 시트 공지 연동 지점

`Sections3.jsx`의 `NoticeBoard` 컴포넌트:

```jsx
const SHEET_CSV_URL = ""; // 구글 시트 웹 게시 CSV URL 입력
// 미입력 시 FALLBACK_NOTICES(하드코딩) 노출
```

시트 형식: `날짜 | 과정 | 내용 | 상태(모집중/상시/마감)`
