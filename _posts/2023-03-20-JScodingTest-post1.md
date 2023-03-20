---
layout: post
title:  "[JS/CodingTest] Array 중복 제거 "
date:   2023-03-20
categories: JSCodingTest
---

# Array 중복 제거하기

--- 

### 1. Set()
ES6문법으로 중복을 허용하지 않는 함수이다. 

```
const nums = [ 1, 2, 3, 6, 6, 7, 2, 2, 8, 9];

const uniqueNums = [...new Set(nums)];
console.log(uniqueNums);
```

> ... 문법
* 비구조화 할당
* 배열[] 이나 객체{} 안의 값을 편하게 꺼내 쓸 수 있는 문법.
* ... 이후 남은 값들을 모두 담게된다. 

> new 생성자 함수
* 일반 함수와 기술적인 차이는 없다.
* 함수 이름의 첫 글자는 대문자다

### 2. indexOf()
배열 함수다. 배열의 특정 요소가 어느 위치에 존재하는지 알려준다. 

```
const uniqueNums = nums.filter((item, position) => {
   return nums.indexOf(item) === position;
});

console.log(uniqueNums);

```

> filter함수
* 특정 조건을 만족하는 새로운 배열을 필요로 할 때 사용한다. 
* 조건을 만족하는 원소에 한에서 새로운 배열을 만들어준다.

### 3. caching / frequency map
배열을 loop 하면서 각각의 요소의 출현빈도를 array나 object에 저장하고 중복검사를 한다.

```
function uniqueNums(arr){
   const uniqueElements = {}
   const result = []
   for ( let element of arr ) {
      if ( !uniqueElements[element] ) {
         result.push(element);
      }
      uniqueElements[element]= element;
   }
   return result;
}

console.log(uniqueNums(nums));
   
```

> for of 문
* 익스플로러 환경에서 지원하지 않는다.
* 열거 가능한 요소의 개수만큼 반복적으로 실행한다. 
* 객체는 사용이 안된다. 

> for in 문
* for of문과 마찬가지로 요소의 개수만큼 반복하는데, 차이점은 for of문은 객체의 key값에도 접근이 가능하다. 
* 객체의 value값에는 직접 접근이 불가능하다. 


공부자료 : https://www.youtube.com/watch?v=zbH7YqUxFpA, 그 외 다수 사이트


+) 자바스크립트로 코딩테스트를 볼 경우, 입출력에 대한 이야기

https://velog.io/@bigsaigon333/Javascript%EB%A1%9C-%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%A4%80%EB%B9%84%ED%95%98%EA%B8%B01-%EC%9E%85%EC%B6%9C%EB%A0%A5

