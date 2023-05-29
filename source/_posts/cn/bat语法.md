---
title: bat语法
catalog: true
lang: cn
date: 2023-05-29 21:45:15
subtitle:
header-img: /img/header_img/nier.png
tags:
- bat
categories:
- Note
sticky: 996
---

## 【 echo 命令 】
打开回显或关闭请求回显功能，或显示消息。如果没有任何参数，echo 命令将显示当前回显设置。

`语法`
```bat
echo [{on|off}] [message]

Sample：@echo off / echo hello world
```
在实际应用中我们会把这条命令和重定向符号（也称为管道符号，一般用>>>^）结合来实现输入一些命令到特定的文件中。

## 【 rem 命令 】

注释命令，类似于在C语言中/\*\*/，它并不会被执行，只是起一个注释的作用，便于别人阅读和你自己日后修改。

`::` 也具有rem的功能

但::和rem还是有区别的，当关闭回显时，rem和::后的内容都不会显示。但是当打开回显时，rem和rem后的内容会显示出来，然而::后的内容仍然不会显示。

```bat
Rem Message

Sample：@Rem Here is the description.
        ::Here is the description.
```

## 【 pause 命令 】

  暂停命令。运行 Pause 命令时，将显示下面的消息：

  Press any key to continue. . .(或：请按任意键继续. . .)

  Sample：

  @echo off

  :begin

  copy G:*.* d：\back

  echo 请插入另一张光盘...

  pause

  goto begin

  在这个例子中，驱动器 G 中磁盘上的所有文件均复制到d:\back中。显示的注释提示您将另一张光盘

  盘放入驱动器 G 时，pause 命令会使程序挂起，以便您更换光盘，然后按任意键继续处理。

## 【 call 命令 】

  从一个批处理程序调用另一个批处理程序，并且不终止父批处理程序。call 命令接受用作调用目标的

  标签。如果在脚本或批处理文件外使用 Call，它将不会在命令行起作用。

  语法

  call [[Drive:][Path] FileName ] [:label [arguments]]

  参数

  [Drive:}[Path] FileName

  指定要调用的批处理程序的位置和名称。

## 【 start 命令 】

  调用外部程序，所有的DOS命令和命令行程序都可以由start命令来调用。

  如：start calc.exe 即可打开Windows的计算器。

  常用参数：

  MIN 开始时窗口最小化

  SEPARATE 在分开的空间内开始 16 位 Windows 程序

  HIGH 在 HIGH 优先级类别开始应用程序

  REALTIME 在 REALTIME 优先级类别开始应用程序

  WAIT 启动应用程序并等候它结束

  parameters 这些为传送到命令/程序的参数

  执行的应用程序是 32-位 GUI 应用程序时，CMD.EXE 不等应用程序终止就返回命令提示。如果在命令

  脚本内执行，该新行为则不会发生。

## 【 goto 命令 】

  跳转命令。程序指针跳转到指定的标签，从标签后的第一条命令开始继续执行批处理程序。

  语法：goto label （label是参数，指定所要转向的批处理程序中的行。）
```
  Sample：

  if {%1}=={} goto noparms

  if {%2}=={} goto noparms（如果这里的if、%1、%2你不明白的话，先跳过去，后面会有详细的解释

  。）

  @Rem check parameters if null show usage

  :noparms

  echo Usage: monitor.bat ServerIP PortNumber

  goto end
```
  标签的名字可以随便起，但是最好是有意义的字母啦，字母前加个：用来表示这个字母是标签，goto

  命令就是根据这个：来寻找下一步跳到到那里。最好有一些说明这样你别人看起来才会理解你的意图啊。

## 【 set 命令 】

  显示、设置或删除变量。

  显示变量：set 或 set s 前者显示批处理当前已定义的所有变量及其值，后者显示所有以s开头的变量及值。

  设置变量：set aa=abcd 此句命令便可向变量aa赋值abcd。如果变量aa已被定义，则aa的值被修改为abcd；若aa尚未定义，则此句命令即可定义新的变量aa，同时为变量aa赋予初始值abcd。

  删除变量：set aa= 此句命令即可删除变量aa。若变量aa已被定义，则删除变量aa；若aa尚未定义，则此句命令为实质意义。

  需要说明的是，批处理中的变量是不区分类型的，不需要像C语言中的变量那样还要区分int、float、char等。比如执行set aa=345后，变量aa的值既可以被视为数字345，也可以被视为字符串345。

  set命令具有扩展功能，如用作交互输入、字符串处理、数值计算等，属于高级命令范畴。

[编辑本段]批处理符号简介

## 【 回显屏蔽 @ 】

  表示不显示@后面的命令，在入侵过程中（例如使用批处理来格式化敌人的硬盘）自然不能让对方看到你使用的命令啦。

  @用法举例：通过运行批处理文件对比pause和@pause命令即可明了@的效果。

