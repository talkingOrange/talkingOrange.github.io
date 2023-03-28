---
layout: post
title:  "[JS/CodingTest] js 큐"
date:   2023-03-28
categories: JSCodingTest

---


# 패스트캠퍼스 온라인 강의 
## Part1.Ch02-04. js 큐

--- 

### 1. 큐란?

* 먼저 삽입된 데이터가 먼저 추출되는 자료구조
* 꼬리에서 들어가서 머리에서 나온다.

![image](https://user-images.githubusercontent.com/88815795/228221118-2b5a380f-d2a2-46de-a6e9-1767464fc523.png)


### 2. 큐 동작 속도

* 배열 < 연결리스트
* 하지만 자바스크립트에서는 `Dictionary 자료형`으로 큐를 구현하는 것이 더 간단하다.

![image](https://user-images.githubusercontent.com/88815795/228220053-f51ed4be-07c0-4be3-a10b-a3bf039b0571.png)

* enqueue: 큐에 원소 추가
* dequeue: 큐 원소 제거 및 반환
* peek: head에 있는 원소 반환

