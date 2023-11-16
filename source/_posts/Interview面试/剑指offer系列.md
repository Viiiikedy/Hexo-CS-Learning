---
title: 剑指Offer系列
tags: Interview面试
---
在这个系列里面，我主要更新刷剑指Offer的时候的真题记录，推荐刷题时使用**C++**或者**Java**，优先**Java**

## Question 1:Find the duplicate number 
## 题目一：寻找重复数字
```
class Solution:
    def findRepeatNumber(self, nums: List[int]) -> int:
        for i in range(len(nums)):
            # 从头开始遍历数组
            while i != nums[i]:
                # 当前下标i和值nums[i]不相等, 进入/继续内层循环
                j = nums[i]
                if nums[i] == nums[j]:
                    # 前提条件: i!=j, 所以nums[i]和nums[j]是数组的两个数字, 它们值相等, 即为重复数字
                    return nums[i]
                # 交换两个值, 使得nums[j] == j, 这样可以继续循环判断i和新的nums[i]
                nums[i], nums[j] = nums[j], nums[i]
```