## 【 重定向1 >与>>】

  将输出信息重定向到指定的设备或文件。系统默认输出到显示器。

  如：echo aaaaa>a.txt 即可将本在显示器上显示的信息aaaaa输出到文件a.txt中，屏幕上没有任何显示。如果文件a.txt本来已经存在，该命令将首先擦除a.txt中的所有信息，然后写入信息aaaaa；若a.txt本来就不存在，该命令即可新建一个a.txt文件，并写入信息aaaaa。

  echo aaaaa>>a.txt 类似于echo aaaaa>a.txt。区别在于：如果a.txt本已存在，>a.txt会擦除a.txt中的原有内容，而>>a.txt并不擦除原有内容，仅在a.txt文件的末尾添加信息aaaaa。a.txt不存在时，二者没有差别。

## 【 重定向2 <】

  将输入信息来源重定向为指定的设备或文件。系统默认从显示器读取输入信息。

  重定向使用举例：

  =========================================

  @echo off

  echo abcdefg——这是文件a.txt中的信息>a.txt

  echo 请任意输入字符，以回车结束：

  set /p ifo=

  cls

  echo ## 【 从屏幕获得的输入信息 】

  echo %ifo%

  set /p ifo=<a.txt

  echo ## 【 从文件a.txt获得的输入信息 】

  echo %ifo%

  pause>nul

  =========================================

  读者观察命令与输出即可体会到重定向的功能和效果。

## 【 管道符号 | 】

  将管道符号前面命令的输出结果重定向输出到管道符号后面的命令中去，作为后面命令的输入。使用格式为：command_1|command_2

  管道符号使用举例：

  =========================================

  @echo off

  echo aaaa>a.txt

  del /p a.txt

  pause

  =========================================

  @echo off

  echo aaaa>a.txt

  echo y|del /p a.txt

  pause

  =========================================

  对比以上两个批处理执行结果，读者即可明白管道符的用法和效果。

  需要说明的是，上面del命令添加开关/p只是为了让读者明白管道符号的使用方法，实际删除文件时不加/p开关即可实现无提示直接删除。

## 【 转义符 ^ 】

  将特殊符号转化为一般符号，即剥离特殊符号的特殊地位。特殊符号指：| &><

  比如，如果我们想输出符号“>”，直接用命令 echo >是不行的，必须修改为 echo ^>。其余几个特殊符号类似需要有同样的处理。

  转义字符使用举例：

  =========================================

  @echo off

  echo aaaa>a.txt

  echo 第一句echo执行完毕

  echo aaaa^>a.txt

  echo 第二句echo执行完毕

  pause

  =========================================

  比较上面的两句echo，第一句echo将信息aaaa输出到了文件a.txt，而第二句echo则在直接屏幕上显示出aaaa>a.txt

## 【 逻辑命令符 】

  逻辑命令符包括：&、&&、||

  &-它的作用是用来连接n个DOS命令，并把这些命令按顺序执行，而不管是否有命令执行失败；

  &&-当&&前面的命令成功执行时，执行&&后面的命令，否则不执行；

  ||-当||前面的命令失败时，执行||后面的命令，否则不执行。

  =========================================

  @echo off

  echo ^|^|

  reg add HKCU /v try /f||echo **成功**

  reg add HKCU1 /v try /f||echo **失败**

  echo ^&^&

  reg delete HKCU /v try /f&&echo **成功**

  reg delete HKCU /v try /f&&echo **失败**

  echo ^&

  reg delete HKCU /v try /f&echo **成功**

  reg delete HKCU /v try /f&echo **失败**

  pause

  =========================================

  执行reg add或reg delete后，系统会给出执行结果；我们通过echo命令也给出了“执行结果”。对比系统和我们自己给出的结果，既可以验证逻辑命令的判断机理。

[编辑本段]常用DOS命令释义

## 【 文件夹管理 】

  cd 显示当前目录名或改变当前目录。

  md 创建目录。

  rd 删除一个目录。

  dir 显示目录中的文件和子目录列表。

  tree 以图形显示驱动器或路径的文件夹结构。

  path 为可执行文件显示或设置一个搜索路径。

  xcopy 复制文件和目录树。

## 【 文件管理 】

  type 显示文本文件的内容。

  copy 将一份或多份文件复制到另一个位置。

  del 删除一个或数个文件。

  move 移动文件并重命名文件和目录。(Windows XP Home Edition中没有)

  ren 重命名文件。

  replace 替换文件。

  attrib 显示或更改文件属性。

  find 搜索字符串。

  fc 比较两个文件或两个文件集并显示它们之间的不同

## 【 网络命令 】

  ping 进行网络连接测试、名称解析

  ftp 文件传输

  net 网络命令集及用户管理

  telnet 远程登陆

  ipconfig显示、修改TCP/IP设置

  msg 给用户发送消息

  arp 显示、修改局域网的IP地址-物理地址映射列表

## 【 系统管理 】

  at 安排在特定日期和时间运行命令和程序

  shutdown立即或定时关机或重启

  tskill 结束进程

  taskkill结束进程(比tskill高级，但WinXPHome版中无该命令)

  tasklist显示进程列表(Windows XP Home Edition中没有)

  sc 系统服务设置与控制

  reg 注册表控制台工具

  powercfg控制系统上的电源设置

  对于以上列出的所有命令，在cmd中输入命令+/?即可查看该命令的帮助信息。如find /?

