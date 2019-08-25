---
title: Ubuntu 18.04 开启 root 账户登录
date: 2018-06-16 19:00:49
tags: [Ubuntu,root,教程]
categories: Linux
---

<!--more-->

1. 设置root密码
2. 更改配置文件

```bash
##step1
#设置root密码
$ sudo passwd root

##step2
#更改权限
$ sudo chmod 777 /etc/pam.d/gdm-autologin
$ sudo chmod 777 /etc/pam.d/gdm-password
#开启root自动输入密码登陆
#注释对应语句,文件第三行
$ gedit /etc/pam.d/gdm-autologin
----------------
#auth require pam_succeed_if.so user !=root quiet_success
----------------
$ gedit /etc/pam.d/gdm-password
----------------
#auth required pam_succeed_if.so user !=root quiet_success
----------------
#更改权限
$ sudo chmod 644 /etc/pam.d/gdm-autologin
$ sudo chmod 644 /etc/pam.d/gdm-password

##step3
#设置自动登陆功能,修改对应语句
$ sudo chmod 777 /etc/gdm3/custom.conf
$ gedit /etc/gdm3/constom.conf
-----------------------
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=root
-----------------------

##step4
#重启，查看是否成功

##step5
#提示错误：Prompt Error found:
$ gedit /root/.profile
#用#注释mesg n这句
#尾行添加
------------------------------------------------------
tty -s && mesg n # change’mesg n’ to‘tty –s && mesg n’
------------------------------------------------------

##step6
##出现提示错误：Audio no function
$ gedit /root/.profile
#############
#添加
pulseaudio --start --log-target=syslog
#############
```

