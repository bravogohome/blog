---
title: Django学习笔记
catalog: true
lang: cn
date: 2022-04-18 12:27:30
subtitle: Django note
header-img: /img/header_img/nier.png
sticky: 998
tags: 
- django
categories:
- Note
---

## Django 简介

Python下有许多款不同的 Web 框架。Django是重量级选手中最有代表性的一位。许多成功的网站和APP都基于Django。  
Django 是一个开放源代码的 Web 应用框架，由 Python 写成。  
Django 遵守 BSD 版权，初次发布于 2005 年 7 月, 并于 2008 年 9 月发布了第一个正式版本 1.0 。  

Django 采用了 MVT 的软件设计模式，即模型（Model），视图（View）和模板（Template）。  
使用 Django，只要很少的代码，Python 的程序开发人员就可以轻松地完成一个正式网站所需要的大部分内容，并进一步开发出全功能的 Web 服务 Django 本身基于 MVC 模型，即 Model（模型）+ View（视图）+ Controller（控制器）设计模式，MVC 模式使后续对程序的修改和扩展简化，并且使程序某一部分的重复利用成为可能。

MVC 优势：  

+ 低耦合
+ 开发快捷
+ 部署方便
+ 可重用性高
+ 维护成本低
+ ...

Python 加 Django 是快速开发、设计、部署网站的最佳组合。

特点：  
+ 强大的数据库功能
+ 自带强大的后台功能
+ 优雅的网址

MVC 与 MTV模型的详情请参见：  
[MVC与MVT模型](/cn/mvc-and-mvt)

## Django安装

> ```
> pip3 install Django -i https://pypi.tuna.tsinghua.edu.cn/simple
> ```

### 创建项目

`使用Pycharm创建`

![pycharm创建django应用](Django-env9.png)

`使用命令行创建`

```
django-admin startproject 项目名称
python manage.py startapp 应用名
```

Django项目结构:  
![Django项目结构](Django-env6.png)

+ `manage.py`: 一个实用的命令行工具，可让你以各种方式与该 Django 项目进行交互。
+ mysite/`__init__.py`: 一个空文件，告诉 Python 该目录是一个 Python 包。
+ mysite/`asgi.py`: 一个 ASGI 兼容的 Web 服务器的入口，以便运行你的项目。
+ mysite/`settings.py`: 该 Django 项目的设置/配置。
+ mysite/`urls.py`: 该 Django 项目的 URL 声明; 一份由 Django 驱动的网站"目录"。
+ mysite/`wsgi.py`: 一个 WSGI 兼容的 Web 服务器的入口，以便运行你的项目。

Django应用结构:  
![Django应用结构](Django-env10.png)

### 运行应用

```
python manage.py runserver 0.0.0.0:8000
```

0.0.0.0 让其它电脑可连接到开发服务器，8000 为端口号。如果不说明，那么端口号默认为 8000。

> 注意：要在 manage.py 同级目录执行命令。

或者
![](startapp.png)
![](pycharm01.png)


在浏览器输入你服务器的 ip（这里我们输入本机 IP 地址： <http://127.0.0.1:8000>） 及端口号，如果正常启动，输出结果如下：

![成功界面](django_init.png)

### Hello World

在应用目录的views.py文件输入以下代码:

```py
from django.http import HttpResponse
 
def hello(request):
    return HttpResponse("Hello world ! ")
```

接着，绑定 URL 与视图函数。打开 urls.py 文件，输入：  

```
from django.urls import path
from App01 import views

urlpatterns = [
    path('hello/',views.hello),
]
```

然后通过浏览器打开<http://127.0.0.1:8000/hello>

得到输出结果如下：  

![](hello.png)

#### path() 函数

Django path() 可以接收四个参数，分别是两个必选参数：route、view 和两个可选参数：kwargs、name。

语法格式：
```py
path(route, view, kwargs=None, name=None)
```

+ route: 字符串，表示 URL 规则，与之匹配的 URL 会执行对应的第二个参数 view。
+ view: 用于执行与正则表达式匹配的 URL 请求。
+ kwargs: 视图使用的字典类型的参数。
+ name: 用来反向获取 URL。

Django2. 0中可以使用 re_path() 方法来兼容 1.x 版本中的 url() 方法，一些正则表达式的规则也可以通过 re_path() 来实现 。

