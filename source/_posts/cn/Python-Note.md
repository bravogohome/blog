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
> \<class '\_\_main__.A'>  
> \<class '\_\_main__.B'>  
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

##### [Python的math模块](#Python-math模块)  
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


##### [Python的random模块](#Python-random模块)
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
> \<class 'str'>


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
| <sp> | 	在正数前面显示空格 |
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
> [1, '7', 2.589, (1, '2')] \<class 'list'>
> [] \<class 'list'>
> [1, 5, 9, '7'] \<class 'list'>
> [16, 25, 81, 64]

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
```python
lst = [1,4]
del lst[0]
print(lst)
```
以上代码的输出结果为：  
> [4]

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
> g:\Codes\Python\algorithm\test.py in <module>
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
> test.py in \<module>
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
> test.py in \<module>
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

************************************

### 数值比较
<!-- TODO: 数值比较 -->

<!-- TODO: _变量 -->
<!-- TODO: del删除对象 引用 -->

****************************************************

## Python序列sequence

### 序列运算
<!-- TODO: 序列运算符 https://blog.csdn.net/bcj296050240/article/details/46313709-->
#### +运算/拼接
#### *运算/复制
#### in运算
#### 切片运算符


*****************************************************


## Python内置函数
<!-- TODO  函数汇总--> 
<!-- TODO: int() tuple()等 -->
<!-- TODO: type()  instance() -->

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



## Python math模块
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



## Python random模块
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