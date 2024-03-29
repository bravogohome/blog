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

## python基本语法

### 编码
<!-- TODO: 编码 -->

### 标识符

+ 第一个字符必须是字母表中字母或下划线 _ 。
+ 标识符的其他的部分由字母、数字和下划线组成。
+ 标识符对大小写敏感。
+ 非关键字

> 在 Python 3 中，可以用中文作为变量名，非 ASCII 标识符也是允许的了。

***********************************

### 语句

Python中通常一行表示一个语句，末尾不需加上分号";".

```python
print("hello world")
```

***`多行语句`***

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠` \ `来实现多行语句，例如：
```py
total = item_one + \
        item_two + \
        item_three
```

但在 [], {}, 或 () 中的多行语句，`不需要使用反斜杠 \` ，例如：
```py
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

***`空行`***
函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。  
空行与代码缩进不同，空行并不是 Python 语法的一部分。书写时不插入空行，Python 解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。  

> 空行也是程序代码的一部分。

***`同行多条语句`***

Python 可以在同一行中使用多条语句，语句之间使用分号 ; 分割 ：

```py
c = 5; print("a"); print("b"); print(c)
```

***`pass语句`***
Python pass是空语句，是为了保持程序结构的完整性。  
pass 不做任何事情，一般用做占位语句，如下实例：  
```Python
while True: 
    pass # 等待键盘中断 (Ctrl+C)
```

**********************************

### 变量赋值

使用等号为变量赋值：

```py
a = 1
b = 2.0
c = "str"
```

也可以同时为多个变量赋值：

```py
a = b = c = 1   # 从右到左依次赋值   
a, b, c = 1, 2.0, "str"   # 同时分别赋值
```

在Python中，类型属于对象，变量是没有类型的：  
```Python
a = 'str'
```

在以上代码中，'str'是String类型，而变量a是没有类型的，它只是一个对象的引用（一个指针），它指向'str'这个String类型对象。

***********************************

### 关键字

关键字又叫保留字，它不能作为任何标识符名称，Python的标准库提供了一个keyword模块，可以输出当前版本的所有关键字：  

```python 
import keyword

print(keyword.kwlist)
```

