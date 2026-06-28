# 00_PROJECT_RULE.md
# 타임아카이브 홈페이지 리뉴얼 — Claude Code 인수인계 문서

> Claude Code에서 이 저장소를 열면 이 파일을 먼저 읽고 시작합니다.
> 모든 작업은 이 규칙과 아래 MD 파일들을 기준으로 진행합니다.

---

## 프로젝트 개요

**클라이언트:** 타임아카이브 사진전문학원
**목표:** 홈페이지 리뉴얼로 매출 향상 (상담 신청 전환율 1% → 5%)
**도메인:** timearchive.co.kr
**전화:** 02-545-5457
**설립:** 1999년 (27년 경력)
**GitHub:** github.com/vipermo15-dotcom/timearchive
**Pages URL:** https://vipermo15-dotcom.github.io/timearchive/
**알림 이메일:** vipermo15@gmail.com

---

## 현재 진행 상태 (2026.06.28 기준)

```
✅ 완료
├── 전략 기획 (PRD, 브랜드, IA, 디자인 시스템)
├── 전체 랜딩페이지 2개 시안 개발 완료
│   ├── 시안 A: 다크룸 (검정 + safelight red)
│   └── 시안 B: 아카이브 (종이톤 + 명조 + teal)
├── GitHub Pages 배포 완료
│   └── https://vipermo15-dotcom.github.io/timearchive/
├── 원장님 피드백 페이지 (Formspree mdarzydb 연동)
└── 피드백 이메일 수신 테스트 완료

⏳ 대기 중
└── 원장님 시안 피드백 수신 → 시안 확정

🔜 다음 작업
├── 확정 시안으로 실제 작품 사진 교체
├── 카페24 호스팅 이전 설정
├── timearchive.co.kr 도메인 연결
└── Supabase 상담 폼 연동
```

---

## 파일 구조 (이 저장소)

```
timearchive/                          ← GitHub 저장소 루트
├── docs/                             ← Claude Code 인수인계 MD
│   ├── 00_PROJECT_RULE.md            ← 지금 이 파일 (먼저 읽기)
│   ├── 01_PRD.md                     ← 제품 요구사항
│   ├── 02_BRAND_GUIDE.md             ← 브랜드 전략
│   ├── 03_DESIGN_SYSTEM.md           ← 디자인 토큰 & 컴포넌트
│   ├── 04_IA.md                      ← 정보구조 & 사이트맵
│   ├── 05_COMPONENT_GUIDE.md         ← 컴포넌트 구조 & 테마 시스템
│   ├── 06_DEPLOY_GUIDE.md            ← 카페24 배포 & 도메인 가이드
│   ├── 07_OPERATION_GUIDE.md         ← 원장님 운영 가이드
│   └── 08_NEXT_STEPS.md              ← 다음 작업 목록 & 체크리스트
├── index.html                        ← 원장님 피드백 페이지 (배포 중)
├── design-a-darkroom.html            ← 시안 A 미리보기
├── design-b-archive.html             ← 시안 B 미리보기
└── README.md
```

---

## 기술 스택

| 항목 | 기술 |
|---|---|
| 프레임워크 | Next.js 14 (App Router) |
| 언어 | TypeScript + JSX |
| 스타일 | Inline styles + CSS-in-JS (테마 토큰) |
| 애니메이션 | Framer Motion (예정) / 현재 CSS transition |
| DB | Supabase (상담 폼 저장) |
| 피드백 알림 | Formspree (ID: mdarzydb) |
| 호스팅 | 카페24 (예정) / GitHub Pages (현재) |
| 도메인 | timearchive.co.kr |

---

## Claude Code 작업 규칙

1. **항상 이 docs/ 폴더를 먼저 읽고 시작**
2. 작업 완료 시 해당 MD 파일 업데이트
3. 새 컴포넌트 추가 시 05_COMPONENT_GUIDE.md 반영
4. 배포 관련 변경 시 06_DEPLOY_GUIDE.md 반영
5. **토큰은 절대 코드에 하드코딩 금지** (.env 사용)
6. GitHub Personal Access Token: 만료 후 재발급 필요 (7일)

---

## 핵심 연락처 & 계정

| 항목 | 값 |
|---|---|
| GitHub ID | vipermo15-dotcom |
| 알림 이메일 | vipermo15@gmail.com |
| Formspree ID | mdarzydb |
| 학원 전화 | 02-545-5457 |
| 도메인 | timearchive.co.kr |
