---
layout: post
title:  "[스터디/알고리즘] 이것이 코딩테스트다 CH5.DFS/BFS(1)"
date:   2022-03-19
categories: studyAlgorithm
---

# CH5-1. DFS/BFS를 학습하기 위한 사전 학습

---

대외 동아리에 가입하면서 동아리 내의 스터디그룹에도 가입하게 되었다. 
막무가내식 코딩을 많이 하고 있기도 하고 이번 학기에 알고리즘 수업을 듣기 때문에 스터디를 가입하면 더 열심히 공부할 수 있지 않을까하는 생각으로 시작했다.
이번 주에는 내가 발표를 맡아, 발표를 준비하는 겸 블로그에 정리글을 올려보고자 한다.

+) [이코테 교재 깃허브](https://github.com/ndb796/python-for-coding-test)

---

### 탐색이란?
많은 양의 데이터 중에서 원하는 데이터를 찾는 과정.
- 대표적인 탐색 알고리즘 : DFS/BFS
- DFS/BFS를 학습하기 위한 사전 학습 개념, *스택과 큐 그리고 재귀함수*

---

### 스택
- 후입선출 구조(=선입후출 구조)
- 박스 쌓기와 치우기
- ![선입후출 구조 이미지](/public/img/studyAlgorithm/stack.png)

-stack 예제
```c++
#include <iostream>
#include <stack>
using namespace std;

stack<int> s;

int main(void) {
    // 삽입(5) - 삽입(2) - 삽입(3) - 삽입(7) - 삭제() - 삽입(1) - 삽입(4) - 삭제()
    s.push(5);
    s.push(2);
    s.push(3);
    s.push(7);
    s.pop();
    s.push(1);
    s.push(4);
    s.pop();
    // 스택의 최상단 원소부터 출력
    while (!s.empty()) {
        cout << s.top() << ' ';
        s.pop();
    }
}
```

<details>
<summary>결과</summary>
<div markdown="1">       

1 3 2 5

</div>
</details>

- C++에서 stack 헤더파일을 이용하면 되고, push와 pop이 기본적으로 삽입과 삭제를 의미하는 함수다. 

---

### 큐
- 선입선출 구조
- 줄 서기
- ![선입선출 구조 이미지](/public/img/studyAlgorithm/queue.png)

-queue 예제
```c++
#include <iostream>
#include <queue>
using namespace std;

queue<int> q;

int main(void) {
    // 삽입(5) - 삽입(2) - 삽입(3) - 삽입(7) - 삭제() - 삽입(1) - 삽입(4) - 삭제()
    q.push(5);
    q.push(2);
    q.push(3);
    q.push(7);
    q.pop();
    q.push(1);
    q.push(4);
    q.pop();
    // 먼저 들어온 원소부터 추출
    while (!q.empty()) {
        cout << q.front() << ' ';
        q.pop();
    }
}
```
<details>
<summary>결과</summary>
<div markdown="1">       

3 7 1 4

</div>
</details>


- C++에서 queue 헤더파일을 이용하면 된다.


---

### 재귀함수
- 자기 자신을 다시 호출하는 함수
- cf) Fractal 구조
- <span style="color:red">재귀함수는 종료조건을 꼭 명시해야한다. </span>
    + 재귀함수는 내부적으로 **스택 자료구조와 동일**하다. 

-재귀함수 예제, factoria(팩토리얼) 수학문제
```c++
#include <iostream>
using namespace std;

// 반복적으로 구현한 n!
int factorialIterative(int n) {
    int result = 1;
    // 1부터 n까지의 수를 차례대로 곱하기
    for (int i = 1; i <= n; i++) {
        result *= i;
    }
    return result;
}

// 재귀적으로 구현한 n!
int factorialRecursive(int n) {
    // n이 1 이하인 경우 1을 반환
    if (n <= 1) return 1;
    // n! = n * (n - 1)!를 그대로 코드로 작성하기
    return n * factorialRecursive(n - 1);
}

int main(void) {
    // 각각의 방식으로 구현한 n! 출력(n = 5)
    cout << "반복적으로 구현:" << factorialIterative(5) << '\n';
    cout << "재귀적으로 구현:" << factorialRecursive(5) << '\n';
}
```
<details>
<summary>결과</summary>
<div markdown="1">       
반복적으로 구현:120
재귀적으로 구현:120
</div>
</details>


- 재귀 함수 장점
    + 코드가 더 간결
- 재귀 함수 주의사항
    + if문을 이용하여 꼭 종료 조건을 구현해주어야 한다. 








> 이미지출처:https://velog.io/@dumok_/DFSBFS-%EA%B0%9C%EB%85%90


