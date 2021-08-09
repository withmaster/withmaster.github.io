---
<<<<<<< HEAD
title:  "깃허브 개요"
=======
title:  "깃허브 - 컴퓨터에서 환경 설정"
>>>>>>> b9beeb50e407551c3c848c5c717d5e64c3ddef33
excerpt: "깃허브 셋업 과정을 정리한 1번째 페이지입니다."

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

# 개요

## 1. 관계도

- 내 컴퓨터, github, Jekyll의 관계도
- 지킬(Jekyll)은 루비(ruby)로 만든 정적 웹사이트 생성기(static websites generator)이다.
<<<<<<< HEAD

![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_0.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_0.png)

## 2. 설치하기
=======
- 지킬(Jekyll)을 설치하고, 싱행시키기 위해서는 루비(ruby)를 먼저 설치해야 한다.
- 루비(ruby)는 인터프리터 형식으로 실행되는 고기능 스크립트 언어이고, 객체지향언어이다.
- 
![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_0.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_0.png)

## 2. 전체적인 설치 과정
1. 내 컴퓨터에서 환경 설정
    * 루비(ruby), 지킬(Jekyll) 설치
    * 블로그 생성
2. 깃허브 계정 생성
    * 블로그 업로드(git push)
3. 커스터마이징
4. Page 및 Post 작성하기
5. 댓글 기능 추가하기
6. 커스텀 도메인 연결하기
7. 검색 사이트 등록하기
8. 광고 추가하기(예정)
>>>>>>> b9beeb50e407551c3c848c5c717d5e64c3ddef33

### 루비(Ruby) 설치

- [루비 다운로드](https://rubyinstaller.org/downloads/)
    - `⇒` 가르키는 것 다운로드

    ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_1.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_1.png)

- 설치 과정

    ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_2.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_2.png)

    ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_3.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_3.png)

    ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_4.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_4.png)

    ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_5.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_5.png)

    ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_6.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_6.png)

- MSYS2 설치 - 1 선택

    ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_7.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_7.png)

<<<<<<< HEAD
### 지킬(Jekyll) 설치하기
=======
### 4. 지킬(Jekyll) 설치하기
>>>>>>> b9beeb50e407551c3c848c5c717d5e64c3ddef33

- [지킬 홈페이지](https://jekyllrb.com/)
- 패키지 설치
    - command 실행
<<<<<<< HEAD

        ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_8.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_8.png)

        ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_9.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_9.png)

    - 설치 명령어 입력

        ```ruby
        gem install jekyll
        gem install minima
        gem install bundler
        gem install jekyll-feed
        gem install tzinfo-data
        ```
=======
        * 지킬(Jekyll)은 설치 파일이 아닌 루비 셸에서 설치할 수 있다.
        * Start Command Prompt with Ruby를 실행시키나        
        ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_8.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_8.png)
        ![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_9.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_9.png)

    - 설치 명령어 입력
        * 설치 위치를 따로 지정하지 않아도 된다.
            ```ruby
            gem install jekyll
            gem install minima
            gem install bundler
            gem install jekyll-feed
            gem install tzinfo-data
            ```
>>>>>>> b9beeb50e407551c3c848c5c717d5e64c3ddef33
