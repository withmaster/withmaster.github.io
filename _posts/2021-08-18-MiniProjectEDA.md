---
title:  "신용카드 사용자 연체 예측 AI 경진대회"
excerpt: "초짜의 생애 첫 EDA 탐방기"

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 데이터 사이언스
tags:
  - data accquisition
  - MachineLearning
---

## 1. Intro

1. 개요
    - 데이터를 보는 것을 좋아하는 직장인입니다.
    - 신용카드 사용자의 데이터를 이용하여 연체를 예측하는 EDA입니다.
    - 분류형 데이터를 위주로 분석을 할 예정입니다.
    - [colab 작업 파일 링크](https://colab.research.google.com/drive/1VL7FzXI2zuNNZ4S1zPVVstu-LyVaEqx8?usp=sharing)
2. 참고 자료

    [데이콘 페이지](https://dacon.io/competitions/official/235713/codeshare/2607?page=3&dtype=recent)

    [데이터 변수 설명](https://www.dacon.io/competitions/official/235713/talkboard/402821/)
    
    [나이와 소득의 관점으로 풀어보는 데이터 탐색(EDA)](https://dacon.io/competitions/official/235713/codeshare/2607?page=3&dtype=recent)

    [신용카드 예측 EDA](https://dacon.io/competitions/official/235713/codeshare/2519?page=3&dtype=recent)

    [입문자의 투박한 EDA](https://dacon.io/competitions/official/235713/codeshare/2494?page=4&dtype=recent)
    
    [Titanic Survival Predictions (Beginner)](https://www.kaggle.com/nadintamer/titanic-survival-predictions-beginner)

3.  라이브러리(Library)

    ```python
    # 분석용 라이브러리
    import numpy as np
    import pandas as pd

    # 시각화 라이브러리
    %matplotlib inline
    import seaborn as sns
    import matplotlib.pyplot as plt

    #ignore warnings
    import warnings
    warnings.filterwarnings('ignore')

    # matplotlib 한글 폰트 출력코드
    # 출처 : 데이터공방( https://kiddwannabe.blog.me)
    import matplotlib
    from matplotlib import font_manager, rc
    import platform

    try : 
        if platform.system() == 'Windows':
        # 윈도우인 경우
            font_name = font_manager.FontProperties(fname="c:/Windows/Fonts/malgun.ttf").get_name()
            rc('font', family=font_name)
        else:    
        # Mac 인 경우
            rc('font', family='AppleGothic')
    except : 
        pass
    matplotlib.rcParams['axes.unicode_minus'] = False
    ```

4. Read in the Data
    - CSV파일이므로 pd.read_csv를 사용합니다.

    ```python
    #import train and test CSV files
    train = pd.read_csv('train.csv')
    test = pd.read_csv("test.csv")

    #take a look at the training data
    train.describe(include="all")
    ```

    ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled.png)

## 2. Explore the Data

1. `train.shape`

    ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%201.png)

2. `train.head()`

    ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%202.png)

3. `train.describe(include='all')`

    ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%203.png)

4. `train.info()`

    ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%204.png)

    1. `train.count()`

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%205.png)

## 3. Data Analysis

1. 데이터 변수의 종류

    ```python
    train.columns
    ```

    ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%206.png)

2. 데이터 변수의  의미
    - index : 인덱스 값
    - gender(성별) `F`, `M`
    - car(차량 소유 여부) `Y`, `N`
    - reality(부동산 소유 여부) `Y`, `N`
    - child_num(자녀의 수)
    - income_total(연간 소득)
    - income_type(수입원)
    `Commercial associate`, `Pensioner`, `State servant`, `Student`, `Working`
    - edu_type(교육 수준)
    `Academic degree`, `Higher education`, `Incomplete higher`, `Lower secondary`, `Secondary / secondary special`
    - family_type(혼인 여부)
    `Civil marriage`, `Married`, `Separated`, `Single / not married`, `Widow`
    - house_type(생활 방식)
    `Co-op apartment`, `House / apartment`, `Municipal apartment`, `Office apartment`, `Rented apartment`, `With parents`
    - DAYS_BIRTH(출생일)
    역산으로 계산할 수 있다.
    - DAYS_EMPLOYED(고용 기간)
    역산하면 일을 시작한 날을 알 수 있다.
    - FLAG_MOBIL(모바일 폰 소유 여부)  `0`, `1`
    - work_phone(업무용 전화 소유 여부) `0`, `1`
    - phone(가정용 전화 소유 여부) `0`, `1`
    - email(이메일 소유 여부) `0`, `1`
    - occyp_type(직업 유형)
    `Accountants`, `Cleaning staff`, `Cooking staff`, `Core staff`, `Drivers`, `HR staff`, `High` , `kill tech staff`, `IT staff`, `Laborers`, `Low-skill Laborers`, `Managers`, `Medicine staff`, `Private service staff`, `Realty agents`, `Sales staff`, `Secretaries`, `Security staff`, `Waiters/barmen staff`, `nan`
    - family_size(가족 규모)
    - begin_month(신용카드 발급 시점)
    월 단위이며, 역산하여 카드를 사용한 시점을 알 수 있다.
    - credit(신용도) `0`, `1`, `2`
    사용자의 신용카드 대금 연체를 기준으로 한 신용도로 0이 신용도가 좋다는 의미이고, 2가 나쁨을 의미한다.
