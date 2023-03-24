---
layout: post
title:  "[JS/CodingTest] 자바스크립트 핵심 문법"
date:   2023-03-24
categories: JSCodingTest
---


# 패스트캠퍼스 온라인 강의 
## Part1.Ch01-02.자바스크립트 핵심 문법

--- 

### 알고리즘 코딩테스트 문제의 입출력 양식
* 문제에서 입력 형식과 출력 형식이 존재한다. 

> 표준 출력 (console.log())
```
//단순 문자열
console.log('오이');

//템플릿 리터럴을 이용하여 문자열 내부에 변수 출력
let result = '오이';
console.log(`정담은 ${result}입니다.`);
```

> 빠른 출력 (반복문과 같이 계속 console.log를 찍어내는 것이 아니라 하나의 변수를 선언하여 한 번에 console.log하는 것이 낫다)
```
let answer = '';
/*
여러 출력 결과를 한 줄에 하나씩 출력할 때 매 번 console.log()를 실행하지 않고,
하나의 문자열에 결과를 저장해서 한꺼번에 출력하는 것이 대개 더 빠르게 수행됩니다.
*/
for (let i = 1; i <= 100; i++) {
answer += i + '\n
'; // 문자열로 변환하여 기록
}
console.log(answer)
```

> 입력, fs 모듈 (입력 데이터가 텍스트 파일 형태로 주어지는 경우 사용하는 파일 시스템 모듈)
```
// readline 모듈보다는 fs를 이용해 파일 전체를 읽어 들여 처리하기
let fs = require('fs');
//문제에서 주어진 파일명이 /dev/stdin일 때,
let input = fs.readFileSync('/dev/stdin').toString().split('\n');
// let input = fs.readFileSync('input.txt').toString().split('\n');
console.log(input);
```

ChatGPT/Q. require함수란?

A. 다른 파일에서 작성된 코드나 라이브러리를 현재 파일에서 사용할 수 있습니다. require 함수를 사용하여 모듈을 가져오면 해당 모듈의 내용을 변수에 할당하여 사용할 수 있습니다.

* require을 통해 모듈을 가져오는 fs 객체를 선언하고 readFileSync를 통해 파일에 데이터를 읽고 toString 문자열로 변환시킨 데이터들을 \n 줄바꿈을 기준으로 데이터를 잘라서 배열에 담아 input 변수에 담는다. 

> 입력, readline 모듈 (파일 시스템을 이용하지 못하도록 막을 수도 있다. fs 모듈을 사용할 수 없을 때, readline을 사용한다.)
```
const rl = require('readline').createInterface({
input: process.stdin,
output: process.stdout
});
let input = [];
//사용자가 입력한 한 줄인 line을 push 함수를 통해 input 배열에 담는다. 
rl.on('line', function(line) {
// 콘솔 입력 창에서 줄바꿈(Enter)를 입력할 때마다 호출
input.push(line);
}).on('close', function() {
// 사용자가 콘솔 입력 창에서 Ctrl + C 혹은 Ctrl + D를 입력하면 호출(입력의 종료)
console.log(input);
process.exit();
});
```

사용자한테 한 줄 한 줄 입력을 받아서 읽는다.


### 기본 사칙 연산
```
console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(parseInt(a / b)); // 몫만 남기기
console.log(a % b);
```

### 조건문 
### for 반복문 
### while 반복문

### 수 <-> 문자열
```
/*
Int -> String
*/
let a = "777";
let b = Number(a);
console.log(b); // 777

/*
String -> Int
*/
let a = 777;
let b = String(a);
console.log(b); // "777"

```

### array.reduce()
가장 큰 값/작은 값 찾기, 원소 합 찾기

* 원소를 순차적으로 연산을 수행할 때 사용한다. 
* 배열에 모든 원소를 하나씩 확인한다. 
```
/*
reduce() 메서드는 배열의 각 요소에 대해 reducer 함수를 실행한 뒤에 하나의 결과를 반환합니다.
reducer의 형태: (accumulator, currentValue) => (반환값)
- 배열의 각 원소를 하나씩 확인하며, 각 원소는 currentValue에 해당합니다.
- 반환값은 그 이후의 원소에 대하여 accumulator에 저장됩니다.
*/

let data = [5, 2, 9, 8, 4];

// minValue 구하기 예제
let minValue = data.reduce((a, b) => Math.min(a, b));
console.log(minValue); // 2

// 원소의 합계 구하기 예제
let summary = data.reduce((a, b) => a + b);
console.log(summary); // 28

```

### 배열 생성 및 초기화
```
// 직접 값을 설정하여 초기화
let arr = [8, 1, 4, 5, 7];

// 길이가 5이고 모든 원소의 값이 0인 배열 초기화
let arr = new Array(5).fill(0);
```

### 집합 자료형
특정 원소의 등장 여부를 파악한다.
set은 중복된 것은 생성하지 않는다. 
has는 원소를 검색한다. 
add/delete는 배열의 원소를 추가하고 지운다.
for of문을 통해 원소를 출력한다.
```
let mySet = new Set(); // 집합 객체 생성
// 여러 개의 원소 삽입
mySet.add(3);
mySet.add(5);
mySet.add(7);
mySet.add(3);
console.log(`원소의 개수: ${mySet.size}`);
console.log(`원소 7을 포함하고 있는가? ${mySet.has(7)}`);
// 원소 5 제거
mySet.delete(5);
// 원소를 하나씩 출력
for (let item of mySet) console.log(item);
```

### 특정 자리에서 소수점 반올림하기 ( toFixed() )
```
// 특정 실수에 대하여 toFixed()를 이용해 소수점 아래 둘째 자리까지 출력
let x = 123.456;
console.log(x.toFixed(2))
```

### 이스케이프 시퀀스
* \t : 탭
* \\ : 역 슬래시
* \" : 큰 따옴표
* \' : 작은 따옴표




