---
title: "[Github 블로그] Repository 변경 (블로그로 잔디심는법)"
categories: 
    - Github.io
tags: 
    - [Github.io]
toc: true
date: 2022-01-10 20:40
---
------------------

오늘 깃허브 블로그용 Repository를 변경해보았다.  


> 변경한 이유 ?
-------------------------

블로그를 만들 때 jekyll 테마를 fork하여 Repository의 이름만 변경해서 그대로 사용하였다.  
하지만 해당 Repository에 commit을 했을 때, fork한 Repository여서 깃허브의 잔디가 심어지지 않았다.  
이를 해결하기 위하여 새로운 Repository를 생성하였다.

물론 이전에 했던 commit들은 아까우니까 ~~(뭐 별로 하지도 않았지만..)~~  
어떻게 방법이 없나 물색하던 도중..  

**한 블로그를 찾아서 이를 해결하였다!**  
해결 방법은 아래와 같다.

## 새로운 Repository 생성

![image](/assets/images/blog/new_repo.PNG)  
우선 기존 Repository를 복사할 새로운 Repository를 생성하였다.

## 복사할 Repository 링크 복사

![image](/assets/images/blog/blog_link.PNG)  
위 링크 옆 복사하기 버튼을 눌러 링크를 복사한다.  
이후 터미널을 켠 뒤,   
```
$git clone --bare https://github.com/ymin2570/ymin2570.github.io.git
```
위와 같은 명령어를 입력하여 bare clone을 진행한다.  
물론 위 링크부분은 복사할 Repository 링크이다. (fork한 Repository)

## 생성된 디렉토리에서 Mirror push

위 명령어로 Bare clone을 진행하였다면, ymin2570.github.io.git 이라는 디렉토리가 생성되었을 것이다.  
```
$cd ymin2570.github.io.git
$git push --mirror https://github.com/ymin2570/new_repos.git
```
위 명령어 두 줄을 입력하면 새로운 Repository에 복사가 된다!  
여기까지 진행했다면, fork를 한 Repository에 commit하여 깔리지 않던 잔디가 전부 깔렸을 것이다.

이제 fork했던 기존 Repository는 삭제하고  
새로운 Repository인 new_repos를 ymin2570.github.io로 이름을 변경한다.

이후 git clone을 통해 로컬 저장소와 연결까지 하면 끝!  
이제부터 새로운 글을 작성할 때마다 잔디가 깔릴 것이다.

모두들 블로그 작성하며 잔디가 깔리는 편안함을 느끼시며 행복하게 공부하시길~  
**화이팅!**

참고한 블로그 링크 : <https://soranhan.tistory.com/11>