3. 각 열의 자료형 분석 

    ```python
    train.dtypes
    ```

    ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%207.png)

    - 숫자형
        1. Continuous (4개)
            - income_total, DAYS_BIRTH, DAYS_EMPLOYED, begin_month
        2. Discrete (5개)
            - index, child_num, FLAG_MOBIL, family_size, credit
    - 분류형
        1. 선택지가 2개인 경우 (6개)
            - gender, car, reality, work_phone, phone, email
        2. 선택지가 2개 이상인 경우 (5개)
            - income_type, edu_type, family_type, house_type, occpy_type
4. 데이터 정리
    - work_phone, phone, email은 데이터 값은 0, 1이지만, 0, 1의 의미는  Y, N과 같으므로 분류형에 두었다.
    - 가족과 관련하여 child_num, family_type, family_size는 서로 상관관계가 있다.
    - occyp_type이 NaN이어도 DAYS_EMPLOYED로는 음수값이 나올 수 있습니다.
5. 결측값 확인하기

    ```python
    train.isnull().sum()
    ```

    ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%208.png)

    - email의 결손값이 8171이다. 전체 데이터의 수가 26457이므로 1/3가량이 결측값이다.
    - 데이터 전처리는 하지 않고, 있는 데이터로만 분석을 진행해 보기로 한다.
6. 데이터 형 변환하기
    - float형은 메모리 사이즈를 많이 차지하므로 float형이 필요한 경우에만 쓰는 것이 좋다.

        ```python
        train.info()
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%209.png)

    - family_size는 가족의 수이므로 소수점 이하 값이 필요없으므로 int형으로 변환한다.
    - begin_month는 카드를 사용한 기간을 의미하므로 음수값은 있어도 소수점 이하 값은 사용하지 않는다. 따라서 int형으로 변환한다.
    - credit는 앞서 살펴본대로 0, 1, 2값만 가지므로 굳이 floa형을 사용할 필요가 없다. 따라서 int형으로 변환하여 준다.

        ```python
        train = train.astype({'family_size': 'int', 'begin_month': 'int', 'credit': 'int'})
        train.info()
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2010.png)

7. 의미 없는 데이터 처리
    - 모델링을 한다면 테이블에서 제거해주어야 하지만, 시각화까지만, 진행할 예정이므로 현 상태를 유지하기로 한다.
    - 인덱스 값은 순서를 나타낼 뿐이서 credit와 관련 없으므로 분석에 사용하지 않는다.
    - FLAG_MOBIL의 데이터값은 1만 있어서 의미없는 데이터이므로 분석에 사용하지 않는다.

        ```python
        print(train_df['FLAG_MOBIL'].unique())
        # >>> [1]
        ```

8. 예측
    - 학력이 높을수록 연체에 대한 불이익을 잘 이해할 것이므로 연체율이 낮을 것이다.
    - 수입이 많을 수록 지급이 용이하므로 연체율이 낮을 것이다.
    - 가족 형태가 클수록 카드 사용이 중요하므로 낮은 연체율을 유지하려고 할 것이다.
    - 나이가 많을 수록 카드 사용 경험이 많기 때문에 신용도에 대한 의미를 잘 이해할 것이므로 연체율이 낮을 것이다.
    - 신용은 사회 경험과 관련이 깊은 영역이므로 성별과 신용도는 큰 관련이 없을 것이다.

## 4. Data Visualization

