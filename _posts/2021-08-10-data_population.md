---
title:  "행정안전부 데이터 수집하기"
excerpt: "행정안전부 포털에서 통계 데이터 수집하기."

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 데이터사이언스
tags:
  - data
  - MachineLearning
---

## 1. 개요

- [행정안전부 홈페이지](https://mois.go.kr/frt/a01/frtMain.do)
    - 행정안전부에서는 정책 입안과 관련하여 다양한 데이터를 제공하고 있습니다.
- 정책자료 - 통계

    ![https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled.png](https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled.png)

- 메뉴 - 정책자료 - 통계

    ![https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%201.png](https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%201.png)

## 2. 데이터의 종류

1. [통계연보·주제별 통계](https://mois.go.kr/frt/bbs/type001/commonSelectBoardList.do?bbsId=BBSMSTR_000000000013)

    ![https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%202.png](https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%202.png)

2. [승인통계](https://mois.go.kr/frt/bbs/type001/commonSelectBoardList.do?bbsId=BBSMSTR_000000000014)

    ![https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%203.png](https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%203.png)

3. [e-나라지표](https://mois.go.kr/frt/sub/a05/statistics/screen.do)

    ![https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%204.png](https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%204.png)

4. [주민등록 인구통계](https://jumin.mois.go.kr/)

    ![https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%205.png](https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%205.png)

5. [행정안전통계 시각화](https://data.mois.go.kr/mois/visual/statMain.do;jsessionid=-q29szU6GYoiLACdhOQN226KqIT5-jwZs7GunJDf.osafety20)

    ![https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%206.png](https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%206.png)

## 예시 - 2020년 10월 전국 인구 및 세대 현황 다운 받기

- 별도로 조작해볼 예정이므로 기간을 제외하고는 특별히 설정은 없습니다.
1. 행정구역
    - 기본 값
2. 등록구분
    - 기본 값
3. 조회기간
    - 월간
    - 2020년 10월~ 2020년 10월
4. 구분
    - 전부 체크
5. 정렬순서
    - 행정기관코드
    - 오름차순
6. 전체읍면동현황
    - 체크
7. CSV 파일 다운로드
    - 아래와 같은 파일이 다운됩니다.
    - 밑으로 내려가면 부산광역시를 포함하여 모든 행정구역이 포함되어 있습니다.
    - 정렬 순서를 행정기관코드로 했기 때문에 서울특별시가 가장 위에 나타나는 것을 알 수 있습니다.

    ![https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%207.png](https://withmaster.github.io/assets/images/2021-08-10-data_population/Untitled%207.png)