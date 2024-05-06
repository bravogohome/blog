---
title: Android开发笔记
catalog: true
lang: cn
date: 2023-11-07 20:17:47
subtitle:
header-img: /img/header_img/nier.png
tags:
- Android
categories:
- Notes
sticky: 999
---

> 参考：
> [Android官方开发文档](https://developer.android.com/develop?hl=zh-cn)
> [维基百科](https://zh.wikipedia.org/wiki/)
> 《Android第一行代码（第三版）》-郭霖


## Android 简介

### Android 系统架构

> Android软件栈-来自Android文档<https://developer.android.com/guide/platform?hl=zh-cn>
> ![android软件栈图](The-Android-software-stack.png)
> Android系统架构图-来自geek<https://www.geeksforgeeks.org/android-architecture/?ref=lbp>
> ![android系统架构图](architecture.jpg)

#### Linux kernel（Linux内核层）

Android系统的基础是Linux内核，它提供了许多底层的**硬件驱动程序**（如wifi驱动、显示驱动、音频驱动、USB驱动、照相机驱动、蓝牙驱动等）和安全机制。

#### Hardware Abstraction Layer（HAL硬件抽象层）

硬件抽象层提供了一组标准接口，用于将设备硬件功能暴露给更高级别的Java API框架。HAL由多个库模块组成，每个模块实现特定类型硬件组件的接口，如相机或蓝牙模块。当框架API要求访问设备硬件时，Android系统将为该硬件组件加载库模块。

####  Platform libraries & Android Runtime（系统运行库层）

这一层通过一些原生C/C++库为Android系统提供了主要的特性支持。如上图中的OpenGL/ES库提供了3D绘图的支持，webkit提供浏览器内核的支持等。

对于运行 Android 5.0（API 级别 21）或更高版本的设备，每个应用都在其自己的进程中运行，并且有其自己的 Android Runtime (ART) 实例。ART 编写为通过执行 DEX 文件在低内存设备上运行多个虚拟机，DEX 文件是一种专为 Android 设计的字节码格式，经过优化，使用的内存很少。编译工具链（例如 Jack）将 Java 源代码编译为 DEX 字节码，使其可在 Android 平台上运行。

#### Application Framework（应用框架层）

这一层主要提供了构建应用程序时可能用到的各种API。

(Java API Framework)
Java API框架提供了大部分Java编程语言的功能，包括一些Java 8语言特性，用于支持Java应用程序的开发。

包括以下一些接口：
1. Activity Manager 活动管理器：它管理活动生命周期和活动堆栈。
2. 电话管理器：它提供对电话服务的访问，作为相关的用户信息，例如电话号码。
3. View System视图系统：它通过处理视图和布局来构建用户界面。
4. 位置管理器：它查找设备的地理位置。
5. 资源管理器：用于访问非代码资源，例如本地化的字符串、图形和布局文件。
6. 通知管理器：可让所有应用在状态栏中显示自定义提醒。
7. 内容提供程序：可让应用访问其他应用（例如“联系人”应用）中的数据或者共享其自己的数据。

#### System Apps（系统应用）

系统应用是Android系统的核心组件，包括电话、联系人、浏览器、短信等应用程序。

### Android 历史版本

Android操作系统有预发行的内部版本，分别为铁臂阿童木（Astro）与机器人班亭（Bender，电视动画《飞出个未来》的角色）。从2009年5月开始，Android的版本代号改以甜点来命名，且每个代号间的前缀以英文本母序接续排列：Cupcake（纸杯蛋糕）、Donut（甜甜圈）、Eclair（闪电泡芙）、Froyo（优格冰淇淋）、Gingerbread（姜饼）、Honeycomb（蜂巢）、Ice Cream Sandwich（冰淇淋三明治）、Jelly Bean（果冻豆）、KitKat（奇巧巧克力）、Lollipop（棒棒糖）、Marshmallow（棉花糖）、Nougat（牛轧糖）、Oreo（奥利奥）、Pie（派）。2019年8月23日，Google宣布从Android Q开始不再以甜品命名，且直接称Android Q为Android 10。

![Android版本历史](Android版本.png)

> [Android各个版本安全特性](https://blog.csdn.net/m0_38036918/article/details/124726889)


## 开发环境搭建

### IDE下载

Android studio 官网下载：<https://developer.android.google.cn/studio?hl=zh-cn>

IDE使用说明

### 模拟器下载

+ 真机测试
+ 雷电模拟器、Mumu模拟器
+ AVM/AVD

## Hello World

### 创建项目

### 运行

### 观察项目结构