[编辑本段]语句结构释义

  类似于C语言，批处理也有它的语句结构。批处理的语句结构主要有选择结构(if语句)、循环结构(for语句)等。

## 【 if语句(选择结构) 】

  if语句实现条件判断，包括字符串比较、存在判断、定义判断等。通过条件判断，if语句即可以实现选择功能。

  1、字符串比较

  if语句仅能够对两个字符(串)是否相同、先后顺序进行判断等。其命令格式为：

  IF [not] string1 compare-op string2 command1 [else command2]

  其中，比较 *** 作符compare-op有以下几类：

  == - 等于

  EQU - 等于

  NEQ - 不等于

  LSS - 小于

  LEQ - 小于或等于

  GTR - 大于

  GEQ - 大于或等于

  选择开关/i则不区分字符串大小写；选择not项，则对判断结果进行逻辑非。

  字符串比较示例：

  ===============================================

  @echo off

  set str1=abcd1233

  set str2=ABCD1234

  if %str1%==%str2% (echo 字符串相同！) else (echo 字符串不相同！)

  if /i %str1% LSS %str2% (echo str1^<str2) else (echo str1^>=str2)

  echo.

  set /p choice=是否显示当前时间？(y/n)

  if /i not %choice% EQU n echo 当前时间是：%date% %time%

  pause>nul

  ===============================================

  对于最后一个if判断，当我们输入n或N时的效果是一样的，都不会显示时间。如果我们取消开关/i，则输入N时，依旧会显示时间。

  另外请注意一下几个细节：1-echo str1^<str2和echo str1^>=str2；2-echo.。

  2、存在判断

  存在判断的功能是判断文件或文件夹是否存在。其命令格式为：

  IF [NOT] EXIST filename command1 [else command2]

  ===============================================

  @echo off

  if exist %0 echo 文件%0是存在的！

  if not exist %~df0 (

  echo 文件夹%~df0不存在！

  ) else echo 文件夹%~df0存在！

  pause>nul

  ===============================================

  这里注意几个地方：

  1-存在判断既可以判断文件也可以判断文件夹；

  2-%0即代表该批处理的全称(包括驱动器盘符、路径、文件名和扩展类型)；

  3-%~df0是对%0的修正，只保留了其驱动器盘符和路径，详情请参考for /?，属高级批处理范畴；

  4-注意if语句的多行书写，多行书写要求command1的左括号必须和if在同一行、else必须和command1的右括号同行、command2的左括号必须与else同行、command1和command2都可以有任意多行，即command可以是命令集。

  3、定义判断

  定义判断的功能是判断变量是否存在，即是否已被定义。其命令格式为：

  IF [not] DEFINED variable command1 [else command2]

  存在判断举例：

  ===============================================

  @echo off

  set var=111

  if defined var (echo var=%var%) else echo var尚未定义！

  set var=

  if defined var (echo var=%var%) else echo var尚未定义！

  pause>nul

  ===============================================

  对比可知，"set var="可以取消变量，收回变量所占据的内存空间。

  4、结果判断

  masm %1.asm

  if errorlevel 1 pause &edit %1.asm

  link %1.obj

  先对源代码进行汇编，如果失败则暂停显示错误信息，并在按任意键后自动进入编辑界面；否则用link程序连接生成的obj文件，这种用法是先判断前一个命令执行后的返回码（也叫错误码，DOS程序在运行完后都有返回码），如果和定义的错误码符合（这里定义的错误码为1），则执行相应的 *** 作（这里相应的 *** 作为pause &edit %1.asm部分）。

  另外，和其他两种用法一样，这种用法也可以表示否定。用否定的形式仍表达上面三句的意思，代码变为：

  masm %1.asm

  if not errorlevel 1 link %1.obj

  pause &edit %1.asm

