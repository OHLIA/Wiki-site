---
title: Windows 镜像文件大于 4G 的安装方法
date: 2018-03-16 21:53:24
tags: [Windows,Learn,教程]
categories: 教程
---



<!--more-->

当前 BIOS 比较通用的启动分区为 FAT32 格式，随着系统的迭代，导致系统实际映像文件 `/source/install.wim` 大于 4G，受限于 FAT32 磁盘格式，无法放入大于 4G 的文件，此时需要一些解决方法。

## 使用 Dism 命令对 WIM 映像文件进行分卷

Windows安装程序原生支持此法，故推荐。  

用管理员权限运行 CMD 或者 Power shell ，输入如下命令：

```
Dism /Split-Image /ImageFile:X:\source\install.wim /SWMFile:Y:\source\install.swm /FileSize:xxxx
```

- X:\source\install.wim表示来源路径和文件
- Y:\source\install.swm表示卷后的路径和文件，后缀名swm
- FileSize:xxxx，XXXX请替换成小于4096的数值，单位为MB，表示单个分卷文件大小，分卷完成后，即可把生成的文件拷贝至启动盘的 `\source`路径下。

## 其他方法

1. PXE 网络安装

2. 使用光驱安装

3. 在 Win PE 下安装，即制作 PE 维护盘，从 PE 里面加载镜像安装系统

4. 启动盘使用 NTFS 分区格式
   - 目前仅部分主板支持
   - 可用 Rufus 制作启动盘提高兼容性，原理是增加一个小分区，放入 NTFS 的驱动，达到启动目的，但仍有部分主板不支持

5. 自行对启动盘双分区：
   - 第一个分区为 NTFS 或者 ExFat 分区格式，并且解压放入 ISO 所有文件
   - 第二个分区为 Fat32 分区格式，放入启动所需文件：
     - BOOT文件夹，里面放入boot.sdi文件

     - EFI文件夹，ISO对应的所有文件

     - Source文件夹，放入 boot.wim 文件

       - ```
       /boot
       |--boot.sdi
       /EFI
       |--/boot
       |--/microsoft
       /source
       |--boot.wim
         ```

       

6. U盘量产成光驱模式