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
#include <iostream>
#include <vector>
using namespace std;

vector<int> dayMoney;
int N, M, sum;

bool Solution(int money)
{
	int temp = money, withdraw = 1;
	for (int i = 0; i < N; i++)
	{
		if (dayMoney[i] > money)
			return false;
		if (temp - dayMoney[i] < 0)
		{
			temp = money;
			withdraw++;
		}
		temp -= dayMoney[i];
	}
	return M >= withdraw;
}
int main(void)
{
	cin >> N >> M;
	for (int i = 0; i < N; i++)
	{
		int n;
		cin >> n;
		dayMoney.push_back(n);
		sum += n;
	}

	// binary_search //
	int start = 1, end = sum; // sum은 M이 1인 모든 금액을 더한 값
	int result;
	while (start <= end)
	{
		int mid = (start + end) / 2;
		if (Solution(mid))	// 인출횟수가 M보다 작거나 같음 -> 인출금을 줄여보자
		{
			result = mid;
			end = mid -1;
		}
		else
			start = mid + 1;
	}
	cout << result << endl;
	return 0;
}

```

---

> 설명

- 현우가 인출하는 금액 : k

현우가 하루에 돈을 1 <= 금액 <= 10,000원 만큼 통장에서 빼서 쓴다. 통장에서 인출하는 금액은 K이다. (매번 동일)

- N일, M번 출금.

현우가 1 <= N <= 100,000일 동안 사용할 돈이 미리 주어진다. 

M번 출금을 하여 먹고 살 수 있도록 하는 가장 작은 K를 구해야 하는 것이다.

- 이진탐색을 이용한다.

우리는 k를 찾아야하고, 출금횟수인 M은 계속해서 오른쪽을 탐구할 것인지 오른쪽을 탐구할 것인지 알려주는 mid이다.  

인출 홧수가 M보다 많응면 mid값을 증가시킨다.

