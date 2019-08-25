---
title: Ubuntu 16.04 设置 root 账号登录
date: 2018-04-02 19:30:49
tags: [Ubuntu,root,教程]
categories: Linux
---

<!--more-->

1. 设置root密码
2. 更改配置文件

```bash
##STEP1
##setting root password:
$ sudo passwd root

##STEP2
##Edit
$ sudo gedit /etc/lightdm/lightdm.conf
############
[Seat:*]
autologin-user=root
############

##STEP3
##If Prompt Error found
$ gedit /root/.profile
############
#用#注释mesg n
#添加
tty -s && mesg n # change’mesg n’ to‘tty –s && mesg n’
############

##STEP4
##If Audio no function
$ gedit /root/.profile
############
#添加
pulseaudio --start --log-target=syslog
############
```

