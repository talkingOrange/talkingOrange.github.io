---
layout: post
title:  "[JS/CodingTest] 그리디 문제 풀이"
date:   2023-05-14
categories: JSCodingTest
---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch04-02. 그리디 문제 풀이

--- 

### 동전 0

[동전 0](https://www.acmicpc.net/problem/11047) 
 
거스름돈이 배수관계일 때, 화폐단위가 큰 것부터 돈을 주면 가장 최소의 동전(or 지폐) 개수로 나눠줄 수 있다.


* 내 풀이

```
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

//동전 개수
let n = Number(input[0].split(' ')[0]); 
//total 금액
let k = Number(input[0].split(' ')[1]);

//입력한 동전 값들
let arr = [];
for (let i = 1; i <= n; i++) arr.push(Number(input[i]));

//결과 
let cnt = 0;

// 배열을 돌면서 total(K) 금액보다 크면, 동전의 크기를 줄여서 반복문을 다시 돈다.
// total보다 작거나 같다면 total금액을 빼고 결과 값이자 동전의 개수를 의미하는 cnt를 하나 증가시킨다.
for(let i = n - 1; i >= 0;){
    if(arr[i] > k){
        i--;
        continue;
    }else{
        k -= arr[i]; 
        cnt++;
         }
}

console.log(cnt);

```

* 강의에서 안내하는 코드

```
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n
');
let n = Number(input[0].split(' ')[0]); // 동전의 개수
let k = Number(input[0].split(' ')[1]); // 만들어야 할 금액
let arr = [];
// 전체 동전(화폐 단위) 데이터 입력
for (let i = 1; i <= n; i++) arr.push(Number(input[i]));
let cnt = 0;
// 가치가 큰 동전부터 확인
for (let i = n - 1; i >= 0; i--) {
cnt += parseInt(k / arr[i]); // 해당 동전을 몇 개 사용해야 하는지
k %= arr[i]; // 해당 동전으로 모두 거슬러 준 뒤 남은 금액
}
console.log(cnt)
```

[ 배울점 ]

1. for문 안에서 두 문장으로 간단하게 구현하였다.

[ 내가 더 나은 방식이라고 생각하는 점 ]

나는 필요없는 동전일 경우, 반복문을 바로 빠져나왔으나, 여기서는 값을 0 처리해서 반복문 과정을 
돌게하였다.

그런데, 내 코드를 더 나아지게 하기 위해서는 강의 코드처럼 parseInt(k/arr[i]) 값을 cnt에 바로 더해주었어햐했다.
내 코드는 하나씩 cnt를 추가하면서 불필요한 for문을 더 돌게하였고, 그 결과 소요시간이 더 걸렸을 것이다.

즉, 필요없는 동전일 경우, 반복문을 바로 빠져나오도록 처리하되 나누기와 나머지 연산자를 통해
불필요하게 반복되는 for문을 줄여보자!


### [ATM](https://www.acmicpc.net/problem/11399)

* 내 풀이 

```
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]); 
let arr = input[1].split(' ').map(Number); 

arr.sort((a, b) => a - b);
let answer = 0
let i = 0;

for(i; i<arr.length;){
    answer += arr[i];
    
    if(arr.length === i+1 ){
        arr.pop();
        i=0;
        continue;
    }
    i++;
}

console.log(answer);
```

1. 오름차순으로 정리한다.
2. arr[0] , arr[0]+arr[1], arr[0]+arr[1]+...arr[arr.length -1] 한 것을 모두 더한다.
- 이 부분을 구현하기 위해서, 나는 정렬된 모든 배열 요소들을 더한다.
- 마지막 요소까지 더했을 때, 마지막 요소를 pop()을 통해 없애고, i를 0으로 초기화시킨다.
- arr.length가 0이 될 때까지 이 과정을 반복한다.



* 강의에서 소개한 코드


```
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n
');
let n = Number(input[0]); // 사람의 수
let arr = input[1].split(' ').map(Number); // 모든 처리 시간 입력받기
// 오름차순 정렬
arr.sort((a, b) => a - b);
let answer = 0;
let summary = 0;
for (let i = 0; i < n; i++) {
summary += arr[i]; // i번째 사람이 기다린 총 시간
answer += summary; // 지금까지 소요된 총 시간
}
console.log(answer)
```
1. 오름차순으로 정리한다.
2. arr[0] 을 최종 값 변수에 저장한다.
3. arr[0]+arr[1] 을 하고 최종 값 변수에 저장한다.
4. arr[0]+arr[1]+arr[2] 을 하고 최종 값 변수에 저장한다.

이처럼 변수를 2개 두어 차례로 더함과 동시에 전체 변수에 값을 저장한다. 


* 비교

![image](https://github.com/talkingOrange/talkingOrange.github.io/assets/88815795/a8bc2e32-9d1e-423d-9c33-ca479a2b0712)

코드 길이는 내가 더 짧지만, 강의에서 제공하는 코드의 메모리와 시간이 훨씬 짧은 것을 알 수 있다. 

나의 단점은 너무 어렵게 생각한다는 것이다. 

문제 요구사항과 해결방법에 대한 아이디어는 틀리지 않았지만, 이를 구현하는 과정에서 비효율적인 코드를 구현한다는 것이다.

많은 문제를 푼다면 이 문제를 해결할 수 있을 것이라고 생각한다. 파이팅!

