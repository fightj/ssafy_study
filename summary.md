버블, 카운팅정렬 2개중 1개가 시험에 나옴(서술형)

카운팅 정렬
```python
numbers = [1,4,1,2,7,5,2]

def counting(arr):
    # arr의 최댓값
    # max_value = max(arr)
    max_v = float('-inf')
    for num in arr:
        if num > max_v:
            max_v = num
    #카운트 배열 초기화
    count = [0] * (max_v+1)

    #카운팅! 각 숫자의 출현 횟수 세기
    for num in arr:
        count[num] += 1

    #카운트 배열을 기반으로 정렬된 리스트 만들기
    sorted_arr = []
    for i in range(len(count)):
        for j in range(count[i]):
            sorted_arr.append(i)

    return sorted_arr

result = counting(numbers)
print(result)
```

순열: 주어진 항목들로 만들 수 있는 모든 가능한 순서
순열을 만드는 메서드
```python
import itertools

lst = [1,2,3]

print(list(itertools.permutations(lst)))
#combination(lst, N) : lst에서 N개의 원소를 가진 모든 조합(원소의 중복 x)
print(list(itertools.combination(lst, N)))

```
- 탐욕(greedy) 알고리즘 : 각 단계에서 가장 최선의 선택을 하는 방법
- 대표적인 에제 문제 : 거스름돈 문제
```python
def greedy(money, coins):
    coins.sort(reverse = True)
    change = {coin : 0 for coin in coins}
    for coin in coins:
        while money >= coin:
            money -= coin
            change[coin] +=1
    return change

result = greedy(380, [100, 50, 10])
print(result)
```
- 알고리즘 2문제 75점 1문제 쉽고 1문제 어려움 /  서술형 1문제

- 웹 배우고 나면 im A형 수준 8월 3째주 월요일 im시험.

0731 알고리즘
- 리스트 순회 

```python
n = int(input())
arr = [list(map(int, input().split())) for _ in range(n)]

di = [0, 1, 0, -1]
dj = [1, 0, -1, 0]

total = 0

for i in range(n):
    for j in range(n):  #NxN 배열의 모든 원소에 대해
        s = 0   #문제에서 원소와 인접원소의 차이 ... 합 저장
        # i, j 원소의 4방향 원소에 대해
        for k in range(4):
            ni = i + di[k]
            nj = j + dj[k]
            if 0 <= ni < n and 0 <= nj < n:
               s += abs(arr[i][j] - arr[ni][nj])    #실존하는 인접원소 ni, nj
        total += s

print(total)
```

- 부분집합 생성하기
```python
import itertools

lst = [1,2,3]
# lst의 순열
ans1 = list(itertools.permutations(lst))
# lst에서 n개의 원소를 가진 모든 조합(원소의 중복이 없다)
ans2 = list(itertools.combinations(lst, 2))
print(ans1)
print(ans2)
```
- 비트 연산자 (시험으로도 출제 될 것임)
- &: 비트 단위로 AND 연산을 한다
- |: 비트 단위로 OR연산을 한다.
- << 피연산자의 비트 열을 왼쪽으로 이동시킨다.
- >> 피연산자의 비트 열을 오른쪽으로 이동시킨다.

- 방향 배열: 2차원 맵(배열)에서 현재 위치를 기준으로 이동할 수 있는 방향을 나타내는 배열
- dy = [-1, 0, 1 ,0]    #상좌하우  
- dx = [0, 0, -1, 1]    #상하좌우

- dy = [-1, -1, 1, 1]   #좌상, 우상, 좌하, 우하
- dx = [-1, 1, -1, 1]   #좌상, 우상, 좌하, 우하  대각선

- 사용법: 현재위치(y,x) i번째 방향으로 이동
- ---> ny, nx = y + dy[i], x + dx[i]



## 0801 알고리즘
- 검색 (순차검색, 이진 검색, 해쉬) 해쉬는 자세히 x
- 순차 검색 : 가장 간단하고 직관적인 검색 방법 / 배열이나 연결 리스트 등 순차구조로 구현된 자료구조에서 원하는 항목을 찾을 때 유용 / 검색 대상의 수가 많은 경우에는 수행시간이 급격히 증가하여 비효율적
  
- 정렬되어 있는 경우 : 검색 대상의 키 값보다 크면 찾는 원소가 없다는 것이므로 더 이상 검색하지 않고 검색을 종료한다.

- 이진검색 : (정렬되어 있어야 사용가능) 중앙을 기준으로 가운데 원소랑 검색하려는 원소를 비교하여 중앙보다 작으면 중앙을 기준으로 왼쪽을 검색함 -> 왼쪽의 중앙을 기준으로 다시 검색하려는 원소를 비교하여 반복.
- 구현방법
```python
def binarySearch(a, N, key):
    start = 0
    end= N-1
    while start <= end:
        middle = (start+end)//2
        if a[middle] == key: #검색성공
            return true
        elif a[middle] > key:
            end = middle -1
        else:
            start = middle +1
    return false                

```
- 선택 정렬
```python
def selectionSort(a,N):
    for i in range(N-1):
        min_idx = i
        for j in range(i+1, N):
            if a[min_idx] > a[j]:
                min_idx = j
        a[i], a[min_idx] = a[min_idx], a[i]        
```

- 비트 연산
- 1. 비트 이동 연산 (<<)
- 1 << 3 ---> 이진수 1을 왼쪽으로 3칸 밀기 ---> 2진수 1000, 10진수 8
- 2. 비트 AND연산(&) != and
- 두 이진수의 각 자리를 비교하여, 둘다 1이면 1, 그렇지 않으면 0  
### 부분집합의 합(19607) 다르게 풀기
```python
import itertools

T=int(input())
for tc in range(1, T+1):
    N, K = map(int, input().split())
    lst = [i for i in range(1,13)]
    # lst에서 N개의 원소를 가진 조합
    lst_comb = itertools.combinations(lst, N)
    
    cnt = 0
    
    for i in lst_comb:
        if sum(i) == K:
            cnt +=1
    print(f'#{tc} {cnt}')
```
```python
T = int(input())
for tc in range(1, T+1):
    N, K = map(int, input().split())
    lst = [i for i in range(1,13)]
    cnt = 0
    
    for i in range(1 << 12): # lst의 원소의 개수가 12개
        sum_sub = 0 # 부분집합의 원소 합
        subset = [] # 현재 부분 집합
        for j in range(12): # 집합의 각 원소에 대해 반복
            # i의 j 번째 비트가 1인지 아닌지 팔별할 수 있다.
            if i & (1 << j):
                sum_sub += lst[j]
                subset.append(lst[j])
        if sum_sub == K and len(subset) == N:
            cnt += 1
        
    print(f'#{tc} {cnt}')
```    





2차원 리스트 40, 1차원 리스트 35, 서술형(버블소트) 25
- 대문자 A:65, 소문자 a:97 의 아스키코드값 암기, 소문자의 아스키 코드값이 더 크다.
- 공백(space)도 아스키 코드값이 있다.
- if, 조건식에서 아스키 코드값을 사용할 필요는 없다.
- 회문 : string == string[::-1]
- 문자열 parsinf 문제에서 자주 사용하는 메서드
- split(), strip() : 공백제거, lstrip(), rstrip()
- replace(), join()
- find(), index() : 문자열 내에서 특정 부분의 위치를 찾기
- isdigit(), isalpha(), isalnum(): 문자열이 숫자, 알파벳 또는 둘다로 이루어져 있는가
  





