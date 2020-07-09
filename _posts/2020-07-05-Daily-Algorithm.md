---
title: Daily Algorithm
key: 20200705
tags: Leetcode algorithm
---

# 461. Hamming Distance
[quesiton](https://leetcode.com/problems/hamming-distance/)

### solution 
```python  
    class solution:
        def hammingDistance(self, x: int, y: int) -> int:  
        count = 0

        for _ in range(32):
            if (x&1) != (y&1):
                count +=1
            x>>=1
            y>>=1
        return count
```
  
```python
class solution:
    def hammingDistance(self, x: int, y: int) -> int:
        counts = 0
        result = x^y
        while result>0:
            counts += result & 1
            result >>=1
        return counts
```

# 1089. Duplicate Zeros
[Question](https://leetcode.com/problems/duplicate-zeros/)  
Given a fixed length array arr of integers, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written.

Do the above modifications to the input array in place, do not return anything from your function.  
### solution
```python
class solution:
    def duplicateZeros(self, arr: List[int]) -> None:
        i = 0
        while i < len(arr):
               if arr[i] != 0:
                i+=1
            else:
                arr.insert(i+1,0)
                i+=2
                arr.pop()
```

# 977. Squares of a Sorted Array
[Question](https://leetcode.com/problems/squares-of-a-sorted-array/)  
Given an array of integers A sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.

### solution
```python
class Solution:
    def sortedSquares(self, A: List[int]) -> List[int]:
        N = len(A) 
        i = 0
        # i positive pointer to right; j negative pointer to left
        # find the least negative pointer as the starting point going negatively, which is j
        while A[i]<0 and i<N:
            i+=1
        j = i-1

        #compare squared value between two sides
        ans=[]
        while i<N and j>=0: # remember to count the last(smallest negative value) therefore including 0
            if A[i]**2 < A[j]**2:
                ans.append(A[i]**2)
                i +=1
            else:
                ans.append(A[j]**2)
                j -=1
        # when either side is done or while loop break then two senarios: 1. lefted negative side 2. lefted positive side
        while i<N:
            ans.append(A[i]**2)
            i +=1
        while j>=0:
            ans.append(A[j]**2)
            j -=1
    return ans

```

# 1295. Find Numbers with Even Number of Digits
[Question](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/)  
Given an array nums of integers, return how many of them contain an even number of digits.

### solution
```python
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        result = 0
        for num in nums:
            count = 0
            while num > 0: 
                count +=1
                num = num // 10 # num becomes remaining digits
            if count % 2 ==0:
                result +=1
        return result
```

# 485. Max Consecutive Ones
[Question](https://leetcode.com/problems/max-consecutive-ones/)  
Given a binary array, find the maximum number of consecutive 1s in this array.

### solution
```python
class Solution:
    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        count = 0
        result = 0
        for num in nums:
            if num == 1:
                count +=1
                result = max(count, result)
            else:
                count = 0
        return result
```

