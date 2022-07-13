---
title:  "[Github Pages] Jekyll Theme로 Github 블로그 만들기_2"
excerpt: "판도 깔아뒀겠다 본격적인 Posting을 시작해보자"

toc: true                         # 목차
toc_sticky: true                  # 목차 사이드바 고정
  
published: true                   # 배포 여부

categories:
  - Git
tags:
  - Github page
  - Blog
  - Posting
last_modified_at: 2022-07-10T10:30:00+09:00
sitemap:
  changefreq: daily
  priority: 0.8
---

## Github Uploading
앞으로 posting할 때마다 수없이 반복해야 하는 조금은 번거롭지만 해두고 나면 다소 뿌듯할 수 있는 과정들이에요.

### 1. github 원격 repo 내 이슈 등록
첫 시작은 github 홈페이지로 로그인하여 이전 글에서 만들어둔 'USERNAME.github.io' repository로 들어가 신규 posting 작성을 위한 이슈를 오픈합니다.  
+ repo 내 'Issue' :arrow_right: 'New Issue'
<center><img src="../../assets/images/github_blog_2_1.png" width="80%"></center>

+ 또는 아래 URL로 직접 접속
```html
https://github.com/USERNAME/USERNAME.github.io/issues/new
```

+ 이슈 제목 및 내용 작성 :arrow_right: 'Submit new issue' 클릭 :arrow_right: 이슈 번호 확인 필수!!
<center><img src="../../assets/images/github_blog_2_2.png" width="80%"></center>


### 2. 이슈 번호와 일치하는 브랜치 생성
+ 생성된 이슈 번호 확인 후 아래 코드를 commandline에 입력하여 새로운 브랜치를 만듭니다.  
  (만약을 대비하여 tracking에 용이하도록 브랜치 명 'feature/{ISSUE_NUM}'로 설정)  
```python
$ cd USERNAME.github.io
$ git checkout gh-pages
$ git pull origin gh-pages
$ git checkout -b feature/{ISSUE_NUM} gh-pages
$ cd ..
```

### 3. 이슈 처리 - 파일 생성/수정
+ 파일의 추가 및 수정등의 업데이트 작업을 진행 합니다.
+ 이번에는 첫 작업인 만큼 랜딩페이지 제목 및 간단한 소개 부분 수정을 해볼께요.  
  전체적인 페이지의 설정은 repository 내의 '_config.yml' 에서 이루어 집니다.  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:bell: 아래 예시 :bell:

<blockquote>
<div class="language-yaml highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="s">$ vi _config.yml</span>
<span class="s">......</span>
<span class="na">locale                   </span><span class="pi">:</span> <span class="s2">"</span><span class="s">en-US" # 언어설정 "ko"=한국어</span>
<span class="na">title                    </span><span class="pi">:</span> <span class="s2">"</span><span class="s">Better Moment,</span><span class="nv"> </span><span class="s">Bright Future" # 제목</span>
<span class="s">......</span>
<span class="na">name                     </span><span class="pi">:</span> <span class="s2">"</span><span class="s">S.</span><span class="nv"> </span><span class="s">Park"  # 이름</span>
<span class="na">description              </span><span class="pi">:</span> <span class="s2">"</span><span class="s">Remark</span><span class="nv"> </span><span class="s">on</span><span class="nv"> </span><span class="s">the</span><span class="nv"> </span><span class="s">journey # 설명</span><span class="nv"> </span>
<span class="na">url                      </span><span class="pi">:</span> <span class="s2">"</span><span class="s">https://sparklabel.github.io"  # 블로그 주소</span>
<span class="s">......</span>
<span class="na">search                   </span><span class="pi">:</span> <span class="no">true</span> <span class="c1"># false  # 검색 허용(default)</span>
<span class="na">search_full_content      </span><span class="pi">:</span> <span class="no">true</span> <span class="c1"># false (default)</span>
<span class="s">......</span></code></pre></div></div>
</blockquote>

