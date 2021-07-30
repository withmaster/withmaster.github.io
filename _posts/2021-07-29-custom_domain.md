---
title:  "개별 도메인 등록하기"
excerpt: "깃허브 셋업 과정을 정리한 6번째 페이지입니다."

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

# 개별 도메인 등록

## 커스텀 도메인 등록

- 도메인 구입
    - www.withmaster.com

        [웹을 넘어 클라우드로. 가비아](https://www.gabia.com/)

        [](https://domain.whois.co.kr/)

        [](https://www.hosting.kr/)

        [카페24 호스팅센터](https://hosting.cafe24.com/)

## 커스텀 도메인 설정

1. 도메인 관리

    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled.png)

2. 도메인 부가 서비스 - DNS 관리 
    - 호스트 IP(A 레코드) 관리 - `185.199.109.153`
    - 별칭(CNMAE) 관리 - `www`

    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%201.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%201.png)

## Github pages 설정

1. Settings - Pages 이동

    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%202.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%202.png)

2. Custom domain - Save

    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%203.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%203.png)

    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%204.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%204.png)

3. Enforce HTTPS 체크

## 서브 도메인 등록

1. cafe24 - 도메인 부가 서비스 - DNS 관리 - 별칭(cName) 관리

    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%205.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%205.png)

2. GitHub Pages - 서브 도메인 입력 - save