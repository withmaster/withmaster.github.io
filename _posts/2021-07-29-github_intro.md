---
title:  "깃허브 개요"
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

![https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_0.png](https://withmaster.github.io/assets/images/2021-07-29-github_intro/1_0.png)

## 2. 설치하기

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

### 지킬(Jekyll) 설치하기

- [지킬 홈페이지](https://jekyllrb.com/)
- 패키지 설치
    - command 실행

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