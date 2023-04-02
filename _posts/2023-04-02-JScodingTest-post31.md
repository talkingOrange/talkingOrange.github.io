---
layout: post
title:  "[JS/CodingTest] 정렬 문제 풀이 2 "
date:   2023-04-02
categories: JSCodingTest
---


# 패스트캠퍼스 온라인 강의 
## Part1.Ch03-07. 정렬 문제 풀이 2

--- 

### 좌표 정렬하기 

```
//내 풀이
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let num = Number(input[0]);
let dot = [];

for (let i = 1; i <= num; i++) {
let [x, y] = input[i].split(' ').map(Number);
dot.push([x, y]);
}

dot.sort(function(a,b){
 if(a[0] != b[0]){
     return a[0]-b[0] ;
 }else
    return a[1]-b[1];
});

let answer = "";

for (let element of dot){
    answer += element[0] + " " + element[1] + '\n';
}
console.log(answer)
```

##### 눈 여겨 볼 부분 😕

* fs 모듈로 파일을 로드하기 때문에 객체 -> 배열로 바꾸어 생각

```
let [x, y] = input[i].split(' ').map(Number);
dot.push([x, y]);
}
```

* 이에 따라 answer 출력하는 과정에서도 배열이 여러개인 상황임을 생각하여 `for of 문`을 이용!

```
let answer = "";

for (let element of dot){
    answer += element[0] + " " + element[1] + '\n';
}
```

### 좌표 정렬하기2

```
//내가 푼 코드
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');

let num = Number(input[0]);
let dot = [];

for(let i=1; i<=num; i++){
    let [x, y] = input[i].split(" ").map(Number);
    dot.push([x, y]);
}

dot.sort(function(a,b){
    if(a[1] !== b[1]) return a[1]-b[1];
    else return a[0]-b[0];
})

let answer = "";

for(let element of dot){
    answer += element[0] + " " + element[1] + "\n";
}

console.log(answer);
```


### 단어 정렬

```
// 내가 푼 코드 (틀림)
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');

let num = Number(input[0]);
let data = [];

for(let i=1; i<=num; i++){
    data.push(input[i]);
}

data = [...new Set(data)];

data.sort(function(a,b){
    if(a.length != b.length){
    return a.length - b.length;}
    else return a - b;
})

for (let x of data){
    console.log(x);
}

```

* 틀린 이유!

문자열의 경우 있는 그대로 출력하려면 sort의 기본 정렬 조건 함수인

```
if(a<b) return -1;
else if(a>b) return 1;
else return 0;
```

을 써주어야한다.


##### 기억해야할 것

* 중복된 원소를 제거하기 위한 집합 Set의 이용

` arr = [ ... new Set(arr) ] ; `
