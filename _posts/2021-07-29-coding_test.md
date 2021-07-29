---
title:  "수식 최대화"
excerpt: "프로그래머스에서 제공되는 Python3 & Level2 문제입니다. "

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 코딩 테스트
tags:
  - 프로그래머스
  - programmers
  - python
  - python3
  - Level 2
  - 카카오
  - 2020
---

# 수식 최대화

## 개요
* 검색 조건: Python3, Level 2
* [프로그래머스 코딩테스트 연습 - 수식 최대화](https://programmers.co.kr/learn/courses/30/lessons/67257?language=python3)

## 작성자의 수준
- C언어를 사용하다 최근에 python을 공부하고 있습니다.
- 파이썬의 유용한 기능들을 잘 몰라서 C언어처럼 작성하곤 합니다.
---   
# 문제
## 정리
1. 문자열 형태의 수식이 주어진다.
2. 수식에는 3개의 연산자 `+`, `-`, `*`가 주어진다.
3. 3개의 연산자의 우선 순위를 재정의할 수 있다.
4. 연산자는 동일한 우선 순위를 가질 수 없다.
5. 같은 연산자끼리는 앞에 있는 것의 우선 순위가 더 높다.
6. 재정의된 우선 순위에 따라 계산된 값의 절대값이 가장 큰 값을 찾아야 한다.

## 분석
1. 문자열 형태의 수식에서 연산자와 피연산자를 분리해야 한다.
2. 피연산자는 계산이 쉽도록 정수 형태로 관리한다.
3. 분리된 연산자와 피연산자를 이용해서 재정의될 수 있는 연산자 우선 순위에 따라 수식을 계산하여 결과값을 도출한다.
4. 절대값이 가장 큰 결과값을 반환한다.

---
# Source Code

```python
def solution(expression):
    # 재정의 가능한 연산자 우선 순위를 별도로 관리한다.
    # 생성 로직을 만들수는 있겠지만, 시간적으로 낭비일꺼 같아 하드 코딩하였다.
    priority = [
        ['+', '-', '*'],
        ['+', '*', '-'],
        ['-', '+', '*'],
        ['-', '*', '+'],
        ['*', '+', '-'],
        ['*', '-', '+']
    ]
	

    op_list = [] # 연산자가 저장될 리스트
    num_list = [] # 피연산자가 저장될 리스트
    pre_idx = 0 # 피연산자 저장을 위해 별도로 관리하는 인덱스, 연산자 바로 다음 위치를 가르킨다.

    # expression을 앞에서부터 전부 살펴본다.
    for i in range(len(expression)):
        # 연산자를 찾으면 연산자를 op_list에 순서대로 추가하고,
        # pre_idx부터 연산자 직전까지에 있는 숫자를 num_list에 추가한다.
        if expression[i] == '+' or expression[i] == '-' or expression[i] == '*':
            op_list.append(expression[i])
            num_list.append(int(expression[pre_idx:i]))						
            pre_idx = i+1 # 연산자 바로 다음 위치를 가르킨다.

    # 마지막 연산자 뒤에 있는 피연산자를 num_list추가한다.
    num_list.append(int(expression[pre_idx:i+1]))

    # 연산자가 3개인 경우 총 6개(3!)의 결과값이 도출되므로 리스트로 관리한다.
    answer = []

    # 연산자가 3개이므로 6번 반복 수행한다.
    for j in range(6):
        # 뒤의pop, insert 연산에 의해 list가 변형되므로 사본으로 연산을 수행한다.
        que_op = op_list.copy()
        que_num = num_list.copy()

        # 연산자가 3가지이므로 각각에 대해 연산을 수행한다.
        for k in range(3):
            # j=0, k=0이면 '+'를 반환한다.
            main_op = priority[j][k]

            # 반환된 연산자의 개수(que_op.count(main_op))만큼 실행한다.
            for l in range(que_op.count(main_op)):
                # 해당 연산자의 위치를 찾는다.
                idx = que_op.index(main_op)
                # 해당 연산자 및 피연산자는 아래에서 소모되므로 리스트에서 제거
                que_op.pop(idx)
                op1 = que_num.pop(idx)
                op2 = que_num.pop(idx)
                if main_op == '+':
                    res = op1 + op2
                elif main_op == '-':
                    res = op1 - op2
                elif main_op == '*':
                    res = op1 * op2
                # 연산 결과를 있던 자리에 다시 저장한다.
                que_num.insert(idx, res)

        # 총 6번 중 한번의 연산이 종료되면 결과값에 절대값을 적용하여을 저장한다. 
        answer.append(abs(que_num[0]))

    # 내림차순 정렬하여 맨 앞에 가장 큰 값이 위치하도록 한다.
    answer.sort(reverse=True)

    # 가장 큰 값을 반환한다.
    return answer[0]
```

# 총평

* 남의 해설을 올릴 수는 없지만, 다른 사람의 코드를 보니 나의 solution은 정말 C언어에 가깝게 작성한 것을 느낄 수 있었다.