## 【 for语句(循环结构) 】

  for语句可以实现类似于C语言里面的循环结构，当然for语句的功能要更强大一点，通过不同的开关可以实现更多的功能。for语句有多个开关，不同开关将会实现不同的功能。

  1、无开关

  无开关的for语句能够对设定的范围内进行循环，是最基本的for循环语句。其命令格式为：

  FOR %%variable IN (set) DO command

  其中，%%variable是批处理程序里面的书写格式，在DOS中书写为%variable，即只有一个百分号(%)；set就是需要我们设定的循环范围，类似于C语言里面的循环变量；do后面的command就是循环所执行的命令，即循环体。

  无开关for语句举例：

  ===============================================

  @echo off

  for %%i in (a,"b c",d) do echo %%i

  pause>nul

  ===============================================

  2、开关/L

  含开关/L的for语句，可以根据set里面的设置进行循环，从而实现对循环次数的直接控制。其命令格式为：

  FOR /L %%variable IN (start,step,end) DO command

  其中，start为开始计数的初始值，step为每次递增的值，end为结束值。当end小于start时，step需要设置为负数。

  含开关/L的for语句举例(创建5个文件夹)：

  ===============================================

  @echo off

  for /l %%i in (1,2,10) do md %%i

  pause

  ===============================================

  上例将新建5个文件夹，文件夹名称依次为1、3、5、7、9。可以发现，%%i的结束值并非end的值10，而是不大于end的一个数。

  3、开关/F

  含开关/F的for语句具有最强大的功能，它能够对字符串进行 *** 作，也能够对命令的返回值进行 *** 作，还可以访问硬盘上的ASCII码文件，比如txt文档等。其命令格式为：

  FOR /F ["options"] %%variable IN (set) DO command

  其中，set为("string"、'command'、file-set)中的一个；options是(eol=c、skip=n、delims=xxx、tokens=x,y,m-n、usebackq)中的一个或多个的组合。各选项的意义参见for /f。一般情况下，使用较多的是skip、tokens、delims三个选项。

  含开关/F的for语句举例：

  ===============================================

  @echo off

  echo **No Options:

  for /f %%a in ("1,2,10") do echo a=%%a

  echo **Options tokens ^&delims:

  for /f "tokens=1-3 delims=," %%a in ("1,2,10") do echo a=%%a b=%%b c=%%c

  pause

  ===============================================

  @echo off

  echo 本文件夹里面的文件有：

  for /f "skip=5 tokens=3* delims= " %%a in ('dir') do (

  if not "%%a"=="<DIR>" if not "%%b"=="字节" if not "%%b"=="可用字节" echo %%b

  )

  pause

  ===============================================

  @echo off

  echo 本文件夹里面的文件有：

  dir>c:\file.txt

  for /f "skip=5 tokens=3* delims= " %%a in (c:\file.txt) do (

  if not "%%a"=="<DIR>" if not "%%b"=="字节" if not "%%b"=="可用字节" echo %%b

  )

  del c:\file.txt

  pause

  ===============================================

  对于后面的两个例子，其中options里面的delims= 是可以删除的，因为只要添加了/F开关系统就将delims的值默认为空格。

  符号字符串中的最后一个字符星号，

  那么额外的变量将在最后一个符号解析之后

  分配并接受行的保留文本。本例中也可以改为4，不过文件名中有空格的文件，只能显示空格以前部分

  同时我们也看到了，for语句的do后面的command也是可以分行的，只需要保证command的左括号和do在同一行就可以了。

  4、开关/D或/R

  含开关/D或/R的for语句是与目录或文件有关的命令，一般情况下很少使用。含开关/R的命令有时候被用于通过遍历文件夹来查找某一个文件或文件夹，故而列举此例。

  含开关/R的for语句举例(文件夹遍历)：

  ===============================================

  @echo off

  setlocal enabledelayedexpansion

  FOR /R d: %%i IN (.) DO (

  set dd=%%i

  set "dd=!dd:~0,-1!"

  echo !dd!

  )

  pause

  exit

  ===============================================

  上例即可以罗列出D盘下的所有文件夹，其速度要比命令"tree d:"慢多了，不过其返回结果的实用性则远远超过了tree命令。

  一般情况下我们不推荐通过遍历文件夹来查找文件，特别是在查找某些程序(比如QQ.exe)的位置时。推荐通过reg命令查找注册表来查找QQ的路径，以保证查找效率。

  上例中也出现了几个新面孔，如setlocal、感叹号等。其中，感叹号其实就是变量百分号(%)的强化版。之所以要用!而不用%，是因为在for循环中，当一个变量被多次赋值时，%dd%所获取的仅仅是dd第一次被赋予的值；要想刷新dd的值，就必须首先通过命令"setlocal enabledelayedexpansion"来开启延迟变量开关，然后用!dd!来获取dd的值。

  for语句是批处理里面功能最强大、使用最普遍却又最难掌握的一套命令，这也是批处理菜鸟和批处理高手最明显的一个分水岭，一旦掌握了这套命令，那么你就离批处理达人不远了！

参考http://baike.baidu.com/view/80110.htm?fr=ala0_1_1#3_2

常用命令
echo、@、call、pause、rem(小技巧：用::代替rem)是批处理文件最常用的几个命令，我们就从他们开始学起。 

==== 注 =========== 

首先, @ 不是一个命令, 而是DOS 批处理的一个特殊标记符, 仅用于屏蔽命令行回显. 下面是DOS命令行或批处理中可能会见到的一些特殊标记符: 

CR(0D) 命令行结束符 

Escape(1B) ANSI转义字符引导符 

Space(20) 常用的参数界定符 

Tab(09) = 不常用的参数界定符 

+ COPY命令文件连接符 

* ? 文件通配符 

"" 字符串界定符 

| 命令管道符 

<>>>文件重定向符 

@ 命令行回显屏蔽符 

/ 参数开关引导符 

: 批处理标签引导符 

% 批处理变量引导符 

其次, :: 确实可以起到rem 的注释作用, 而且更简洁有效但有两点需要注意: 

第一, 除了 :: 之外, 任何以 :开头的字符行, 在批处理中都被视作标号, 而直接忽略其后的所有内容, 只是为了与正常的标号相区别, 建议使用 goto 所无法识别的标号, 即在 :后紧跟一个非字母数字的一个特殊符号. 

第二, 与rem 不同的是, ::后的字符行在执行时不会回显, 无论是否用echo on打开命令行回显状态, 因为命令解释器不认为他是一个有效的命令行, 就此点来看, rem 在某些场合下将比 :: 更为适用另外, rem 可以用于 config.sys 文件中. 

