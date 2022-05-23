---
title: MongoDB
catalog: true
lang: cn
date: 2022-03-22 20:15:29
subtitle: MongoDB学习
header-img: /img/header_img/nier.png
sticky: 996
tags:
- MongoDB
categories:
---

## MongoDB简介
MongoDB 是一个基于分布式文件存储的数据库。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。
MongoDB 是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。

**非关系型数据库NoSQL**

NoSQL(NoSQL = Not Only SQL )，意即"不仅仅是SQL"。

通过应用实践证明，关系模型是非常适合于客户服务器编程，远远超出预期的利益，今天它是结构化数据存储在网络和商务应用的主导技术。

NoSQL 是一项全新的数据库革命性运动，早期就有人提出，发展至2009年趋势越发高涨。NoSQL的拥护者们提倡运用非关系型的数据存储，相对于铺天盖地的关系型数据库运用，这一概念无疑是一种全新的思维的注入。

NoSQL，指的是非关系型的数据库。NoSQL有时也称作Not Only SQL的缩写，是对不同于传统的关系型数据库的数据库管理系统的统称。

NoSQL用于超大规模数据的存储。（例如谷歌或Facebook每天为他们的用户收集万亿比特的数据）。这些类型的数据存储不需要固定的模式，无需多余操作就可以横向扩展。

**MongoDB**

MongoDB 是由C++语言编写的，是一个基于分布式文件存储的开源数据库系统。  
在高负载的情况下，添加更多的节点，可以保证服务器性能。  
MongoDB 旨在为WEB应用提供可扩展的高性能数据存储解决方案。  
MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。

MongoDB下载： <https://www.mongodb.com/try/download/community>

**MongoDB的主要特点**

+ MongoDB 是一个面向文档存储的数据库，操作起来比较简单和容易。
+ 你可以在MongoDB记录中设置任何属性的索引 (如：FirstName="Sameer",Address="8 Gandhi Road")来实现更快的排序。
+ 你可以通过本地或者网络创建数据镜像，这使得MongoDB有更强的扩展性。
+ 如果负载的增加（需要更多的存储空间和更强的处理能力） ，它可以分布在计算机网络中的其他节点上这就是所谓的分片。
+ Mongo支持丰富的查询表达式。查询指令使用JSON形式的标记，可轻易查询文档中内嵌的对象及数组。
+ MongoDb 使用update()命令可以实现替换完成的文档（数据）或者一些指定的数据字段 。
+ Mongodb中的Map/reduce主要是用来对数据进行批量处理和聚合操作。
+ Map和Reduce。Map函数调用emit(key,value)遍历集合中所有的记录，将key与value传给Reduce函数进行处理。
+ Map函数和Reduce函数是使用Javascript编写的，并可以通过db.runCommand或mapreduce命令来执行MapReduce操作。
+ GridFS是MongoDB中的一个内置功能，可以用于存放大量小文件。
+ MongoDB允许在服务端执行脚本，可以用Javascript编写某个函数，直接在服务端执行，也可以把函数的定义存储在服务端，下次直接调用即可。
+ MongoDB支持各种编程语言:RUBY，PYTHON，JAVA，C++，PHP，C#等多种语言。
+ MongoDB安装简单。

## MongoDB概念解析

不管我们学习什么数据库都应该学习其中的基础概念，在mongodb中基本的概念是文档、集合、数据库，下面我们挨个介绍。  
下表将帮助您更容易理解Mongo中的一些概念：

| SQL术语/概念 | MongoDB术语/概念 | 解释/说明 |
| :---  |  :-----  |   :------  |
| database | database | 数据库 |
| table | collection | 数据库表/集合 |
| row | document | 数据记录行/文档 |
| column | field | 数据字段/域 |
| index | index | 索引 |
| table | joins	| 表连接,MongoDB不支持 |
| primary key | primary key | 主键,MongoDB自动将_id字段设置为主键 |

通过下图实例，我们也可以更直观的了解Mongo中的一些概念：

![表与MongoDB](Figure-1-Mapping-Table-to-Collection-1.png)

### 数据库

一个mongodb中可以建立多个数据库。  
MongoDB的默认数据库为"db"，该数据库存储在data目录中。  
MongoDB的单个实例可以容纳多个独立的数据库，每一个都有自己的集合和权限，不同的数据库也放置在不同的文件中。  

"show dbs" 命令可以显示所有数据的列表。  
"db" 命令可显示当前数据库对象或集合

数据库也通过名字来标识。数据库名可以是满足以下条件的任意UTF-8字符串。  
+ 不能是空字符串（"")。
+ 不得含有' '（空格)、.、$、/、\和\0 (空字符)。
+ 应全部小写。
+ 最多64字节。

有一些数据库名是保留的，可以直接访问这些有特殊作用的数据库。

+ admin： 从权限的角度来看，这是"root"数据库。要是将一个用户添加到这个数据库，这个用户自动继承所有数据库的权限。一些特定的服务器端命令也只能从这个数据库运行，比如列出所有的数据库或者关闭服务器。
+ local: 这个数据永远不会被复制，可以用来存储限于本地单台服务器的任意集合
+ config: 当Mongo用于分片设置时，config数据库在内部使用，用于保存分片的相关信息。

### 集合

集合就是 MongoDB 文档组，类似于 RDBMS （关系数据库管理系统：Relational Database Management System)中的表格。  
集合存在于数据库中，集合没有固定的结构，这意味着你在对集合可以插入不同格式和类型的数据，但通常情况下我们插入集合的数据都会有一定的关联性。  
比如，我们可以将以下不同数据结构的文档插入到集合中：

```json
{"site":"www.baidu.com"}
{"site":"www.google.com","name":"Google"}
```

当第一个文档插入时，集合就会被创建。

`合法的集合名`
+ 集合名不能是空字符串""。
+ 集合名不能含有\0字符（空字符)，这个字符表示集合名的结尾。
+ 集合名不能以"system."开头，这是为系统集合保留的前缀。
+ 用户创建的集合名字不能含有保留字符。有些驱动程序的确支持在集合名里面包含，这是因为某些系统生成的集合中包含该字符。除非你要访问这种系统创建的集合，否则千万不要在名字里出现$。　

