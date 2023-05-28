---
title: Python 爬虫
catalog: true
lang: cn
date: 2022-08-15 22:39:42
subtitle:
header-img: /img/header_img/nier.png
tags:
categories:
---
# 爬虫一

## 爬虫概述

**************************

## 爬虫示例

```python
from urllib.request import urlopen

url = "https://www.baidu.com"

with open("baidu.html",mode="w") as f:
    f.write(urlopen(url).read().decode("utf-8"))
print("Over")
```

*************************

## Web请求过程

在学习爬虫前，我们需要先学习网页的请求原理及过程。

--------------------------------------------------------------

# 爬虫二

## 学习路径

+ HTML基础知识
+ 爬虫四步：获取数据、解析数据、提取数据、存储数据对应的模块与应用
+ 模拟登录，以及定时将爬虫结果发送邮箱
+ 利用协程和scrapy框架优化爬虫效率和稳定性
+ 常见应对反爬虫技巧

> 换行\\n代表【+newline】；退格\\b代表【+backspace】；回车\\r代表【+return】