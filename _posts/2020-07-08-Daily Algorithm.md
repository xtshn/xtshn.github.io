---
title: Daily Algorithm
key: 20200708
tags: Leetcode algorithm 
---

# [15. 3Sum](https://leetcode.com/problems/3sum/)

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        results = []
        n = len(nums)
        nums.sort()
        
        for i in range(n-2):
            if nums[0] + nums[1] + nums[2] > 0:
                break 
            if nums[i] + nums[n-1] + nums[n-2] <0:
                continue
            if i>0 and nums[i] == nums[i-1]:
                continue
            l = i+1
            r = n-1 
            while l < r:
                tmp = nums[i] + nums[l] + nums[r]
                    if tmp == 0:
                        results.append([nums[i], nums[l], nums[r]])
                        while l+1< r and nums[l] == nums[l+1]:
                            l += 1
                        l +=1
                        while l< r-1 and nums[r] == nums[r-1]:
                            r -=1
                        r -=1
                    elif tmp<0:
                        l +=1
                    else:
                        r -=1
        return results
```

# [1051. Height Checker](https://leetcode.com/problems/height-checker/)
```python
class Solution:
    def heightChecker(self, heights: List[int]) -> int:
        return sum(h1!=h2 for h1, h2 in zip(heights, sorted(heights)))
```

# [414. Third Maximum Number](https://leetcode.com/problems/third-maximum-number/)
```python
class Solution:
    def thirdMax(self, nums: List[int]) -> int:
        nums = sorted(list(set(nums)))
       
        if len(nums)<3:
            return max(nums)
        else:
            return nums[-3]
        
```

# [448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)
```python
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        marked = set(nums)
        return [i for i in range(1, len(nums)+1) if i not in marked]
```

```python

class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        for n in nums:
            a = abs(n) - 1
            if nums[a] > 0: nums[a] *= -1
        return [i+1 for i in range(len(nums)) if nums[i] > 0]
```