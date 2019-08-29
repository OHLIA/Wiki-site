---
title: Install Driver on Windows
toc: true
date: 2019-08-29 11:38:23
tags: [Windows,Driver]
categories: [Windows]
---



<!--more-->

## 双击可执行文件

## CMD 下静默安装

在 Windows CMD 通过类似 `setup.exe -s` 命令在后台安装，具体查看相关驱动的文档。

## Windows update

   1. Windows update 推送，比如 Graphic Driver；

   2. 点击 自动搜索更新的驱动程序软件 ；

      ![](Install-Driver-on-Windows/update-driver-online.jpg)

      ![1567057527757](Install-Driver-on-Windows/1567057527757.png)

## 通过 `.inf`[^1] 文件安装

   1. 右键点选安装;   
      以 PASSMARK USB 3.0 Loopback 为例：
      
      ![](Install-Driver-on-Windows/inf-install.png)

   2. 手动添加安装;  
      以并口打印机为例：
      
      ![](Install-Driver-on-Windows/Snipaste_2019-08-29_13-25-40.jpg)
      
      ![](Install-Driver-on-Windows/Snipaste_2019-08-29_13-28-45.jpg)
      
      ![](Install-Driver-on-Windows/Snipaste_2019-08-29_13-29-42.jpg)
      
      ![](Install-Driver-on-Windows/Snipaste_2019-08-29_13-30-19.jpg)
      
      ![](Install-Driver-on-Windows/Snipaste_2019-08-29_13-32-39.jpg)
      
      ![](Install-Driver-on-Windows/Snipaste_2019-08-29_13-35-25.jpg)
      
      ![](Install-Driver-on-Windows/Snipaste_2019-08-29_13-35-49.jpg)
      
      ![1567056987814](Install-Driver-on-Windows/1567056987814.png)
      
      ![1567057029976](Install-Driver-on-Windows/1567057029976.png)
      
      ![1567057103778](Install-Driver-on-Windows/1567057103778.png)
      
      ![](Install-Driver-on-Windows/Snipaste_2019-08-29_13-39-10.jpg)





## 参考资料

[^1]: INF是Device INFormation File的英文缩写，是Microsoft公司为硬件设备制造商发布其驱动程序推出的一种文件格式，INF文件中包含硬件设备的信息或脚本以控制硬件操作。在INF文件中指明了硬件驱动该如何安装到系统中，源文件在哪里、安装到哪一个文件夹中、怎样在注册表中加入自身相关信息等等。

