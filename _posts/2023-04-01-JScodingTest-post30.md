---
layout: post
title:  "[JS/CodingTest] 정렬 문제 풀이 1 "
date:   2023-04-01
categories: JSCodingTest
---

# 패스트캠퍼스 온라인 강의 
## Part1.Ch03-06. 정렬 문제 풀이 1

--- 

### 세수정렬

```
// 내 코드 중 일부 (정렬함수)
data.sort((a,b)=>a-b;)
```

```
// 정답 코드 예시
arr.sort(function(a,b) { return a-b; })
```

* 나는 화살표함수로 더 간단해보이게 작성했다!
* fs모듈을 이용해 파일을 읽어와서 숫자 배열로 저장하는 코드

```
// 한줄로 되어있을 때
let arr = input[0].split(' ').map(Number);
```

```
// 여러줄로 되어있을 
let arr = [];
for (let i = 1; i <= n; i++) {
arr.push(Number(input[i]));
}
```

+) 선택정렬함수를 이용하면? (데이터가 1000개 이상일땐 효율적이다.)

![image](https://user-images.githubusercontent.com/88815795/229296974-afabf477-8995-4593-9ac7-2d110315324d.png)

### 수 정렬하기

+) 선택정렬함수를 이용하면?

![image](https://user-images.githubusercontent.com/88815795/229298108-728467e0-5969-4538-9007-bcf906fc6b7b.png)


### 수 정렬하기 2

데이터 개수가 100만개일 때에는 sort함수가 O(nlogn)으로 사용가능

### K번째 수

* 파일에서 배열 원소의 개수 n 과 k index라는 두 정보를 한 줄에서 읽어와야할 때

```
let [n , k ] = input[0].split(' ').map(Number);
```
