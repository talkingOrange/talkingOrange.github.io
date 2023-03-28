---
layout: post
title:  "[JS/CodingTest] js 스택"
date:   2023-03-28
categories: JSCodingTest

---


# 패스트캠퍼스 온라인 강의 
## Part1.Ch02-03. js 스택

--- 

### 1. 스택이란?

* 먼저 들어온 데이터가 나중에 나가는 자료구조

 ![image](https://user-images.githubusercontent.com/88815795/228216059-f999424b-d86c-4531-bb42-b263a050ddab.png)

* 머리 : 삽입되고 삭제되는 맨 위에 있는 원소이다. 

### 2. 스택 연산별 시간 복잡도

![image](https://user-images.githubusercontent.com/88815795/228216562-19b2e2c4-616a-4b5b-9381-55cd5f2a966b.png)

### 3. JavaScript에서의 스택

ㄱ. 배열 자료형

* push() : O(1)
* pop() : O(1)

+ if, 최상단원소(머리)부터 출력하고 싶을 경우

```
let reversed = stack.slice().reverse();
```

