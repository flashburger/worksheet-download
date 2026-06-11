# CLAUDE.md — worksheet-download

## 프로젝트 개요

초등학생 수학 학습지를 무료로 출력하거나 PDF로 저장할 수 있는 사이트.
GitHub Pages로 운영하는 정적 사이트 (HTML/CSS/JS).

---

## 핵심 가치

- **회원가입 없이** 바로 이용
- **프린트 최적화** 레이아웃
- **깔끔한 디자인** (321st Art 퀄리티)
- 학년/단원 구조가 명확해서 **찾기 쉬움**

---

## 타겟 사용자

- 초등학생 자녀를 둔 **학부모** (집에서 프린트해서 아이에게)
- 페인포인트: 괜찮은 학습지 찾기 귀찮음, 회원가입 장벽, 프린트 레이아웃 깨짐

---

## 사이트 구조 (MVP)

```
index.html              — 메인 (학년/단원별 카드 탐색)
/worksheets/            — 학습지 HTML 파일 보관
    2grade-length.html  — 예시: 2학년 길이재기
    1grade-addition.html
    ...
/assets/                — 이미지, 공통 CSS, JS
```

---

## 핵심 UX 플로우

```
index.html 카드 클릭
        ↓
/worksheets/[학습지].html (학습지 페이지)
        ↓
  [📄 PDF 저장]  [🖨 바로 출력]  ← 버튼 두 개
        ↓
window.print() 실행
```

- 학습지 페이지 자체가 웹페이지로 존재
- PDF 저장 = 프린트 다이얼로그에서 PDF로 저장
- 바로 출력 = 프린트 다이얼로그 바로 실행
- 버튼은 프린트 시 숨김 처리 (`@media print { display: none }`)

---

## 콘텐츠 방향

- 학습지는 HTML로 직접 제작 (AI 보조 활용)
- A4 프린트 최적화 레이아웃
- 학년별/단원별 분류 (1~6학년)

---

## 학습지 HTML 디자인 기준

- `page-wrap` 구조 (흰 카드, 둥근 모서리, 그림자)
- 문제 번호는 파란 원형 배지
- 빈칸은 파란 밑줄 스타일 (`class="blank"`)
- 정답 영역은 점선으로 분리 (하단 고정)
- 버튼은 우측 상단, 프린트 시 숨김 (`class="no-print"`)
- Google Fonts Nanum Gothic 사용
- 모바일 반응형 포함

---

## 기술 스택

- HTML / CSS / JavaScript (순수, 프레임워크 없음)
- GitHub Pages 배포
- 도메인 없이 운영 → 반응 좋으면 추후 커스텀 도메인 연결

---

## 수익화 계획

1. **현재**: 무료 운영, 트래픽 확보
2. **단기**: Google AdSense 광고 삽입
3. **장기**: 프리미엄 학습지 유료 다운로드, 도메인 연결

---

## 배포 방법

```bash
git add .
git commit -m "변경내용"
git push origin main
```

push 후 GitHub Actions에서 자동 배포 (1~2분 소요)
사이트 URL: https://flashburger.github.io/worksheet-download

---

## 디자인 원칙

- 밝고 깔끔한 톤 (학부모 대상)
- 모바일에서도 잘 보여야 함 (스마트폰으로 접속해서 바로 출력)
- 과도한 장식 금지, 기능 중심

---

## 작업 시 주의사항

- 정적 사이트이므로 백엔드 없음 (회원가입, DB 불가)
- 학습지는 PDF가 아닌 HTML 파일로 제작
- 새 학습지 추가 시: `/worksheets/`에 HTML 파일 추가 + `index.html` 카드 추가
- 외부 폰트는 Google Fonts 사용 가능