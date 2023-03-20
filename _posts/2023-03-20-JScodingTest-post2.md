---
layout: post
title:  "[JS/CodingTest] 프로그래머스 입문_다음에 올 숫자 "
date:   2023-03-20
categories: JSCodingTest
---


# 프로그래머스 입문
## 다음에 올 숫자

--- 

### 문제
등차수열 혹은 등비수열 common이 매개변수로 주어질 때, 마지막 원소 다음으로 올 숫자를 return 하도록 solution 함수를 완성해보세요.

제한사항

2 < common의 길이 < 1,000

-1,000 < common의 원소 < 2,000

common의 원소는 모두 정수입니다.

등차수열 혹은 등비수열이 아닌 경우는 없습니다.

등비수열인 경우 공비는 0이 아닌 정수입니다.

입출력 예
```
common	result
[1, 2, 3, 4]	5
[2, 4, 8]	16
```

입출력 예 설명

입출력 예 #1

[1, 2, 3, 4]는 공차가 1인 등차수열이므로 다음에 올 수는 5이다.

입출력 예 #2

[2, 4, 8]은 공비가 2인 등비수열이므로 다음에 올 수는 16이다.


### 나의 풀이

```
function solution(common) {
    let answer = 0;

    const a = common[1] / common[0];
    const b = common[1] - common[0];

    for ( let i = 1; i < common.length; i++){
        if(common[i+1] / common[i] === a){
            answer = common[common.length -1] * a;
        }else if(common[i+1] - common[i]===b){
            answer = common[common.length -1] + b;
        }
    }

    return answer;
}
```

- 상수 a와 b를 설정했다. 등비수열이거나 등차수열일 경우, 어떤 수가 곱해지거나 더해지는지 담았다.
- 배열 안에있는 모든 수를 나눴을 때, 모두 a 값이 나오면 등비수열이다.
- 배열 안에있는 모든 수를 곱했을 때, 모두 b 값이 나오면 등차수열이다.

### 모든 풀이 중
```
function solution(common) {
    if ((common[1]-common[0])==(common[2]-common[1])){
        return common.pop() + common[1] - common[0];
    }
    else{
        return common.pop()*common[1]/common[0];
    }
}
```

> pop함수는 배열의 가장 상단의 요소를 제거한다. 단, 그 요소를 return해준다. 

### 내가 놓친 부분

" 배열이 모두 등차수열이거나 등비수열이다 " 는 것을 놓쳤다.

배열이 등차수열이거나 등비수열이라는 것은 배열을 무조건 모두 돌 필요없이, arr[0], arr[1], arr[2] 만 비교해도 된다는 의미이다.

즉, for문이 필요없었다. 

문제를 잘 읽자! 

### 기억해야할 점

1. 문제를 잘 읽자!
2. 배열의 pop
