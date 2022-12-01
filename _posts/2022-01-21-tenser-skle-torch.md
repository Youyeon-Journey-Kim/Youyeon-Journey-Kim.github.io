---
layout: post
title: 데이터 사이언티스트가 알아야하는 Tensorflow, Sklearn, Pytorch, Keras
tags: [Tensorflow, Sklearn, Pytorch]
math: true
date: 2022-01-21 22:18 +0800
---

#### 데이터 사이언티스트가 알아야하는 Tensorflow, Sklearn, Pytorch

##### 머신러닝(딥러닝)에 대한 공부를 시작하면서 Tensorflow, Sklearn, Pytorch, Keras 이 네가지의 프레임워크에 대해 많이 들었다.

##### 그래서 이 많이 사용되는 이 네가지 프레임워크에 대해 정확히 짚고 넘어가기로 했다.


#### Scikit-learn

>##### Scikit-learn is a python library used for machine learning. More specifically, it's a set of simple and efficient tools for data mining and data analysis.

>##### The framework is built on top of several Python packages, Namely Numpy, SciPy, and matplotlib.

>##### A major benefit of this library is the **BDS license** it's distributed under.
    > ##### This license allows you to decide whether to upstream your changes without any restriction on commercial use.

>##### The main advantage of this solution is its accessibility and simplicity -it's easy to use even for beginners and a great choice for simpler data anaysis tasks. On the other hand, scikit-learn is not the best for deep learning.   


##### **Scikit-learn**은 기계학습에 사용되는 Python 라이브러리로 **데이터 마이닝 및 데이터 분석을 위한 simple하고 effiecient한 tool**이다. 또한 **Numpy,SciPy,matplotlib와 같은 Python 패키지 위에 구축**된다. sklearn의 장점은 접근성(accessibility)와 단순성(simplicity)으로 초보자도 쉽게 사용할 수 있으며 간단한 데이터 분석 작업에 사용하기 좋으나 딥 러닝을 위한 최선의 선택은 아니다.


***

#### TensorFlow

> ##### Tensorflow is, according to its inviting tagline, an open-source platform for machine learning. The tool was initially developed for internal use at Google, but was released publicly under the Apache 2.0 open-source license on November 9,2015, and has gained enormous popularity since then.


> ##### The framework is extremly powerful. You can easily build  simple models like **linear regression or convolutional neural networks with millions of parameters.**

> ##### TensorFlow has many **pretrained models** that you can use (after some fine-tuning) for your problem. One  thing Tensorflow is **great at is deep learning**. One major example is **BERT**, a transfomer-based machine learning technique initially used at Google to better understand user searches.

> ##### Many years have passed since its initial release. it used to be a tool for coding deep neural networks. At least two aspects have changed. Since the release of TF2(its second version), **TensorFlow has become more user-friendly**. The second thing is that many tools have been built arouond and on top of it. This means that users have a large ecosystem at their disposal that helps them to be efficient from initial prototyping to deployment and monitoring.

##### 텐서플로우는 기계학습을 위한 오픈 소스 플랫폼으로 수백만개의 매개변수가 있는 선형 회기(linear regression)와 convolutional neural networks과 같은 모델을 쉽게 구축할 수 있다. TensorFlow 는 사전 훈련된 모델들[(*TensorFlow hub)](https://tfhub.dev/)이 많다, TensorFlow의 장점 중 하나는 딥러닝인데. 한가지 주요 예로는 사용자 검색을 더 잘 이해하기 위해 Google에서 처음에 사용된 변환기 기반 기계학습 기술인 **BERT**이다.

- ##### MLCC **[Machine Learning Crash Course with TensorFlow APIs](https://developers.google.com/machine-learning/crash-course/)** : an useful introduction to ML developed by Google.


***


#### PyTorch

> ##### PyTorch, a Python-centric deep learning framework, is all about flexible experimentation and customization, as well as strong GPU acceleration.


> ##### Some [example application](https://github.com/pytorch/examples) include word-level language modeling, time sequence prediction, and training imagenet classifiers. A major advantage of this framework is its support for **dynamic computation graphs(DCGs)**, which is a boon for uses such **linguistic analysis**. it is **the favourite library of research-oriented developers.**

> ##### It is more flexinle than TensorFlow, but it is hard to tell which one of the two is better. A rule of thumb is that PyTorch is better at research-oriented projects and TensorFlow is a better fit for production use.


***


#### Keras

> ##### Keras is a Python deep learning library. It has been created to make coding neural networks easy, so its tagline "**Deep learning for humans**" is not an accident. It used to be a stand-alone library.


> ##### Now it is **a part of TensorFlow** and users are advised to use this [version](https://www.tensorflow.org/api_docs/python/tf/keras),which **in fact technically is a module of TF.**

> ##### Now, it's a part of TF and all its advantages have been naturally inherited






                                                          

***


_참고글_   

##### [[ML Frameworks Compared]](https://www.netguru.com/blog/top-machine-learning-frameworks-compared)

