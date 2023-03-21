---
layout: post
title:  "[JS/CodingTest] 프로그래머스 입문_분수의 덧셈 "
date:   2023-03-21
categories: JSCodingTest
---


# 프로그래머스 입문
## 분수의 덧셈

--- 

### 문제
첫 번째 분수의 분자와 분모를 뜻하는 numer1, denom1, 두 번째 분수의 분자와 분모를 뜻하는 numer2, denom2가 매개변수로 주어집니다. 두 분수를 더한 값을 기약 분수로 나타냈을 때 분자와 분모를 순서대로 담은 배열을 return 하도록 solution 함수를 완성해보세요.

제한사항

0 <numer1, denom1, numer2, denom2 < 1,000

입출력 예

```
numer1	denom1	numer2	denom2	result
1	2	3	4	[5, 4]
9	2	1	3	[29, 6]
```

입출력 예 설명

입출력 예 #1

1 / 2 + 3 / 4 = 5 / 4입니다. 따라서 [5, 4]를 return 합니다.

입출력 예 #2

9 / 2 + 1 / 3 = 29 / 6입니다. 따라서 [29, 6]을 return 합니다.

### 나의 풀이

```

function solution(numer1, denom1, numer2, denom2) {

    //분모, 분자 구하기
    const denom = denom1 * denom2; 
    const numer = denom2 * numer1 + denom1 * numer2;

    //분자와 분모 중에 작은 값 구하기
    let sortNum = [denom, numer];
    sortNum.sort(function(a,b){return a-b});

    //기약분수로 만들기 위한 for문
    let maxMultiply = 1;

    for(let i = 1 ; i <= sortNum[0] ; i ++) {
        if(denom%i === 0 && numer%i === 0) {
            maxMultiply = i
        }
    }

    //결과
    var answer = [numer/maxMultiply, denom/maxMultiply];

    return answer;
}

```

- 분모와 분자를 구한다.
- 기약분수를 만든다. 이때, sort()함수를 이용해서 작은 값을 찾았는데 for문을 최대한 적게 돌리기 위해 이용한 것이다. sort()로 오름차순을 이용해보고 싶었어서 사용한 것도 있다.

### 모든 풀이 중
```
function fnGCD(a, b){
    return (a%b)? fnGCD(b, a%b) : b;
}

function solution(denum1, num1, denum2, num2) {
    let denum = denum1*num2 + denum2*num1;
    let num = num1 * num2;
    let gcd = fnGCD(denum, num); //최대공약수

    return [denum/gcd, num/gcd];
}

```

> 함수 fnGCD를 이용해 최대공약수를 구했는데, 나눗셈을 이용하여 최대공약수를 구하는 방법을 코드화시켰다. 참 똑똑한 코드 같다.


### 기억해야할 점

1. 최대공약수를 구하는 함수를 눈여겨 보자!
