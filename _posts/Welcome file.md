# Data-structure

- Study D.S. // 꾸준히 하면 다이긴다.
  
## 1. 선형 배열(Linear Array)

- 흔히 Python에서 리스트 내 원소(?)들에 대해서 append, pop등의 행위를 하는것을 말한다.
- 짚고 넘어가야 할 부분은 O(1)과 O(n)의 차이.
- O(1)는 리스트의 길이와 무관한 상수시간 동안의 시간이 소요, O(N)은 리스트 내부에 인덱스 요소를 써치하기 때문에 리스트의 길이에 비례해 시간이 소요됨.

> 시간복잡도 O(1)에 해당하는 리스트 원소의 추가,삭제(append, pop)은 리스트의 마지막에 요소를 넣었다가 뺐다가 한다.

> 하지만 시간복잡도 O(n)에 해당하는 리스트 내 원소의 삽입이나 제거(?) (insert, del) 은 리스트의 index 위치를 파라미터로 입력받는 차이점이 있다. ex) insert([index], element), del(list[index])



리스트의 조작은 밥먹듯이 하는 기본적인 것으로 리스트의 조작은 가볍게 pass 하도록 한다.  
ㄴ 리스트 조작하기 : https://dojang.io/mod/page/view.php?id=2281

그런데 문득 append()와 extend()의 차이가 무엇인지 궁금해서 구글링을 하였다.  
ㄴ 결론 : append는 x 그 자체를 원소로 넣고 extend는 iterable의 각 항목들을 넣습니다  
ㄴ https://m.blog.naver.com/PostView.nhn?blogId=wideeyed&logNo=221541104629&categoryNo=50&proxyReferer=

## 2. 정렬(Sorting)

#### 1) 선택정렬 (Selection Sort)
- 시간복잡도 : O(N^2)
- 선택정렬은 입력된 값 이외에 추가적인 메모리를 요구하지 않는 '제자리 정렬'의 일종이다.
- 내림차순의 배열을 오름차순으로 정렬할 때 가장 큰 효율을 자랑한다.
- 주어진 배열에서 최소값(min)을 찾은 후, 그 값을 배열의 가장 앞의 요소와 바꾼다.
- 이후 맨처음 위치를 빼고 상기 과정을 반복해서 정렬을 완성한다.

- 장점으로 자료의 이동 횟수가 미리 결정되지만, 같은 값의 요소인 경우 연산을 할 수도 있음.
```sh
# 랜덤한 리스트 생성 후 선택 정렬.
import random

def randomList(num):
    result = []
    for i in range(num):
            result.append(random.randint(0, num))
    return result

def selectionSort(x):
    length = len(x)
    for i in range(length - 1):
        indexMin = i;
        for j in range(i + 1, length):
            if x[indexMin] > x[j]:
                indexMin = j
        x[i], x[indexMin] = x[indexMin], x[i]
    return x

x = randomList(7777)

print(x)
print(selectionSort(x))
```

> Reference : https://gmlwjd9405.github.io/2018/05/06/algorithm-selection-sort.html


#### 2) 삽입정렬 (Insertion Sort)

- 시간복잡도 : O(N ~ N^2)
- 자료 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분과 비교하여, 자신의 위치를 찾아 삽입함.
- 삽입정렬은 이름 그대로 원하는 위치에 원소를 삽입하는 정렬임.
- 대상으로하는 리스트가 이미 정렬되어있는 상태에 가까울 때 최고의 효율을 자랑함.  ex) [1,2,3,4,5,7,6]
- 단점은 반대로 내림차순을 오름차순으로 바꿀경우 효율이 좋지 않음.

```sh
# 2번째 원소부터 써치
def insert_sort(x):
    for i in range(1, len(x)):
        for j in range(i, 0, -1):
            if x[j-1] > x[j]:
                x[j-1], x[j] = x[j], x[j-1]
```

> Reference : https://www.daleseo.com/sort-insertion/


#### 3) 버블정렬 (Bubble Sort)
- 시간복잡도 : O(N^2)
- 서로 인접한 두 레코드를 검사하여 정렬하는 알고리즘.
- 역시 시간복잡도 좋지 않아 잘 사용하지 않음.
- 장점으로 구현이 매우 간단하지만, 인접한 레코드를 바꾸는 것(SWAP) 보다 맞는 위치로 옮기는 거(MOVE)가 효율이 좋음.

```sh
def bubble_sort(x):
    for i in range(len(x)-1):
        temp = i
        for j in range(i+1, len(x)):
            if x[j] < x[i]:
                x[j], x[i] = x[i], x[j]
    return x
```


## 3. 스택/큐 (Stack/Queue) 

#### 1) 스택(Stack)
- 리스트의 한 쪽 끝에서만 자료를 넣고 뺄 수 있는 LIFO(후입선출) 자료구조. LIFO Queue 라고도 불림.
- PUSH / POP을 이용해 레코드를 한쪽에서만 넣었다 뺐다함.
- Stack overflow는 스택이 꽉차서 레코드가 안들어갈 때, Stack underflow는 삭제해야할 자료가 남아있지 않을 때  
※ Stack에 기억되어 있는 자료를 삭제시킬 때는 제일 먼저 삭제할 자료가 있는지 없는지부터 확인해야 한다.


```sh
# Stack Class

class stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        return self.items.pop()

    def isEmpty(self):
        return not self.items

stk = stack()
print(stk)
print(stk.isEmpty())
stk.push(1)
stk.push(2)

print(stk.pop())
print(stk.pop())
print(stk.isEmpty())

```

> Reference : https://korbillgates.tistory.com/79, https://daimhada.tistory.com/105