`capped collections`
Capped collections 就是固定大小的collection。  
它有很高的性能以及队列过期的特性(过期按照插入的顺序). 有点和 "RRD" 概念类似。  
Capped collections 是高性能自动的维护对象的插入顺序。它非常适合类似记录日志的功能。和标准的 collection 不同，你必须要显式的创建一个capped collection，指定一个 collection 的大小，单位是字节。collection 的数据存储空间值提前分配的。  
Capped collections 可以按照文档的插入顺序保存到集合中，而且这些文档在磁盘上存放位置也是按照插入顺序来保存的，所以当我们更新Capped collections 中文档的时候，更新后的文档不可以超过之前文档的大小，这样话就可以确保所有文档在磁盘上的位置一直保持不变。  
由于 Capped collection 是按照文档的插入顺序而不是使用索引确定插入位置，这样的话可以提高增添数据的效率。MongoDB 的操作日志文件 oplog.rs 就是利用 Capped Collection 来实现的。  
要注意的是指定的存储大小包含了数据库的头信息。

```c
db.createCollection("mycoll", {capped:true, size:100000})
```

+ 在 capped collection 中，你能添加新的对象。
+ 能进行更新，然而，对象不会增加存储空间。如果增加，更新就会失败 。
+ 使用 Capped Collection 不能删除一个文档，可以使用 drop() 方法删除 collection 所有的行。
+ 删除之后，你必须显式的重新创建这个 collection。
+ 在32bit机器中，capped collection 最大存储为 1e9( 1*10^9)个字节。

### 文档

文档是一组键值(key-value)对(即 BSON)。MongoDB 的文档不需要设置相同的字段，并且相同的字段不需要相同的数据类型，这与关系型数据库有很大的区别，也是 MongoDB 非常突出的特点。

需要注意的是：

+ 文档中的键/值对是有序的。
+ 文档中的值不仅可以是在双引号里面的字符串，还可以是其他几种数据类型（甚至可以是整个嵌入的文档)。
+ MongoDB区分类型和大小写。
+ MongoDB的文档不能有重复的键。
+ 文档的键是字符串。除了少数例外情况，键可以使用任意UTF-8字符。

文档键命名规范：

+ 键不能含有\0 (空字符)。这个字符用来表示键的结尾。
+ .和$有特别的意义，只有在特定环境下才能使用。
+ 以下划线"_"开头的键是保留的(不是严格要求的)。

### 元数据

数据库的信息是存储在集合中。它们使用了系统的命名空间：

```
dbname.system.*
```

在MongoDB数据库中名字空间 &lt;dbname>.system.* 是包含多种系统信息的特殊集合(Collection)，如下:

| 集合命名空间 | 描述 |
| :----  | :--------- |
| dbname.system.namespaces	| 列出所有名字空间。 |
| dbname.system.indexes | 列出所有索引。 |
| dbname.system.profile | 包含数据库概要(profile)信息。 |
| dbname.system.users | 列出所有可访问数据库的用户。 |
| dbname.local.sources | 包含复制对端（slave）的服务器信息和状态。 |

对于修改系统集合中的对象有如下限制。  
在{{system.indexes}}插入数据，可以创建索引。但除此之外该表信息是不可变的(特殊的drop index命令将自动更新相关信息)。  
{{system.users}}是可修改的。 {{system.profile}}是可删除的。

## MongoDB 数据类型

下表为MongoDB中常用的几种数据类型。

| 数据类型 | 描述 |
| :---- | :------- |
| String | 字符串。存储数据常用的数据类型。在 MongoDB 中，UTF-8 编码的字符串才是合法的。 |
| Integer | 整型数值。用于存储数值。根据你所采用的服务器，可分为 32 位或 64 位。 |
| Boolean | 布尔值。用于存储布尔值（真/假）。 |
| Double | 双精度浮点值。用于存储浮点值。 |
| Min/Max keys | 将一个值与 BSON（二进制的 JSON）元素的最低值和最高值相对比。 |
| Array | 用于将数组或列表或多个值存储为一个键。 |
| Timestamp | 时间戳。记录文档修改或添加的具体时间。 |
| Object | 用于内嵌文档。 |
| Null | 用于创建空值。 |
| Symbol | 符号。该数据类型基本上等同于字符串类型，但不同的是，它一般用于采用特殊符号类型的语言。 |
| Date | 日期时间。用 UNIX 时间格式来存储当前日期或时间。你可以指定自己的日期时间：创建 Date 对象，传入年月日信息。 |
| Object ID | 对象 ID。用于创建文档的 ID。 |
| Binary Data | 二进制数据。用于存储二进制数据。 |
| Code |代码类型。用于在文档中存储 JavaScript 代码。 |
| Regular expression | 正则表达式类型。用于存储正则表达式。 |

下面说明下几种重要的数据类型。

`ObjectId`

ObjectId 类似唯一主键，可以很快的去生成和排序，包含 12 bytes，含义是：

+ 前 4 个字节表示创建 unix 时间戳,格林尼治时间 UTC 时间，比北京时间晚了 8 个小时
+ 接下来的 3 个字节是机器标识码
+ 紧接的两个字节由进程 id 组成 PID
+ 最后三个字节是随机数

![ObjectId](ObjectId.jpeg)

MongoDB 中存储的文档必须有一个 _id 键。这个键的值可以是任何类型的，默认是个 ObjectId 对象

由于 ObjectId 中保存了创建的时间戳，所以你不需要为你的文档保存时间戳字段，你可以通过 getTimestamp 函数来获取文档的创建时间:

```c
> var newObject = ObjectId()
> newObject.getTimestamp()
ISODate("2022-03-23T06:31:09.000Z")
```

ObjectId 转为字符串

```c
> newObject.str
623abece277b0000e1003d84
```


## MongoDB可视化工具

