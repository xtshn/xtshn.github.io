---
title: Daily Algorithm and Priority Queues
key: 20200707
tags: Leetcode algorithm 
---

# [463. Island Perimeter](https://leetcode.com/problems/island-perimeter/)

```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
     result = 0
     for i in range(len(grid)):
        for j in range(len(grid[0])):
            if grid[i][j] == 1:
                result += 4
                if i>0 and grid[i-1][j] == 1:
                    result -= 2
                if j>0 and grid[i][j-1] == 1:
                    result -= 2
    return result
```

# [941. Valid Mountain Array](https://leetcode.com/problems/valid-mountain-array/) 
```python
class Solution:
    def validMountainArray(self, A: List[int]) -> bool:
        i = 0
        N = len(A)

        while i<N and A[i] < A[i-1]:
            i+=1
        # A.length >= 3 
        if i==0 or i==N-1:
            return False
        
        while i<N and A[i] > A[i+1]:
            i+=1
        # return boolean
        # True if i go through the whole list, otherwise break the loop above 
        return i == N - 1

```

# [1299. Replace Elements with Greatest Element on Right Side](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/)
```python
class Solution:
    def replaceElements(self, arr: List[int]) -> List[int]:
        rightMax = -1
        # if arr would be backward, then range would be len(arr) - 1 
        # OR for i in reversed(range(len(arr))):
        for i in range(len(arr) -1, -1, -1):
            newMax = max(arr[i], rightMax)
            arr[i] = rightMax
            rightMax = newMax
        return arr         
```

# [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        pos = 0
        for i in range(len(nums)):
            if nums[i]: # if true (i!=0) assign value else continue for loop
                nums[pos] = nums[i]
                pos += 1
        for i in range(pos, len(nums)):
            nums[i] = 0
```

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        pos = 0
        for i in range(len(nums)):
            if nums[i] == 0:
                i += 1
            else:
                nums[i], nums[pos] = nums[pos], nums[i]
                i += 1
                pos += 1
        return nums
```

# [905. Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)
```python
class Solution:
    def sortArrayByParity(self, A: List[int]) -> List[int]:
    pos = 0
    # same method as the last one. First condition is the one we will ignore and continue until we find the one we need and swap it to the postion. All we don't need will be added at the end and i is the pointer to go through the list.
    for i in range(len(A)):
        if A[i] % 2 !=0:
            i += 1
        else:
            A[pos], A[i] = A[i], A[pos]
            i +=1
            pos +=1
    return A
```
