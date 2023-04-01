---
layout: post
title:  "[JS/CodingTest] JS 정렬 라이브러리"
date:   2023-04-01
categories: JSCodingTest
---


# 패스트캠퍼스 온라인 강의 
## Part1.Ch03-05. JS 정렬 라이브러리

--- 

### JS 정렬 라이브러리 (O(NlogN))

* 본인이 사용하는 코딩테스트에서 라이브러리를 이용할 수 있다면 사용하는 것이 간단히 작성할 수 있도록 해준다. 
* sort()함수 사용이 제한되는 곳일 수도 있다. 그렇다면 병합 정렬과 같은 알고리즘을 직접 구현해야한다. 

`arr.sort(compageFunction);`

### JS 정렬 기준 함수

* 두 개의 원소 a, b를 입력 받는다.
* 반환 값이 0보다 작으면? 우선순위 a>b 
* 반환 값이 0보다 크면? 우선순위 a<b
* 반환 값이 0이면? 순서 변경 X
                         
=> sort에서 기준 함수를 이해없이 외우고 사용했었는데 이제 알았다!!!!
  
* 유니코드 값 순서대로 정렬되기에 정렬 기준함수를 명시해야한다!

### 오름차순 예시 1
  
 ![image](https://user-images.githubusercontent.com/88815795/229294842-3863be76-5e5f-4a46-a105-7228d9862bab.png)

 ### 오름차순 예시 2

  ![image](https://user-images.githubusercontent.com/88815795/229294913-629a7481-19c3-4f04-8bce-2b607f9780f4.png)

  
 ### 오름차순 예시 3
  
 ![image](https://user-images.githubusercontent.com/88815795/229294933-b91b2fe2-a734-4347-bb52-daa7a8e618a8.png)

  ### 내림차순 예시
  
  ![image](https://user-images.githubusercontent.com/88815795/229294966-edb12c21-5890-4185-8fec-ffd6e342ff25.png)
  
  ### 문자열에 대한 오름차순
  
  * 함수를 따로 적용하지 않으면 유니코드 순으로 정렬되기 때문에 아무런 함수 없이 sort만 이용해주면 된다. 
  
  ![image](https://user-images.githubusercontent.com/88815795/229295006-c4aff18f-741b-40b6-a710-566c683f9bec.png)

  ### 문자열에 대한 내림차순
  
  ![image](https://user-images.githubusercontent.com/88815795/229295039-a9e2292d-074b-42e0-aa17-d2b248366874.png)

  ### 대소문자의 구분 없이 오름차순
  
* toUpperCase()를 이용한다. 
  
  ### ( :star: 중요 :star: ) 객체 오름차순
  
  ![image](https://user-images.githubusercontent.com/88815795/229295241-dfb44bda-288e-441e-808c-288c03700b5a.png)

=> 오호 value값에 접근하는 방법 몰라서 엄청 검색했었는데 그냥 c++에 객체접근 방법이랑 똑같구나.!
