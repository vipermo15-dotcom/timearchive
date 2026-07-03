# Pinterest (kr.pinterest.com) — 디자인 시스템 분석 보고서

> **분석 출처**: Firecrawl + WebFetch + GitHub 오픈소스 토큰  
> **데이터 기준**: Gestalt Design System v177.0.13 (2026.01.07 기준)  
> **GitHub**: https://github.com/pinterest/gestalt  
> **문서**: https://gestalt.pinterest.systems/

---

## 1. 브랜드 개요

| 항목 | 내용 |
|------|------|
| 서비스명 | Pinterest (핀터레스트) |
| 슬로건 | "사람들이 사랑하는 삶을 만들 수 있도록 영감을 주는 경험을 구축한다" |
| 디자인 시스템 | **Gestalt** (Pinterest 자체 디자인 시스템) |
| 기술 스택 | React + TypeScript, Apache-2.0 오픈소스 |
| 주요 사용자 | 비주얼 콘텐츠 탐색·저장·쇼핑 관심층 |
| 한국 특화 도메인 | kr.pinterest.com |

---

## 2. 색상 시스템

### 2-1. Base Color Palette (실제 토큰 값)

Pinterest는 색상 이름에 **고유 별명**을 사용한다 (Pushpin, Skycicle 등).

#### 🔴 Red · Pushpin (브랜드 핵심색)
| 단계 | 토큰명 | Hex |
|------|--------|-----|
| 0 | `red.pushpin.0` | `#FFF7F7` |
| 50 | `red.pushpin.50` | `#FFEBEB` |
| 100 | `red.pushpin.100` | `#FFE0E0` |
| 200 | `red.pushpin.200` | `#FCBBBB` |
| 300 | `red.pushpin.300` | `#F47171` |
| 400 | `red.pushpin.400` | `#EB4242` |
| **450** | **`red.pushpin.450`** | **`#E60023`** ← 브랜드 레드 (Primary) |
| 500 | `red.pushpin.500` | `#CC0000` |
| 600 | `red.pushpin.600` | `#B60000` |
| 700 | `red.pushpin.700` | `#9B0000` |
| 800 | `red.pushpin.800` | `#800000` |
| 900 | `red.pushpin.900` | `#660000` |

#### 🩶 Gray · Roboflow
| 단계 | Hex |
|------|-----|
| 50 | `#F9F9F9` |
| 100 | `#F1F1F1` |
| 200 | `#E9E9E9` |
| 300 | `#CDCDCD` |
| 400 | `#A5A5A5` |
| 500 | `#767676` (접근성 최소 명도) |
| 550 | `#5F5F5F` |
| 600 | `#4A4A4A` |
| 700 | `#2B2B2B` |
| 800 | `#191919` |

#### ⬛ Black · Cosmicore / White · Mochimalist
| 토큰 | Hex |
|------|-----|
| `black.cosmicore.900` | `#111111` |
| `white.mochimalist.0` | `#FFFFFF` |

#### 기타 팔레트 (주요값 450 기준)
| 색상 | 별명 | 450값 |
|------|------|-------|
| Pink | Flaminglow | `#EE376A` |
| Blue | Skycicle | `#007CFF` |
| Teal | Spabattical | `#009990` |
| Green | Matchacado | `#1DAD65` |
| Purple | Mysticool | `#8A39FA` |
| Orange | Firetini | `#FF5B45` |
| Yellow | Caramellow | `#D86800` |

---

### 2-2. Semantic Color (라이트 모드)

```
텍스트
  text.default      → #111111  (검정)
  text.subtle       → #767676  (회색, 접근성 AA 기준)
  text.disabled     → #A5A5A5
  text.error        → #CC0000
  text.success      → #005F3E
  text.link         → #004BA9

배경
  background.default          → #FFFFFF
  background.primary.base     → #E60023  (브랜드 레드)
  background.primary.strong   → #B60000  (hover)
  background.secondary.base   → #E9E9E9  (연회색)
  background.wash.dark        → rgba(0, 0, 0, 0.8)
  background.wash.light       → rgba(255, 255, 255, 0.9)

테두리
  border.container  → #CDCDCD
  border.default    → #767676
  border.focus      → rgba(0, 132, 255, 0.5)  (파란 포커스링)
  border.error      → #CC0000
```

