---
layout: post
title:  "[스터디/알고리즘] DFS/BFS 백준 1260번"
date:   2022-03-29
categories: studyAlgorithm
---

# 백준 1260번
- DFS/BFS 코드 짜기

---

### 문제

그래프를 DFS로 탐색한 결과와 BFS로 **탐색한 결과를 출력하는 프로그램**을 작성하시오. 

단, 방문할 수 있는 정점이 여러 개인 경우에는 정점 번호가 작은 것을 먼저 방문하고, 더 이상 방문할 수 있는 점이 없는 경우 종료한다. 

정점 번호는 1번부터 N번까지이다.

---

> 코드 풀이

```c++
#include <iostream>
#include <queue>
using namespace std;

int n, m, v;
const int MAX=1000+1;
int map[MAX][MAX];
bool visited[MAX];
queue<int> q;

//초기화 함수
void reset(){
    for(int i=0;i<MAX;i++){
        visited[i]=0;
    }
}

void dfs(int v){
    visited[v]=1; //검색하는 정점 방문 저장
    cout << v << " "; // 검색하는 것은 모두 출력해주어야 하므로.
    for(int i=1;i<=n;i++){ //연결 노드들 검색
        if(map[v][i]==1 && !visited[i]){ //방문하지 않은 것이 있을 경우 재귀함수로 방문
            dfs(i);
        }
    }
}

void bfs(int v){
    q.push(v); // 정점 큐에 넣기
    visited[v]=1; //검색하는 정점 방문 저장
    cout << v << " "; //검색하는 것은 모두 출력해주어야 하므로.
    
    while(!q.empty()){ //큐가 비어있을 때까지 수행하기.
        v=q.front(); //큐에서 처음꺼 v에 넣음.
        q.pop(); // 큐에서 빼냄 
        
        for(int i=1;i<=n;i++){ //연결 노드들 검색 
            if(map[v][i]==1 && !visited[i]){ //방문하지 않았다면 방문
                q.push(i); //반복
                visited[i]=1; 
                cout << i << " ";
            }
        }         
    }
}

int main(){
    cin >> n >> m >> v; //정점의 수, 간선의 수, 처음 검색할 수 입력
    for(int i=0;i<m;i++){ //간선 정보 입력
        int a,b;
        cin >> a >> b;
        map[a][b]=1;
        map[b][a]=1;
    }
    
    reset(); //초기화
    dfs(v); 
    
    cout << '\n';
    
    reset(); //
    bfs(v);
       
    return 0;
}

```

---

> 입력

4 5 1

1 2

1 3

1 4

2 4

3 4


>출력

1 2 4 3

1 2 3 4


