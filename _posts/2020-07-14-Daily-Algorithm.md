---
title: Daily Algorithm
key: 20200714
tags: Leetcode algorithm 
---

# [1344. Angle Between Hands of a Clock](https://leetcode.com/problems/angle-between-hands-of-a-clock/)

```python
class Solution:
    def angleClock(self, hour: int, minutes: int) -> float:
        h_place = 30*hour + 0.5*minutes
        m_place = 6*minutes
        diff = abs(h_place - m_place)
        return diff if diff < 180 else 360-diff
```