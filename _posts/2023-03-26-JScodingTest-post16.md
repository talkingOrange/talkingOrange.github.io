---
layout: post
title:  "[JS/CodingTest] JS 반복문 문제 풀이"
date:   2023-03-26
categories: JSCodingTest

---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch01-04.JS 반복문 문제 풀이

--- 

### 합

* 문자열을 수로 변환할 때, parseInt 보다 Number 함수의 속도가 더 빠르다. 

```
//내가 푼 코드
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');

let num = Number(input[0]);
let answer = 0;
for(let i=1; i<=num; i++){
    answer+=i;
}

console.log(answer);
```

* 시간 복잡도는 O(n)이다.

```
//답안으로 나온 코드
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n
');
// 문자열을 수로 변환할 때 parseInt에 비하여 Number의 속도가 더 빠르게 동작
let n = Number(input[0]);
// 등차수열의 합 공식
console.log(n * (n + 1) / 2);
```

* 등차수열을 이용하여, O(상수)로 빠른 처리가 가능하다. 


### 구구단

* 템플릿 리터럴을 사용해서 문자열 내부에 변수를 포함한다. 
``` 
console.log(`${num} * ${i} = ${num * i}`); 
```


### 별 찍기 - 1

* 이중 반복문에서 첫 for문은 열, 두번째 for문은 행을 의미한다.

### 빠른 A+B

* 어떤 변수에 값을 계속해서 붙여나가고 싶다면 for문과 +=을 이용한다.

```
answer += a+b+'\n'
```


