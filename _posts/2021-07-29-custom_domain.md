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

## 개별 도메인 등록하기
* 개별 도메인을 이용하면 접속 주소를 짧게 할 수 있어서 방문자가 쉽게 기억할 수 있다.
* 호스팅 회사에서 제공하는 도메인은 3차 도메인(예 username.github.com) 또는 4차 도메인(username.tistory.co.kr)으로 긴 명칭을 가지게 된다.
* 또한, 개별 도메인을 사용하면 호스팅 서버를 변경하더라도 동일한 도메인을 사용할 수 있다.
* 다른 블로그들에서는 가비아를 많이 추천하고 있다. 난 별 생각없이 cafe24에서 샀어서 이걸 이용하기로 한다.
>* 도메인 구입
>    * [웹을 넘어 클라우드로. 가비아](https://www.gabia.com/)
>    * [후이즈](https://domain.whois.co.kr/)
>    * [호스팅.kr](https://www.hosting.kr/)
>    * [카페24 호스팅센터](https://hosting.cafe24.com/)


## DNS 설정

1. 도메인 관리
    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled.png)

2. 도메인 부가 서비스 - DNS 관리 
    - 호스트 IP(A 레코드) 관리
      - `185.199.108.153` ~ `185.199.111.153` 중에 하나를 입력한다.
    - 별칭(CNMAE) 관리
      - `www`, `withmaster.github.io` 입력한다.

    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%201.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%201.png)

## Github pages 설정

1. Settings - Pages 이동
    * Your site is published at https://username.github.io가 떠 있으면 정상적으로 호스팅하고 있음을 의미한다.
    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%202.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%202.png)

2. Custom domain - Save  
    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%203.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%203.png)
    ![https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%204.png](https://withmaster.github.io/assets/images/2021-07-29-custom_domain/Untitled%204.png)

3. Enforce HTTPS 체크한다.
