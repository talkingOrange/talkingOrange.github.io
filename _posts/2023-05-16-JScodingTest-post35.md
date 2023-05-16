---
layout: post
title:  "[JS/CodingTest] 그리디 문제 풀이"
date:   2023-05-16
categories: JSCodingTest
---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch04-03. 그리디 문제 풀이

--- 

### [설탕배달](https://www.acmicpc.net/problem/2839) 
 
[ 문제 ]

3kg 봉지, 5kg 봉지로 Nkg 설탕을 배달한다. 

이 때, 최소 봉지로 설탕을 배달한다면?

(정확하게 Nkg 나눌 수 없다면 -1 출력)

[ 아이디어(틀림) ]

1. Nkg을 5로 먼저 나눈다.
2. 몫을 저장한다.
3. 나머지를 3으로 나눈다.
4. 만약 나머지가 0이라면, 2번 값에 몫을 더해준다.
 
 4-1. 만약 나머지가 0이 아니라면, Nkg을 3으로 나눈다. 
 4-2. 나머지가 0이라면, 몫을 저장한다.
 4-3. 나머지가 0이 아니라면, -1을 저장한다.

5. 출력한다.

* 해당 아이디어가 틀린 이유는, 만약 N=11이라면, 답은 3이지만, 이 아이디어에는 -1이 출력됨.

[ 아이디어 ]

1. N%5===0이면, 몫을 저장한다.
2. N%5!==0이면, N%5===0이 될 때까지 N-3을 반복해준다.

나머지가 0이 안되면, -1을 저장한다.


```
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n
');
let n = Number(input[0]);
let cnt = 0;
let flag = false;
while (n >= 0) { // 더 이상 반복할 수 없을 때까지 반복
// n이 0이 되었거나, 5로 나누어 떨어지는 값인 경우
if (n == 0 || n % 5 == 0) {
cnt += parseInt(n / 5); // 5로 나눈 몫을 더하기
console.log(cnt);
flag = true;
break;
}
n -= 3;
cnt += 1;
}
if (!flag) {
console.log(-1);
}
```

