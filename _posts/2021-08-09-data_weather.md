---
title:  "기후 데이터를 구해보자"
excerpt: "기상 자료 개발 포털로부터 데이터 수집하기."

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 데이터 사이언스
tags:
  - data
  - MachineLearning
---


## 개요

[기상자료개방포털이란?](https://data.kma.go.kr/cmmn/static/staticPage.do?page=intro)

* 기상과 관련하여 기상청에 의해 수집된 모든 데이터가 제공되고 있습니다. 
* 다만, 실시간 기상 정보는 제공하고 있지 않습니다.    

## 데이터의 종류

1. 데이터 Tab

    ![https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled.png](https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled.png)

2. 기후통계분석 Tab

    ![https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled%201.png](https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled%201.png)

3. 간행물 Tab

    ![https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled%202.png](https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled%202.png)

## 기온데이터 수집하기(예시)

1. [기후통계분석 탭 - 기온분석 클릭]      

2. 검색 조건 입력

    ![https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled%203.png](https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled%203.png)

    - 자료구분 : `일`, `월`, `계절`, `년`
    - 자료형태 : `기본`
    - 기간 : `시작일` ~ `종료일`
        - `시작일` 1904년 1월 1일부터 제공되고 있습니다.
    - 지역/지점

        ![https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled%204.png](https://withmaster.github.io/assets/images/2021-08-09-data_weather/Untitled%204.png)

    - 검색 후 데이터 형식(`CSV`, `Excel`) 선택하여 저장하기
        - 자신이 분석할 툴에 따라 선택하면 됩니다.