```py
from django.urls import include, re_path

urlpatterns = [
    re_path(r'^index/$', views.index, name='index'),
    re_path(r'^bio/(?P<username>\w+)/$', views.bio, name='bio'),
    re_path(r'^weblog/', include('blog.urls')),
    ...
]
```

## Django模板(template)

在上一章节中我们使用 django.http.HttpResponse() 来输出 "Hello World！"。该方式将数据与视图混合在一起，不符合 Django 的 MVC 思想。  
本章节我们将为大家详细介绍 Django 模板的应用，模板是一个文本，用于分离文档的表现形式和内容。

首先我们在templates下新建一个test.html，文件代码如下：  

```html
<h1>{{ test_data }}</h1>
```

接下来我们修改views.py，增加一个新的对象，用于向模板提交数据：  

```py
from django.shortcuts import render
 
def test(request):
    context = dict()
    context['test_data'] = 'Hello World!'
    return render(request, 'test.html', context)
```

```py
from django.urls import path
 
from . import views
 
urlpatterns = [
    path('test/', views.test),
]
```

可以看到，我们这里使用 render 来替代之前使用的 HttpResponse。render 还使用了一个字典 context 作为参数。  
context 字典中元素的键值 hello 对应了模板中的变量 {% raw %} {{ hello }} {% endraw %}。  
再次访问 <http://127.0.0.1:8000/test>

这样我们就完成了使用模板来输出数据，从而实现数据与视图分离。  
接下来我们将具体介绍模板中常用的语法规则。

### 模板语法规则

#### 传值

`变量`

```python
def test(request):
    test = 'test'
    return render(request,'test.html',{'test':test})
```

```html
<p>{{ test }}</p>
```

`列表`

```python
def test(request):
    test_lst = ['1','2','5']
    return render(request,'test.html',{'test_lst':test_lst})
```

```html
<p>{{ test_lst }}</p>  # 取出整个列表
<p>{{ test_lst.1 }}</p>  # 取出列表的第二个元素
```

`字典`

```python
def test(request):
    test_dict = {'test':'test'}
    return render(request,'test.html',{'test_dict':test_dict})
```

```html
<p>{{ test_dict }}</p>   # 显示所有字典
<p>{{ test_dict.test }}</p>  # 取出字典对应的键值
```

#### 过滤器

```html
{{ 变量名 | 过滤器：可选参数 }}
```

模板过滤器可以在变量被显示前修改它，过滤器使用管道字符  
过滤管道可以被`套接` ，既是说，一个过滤器管道的输出又可以作为下一个管道的输入：

有以下几个常用过滤器：  

| 过滤器 | 参数 | 效果 |
| :---: | :-- | :----- |
| `lower` |  | 文档大写转换文本为小写 |
| `upper` |  | 文档小写转换文本为大写 |
| `first` |  | 获取列表的第一个元素 |
| `truncatewords` | "num" | 显示变量的前num个词 |
| `truncatechars` | num | 如果字符串包含的字符总个数多于指定的字符数量，那么会被截断掉后面的部分。截断的字符串将以 ... 结尾。 |
| `addslashes` |  | 添加反斜杠到任何反斜杠、单引号或者双引号前面。 |
| `date` |  | 根据给定格式对一个日期变量进行格式化。格式 `Y-m-d H:i:s`返回 年-月-日 小时:分钟:秒 的格式时间。 |
| `length` |  | 返回变量的长度。适用于字符串和列表。字典返回的是键值对的数量，集合返回的是去重后的长度。 |
| `default` | str | 如果 views 传的变量的值是 false，则使用指定的默认值。false值有：0、0.0、False、0j、""、[]、()、set()、{}、None |
| `filesizeformat` | | 以更易读的方式显示文件的大小（即'13 KB', '4.1 MB', '102 bytes'等）。|
| `safe` |  | 将字符串标记为安全，不需要转义。 |



#### if/else

```js
{% if condition1 %}
   ... display 1
{% elif condition2 %}
   ... display 2
{% else %}
   ... display 3
{% endif %}
```

根据条件判断是否输出。if/else 支持嵌套。

标签{% raw %} {% if %} {% endraw %}接受 and ， or  关键字来对多个变量做判断 ，或者对变量取反（ not )

#### for

标签{% raw %} {% for %} {% endraw %}允许我们在一个序列上迭代。  
与 Python 的 for 语句的情形类似，循环语法是 for X in Y ，Y 是要迭代的序列而 X 是在每一个特定的循环中使用的变量名称。  
每一次循环中，模板系统会渲染在{% raw %} {% for %} 和 {% endfor %} {% endraw %}之间的所有内容。

