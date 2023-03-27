---
layout: post
title:  "[JS/CodingTest] JS 문자열 문제 풀이"
date:   2023-03-27
categories: JSCodingTest

---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch01-07.JS 문자열 문제 풀이

--- 

### 1. 숫자의 합

```
// 문자열에 포함된 문자를 하나씩 확인하며
for (let x of string) {
// 모든 숫자를 더하기
answer += Number(x);
}
```
* 하나씩 확인해서 무언가를 처리해줄 때에는 for of문을 이용하면 된다!

### 2. 문자열 반복 

* string.charAt(숫자) : 숫자번째에 있는 char를 리턴해준다. 

### 3. 그룹 단어 체커

* set.has(원소) : 집합 set에서 어떤 원소가 존재하는지 확인해준다. 

### 4. 단어의 개수

* trim() : 문자열 양 끝의 공백을 제거한다.

```
let data = input[0].trim().split(" ");
```
