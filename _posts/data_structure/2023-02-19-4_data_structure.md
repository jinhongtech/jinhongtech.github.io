---
layout: single
title: "04.큐(Queue)"
categories: 
  - DA
---


- FIFO(First In First Out) 규칙의 순차적 자료구조
- 필수 연산
    - 삽입(enqueue)
    - 삭제(dequeue)

<img src="/images/data_structure/4.queue1.png" width="100%" height="100%">

```python
class Queue:
	def __init__(self):
		self.items = []
		self.front_index = 0

	def enqueue(self, val):
		self.items.append(val)

	def dequeue(self):
		if self.front_index == len(self.items):
			print("Queue is empty")
		else:
			x = self.items[front_index]
			self.front_index += 1
			return x
```

- ex) [Josephus problem](https://en.wikipedia.org/wiki/Josephus_problem)