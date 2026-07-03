---
version: 1.0
name: TIME ARCHIVE — Studio System (和 / Wa)
description: >
  일본 사진 교육 기관(Ken Domon Museum, Tokyo Photographers' Gallery)과
  무지(Muji), 야나기 소리(Yanagi Sori) 산업 디자인에서 추출한 스튜디오 시스템.
  間(Ma) — 여백이 능동적 설계 요소다. Noto Serif KR 명조 위계, 인디고 단일 액센트,
  화지(和紙) 팔레트. 정밀함이 침묵을 섬긴다.

colors:
  # ─── 캔버스 ───────────────────────────────────────────
  canvas:           "#f8f6f1"   # 화지(和紙) 화이트 — 천연 닥나무 종이 색
  canvas-deep:      "#edeae3"   # 린넨 베이지 — 섹션 배경
  warm-stone:       "#d8d3cc"   # 돌 회색 — 구분선·보더
  warm-wood:        "#8c7355"   # 목재 갈색 — 포인트 서페이스

  # ─── 타이포 ───────────────────────────────────────────
  ink:              "#1c1c1c"   # 墨(먹) — 먹물 검정 (약간의 온기 포함)
  ink-muted:        "#757070"   # 중간 회색 — 캡션·서브텍스트
  ink-light:        "#a8a4a0"   # 라이트 그레이 — 파인프린트

  # ─── 액센트 (단일) ────────────────────────────────────
  accent:           "#3d5a6e"   # 藍(아이) 인디고 — 일본 전통 쪽빛
  accent-soft:      "#5a7a90"   # 소프트 인디고 — hover·라이트 서페이스
  accent-on-dark:   "#7aafc8"   # 다크 서페이스용 라이트 인디고

  # ─── 다크 서페이스 ────────────────────────────────────
  surface-dark:     "#1a1a1a"   # 漆(우루시) — 옻칠 근-흑 (따뜻함 없음)
  surface-dark-2:   "#202020"   # 다크 섹션 미세 분리용
  on-dark:          "#f0ede6"   # 다크 위 텍스트 (canvas보다 약간 따뜻)
  on-dark-muted:    "#9e9a94"   # 다크 위 서브텍스트

typography:
  # ─── 디스플레이: Noto Serif KR (Google Fonts 무료) ────
  # 출판용 명조. 권위 있고 정돈된 느낌. 일본 사진 기관의 간판 느낌.
  hero:
    fontFamily: "'Noto Serif KR', 'Gowun Serif', Georgia, serif"
    fontSize: clamp(36px, 5vw, 56px)
    fontWeight: 700
    lineHeight: 1.08
    letterSpacing: "-0.015em"
  display-lg:
    fontFamily: "'Noto Serif KR', 'Gowun Serif', Georgia, serif"
    fontSize: clamp(26px, 3.2vw, 40px)
    fontWeight: 600
    lineHeight: 1.15
    letterSpacing: "0"
  display-md:
    fontFamily: "'Noto Serif KR', 'Gowun Serif', Georgia, serif"
    fontSize: clamp(20px, 2.5vw, 28px)
    fontWeight: 600
    lineHeight: 1.25
    letterSpacing: "0"
  display-sm:
    fontFamily: "'Noto Serif KR', 'Gowun Serif', Georgia, serif"
    fontSize: 21px
    fontWeight: 500
    lineHeight: 1.40
    letterSpacing: "0"

  # ─── 본문: Noto Sans KR ───────────────────────────────
  lead:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 300
    lineHeight: 1.80
    letterSpacing: "0"
  body:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 15px
    fontWeight: 400
    lineHeight: 1.85
    letterSpacing: "0.01em"
  body-strong:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 15px
    fontWeight: 600
    lineHeight: 1.85
    letterSpacing: "0.01em"

  # ─── 레이블 / 캡션 ────────────────────────────────────
  caption:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: "0.05em"
  label:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 10px
    fontWeight: 500
    lineHeight: 1.30
    letterSpacing: "0.14em"
    textTransform: uppercase
  fine-print:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 10px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: "0.03em"

rounded:
  none: "0px"      # 풀블리드 — 直線(직선)
  xs: "2px"        # 미세 chip (거의 직각)
  sm: "4px"        # 유틸리티 버튼
  md: "8px"        # 카드 이미지 내부
  lg: "14px"       # 코스 카드
  pill: "9999px"   # 검색 입력 (예외적으로만)
  full: "9999px"

spacing:
  xxs: "4px"
  xs: "8px"
  sm: "12px"
  md: "20px"
  lg: "32px"
  xl: "52px"
  xxl: "72px"
  section: "112px"    # 간(間) — 넉넉한 여백이 핵심
  section-lg: "144px" # 주요 섹션 상단

components:
  # 버튼
  btn-primary:
    backgroundColor: "{colors.accent}"
    textColor: "{colors.on-dark}"
    typography: "{typography.body}"
    rounded: "{rounded.sm}"
    padding: "11px 26px"
  btn-ghost:
    backgroundColor: "transparent"
    textColor: "{colors.accent}"
    border: "1px solid {colors.accent}"
    typography: "{typography.body}"
    rounded: "{rounded.sm}"
    padding: "10px 26px"
  btn-ghost-dark:
    backgroundColor: "transparent"
    textColor: "{colors.accent-on-dark}"
    border: "1px solid {colors.accent-on-dark}"
    typography: "{typography.body}"
    rounded: "{rounded.sm}"
    padding: "10px 26px"
  text-link:
    textColor: "{colors.accent}"
    typography: "{typography.body}"
  text-link-dark:
    textColor: "{colors.accent-on-dark}"
    typography: "{typography.body}"

  # 타일
  tile-canvas:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    padding: "{spacing.section} 48px"
    rounded: "{rounded.none}"
  tile-deep:
    backgroundColor: "{colors.canvas-deep}"
    textColor: "{colors.ink}"
    padding: "{spacing.section} 48px"
    rounded: "{rounded.none}"
  tile-dark:
    backgroundColor: "{colors.surface-dark}"
    textColor: "{colors.on-dark}"
    padding: "{spacing.section} 48px"
    rounded: "{rounded.none}"
  tile-dark-2:
    backgroundColor: "{colors.surface-dark-2}"
    textColor: "{colors.on-dark}"
    padding: "{spacing.section} 48px"
    rounded: "{rounded.none}"

  # 카드
  course-card:
    backgroundColor: "{colors.canvas}"
    border: "1px solid {colors.warm-stone}"
    textColor: "{colors.ink}"
    rounded: "{rounded.lg}"
    padding: "32px"
  stats-cell:
    backgroundColor: "transparent"
    border: "none"
    borderTop: "1px solid {colors.warm-stone}"
    textColor: "{colors.ink}"
    rounded: "{rounded.none}"
    padding: "28px 0"

  # 내비게이션
  gnav:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.on-dark}"
    typography: "{typography.caption}"
    height: "48px"
  sub-nav:
    backgroundColor: "rgba(248,246,241,0.90)"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    backdropFilter: "saturate(140%) blur(24px)"
    borderBottom: "1px solid {colors.warm-stone}"
    height: "52px"

  # 푸터
  footer:
    backgroundColor: "{colors.canvas-deep}"
    textColor: "{colors.ink-muted}"
    typography: "{typography.fine-print}"
    borderTop: "1px solid {colors.warm-stone}"
    padding: "72px 48px"
