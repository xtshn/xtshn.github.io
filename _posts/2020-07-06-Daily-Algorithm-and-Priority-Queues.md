---
title: Daily Algorithm and Priority Queues
key: 20200706
tags: Leetcode algorithm PriorityQueues
---

# Priority Queue
A prority queue is a Abstract Data Type (ADT) that operates similar to a normal queus except that each element has a certain priority. The priority of the elements in the priority queue determine the order in which elements are removed from PQ.  
[tutorial](https://www.youtube.com/watch?v=wptevk0bshY)  

#### sidenote
ADT only define how a data structure should be behaved and what methods it should have. but not the details surrounding how those methods are implemented. e.g: Priority Queue is a ADT but heap are one of its methods.  


# [66.Plus one](https://leetcode.com/problems/plus-one/)  

```python
class solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        num = int(''.join(map(str, digits))) + 1
        return [int(i) for i in str(num)]
```

```python
class solution:
    def plusone(self, digits: List[int]) -> List [int]:
    toStr = ''.join(str(e) for e in digits)
    num = int(toStr) + 1
    return [int(e) for e in str(num)]
```

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        # when the last digit is 9, it has to be turn to 0 and the second last digit would be an increment 
        for i in reversed(range(len(digits))):
            if digits[i] == 9:
                digits[i] = 0
            else:
                digit[i] +=1
                return digits
        ### if digits was 999
        digits[0] = 1
        digits.append(0)
        return digits
```




# [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        while m>0 and n>0:
            if nums1[m-1] <= nums2[n-1]:
                nums1[m-1+n] = nums2[n-1]
                n -= 1
            else:
            # swap!!
                nums1[m-1], nums1[m-1+n] = nums1[m-1+n], nums1[m-1]
                m-=1
        if m == 0 and n >0:
            nums1[:n] = nums2[:n]
```

# [27. Remove Element](https://leetcode.com/problems/remove-element/)

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        i, j = 0, len(nums) -1 # two pointers method
        while i<=j:
            if nums[i] == val:
                nums[i] = nums[j]
                j-=1
            else:
                i+=1
        return j+1 # To plus one is because j is index not count
```

# [26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if not nums:
            return 0 
        i = 0
        j = 1
        for j in range(len(nums)):
            if nums[i] != nums[j]:
                i += 1
                nums[i] = nums[j]
            j +=1
        return i + 1

```

# [1346. Check If N and Its Double Exist](https://leetcode.com/problems/check-if-n-and-its-double-exist/)

```python
class Solution:
    def checkIfExist(self, arr: List[int]) -> bool:
        seen = set()
        for i in arr:
            if 2 * i in seen or i%2==0 and i//2 in seen:
                return True
            seen.add(i)
        return False
```