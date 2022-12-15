---
layout: post
title: NLP(2)- Transformer,BERT
tags: [ML, Transfomer, BERT]
math: true
date: 2022-07-21 18:46 +0800
---


#### 데이터 사이언티스트가 알아야하는 NLP(2)- Transformer,BERT

###### 정리하다 힘들어서 추후 마저 기록하겠다...!

**Transfomer Model 이란?**

**Attention is all you need.**

- ##### 트랜스포머 모델은 문장 속 단어와 같은 순차 데이터 내의 관계를 추적해 맥락과 의미를 학습하는 신경망이다.


- ##### 트랜스포머 모델은 문장 속 단어와 같은 순차 데이터 내의 관계를 추적해 맥락과 의미를 학습하는 신경망이다.

- ##### Attention 또는 Self-attention 이라 부리며 진화를 거듭하는 수학적 기법을 응용해 서로 떨어져 있는 데이터 요소들의 의미가 관계에따라 미묘하게 달라지는 부분까지 감지한다.

- ##### Google의 2017년 논문에 처음 등장한 트랜스포머는 지금까지 개발된 모델 중 가장 새롭고 강력하다고한다. '트랜스포머 AI'라 불리기도 하는 머신러닝계의 혁신을 주도학 있다.

- ##### CNN,RNN을 전혀 필요로 하지 않고 attention만을 이용는데 이 떄, RNN과 같이 문장안의 각 단어의 순서 정보를 주기 어려운데 이를 **Positional Encoding**을 이용해 순서 정보를 준다.

- ##### Encoder와 Decoder로 구성되는 것은 동일하나 Attention 과정을 여러 layer에 반복 한다. 즉, Encoder가 N개 중첩된다.

- ##### RNN, LSTM 입력단어 갯수만큼 Encoder layer를 거쳐 hidden state를 만들지만, **trans는 단어가 하나로 연결되어 병렬적으로 한번의 Encoder를 거쳐 병렬적으로 출력값을 생성함**(계산 복잡도를 줄임.)

![trans](https://blog.kakaocdn.net/dn/ckWMvU/btroMqAsgcK/UB6GTvFbFZnH8GgMArDI60/img.png)

- ##### RNN은 순서대로 들어가기 때문에 state는 순서 정보를 가지고 있다. 이를 해결하기 위해 Positional Encoding을 Input Embedding Matrix와 element wise를 통해(더해줌) 구한다, 때문에 Positional Encoding 과 Input Embedding Matrix는 동일한 차원이여야한다.

![trans2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdW8wAB%2FbtrkvI6NhyL%2FoMbibRc2OqIB6kOoKSh600%2Fimg.png)

- ##### 인코더와 디코더라는 단위가 N개로 구성되는 구조이다. 그래서 Encoders(인코더들), Decoders(디코더들)이라고 부른다. 


**Transformer의 주요 hyper parameter**

- ##### 아래에서 정의한 수치값은 트랜스포머를 제안한 논문에서 사용한 것으로 사용자의 입맛에 따라 임의로 변경 가능.

1. ##### **d**model = 512

- #####  트랜스포머의 인코더와 디코더에서의 정해진 입력과 출력의 크기를 의미한다. 임베딩 벡터의 차원 또한  **d**model 이며, 각 인코더와 디코더가 다음 층의 인코더와 디코더로 값을 보낼때에도 이 차원을 유지한다.

2. ##### num_layers = 6

- ##### 트랜스포머에서 하나의 인코더와 디코더를 층으로 생각했을 때, 트랜스포머 모델에서 인코더와 디코더가 총 몇 층으로 구성되었는지를 의미한다. 논문에서는 인코더와 디코더를 각각 6층을 쌓았다.

3. ##### num_heads = 8

- ##### 트랜스포머에서는 어텐션을 사용할 떄, 1번 하는 것보다 여러개로 분할해서 병렬로 어텐션을 수행하고 결과값을 다시 하나로 합치는 방식을 택했다. 이 때 병령의 개수를 의미 한다.

4. ##### **d**ff = 2048

- ##### 트랜스포머 내부에는 피드 포워드 신경망이 존재한다. 이떄 은닉층의 크기를 의미한다. 피드 포워드 신경망의 입력층과 출력층의 크기는 **d**model 이다.

***

**BERT 란?**

- ##### BERT(Bidirectional Encoder Representations from Transfomers, BERT)는 2018년 구글이 개발한 자연어 처리 신경망 구조이다. 기존의 단방향 자연어 처리 모델들의 단점을 보완한 양방향 자연어 처리 모델이다.

- ##### 트랜스포머를 이용하여 구현되었으며, 방대한 양의 텍스트 데이터로 사전 훈련된 언어 모델이다.

![bert](https://wikidocs.net/images/page/35594/bartbase%EC%99%80large.PNG)

###### 출처: https://wikidocs.net/115055

- ##### BERT의 기본 구조는 위와 같이 transformer의 encoder를 쌓아올린 구조.



***

***


##### _참고글_
[1](https://moondol-ai.tistory.com/460)
[2](https://ebbnflow.tistory.com/316)
[3](https://wikidocs.net/115055)