还可以给标签增加一个 reversed 使得该列表被反向迭代：

```js
{% for athlete in athlete_list reversed %}
...
{% endfor %}
```

遍历字典: 可以直接用字典 .items 方法，用变量的解包分别获取键和值。

```js
{% for i,j in views_dict.items %}
{{ i }}---{{ j }}
{% endfor %}
```

可以通过  `{{forloop}}` 变量获取循环序号。

+ forloop.counter: 顺序获取循环序号，从 1 开始计算
+ forloop.counter0: 顺序获取循环序号，从 0 开始计算
+ forloop.revcounter: 倒序获取循环序号，结尾序号为 1
+ forloop.revcounter0: 倒序获取循环序号，结尾序号为 0
+ forloop.first（一般配合if标签使用）: 第一条数据返回 True，其他数据返回 False
+ forloop.last（一般配合if标签使用）: 最后一条数据返回 True，其他数据返回 False

可选的 {% raw %}{% empty %}{% endraw %} 从句：在循环为空的时候执行（即 in 后面的参数布尔值为 False ）。

```js
{% for i in listvar %}
    {{ forloop.counter0 }}
{% empty %}
    空空如也～
{% endfor %}
```


#### ifequal/ifnotequal

标签{% raw %}{% ifequal var1 var2 %} {% endraw %}比较两个值，当他们相等时，显示在{% raw %} {% ifequal %} 和 {% endifequal %} {% endraw %}之中所有的值。

和 {% raw %}{% if %} {% endraw %}类似， {%raw%}{% ifequal %}{%endraw%} 支持可选的 {%raw%}{% else%}{%endraw%} 标签：

#### 注释

