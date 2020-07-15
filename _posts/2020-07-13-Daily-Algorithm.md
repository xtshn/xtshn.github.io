---
title: Daily Algorithm
key: 20200713
tags: Leetcode algorithm 
---

# [100. Same Tree](https://leetcode.com/problems/same-tree/)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if not q and not p:
            return True
        
        if p is not None and q is not None:
            return p.val = q.val and self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)

        return False
```

# [707. Design Linked List](https://leetcode.com/problems/design-linked-list/)

```python
class Node:
	def __init__(self, val):
		self.val = val
		self.next = None
		self.prev = None

class MyLinkedList:

	def __init__(self):
		"""
		Initialize your data structure here.
		"""
		self.size = 0
		self.tail = None
		self.head = None


	def get(self, index: int) -> int:
		"""
		Get the value of the index-th node in the linked list. If the index is invalid, return -1.
		"""
		if index >= self.size or index < 0:
			return -1
		else:
			node = self.getIdxNode(index)
			return node.val


	def addAtHead(self, val: int) -> None:
		"""
		Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
		"""
		newNode = Node(val)
		if self.head is None:
			self.head = newNode
			self.tail = newNode
		else:
			#this also covers the case when size == 1, just think
			newNode.next = self.head
			self.head.prev = newNode
			self.head = newNode
		self.size += 1


	def addAtTail(self, val: int) -> None:
		"""
		Append a node of value val to the last element of the linked list.
		"""
		newNode = Node(val)
		if self.head is None:
			self.head = newNode
			self.tail = newNode
		else:
			newNode.prev = self.tail
			self.tail.next = newNode
			self.tail = newNode
		self.size += 1

	def addAtIndex(self, index: int, val: int) -> None:
		"""
		Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted.
		"""
		if index <= 0:
			#add at head
			self.addAtHead(val)
		elif index == self.size:
			#add at tail
			self.addAtTail(val)
		elif index <= self.size - 1:
			newNode = Node(val)
			idxNode = self.getIdxNode(index)
			#set pointers for newNode
			newNode.prev = idxNode.prev
			newNode.next = idxNode

			#update idxNode.prev
			idxNode.prev.next = newNode

			#idxNode
			idxNode.prev = newNode

			self.size += 1

	def deleteAtIndex(self, index: int) -> None:
		"""
		Delete the index-th node in the linked list, if the index is valid.
		"""
		if index < 0 or index >= self.size:
			return

		if index == 0:
			#delete from head
			self.deleteHead()
		elif index == self.size - 1:
			# delete from tail
			self.deleteTail()
		else:
			idxNode = self.getIdxNode(index)
			idxNode.prev.next = idxNode.next
			idxNode.next.prev = idxNode.prev
			del idxNode

		self.size -= 1

	def getIdxNode(self, idx):
		tmp = self.head
		while idx > 0:
			tmp = tmp.next
			idx -= 1

		return tmp 

	def deleteHead(self):
		oldHead = self.head
		if self.size == 1:
			self.head == None
			self.tail == None
		else:    
			self.head.next.prev = None
			self.head = self.head.next
		del oldHead

	def deleteTail(self):
		oldTail = self.tail
		if self.size == 1:
			self.head == None
			self.tail == None
		else:
			self.tail.prev.next = None
			self.tail = self.tail.prev
		del oldTail
        
# Your MyLinkedList object will be instantiated and called as such:
# obj = MyLinkedList()
# param_1 = obj.get(index)
# obj.addAtHead(val)
# obj.addAtTail(val)
# obj.addAtIndex(index,val)
# obj.deleteAtIndex(index)
```

# [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        curr = NodeList(0) = dummy

        while l1 and l2:
            if l1.val < l2.val:
                curr.next = l1
                l1 = l1.next
            else:
                curr.next = l2
                l2 = l2.next
            curr = curr.next
        curr.next = l1 or l2
```

# [2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        carry = 0
        dummy = NodeList(0)
        p = dummy

        while l1 and l2:
            p.next = ListNode((l1.val + l2.val + carry)%10)
            carry = (l1.val+l2.val)//10
            l1 = l1.next
            l2 = l2.next
            p = p.next
        
        if l1:
            while l1:
                p.next = ListNode((l1.val + carry)%10)
                carry = (l1.val+carry)//10
                l1 = l1.next
                p = p.next
        
        if l2:
            while l2:
                p.next = ListNode((l2.val+carry)%10)
                carry = (l2.val+carry)//10
                l2 = l2.next
                p = p.next

        if carry == 1:
            p.next = ListNode(1)
        
        return dummy.next

```

# [138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, x: int, next: 'Node' = None, random: 'Node' = None):
        self.val = int(x)
        self.next = next
        self.random = random
"""

class Solution:
    def copyRandomList(self, head: 'Node') -> 'Node':
        dic = dict()
        m = n = head

        while m:
            dic[m] = Node(m.val)
            m = m.next
        while n:
            dic[n].next = dic.get(n.next)
            dic[n].random = dic.get(n.random)
            n = n.next
        return dic.get(head) # don\t really understand... 
```