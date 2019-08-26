---
title: 通过 CMD 制作 Windows Legacy 启动设备
toc: true
date: 2019-08-26 23:37:02
tags: [Windows,Boot]
categories: [Windows]
---



<!--more-->

1. 创建主分区，激活主分区，使之可启动。

```bash
diskpart
list disk #列出所有存储设备
select disk x #选择设备 x
clean #清除该设备所有磁盘信息
convert mbr #转换为 mbr 磁盘格式
create partition primary size=4096 #创建主分区.分区大小4096M,如不加此参数则使用全盘空间.
list partition
select partition 1
active #激活主分区
format quick fs=fat32 #快速格式化当前分区,确认格式化为FAT32.
```

2. 解压复制 Windows ISO 所有文件到存储设备的根目录。