---
layout: post
title: Elasticsearch
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
    - Elasticsearch의 빠른 검색을 통해 데이터를 시각화 및 모니터링
![img1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F993B7E495C98CAA706)


***

**Elasticsearch와 RDBMS 비교**

흔히 사용하고 있는 RDB는 Elasticsearch에서 다음과 같이 대응 시킬 수 있다.

![img2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F998444375C98CC021F)

|RDBMS|Elasticsearch|
|:---:|:---:|
|Database|Index|
|Table|Type|
|Row|Document|
|Column|Field|
|Index|Analyze|
|Primary Key|_id|
|Schema|Mapping|
|Physical partition|Shard|
|Logical Partition|Route|
|Relational|Parent/Child,Nested|
|SQL|Query DSL|


***

**Elasticsearch 아키텍쳐/용어 정리**   

Elasticsearch에서 사용하는 대부분의 개념은 RDBMS에도 존재하는 개념들이다.   
![Elasticsearch Architecture](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99A97A355C98D42D2E)

- **Cluster(클러스터)**
    - ##### 클러스터란 ES에서 가장 큰 시스템 단위를 말하며, 최소 하나 이상의 노들 이루어진 노드들의 집합니다.   
    ##### 서로 다른 클러스터는 데이터의 접근, 교환을 할 수 없는 독립적인 시스템으로 유지되며, 여러대의 서버가 하나의 클러스터를 구성할 수 있고, 한 서버에 여러개의 클러스터가 존재할 수 도 있다.   
- **Node(노드)**
    - ##### Elasticsearch를 구성하는 하나의 단위 프로세스를 말한다. 그 역할에 따라 Master-eligible, Data, Ingest, Tribe 노드로 구분할 수 있다.   
        - ##### master-eligible node
            - ##### 클러스터를 제어하는 마스터로 선택할 수 있는 노드를 말한다. master node의 역할은 아래오 같다.
                - ##### 인덱스 생성, 삭제

                - ##### 클러스터 노드들의 추적, 관리

                - ##### 데이터 입력 시 어느 샤드에 할당할 것인지

        - ##### Data node
            - ##### 데이터와 관련된 CRUD 작업과 관련있는 노드로 CPU,메모리 등 자원을 많이 소모하므로 모니터링이 필요하며, master 노드와 분리되는 것이 좋다.
            
        - ##### Ingest node
            - ##### 데이터를 변환하는 등 사전 처리 파이프라인을 실행하는 역할을 합니다.
        - ##### Coordination only node
            - ##### data node와 master-eligible node의 일을 대신하는 노드로 대규모 클러스터에서 큰 이점이 있다. 로드밸런서와 비슷한 역할을 함

- **Index/Shard/Replice**   

    - ##### Elasticsearch에서 index는 RDBMS에서 database와 대응하는 개념이다. shard와 replica는 Elasticsearch에만 존재하는 개념이 아닌, 분산 데이터베이스 시스템에도 존재하는 개념이다.  

    - ##### Sharding은 데이터를 분산해서 저장하는 방법을 의미한다. 즉, Elasticsearch에서 스케일 아웃을 위해 index를 여러 shard로 쪼갠 것이다. 기본적으로 1개가 존재하며, 검색 성능 향상을 위해 클러스터의 샤드 갯수를 조정하는 튜닝을 하기도 한다.

    - ##### Replica는 또 다른 형태의 Shard라고 할 수 있다. 노드를 손실했을 경우 데이터의 신뢰성을 위해 샤드들을 복제하는 것, 따라서 replica는 서로 다른 노드레 존재할 것을 권장한다. 아래 사진에서 보는 바와 같이 Replica1은 Node2에 존재하는 것을 확인 할 수 있다.
    ![replica_Example](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F991563425C98CB341A)


***
