---
title: Daily Algorithm
key: 20200709
tags: Leetcode algorithm 
---

# [662. Maximum Width of Binary Tree](https://leetcode.com/problems/maximum-width-of-binary-tree/)
```python 
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def widthOfBinaryTree(self, root: TreeNode) -> int:
        min_hash={}
        max_hash={}

    def dfs(node, level, index):
        if node is None:
            return 
        if level in min_hash:
            min_hash[level] = min(min_hash[level], index)
        else:
            min_hash[level] = index
        if level in max_hash:
            max_hash[level] = max(max_hash[level], index)
        else:
            max_hash[level] = index
        best = max(best, max_hash[level] - min_hash[level]+1)
        
        dfs(node.left, level + 1, index*2+1)
        dfs(node.right, level + 1, index*2+2)
    dfs(root, 0, 0)
    return best

```

```python
class Solution(object):
    def widthOfBinaryTree(self, root):
        self.res = 1
        self.dfs(root, 0, 1, [])
        return self.res

    def dfs(self, root, level, index, start):
        if not root: return 
        if len(start) == level:
            start.append(index)
        else:
            self.res = max(self.res, index - start[level] + 1)
        self.dfs(root.left, level + 1, index * 2, start)
        self.dfs(root.right, level + 1, index * 2 + 1, start)
```


# [707. Design Linked List](https://leetcode.com/problems/design-linked-list/)

```python
class Node(object):

    def __init__(self, val):
        self.val = val
        self.next = None

class MyLinkedList(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.head = None
        self.size = 0

    def get(self, index):
        """
        Get the value of the index-th node in the linked list. If the index is invalid, return -1.
        :type index: int
        :rtype: int
        """
        if index < 0 or index >= self.size:
            return -1

        if self.head is None:
            return -1

        curr = self.head
        for i in range(index):
            curr = curr.next
        return curr.val

    def addAtHead(self, val):
        """
        Add a node of value val before the first element of the linked list.
        After the insertion, the new node will be the first node of the linked list.
        :type val: int
        :rtype: void
        """
        node = Node(val)
        node.next = self.head
        self.head = node

        self.size += 1

    def addAtTail(self, val):
        """
        Append a node of value val to the last element of the linked list.
        :type val: int
        :rtype: void
        """
        curr = self.head
        if curr is None:
            self.head = Node(val)
        else:
            while curr.next is not None:
                curr = curr.next
            curr.next = Node(val)

        self.size += 1

    def addAtIndex(self, index, val):
        """
        Add a node of value val before the index-th node in the linked list.
        If index equals to the length of linked list, the node will be appended to the end of linked list.
        If index is greater than the length, the node will not be inserted.
        :type index: int
        :type val: int
        :rtype: void
        """
        if index < 0 or index > self.size:
            return

        if index == 0:
            self.addAtHead(val)
        else:
            curr = self.head
            for i in range(index - 1):
                curr = curr.next
            node = Node(val)
            node.next = curr.next
            curr.next = node

            self.size += 1

    def deleteAtIndex(self, index):
        """
        Delete the index-th node in the linked list, if the index is valid.
        :type index: int
        :rtype: void
        """
        if index < 0 or index >= self.size:
            return

        curr = self.head
        if index == 0:
            self.head = curr.next
        else:
            for i in range(index - 1):
                curr = curr.next
            curr.next = curr.next.next

        self.size -= 1
```

# [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True
        return False

```

```python
class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        seen = set()
        while head:
            if head in seen:
                return True
            else:
                seen.add(head)
            head = head.next
        return False
```

# 142. Linked List Cycle II(https://leetcode.com/problems/linked-list-cycle-ii/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: ListNode) -> ListNode:
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                break
                        
        if not fast or not fast.next:
            return None

        slow = head 
        while slow != fast:
            slow = slow.next
            fast = fast.next
        return slow
```
```python
class Solution:
    def detectCycle(self, head: ListNode) -> ListNode:
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                while head:
                    if head = slow:
                        return head
                    head = head.next
                    slow = slow.next
        return None
```


# [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        p1 = headA
        p2 = headB
        while p1!=p2:
            if not p1:
                p1 = headB
            else:
                p1 = p1.next
            if not p2:
                p2= headA
            else:
                p2 = p2.next
        return p1
```
