---
title:  "깃허브 블로그 생성하기"
excerpt: "깃허브 셋업 과정을 정리한 2번째 페이지입니다."

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 자료
tags:
  - 깃허브
  - github
  - blog
  - 블로그
---

# 생성

## 내 컴퓨터에서 호스팅하기

1. 샘플 블로그 생성

    ```ruby
    jekyll new helloBlog
    ```

    ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled.png)

2. 웹페이지 호스팅하기
    - 생성된 블로그 폴더로 이동

        ```bash
        cd helloBlog
        ```

    - 웹페이지 서버 호스팅
        - webrick 설치

            ```bash
            bundle add webrick
            ```

            ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%201.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%201.png)

            webrick을 설치하지 않는 경우
            cannot load such file — webrick 에러 발생

            ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%202.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%202.png)

    - 호스팅 서버 실행

        ```bash
        bundle exec jekyll serve
        ```

        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%203.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%203.png)

3. 웹페이지 접속하기
    - 내 컴퓨터에서 접속하기

        [](http://127.0.0.1:4000/)

    - 같은 공유기의 다른 장치에서 접속하기

        192.168.0.2는 현재 컴퓨터의 공유기 내부 IP 주소로 바꿔야 한다.

        ```bash
        bundle exec jekyll serve -H 192.168.0.2
        ```

        [](http://192.168.0.2:4000/)

4. minimal-mistakes 다운로드
    - 내 컴퓨터에 다운로드

        ```bash
        git clone https://github.com/mmistakes/minimal-mistakes.git
        ```

        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%204.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%204.png)

    - bundle 설치

        ```bash
        cd minimal-mistakes
        bundle
        ```

        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%205.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%205.png)

## github에서 호스팅하기

1. [github.com](http://github.com) 에서 계정 생성하기
2. repository 생성하기
    - create repository

        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%206.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%206.png)

    - Repository name - Owner명과 반드시 일치 시킬 것

        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%207.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%207.png)

    - Public / Private - Public

        ![https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%208.png](https://withmaster.github.io/assets/images/2021-07-29-create_blog/Untitled%208.png)

3. 내 컴퓨터에서 생성된 repository로 upload
    - 내 PC의 폴더명 변경(helloBlog → username)
    - 내 PC와 github 서버와 연결(username은 반드시 변경해주어야 함.)

        ```bash
        git remote remove origin https://github.com/username/username.github.io.git
        ```

    - 내 계정과 연결하기

        브라우저에 나오는 Authentication 하기(github.com에 로그인한 상태에서 아래 코드 실행)

        ```bash
        git push -u origin master
        ```

4. 블로그 접속하기

    [Site Title](https://withmaster.github.io/)