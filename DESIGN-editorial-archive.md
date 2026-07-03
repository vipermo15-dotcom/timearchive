---
version: 1.0
name: TIME ARCHIVE — Editorial Archive System
description: >
  사진전문 출판물(Aperture Foundation, Foam Magazine, Magnum Archive)에서 추출한
  에디토리얼 아카이브 디자인 시스템. 아카이브 베이지 팔레트와 한국어 세리프 활자로
  사진작가의 작품이 벽이 되고, 텍스트는 캡션이 된다는 원칙을 구현한다.
  Action Blue·SF Pro 없음. 단일 클레이 액센트와 따뜻한 차콜만 사용.

colors:
  # ─── 캔버스 ───────────────────────────────────────────
  canvas:           "#faf8f3"   # 크림 화이트 — 기본 배경 (aged paper)
  parch:            "#f0ebe0"   # 아카이브 베이지 — 섹션 배경
  parch-deep:       "#e4ddd0"   # 딥 베이지 — 구분용 dark surface
  warm-mid:         "#c8bfad"   # 구분선·보더 (warm hairline)

  # ─── 타이포 ───────────────────────────────────────────
  ink:              "#1a1a18"   # 따뜻한 차콜 — 헤드라인·본문 (순흑 아님)
  ink-muted:        "#6b6560"   # 서브텍스트·캡션
  ink-light:        "#a09890"   # 파인프린트·레이블

  # ─── 액센트 (단일) ────────────────────────────────────
  accent:           "#7a5c3a"   # 로스팅 클레이 — 링크·버튼·포커스
  accent-warm:      "#9e7048"   # 라이트 서페이스 hover 상태
  accent-on-dark:   "#c49a6a"   # 다크 서페이스 링크

  # ─── 다크 서페이스 ────────────────────────────────────
  surface-dark:     "#1f1d1a"   # 따뜻한 근-흑 (pure black 아님)
  surface-dark-2:   "#252320"   # 다크 섹션 분리용 미세 차이
  on-dark:          "#f0ebe0"   # 다크 위 주 텍스트 (parch 재활용)
  on-dark-muted:    "#a09880"   # 다크 위 서브텍스트

typography:
  # ─── 디스플레이: Gowun Serif (Google Fonts, 무료) ─────
  # 한국어 특화 명조, 획의 굵기 대비가 아카이브 에디토리얼과 잘 어울림
  hero:
    fontFamily: "'Gowun Serif', 'Noto Serif KR', Georgia, serif"
    fontSize: clamp(38px, 5.5vw, 58px)
    fontWeight: 700
    lineHeight: 1.06
    letterSpacing: "-0.02em"
  display-lg:
    fontFamily: "'Gowun Serif', 'Noto Serif KR', Georgia, serif"
    fontSize: clamp(28px, 3.5vw, 42px)
    fontWeight: 700
    lineHeight: 1.10
    letterSpacing: "-0.01em"
  display-md:
    fontFamily: "'Gowun Serif', 'Noto Serif KR', Georgia, serif"
    fontSize: clamp(22px, 2.8vw, 32px)
    fontWeight: 600
    lineHeight: 1.20
    letterSpacing: "0"

  # ─── 본문: Noto Sans KR ───────────────────────────────
  lead:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 21px
    fontWeight: 300
    lineHeight: 1.60
    letterSpacing: "0"
  body:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.75
    letterSpacing: "0"
  body-strong:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 600
    lineHeight: 1.75
    letterSpacing: "0"

  # ─── 레이블 / 캡션 ────────────────────────────────────
  caption:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: "0.04em"
  label:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 11px
    fontWeight: 500
    lineHeight: 1.30
    letterSpacing: "0.10em"
    textTransform: uppercase
  fine-print:
    fontFamily: "'Noto Sans KR', system-ui, sans-serif"
    fontSize: 11px
    fontWeight: 400
    lineHeight: 1.40
    letterSpacing: "0.02em"

