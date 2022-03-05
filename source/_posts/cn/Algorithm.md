---
title: 算法题库
catalog: true
lang: cn
date: 2021-11-08 11:04:24
subtitle: 力扣每日一题
header-img: /img/header_img/nier.png
tags:
- Algorithm
- Leetcode
categories:
- Note
- Algorithm
sticky: 900
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
#### 模拟
根据题意，对于公牛，需要满足数字和确切位置都猜对。我们可以遍历` secret `和` guess `，统计满足` secret[i]=guess[i] `的下标个数，即为公牛的个数。

对于奶牛，需要满足数字猜对但是位置不对。我们可以在` guess[i] ≠ secret[i] `时，分别统计` secret `和` guess `的各个字符的出现次数，记在两个长度为` 10 `的数组中。根据题目所述的「这次猜测中有多少位非公牛数字可以通过重新排列转换成公牛数字」，由于多余的数字无法匹配，对于0到9的每位数字，应取其在` secret `和` guess `中的出现次数的最小值。将每位数字出现次数的最小值累加，即为奶牛的个数。

##### 复杂度分析
+ 时间复杂度：` O(N) `，其中` N `是字符串 ` secret ` 的长度。
+ 空间复杂度：` O(C) `。需要常数个空间统计字符出现次数，由于我们统计的是数字字符，因此` C=10 `。  

### 题解
#### `Python`
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

#### `C#`
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

-------------------------------------------------------------------

## 猜数字大小Ⅱ
leetcode链接：<https://leetcode-cn.com/problems/guess-number-higher-or-lower-ii/>

> 我们正在玩一个猜数游戏，游戏规则如下：
> + 我从 1 到 n 之间选择一个数字。
> + 你来猜我选了哪个数字。
> + 如果你猜到正确的数字，就会 赢得游戏 。
> + 如果你猜错了，那么我会告诉你，我选的数字比你的 更大或者更小 ，并且你需要继续猜数。
> + 每当你猜了数字 x 并且猜错了的时候，你需要支付金额为 x 的现金。如果你花光了钱，就会 输掉游戏。
> 
> 给你一个特定的数字 n ，返回能够 确保你获胜 的最小现金数，不管我选择那个数字 。


### 解题思路
#### 动态规划

##### 复杂度分析


### 题解
#### `Python`
```python

```

#### `C#`
```csharp

```

-------------------------------------------------------------------

## 检测大写字母
leetcode链接：<https://leetcode-cn.com/problems/detect-capital/>

> 我们定义，在以下情况时，单词的大写用法是正确的：
> + 全部字母都是大写，比如 "USA" 。
> + 单词中所有字母都不是大写，比如 "leetcode" 。
> + 如果单词不只含有一个字母，只有首字母大写， 比如 "Google" 。
> 
> 给你一个字符串 word 。如果大写用法正确，返回 true ；否则，返回 false 。


### 解题思路
#### 

##### 复杂度分析


### 题解
#### `Python`
```python
class Solution:
    def detectCapitalUse(self, word: str) -> bool:
        return word.islower() or word.isupper() or word.istitle()
```

#### `C#`
```csharp

```

-------------------------------------------------------------------

## 键值映射
leetcode链接：<https://leetcode-cn.com/problems/map-sum-pairs/>

> 实现一个 MapSum 类，支持两个方法，insert 和 sum：
> + MapSum() 初始化 MapSum 对象
> + void insert(String key, int val) 插入 key-val 键值对，字符串表示键 key ，整数表示值 val 。如果键 key 已经存在，那么原来的键值对将被替代成新的键值对。
> + int sum(string prefix) 返回所有以该前缀 prefix 开头的键 key 的值的总和。

示例：
> **输入**：  
> ["MapSum", "insert", "sum", "insert", "sum"]  
> [[], ["apple", 3], ["ap"], ["app", 2], ["ap"]]  
> **输出**：  
> [null, null, 3, null, 5]  
> **解释**：  
> MapSum mapSum = new MapSum();   
> mapSum.insert("apple", 3);    
> mapSum.sum("ap");           // return 3 (apple = 3)    
> mapSum.insert("app", 2);      
> mapSum.sum("ap");           // return 5 (apple + app = 3 + 2 = 5)


### 解题思路
#### 暴力扫描
将所有的key-val键值存储，在需要搜索给定前缀的和时，依次搜索所有键值，如果key以prefix为前缀，把对应的val累加并返回。

