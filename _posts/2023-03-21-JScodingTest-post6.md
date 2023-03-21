---
layout: post
title:  "[JS/CodingTest] 프로그래머스 입문_배열 두 배 만들기"
date:   2023-03-21
categories: JSCodingTest
---


# 프로그래머스 입문
## 배열 두 배 만들기

--- 

### 문제
정수 배열 numbers가 매개변수로 주어집니다. numbers의 각 원소에 두배한 원소를 가진 배열을 return하도록 solution 함수를 완성해주세요.

제한사항

-10,000 ≤ numbers의 원소 ≤ 10,000

1 ≤ numbers의 길이 ≤ 1,000

입출력 예

```
numbers	result
[1, 2, 3, 4, 5]	[2, 4, 6, 8, 10]
[1, 2, 100, -99, 1, 2, 3]	[2, 4, 200, -198, 2, 4, 6]
```

입출력 예 설명

입출력 예 #1

[1, 2, 3, 4, 5]의 각 원소에 두배를 한 배열 [2, 4, 6, 8, 10]을 return합니다.

입출력 예 #2

[1, 2, 100, -99, 1, 2, 3]의 각 원소에 두배를 한 배열 [2, 4, 200, -198, 2, 4, 6]을 return합니다.


### 나의 풀이

```
function solution(numbers) {
    var answer = [];
    for(let element of numbers){
        answer.push(element*2);
    }

    return answer;
}

```

- for of 문을 한 번도 사용한 적이 없어서 활용해보았다.


### 모든 풀이 중
```
function solution(numbers) {
    return numbers.map(i=>i*2);
}
```

> map 함수를 사용한 코드이다. map함수도 다음 번에 활용해보아야겠다.

* map은 callback 함수를 각각의 요소에 대해 한번씩 순서대로 불러 그 함수의 반환값으로 새로운 배열을 만든다. 즉, array를 돌면서 array 로 결과가 출력된다.


### 기억해야할 점

1. map 함수