MongoDB可视化工具软件有很多，推荐三款正在使用的：

+ navicat
+ mongo campass
+ robo3T

## MongoDB数据库操作

### 创建数据库

语法：  
```mongodb
use DATABASE_NAME
```

如果数据库不存在，则创建数据库，否则切换到指定数据库。

```
> use testdb
switched to db testdb
> db
testdb
>
```

如果你想查看所有数据库，可以使用 show dbs 命令：

```
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
> 
```

可以看到，我们刚创建的数据库 newTestDB 并不在数据库的列表中， 要显示它，我们需要向 newTestDB 数据库插入一些数据。

```c
> db.collection1.insert({"name":"name1","value":1})
WriteResult({ "nInserted" : 1 })
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
testdb  0.000GB
```

MongoDB 中默认的数据库为 test，如果你没有创建新的数据库，集合将存放在 test 数据库中。

> 注意: 在 MongoDB 中，集合只有在内容插入后才会创建! 就是说，创建集合(数据表)后要再插入一个文档(记录)，集合才会真正创建。

### 删除数据库

语法：  

```
db.dropDatabase()
```

### 创建集合

语法：  

```
db.createCollection(name, options)
```

+ name: 要创建的集合名称
+ options: 可选参数, 指定有关内存大小及索引的选项
  + capped: 布尔类型，如果为 true，则创建固定集合。固定集合是指有着固定大小的集合，当达到最大值时，它会自动覆盖最早的文档。当该值为 true 时，必须指定 size 参数。
  + size: 数值，为固定集合指定一个最大值，即字节数。如果 capped 为 true，也需要指定该字段。
  + max: 数值，指定固定集合中包含文档的最大数量。

在插入文档时，MongoDB 首先检查固定集合的 size 字段，然后检查 max 字段。

如果要查看已有集合，可以使用 `show collections` 或 `show tables` 命令：  

下面是带有几个关键参数的 createCollection() 的用法：  
创建固定集合 mycol，整个集合空间大小 6142800 B, 文档最大个数为 10000 个。

```c
> db.createCollection("mycol", { capped : true, autoIndexId : true, size : 
   6142800, max : 10000 } )
{ "ok" : 1 }
>
```

在 MongoDB 中，当你插入一些文档时，MongoDB 会自动创建集合。

### 删除集合

语法：  

```c
db.collection.drop()
```

如果成功删除选定集合，则 drop() 方法返回 true，否则返回 false。

### 插入文档

文档的数据结构和 JSON 基本一样。  
所有存储在集合中的数据都是 BSON 格式。  
BSON 是一种类似 JSON 的二进制形式的存储格式，是 Binary JSON 的简称。

语法：  

```
db.COLLECTION_NAME.insert(document)
或
db.COLLECTION_NAME.save(document)
```

+ save()：如果 _id 主键存在则更新数据，如果不存在就插入数据。该方法新版本中已废弃，可以使用 db.collection.insertOne() 或 db.collection.replaceOne() 来代替。
+ insert(): 若插入的数据主键已经存在，则会抛 org.springframework.dao.DuplicateKeyException 异常，提示主键重复，不保存当前数据。

3.2 版本之后新增了 db.collection.insertOne() 和 db.collection.insertMany()。

db.collection.insertOne() 用于向集合插入一个新文档，语法格式如下：

```
db.collection.insertOne(
   <document>,
   {
      writeConcern: <document>
   }
)
```

db.collection.insertMany() 用于向集合插入一个多个文档，语法格式如下：

```
db.collection.insertMany(
   [ <document 1> , <document 2>, ... ],
   {
      writeConcern: <document>,
      ordered: <boolean>
   }
)
```

+ document：要写入的文档。
+ writeConcern：写入策略，默认为 1，即要求确认写操作，0 是不要求。
+ ordered：指定是否按顺序写入，默认 true，按顺序写入。

我们也可以将数据定义为一个变量，如下所示：

```js
document=({title: 'MongoDB', 
    description: 'MongoDB 是一个 Nosql 数据库',
    by: 'blog',
    url: 'http://www.bravogohome.top',
    tags: ['mongodb', 'database', 'NoSQL'],
    likes: 100
});
```

执行后显示结果如下：

```json
// 1
{
    "title": "MongoDB",
    "description": "MongoDB 是一个 Nosql 数据库",
    "by": "blog",
    "url": "http://www.bravogohome.top",
    "tags": [
        "mongodb",
        "database",
        "NoSQL"
    ],
    "likes": 100
}
```

执行插入操作：  

```
db.testcollection.insert(document)
```

### 查询文档

语法：  

```
db.collection.find(query, projection)
```

+ query ：可选，使用查询操作符指定查询条件
+ projection ：可选，使用投影操作符指定返回的键。查询时返回文档中所有键值， 只需省略该参数即可（默认省略）。

如果你需要以易读的方式来读取数据，可以使用 pretty() 方法，语法格式如下：

> db.col.find().pretty()

pretty() 方法以格式化的方式来显示所有文档。

如果你熟悉常规的 SQL 数据，通过下表可以更好的理解 MongoDB 的条件语句查询：

| 操作 | 格式 | 范例 | RDBMS中的类似语句 |
| :-- | :--: | :---- | :----- |
| 等于 | {&lt;key>:&lt;value>} | db.col.find({"name":"name1"}).pretty() | where name = 'name1' |
| 小于 | {&lt;key>:{$lt:&lt;value>}} | db.col.find({"likes":{$lt:50}}).pretty() | where likes < 50 |
| 小于或等于 | {&lt;key>:{$lte:&lt;value>}} | db.col.find({"likes":{$lte:50}}).pretty() | where likes <= 50 |
| 大于 | {&lt;key>:{$gt:&lt;value>}} | db.col.find({"likes":{$gt:50}}).pretty() | where likes > 50 |
| 大于或等于 | {&lt;key>:{$gte:&lt;value>}} | db.col.find({"likes":{$gte:50}}).pretty() | where likes >= 50 |
| 不等于 | {&lt;key>:{$ne:&lt;value>}} | db.col.find({"likes":{$ne:50}}).pretty() | where likes != 50 |

