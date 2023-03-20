---
layout: post
title:  "[JS/CodingTest] 프로그래머스 입문_연속된 수의 합 "
date:   2023-03-20
categories: JSCodingTest
---


# 프로그래머스 입문
## 연속된 수의 합
풀이시간 30분

--- 

### 문제
연속된 세 개의 정수를 더해 12가 되는 경우는 3, 4, 5입니다. 두 정수 num과 total이 주어집니다. 연속된 수 num개를 더한 값이 total이 될 때, 정수 배열을 오름차순으로 담아 return하도록 solution함수를 완성해보세요.

제한사항

1 ≤ num ≤ 100

0 ≤ total ≤ 1000

num개의 연속된 수를 더하여 total이 될 수 없는 테스트 케이스는 없습니다.

입출력 예
```
num	total	result
3	12	[3, 4, 5]
5	15	[1, 2, 3, 4, 5]
4	14	[2, 3, 4, 5]
5	5	[-1, 0, 1, 2, 3]
```

입출력 예 설명

입출력 예 #1

num = 3, total = 12인 경우 [3, 4, 5]를 return합니다.

입출력 예 #2

num = 5, total = 15인 경우 [1, 2, 3, 4, 5]를 return합니다.

입출력 예 #3

4개의 연속된 수를 더해 14가 되는 경우는 2, 3, 4, 5입니다.

입출력 예 #4

설명 생략


### 나의 풀이

```
function solution(num, total) {
    let a, b, firstElement = 0;
    var answer = [];

    a = num / 2;
    b = total / a;
    firstElement = (b-num) / 2;

    for( let i=0; i<num; i++){
        let element = Math.round(firstElement + i);
        answer.push(element);
    }


    return answer;
}
```

- 문제를 푸는데 있어서 가장 큰 아이디어는 첫 번째요소와 마지막 요소를 더한 수에 집중했다.
 
모든 수를 더하여 나온 total 값은 앞과 뒤를 더한 num/2 의 쌍을 다 더한 값과 같다.

예를 들면 1, 2, 3, 4, 5 는 총 5(num)개로 모두 더하면 15(total)이다. 여기서 배열의 맨 앞과 뒤를 연결지으면 (1+5), (2+4), 3 로 3개의 쌍을 만들 수 있고 이들은 모두 값이 6이다. (홀수의 개수면 6의 절반인 3이 하나 생긴다.)

이 6은 잠시 두고 firstElement(ㄱ)를 구하기 위해 한 가지 개념을 더 갖고 온다., [ ㄱ, ㄴ, ㄷ, ㄹ, ㅁ ] 배열은 연속된 숫자임으로 ㅁ - ㄱ = 5(num) 이다. 

즉, ㄱ + ㅁ = 6 이자, ㅁ - ㄱ = 5 임으로 ㄱ+ㄱ+5(num) = 6이다. 깔끔하게 첫번째 요소 firstElement(ㄱ) 은 ( 6 - num(5) ) / 2 와 같고

홀수일 경우 값을 반올림해주어야한다. 


- 변수 a, b, firstElement를 설정했다. 
- a는 배열의 요소들을 맨 앞 요소와 맨 뒤 요소로 묶었을 때, 몇 개의 쌍이 나오는지 담는 변수다.
- b는 맨 앞 요소와 맨 뒤 요소를 더했을 때 갖는 값을 담는 변수다.
- firstElement는 맨 처음 갖는 배열의 요소다. 
- firstElement를 변수 a와 b를 통해 구하고, for문을 통해 연속되는  배열을 완성시킨다. 

### 모든 풀이 중
```
function solution(num, total) {
    var min = Math.ceil(total/num - Math.floor(num/2));
    var max = Math.floor(total/num + Math.floor(num/2));

    return new Array(max-min+1).fill(0).map((el,i)=>{return i+min;});
}
```

- total/num을 했을 때, 나오는 수는 홀수 일 경우, 가장 중앙의 숫자이며, 짝수의 경우, 중간의 요소 2개의 합이다.

> Math.ceil : 소수점 올림
> Math.floor : 소수점 내림
> Math.round : 소수점 반올림

### 내가 놓친 부분
-

### 기억해야할 점

1. 변수 이름을 설정할 때, 누구든 알아볼 수 있도록 좋은 이름을 지어보자.
