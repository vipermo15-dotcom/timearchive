# 08_NEXT_STEPS.md
# 타임아카이브 — 다음 작업 목록

> Claude Code에서 이 파일을 보고 다음 작업을 이어갑니다.
> 완료 시 [ ] → [x] 로 업데이트하세요.

---

## 현재 상태 (2026.06.30)

```
✅ 전략 기획 완료
✅ 두 시안 전체 개발 완료 (14개 섹션)
✅ GitHub Pages 배포 완료
✅ 원장님 피드백 페이지 + Formspree 알림 연동 완료
✅ 상담 폼 Formspree 실제 연동 완료 (mdarzydb → vipermo15@gmail.com)
✅ SEO 메타태그 추가 완료 (두 시안 모두)
✅ 사파사진학원 벤치마킹 완료 → 제안서 작성 완료
⏳ 원장님 시안 피드백 대기 중
```

---

## Phase 1 — 피드백 반영 (원장님 회신 후)

- [ ] 피드백 MD 파일 수신 확인 (vipermo15@gmail.com)
- [ ] 선호 시안 확인 (A 다크룸 / B 아카이브)
- [ ] 수정 요청 사항 목록화
- [ ] 확정 시안 기준으로 수정 적용
- [ ] GitHub 업데이트 → Pages 재배포

---

## Phase 2 — 실제 자료 교체

```
지금은 플레이스홀더(색상 그라데이션) 상태.
원장님에게 아래 자료를 받아야 함.
```

- [ ] **수강생 작품 사진** 수령
  - 인물·패션 3~5장
  - 제품·커머스 3~5장
  - 영상·릴스 썸네일 2~3장
  - AI 리터칭 Before/After 2~3쌍
- [ ] **원장 프로필 사진** 수령 (3:4 비율 권장)
- [ ] **수료생 인터뷰 영상** 수령 (유튜브 링크 또는 파일)
- [ ] 실제 이미지로 플레이스홀더 교체 (GalleryShowcase, MosaicPortfolio, Instructor)
- [ ] AI Before/After 토글 실제 이미지로 교체 (WorksGallery)

---

## Phase 3 — Supabase 상담 폼 연동 (선택 — Formspree로 이미 작동 중)

> ⚠️ 현재 Formspree로 실제 상담 신청이 vipermo15@gmail.com으로 전송됨.
> Supabase는 신청 내역을 대시보드로 조회하고 싶을 때 추가.

- [ ] Supabase 프로젝트 생성 (supabase.com)
- [ ] consultations 테이블 생성
  ```sql
  create table consultations (
    id uuid default gen_random_uuid() primary key,
    name text not null,
    phone text not null,
    course text,
    created_at timestamptz default now(),
    status text default '신규'
  );
  alter table consultations enable row level security;
  create policy "allow insert for all" on consultations
    for insert to anon with check (true);
  ```
- [ ] 빌드된 HTML에서 Formspree fetch 코드 → Supabase JS SDK 코드로 교체
- [ ] 폼 제출 테스트 확인

---

## Phase 4 — 카페24 배포

- [ ] 확정 시안 최종 빌드 (`esbuild entryA.jsx` 또는 `entryB.jsx`)
- [ ] 카페24 호스팅 신청
- [ ] FTP로 index.html + site.js 업로드
- [ ] timearchive.co.kr 임시 확인 (도메인 변경 전)
- [ ] 도메인 소유권 확인 (원장님 명의 여부)
- [ ] timearchive.co.kr 네임서버 → 카페24로 변경
- [ ] 도메인 적용 확인 (1~24시간)
- [ ] 기존 외주 호스팅 해지

---

## Phase 5 — 자동 연동 (P1 — 오픈 후 1개월)

- [ ] 인스타그램 비즈니스 계정 전환
- [ ] Instagram Graph API 토큰 발급
- [ ] INSTAGRAM_ACCESS_TOKEN + USER_ID 환경변수 입력
- [ ] 구글 시트 공지 연동 (CSV URL 입력)
- [ ] 카카오 채널 연동 (플로팅 버튼 추가)

---

## Phase 6 — SEO & 성능 (P2)

- [x] title, description, OG 태그, LD+JSON 구조화 데이터 추가 (2026.06.30)
- [ ] robots.txt + sitemap.xml 생성
- [ ] 네이버 서치어드바이저 등록
- [ ] Google Search Console 등록
- [ ] Core Web Vitals 최적화 (LCP < 2.5s)
- [ ] next/image로 이미지 최적화

---

## 추가 자료 (2026.06.30)

- `/Desktop/홍보-자동화/outputs/제안서-타임사진학원-20260630.md`
  - 사파사진학원 벤치마킹 전체 분석
  - 영상 과정 신설 3개 제안
  - AI 과정 신설 3개 제안
  - 홈페이지 리뉴얼 우선순위 / 마케팅 전략 / 실행 로드맵
  - 원장님 제출 전 검토 권장

---

## Claude Code 인수인계 메모

### 바로 작업 가능한 것 (자료 없어도)
1. Supabase 테이블 생성 + 코드 연결
2. Next.js 프로젝트로 이식 (app/page.tsx)
3. SEO 메타데이터 강화
4. 모바일 미세 조정

### 자료 받으면 바로 할 것
1. 실제 사진으로 플레이스홀더 교체
2. 인스타 자동 연동 활성화
3. 구글 시트 공지 연동 활성화

### 주의사항
- GitHub 토큰 `ghp_xxxx_재발급_필요` 는 7일 한시적 — 만료 시 재발급
- 5060 타겟: 폰트 18px 이상, 버튼 56px 이상 유지
- 시안 A/B 두 버전 모두 site/ 폴더에 보존
- timearchive15.kr 이 아닌 **timearchive.co.kr** 이 실제 도메인