##### 复杂度分析
+ 时间复杂度： insert操作为`O(1)`。 sum操作为`O(NM)`，其中N是插入的key的数目，M是给定前缀prefix的长度。
+ 空间复杂度： `O(NM)`，其中 NN 是插入的key的数目，MM是字符串key的最大长度。

### 题解
#### `Python`
```python
class MapSum:
    def __init__(self):
        self.mapsum = {}

    def insert(self, key: str, val: int) -> None:
        self.mapsum[key] = val

    def sum(self, prefix: str) -> int:
        sum = 0
        for key in self.mapsum.keys():
            if key.find(prefix) == 0:
            # 或者 key.startswith(prefix):
                sum += self.mapsum[key]
        return sum
```

#### `C#`
```csharp

```

-------------------------------------------------------------------

## 灯泡开关
leetcode链接：<https://leetcode-cn.com/problems/bulb-switcher/>

> 初始时有 n 个灯泡处于关闭状态。第一轮，你将会打开所有灯泡。接下来的第二轮，你将会每两个灯泡关闭一个。  
> 第三轮，你每三个灯泡就切换一个灯泡的开关（即，打开变关闭，关闭变打开）。第 i 轮，你每 i 个灯泡就切换一个灯泡的开关。直到第 n 轮，你只需要切换最后一个灯泡的开关。  
> 找出并返回 n 轮后有多少个亮着的灯泡。
  
示例：  
> ![灯泡开关示例](bulbswitcher.jpg)
> 
> **输入**：n = 3
> **输出**：1 
> **解释**：
> 初始时, 灯泡状态 [关闭, 关闭, 关闭].
> 第一轮后, 灯泡状态 [开启, 开启, 开启].
> 第二轮后, 灯泡状态 [开启, 关闭, 开启].
> 第三轮后, 灯泡状态 [开启, 关闭, 关闭]. 
> 
> 你应该返回 1，因为只有一个灯泡还亮着。



### 解题思路
#### 数学
如果我们将所有的灯泡从左到右依次编号为 1,2,⋯,n，那么可以发现：

在第 i 轮时，我们会将所有编号为 i 的倍数的灯泡进行切换。

因此，对于第 k 个灯泡，它被切换的次数恰好就是 `k 的约数个数`。

如果 k 有偶数个约数，那么最终第 k 个灯泡的状态为暗；如果 k 有奇数个约数，那么最终第 k 个灯泡的状态为亮。

对于 k 而言，如果它有约数 x，那么一定有约数`x/k`。因此只要当 `x^2≠k` 时，约数都是「成对」出现的。这就说明，只有当 k 是「`完全平方数`」时，它才会有奇数个约数，否则一定有偶数个约数。

因此我们只需要找出 1,2,⋯,n 中的完全平方数的个数即可，答案即为"`n的平方根并向下取整`".


##### 复杂度分析
+ 时间复杂度： `O(1)`
+ 空间复杂度： `O(1)`

### 题解
#### `Python`
```python
class Solution:
    # 暴力、n = 10000时超出时间限制
    # def bulbSwitch(self, n: int) -> int:
    #     stats = [1] * n
    #     for i in range(1,n):
    #         for j in range(len(stats)):
    #             if (j+1)%(i+1)==0:
    #                 stats[j]*=-1
    #     return stats.count(1)
    
    # 模拟，n = 9999999时超出时间限制
    # def bulbSwitch(self, n: int) -> int:
    #     stats = set()
    #     for i in range(1,n):
    #         dir = [(i + 1) * x for x in range(1, n // (i + 1) + 1)]
    #         for j in dir:
    #             if j in stats:
    #                 stats.remove(j)
    #             else:
    #                 stats.add(j)
    #     return n-len(stats)

    # 计算变化次数，99999时超出时间限制
    # def bulbSwitch(self, n: int) -> int:
    #     if n < 1: return 0
    #     count = 1
    #     for i in range(1,n):
    #         changetimes = 0  # 变化次数
    #         for j in range(1,(i+1)//2+1):
    #             if (i+1)%j==0:
    #                 changetimes += 1
    #         count += ((changetimes+1)%2)
    #     return count


    # 数学，变化次数为奇数的，最终为暗，为偶数的，变化为亮，只有完全平方数才会变化为亮，最终变为求完全平方数的个数
    def bulbSwitch(self, n: int) -> int:
        return int(sqrt(n))
```

#### `C#`
```csharp

```

-------------------------------------------------------------------

## 最大单词长度乘积
leetcode链接：<https://leetcode-cn.com/problems/maximum-product-of-word-lengths/>