Django 注释使用 {% raw %}{# #}{% endraw %}。

```
{# 这是一个注释 #}
```

#### include

标签{%raw%}{% include %}{%endraw%}允许在模板中包含其它的模板的内容。

下面这个例子包含了 nav.html 模板：

```
{% include "nav.html" %}
```


### csrf_token

csrf_token 用于form表单中，作用是跨站请求伪造保护。  
如果不用 {%raw%}{% csrf_token %}{%endraw%} 标签，在用 form 表单时，要再次跳转页面会报 403 权限错误。  
用了{%raw%}{% csrf_token %}{%endraw%} 标签，在 form 表单提交数据时，才会成功。  

解析：  
> 首先，向服务器发送请求，获取登录页面，此时中间件 csrf 会自动生成一个隐藏input标签，该标签里的 value 属性的值是一个随机的字符串，用户获取到登录页面的同时也获取到了这个隐藏的input标签。  
> 然后，等用户需要用到form表单提交数据的时候，会携带这个 input 标签一起提交给中间件 csrf，原因是 form 表单提交数据时，会包括所有的 input 标签，中间件 csrf 接收到数据时，会判断，这个随机字符串是不是第一次它发给用户的那个，如果是，则数据提交成功，如果不是，则返回403权限错误。

### 自定义标签和过滤器

1、在应用目录下创建 templatetags 目录(与 templates 目录同级，目录名只能是 templatetags)。

```
HelloWorld/
|-- HelloWorld
|   |-- __init__.py
|   |-- __init__.pyc
|   |-- settings.py
...
|-- manage.py
`-- templatetags
`-- templates
```

2、在 templatetags 目录下创建任意 py 文件，如：my\_tags.py。

3、my\_tags.py 文件代码如下：

```py
from django import template

register = template.Library()   #register的名字是固定的,不可改变
```

修改 settings.py 文件的 TEMPLATES 选项配置，添加 libraries 配置：

```py
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR, "/templates",],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
            "libraries":{                          # 添加这边三行配置
                'my_tags':'templatetags.my_tags'   # 添加这边三行配置        
            }                                      # 添加这边三行配置
        },
    },
]
```

4、利用装饰器 @register.filter 自定义过滤器。

注意：装饰器的参数最多只能有 2 个。

```py
@register.filter
def my_filter(v1, v2):
    return v1 * v2
```

5、利用装饰器 @register.simple_tag 自定义标签。

```py
@register.simple_tag
def my_tag1(v1, v2, v3):
    return v1 * v2 * v3
```

6、在使用自定义标签和过滤器前，要在 html 文件 body 的最上方中导入该 py 文件。

```
{% load my_tags %}
```

7、在 HTML 中使用自定义过滤器。

```
{{ 11|my_filter:22 }}
```

8、在 HTML 中使用自定义标签。

```
{% my_tag1 11 22 33 %}
```

9、语义化标签

在该 py 文件中导入 mark_safe。

```py
from django.utils.safestring import mark_safe
```

定义标签时，用上 mark\_safe 方法，令标签语义化，相当于 jQuery 中的 html() 方法。  
和前端HTML文件中的过滤器 safe 效果一样。

```py
@register.simple_tag
def my_html(v1, v2):
    temp_html = "<input type='text' id='%s' class='%s' />" %(v1, v2)
    return mark_safe(temp_html)
```

在HTML中使用该自定义标签，在页面中动态创建标签。

```
{% my_html "zzz" "xxx" %}
```

### 配置静态文件

1、在项目根目录下创建 statics 目录。

2、在 settings 文件的最下方配置添加以下配置：

```
STATIC_URL = '/static/' # 别名 
STATICFILES_DIRS = [ 
    os.path.join(BASE_DIR, "statics"), 
]
```

3、在 statics 目录下创建 css 目录，js 目录，images 目录，plugins 目录， 分别放 css文件，js文件，图片，插件。

4、把 bootstrap 框架放入插件目录 plugins。

5、在 HTML 文件的 head 标签中引入 bootstrap。

注意：此时引用路径中的要用配置文件中的别名 static，而不是目录 statics。

```md
<link rel="stylesheet" href="/static/plugins/bootstrap-3.3.7/dist/css/bootstrap.css">
```

在模板中使用需要加入{%raw%} {% load static %} {%endraw%}代码，以下实例我们从静态目录中引入图片。

```
{% load static %}
<img src="{% static 'images/logo.png' %}" alt="logo">
```

### 模板继承

模板可以用继承的方式来实现复用，减少冗余内容。  
网页的头部和尾部内容一般都是一致的，我们就可以通过模板继承来实现复用。  
父模板用于放置可重复利用的内容，子模板继承父模板的内容，并放置自己的内容。  

`父模板`

标签 block...endblock: 父模板中的预留区域，该区域留给子模板填充差异性的内容，不同预留区域名字不能相同。

```
{% block 名称 %} 
预留给子模板的区域，可以设置设置默认内容
{% endblock 名称 %}
```

`子模板`

子模板使用标签 extends 继承父模板：

```
{% extends "父模板路径"%} 
```

子模板如果没有设置父模板预留区域的内容，则使用在父模板设置的默认内容，当然也可以都不设置，就为空。

子模板设置父模板预留区域的内容：

```
{ % block 名称 % }
内容 
{% endblock 名称 %}
```


接下来我们先创建之前项目的 templates 目录中添加 base.html 文件，代码如下：

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Title</title>
</head>
<body>
    <h1>Hello World!</h1>
    <p>Django 测试。</p>
    {% block mainbody %}
       <p>original</p>
    {% endblock %}
</body>
</html>
```

以上代码中，名为 mainbody 的 block 标签是可以被继承者们替换掉的部分。   
所有的{%raw%} {% block %} {%endraw%}标签告诉模板引擎，子模板可以重载这些部分。   
我们使用ex.html 继承 base.html，并替换特定 block，ex.html 修改后的代码如下：  

```html
{%extends "base.html" %}
 
{% block mainbody %}
<p>继承了 base.html 文件</p>
{% endblock %}
```

## Django模型model

### Django ORM

Django 模型使用自带的 ORM。  
对象关系映射（Object Relational Mapping，简称 ORM ）用于实现面向对象编程语言里不同类型系统的数据之间的转换。  
ORM 在业务逻辑层和数据库层之间充当了桥梁的作用。   
ORM 是通过使用描述对象和数据库之间的映射的元数据，将程序中的对象自动持久化到数据库中。  

![django-orm](django-orm1.png)

使用 ORM 的好处：

+ 提高开发效率。
+ 不同数据库可以平滑切换。

使用 ORM 的缺点：

+ ORM 代码转换为 SQL 语句时，需要花费一定的时间，执行效率会有所降低。
+ 长期写 ORM 代码，会降低编写 SQL 语句的能力。

ORM 解析过程:

+ 1、ORM 会将 Python 代码转成为 SQL 语句。
+ 2、SQL 语句通过 pymysql 传送到数据库服务端。
+ 3、在数据库中执行 SQL 语句并将结果返回。

ORM 对应关系表：  
![ORM 对应关系表](orm-object.png)

### 数据库配置

见[mysql](/cn/mysql)和[Python操作MySQL](/cn/Python-Note/#Python操作MySQL)

首先先创建一个mysql数据库( ORM 无法操作到数据库级别，只能操作到数据表)  
例如我们创建了一个testdb数据库：  

```sql
create database testdb default charset=utf8;   
```

接着我们在项目的 settings.py 文件中找到 DATABASES 配置项，将其信息修改为：

```py
DATABASES = { 
    'default': 
    { 
        'ENGINE': 'django.db.backends.mysql',    # 数据库引擎
        'NAME': 'testdb', # 数据库名称
        'HOST': '127.0.0.1', # 数据库地址，本机 ip 地址 127.0.0.1 
        'PORT': 3306, # 端口 
        'USER': 'root',  # 数据库用户名
        'PASSWORD': 'xxxxxx', # 数据库密码
    }  
}
```

> 如果你使用了 Python2.x 版本这里添加了中文注释，那么你需要在 HelloWorld/settings.py 文件头部添加 `# -*- coding: UTF-8 -*-`。

上面包含数据库名称和用户的信息，它们与 MySQL 中对应数据库和用户的设置相同。Django 根据这一设置，与 MySQL 中相应的数据库和用户连接起来。  
接下来，告诉 Django 使用 pymysql 模块连接 mysql 数据库：

```py
# 在与 settings.py 同级目录下的 __init__.py 中引入模块和进行配置
import pymysql
pymysql.install_as_MySQLdb()
```

### 定义模型

创建 APP:  

Django 规定，如果要使用模型，必须要创建一个 app。

我们修改 app02/models.py 文件，代码如下：

```py
# models.py
from django.db import models
 
class Test(models.Model):
    name = models.CharField(max_length=20)
```

以上的类名代表了数据库表名，且继承了models.Model，类里面的字段代表数据表中的字段(name)，数据类型则由CharField（相当于varchar）、DateField（相当于datetime）， max_length 参数限定长度。

在命令行中运行：

```bash
$ python3 manage.py migrate   # 创建表结构

$ python3 manage.py makemigrations TestModel  # 让 Django 知道我们在我们的模型有一些变更
$ python3 manage.py migrate TestModel   # 创建表结构
```

你的数据表就创建好了。

```
Migrations for 'app02':
  app02\migrations\0001_initial.py
    - Create model Test

Operations to perform:
  Apply all migrations: app02
Running migrations:
  Applying app02.0001_initial... OK
```

表名组成结构为：应用名_类名（如：app02_test）

> 注意：尽管我们没有在 models 给表设置主键，但是 Django 会自动添加一个 id 作为主键。

### 数据库操作

接下来我们在 HelloWorld 目录中添加 testdb.py 文件（下面介绍），并修改 urls.py：

```python
from django.urls import path
 
from . import views,testdb
 
urlpatterns = [
    path('runoob/', views.runoob),
    path('testdb/', testdb.testdb),
]
```

#### 添加数据

添加数据需要先创建对象，然后再执行 save 函数，相当于SQL中的INSERT：  

```python
# -*- coding: utf-8 -*-
 
from django.http import HttpResponse
 
from app02.models import Test
 
# 数据库操作
def testdb(request):
    test1 = Test(name='name1')
    test1.save()
    return HttpResponse("<p>数据添加成功！</p>")
```

访问 <http://127.0.0.1:8000/testdb> 就可以看到数据添加成功的提示。

#### 获取数据

Django提供了多种方式来获取数据库的内容

修改testdb如下代码所示：

```python
# -*- coding: utf-8 -*-
 
from django.http import HttpResponse
 
from app02.models import Test
 
# 数据库操作
def testdb(request):
    # 初始化
    response = ""
    
    # 通过objects这个模型管理器的all()获得所有数据行，相当于SQL中的SELECT * FROM
    list = Test.objects.all()

    # 输出所有数据
    for var in list:
        response += var.name + " "

    return HttpResponse("<p>" + response + "</p>")
```

Test.objects是Test的模型管理器，其下拥有些方法方便我们进行操作。

`all`

all()可以获得所有数据行，相当于SQL中的`SELECT * FROM`。  
这个函数返回一个QuerySet[T].

`filter`

filter()相当于SQL中的WHERE，可设置条件过滤结果，函数返回一个QuerySet[T]。例如：  

```py
result = Test.objects.filter(id=1) 
```

`get`

get()用于获取单个对象，例如：  

```py
result = Test.objects.get(id=1)
```

`order_by`

order_by()函数用于数据排序，作用等同sql语句的ORDER BY.

```py
Test.objects.order_by("id")
```


> 上面的方法可以连锁使用：  
> ```py
> Test.objects.filter(name="name1").order_by("id")
> ```
> 
> 返回的结果集还可以使用切片截取限制，相当于SQL 中的 OFFSET 0 LIMIT 2;
> result[0:2]


#### 更新数据

修改数据可以使用 save() 或 update():

```python
# -*- coding: utf-8 -*-
 
from django.http import HttpResponse
 
from TestModel.models import Test
 
# 数据库操作
def testdb(request):
    # 修改其中一个id=1的name字段，再save，相当于SQL中的UPDATE
    test1 = Test.objects.get(id=1)
    test1.name = 'Google'
    test1.save()
    
    # 另外一种方式
    #Test.objects.filter(id=1).update(name='Google')
    
    # 修改所有的列
    # Test.objects.all().update(name='Google')
    
    return HttpResponse("<p>修改成功</p>")
```

#### 删除数据

删除数据库中的对象只需调用该对象的delete()方法即可：   

```python
# -*- coding: utf-8 -*-
 
from django.http import HttpResponse
 
from TestModel.models import Test
 
# 数据库操作
def testdb(request):
    # 删除id=1的数据
    test1 = Test.objects.get(id=1)
    test1.delete()
    
    # 另外一种方式
    # Test.objects.filter(id=1).delete()
    
    # 删除所有数据
    # Test.objects.all().delete()
    
    return HttpResponse("<p>删除成功</p>")
```


## Django表单form

HTML表单是网站交互性的经典方式。 本章将介绍如何用Django对用户提交的表单数据进行处理。

### HTTP请求

HTTP协议以"请求－回复"的方式工作。客户发送请求时，可以在请求中附加数据。服务器通过解析请求，就可以获得客户传来的数据，并根据URL来提供特定的服务。

#### Get方法

我们在之前的项目中创建一个 search.py 文件，用于接收用户的请求：  

```python
from django.http import HttpResponse
from django.shortcuts import render
# 表单
def search_form(request):
    return render(request, 'search_form.html')
 
# 接收请求数据
def search(request):  
    request.encoding='utf-8'
    if 'q' in request.GET and request.GET['q']:
        message = '你搜索的内容为: ' + request.GET['q']
    else:
        message = '你提交了空表单'
    return HttpResponse(message)
```

在模板目录 templates 中添加 search_form.html 表单：

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>search</title>
</head>
<body>
    <form action="/search/" method="get">
        <input type="text" name="q">
        <input type="submit" value="搜索">
    </form>
</body>
</html>
```

同时修改urls.py规则。

访问地址 <http://127.0.0.1:8000/search-form/> 并搜索，可以看到get请求进行的表单传值结果。

#### Post方法

上面我们使用了GET方法。视图显示和请求处理分成两个函数处理。  
提交数据时更常用POST方法。我们下面使用该方法，并用一个URL和处理函数，同时显示视图和处理请求。  

我们在 templates 创建 post.html：

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Title</title>
</head>
<body>
    <form action="/search_post/" method="post">
        {% csrf_token %}
        <input type="text" name="q">
        <input type="submit" value="搜索">
    </form>
 
    <p>{{ rlt }}</p>
</body>
</html>
```

在模板的末尾，我们增加一个 rlt 记号，为表单处理结果预留位置。  
表单中还有一个{% raw %}{% csrf_token %}{% endraw %}的标签。csrf 全称是 Cross Site Request Forgery。这是Django提供的防止伪装提交请求的功能。POST 方法提交的表格，必须有此标签。  

在app目录下新建 search2.py 文件并使用 search_post 函数来处理 POST 请求：

```python
# -*- coding: utf-8 -*-
 
from django.shortcuts import render
from django.views.decorators import csrf
 
# 接收POST请求数据
def search_post(request):
    ctx ={}
    if request.POST:
        ctx['rlt'] = request.POST['q']
    return render(request, "post.html", ctx)
```

记得同时修改urls规则。  
最后访问 <http://127.0.0.1:8000/search-post/>.

### Request对象

HttpRequest对象包含当前请求URL的一些信息：  

<table>
<thead>
<tr>
<th style = "text-align : center">
属性
</th>
<th style = "text-align : center">
描述
</th>
</tr>
</thead>

<tbody>

<tr>
<td style = "text-align : center">
path
</td>
<td>
请求页面的全路径,不包括域名—例如, "/hello/"。
</td>
</tr>

<tr>
<td style = "text-align : center">
method
</td>
<td>
请求中使用的HTTP方法的字符串表示。全大写表示。例如:

```py
if request.method == 'GET':
    do_something()
elif request.method == 'POST':
    do_something_else()
```

</td>
</tr>

<tr>
<td style = "text-align : center">
GET
</td>
<td>

包含所有HTTP GET参数的类字典对象。参见[QueryDict](#querydict对象)文档。
</td>
</tr>

<tr>
<td style = "text-align : center">
POST
</td>
<td>

包含所有HTTP POST参数的类字典对象。参见[QueryDict](#QueryDict对象) 文档。<br>
服务器收到空的POST请求的情况也是有可能发生的。也就是说，表单form通过HTTP POST方法提交请求，但是表单中可以没有数据。因此，不能使用语句if request.POST来判断是否使用HTTP POST方法；应该使用if request.method == "POST" (参见本表的method属性)。<br>
注意: POST不包括file-upload信息。参见FILES属性。
</td>
</tr>

<tr>
<td style = "text-align : center">
REQUEST
</td>
<td>
为了方便，该属性是POST和GET属性的集合体，但是有特殊性，先查找POST属性，然后再查找GET属性。借鉴PHP's $_REQUEST。
<br>
例如，如果GET = {"name": "john"} 和POST = {"age": '34'},则 REQUEST["name"] 的值是"john", REQUEST["age"]的值是"34".
<br>
强烈建议使用GET and POST,因为这两个属性更加显式化，写出的代码也更易理解。
</td>
</tr>

<tr>
<td style = "text-align : center">
COOKIES
</td>
<td>
包含所有cookies的标准Python字典对象。Keys和values都是字符串。
</td>
</tr>

<tr>
<td style = "text-align : center">
FILES
</td>
<td>
包含所有上传文件的类字典对象。FILES中的每个Key都是

`<input type="file" name="" \>` 标签中name属性的值. FILES中的每个value 同时也是一个标准Python字典对象，包含下面三个Keys:
<br>

+ filename: 上传文件名,用Python字符串表示
+ content-type: 上传文件的Content type
+ content: 上传文件的原始内容

注意：只有在请求方法是POST，并且请求页面中`<form>`有enctype="multipart/form-data"属性时FILES才拥有数据。否则，FILES 是一个空字典。
</td>
</tr>

<tr>
<td style = "text-align : center">
user
</td>
<td>
是一个django.contrib.auth.models.User 对象，代表当前登录的用户。
<br>
如果访问用户当前没有登录，user将被初始化为django.contrib.auth.models.AnonymousUser的实例。
<br>
你可以通过user的is_authenticated()方法来辨别用户是否登录：

```py
if request.user.is_authenticated():
    # Do something for logged-in users.
else:
    # Do something for anonymous users.
```
只有激活Django中的AuthenticationMiddleware时该属性才可用
</td>
</tr>

<tr>
<td style = "text-align : center">
META
</td>
<td>
包含所有可用HTTP头部信息的字典。 例如:

+ CONTENT_LENGTH
+ CONTENT_TYPE
+ QUERY_STRING: 未解析的原始查询字符串
+ REMOTE_ADDR: 客户端IP地址
+ REMOTE_HOST: 客户端主机名
+ SERVER_NAME: 服务器主机名
+ SERVER_PORT: 服务器端口

META 中这些头加上前缀 HTTP_ 为 Key, 冒号(:)后面的为 Value， 例如:

+ HTTP_ACCEPT_ENCODING
+ HTTP_ACCEPT_LANGUAGE
+ HTTP_HOST: 客户发送的HTTP主机头信息
+ HTTP_REFERER: referring页
+ HTTP_USER_AGENT: 客户端的user-agent字符串
+ HTTP_X_BENDER: X-Bender头信息

</td>
</tr>

<tr>
<td style = "text-align : center">
session
</td>
<td>
唯一可读写的属性，代表当前会话的字典对象。只有激活Django中的session支持时该属性才可用。
</td>
</tr>

<tr>
<td style = "text-align : center">
raw_post_data
</td>
<td>
原始HTTP POST数据，未解析过。 高级处理时会有用处。
</td>
</tr>


</tbody>

</table>

Request对象也有一些有用的方法：

| 方法 | 描述 |
|:--- | :----- |
| \_\_getitem\_\_(key) | 返回GET/POST的键值,先取POST,后取GET。如果键不存在抛出 KeyError。<br>这是我们可以使用字典语法访问HttpRequest对象。<br>例如,request["foo"]等同于先request.POST["foo"] 然后 request.GET["foo"]的操作。 |
| has\_key() | 检查request.GET 或者 request.POST中是否包含参数指定的Key。 |
| get\_full\_path() | 返回包含查询字符串的请求路径。例如， "/music/bands/the_beatles/?print=true" |
| is\_secure() | 如果请求是安全的，返回True，就是说，发出的是HTTPS请求。 |

### QueryDict对象

在HttpRequest对象中, GET和POST属性是django.http.QueryDict类的实例。  
QueryDict类似字典的自定义类，用来处理单键对应多值的情况。  
QueryDict实现所有标准的词典方法。

<table>
<thead>
<tr>
<th style = "text-align : center">
方法
</th>
<th style = "text-align : center">
描述
</th>
</tr>
</thead>

<tbody>

<tr style = "text-align : center">
<td>
__getitem__()
</td>
<td>
和标准字典的处理有一点不同，就是，如果Key对应多个Value，__getitem__()返回最后一个value。
</td>
</tr>

<tr style = "text-align : center">
<td>
__setitem__()
</td>
<td>
设置参数指定key的value列表(一个Python list)。注意：它只能在一个mutable QueryDict 对象上被调用(就是通过copy()产生的一个QueryDict对象的拷贝).
</td>
</tr>

<tr style = "text-align : center">
<td>
get()
</td>
<td>
如果key对应多个value，get()返回最后一个value。
</td>
</tr>

<tr style = "text-align : center">
<td>
update()
</td>
<td>
参数可以是QueryDict，也可以是标准字典。和标准字典的update方法不同，该方法添加字典 items，而不是替换它们:

```py
>>> q = QueryDict('a=1')

>>> q = q.copy() # to make it mutable

>>> q.update({'a': '2'})

>>> q.getlist('a')

['1', '2']

>>> q['a'] # returns the last

['2']
```
</td>
</tr>


<tr style = "text-align : center">
<td>
items()
</td>
<td>
和标准字典的items()方法有一点不同,该方法使用单值逻辑的__getitem__():

```py
>>> q = QueryDict('a=1&a=2&a=3')

>>> q.items()

[('a', '3')]
```
</td>
</tr>

<tr style = "text-align : center">
<td>
values()
</td>
<td>
和标准字典的values()方法有一点不同,该方法使用单值逻辑的__getitem__()
</td>
</tr>

<tr style = "text-align : center">
<td>
values()
</td>
<td>
和标准字典的values()方法有一点不同,该方法使用单值逻辑的__getitem__()
</td>
</tr>

<tr style = "text-align : center">
<td>
copy()
</td>
<td>
返回对象的拷贝，内部实现是用Python标准库的copy.deepcopy()。该拷贝是mutable(可更改的) — 就是说，可以更改该拷贝的值。
</td>
</tr>

<tr style = "text-align : center">
<td>
getlist(key)
</td>
<td>
返回和参数key对应的所有值，作为一个Python list返回。如果key不存在，则返回空list。 It's guaranteed to return a list of some sort..
</td>
</tr>

<tr style = "text-align : center">
<td>
setlist(key,list...)
</td>
<td>
设置key的值为list_ (unlike __setitem__()).
</td>
</tr>

<tr style = "text-align : center">
<td>
appendlist(key,item)
</td>
<td>
添加item到和key关联的内部list.
</td>
</tr>


<tr style = "text-align : center">
<td>
setlistdefault(key,list)
</td>
<td>
和setdefault有一点不同，它接受list而不是单个value作为参数。
</td>
</tr>

<tr style = "text-align : center">
<td>
lists()
</td>
<td>
和items()有一点不同, 它会返回key的所有值，作为一个list, 例如:

```py
>>> q = QueryDict('a=1&a=2&a=3')

>>> q.lists()

[('a', ['1', '2', '3'])]
```

</td>
</tr>


<tr style = "text-align : center">
<td>
urlencode()
</td>
<td>
返回一个以查询字符串格式进行格式化后的字符串(例如："a=2&b=3&b=5")。
</td>
</tr>



</tbody>
</table>