rounded:
  none: "0px"       # 풀블리드 타일 — 라운딩 없음
  xs: "3px"         # 미세 인라인 chip
  sm: "6px"         # 유틸리티 버튼 (소)
  md: "10px"        # 카드 이미지 내부 라운딩
  lg: "16px"        # 코스 카드
  pill: "9999px"    # 텍스트 링크 chip, 검색 입력
  full: "9999px"

spacing:
  xxs: "4px"
  xs: "8px"
  sm: "14px"
  md: "20px"
  lg: "32px"
  xl: "48px"
  xxl: "64px"
  section: "96px"    # Apple 80px보다 여유 있음 (에디토리얼 공기감)
  section-lg: "128px"

components:
  # 버튼
  btn-primary:
    backgroundColor: "{colors.accent}"
    textColor: "{colors.canvas}"
    typography: "{typography.body}"
    rounded: "{rounded.sm}"
    padding: "11px 24px"
  btn-ghost:
    backgroundColor: "transparent"
    textColor: "{colors.accent}"
    border: "1px solid {colors.accent}"
    typography: "{typography.body}"
    rounded: "{rounded.sm}"
    padding: "10px 24px"
  btn-ghost-dark:
    backgroundColor: "transparent"
    textColor: "{colors.accent-on-dark}"
    border: "1px solid {colors.accent-on-dark}"
    typography: "{typography.body}"
    rounded: "{rounded.sm}"
    padding: "10px 24px"
  text-link:
    textColor: "{colors.accent}"
    typography: "{typography.body}"
  text-link-dark:
    textColor: "{colors.accent-on-dark}"
    typography: "{typography.body}"

  # 타일 (풀블리드, 갭 없음)
  tile-cream:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    padding: "{spacing.section} 44px"
    rounded: "{rounded.none}"
  tile-parch:
    backgroundColor: "{colors.parch}"
    textColor: "{colors.ink}"
    padding: "{spacing.section} 44px"
    rounded: "{rounded.none}"
  tile-dark:
    backgroundColor: "{colors.surface-dark}"
    textColor: "{colors.on-dark}"
    padding: "{spacing.section} 44px"
    rounded: "{rounded.none}"
  tile-dark-2:
    backgroundColor: "{colors.surface-dark-2}"
    textColor: "{colors.on-dark}"
    padding: "{spacing.section} 44px"
    rounded: "{rounded.none}"

  # 카드
  course-card:
    backgroundColor: "{colors.canvas}"
    border: "1px solid {colors.warm-mid}"
    textColor: "{colors.ink}"
    rounded: "{rounded.lg}"
    padding: "28px"
  course-card-dark:
    backgroundColor: "{colors.surface-dark-2}"
    border: "1px solid rgba(255,255,255,0.08)"
    textColor: "{colors.on-dark}"
    rounded: "{rounded.lg}"
    padding: "28px"
  gallery-frame:
    backgroundColor: "{colors.parch-deep}"
    border: "none"
    rounded: "{rounded.none}"
    padding: "0"

  # 내비게이션
  gnav:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.on-dark}"
    typography: "{typography.caption}"
    height: "52px"
  sub-nav:
    backgroundColor: "rgba(240,235,224,0.92)"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    backdropFilter: "saturate(160%) blur(20px)"
    borderBottom: "1px solid {colors.warm-mid}"
    height: "52px"

  # 푸터
  footer:
    backgroundColor: "{colors.parch}"
    textColor: "{colors.ink-muted}"
    typography: "{typography.fine-print}"
    borderTop: "1px solid {colors.warm-mid}"
    padding: "64px 44px"
---

## 개요

**에디토리얼 아카이브 시스템**은 *Aperture*, *Foam*, *Magnum Archive* 같은
사진 전문 출판물에서 추출한 디자인 언어다. 핵심 전제는 하나:
**사진이 벽이 되고, 텍스트는 그 아래 캡션이 된다.**

