---
layout: post
title:  "[JS/CodingTest] 병합 정렬"
date:   2023-04-01
categories: JSCodingTest
---


# 패스트캠퍼스 온라인 강의 
## Part1.Ch03-04. 병합 정렬

--- 

### 병합정렬이란? (O(NlogN))

* 자주쓰고 잘 이용됨.
* 전형적인 분할 정복 알고리즘이다.

#### 분할정복이란?
* 분할 : 큰 문제를 작은 문제로 쪼갠다.
* 정복 : 작은 문제를 해결한다.
* 조합 : 부분 답을 이용해 큰 문제를 해결한다. 

![image](https://user-images.githubusercontent.com/88815795/229289931-62263f45-c19d-4ede-84e5-8b71418df59a.png)

#### 분할정복의 단점
* 일반적으로 재귀함수를 사용하는데, 함수 호출이 늘어나며 `오버헤드`가 생길 수 있다.
** 오버헤드란? 제어프로그램이 시스템 지원을 위해 대기하는 시간

### 병합 정렬 동작 
ㄱ. 분할 : 정렬할 배열을 같은 크기로 2개의 배열로 분할
ㄴ. 정복 : 부분 배열 정렬 O(N) => 첫번째 원소부터 하나씩 확인한다.
ㄷ. 조합 : 하나의 배열로 합친다.

![image](https://user-images.githubusercontent.com/88815795/229290123-4f948b0b-910a-46f8-bee4-9753661a755d.png)

-> 각 배열에 원소가 하나만 남았다는 것이 정렬되어있다는 것이다. 

![image](https://user-images.githubusercontent.com/88815795/229293465-39ed098b-b782-4986-bc14-60cd2f73ae3c.png)

-> 정복 : 각각의 배열을 (0)에서부터 비교하고 더 작은 것들을 합친 배열에 넣고 index +1 을 해준다.

* 단점 : 정복에서 임시 배열이 필요하다.


### 병합 정렬 소스코드

![image](https://user-images.githubusercontent.com/88815795/229293641-5ad0569d-f8fb-476f-95af-a3da3414fb28.png)
![image](https://user-images.githubusercontent.com/88815795/229293709-a61e4f68-ab93-4eec-80e4-055e2942cad8.png)



