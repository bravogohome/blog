---
title: 半爬取-获取omofun app的视频资源
catalog: true
lang: cn
date: 2022-06-18 23:03:20
subtitle: Get Omofun Mp4
header-img: /img/header_img/nier.png
tags:
categories:
---

> 首先，非正常方法，其次，资源途径很多，这个方法只是让我乘乘凉。提供一种思路，很多第三方资源网站缓存都可以用下面的方法。  
> 方法基于以前爬取视频的经验，但是最近懒得找资源站和写代码。orz  
> 悄悄地，打枪的不要。

## 准备工具

+ 雷电模拟器 - PC
+ omofun安装包/其他第三方资源软件（次元站？ - apk
+ libchecker - apk
+ 夸克浏览器 - 手机
+ 文本编辑器（vscode、notepad++、其实记事本也可以） - PC

## 开始

1. **安装雷电模拟器，并在模拟器内安装omofun或其他资源软件以及libchecker**

> omofun官网： <https://omofun.tv/>  
> libchecker GitHub ： <https://github.com/zhaobozhen/LibChecker>  

或者你可以直接访问以下链接获取apk: 

[omofun](https://bravogohome-my.sharepoint.com/:u:/g/personal/lgh1598_bravogohome_onmicrosoft_com/EdKhMWV3gAtEn8mVp3Cy61YB0yRlJDhH23r8gGtuh536Cw?e=sV5FOr)  
[libchecker](https://bravogohome-my.sharepoint.com/:u:/g/personal/lgh1598_bravogohome_onmicrosoft_com/Eas_ob516mtOpo5PJItiSB0BZd6YGSQ_f2XiJKq3d4jrsQ?e=nyD7sS)


![雷电模拟器](leidian.png)


2. **进入omofun，找到你要的资源（不一定有），然后缓存**

![示例下载1](omofun1.png)
![示例下载2](omofun2.png)
![示例下载3](omofun3.png)
![示例下载4](omofun4.png)

3. **接着打开libchecker，查看omofun或者你的第三方资源软件的包名**

![libchecker](libchecker.png)

> 这里提供的是一个泛解/思路，只想应用于omofun请直接跳转到第四步。  

这个`com.dogal.kenhuangzhe.geh.omofun`就是应用包名。

4. **然后打开雷电模拟器系统应用的文件管理器**

![文件管理器](filemanager.png)

因为模拟器是直接基于Linux内核制作的，所以一般都可以以超级管理员进行文件操作，这个在手机上无法访问根目录是选择模拟器的原因，且部分资源软件缓存不在可显示存储中。

废话不多说，我们依次进入以下路径：  

```py
/ -> 
/data/ -> 
/data/data/ -> 
/data/data/com.dogal.kenhuangzhe.geh.omofun/   # 这个文件夹就是第三步你获取的包名
# 接下来的根据不同的应用，路径不同，找一下就好了
/data/data/com.dogal.kenhuangzhe.geh.omofun/databases/
/data/data/com.dogal.kenhuangzhe.geh.omofun/databases/video_download/
```

在这个文件夹下，就是你缓存的视频了。  

> 为什么要这么麻烦呢？还不是这个app它不把缓存视频放在我可轻松取到的地方，要访问这个路径，除了root(对手机不好吧是吧)工具以及adb工具，我觉得使用模拟器是一个比较好的选择，而且可以更直观的查看和修改文件。

![缓存视频-文件管理](filemanager2.png)


这里有两个文件夹对应着两刚刚你缓存的两个视频。  

然后打开雷电模拟器的文件共享：  

![雷电模拟器-文件共享](filemanager3.png)
![文件共享](share.png)

这里可以修改文件共享到你电脑的路径，以及模拟器对应路径（默认为/sdcard/Picture/，好像是不可以修改）。
第一次修改需要重启模拟器，重启后重新进入这个路径就好了。  

接着我们选定两个文件夹和下面同名的空白文件：  

![文件共享2](share2.png)

然后依次进入：  

```
/sdcard/Pictures/
```

来到我们的共享文件夹，并把刚刚的文件移动过来。

![文件共享3](share3.png)

之后打开刚刚你设置的在电脑共享文件夹，可以看到已经能在电脑上操作了：  

![文件共享4](share4.png)

5. **新建文件夹，改名，良好的命名是必要的**

并把刚刚弄过来的文件夹和对应名字的文件移进去（因为我移了两个，不知道哪个是哪集，但是问题不大，后面都能改）  

![文件共享5](share5.png)

6. **我们用文本编辑工具（记事本等）打开那个“空白”文件**

![准备转换1](translate.png)

不用惊慌，打开记事本的替换：  

![准备转换2](translate2.png)
![准备转换3](translate3.png)

```py
# 将 /data/user/0/com.dogal.kenhuangzhe.geh.omofun/databases/video_download/ 
# 替换成 ./
```

然后`Ctrl+S`保存后退出!!!

可以重新打开看一下是否替换成功。

![准备转换4](translate4.png)

然后我们将这个文件添加后缀为`.m3u8`

![准备转换5](translate5.png)

到此准备工作就结束了。

7. 我们把这个大文件夹（品酒要在成为夫妻后1）拷贝到手机，并打开手机的文件管理器

![准备转换6](translate6.png)

然后打开夸克

![转换1](tomp4_1.png)
![转换2](tomp4_2.png)
![转换3](tomp4_3.png)
![转换4](tomp4_4.png)
![转换5](tomp4_5.png)
![转换6](tomp4_6.png)

这样就完成啦！！

然后配合[one drive 25T云盘](/cn/Microsoft-E5/)就可以实现自己的资源库（偷来的）辣。