MongoDB 的 find() 方法可以传入多个键(key)，每个键(key)以逗号隔开，即常规 SQL 的 AND 条件。

语法格式如下：

> db.col.find({key1:value1, key2:value2}).pretty()

MongoDB OR 条件语句使用了关键字 $or,语法格式如下：

```cpp
db.col.find(
   {
      $or: [
         {key1: value1}, {key2:value2}
      ]
   }
).pretty()
```

### 更新文档

MongoDB 使用 update() 和 save() 方法来更新集合中的文档。接下来让我们详细来看下两个函数的应用及其区别。

update() 方法用于更新已存在的文档。语法格式如下：

```cpp
db.collection.update(
   <query>,
   <update>,
   {
     upsert: <boolean>,
     multi: <boolean>,
     writeConcern: <document>
   }
)
```

参数说明：

+ query : update的查询条件，类似sql update查询内where后面的。
+ update : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内set后面的
+ upsert : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
+ multi : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
+ writeConcern :可选，抛出异常的级别。

实例：  

```cpp
db.coll2.update({"title":"MongoDB"},{$set:{"likes":"0"}})
```

> db.collection.updateOne() 向指定集合更新单个文档
> db.collection.updateMany() 向指定集合更新多个文档

save() 方法通过传入的文档来替换已有文档，_id 主键存在就更新，不存在就插入。语法格式如下：

```cpp
db.collection.save(
   <document>,
   {
     writeConcern: <document>
   }
)
```

参数说明：

+ document : 文档数据。
+ writeConcern :可选，抛出异常的级别。

### 删除文档

MongoDB remove() 函数是用来移除集合中的数据。

MongoDB 数据更新可以使用 update() 函数。在执行 remove() 函数前先执行 find() 命令来判断执行的条件是否正确，这是一个比较好的习惯。

语法：  

```cpp
db.collection.remove(
   <query>,
   {
     justOne: <boolean>,
     writeConcern: <document>
   }
)
```

参数说明：  

+ query :（可选）删除的文档的条件。
+ justOne : （可选）如果设为 true 或 1，则只删除一个文档，如果不设置该参数，或使用默认值 false，则删除所有匹配条件的文档。
+ writeConcern :（可选）抛出异常的级别。

如果你想删除所有数据，可以使用以下方式（类似常规 SQL 的 truncate 命令）：

> db.col.remove({})

remove() 方法已经过时了，现在官方推荐使用 deleteOne() 和 deleteMany() 方法。

如删除集合下全部文档：

```
db.inventory.deleteMany({})
```

删除 status 等于 A 的全部文档：

```
db.inventory.deleteMany({ status : "A" })
```

删除 status 等于 D 的一个文档：

```
db.inventory.deleteOne( { status: "D" } )
```

## MongoDB条件操作符

条件操作符用于比较两个表达式并从mongoDB集合中获取数据。

在本章节中，我们将讨论如何在MongoDB中使用条件操作符。

MongoDB中条件操作符有：

+ (>) 大于 - $gt
+ (<) 小于 - $lt
+ (>=) 大于等于 - $gte
+ (<= ) 小于等于 - $lte
+ (!=) 不等于 - $ne
+ 特殊操作符 - $type

`MongoDB $type操作符`

\$type操作符是基于BSON类型来检索集合中匹配的数据类型，并返回结果。

MongoDB 中可以使用的类型如下表所示：

| 类型 | 数字 | 备注 |
| :--- | :----: | :---- |
| Double | 1 | |
| String | 2 | |
| Object | 3 | |
| Array | 4	| |
| Binary data | 5 |
| Undefined | 6 | 已废弃。 |
| Object id | 7 |	|
| Boolean | 8 |	| 
| Date | 9 |  |
| Null | 10 | | 
| Regular Expression | 11 | |
| JavaScript | 13 | |
| Symbol | 14 | |
| JavaScript (with scope) | 15 |	| 
| 32-bit integer | 16 |	 | 
| Timestamp | 17	| | 
| 64-bit integer | 18 |  |
| Min key | 255 | Query with -1 |
| Max key | 127 | | 

如果想获取 "col" 集合中 title 为 String 的数据，你可以使用以下命令：

```
db.col.find({"title" : {$type : 2}})
或
db.col.find({"title" : {$type : 'string'}})
```

## MongoDB Limit与SKip方法

### Limit()

如果你需要在MongoDB中读取指定数量的数据记录，可以使用MongoDB的Limit方法，limit()方法接受一个数字参数，该参数指定从MongoDB中读取的记录条数。

语法:  

```
db.COLLECTION_NAME.find().limit(NUMBER)
```

> 如果你们没有指定limit()方法中的参数则显示集合中的所有数据。

### Skip()

我们除了可以使用limit()方法来读取指定数量的数据外，还可以使用skip()方法来跳过指定数量的数据，skip方法同样接受一个数字参数作为跳过的记录条数。

语法:   

```
db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)
```

> skip()方法默认参数为 0 。

## MongoDB排序

在 MongoDB 中使用 sort() 方法对数据进行排序，sort() 方法可以通过参数指定排序的字段，并使用 1 和 -1 来指定排序的方式，其中 1 为升序排列，而 -1 是用于降序排列。

语法：  

```
db.COLLECTION_NAME.find().sort({KEY:1})
```

> skip(), limilt(), sort()三个放在一起执行的时候，执行的顺序是先 sort(), 然后是 skip()，最后是显示的 limit()。

## MongoDB索引

索引通常能够极大的提高查询的效率，如果没有索引，MongoDB在读取数据时必须扫描集合中的每个文件并选取那些符合查询条件的记录。  
这种扫描全集合的查询效率是非常低的，特别在处理大量的数据时，查询可以要花费几十秒甚至几分钟，这对网站的性能是非常致命的。  
索引是特殊的数据结构，索引存储在一个易于遍历读取的数据集合中，索引是对数据库表中一列或多列的值进行排序的一种结构。  

