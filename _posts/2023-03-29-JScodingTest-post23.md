---
layout: post
title:  "[JS/CodingTest] 트리와 우선순위 큐"
date:   2023-03-29
categories: JSCodingTest

---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch02-05. 트리와 우선순위 큐

--- 

### 1. 트리란?

* 계층적인 구조를 표현하는 자료구조이다. 
![image](https://user-images.githubusercontent.com/88815795/228222363-af00dd01-251e-4ece-939b-d802710cc002.png)

* 루트 노드 : 부모가 없는 최상위 노드
* 단말 노드(=리프 노드) : 자식이 없는 노드
* 깊이 : 루트 노드에서의 길이 ( 출발 노드에서 목적지 노드까지의 간선의 수 )

### 2. 이진 트리란?

* 최대 2개의 자식을 가지는 트리

### 3. 우선순위 큐란?

* 우선순위에 따라 데이터를 추출하는 자료 구조
* 일반적으로 힙(heap)으로 구현

### 4. 스택 vs 큐 vs 우선순위 큐

![image](https://user-images.githubusercontent.com/88815795/228223700-a00d0d60-26ed-4fa4-9f33-7243f4b1d2a0.png)

### 5. 우선순위 큐를 구현하는 방법

ㄱ. 배열 : 삽입 O(1) / 삭제 O(N)
ㄴ. 힙 : 삽입 O(logN) / 삭제 O(logN)

* 우선순위 큐는 이진 트리를 이용한다. 

### 6. 이진트리의 종류

ㄱ. 포화 이진 트리 : 모든 노드가 두 자식을 가진 트리
ㄴ. 완전 이진 트리 : 모든 노드가 왼쪽 자식부터 채워진 트리
ㄷ. 높이 균형 트리 : 왼쪽 자식 트리와 오른쪽 자식 트리의 높이가 1 이상 차이 나지 않는 트리 

### 7. 힙(heap) -> 완전 이진트리의 이용

* 원소들 중에 최댓값 or 최솟값을 빠르게 찾는 자료구조
* 우선순위가 높은 노드가 루트에 존재한다.
* 최대 힙: 값이 큰 원소부터 추출 

//부모노드 > 자식노드 

//루트노드가 가장 큰 값

* 최소 힙: 값이 작은 원소부터 추출 Heapify

//부모노드 < 자식노드

//루트노드가 가장 작은 값

![image](https://user-images.githubusercontent.com/88815795/228225876-e7f671b9-a365-448a-91c5-aa9f02220978.png)


* 삽입/삭제: O(logN)

// 삽입 : 상향식으로 부모가 자신보다 더 작으면 위치를 교체한다.

![image](https://user-images.githubusercontent.com/88815795/228226240-8288c56e-502d-45b3-8cb9-f76f8c94b91c.png)

// 삭제 : 가장 마지막 노드를 루트 노드로 바꾼다.

![image](https://user-images.githubusercontent.com/88815795/228226268-005d4e76-ecf2-4764-8c19-6881bc8c86b4.png)

### 8. 자바스크립트에서 우선순위 큐 ( = 힙)
![image](https://user-images.githubusercontent.com/88815795/228519378-9a1d5e86-c4c5-4967-86d3-9d8131d706d4.png)





