---
title: 通过 Project pages 搭建个人的 Wiki 和 Blog
toc: true
date: 2019-08-25 23:11:33
tags: [Github,Html,Hexo,Wiki]
categories: [Github,Hexo,Wiki]
---



<!--more-->

## Github pages 的分类

当前 Github pages 可以创建以下两种站点：

- User and Organization pages sites（个人和组织页面站点）
- Project pages sites（项目页面站点）

### 个人和组织页面站点

 Hexo 站点通常用到这种 Github pages 。

网页文件需要放到项目的 `master` 分支。

访问站点链接：
`http(s)://<username>.github.io`

`http(s)://<orgname>.github.io`

### 项目页面站点

网页文件需要放到项目的特定分支或者路径：

- master 分支
- gh-pages 分支
- master 分支的 docs 目录下

站点链接：
`http(s)://<username>.github.io/<projectname>`
`http(s)://<orgname>.github.io/<projectname>`

## 搭建个人 Blog + Wiki 站点

当前自己的方式是，个人页面站点使用 Next 主题写博客，项目页面站点使用 [Wikitten](https://github.com/zthxxx/hexo-theme-Wikitten) 主题写 Wiki 。

### 创建项目

- 创建 `<username>.github.io` 项目，设置 `hexo` 分支为默认分支用以存放 `Next` 主题的 hexo 配置文件，设置 master 分支存放 Next 主题的 Hexo 站点内容。

- 创建 `Wiki-site` 项目，设置 `writing` 分支为默认分支用以存放 `Wikitten` 主题的 Hexo 站点的配置文件，设置 `gh-pages` 分支存放 `Wikitten` 主题的 Hexo 站点内容

### 站点配置

#### Wikitten 站点

为了正确访问站点内容，需修改 Wikitten 主题 Hexo 站点配置文件 _config.yml :

```yaml
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://<username>.github.io/Wiki-site
root: /Wiki-site
permalink: wiki/:title/
permalink_defaults:
```

在顶栏菜单添加链接跳转回博客页面，需修改 Wikitten 主题的配置文件 _config.yml ：

```yaml
# Menus
menu:
  首页: /
  归档: /archives
  分类: /categories
  标签: /tags
  关于: /about
  Blog: https://<username>.github.io
```

#### Next 站点

在顶栏菜单添加链接跳转至 Wiki 页面，需修改 Next 主题的配置文件 _config.yml ：

```yaml
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive
  schedule: /schedule/ || calendar
  sitemap: /sitemap.xml || sitemap
  commonweal: /404/ || heartbeat
  WIKI: /Wiki-site/ || wikipedia-w
```



以上完成后，其余步骤参考搭建 Hexo 站点相关教程即可。



## 参考资料

> - [User, Organization, and Project Pages](https://help.github.com/en/articles/user-organization-and-project-pages)