### 创建索引

MongoDB使用 createIndex() 方法来创建索引。

语法：  

```
db.collection.createIndex(keys, options)
```

语法中 Key 值为你要创建的索引字段，1 为指定按升序创建索引，如果你想按降序来创建索引指定为 -1 即可。  
createIndex() 方法中你也可以设置使用多个字段创建索引（关系型数据库中称作复合索引）。

createIndex() 接收可选参数，可选参数列表如下：

| Parameter | Type | Description |
| :----- | :----- | :------------ |
| background | Boolean | 建索引过程会阻塞其它数据库操作，background可指定以后台方式创建索引，即增加 "background" 可选参数。 "background" 默认值为false。 |
| unique | Boolean | 建立的索引是否唯一。指定为true创建唯一索引。默认值为false. |
| name | string | 索引的名称。如果未指定，MongoDB的通过连接索引的字段名和排序顺序生成一个索引名称。 |
| dropDups | Boolean | 3.0+版本已废弃。在建立唯一索引时是否删除重复记录,指定 true 创建唯一索引。默认值为 false. |
| sparse | Boolean | 对文档中不存在的字段数据不启用索引；这个参数需要特别注意，如果设置为true的话，在索引字段中不会查询出不包含对应字段的文档.。默认值为 false. |
| expireAfterSeconds | integer | 指定一个以秒为单位的数值，完成 TTL设定，设定集合的生存时间。 |
| v | index version | 索引的版本号。默认的索引版本取决于mongod创建索引时运行的版本。 |
| weights | document | 索引权重值，数值在 1 到 99,999 之间，表示该索引相对于其他索引字段的得分权重。 |
| default_language | string | 对于文本索引，该参数决定了停用词及词干和词器的规则的列表。 默认为英语 |
| language_override | string | 对于文本索引，该参数指定了包含在文档中的字段名，语言覆盖默认的language，默认值为 language. |

### 查看集合索引

```
db.col.getIndexes()
```

### 查看集合索引大小

```
db.col.totalIndexSize()
```

### 删除集合所有索引

```
db.col.dropIndexes()
```

### 删除集合指定索引

```
db.col.dropIndex("索引名称")
```

## MongoDB聚合

MongoDB 中聚合(aggregate)主要用于处理数据(诸如统计平均值，求和等)，并返回计算后的数据结果。  
有点类似 SQL 语句中的 count(*)。

### aggregate()

语法：  

```
db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)
```

下表展示了一些聚合的表达式:

| 表达式 | 描述 | 实例 |
| :---- | :------- | :--------- |
| $sum | 计算总和。 | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : "$likes"}}}]) |
| $avg | 计算平均值 | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$avg : "$likes"}}}]) |
| $min | 获取集合中所有文档对应值得最小值。 | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$min : "$likes"}}}]) |
| $max | 获取集合中所有文档对应值得最大值。	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$max : "$likes"}}}]) |
| $push | 将值加入一个数组中，不会判断是否有重复的值。	 | db.mycol.aggregate([{$group : {_id : "$by_user", url : {$push: "$url"}}}]) |
| $addToSet | 将值加入一个数组中，会判断是否有重复的值，若相同的值在数组中已经存在了，则不加入。 | 	db.mycol.aggregate([{$group : {_id : "$by_user", url : {$addToSet : "$url"}}}]) |
| $first | 根据资源文档的排序获取第一个文档数据。 |  db.mycol.aggregate([{$group : {_id : "$by_user", first_url : {$first : "$url"}}}]) |
| $last | 根据资源文档的排序获取最后一个文档数据 | db.mycol.aggregate([{$group : {_id : "$by_user", last_url : {$last : "$url"}}}]) |

### 管道的概念

管道在Unix和Linux中一般用于将当前命令的输出结果作为下一个命令的参数。  
MongoDB的聚合管道将MongoDB文档在一个管道处理完毕后将结果传递给下一个管道处理。管道操作是可以重复的。  
表达式：处理输入文档并输出。表达式是无状态的，只能用于计算当前聚合管道的文档，不能处理其它的文档。  

这里我们介绍一下聚合框架中常用的几个操作：  

+ $project：修改输入文档的结构。可以用来重命名、增加或删除域，也可以用于创建计算结果以及嵌套文档。
+ $match：用于过滤数据，只输出符合条件的文档。$match使用MongoDB的标准查询操作。
+ $limit：用来限制MongoDB聚合管道返回的文档数。
+ $skip：在聚合管道中跳过指定数量的文档，并返回余下的文档。
+ $unwind：将文档中的某一个数组类型字段拆分成多条，每条包含数组中的一个值。
+ $group：将集合中的文档分组，可用于统计结果。
+ $sort：将输入文档排序后输出。
+ $geoNear：输出接近某一地理位置的有序文档。

管道操作符实例

1、$project实例

```c
db.article.aggregate(
    { $project : {
        title : 1 ,
        author : 1 ,
    }}
 );
```

这样的话结果中就只还有_id,tilte和author三个字段了，默认情况下_id字段是被包含的，如果要想不包含_id话可以这样:

```c
db.article.aggregate(
    { $project : {
        _id : 0 ,
        title : 1 ,
        author : 1
    }});
```

2、$match实例

```c
db.articles.aggregate( [
                        { $match : { score : { $gt : 70, $lte : 90 } } },
                        { $group: { _id: null, count: { $sum: 1 } } }
                       ] );
```

$match用于获取分数大于70且小于或等于90记录，然后将符合条件的记录送到下一阶段$group管道操作符进行处理。

3、$skip实例

```c
db.article.aggregate(
    { $skip : 5 });
```

经过$skip管道操作符处理后，前五个文档被"过滤"掉。

## MongoDB复制（副本集）

MongoDB复制是将数据同步在多个服务器的过程。  
复制提供了数据的冗余备份，并在多个服务器上存储数据副本，提高了数据的可用性， 并可以保证数据的安全性。  
复制还允许您从硬件故障和服务中断中恢复数据。


