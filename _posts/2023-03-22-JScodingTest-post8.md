---
layout: post
title:  "[JS/CodingTest] 프로그래머스 입문_가장 큰 수 찾기"
date:   2023-03-22
categories: JSCodingTest
---


# 프로그래머스 입문
## 가장 큰 수 찾기

--- 

### 문제
정수 배열 array가 매개변수로 주어질 때, 가장 큰 수와 그 수의 인덱스를 담은 배열을 return 하도록 solution 함수를 완성해보세요.

제한사항

1 ≤ array의 길이 ≤ 100

0 ≤ array 원소 ≤ 1,000

array에 중복된 숫자는 없습니다.

입출력 예
```
array	result
[1, 8, 3]	[8, 1]
[9, 10, 11, 8]	[11, 2]
```
입출력 예 설명

입출력 예 #1

1, 8, 3 중 가장 큰 수는 8이고 인덱스 1에 있습니다.

입출력 예 #2

9, 10, 11, 8 중 가장 큰 수는 11이고 인덱스 2에 있습니다.

### 나의 풀이

```
function solution(array) {
    var answer = [];
    let sortArray =[];

    //배열의 복사
    for(let element of array){
        sortArray.push(element);
    }

    //복사된 배열 sort로 내림차순 정렬 
    sortArray.sort((a,b)=> b-a);

    //내림차순된 배열로 가장 큰 수 얻음
    answer.push(sortArray[0]);

    //기존 배열에서 가장 큰 수가 어디에 담겨있는 지 for문으로 확인
    for(let i=0; i < array.length; i++){
        if(sortArray[0] === array[i]){
            answer.push(i)
        }
    }

    return answer;
}
```

- 큰 수를 찾기 위해서 배열 하나를 복사해서 sort로 내림차순 정렬함. 
- for문을 통해 그 큰 수가 원 배열에 어느 index를 가지고 있는지 찾음. 

### 모든 풀이 중
```
function solution(array) {
    let max = Math.max(...array);
    return [max, array.indexOf(max)];
}
```

> Math.max() 함수는 가장 큰 수를 반환해준다. 
> indexOf() 함수는 배열 검색하고자하는 값이 배열의 element에 존재하는지에 대한 index를 알려준다. 

(인턴했던 회사에서 배열에 값이 있는지 판별할 때, .indexOf() > -1 를 많이 사용했었다.)

### 내가 놓친 부분

max 값을 구해주는 Math의 함수가 있다는 것과 indexOf를 이용하면 굳이 불필요한 반복문을 돌지 않아도 된다. 

### 기억해야할 점

1. Math.max()
2. indexOf()