===================== 

echo 表示显示此命令后的字符 

echo off 表示在此语句后所有运行的命令都不显示命令行本身 

@与echo off相象，但它是加在每个命令行的最前面，表示运行时不显示这一行的命令行（只能影响当前行）。 

call 调用另一个批处理文件（如果不用call而直接调用别的批处理文件，那么执行完那个批处理文件后将无法返回当前文件并执行当前文件的后续命令）。 

pause 运行此句会暂停批处理的执行并在屏幕上显示Press any key to continue...的提示，等待用户按任意键后继续 

rem 表示此命令后的字符为解释行（注释），不执行，只是给自己今后参考用的（相当于程序中的注释）。 

==== 注 ===== 

此处的描述较为混乱, 不如直接引用个命令的命令行帮助更为条理 

------------------------- 

ECHO 

当程序运行时，显示或隐藏批处理程序中的正文。也可用于允许或禁止命令的回显。 

在运行批处理程序时，MS-DOS一般在屏幕上显示（回显）批处理程序中的命令。 

使用ECHO命令可关闭此功能。 

语法 

ECHO [ON|OFF] 

若要用echo命令显示一条命令，可用下述语法： 

echo [message] 

参数 

ON|OFF 

指定是否允许命令的回显。若要显示当前的ECHO的设置，可使用不带参数的ECHO 

命令。 

message 

指定让MS-DOS在屏幕上显示的正文。 

------------------- 

CALL 

从一个批处理程序中调用另一个批处理程序，而不会引起第一个批处理的中止。 

语法 

CALL [drive:][path]filename [batch-parameters] 

参数 

[drive:][path]filename 

指定要调用的批处理程序的名字及其存放处。文件名必须用.BAT作扩展名。 

batch-parameters 

指定批处理程序所需的命令行信息。 

------------------------------- 

PAUSE 

暂停批处理程序的执行并显示一条消息，提示用户按任意键继续执行。只能在批处 

理程序中使用该命令。 

语法 

PAUSE 

REM 

在批处理文件或CONFIG.SYS中加入注解。也可用REM命令来屏蔽命令（在CONFIG.SYS 

中也可以用分号 代替REM命令，但在批处理文件中则不能替代）。 

语法 

REM [string] 

参数 

string 

指定要屏蔽的命令或要包含的注解。 

======================= 

例1：用edit编辑a.bat文件，输入下列内容后存盘为c:\a.bat，执行该批处理文件后可实现：将根目录中所有文件写入 a.txt中，启动UCDOS，进入WPS等功能。 

批处理文件的内容为: 命令注释： 

@echo off 不显示后续命令行及当前命令行 

dir c:\*.* >a.txt 将c盘文件列表写入a.txt 

call c:\ucdos\ucdos.bat 调用ucdos 

echo 你好 显示"你好" 

pause 暂停,等待按键继续 

rem 准备运行wps 注释：准备运行wps 

cd ucdos 进入ucdos目录 

wps 运行wps 

批处理文件的参数 

批处理文件还可以像C语言的函数一样使用参数（相当于DOS命令的命令行参数），这需要用到一个参数表示符"%"。 

%[1-9]表示参数，参数是指在运行批处理文件时在文件名后加的以空格（或者Tab）分隔的字符串。变量可以从%0到%9，%0表示批处理命令本身，其它参数字符串用%1到%9顺序表示。 

例2：C:根目录下有一批处理文件名为f.bat，内容为： 

@echo off 

format %1 

如果执行C:\>f a: 

那么在执行f.bat时，%1就表示a:，这样format %1就相当于format a:，于是上面的命令运行时实际执行的是format a: 

例3：C:根目录下一批处理文件名为t.bat，内容为: 

@echo off 

type %1 

type %2 

那么运行C:\>t a.txt b.txt 

%1 : 表示a.txt 

%2 : 表示b.txt 

于是上面的命令将顺序地显示a.txt和b.txt文件的内容。 

==== 注 =============== 

参数在批处理中也作为变量处理, 所以同样使用百分号作为引导符, 其后跟0-9中的一个数字构成参数引用符. 引用符和参数之间 (例如上文中的 %1 与 a: ) 的关系类似于变量指针与变量值的关系. 当我们要引用第十一个或更多个参数时, 就必须移动DOS 的参数起始指针. shift 命令正充当了这个移动指针的角色, 它将参数的起始指针移动到下一个参数, 类似C 语言中的指针 *** 作. 图示如下: 

初始状态, cmd 为命令名, 可以用 %0 引用 

cmd arg1 arg2 arg3 arg4 arg5 arg6 arg7 arg8 arg9 arg10 

^ ^ ^ ^ ^ ^ ^ ^ ^ ^ 

| | | | | | | | | | 

%0 %1 %2 %3 %4 %5 %6 %7 %8 %9 

经过1次shift后, cmd 将无法被引用 

cmd arg1 arg2 arg3 arg4 arg5 arg6 arg7 arg8 arg9 arg10 

^ ^ ^ ^ ^ ^ ^ ^ ^ ^ 

| | | | | | | | | | 

