---
title:  "공공데이터 포털에서 데이터 수집하기"
excerpt: "공공데이터 포털에서 상권 정보 데이터 수집하기."

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 데이터 사이언스
tags:
  - data accquisition
  - MachineLearning
---

## 1. 개요

- [공공데이터포털 홈페이지](https://www.data.go.kr/index.do)

    ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled.png)

- 공공데이터포털은 공공데이터의 제공 및 이용 활성화에 관한 법률 제21조에 따라 공공기관이 생성 또는 취득하여 관리하는 공공데이터를 제공하고 있습니다.

## 2. 데이터의 종류

- 테마별

    총 16가지의 테마로 나뉘어진 데이터를 제공하고 있습니다.

    ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%201.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%201.png)

    ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%202.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%202.png)

- 국가중점 데이터별
    - 국가 중점 데이터는 수요 중심으로 개방의 효과성, 시급성 등이 높은 분야에 대한 데이터를 의미합니다.

    ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%203.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%203.png)

    - 더보기를 클릭하면, 건강보험심평원에서 제공하는 국민의료정보를 시작으로 100여 가지나 넘는 중점 데이터들을 확인할 수 있습니다.

        ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%204.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%204.png)

- 제공기관 유형별
    - 법률기관을 포함하여 8개로 분류되어 있습니다.

        ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%205.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%205.png)

    - 국가행정 기관을 클릭하면 아래와 같이 8,000건이 넘는 검색결과를 확인할 수 있습니다.

        ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%206.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%206.png)

## 3. 상권 정보 데이터 받아보기

- 영업 중인 전국 상가업소 데이터를 받아보도록하겠습니다.
1. 홈페이지 접속

    ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%207.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%207.png)

2. 검색창을 통해 찾아보겠습니다.

    ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%208.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%208.png)

3. 검색 결과 화면

    ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%209.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%209.png)

4. 상세 화면

    ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%2010.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%2010.png)

5. 다운로드
    - 오른쪽 위의 다운로드 버튼을 눌러서 zip 파일을다운받을 수 있습니다.
    - 267mb 파일의 압축을 풀어보니 1gb가 넘는 폴더가 생성되었고, 지역별 상가 정보를 포함하는 파일들을 포함하고 있습니다.
    - 서울은158mb이고, 경기는 253mb입니다. 수도권의 인구분포가 절반가량 되는 만큼 상권 데이터에 있어서도 파일 사이즈로만 40%가량을 차지하네요.

        ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%2011.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%2011.png)

6. 데이터 확인
    - 파일의 크기가 가장 작은 세종시 데이터의 내용입니다.

        ![https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%2012.png](https://withmaster.github.io/assets/images/2021-08-11-data_publicdata/Untitled%2012.png)