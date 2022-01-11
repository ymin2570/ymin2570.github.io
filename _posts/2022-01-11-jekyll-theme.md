---
title: "[Github 블로그] jekyll 테마를 이용하여 블로그 만들기"
layout: archive
categories: 
    - Github.io
tags: 
    - [Github.io, jekyll]
toc: true
date: 2022-01-11 01:00
---
------------------

jekyll 테마를 이용하여 깃허브 블로그 만드는 방법을 포스팅해야겠다고 생각한지 벌써 반년이 됐다.  
블로그도 본격적으로 시작한 김에 이 것부터 얼른 해치워야겠다 라는 생각으로 글 작성 시작!

## 1. 세팅하기
-------------------
제일 먼저 깔아야하는 것들이 있다.  
바로 Ruby와 Git 설치!  

### Git 설치
-------------------
<https://git-scm.com/downloads>  
위 Git 공식 사이트에서 설치를 진행하고  
```
$git --version
```
위 명령어를 통해 Git이 제대로 설치되었는지 확인할 수 있다.  

```
$git config --global user.name "name"
$git config --global user.email "your@email.com"
```
그 다음, 위 명령어를 통해 설정을 진행한다.  

```
$git config --list
```
위 명령어를 통해 설정한 내용을 확인할 수 있다.

### Ruby 설치
--------------------
<https://rubyinstaller.org/downloads/>  
위 사이트에서 자신의 운영체제에 맞게 WITH DEVKIT을 설치하면 된다.  
jekyll이 Ruby라는 언어로 만들어져서 반드시 설치해야한다.
```
$ruby --version
```
위 명령어를 통해 버전을 확인할 수 있다.  

### Jekyll Bundler 설치
-------------------
마지막으로 Bundler를 설치해줘야한다.  
설치하는 이유는 gem들의 올바른 버전을 추적하고 설치해서 일관된 환경을 제공하기 위함이라고 한다.  
```
$gem install jekyll bundler
```
위 명령어를 통해 Bundler까지 설치하면 기본 세팅 끝!  

## 2. Repository 생성하기
-------------------
![image](/assets/images/blog/repos.PNG)  
블로그 용으로 쓸 새로운 Repository를 위 사진처럼 githubID.github.io로 생성한다.  

그 다음 해당 repository로 이동하여  
![image](/assets/images/blog/blog_link.PNG)  
해당 Repository의 주소를 오른쪽 복사 버튼을 통해 복사한다.  

## 3. Local 폴더와 Repository 연동하기
--------------------
터미널 창을 켜서 폴더를 설치하고 싶은 위치로 이동한 다음
```
$git clone https://github.com/ymin2570/ymin2570.github.io.git
```
위와 같이 아까 복사해둔 Repository의 주소를 붙여넣기하면 로컬에 해당 Repository의 폴더가 생겼을 것이다.  
이렇게 하면 원격으로 연결이 된 것이다.  

## 4. 원하는 Jekyll 테마 다운로드하기
--------------------
<https://github.com/topics/jekyll-theme>
위 링크에서 다양한 테마를 확인할 수 있다.  
참고로 본인은 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes) 테마를 사용하고 있으며, 해당 테마를 추천한다. (다른 테마도 써봤는데 사람들이 많이 쓰는 데에는 이유가 있더라..)  

원하는 테마를 골랐다면 해당 테마의 Repository로 들어가서  
![image](/assets/images/blog/minimal.PNG)  
위 사진처럼 code 버튼을 누른 후, 제일 아래에 있는 Download ZIP 버튼을 눌러 테마를 다운로드해준다.  

이후 다운로드한 폴더를 전부 복사하여 3번에서 만들어둔 로컬 폴더에 붙여넣는다.  
여기까지 진행한 후에 commit을 하면 테마가 적용된 블로그를 확인할 수 있을 것이다.

## 5. 설정하기
------------------
우리 블로그는 우리 입맛대로 또 설정을 바꿔줘야겠지?

### _config.yml 파일 수정
------------------
내 정보를 입력하기 위해선 _config.yml 파일을 수정하면 된다.  

minimal-mistakes 테마를 기준으로 설명하면  
title, name, description, url, repository 부분과 그 밑에 author 부분을 기본적으로 수정하는 것을 추천한다.  
이외에 설정들은 직접 바꾸면서 어떤 것이 좋은지 커스터마이징하길 바란다.

## 6. Commit하기
-----------------
혹시나 commit하는 방법을 모르는 사람이 있을까봐 추가한다.  
```
$git add .
$git commit -m "message"
$git push origin --all
```
위 명령어 세 개를 통해 내 Repository로 Commit할 수 있다.  
두 번째 명령어에서 "message"는 무엇을 수정했는지 메모 정도의 느낌이라고 생각하면 된다.  

## 7. 글 작성하기
-----------------
블로그의 핵심이라고 할 수 있는 글 작성하는 방법이다.  
이는 _post 폴더에서 작성하면 되는데, 만약 해당 폴더가 없다면 생성하면 된다.  
글을 작성할 때 파일 이름은 YYYY-MM-DD-title.md 형식으로 생성하고, md 파일이기에 마크다운 형식으로 작성해야 한다.    
```
---
title: "[Github 블로그] jekyll 테마를 이용하여 블로그 만들기"
layout: archive
categories: 
    - Github.io
tags: 
    - [Github.io, jekyll]
date: 2022-01-11 01:00
---
```
머릿말은 위와 같이 작성하고, 그 아래에 글을 작성하면 된다.

모두들 즐겁게 블로그 운영하시길!