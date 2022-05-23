---
title: MVT 与 MVC 模型
catalog: true
lang: cn
date: 2022-04-18 13:41:47
subtitle:
header-img: /img/header_img/nier.png
tags:
- MVT
- MVC
categories:
- Note
---

## MVC模型

MVC 模式（Model–view–controller）是软件工程中的一种软件架构模式，把软件系统分为三个基本部分：模型（Model）、视图（View）和控制器（Controller）。

MVC 以一种插件式的、松耦合的方式连接在一起。

+ 模型（M）- 编写程序应有的功能，负责业务对象与数据库的映射(ORM)。
+ 视图（V）- 图形界面，负责与用户的交互(页面)。
+ 控制器（C）- 负责转发请求，对请求进行处理。

![mvc模型](mvc.png)

## MVT模型

MTV 模式本质上和 MVC 是一样的，也是为了各组件间保持松耦合关系，只是定义上有些许不同:  

+ M 表示模型（Model）：编写程序应有的功能，负责业务对象与数据库的映射(ORM)。
+ T 表示模板 (Template)：负责如何把页面(html)展示给用户。
+ V 表示视图（View）：负责业务逻辑，并在适当时候调用 Model和 Template。

除了以上三层之外，还需要一个 URL 分发器，它的作用是将一个个 URL 的页面请求分发给不同的 View 处理，View 再调用相应的 Model 和 Template，MTV 的响应模式如下所示：

简易图：
![MTV-Diagram.png](MTV-Diagram.png)
用户操作流程图：
![mvt.png](mvt.png)

解析：

用户通过浏览器向我们的服务器发起一个请求(request)，这个请求会去访问视图函数：

+ a.如果不涉及到数据调用，那么这个时候视图函数直接返回一个模板也就是一个网页给用户。
+ b.如果涉及到数据调用，那么视图函数调用模型，模型去数据库查找数据，然后逐级返回。

视图函数把返回的数据填充到模板中空格中，最后返回网页给用户。
