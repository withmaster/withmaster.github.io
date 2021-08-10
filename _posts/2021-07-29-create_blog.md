---
title:  "깃허브 블로그 생성하기"
excerpt: "깃허브 셋업 과정을 정리한 2번째 페이지입니다."

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 블로그
tags:
  - github
  - hosting

---

# 생성

## 블로그 생성하기
1. 샘플 블로그 생성
    * 아래 명령어를 실행시키는 폴더에 helloBlog라는 폴더 및 블로그가 생성된다.
    * 어디까지나 기본 블로그이므로 이런 방법이 있다는 것만 알아두자
    
        ```ruby
        jekyll new helloBlog
        ```
         ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled.png)

2. 테마가 적용된 블로그 생성하기
   * 참고 사항
     * 지킬(Jekyll)에는 다양한 테마가 적용된 블로그들이 많이 있다.
     * 초반에는 많은 사용자들이 있어서 자료를 찾기 쉽고, 무료로 제공되는 minimal-mistakes 테마를 이용해본다.
     *  Jekyll theme 콜렉션 사이트
        * http://jekyllthemes.org/
        * http://themes.jekyllrc.org/
        * https://jekyllthemes.io/
        
    * 내 컴퓨터에 minimal-mistakes 다운로드
        * minimal-mistakes 전체 소스 코드를 다운하는 과정이다.
        ```bash
        git clone https://github.com/mmistakes/minimal-mistakes.git
        ```
        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%204.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%204.png)
        

## 내 컴퓨터에서 호스팅하기
1. bundle 설치
    * 설치된 폴더로 들어가서 bundle을 설치한다.
        ```bash
        cd minimal-mistakes
        bundle
        ```
        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%205.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%205.png)
    * webrick은 내 컴퓨터에서 호스팅하기 위해 필요한 파일인데, 기본 패키지에 없으므로 추가한다.
        ```bash
        bundle add webrick
        ```
        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%201.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%201.png)
     
    * webrick을 설치하지 않으면 cannot load such file — webrick 에러가 발생할 수 있다.
        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%202.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%202.png)


1. 내 컴퓨터에서 호스팅하기
    > * 생성된 블로그 폴더로 이동해서 웹서버를 실행시킨다.
    > * 웹서버는 글 포스팅 및 각종 설정 변경시 빠른 확인을 위해 주로 사용하게 된다.    
    1. 내 컴퓨터에서 접속하기[](http://127.0.0.1:4000/)
        ```bash
        cd minimal-mistakes
        bundle exec jekyll serve
        ```
        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%203.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%203.png)

    2. 같은 공유기를 사용하는 다른 장치에서 접속하기
        * 192.168.0.2자리에는 현재 내 컴퓨터의 공유기 내부 IP 주소를 입력해야 한다.
            ```bash
            bundle exec jekyll serve -H 192.168.0.2
            ```
        [](http://192.168.0.2:4000/)
## github에서 호스팅하기

1. [github.com](http://github.com) 에서 계정 생성하기
   * username이 블로그의 방문주소로 이용되므로 신중하게 선택하자.

2. repository 생성하기
    * create repository 선택
        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%206.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%206.png)

    * Repository name - Owner는 생성한 username으로 Owner.github.io를 입력하면 된다.
        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%207.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%207.png)
    
    * Public / Private - Public 선택        
        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%208.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%208.png)

3. 내 컴퓨터와 repository 연결하기
    * 내 PC의 폴더명 변경(minimal-mistakes → username)
    * 내 PC와 github 서버와 연결(아래 코드에서 username은 반드시 변경해주어야 한다..)   
    * git remote는 원격 제어를 위한 명령어이다.
    * origin은 원격 저장소의 이름으로 github에 생성된 내 저장공간을 의미한다.
    * git remote remove origin은 최초 생성시에는 없어도 되지만, 다시 설치하는 경우에는 실행해주는 것이 좋다.
        ```bash
        git remote remove origin
        git remote add origin https://github.com/username/username.github.io.git
        ```
4. 내 컴퓨터에서 repository로 업로드하기 
    * 아래 코드는 origin이라는 이름을 가진 원격 저장소의 master 브랜치로 업로드 한다는 의미이다.
        ```bash
        git push -u origin master    
    * 참고 사항
        > * 여기서는 내 컴퓨터에서 minimal-mistakes를 다운(clone)받아서 git의 repository에 업로드(push)하는 방법을 사용하고 있다.
        > * minimal-mistakes의 소스를 곧바로 git의 repository로 복사(fork)하고, 내 컴퓨터로 다운(fetch)받는 방법도 있다는 것만 알아두자.
        > * https://www.youtube.com/watch?v=ACzFIAOsfpM&t=316s    ```

5. 블로그 접속하기

    [Site Title](https://withmaster.github.io/)