1. 신용 등급 비율
    - 전체

        ```python
        credit_count = train['credit'].value_counts()
        credit_count
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2011.png)

        ```python
        plt.pie(x=credit_count, labels=credit_count.index, autopct='%1.1f%%', 
        				colors=['blue', 'green', 'red'])
        plt.title('credit')
        plt.legend()
        plt.show()
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2012.png)

        - Credit 2가 2/3 가량을 차지합니다.
        - Credit 0는 상위 12%이므로 신용이 상당히 좋은 것임을 알 수 있습니다.

### 1) 분류형 - 선택지가 2개인 경우

- 선택지가 2개인 경우에는 아래 함수를 호출하기로 한다.

    ```python
    def plt_pie(label, sample):
      data = train[train[label] == sample]
      data_c = data['credit'].value_counts()
      data_c
      plt.pie(x=data_c, labels=data_c.index, autopct='%1.1f%%')
      plt.title(label+'_'+str(sample))
      plt.show()
    ```

1. 성별에 따른 신용 등급 차이
    - 전체

        ```python
        sns.countplot(x='gender', data=train, hue='credit')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2013.png)

        - 전체 수로는 여성(F)의 Credit 2가 가장 많은 것을 알 수 있다. 그러나 Credit 0, Credit 1도 많이 있으므로 비율을 볼 필요가 있다.
    - 남성

        ```python
        plt_pie('gender', 'M')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2014.png)

    - 여성

        ```python
        plt_pie('gender', 'F')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2015.png)

    - 비율에 있어서 성별간 차이가 거의 없는 것을 알 수 있다. 따라서, 여성의 Credit 2가 많았던건 단지 표본이 많았던 것이므로 credit를 산정함에 있어서 성별은 큰 의미가 없는 것을 알 수 있다.
2. 자동차 소유여부에 따른 신용 등급 차이
    - 전체 확인하기

        ```python
        car_credit = pd.crosstab(train['credit'],train['car'])
        car_credit
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2016.png)

    - 자동차를 소유하는 경우의 신용 등급

        ```python
        plt_pie('car', 'Y')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2017.png)

    - 자동차를 소유하지 않는 경우의 신용 등급

        ```python
        plt_pie('car', 'N')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2018.png)

    - credit 0은 소수점 이하범위에서 차이지만, credit 1과 credit 2에서는 약 1.5%가량 차이가 있다. 차가 있는 경우에 credit 2가 더 많은 걸로 봐서 차량의 소유가 credit에는 좋지 않은 영향을 끼치는 것으로 생각해볼 수 있다.
3. 부동산 소유여부에 따른 신용 등급 차이
    - 부동산을 소유하는 경우

        ```python
        plt_pie('reality', 'Y')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2019.png)

    - 부동산을 소유하지 않는 경우

        ```python
        plt_pie('reality', 'N')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2020.png)

        - 차량 소유에서와 비슷한 양상을 보이고 있다. credit 0은 비슷하지만, credit 1, credit 2에서 차이가 있음을 알 수 있다.
        - 부동산을 소유하지 않는 경우에 credit 2가 큰 값을 가지는 것을 알 수 있는데, 부동산이 없다는 것은 것은 재산 규모가 작다고 생각해 볼 수 있고, 신용 등급 관리에 어려움이 있는 것으로 생각해볼 수 있다.
4.  work_phone 여부에 따른 신용등급 차이
    - 0인 경우

        ```python
        plt_pie('work_phone', 0)
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2021.png)

    - 1인 경우

        ```python
        plt_pie('work_phone', 1)
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2022.png)

    - 0, 1의 값이 의미하는 바가 무엇이던 간에 소수점 이하 범위에서 차이임을 알 수 있다.
5. phone 여부에 따른 신용등급 차이
    - 0인 경우

        ```python
        plt_pie('phone', 0)
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2023.png)

    - 1인 경우

        ```python
        plt_pie('phone', 1)
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2024.png)

    - work_phone과는 달리 값이 1인 경우 credit 2가 많은 것을 알 수 있다. 집전화가 있는 것이
6. email 여부에 따른 신용등급 차이
    - 0인 경우

        ```python
        plt_pie('email', 0)
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2025.png)

    - 1인 경우

        ```python
        plt_pie('email', 1)
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2026.png)

    - email이 1인 경우에 credit이 나빠짐을 알 수 있다. 어떤 의미로 해석해야 할지 모르겠다.

### 2) 분류형 - 선택지가 2개보다 많은 경우

