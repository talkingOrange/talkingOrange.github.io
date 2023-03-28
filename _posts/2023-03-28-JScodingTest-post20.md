---
layout: post
title:  "[JS/CodingTest] 배열과 리스트"
date:   2023-03-28
categories: JSCodingTest

---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch02-02. 배열과 리스트

--- 

### 1. 배열이란?

* 같은 성질을 가진 데이터를 나열한 자료구조
* 인덱스가 존재한다. (0부터 시작)
* 인덱스에 접근하는 것은 O(1)의 복잡도를 가진다. 
* 컴퓨터에서 배열공간은 연속적으로 할당된다.
* 장점: 조회가 빠르다
* 단점: 배열의 크기를 미리 지정해야하여 데이터 추가 및 삭제에 한계가 존재한다. 

![image](https://user-images.githubusercontent.com/88815795/228207620-587f232e-4a38-45a3-840f-2e9606a38ee9.png)


### 2. 연결리스트란?

* 컴퓨터에서 주소가 연속적이지 않다.
* 장점: 포인터로 다음 데이터 위치를 가리켜서 삽입과 삭제가 간편하다, 배열의 크기를 동적 변경할 수 있다.
* 단점: 데이터 검색이 느리다.

![image](https://user-images.githubusercontent.com/88815795/228208057-2a9cbbca-c217-4b67-adda-3256e8997c65.png)

### 코딩테스트에서 연결리스트

* 연결리스트는 직접 구현하지 않아도 알고리즘 문제를 해결하는데에 있어서 어려움이 없다. 
* 따라서 따로 구현하는 법을 강의에서 다루지않는다. 

### 자바스크립트에서 배열

* 배열 기능을 기본적으로 제공한다.
* 인덱스로 직접 접근이 가능하다.
* 자바스크립트에서는 동적 배열의 기능을 제공한다. 따라서 맨 뒤에 원소 추가가 가능하다. 

=> 내부적으로 포인터를 사용해서 연결 리스트의 장점을 구현한다. 

=> 배열의 용량이 차면 자동적으로 크기를 증가한다. 

* 배열과 스택이 필요할 때 사용한다. (큐는 XXX)

```
//배열 생성(1)
let arr = [];

arr.push(7);

//배열 생성(2)
let arr = new Array();

arr.push(7);

//배열의 크기를 정하고 하나의 값으로 초기화 하기
let arr = Array.from({length:5}, ()=> 7);  //[7,7,7,7,7]

// 2차원 배열
let arr = [
   [0,1,2,3],
   [4,5,6,7],
   [8,9,10,11]
];

// 2차원 배열 크기만 잡고 값은 안들어가도록 초기화
let arr = Array.from(Array(4), ()=>new Array(5)) //5개 배열들이 4줄 생김
```

* 반복문으로 2차원 배열 초기화
 ![image](https://user-images.githubusercontent.com/88815795/228211304-dd39d70e-59b5-4a25-ae67-81ffd224a814.png)

* concat() : 여러 개의 배열을 이어 붙여서 합친 결과를 반환한다. O(N)
![image](https://user-images.githubusercontent.com/88815795/228213814-adf790f7-e44f-4a22-bf9e-1310b3cd83c6.png)

* slice(left, right) : 특정 구간의 원소를 꺼낸 배열을 반환한다. O(N) // 시작 인덱스 ~ 끝 인덱스 -1
![image](https://user-images.githubusercontent.com/88815795/228214141-2a533690-ab7b-4de6-ac05-a320619fdbc4.png)

* indexOf() : 특정한 값을 가지는 원소의 첫 째 인덱스를 반환한다. O(N) //없으면 -1 반환
![image](https://user-images.githubusercontent.com/88815795/228214492-6dda4799-f9f1-4fa9-92ee-85587bac2634.png)