***什么是复制?***

+ 保障数据的安全性
+ 数据高可用性 (24*7)
+ 灾难恢复
+ 无需停机维护（如备份，重建索引，压缩）
+ 分布式读取数据

### MongoDB复制原理

mongodb的复制至少需要两个节点。其中一个是主节点，负责处理客户端请求，其余的都是从节点，负责复制主节点上的数据。  
mongodb各个节点常见的搭配方式为：一主一从、一主多从。  
主节点记录在其上的所有操作oplog，从节点定期轮询主节点获取这些操作，然后对自己的数据副本执行这些操作，从而保证从节点的数据与主节点一致。  
MongoDB复制结构图如下所示：

![mongodb复制原理.png](mongodb复制原理.png)

以上结构图中，客户端从主节点读取数据，在客户端写入数据到主节点时， 主节点与从节点进行数据交互保障数据的一致性。

副本集特征：

+ N个节点的集群
+ 任何节点可作为主节点
+ 所有写入操作都在主节点上
+ 自动故障转移
+ 自动恢复

### MongoDB副本集设置

在本教程中我们使用同一个MongoDB来做MongoDB主从的实验， 操作步骤如下：

1. 关闭正在运行的MongoDB服务器。

2. 我们通过指定 --replSet 选项来启动mongoDB。--replSet 基本语法格式如下：
```bash
mongod --port "PORT" --dbpath "YOUR_DB_DATA_PATH" --replSet "REPLICA_SET_INSTANCE_NAME"
```
> 实例  
> mongod --port 27017 --dbpath "D:\set up\mongodb\data" --replSet rs0  
> 以上实例会启动一个名为rs0的MongoDB实例，其端口号为27017。

3. 启动后打开命令提示框并连接上mongoDB服务。  
在Mongo客户端使用命令rs.initiate()来启动一个新的副本集。  
我们可以使用rs.conf()来查看副本集的配置  
查看副本集状态使用 rs.status() 命令

### 副本集添加成员

添加副本集的成员，我们需要使用多台服务器来启动mongo服务。进入Mongo客户端，并使用rs.add()方法来添加副本集的成员。

语法:  

```
rs.add(HOST_NAME:PORT)
```

实例:   
假设你已经启动了一个名为 mongod1.net ，端口号为27017的Mongo服务。 在客户端命令窗口使用rs.add() 命令将其添加到副本集中，命令如下所示：

```
rs.add("mongod1.net:27017")
```

MongoDB中你只能通过主节点将Mongo服务添加到副本集中， 判断当前运行的Mongo服务是否为主节点可以使用命令db.isMaster() 。  
MongoDB的副本集与我们常见的主从有所不同，主从在主机宕机后所有服务将停止，而副本集在主机宕机后，副本会接管主节点成为主节点，不会出现宕机的情况。

## MongoDB分片

### 分片

在Mongodb里面存在另一种集群，就是分片技术,可以满足MongoDB数据量大量增长的需求。  
当MongoDB存储海量的数据时，一台机器可能不足以存储数据，也可能不足以提供可接受的读写吞吐量。这时，我们就可以通过在多台机器上分割数据，使得数据库系统能存储和处理更多的数据。

### 为什么使用分片

+ 复制所有的写入操作到主节点
+ 延迟的敏感数据会在主节点查询
+ 单个副本集限制在12个节点
+ 当请求量巨大时会出现内存不足。
+ 本地磁盘不足
+ 垂直扩展价格昂贵

### MongoDB分片
下图展示了在MongoDB中使用分片集群结构分布：

![mongodb分片集群结构分布](mongodb分片集群结构分布.png)

上图中主要有如下所述三个主要组件：

Shard:  
用于存储实际的数据块，实际生产环境中一个shard server角色可由几台机器组个一个replica set承担，防止主机单点故障

Config Server:  
mongod实例，存储了整个 ClusterMetadata，其中包括 chunk信息。

Query Routers:  
前端路由，客户端由此接入，且让整个集群看上去像单一数据库，前端应用可以透明使用。

## MongoDB 备份(mongodump)与恢复(mongorestore)

### MongoDB数据备份

在Mongodb中我们使用mongodump命令来备份MongoDB数据。该命令可以导出所有数据到指定目录中。  
mongodump命令可以通过参数指定导出的数据量级转存的服务器。

语法：  

```
mongodump -h dbhost -d dbname -o dbdirectory
```

-h：  
MongoDB 所在服务器地址，例如：127.0.0.1，当然也可以指定端口号：127.0.0.1:27017

-d：  
需要备份的数据库实例，例如：test

-o：  
备份的数据存放位置，例如：c:\data\dump，当然该目录需要提前建立，在备份完成后，系统自动在dump目录下建立一个test目录，这个目录里面存放该数据库实例的备份数据。


mongodump 命令可选参数列表如下所示：  

| 语法 | 描述 | 实例 |
| :---- | :---- | :------ |
| mongodump --host HOST_NAME --port PORT_NUMBER | 该命令将备份所有MongoDB数据 | mongodump --host 127.0.0.1 --port 27017 |
| mongodump --dbpath DB_PATH --out BACKUP_DIRECTORY |  | mongodump --dbpath /data/db/ --out /data/backup/ |
| mongodump --collection COLLECTION --db DB_NAME | 该命令将备份指定数据库的集合。 | mongodump --collection mycol --db test |


### MongoDB数据恢复

mongodb使用 mongorestore 命令来恢复备份的数据。

语法:  

```
mongorestore -h <hostname><:port> -d dbname <path>
```

--host &lt;:port>, -h &lt;:port>：
MongoDB所在服务器地址，默认为： localhost:27017

--db , -d ：
需要恢复的数据库实例，例如：test，当然这个名称也可以和备份时候的不一样，比如test2

--drop：
恢复的时候，先删除当前数据，然后恢复备份的数据。就是说，恢复后，备份后添加修改的数据都会被删除，慎用哦！

&lt;path>：
mongorestore 最后的一个参数，设置备份数据所在位置，例如：c:\data\dump\test。

