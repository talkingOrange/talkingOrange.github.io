---
layout: post
title:  "[스터디/알고리즘] BFS 백준 24444번"
date:   2022-03-29
categories: studyAlgorithm
---

# 백준 24444번
- BFS 코드 짜기

---

### 문제

오늘도 서준이는 너비 우선 탐색(BFS) 수업 조교를 하고 있다. 아빠가 수업한 내용을 학생들이 잘 이해했는지 문제를 통해서 확인해보자.

N개의 정점과 M개의 간선으로 구성된 무방향 그래프(undirected graph)가 주어진다. 

정점 번호는 1번부터 N번이고 모든 간선의 가중치는 1이다. **정점 R에서 시작하여 너비 우선 탐색으로 노드를 방문할 경우 노드의 방문 순서를 출력하자.**

너비 우선 탐색 의사 코드는 다음과 같다. 인접 정점은 **오름차순**으로 방문한다.


> 의사코드

```c++
bfs(V, E, R) {  # V : 정점 집합, E : 간선 집합, R : 시작 정점
    for each v ∈ V - {R}
        visited[v] <- NO;
    visited[R] <- YES;  # 시작 정점 R을 방문 했다고 표시한다.
    enqueue(Q, R);  # 큐 맨 뒤에 시작 정점 R을 추가한다.
    while (Q ≠ ∅) {
        u <- dequeue(Q);  # 큐 맨 앞쪽의 요소를 삭제한다.
        for each v ∈ E(u)  # E(u) : 정점 u의 인접 정점 집합.(정점 번호를 오름차순으로 방문한다)
            if (visited[v] = NO) then {
                visited[v] <- YES;  # 정점 v를 방문 했다고 표시한다.
                enqueue(Q, v);  # 큐 맨 뒤에 정점 v를 추가한다.
            }
    }
}
```


---

> 코드 풀이

```c++
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>
using namespace std;

vector<int> adj[200001]; // 간선을 저장할 vector 자료 구조
vector<bool> visit;  // bfs일 경우 방문했는지에 대한 정보
queue<int> q; // bfs일 경우 이용할 queue 자료 구조
int vn[100001];
int n, m, v, ans;  // 정점의 수, 간선의 수, 처음 검색할 수 

void bfs(int v) {

	visit[v] = true; // 검색할 정점에 대하여 방문했다고 저장함
	q.push(v); // 해당 정점을 큐에 넣음
	while (!q.empty()) { // 큐가 비어있을 때까지 수행함
		int f = q.front(); // 큐에 쌓여있는 첫 정점을 반환
		q.pop(); // 큐에 쌓여있는 첫 정점을 큐에서 빼냄
		vn[f] = ++ans; // 방문 순서를 배열에 저장해 둠._출력을 위해서
		for (int i = 0; i < adj[f].size(); i++) { // 빼낸 정점에 연결되어 있는 정점들 검색
			if (visit[adj[f][i]] == false) { // 방문되지 않았다면 방문함
				q.push(adj[f][i]); // 큐에 넣음
				visit[adj[f][i]] = true; // 방문했다고 저장함
			}
		}
	}
}

void solution() {
	cin >> n >> m >> v; // 정점의 수, 간선의 수, 처음 검색할 수 입력 받음
	for (int i = 0; i <= n; i++) { // 초기화
		visit.push_back(false);
	}

	// 간선 정보 입력
	for (int i = 0; i < m; i++) {
		int x, y;
		cin >> x >> y;
		adj[x].push_back(y);
		adj[y].push_back(x);
	}

	// 각 간선 정보에 대하여 오름 차순으로 정렬
	// 방문할 수 있는 정점이 여러 개인 경우, 정점 번호가 작은 것을 먼저 방문한다는 뜻.
	for (int i = 0; i <= n; i++) {
		sort(adj[i].begin(), adj[i].end());
	}

//bfs 실행 및 답 출력
	bfs(v); 

	for (int i = 1; i <= n; i++)
	{
		cout << vn[i] << "\n";
	}
}

int main() {
	solution();

	return 0;
}
```

---

> 입력

5 5 1

1 4

1 2

2 3

2 4

3 4


>출력

1

2

4

3

0


