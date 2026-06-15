# computerdrug

매일 공부한 거 기록하는 랩노트. Jekyll + GitHub Pages.

## 새 글 쓰기 (이게 전부)

`_posts/` 에 `YYYY-MM-DD-제목.md` 파일 하나 만들고 위에 front matter:

```markdown
---
title: "글 제목"
date: 2026-06-16
tags: [docking, gromacs]
---

여기부터 마크다운으로 그냥 쓰면 됨.
코드, 표, 이미지 다 됨.
```

```bash
git add . && git commit -m "TIL: ..." && git push
```

push 하면 GitHub Pages가 알아서 빌드 → 배포. HTML 한 줄도 안 건드림.

## 페이지

- `/`        최근 글 목록
- `/tags/`   태그별 모아보기
- `/search/` 제목·본문·태그 키워드 검색

## 검색

`search.json` 이 빌드 때 모든 글을 색인하고, `/search/` 페이지에서
Simple-Jekyll-Search(순수 JS)가 실시간 필터. 플러그인 의존성 없음.

## 설정 (`_config.yml`)

- **유저 페이지** (`winningyear.github.io`) 로 쓰면 → `baseurl: ""`
- **프로젝트 페이지** (`winningyear.github.io/computerdrug`) 면 → `baseurl: "/computerdrug"` (현재 값)

## 로컬 미리보기 (선택)

```bash
bundle install
bundle exec jekyll serve
# http://localhost:4000/computerdrug/
```

## 이미지 넣기

`assets/img/` 에 파일 두고 글에서:

```markdown
![설명](/assets/img/figure.png)
```
