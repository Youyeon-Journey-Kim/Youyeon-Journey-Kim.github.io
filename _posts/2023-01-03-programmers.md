---
layout: post
title: 프로그래머스 문제풀이(이진 변환 반복하기, 다음 큰 숫자, 짝지어 제거하기) with Python
tags: [코테]
math: true
date: 2023-01-03 12:42 +0800
---

### 이진 변환 반복하기

#### 문제 설명
##### 0과 1로 이루어진 어떤 문자열 x에 대한 이진 변환을 다음과 같이 정의합니다.


##### x의 모든 0을 제거합니다.

##### x의 길이를 c라고 하면, x를 "c를 2진법으로 표현한 문자열"로 바꿉니다.

##### 예를 들어, x = "0111010"이라면, x에 이진 변환을 가하면 x = "0111010" -> "1111" -> "100" 이 됩니다.


##### 0과 1로 이루어진 문자열 s가 매개변수로 주어집니다. s가 "1"이 될 때까지 계속해서 s에 이진 변환을 가했을 때, 이진 변환의 횟수와 변환 과정에서 제거된 모든 0의 개수를 각각 배열에 담아 return 하도록 solution 함수를 완성해주세요.


#### 내 답안

##### 정규표현식을 활용함

```python
import re

def solution(s):
    count_zero = 0
    count_trans = 0
    while s != '1':
        len1 = len(s)
        s2 = re.sub(r'0','',s)
        count_zero += (len(s)-len(s2))
        s = bin(len(s2))[2:]
        count_trans += 1
    answer = [count_trans,count_zero]
    return answer
```
***

### 다음 큰 숫자

#### 문제 설명

##### 자연수 n이 주어졌을 때, n의 다음 큰 숫자는 다음과 같이 정의 합니다.


##### 조건 1. n의 다음 큰 숫자는 n보다 큰 자연수 입니다.

##### 조건 2. n의 다음 큰 숫자와 n은 2진수로 변환했을 때 1의 갯수가 같습니다.

##### 조건 3. n의 다음 큰 숫자는 조건 1, 2를 만족하는 수 중 가장 작은 수 입니다.

##### 예를 들어서 78(1001110)의 다음 큰 숫자는 83(1010011)입니다.


##### 자연수 n이 매개변수로 주어질 때, n의 다음 큰 숫자를 return 하는 solution 함수를 완성해주세요.


```python
def solution(n):
    count = bin(n).count('1')
    while True:
        n = n+1
        check = bin(n).count('1')
        if count == check:
            break
    
    answer = n
    return answer
```

##### 제한 사항

##### n은 1,000,000 이하의 자연수 입니다.

***

### 짝지어 제거하기

#### 문제 설명


##### 짝지어 제거하기는, 알파벳 소문자로 이루어진 문자열을 가지고 시작합니다. 먼저 문자열에서 같은 알파벳이 2개 붙어 있는 짝을 찾습니다. 그다음, 그 둘을 제거한 뒤, 앞뒤로 문자열을 이어 붙입니다. 이 과정을 반복해서 문자열을 모두 제거한다면 짝지어 제거하기가 종료됩니다. 문자열 S가 주어졌을 때, 짝지어 제거하기를 성공적으로 수행할 수 있는지 반환하는 함수를 완성해 주세요. 성공적으로 수행할 수 있으면 1을, 아닐 경우 0을 리턴해주면 됩니다.


##### 예를 들어, 문자열 S = baabaa 라면


##### b aa baa → bb aa → aa → 

##### 의 순서로 문자열을 모두 제거할 수 있으므로 1을 반환합니다.


##### 제한사항

##### 문자열의 길이 : 1,000,000이하의 자연수

##### 문자열은 모두 소문자로 이루어져 있습니다.


#### 내 답안

##### stack을 활용하여 풀었다.

```python
def solution(s):
    answer = -1
    
    s2 = s
    
    while True:
        stack = list()
        pre_s = s2
        
        for c in s2:
            if len(stack) == 0:
                stack.append(c)
            else:
                if stack[-1] == c:
                    stack.pop()
                else:
                    stack.append(c)
        
        s2 = ''.join(stack)
        if len(s2) == 0:
            answer = 1
            break
        elif len(s2) != 0 and len(s2) == len(pre_s):
            answer = 0
            break
    return answer
```