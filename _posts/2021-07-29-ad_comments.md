---
title:  "댓글 기능 등록하기"
excerpt: "깃허브 셋업 과정을 정리한 8번째 페이지입니다."

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

# 댓글 기능 등록

## Disque 가입
- 홈페이지

    [](https://disqus.com/)

- Get Started
- `I want to install Disqus on my site` 선택

    ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled.png)

- Create a new site

    ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%201.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%201.png)

- Select Plan - `Basic`

    ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%202.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%202.png)

- Install Disqus
    1. Selection Platform - `Jekyll`

        ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%203.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%203.png)

    2. Jekyll install instructions

        [YAML From Matter](https://jekyllrb.com/docs/front-matter/)
        [Universal Embed Code](https://withmaster-github-io.disqus.com/admin/install/platforms/universalcode/)

        ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%204.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%204.png)

    3. Configure Disqus

        ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%205.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%205.png)

    4. Setup Moderation

        ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%206.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%206.png)

## 블로그에 Disqus 정보 기입하기

- `_config.xml` 수정

    shortname : `withmaster-github-io`

    ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%207.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%207.png)

- `_pages/year-archive.md` 추가

    ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%208.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%208.png)

## 게시물에 댓글 기능 넣기

- `_config.xml` 수정 - post 게시물에 comments 기능 사용 설정

    ![https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%209.png](https://withmaster.github.io/assets/images/2021-07-29-ad_comments/Untitled%209.png)

- post별, page별 기능 추가 및 기능 제거 가능 - overriding