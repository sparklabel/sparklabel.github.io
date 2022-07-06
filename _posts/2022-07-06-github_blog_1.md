---
title:  "[Github Pages] Jekyll Theme로 Github 블로그 만들기_1"
excerpt: "YearDream offline group4"

toc: true                         # 목차
toc_sticky: true                  # 목차 사이드바 고정
  
published: true                   # 배포 여부

categories:
  - Git
tags:
  - Github
  - Github Pages
  - Blog
last_modified_at: 2022-07-05T10:30:00+09:00
sitemap:
  changefreq: daily
  priority: 0.8
---

## 준비사항

### 1. ruby 설치
아래 링크에 따라 설치 합니다.  
https://ryureka.github.io/blog/GitHub-블로그-만들기(2)-개발-환경-구축하기/

## Github Pages로 블로그 만들기
Jekyll Theme 중 하나인 minimal mistake를 활용합니다.

### 1. Github 계정 만들기
깃허브 계정만드는 방법은 흔하디 흔한 회원가입 과정과 비슷하니 구글링으로 쉽게 검색해 봅니다.  
허나, 그것도 귀찮으신분들을 위해 [가입 과정 상세 안내 링크](https://www.lainyzine.com/ko/article/how-to-create-github-account/ "Lainyzine님 블로그") 걸어 드려요.^^  
(이하 'USERNAME'은 자신의 Github USERNAME 입니다.)

### 2. jekyll theme fork - minimal mistake
[jekyll Theme (minimal mistake) Repository](https://github.com/mmistakes/minimal-mistakes "minimal mistake")로 방문하여 우측 상단 'fork'클릭 후 'USERNAME/minimal-mistakes' Repository 생성합니다.

<center><img src="../../assets/images/github_blog_1_2.png" width="80%"></center>

### 3. 리포지토리 이름 변경
생성된 레포지토리 내 __'Settings ==> General'__ 를 클릭하거나 아래 URL로 이동 후, Repository name을 'USERNAME.github.io'를 입력하고 'Rename'을 클릭합니다.
```html
https://github.com/USERNAME/minimal-mistakes/settings
```
<center><img src="../../assets/images/github_blog_1_3.png" width="80%"></center>

### 4. 로컬 저장소 생성
CLI에서 로컬 저장소로 사용할 곳을 찾아 원격 저장소의 소스를 clone합니다.  
*참고: 클론 시 'USERNAME.github.io'로 하위 폴더 생성  
(로컬 저장소 = 내 컴퓨터 내 저장소 / 원격 저장소 = Github 내 저장소)
```python
$ git clone https://github.com/USERNAME/USERNAME.github.io.git
```

### 5. 브랜치 생성
gh-pages 및 remotes/origin/gh-pages 브랜치를 생성합니다.

```python
$ cd USERNAME.github.io
$ git checkout master # master 브랜치로 이동
$ git checkout -b gh-pages master 
  # git checkout -b {local branch name} {remote branch name}
$ git push origin gh-pages
$ cd ..
```

### 6. Source 브랜치 설정
리포지토리의 __'Settings ==> Pages'__ 를 클릭하거나 아래 URL로 이동하여 'Source' 브랜치를 gh-pages로 변경합니다.
```html
https://github.com/USERNAME/minimal-mistakes/settings/pages
```
<center><img src="../../assets/images/github_blog_1_6.png" width="80%"></center>

'Your site is published at https://USERNAME.github.io/'에 녹색불이 들어와 있으면 OK입니다.

### 7. 완료 확인
브라우저에 자신의 블로그 주소를 입력하여 사이트를 확인합니다. 
```html
https://USERNAME.github.io/
```
<center><img src="../../assets/images/github_blog_1_7.png" width="80%"></center>