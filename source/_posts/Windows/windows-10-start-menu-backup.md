---
title: 备份恢复 Windows 10 开始菜单
date: 2018-05-01 18:30:49
tags: [Windows,开始菜单,备份,恢复]
---

<!--more-->

1. WIN+R, 输入 `powershell`，运行 Powershell 。
2. 备份到指定目录

```powershell
Export-startlayout –path d:\documents\start\start.xml
```
3. 导入指定的备份文件

```powershell
import-startlayout -layoutpath d:\documents\start\start.xml -mountpath c:
```

