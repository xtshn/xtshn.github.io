---
title: Daily Algorithm
key: 20200711
tags: Leetcode algorithm 
---

# [78. Subsets](https://leetcode.com/problems/subsets/)
```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        result = [[]]
        for num in nums:
            results += [curr + [num] for curr in nums]
        return results
```
[solution](https://leetcode.com/problems/subsets/solution/)

# [328. Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/)
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def oddEvenList(self, head: ListNode) -> ListNode:
        if not head:
        return None
        odd = head 
        even = head.next
        evenHead = even
        while even!= None and even.next!= None:
            odd.next = even.next
            odd = odd.next
            even.next = odd.next
            even = even.next
        odd.next = evenHead
        return head

```

# [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        stack = []
        while head:
            stack.append(head.val)
            head = head.next
        return stack = stack[::-1]
``