%0 %1 %2 %3 %4 %5 %6 %7 %8 %9 

经过2次shift后, arg1也被废弃, %9指向为空, 没有引用意义 

cmd arg1 arg2 arg3 arg4 arg5 arg6 arg7 arg8 arg9 arg10 

^ ^ ^ ^ ^ ^ ^ ^ ^ 

| | | | | | | | | 

%0 %1 %2 %3 %4 %5 %6 %7 %8 

遗憾的是, win9x 和DOS下均不支持 shift 的逆 *** 作. 只有在 nt 内核命令行环境下, shift 才支持 /n 参数, 可以以第一参数为基准返复移动起始指针. 

================= 

特殊命令 

if goto choice for是批处理文件中比较高级的命令，如果这几个你用得很熟练，你就是批处理文件的专家啦。 

一、if 是条件语句，用来判断是否符合规定的条件，从而决定执行不同的命令。 有三种格式: 

1、if [not] "参数" == "字符串" 待执行的命令 

参数如果等于(not表示不等，下同)指定的字符串，则条件成立，运行命令，否则运行下一句。 

例：if "%1"=="a" format a: 

==== 

if 的命令行帮助中关于此点的描述为: 

IF [NOT] string1==string2 command 

在此有以下几点需要注意: 

1. 包含字符串的双引号不是语法所必须的, 而只是习惯上使用的一种"防空"字符 

2. string1 未必是参数, 它也可以是环境变量, 循环变量以及其他字符串常量或变量 

3. command 不是语法所必须的, string2 后跟一个空格就可以构成一个有效的命令行 

============================= 

2、if [not] exist [路径\]文件名 待执行的命令 

如果有指定的文件，则条件成立，运行命令，否则运行下一句。 

如: if exist c:\config.sys type c:\config.sys 

表示如果存在c:\config.sys文件，则显示它的内容。 

****** 注 ******** 

也可以使用以下的用法: 

if exist command 

device 是指DOS系统中已加载的设备, 在win98下通常有: 

AUX, PRN, CON, NUL 

COM1, COM2, COM3, COM4 

LPT1, LPT2, LPT3, LPT4 

XMSXXXX0, EMMXXXX0 

A: B: C: ..., 

CLOCK$, CONFIG$, DblBuff$, IFS$HLP$ 

具体的内容会因硬软件环境的不同而略有差异, 使用这些设备名称时, 需要保证以下三点: 

1. 该设备确实存在(由软件虚拟的设备除外) 

2. 该设备驱动程序已加载(aux, prn等标准设备由系统缺省定义) 

3. 该设备已准备好(主要是指a: b: ..., com1..., lpt1...等) 

可通过命令 mem/d | find "device" /i 来检阅你的系统中所加载的设备 

另外, 在DOS系统中, 设备也被认为是一种特殊的文件, 而文件也可以称作字符设备因为设备(device)与文件都是使用句柄(handle)来管理的, 句柄就是名字, 类似于文件名, 只不过句柄不是应用于磁盘管理, 而是应用于内存管理而已, 所谓设备加载也即指在内存中为其分配可引用的句柄. 

================================== 

3、if errorlevel <数字>待执行的命令 

很多DOS程序在运行结束后会返回一个数字值用来表示程序运行的结果(或者状态)，通过if errorlevel命令可以判断程序的返回值，根据不同的返回值来决定执行不同的命令(返回值必须按照从大到小的顺序排列)。如果返回值等于指定的数字，则条件成立，运行命令，否则运行下一句。 

如if errorlevel 2 goto x2 

==== 注 =========== 

返回值从大到小的顺序排列不是必须的, 而只是执行命令为 goto 时的习惯用法, 当使用 set 作为执行命令时, 通常会从小到大顺序排列, 比如需将返回码置入环境变量, 就需使用以下的顺序形式: 

if errorlevel 1 set el=1 

if errorlevel 2 set el=2 

if errorlevel 3 set el=3 

if errorlevel 4 set el=4 

if errorlevel 5 set el=5 

... 

当然, 也可以使用以下循环来替代, 原理是一致的: 

for %%e in (1 2 3 4 5 6 7 8...) do if errorlevel %%e set el=%%e 

更高效简洁的用法, 可以参考我写的另一篇关于获取 errorlevel 的文章 

出现此种现象的原因是, if errorlevel 比较返回码的判断条件并非等于, 而是大于等于. 由于 goto 的跳转特性, 由小到大排序会导致在较小的返回码处就跳出而由于 set命令的 "重复" 赋值特性, 由大到小排序会导致较小的返回码 "覆盖" 较大的返回码. 

另外, 虽然 if errorlevel=<数字>command 也是有效的命令行, 但也只是 command.com 解释命令行时将 = 作为命令行切分符而忽略掉罢了 

=========================== 

二、goto 批处理文件运行到这里将跳到goto所指定的标号(标号即label，标号用:后跟标准字符串来定义)处，goto语句一般与if配合使用，根据不同的条件来执行不同的命令组。 

如: 

goto end 

:end 

echo this is the end 

标号用":字符串"来定义，标号所在行不被执行。 

==== willsort 编注 

label 常被译为 "标签" , 但是这并不具有广泛的约定性. 

