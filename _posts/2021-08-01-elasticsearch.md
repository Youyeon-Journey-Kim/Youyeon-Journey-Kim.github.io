`---
layout: post
title: 데이터 엔지니어가 알아야하는 Elasticsearch
tags: [엘라스틱서치, Elasticsearch]
math: true
date: 2021-08-01 22:13 +0800
---

### 데이터 엔지니어가 알아야하는 Elasticsearch


_이번에 회사에서 맡게 된 프로젝트에서 Elasticsearch를 쓰게 되었다. 이유는 대용량 텍스트 데이터의 처리 속도 + 형태소 분석기의 활용을 위해서다._

내가 ES 공부를 위해 노션에 정리한 내용을 공유해보겠다.

#### Elasticsearch란?   
Apache Lucene(아파치 루씬) 기반의 Java 오픈소스 분산 검색엔진이다.

Elasticsearch를 통해 루씬 라이브러리를 단독으로 사용할 수 있게 되었으며, 방대한 양의 데이터를 신속하게,거의 실시간(NRT, Near Real Time)으로 저장, 검색 ,분석 할 수 있다.


Elasticsearch는 검색을 위해 단독으로 사용되기도 하며, ELK(Elasticsearch/Logstash/Kibana) 스택으로 사용되기도 한다.
) ELK 스택이란 다음과 같다.

- __Logstash__
    - 다양한 소스(DB,csv파일 등)의 로그 또는 트랜잭션 데이터를 수집, 집계, 파싱하여 Elasticsearch로 전달
- __Elasticsearch__
    - Logstash로부터 받은 데이터를 검색 및 집계를 하여 관심있는 정보를 흭득
- __Kibana__
    - Elasticsearch의 빠를 검색을 통해 데이터를 시각화 및 모니터링
![img1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F993B7E495C98CAA706)


***

**Elasticsearch와 관계형 DB 비교**
