### ๐ย ๋ฌธ์  ์ถ์ฒ

- [๋ฐฑ์ค] 2644๋ฒ : ์ด์๊ณ์ฐ
- [์๊ธ ๋งํฌ](https://www.acmicpc.net/problem/2644)

### โ์์ ์๋ ฅ

```
9
7 3
7
1 2
1 3
2 7
2 8
2 9
4 5
4 6
```

```
9
8 6
7
1 2
1 3
2 7
2 8
2 9
4 5
4 6
```

### โผ๏ธ์ ๊ทผ ๋ฐฉ์

- BFS ๋ก ์ฒ์ ์ ๊ทผํด์ ํ์๋ค๊ฐ ๊ฐ์๋ฅผ ์ธ๊ธฐ๊ฐ ํ๋ค๋ค๋ ์ ์ ๊นจ๋ซ๊ณ 
- DFS ๋ก ๋ฐ๊ฟจ์
- ๋จ์ DFS ๋ฅผ ๊ตฌํํ๋๋ฐ ํ์คํธ ์ผ์ด์ค๋ฅผ ํต๊ณผํ๋๋ฐ ์ ์ถ์ ์คํจ๋ธ
- ๊ทธ ์ด์ ๋ฅผ ๋ชป ์ฐพ๊ณ  ์์

### ๐ย ์๊ณ ๋ฆฌ์ฆ ๋ฐ ์ฝ๋ ๊ตฌํ

```python

n = int(input())
start, end = map(int,input().split())
m = int(input())
graph = [[] for _ in range(n)]
visited = [False] * n
for _ in range(m):
  a, b = map(int,input().split())
  graph[a-1].append(b)
  graph[b-1].append(a)
for node in graph:
  node.sort()
# print(graph)
cnt = 0
flag = False
def dfs(node):
  global flag
  global cnt
  visited[node-1] = True
  cnt +=1
  if node == end:
    flag = True
    print(cnt-1)
    return
  for v in graph[node-1]:
    if visited[v-1] == False:
      dfs(v)
dfs(start)

if not flag:
  print('-1')
```

### ๐ฐย ์๊ฐ๋ถ์

- ํด๋น ์ฝ๋์ ์๊ฐ:
  O(N)
- ํ๋จํ ์ด์ :
  dfs ๋ ์ ํ ์๊ฐ

### โ๏ธย ์์ธ์ฒ๋ฆฌ

### โ๏ธย ์ฝ๋ ์ค๋ํซ ๋ฐ ๋ด์ฅ ๋ชจ๋

```python
# ์ฝ๋ ์ค๋ํซ
start, end = map(int,input().split())
```

```python
# ๋ด์ฅ ๋ชจ๋
```

### โ๏ธ ํ๊ณ 

> ์ ๊ทผ ๋ฐฉ์์ ์จ๋๋๋ฐ bfs ๋ก ๋จผ์  ๋ค๊ฐ๊ฐ๊ณ  ๋ธ๋ ํ ์นธ์ฉ ์ด๋ํ  ๋๋ง๋ค ๊ฐ์๋ฅผ ์ธ๊ธฐ ์ํด์๋
> dfs ๊ฐ ์ ์ ํ๋ค๋ ๊ฒ์ ๊นจ๋ซ๊ณ  ๊ณ ์ณค๋ค. ๊ทผ๋ฐ ํ์คํธ ์ผ์ด์ค๋ฅผ ํต๊ณผํ๋๋ฐ ๋ฌธ์ ๋ ํ๋ฆฐ๋ค. ์ด๋ ๋ถ๋ถ์์
> ํ๋ฆฌ๋์ง ํ์ธ์ ๋ชป ํ๋ ์ค.


----

### ๐ย ๋ฌธ์  ์ถ์ฒ

- [BOJ] 2583 : ์์ญ ๊ตฌํ๊ธฐ
- [์๊ธ ๋งํฌ](https://www.acmicpc.net/problem/2583)

### โ์์ ์๋ ฅ
```
5 7 3
0 2 4 4
1 1 2 5
4 0 6 2
```

### โผ๏ธ์ ๊ทผ ๋ฐฉ์

- ์ง์ฌ๊ฐํ ๋๊ธฐ
- ๋์ด ๊ณ์ฐ

### ๐ย ์๊ณ ๋ฆฌ์ฆ ๋ฐ ์ฝ๋ ๊ตฌํ

```python
# ์์ญ ๊ตฌํ๊ธฐ
# 22.11.2
# dfs

import sys
read=sys.stdin.readline
n,m,k=map(int,read().split())

graph = [[0]*(m) for _ in range(n)]

# ๋ฎ๊ธฐ
for _ in range(k):
  a,b,c,d = map(int,read().split())
  for i in range(b,d):
    for j in range(a,c):
      graph[i][j] = 1
    
# for row in graph:
#     print(row)

# ์นด์ดํธ
dx=[-1,0,1,0] 
dy=[0,1,0,-1]
test = 0
test2 = []
def dfs(x,y):
  global test
  if x<0 or y <0 or x>=n or y>=m:
    return False
  if graph[x][y] == 0:
    graph[x][y] = test+1
    test+=1
    for i in range(4):
      nx = x + dx[i]
      ny = y + dy[i]
      dfs(nx,ny)
  else:
    return False
  return True

cnt = 0
for i in range(n):
  for j in range(m):
    if dfs(i,j):
      cnt +=1

for v in graph:
  print(v)

```

### ๐ฐย ์๊ฐ๋ถ์

- ํด๋น ์ฝ๋์ ์๊ฐ:
O(N)
- ํ๋จํ ์ด์ :
DFS ๋ ์ ํ ์๊ฐ

### โ๏ธย ์์ธ์ฒ๋ฆฌ

### โ๏ธย ์ฝ๋ ์ค๋ํซ ๋ฐ ๋ด์ฅ ๋ชจ๋

```python
# ์ฝ๋ ์ค๋ํซ
```

```python
# ๋ด์ฅ ๋ชจ๋
```

### โ๏ธ ํ๊ณ 
> ๊ฐ์๋ ์ธ์๋๋ฐ, ๋์ด๋ ๊ตฌํ์ง ๋ชป ํจ.
>

----


### ๐ย ๋ฌธ์  ์ถ์ฒ

- [BOJ] 1987 : ์ํ๋ฒณ
- [์๊ธ ์ถ์ฒ](https://www.acmicpc.net/problem/1987)

### โ์์ ์๋ ฅ

```
3 6
HFDFFB
AJHGDH
DGAGEH
```

### โผ๏ธ์ ๊ทผ ๋ฐฉ์

- ์ํ๋ฒณ ์ข๋ฅ ์ ์ฅ
- ์ข์ธก ์๋จ๋ถํฐ ํ์ ์์
- ํ ์นธ ์ด๋ํ  ๋ ๋ง๋ค +1
- ๊ทธ ์นธ์ ์ ๋ณด๊ฐ ์ด์ ์ ์ ์ฅ๋ ์ํ๋ฒณ์ด๋ฉด ๋ฉ์ถ๊ณ  cnt ๋ฐํ

### ๐ย ์๊ณ ๋ฆฌ์ฆ ๋ฐ ์ฝ๋ ๊ตฌํ

```python
# ์ํ๋ฒณ
# 22.11.4

import sys
read=sys.stdin.readline
r,c=map(int,read().split())

visited = [[False]*c for _ in range(r)]
visited[0][0]=1
alphabet = [ list(input()) for _ in range(r)]

dx=[-1,0,1,0] 
dy=[0,1,0,-1]
test = []
cnt = 0
ans = 0
def dfs(x,y,cnt):
  global ans
  ans = max(cnt,ans)
  now = alphabet[x][y]
  for i in range(4):
    nx = x + dx[i]
    ny = y + dy[i]
    if nx <0 or ny <0 or nx>=r or ny >=c:
      continue
    if not visited[nx][ny] and alphabet[nx][ny] not in test:
      test.append(alphabet[nx][ny])
      dfs(nx,ny,cnt+1)

dfs(0,0,1)
print(f'ans:{ans}')
```

### ๐ฐย ์๊ฐ๋ถ์

- ํด๋น ์ฝ๋์ ์๊ฐ
- ํ๋จํ ์ด์ 

### โ๏ธย ์์ธ์ฒ๋ฆฌ

### โ๏ธย ์ฝ๋ ์ค๋ํซ ๋ฐ ๋ด์ฅ ๋ชจ๋

```python
# ์ฝ๋ ์ค๋ํซ
```

```python
# ๋ด์ฅ ๋ชจ๋
```

### โ๏ธ ํ๊ณ 
> 
>