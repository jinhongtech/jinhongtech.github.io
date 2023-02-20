---
layout: single
title: "연결리스트(Linked List)"
categories: 
  - DA
---

# 5. 연결리스트(Linked List)

## 한방향 연결리스트(Singly Linked List)

- 필요연산
    - 삽입연산(pushFront, pushBack)
    - 삭제연산(popFront, popBack)
- 추가연산
    - 탐색(search)
    - 제너레이터(generator)

<img src="/images/linkedlist1.png" width="50%" height="50%">


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

<img src="/images/linkedlist2.png" width="50%" height="50%">


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

<img src="/images/linkedlist3.png" width="50%" height="50%">