UI 크롬은 최소화하고, 액션을 알리는 색은 단 하나 — 로스팅 클레이(`{colors.accent}` #7a5c3a).
타이포그래피는 Gowun Serif(명조) + Noto Sans KR(고딕)의 대비로 에디토리얼 리듬을 만든다.
베이지·크림 팔레트와 따뜻한 차콜은 아카이브 용지의 물성(物性)을 스크린에 번역한다.

### 핵심 원칙
- **사진 우선**: 이미지는 항상 풀블리드 혹은 프레임 없이. 사진에 그림자·보더 없음.
- **단일 액센트**: `{colors.accent}` 클레이만 인터랙티브 신호로 사용. 보조 색 없음.
- **활자 대비**: Gowun Serif 헤드라인 × Noto Sans KR 본문. 둘 다 무료 Google Fonts.
- **에디토리얼 여백**: 섹션 패딩 최소 96px. 사진과 텍스트 사이 40px 이상.
- **풀블리드 타일**: 섹션 경계는 색 전환으로 — 보더·그림자 없음.

---

## 색상

### 캔버스
- **크림 화이트** (`{colors.canvas}` — #faf8f3): 기본 페이지 배경. 아카이브 용지 느낌. 순백(#ffffff)보다 따뜻함.
- **아카이브 베이지** (`{colors.parch}` — #f0ebe0): 홍보 섹션·서비스 섹션 배경. 타임아카이브 브랜드의 핵심 색.
- **딥 베이지** (`{colors.parch-deep}` — #e4ddd0): 갤러리 배경·통계 섹션. parch보다 한 단계 깊음.
- **웜 헤어라인** (`{colors.warm-mid}` — #c8bfad): 카드 보더·구분선. 딱딱하지 않은 따뜻한 선.

### 다크 서페이스
- **따뜻한 근-흑** (`{colors.surface-dark}` — #1f1d1a): 다크 타일 배경. 순흑(#000000)보다 따뜻하고 아날로그적.
- **다크-2** (`{colors.surface-dark-2}` — #252320): 연속 다크 타일 분리용. 미세 차이로 충분.

### 액센트
- **로스팅 클레이** (`{colors.accent}` — #7a5c3a): 링크·버튼·포커스링에만 사용. 흑백 사진 위에 정착한 세피아 톤.
- **웜 클레이** (`{colors.accent-warm}` — #9e7048): 라이트 서페이스 hover.
- **라이트 클레이** (`{colors.accent-on-dark}` — #c49a6a): 다크 서페이스 링크.

### 텍스트
- **따뜻한 차콜** (`{colors.ink}` — #1a1a18): 모든 헤드라인·본문. 순흑이 아닌 약간의 갈색 언더톤.
- **뮤트 그레이** (`{colors.ink-muted}` — #6b6560): 캡션·서브텍스트.
- **라이트 그레이** (`{colors.ink-light}` — #a09890): 파인프린트·레이블.

---

## 타이포그래피

### 폰트 패밀리
- **Gowun Serif** (Google Fonts 무료): 디스플레이·헤드라인. 한국어 명조체 중 에디토리얼 감성에 가장 가까운 선택.
  아랫획의 유려한 시리프와 획 대비가 아카이브 출판물과 자연스럽게 맞아떨어진다.
- **Noto Sans KR** (Google Fonts 무료): 본문·UI·캡션. Google/Adobe 공동 개발, 한국어 가독성 최상.
  Body 사이즈에서 line-height 1.75를 유지해 사진 사이 읽기 편한 리듬을 만든다.

### 위계

| 토큰 | 크기 | 굵기 | 행간 | 자간 | 용도 |
|---|---|---|---|---|---|
| `{typography.hero}` | clamp(38–58px) | 700 | 1.06 | -0.02em | 히어로 헤드라인 |
| `{typography.display-lg}` | clamp(28–42px) | 700 | 1.10 | -0.01em | 섹션 헤드 |
| `{typography.display-md}` | clamp(22–32px) | 600 | 1.20 | 0 | 서브 섹션 헤드 |
| `{typography.lead}` | 21px | 300 | 1.60 | 0 | 히어로 서브카피 |
| `{typography.body}` | 16px | 400 | 1.75 | 0 | 기본 본문 |
| `{typography.body-strong}` | 16px | 600 | 1.75 | 0 | 강조 인라인 |
| `{typography.caption}` | 13px | 400 | 1.50 | 0.04em | 캡션·보조 정보 |
| `{typography.label}` | 11px | 500 | 1.30 | 0.10em (uppercase) | 섹션 레이블·카테고리 태그 |
| `{typography.fine-print}` | 11px | 400 | 1.40 | 0.02em | 약관·법적 고지 |

### 원칙
- **명조 × 고딕 대비**: 헤드라인을 Gowun Serif로, 본문을 Noto Sans KR로. 둘 사이의 획 대비가 에디토리얼 리듬을 만든다.
- **자간은 명조에만 음수**: 대형 명조는 -0.01~-0.02em. Noto Sans KR 본문은 자간 0 (이미 최적화됨).
- **행간 1.75는 불변**: 사진 전문 학원 특성상 설명 텍스트가 읽혀야 함. Apple(1.47)보다 여유 있게.
- **weight 300은 lead에만**: 히어로 서브카피의 가벼운 공기감을 위해. 본문은 항상 400.
- **uppercase label**: 섹션 구분 레이블은 uppercase + 0.10em 자간. 아카이브 색인 느낌.

---

## 레이아웃

### 간격 시스템
- **기본 단위**: 8px. 구조 레이아웃은 8의 배수로 정렬.
- **섹션 패딩**: 96px (Apple 80px보다 여유 — 에디토리얼 공기감).
- **수평 패딩**: 44px (좁은 화면), 최대 컨텐츠 폭 1200px에서 auto margin.
- **카드 내부**: 28px.
- **이미지 ↔ 텍스트 간격**: 최소 40px.

### 그리드
- **싱글 컬럼 히어로**: 텍스트 중앙 정렬, 이미지 풀블리드.
- **2컬럼 분할**: 강사·과정 소개 (이미지 左 × 텍스트 右 또는 반전).
- **3컬럼 카드**: 과정 카드 그리드, gap 24px.
- **갤러리**: 2–3컬럼 masonry 또는 equal-height 그리드, gap 2–4px (타이트한 아카이브 배열).

### 화이트스페이스 철학
아카이브 에디토리얼에서 여백은 수동적 공간이 아니라 능동적 요소다.
사진 위아래로 최소 64px의 공기를 확보하고, 섹션 경계는 배경색 전환으로만 표시한다.

---

## 엘리베이션 & 깊이

| 레벨 | 처리 | 사용처 |
|---|---|---|
| 플랫 | 그림자·보더 없음 | 풀블리드 타일, 내비게이션, 히어로 이미지 |
| 웜 헤어라인 | 1px solid `{colors.warm-mid}` | 코스 카드, 통계 테이블 |
| 프로스트 글라스 | sub-nav: rgba(240,235,224,0.92) + blur(20px) | 서브 내비게이션 |
| 사진 그림자 | rgba(0,0,0,0.16) 0px 4px 24px | 사진이 서페이스에 놓일 때만 |

> **규칙**: 카드·버튼·텍스트에 그림자 없음. 사진 이미지에만 선택적으로 적용.

---

## 컴포넌트

### 내비게이션
- **gnav**: 고정 상단 바. `{colors.ink}` 배경, `{colors.on-dark}` 텍스트 12px. 높이 52px.
- **sub-nav**: gnav 아래 고정. 반투명 베이지 프로스트 글라스. 브랜드명 좌측, CTA 우측.

### 버튼
- **btn-primary**: 클레이 배경 + 크림 텍스트, `{rounded.sm}` (6px). Apple pill 아님 — 에디토리얼 감성의 직선.
- **btn-ghost**: 클레이 보더 + 클레이 텍스트, 투명 배경. 보조 CTA.
- **btn-ghost-dark**: 다크 서페이스용. accent-on-dark 클레이 라이트.
- **text-link**: 인라인 링크. underline 또는 클레이 색상으로만 구분.

> 버튼 액티브 상태: `transform: scale(0.97)`. Apple처럼 0.95까지 누르지 않음 — 좀 더 정적.

### 타일
섹션은 색 전환으로만 구분. 갭·보더 없음.
- **tile-cream** → **tile-parch** → **tile-dark** → **tile-parch** 순환 리듬.
- 연속 다크 섹션이 필요하면 **tile-dark-2** (#252320)로 미세 분리.

### 카드
- **course-card**: 화이트 배경, 웜 헤어라인 보더, 16px 라운딩. 과정·클래스 정보용.
- **gallery-frame**: 라운딩 없음. 이미지가 카드 = 갤러리 감각.

### 푸터
베이지(`{colors.parch}`) 배경, 웜 헤어라인 상단 구분선. 컬럼형 링크 목록, 11px fine-print.

---

## Do / Don't

### Do
- Gowun Serif 헤드라인에 `{colors.ink}` (#1a1a18)을 — 따뜻한 차콜이 베이지 위에서 빛난다.
- 모든 인터랙티브 요소에 `{colors.accent}` 클레이만 사용. 두 번째 액센트 색 없음.
- 사진은 풀블리드 또는 갭 없이. 프레임·보더 없음.
- 섹션 패딩 96px 이상 유지. 여백이 곧 품격.
- `{typography.label}` uppercase + 0.10em 자간 — 카테고리·레이블에 아카이브 색인 감각 부여.

### Don't
- 두 번째 액센트 색 도입하지 않는다 — 클레이 하나로 충분.
- 버튼에 그림자 넣지 않는다. 그림자는 사진에만.
- 풀블리드 타일에 border-radius 넣지 않는다. 타일은 직각.
- Noto Sans KR 본문 line-height를 1.75 아래로 줄이지 않는다.
- 다크 서페이스에서 `{colors.accent}` 직접 쓰지 않는다 — `{colors.accent-on-dark}` 라이트 클레이 사용.
- 장식 그라디언트 없음. 사진이 분위기를 만든다.

---

## 반응형

| 이름 | 폭 | 주요 변화 |
|---|---|---|
| 모바일 | ≤ 640px | 단일 컬럼, 섹션 패딩 48px, hero 글자 32px |
| 태블릿 | 641–1023px | 2컬럼 카드, 섹션 패딩 64px, gnav 축소 |
| 데스크톱 | 1024–1400px | 3컬럼 카드, 풀 레이아웃 |
| 와이드 | ≥ 1401px | 컨텐츠 1200px 고정, 여백 흡수 |

---

## 반복 가이드 (에이전트용)

1. 컴포넌트는 `{component.토큰}`, 색은 `{colors.토큰}`, 타이포는 `{typography.토큰}`으로만 참조.
2. 새 버튼 스타일 필요 시: ghost/primary 둘 중 하나에서 파생. 3번째 스타일 만들지 않는다.
3. 섹션 배경 순서: cream → parch → dark → parch. 연속 다크 필요 시 dark-2 사용.
4. 한국어 헤드라인: Gowun Serif 700. 영문 병기 시 같은 폰트로 weight 600.
5. 사진 그림자는 "이미지가 서페이스에 놓여있는" 연출에만. 플로팅 UI엔 사용 안 함.
6. accent 컬러 변경이 필요한 경우: accent 하나만 교체 → 전체 인터랙션 일관성 자동 유지.
