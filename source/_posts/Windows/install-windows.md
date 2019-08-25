---
title: 安装 Windows 系统
date: 2018-03-15 22:01:13
tags: [教程,Windows,系统]
categories: Windows
---

## 下载系统镜像  
- 从 [MSDN, I tell you](https://msdn.itellyou.cn/) 下载需要的 ISO 文件，下载后比对 hash 值，确保无篡改。
- 启动盘工具 Rufus 同样提供下载镜像功能。

## 制作启动盘

> 现今主流为 UEFI mode 启动，比较旧的主板可能只支持 Legacy mode 启动，
> 从EFI Firmware 2.5 开始只支持UEFI，彻底抛弃 Legacy（并不绝对，看厂商和客户需求）。

一般启动盘都是格式化成 FAT32，不能存储单个大于 4G 的文件，需要其它方法解决。

- Legacy mode
  - Windows CMD 创建。
  - [软碟通](https://cn.ultraiso.net/)往 U 盘或者移动硬盘写入镜像来制作可启动设备，非免费软件。
  - [Rufus](https://rufus.akeo.ie/)，开源免费的多功能启动盘制作工具，推荐。
  - [Bootice](http://www.ipauly.com/2015/11/15/bootice/)，如果不想格式化移动存储设备，可以使用此软件写入 主引导记录，分区引导记录，然后把镜像文件全部解压到U盘或者移动硬盘。
- UEFI mode
  - 把镜像文件**直接全部解压**到U盘或者移动硬盘第一分区**根目录**即可，并不需要第三方工具。

## 安装

1. 开机按快捷键（看厂商定义）进入BIOS（实际现在都是 UEFI firmware ）

2. 点选`自定义`，全新安装

3. 硬盘分区，如果是全新硬盘，点选新建，程序会自动建立 4 个分区

4. 选择第四个分区安装系统

5. 安装完成后，设置用户名和密码



## 激活

合法途径：

- 官网购买授权。
- 从 Windows7/8/8.1 升级。

非法途径：

- 数字权利激活

- VOL，即零售版可以使用 KMS 激活。
  - 可用 KMSpico 软件本地激活

  - 也可网络KMS服务器激活，如 https://03k.org/kms.html ，
    直接两条命令无脑激活即可

  ```bash
  #用管理员权限运行CMD或者Power shell
  slmgr /skms kms.03k.org
  slmgr /ato
  ```

## 安装驱动

- Windows10 update 会联网下载更新一些驱动，比如：CPU 核显驱动
- 如果是品牌机，请务必到官网下载驱动
- 如果是组装机，可能需要驱动助手类软件，不推荐国产的各种驱动人生/精灵等，避免被捆绑安装，推荐使用 [Driver Booster 5](https://www.iobit.com/en/driver-booster.php) ，免费版足够使用。
  - 该软件公司疑似中国公司。  



