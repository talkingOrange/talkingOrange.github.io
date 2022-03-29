---
layout: post
title:  "[스터디/알고리즘] DFS 백준 24480번"
date:   2022-03-28
categories: studyAlgorithm
---

# 백준 24480번
- DFS 코드 짜기

---

### 문제

오늘도 서준이는 깊이 우선 탐색(DFS) 수업 조교를 하고 있다. 아빠가 수업한 내용을 학생들이 잘 이해했는지 문제를 통해서 확인해보자.


N개의 정점과 M개의 간선으로 구성된 무방향 그래프(undirected graph)가 주어진다. 정점 번호는 1번부터 N번이고 모든 간선의 가중치는 1이다. 


***정점 R에서 시작하여 깊이 우선 탐색으로 노드를 방문할 경우 노드의 방문 순서를 출력하자.***


깊이 우선 탐색 의사 코드는 다음과 같다. 인접 정점은 **내림차순**으로 방문한다.

< 의사코드 >

```c++
dfs(V, E, R) {  # V : 정점 집합, E : 간선 집합, R : 시작 정점
    visited[R] <- YES;  # 시작 정점 R을 방문 했다고 표시한다.
    for each x ∈ E(R)  # E(R) : 정점 R의 인접 정점 집합.(정점 번호를 오름차순으로 방문한다)
        if (visited[x] = NO) then dfs(V, E, x);
}
```


---


```c++
#include <iostream>
#include <algorithm>
#include <vector>
#include <array>

using namespace std;

int n, m, r, u, v, ans;
// n = 정점의 개수, m = 간선의 개수
// r = 시작 정점, x, y = 연결된 두 정점
vector<int> adj[100001];
int visit[100001];
int vn[100001];

void dfs(int c) {
    // c = 현재 방문 중인 정점 번호
    visit[c] = 1; // 검색하는 정점에 방문 저장
    vn[c] = ++ans; // 현재 방문 순서 = 전체 방문 순서 + 1
    for (int i = 0; i < adj[c].size(); i++) { //입력된 정점에 연결되어 있는 다른 정점을 검색하는 for문
        int next = adj[c][i];
        if (visit[next] == 0) { //방문하지 않았다면 재귀함수로 방문
            dfs(next);
        }
    }
}

//내림차순을 위한 함수
bool cmp(const int& a, const int& b) {
    return a > b;
}


void solution() {
    cin >> n >> m >> r; //정점의 수, 간선의 수, 처음 검색할 수 입력
    
    //간선의 정보 입력
    for (int i = 0; i < m; i++) { 
        cin >> u >> v;
        adj[u].push_back(v);
        adj[v].push_back(u);
    }

//간선 내림차순으로 정렬 - 방문 정점이 여러개일 때, 정점 번호가 작은 것부터 방문하라는 뜻.
    for (int i = 0; i <= n; i++) {
        sort(adj[i].begin(), adj[i].end(), cmp);
    }

//dfs 실행 및 답출력
    dfs(r);

    for (int i = 1; i <= n; i++) {
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

4

3

2

0

