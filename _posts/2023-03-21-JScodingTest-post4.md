---
layout: post
title:  "[JS/CodingTest] 애너그램 판별"
date:   2023-03-20
categories: JSCodingTest
---

# 애너그램 판별하기

--- 

### 애너그램이란?
단어의 문자를 재배열해서 다른 뜻을 가지는 다른 단어로 바꾼다.

ex) Listen 과 Silent => 두 단어는 다르지만 구성요소는 같다.

### 1. split(), sort(), join()

```
const stringA = "listen";
const stringB = "silent";

function isAnagram(strA, strB){
   if(strA.length !== strB.length){   //문자열의 길이 검사
      return false;
   }
   return strA.split("").sort().join() === strB.split("").sort().join();
}

console.log(isAnagram(strA, strB);

```
>split() : 문자열을 일정한 구분자로 잘라서 배열로 저장한다. 

* split() : 문자열 전체를 배열에 담는다.

* split(separator) :문자열을 자를 구분자

* split(separator, limit) : 구분자와 최대 분할 수

>sort() : 정렬

* sort() : 유니코드 순서에 따른 오름차순
* sort(함수) 

```
// 숫자 크기 순서에 따른 오름차순
arr.sort(function(a, b)  {
  return a - b;
});
```

```
// 숫자 크기 순서에 따른 내림차순
arr.sort(function(a, b)  {
  return b - a;
});
```

이외에도 문자열 내림차순, 대소문자 구분없는 오름차순/내림차순 등을 만들 수 있다.

> join() : 떨어진 배열 요소들을 하나로 연결한다.

* join() : 쉼표로 붙인다. 
* join('') : 단어끼리 그냥 붙인다.
* join('-') : 단어 사이에 - 를 넣고 붙인다. 

### 2. hashMap object 생성
배열 함수다. 배열의 특정 요소가 어느 위치에 존재하는지 알려준다. 

```
function isAnagram(strA, strB){
   if(strA.length !== strB.length) {
      return false;
   }
   const hashMap = {}
   for (const char of strA){
      hashMap[char] = hashMap[char] ? hashMap[char] + 1 : 1;
   }
   for(const char of strB){
      if(!hashMap[char]){
         return false;
      }
      hashMap[char]--;
   }
   return true;
}

```

> hashMap 값 가져오기, 넣기

```
var map = new HashMap();
map.put("user_id", "speed");
map.get("user_id") // return 'speed' 

```
* Map 객체는 키-값 쌍으로 이루어져있다. 



공부자료 : [https://www.youtube.com/watch?v=zbH7YqUxFpA](https://youtube.com/watch?v=WYXT6fnp9Eg&feature=shares), 그 외 다수 사이트

