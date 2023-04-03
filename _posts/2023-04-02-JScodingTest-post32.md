---
layout: post
title:  "[JS/CodingTest] 정렬 문제 풀이 3 (Map 객체)"
date:   2023-04-02
categories: JSCodingTest
---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch03-07. 정렬 문제 풀이 3

--- 

### 좌표 압축

```
// 내가 푼 해결방법
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');

let num = Number(input[0]);
let data = input[1].split(' ').map(Number);

// sortData로 중복 제거한 배열 새로 생성
let sortData = [...new Set(data)];

//sortData 정렬
sortData.sort((a,b)=>a-b);

for(let i=0; i<num; i++){
    for(let j=0; j<sortData.length; j++){
        if(data[i] == sortData[j]){
            data[i] = j;
            break;
        }
    }
}

let answer = "";

for(let i=0; i<data.length; i++){
    answer += data[i]+"\n";
}

console.log(answer);
```

* 시간초과가 발생한다.
* 아이디어 : 중복없는 배열로 바꾸어 sort한다. 중첩 for문을 이용해 기존 배열과 중복없이 sort된 배열을 비교하며 기존 배열의 값을 sort 배열의 인덱스로 바꾸어준다. 
* 중첩 for문으로 인해 O(N^2)이 되어 시간초과가 발생한다. 
* 문제의 조건이 `1 ≤ N ≤ 1,000,000` 이기에 O(NlogN)이어야 한다.

```
//답안
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let arr = input[1].split(' ').map(Number);

// 집합(set)으로 변경해 중복 값을 없앤 뒤에 다시 배열로 변환
let uniqueArray = [...new Set(arr)];
uniqueArray.sort((a, b) => a - b); // 오름차순 정렬 수행

// 0부터 차례대로 매핑(mapping) 수행
let myMap = new Map();
for (let i = 0; i < uniqueArray.length; i++) {
myMap.set(uniqueArray[i], i);
}

// mapping값 출력
answer = "";
for (x of arr) answer += myMap.get(x) + " ";
console.log(answer);
```

* 아이디어 : 배열을 중복 제거하고 정렬한다. `dictionary`로 매핑하고 `매핑값을 출력`한다. 

##### Map 객체
: 키와 값을 한 쌍으로 이룬 컬렉션

`const map = new Map();`

* Map 값 추가 `map.set(키,값)`
* Map 값 삭제 `map.delete(키)`
* Map 값 출력 `map.get()`
* Map 반복

```
// map 선언
const map = new Map([['key1', 'value1'], ['key2', 'value2']]);

map.forEach((val, key) => {
  console.log(val + "," + key);
});

// 결과입니다
// value1,key1
// value2,key2


// key값 가져오기
for (let key of map.keys()){
    console.log("key : " + key);
}
// 결과입니다
// key : key1
// key : key2


// value 값 가져오기
for (const value of map.values()) {
    console.log("value : " + value);
}
// 결과입니다
// value : value1
// value : value2


// entries 반복문
for (let[key, value] of map.entries()) {
    console.log(key + " : " +value);
}
// 결과입니다
// key1 : value1
// key2 : value2

```

### 나이순 정렬

```
//내가 푼 풀이
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');

let num= Number(input[0]);
let data = [];
for(let i = 1 ; i <=num ; i++){
    let age = Number(input[i].split(' ')[0]);
    let name = input[i].split(' ')[1];
    data.push([age, name]);
}

data.sort((a,b)=>a[0]-b[0]);

let answer="";
for(let element of data){
    answer += element[0] + " " + element[1]+ "\n";
}
console.log(answer)
```

=> 이제 별 2개도 풀다니!!

### 소트인사이드

```
//내가 푼 풀이
let fs=require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');

let data = input[0].split('').map(Number);

data.sort((a,b)=>b-a);

let answer ='';

for(let element of data){
    answer += element;
}

console.log(answer);
```

```
//답안 
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n
');
let n = input[0]; // 수(N) 입력받기
// 0부터 9까지 각 숫자(digit)의 출현 빈도를 담을 배열(array) 선언
let cnt = Array(10).fill(0); // 초기 빈도 값은 0으로 초기화
for (let x of n) { // 한 자리씩 숫자(digit)를 확인하며
cnt[Number(x)]++;
}
let answer = 
"";
// 9부터 0까지 하나씩 숫자(digit)를 확인하며
for (let i = 9; i >= 0; i--) {
// 출현 빈도만큼 출력하기
for (let j = 0; j < cnt[i]; j++) answer += i + "";
}
console.log(answer)
```

* sort 말고 0~9까지의 숫자의 빈도수를 검사하여 빈도수만큼 출력해주었다.
