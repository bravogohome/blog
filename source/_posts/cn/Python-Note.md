---
title: Python学习笔记
catalog: true
lang: cn
date: 2021-11-04 15:25:13
subtitle: Python学习笔记
header-img: /img/header_img/nier.png
tags:
- Python
categories:
- Note
sticky: 999
---
> Python3和Python2在部分使用上有区别，详情请参见官方文档
> 本文使用的是`Python3`

## python安装

1. 访问[Python官网](https://www.python.org/)并下载Python  
windows下载地址<https://www.python.org/downloads/windows/>  
安装完成后打开命令提示符窗口输入`python`查看是否安装成功。  
2. 配置环境变量
3. 安装IDE/编辑器:vscode  
    + Pycharm
    + Rider 
4. 创建py文件

## python语法
### 变量赋值

使用等号为变量赋值：

```py
a = 1
b = 2.0
c = "str"
```

也可以同时为多个变量赋值：

```py
a = b = c = 1   # 从左到右依次赋值   
a, b, c = 1, 2.0, "str"   # 分别赋值
```

************************************************************


## Python基本数据类型

Python中的变量不需要声明。每个变量在使用前都必须赋值，**变量赋值以后该变量才会被创建**。  
在Python中，变量就是变量，它“没有类型”，数据类型指的是**变量所指的内存中对象的类型**。  
等号（=）运算符左边的是一个变量名，等号（=）运算符右边的是将存储在变量的值。 
> 一个变量可以通过赋值指向不同类型的对象。

python中有六个标准的数据类型：

- [Number](#Number数字)
- [Tuple](#Tuple元组)
- [String](#String字符串)
- [List](#List列表)
- [Set](#Set集合)
- [Dictionary](#Dictionary字典)

其中`不可变`的数据类型为： `Number`、`Tuple`、`String`  
`可变`的数据类型为： `List`、`Set`、`Dictionary`

在解释这六个数据类型前，有两个方法需要介绍：

### `type()` 和 `isinstance()`

Python内置的 **type()** 函数可以用来查询变量所指的对象类型。  
type()函数有两个重载方法：  

```python
type(object) -> type # the object's type
type(name, bases, dict) -> object # a new type object
```

如果只有一个参数则返回对象的类型，三个参数返回新的类型对象。  

而 **isinstance()** 函数用来判断一个对象是否是一个已知的类型。  
使用方法：

```python
isinstance(object, classinfo) -> bool
```

> 参数：
> + object - 实例对象  
> + classinfo - 可以是直接或间接类名、基本类型或者由它们组成的元组
> > classinfo为基本类型时,可以是`int`，`float`，`bool`，`complex`，`str`(字符串)，`list`，`dict`(字典)，`set`，`tuple`。  
> > 要注意的是，classinfo 的字符串是 `str` 而不是 `string`，字典也是简写 `dict`。

#### isinstance() 与 type() 区别：

type() 不会认为子类是一种父类类型，`不考虑`**继承**关系。  
isinstance() 会认为子类是一种父类类型，`考虑`**继承**关系。  
如果要判断两个类型是否相同推荐使用` isinstance() `。  

```python
# 示例代码
class A:
    pass
class B(A):
    pass

a = A()
b = B()

print(isinstance(a,A))
print(isinstance(b,A))
print(type(a))
print(type(b))
print(type(a)==A)
print(type(b)==A)
```

以上代码的输出结果为：  
> True  
> True  
> <class '\_\_main__.A'>  
> <class '\_\_main__.B'>  
> True  
> False  


### Number数字

数字类型是不允许改变的，这就意味着如果改变数字数据类型的值，将重新分配内存空间。

python数字类型包括：`整型int`、`浮点型float`、`布尔型bool`、`复数型complex`。  

> 其中在Python3中，只有一种整数类型int，表示为长整型，没有Python2中的Long

#### 具体类型
##### int

int通常被称为是整型或整数，是正或负整数，不带小数点。Python3 整型是没有限制大小的，可以当作“Long”长整型使用，所以 Python3 没有 Python2 的 Long 类型。  
除了用正常的十进制数，我们还可以使用十六进制或八进制数来代表整数：

```python
>>> number = 0xA0F # 十六进制
>>> number
2575

>>> number=0o37 # 八进制
>>> number
31
```

##### float

浮点型由整数部分与小数部分组成，浮点型也可以使用科学计数法表示（2.5e2 = 2.5 x 102 = 250）  
以下变量都表示为float类型：

```python
>>> number1 = 0.0
>>> number2 = 13.10
>>> number3 = 1.2e2
>>> number4 = 2.5e+3
>>> number5 = 9.
>>> number6 = -2.1E-5
```

> Python对**绝对值小于**`0.0001`的浮点数使用科学计数法显示：  
> ```python 
> >>> 0.0001
> 0.0001
> >>> 0.00001
> 1e-05
> ```
> 
> 另一个临界点是`1e+16`:
> ```python
> >>> 1000000000000000.0  
> 1000000000000000.0
> >>> 10000000000000000.0 
> 1e+16
> ```
> 
> float的正常最多位为16位小数，比如：
> ```python
> >>> 1 / 3.0
> 0.3333333333333333
> >>> 9.9999999999999999 
> 10.0
> >>> 9.999999999999999 
> 9.999999999999998
> >>> 9.99999999999999
> 9.99999999999999
> ```
> 
> 这里和临界点外有关的数据运算将会产生数据精度和数据损失的相关问题:[python float 精度问题](#精度问题)  


##### bool

bool用来表示真假的状态，`True`表示真，`False`表示假，注意`区分大小写`。  
Python3中，bool是int的`子类`；  
> 在 Python2 中是没有布尔型的，它用数字 0 表示 False，用 1 表示 True。

*True* 和 *False* 可以和数字相加，`True==1` `False==0`会返回***True***，但可以通过`is`来判断类型。

```python
print(issubclass(bool, int))
print(True==1)
print(False==0)
print(True+1)
print(False+1)
print(1 is True)
print(0 is False)
```

以上代码的输出结果为：  
> True  
> True  
> True  
> 2  
> 1  
> False  
> False

> 注意：从Python3.8开始，使用***is***和***is not***运算符时，会抛出`SyntaxWarning: "is" with a literal. Did you mean "=="?`语法警告信息。

##### complex

复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型。

#### 数值运算

Python 解释器可以作为一个简单的计算器，您可以在解释器里输入一个表达式，它将输出表达式的值。   
表达式的语法很直白： `+`加法, `-`减法, `*`乘法, `/`除法, `//`整除, `%`取余, `**`乘方/幂

```python
# 解释器形式,非解释器需要在表达式外加上print函数才能在输出到终端显示
>>> 5 + 4 # 加法
9
>>> 4.3 - 2 # 减法
2.3
>>> 3 * 7  # 乘法
21
>>> 2 / 4  # 除法，得到一个浮点数
0.5
>>> 2 // 4 # 除法，得到一个整数
0
>>> 17 % 3 # 取余
2
>>> 2 ** 5 # 乘方/幂
32
```

在混合运算中，Python会把整型转换成浮点数后参加运算。  
比如，整除返回的不一定是整数类型，它和分母分子的数据类型有关：

```python
>>> 7//2
3
>>> 7.0//2
3.0
>>> 7/2.0
3.0
```


#### 数字类型转换

Python各数字类型间支持互相转换。  
Python的数字类型转化和创建都可以直接将***数据类型作为函数名***即可。  

注意强制类型转换可能会导致***数据损失***。  

```python
>>> int(1.2)
1   
>>> int(2.0) 
2   
>>> float(1) 
1.0 
>>> float(1.1)
1.1
>>> bool(1) 
True
>>> bool(0)
False
>>> bool(2)
True
>>> bool(-1)
True
>>> bool(True)
True
>>> complex(1,2)
(1+2j)
>>> complex(2)
(2+0j)
>>> complex(1.2,True)
(1.2+1j)
```

#### 相关函数

| 函数 | 返回值 / 描述  |
| :--: | :------------ |
| [abs()](#abs) | 返回数字的`绝对值`，如`abs(-10)`返回`10`，如果参数是一个复数，则返回它的大小 |
| [ceil()](#ceil) | 返回数字的`向上取整`的整数值，如`math.ceil(2.1)`返回`5` |
| [exp()](#exp) | 返回e的x次幂(e^x)，如math.exp(1)返回2.718281828459045 |


#### 相关常量

### Tuple元组
### String字符串
### List列表
### Set集合
### Dictionary字典

<!-- TODO: _变量 -->
<!-- TODO: del删除对象 引用 -->

****************************************************

<!-- TODO  函数汇总-->
## Python内置函数
### abs()

abs()函数返回数字的绝对值，如果参数是一个复数，则返回它的大小。  

语法：  
> 
> ```python
> abs(x)
> ```
> 
> **参数说明：**  
> + `x` : 数值表达式，可以是int,float,bool,complex
> 
> **返回值：**  
> 返回对应参数的类型，注意如果是复数返回的是其模。

用例：  
```python
print(abs(-1))
print(abs(-1.0))
print(abs(3+4j))
print(abs(False))
```

以上代码运行后的输出结果为：  
> 1
> 1.0
> 5.0
> 0

*************************************************

*************************************************

## Python math 函数

### ceil()

xxxxxxxxxx

语法：  
> 
> ```python
> 
> ```
> 
> **参数说明：**  
> + x :  
> 
> **返回值：**  
> 

用例：  
```python

```

以上代码运行后的输出结果为：  
> 1

*************************************************

### exp()

xxxxxxxxxx

语法：  
> 
> ```python
> 
> ```
> 
> **参数说明：**  
> + x :  
> 
> **返回值：**  
> 

用例：  
```python

```

以上代码运行后的输出结果为：  
> 1

*************************************************


<!-- TODO：新建文章记录错误 -->
## Python常见错误
### 精度问题
Python的float的两个临界点会转换科学计数法表示，是精度问题出现的原因：  

```python
>>> 10000000000000001.0 
1e+16
>>> 10000000000000001.0 - 1
1e+16
>>> 10000000000000001.0 - 2 
9999999999999998.0
>>> 10000000000000002.0 - 2 
1e+16
>>> 10000000000000003.0 - 2 
1.0000000000000002e+16

>>> 9.9999999999999999 
10.0
>>> 9.999999999999999 
9.999999999999998
>>> 9.99999999999999
9.99999999999999
```

解决精度问题的方法是使用`decimal`包