> 给定一个字符串数组 words，找到 length(word[i]) * length(word[j]) 的最大值，并且这两个单词不含有公共字母。你可以认为每个单词只包含小写字母。如果不存在这样的两个单词，返回 0。
  
示例：  
> 
> **输入**：["abcw","baz","foo","bar","xtfn","abcdef"]  
> **输出**：16   
> **解释**：  
> "abcw", "xtfn"  
> 4 * 4 = 16   



### 解题思路
#### 暴力遍历
遍历每一对字符串，如果这对不含有公共字母，则计算length(word[i]) * length(word[j]) 并得到最大值。

##### 复杂度分析
+ 时间复杂度： 
+ 空间复杂度： 

#### 位运算
详见力扣题解：<https://leetcode-cn.com/problems/maximum-product-of-word-lengths/solution/zui-da-dan-ci-chang-du-cheng-ji-by-leetc-lym9/>

### 题解
#### `Python`
```python
def maxProduct(self, words: List[str]) -> int:
    result = 0
    for i in range(len(words)-1):
        wordset = set(words[i])
        # wordset = set()
        # for x in words[i]:
        #     wordset.add(x)
        # 使用上面代码代替时内存消耗会小0.2-0.3MB，原因未知，待以后深掘。
        for j in range(i + 1, len(words)):
            flag = 0
            for x in words[j]:
                if x in wordset:  # 这一对字符含有公共字母
                    flag = 1
                    break
            # 这一对字符不含有公共字母
            if flag == 0 and len(words[i]) * len(words[j]) > result:  # 这一对不含有公共字母
                result = len(words[i]) * len(words[j])
    return result
```

#### `C#`
```csharp

```


-------------------------------------------------------------------


## 各位相加
leetcode链接：<https://leetcode-cn.com/problems/add-digits/>

> 
  
示例：  
> 
> 
> **输入**：num = 38
> **输出**：2 
> **解释**：  
> 各位相加的过程为：   
> 38 --> 3 + 8 --> 11   
> 11 --> 1 + 1 --> 2   
> 由于 2 是一位数，所以返回 2。  
> 


### 解题思路

#### 循环相加

##### 复杂度分析
+ 时间复杂度： 
+ 空间复杂度： 

#### 数学

##### 复杂度分析
+ 时间复杂度： 
+ 空间复杂度： 



### 题解
#### `Python`
```python
class Solution:
    def addDigits(self, num: int) -> int:
        while num >= 10:
            lst = list(map(int,str(num)))  # [int(x) for x in str(num)]
            num = 0
            for n in lst:
                num += n
        return num
```

```python
class Solution:
    def addDigits(self, num: int) -> int:
        # 数学方法
        if num==0 : return 0
        if num%9==0 : return 9
        else : return num%9
```

```python
class Solution:
    def addDigits(self, num: int) -> int:
        # 数学方法2
        if num==0 : return 0
        return (num-1)%9+1
```

#### `C#`
```csharp

```

**********************************

## 构造 K 个回文字符串
leetcode链接：<https://leetcode-cn.com/problems/construct-k-palindrome-strings/>

> 给你一个字符串 s 和一个整数 k 。请你用 s 字符串中 所有字符 构造 k 个非空 回文串 。   
> 如果你可以用 s 中所有字符构造 k 个回文字符串，那么请你返回 True ，否则返回 False 。
  
示例：  
> 
> 
> **输入**：s = "annabelle", k = 2   
> **输出**：true  
> **解释**：  
> 一些可行的构造方案包括："anna" + "elble"，"anbna" + "elle"，"anellena" + "b"  
> 
> 



### 解题思路
#### 

##### 复杂度分析
+ 时间复杂度： 
+ 空间复杂度： 

### 题解
#### `Python`
```python
class Solution:
    def canConstruct(self, s: str, k: int) -> bool:
        if len(s)<k : return False
        m = {x: s.count(x) for x in set(s)}
        i = 0
        for key in m:
            if m[key] % 2 == 1:
                i += 1
        if i>k: return False
        else : return True
```

#### `C#`
```csharp

```

**********************************

## new problem
leetcode链接：<>

> 
  
示例：  
> 
> 
> **输入**：
> **输出**：
> **解释**：
> 
> 



### 解题思路
#### 

##### 复杂度分析
+ 时间复杂度： 
+ 空间复杂度： 

### 题解
#### `Python`
```python

```

#### `C#`
```csharp

```

**********************************