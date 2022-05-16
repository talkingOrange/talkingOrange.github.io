---
layout: post
title:  "[스터디/알고리즘] 이진탐색 백준 6236번"
date:   2022-05-16
categories: studyAlgorithm
---

# 백준 6236번
- https://www.acmicpc.net/problem/6236

---

### 문제

현우는 용돈을 효율적으로 활용하기 위해 계획을 짜기로 하였다. 

현우는 앞으로 N일 동안 자신이 사용할 금액을 계산하였고, 돈을 펑펑 쓰지 않기 위해 정확히 M번만 통장에서 돈을 빼서 쓰기로 하였다. 

현우는 통장에서 K원을 인출하며, 통장에서 뺀 돈으로 하루를 보낼 수 있으면 그대로 사용하고, 모자라게 되면 남은 금액은 통장에 집어넣고 다시 K원을 인출한다. 

다만 현우는 M이라는 숫자를 좋아하기 때문에, 정확히 M번을 맞추기 위해서 남은 금액이 그날 사용할 금액보다 많더라도 남은 금액은 통장에 집어넣고 다시 K원을 인출할 수 있다. 

현우는 돈을 아끼기 위해 인출 금액 K를 최소화하기로 하였다. 현우가 필요한 최소 금액 K를 계산하는 프로그램을 작성하시오.

---

> 코드 풀이

```c++
#include<iostream>
#include<algorithm>
using namespace std;
 
 
int main() {
    int N, M, min = 0;
    cin >> N >> M;
    int arr[100001];
    int hi = 0;
 
    for (int i = 0; i < N; i++) {
        cin >> arr[i];
        min = max(min, arr[i]);
        hi = hi + arr[i];
    }
 
    int mid = 0;
 
    //이진 탐색
    while (lo <= hi) {
        mid = (lo + hi) / 2;
        int cnt = 1;
        int money = mid;
        for (int i = 0; i < N; i++) {
            money = money - arr[i];
            if (money <= 0) {
                money = mid - arr[i];
                cnt++;
            }
        }
 
        if (cnt > M) lo = mid + 1;
        else
            hi = mid - 1;
 
    }
 
    cout << mid;
 
}


```

---

> 입력

https://blog.potados.com/ps/boj-6236-money/

참고해서 해설쓰기