1. Income type 따른 신용등급 차이
    - 전체값 확인

        ```python
        pd.crosstab(train['credit'],train['income_type'])
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2027.png)

        ```python
        pd.crosstab(train['income_type'],train['credit']).plot(kind='bar')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2028.png)

        - 학생은 샘플 자체가 적기때문에 그래프에서 나타나지 않음을 알 수 있다.
        - Commercial associate

            ```python
            plt_pie('income_type', 'Commercial associate')
            ```

            ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2029.png)

        - Pensioner

            ```python
            plt_pie('income_type', 'Pensioner')
            ```

            ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2030.png)

        - State servant

            ```python
            plt_pie('income_type', 'State servant')
            ```

            ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2031.png)

        - Student

            ```python
            plt_pie('income_type', 'Student')
            ```

            ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2032.png)

        - Working

            ```python
            plt_pie('income_type', 'Working')
            ```

            ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2033.png)

    - Students의 경우 샘플이 적기 때문에 비율은 의미가 없다.
    - Commercial associate와 State servant에서 credit 2가 많음을 알 수 있다.
2. edu_type에 따른 신용등급 차이
    - 전체

        ```python
        pd.crosstab(train['edu_type'],train['credit'], normalize=True).plot(kind='bar')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2034.png)

    - Academic degree

        ```python
        plt_pie('edu_type', 'Academic degree')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2035.png)

    - Higher education

        ```python
        plt_pie('edu_type', 'Higher education')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2036.png)

    - Incomplete higher

        ```python
        plt_pie('edu_type', 'Incomplete higher')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2037.png)

    - Lower secondary

        ```python
        plt_pie('edu_type', 'Lower secondary')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2038.png)

    - Secondary / secondary special

        ```python
        plt_pie('edu_type', 'Secondary / secondary special')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2039.png)

    - Lower secondary에서 credit 2가 많은 걸로 봐서는 edu_type에 따른 차이가 있음을 알 수 있다.
3. family_type
    - 전체

        ```python
        pd.crosstab(train['family_type'],train['credit'], normalize=True).plot(kind='bar')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2040.png)

        - Married이 압도적으로 많고, 나머지는 비슷함을 알 수 있다.
    - Civil marriage

        ```python
        plt_pie('family_type', 'Civil marriage')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2041.png)

    - Married

        ```python
        plt_pie('family_type', 'Married')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2042.png)

    - Separated

        ```python
        plt_pie('family_type', 'Separated')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2043.png)

    - Single / not married

        ```python
        plt_pie('family_type', 'Single / not married')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2044.png)

    - Widow

        ```python
        plt_pie('family_type', 'Widow')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2045.png)

    - Civil marriage, Single / not married, Widow에서 유의미하게 credit이 양호함을 알 수 있다.
    Civil marriage, Single / not married의 경우 생활이 안정적인 것으로 생각해볼 수 있고, 
    Widow의 경우 보험금등의 수입원이 있을 것으로 예상해볼 수 있다.
    - 반대로 Married, Separated는 Credit 2가 많은데, 생활 상태의 불안정성이 Credit에 반영되는걸로 생각해볼 수 있다.
