# 타임아카이브 사진전문학원 — Claude Code 프로젝트 컨텍스트

## 프로젝트 개요
타임아카이브 사진전문학원 홈페이지 리뉴얼 프로젝트.  
GitHub Pages로 배포 중이며, 모든 작업은 이 폴더(timearchive/)에서 관리한다.

- **라이브 URL**: https://vipermo15-dotcom.github.io/timearchive/
- **GitHub Repo**: https://github.com/vipermo15-dotcom/timearchive
- **배포 방법**: `bash deploy.sh` (auto-retry 내장)

---

## 학원 기본 정보
| 항목 | 내용 |
|------|------|
| 학원명 | 타임아카이브 사진전문학원 (Visual Art TIME ARCHIVE) |
| 원장 | **박희수** (30년 현장 경력) |
| 부원장 | 조영상 (Chapman 대학교, 대통령선거 전속촬영) |
| 주소 | 서울 강남구 언주로 113길 13 성창빌딩 2층 |
| 전화 | **02-545-5457** |
| 설립 | 1999년 |

### 원장 박희수 주요 이력
- 삼성전자·기아차·KB국민은행·GS홈쇼핑 광고 촬영
- 삼성 갤럭시 S10~S20 시리즈 제품 사진, 제일기획 협업
- 서울시립중부교육원 명예학과장

### 원장 철학
> "사진은 기술과 감성의 집합체입니다. 30년 현장 경험과 인문학을 통한 수업으로 꼭 필요한 기술과 감성을 집약합니다."

---

## 디자인 확정
**시안 B (아카이브)** 최종 확정.

### 확정 팔레트
| 토큰 | 값 | 용도 |
|------|-----|------|
| 딥그린 | `#2C4A47` | 메인 액센트 |
| 골드 | `#C9A84C` | 포인트 |
| 베이지 | `#EDEAE3` | 배경 |

### 로고 구조 (HTML/CSS)
```html
<span class="ta-logo">
  <span class="ta-script">Visual Art</span>   <!-- Pinyon Script -->
  <span class="ta-time">TIME</span>            <!-- 900 weight -->
  <span class="ta-archive">ARCHIVE</span>      <!-- letter-spacing .14em -->
  <span class="ta-kr">사진전문학원</span>
</span>
```

---

## 파일 구조
```
timearchive/
├── CLAUDE.md               ← 이 파일 (프로젝트 컨텍스트)
├── deploy.sh               ← GitHub Pages 자동 배포
├── index.html              ← 시안 비교 메인 페이지
├── viewer.html             ← 시안 전환/비교 뷰어
│
├── design-a-darkroom.html  ← 시안 A: 다크룸 (React 빌드)
├── design-b-archive.html   ← 시안 B: 아카이브 ✓ 확정 (React 빌드)
├── design-c-editorial.html ← 시안 C: 에디토리얼
├── design-d-chrome.html    ← 시안 D: 크롬
├── design-e-store.html     ← 시안 E: 스토어
├── design-f-editorial.html ← 시안 F: 에디토리얼 아카이브 × B팔레트
├── design-g-studio.html    ← 시안 G: 스튜디오 和 × B팔레트
├── design-h-visual.html    ← 시안 H: 비주얼 핀터레스트
│
├── data/                   ← 리서치·기획 문서
│   ├── 제안서-타임사진학원-20260630.md
│   ├── 사이트크롤링-20260630.md
│   ├── 사이트리서치-20260629.md
│   ├── 사이트크롤링-전체-20260629.md
│   ├── 수료생-인터뷰-대본-20260702.md
│   └── 카페24-이전-방안-20260702.md
│
├── docs/                   ← 설계 문서 (PRD, IA, 브랜드가이드 등)
│   ├── 00_PROJECT_RULE.md
│   ├── 01_PRD.md
│   ├── 02_BRAND_GUIDE.md
│   ├── 03_DESIGN_SYSTEM.md
│   └── ...
│
├── assets/                 ← 에셋 (git 추적 안함)
│   └── screenshots/        ← 작업 스크린샷 (19개)
│
└── skills/                 ← Claude Code 스킬
    └── time-archive-instagram.md
```

---

## 작업 규칙

### 코드
- 시안 C~H: **Vanilla HTML/CSS/JS** (프레임워크 없음)
- 시안 A/B: React 빌드 결과물 (직접 편집 금지)
- CSS는 `:root {}` 토큰 시스템 사용
- Google Fonts: Pinyon Script (로고), Pretendard (본문), Gowun Serif/Noto (일부 시안)

### 배포
```bash
bash deploy.sh   # push → 워크플로우 감시 → 실패시 수동 dispatch 자동 재시도
```

### 파일 추가 위치
| 종류 | 위치 |
|------|------|
| 리서치·기획 MD | `data/` |
| 설계·스펙 문서 | `docs/` |
| 로고·이미지 원본 | `assets/logos/` |
| 스크린샷 | `assets/screenshots/` |
| 새 시안 HTML | 루트 (`design-i-*.html` 형식) |

---

## 다음 단계 (as of 2026-07-05)
- [ ] 시안 B 기반 실제 제작 착수 (카페24 또는 직접 개발)
- [ ] 원장 프로필 실제 사진 확보 후 삽입
- [ ] 인스타그램 홍보 자동화 연동
- [ ] 수강생 후기 콘텐츠 수집·반영
