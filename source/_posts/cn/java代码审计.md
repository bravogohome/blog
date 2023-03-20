---
title: java代码审计
catalog: true
lang: cn
date: 2022-09-22 14:36:05
subtitle:
header-img: /img/header_img/nier.png
tags:
- java
categories:
- Note
sticky: 996
---

## java基础


`JDK(Java Development Kit)`是针对java开发员的产品(SDK)，是整个java的核心。开发工具位于bin子目录中，指工具和实用程序，可帮助开发、执行、调试以java编程语言编写的程序，例如编译器javac.exe和解释器java.exe都位于该目录中;java运行环境包括java虚拟机、类库以及其他支持执行以java编程语言编写的程序的文件。
附加库位于lib子目录中，开发工具所需的其他类库和支持文件C头文件源代码

`JRE (Java Runtime Environment)`是运行java程序所必须的环境集合，包含JVM标准、及java核心类库。

`JVM(Java Virtual Machine)` java虚拟机是整个实现跨平台的最核心部分，能够运行以java语言编写的软件程序。

Java SE(java Platform, Standard Edition)这是标准版，基础版本。允许开发和部署在桌面、服务器、嵌入式环境和实时环境中使用的Java应用程序。Java SE包含了支持Java Web服务开发的类。通常用来开发java的桌面软件;

Java EE(Java Platform,Enterprise Edition): JavaEE是在Java SE的基础上构建的，他提供Web服务、组件模型、管理、通信API,用来实现企业级的面向服务体系结构和web2.0应用程序;

Java ME(Java Platform, Micro Edition):为在移动设备和嵌入式设备(比如手机、PDA、电视机顶盒和打印机)上运行的运用程序提供一个健壮且灵活的环境;

常见的Java服务器:Tomcat 、Weblogic、Jetty、JBoss、GlassFish等;

## 反射

反射可以用于判断任意对象所属的类，获得Class对象，构造任意一个对象以及调用一个对象。


