---
title:  "티머니 교통 데이터 수집하기"
excerpt: "티머니 홈페이지에서 교통 통계 데이터 수집하기."

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 데이터 사이언스
tags:
  - data
  - MachineLearning
---


## 1. 개요

- [티머니 홈페이지](https://pay.tmoney.co.kr/index.dev)

티머니는 교통카드 결제 서비스를 제공하는 회사입니다. 교통 카드의 소유자가 등록된 상태에서 대중 교통 이용을 위해 결제를하면 누가 언제 어디서 출발해서 어디에서 내리는지를 알 수 있고, 이를 통계 자료로 제공하고 있습니다.

## 2. 데이터의 종류

교통 카드 결제에 따라 발생하는 데이터를 이용한 통계를 제공하고 있으며, 2013년 1월부터 월 단위로 집계된 통계 자료를 제공하고 있습니다.

1. 버스정류장별 이용현황

    ![https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled.png](https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled.png)

2. 지하철 노선별 역별 이용현황

    ![https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%201.png](https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%201.png)

3. 지하철 유무임별 이용현황

    ![https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%202.png](https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%202.png)

4. 지하철 시간대별 이용현황

    ![https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%203.png](https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%203.png)

## 3. 대중 교통 데이터 받아보기

1. 좌측 상단에 `이용안내` 

    ![https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%204.png](https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%204.png)

2. `대중교통 통계자료`

    ![https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%205.png](https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%205.png)

3. 월간 교통카드 통계자료

    ![https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%206.png](https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%206.png)

4. 첨부파일 다운로드

    ![https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%207.png](https://withmaster.github.io/assets/images/2021-08-10-data_tmoney/Untitled%207.png)