---
title: '그래프'
date: '2022-12-20'
tags: ['algorithm', 'algorithm study', 'python', 'boj', 'graph']
draft: false
summary: 알고리즘 스터디 5주차 - 그래프
layout: PostSimple
---

이번 주 알고리즘 스터디 주제는 dfs && bfs였다. 워낙 방대하고 나에게는 어려운 부분이라 그래프부터 정리를 해보려 한다.

# 그래프

그래프는 어떤 자료나 개념을 표현하는 정점들의 집합과 이들을 연결하는 간선들의 집합으로 구성된 자료구조이다. 이 때, 정점의 위치나 간선의 순서는 그래프의 정의에 포함되지 않는다. 따라서 다른 모양임에도 같은 그래프를 표현할 수도 있다.

## 그래프의 종류

그래프의 정의는 위처럼 간단하지만, 표현하고자 하는 대상에 따라 여러가지 변형된 형태를 가질 수 있다. 정점이나 간선에 추가적인 속성을 부여할 수도 있고, 제약을 둘 수도 있다.

대표적으로는 방향 그래프가 있으며, 각 간선이 방향이라는 새로운 속성을 가진다.

반대로 무향 그래프는 각 간선에 방향이 없는 그래프를 뜻한다.

또한, 가중치 그래프는 각 간선마다 가중치 속성을 부여해서 각 정점사이의 거리, 비율 등의 정보를 표현하는 데 사용된다.

![Alt text](https://github.com/chanwoong1/chanwoong1.github.io/blob/main/public/static/images/blog_posts/algorithm_study/graph/graph_md/00.png?raw=true)

그림 중, 다중 그래프는 두 정점 사이에 두개 이상의 간선이 포함될 때 사용된다.

루트 없는 트리는 부모 자식의 관계가 없을 뿐 트리의 구조를 띄고 있는 무향 그래프를 말한다.

이분 그래프는 정점들을 겹치지 않는 두개의 그룹으로 나누어 서로 다른 그룹에 속한 경우에만 간선을 연결하도록 만든 것이다.

마지막으로 DAG는 사이클 없는 방향 그래프(Directed Acyclic Graph)를 줄여 말한 것이며, 한 점에서 출발해서 자기 자신으로 돌아오는 경로가 존재하지 않을 경우를 말한다.

## 그래프의 경로

그래프에서 경로는 가장 중요한 개념 중 하나로, 서로 연결된 간선들을 순서대로 나열한 것이다. 경로는 거쳐 가는 정점의 번호만을 사용해서 간단히 표기할 수 있다.

## 그래프 표현 방법

- 인접 리스트 표현

  인접 리스트 표현은 각 정점마다 해당 정점에서 나가는 간선의 목록을 저장해서 그래프로 표현한다. 리스트를 사용해서 표현하기 때문에 계산 속도가 좋지 않을 수 있다. 그러나 간선의 수에 따라 복잡도가 결정이 되므로, 간선의 수가 적다면 사용하기 좋은 방법일 수 있다. 정점의 수를 N, 간선의 수를 E라고 했을 경우, 인접 리스트의 시간 복잡도는 O(N + E)가 된다.

- 인접 행렬 표현

  인접 행렬 표현은 2차원 배열을 이용해서 그래프의 간선 정보를 저장한다. 정점의 번호 (u, v)가 주어졌을 때, 두 정점을 잇는 간선이 있는지 한번의 접근만으로 확인할 수 있다는 장점이 있다. 그러나, 간선의 갯수와 관계없이 항상 **N X N** 크기의 공간을 사용하기 때문에, 정점의 갯수에 비해 간선이 적다면 복잡도 면에서 좋지 않은 결과가 나올 수 있다.

- 암시적 그래프 표현

  그래프를 통해 문제를 풀더라도, 항상 그래프 전체를 메모리에 저장해 둘 필요는 없다. 그래프의 크기는 매우 크지만, 실제로는 일부만 사용하는 경우, 각 정점이 인접해 있는지만 확인하면 된다. 주어진 입력을 그래프로 변환하는 과정을 거칠 필요가 없다.

# 출처

[알고리즘 문제 해결 전략](https://book.algospot.com/index.html)
