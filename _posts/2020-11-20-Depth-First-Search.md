---  
toc: true
toc_label: "Depth-First Search"
toc_icon: "cog"

categories:
  - Algorithm
tags:
  - Python
  - Depth-First Search
  - 깊이 우선 탐색
---  

# 깊이 우선 탐색 DFS(Depth-First Search)   
Depth First Search. 흔히 줄여서 DFS로 쓴다. 한국어 표기는 깊이 우선 탐색.  
그래프나 트리 형태의 구조에서 한 가지의 루트를 끝까지 탐색하는 알고리즘 이다.  
흔히 BFS (너비 우선 탐색)과 자주 비교대상이 되는 알고리즘임.  
DFS는 stack 자료구조를 이용하며 BFS는 Queue를 이용함.  
  
# 장단점
## 1. 장점 
- 현 경로상의 노드들만 기억하면 되기 때문에 저장공간의 수요가 적음.  
- 목표로 하는 노드가 깊은 단계에 있는 경우에 BFS에 비해 해를 빨리 찾을수 있음.  

## 2. 단점
- 해가 없는 루트에 깊이 빠지면 해를 구하는데 어려움이 있을 수 있음. (임의의 깊이를 지정하고 목표 깊이에 없는 경우 다음 루트를 탐색하면 꽤 효율적일 수 있음)  
> A* 알고리즘 (?)  

- 목표로 하는 해가 여러개일 경우에, DFS는 한개의 해에 다다르면 탐색이 끝나므로 최적해가 아닐 수도(?) 있음.  

# 구현
ㅡ python code  
```python  
# 임의의 그래프 구현
graph = {'A':['B','C'],
         'B':['A','D','E'],
         'C':['A','G','H'],
         'D':['B'],
         'E':['B','F'],
         'F':['E'],
         'G':['C'],
         'H':['C']}


#print(graph)
#print(graph['A'])

for i in reversed(graph['A']):
    print(i)

def dfs(graph, start_node):
    visited = list()
    stack = list()

    stack.append(start_node)

    while stack:
        node = stack.pop()
        print(node, 'node임')
        if node not in visited:
            visited.append(node)
            stack.extend(reversed(graph[node])) # 해당 노드의 자식들을 스택에 추가해줌.
            print(stack, '스택임')

    return visited

print(dfs(graph,'A'))

# ['A', 'B', 'D', 'E', 'F', 'C', 'G', 'H']
# Process finished with exit code 0
``` 
