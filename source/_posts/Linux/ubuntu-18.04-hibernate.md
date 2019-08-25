---
title: Ubuntu 18.04 开启 S4 休眠功能
date: 2018-06-23 19:00:49
tags: [Ubuntu,ACPI,Hibernate,教程]
categories: Linux
---

<!--more-->


1. 获取参数
2. 修改配置文件

```bash
#使用root权限

##step1
$ cat /sys/power/state
#确认返回值有 disk

##step2
$ grep swap /etc/fstab
$ grep UUID /etc/fstab
#记录 UUID，如 UUID=0b3e8d9b-a63e-4bdd-8f47-8a9a764fe7ed

##step3
$ filefrag -v /swapfile
#记录内存值
#如下记录中的 ext:0 length:34816
###############################
ext:     logical_offset:        physical_offset: length:   expected: flags:
   0:        0..   32767:      34816..     67583:  32768:            
   1:    32768..   63487:      67584..     98303:  30720:            
   2:    63488..   96255:     100352..    133119:  32768:      98304:
   3:    96256..  126975:     133120..    163839:  30720:   
###############################

##step4
$ gedit /etc/default/grub
#编辑 grub,填入记录的 UUID 和 length 数值：
###############################
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=09e601cd-5bac-491a-9115-fda1b2eb4664 resume_offset=34816"
###############################

##step5
$ update-grub

##step6
$ reboot

##step7
$ rtcwake -m disk -s 60 #进入S4，60秒后自启
$ systemctl hibernate #直接进入S4

###form https://askubuntu.com/questions/1053134/hibernation-in-18-04#1053227
```