#### 2) 큐(Queue)
- 스택에 반대되는 개념으로 선입선출(FIFO) 
- PUT / GET을 통해 리스트에 원소를 덧붙이거나 끝에서 꺼냄.
- 리스트를 사용했을 경우 enqueue(추가) 시간복잡도는 O(1), dequeue(삭제) 시간복잡도는 O(N).
- Queue의 종류는 선형큐, 환형큐, 우선순위큐 등이 있음.
- 일반적인 선형큐는 마지막 index를 가리키는 변수가 있는데, dequeue를 할때마다 비어있는 공간이 생기게되면서 이를 활용할수 없게 됨.  
ㄴ 이러한 방식을 해결하기 위해 원형큐가 나옴

```sh
class ListQueue(object):
    def __init__(self):
        self.queue = []

    def enqueue(self, n):
        self.queue.append(n)

    def dequeue(self):
        if len(self.queue) == 0:
            return -1
        return self.queue.pop(0)

    def printQueue(self):
        print(self.queue)

lq = ListQueue()
lq.enqueue(1)
lq.enqueue(2)
lq.enqueue(3)
lq.enqueue(4)
lq.printQueue()
print(lq.dequeue())
print(lq.dequeue())
print(lq.dequeue())
print(lq.dequeue())
lq.printQueue()
```

- 파이썬은 collections.deque 모듈을 지원한다.
- 데크는 double-ended-queue의 줄임말로 앞뒤 방향에서 데이터를 처리할 수 있게하는 자료구조이며 내부적으로 doubly 링크드 리스트로 구현이 되어있다고 한다.
- 데크의 시간복잡도는 O(1)로 아주 강력한 놈이다.

```sh
from collections import deque

dq = deque([])

dq.append(1)
dq.append(2)
dq.append(3)
dq.append(4)

print(dq)

dq.popleft()
dq.popleft()
dq.popleft()
dq.popleft()

print(dq)

```
> *collections.deque Reference : https://excelsior-cjh.tistory.com/96*


- 파이썬의 Queue 모듈 사용해서도 구현이 가능하다.
- Queue 모듈은 스레드 환경을 고려해서 작성되어 있기 때문에 동시에 여러개의 작업을 수행해도 전혀 문제되지 않는다.

```sh
import queue

q = queue.Queue()

q.put(1)
q.put(2)
q.put(3)
q.put(4)


print(q.get())
print(q.get())
print(q.get())
print(q.get())


from collections import deque

class Queue(deque):
    def enqueue(self, x):
        super().append(x)

    def dequeue(self):
        super().popleft()

    def display(self):
        for node in self.__iter__():
            print(node)
```
- Linked list Queue는 다음에 연결리스트 정리할 때 한번에 하는걸로...
> Queue Reference : https://daimhada.tistory.com/107


## 4. 힙 (Heap) 

#### 힙 (Heap)
- 우선순위 큐를 위해서 만들어진 자료구조. (가장 우선순위가 높은 레코드를 먼저 꺼낼 수(?) 있음!)
- 시간복잡도 : O(logN) (삽입, 삭제 시)
- 완전이진트리로 구성되어 있으며, 부모 노드는 자식 노드보다 반드시 크거나 같다. (최소 힙일 경우에는 반대 부모 노드가 자식노드보다 작거나 같다.)
- 힙의 경우 배열 내 첫번 째 인덱스 0 은 건너뛰고 1부터 시작.
- Python의 경우 HeapQ 모듈을 이용해 간단하게 구현할 수 있을 거로 보임.

```sh
# heapQ push,pop() 사용법

import heapq
# text  = "내이름은 한규문 명탐정 이죠"
h = []
heapq.heappush(h, (3, " 명탐정"))
heapq.heappush(h, (4, " 이죠"))
heapq.heappush(h, (1, "내이름은"))
heapq.heappush(h, (2, " 한규문"))
heapq.heappush(h, (5, " 훗"))

print(h)

first = heapq.heappop(h)
second = heapq.heappop(h)
third = heapq.heappop(h)
print("first:", first)
print("second:", second)
print("third:", third)

print(h)
```
> 힙에서의 부모 노드와 자식 노드의 관계  
> 왼쪽 자식의 인덱스 = (부모의 인덱스) * 2  
> 오른쪽 자식의 인덱스 = (부모의 인덱스) * 2 + 1  
> 부모의 인덱스 = (자식의 인덱스) / 2  

> Reference  
> ㄴ https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html  
> ㄴ https://velog.io/@junhok82/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%ED%9E%99heap  
> ㄴ HeapQ 모듈 : https://medium.com/@yhmin84/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9A%B0%EC%84%A0%EC%88%9C%EC%9C%84-%ED%81%90-priority-queue-%EB%A5%BC-%EC%9C%84%ED%95%9C-heapq-%EB%AA%A8%EB%93%88-%EC%82%AC%EC%9A%A9%EB%B2%95-b33c4e0ef2b1  


## 5. 탐욕 알고리즘 (Greedy) 

#### 탐욕 알고리즘 (Greedy) 
- 부분적인 최적해가 전체의 해가되는 알고리즘.  
- 매번 최선의 선택을 통해 전체 해를 맞춘다고 생각하면 됨   
- 매번 최선의 선택을 하지만 그것이 반드시 최적화된 값이라고는 판정지을 수는 없다. 즉, 한번의 선택이 다음 선택에는 전혀 무관한 값이여야 하며 매 순간의 최적해가 문제에 대한 최적해여야 한다는 의미이다.  

| 탐욕 알고리즘 Problems  
| ㄴhttps://programmers.co.kr/learn/courses/30/parts/12244  

> Reference  
> ㄴhttps://namu.wiki/w/%EA%B7%B8%EB%A6%AC%EB%94%94%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98  

# Programmers in python 

See [Programmers](https://programmers.co.kr/)