---
layout: post
title:  "[JS/CodingTest] 버블 정렬"
date:   2023-03-31
categories: JSCodingTest
---


# 패스트캠퍼스 온라인 강의 
## Part1.Ch03-02. 버블 정렬

--- 

### 버블정렬이란? (O(N^2))

* 인접한 두 원소를 확인해서 정렬이 안 되어 있을 때, 위치를 변경한다.
* 비효율적인 정렬 알고리즘

ㄱ. 첫째와 둘째를 비교한다.
ㄴ. 둘째와 셋째를 비교한다.
ㄷ. 셋째와 넷째를 비교한다.
ㄹ. 가장 큰 원소가 맨 뒤로 이동하게된다. 

즉, N개의 원소일 때 가장 큰 값이 오른쪽으로 이동하여 N-1번 반복한다. (선형탐색)


![image](https://user-images.githubusercontent.com/88815795/229134828-0af83977-2535-4570-8c16-2c77ebc1ae0c.png)