以上代码的输出结果为（版本Python 3.9.8）：  
> ['False', 'None', 'True', '\_\_peg\_parser\_\_', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']

***********************************

### 注释

***`单行注释`***
Python的单行注释使用`#`号：  
```python
# 单行注释
a = 1  # 注释
```

***`多行注释`***
Python的多行注释使用` ''' ` 或 ` """ `:  
```python
'''
多行
注释
1
'''

"""
多行注释
2
"""

```

*************************

### 代码块

和其他语言不同，Python使用缩进表示不同的代码块，而不需要使用大括号<kbd>{}</kbd>。  
缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。  

```python
if True:
    print ("True")
else:
    print ("False")
```

如果同一代码块的缩进空格数不一致，会导致运行错误：  

```python
if True:
    print ("True")
else:
    print ("False")
  print("error")
```

以上代码的输出结果为：  
>   File "&lt;tokenize>", line 5
>     print("error")
>     ^
> IndentationError: unindent does not match any outer indentation level

***********************************

### 输入输出

Python的内置函数[input()](#input)和[print()](#print)分别表示输入和输出:  

```python
input("\n\n按下 enter 键后退出。")

print("输出")
print("print默认是换行的，如果不需要换行需要在后面参数加上end=''",end = '')
```

*******************************

### 导入import
在 python 用 `import` 或者 `from...import` 来导入相应的模块。
将整个模块(somemodule)导入，格式为： `import somemodule`
从某个模块中导入某个函数,格式为： `from somemodule import somefunction`
从某个模块中导入多个函数,格式为： `from somemodule import firstfunc, secondfunc, thirdfunc`
将某个模块中的全部函数导入，格式为： `from somemodule import *`

***************************

### 解释器
<!-- TODO: 解释器 -->

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

其中`不可变`immutable的数据类型为： `Number`、`Tuple`、`String`  
`可变`mutable的数据类型为： `List`、`Set`、`Dictionary`


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
> &lt;class '\_\_main__.A'>  
> &lt;class '\_\_main__.B'>  
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
> 这里和临界点外有关的数据运算将会产生数据精度和数据损失的相关问题:[python float 精度问题](#float精度问题)  


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

#### 常用函数

##### [Python的内置函数](#Python内置函数)
| 序号 | 函数 | 返回值 / 描述  |
| :-: |:--: | :------------ |
| 1 | [max()](#max) | 返回给定参数的`最大值`，如`max([1,2,3,5,1])`返回`5`，参数可以为序列 |
| 2 | [min()](#min) | 返回给定参数的`最小值`，如`min([1,2,3,5,-1])`返回`-1`，参数可以为序列 |
| 3 | [round()](#round) | 给定浮点数和保留位数，返回浮点数的`四舍五入`值，如`round(3.526,2)`返回3.53。**其实准确的说是保留值将保留到离上一位更近的一端。** |
| 4 | [abs()](#abs) | 返回数字的`绝对值`，如`abs(-10)`返回`10`，如果参数是一个复数，则返回它的大小 |

##### [Python的math模块](#Python-math模块方法)  
| 序号 | 函数 | 返回值 / 描述  |
| :-: |:--: | :------------ |
| 1 | [fabs()](#fabs) | fabs也返回数字的`绝对值`，相较abs()更具局限性，只作用于浮点型或整型，`math.fabs(-10)`将返回10.0 |
| 2 | [ceil()](#ceil) | 返回数字的`上入整数`，如`math.ceil(2.1)`返回`3` |
| 3 | [floor()](#floor) | 返回数字的`下舍整数`，如`math.floor(2.1)`返回`2` | 
| 4 | [exp()](#exp) | 返回`e的x次幂`即指数(e^x)，如`math.exp(1)`返回2.718281828459045 |
| 5 | [log()](#log) | 返回`给定底数的对数值`，如`math.log(100,10)`返回2.0 |
| 6 | [log10()](#log10) | 返回`以10为底的对数值`，如`math.log10(100)`返回2.0 |
| 7 | [modf()](#modf) | 返回数字的`整数和小数部分`，如`math.modf(-100.03)`返回(-0.030000000000001137, -100.0) |
| 8 | [pow()](#pow) | 返回`幂运算结果`，如`math.pow(2,3)`返回8.0，效果等同`**`运算 |
| 9 | [sqrt()](#sqrt) | 返回数字的`平方根`，如`math.sqrt(4)`返回2.0 |
| | `三角函数` |
| 1 | [sin()](#sin) | 返回弧度的`正弦值`，如`math.sin(math.pi/2)`返回1.0 |
| 2 | [asin()](#asin) | 返回弧度的`反正弦弧度值`，如`math.asin(0)`返回0.0 |
| 3 | [cos()](#cos) | 返回弧度的`余弦值`，如`math.cos(math.pi)`返回-1.0 |
| 4 | [acos()](#acos) | 返回弧度的`反余弦弧度值`，如`math.acos(-1)`返回3.141592653589793 |
| 5 | [tan()](#tan) | 返回弧度的`正切值`，如`math.tan(math.pi/4)`返回0.9999999999999999 |
| 6 | [atan()](#atan) | 返回弧度的`反正切弧度值`，如`math.atan(0)`返回0.0 |
| 7 | [degress()](#degress) | 将`弧度转换为角度`,如`math.degrees(math.pi/2)`，返回90.0 |
| 8 | [radians()](#radians) | 将`角度转换为弧度`,如`math.radians(180)`，返回3.141592653589793 |


##### [Python的random模块](#Python-random模块方法)
| 序号 | 函数 | 返回值 / 描述  |
| :-: |:--: | :------------ |
| 1 | [choice()](#choice) | 从`序列`的元素中`随机挑选一个元素`，比如`random.choice(range(10))`，返回从0到9中随机挑选的一个整数。 |
| 2 | [randrange()](#randrange) | `random.randrange([start,]stop[,step])`从指定范围内，按指定基数递增的集合中获取一个随机数，基数默认值为 1，如`random.randrange(1,100,2)`表示从1-100中选取一个奇数 |
| 3 | [random()](#random) | 在`[0,1)范围`内，随机生成下一个实数。`random.random()` |
| 4 | [uniform()](#uniform) | 在`[x,y]范围`内，随机生成下一个实数。`random.uniform(x,y)` |
| 5 | [seed()](#seed) | `改变随机数生成器的种子`seed。如果你不了解其原理，你不必特别去设定seed，Python会帮你选择seed。`random.seed()` |
| 6 | [shuffle()](#shuffle) | 将`序列`的所有元素`随机排序`。`random.shuffle(list)` |


#### 相关常量
| 常量 | 描述 |
| :--:| :---------|
| pi | 圆周率，数学常量 pi `math.pi = 3.141592653589793` |
| e | 自然常数，数学常量 e `math.e = 2.718281828459045` |

********************************************************

### Tuple元组

Python中元组是不可变的数据类型，即元组中的元素不能被修改。  

#### 元组的创建
元组的创建方式有两种：
```python
# 直接使用小括号创建，元素间使用逗号隔开
tuple1 = (1, 5, 6, 7)
# 元组中的元素类型可以混合
tuple2 = (1, "1", 1.0, (1, 2), [1])
```

```python
# 使用tuple方法创建
list = [1,5,7]
tuple3 = tuple(lst)
```

创建***空元组***：  
```python
tuple1 = ()
tuple2 = tuple()
```

创建`只有一个元素`的元组时，需要在元素后添加一个**逗号**`,` ， 否则括号会被当成运算符使用！！:  
```python
>>> tuple1 = (1,)
>>> print(type(tuple1))
<class 'tuple'>   # 加上逗号，类型为元组

>>> tuple2 = (1)
>>> print(type(tuple2))
<class 'int'>   # 不加逗号，类型为整型
```

#### 元组的索引和截取

因为元组也是一个序列，所以我们可以使用[`切片运算符`](#切片运算符)来进行索引和截取：  

***索引***
```python
tuple_test = (1, 5, 6, 7, 11, 3)

# 正向索引
print(tuple_test[2])   # 读取第3个元素 / 读取索引为2的元素
# 逆向索引
print(tuple_test[-1])   # 读取倒数第1个元素
```
以上代码的输出结果为：  
> 6  
> 3

***截取***
```python
tuple_test =  (6, 8, 9, 7, 2, 23, 1, 1, 13)
print(tuple_test)

# 截取
print(tuple_test[1:])     # 截取元组从索引为1的元素开始后的所有元素
print(tuple_test[1:3])    # 截取元组索引区间[1,3)，即第二到第三个元素间的片段
print(tuple_test[1:-1])    # 截取元组第二到倒数第二个元素间的片段
print(tuple_test[1:-1:2])   # 从1到-1索引元素方向，按每次索引递增步长的趋势截取，此时步长为2，即隔位截取
print(tuple_test[1:-1:-1])  # 从1到-1索引元素方向，按每次索引递增步长=-1的趋势截取，很明显此时无截取片段
print(tuple_test[-1:1:-1])   # 从-1到1索引元素方向，按每次索引递增步长=-1的趋势截取，即为反向截取
```

以上代码的运行结果为：  
> (6, 8, 9, 7, 2, 23, 1, 1, 13)  
> (8, 9, 7, 2, 23, 1, 1, 13)   
> (8, 9)  
> (8, 9, 7, 2, 23, 1, 1)  
> (8, 7, 23, 1)  
> ()  
> (13, 1, 1, 23, 2, 7, 9)  


#### 元组运算

元组运算满足[序列运算规则](#序列运算)：  

***`+运算`***

```python
print((2, 6, 9, 8, 2) + (1, 6, 11))
```

以上代码的输出结果为：  
> (2, 6, 9, 8, 2, 1, 6, 11)

***`*运算`***

```python
print(("a", "b") * 4)
```

以上代码的输出结果为：  
> ('a', 'b', 'a', 'b', 'a', 'b', 'a', 'b')


***`in运算`***

```python
print(5 in (1,2,6,4,6,5))
```

以上代码的运行结果为：  
> True

***`切片运算`***
见上文的[元组的索引和截取](#元组的索引和截取)

#### 常用函数

<br>

<table>
<thead>
<tr>
<th>
序号
</th>
<th>
方法及描述
</th>
<th>
实例
</th>
</tr>
</thead>
<tbody>
<tr>
<td>
1
</td>
<td>
<a href = "#len">len(tuple)</a><br>计算元组元素个数
</td>
<td>

```python
>>> tuple1 = (1, 2, 5)
>>> len(tuple1)
3
```

</td>
</tr>
<tr>
<td>
2
</td>
<td>
<a href = "#max">max(tuple)</a><br>返回元组中元素的最大值
</td>
<td>

```python
>>> tuple2 = (5, 9, 6)
>>> max(tuple2)
9
```

</td>
</tr>
<tr>
<td>
3
</td>
<td>
<a href = "#min">min(tuple)</a><br>返回元组中元素的最小值
</td>
<td>

```python
>>> tuple3 = (5, 9, 6)
>>> min(tuple3)
5
```

</td>
</tr>
<tr>
<td>
4
</td>
<td>
<a href = "#tuple">tuple(iterable)</a><br>将可迭代系列转换为元组
</td>
<td>

```python
>>> list1= ['1', '2', '4', '3']
>>> tuple1=tuple(list1)
>>> tuple1
('1', '2', '4', '3')
```

</td>
</tr>
</tbody>
</table>

***********************************************

### String字符串

Python string是不可变的数据类型。

#### 字符串创建

我们使用引号`( ' 或 " )`来创建字符串。
```python
str1 = "a1"
str2 = 'b5555'
```

python中没有传统的单字符char类型，在Python中单字符也作为字符串使用
```python
print(type('a'))
```

以上代码的输出结果为：  
> &lt;class 'str'>


还可以使用三引号`( """ 或 '''  )`来创建多行字符串  
三引号允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符。  
```python
para_str = """这是一个多行字符串的实例
多行字符串可以使用制表符
TAB ( \t )。
也可以使用换行符 [ \n ]。
"""
print (para_str)
```

以上代码的结果为：  
> 这是一个多行字符串的实例  
> 多行字符串可以使用制表符  
> TAB ( 	 )。  
> 也可以使用换行符 [   
>  ]。   

三引号让程序员从引号和特殊字符串的泥潭里面解脱出来，自始至终保持一小块字符串的格式是所谓的`WYSIWYG（所见即所得）`格式的。  
一个典型的用例是，当你需要一块`HTML或者SQL`时，这时用字符串组合，特殊字符串转义将会非常的繁琐。而使用三引号多行字符就可以轻松完成。  
```python
errHTML = '''
<HTML><HEAD><TITLE>
Friends CGI Demo</TITLE></HEAD>
<BODY><H3>ERROR</H3>
<B>%s</B><P>
<FORM><INPUT TYPE=button VALUE=Back
ONCLICK="window.history.back()"></FORM>
</BODY></HTML>
'''
cursor.execute('''
CREATE TABLE users (  
login VARCHAR(8), 
uid INTEGER,
prid INTEGER)
''')
```


#### 字符串访问

字符串的访问和元组类似，使用切片运算和索引定位。   

> 字符串可以被看成是`特殊的元组`

***索引***
```python
str_test = "sajldfj*(&5"

# 正向索引
print(str_test[2])   # 读取第3个元素 / 读取索引为2的元素
# 逆向索引
print(str_test[-1])   # 读取倒数第1个元素
```

以上代码的输出结果为：  
> 'j'  
> '5'

***截取***
```python
str_test =  "hello world"
print(str_test)

# 截取
print(str_test[1:])     # 截取字符串从索引为1的元素开始后的所有元素
print(str_test[1:3])    # 截取字符串索引区间[1,3)，即第二到第三个元素间的片段
print(str_test[:-1])     # 从字符串起始截取到倒数第一个元素前的片段
print(str_test[1:-1])    # 截取字符串第二到倒数第二个元素间的片段
print(str_test[1:-1:2])   # 从1到-1索引元素方向，按每次索引递增步长的趋势截取，此时步长为2，即隔位截取
print(str_test[1:-1:-1])  # 从1到-1索引元素方向，按每次索引递增步长=-1的趋势截取，很明显此时无截取片段
print(str_test[-1:1:-1])   # 从-1到1索引元素方向，按每次索引递增步长=-1的趋势截取，即为反向截取
print(str_test[::-1])      # 逆向输出字符串
```

以上代码的运行结果为：  
> hello world  
> ello world  
> el  
> hello worl
> ello worl  
> el ol  
>   
> dlrow oll  
> dlrow olleh


#### 字符串运算

字符串运算满足[序列运算规则](#序列运算)：  

***`+运算`***

```python
print("hello"+" world")
```

以上代码的输出结果为：  
> hello world

***`*运算`***

```python
print("a" * 4)
```

以上代码的输出结果为：  
> aaaa


***`in运算`***

```python
print('a' in "hello world")
```

以上代码的运行结果为：  
> False

***`切片运算`***
见上文的[字符串访问](#字符串访问)


#### 字符串格式化

##### 转义字符
普通字符串中使用反斜杠`(\)`做特殊字符的转义字符：  
更多请见下文[Python转义字符](#Python转义字符)

##### r-string
r-string将输出`原始字符串`，转义字符将不生效。  
使用方法是在字符串引号前加上 ` r/R `：  
```python
print(r"row string")
print(r"\n jh\nj")
```

以上代码的运行结果为：  
> row string
> \n jh\nj

##### 级联

Python按字面意义级联字符串，如 "this " "is " "string" 会被自动转换为 this is string。
```python
print("this " "is " "string")
```

以上代码的输出结果为：  
> this is string

##### %格式
%格式化的基本用法是将一个值插入到一个有字符串格式符的位置中。  
```python
print ("插入点1： %s 。插入点2： %d 。" % ('string', 222))
```

以上代码的输出结果为：  
> 插入点1： string 。插入点2： 222 。

***python字符串格式化符号***

| 符号 | 描述 |
| :--: | :------------------|
|  %c  | 格式化字符及其ASCII码 |
|  %s  | 格式化字符串 |
|  %d  | 格式化整数 |
|  %u  | 格式化无符号整型 |
|  %o  | 格式化无符号八进制数 |
|  %x  | 格式化无符号十六进制数 |
|  %X  | 格式化无符号十六进制数（大写） |
|  %f  | 格式化浮点数字，可指定小数点后的精度 |
|  %e  | 用科学计数法格式化浮点数 |
|  %E  | 作用同%e，用科学计数法格式化浮点数 |
|  %g  | %f和%e的简写 |
|  %G  | %f 和 %E 的简写 |
|  %p  | 用十六进制数格式化变量的地址 |

***格式化操作符辅助指令***
格式化操作符位于%和格式化符号字母中间。    ex. %.2f
| 符号 | 功能 |
| :--: | :----- |
| * | 定义宽度或者小数点精度 |
| - | 用做左对齐 |
| + | 在正数前面显示加号( + ) |
| <sp> | 在正数前面显示空格 |
| #	| 在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X') |
| 0	| 显示的数字前面填充'0'而不是默认的空格 |
| % |	'%%'输出一个单一的'%' |
| (var)	| 映射变量(字典参数) |
| m.n. | m 是显示的最小总宽度,n 是小数点后的位数(如果可用的话) |

##### format函数
Python格式化字符串的函数[` str.format() `](#format)，它增强了字符串格式化的功能。
```python
print("{1} {0} {1}".format("hello", "world"))
```

以上代码的输出结果为：  
> world hello world

更多使用方法请看[format()](#format)

##### f-string
f-string 是 python3.6 之后版本添加的，f-string 称之为字面量格式化字符串，是新的格式化字符串的语法。  
f-string 格式化字符串以 f 开头，后面跟着字符串，字符串中的表达式用大括号 {} 包起来，它会将变量或表达式计算后的值替换进去:  

```python
a = 56
print(f"a = {a}")
```

以上代码的输出结果为:  
> a = 56

在 Python 3.8 的版本中可以使用 = 符号来拼接运算表达式与结果：  
```python
x = 1
print(f"{x+1=}")
```

以上代码的输出结果为：  
> x+1=2

#### 常用函数

| 序号 | 方法 | 返回值/描述 |
| :-: | :--: | :---------- |
| 1 | [encode()](#encode) | `str.encode(encoding='UTF-8',errors='strict')`以 encoding 指定的编码格式`编码字符串`，如果出错默认报一个ValueError 的异常，除非 errors 指定的是'ignore'或者'replace' |
| 2 | [decode()](#decode) | `bytes.decode(encoding="utf-8", errors="strict")`Python3 中没有 decode 方法，但我们可以使用 bytes 对象的 decode()方法来`解码`给定的 `bytes` 对象，这个 bytes 对象可以由 str.encode() 来编码返回。 |
| 3 | [len()](#len) | 返回字符串的`长度` |
| 4 | [max()](#max) | 返回字符串的`最大的字母` |
| 5 | [min()](#min) | 返回字符串的`最小的字母` |
|  | ----- | ***检查\检测 方法*** |
| 1 | [count()](#count) | `str.count(s,beg=0,end=len(str))`返回某段子字符串在字符串里的`出现次数`，beg和end可以指定范围 |
| 2 | [startswith()](#startswith) |  `str.startswith(substr,beg=0,end=len(str))`检查字符串在指定范围内`是否以substr开始`，如果是返回True，否则返回False |
| 3 | [endswith()](#endswith) |  `str.endswith(suffix,beg=0,end=len(str))`检查字符串在指定范围内`是否以suffix结束`，如果是返回True，否则返回False |
| 4 | [find()](#find) | `str.find(s,beg=0,end=len(str))`检测在指定范围内str中`是否包含子字符串`s，如果成功则`返回开始的索引值`，否则返回-1 |
| 5 | [rfind()](#rfind) | `str.rfind(s,beg=0,end=len(str))`类似于find()函数，不过是从`右边开始查找`. |
| 6 | [index()](#index) | `str.index(s,beg=0,end=len(str))`和find()方法一样，用于检测`是否包含子字符串`，不同的是如果不包含则会报一个异常 |
| 7 | [rindex()](#rindex) | `str.rindex(s,beg=0,end=len(str))`类似于 index()，不过是从`右边开始`. |
| 8 | [isalnum()](#isalnum) | 如果字符串至少有一个字符并且`所有字符都是字母或数字`则返回True，否则返回 False |
| 9 | [isalpha()](#isalpha) | 如果字符串至少有一个字符并且`所有字符都是字母或中文字`则返回True，否则返回 False |
| 10 | [isdigit()](#isdigit) | 如果字符串`只包含数字`则返回True，否则返回False |
| 11 | [isnumeric()](#isnumeric) | 如果字符串`只包含数字字符`则返回True，否则返回False |
| 12 | [isspace()](#isspace) | 如果字符串中`只包含空白`则返回True，否则返回False |
| 13 | [isdecimal()](#isdecimal) | 检查字符串是否`只包含十进制字符`，如果是返回True，否则返回False。 |
| 14 | [islower()](#islower) | 如果字符串中包含至少一个区分大小写的字符，并且所有这些`(区分大小写的)字符都是小写`，则返回 True，否则返回 False |
| 15 | [isupper()](#isupper) | 如果字符串中包含至少一个区分大小写的字符，并且所有这些`(区分大小写的)字符都是大写`，则返回 True，否则返回 False |
| 16 | [istitle()](#istitle) | 检查字符串`是否是标题化`的，是则返回 True，否则返回 False |
|  | ----- | ***字符串操作 方法*** |
| 1 | [replace()](#replace) | `str.replace(old,new[,max])`把将字符串中的`old替换成new`,如果max指定，则替换不超过max次。 |
| 2 | [join()](#join) | `str.join(sequence)`将`序列`中的元素`以指定的字符连接`生成一个新的字符串。 |
| 3 | [split()](#split) | `str.split(s="", num=str.count(s))`通过`指定分隔符对字符串进行切片`，返回分割后的字符串列表。 |
| 4 | [splitlines()](#splitlines) | `str.([keependsplitliness])`按照`行分隔`('\r', '\r\n', \n')，返回一个包含各行作为元素的列表，如果参数 keepends为False，则不包含换行符，如果为True，则保留换行符。 |
| 5 | [lstrip()](#lstrip) | `str.lstrip(chars="")`将`截掉字符串左边/开始的指定字符`，默认为空格。 |
| 6 | [strip()](#strip) | `str.strip(chars="")`将`截掉字符串两端的指定字符`，即在字符串上执行lstrip()和rstrip()。 |
| 7 | [rstrip()](#rstrip) | `str.rstrip(chars="")`将`截掉字符串右边/末尾的指定字符`，默认为空格。 |
| 8 | [capitalize()](#caplitalize) |  将字符串的`第一个字符`转换为`大写` |
| 9 | [lower()](#lower) |  将字符串的`所有大写字符`转换为`小写` |
| 10 | [upper()](#upper) |  将字符串的`所有小写字符`转换为`大写` |
| 11 | [swapcase()](#swapcase) |  将字符串中`大写转换为小写，小写转换为大写` |
| 12 | [title()](#title) |  返回`"标题化"`的字符串,就是说所有单词都是以大写开始，其余字母均为小写 |
| 13 | [ljust()](#ljust) | `str.ljust(width,fillchar)`返回一个指定宽度为width且`左对齐右边填充`fillchar的字符串 |
| 14 | [center()](#center) | `str.center(width,fillchar)`返回一个指定宽度为width且`居中两边填充`fillchar的字符串 |
| 15 | [rjust()](#rjust) | `str.rjust(width,fillchar)`返回一个指定宽度为width且`右对齐左边填充`fillchar的字符串 |
| 16 | [zfill()](#zfill) | `str.zfill(width)`返回一个指定宽度为width且`右对齐左边填充0`的字符串，等价于rjust(width,'0') |
| 17 | [expandtabs()](#expandtabs) | `str.expandtabs(tabsize=8)`把字符串中的`tab符号转为空格`，tab符号默认的空格数是8。 |
| 18 | [maketrans()](#maketrans) | `str.maketrans(intab,outtab)`用于`创建字符映射的转换表`，对于接受两个参数的最简单的调用方式，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。 |
| 19 | [translate()](#translate) | `str.translate(table, deletechars="")`根据给出的`表转换`str的字符, 要过滤掉的字符放到 deletechars 参数中 |

<!-- TODO: string常用函数 -->

#### Python转义字符

| 转义字符 | 描述 |
| :-- | :-- |
| \\(在行尾时) | 续行符 |	
| \\\\ | 反斜杠符号 |
| \\' | 单引号 |
| \\" | 双引号 |
| \\a | 响铃 |
| \\b | 退格 |
| \\000 | 空 |
| \\n | 换行 |
| \\v | 纵向制表符 |
| \\t | 横向制表符 |
| \\r | 回车，将 \\r 后面的内容移到字符串开头，并逐一替换开头部分的字符，直至将 \\r 后面的内容完全替换完成。 |
| \\f | 换页 |
| \\yyy | 八进制数，y代表0~7的字符，例如：\\012 代表换行。 |
| \\xyy | 十六进制数，以\\x开头,y代表的字符，例如\\x0a 代表换行 |

************************************************

### List列表

List是Python中被频繁使用的数据类型，列表的元素可以存储不同的数据类型，甚至可以包含列表元组等。  
列表是可变的数据类型，即其内的数据可以被改变。  

#### 创建列表
创建列表的方式有三种：
+ 使用方括号`[]`创建
+ 使用`list()`函数创建
+ 使用`推导式`创建(更多推导式相关请看[Python推导式](#Python推导式))

```python
lst1 = [1,"7",2.589,(1,"2")]
lst2 = []

seq = (1,5,9,"7")
lst3 = list(seq)

print(lst1,type(lst1))
print(lst2,type(lst2))
print(lst3,type(lst3))

# 使用推导式创建
lst4 = [x**2 for x in (4,5,9,8,11) if x <= 10]
print(lst4)
```

以上代码的运行结果为：  
> [1, '7', 2.589, (1, '2')] &lt;class 'list'>
> [] &lt;class 'list'>
> [1, 5, 9, '7'] &lt;class 'list'>
> [16, 25, 81, 64]

#### 列表的嵌套

列表是可以嵌套的：  
```python
matrix = [
    [1,2,5],
    [2,7,8],
    [4,5,6,7,9],
    [2,9,7,11]
]
```

若要访问该列表的元素只需逐层访问即可：  
```python
print(matrix[2][0])

for row in matrix:
    for e in row:
        print(e, end=" ")
    print()
```

以上代码的输出结果为：  
> 4  
> 1 2 5  
> 2 7 8   
> 4 5 6 7 9   
> 2 9 7 11 


#### 列表的索引和截取

因为列表也是一个序列，所以我们可以使用[`切片运算符`](#切片运算符)来进行索引和截取：  

***索引***
```python
list_test = [1, 5, 6, 7, 11, 3]

# 正向索引
print(list_test[2])   # 读取第3个元素 / 读取索引为2的元素
# 逆向索引
print(list_test[-1])   # 读取倒数第1个元素
```

以上代码的输出结果为：  
> 6  
> 3

***截取***
```python
list_test =  [6, 8, 9, 7, 2, 23, 1, 1, 13]
print(list_test)

# 截取
print(list_test[1:])     # 截取列表从索引为1的元素开始后的所有元素
print(list_test[1:3])    # 截取列表索引区间[1,3)，即第二到第三个元素间的片段
print(list_test[1:-1])    # 截取列表第二到倒数第二个元素间的片段
print(list_test[1:-1:2])   # 从1到-1索引元素方向，按每次索引递增步长的趋势截取，此时步长为2，即隔位截取
print(list_test[1:-1:-1])  # 从1到-1索引元素方向，按每次索引递增步长=-1的趋势截取，很明显此时无截取片段
print(list_test[-1:1:-1])   # 从-1到1索引元素方向，按每次索引递增步长=-1的趋势截取，即为反向截取
print(list_test[-1::-1])   # 第二个参数为空，表示移动到列表末尾
```

以上代码的运行结果为：  
> [6, 8, 9, 7, 2, 23, 1, 1, 13]  
> [8, 9, 7, 2, 23, 1, 1, 13]  
> [8, 9]  
> [8, 9, 7, 2, 23, 1, 1]  
> [8, 7, 23, 1]  
> []  
> [13, 1, 1, 23, 2, 7, 9]   
> [13, 1, 1, 23, 2, 7, 9, 8, 6]   

#### 修改列表元素

因为列表属于可变的数据类型，所以其元素可以修改：  
```python
lst = [1,5,6]
lst[1] = 7
print(lst)
```

以上代码的输出结果为：  
> [1,7,6]

***使用del***删除列表元素：  

使用del可以根据索引删除一个元素或者一个切割

```python
lst = [1,4,5,9,8,3,1,2,0,11]
del lst[0]
print(lst)

del lst[1:-3:2]
print(lst)

del lst[:]
print(lst)
```

以上代码的输出结果为：  
> [4, 5, 9, 8, 3, 1, 2, 0, 11]  
> [4, 9, 3, 2, 0, 11]  
> []

#### 列表运算

列表运算满足[序列运算规则](#序列运算)：  

***`+运算`***

```python
print([2, 6, 9, 8, 2] + [1, 6, 11])
```

以上代码的输出结果为：  
> [2, 6, 9, 8, 2, 1, 6, 11]

***`*运算`***

```python
print(["a", "b"] * 4)
```

以上代码的输出结果为：  
> ['a', 'b', 'a', 'b', 'a', 'b', 'a', 'b']


***`in运算`***

```python
print(5 in [1,2,6,4,6,5])
```

以上代码的运行结果为：  
> True

***`切片运算`***
见上文的[列表的索引和截取](#列表的索引和截取)

#### 列表遍历

列表遍历将使用[循环语句](#Python循环语句).

<!--TODO: enumerate()  -->

> 使用[enumerate()](#enumerate)函数可以得到索引和对应值

```py
lst = [1,2,7,3,6,4]

for i in lst:
    print(i,end=" ")

for i,value in enumerate(lst):
    print(i,value)
```

以上代码的运行结果为：  
> 1 2 7 3 6 4
> 1 2
> 2 7
> 3 3
> 4 6
> 5 4

<!--TODO: zip()  -->
如果要同时遍历多个列表，可以使用[zip()](#zip)函数：  
```python
questions = ['name', 'quest', 'favorite color']
answers = ['lancelot', 'the holy grail', 'blue']
for q, a in zip(questions, answers):
    print('What is your {0}?  It is {1}.'.format(q, a))
```

以上代码的输出结果为：  
> What is your name?  It is lancelot.  
> What is your quest?  It is the holy grail.  
> What is your favorite color?  It is blue.

#### 常用函数

| 序号 | 方法 | 返回值/描述 |
| :-: | :--: | :---------- |
| 1 | [len()](#len) | 返回列表的`长度` |
| 2 | [max()](#max) | 返回列表的`最大的元素` |
| 3 | [min()](#min) | 返回列表的`最小的元素` |
|  | ----- | ***列表操作 方法*** |
| 1 | [reverse()](#reverse) | `lst.reverse()`,`反向列表`中元素 |
| 2 | [append()](#append) | `lst.append(obj)`,在lst列表`末尾添加`新的对象obj |
| 3 | [pop()](#pop) | `lst.pop(index=-1)`,`移除列表中的一个元素`（默认最后一个元素），并且返回该元素的值 |
| 4 | [count()](#count) | `lst.count(obj)`,统计obj`元素`在列表lst中`出现的次数` |
| 5 | [extend()](#extend) | `lst.extend(seq)`,在lst`列表末尾`一次性`追加另一个序列`seq中的多个值（用新列表扩展原来的列表） |
| 6 | [index()](#index) | `lst.index(obj)`,从lst列表中找出obj值的`第一个匹配项的索引`位置 |
| 7 | [remove()](#remove) | `lst.remove(obj)`,`移除`列表中某个值的`第一个匹配项` |
| 8 | [insert()](#insert) | `lst.insert(index,obj)`,将对象obj`插入列表指定索引位置` |
| 9 | [sort()](#sort) | `lst.sort(key=None,reverse=False)`,对原列表进行`排序` |
| 10 | [clear()](#clear) | `lst.clear()`,`清空列表` |
| 11 | [copy()](#copy) | `lst.copy()`,`复制列表` |

<!-- TODO: list常用函数 -->

************************************

### Set集合

集合（set）是一个无序的不重复元素序列。  
在Python中是可变的数据结构之一。

#### 创建集合
可以使用大括号 `{ }` 或者 `set()` 函数创建集合  
> 注意：创建一个空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。

基本功能是进行成员关系测试和删除重复元素。

```python
set1 = {1,5,6}
set2 = set([1,2,63,7,5,1])

print(set1)
print(set2)
```

以上代码的输出结果为：  
> {1, 5, 6}
> {1, 2, 5, 7, 63}

集合还可以通过推导式来创建(更多推导式相关请看[Python推导式](#Python推导式))

```python
set1 = {x ** 2 for x in (2, 4, 6)}
print(set1)
```

以上代码的输出结果为：  
> {4, 16, 36}

#### 操作集合
##### 添加元素
```python
set1 = {1,5,9,8}

set1.add(2)
print(set1)

set1.add(1)
print(set1)

set1.update({11,13})
print(set1)

set1.update(['1','2'],['3','4'])
print(set1)
```

以上代码的运行结果为：  
> {1, 2, 5, 8, 9}  
> {1, 2, 5, 8, 9}  
> {1, 2, 5, 8, 9, 11, 13}  
> {1, 2, 5, '3', 8, 9, 11, 13, '4', '2', '1'}  

##### 移除元素
```python
set1 = {3,6,8,9,2,7}
set1.remove(3)
print(set1)

set1.discard('4')   # 使用discard移除不存在的元素不会发生错误
print(set1)

x = set1.pop()
print(x)
print(set1)

set1.remove('4')  # 使用remove移除不存在的元素会发生错误
```

以上代码的输出结果为：  
> {2, 6, 7, 8, 9}
> {2, 6, 7, 8, 9}
> 2
> {6, 7, 8, 9}
> Traceback (most recent call last)
> test.py in &lt;module>
> ----> set1.remove('4')
> 
> KeyError: '4'

#### 集合运算

***`数学集合运算`***

```python
a = set('abracadabra')
b = set('alacazam')
print(a)
print(b)
print(f"a-b = {a-b}")   # 差集
print(f"a|b = {a|b}")   # 并集
print(f"a&b = {a&b}")   # 交集
print(f"a^b = {a^b}")   # 异或集
```

以上代码的输出结果为：  
> {'a', 'b', 'd', 'r', 'c'}
> {'a', 'c', 'l', 'm', 'z'}
> a-b = {'r', 'd', 'b'}
> a-b = {'a', 'b', 'd', 'r', 'c', 'l', 'm', 'z'}
> a-b = {'c', 'a'}
> a-b = {'l', 'b', 'd', 'r', 'm', 'z'}

***`in运算`***
```python
print(3 in {3,5})
```

以上代码的输出结果为：  
> True

#### 常用函数

| 序号 | 方法 | 返回值/描述 |
| :-: | :--: | :---------- |
| 1 | [add()](#add) | `set1.add(x)`为集合`添加元素`x |
| 2 | [clear()](#clear) | `set1.clear()` `清空集合`中的所有元素 |
| 3 | [copy()](#copy) | `set1.copy()`返回一个集合的`拷贝` |
| 4 | [difference()](#difference) | `set1.difference(set2)`返回多个`集合的差集`,即包含在set1，但不在set2的元素集 |
| 5 | [difference_update()](#difference_update) | `set1.difference_update(set2)`用于`移除两个集合中都存在的元素` |
| 6 | [discard()](#discard) | `set1.discard(value)` 用于`移除指定的集合元素` |
| 7 | [intersection()](#intersection) | `set1.intersection(set2[,...])` 返回集合的`交集` |
| 8 | [intersection_update()](#intersection_update) | `set1.intersection_update(set2[,...])` 用于将`交集更新`到原集合中 |
| 9 | [isdisjoint()](#isdisjoint) | `set1.sidisjoint(set2)` 判断两个集合`是否包含相同的元素`，如果没有返回 True，否则返回 False |
| 10 | [issubset()](#issubset) | `set1.issubset(set2)` 判断指定集合`是否为`该方法参数集合的`子集`。 |
| 11 | [issuperset()](#issuperset) | `set1.issuperset(set2)` 判断指定集合`是否为`该方法参数集合的`父集`。 |
| 12 | [pop()](#pop) | `set1.pop()` 用于`随机移除`一个元素。 |
| 13 | [remove()](#remove) | `set1.remove(x)` `移除指定元素` |
| 14 | [symmetric_difference()](#symmetric_difference) | `set1.symmetric_difference(set2)` 返回两个集合中`不重复的元素集合`，即会移除两个集合中都存在的元素 |
| 15 | [symmetric_difference_update()](#symmetric_difference_update) | `set1.symmetric_difference_update(set2)` 返回两个集合中`不重复的元素集合并更新至原集合` |
| 16 | [union()](#union) | `set1.union(set2)` 返回两个集合的`并集` |
| 17 | [update()](#update) | `set1.update(x)` 给集合`添加元素` | 

<!-- TODO： set常用函数 -->


************************************

### Dictionary字典

> 列表是有序的对象集合，字典是无序的对象集合。两者之间的区别在于：字典当中的元素是通过键来存取的，而不是通过偏移存取。

字典是一种映射类型，字典用 { } 标识，它是一个无序的 键(key) : 值(value) 的集合。

`键(key)必须使用不可变类型。`

在同一个字典中，键(key)必须是唯一的。

#### 创建字典

创建字典的方法有三种：  
+ 使用花括号`{}`创建
+ 使用`dict()`方法创建
+ 使用`推导式`创建

```python
dict1 = {"1": "2", "code": "3", 1: 5}

# 直接从键值对序列中构建字典
dict2 = dict([('Baidu', 1), ('Google', 2), ('Taobao', 3)])
dict3 = dict(Baidu=1, Google=2, Taobao=3)

# 使用推导式创建字典
dict4 = {x: x**2 for x in (2, 4, 6)}

# 创建空字典
dict5 = {}
dict6 = dict()

print(dict1)
print(dict2)
print(dict3)
print(dict4)
print(dict5)
print(dict6)

```

以上代码的输出结果为：  
> {'1': '2', 'code': '3', 1: 5}  
> {'Baidu': 1, 'Google': 2, 'Taobao': 3}  
> {'Baidu': 1, 'Google': 2, 'Taobao': 3}  
> {2: 4, 4: 16, 6: 36}  
> {}  
> {}  

#### 字典操作

***`访问值`***
要访问字典的值只需要将键值填入字典后的方括号中：  
```Python
dict1 = {'a':1,'b':2}
print(dict1['a'])
```

以上代码的输出结果为：  
> 1

如果访问的键值不存在，则会返回错误：  
```python
dict1 = {'a':1,'b':2}
print(dict1['c'])
```

以上代码的输出结果为：  
> KeyError                                  Traceback (most recent call last)
> test.py in &lt;module>
>       1 dict1 = {'a':1,'b':2}
> ----> 2 print(dict1['c'])
> 
> KeyError: 'c'

***`修改/创建值`***
要修改字典的值，直接将对应的键值修改即可：  
```python
dict1 = {'a':1,'b':2}
dict1['a'] = 3
print(dict1['a'])
```

以上代码的输出结果为：  
> 3  

如果该键不存在，则将直接创建这个键值对：  
```python
dict1 = {'a':1,'b':2}
dict1['c'] = 3
print(dict1)
```

以上代码的输出结果为：  
> {'a': 1, 'b': 2, 'c': 3}

***`删除值`***
```python
dict1 = {"a": 1, "b": 2, "c": 3}

# 删除键
del dict1['a']
print(dict1)

# 清空字典
dict1.clear()
print(dict1)

# 删除字典
del dict1
print(dict1)
```

以上代码的输出结果为：  
> {'b': 2, 'c': 3}  
> {}  
> \----------------------------------------------------   
> NameError                                 Traceback (most recent call last)
> test.py in &lt;module>
>      11 # 删除字典
>      12 del dict1
> ---> 13 print(dict1)
> 
> NameError: name 'dict1' is not defined

***`in运算`***
判断key是否在字典中已存在.
```Python
dict1 ={'k':1}
print('a' in dict1)
```

以上代码的输出结果为： 
> False


#### 常用函数


| 序号 | 方法 | 返回值/描述 |
| :-: | :--: | :---------- |
| 1 | [len()](#len) | `len(dict)` 求字典的`键值对个数` |
| 2 | [clear()](#clear) | `dict.clear()` `清空字典` |
| 3 | [copy()](#copy) | `dict.copy()` 返回一个字典的`浅复制` |
| 4 | [fromkeys()](#fromkeys) | `dict.fromkeys(seq[,val])` 返回一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值，默认为None |
| 5 | [get()](#get) | `dict.get(key,default=None)` 返回`指定键的值`，如果`键不在字典中返回` default 设置的`默认值` |
| 6 | [items()](#items) | `dict.items()` 以列表返回一个视图对象 |
| 7 | [keys()](#keys) | `dict.keys()` 返回一个键视图对象 |
| 8 | [values()](#values) | `dict.values()` 返回一个值视图对象 |
| 9 | [setdefault()](#setdefault) | `dict.setdefault()` 和get()类似, 但如果`键不存在于字典中`，将会`添加键`并将`值设为default` |
| 10 | [update()](#update) | `dict.update(dict2)` 把字典dict2的键/值对更新到dict里 |
| 11 | [pop()](#pop) | `dict.pop(key[,default])` 删除字典给定键 key 所对应的值，`返回值为被删除的值`。key值必须给出。 否则，返回default值。 |
| 12 | [popitem()](#popitem) | `dict.popitem()` 随机返回并删除字典中的最后一对键和值。 |

<!-- TODO:dict常用函数 -->

****************************************************

## Python运算符

Python的运算符可以分为以下几类：  

+ [算术运算符](#算术运算符)
+ [比较(关系)运算符](#比较(关系)运算符)
+ [赋值运算符](#赋值运算符)
+ [逻辑运算符](#逻辑运算符)
+ [位运算符](#位运算符)
+ [成员运算符](#成员运算符)
+ [身份运算符](#身份运算符)

> [运算符优先级](#运算符优先级)

### 算术运算符
| 运算符 | 描述 |
| :--: | :---- |
| + | 加 |
| - | 减 |
| * | 乘 |
| / | 除 |
| % | 取模 |
| ** | 幂 |
| // | 整除 |

### 比较(关系)运算符
| 运算符 | 描述 |
| :--: | :---- |
| == | 等于 |
| > | 大于 |
| < | 小于 |
| != | 不等于 |
| >= | 大于等于 |
| <= | 小于等于 |

### 赋值运算符
| 运算符 | 描述 | 说明 |
| :--: | :----- | :--- |
| = | 简单的赋值运算符 | 将运算符右侧的值赋予左侧 |
| += | 加法赋值运算符 | a+=b等价于a=a+b |
| -= | 减法赋值运算符 | a-=b等价于a=a-b |
| *= | 乘法赋值运算符 | a*=b等价于a=a*b |
| /= | 除法赋值运算符 | a/=b等价于a=a/b |
| %= | 取模赋值运算符 | a%=b等价于a=a%b |
| **= | 幂赋值运算符 | a**=b等价于a=a**b |
| //= | 取整赋值运算符 | a//=b等价于a=a//b |
| := | 海象运算符 | `Python3.8`版本新增运算符。可在表达式内部为变量赋值。|

> 海象运算符的使用：  
> ```python
> if (n := len(a)) > 10:  
>    print(f"List is too long ({n} elements, expected <= 10)")
> ```


### 逻辑运算符

| 运算符 | 逻辑表达式 | 描述 |
| :--: | :----- | :----- | 
| and | x and y	| 布尔"与" - 如果 x 为 False，x and y 返回 x 的值，否则返回 y 的计算值。|
| or | x or y | 布尔"或" - 如果 x 是 True，它返回 x 的值，否则它返回 y 的计算值。|
| not | not x | 布尔"非" - 如果 x 为 True，返回 False 。如果 x 为 False，它返回 True。 |

### 位运算符
按位运算符是把数字看作二进制来进行计算的。

| 运算符 | 描述 | 实例 |
| :--: | :---| :---- |
| `&` | 按位与运算符：参与运算的两个值,如果两个相应位都为1,则该位的结果为1,否则为0 | `(a & b)` 输出结果 12 ，二进制解释： 0000 1100 |
| `|` | 按位或运算符：只要对应的二个二进位有一个为1时，结果位就为1。否则为0  | `(a | b)` 输出结果 61 ，二进制解释： 0011 1101 |
| `^` | 按位异或运算符：当两对应的二进位相异时，结果为1，否则为0  | `(a ^ b)` 输出结果 49 ，二进制解释： 0011 0001 |
| `~` | 按位取反运算符：对数据的每个二进制位取反,即把1变为0,把0变为1。~x 类似于 -x-1 | `(~a )` 输出结果 -61 ，二进制解释： 1100 0011， 在一个有符号二进制数的补码形式。|
| `<<` | 左移动运算符：运算数的各二进位全部左移若干位，由"<<"右边的数指定移动的位数，高位丢弃，低位补0。| `a << 2` 输出结果 240 ，二进制解释： 1111 0000 |
| `>>` | 右移动运算符：把">>"左边的运算数的各二进位全部右移若干位，">>"右边的数指定移动的位数 | `a >> 2` 输出结果 15 ，二进制解释： 0000 1111 |


### 成员运算符

| 运算符 | 描述 |
| :--: | :------- |
| in | 如果在指定的序列中找到值返回 True，否则返回 False。|
| not in | 如果在指定的序列中没有找到值返回 True，否则返回 False。|

### 身份运算符
身份运算符用于比较两个对象的存储单元

| 运算符 | 描述 | 实例 |
| :---: | :----- | :----- |
| is | is 是判断两个标识符是不是引用自一个对象 | x is y, 类似 id(x) == id(y) , 如果引用的是同一个对象则返回 True，否则返回 False |
| is not | is not 是判断两个标识符是不是引用自不同对象 | x is not y ， 类似 id(a) != id(b)。如果引用的不是同一个对象则返回结果 True，否则返回 False。|

### 运算符优先级

以下表格列出了从最高到最低优先级的所有运算符：

| 运算符 | 描述 |
| :--: | :------ |
| `**` | 指数 (最高优先级) |
| `~ + -` | 按位翻转, 一元加号和减号 (最后两个的方法名为 +@ 和 -@) |
| `* / % //` | 乘，除，求余数和取整除 |
| `+ -` | 加法减法 |
| `>> <<` | 右移，左移运算符 |
| `&` | 位 'AND' |
| `^ |` | 位运算符 |
| `<= < > >=`	 | 比较运算符 |
| `== !=` | 等于运算符 |
| `= %= /= //= -= += *= **=` | 赋值运算符 |
| `is is not` | 身份运算符 |
| `in not in` | 成员运算符 |
| `not and or` | 逻辑运算符 |

**************************************

## Python条件控制

Python条件控制使用if、elif和else关键字,一般流程图如下： 
![if流程图](if-1.png)

共有三种模式：  

***if***
```python
if (<condition_expr>) :
    # statement_block_1
# statement_block_other
```
***if-else***
```python
if (<condition_expr>) :
    # statement_block_1
else :
    # statement_block_else
# statement_block_other
```
***if-elif-else***
```python
if (<condition_expr_1>) :
    # statement_block_1
elif (<condition_expr_2>) :
    # statement_block_2
# ……
else :
    # statement_block_else
# statement_block_other
```
上述代码的流程如下：  
![if-elif-else](if-2.png)

Python条件控制还支持if条件的`嵌套`：  
```python
if (<expr>):
    if (<expr_2>):
        # statement_block_1
    else:
        # statement_block_2
    # statement_block_3
else:
    # ……
```

*************************************

## Python循环语句

循环语句将在条件成立时循环执行。流程图如下：  
![loop-1](loop-1.jpg)
Python的循环语句有两种形式：  

***`while`***
> 循环语句可以有 else 子句，它在穷尽列表(以for循环)或条件变为 false (以while循环)导致循环终止时被执行，但循环被 break 终止时不执行。  

```python
while (<condition_expr>):
    # loop_statement_block
else:
    # false_statement
```

> 可以使用`while True`来实现无限循环

***`for`***
Python for 循环可以遍历任何可迭代对象([序列](#Python序列sequence))
```python
for <variable> in <sequence>:
    <statements>
else:
    <statements>
```
经常和for配合的一个函数为[range()](#range):  
range()函数会生成一个数字序列：  
```python
>>>for i in range(5):
...     print(i)
...
0
1
2
3
4
```


如果要提前结束循环，需要使用关键字`break`跳出当前循环:  
```python
x = 10
while x >= 3 :
    print(x, end=" ")
    if x == 6 :
        break
    x -= 1
```
以上代码循环到x==6时就会停止:  
> 10 9 8 7 6  

如果只是跳过一次循环，使用关键字`continue`可以跳过本次循环，进入下次循环:  
```python
x = 10
while x >= 3:
    x -= 1
    if x == 6:
        continue
    print(x, end=" ")
```
以上代码的输出结果为：  
> 9 8 7 5 4 3 2

break和continue在循环中的作用如下图：  
![break-continue](break-continue.jpg)
> break 语句可以跳出 for 和 while 的循环体。如果你从 for 或 while 循环中终止，任何对应的循环 else 块将不执行。  
> continue 语句被用来告诉 Python 跳过当前循环块中的剩余语句，然后继续进行下一轮循环。

*****************************************

## Python序列sequence

### 序列运算
<!-- TODO: 序列运算符 https://blog.csdn.net/bcj296050240/article/details/46313709-->
#### +运算/拼接
#### *运算/复制
#### in运算
#### 切片运算符

***************************************

## Python迭代器与生成器

### 迭代器iterator
迭代是访问集合元素的一种方式。  
迭代器是一个可以记住遍历的位置的对象。 
迭代器对象从集合的第一个元素开始访问，直到所有的元素被访问完结束。迭代器只能往前`不会后退`。   

迭代器有两个基本的方法：`iter()` 和 `next()`。  
iter()用于创建迭代器对象，next()用于控制迭代器前进。  
字符串，列表或元组对象都可用于创建迭代器：  
```python
lst = [1,5,6,4,7,8]
it = iter(lst)   # 创建迭代器对象
print(type(it))
print(next(it))  # 输出迭代器的下一个元素
print(next(it))
```
以上代码的输出结果为：  
> &lt;class 'list_iterator'>
> 1
> 5

迭代器对象可以使用常规for语句进行遍历：  
```python
lst = [1,2,3,4,5]
it = iter(lst)
for i in it:
    print(x, end=" ")
```
以上代码的输出结果为：  
> 1 2 3 4 5 

#### 自定义迭代器
把一个类作为一个迭代器使用需要在类中实现两个方法 \_\_iter\_\_() 与 \_\_next\_\_() 。  
如果你已经了解面向对象编程，就知道类都有一个构造函数，Python 的构造函数为 \_\_init\_\_(), 它会在对象初始化的时候执行。有关面向对象编程请看：[Python面向对象](#Python面向对象)  
`__iter__()` 方法返回一个特殊的迭代器对象， 这个迭代器对象实现了 \_\_next\_\_() 方法并通过 StopIteration 异常标识迭代的完成。  
`__next__()` 方法会返回下一个迭代器对象。  

> ***`StopIteration`***
> StopIteration 异常用于标识迭代的完成，防止出现无限循环的情况，在 \_\_next\_\_() 方法中我们可以设置在完成指定循环次数后触发 StopIteration 异常来结束迭代。 

以下实例将创建一个返回数字的迭代器，初始值为 1，逐步递增 1：  
```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    if self.a <= 20:    # 设置循环上限
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration
 
myclass = MyNumbers()
myiter = iter(myclass)
 
for x in myiter:
  print(x, end=" ")
```
执行输出结果为：  
> 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 

****************************

### 生成器generator

在Python中，使用了`yield`的函数被称为生成器。  
跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个迭代器。  
在调用生成器运行的过程中，每次遇到 yield 时函数会`暂停并保存当前所有的运行信息`，***返回 yield 的值***, 并在下一次执行 next() 方法时从当前位置继续运行。  

以下实例使用生成器实现斐波那契数列：  
```python
def fibonacci(n): # 生成器函数 - 斐波那契
    a, b, counter = 0, 1, 0
    while True:
        if (counter > n): 
            return
        yield a
        a, b = b, a + b
        counter += 1
f = fibonacci(10) # f 是一个迭代器，由生成器返回生成
 
while True:
    try:
        print (next(f), end=" ")
    except StopIteration:
        break
```
以上代码的输出结果为：  
> 0 1 1 2 3 5 8 13 21 34 55

*****************************************************

## Python函数

函数是组织好的，可重复使用的，用来实现单一，或相关联功能的代码段。  
函数能提高应用的模块性，和代码的重复利用率。  

除了之前见过的Python的内建函数外，我们还可以自己创建函数，也就是自定义函数。

### 定义一个函数

函数的组成有以下几条规则:  
+ 函数以`def`关键字开头，后接`函数标识符`名称和`参数列表`
+ 函数内容以冒号`:`开始，下面的函数体缩进
+ 以`return [表达式]`结束函数，并选择性返回一个值给调用方，不带任何表达式的return相当于返回None

下图是一个简单的函数形式说明:  
![函数说明](function-1.png)
总结来说，Python的函数语法格式如下：  
```Python
def 函数名(参数列表):
    函数体
```

### 参数

在之前我们知道了Python有两种数据类型：可变类型和不可变类型，而对Python的`参数传递`来说也对应着两种：  
+ **可变类型**：类似C++的引用传递，如传递列表、字典时，传递的是“真正的”对象，如果在函数内部修改了这个对象，函数外部也会收到影响而改变。  
+ **不可变类型**：类似C++的值传递，不可变的类型对象传递的只是他们的值，无法影响到外部的对象，在函数内部修改该类型的值，是新生成一个对象修改。

> python 中一切都是对象，严格意义我们不能说值传递还是引用传递，我们应该说传不可变对象和传可变对象。

Python的函数`参数`共有下面四种类型：  
+ 必需参数
+ 关键字参数
+ 默认参数
+ 不定长参数

***`必需参数`***
必需参数须以正确的顺序传入函数。调用时的数量必须和声明时的一样。  
***`关键字参数`***
关键字参数和函数调用关系紧密，函数调用使用关键字参数来确定传入的参数值。  
使用关键字参数允许函数调用时参数的顺序与声明时不一致，因为 Python 解释器能够用参数名匹配参数值。  
***`默认参数`***
调用函数时，如果没有传递参数，则会使用默认参数。
***`不定长参数`***
你可能需要一个函数能处理比当初声明时更多的参数。这些参数叫做不定长参数，和上述 2 种参数不同，声明时不会命名。基本语法如下：  
```py
def functionname([formal_args,] [*var_args_tuple,] [**var_args_dict] ):
   function_suite
   return [expression]
```
加了星号 * 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。  
加了两个星号 ** 的参数会以字典的形式导入。

下面结合函数的使用来理解这四种参数类型：  

### 函数的使用
使用函数只需要直接使用函数名并传入对应参数就可以调用了。

```python
def function1(a,b,c):
    print(a,b,c)
    return
    
function1(1,2,3)  # 必需参数的使用，参数按顺序对应传入
function1(1, c = "5", b = 2)  # 关键字参数的使用，参数在使用时可以直接使用关键字，且不必按顺序传入

def function2(a,b,c = 5):   # 默认参数，在函数声明时指定其默认值
    print(a,b,c)
    return

function2(2,3)       # 默认参数在调用时不指定则使用默认值

def function3(a,b,*args_tuple):   # 不定长参数，传入时先按顺序给必需参数赋值，多余参数将以元组/字典的方式存放传入
    print(a,b,args_tuple)
    return

function3(1,2,3,4,5,6)

def function4(a,b,**args_dict):   # 不定长参数，传入时先按顺序给必需参数赋值，多余参数将以元组/字典的方式存放传入
    print(a,b,args_dict)
    return

function4(1,2,c = 3,d = 4,e = 5,f = 6)
```

以上代码的输出结果为：  
> 1 2 3  
> 1 2 5  
> 2 3 5  
> 1 2 (3, 4, 5, 6)  
> 1 2 {'c': 3, 'd': 4, 'e': 5, 'f': 6}  

声明函数时，参数中星号 * 可以单独出现，如果单独出现星号 * 后的参数`必须用关键字`传入。
```Python
def function1(a,b,*,c):
    print(a,b,c)
    return

function1(1,2,c=5)
```

以上代码的输出结果为：  
> 1 2 5

### 匿名函数

Python使用lambda关键字来创建匿名函数。  
匿名函数不需要像普通函数一样使用def来声明，它是一个表达式，仅仅能在lambda表达式中封装有限的逻辑进去。  
lambda 函数拥有自己的命名空间，且不能访问自己参数列表之外或全局命名空间里的参数。  

lambda 函数的语法只包含一个语句，如下：  
```Python
lambda [arg1 [,arg2,.....argn]]:expression
```

使用实例来增进理解：  
```python
sum = lambda arg1,arg2:arg1+arg2    # 一个简单的匿名函数使用

print(sum(1,2))
```

以上代码的输出结果为：  
> 3

### return语句
return作为函数的结束语句，可以选择性地返回一个表达式，没有表达式的return返回None。  
```python
def function1(a,b):
    return a+b

c = function1(1,2)
print(c)
```

以上代码的输出结果为：  
> 3

### 强制位置参数
Python3.8 新增了一个函数形参语法` / `用来指明符号前的函数形参必须使用必需指定位置参数，不能使用关键字参数的形式。
在以下的例子中，形参 a 和 b 必须使用指定位置参数，c 或 d 可以是位置形参或关键字形参，而 e 和 f 要求为关键字形参:  
```python
def f(a, b, /, c, d, *, e, f):
    print(a, b, c, d, e, f)

f(10, 20, 30, d=40, e=50, f=60)  # 这种使用方式是正确的
# 下面两种是错误的使用
f(10, b=20, c=30, d=40, e=50, f=60)   # b 不能使用关键字参数的形式
f(10, 20, 30, 40, 50, f=60)           # e 必须使用关键字参数的形式
```
****************************************

## Python推导式

Python的推导式应用于简化规律的列表或元组等序列的创建：  
每个推导式都在 for 之后跟一个表达式，然后有零到多个 for 或 if 子句。返回结果是一个根据表达从其后的 for 和 if 上下文环境中生成出来的序列。  
> 需要注意的是，使用括号的元组推导式创建后得到的对象是生成器generator对象，需要进一步转换。


简单语法是：  
```Python
new_lst = [var for var in varrange if varexpr]
```

比如我们想得到一个偶数数列：  
```python
lst = [x for x in range(20) if x % 2 == 0]

print(lst)

tup = (x*2 for x in range(10))   # 括号生成的是生成器对象

print(type(tup))
print(tuple(tup))
```

以上代码的输出结果为：  
> [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
> &lt;class 'generator'>
> (0, 2, 4, 6, 8, 10, 12, 14, 16, 18)

推导式的更多使用建议自己上手尝试一下：  
```python 
lst = [y for y in (x * 3 for x in range(10)) if y % 2 == 1]

print(lst)

lst = [[x, y] for x in range(5) for y in range(5)]

print(lst)

ve = ["x","xx","xxx","xxxx"]
lst = [len(v) for v in ve]  # 推导式还可以对匿名变量使用函数

print(lst)

lst = [str(round(355/113, i)) for i in range(1, 6)]   # 使用复杂表达式和嵌套函数

print(lst)
```

以上代码的输出结果为：  
> [3, 9, 15, 21, 27]
> [[0, 0], [0, 1], [0, 2], [0, 3], [0, 4], [1, 0], [1, 1], [1, 2], [1, 3], [1, 4], [2, 0], [2, 1], [2, 2], [2, 3], [2, 4], [3, 0], [3, 1], [3, 2], [3, 3], [3, 4], [4, 0], [4, 1], [4, 2], [4, 3], [4, 4]]
> [1, 2, 3, 4]
> ['3.1', '3.14', '3.142', '3.1416', '3.14159']

***********************

## Python模块

模块是一个包含所有你定义的函数和变量的文件，其后缀名是.py。  
模块可以被别的程序引入，以使用该模块中的函数等功能。这也是使用 python 标准库的方法。

下面是一个使用 python 标准库中模块的例子。
```python 
import sys
 
print('命令行参数如下:')
for i in sys.argv:
   print(i)

print('\n\nPython 路径为：', sys.path, '\n')
```

> + import sys 引入 python 标准库中的 sys.py 模块；这是引入某一模块的方法。  
> + sys.argv 是一个包含命令行参数的列表。  
> + sys.path 包含了一个 Python 解释器自动查找所需模块的路径的列表。  

### import语句

想使用 Python 源文件，只需在另一个源文件里执行 import 语句，语法如下：  
```python
import module1[,module2...]
```

当解释器遇到import语句，如果模块在当前的搜索路径就会被导入。  

下面是自定义模块的使用:  
这里先定义一个模块  
```python
# file_name:  test_module.py

def function(a,b):
    return a+b

print('file_name: test_module.py')
```
然后再其他文件里导入
```python
# file_name:  test.py

import test_module

print('file_name: test.py')

print(test_module.function(1,2))     # 使用模块定义的方法
```

以上代码的运行结果为：    
> file_name: test_module.py
> file_name: test.py
> 3

可以看到，在导入模块的时候会自动运行一遍模块的代码。并且我们可以调用模块内定义的函数。  

并且一个模块只会被导入一次，不管你执行了多少次import。这样可以防止导入模块被一遍又一遍地执行。  
![模块只会被导入一次，执行一次](module-1.png)

> 当我们使用import语句的时候，Python解释器是怎么找到对应的文件的呢？  
这就涉及到Python的搜索路径，搜索路径是由一系列目录名组成的，Python解释器就依次从这些目录中去寻找所引入的模块。    
这看起来很像环境变量，事实上，也可以通过定义环境变量的方式来确定搜索路径。  
搜索路径是在Python编译或安装的时候确定的，安装新的库应该也会修改。  
搜索路径被存储在sys模块中的path变量，我们可以直接在终端输出查看搜索路径：  
```python
import sys

print(sys.path)
```

以上代码的输出结果为：  
> ['g:\\Codes\\Python\\testpy', 'c:\\Users\\Administrator\\.vscode\\extensions\\ms-toolsai.jupyter-2021.11.1001550889\\pythonFiles', 'c:\\Users\\Administrator\\.vscode\\extensions\\ms-toolsai.jupyter-2021.11.1001550889\\pythonFiles\\lib\\python', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39\\python39.zip', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39\\DLLs', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39\\lib', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39', '', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39\\lib\\site-packages', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39\\lib\\site-packages\\win32', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39\\lib\\site-packages\\win32\\lib', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39\\lib\\site-packages\\Pythonwin', 'C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python39\\lib\\site-packages\\IPython\\extensions', 'C:\\Users\\Administrator\\.ipython']

sys.path 输出是一个列表，其中第一项是当前目录。  

如果你打算经常使用一个函数，你可以把它赋给一个本地的名称：  
```python
import test_module

fun = test_module.function

print(fun(1,2))
```

### from...import语句

Python 的 from 语句让你从模块中导入一个指定的部分到当前命名空间中，语法如下：  
```Python
from modname import name1[, name2[, ... nameN]]
```
这个声明不会把整个模块导入到当前的命名空间中，它只会将某模块里的某个成员（函数、变量）引入进来。 
 
而如果要把一个模块所有成员导入当前的命名空间中，语法如下：  
```python
from modname import *
```

这提供了一个简单的方法来导入一个模块中的所有项目。但是那些由单一下划线（_）开头的名字不在此例，如'\_a'此类。
然而这种声明不该被过多地使用。因为引入的其它来源的命名，很可能覆盖了已有的定义。

### 深入模块

前面我们知道了模块在第一次被导入的时候会被解释器自动执行一遍代码。  
我们一般使用这些可执行代码来初始化模块。  
每个模块有各自独立的符号表，在模块内部为所有的函数当作全局符号表来使用。  
所以，模块的作者可以放心大胆的在模块内部使用这些全局变量，而不用担心把其他用户的全局变量搞混。  
从另一个方面，当你确实知道你在做什么的话，你也可以通过 `modname.itemname` 这样的表示法来访问模块内的函数。  

但是需要注意：  
> 在导入其他模块的命名时，要注意和本空间的冲突，因为引入的其它来源的命名，很可能覆盖了已有的定义。  

### __name__属性

一个模块被另一个程序第一次引入时，其主程序将运行。如果我们想在模块被引入时，模块中的某一程序块不执行，我们可以用\_\_name\_\_属性来使该程序块仅在该模块自身运行时执行。  
> 注意是前后`两个下划线`

```python
# file_name:  test_module.py
if __name__ == '__main__':
    print('test_module_main')
else:
    print('file_name: test_module.py')
```

每个模块都有一个\_\_name\_\_属性，当其值是'\_\_main\_\_'时，表明该模块自身在运行，否则是被引入。

### dir()函数

内置的函数 [`dir()`](#dir) 可以找到模块内定义的所有名称。以一个字符串列表的形式返回:  
```python
import test_module,sys
print(dir(test_module))
print(dir(sys))
```

以上代码的输出结果为：  
> ['\_\_builtins\_\_', '\_\_cached\_\_', '\_\_doc\_\_', '\_\_file\_\_', '\_\_loader\_\_', '\_\_name\_\_', '\_\_package\_\_', '\_\_spec\_\_', 'function']  
> ['\_\_breakpointhook\_\_', '\_\_displayhook\_\_', '\_\_doc\_\_', '\_\_excepthook\_\_', '\_\_interactivehook\_\_', '\_\_loader\_\_', '\_\_name\_\_', '\_\_package\_\_', '\_\_spec\_\_', '\_\_stderr\_\_', '\_\_stdin\_\_', '\_\_stdout\_\_', '\_\_unraisablehook\_\_', '\_base\_executable', '\_clear\_type\_cache', '\_current\_frames', '\_debugmallocstats', '\_enablelegacywindowsfsencoding', '\_framework', '\_getframe', '\_git', '\_home', '\_xoptions', 'addaudithook', 'api\_version', 'argv', 'audit', 'base_exec_prefix', 'base_prefix', 'breakpointhook', 'builtin_module_names', 'byteorder', 'call_tracing', 'copyright', 'displayhook', 'dllhandle', 'dont_write_bytecode', 'exc_info', 'excepthook', 'exec_prefix', 'executable', 'exit', 'flags', 'float_info', 'float_repr_style', 'get_asyncgen_hooks', 'get_coroutine_origin_tracking_depth', 'getallocatedblocks', 'getdefaultencoding', 'getfilesystemencodeerrors', 'getfilesystemencoding', 'getprofile', 'getrecursionlimit', 'getrefcount', 'getsizeof', 'getswitchinterval', 'gettrace', 'getwindowsversion', 'hash_info', 'hexversion', 'implementation', 'int_info', 'intern', 'is_finalizing', 'maxsize', 'maxunicode', 'meta_path', 'modules', 'path', 'path_hooks', 'path_importer_cache', 'platform', 'platlibdir', 'prefix', 'ps1', 'ps2', 'ps3', 'pycache_prefix', 'set_asyncgen_hooks', 'set_coroutine_origin_tracking_depth', 'setprofile', 'setrecursionlimit', 'setswitchinterval', 'settrace', 'stderr', 'stdin', 'stdout', 'thread_info', 'unraisablehook', 'version', 'version_info', 'warnoptions', 'winver']

如果没有给定参数，那么 dir() 函数会罗列出当前定义的所有名称:
```Python
print(dir())
```

> ['\_\_annotations\_\_', '\_\_builtins\_\_', '\_\_cached\_\_', '\_\_doc\_\_', '\_\_file\_\_', '\_\_loader\_\_', '\_\_name\_\_', '\_\_package\_\_', '\_\_spec\_\_']

### 其他模块

除了本章使用到的自定义模块和sys模块，Python还有其他的一些内置模块，可以查看[Python库参考文档](#Python库参考文档)。  

有些模块直接被构建在解析器里，这些虽然不是一些语言内置的功能，但是他却能很高效的使用，甚至是系统级调用也没问题。  
这些组件会根据不同的操作系统进行不同形式的配置，比如 winreg 这个模块就只会提供给 Windows 系统。  
应该注意到这有一个特别的模块 sys ，它内置在每一个 Python 解析器中。变量 sys.ps1 和 sys.ps2 定义了主提示符和副提示符所对应的字符串:  
```python
import sys
print(sys.ps1)
print(sys.ps2)
```

### 包

包是一种管理 Python 模块命名空间的形式，采用"点模块名称"。  
比如一个模块的名称是 A.B， 那么他表示一个包 A中的子模块 B 。  
就好像使用模块的时候，你不用担心不同模块之间的全局变量相互影响一样，采用点模块名称这种形式也不用担心不同库之间的模块重名的情况。  

在导入一个包的时候，Python 会根据 sys.path 中的目录来寻找这个包中包含的子目录。  
目录只有包含一个叫做 \_\_init\_\_.py 的文件才会被认作是一个包，主要是为了避免一些滥俗的名字（比如叫做 string）不小心的影响搜索路径中的有效模块。
最简单的情况，放一个空的 :file:\_\_init\_\_.py就可以了。  
当然这个文件中也可以包含一些初始化代码或者为（将在后面介绍的） __all__变量赋值。  

注意当使用 from package import item 这种形式的时候，对应的 item 既可以是包里面的子模块（子包），或者包里面定义的其他名称，比如函数，类或者变量。  
import 语法会首先把 item 当作一个包定义的名称，如果没找到，再试图按照一个模块去导入。如果还没找到，抛出一个 :exc:ImportError 异常。  
反之，如果使用形如 import item.subitem.subsubitem 这种导入形式，除了最后一项，都必须是包，而最后一项则可以是模块或者是包，但是不可以是类，函数或者变量的名字。  

如果我们使用 from sound.effects import * 会发生什么呢？  
Python 会进入文件系统，找到这个包里面所有的子模块，然后一个一个的把它们都导入进来。  
但这个方法在 Windows 平台上工作的就不是非常好，因为 Windows 是一个不区分大小写的系统。  
在 Windows 平台平台上，我们无法确定一个叫做 ECHO.py 的文件导入为模块是 echo 还是 Echo，或者是 ECHO。  
为了解决这个问题，我们只需要提供一个精确包的索引。  
导入语句遵循如下规则：如果包定义文件 \_\_init\_\_.py 存在一个叫做 \_\_all\_\_ 的列表变量，那么在使用 from package import * 的时候就把这个列表中的所有名字作为包内容导入。  
作为包的作者，可别忘了在更新包之后保证 \_\_all\_\_ 也更新了啊。  
\_\_all\_\_是一个存储模块名字符串的列表。  

*************************************

## Python输入输出

再前面我们已经接触过Python的输入[input()](#input)和输出[print()](#print)了，本章主要是介绍输入输出的进阶技巧。  

### 输出格式美化

Python两种输出值的方式: 表达式语句和 print() 函数。  
第三种方式是使用文件对象的 write() 方法，标准输出文件可以用 sys.stdout 引用。  
如果你希望输出的形式更加多样，可以使用 str.format() 函数来格式化输出值。  
如果你希望将输出的值转成字符串，可以使用 repr() 或 str() 函数来实现。  
> + str()： 函数返回一个用户易读的表达形式。
> + repr()： 产生一个解释器易读的表达形式。

下面是在Python解释器的运行说明，可以更好的帮忙理解str()和repr()的区别：  
```Python
>>> a = '1' 
>>> str(a)
'1'
>>> repr(a)
"'1'"
>>> print(a)
1
>>> print(str(a))
1
>>> print(repr(a))
'1'
>>> s = f'{str(a)},{repr(a)}'
>>> print(s)
1,'1'
>>> #  repr() 函数可以保留转义字符串中的特殊字符
>>> hello = 'hello, world\n'      
>>> hellos = repr(hello)
>>> print(hellos)
'hello, world\n'
>>> hellos_1 = str(hello)
>>> print(hellos_1)
hello, world

>>> repr((x, y, ('Go','Python')))      
"(32.5, 40000, ('Go', 'Python'))"
```

关于str()和repr()的更多区别请参见[str()和repr()的区别](str()和repr()的区别)

其他关于字符串格式化内容请参见: [字符串格式化](#字符串格式化)

### 读取输入

Python 提供了 input() 内置函数从标准输入读入一行文本，默认的标准输入是键盘。

***********************************************

## Python文件读写操作

### 读和写文件

[open()](#open)函数将会返回一个file对象，其基本语法如下：  
```python
open(filename, mode)
```

+ filename : 包含了你要访问的文件的字符串值。
+ mode : 决定了打开文件的模式（只读，写入，追加）等。所有可取值见如下的完全列表。这个参数是非强制的，默认文件访问模式为只读(r)。

不同模式打开文件的完全列表：  

| 模式 | 描述 |
| :-: | :----- |
| r | 以`只读`方式打开文件。文件的指针将会放在文件的`开头`。这是`默认`模式。 |
| rb | 以`二进制`格式打开一个文件用于`只读`。文件指针将会放在文件的`开头`。 |
| r+ | 打开一个文件用于`读写`。文件指针将会放在文件的`开头`。 |
| rb+ | 以`二进制`格式打开一个文件用于`读写`。文件指针将会放在文件的`开头`。 |
| w | 打开一个文件只用于`写入`。如果该文件已`存在则打开`文件，并从`开头`开始编辑，即`原有内容会被删除`。如果该文件`不存在则创建`新文件。 |
| wb | 以`二进制`格式打开一个文件只用于`写入`。如果该文件已`存在则打开`文件，并从`开头`开始编辑，即`原有内容会被删除`。如果该文件`不存在则创建`新文件。 |
| w+ | 打开一个文件用于`读写`。如果该文件已`存在则打开`文件，并从`开头`开始编辑，即`原有内容会被删除`。如果该文件`不存在则创建`新文件。 |
| wb+ | 以`二进制`格式打开一个文件用于`读写`。如果该文件已`存在则打开`文件，并从`开头`开始编辑，即`原有内容会被删除`。如果该文件`不存在则创建`新文件。 |
| a | 打开一个文件用于`追加`。如果该文件已`存在`，文件指针将会放在文件的`结尾`。也就是说，新的内容将会被`写入到已有内容之后`。如果该文件`不存在则创建`新文件进行写入。 |
| ab | 以`二进制`格式打开一个文件用于`追加`。如果该文件已`存在`，文件指针将会放在文件的`结尾`。也就是说，新的内容将会被`写入到已有内容之后`。如果该文件`不存在则创建`新文件进行写入。 |
| a+ | 打开一个文件用于`读写`。如果该文件已`存在`，文件指针将会放在文件的`结尾`。文件打开时会是追加模式。如果该文件`不存在则创建`新文件用于读写。 |
| ab+ | 以`二进制格式`打开一个文件用于`读写`。如果该文件已`存在`，文件指针将会放在文件的`结尾`。如果该文件`不存在则创建`新文件用于读写。 |

总结来说模式的情况有三种：  
+ 基础模式： 也就是 `r` `w` `a` (read、write、append)
+ 二进制模式：  在基础模式上加上`b`表示以二进制格式打开文件(byte)
+ 读写模式：  在以上两种模式上加上`+`表示打开的文件可读写

| 模式 | r | r+ | w | w+ | a | a+ |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 读 | √ | √ |   | √ |   | √ |
| 写 |   | √ | √ | √ | √ | √ |
| 创建 |   |   | √ | √ | √ | √ |
| 覆盖 |   |   | √ | √ |   |   |
| 指针在开始 | √ | √ | √ | √ |   |   |
| 指针在结尾 |   |   |   |   | √ | √ |

![读写模式](rwa-1.png)

下面是一个读写文件的实例:  
```python
import traceback

f = None

try:
    f = open(r"testpy\test.txt", "r")
    print(f.read())
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test.txt", "w")
    f.write("w模式写入")
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test.txt", "r")
    print(f.read())
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test.txt", "a")
    f.write("a模式写入")
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test.txt", "r")
    print(f.read())
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test.txt", "w")
    f.write("w模式再写入")
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test.txt", "r")
    print(f.read())
    f.close()
except:
    traceback.print_exc()

```

以上代码的输出结果为：  
> Traceback (most recent call last):
>   File "\\testpy\\quick.py", line 6, in &lt;module>
>     f = open(r"testpy\\test.txt", "r")
> FileNotFoundError: [Errno 2] No such file or directory: 'testpy\\test.txt'
> w模式写入
> w模式写入a模式写入
> w模式再写入

可以看到下图文件结构的改变
![读写测试-前](rw_test_1.png)
![读写测试-后](rw_test_2.png)

以及可以看到，w模式的创建、a模式的附加、w模式的覆盖这几个特性。

> 这里有几个需要注意的点: 
> + 文件的路径，由于带有反斜杠\\，会被转义，所以需要使用r-string
> + 打开的文件需要使用f.close()关闭或者使用[with...as...](#with关键字)代码块
> + 读写文件通常需要在try...except里进行

如果你点开刚刚创建的这个test.txt，你可能会遇到下面的情况：  
![文字乱码](rw-problem.png)
文字乱码一般是编码问题。处理方法之一是更改打开文件的编码和我们写入的编码匹配：  
vscode选择右下角的编码格式改变：
![vscode选择编码](vscode.png)
![vscode选择编码-2](vscode-2.png)
![vscode选择编码-3](vscode-3.png)
![文字乱码解决](solute.png)

还有一种解决办法是在我们在用代码创建时，可以选择编码类型，在这里选择想要的编码：  
```python
f = open(r"testpy\test.txt", "w", encoding="utf-8")
# ...
f.close()
```


关于上面实例使用的文件对象的方法，请看下节。  

### 文件对象的方法
<!-- TODO: 文件对象方法 -->

#### [`f.read()`](#read)

为了读取一个文件的内容，调用 f.read(size), 这将读取一定数目的数据, 然后作为字符串或字节对象返回。  
size 是一个可选的数字类型的参数。 当 size 被忽略了或者为负, 那么该文件的所有内容都将被读取并且返回。  

```python
import traceback

f = None

try:
    f = open(r"testpy\test.txt", "w")
    f.write("写入字符串")
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test.txt", "r")
    print(f.read(2))
    print(f.read(1))
    f.close()
except:
    traceback.print_exc()

```
以上代码的输出结果为：  
> 写入  
> 字

可以看到同一个文件对象read()读取的时候是接续读取而不是重头读取  
> 这是因为read()同时会向后移动指针size个字符.

但是这时候有人又有问题了：  
```python
import traceback

f = None

try:
    f = open(r"testpy\test.txt", "w")
    f.write("写入字符串")
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test.txt", "a+")
    print(f.read(2))
    f.close()
except:
    traceback.print_exc()

```

这个时候他说a+模式不是用于读写吗？为什么我这样写没有输出呢？
> 这个是因为read()方法读取的是当前指针后面的size个字符并返回，而a+模式的指针初始在文件末尾，所以读取不到任何字符。

如果你打开文件的方式没有读的权限，那么会报出以下的错误：  
```python
import traceback

f = None

try:
    f = open(r"testpy\test.txt", "w")
    print(f.read())
    f.close()
except:
    traceback.print_exc()

```

> Traceback (most recent call last): 
>   File "\\testpy\\quick.py", line 18, in &lt;module>  
>     print(f.read())
> `io.UnsupportedOperation: not readable`

#### [`f.readline()`](#readline)
f.readline() 会从文件中读取单独的一行。换行符为 '\n'。f.readline() 如果返回一个空字符串, 说明已经已经读取到最后一行。

```python
import traceback

f = None

try:
    f = open(r"testpy\test2.txt", "a", encoding="utf-8")
    f.write("写入字符串1\n")
    f.close()
except:
    traceback.print_exc()

try:
    f = open(r"testpy\test2.txt", "r", encoding="utf-8")
    print(repr(f.readline()))
    print(repr(f.readline()))
    f.close()
except:
    traceback.print_exc()

```

以上代码的输出结果为：  
> '写入字符串\n'  
> '写入字符串1\n'  

可以看到调用readline()和read()一样都会向后移动指针

还可以使用迭代文件对象的方式遍历每一行：  
```python
import traceback

try:
    # 使用with...as在代码块结束时会自动关闭文件对象
    with open(r"testpy\test2.txt", "r", encoding="utf-8") as f:
        for line in f:
            print(line, end="")
except:
    traceback.print_exc()

```

以上代码的输出结果为：  
> 写入字符串  
> 写入字符串1

#### [`f.readlines()`](#readlines)

f.readlines() 将返回该文件中包含的所有行。  
如果设置可选参数 sizehint, 则读取指定长度的字节, 并且将这些字节按行分割。

```python
import traceback

f = None

try:
    f = open(r"testpy\test2.txt", "r", encoding="utf-8")
    print(f.readlines())
    f.close()
except:
    traceback.print_exc()

```

以上代码的输出结果为：  
> ['写入字符串\n', '写入字符串1']

#### [`f.write()`](#write)

f.write(string) 将 string 写入到文件中, 然后返回写入的字符数。
```Python
import traceback

try:
    with open(r"testpy\test2.txt", "w", encoding="utf-8") as f:
        print(f'写入{f.write("写入测试")}个字符')
except:
    traceback.print_exc()

```

以上代码的输出结果为：  
> 写入4个字符

#### [`f.tell()`](#tell)

f.tell() 返回文件对象当前游标所处的位置, 它是从文件开头开始算起的字节数。中文utf-8编码一个字占三个字节数

```python
import traceback

try:
    with open(r"testpy\test2.txt", "w", encoding="utf-8") as f:
        print(f'写入{f.write("写入测试")}个字符')
        print(f'当前游标处于第{f.tell()}字节处')
except:
    traceback.print_exc()

```

以上代码的输出结果为：  
> 写入4个字符  
> 当前游标处于第12字节处

一些常用编码一个字符所占的字节数：  
| 编码 | 中文 | 英文 | 其他说明 |
| :--: | :--: | :--: | :-- |
| ASCII | 2 | 1 |  |
| Unicode | 2 | 2 | 英文符号只占1个字节 |
| GB2312 | 2 | 2 | |
| GBK | 2 | 1 | |
| ISO-8859-1 | 1 | 1 | |
| UTF-8 | 3 | 1 | |
| UTF-16 | 2 | 2 | Unicode扩展区的一些汉字存储需要4个字节 |
| UTF-32 | 4 | 4 |  |

#### [`f.seek()`](#seek)

如果要改变文件游标当前的位置, 可以使用 f.seek(offset, from_what) 函数。

offset 是偏移量；
from_what 的值, 如果是 0 表示开头, 如果是 1 表示当前位置, 2 表示文件的结尾，例如：

+ seek(x,0) ： 从起始位置即文件首行首字符开始移动 x 个字符
+ seek(x,1) ： 表示从当前位置往后移动x个字符
+ seek(-x,2)：表示从文件的结尾往前移动x个字符
from_what 值默认为0，即文件开头。下面给出一个完整的例子：

```python
import traceback

try:
    with open(r"testpy\test2.txt", "w", encoding="utf-8") as f:
        print(f'写入{f.write("写入测试")}个字符')
        print(f"当前游标处于第{f.tell()}字节处")
        print(f.seek(0))
        print(f"当前游标处于第{f.tell()}字节处")
        print(f.seek(0, 2))
        print(f"当前游标处于第{f.tell()}字节处")
except:
    traceback.print_exc()

```

以上代码的输出结果为：  
> 写入4个字符  
> 当前游标处于第12字节处  
> 0  
> 当前游标处于第0字节处  
> 12  
> 当前游标处于第12字节处

#### [`f.close()`](#close)

在文本文件中 (那些打开文件的模式下没有 b 的), 只会相对于文件起始位置进行定位。  
当你处理完一个文件后, 调用 f.close() 来关闭文件并释放系统的资源，如果尝试再调用该文件，则会抛出异常。


### pickle模块

python的pickle模块实现了基本的数据序列和反序列化。  
通过pickle模块的序列化操作我们能够将程序中运行的对象信息保存到文件中去，永久存储。  
通过pickle模块的反序列化操作，我们能够从文件中创建上一次程序保存的对象。  

下面通过一个简单实例来说明pickle模块：  
```python
import pickle

# 使用pickle模块将数据对象保存到文件
data1 = {"a": [1, 2.0, 3, 4 + 6j], "b": ("string", u"Unicode string"), "c": None}

output = open("data.pkl", "wb")

selfref_list = [1, 2, 3]
selfref_list.append(selfref_list)

# Pickle dictionary using protocol 0.
pickle.dump(data1, output)

# Pickle the list using the highest protocol available.
pickle.dump(selfref_list, output, 1)

output.close()
```

上面的实例使用pickle模块将数据对象保存到文件，使用到的方法是：  
```python
pickle.dump(obj, file, [,protocol])
```

它的作用是序列化对象，并将结果数据流写入到文件对象中。参数protocol是序列化模式，默认值为0，表示以文本的形式序列化。protocol的值还可以是1或2，表示以二进制的形式序列化。

```python
import pickle

pkl_file = open("data.pkl", "rb")

# 使用pickle模块从文件中重构python对象
data1 = pickle.load(pkl_file)
print(data1)
data2 = pickle.load(pkl_file)
print(data2)

pkl_file.close()
```

以上代码的输出结果为：  
> {'a': [1, 2.0, 3, (4+6j)], 'b': ('string', 'Unicode string'), 'c': None}  
> [1, 2, 3]

上面的实例使用pickle模块从文件中重构python对象，使用到的接口是：  
```python
any_x = pickle.load(file)
```

*************************

## Python os模块
<!-- TODO: os模块方法 -->

### os模块常用方法

[os模块](#Python-os模块方法)提供了非常丰富的方法用来处理文件和目录。常用的方法如下表所示：  

<table>
<thead>
<tr>
<th style = "text-align : center">
方法
</th>
<th style = "text-align : center">
实例
</th>
<th style = "text-align : center">
输出
</th>
<th style = "text-align : center">
描述
</th>
</tr>
</thead>
<tbody>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[access()](#access)
</td>
<td style = "vertical-align : middle;">

```python
import os

print(os.access("./testpy/test.txt", os.F_OK))
print(os.access("./testpy/test.txt1111", os.F_OK))
print(os.access("./testpy/data.pkl", os.R_OK))
print(os.access("./testpy/test.pkl", os.W_OK))
print(os.access("./testpy/test.pkl", os.X_OK))

```
</td>
<td style = "vertical-align : middle;">

```python
True
False
True
False
False
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
检验文件/路径的权限模式
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[getcwd()](#getcwd)
</td>
<td style = "vertical-align : middle;">

```python
import os
# 返回你的当前工作目录
print(os.getcwd())
```
</td>
<td style = "vertical-align : middle;">

```python
g:\Codes\Python\testpy
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
返回当前工作目录
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[chdir()](#chdir)
</td>
<td style = "vertical-align : middle;">

```python
import os

print(os.getcwd())
os.chdir("../")
print(os.getcwd())
```
</td>
<td style = "vertical-align : middle;">

```python
g:\Codes\Python\testpy
g:\Codes\Python\
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
改变当前工作目录
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[chmod()](#chmod)
</td>
<td style = "vertical-align : middle;">

```python
import os, stat

print(os.access("./testpy/data.pkl", os.W_OK))
os.chmod("./testpy/data.pkl", stat.S_IREAD)
print(os.access("./testpy/data.pkl", os.W_OK))
```
</td>
<td style = "vertical-align : middle;">

```python
True
False
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
更改文件或目录的权限
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[open()](#open)
</td>
<td rowspan="4" style = "vertical-align : middle;">

```python
import os

fd = os.open("./testpy/test3.txt", os.O_CREAT | os.O_RDWR)
os.write(fd, str.encode("This is test\n"))
os.close(fd)

fd = os.open("./testpy/test3.txt", os.O_RDONLY)
print(os.read(fd, 10))
os.close(fd)
```
</td>
<td rowspan="4" style = "vertical-align : middle;">

```python
b'This is te'
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
打开一个文件，并且设置需要的打开选项
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[write()](#write)
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
写入字符串到文件描述符 fd中. 返回实际写入的字符串长度
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[read()](#read)
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
从文件描述符 fd 中读取最多 n 个字节，返回包含读取字节的字符串，文件描述符 fd对应文件已达到结尾, 返回一个空字符串。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[close()](#close)
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
关闭指定的文件描述符 fd
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[closerange()](#closerange)
</td>
<td style = "vertical-align : middle;">

```python
import os
fd = os.open("./test.txt",os.O_RDONLY)
os.closerange(fd,fd)
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
关闭所有文件描述符，从 fd_low (包含) 到 fd_high (不包含), 错误会忽略
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[dup()](#dup)
</td>
<td style = "vertical-align : middle;">

```python
import os

# 打开文件
fd = os.open("foo.txt", os.O_RDWR | os.O_CREAT)
# 复制文件描述符
d_fd = os.dup(fd)
# 使用复制的文件描述符写入文件
os.write(d_fd, "This is test".encode())
# 关闭文件
os.closerange(fd, d_fd)
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
复制文件描述符 fd
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[dup2()](#dup2)
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
将一个文件描述符 fd 复制到另一个 fd2
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[fdopen()](#fdopen)
</td>
<td style = "vertical-align : middle;">

```python
# os.fdopen()
# 用于通过文件描述符 fd 创建一个文件对象，并返回这个文件对象。
# 该方法是内置函数 open() 的别名;
# 可以接收一样的参数，唯一的区别是 fdopen() 的第一个参数必须是整型。
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
通过文件描述符 fd 创建一个文件对象，并返回这个文件对象
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[stat()](#stat)
</td>
<td style = "vertical-align : middle;" rowspan = "3">

```python
import os

path = "./testpy/test.txt"

print(os.stat(path))

info = os.lstat(path)

print(info)
print(f"st_uid = {info.st_uid}")

fd = os.open(path, os.O_RDWR)
info = os.fstat(fd)

print(info)
os.close(fd)
```
</td>
<td style = "vertical-align : middle;" rowspan = "3">

```python
os.stat_result(st_mode=33206, st_ino=1407374883563448, 
st_dev=2427623123, st_nlink=1, st_uid=0, st_gid=0, st_size=0, 
st_atime=1642992982, st_mtime=1642992982, st_ctime=1642908751)
os.stat_result(st_mode=33206, st_ino=1407374883563448, 
st_dev=2427623123, st_nlink=1, st_uid=0, st_gid=0, st_size=0, 
st_atime=1642992982, st_mtime=1642992982, st_ctime=1642908751)
st_uid = 0
os.stat_result(st_mode=33206, st_ino=1407374883563448, 
st_dev=2427623123, st_nlink=1, st_uid=0, st_gid=0, st_size=0, 
st_atime=1642992982, st_mtime=1642992982, st_ctime=1642908751)
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
获取path指定的路径的信息，功能等同于C API中的stat()系统调用。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[lstat()](#lstat)
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
像stat(),但是没有软链接
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[fstat()](#fstat)
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
返回文件描述符fd的状态，像stat()。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[fsync()](#fsync)
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
强制将文件描述符为fd的文件写入硬盘。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[link()](#link)
</td>
<td style = "vertical-align : middle;">

```python
os.link(src, dst)
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
创建硬链接，名为参数 dst，指向参数 src.该方法对于创建一个已存在文件的拷贝是非常有用的。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[listdir()](#listdir)
</td>
<td style = "vertical-align : middle;">

```python
import os
path = "./"
print(os.listdir(path))
```
</td>
<td style = "vertical-align : middle;">

```python
['.vscode', 'auto.py', 'data.pkl', 'dp1.py', 'foo.txt', 'test.py', 'test.txt', 'testpy', 'test_module.py', 'test_pack', 'unable', 'workspace.code-workspace', '__pycache__']
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
返回path指定的文件夹包含的文件或文件夹的名字的列表。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[makedirs()](#makedirs)
</td>
<td style = "vertical-align : middle;">

```python
import os

path = "./testpy/test_makedirs1/test_makedirs2/"

os.makedirs(path, 0o777)
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
递归文件夹创建函数。像mkdir(), 但创建的所有intermediate-level文件夹需要包含子文件夹。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[mkdir()](#mkdir)
</td>
<td style = "vertical-align : middle;">

```python
import os

path = "./testpy/test_makedirs1/test_makedirs2/test_mkdir"

os.mkdir(path)
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
os.mkdir() 方法用于以数字权限模式创建目录。默认的模式为 0777 (八进制)。
如果目录有多级，则创建最后一级，如果最后一级目录的上级目录有不存在的
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[pipe()](#pipe)
</td>
<td style = "vertical-align : middle;">

```python
import os

r,w = os.pipe()
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
os.pipe() 方法用于创建一个管道, 返回一对文件描述符(r, w) 分别为读和写。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[popen()](#popen)
</td>
<td style = "vertical-align : middle;">

```python
import os

with os.popen("mkdir test_popen","r",1) as f:
    print(f)
```
</td>
<td style = "vertical-align : middle;">

```python
<os._wrap_close object at 0x000001D8FC929430>
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
os.popen() 方法用于从一个命令command打开一个管道。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[system()](#system)
</td>
<td style = "vertical-align : middle;">

```python
import os

os.system(r"adb devices")
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
system()用于简单执行一个系统命令
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[remove()](#remove)
</td>
<td style = "vertical-align : middle;">

```python
import os

# 列出目录
print("目录为: %s" % os.listdir(os.getcwd() + "/testpy/"))

os.remove("./testpy/test.txt")

# 移除后列出目录
print("目录为: %s" % os.listdir(os.getcwd() + "/testpy/"))
```
</td>
<td style = "vertical-align : middle;">

```python
目录为: ['data.pkl', 'quick.py', 'quick2.py', 'test.txt', 'test1.txt', 'test2.txt', 'test3.txt', 'test_makedirs1', 'test_unicode.txt']
目录为: ['data.pkl', 'quick.py', 'quick2.py', 'test1.txt', 'test2.txt', 'test3.txt', 'test_makedirs1', 'test_unicode.txt']
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
删除路径为path的文件。如果path 是一个文件夹，将抛出OSError; 查看下面的rmdir()删除一个 directory。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[removedirs()](#removedirs)
</td>
<td style = "vertical-align : middle;">

```python
import os

os.removedirs(r"./testpy/test_makedirs1/test_makedirs2/test_mkdir")
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
递归删除目录。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[rmdir()](#rmdir)
</td>
<td style = "vertical-align : middle;">

```python
import os

os.rmdir(r"./testpy/test_makedirs1/test_makedirs2/test_mkdir")
```
</td>
<td style = "vertical-align : middle;">

```python

```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
删除path指定的空目录，如果目录非空，则抛出一个OSError异常。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[rename()](#rename)
</td>
<td style = "vertical-align : middle;">

```python
import os

print(os.listdir())

os.rename("test_pack", "test_rename")

print(os.listdir())
```
</td>
<td style = "vertical-align : middle;">

```python
['.vscode', 'auto.py', 'data.pkl', 'dp1.py', 'foo.txt', 'test.py', 'test.txt', 'testpy', 'test_module.py', 'test_pack', 'test_popen', 'unable', 'workspace.code-workspace', '__pycache__']
['.vscode', 'auto.py', 'data.pkl', 'dp1.py', 'foo.txt', 'test.py', 'test.txt', 'testpy', 'test_module.py', 'test_popen', 'test_rename', 'unable', 'workspace.code-workspace', '__pycache__']
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">

</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[renames()](#renames)
</td>
<td style = "vertical-align : middle;">

```python
import os
print ("当前目录为: %s" %os.getcwd())

# 列出目录
print ("目录为: %s"%os.listdir(os.getcwd()))

# 重命名 "aa1.txt"
os.renames("aa1.txt","newdir/aanew.txt")

print ("重命名成功。")

# 列出重命名的文件 "aa1.txt"
print ("目录为: %s" %os.listdir(os.getcwd()))
```
</td>
<td style = "vertical-align : middle;">

```python
当前目录为: /tmp
目录为:
 [  'a1.txt','resume.doc','a3.py','aa1.txt','Administrator','newdir','amrood.admin' ]
重命名成功。
目录为:
 [  'a1.txt','resume.doc','a3.py','Administrator','newdir','amrood.admin' ]
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
os.renames() 方法用于递归重命名目录或文件。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[walk()](#walk)
</td>
<td style = "vertical-align : middle;">

```python
import os

for root, dirs, files in os.walk(".", topdown=False):
    for name in files:
        print(os.path.join(root, name))
    for name in dirs:
        print(os.path.join(root, name))
```
</td>
<td style = "vertical-align : middle;">

```python
.\.vscode\settings.json
.\testpy\data.pkl
.\testpy\quick.py
.\testpy\quick2.py
.\testpy\test1.txt
.\testpy\test2.txt
.\testpy\test3.txt
.\testpy\test_unicode.txt
.\test_pack\test_py.py
.\test_pack\__init__.py
.\unable\__pycache__\un_test.cpython-39.pyc
.\unable\un_test.py
.\unable\__pycache__
.\__pycache__\test_module.cpython-39.pyc
.\auto.py
.\data.pkl
.\dp1.py
.\foo.txt
.\test.py
.\test.txt
.\test_module.py
.\workspace.code-workspace
.\.vscode
.\testpy
.\test_pack
.\test_popen
.\unable
.\__pycache__
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
os.walk() 方法用于通过在目录树中游走输出在目录中的文件名，向上或者向下。
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">

[pardir()](#pardir)
</td>
<td style = "vertical-align : middle;">

```python
import os
 
# 输出默认值 ..
print(os.pardir)
```
</td>
<td style = "vertical-align : middle;">

```python
..
```
</td>
<td style = "vertical-align : middle; text-align : left;white-space: nowrap;">
获取当前目录的父目录
</td>
</tr>

</tbody>
</table>

### path模块

os.path 模块主要用于获取文件的属性。  
以下是 os.path 模块的几种常用方法：  

| 方法 | 说明 |
| :--: | :------------------- |
| os.path.`abspath`(path) | 返回绝对路径 |
| os.path.`basename`(path) | 返回文件名 |
| os.path.`commonprefix`(list) | 返回list(多个路径)中，所有path共有的最长的路径 |
| os.path.`dirname`(path) | 返回文件路径 |
| os.path.`exists`(path) | 路径存在则返回True,路径损坏返回False |
| os.path.`expanduser`(path) | 把path中包含的"~"和"~user"转换成用户目录 |
| os.path.`expandvars`(path) | 根据环境变量的值替换path中包含的"$name"和"${name}" |
| os.path.`getatime`(path) | 返回最近访问时间（浮点型秒数） |
| os.path.`getmtime`(path) | 返回最近文件修改时间 |
| os.path.`getctime`(path) | 返回文件 path 创建时间 |
| os.path.`getsize`(path) | 返回文件大小，如果文件不存在就返回错误 |
| os.path.`isabs`(path) | 判断是否为绝对路径 |
| os.path.`isfile`(path) | 判断路径是否为文件 |
| os.path.`isdir`(path) | 判断路径是否为目录 |
| os.path.`islink`(path) | 判断路径是否为链接 |
| os.path.`ismount`(path) | 判断路径是否为挂载点 |
| os.path.`join`(path1[, path2[, ...]]) | 把目录和文件名合成一个路径 |
| os.path.`normcase`(path) | 转换path的大小写和斜杠 |
| os.path.`normpath`(path) | 规范path字符串形式 |
| os.path.`realpath`(path) | 返回path的真实路径 |
| os.path.`relpath`(path[, start]) | 从start开始计算相对路径 |
| os.path.`samefile`(path1, path2) | 判断目录或文件是否相同 |
| os.path.`sameopenfile`(fp1, fp2) | 判断fp1和fp2是否指向同一文件 |
| os.path.`samestat`(stat1, stat2) | 判断stat tuple stat1和stat2是否指向同一个文件 |
| os.path.`split`(path) | 把路径分割成 dirname 和 basename，返回一个元组 |
| os.path.`splitdrive`(path) | 一般用在 windows 下，返回驱动器名和路径组成的元组 |
| os.path.`splitext`(path) | 分割路径中的文件名与拓展名 |
| os.path.`walk`(path, visit, arg) | 遍历path，进入每个目录都调用visit函数，visit函数必须有3个参数(arg, dirname, names)，dirname表示当前目录的目录名，names代表当前目录下的所有文件名，args则为walk的第三个参数 |
| os.path.`supports_unicode_filenames` | 设置是否支持unicode路径名 |

<!--TODO: ### os.open()与open()的区别 -->

<!--TODO: ### os.popen()与os.system()的区别 -->

***************************

## Python错误与异常处理

Python有两种错误：语法错误和异常。  
Python [assert](#assert-断言)（断言）用于判断一个表达式，在表达式条件为 False 的时候触发异常。

### 语法错误
Python 的语法错误或者称之为解析错，会报出以下的错误：  

```python
print('a)

```

```python
line 1
    print('a)
             ^
SyntaxError: EOL while scanning string literal
```

```python
print('a') print('b')
```

```python
line 1
    print('a') print('b')
               ^
SyntaxError: invalid syntax
```

如上，程序会报出语法错误`SyntaxError`，后面跟着的是错误的提示信息。  
语法分析器会指出出错的一行，并且在最先找到的错误的位置标记上箭头。

### 异常

即便 Python 程序的语法是正确的，在运行它的时候，也有可能发生错误。运行期检测到的错误被称为异常。  
大多数的异常都不会被程序处理，都以错误信息的形式展现在这里:  

```Python
>>> 10 * (1/0)             # 0 不能作为除数，触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ZeroDivisionError: division by zero
>>> 4 + spam*3             # spam 未定义，触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'spam' is not defined
>>> '2' + 2               # int 不能与 str 相加，触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

异常类型和异常信息会显示出来，例子中的异常类型有：`ZeroDivisionError`、`NameError`、`TypeError`  
程序打印出异常发生的上下文的后面是错误信息，以调用栈的形式显示具体信息。
程序在运行到第一个错误或异常就会停止并打印出错误/异常信息，如果希望程序运行时遇到异常继续运行或者对异常做出反应，就要使用异常处理。

### 异常处理

异常处理的格式是：  
```python
try:
    <code_segment>
except [ErrorType]:
    <solute_segment>
[...
except:
    <solute_segment>
]
[else:
    <code_segment>]
[finally:
    <code_segment>]
```

异常处理的工作流程如下：
+ try代码块为要执行的代码，被先执行;
+ 如果在try代码块产生了异常，程序根据异常类型去到对应except处理区;
+ 如果没有对应处理区则会继续将异常向上抛出到主程序块，异常会在finally语句执行后被执行结束程序产生异常;
+ 如果try代码块没有产生异常则执行else代码块(如果有);
+ 最后执行finally代码块, finally 语句无论异常是否发生都会执行。

> 一个except子句可以同时处理多个异常，这些异常将被放在一个括号里成为一个元组，例如:
> ```python
> except (RuntimeError, TypeError, NameError):
>     pass
> ```

### 抛出异常

python使用raise关键字向上层抛出异常:  

```python
try:
    x = int(input("请输入一个小于10的数字"))
    if x >= 10:
        raise ValueError
except ValueError:
    print("输入数字大于等于10")
else:
    print("正确")
```

上面的例子中，如果输入的数字大于等于10就会自定义产生一个异常，被except检测处理。 
raise后面如果跟了具体的参数，它必须是一个异常的实例或者是异常的类（也就是 Exception 的子类）。  
raise后面如果不跟具体异常，这样会向上抛出`RuntimeError`:  
```python
try:
    x = int(input("请输入一个小于10的数字"))
    if x >= 10:
        raise
except RuntimeError:
    print("输入数字大于等于10")
else:
    print("正确")
```

异常输出：  
```python
Traceback (most recent call last):
  File "<stdin>" , line 4, in <module>
    raise
RuntimeError: No active exception to reraise
```

### 自定义异常

用户可以通过[继承](#继承)Exception类创建一个新的异常类。异常类继承自 Exception 类，可以直接继承，或者间接继承，例如:  
```Python
class MyError(Exception):
    def __init__(self, value):
        self.value = value

    def __str__(self):
        return repr(self.value)


try:
    raise MyError(0)
except MyError as e:
    print("error code:", e.value)

raise MyError("MyError")
```

以上代码的输出结果为：  
> error code: 0
> Traceback (most recent call last):
  File "&lt;stdin>", line 14, in &lt;module>
    raise MyError("MyError")
> \_\_main\_\_.MyError: 'MyError'  


> 大多数的异常的名字都以"Error"结尾，就跟标准的异常命名一样。

### assert(断言)

Python assert（断言）用于判断一个表达式，在表达式条件为 false 的时候触发异常。  
断言可以在条件不满足程序运行的情况下直接返回错误，而不必等待程序运行后出现崩溃的情况。  

语法格式为：  
```python
assert expression
```

等价于
```python
if not expression:
    raise AssertionError
```

assert 后面也可以紧跟参数:  
```python
assert expression [, arguments]
```

等价于
```python
if not expression:
    raise AssertionError(arguments)
```

下面是实例：  
```python
assert True
print("正常运行")
assert False
```

输出结果为：  
```python
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    assert False
AssertionError
```

带参数的实例：  
```python
assert 1>2, "1大于2是错误的"
```

```python
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    assert 1 > 2, "1大于2是错误的"
AssertionError: 1大于2是错误的
```

以下实例判断当前系统是否为 Linux，如果不满足条件则直接触发异常，不必执行接下来的代码：
```python
import sys
assert ('linux' in sys.platform), "该代码只能在 Linux 下执行"

# 接下来要执行的代码
```

### with关键字

Python 中的 with 语句用于异常处理，封装了 try…except…finally 编码范式，提高了易用性。  
with 语句使代码更清晰、更具可读性， 它简化了文件流等公共资源的管理。  
在处理文件对象时使用 with 关键字是一种很好的做法。  
我们可以看下以下几种代码实例：  
不使用 with，也不使用 try…except…finally
```python
file = open('./test.txt', 'w')
file.write('hello world !')
file.close()
```

以上代码如果在调用 write 的过程中，出现了异常，则 close 方法将无法被执行，因此资源就会一直被该程序占用而无法被释放。 接下来我们呢可以使用 try…except…finally 来改进代码：  

```python
file = open('./test.txt', 'w')
try:
    file.write('hello world')
finally:
    file.close()
```

以上代码我们对可能发生异常的代码处进行 try 捕获，发生异常时执行 except 代码块，finally 代码块是无论什么情况都会执行，所以文件会被关闭，不会因为执行异常而占用资源。

使用 with 关键字：
```python
with open('./test.txt', 'w') as file:
    file.write('hello world !')
```

使用 with 关键字系统会自动调用 f.close() 方法， with 的作用等效于 try/finally 语句是一样的。  
我们可以在执行 with 关键字后检验文件是否关闭：
```python
with open("./test.txt") as f:
    print(f.closed)
print(f.closed)
```

以上代码输出结果为：  
> False  
> True

with 语句实现原理建立在上下文管理器之上。  
上下文管理器是一个实现 \_\_enter\_\_ 和 \_\_exit\_\_ 方法的类。  
使用 with 语句确保在嵌套块的末尾调用 \_\_exit\_\_ 方法。  
这个概念类似于 try...finally 块的使用。

> 在文件对象中定义了 \_\_enter\_\_ 和 \_\_exit\_\_ 方法，即文件对象也实现了上下文管理器，首先调用 \_\_enter\_\_ 方法，然后执行 with 语句中的代码，最后调用 \_\_exit\_\_ 方法。 即使出现错误，也会调用 \_\_exit\_\_ 方法，也就是会关闭文件流。

<!-- TODO：traceback模块 -->
<!-- TODO: logging模块 -->

*****************************

## Python面向对象

### 面向对象技术简介

+ 类(Class): 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。
+ 方法：类中定义的函数。
+ 类变量：类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。
+ 数据成员：类变量或者实例变量用于处理类及其实例对象的相关的数据。
+ 方法重写：如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖（override），也称为方法的重写。
+ 局部变量：定义在方法中的变量，只作用于当前实例的类。
+ 实例变量：在类的声明中，属性是用变量来表示的，这种变量就称为实例变量，实例变量就是一个用 self 修饰的变量。
+ 继承：即一个派生类（derived class）继承基类（base class）的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待。例如，有这样一个设计：一个Dog类型的对象派生自Animal类，这是模拟"是一个（is-a）"关系（例图，Dog是一个Animal）。
+ 实例化：创建一个类的实例，类的具体对象。
+ 对象：通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。

### 定义类

```python
class ClassName:
    <statement-1>
    .
    .
    .
    <statement-N>
```

类实例化后，可以使用其属性，实际上，创建一个类之后，可以通过类名访问其属性。

### 类对象

类对象支持两种操作：属性引用和实例化。
属性引用使用和 Python 中所有的属性引用一样的标准语法：obj.name。
类对象创建后，类命名空间中所有的命名都是有效属性名。所以如果类定义是这样:  

```Python
class MyClass:
    """一个简单的类实例"""
    i = 12345
    def f(self):
        return 'hello world'

# 实例化类
x = MyClass()
 
# 访问类的属性和方法
print("MyClass 类的属性 i 为：", x.i)
print("MyClass 类的方法 f 输出为：", x.f())
```

以上代码的运行结果是：  
> MyClass 类的属性 i 为： 12345  
> MyClass 类的方法 f 输出为： hello world

类有一个名为 \_\_init\_\_() 的特殊方法（构造方法），该方法在类实例化时会自动调用，像下面这样：  

```python
def __init__(self):
    self.data = []
```

类定义了 \_\_init\_\_() 方法，类的实例化操作会自动调用 \_\_init\_\_() 方法。  
当然， \_\_init\_\_() 方法可以有参数，参数通过 \_\_init\_\_() 传递到类的实例化操作上。例如:

```python 
class Complex:
    def __init__(self, realpart, imagpart):
        self.r = realpart
        self.i = imagpart
x = Complex(3.0, -4.5)
print(x.r, x.i)   # 输出结果：3.0 -4.5
```

***self代表类的实例，而非类***
类的方法与普通的函数只有一个特别的区别——它们必须有一个额外的第一个参数名称, 按照惯例它的名称是 self。

```python
class Test:
    def prt(self):
        print(self)
        print(self.__class__)
 
t = Test()
t.prt()
```

以上代码的运行结果为：  
> &lt;\_\_main\_\_.Test instance at 0x0000025D089CCFD0>
> \_\_main\_\_.Test

从执行结果可以很明显的看出，self 代表的是类的实例，代表当前对象的地址，而 self.class 则指向类。

self 不是 python 关键字，我们把他换成其他也是可以正常执行的

### 类的方法

在类的内部，使用 def 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self, 且为第一个参数，self 代表的是类的实例。

```python
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
# 实例化类
p = people('sam',10,30)
p.speak()
```

以上代码的输出结果为：  
> sam 说: 我 10 岁。

### 继承

派生类的定义语法如下：  

```python
class DerivedClassName(BaseClassName):
    <statement-1>
    .
    .
    .
    <statement-N>
```

子类（派生类 DerivedClassName）会继承父类（基类 BaseClassName）的属性和方法。

BaseClassName（实例中的基类名）必须与派生类定义在一个作用域内。除了类，还可以用表达式，基类定义在另一个模块中时这一点非常有用:  
```python
class DerivedClassName(modname.BaseClassName):
```

单继承：  

```python
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 

s = student('ken',10,60,3)
s.speak()
```

以上代码的输出结果为：  
> ken 说: 我 10 岁了，我在读 3 年级

### 多继承

Python同样有限的支持多继承形式。多继承的类定义形如下例:  
```python
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>
```

需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。

```python
# 类定义
class people:
    # 定义基本属性
    name = ""
    age = 0
    # 定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    # 定义构造方法
    def __init__(self, n, a, w):
        self.name = n
        self.age = a
        self.__weight = w

    def speak(self):
        print("%s 说: 我 %d 岁。" % (self.name, self.age))


# 单继承示例
class student(people):
    grade = ""

    def __init__(self, n, a, w, g):
        # 调用父类的构函
        people.__init__(self, n, a, w)
        self.grade = g

    # 覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级" % (self.name, self.age, self.grade))


# 另一个类，多重继承之前的准备
class speaker:
    topic = ""
    name = ""

    def __init__(self, n, t):
        self.name = n
        self.topic = t

    def speak(self):
        print("我叫 %s，我是一个演说家，我演讲的主题是 %s" % (self.name, self.topic))


# 多重继承
class sample(speaker, student):
    a = ""

    def __init__(self, n, a, w, g, t):
        student.__init__(self, n, a, w, g)
        speaker.__init__(self, n, t)


test = sample("Tim", 25, 80, 4, "Python")
test.speak()  # 方法名同，默认调用的是在括号中参数位置排前父类的方法
```

以上代码的运行结果为：  
> 我叫 Tim，我是一个演说家，我演讲的主题是 Python

### 方法重写

如果你的父类方法的功能不能满足你的需求，你可以在子类重写你父类的方法，实例如下：

```python
class Parent:        # 定义父类
   def myMethod(self):
      print ('调用父类方法')
 
class Child(Parent): # 定义子类
   def myMethod(self):
      print ('调用子类方法')
 
c = Child()          # 子类实例
c.myMethod()         # 子类调用重写方法
super(Child,c).myMethod() # 用子类对象调用父类已被覆盖的方法
```
<!-- TODO: super() -->
[`super()`](#super) 函数是用于调用父类(超类)的一个方法。  
执行以上程序输出结果为：
> 调用子类方法  
> 调用父类方法

### 类属性和方法

**类的私有属性**
\_\_private\_attrs：两个下划线开头，声明该属性为私有，不能在类的外部被使用或直接访问。在类内部的方法中使用时 self.\_\_private\_attrs。

**类的方法**
在类的内部，使用 def 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self，且为第一个参数，self 代表的是类的实例。  
self 的名字并不是规定死的，也可以使用 this，但是最好还是按照约定使用 self。

**类的私有方法**
\_\_private\_method：两个下划线开头，声明该方法为私有方法，只能在类的内部调用 ，不能在类的外部调用。self.\_\_private\_methods。

```python
class JustCounter:
    __secretCount = 0  # 私有变量
    publicCount = 0    # 公开变量
 
    def count(self):
        self.__secretCount += 1
        self.publicCount += 1
        print (self.__secretCount)
 
counter = JustCounter()
counter.count()
counter.count()
print (counter.publicCount)
print (counter.__secretCount)  # 报错，实例不能访问私有变量
```

以上代码的输出结果为：  
> 1  
> 2  
> 2  
> Traceback (most recent call last):    
>   File "test.py", line 16, in &lt;module>  
>     print (counter.__secretCount)  # 报错，实例不能访问私有变量  
> AttributeError: 'JustCounter' object has no attribute '__secretCount'  

### 私有变量

那种仅限从一个对象内部访问的“私有”实例变量在 Python 中并不存在。 但是，大多数 Python 代码都遵循这样一个约定：带有一个下划线的名称 (例如 \_spam) 应该被当作是 API 的非公有部分 (无论它是函数、方法或是数据成员)。 这应当被视为一个实现细节，可能不经通知即加以改变。  
由于存在对于类私有成员的有效使用场景（例如避免名称与子类所定义的名称相冲突），因此存在对此种机制的有限支持，称为 名称改写。 任何形式为 \_\_spam 的标识符（至少带有两个前缀下划线，至多一个后缀下划线）的文本将被替换为 \_classname\_\_spam，其中 classname 为去除了前缀下划线的当前类名称。 这种改写不考虑标识符的句法位置，只要它出现在类定义内部就会进行。

名称改写有助于让子类重载方法而不破坏类内方法调用。

<!-- TODO：私有变量 -->

### 类的专有方法

+ \_\_init\_\_ : 构造函数，在生成对象时调用
+ \_\_del\_\_ : 析构函数，释放对象时使用
+ \_\_repr\_\_ : 打印，转换
+ \_\_setitem\_\_ : 按照索引赋值
+ \_\_getitem\_\_: 按照索引获取值
+ \_\_len\_\_: 获得长度
+ \_\_cmp\_\_: 比较运算
+ \_\_call\_\_: 函数调用
+ \_\_add\_\_: 加运算
+ \_\_sub\_\_: 减运算
+ \_\_mul\_\_: 乘运算
+ \_\_truediv\_\_: 除运算
+ \_\_mod\_\_: 求余运算
+ \_\_pow\_\_: 乘方

### 运算符重载

Python同样支持运算符重载，我们可以对类的专有方法进行重载，实例如下：

```python
class Vector:
   def __init__(self, a, b):
      self.a = a
      self.b = b
 
   def __str__(self):
      return 'Vector (%d, %d)' % (self.a, self.b)
   
   def __add__(self,other):
      return Vector(self.a + other.a, self.b + other.b)
 
v1 = Vector(2,10)
v2 = Vector(5,-2)
print (v1 + v2)
```

以上代码的运行结果为：  
> Vector(7,8)

********************************

## Python命名空间和作用域

### 命名空间

先看看官方文档的一段话：

> A namespace is a mapping from names to objects.Most namespaces are currently implemented as Python dictionaries。
> 
> 命名空间(Namespace)是从名称到对象的映射，大部分的命名空间都是通过 Python 字典来实现的。

命名空间提供了在项目中避免名字冲突的一种方法。各个命名空间是独立的，没有任何关系的，所以一个命名空间中不能有重名，但不同的命名空间是可以重名而没有任何影响。  
我们举一个计算机系统中的例子，一个文件夹(目录)中可以包含多个文件夹，每个文件夹中不能有相同的文件名，但不同文件夹中的文件可以重名。

一般有三种命名空间：  

+ 内置名称（built-in names）， Python 语言内置的名称，比如函数名 abs、char 和异常名称 BaseException、Exception 等等。
+ 全局名称（global names），模块中定义的名称，记录了模块的变量，包括函数、类、其它导入的模块、模块级的变量和常量。
+ 局部名称（local names），函数中定义的名称，记录了函数的变量，包括函数的参数和局部定义的变量。（类中定义的也是）

![命名空间](命名空间.png)

命名空间查找顺序:  
假设我们要使用变量 test，则 Python 的查找顺序为：**局部的命名空间去 -> 全局命名空间 -> 内置命名空间**。
如果找不到变量 test，它将放弃查找并引发一个 NameError 异常:

```python
NameError: name 'test' is not defined。
```

命名空间的生命周期：  
命名空间的生命周期取决于对象的作用域，如果对象执行完成，则该命名空间的生命周期就结束。   
因此，我们无法从外部命名空间访问内部命名空间的对象。

```python
# var1 是全局名称
var1 = 5
def some_func():
 
    # var2 是局部名称
    var2 = 6
    def some_inner_func():
 
        # var3 是内嵌的局部名称
        var3 = 7
```

如下图所示，相同的对象名称可以存在于多个命名空间中。

![命名空间-2](命名空间-2.png)

### 作用域

> A scope is a textual region of a Python program where a namespace is directly accessible. "Directly accessible" here means that an unqualified reference to a name attempts to find the name in the namespace.

作用域就是一个 Python 程序可以直接访问命名空间的正文区域。  
在一个 python 程序中，直接访问一个变量，会从内到外依次访问所有的作用域直到找到，否则会报未定义的错误。  
Python 中，程序的变量并不是在哪个位置都可以访问的，访问权限决定于这个变量是在哪里赋值的。  

变量的作用域决定了在哪一部分程序可以访问哪个特定的变量名称。Python 的作用域一共有4种，分别是：

+ L（Local）：最内层，包含局部变量，比如一个函数/方法内部。
+ E（Enclosing）：包含了非局部(non-local)也非全局(non-global)的变量。比如两个嵌套函数，一个函数（或类） A 里面又包含了一个函数 B ，那么对于 B 中的名称来说 A 中的作用域就为 nonlocal。
+ G（Global）：当前脚本的最外层，比如当前模块的全局变量。
+ B（Built-in）： 包含了内建的变量/关键字等，最后被搜索。

在局部找不到，便会去局部外的局部找（例如闭包），再找不到就会去全局找，再者去内置中找。

![作用域](作用域.png)

```python
g_count = 0  # 全局作用域
def outer():
    o_count = 1  # 闭包函数外的函数中
    def inner():
        i_count = 2  # 局部作用域
```

内置作用域是通过一个名为 builtin 的标准模块来实现的，但是这个变量名自身并没有放入内置作用域内，所以必须导入这个文件才能够使用它。在Python3.0中，可以使用以下的代码来查看到底预定义了哪些变量:  

```python
import builtins
print(dir(builtins))
```

以上代码的输出结果为：  
> ['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException', 'BlockingIOError', 'BrokenPipeError', 'BufferError', 'BytesWarning', 'ChildProcessError', 'ConnectionAbortedError', 'ConnectionError', 'ConnectionRefusedError', 'ConnectionResetError', 'DeprecationWarning', 'EOFError', 'Ellipsis', 'EnvironmentError', 'Exception', 'False', 'FileExistsError', 'FileNotFoundError', 'FloatingPointError', 'FutureWarning', 'GeneratorExit', 'IOError', 'ImportError', 'ImportWarning', 'IndentationError', 'IndexError', 'InterruptedError', 'IsADirectoryError', 'KeyError', 'KeyboardInterrupt', 'LookupError', 'MemoryError', 'ModuleNotFoundError', 'NameError', 'None', 'NotADirectoryError', 'NotImplemented', 'NotImplementedError', 'OSError', 'OverflowError', 'PendingDeprecationWarning', 'PermissionError', 'ProcessLookupError', 'RecursionError', 'ReferenceError', 'ResourceWarning', 'RuntimeError', 'RuntimeWarning', 'StopAsyncIteration', 'StopIteration', 'SyntaxError', 'SyntaxWarning', 'SystemError', 'SystemExit', 'TabError', 'TimeoutError', 'True', 'TypeError', 'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError', 'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning', 'ValueError', 'Warning', 'WindowsError', 'ZeroDivisionError', '\_\_build_class\_\_', '\_\_debug\_\_', '\_\_doc\_\_', '\_\_import\_\_', '\_\_loader\_\_', '\_\_name\_\_', '\_\_package\_\_', '\_\_spec\_\_', 'abs', 'all', 'any', 'ascii', 'bin', 'bool', 'breakpoint', 'bytearray', 'bytes', 'callable', 'chr', 'classmethod', 'compile', 'complex', 'copyright', 'credits', 'delattr', 'dict', 'dir', 'divmod', 'enumerate', 'eval', 'exec', 'exit', 'filter', 'float', 'format', 'frozenset', 'getattr', 'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int', 'isinstance', 'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'map', 'max', 'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow', 'print', 'property', 'quit', 'range', 'repr', 'reversed', 'round', 'set', 'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple', 'type', 'vars', 'zip']

Python 中只有模块（module），类（class）以及函数（def、lambda）才会引入新的作用域，其它的代码块（如 if/elif/else/、try/except、for/while等）是不会引入新的作用域的，也就是说这些语句内定义的变量，外部也可以访问.

```python
if True:
    test = "test"
print(test)
```

以上代码的输出结果为：  
> test

实例中 test 变量定义在 if 语句块中，但外部还是可以访问的。  
如果将 test 定义在函数中，则它就是局部变量，外部不能访问：

```python
def test_func():
    test = "test"
    return None

print(test)
```

以上代码的运行结果为：  
> Traceback (most recent call last):
>   File "&lt;stdin>", line 1, in &lt;module>
> NameError: name 'test' is not defined

从报错的信息上看，说明了 test 未定义，无法使用，因为它是局部变量，只有在函数内可以使用。

### 全局变量和局部变量

定义在函数内部的变量拥有一个局部作用域，定义在函数外的拥有全局作用域。  
局部变量只能在其被声明的函数内部访问，而全局变量可以在整个程序范围内访问。调用函数时，所有在函数内声明的变量名称都将被加入到作用域中。  

```python
total = 0 # 这是一个全局变量
# 可写函数说明
def sum( arg1, arg2 ):
    #返回2个参数的和."
    total = arg1 + arg2 # total在这里是局部变量.
    print ("函数内是局部变量 : ", total)
    return total
 
#调用sum函数
sum( 10, 20 )
print ("函数外是全局变量 : ", total)
```

以上实例输出结果：
> 函数内是局部变量 :  30   
> 函数外是全局变量 :  0

### global和nonlocal关键字

当内部作用域想修改外部作用域的变量时，就要用到 global 和 nonlocal 关键字了。

```python
num = 1
def fun1():
    global num  # 需要使用 global 关键字声明
    print(num) 
    num = 123
    print(num)
fun1()
print(num)
```

以上代码的运行结果为：  
> 1  
> 123  
> 123

如果要修改嵌套作用域（enclosing 作用域，外层非全局作用域）中的变量则需要 nonlocal 关键字了，如下实例：

```python
def outer():
    num = 10
    def inner():
        nonlocal num   # nonlocal关键字声明
        num = 100
        print(num)
    inner()
    print(num)
outer()
```

以上代码的运行结果为：  
> 100  
> 100

************************************

## Python标准库概览

### 操作系统接口

`os模块`提供了不少与操作系统相关联的函数。更多请参见：[Python os模块](#Python-os模块)和[Python os模块方法](#Python-os模块方法)

> 建议使用 "import os" 风格而非 "from os import *"。这样可以保证随操作系统不同而有所变化的 os.open() 不会覆盖内置函数 open()。

针对日常的文件和目录管理任务，`shutil模块`提供了一个易于使用的高级接口，更多请见：[Python shutil模块](Python-shutil模块方法)

### 文件通配符

`glob模块`提供了一个函数用于从目录通配符搜索中生成文件列表：  

```python
import glob
print(glob.glob('*.py'))
```

```python
['quick.py', 'quick2.py']
```

### 命令行参数

通用工具脚本经常调用命令行参数。这些命令行参数以链表形式存储于 sys 模块的 argv 变量。例如在命令行中执行 "python demo.py one two three" 后可以得到以下输出结果:  

```python
>>> import sys
>>> print(sys.argv)
['demo.py', 'one', 'two', 'three']
```

### 错误输出重定向和程序终止

sys 还有 stdin，stdout 和 stderr 属性，即使在 stdout 被重定向时，后者也可以用于显示警告和错误信息。   
大多脚本的定向终止都使用 "sys.exit()"。

```python
import sys

sys.stderr.write("stderr.write_test\n")

sys.exit()

print(0)
```

```
stderr.write_test

```

### 字符串正则匹配

`re模块`为高级字符串处理提供了正则表达式工具。对于复杂的匹配和处理，正则表达式提供了简洁、优化的解决方案:

```python
import re
print(re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest'))
print(re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat'))
```

以上代码的运行结果为：  
> ['foot', 'fell', 'fastest']   
> 'cat in the hat'

如果只需要简单的功能，应该首先考虑字符串方法，因为它们非常简单，易于阅读和调试:

```python
>>> 'tea for too'.replace('too', 'two')
'tea for two'
```

更多关于正则表达式表达见后文[正则表达式](#Python正则表达式)

### 数学

python提供了`math模块`对简单数学支持，以及`random模块`对随机数的支持。

### 访问互联网

有几个模块用于访问互联网以及处理网络通信协议。其中最简单的两个是用于处理从 urls 接收的数据的 urllib.request 以及用于发送电子邮件的 smtplib。

### 日期和时间

`datetime模块`为日期和时间处理同时提供了简单和复杂的方法。  
支持日期和时间算法的同时，实现的重点放在更有效的处理和格式化输出。
该模块还支持时区处理:  

```python
# dates are easily constructed and formatted
import datetime

now = datetime.date.today()
print(now)
print(datetime.date(2023, 12, 2))
print(now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B."))

# dates support calendar arithmetic
birthday = datetime.date(1964, 7, 31)
age = now - birthday
print(age.days)
```

```
2022-02-21
2023-12-02
02-21-22. 21 Feb 2022 is a Monday on the 21 day of February.
21024
```

### 数据压缩

以下模块直接支持通用的数据打包和压缩格式：zlib，gzip，bz2，zipfile，以及 tarfile。

```python
import zlib

s = b"witch which has which witches wrist watch"
print(len(s))

t = zlib.compress(s)
print(len(t))

print(zlib.decompress(t))
print(zlib.crc32(s))
```

```
41
37
b'witch which has which witches wrist watch'
226805979
```

### 性能度量

有些用户对了解解决同一问题的不同方法之间的性能差异很感兴趣。Python 提供了一个度量工具，为这些问题提供了直接答案。
例如，使用元组封装和拆封来交换元素看起来要比使用传统的方法要诱人的多,timeit 证明了现代的方法更快一些。

```python
>>> from timeit import Timer
>>> Timer('t=a; a=b; b=t', 'a=1; b=2').timeit()
0.57535828626024577
>>> Timer('a,b = b,a', 'a=1; b=2').timeit()
0.54962537085770791
```

相对于 timeit 的细粒度，profile 和 pstats 模块提供了针对更大代码块的时间度量工具。

### 测试模块

开发高质量软件的方法之一是为每一个函数开发测试代码，并且在开发过程中经常进行测试  
`doctest模块`提供了一个工具，扫描模块并根据程序中内嵌的文档字符串执行测试。  
测试构造如同简单的将它的输出结果剪切并粘贴到文档字符串中。   
通过用户提供的例子，它强化了文档，允许 doctest 模块确认代码的结果是否与文档一致:

```python
def average(values):
    """Computes the arithmetic mean of a list of numbers.

    >>> print(average([20, 30, 70]))
    40.0
    """
    return sum(values) / len(values)

import doctest
doctest.testmod()   # 自动验证嵌入测试
```

以上代码的运行结果为：  
> TestResults(failed=0, attempted=1)

`unittest模块`不像 doctest模块那么容易使用，不过它可以在一个独立的文件里提供一个更全面的测试集:

```python
import unittest

class TestStatisticalFunctions(unittest.TestCase):

    def test_average(self):
        self.assertEqual(average([20, 30, 70]), 40.0)
        self.assertEqual(round(average([1, 5, 7]), 1), 4.3)
        self.assertRaises(ZeroDivisionError, average, [])
        self.assertRaises(TypeError, average, 20, 30, 70)

unittest.main() # Calling from the command line invokes all tests
```

*************************************

## Python正则表达式

正则表达式是一个特殊的字符序列，它能帮助你方便的检查一个字符串是否与某种模式匹配。  
`re 模块`使 Python 语言拥有全部的正则表达式功能。  

compile 函数根据一个模式字符串和可选的标志参数生成一个正则表达式对象。该对象拥有一系列方法用于正则表达式匹配和替换。  
re 模块也提供了与这些方法功能完全一致的函数，这些函数使用一个模式字符串做为它们的第一个参数。  

本章节主要介绍 Python 中常用的正则表达式处理函数，如果你对正则表达式不了解，可以查看[正则表达式](/cn/regex)。

### re.match函数

re.match 尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，match()就返回none。

函数语法：
```python
re.match(pattern, string, flags=0)
```

函数参数说明：  
+ pattern : 匹配的正则表达式
+ string : 要匹配的字符串。
+ flags : 可选参数，标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：[正则表达式修饰符](#正则表达式修饰符)

匹配成功re.match方法返回一个匹配的对象，否则返回None。  

我们可以使用group(num) 或 groups() 匹配对象函数来获取匹配表达式。  
+ group(num=0) 匹配的整个表达式的字符串，group() 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。
+ groups() 返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。

以下是实例：  

```python
import re

print(re.match("www", "www.baidu.com").span())  # 在起始位置匹配
print(re.match("com", "www.baidu.com"))  # 不在起始位置匹配

line = "Cats are smarter than dogs"
# .* 表示任意匹配除换行符（\n、\r）之外的任何单个或多个字符
# (.*?) 表示"非贪婪"模式，只保存第一个匹配到的子串
matchObj = re.match(r"(.*) are (.*?) .*", line, re.M | re.I)

if matchObj:
    print("matchObj.group() : ", matchObj.group())
    print("matchObj.group(1) : ", matchObj.group(1))
    print("matchObj.group(2) : ", matchObj.group(2))
    print("matchObj.groups() : ", matchObj.groups())
else:
    print("No match!!")
```

以上代码的运行结果为：  
> (0, 3)  
> None  
> matchObj.group() :  Cats are smarter than dogs  
> matchObj.group(1) :  Cats  
> matchObj.group(2) :  smarter  
> matchObj.groups() :  ('Cats', 'smarter')


### re.search函数

re.search扫描整个字符串并返回第一个成功的匹配。

函数语法：

```python 
re.search(pattern, string, flags=0)
```

函数参数说明：  
+ pattern : 匹配的正则表达式
+ string : 要匹配的字符串
+ flags : 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：[正则表达式修饰符](#正则表达式修饰符)

匹配成功re.search方法返回一个匹配的对象，否则返回None。   
我们可以使用group(num) 或 groups() 匹配对象函数来获取匹配表达式。

<!-- TODO: 正则表达式补全 -->

**********************************

## Python操作MySQL

MySQL是最流行的关系型数据库管理系统。
Python连接mysql数据库的方法有`mysql-connector`和`PyMySQL`两种，接下来我们来介绍这两个模块。

```base
python -m pip install mysql-connector
```

```base
python -m pip install PyMySQL
```

使用以下代码测试mysql-connector/pymysql是否安装成功：  

```python
import mysql.connector
```

```python
import pymysql
```

执行以上代码，如果没有产生错误，表明安装成功。

两个模块的方法基本一致.

### 创建数据库连接

可以使用以下代码来连接数据库：  

```python
import mysql.connector

db = mysql.connector.connect(
    host = "localhost",   # 数据库主机地址
    user = "yourusername",    # 数据库用户名
    passwd = "yourpassword"    #  数据库密码 
)

print(db)
```

如果出现以下错误：  
```
mysql.connector.errors.NotSupportedError: Authentication plugin 'caching_sha2_password' is not supported
```

是因为你的 MySQL 是 8.0 以上版本，密码插件验证方式发生了变化，早期版本为 mysql_native_password，8.0 版本为 caching_sha2_password，所以需要做些改变：

```python
db = mysql.connector.connect(
    host = "localhost",   # 数据库主机地址
    user = "yourusername",    # 数据库用户名
    passwd = "yourpassword",    #  数据库密码 
    database = "yourdatabase",   # 选择数据库
    auth_plugin="mysql_native_password"     # 选择密码插件验证方式为mysql_native_password
)
```

或者修改mysql的my.ini配置：

```python
[mysqld]
default_authentication_plugin=mysql_native_password
```

### 数据库操作

在连接好数据库后，我们使用cursor.execute(sql)来执行数据库操作,并用迭代器打印结果：  

```python
# 假设以连接好数据库db = mysql.connector.connect()

cursor= db.cursor()

cursor.execute("use mydb")

cursor.execute("show tables")

for x in cursor:
    print(x)
```

执行的sql语句参见[mysql](/cn/mysql)

<!-- TODO: mysql博客 -->

当使用sql语句导致数据表内容有更新时，必须使用db.commit()提交

> cursor.rowcount为更改的行数

cursor.execute()只会执行一次数据操作，如果要执行批量插入修改等操作，需要使用executemany(sql,args_tuple_list)方法。该方法的第二参数是一个元组列表,包含要操作的数据。如：  

```python
sql = "insert into testtable (name,value) values (%s,%s)"
val = [
    ('name1','1'),
    ('name2','2'),
    ('name3','3'),
    ('name4','4')
]

cursor.executemany(sql,val)

db.commit()

print(mycursor.rowcount, "记录插入成功。")
```

> mycursor.lastrowid表示最新数据记录的ID

如果使用查询，可以使用fetchall()获取所有记录，或者fetchone/fetchmany等选择性获取。

fetchall返回的是一个列表，记录存储为元组。

#### 使用预处理格式（占位符格式）

可以查看一下execute()方法的定义：

```python
class MySQLCursor(CursorBase):
    '''
        省略很多方法和变量
    '''
 
    def execute(self, operation, params=None, multi=False):
        """Executes the given operation
 
        Executes the given operation substituting any markers with
        the given parameters.
 
        For example, getting all rows where id is 5:
          cursor.execute("SELECT * FROM t1 WHERE id = %s", (5,))
 
        The multi argument should be set to True when executing multiple
        statements in one operation. If not set and multiple results are
        found, an InterfaceError will be raised.
 
        If warnings where generated, and connection.get_warnings is True, then
        self._warnings will be a list containing these warnings.
 
        Returns an iterator when multi is True, otherwise None.
        """
```

第1个参数是要执行的SQL语句，其中，参数位置先使用占位符来占位.   
第2个参数是一个tuple（元组），元素值就是SQL占位符对应的参数，注意只有一个参数的时候，要写成(xxx,)，后面的逗号不要忘记。  
第3个参数是一个bool值，表示第一个参数是不是多个SQL语句，如果是的话，就传入True，否则传入False。

**注意，在SQL中的占位符，统一写%s, 具体的类型，是在tuple中，传入的参数元素类型决定**

#### 关闭数据库连接

使用db.close()关闭数据库连接

#### 数据库回滚

如果数据库发生错误，建议使用db.rollback()进行回滚

***********************************

## Python多线程

多线程类似于同时执行多个不同程序，多线程运行有如下优点：

+ 使用线程可以把占据长时间的程序中的任务放到后台去处理。
+ 用户界面可以更加吸引人，比如用户点击了一个按钮去触发某些事件的处理，可以弹出一个进度条来显示处理的进度。
+ 程序的运行速度可能加快。
+ 在一些等待的任务实现上如用户输入、文件读写和网络收发数据等，线程就比较有用了。在这种情况下我们可以释放一些珍贵的资源如内存占用等等。

每个独立的线程有一个程序运行的入口、顺序执行序列和程序的出口。但是线程不能够独立执行，必须依存在应用程序中，由应用程序提供多个线程执行控制。  
每个线程都有他自己的一组CPU寄存器，称为线程的上下文，该上下文反映了线程上次运行该线程的CPU寄存器的状态。  
指令指针和堆栈指针寄存器是线程上下文中两个最重要的寄存器，线程总是在进程得到上下文中运行的，这些地址都用于标志拥有线程的进程地址空间中的内存。  

+ 线程可以被抢占（中断）。
+ 在其他线程正在运行时，线程可以暂时搁置（也称为睡眠） -- 这就是线程的退让。

线程可以分为:

+ 内核线程：由操作系统内核创建和撤销。
+ 用户线程：不需要内核支持而在用户程序中实现的线程。

Python3 线程中常用的两个模块为：

+ \_thread
+ threading(推荐使用)

thread 模块已被废弃。用户可以使用 threading 模块代替。所以，在 Python3 中不能再使用"thread" 模块。为了兼容性，Python3 将 thread 重命名为 "\_thread"。

Python3 通过两个标准库 \_thread 和 threading 提供对线程的支持。  
\_thread 提供了低级别的、原始的线程以及一个简单的锁，它相比于 threading 模块的功能还是比较有限的。  
threading 模块除了包含 \_thread 模块中的所有方法外，还提供的其他方法：

+ threading.currentThread(): 返回当前的线程变量。
+ threading.enumerate(): 返回一个包含正在运行的线程的list。正在运行指线程启动后、结束前，不包括启动前和终止后的线程。
+ threading.activeCount(): 返回正在运行的线程数量，与len(threading.enumerate())有相同的结果。

除了使用方法外，线程模块同样提供了Thread类来处理线程，Thread类提供了以下方法:

+ run(): 用以表示线程活动的方法。
+ start():启动线程活动。
+ join([time]): 等待至线程中止。这阻塞调用线程直至线程的join() 方法被调用中止-正常退出或者抛出未处理的异常-或者是可选的超时发生。
+ isAlive(): 返回线程是否活动的。
+ getName(): 返回线程名。
+ setName(): 设置线程名。

### \_thread模块

Python中使用线程有两种方式：函数或者用类来包装线程对象。

函数式：调用 \_thread 模块中的`start_new_thread`()函数来产生新线程。语法如下:   

```python
_thread.start_new_thread ( function, args[, kwargs] )
```

参数说明:

+ function - 线程函数。
+ args - 传递给线程函数的参数,他必须是个tuple类型。
+ kwargs - 可选参数。

以下是一个实例：  

```python
import _thread
import time


# 为线程定义一个函数
def print_time(threadName, delay, loopTime):
    count = 0
    while count < loopTime:
        time.sleep(delay)
        count += 1
        print("%s: %s" % (threadName, time.ctime(time.time())))


# 创建两个线程
try:
    _thread.start_new_thread(print_time, ("Thread-1", 2, 5))
    _thread.start_new_thread(print_time, ("Thread-2", 4, 6))
except:
    print("Error: 无法启动线程")

while 1:
    pass
```

以上代码的输出结果为：  

> Thread-1: Tue Mar 22 16:16:05 2022
> Thread-2: Tue Mar 22 16:16:07 2022
> Thread-1: Tue Mar 22 16:16:07 2022
> Thread-1: Tue Mar 22 16:16:09 2022
> Thread-2: Tue Mar 22 16:16:11 2022
> Thread-1: Tue Mar 22 16:16:11 2022
> Thread-1: Tue Mar 22 16:16:13 2022
> Thread-2: Tue Mar 22 16:16:15 2022
> Thread-2: Tue Mar 22 16:16:19 2022
> Thread-2: Tue Mar 22 16:16:23 2022
> Thread-2: Tue Mar 22 16:16:27 2022

### treading模块

我们可以通过直接从 threading.Thread 继承创建一个新的子类，并实例化后调用 start() 方法启动新线程，即它调用了线程的 run() 方法：

```Python
import threading
import time

exitFlag = 0

class myThread (threading.Thread):
    def __init__(self, threadID, name, delay):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.delay = delay
    def run(self):
        print ("开始线程：" + self.name)
        print_time(self.name, self.delay, 5)
        print ("退出线程：" + self.name)

def print_time(threadName, delay, counter):
    while counter:
        if exitFlag:
            threadName.exit()
        time.sleep(delay)
        print ("%s: %s" % (threadName, time.ctime(time.time())))
        counter -= 1

# 创建新线程
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)

# 开启新线程
thread1.start()
thread2.start()
thread1.join()
thread2.join()
print ("退出主线程")
```

以上代码的运行结果为： 

> 开始线程：Thread-1  
> 开始线程：Thread-2
> Thread-1: Tue Mar 22 16:31:08 2022
> Thread-1: Tue Mar 22 16:31:09 2022
> Thread-2: Tue Mar 22 16:31:09 2022
> Thread-1: Tue Mar 22 16:31:10 2022
> Thread-1: Tue Mar 22 16:31:11 2022
> Thread-2: Tue Mar 22 16:31:11 2022
> Thread-1: Tue Mar 22 16:31:12 2022
> 退出线程：Thread-1
> Thread-2: Tue Mar 22 16:31:13 2022
> Thread-2: Tue Mar 22 16:31:16 2022
> Thread-2: Tue Mar 22 16:31:18 2022
> 退出线程：Thread-2
> 退出主线程

### 线程同步

如果多个线程共同对某个数据修改，则可能出现不可预料的结果，为了保证数据的正确性，需要对多个线程进行同步。  
使用 Thread 对象的 Lock 和 Rlock 可以实现简单的线程同步，这两个对象都有 acquire 方法和 release 方法，对于那些需要每次只允许一个线程操作的数据，可以将其操作放到 acquire 和 release 方法之间。如下：

多线程的优势在于可以同时运行多个任务（至少感觉起来是这样）。但是当线程需要共享数据时，可能存在数据不同步的问题。  
考虑这样一种情况：一个列表里所有元素都是0，线程"set"从后向前把所有元素改成1，而线程"print"负责从前往后读取列表并打印。  
那么，可能线程"set"开始改的时候，线程"print"便来打印列表了，输出就成了一半0一半1，这就是数据的不同步。为了避免这种情况，引入了锁的概念。  
锁有两种状态——锁定和未锁定。每当一个线程比如"set"要访问共享数据时，必须先获得锁定；如果已经有别的线程比如"print"获得锁定了，那么就让线程"set"暂停，也就是同步阻塞；等到线程"print"访问完毕，释放锁以后，再让线程"set"继续。  
经过这样的处理，打印列表时要么全部输出0，要么全部输出1，不会再出现一半0一半1的尴尬场面。

```Python
import threading
import time

class myThread (threading.Thread):
    def __init__(self, threadID, name, delay):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.delay = delay
    def run(self):
        print ("开启线程： " + self.name)
        # 获取锁，用于线程同步
        threadLock.acquire()
        print_time(self.name, self.delay, 3)
        # 释放锁，开启下一个线程
        threadLock.release()

def print_time(threadName, delay, counter):
    while counter:
        time.sleep(delay)
        print ("%s: %s" % (threadName, time.ctime(time.time())))
        counter -= 1

threadLock = threading.Lock()
threads = []

# 创建新线程
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)

# 开启新线程
thread1.start()
thread2.start()

# 添加线程到线程列表
threads.append(thread1)
threads.append(thread2)

# 等待所有线程完成
for t in threads:
    t.join()
print ("退出主线程")
```

### 线程优先级队列

Python 的 Queue 模块中提供了同步的、线程安全的队列类，包括FIFO（先入先出)队列Queue，LIFO（后入先出）队列LifoQueue，和优先级队列 PriorityQueue。  
这些队列都实现了锁原语，能够在多线程中直接使用，可以使用队列来实现线程间的同步。  
Queue 模块中的常用方法:

+ Queue.qsize() 返回队列的大小
+ Queue.empty() 如果队列为空，返回True,反之False
+ Queue.full() 如果队列满了，返回True,反之False
+ Queue.full 与 maxsize 大小对应
+ Queue.get([block[, timeout]])获取队列，timeout等待时间
+ Queue.get_nowait() 相当Queue.get(False)
+ Queue.put(item) 写入队列，timeout等待时间
+ Queue.put_nowait(item) 相当Queue.put(item, False)
+ Queue.task_done() 在完成一项工作之后，Queue.task_done()函数向任务已经完成的队列发送一个信号
+ Queue.join() 实际上意味着等到队列为空，再执行别的操作


```Python

import queue
import threading
import time

exitFlag = 0

class myThread (threading.Thread):
    def __init__(self, threadID, name, q):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.q = q
    def run(self):
        print ("开启线程：" + self.name)
        process_data(self.name, self.q)
        print ("退出线程：" + self.name)

def process_data(threadName, q):
    while not exitFlag:
        queueLock.acquire()
        if not workQueue.empty():
            data = q.get()
            queueLock.release()
            print ("%s processing %s" % (threadName, data))
        else:
            queueLock.release()
        time.sleep(1)

threadList = ["Thread-1", "Thread-2", "Thread-3"]
nameList = ["One", "Two", "Three", "Four", "Five"]
queueLock = threading.Lock()
workQueue = queue.Queue(10)
threads = []
threadID = 1

# 创建新线程
for tName in threadList:
    thread = myThread(threadID, tName, workQueue)
    thread.start()
    threads.append(thread)
    threadID += 1

# 填充队列
queueLock.acquire()
for word in nameList:
    workQueue.put(word)
queueLock.release()

# 等待队列清空
while not workQueue.empty():
    pass

# 通知线程是时候退出
exitFlag = 1

# 等待所有线程完成
for t in threads:
    t.join()
print ("退出主线程")
```

*************************************

## Python MongoDB

MongoDB 是目前最流行的 NoSQL 数据库之一，使用的数据类型 BSON（类似 JSON）。  
关于MongoDB 数据库以查看这篇[MongoDB博客](/cn/mongodb)。

mongoDB下载：<https://www.mongodb.com/try/download/community>

<!-- TODO： mongodb blog -->

*************************************

## Python request



*********************************

## Python网络编程

Python提供了两个级别访问的网络服务：  

+ 低级别的网络服务支持基本的 Socket，它提供了标准的 BSD Sockets API，可以访问底层操作系统Socket接口的全部方法。
+ 高级别的网络服务模块 SocketServer， 它提供了服务器中心类，可以简化网络服务器的开发。

> Socket又称"套接字"，应用程序通常通过"套接字"向网络发出请求或者应答网络请求，使主机间或者一台计算机上的进程间可以通讯。


********************************

## Python Json数据解析

Python3 中可以使用 json 模块来对 JSON 数据进行编解码。

> import json

它包含了两个函数：

+ json.dumps() 对数据进行`编码`。将Python String转换成Json Object。
+ json.loads()  对数据进行`解码`。将Json string解析成Python Object。






********************************

<!-- TODO: argparse -->
<!-- TODO: _变量 -->
<!-- TODO: as关键字 -->
<!-- TODO: dir() 和 help() -->

******************************

## Python内置函数
<!-- TODO  函数汇总--> 
<!-- TODO: int() tuple()等 -->
<!-- TODO: type()  isinstance() -->

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
> 返回对应参数的类型，注意如果是复数返回的是其`模`。

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

### format()

format 基本语法是通过 {} 和 : 来代替以前的 % 。 

语法：  
> 
> ```python
> S.format(*args: object, **kwargs: object) -> str
> ```
> 
> **参数说明：**  
> + S :  需要格式化的字符串
> + *args/**kwargs :  传入的参数值表
> 
> **返回值：**  
> 返回格式化后的字符串

用例：  
```python
# 不设置指定位置，按默认顺序
print("{} {}".format("hello", "world"))    

# 设置指定位置
print("{1} {0} {1}".format("hello", "world"))  

# 直接设置参数
print("网站名：{name}, 地址 {url}".format(name="百度", url="https://www.baidu.com"))   

# 通过字典设置参数
site = {"name": "谷歌", "url": "https://www.google.com"}
print("网站名：{name}, 地址 {url}".format(**site))
 
# 通过列表索引设置参数
my_list = ['哔哩哔哩', 'https://www.bilibili.com']
print("网站名：{0[0]}, 地址 {0[1]}".format(my_list))  # "0" 是必须的

# 还可以传入对象
class TestValue(object):
    def __init__(self, value):
        self.value = value
my_value = TestValue(13)
print('value 为: {0.value}'.format(my_value))  # "0" 是可选的
print('value 为: {.value}'.format(my_value))  # "0" 是可选的，等同上行

# 使用大括号转义大括号
print("{} 元素对应的位置是 {{0}}".format("a"))
```

以上代码运行后的输出结果为：  
> hello  
> world hello world   
> 网站名：百度, 地址 https://www.baidu.com  
> 网站名：谷歌, 地址 https://www.google.com  
> 网站名：哔哩哔哩, 地址 https://www.bilibili.com  
> value 为: 13  
> value 为: 13  
> a 元素对应的位置是 {0}  


<!-- TODO: 待补充说明(Python输入输出\输出格式美化) -->

***还可以使用format函数进行数字格式化***

<table>
<thead>
<tr>
<th style = "text-align : center">
格式
</th>
<th style = "text-align : center">
实例
</th>
<th style = "text-align : center">
输出
</th>
<th style = "text-align : center">
描述
</th>
</tr>
</thead>
<tbody>
<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">
<code>{:[+].[n]f}</code>
</td>
<td>

```python
print("{:.2f}".format(3.1415926))
print("{:.4f}".format(math.e))
print("{:+.2f}".format(3.1415926))
print("{:+.2f}".format(-3.1415926))
```
</td>
<td>

```python
3.14
2.7183
+3.14
-3.14
```
</td>
<td style = "vertical-align : middle; text-align : center">
保留小数点后n位,<br>类似执行 <a href = "#round">round()</a>
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">
<code>{:[c][s][n]d}</code>
</td>
<td>

```python
print("{:0>5d}".format(101))
print("{:s<4d}".format(1))
print("{:>4d}".format(1))
print("{:.^5d}".format(1))
```
</td>
<td>

```python
00101
1sss
   1
..1..
```
</td>
<td style = "vertical-align : middle; text-align : center">
设定数字宽度为n、对齐方式为>(右)<(左)^(中)、填充字符为c(默认为空格)
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">
<code>{:,}</code>
</td>
<td>

```python
print("{:,}".format(13000000))
print("{:,}".format(1000.7651))
```
</td>
<td>

```python
13,000,000
1,000
```
</td>
<td style = "vertical-align : middle; text-align : center">
以逗号分隔的数字格式
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">
<code>{:[+].[n]%}</code>
</td>
<td>

```python
print("{:.2%}".format(1.2))
print("{:.1%}".format(0.25))
print("{:+.2%}".format(-0.25))
print("{:+.2%}".format(0.25))
```
</td>
<td>

```python
120.00%
25.0%
-25.00%
+25.00%
```
</td>
<td style = "vertical-align : middle; text-align : center">
保留n位小数的百分比格式
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">
<code>{:[+].[n]e}</code>
</td>
<td>

```python
print("{:.2e}".format(1.2))
print("{:.1e}".format(0.25))
print("{:+.2e}".format(-0.25))
print("{:+.2e}".format(0.25))
```
</td>
<td>

```python
1.20e+00
2.5e-01
-2.50e-01
+2.50e-01
```
</td>
<td style = "vertical-align : middle; text-align : center">
保留n位小数的指数格式
</td>
</tr>

<tr>
<td style = "vertical-align : middle;
            text-align :center;
            white-space: nowrap;">
<code>{:[]}</code>
</td>
<td>

```python
print("{:b}".format(11))
print("{:d}".format(11))
print("{:o}".format(11))
print("{:x}".format(11))
print("{:#x}".format(11))
print("{:#X}".format(11))
```
</td>
<td>

```python
1011
11
13
b
0xb
0XB
```
</td>
<td style = "vertical-align : middle; text-align : center">
b:二进制<br>
d:十进制<br>
o:八进制<br>
x:十六进制
</td>
</tr>
</tbody>
</table>

*************************************************


### len()

Python len() 方法返回对象（字符、列表、元组等）长度或项目个数。

语法：  
> 
> ```python
> len( s )
> ```
> 
> **参数说明：**  
> + s :  对象，可以是序列（如 string、bytes、tuple、list 或 range 等）或集合（如 dictionary、set 或 frozen set 等）
> 
> **返回值：**  
> 返回对象长度。

用例：  
```python
len((1,2,6,8,7))
len([])
len("abfasdfja")
```

以上代码运行后的输出结果为：  
> 5  
> 0  
> 9

*************************************************


### max()

max() 方法返回给定参数的最大值，参数可以为序列。

语法：  
> 
> ```python
> max( x, y, z, .... )
> ```
> 
> **参数说明：**  
> + x,y,z: 数值表达式，可以为序列  
> 
> **返回值：**  
> 返回给定参数的最大值。

用例：  
```python
print(max(1, 5, 3))
print(max([-1, 6, 2]))
print(max("asdfghj"))
print(max((1, 2, 6)))
print(max([1, 2, 6], [1, 3, 4]))
print(max([1, 2, 6, 5, 3], [2, 1, 9, 4]))
print(max("abcdefg","abcd","babc"))

print(max(True, 1))
print(max(1, True))
print(max(False,0))
print(max(0, False))
```

以上代码运行后的输出结果为：  
> 5
> 6
> s
> 6
> [1, 3, 4]
> [2, 1, 9, 4]
> babc
> 
> True
> 1
> False
> 0

`max(x, y[, z...]):Number|Sequence` 不能混合入参（要么全Number(int|float|complex|bool），要么全序列）。  

求最大值时，若最大值为`True和1`或者`False和0`，将取决于`参数顺序`，更先的成为返回值。  
  
> 关于大小的比较，请查看[数值比较](#数值比较)

*************************************************

### min()

min() 方法返回给定参数的最小值，参数可以为序列。

语法：  
> 
> ```python
> min( x, y, z, .... )
> ```
> 
> **参数说明：**  
> + x,y,z: 数值表达式，可以为序列  
> 
> **返回值：**  
> 返回给定参数的最小值。

用例：  
```python
print(min(1, 5, 3))
print(min([-1, 6, 2]))
print(min("asdfghj"))
print(min((1, 2, 6)))
print(min([1, 2, 6], [1, 3, 4]))
print(min([1, 2, 6, 5, 3], [2, 1, 9, 4]))
print(min("abcdefg","abcd","babc"))

print(min(True, 1))
print(min(1, True))
print(min(False,0))
print(min(0, False))
```

以上代码运行后的输出结果为：  
> 1
> -1
> a
> 1
> [1, 2, 6]
> [1, 2, 6, 5, 3]
> abcd
> True
> 1
> False
> 0

`min(x, y[, z...]):Number|Sequence` 不能混合入参（要么全Number(int|float|complex|bool），要么全序列）。  

求最小值时，若最小值为`True和1`或者`False和0`，将取决于`参数顺序`，更先的成为返回值。  
  
> 关于大小的比较，请查看[数值比较](#数值比较)

*************************************************


### pow()

pow() 方法返回 x^y（x的y次方） 的值。

语法：  
> 
> ```python
> pow(x,y[,z])
> ```
> 
> **参数说明：**  
> + x :  数值表达式
> + y :  数值表达式
> + z :  数值表达式(**可选参数，默认值为 `1`**）
> 
> **返回值：**  
> 函数是计算x的y次方，如果z在存在，则再对结果进行取模，其结果等效于pow(x,y) %z

用例：  
```python
print(pow(2, 3))
print(pow(2.5, 3))
print(pow(2, 3, 2))
```

以上代码运行后的输出结果为：  
> 8
> 15.625
> 0


> 还有一个math模块的pow函数:[pow()](#pow-2)   
> pow() 通过内置的方法直接调用，内置方法会把参数作为整型，而 math 模块则会把参数转换为 float。

*************************************************

### round()

round()返回浮点数 x 的四舍五入值，准确的说保留值将保留到离上一位更近的一端（四舍六入）。  
精度要求高的，不建议使用该函数。    

语法：  
> 
> ```python
> round(x[,n])
> ```
> 
> **参数说明：**  
> + x : 数字表达式。
> + n : 表示保留的小数点位数，(**可选参数，默认值为 `0`**）。
> 
> **返回值：**  
> 返回浮点数x保留位数后的最近端点数

用例：  
```python
print(round(10.23))
print(round(10.53))
print(round(1.531,2))
print(round(1.564,1))
print(round(1.325,2))     # 由于精度问题，实际值不足1.325，所以round(x,2)==1.32
print(round(-0.5))         # 由于精度问题更偏向0，所以round(-0.5)==0
print(round(-1.236,2))
print(round(-2.165,2))
```

以上代码运行后的输出结果为：  
> 10
> 11
> 1.53
> 1.6
> 1.32
> 0
> -1.24
> -2.17

注意： 关于round()其实并不是常规的四舍五入，例如在上面第五、六个用例中，1.325进到1.32时，因为精度问题无法进位，详情请参见[round()关于四舍五入不成功的问题](#round-关于四舍五入不成功的问题)

*************************************************

### tuple()

tuple 函数将可迭代系列（如列表）转换为元组。

语法：  
> 
> ```python
> tuple(iterable)
> ```
> 
> **参数说明：**  
> + iterable :  要转换为元组的可迭代序列。
> 
> **返回值：**  
> 返回元组。

用例：  
```python
tup = tuple([1,2,6])
print(tup)
```

以上代码运行后的输出结果为：  
> (1,2,6)

*************************************************

## Python os模块方法

********************************

## Python math模块方法
<!-- TODO:三角函数 -->

> 导入模块
> ```python
> import math
> ```

### acos()

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
> 

*************************************************

### asin()

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
> 

*************************************************

### atan()

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
> 

*************************************************


### ceil()

ceil()函数返回`上入整数`，即大于或等于 x 的的最小整数。

语法：  
> 
> ```python
> math.ceil(x)
> ```
> 
> **参数说明：**  
> + x :  数值表达式
> 
> **返回值：**  
> 返回上入整数  

用例：  
```python
print(math.ceil(4.5))
print(math.ceil(-4.5))
```

以上代码运行后的输出结果为：  
> 5
> -4

*************************************************

### cos()

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
> 

*************************************************

### degress()

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
> 

*************************************************

### exp()

exp()方法返回x的指数,e^x。

语法：  
> 
> ```python
> math.exp(x)   ->  float
> ```
> 
> **参数说明：**  
> + x :  数值表达式
> 
> **返回值：**  
> 返回x的指数

用例：  
```python
print(math.exp(1))
print(math.exp(math.pi))
```

以上代码运行后的输出结果为：  
> 2.718281828459045
> 23.140692632779267

*************************************************

### fabs()

返回数字的绝对值，相较abs()更具局限性，fabs()只作用于浮点型和整型，而abs()还可以运用于复数中

语法：  
> 
> ```python 
> math.fabs(x) -> float
> ```
> 
> **参数说明：**  
> + x :  数学表达式
> 
> **返回值：**  
> 返回数字的绝对值，浮点数

用例：  
```python
print(math.fabs(-1.2))
print(math.fabs(-1))
```

以上代码运行后的输出结果为：  
> 1.2
> 1.0

*************************************************

### floor()

floor()函数返回`下舍整数`，即小于或等于 x 的的最大整数。

语法：  
> 
> ```python
> math.floor(x)
> ```
> 
> **参数说明：**  
> + x :  数值表达式
> 
> **返回值：**  
> 返回下舍整数  

用例：  
```python
print(math.floor(4.5))
print(math.floor(-4.5))
```

以上代码运行后的输出结果为：  
> 4
> -5

*************************************************



### log()

log() 方法返回x的对数，默认为自然对数，即以e为底，x > 0。

语法：  
> 
> ```python
> math.log(x[,y=math.e]) -> float
> ```
> 
> **参数说明：**  
> + x :  数值表达式，`x > 0`
> + y :  底数(**可选参数，默认值为`e`**)
> 
> **返回值：**  
> 返回x的对数，浮点数

用例：  
```python
print(math.log(1))
print(math.log(math.e))
print(math.log(100, 10))
print(math.log(8, 3))
```

以上代码运行后的输出结果为：  
> 0.0
> 1.0
> 2.0
> 1.892789260714372
  

> 如果参数为负数，会返回`ValueError`: math domain error

*************************************************

### log10()

log10() 方法返回以10为基数的x对数，x > 0。

语法：  
> 
> ```python
> math.log10(x) -> float
> ```
> 
> **参数说明：**  
> + x :  数值表达式，`x > 0`
> 
> **返回值：**  
> 返回以10为基数的x对数

用例：  
```python
print(math.log10(1000))
```

以上代码运行后的输出结果为：  
> 3.0

> 如果参数为负数，会返回`ValueError`: math domain error

*************************************************

### modf()

modf() 方法返回 x 的整数部分与小数部分，两部分的数值符号与 x 相同，整数部分以浮点型表示。

语法：  
> 
> ```python
> math.modf(x) -> tuple
> ```
> 
> **参数说明：**  
> + x :  数值表达式
> 
> **返回值：**  
> 返回元组包含x的整数部分和小数部分

用例：  
```python
print(math.modf(100.1))
print(math.modf(-1.52))
print(math.modf(1))
```

以上代码运行后的输出结果为：  
> (0.09999999999999432, 100.0)
> (-0.52, -1.0)
> (0.0, 1.0)

*************************************************

### pow()

pow() 方法返回 x^y（x的y次方） 的值。

语法：  
> 
> ```python
> math.pow(x,y)  ->  float
> ```
> 
> **参数说明：**  
> + x :  数值表达式
> + y :  数值表达式
> 
> **返回值：**  
> 返回x的y次方值

用例：  
```python
print(math.pow(2, 3))
print(math.pow(2.5, 3))
```

以上代码运行后的输出结果为：  
> 8.0
> 15.625


> 还有一个内置的pow函数:[pow()](#pow)   
> pow() 通过内置的方法直接调用，内置方法会把参数作为整型，而 math 模块则会把参数转换为 float。

*************************************************

### radians()

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
> 

*************************************************

### sin()

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
> 

*************************************************

### sqrt()

sqrt() 方法返回数字x的平方根。

语法：  
> 
> ```python
> math.sqrt(x)    ->  float
> ```
> 
> **参数说明：**  
> + x :  数值表达式
> 
> **返回值：**  
> 返回数字x的平方根。

用例：  
```python
print(math.sqrt(9))
```

以上代码运行后的输出结果为：  
> 3.0

*************************************************

### tan()

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
> 

*************************************************



## Python random模块方法
> 导入模块
> ```python
> import random
> ```

### choice()

choice() 方法从序列的元素中随机挑选一个元素返回。

语法：  
> 
> ```python
> random.choice(seq)
> ```
> 
> **参数说明：**  
> + seq :  可序列对象，可以是一个列表、元组、字符串
> 
> **返回值：**  
> 返回一个随机项

用例：  
```python
print(random.choice("asdfghjk"))
print(random.choice((1,3,5,9,3)))
print(random.choice([1,36,5,4,6,9]))
print(random.choice(range(10)))  # 返回从0到9中随机挑选的一个整数。
```

*****************************************

### random()

random() 方法返回随机生成的一个实数，它在`[0,1)`范围内。

语法：  
> 
> ```python
> random.random()
> ```
> 
> **参数说明：**  
> 无  
> 
> **返回值：**  
> 返回随机生成的一个实数，它在[0,1)范围内。

用例：  
```python
random.random()
```

*****************************************

### randrange()

randrange() 方法返回指定递增基数集合中的一个随机数，基数默认值为1。  

语法：  
> 
> ```python
> random.randrange ([start,] stop [,step])
> ```
> 
> **参数说明：**  
> + start :  指定范围内的开始值，`包含`在范围内。(**可选参数，默认值为`0`**)
> + stop :  指定范围内的结束值，`不包含`在范围内。
> + step :  指定递增基数。 (**可选参数，默认值为`1`**)
> 
> **返回值：**  
> 从给定的范围返回随机项。

用例：  
```python
random.randrange(100)   # 从0-100中随机选取一个数
random.randrange(0,100, 2)   # 从0-100中随机选取一个偶数
random.randrange(0,100, 4)  # 从0-100中随机选取一个能被4整除的整数
random.randrange(1,100, 3)  # 从0-100中随机选取一个能被3整除后余1的数
```


*****************************************

### seed()

改变随机数生成器的种子seed。**可以在调用其他随机模块函数之前调用此函数**。  

语法：  
> 
> ```python
> random.seed([x])
> ```
> 
> **参数说明：**  
> + x :  (**可选参数**)改变随机数生成器的种子seed。如果你不了解其原理，你不必特别去设定seed，Python会帮你选择seed。
> 
> **返回值：**  
> 无

用例：  
```python
random.seed()
print ("使用默认种子生成随机数：", random.random())
print ("使用默认种子生成随机数：", random.random())

random.seed(10)
print ("使用整数 10 种子生成随机数：", random.random())
random.seed(10)
print ("使用整数 10 种子生成随机数：", random.random())

random.seed("hello",2)
print ("使用字符串种子生成随机数：", random.random())
```

以上代码运行后的输出结果为：  
> 使用默认种子生成随机数： 0.9506421767605476
> 使用默认种子生成随机数： 0.20706442655860602
> 使用整数 10 种子生成随机数： 0.5714025946899135
> 使用整数 10 种子生成随机数： 0.5714025946899135
> 使用字符串种子生成随机数： 0.3537754404730722

*****************************************

### shuffle()

将序列的所有元素随机排序

语法：  
> 
> ```python
> random.shuffle(lst)
> ```
> 
> **参数说明：**  
> + lst :  列表 
> 
> **返回值：**  
> 返回None

用例：  
```python
list1 = [1,2,3,4,6]
random.shuffle(list1)
print(list1)
```

以上代码运行后的输出结果为：  
> [3, 2, 4, 1, 6]

*****************************************


### uniform()

uniform() 方法将随机生成下一个实数，它在 `[x,y]` 范围内。

语法：  
> 
> ```python
> random.uniform(x,y)
> ```
> 
> **参数说明：**  
> + x :  随机数的最小值，`包含`该值。
> + y :  随机数的最大值，`包含`该值。
> 
> **返回值：**  
> 返回一个浮点数 N，取值范围为如果 <kbd>x<y</kbd> 则`x <= N <= y`，如果 <kbd>y<x</kbd> 则`y <= N <= x`。

用例：  
```python
random.uniform(1,2)
```


*****************************************

## Python shutil模块方法

**************************************

## Python re模块方法

**************************************

<!-- TODO：新建文章记录错误 -->

## Python常见问题
### float精度问题
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

*****************************************

### round()关于四舍五入不成功的问题

本质还是和浮点数的精度有关。在机器中浮点数不一定能精确表达，因为换算成一串 1 和 0 后可能是无限位数的，机器已经做出了截断处理。那么在机器中保存的2.675这个数字就比实际数字要小那么一点点。这一点点就导致了它离 2.67 要更近一点点，所以保留两位小数时就近似到了 2.67。 
 <!-- TODO:round精度问题补全  -->
更多请见：<https://www.runoob.com/w3cnote/python-round-func-note.html>

*************************************

### str()和repr()的区别