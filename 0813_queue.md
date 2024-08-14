큐 or 스택 서술형으로 나올 수 있음.!! or DFS, BFS 서술형
# 0813 Queue
# 선형큐
## BFS
- 
```python
# 인접행렬 bfs 시작

from collections import deque

n = int(input())
MAP = [list(map(int, input().split())) for _ in range(n)]

def bfs(node):
    q = deque([node]) # 시작 노드 큐에 추가
    visited = [0] * n
    visited[node] = 1 # 시작 노드 방문 표시

    while q:
        now = q.popleft()
        print(now, end = ' ')
        for i in range(n):
            # 이미 방문 했거나(visited배열이 1), 연결되어 있지 않은 노드(인접행렬이 0)면 continue
            if MAP[now][i] == 0 or visited[i] == 1:
                continue
            visited[i] = 1
            q.append(i)

bfs(0)
'''
# 인접행렬 dfs 시작
'''
n = int(input())
MAP = [list(map(int, input().split())) for _ in range(n)]

def dfs(now):
    print(now, end = " ")
    for i in range(n):
        # if MAP[now][i] == 1: # 현재 위치에서 i로 갈수 있는 길이 있으면
        #     dfs(i)
        if MAP[now][i] == 0: 
            continue
        dfs(i)

dfs(0)

```
