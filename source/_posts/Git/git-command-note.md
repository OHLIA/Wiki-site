---
title: Git 命令记录
date: 2019-08-22 23:39:50
tags: [Note,Github,Git]
category: [Git,Github]
---

## 基本用法

下载 Github 项目

```bash
git clone <Github-repository-URL>
```



## 分支

查看远程分支

```
git branch -a
```

查看本地分支

```
git branch
```

添加新分支

```
git checkout -b <branch-name>
```

切换分支

```
#切换本地分支
git checkout <branch-name>

#切换远程分支，切换远程的 new 分支到本地，本地分支名称叫  new
git checkout -b new origin/new
```



## 版本

还原至某个版本

```bash
git reset --hard <commit-number>
#版本 commit 号可用 git log 命令查看。
#不加 commit 号，默认还原至上一个版本。
```



## 技巧

### 单独删除某个文件的所有历史记录

1. 删除相应文件或者文件夹
   - **执行前请先备份相应的文件或者文件夹。**
   - `PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA` 更改为要删除的文件或文件夹。
   - 此处删除文件夹，故需要在前面添加 `-r` 参数。

   ```bash
   $ git filter-branch --force --index-filter \
     "git rm --cached --ignore-unmatch -r PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA" \
     --prune-empty --tag-name-filter cat -- --all
     > Rewrite 48dc599c80e20527ed902928085e7861e6b3cbe6 (266/266)
     > Ref 'refs/heads/master' was rewritten
   ```

   

2. 本地记录覆盖到 Github 仓库（所有 Branch 以及 tags）。

   ```bash
   $ git push origin --force --all
   > Counting objects: 1074, done.
   > Delta compression using 2 threads.
   > Compressing objects: 100% (677/677), done.
   > Writing objects: 100% (1058/1058), 148.85 KiB, done.
   > Total 1058 (delta 590), reused 602 (delta 378)
   > To https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
   >  + 48dc599...051452f master -> master (forced update)
   ```
   ```bash
   $ git push origin --force --tags
   > Counting objects: 321, done.
   > Delta compression using up to 8 threads.
   > Compressing objects: 100% (166/166), done.
   > Writing objects: 100% (321/321), 331.74 KiB | 0 bytes/s, done.
   > Total 321 (delta 124), reused 269 (delta 108)
   > To https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
   >  + 48dc599...051452f master -> master (forced update)
   ```


3. 确认远程仓库所有相关记录清除后，强制解除对本地存储库中的所有对象的引用和垃圾收集。

   ```bash
   $ git for-each-ref --format="delete %(refname)" refs/original | git update-ref --stdin
   $ git reflog expire --expire=now --all
   $ git gc --prune=now
   > Counting objects: 2437, done.
   > Delta compression using up to 4 threads.
   > Compressing objects: 100% (1378/1378), done.
   > Writing objects: 100% (2437/2437), done.
   > Total 2437 (delta 1461), reused 1802 (delta 1048)
   ```




### 删除 Git 服务器文件但是保留本地文件

1. `.gitignore` 添加要过滤的文件和文件夹

2. 执行命令

   ```bash
   git rm -r --cached .
   git add .
   git commit
   git push  -u origin <branch-name>
   ```



## 参考

[git命令总结记录](https://blog.csdn.net/qq_26710805/article/details/80674006)

[删除Git服务器文件但是保留本地文件](https://www.cnblogs.com/kaerxifa/p/10973731.html)

[Github: 单独删除某个文件的所有历史记录](https://blog.csdn.net/q258523454/article/details/83899911)

[Removing sensitive data from a repository](https://help.github.com/en/articles/removing-sensitive-data-from-a-repository)