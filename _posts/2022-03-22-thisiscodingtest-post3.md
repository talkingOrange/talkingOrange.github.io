---
layout: post
title:  "[스터디/알고리즘] 이것이 코딩테스트다 CH5.DFS/BFS(3)"
date:   2022-03-22
categories: studyAlgorithm
---

# CH5-3. 탐색 알고리즘, DFS/BFS의 예제1/2

---

### [실전문제] 음료수 얼려 먹기
 ![음료수 얼려 먹기 문제 이미지](/public/img/studyAlgorithm/DFS_Q1.png)
 ![음료수 얼려 먹기 문제 이미지](/public/img/studyAlgorithm/DFS_Q1(2).png)

- DFS로 해결하는 문제
- 방문처리가 이루어 지는 것의 개수만 세면 됨.(0인 노드 중)



```c++
#include<iostream>
using namespace std;

int n,m;
int graph[1000][1000];
	
// DFS로 특정 노드를 방문하고 연결된 모든 노드들도 방문
bool dfs(int x, int y){
	// 주어진 범위를 벗어나는 경우에는 즉시 종료
	if(x < 0 || x > n - 1 || y < 0 || y > m - 1){
		return false;
	}
	
	// 현재 노드를 아직 방문하지 않았다면
	if(graph[x][y] == 0){
		// 구멍이 뚫려 있는 부분 방문 처리  
		graph[x][y] = 1;
		
		// 상, 하, 좌, 우의 위치들도 모두 재귀적으로 호출  
		dfs(x - 1, y); 
		dfs(x + 1, y); 
		dfs(x, y - 1); 
		dfs(x, y + 1); 
		
		return true; 
	}
	
	return false; // 칸막이가 존재하는 부분  
}

int main(void){
	
	int result = 0;
	// N, M을 공백을 기준으로 구분하여 입력 받기
	cin >> n >> m;	
	
	// 2차원 리스트의 맵 정보 입력 받기
	for(int i = 0; i < n; i++){
		for(int j = 0; j < m; j++){
			scanf("%1d", &graph[i][j]);
		}
	}
	
	// 모든 노드(위치)에 대하여 음료수 채우기
	for(int i = 0; i < n; i++){
		for(int j = 0; j < m; j++){
			if(dfs(i,j)){
				result += 1;
			}
		}
	}
	
	cout << result;
}

```




- scanf("%1d"...) 를 통해 *공백 없이* , *한 문자씩* 2차원 배열에 담는다.

---

### [실전문제] 미로 탈출
 ![미로탈출 문제 이미지](/public/img/studyAlgorithm/BFS_Q2.png)

- BFS로 해결하는 문제
- 괴물이 있는 0을 피해서 최하단으로 이동하는 최소 거리를 구하기
- 인접노드가 값이 1일 때, 인접노드로 이동하고 그 값은 +1해준다.




```c++
#include<iostream>
using namespace std;

int n, m;
int graph[201][201];

// 이동할 네 가지 방향 정의 (상, 하, 좌, 우) 
int dx[] = {-1, 1, 0, 0};
int dy[] = {0, 0, -1, 1};

int bfs(int x, int y) {
    // 큐(Queue) 구현을 위해 queue 라이브러리 사용 
    queue<pair<int, int> > q;
    q.push({x, y});
    // 큐가 빌 때까지 반복하기 
    while(!q.empty()) {
        int x = q.front().first;
        int y = q.front().second;
        q.pop();
        // 현재 위치에서 4가지 방향으로의 위치 확인
        for (int i = 0; i < 4; i++) {
            int nx = x + dx[i];
            int ny = y + dy[i];
            // 미로 찾기 공간을 벗어난 경우 무시
            if (nx < 0 || nx >= n || ny < 0 || ny >= m) continue;
            // 벽인 경우 무시
            if (graph[nx][ny] == 0) continue;
            // 해당 노드를 처음 방문하는 경우에만 최단 거리 기록
            if (graph[nx][ny] == 1) {
                graph[nx][ny] = graph[x][y] + 1;
                q.push({nx, ny});
            } 
        } 
    }
    // 가장 오른쪽 아래까지의 최단 거리 반환
    return graph[n - 1][m - 1];
}

int main(void) {
    // N, M을 공백을 기준으로 구분하여 입력 받기
    cin >> n >> m;
    // 2차원 리스트의 맵 정보 입력 받기
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            scanf("%1d", &graph[i][j]);
        }
    }
    // BFS를 수행한 결과 출력
    cout << bfs(0, 0) << '\n';
    return 0;
}

```



- pair<> 객체를 이용해서 데이터의 쌍을 클래스를 따로 만들지 않아도 표현할 수 있다.