你不能同时指定 &lt;path> 和 --dir 选项，--dir也可以设置备份目录。

--dir：
指定备份的目录

你不能同时指定 &lt;path> 和 --dir 选项。


## MongoDB 监控

在你已经安装部署并允许MongoDB服务后，你必须要了解MongoDB的运行情况，并查看MongoDB的性能。这样在大流量得情况下可以很好的应对并保证MongoDB正常运作。

MongoDB中提供了mongostat 和 mongotop 两个命令来监控MongoDB的运行情况。

### mongostat 命令

mongostat是mongodb自带的状态检测工具，在命令行下使用。它会间隔固定时间获取mongodb的当前运行状态，并输出。如果你发现数据库突然变慢或者有其他问题的话，你第一手的操作就考虑采用mongostat来查看mongo的状态。

启动你的Mongod服务，进入到你安装的MongoDB目录下的bin目录， 然后输入mongostat命令

### mongotop 命令

mongotop也是mongodb下的一个内置工具，mongotop提供了一个方法，用来跟踪一个MongoDB的实例，查看哪些大量的时间花费在读取和写入数据。 mongotop提供每个集合的水平的统计数据。默认情况下，mongotop返回值的每一秒。

启动你的Mongod服务，进入到你安装的MongoDB目录下的bin目录， 然后输入mongotop命令


## MongoDB 关系

MongoDB 的关系表示多个文档之间在逻辑上的相互联系。  
文档间可以通过嵌入和引用来建立联系。  
MongoDB 中的关系可以是：

+ 1:1 (1对1)
+ 1: N (1对多)
+ N: 1 (多对1)
+ N: N (多对多)

接下来我们来考虑下用户与用户地址的关系。  
一个用户可以有多个地址，所以是一对多的关系。  
以下是 user 文档的简单结构：

```json
{
   "_id":ObjectId("52ffc33cd85242f436000001"),
   "name": "Tom Hanks",
   "contact": "987654321",
   "dob": "01-01-1991"
}
```

以下是 address 文档的简单结构：

```json
{
   "_id":ObjectId("52ffc4a5d85242602e000000"),
   "building": "22 A, Indiana Apt",
   "pincode": 123456,
   "city": "Los Angeles",
   "state": "California"
} 
```

### 嵌入式关系

使用嵌入式方法，我们可以把用户地址嵌入到用户的文档中：

```json
{
   "_id":ObjectId("52ffc33cd85242f436000001"),
   "contact": "987654321",
   "dob": "01-01-1991",
   "name": "Tom Benzamin",
   "address": [
      {
         "building": "22 A, Indiana Apt",
         "pincode": 123456,
         "city": "Los Angeles",
         "state": "California"
      },
      {
         "building": "170 A, Acropolis Apt",
         "pincode": 456789,
         "city": "Chicago",
         "state": "Illinois"
      }]
} 
```

以上数据保存在单一的文档中，可以比较容易的获取和维护数据。 你可以这样查询用户的地址：

>db.users.findOne({"name":"Tom Benzamin"},{"address":1})

这种数据结构的缺点是，如果用户和用户地址在不断增加，数据量不断变大，会影响读写性能。


### 引用式关系

引用式关系是设计数据库时经常用到的方法，这种方法把用户数据文档和用户地址数据文档分开，通过引用文档的 id 字段来建立关系。

```json
{
   "_id":ObjectId("52ffc33cd85242f436000001"),
   "contact": "987654321",
   "dob": "01-01-1991",
   "name": "Tom Benzamin",
   "address_ids": [
      ObjectId("52ffc4a5d85242602e000000"),
      ObjectId("52ffc4a5d85242602e000001")
   ]
}
```

以上实例中，用户文档的 address_ids 字段包含用户地址的对象id（ObjectId）数组。  
我们可以读取这些用户地址的对象id（ObjectId）来获取用户的详细地址信息。  
这种方法需要两次查询，第一次查询用户地址的对象id（ObjectId），第二次通过查询的id获取用户的详细地址信息。

```cpp
var result = db.users.findOne({"name":"Tom Benzamin"},{"address_ids":1})
var addresses = db.address.find({"_id":{"$in":result["address_ids"]}})
```

> 注意这一句中的 findOne 不能写成 find，因为 find 返回的数据类型是数组，findOne 返回的数据类型是对象。  
> 如果这一句使用了 find，那么下面一句应该改写为:  
> var addresses = db.address.find({"_id":{"$in":result[0]["address_ids"]}})

## MongoDB 数据库引用

在上一章节MongoDB关系中我们提到了MongoDB的引用来规范数据结构文档。

MongoDB 引用有两种：

+ 手动引用（Manual References）
+ DBRefs

考虑这样的一个场景，我们在不同的集合中 (address_home, address_office, address_mailing, 等)存储不同的地址（住址，办公室地址，邮件地址等）。  
这样，我们在调用不同地址时，也需要指定集合，一个文档从多个集合引用文档，我们应该使用 DBRefs。

### 使用 DBRefs

DBRef的形式：

```
{ $ref : , $id : , $db :  }
```

三个字段表示的意义为：

+ $ref：集合名称
+ $id：引用的id
+ $db: 数据库名称，可选参数

以下实例中用户数据文档使用了 DBRef, 字段 address：

```json
{
   "_id":ObjectId("53402597d852426020000002"),
   "address": {
   "$ref": "address_home",
   "$id": ObjectId("534009e4d852427820000002"),
   "$db": "testdb"},
   "contact": "987654321",
   "dob": "01-01-1991",
   "name": "Tom Benzamin"
}
```

address DBRef 字段指定了引用的地址文档是在 testdb 数据库下的 address_home 集合，id 为 534009e4d852427820000002。  
以下代码中，我们通过指定 $ref 参数（address_home 集合）来查找集合中指定id的用户地址信息：  

```cpp
var user = db.users.findOne({"name":"Tom Benzamin"})
var dbRef = user.address
db[dbRef.$ref].findOne({"_id":(dbRef.$id)})
```