- house_type
    - 전체
        - House / apartment가 압도적으로 많다. 개개인의 선호의 문제도 있고, 건축의 편의에 따른 공급이 많아서일수도 있다. 지역적인 특성이 있을수도 있다.

        ```python
        pd.crosstab(train['house_type'],train['credit'], normalize=True).plot(kind='bar')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2046.png)

    - Co-op apartment

        ```python
        plt_pie('house_type', 'Co-op apartment')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2047.png)

    - House / apartment

        ```python
        plt_pie('house_type', 'House / apartment')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2048.png)

    - Municipal apartment

        ```python
        plt_pie('house_type', 'Municipal apartment')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2049.png)

    - Office apartment

        ```python
        plt_pie('house_type', 'Office apartment')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2050.png)

    - Rented apartment

        ```python
        plt_pie('house_type', 'Rented apartment')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2051.png)

    - With parents

        ```python
        plt_pie('house_type', 'With parents')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2052.png)

    - 샘플이 가장 많은 House / apartment는 평균값과 유사하고, With parents의 경우도 평균값과 유사한 경향을 나타낸다.
    - Co-op apartment와 Rented apartment의 경우 credit이 굉장히 양호한 것을 알 수 있다. 임대형태로 많이 사용되는 거주공간인데, 직장과 가까운 곳에서 생활할 경우 임대를 하는 경우가 많으므로 꾸준한 수입이 있는 직장인들의 credit으로 생각해볼 수 있다.
    - 반대로 Municipal apartment의 경우 Credit 2가 많은데, 공공 주택은 통상적으로 소득 수준이 낮은 사람들을 위한 거주 공간이므로 낮은 소득에 따른 Credit관리가 잘 안되는 것으로 볼 수 있다.

## 5. Intermediate

- 중간 평가
    - 선택지가 2개인 경우에는 각각 sample이 많기 때문인지 전체 값과 유사한 경향을 나타내었다.
    - 선택지가 2개보다 많은 경우에는 유의미한 차이가 있음을 알 수 있었다.
    - 특히, family_type과 house_type에서 상당한 차이가 있었음을 알 수 있었고, 상호 교집합을 통해 credit 비율의 차이 찾아본다
    - 교차값에서 credit 비율을 구하기 위해 아래 함수를 사용한다.

        ```python
        def plot_cross(col1, label1, col2, label2):
          data1 = train[train[col1] == label1]
          data2 = data1[data1[col2] == label2]
          data3 = data2['credit'].value_counts()  
          plt.pie(x=data3, labels=data3, autopct='%1.1f%%')
          plt.title(col1+':'+label1+', '+col2+':'+label2)
          plt.legend(data3.index)
          plt.show()
        ```

    - house_type = Rented apartment & family_type = Civil marriage인 경우

        ```python
        plot_cross('house_type', 'Rented apartment', 'family_type', 'Civil marriage')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2053.png)

        - 앞서 살펴본 바에 따르면, house_type이 Rented apartment인 경우에 credit이 좋았었고,  family_type이 Civil marriage인 경우에 credit이 좋았었는데, 교차값에서는 credit 0과 credit 1이 과반을 차지하는 것을 볼 수 있다.
    - house_type = Rented apartment & family_type = Civil marriage인 경우

        ```python
        plot_cross('house_type', 'Rented apartment', 'family_type', 'Civil marriage')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2053.png)

        - 앞서 살펴본 바에 따르면, house_type이 Rented apartment인 경우에 credit이 좋았었고,  family_type이 Civil marriage인 경우에 credit이 좋았었는데, 교차값에서는 credit 0과 credit 1이 과반을 차지하는 것을 볼 수 있다.
    - house_type = House / apartment & family_type = Civil marriage인 경우

        ```python
        plot_cross('house_type', 'House / apartment', 'family_type', 'Civil marriage')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2054.png)

        - Rented apartment의 경우 sample이 적었기 때문에 가장 많은 sample을 가지는 두 값을 교차해보았다.
        - 아주 큰 차이는 아니지만, credit 2가 줄고, 줄어든 만큼 credit 1이 늘어났다.
        - 안정적인 가정 상황을 연상한 조합으로 credit도 양호함을 알 수 있다.
    - house_type = Municipal apartment & family_type = Married인 경우

        ```python
        plot_cross('house_type', 'Municipal apartment', 'family_type', 'Married')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2055.png)

        - credit이 좋지 않았던 경우인 house_type이 Municipal apartment이고, family_type이 Married인 경우에는 credit 2의 비율이 전체 비율인 64.1%보다 4.3%가량 많았다.
        - 불안정한 가정 상황을 고려한 조합으로 생각대로 credit이 좋지 않음을 알 수 있다.
    - edu_type = Academic degree & house_type = House / apartment인 경ㅇ

        ```python
        plot_cross('edu_type', 'Academic degree', 'house_type', 'House / apartment')
        ```

        ![Untitled](https://withmaster.github.io/assets/images/2021-08-18-MiniProjectEDA/Untitled%2056.png)

        - 샘플이 많진 않지만, 높은 교육 수준과 안정적인 주거는 높은 credit으로 연결되는 것을 알 수 있다.

## 6. Conclusion

- 값이 3개 이상인 분류형 값(edu_type, house_type, family_type)을 조합하여 credit을 예상해보았다.
- 안정적인 가정의 credit이 양호할 것이라고 예상하였고, 가정이 안정적인 상태를 유지하기 위해서는 Civil marrige, House / apartment, Academic degree가 영향을 줄 것으로 예상하였고,  각각을 조합한 결과에서는 credit 2가 감소하고, credit 1증가한 것을 알 수 있었다.
- 3개의 값을 조합하고 싶었지만, 샘플의 수가 너무 적어서 분석할 수가 없어서 아쉬움이 남는다.