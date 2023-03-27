---
layout: post
title:  "[JS/CodingTest] JS 배열 문제 풀이"
date:   2023-03-27
categories: JSCodingTest

---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch01-06.JS 배열 문제 풀이

--- 

### 1. 최소, 최대


```
//내가 푼 코드
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');

let num = Number(input[0]);
let data = input[1].split(' ').map(Number);

data.sort((a,b)=> a-b);

console.log(data[0] + ' ' +data[data.length - 1])
```

* 배열의 sort 함수를 이용하여 정렬을 해준 다음, 데이터의 첫번째 인덱스와 마지막 인덱스를 출력함으로써 최소와 최대를 구해줬따.

```
//답안으로 나온 코드 1
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');
let n = Number(input[0]);
let arr = input[1].split(' ').map(Number);
/*
모든 정수는 -1,000,000보다 크거나 같고,
1,000,000보다 작거나 같은 정수이다.
*/
let minValue = 1000001; // 일단 큰 수로 초기화
let maxValue = -1000001; // 일단 작은 수로 초기화
for (let i = 0; i < n; i++) {
if (minValue > arr[i]) minValue = arr[i];
if (maxValue < arr[i]) maxValue = arr[i];
}
console.log(minValue, maxValue);
```

```
//답안으로 나온 코드 2
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let data = input[1].split(' ').map(x => Number(x));
let minValue = data.reduce((a, b) => Math.min(a, b));
let maxValue = data.reduce((a, b) => Math.max(a, b));
console.log(minValue + " " + maxValue);
```

* 차이점은 속도에 있다.
![image](https://user-images.githubusercontent.com/88815795/227892988-59226f36-9256-4586-b94a-ed7c6afab439.png)

마지막이 내가 구현한 코드의 메모리와 시간이고 상단 2개가 강의에서 소개된 코드의 메모리와 시간이다. 

강의에서 주어진 코드에서는 배열을 하나씩 비교하는데(O(n)), 내가 푼 코드에서는 sort함수를 이용하여 ([0],[1]), ([1],[2])... 중복되는 원소의 비교가 존재한다. 

### 2. 최댓값

```
//내가 푼 코드
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');
let max= 0;

for(let i=0; i<9; i++){
    let data = Number(input[i]);
    max= data.reduce((a,b)=>Math.max(a,b));
}

console.log(max);
console.log(input.indexOf(max)+1 );

```

* 런타임 에러가 발생했다. 

```
//답안으로 나온 코드
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');
let data = input.map(x => Number(x));
let max = Math.max(...data)
console.log(max)
console.log(input.indexOf(max) + 1;
```

* 풀이 과정, 아이디어는 같으나 skill의 문제인 듯하다.


```
for (let i = 0; i < 9; i++) { // 모든 데이터를 하나씩 확인하며
let data = Number(input[i]) }
```

* input의 데이터들을 받아오는 방법도 많이 알아두는게 좋을 것 같다.

* 그런데... 답안 코드도 틀렸습니다로 나온다..!


### 3. 나머지

* 집합은 중복되지 않은 원소를 담기 적합하다.

```
let set = new Set(); // 집합 객체 만들기
```

* set.add() : 집합에 원소 넣기
* set.size : 집합의 크기(=원소의 개수) 구하기

### 4. 평균은 넘겠지

* number.toFixed()를 통해 소수점을 제한한다. 



## 기억해야할 것

* 집합 자료형


