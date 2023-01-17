---
layout: post
title: 프로그래머스 문제풀이(최댓값과 최솟값, JadenCase 문자열 만들기, 최솟값 만들기, 올바른 괄호) with Python
tags: [코테]
math: true
date: 2022-12-23 12:49 +0800
---
### 1. 최댓값과 최솟값
#### 문제 설명

##### 문자열 s에는 공백으로 구분된 숫자들이 저장되어 있습니다. str에 나타나는 숫자 중 최소값과 최대값을 찾아 이를 "(최소값) (최대값)"형태의 문자열을 반환하는 함수, solution을 완성하세요.예를들어 s가 "1 2 3 4"라면 "1 4"를 리턴하고, "-1 -2 -3 -4"라면 "-4 -1"을 리턴하면 됩니다.


#### 제한 조건

##### s에는 둘 이상의 정수가 공백으로 구분되어 있습니다.


#### 입출력 예


|s|	return|
|:---|:---|
|"1 2 3 4"|"1 4"|
|"-1 -2 -3 -4"|"-4 -1"|
|"-1 -1"|"-1 -1"|

#### 내 답안

```python
def solution(s):
    l = list(map(int,s.split(sep=' ')))
    answer = str(min(l)) + ' ' + str(max(l))

    return answer
```

***

### JadenCase 문자열 만들기


#### 문제 설명

##### JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고) 문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

#### 제한 조건
##### s는 길이 1 이상 200 이하인 문자열입니다.   s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.    숫자는 단어의 첫 문자로만 나옵니다.   숫자로만 이루어진 단어는 없습니다.   공백문자가 연속해서 나올 수 있습니다.


#### 입출력 예

|s|return|
|:---|:---|
|"3people unFollowed me"|"3people Unfollowed Me"|
|"for the last week"|"For The Last Week"|


#### 내 답안

```python
def solution(s):
    n_list = list(map(str,(range(10))))
    s = s.lower()
    c_list = list(s)
    flag = 0
    answer = ''
    for idx,c in enumerate(c_list):
        if c == ' ':
            answer += c
            flag = 1
            continue
        if idx == 0:
            flag = 1
        if c in n_list:
            flag = 0
            answer += c
            continue
        #문장 첫글자 처리
        if c not in n_list and flag == 1:
            answer += c.upper()
            flag = 0
            continue
        else:
            answer += c

    return answer
```

### 최솟값 만들기

#### 문제 설명

##### 길이가 같은 배열 A, B 두개가 있습니다. 각 배열은 자연수로 이루어져 있습니다.   배열 A, B에서 각각 한 개의 숫자를 뽑아 두 수를 곱합니다. 이러한 과정을 배열의 길이만큼 반복하며, 두 수를 곱한 값을 누적하여 더합니다. 이때 최종적으로 누적된 값이 최소가 되도록 만드는 것이 목표입니다. (단, 각 배열에서 k번째 숫자를 뽑았다면 다음에 k번째 숫자는 다시 뽑을 수 없습니다.)


### 내 답안

```python
def solution(A,B):
    answer = sum(a*b for a,b in zip(sorted(A),sorted(B,reverse=True)))
    return answer
```

### 올바른 괄호

#### 문제 설명

##### 괄호가 바르게 짝지어졌다는 것은 '(' 문자로 열렸으면 반드시 짝지어서 ')' 문자로 닫혀야 한다는 뜻입니다. 예를 들어

- ##### "()()" 또는 "(())()" 는 올바른 괄호입니다.

- ##### ")()(" 또는 "(()(" 는 올바르지 않은 괄호입니다.

##### '(' 또는 ')' 로만 이루어진 문자열 s가 주어졌을 때, 문자열 s가 올바른 괄호이면 true를 return 하고, 올바르지 않은 괄호이면 false를 return 하는 solution 함수를 완성해 주세요.

#### 제한사항

##### 문자열 s의 길이 : 100,000 이하의 자연수
##### 문자열 s는 '(' 또는 ')' 로만 이루어져 있습니다.

#### 입출력 예


|s|answer|
|:---|:---|
|"()()"|true|
|"(())()"|true|
|")()("|false|
|"(()("|false|

### Stack 과 Queue

1. Queue

- 가장 먼저 입력된 데이터가 가장 먼저 출력되는 구조 : FIFO(First in, First out)
- Python에서는 queue라는 내장 모듈을 제공한다.
    - queue에 데이터를 넣을때(Enqueue) : put()
    - queue에서 데이터를 꺼낼때(Dequeue) : get()


2. Stack

- 나중에 입력 된 데이터가 먼저 출력되는 구조 : LIFO(Last In, First Out)
    - push : 데이터 입력
    - pop : 데이터 꺼내기
- Python에서는 append를 통해 데이터를 넣고 꺼낼때는 pop()함수를 사용



### 내 답안
```python
def solution(s):
    stl = list(s)
    if stl[0] == ')' or stl[-1] == '()':
        return False
    q_stack = list()
    for c in stl:
        if c == '(':
            q_stack.append(c)
        else:
            if len(q_stack):
                q_stack.pop()
            else:
                return False
    if len(q_stack) == 0:
        return True
    else:
        return False
```