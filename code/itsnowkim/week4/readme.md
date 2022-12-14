필수 문제
# 1931 : [회의실 배정](https://www.acmicpc.net/problem/1931)
- 가장 빨리 끝나는 순서대로 정렬하는 것이 핵심이다.
그러나 빨리 끝나는 것들 중에서 빨리 시작하는 회의를 골라야 하기 때문에 정렬을 두 번 해야 한다.
이 점을 캐치하는 것이 포인트였던 것 같다.
python의 sorted 옵션으로 lambda를 사용하여 구현하였다.

# 13334 : 철로 https://www.acmicpc.net/problem/13334
- 가장 많이 겹치는 것을 찾되, 지정된 철로의 길이보다 짧은 것을 찾는 것이 문제였다.
철로의 길이를 시작점 기준으로 정렬하여 for loop을 돌았다.
우선 철로의 길이보다 긴 것은 애초에 고려 대상이 아니므로, 첫 번째 분기를 철로의 길이로 하였다.

그 후, 이전 시작점과 겹치는지 여부를 확인해야 하는데,
'겹친다'의 조건은 이전 종료 지점보다 확인해야 하는 시작점이 더 작으면 성립하므로,
그러한 조건에 따라 분기처리를 하여 개수를 세어 주었다.

그런데 이렇게 풀면 50퍼센트 즈음에 틀리는데, 이유가 뭔지 모르겠다.

# 1202 : 보석 도둑 https://www.acmicpc.net/problem/1202
- 어떤 보석을 먼저 가방에 넣을지가 핵심이다. 가방에 들어가는 최대 무게 중에서 가장 비싼 보석을 찾는 것이 중요하다. 
즉, 두 개의 조건이 모두 최댓값이 되도록 하면 된다.
우선 가방에 꾸역꾸역 넣어야 한다고 생각해서 가방을 무게가 적게 나가는 순으로 먼저 정렬했고,
보석은 비싼 순으로 정렬하되, 무게는 적게 나가는 순서로 정렬하는 것이 좋다.
이렇게 풀면 근데 시간초과가 걸린다. 너무 짜증나서 검색해 보니까 자료구조를 활용해야 한다.
그래서 자료구조를 활용해서 O(nlogn)으로 줄였다.
리스트를 활용했을 때는 시간복잡도가 최악의 경우 O(N * K)이었던 것을 생각하면(가방개수 * 보석개수) 좋아졌으므로, 앞으로 어떨 때 이러한 자료구조를 택해야 하는지 생각해 볼 수 있는 문제였다.

- 시간초과의 늪에 빠진 나...

- 시도1. 시간초과.
```python 
for w in bag:
    while jewl and w >= jewl[0][0]:
        heapq.heappush(heap, -jewl.pop(0)[1])
    if heap:
        res -= heapq.heappop(heap)
```

- 시도2. elif 조건 추가. 시간초과.
```python 
for w in bag:
    while jewl and w >= jewl[0][0]:
        heapq.heappush(heap, -jewl.pop(0)[1])
    if heap:
        res -= heapq.heappop(heap)
    elif not jewl:
        break
```

- 시도3. pop(0)이 list의 길이만큼의 시간복잡도를 가진다는 것을 알고 다른 방법을 찾아야 했다.
-> 이거도 heap으로 처음에 받자. 시간초과....
```python 
for w in bag:
    while jewl and w >= jewl[0][0]:
        [tempweight, tempval] = heapq.heappop(jewl)
        heapq.heappush(heap, -tempval)
    if heap:
        res -= heapq.heappop(heap)
    elif not jewl:
        break
```

- 시도4. 개빡쳐서 머리 굴리던 중 pypy가 python3보다 더 빠르게 컴파일된다는 것을 알게 되어 그렇게 제출하였다. 추가로 input()에서 sys.stdin.readline()으로 입력을 바꿔줬다. 그랬더니 성공,,,
어이 없네,,,