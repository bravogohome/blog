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

