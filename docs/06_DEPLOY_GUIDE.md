# 06_DEPLOY_GUIDE.md
# 타임아카이브 — 배포 가이드

---

## 1. 배포 환경 (확정)

| 항목 | 값 |
|---|---|
| 도메인 | **timearchive.co.kr** |
| 호스팅 | **카페24** (기존 외주 호스팅 → 이전) |
| 현재 임시 배포 | GitHub Pages (https://vipermo15-dotcom.github.io/timearchive/) |
| 상담 폼 알림 | Formspree ID: mdarzydb → vipermo15@gmail.com |
| 상담 폼 저장 | Supabase (미연결 → P0 완료 후 연결) |

---

## 2. 카페24 이전 순서

```
① 원장님 시안 피드백 수신
② 확정 시안으로 실제 사진 교체 + 최종 빌드
③ 카페24 호스팅 신청
④ 완성 파일 2개를 카페24 FTP public_html에 업로드
   - index.html
   - site.js
⑤ timearchive.co.kr 네임서버를 카페24로 변경
⑥ 1~24시간 후 도메인 적용 확인
⑦ 기존 외주 호스팅 해지
```

> ⚠️ **중요:** 새 사이트를 카페24에 먼저 올려서 확인한 뒤,
> 도메인 네임서버를 바꿔야 기존 사이트 공백이 없습니다.

---

## 3. 빌드 및 카페24 업로드

```bash
# 1. 확정 시안 번들 생성 (A 또는 B)
./node_modules/.bin/esbuild entryA.jsx \
  --bundle --outfile=site.js \
  --loader:.jsx=jsx --jsx=automatic

# 2. 카페24 FTP 업로드
# FileZilla 또는 카페24 웹 FTP 사용
# 접속: 카페24 관리자 → 호스팅 관리 → FTP 정보
# 업로드 위치: public_html/
#   - index.html  (빌드된 HTML)
#   - site.js     (번들 파일)
```

**index.html 구조:**
```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>타임아카이브 사진전문학원 | 사진·영상·AI 1:1 아카데미</title>
  <meta name="description" content="27년 경력 현직 작가에게 1:1로 배웁니다. 사진·영상·AI를 한 번에, 100% 실습으로.">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css">
  <!-- 시안 B만 추가 -->
  <!-- <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@500;700&display=swap" rel="stylesheet"> -->
</head>
<body>
  <div id="root"></div>
  <script src="./site.js"></script>
</body>
</html>
```

---

## 4. 환경 변수 (.env.local)

```bash
# Supabase (상담 신청 저장)
NEXT_PUBLIC_SUPABASE_URL=https://xxxxx.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJxxxxx...

# Instagram (작품 피드 — P1)
INSTAGRAM_ACCESS_TOKEN=IGQVxxxxx...
INSTAGRAM_USER_ID=178xxxxx

# 구글 시트 공지 (공개 CSV — 키 불필요)
NEXT_PUBLIC_NOTICE_SHEET_URL=https://docs.google.com/.../pub?output=csv
```

---

## 5. SEO 메타데이터

```tsx
// app/layout.tsx
export const metadata = {
  title: "타임아카이브 사진전문학원 | 사진·영상·AI 1:1 아카데미",
  description: "27년 경력 현직 작가에게 1:1로 배웁니다. 사진·영상·AI를 한 번에, 100% 실습으로. 쇼핑몰 창업·제품 촬영·영상 편집까지.",
  keywords: ["사진학원","영상편집학원","AI사진보정","쇼핑몰사진","1:1사진레슨","타임아카이브"],
  openGraph: {
    title: "타임아카이브 | 사진·영상·AI 1:1 전문 아카데미",
    description: "찍고, 편집하고, 팔리게 만든다.",
    type: "website", locale: "ko_KR",
  },
};

// 구조화 데이터
const jsonLd = {
  "@context": "https://schema.org",
  "@type": "EducationalOrganization",
  name: "타임아카이브 사진전문학원",
  foundingDate: "1999",
  telephone: "02-545-5457",
  url: "https://timearchive.co.kr",
  areaServed: "KR",
};
```

---

## 6. 도메인 연결 (timearchive.co.kr)

```
현재 도메인 관리자 → 카페24 네임서버로 변경:
ns1.cafe24.com
ns2.cafe24.com
ns3.cafe24.com

또는 A 레코드: 카페24 호스팅 IP로 지정
(카페24 관리자 → 호스팅 정보에서 IP 확인)
```

> ⚠️ 도메인 소유권이 원장님 명의인지 기존 외주사 명의인지 먼저 확인 필요.
> 외주사 명의면 이전 요청 후 진행.

---

## 7. 배포 전 체크리스트

```
실제 자료
- [ ] 수강생 작품 사진 (인물/제품/영상/AI 카테고리별 각 3~5장)
- [ ] 원장 프로필 사진
- [ ] 수료생 인터뷰 영상 (유튜브 링크 또는 직접 파일)

연동 설정
- [ ] Supabase 테이블 생성 + API 키 입력
- [ ] 상담 폼 코드 주석 해제 (Sections3.jsx Consult)
- [ ] 인스타그램 비즈니스 계정 전환 + 토큰 발급 (P1)
- [ ] 구글 시트 공개 CSV URL 입력 (P1)

배포
- [ ] 최종 빌드 확인 (에러 0)
- [ ] 모바일 실기기 테스트
- [ ] 카페24 FTP 업로드
- [ ] timearchive.co.kr 도메인 연결
- [ ] 기존 외주 호스팅 해지
```
