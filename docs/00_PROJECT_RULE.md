# 00_PROJECT_RULE.md
# 타임아카이브 홈페이지 리뉴얼 — 프로젝트 허브

> Claude Code에서 이 저장소를 열면 이 파일을 먼저 읽고 시작합니다.
> 모든 작업은 이 규칙과 아래 MD 파일들을 기준으로 진행합니다.

---

## 프로젝트 개요

| 항목 | 내용 |
|------|------|
| 클라이언트 | 타임아카이브 사진전문학원 |
| 원장 | 박희수 (27년 경력, 현직 상업 사진작가) |
| 부원장 | 조영상 |
| 목표 | 홈페이지 리뉴얼 → 상담 신청 전환율 1% → 5% |
| 도메인 | timearchive.co.kr |
| 전화 | 02-545-5457 |
| 인스타그램 | @time_photoacademy |
| GitHub | github.com/vipermo15-dotcom/timearchive |
| Pages URL | https://vipermo15-dotcom.github.io/timearchive/ |
| 알림 이메일 | vipermo15@gmail.com |

---

## 현재 상태 (2026.06.30 기준)

```
✅ 완료
├── 전략 기획 (PRD, 브랜드, IA, 디자인 시스템)
├── 경쟁사 벤치마킹 — 사파사진학원(sappa.co.kr) 전수 분석
├── 기존 사이트 크롤링 — timearchive.co.kr 18페이지
├── 제안서 작성 — 영상/AI 커리큘럼 신설 전략
├── 전체 랜딩페이지 2개 시안 개발 완료
│   ├── 시안 A: 다크룸 (검정 + safelight red)
│   └── 시안 B: 아카이브 (종이톤 + 명조 + teal)
├── GitHub Pages 배포 완료
├── 상담 폼 Formspree 실제 연동 완료 (mdarzydb)
└── SEO 메타태그 추가 (og태그, LD+JSON 구조화 데이터)

⏳ 원장님 답변 대기 중
├── 🔵 홈페이지 시안 피드백 — A(다크룸) vs B(아카이브) 선택
└── 🟡 인스타그램 계정 유형 확인 — 비즈니스/크리에이터 여부

🔜 답변 오면 즉시 진행
├── 확정 시안으로 실제 작품 사진 교체
├── 인스타그램 Graph API 토큰 발급 → 피드 자동 연동
├── 카페24 배포 + timearchive.co.kr 도메인 연결
└── 카카오 채널 플로팅 버튼 추가
```

---

## 파일 구조

```
timearchive/
├── docs/                             ← 전략 · 기획 · 운영 문서
│   ├── 00_PROJECT_RULE.md            ← 지금 이 파일 (먼저 읽기)
│   ├── 01_PRD.md                     ← 제품 요구사항 · 타겟 · 커리큘럼 · KPI
│   ├── 02_BRAND_GUIDE.md             ← 브랜드 전략 · 카피 · 보이스
│   ├── 03_DESIGN_SYSTEM.md           ← 디자인 토큰 · 컴포넌트 · 반응형
│   ├── 04_IA.md                      ← 사이트맵 · 전환 흐름 · SEO
│   ├── 05_COMPONENT_GUIDE.md         ← 컴포넌트 구조 · 빌드 방법 · 연동 지점
│   ├── 06_DEPLOY_GUIDE.md            ← 카페24 배포 · 도메인 · 환경변수
│   ├── 07_OPERATION_GUIDE.md         ← 원장님 운영 가이드
│   └── 08_NEXT_STEPS.md              ← 다음 작업 체크리스트
│
├── data/                             ← 리서치 · 제안 자료
│   ├── 사이트크롤링-20260630.md       ← timearchive.co.kr 전체 크롤링 결과
│   └── 제안서-타임사진학원-20260630.md ← 사파 벤치마킹 + 영상/AI 커리큘럼 제안
│
├── index.html                        ← 원장님 피드백 페이지 (배포 중)
├── design-a-darkroom.html            ← 시안 A 미리보기
├── design-b-archive.html             ← 시안 B 미리보기
└── README.md                         ← 프로젝트 링크 모음
```

---

## 원장님 피드백 대기 항목 상세

### 🔵 시안 피드백 (가장 중요)

피드백 페이지: https://vipermo15-dotcom.github.io/timearchive/

| 시안 | 분위기 | URL |
|------|--------|-----|
| A · 다크룸 | 검정 배경, 어두운 암실 감성, 붉은 포인트 | https://vipermo15-dotcom.github.io/timearchive/design-a-darkroom.html |
| B · 아카이브 | 종이 베이지, 명조체, 클래식-모던 | https://vipermo15-dotcom.github.io/timearchive/design-b-archive.html |

원장님 선택 후 바로 할 것:
1. 확정 시안 기준으로 실제 사진 교체
2. 카페24 최종 빌드 + 업로드
3. timearchive.co.kr 도메인 전환

---

### 🟡 인스타그램 계정 확인

| 상태 | 다음 단계 |
|------|-----------|
| 비즈니스/크리에이터 계정 + Facebook 페이지 있음 | Meta 앱 생성 → 토큰 발급 → 홈페이지 피드 자동 연동 |
| 비즈니스/크리에이터인데 Facebook 페이지 없음 | Facebook 페이지 생성 대행 → 연동 |
| 개인 계정 | 비즈니스 전환 요청 후 진행 |

연동되면 홈페이지 인스타 피드 섹션(현재 색상 플레이스홀더)이 실제 사진으로 자동 교체됨.

---

## 원장님에게 받아야 할 자료 목록

```
사진 자료
├── 수강생 작품 사진 (각 3~5장)
│   ├── 인물·패션
│   ├── 제품·커머스
│   ├── 영상·릴스 썸네일
│   └── AI 리터칭 Before/After
├── 원장 프로필 사진 (3:4 비율 권장)
└── 수료생 인터뷰 영상 (유튜브 링크 또는 파일)
```

---

## 기술 스택

| 항목 | 기술 |
|------|------|
| 현재 배포 형태 | 단일 번들 HTML (esbuild 빌드) |
| 프레임워크 | React (JSX) |
| 피드백 알림 | Formspree (ID: mdarzydb → vipermo15@gmail.com) |
| 상담 폼 | Formspree 실제 전송 중 ✅ |
| 호스팅 (예정) | 카페24 |
| 호스팅 (현재) | GitHub Pages |
| 도메인 | timearchive.co.kr |

---

## 작업 규칙

1. **항상 이 docs/ 폴더를 먼저 읽고 시작**
2. 작업 완료 시 `08_NEXT_STEPS.md` 체크리스트 업데이트
3. 새 자료 추가 시 `data/` 폴더에 날짜 붙여 저장 (예: `크롤링결과-YYYYMMDD.md`)
4. **토큰·API키는 절대 코드에 하드코딩 금지**
5. GitHub Personal Access Token: 7일 한시적, 만료 시 재발급

---

## 핵심 계정 정보

| 항목 | 값 |
|------|-----|
| GitHub ID | vipermo15-dotcom |
| 알림 이메일 | vipermo15@gmail.com |
| Formspree ID | mdarzydb |
| 학원 전화 | 02-545-5457 |
| 인스타그램 | @time_photoacademy |
| 도메인 | timearchive.co.kr |