goto 与 : 联用可实现执行中途的跳转, 再结合 if 可实现执行过程的条件分支, 多个 if 即可实现命令的分组, 类似 C 中 switch case 结构或者 Basic 中的 select case 结构, 大规模且结构化的命令分组即可实现高级语言中的函数功能. 以下是批处理和C/Basic在语法结构上的对照: 

Batch C / Basic 

goto&: goto&: 

goto&:&if if{}&else{} / if&elseif&endif 

goto&:&if... switch&case / select case 

goto&:&if&set&envar... function() / function(),sub() 

================================== 

三、choice 使用此命令可以让用户输入一个字符（用于选择），从而根据用户的选择返回不同的errorlevel，然后于if errorlevel配合，根据用户的选择运行不同的命令。 

注意：choice命令为DOS或者Windows系统提供的外部命令，不同版本的choice命令语法会稍有不同，请用choice /?查看用法。 

choice的命令语法（该语法为Windows 2003中choice命令的语法，其它版本的choice的命令语法与此大同小异）： 

CHOICE [/C choices] [/N] [/CS] [/T timeout /D choice] [/M text] 

描述: 

该工具允许用户从选择列表选择一个项目并返回所选项目的索引。 

参数列表: 

/C choices 指定要创建的选项列表。默认列表是 "YN"。 

/N 在提示符中隐藏选项列表。提示前面的消息得到显示， 

选项依旧处于启用状态。 

/CS 允许选择分大小写的选项。在默认情况下，这个工具 

是不分大小写的。 

/T timeout 做出默认选择之前，暂停的秒数。可接受的值是从 0 

到 9999。如果指定了 0，就不会有暂停，默认选项 

会得到选择。 

/D choice 在 nnnn 秒之后指定默认选项。字符必须在用 /C 选 

项指定的一组选择中同时，必须用 /T 指定 nnnn。 

/M text 指定提示之前要显示的消息。如果没有指定，工具只 

显示提示。 

/? 显示帮助消息。 

注意: 

ERRORLEVEL 环境变量被设置为从选择集选择的键索引。列出的第一个选 

择返回 1，第二个选择返回 2，等等。如果用户按的键不是有效的选择， 

该工具会发出警告响声。如果该工具检测到错误状态，它会返回 255 的 

ERRORLEVEL 值。如果用户按 Ctrl+Break 或 Ctrl+C 键，该工具会返回 0 

的 ERRORLEVEL 值。在一个批程序中使用 ERRORLEVEL 参数时，将参数降 

序排列。 

示例: 

CHOICE /? 

CHOICE /C YNC /M "确认请按 Y，否请按 N，或者取消请按 C。" 

CHOICE /T 10 /C ync /CS /D y 

CHOICE /C ab /M "选项 1 请选择 a，选项 2 请选择 b。" 

CHOICE /C ab /N /M "选项 1 请选择 a，选项 2 请选择 b。" 

==== willsort 编注 =============================== 

我列出win98下choice的用法帮助, 已资区分 

Waits for the user to choose one of a set of choices. 

等待用户选择一组待选字符中的一个 

CHOICE [/C[:]choices] [/N] [/S] [/T[:]c,nn] [text] 

/C[:]choices Specifies allowable keys. Default is YN 

指定允许的按键(待选字符), 默认为YN 

/N Do not display choices and ? at end of prompt string. 

不显示提示字符串中的问号和待选字符 

/S Treat choice keys as case sensitive. 

处理待选字符时大小写敏感 

/T[:]c,nn Default choice to c after nn seconds 

在 nn 秒后默认选择 c 

text Prompt string to display 

要显示的提示字符串 

ERRORLEVEL is set to offset of key user presses in choices. 

ERRORLEVEL 被设置为用户键入的字符在待选字符中的偏移值 

如果我运行命令：CHOICE /C YNC /M "确认请按 Y，否请按 N，或者取消请按 C。" 

屏幕上会显示： 

确认请按 Y，否请按 N，或者取消请按 C。 [Y,N,C]? 

例：test.bat的内容如下（注意，用if errorlevel判断返回值时，要按返回值从高到低排列）: 

@echo off 

choice /C dme /M "defrag,mem,end" 

if errorlevel 3 goto end 

if errorlevel 2 goto mem 

if errorlevel 1 goto defrag 

:defrag 

c:\dos\defrag 

goto end 

:mem 

mem 

goto end 

:end 

echo good bye 

此批处理运行后，将显示"defrag,mem,end[D,M,E]?" ，用户可选择d m e ，然后if语句根据用户的选择作出判断，d表示执行标号为defrag的程序段，m表示执行标号为mem的程序段，e表示执行标号为end的程序段，每个程序段最后都以goto end将程序跳到end标号处，然后程序将显示good bye，批处理运行结束。 

四、for 循环命令，只要条件符合，它将多次执行同一命令。 

语法： 

对一组文件中的每一个文件执行某个特定命令。 

FOR %%variable IN (set) DO command [command-parameters] 

%%variable 指定一个单一字母可替换的参数。 

(set) 指定一个或一组文件。可以使用通配符。 

command 指定对每个文件执行的命令。 

