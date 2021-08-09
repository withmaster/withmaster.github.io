---
title:  "검색 사이트에 내 블로그 등록하기"
excerpt: "깃허브 셋업 과정을 정리한 7번째 페이지입니다."

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

## Google Search Console 등록하기
> * 참고 사항
>    * 구글 검색 엔진에 웹사이트가 검색되도록 등록해주고, 구글 검색 결과가 어떻게 이뤄지고 있는지 모니터링 결과도 알려준다.
>    * 구체적으로 Google에서 웹사이트를 크롤링해서 색인 생성을 요청할 수 있고, 웹사이트의 Google 검색 트래픽 데이터(Google 검색에 사이트가 표시되는 빈도, 사이트를 표시하는 검색어, 검색 사용자가 검색어를 클릭하여 연결하는 빈도 등)를 확인할 수 있다. Search Console에 가입하지 않아도 시간이 지나면 구글이 웹사이트의 존재를 알아차리고 Google 검색결과에 포함된다. 하지만 Search Console에 가입해서 색인 생성을 요청하고 웹사이트 관리를 하면 보다 능동적으로 Google 검색 엔진이 웹사이트를 파악하고 개선할 수 있게 만들 수 있다.
1. Google Search Console 홈페이지
    [Google Search Console](https://search.google.com/search-console/about)

2. Select property type - `URL 접두어` 선택  
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled.png)
    * 도메인(Domain)
        * 서브도메인을 포함한 모든 URL을 통합으로 관리하는 방식이다.
        * 이 방식은 DNS verification만 지원하므로 [github.io](http://github.io/) 도메인을 사용하면 지원이 안된다.
3. 소유권 확인(Verify owvership)
    * 파일 다운로드
    * 최상위 폴더에 저장
    * 소유권 확인 - `속성으로 이동`      
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%201.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%201.png)
             
4. URL 검사(Inspectation)
    * URL 입력후 enter
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%202.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%202.png)

    * 색인 생성 요청
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%203.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%203.png)
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%204.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%204.png)

5. sitemap.xml 등록하기
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%205.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%205.png)

### Google Analytics 등록하기
> * 참고사항       
>     * 웹분석 도구로 구글 검색 엔진과는 별개로 사람들이 본인의 웹사이트를 어떻게 사용하는지 효과적으로 파악할 수 있게 해준다.
>     * Google search Console에서 구글 검색 엔진을 통해서 웹사이트에 유입되는 방문자 정보를 확인 할 수 있다면 Google Analytics는 웹사이트로 유입되는 모든 방문자의 정보를 확인할 수 있다. 이 방문자의 유입 경로는 네이버 검색, 다음 검색, 타사이트 추천, 직접 입력 등이 모두 포함된다. 이 외에도 방문자의 위치, 네트워크, 사용 기기 등의 정보도 확인할 수 있다. 이런 정보를 통해 주 방문자들의 현황을 파악하고 웹사이트 이용 만족도를 개선해서 더 좋은 웹사이트를 만들 수 있다.
* Google Analytics 구조   
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%206.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%206.png)

    - Google Analytics 방문
        [Google Analytics](https://analytics.google.com/analytics/web/provision/#/provision)
        [사용자 페이지](https://analytics.google.com/analytics/web/provision/#/a203159968w280572411p247767796/admin/tracking/tracking-code/)

    1. 계정 설정
        ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%207.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%207.png)
        - 계정이름 : 구글 애널리틱슬르 사용할 서비스의 소속명(예: 카카오 corp)
    2. 속성 설정
        ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%208.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%208.png)
        - 속성이름 : 카카오 뱅크
    3. 비즈니스 정보     
        ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%209.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%209.png)
    4. Google 애널리틱스 서비스 약관 계약     
        ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2010.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2010.png)

        - `_config.yml` 수정 - Tracking ID 입력
            ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2011.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2011.png)
            ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2012.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2012.png)

## Naver 검색 등록
1. 네이버 웹 마스터
    [네이버 서치어드바이저](https://searchadvisor.naver.com/)
2. 웹마스터 도구
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2013.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2013.png)
3. 사이트 등록      
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2014.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2014.png)
4. 사이트 소유 확인
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2015.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2015.png)
5. 사이트 맵 제출하기
    * [https://withmaster.github.io](https://withmaster.github.io) 클릭
        ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2016.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2016.png)

    * 요청 - 사이트맵 제출 - sitemap.xml - 확인
        ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2017.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2017.png)

## Bing
1. bing 웹마스터
    [Bing Webmaster Tools](https://www.bing.com/webmasters/about)
2. Google Search Engine 에서 가져오기 - 올
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2018.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2018.png)

## Daum
1. 다음 검색등록
    [](https://register.search.daum.net/index.daum)
2. 신규 등록
    ![https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2019.png](https://withmaster.github.io/assets/images/2021-07-29-search_engine/Untitled%2019.png)