> db[dbRef.$ref].findOne({"\_id":ObjectId(dbRef.$id)})

以上实例返回了 address_home 集合中的地址数据：

```json
{
   "_id" : ObjectId("534009e4d852427820000002"),
   "building" : "22 A, Indiana Apt",
   "pincode" : 123456,
   "city" : "Los Angeles",
   "state" : "California"
}
```

## MongoDB 覆盖索引查询

官方的MongoDB的文档中说明，覆盖查询是以下的查询：

+ 所有的查询字段是索引的一部分
+ 所有的查询返回字段在同一个索引中

由于所有出现在查询中的字段是索引的一部分， MongoDB 无需在整个数据文档中检索匹配查询条件和返回使用相同索引的查询结果。  
因为索引存在于RAM中，从索引中获取数据比通过扫描文档读取数据要快得多。

### 使用覆盖索引查询

为了测试覆盖索引查询，使用以下 users 集合:

```json
{
   "_id": ObjectId("53402597d852426020000002"),
   "contact": "987654321",
   "dob": "01-01-1991",
   "gender": "M",
   "name": "Tom Benzamin",
   "user_name": "tombenzamin"
}
```

我们在 users 集合中创建联合索引，字段为 gender 和 user_name :

```c
db.users.createIndex({gender:1,user_name:1})
```

现在，该索引会覆盖以下查询：

```c
db.users.find({gender:"M"},{user_name:1,_id:0})
```

也就是说，对于上述查询，MongoDB的不会去数据库文件中查找。相反，它会从索引中提取数据，这是非常快速的数据查询。  
由于我们的索引中不包括 \_id 字段，\_id在查询中会默认返回，我们可以在MongoDB的查询结果集中排除它。  
下面的实例没有排除_id，查询就不会被覆盖：

```c
db.users.find({gender:"M"},{user_name:1})
```

最后，如果是以下的查询，不能使用覆盖索引查询：

+ 所有索引字段是一个数组
+ 所有索引字段是一个子文档

## MongoDB 查询分析

MongoDB 查询分析可以确保我们所建立的索引是否有效，是查询语句性能分析的重要工具。   
MongoDB 查询分析常用函数有：explain() 和 hint()。

### explain()

explain 操作提供了查询信息，使用索引及查询统计等。有利于我们对索引的优化。  
接下来我们在 users 集合中创建 gender 和 user_name 的索引：

```c
db.users.ensureIndex({gender:1,user_name:1})
```

现在在查询语句中使用 explain ：

```c
db.users.find({gender:"M"},{user_name:1,_id:0}).explain()
```

以上的 explain() 查询返回如下结果：

```c
{
   "cursor" : "BtreeCursor gender_1_user_name_1",
   "isMultiKey" : false,
   "n" : 1,
   "nscannedObjects" : 0,
   "nscanned" : 1,
   "nscannedObjectsAllPlans" : 0,
   "nscannedAllPlans" : 1,
   "scanAndOrder" : false,
   "indexOnly" : true,
   "nYields" : 0,
   "nChunkSkips" : 0,
   "millis" : 0,
   "indexBounds" : {
      "gender" : [
         [
            "M",
            "M"
         ]
      ],
      "user_name" : [
         [
            {
               "$minElement" : 1
            },
            {
               "$maxElement" : 1
            }
         ]
      ]
   }
}
```

现在，我们看看这个结果集的字段：

+ indexOnly: 字段为 true ，表示我们使用了索引。
+ cursor：因为这个查询使用了索引，MongoDB 中索引存储在B树结构中，所以这是也使用了 BtreeCursor 类型的游标。如果没有使用索引，游标的类型是 BasicCursor。这个键还会给出你所使用的索引的名称，你通过这个名称可以查看当前数据库下的system.indexes集合（系统自动创建，由于存储索引信息，这个稍微会提到）来得到索引的详细信息。
+ n：当前查询返回的文档数量。
+ nscanned/nscannedObjects：表明当前这次查询一共扫描了集合中多少个文档，我们的目的是，让这个数值和返回文档的数量越接近越好。
+ millis：当前查询所需时间，毫秒数。
+ indexBounds：当前查询具体使用的索引。

### hint()

虽然MongoDB查询优化器一般工作的很不错，但是也可以使用 hint 来强制 MongoDB 使用一个指定的索引。  
这种方法某些情形下会提升性能。 一个有索引的 collection 并且执行一个多字段的查询(一些字段已经索引了)。  
如下查询实例指定了使用 gender 和 user_name 索引字段来查询：  

```c
db.users.find({gender:"M"},{user_name:1,_id:0}).hint({gender:1,user_name:1})
```

可以使用 explain() 函数来分析以上查询：

```c
db.users.find({gender:"M"},{user_name:1,_id:0}).hint({gender:1,user_name:1}).explain()
```

## MongoDB 原子操作

mongodb不支持事务，所以，在你的项目中应用时，要注意这点。无论什么设计，都不要要求mongodb保证数据的完整性。  
但是mongodb提供了许多原子操作，比如文档的保存，修改，删除等，都是原子操作。  
所谓原子操作就是要么这个文档保存到Mongodb，要么没有保存到Mongodb，不会出现查询到的文档没有保存完整的情况。

### 原子操作数据模型

考虑下面的例子，图书馆的书籍及结账信息。  
实例说明了在一个相同的文档中如何确保嵌入字段关联原子操作（update：更新）的字段是同步的。

```json
book = {
          _id: 123456789,
          title: "MongoDB: The Definitive Guide",
          author: [ "Kristina Chodorow", "Mike Dirolf" ],
          published_date: ISODate("2010-09-24"),
          pages: 216,
          language: "English",
          publisher_id: "oreilly",
          available: 3,
          checkout: [ { by: "joe", date: ISODate("2012-10-15") } ]
        }
```

你可以使用 db.collection.findAndModify() 方法来判断书籍是否可结算并更新新的结算信息。  
在同一个文档中嵌入的 available 和 checkout 字段来确保这些字段是同步更新的:


