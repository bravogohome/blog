---
title: 算法笔记
catalog: true
lang: cn
date: 2021-11-12 10:09:37
subtitle: Algorithm Note
header-img: /img/header_img/nier.png
tags:
- Algorithm
categories:
- Note
- Algorithm
sticky: 999
---
## 动态规划 Dynamic Programming，DP
动态规划是计算机中解决最优化问题的一种方法

### 理解一
> 首先有一个经典的动态规划问题：  
> 给一个无序的数组，` nums = [1, 5, 2, 4, 3] `，找出其中的` 最长的递增的子序列 `的长度。  
> 
> 我们先使用` 暴力枚举/暴力搜索 ` 列出所有的可能性解：
> > 举例：从1出发的遍历树
> > ![暴力-树](dp1.png)
> 
> > 代码：
> > ```python
> > # 递归
> > def L(nums, i):  # nums为数组，i为开始的下标
> >     if i == len(nums) - 1: # 最后一个数字
> >         return 1
> >     max_len = 1
> >     for j in range(i + 1, len(nums)):
> >         if nums[j] > nums[i]:
> >             max_len = max(max_len, L(nums, j) + 1)
> >     return max_len
> >
> > def length_of_LIS(nums):
> >     return max(L(nums, i) for i in range(len(nums)))
> > ``` 
> > 时间复杂度：` O(n*2^n) `
> 
> 我们发现这个方法中存在重复操作，比如在遍历1-2-4的时候已经计算过一次4的子序列，而之后在遍历1-4的时候又重复计算了一次。  
> 因此我们可以在第一次计算的时候将结果保存下来，之后遍历到相同的节点就不需要重复计算直接将结果返回就可以了。  
> 我们使用一个` 字典（哈希表） `来存放结果 :  
> ```python
> memo = {}
> def L(nums, i):
>     if i in memo:
>         return memo[i]
>     ...
>     memo[i] = max_len
>     return max_len
> ...
> ```
> 由于用到了字典/哈希表来保存计算的中间结果，因此也称之为记忆化搜索（Recursion with Memoization），也就是常说的动态规划是“空间”换“时间”；   
> 也有人叫它“带备忘录的递归”或者“递归树的剪枝（pruning）”  
> 
> 接下来尝试将它改成` 非递归（non-recursive）/ 迭代（iterative）`形式：
> 这样可以更直观地去计算它的时间复杂度，并且避免了递归时候的函数调用开销   
> <!-- TODO: 递归转迭代  -->
> 递归转换迭代的方式，可以查看这篇文章：[递归转迭代](/cn/Algorithm-Note/#递归转迭代)
> 迭代的实现：
> ```python
> def length_of_LIS(nums):
>     n = len(nums)
>     L = [1] * n # 存放运算结果
>     for i in reversed(range(n)):
>         for j in range(i+1, n):
>             if nums[j] > nums[i]:
>                 L[i] = max(L[i], L[j]+1)
>     return max(L)
> ```
> 时间复杂度：` O（N^2） `  
> 
> 可以总结出动态规划的一般思路：  
> 1. 可以简单粗暴的使用穷举法并画出递归树
> 2. 发现其中存在重复操作，使用记忆化搜索/剪枝，尝试用哈希表将数据缓存下来
> 3. 最后可以把递归转化成迭代形式

------------------------------------------------------------------------

### 理解二


### 练习
> 给定一个数组nums，要求找出其中的连续子序列的最大和：  
> > 输入：[3, -4, 2, -1, 2, 6, -5, 4]
> > 输出：9
> > 解释：连续子序列[2, -1, 2, 6]可得其最大和9  
> 
> 题解：(python)
> ```python
>     def maxSubArray(self, nums) -> int:
>        if len(nums) == 0:
>            return 0
>        dp = len(nums) * [0]
>        dp[0] = nums[0]
>        for i in range(1, len(nums)):
>            dp[i] = max(dp[i - 1] + nums[i], nums[i])  # python 中 max 是函数
>        return max(dp)
> ```