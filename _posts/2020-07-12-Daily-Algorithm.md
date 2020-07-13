---
title: Daily Algorithm
key: 20200712
tags: Leetcode algorithm 
---

# [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/)
```python
class Solution:
    def reverseBits(self, n: int) -> int:
        ret, power = 0, 31
        while n:
            ret += (n&1) << power
            n >> 1
            power -= 1
        return ret

```

```python
class Solution:
    def reverseBits(self, n: int) -> int:
        res, mask = 0, 1
        for _ in range(32):
            res <<= 1
            res |= n & mask
            n >>= 1
        return res
```