---

## 개요

**Studio System (和/Wa)**은 일본 사진 기관과 공예 철학에서 추출한 디자인 언어다.
중심 개념은 **間(Ma) — 여백은 공백이 아니라 설계된 침묵이다**.

색은 최소 — 화지(和紙) 화이트, 먹 검정, 인디고 하나.
형태는 직선 우선 — 불필요한 라운딩 없음.
타이포는 Noto Serif KR 명조 × Noto Sans KR 고딕의 권위와 명료함.
사진은 언제나 첫 번째다. UI는 그 뒤에 선다.

Editorial Archive System과 같은 베이지 계열이지만
더 차갑고, 더 정밀하고, 더 조용하다.

### 핵심 원칙
- **間(Ma)**: 섹션 패딩 최소 112px. 요소 간 간격이 곧 관계를 정의한다.
- **漆(Urushi) 어두움**: 다크 서페이스는 따뜻함 없는 순수한 漆 근-흑 (#1a1a1a).
- **단일 인디고**: `{colors.accent}` 藍(쪽빛) 하나만 인터랙티브 신호.
- **직선 우선**: border-radius는 최소 (sm: 4px). Apple pill 없음.
- **명조의 권위**: Noto Serif KR은 '전문 기관'의 신뢰감을 준다.

---

## 색상

### 캔버스
- **화지 화이트** (`{colors.canvas}` — #f8f6f1): 화지(和紙) 느낌의 따뜻한 기본 배경. 가장 흰 서페이스.
- **린넨 베이지** (`{colors.canvas-deep}` — #edeae3): 서비스·과정 섹션 배경. 한 단계 깊은 자연 색.
- **스톤 그레이** (`{colors.warm-stone}` — #d8d3cc): 카드 보더·구분선. 차갑지 않은 돌 느낌.
- **목재 브라운** (`{colors.warm-wood}` — #8c7355): 포인트 강조 서페이스. 나무 결.

### 다크 서페이스
- **漆 근-흑** (`{colors.surface-dark}` — #1a1a1a): 옻칠(漆) 느낌의 묵직한 어두움. 온기 없음.
  Editorial Archive의 surface-dark(#1f1d1a)보다 더 차갑고 정밀.
- **다크-2** (`{colors.surface-dark-2}` — #202020): 연속 다크 타일 분리.

### 액센트
- **藍 인디고** (`{colors.accent}` — #3d5a6e): 일본 전통 쪽빛. 링크·버튼·포커스. 따뜻한 클레이(Editorial)와 대비.
- **소프트 인디고** (`{colors.accent-soft}` — #5a7a90): hover 상태.
- **라이트 인디고** (`{colors.accent-on-dark}` — #7aafc8): 다크 서페이스 링크.

### 텍스트
- **墨(먹) 검정** (`{colors.ink}` — #1c1c1c): 먹물의 약간의 온기가 남은 진검정.
- **중간 그레이** (`{colors.ink-muted}` — #757070): 캡션·서브텍스트.
- **라이트 그레이** (`{colors.ink-light}` — #a8a4a0): 파인프린트.

---

## 타이포그래피

### 폰트 패밀리
- **Noto Serif KR** (Google Fonts 무료): 디스플레이·헤드라인. CJK 통합 명조체. 일본 출판 인쇄의 명조 문화와 연결.
  Editorial Archive의 Gowun Serif보다 더 단정하고 기관적(institutional). 획 대비가 낮아 차분함.
- **Noto Sans KR** (Google Fonts 무료): 본문·UI·레이블. 동일한 Noto 패밀리여서 세리프↔산세리프 전환이 자연스럽다.

### 위계

| 토큰 | 크기 | 굵기 | 행간 | 자간 | 용도 |
|---|---|---|---|---|---|
| `{typography.hero}` | clamp(36–56px) | 700 | 1.08 | -0.015em | 히어로 |
| `{typography.display-lg}` | clamp(26–40px) | 600 | 1.15 | 0 | 섹션 헤드 |
| `{typography.display-md}` | clamp(20–28px) | 600 | 1.25 | 0 | 서브 섹션 |
| `{typography.display-sm}` | 21px | 500 | 1.40 | 0 | 카드 헤드 |
| `{typography.lead}` | 18px | 300 | 1.80 | 0 | 서브카피 (가벼운 공기감) |
| `{typography.body}` | 15px | 400 | 1.85 | 0.01em | 기본 본문 |
| `{typography.body-strong}` | 15px | 600 | 1.85 | 0.01em | 강조 인라인 |
| `{typography.caption}` | 12px | 400 | 1.55 | 0.05em | 캡션 |
| `{typography.label}` | 10px | 500 | 1.30 | 0.14em (uppercase) | 카테고리·레이블 |
| `{typography.fine-print}` | 10px | 400 | 1.50 | 0.03em | 약관 |

### 원칙
- **행간 1.85 — 間의 구현**: 본문에 가장 넉넉한 행간. 읽는 속도를 늦춰 사진을 보게 만든다.
- **15px 본문**: 16px(Editorial)보다 작다. 더 조심스럽고 정밀한 정보 제공.
- **weight 300은 lead 전용**: 서브카피의 침묵 같은 가벼움. 본문은 항상 400.
- **명조 자간 음수(-0.015em)는 hero에만**: display-lg 이하는 자간 0.
- **uppercase label 0.14em**: 더 벌린 자간 — 일본 타입 색인의 정밀함.

---

## 레이아웃

### 間(Ma) — 여백 철학
여백은 수동적 공간이 아니다. 요소 간 간격이 관계와 위계를 정의한다.
사진 위아래 최소 80px. 텍스트 블록 사이 최소 48px.
'비어있음'은 곧 품격이다.

### 간격 시스템
- **섹션 패딩**: 112px (가장 넉넉한 시스템).
- **수평 패딩**: 48px. 최대 컨텐츠 폭 1160px.
- **카드 내부**: 32px.
- **그리드 갭**: 카드 그리드 28px, 갤러리 그리드 3–6px.

### 그리드
- **비대칭 히어로**: 이미지 60% + 텍스트 40% (항상 50:50이 아님). 간(間)의 비대칭 균형.
- **2컬럼 분할**: 강사 소개, 과정 상세.
- **3컬럼 카드**: 과정 카드 그리드, gap 28px.
- **갤러리**: 엄격한 equal-height 2–3컬럼. 아카이브 분류 감각.

---

## 엘리베이션 & 깊이

| 레벨 | 처리 | 사용처 |
|---|---|---|
| 플랫 | 없음 | 풀블리드 타일, 내비게이션, 히어로 |
| 스톤 보더 | 1px solid `{colors.warm-stone}` | 코스 카드, 통계 구분 |
| 프로스트 글라스 | rgba(248,246,241,0.90) + blur(24px) | 서브 내비게이션 |
| 사진 그림자 | rgba(0,0,0,0.12) 0px 4px 20px | 사진이 서페이스에 놓일 때만 |

> **규칙**: Editorial Archive와 동일 — 카드·버튼에 그림자 없음. 사진에만.

---

## 컴포넌트

### 버튼
- **btn-primary**: 인디고 배경. `{rounded.sm}` (4px) — 직선에 가까운 라운딩.
- **btn-ghost**: 인디고 보더 + 텍스트. 얇은 선.
- 액티브: `transform: scale(0.98)` — 거의 움직이지 않는 정적인 반응.

### 타일
- **tile-canvas** → **tile-deep** → **tile-dark** → **tile-canvas** 순환.
- 경계: 배경색 전환만. 선·그림자 없음.

### 카드
- **course-card**: 화지 화이트 + 스톤 보더, 14px 라운딩. 정갈한 카드.
- **stats-cell**: 경계선 없음, 상단 스톤 보더만. 신문 통계 표 스타일.

### 내비게이션
- **gnav**: 먹 검정 고정 상단 바. 높이 48px (Editorial보다 작음 — 더 정밀).
- **sub-nav**: 화지 화이트 프로스트 글라스.

---

## Do / Don't

### Do
- 섹션 패딩 112px 이상. 間(Ma) 철학.
- 모든 인터랙션에 `{colors.accent}` 인디고만. 단색 원칙.
- Noto Serif KR 헤드라인 — 권위와 정밀함을 위해.
- 직선 우선. border-radius는 sm(4px) 또는 lg(14px)만.
- 사진은 풀블리드 또는 갭 없는 그리드. 프레임 없음.
- body 행간 1.85 유지. 간결하지 않게 — 넉넉하게.

### Don't
- Apple pill(9999px) 버튼 쓰지 않는다. 직선 감성.
- 두 번째 액센트 색 없음. 인디고 하나.
- 다크 서페이스에서 `{colors.accent}` 직접 쓰지 않는다 — `{colors.accent-on-dark}` 사용.
- 카드·버튼에 그림자 없음.
- 장식 그라디언트 없음.
- 본문 행간을 1.85 아래로 줄이지 않는다.
- 헤드라인 weight 400 쓰지 않는다. 최소 500, 주로 600/700.

---

## Editorial Archive vs Studio (和) 비교

| 항목 | Editorial Archive | Studio (和) |
|---|---|---|
| 팔레트 | 베이지·크림 따뜻함 | 화지·린넨 중립적 |
| 액센트 | 클레이 #7a5c3a (따뜻함) | 인디고 #3d5a6e (차가움) |
| 헤드라인 | Gowun Serif (유려함) | Noto Serif KR (단정함) |
| 버튼 | sm 6px (약간 라운드) | sm 4px (거의 직선) |
| 본문 | 16px / 1.75 | 15px / 1.85 |
| 섹션 패딩 | 96px | 112px |
| 다크 서페이스 | #1f1d1a (약간 따뜻) | #1a1a1a (차갑고 정밀) |
| 전체 느낌 | 출판물·잡지 | 기관·박물관 |

> **선택 가이드**: 따뜻하고 친근한 사진학원 → Editorial Archive.
> 권위 있고 전문적인 아카이브 기관 → Studio (和).

---

## 반복 가이드 (에이전트용)

1. 여백 먼저 확보하고 컨텐츠 배치. section: 112px 이하로 시작하지 않는다.
2. 인디고 `{colors.accent}`는 클릭 가능한 요소에만.
3. 헤드라인은 Noto Serif KR 600/700. body는 Noto Sans KR 400.
4. 다크 타일에서 연속이 필요하면 dark-2 사용.
5. 카드 border-radius: `{rounded.lg}` (14px). 버튼: `{rounded.sm}` (4px).
6. 통계·수치 섹션: stats-cell 패턴 (상단 보더만, 패딩 없는 그리드).