+ 위와 같이 vim을 활용하여 수정하거나 에디터를 활용해 수정된 '_config.yml' 파일을 로컬 저장소에 저장
+ 신규 포스팅을 등록할 경우 파일명 형식(마크다운 형식, 파일명: yyyy-mm-dd-filename.md)을 준수하여 '_post' 폴더에 저장합니다. 파일명 양식과 상이하면 블로그에서 보이지 않아요 :cry: 
+ 포스팅에 첨부되는 이미지의 경우 'assets' 폴더 내 'images' 폴더를 만들고 그 안에 넣어 두어야 활용하실 수 있습니다. 이 또한 폴더명 'images' 지켜주셔야 해요

### 4. 이슈 테스트
+ 아래와 같이 입력하여 로컬 내에서 feature/{ISSUE_NUM}의 상태를 확인합니다.

```python
$ cd USERNAME.github.io
$ bundle install
$ bundle exec jekyll serve --host localhost --port 4000
$ cd ..
```
<center><img src="../../assets/images/github_blog_2_3.png" width="100%"></center>

### 5. 로컬 사이트 확인 
```html
http://localhost:4000
```

<center><img src="../../assets/images/github_blog_2_4.png" width="80%"></center>
+ 'ctrl + c' 를 눌러 로컬 서버 중지하여 확인 종료

### 6. 정상 확인 후, 이슈 커밋
+ 로컬에서 정상 작동을 확인 하였으면 아래를 따라 이슈를 커밋 합니다.
```python
$ cd USERNAME.github.io
$ git add .
$ git commit -m "Create a temporary post #{ISSUE_NUM}"
$ cd ..
```

### 7. 머지와 푸시를 통한 웹 업데이트
+ 원격 repo의 브랜치들을 갱신하고 직접 'https://USERNAME.github.io'에 접속하여 확인합니다.
```python
$ cd USERNAME.github.io
$ git checkout gh-pages
$ git merge --no-ff feature/{ISSUE_NUM}
$ git push origin gh-pages
$ cd ..
```
<center><img src="../../assets/images/github_blog_2_5.png" width="80%"></center>

### 8. 이슈 닫기
+ 모든 이슈가 완결되었으면 github 홈페이지의 오픈된 이슈를 닫아줍니다.
<center><img src="../../assets/images/github_blog_2_6.png" width="80%"></center>  

이번 포스팅의 내용은 처음엔 매우 번거롭고 좀 복잡해보일 수도 있겠으나 몇번 반복하다 보면 식사 후 양치질과 같이 익숙해져 아주 쉽고 당연한 절차로 받아들이게 될거에요. :+1:  
<br>

---
## :bulb: 참고
원래 따로 포스팅으로 다루려 했으나... 요 몇일동안 윈도우를 애플로:question: 만들어보고자 노력하다 CLI를 뒤집어 엎는 바람에 주말을 통째로 날렸네요. 다음에는 이 주말의 얘기를 다룰까 싶어 아래 작은 친구들은 링크로 남겨둬요.  

### :one: jekyll 오류 해결
+ 처음부터 순서를 뒤죽박죽 깔게된 저의 전철을 밟지 마시길 바라며...
도움받은 블로그 링크걸어 둬요~ [jekyll 오류 해결 (부제: github 블로그 만들기)](https://velog.io/@minji-o-j/jekyll-%EC%98%A4%EB%A5%98-%ED%95%B4%EA%B2%B0)

### :two: favicon 준비 (favicon이 무엇인지는 [여기](https://en.wikipedia.org/wiki/Favicon "Favicon") 또는 [저기](https://namu.wiki/w/%ED%8C%A8%EB%B9%84%EC%BD%98 ))
아이콘으로 사용할 작은 벡터 이미지 파일(ex: png) 준비 후 확장자 'ico' 파일로 바꿔줍니다.  
/assets 폴더 내에 favicon.ico 파일을 넣어줍니다.
_includes 폴더 내에 head.html의 위쪽에 아래 내용을 추가해줍니다
```python
<!-- 20210119 ADD favicon-->
<link rel="icon" type="image/png" href="/assets/favicon.ico">
```