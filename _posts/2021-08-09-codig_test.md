---
title:  "키패드 누르기"
excerpt: "프로그래머스에서 제공되는 Python3 & Level 1 문제입니다. "

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 코딩 테스트
tags:
  - programmers
  - python
  - Level 1
  - Kakao
---

# 개요

- 저번에 Level 2를 시도했다가 고생해서 Level 1을 시도했습니다.
- Level 1에서 완료한 사람이 비교적 적은걸 찾아봤습니다.

  >  [코딩테스트 연습 - 키패드 누르기](https://programmers.co.kr/learn/courses/30/lessons/67256)


         
# 문제 정리 및 분석

1. 특정 숫자열에 따라 키패드 입력을 합니다.
2. 1, 4, 7일 경우에는 왼손 엄지로 입력(문자열에 `L`을 추가)하고, 3, 6, 9일 경우에는  엄지로 입력(문자열에 `R`을 추가)합니다.
3. 2, 5, 8, 0의 경우 가까이에 있는 엄지로 입력하며, 거리가 같은 경우에는 자신의 주손의 엄지 손가락으로 입력합니다
4. 
5. 피연산자는 계산이 쉽도록 정수 형태로 관리한다.
6. 분리된 연산자와 피연산자를 이용해서 재정의될 수 있는 연산자 우선 순위에 따라 수식을 계산하여 결과값을 도출한다.
7. 절대값이 가장 큰 결과값을 반환한다.

# Source Code

```python
def solution(numbers, hand):

    answer = ''
		# 실제 keypad와 매칭합니다.
		# 인덱스 0에 키패드 0의 위치 정보를 저장하고 있습니다.
    keypad = [[3, 1],
              [0, 0], [0, 1], [0, 2],
              [1, 0], [1, 1], [1, 2],
              [2, 0], [2, 1], [2, 2],
              [3, 0],         [3, 2]]

    k_pos = 0 # 현재 입력된 키패드의 값
    l_pos = 10 # 왼손 엄지의 현재 위치
    r_pos = 11 # 오른손 엄지의 현재 위치

	
    for k_pos in numbers:
				# 1, 4, 7이 입력된 경우
        if k_pos == 1 or k_pos == 4 or k_pos == 7:
            answer = answer + 'L'
            l_pos = k_pos

				# 3, 6, 9가 입력된 경우
        elif k_pos == 3 or k_pos == 6 or k_pos == 9:
            answer = answer + 'R'
            r_pos = k_pos

				# 2, 5, 8, 0이 입력된 경우
        else: 
						# 거리 측정, 간단하게 맨하탄 거리를 이용한다.
            l_dist = abs(keypad[l_pos][0] - keypad[k_pos][0]) + abs(keypad[l_pos][1] - keypad[k_pos][1])
            r_dist = abs(keypad[r_pos][0] - keypad[k_pos][0]) + abs(keypad[r_pos][1] - keypad[k_pos][1])
						
						# 거리가 가까운 손으로 입력
            if l_dist > r_dist:
                answer = answer + 'R'
                r_pos = k_pos
            elif l_dist < r_dist:
                answer = answer + 'L'
                l_pos = k_pos
						# 거리가 같은 경우에는 주손의 엄지로 입력
            else: # l_dist == r_dist
                if hand == 'right':
                    answer = answer + 'R'
                    r_pos = k_pos
                else: # hand == 'left':
                    answer = answer + 'L'
                    l_pos = k_pos
    return answer
```

# 총평

- 키패드의 값과 인덱스의 값을 일치시켜서 계산하는 아이디어덕에 쉽게 풀렸습니다.
- 해설을 보고 나니 dict를 사용하는 것이 가장 직관적인 방법이라는 생각이 들었구요.
- 하나의 for문을 사용했고, 별도의 호출이 없어서 코드 효율을 괜찮다고 생각합니다.