### 2-3. 버튼 컬러 상태값

| 버튼 종류 | Default | Hover | Active |
|-----------|---------|-------|--------|
| **Primary** | `#E60023` | `#B60000` | `#a3081a` |
| **Secondary** | `#E9E9E9` | `#e2e2e2` | `#dadada` |
| **White** | `#FFFFFF` | `#f0f0f0` | `#e0e0e0` |
| **Dark** | `#111111` | `#000000` | `#000000` |
| **Shopping** | `#0074E8` | `#4a8ad4` | `#4a85c9` |

---

## 3. 타이포그래피

### 3-1. 폰트 패밀리

```css
/* 기본 (라틴·한국어 포함) */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
  Oxygen-Sans, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol',
  Ubuntu, Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
  Helvetica, 'ヒラギノ角ゴ Pro W3', 'メイリオ', Meiryo, Arial, sans-serif;

/* 코드 */
font-family: SFMono-Medium, 'SF Mono', 'Segoe UI Mono',
  'Roboto Mono', 'Ubuntu Mono', Menlo, Consolas, Courier, monospace;
```

> ⚠️ **한국어 주의**: Pinterest는 별도 한국어 웹폰트를 로드하지 않는다.  
> 시스템 폰트 스택에 의존 → macOS는 Apple SD Gothic Neo, Windows는 맑은 고딕.

### 3-2. 폰트 크기 스케일

| 토큰 | 값 | 용도 |
|------|----|------|
| `font.size.100` | `12px` | Caption, 태그, 라벨 |
| `font.size.200` | `14px` | Body small, 부제목 |
| `font.size.300` | `16px` | Body default |
| `font.size.400` | `20px` | 서브헤드 |
| `font.size.500` | `28px` | 섹션 헤드 |
| `font.size.600` | `36px` | 페이지 헤드 |

### 3-3. 폰트 굵기

| 토큰 | 값 | 용도 |
|------|----|------|
| `font.weight.normal` | `400` | 본문 |
| `font.weight.semibold` | `600` | 강조, UI 레이블 |
| `font.weight.bold` | `700` | 헤드라인, CTA |

---

## 4. 간격 시스템 (Spacing)

**4px 기반 그리드** 사용.

| 토큰 | 값 |
|------|----|
| `space.0` | `0px` |
| `space.100` | `4px` |
| `space.200` | `8px` |
| `space.300` | `12px` |
| `space.400` | `16px` ← 기본 카드 패딩 |
| `space.500` | `20px` |
| `space.600` | `24px` |
| `space.800` | `32px` |
| `space.1000` | `40px` |
| `space.1200` | `48px` |
| `space.1600` | `64px` ← 섹션 간격 |

---

## 5. 모서리 둥글기 (Border Radius / Rounding)

| 토큰 | 값 | 용도 |
|------|----|------|
| `rounding.0` | `0px` | 테이블, 구분선 |
| `rounding.100` | `4px` | 작은 태그, 칩 |
| `rounding.200` | `8px` | 드롭다운, 툴팁 |
| `rounding.300` | `12px` | 모달, 토스트 |
| `rounding.400` | `16px` | **핀 카드** (Pinterest 핵심 컴포넌트) |
| `rounding.600` | `24px` | 큰 카드 |
| `rounding.pill` | `999px` | 버튼, 배지, 검색창 |
| `rounding.circle` | `50%` | 아바타, 프로필 이미지 |

> **핀터레스트 카드 = rounding.400 (16px)** — 이 값이 Pinterest 시각적 정체성의 핵심

---

## 6. 레이아웃 패턴

### 6-1. 핵심 레이아웃: Masonry Grid (메이슨리 그리드)

