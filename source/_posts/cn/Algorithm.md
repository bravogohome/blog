---
title: 算法笔记 Algorithm Note
catalog: true
lang: cn
date: 2021-11-08 11:04:24
subtitle: 力扣每日一题
header-img: /img/header_img/nier.png
tags:
- Algorithm
categories:
- Note
- Algorithm
sticky: 999
---
## 猜数字游戏
leetcode链接：<https://leetcode-cn.com/problems/bulls-and-cows>

> 你在和朋友一起玩 猜数字（Bulls and Cows）游戏，该游戏规则如下：  
> 写出一个秘密数字，并请朋友猜这个数字是多少。朋友每猜测一次，你就会给他一个包含下述信息的提示：  
> + 猜测数字中有多少位属于数字和确切位置都猜对了（称为 "Bulls", 公牛），
> + 有多少位属于数字猜对了但是位置不对（称为 "Cows", 奶牛）。也就是说，这次猜测中有多少位非公牛数字可以通过重新排列转换成公牛数字。
>   
> 给你一个秘密数字 secret 和朋友猜测的数字 guess ，请你返回对朋友这次猜测的提示。  
> 提示的格式为 "xAyB" ，x 是公牛个数， y 是奶牛个数，A 表示公牛，B 表示奶牛。  
>  请注意秘密数字和朋友猜测的数字都可能含有重复数字。

### 解题思路
根据题意，对于公牛，需要满足数字和确切位置都猜对。我们可以遍历` secret `和` guess `，统计满足` secret[i]=guess[i] `的下标个数，即为公牛的个数。

对于奶牛，需要满足数字猜对但是位置不对。我们可以在` guess[i] ≠ secret[i] `时，分别统计` secret `和` guess `的各个字符的出现次数，记在两个长度为` 10 `的数组中。根据题目所述的「这次猜测中有多少位非公牛数字可以通过重新排列转换成公牛数字」，由于多余的数字无法匹配，对于0到9的每位数字，应取其在` secret `和` guess `中的出现次数的最小值。将每位数字出现次数的最小值累加，即为奶牛的个数。

#### 复杂度分析
+ 时间复杂度：` O(N) `，其中` N `是字符串 ` secret ` 的长度。

+ 空间复杂度：` O(C) `。需要常数个空间统计字符出现次数，由于我们统计的是数字字符，因此` C=10 `。  

### 题解
#### Python
```python
# 使用两个数组两次遍历
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        bulls = 0
        secretCount, guessCount = [0] * 10, [0] * 10
        for s, g in zip(secret, guess):
            if s == g:
                bulls += 1
            else:
                secretCount[int(s)] += 1
                guessCount[int(g)] += 1
        cows = sum(min(s, g) for s, g in zip(secretCount, guessCount))
        return f'{bulls}A{cows}B'
```
```python
# 改进版：使用一个数组一次遍历
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        bulls, cows = 0, 0
        arr = [0] * 10
        for i in range(len(secret)):
            if secret[i] == guess[i]:
                bulls += 1
            else:
                # 小于0说明之前guess中出现过相同的字符
                if arr[int(secret[i])] < 0:
                    cows += 1
                arr[int(secret[i])] += 1
                # 大于0说明之前secret中出现过相同的字符
                if arr[int(guess[i])] > 0:
                    cows += 1
                arr[int(guess[i])] -= 1
        return f'{bulls}A{cows}B'
```
#### C#
```csharp
// 使用两个数组两次遍历
public class Solution {
    public string GetHint(string secret, string guess) {
        int bulls = 0;
        int[] secretCount = new int[10];
        int[] guessCount = new int[10];
        for (int i = 0; i < secret.Length; ++i) {
            if (secret[i] == guess[i]) {
                ++bulls;
            } else {
                ++secretCount[secret[i] - '0'];
                ++guessCount[guess[i] - '0'];
            }
        }
        int cows = 0;
        for (int i = 0; i < 10; ++i) {
            cows += Math.Min(secretCount[i], guessCount[i]);
        }
        return $"{bulls}A{cows}B";
    }
}
```
```csharp
// 改进版：使用一个数组一次遍历
public class Solution {
    public string GetHint(string secret, string guess) {
        int bulls = 0;
        int cows = 0;
        int[] arr = new int[10];
        for (int i = 0; i < secret.Length; i++){
            if (secret[i] == guess[i]) ++bulls;
            else{
                // 小于0说明之前guess中出现过相同的字符
                if (arr[secret[i]-'0']++ < 0) cows++;
                // 大于0说明之前secret中出现过相同的字符
                if (arr[guess[i]-'0']-- > 0) cows++;
            }
        }
        return $"{bulls}A{cows}B";
    }
}
```