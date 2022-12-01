---
layout: post
title: 데이터 사이언티스트가 알아야하는 NLP(1)-Seq2Seq,Tramsformer,BERT, Electra등
tags: [Bert, Electra]
math: true
date: 2022-05-08 00:46 +0800
---


#### 데이터 사이언티스트가 알아야하는 NLP(1)-Seq2Seq,Tramsformer,BERT, Electra 등

**딥러닝 기반 기계번역 발전 과정**
#### RNN → LSTM → Seq2Seq (_고정된 크기의 context vector 사용_) → Attention → Transformer → GPT,BERT(_입력 시퀀스 전체에서 정보를 추출하는 방향으로 발전_)

##### GPT : Transformer Decoder Architecture 활용
##### BERT : Transformer Incoder Architecture 활용


***

#### Seq2Seq Model

- Encoder

##### → *(sos(start of sentence))* quten abend *(eos(end of sentence))*

- ##### 각 토큰은 embedding layer를 거쳐 RNN layer를 지나면서 각 layer의 출력값(h1,h2,...:activation function을 지난 후의 값)이 생기게 되며 이떄 각 출력값은 다음 layer의 input으로 들어가게 된다(RNN이기 떄문) 각 출력값(h1,h2...)는 고정된 크기의 context vector v에 모아지게 된다.

- Decoder
##### → *(sos(start of sentence))* good evening

- ##### Decoder의 layer도 마찬가지로 각 token이 embedding, RNN layer를 거쳐 출력값(s1,s2...)이 생성된다. context v는 첫번째 layer의 input으로 들어가게되고 s1으로 출력된다.


**Seq2Seq Model의 문제점**

1. ##### context vector는 가장 마지막 layer의 output 값이다. Encoder의 소스 문장 전체의 문맥 정보를 포함하고 있으며 **병목현상**이 발생하고 성능 하락의 원인이 됨.

2. ##### context vector를 Decoder의 첫번째 layer에만 반영하는 것이 아니라 Decoder 모든 layer에 입력으로 넣으면 성능이 조금 개선될 수 있으나, 소스 문장이 압축될때 정보가 손실되는 문제는 여전히 존재함.



***




**Transfomer Model 이란?**

- ##### 트랜스포머 모델은 문장 속 단어와 같은 순차 데이터 내의 관계를 추적해 맥락과 의미를 학습하는 신경망이다.


- ##### 트랜스포머 모델은 문장 속 단어와 같은 순차 데이터 내의 관계를 추적해 맥락과 의미를 학습하는 신경망이다.

- ##### Attention 또는 Self-attention 이라 부리며 진화를 거듭하는 수학적 기법을 응용해 서로 떨어져 있는 데이터 요소들의 의미가 관계에따라 미묘하게 달라지는 부분까지 감지한다.

- ##### Google의 2017년 논문에 처음 등장한 트랜스포머는 지금까지 개발된 모델 중 가장 새롭고 강력하다고한다. '트랜스포머 AI'라 불리기도 하는 머신러닝계의 혁신을 주도학 있다.