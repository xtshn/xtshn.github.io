---
title: Daily Algorithm
key: 20200710
tags: Leetcode algorithm 
---
# [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
```python
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        dummy = ListNode(float('-inf))
        dummy = head
        slow = fast = dummy
        for _ in range(n):
            fast = fast.next
        while fast.next: # if it was fast, then it would end up at the one needed to be deleted. Then the slow pointer would lose the reference from the previous one. 
            slow = slow.next
            fast = fast.next
        slow.next = slow.next.next
        return dummy.next        
```

# [430. Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val, prev, next, child):
        self.val = val
        self.prev = prev
        self.next = next
        self.child = child
"""

class Solution:
    def flatten(self, head: 'Node') -> 'Node':
        curr = head
        stack =[]

        while head:
            if head.child:
                if head.next:
                    stack.append(head.next)
                head.next = head.child
                head.next.prev = head
                head.child = None
            elif not head.next and stack:
                head.next = stack.pop()
                head.next.prev = head
            head = head.next
        return temp
```

# [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        curr = head
        prev = None
        while curr:
            curr.next, prev, curr = prev, curr, curr.next
        return prev
```

# [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)

```python
    # Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeElements(self, head: ListNode, val: int) -> ListNode:
        dummy = ListNode(float('-inf))
        dummy.next = head
        prev, curr = dummy, dummy.next

        while curr:
            if curr == val:
                prev.next = curr.next
            else:
                prev = curr
            curr = curr.next
        return dummy.next
```