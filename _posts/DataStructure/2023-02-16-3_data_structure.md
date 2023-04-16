---
layout: single
title: "03.스택(Stack)"
categories: 
  - DataStructure
  - CS
---


- LIFO(Last In First Out)

<img src="/images/data_structure/3.stack1.png" width="80%" height="80%">

- 필수연산
    - 삽입(push)
    - 삭제(pop)

```python
class Stack:
	def __init__(self):
		self.items = []

	def push(self, val):					#O(1)
		self.items.append(val)

	def pop(self):						#O(1)
			try:
				return self.items.pop()
			except:
				print("Stack is empty")

#위는 필수
#----------------------------------------------------------------------
#아래는 필수는 아님

	def top(self):					# 스택 맨위의 값을 리턴  O(1)
		try:
			return self.items[-1]
		except IndexError:
			print("Stack is empty")

	def __len__(self):				# O(1) -> 파이썬 자료구조는 internal count를 통해 요소가 
							# 몇개인지 자체적으로 저장하기 때문에 저장된 값만 리턴하면 되기 때문
		return len(self.items)
```

- ex1) 괄호 맞추기
    - ‘(()())’  → true  , ‘(())))(’ →false
- ex2) 계산기 코드 작성
    - “2 + 3 * 5” → “2” “+” “3” “*” “5” → (2+(3*5)) → 17 출력
    - A + B * C → A B C * +
    - A * B + C → A B * C +