```
Pinterest 핀 피드 구조:
┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐
│    │ │    │ │    │ │    │ │    │
│ 핀 │ │ 핀 │ │    │ │ 핀 │ │    │
│    │ │    │ │ 핀 │ │    │ │ 핀 │
└────┘ │    │ │    │ └────┘ │    │
┌────┐ └────┘ └────┘ ┌────┐ └────┘
│    │ ┌────┐ ┌────┐ │    │
│ 핀 │ │ 핀 │ │ 핀 │ │ 핀 │
└────┘ └────┘ └────┘ └────┘
```

- **열 너비**: 고정 236px (데스크탑 기준)
- **열 수**: 화면 너비에 따라 2~8열 자동 조정
- **거터**: 16px (`space.400`)
- **핀 높이**: 가변 (이미지 비율에 따름, 종횡비 유지)
- **무한 스크롤**: 하단 도달 시 추가 로드

### 6-2. 글로벌 내비게이션

```
┌─────────────────────────────────────────────────────────┐
│ [📌로고]  [홈] [만들기]  [  🔍 검색  ]  [알림] [👤프로필] │
│           ← 좌측 고정   ← 가운데     ← 우측 아이콘들   │
└─────────────────────────────────────────────────────────┘
높이: ~64px, position: fixed, background: #ffffff
```

**내비게이션 링크 (한국어 실제 텍스트):**
- `Explore` / 탐색
- `Log in` / 로그인
- `Sign up` / 회원가입

### 6-3. 카테고리 구조 (실제 데이터)

```
Animals · Art · Beauty · Design · Diy And Crafts ·
Food And Drink · Home Decor · Mens Fashion · Quotes · Tattoos
```

---

## 7. 핵심 UX 패턴

### 7-1. 핀 카드 (Pin Card)
```
┌──────────────────┐
│                  │ ← 이미지 (가변 높이, rounding-top: 16px)
│     이미지       │
│                  │
│   ─────────────  │ ← hover 시 반투명 오버레이
│   [저장] [더보기]│ ← 액션 버튼 (항상 우측 상단에)
├──────────────────┤
│ 제목 텍스트       │ ← font-size: 14px, weight: 600
│ 출처 · 도메인    │ ← font-size: 12px, color: #767676
└──────────────────┘
border-radius: 16px
```

**핀 hover 인터랙션:**
1. 이미지 위 `다크 wash` 오버레이 (rgba(0,0,0,0.04))
2. 우측 상단: `저장` 버튼 (빨간 Primary 버튼)
3. 우측 하단: `더보기(...)` 아이콘

### 7-2. 저장(Save) 버튼 패턴
```css
/* 핀 hover 시 나타나는 저장 버튼 */
background: #E60023;          /* red.pushpin.450 */
color: #FFFFFF;
border-radius: 999px;         /* pill */
padding: 8px 16px;
font-weight: 700;
font-size: 14px;
```

### 7-3. 검색 UI
- 검색창: `border-radius: 999px` (완전 pill 형태)
- 배경: `gray.roboflow.100` (`#F1F1F1`)
- 내부: 좌측 🔍 아이콘, 우측 📷 비주얼 서치 카메라 아이콘
- 검색 가이드 칩: 컬러풀한 배경 (skycicle.200, matchacado.200, firetini.200...)

### 7-4. 프로필 아바타
- 형태: `border-radius: 50%` (circle)
- 빈 상태: `background: #efefef`
- 테두리: `border: 2px solid #FFFFFF`

### 7-5. 모바일 UI
- 하단 탭바 (Bottom Navigation)
- 핀 카드: 2열 그리드
- `position: sticky` 상단 검색창

---

## 8. 컴포넌트 패턴 요약

### Button
```
Primary:   bg #E60023  text #FFF   radius pill(999px)  weight 700
Secondary: bg #E9E9E9  text #111   radius pill
White:     bg #FFFFFF  text #111   radius pill
Dark:      bg #111111  text #FFF   radius pill
```

### Badge (배지)
```
Neutral:        bg gray  text gray
Error:          bg #CC0000  text #FFF
Success:        bg green
Info:           bg blue
Recommendation: bg purple
```

