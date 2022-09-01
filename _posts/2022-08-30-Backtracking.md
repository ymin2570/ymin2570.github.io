---
title: "[알고리즘] 백트래킹"
categories:
    - Algorithm
tags:
    - [Algorithm]
    - [BackTracking]
toc: true
toc_sticky: true
date: 2022-08-30 20:20
---
--------------------------

알고리즘 중 하나인 백트래킹에 대해 복습하고자 한다.

## 백트래킹

필자는 이전 알고리즘을 공부할 때 백트래킹을 공부했었고, 유명한 예시인 N Queen도 풀어보았는데, 이제 와서 다시 풀어보려니 잘 되지 않아 개념부터 잡고 가려고 한다.  
(이래서 공부한 내용은 정리해두는 것이 중요하구나 싶다.)

우선 백트래킹과 비슷한 알고리즘인 DFS가 있다.  
DFS는 가능한 모든 경로를 탐색하기에 경우의 수를 줄이지 못한다. 따라서 N!가지의 경우의 수를 가진 문제는 DFS로 처리할 수 없는 문제가 있다.

백트래킹은 답을 찾아가는 중, 경로가 답이 아닌 것 같으면 더이상 해당 경로로 가지 않고 돌아간다고 한다. 이를 가지치기(pruning)라고 부른다.

## N과 M(1) (14649번)
```python
import sys

N, M = map(int,sys.stdin.readline().split())
visit = [False] * (N)
s = []

def back():
    if len(s) == M:
        for i in range(M):
            print(s[i],end=' ')
        print()
        return
    for i in range(1,N+1):
        if visit[i-1] == False:
            s.append(i)
            visit[i - 1] = True
            back()
            s.pop()
            visit[i - 1] = False

back()
```
백트래킹의 기본을 다지기 위해 N과 M을 풀어보았다.  
이전에 N과 M을 싹다 풀었었는데 지금 와서 풀려고 보니 아무것도 기억이 안나서 살짝 충격.. 열심히 공부해야겠다..

2022-09-01  
N과 M 전부를 풀어보았고, 이제 N Queen을 풀고 있다.  
이전에 풀었던 방식은 2차원 배열을 만들어 Queen을 놓았을 때 불가능한 부분에 depth 숫자를 적어서 pruning을 할 때 해당 depth의 숫자가 적힌 부분을 지우는 식으로 진행하였다.  
그런데, 다른 사람들의 풀이를 찾아보니 1차원 배열에 인덱스와 값을 활용하여 row와 column의 값을 저장하는 방식도 있었다.  
이런 방식이 신기해서 분석을 좀 하다가 더 많은 사람들의 풀이를 보고 싶어서 찾아보았는데 이상하게도 검색해서 나온 풀이들이 다 비슷비슷했다..  
당장 나만해도 풀이 방식이 다른데 이사람들은 도대체 왜 다 풀이 방식이 똑같은걸까..

## N-Queen  
작성하기 앞서 해당 코드는 내가 직접 구현한 코드가 아닌, 다른 사람의 코드를 분석해서 공부한 것임을 알린다.  
```python
import sys

N = int(sys.stdin.readline())
Chess = [0 for i in range(N)]   #퀸의 위치를 저장하는 1차원 배열
Visited = [False for i in range(N)]
cnt = 0

def Valid(depth):       #퀸을 놓을 수 있는 지 유효성 검사, 인자로 몇번째 행인지를 받는다.
    for i in range(depth):
        if(Chess[i] == Chess[depth] or depth - i == (abs(Chess[depth] - Chess[i]))):    #같은 열에 있는 퀸이 존재하는 지, 혹은 대각선에 퀸이 존재하는 지 확인
            return 0
    return 1

def Queen(depth):
    global cnt
    if(depth == N):     #N개의 퀸을 놓는 경우를 찾았을 때
        cnt += 1
        return
    else:
        for j in range(N):
            if not Visited[j]:
                Chess[depth] = j    #현재 행과 열에 퀸을 놓고, 유효성 확인
                if(Valid(depth)):
                    Visited[j] = True
                    Queen(depth+1)
                    Visited[j] = False

Queen(0)
print(cnt)
```
해당 코드를 Python으로 제출해보았더니 시간 초과가 나온다.. 음..  
Pypy3로 제출하면 해결된다는데 ... 뭔가 좀 후련하지 않은 기분.. 파이썬은 시간초과 오류를 주의해야겠구나 싶었다.  

+) 심지어 인터넷에 만연한 코드들은 Visited라는 bool 배열이 없어 Pypy3으로 제출해도 시간 초과가 걸렸다.. 도대체 뭐지 이사람들..?