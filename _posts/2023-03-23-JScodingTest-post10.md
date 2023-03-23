---
layout: post
title:  "[JS/CodingTest] 프로그래머스 입문_특정 문자 제거하기 "
date:   2023-03-23
categories: JSCodingTest
---

# 프로그래머스 입문
## 특정 문자 제거하기

--- 

### 문제
문자열 my_string과 문자 letter이 매개변수로 주어집니다. my_string에서 letter를 제거한 문자열을 return하도록 solution 함수를 완성해주세요.

제한사항

1 ≤ my_string의 길이 ≤ 100

letter은 길이가 1인 영문자입니다.

my_string과 letter은 알파벳 대소문자로 이루어져 있습니다.

대문자와 소문자를 구분합니다.

입출력 예
```
my_string	letter	result
"abcdef"	"f"	"abcde"
"BCBdbe"	"B"	"Cdbe"
```
입출력 예 설명

입출력 예 #1

"abcdef" 에서 "f"를 제거한 "abcde"를 return합니다.

입출력 예 #2

"BCBdbe" 에서 "B"를 모두 제거한 "Cdbe"를 return합니다.

### 나의 풀이

```
function solution(my_string, letter) {
    //정규식 안에 변수 넣기 g와 gi
    let regexAll = new RegExp(letter, "g");
    
    //replace함수로 원하는 문자열만 추출하기
    var answer = my_string.replace(regexAll, "");
    return answer;
}
```

- 정규식으로 통해 letter의 모든 것을 불러오라는 변수를 선언했다. 
- 문자열의 replace함수로 regexAll이라면 "" 빈 문자열, 공백으로 만들어라 하여 조건에 맞는 문자열을 answer에 담았다.

> 변수를 포함한 정규식 
* 일반적으로 정규식은 //(시작과 끝을 알리는 표식)과 g(전부 검사) gi(전부 검사하고 대소문자 구분없이)라는 추가 조건을 넣는다. 
* 변수를 포함한 정규식을 만들기 위해서는 생성자 함수를 이용해야한다. 


### 모든 풀이 중

```
unction solution(my_string, letter) {
    const answer = my_string.split(letter).join('')
    return answer;
}
```

> 문자열의 split함수로 letter을 기준으로 문자열을 자른다.
> 배열의 join함수로 ''배열의 원소들을 모두 띄어쓰기나 추가 요소 없이 붙여준다. 


### 기억해야할 점

1. 변수를 포함한 정규식 만들기
2. split 함수
3. join 함수
