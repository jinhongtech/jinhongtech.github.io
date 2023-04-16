---
layout: single
title: "05.연결리스트(Linked List)"
categories: 
  - DataStructure
  - CS
---


## 한방향 연결리스트(Singly Linked List)

- 필요연산
    - 삽입연산(pushFront, pushBack)
    - 삭제연산(popFront, popBack)
- 추가연산
    - 탐색(search)
    - 제너레이터(generator)

<img src="/images/data_structure/5.linkedlist1.png" width="90%" height="90%">


```python
#노드 생성 클래스
class Node:
	def __init__(self,key=None):
		self.key = key
		self.next = None
	def __str__(self):
		return str(self.key)

a = Node(3)
b = Node(9)
c = Node(-1)
a.next = b
b.next = c
			
```

<img src="/images/data_structure/5.linkedlist2.png" width="100%" height="100%">


```python
class Node:
	def __init__(self,key=None):
		self.key = key #현재 노드의 데이터 값
		self.next = None #다음 노드
	def __str__(self):
		return str(self.key)

#연결 리스트 객체 생성 클래스
class SinglyLinkedList:
	def __init__(self):
		self.head = None
		self.size = 0

	def pushFront(self, key): #헤드 노드 앞에 새로운 노드 삽입
		new_node = Node(key)
		new_node.next = self.head
		self.head = new_node
		self.size += 1

	def pushBack(self, key): #테일 노드 앞에 새로운 노드 삽입
		new_node = Node(key)
			if len(self) == 0: #빈 리스트에 pushBack으로 노드 삽입 시 그 노드가 head이자 tail이 됨
				self.head = new_node
			else: #next가 None인 노드를 head에서부터 찾아야됨
				tail = self.head
				while tail.next != None:
					tail = tail.next
				tail.next = new_node
		self.size += 1

	def popFront(self):
		if len(self) == 0:
			return None
		else:
			head_node = self.head
			key = head_node.key
			self.head = head_node.next
			self.size -= 1
			del head_node #기존 head_node 메모리 삭제
		return key

	def popBack(self):
		if len(self) == 0:
			return None
		else:
			#running technique
			prev, tail = None, self.head
			while tail.next != None:
				prev = tail
				tail = tail.next
			if len(self) == 1: #노드가 하나밖에 없다면 그 노드가 head이자 tail이 되기 때문에 head도 제거
				self.head = None
			else:
				prev.next = None
			key = tail.key
			del tail
			self.size += 1
		return key		

	def search(self,key): #key값의 노드를 리턴, 없으면 None 리턴
		v = self.head
		while v != None:
			if v.key == key:
				return v
			v = v.next
		return None

	def __iterator__(self): #제너레이터: for _ in 연결리스트 사용 가능하게
		v = self.head
		while v != None:
			yield v
			v = v.next
```

- pushFront, pushFront → O(1)
- pushBack, popBack → O(n) (tail 노드를 찾아야되기 때문에)
- search → O(n) (최악의 경우 모든 노드를 찾아봐야함)


## 양방향 연결리스트(Doubly Linked List)

- 한방향 연결리스트: tail node를 지울 때 tail node를 알고 있어도 tail node 직전에 있는 prev node를 알아야한다.(prev node의 링크가 더이상 tail node를 가리키면  안되기 때문 또한 tail node 를 알아도 prev node를 알 수 없기 때문에 head node부터 다시 찾아야함)
- 노드(key값 + next link + prev link)
- 한방향 연결리스트에 비해서 한 노드에 사용되는 메모리가 증가하지만 특정 위치의 노드를 삭제하거나 추가할 때 시간복잡도가 줄어든다.

<img src="/images/data_structure/5.linkedlist3.png" width="100%" height="100%">

### 원형 양방향 연결리스트(Circularly Doubly Linked List)

- 기존 양방향 연결리스트에 비해 삽입 삭제 연산들이 간단해진다.

<img src="/images/data_structure/5.linkedlist4.png" width="100%" height="100%">


- 원형연결리스트의 시작을 표기하기 위해 빈리스트 dummy node를 사용한다.
    
<img src="/images/data_structure/5.linkedlist5.png" width="100%" height="100%">

    

```python
class Node: #새로운 노드 생성
	def __init__(self, key=None):
		self.key =key
		self.next = self
		self.prev = self

class DoublkyLinkedList:
	def __init__(self):
		self.head = Node()
		self.size = 0

	def __iter__(): #generator
	def __str__(): #print 가능하게
	def __len__(): #len

  #splice 연산: 연결리스트 안에 있는 a에서 b까지의 노드를 잘라서 x노드 뒤에 붙이는 연산
	#조건1: a -> ... -> b
	#조건2: a와 b사이에 head가 없어야됨
	def splice(self, a, b, x):
		ap = a.prev
		bn = b.next
		xn = x.next
		#a~b cut
		ap.next = bn
		bn.prev = ap
		#x뒤에 a~b 붙이기
		xn.next = a
		a.prev = x
		b.next = xn
		xn.prev = b

	#splice를 통해서 다음 함수를 구현가능
	def moveAfter(self,a,x):
		splice(a,a,x)
	def moveBefore(self,a,x):
		splice(a,a,x.prev)
	def insertAfter(x,key):
		moveAfter(Node(key),x)
	def insertBefore(x,key):
		moveBefore(Node(key), x)
	def pushFront(key):
		insertAfter(self.head, key)
	def pushBack(key):
		insertBefore(self.head, key)

	#탐색
	def search(self,key):
		v = self.head #dummy node
		while v.next != self.head:
			if v.key == key:
				return v
			v = v.next
		return None

	#삭제
	def remove(x): # x 노드 삭제
		if x == None or x == self.head:
			return None
		xp = x.prev
		xn = x.next
		xp.next = xn
		xn.prev = xp
		del x

	def popFront(): #head node 의 next node를 제거
		if len(self) == 0:
			return None
		remove(self.head.next)

	def popBack(): #head node의 prev node를 제거
		...

	#join 함수: 두연결리스트 하나로 합치기
	#split 함수: 한 연결리스트를 특정 노드를 기준으로 split
```

- splice 연산 그림

<img src="/images/data_structure/5.linkedlist6.png" width="100%" height="100%">


- 시간복잡도
    - search(key): O(n)
    - splice(a,b,x): O(1) → 6개의 링크만 수정해주면 되기 때문에
    - splice로 구현된 함수들: O(1)
    - remove(x): O(1)

    