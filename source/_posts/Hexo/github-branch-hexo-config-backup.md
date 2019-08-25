---
title: Github 分支备份 Hexo 配置
date: 2019-08-22 08:33:35
tags: [Hexo,Blog,Github,branch]
categories: Hexo
---



<!--more-->

## 创建 Github 仓库

创建仓库 `Your-username.github.io` 。

创建分支 `Hexo` ，此分支用于存放配置文件。

设置默认分支为 `Hexo` 。

Github pages 需把网页文件放到 `master` 分支。

## 本地设置

进入本地 Hexo 文件夹，绑定远程仓库

```bash
git remote add origin git@github.com:Your-username.github.io.git 
```

如果提示错误，则手动生成 .git 文件夹

```bash
git init
```
编辑`.gitignore`文件，设置不上传的文件和文件夹。

```bash
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

## 推送

推送文件到 Github 远程仓库


```bash
git add .

git commit -m “hexo source post”

git push origin hexo
```

之后运行上面的命令行即可上传 Hexo 相关配置文件到 Github 仓库的默认 Hexo 分支，而 Hexo 生成的网页文件通过 `hexo deploy` 上传到 master 分支。