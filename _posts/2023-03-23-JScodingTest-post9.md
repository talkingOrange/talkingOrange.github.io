---
layout: post
title:  "[JS/CodingTest] 프로그래머스 입문_배열 자르기 "
date:   2023-03-23
categories: JSCodingTest
---

# 프로그래머스 입문
## 배열 자르기

--- 

### 문제
정수 배열 numbers와 정수 num1, num2가 매개변수로 주어질 때, numbers의 num1번 째 인덱스부터 num2번째 인덱스까지 자른 정수 배열을 return 하도록 solution 함수를 완성해보세요.

제한사항

2 ≤ numbers의 길이 ≤ 30

0 ≤ numbers의 원소 ≤ 1,000

0 ≤num1 < num2 < numbers의 길이

입출력 예
```
numbers	num1	num2	result
[1, 2, 3, 4, 5]	1	3	[2, 3, 4]
[1, 3, 5]	1	2	[3, 5]
```
입출력 예 설명

입출력 예 #1

[1, 2, 3, 4, 5]의 1번째 인덱스 2부터 3번째 인덱스 4 까지 자른 [2, 3, 4]를 return 합니다.

입출력 예 #2

[1, 3, 5]의 1번째 인덱스 3부터 2번째 인덱스 5까지 자른 [3, 5]를 return 합니다

### 나의 풀이

```
function solution(numbers, num1, num2) {
    let answer = [];
    for(let i = num1; i <=num2; i++){
        answer.push(numbers[i]);
    }
    return answer;
}
```

- 인덱스 num1 부터 num2까지를 for문을 돌려 새로 만든 배열안에 push해준다.


### 모든 풀이 중

```
function solution(numbers, num1, num2) {
    return numbers.splice(num1, num2-num1+1);
}
```

> 배열 splice함수 : 파라 미터로 시작index, 제거할 요소의 개수, 추가할 요소를 넣는다. 



### 기억해야할 점

1. 배열 splice 함수
2. 배열에서 사용하는 함수, 문자열에서 사용하는 함수 대표적인 것을 나눠서 정리해놓아야겠다.
