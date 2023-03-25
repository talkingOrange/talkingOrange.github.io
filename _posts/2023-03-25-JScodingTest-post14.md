---
layout: post
title:  "[JS/CodingTest] JS 입출력 문제 풀이"
date:   2023-03-25
categories: JSCodingTest
---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch01-03.JS 입출력 문제 풀이

--- 

###  사칙연산

```
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split("\n");

let line = input[0].split(' ');

let a  = Number(line[0]);
let b = Number(line[1]);

console.log(a+b);
console.log(a-b);
console.log(a*b);
console.log(parseInt(a/b));
console.log(a%b);
```

##### 확인해야할 것

* fs로 불러와 배열의 내용을 숫자로 변형할 때, 다음과 같이 줄여쓸 수 있다.

```
let a = Number(input[0].split(' ')[0]);
```

* 나눗셈 연산에서는 몫을 구해야함으로 paresInt()가 필요하다. 