command-parameters 

为特定命令指定参数或命令行开关。 

例如一个批处理文件中有一行: 

for %%c in (*.bat *.txt) do type %%c 

则该命令行会显示当前目录下所有以bat和txt为扩展名的文件的内容。 

==== willsort 编注 ===================================================== 

需要指出的是, 当()中的字符串并非单个或多个文件名时, 它将单纯被当作字符串替换, 这个特性再加上()中可以嵌入多个字符串的特性, 很明显 for 可以被看作一种遍历型循环. 

当然, 在 nt/2000/xp/2003 系列的命令行环境中, for 被赋予了更多的特性, 使之可以分析命令输出或者文件中的字符串, 也有很多开关被用于扩展了文件替换功能. 

======================================================================== 

批处理示例 

1. IF-EXIST 

1) 首先用记事本在C:\建立一个test1.bat批处理文件，文件内容如下： 

@echo off 

IF EXIST \AUTOEXEC.BAT TYPE \AUTOEXEC.BAT 

IF NOT EXIST \AUTOEXEC.BAT ECHO \AUTOEXEC.BAT does not exist 

然后运行它： 

C:\>TEST1.BAT 

如果C:\存在AUTOEXEC.BAT文件，那么它的内容就会被显示出来，如果不存在，批处理就会提示你该文件不存在。 

2) 接着再建立一个test2.bat文件，内容如下： 

@ECHO OFF 

IF EXIST \%1 TYPE \%1 

IF NOT EXIST \%1 ECHO \%1 does not exist 

执行: 

C:\>TEST2 AUTOEXEC.BAT 

该命令运行结果同上。 

说明： 

(1) IF EXIST 是用来测试文件是否存在的，格式为 

IF EXIST [路径+文件名] 命令 

(2) test2.bat文件中的%1是参数，DOS允许传递9个批参数信息给批处理文件，分别为%1~%9(%0表示test2命令本身) ，这有点象编程中的实参和形参的关系，%1是形参，AUTOEXEC.BAT是实参。 

==== willsort 编注 ===================================================== 

DOS没有 "允许传递9个批参数信息" 的限制, 参数的个数只会受到命令行长度和所调用命令处理能力的限制. 但是, 我们在批处理程序中, 在同一时刻只能同时引用10个参数, 因为 DOS只给出了 %0~%9这十个参数引用符. 

======================================================================== 

3) 更进一步的，建立一个名为TEST3.BAT的文件，内容如下： 

@echo off 

IF "%1" == "A" ECHO XIAO 

IF "%2" == "B" ECHO TIAN 

IF "%3" == "C" ECHO XIN 

如果运行： 

C:\>TEST3 A B C 

屏幕上会显示: 

XIAO 

TIAN 

XIN 

如果运行： 

C:\>TEST3 A B 

屏幕上会显示 

XIAO 

TIAN 

在这个命令执行过程中，DOS会将一个空字符串指定给参数%3。 

2、IF-ERRORLEVEL 

建立TEST4.BAT，内容如下： 

@ECHO OFF 

XCOPY C:\AUTOEXEC.BAT D:\ 

IF ERRORLEVEL 1 ECHO 文件拷贝失败 

IF ERRORLEVEL 0 ECHO 成功拷贝文件 

然后执行文件: 

C:\>TEST4 

如果文件拷贝成功，屏幕就会显示"成功拷贝文件"，否则就会显示"文件拷贝失败"。 

IF ERRORLEVEL 是用来测试它的上一个DOS命令的返回值的，注意只是上一个命令的返回值，而且返回值必须依照从大到小次序顺序判断。 

因此下面的批处理文件是错误的： 

@ECHO OFF 

XCOPY C:\AUTOEXEC.BAT D:\ 

IF ERRORLEVEL 0 ECHO 成功拷贝文件 

IF ERRORLEVEL 1 ECHO 未找到拷贝文件 

IF ERRORLEVEL 2 ECHO 用户通过ctrl-c中止拷贝 *** 作 

IF ERRORLEVEL 3 ECHO 预置错误阻止文件拷贝 *** 作 

IF ERRORLEVEL 4 ECHO 拷贝过程中写盘错误 

无论拷贝是否成功，后面的： 

未找到拷贝文件 

用户通过ctrl-c中止拷贝 *** 作 

预置错误阻止文件拷贝 *** 作 

拷贝过程中写盘错误 

都将显示出来。 

以下就是几个常用命令的返回值及其代表的意义： 

backup 

0 备份成功 

1 未找到备份文件 

2 文件共享冲突阻止备份完成 

3 用户用ctrl-c中止备份 

4 由于致命的错误使备份 *** 作中止 

diskcomp 

0 盘比较相同 

1 盘比较不同 

2 用户通过ctrl-c中止比较 *** 作 

3 由于致命的错误使比较 *** 作中止 

4 预置错误中止比较 

diskcopy 

0 盘拷贝 *** 作成功 

1 非致命盘读/写错 

2 用户通过ctrl-c结束拷贝 *** 作 

3 因致命的处理错误使盘拷贝中止 

4 预置错误阻止拷贝 *** 作 

format 

0 格式化成功 

3 用户