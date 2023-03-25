---
layout: post
title:  "[JS/CodingTest] JS 조건문 문제 풀이"
date:   2023-03-25
categories: JSCodingTest
---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch01-04.JS 조건문 문제 풀이

--- 

### 시험 성적

```
//내가 푼 코드
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split("\n");

let num = Number(input[0]);
let answer = '';
if( 90 <= num && num <= 100){
    answer = 'A';
}else if( 80 <= num && num < 90){
    answer = 'B';
}else if(70 <= num && num < 80){
    answer = 'C';
}else if(60 <= num && num <70 ){
    answer = 'D';
}else
    answer = 'F';

console.log(answer);
```

```
//답안으로 나온 코드
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n
');
data = Number(input[0]);
function check(a) {
if (90 <= a && a <= 100) console.log('A');
else if (80 <= a && a <= 89) console.log('B');
else if (70 <= a && a <= 79) console.log('C');
else if (60 <= a && a <= 69) console.log('D');
else console.log('F');
}
check(data);
```

* 내 답안과 차이점은 함수로 만들었다는 것이다.
* 무언가를 작성할 때, 단위별로 함수를 만들어볼 생각을 해보자!

### 오븐 시계

```
let hour = Number(input[0].split(' ')[0]);
let minute = Number(input[0].split(' ')[1])
```

```
let [a, b] = input[0].split(' ').map(Number)
```

* map 함수로 쉽게 담을 수 있다.