### Search Guide Chip (검색 가이드)
다채로운 파스텔 칩 — 카테고리별 색상 할당:
```
01: #ABDBFF (skycicle-200)
02: #A4F9AC (matchacado-200)
03: #FFC58F (firetini-200)
04: #FCBBBB (pushpin-200)
05: #D5C7FF (mysticool-200)
```

---

## 9. 한국어 특화 고려사항

| 항목 | 현황 | 개선 포인트 |
|------|------|-------------|
| **웹폰트** | 별도 로드 없음, 시스템 폰트 의존 | 한국어는 Apple SD Gothic Neo / 맑은 고딕 |
| **레이아웃** | 영문 기준 설계, 한국어 텍스트 오버플로우 위험 | 카드 제목 줄바꿈 대응 필요 |
| **카테고리** | 영문 카테고리 그대로 노출 (Home Decor 등) | 한국어화 미흡 |
| **날짜/숫자** | 영문 포맷 | 한국어 localization 필요 |
| **검색** | 한국어 자동완성 지원 | 한글 조합 처리 중요 |

---

## 10. 타임아카이브에 참고할 포인트

### ✅ 즉시 적용 가능
| Pinterest 패턴 | 타임아카이브 적용 |
|----------------|-----------------|
| **Masonry Grid** | 갤러리 섹션에 적용 — 수강생 작품을 Pinterest처럼 |
| **Pin Card rounding: 16px** | 수강 과정 카드, 후기 카드 radius |
| **Pill 버튼** | CTA 버튼 — pill 형태로 통일 |
| **저장/호버 오버레이** | 갤러리 이미지 hover 시 "상세보기" 오버레이 |
| **카테고리 칩** | 과정 분류 칩 (인물, 제품, 식품...) |
| **4px 기반 스페이싱** | 일관된 여백 시스템 도입 |

### 🎨 색상 참고
```
Pinterest 브랜드 레드 #E60023  →  타임아카이브는 딥그린 #2C4A47 (B 시안 기준)
Pinterest 시스템 회색 #767676  →  텍스트 서브컬러로 동일 기준 사용 권장
Pinterest 배경 #F9F9F9         →  섹션 배경으로 참고
```

### 🧩 레이아웃 인사이트
- **고정 네비게이션**: 스크롤 시에도 GNV 고정 (타임아카이브도 이미 적용)
- **검색 중심 UX**: 수강 과정 검색 기능 추가 시 pill 형태 권장
- **비주얼 퍼스트**: 텍스트보다 이미지가 먼저 — 갤러리 비중을 높게

---

## 11. 설계 철학

> **"Build experiences that inspire people to create the life they love."**  
> — Gestalt Design System 공식 미션

| 원칙 | 내용 |
|------|------|
| **Visual First** | 텍스트보다 이미지·비주얼이 핵심 커뮤니케이션 수단 |
| **Accessibility** | WCAG AA 기준 (`#767676` = 최소 명도비) |
| **Consistency** | 디자인 토큰 기반 — 컴포넌트 간 일관성 |
| **Delight** | 미세한 호버·애니메이션으로 감성적 경험 |
| **Scale** | 5인 팀이 전사 디자인 시스템 운영 가능한 구조 |

---

## 12. 기술 스택 참고

| 항목 | 내용 |
|------|------|
| UI 프레임워크 | React 18 |
| 언어 | TypeScript 85%, CSS 11%, JS 4% |
| 디자인 토큰 | Style Dictionary 기반 JSON → CSS 변환 |
| 패키지 | `gestalt` / `gestalt-charts` / `gestalt-datepicker` |
| 버전 (2026.01) | v177.0.13 |
| 라이선스 | Apache-2.0 (상업적 사용 가능) |
| GitHub 스타 | 4,400+ |

```bash
# 설치
npm install gestalt

# 사용
import { Button, Pin, Text } from 'gestalt';
import 'gestalt/dist/gestalt.css';
```

---

*분석 기준일: 2026-07-04*  
*출처: kr.pinterest.com · gestalt.pinterest.systems · github.com/pinterest/gestalt*
