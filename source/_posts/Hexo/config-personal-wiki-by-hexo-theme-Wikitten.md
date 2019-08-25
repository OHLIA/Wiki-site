---
title: 通过 hexo-theme-Wikitten 配置个人 Wiki
date: 2019-08-23 17:59:44
tags: [Hexo,Wiki,Note]
category: [Hexo,Theme,Wiki]
---



<!--more-->

## 安装说明

### 安装

**注意：本主题需要 Hexo v3.6 及以上版本。**

1. 进入你的 hexo 站点文件夹，克隆 `Wikitten` 主题到 `themes/` 路径下

```
$ cd your-hexo-directory
$ git clone https://github.com/zthxxx/hexo-theme-Wikitten.git themes/Wikitten
```

2. 覆盖站点目录中一些默认页面模板

```
$ cp -rf themes/Wikitten/_source/* source/
$ cp -rf themes/Wikitten/_scaffolds/* scaffolds/
```

3. 重命名主题中的 `_config.yml.example` 到 `_config.yml`，然后可以使用配置文件配置主题

```
$ cp -f themes/Wikitten/_config.yml.example themes/Wikitten/_config.yml
# 编辑配置文件，定制你的配置项
$ vim themes/Wikitten/_config.yml
```

大部分的配置项都和 [icarus](https://github.com/ppoffice/hexo-theme-icarus) 主题中的配置项一样，你可以首先去阅读一下 [icraus 的文档](https://github.com/ppoffice/hexo-theme-icarus/wiki)。

一些你可以开箱即用的推荐配置见下面的文档：[#Configuration](https://github.com/zthxxx/hexo-theme-Wikitten/blob/master/README_zh-CN.md#Configuration)

4. 需要安装的插件写在主题的 [`package.json`](https://github.com/zthxxx/hexo-theme-Wikitten/blob/master/package.json) 文件中

这里列出了这些插件的功能作用：

```
hexo-autonofollow	    // 打开非本站链接时自动开启新标签页
hexo-directory-category // 根据文章文件目录自动为文章添加分类
hexo-generator-feed	    // 生成 RSS 源
hexo-generator-json-content	// 生成全站文章 json 内容，用于全文搜索
hexo-generator-sitemap	// 生成全站站点地图 sitemap
```

你可以将这些插件合并到**站点**的 `package.json` 文件中通过 `npm install` 一次安装，

或者在**站点目录**下，你可以通过以下命令安装他们：

```
$ npm i -S hexo-autonofollow hexo-directory-category hexo-generator-feed hexo-generator-json-content hexo-generator-sitemap
```

5. 配置mathjax渲染（可选）：

如果你在博客中需要撰写数学公式，推荐进行以下配置：

首先安装[pandoc](https://pandoc.org/installing.html)，同时在hexo站点下修改渲染引擎：

```
$ npm un hexo-renderer-marked --save
$ npm i hexo-rendere-pandoc --save # or hexo-renderer-krammed
```

然后将以下配置加到站点`_config.yml`文件中：

```
math:
  enable: true
  engine: mathjax
```

### 启用

修改站点 `_config.yml` 文件中的 `theme` 选项为 **Wikitten**。

### 更新

```
$ cd themes/Wikitten
$ git pull origin master
```

## 配置说明

### 站点配置

在站点配置文件 `_config.yml` 中， **开箱即用配置为**：

- 复制并修改 `<>` 标记的内容即可。

```yaml
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: <title>
subtitle:
description:
keywords:
author: <author>
language: en
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com
root: /
permalink: wiki/:title/
permalink_defaults:

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:
  - README.md
  - '_posts/**/embed_page/**'

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
  
## Markdown
## https://github.com/hexojs/hexo-renderer-marked
marked:
  gfm: true

## Plugins: https://hexo.io/plugins/
### JsonContent
jsonContent:
  meta: false
  pages:
    title: true
    date: true
    path: true
    text: true
  posts:
    title: true
    date: true
    path: true
    text: true
    tags: true
    categories: true
  ignore:
    - 404.html
    
### Creat sitemap
sitemap:
  path: sitemap.xml

### Adds nofollow attribute to all external links in your hexo blog posts automatically.
nofollow:
  enable: true
  exclude:
    - <your site url domain> # eg: zthxxx.me  

## https://github.com/zthxxx/hexo-directory-category	
auto_dir_categorize:
  enable: true  # options:true, false; default is true
  force: true # options:true, false; default is false
 
# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date
  
# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: wikitten

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type:
```



### 主题配置

在**主题**配置文件 `Wikitten/_config.yml` 中，你能阅读到各个选项更多的细节配置。

**在开始之前，首先请将主题配置文件示例中「我」的信息修改为「你」自己的信息，其中包括 profile social_links history_control等配置项。**

 `profile`、`comment`、`Share` 和 `miscellaneous` 项都是 **默认关闭的**！

（你任然可以打开那些选项，只是不推荐这样做。）

 **开箱即用推荐设置为**：

- 只需修改用 `<>` 标记的内容。

```yaml
# Menus
menu:
  首页: /
  归档: /archives
  分类: /categories
  标签: /tags
  关于: /about

# Customize
customize:
    logo:
        enabled: true
        width: 40
        height: 40
        url: /logo.png
    profile:
        enabled: false # Whether to show profile bar
        avatar: # css/images/avatar.png
        gravatar: zth_9451@qq.com # Gravatar email address, if you enable Gravatar, your avatar config will be overriden
        author: <author>
        author_title: <Designer & Programmer>
        location: <Chengdu, China>
        follow: <https://github.com/username/>
    highlight: monokai
    sidebar: left # sidebar position, options: left, right
    category_perExpand: false # enable article categories list per expanding
    thumbnail: true # enable posts thumbnail, options: true, false
    favicon: /favicon.ico # path to favicon
    default_index_file: index.md # if this, it will display at site index instead of default index page
    social_links:
        github: <https://github.com/username/username.github.io>
        #stack-overflow: <http://stackoverflow.com/users/7277090/zthxxx?tab=profile>
        #codepen: http://codepen.io/zthxxx/
        rss: /atom.xml
    social_link_tooltip: true # enable the social link tooltip, options: true, false

# Widgets
widgets: # default use category only
    - category
    # - recent_posts
    # - archive
    # - tag
    # - tagcloud
    # - links
    
# Excerpt 
## Auto creat excerpt with not <!--more-->
## Enable will truncate auto_excerpt.lines rows in post head to replace excerpt.
auto_excerpt:
    enable: true
    lines: 5

# Search
search:
    insight: true # you need to install `hexo-generator-json-content` before using Insight Search
    swiftype: # enter swiftype install key here
    baidu: false # you need to disable other search engines to use Baidu search, options: true, false

# History version 
history_control: # make you wiki has history version control in page
    enable: true #启用这一项使得 wiki 能有历史版本的功能（查看源码、在线编辑、对比历史变动）
    server_link: https://github.com # recommend use GitHub https://github.com
    user: <your GitHub name>
    repertory: <your repertory name of this wiki source code>
    branch: <branch name of this wiki site source code>

# Comment
comment:
    disqus: # enter disqus shortname here
    duoshuo: # enter duoshuo shortname here
    youyan: # enter youyan uid here

# Share
share: default # options: jiathis, bdshare, addtoany, default

# Plugins
plugins:
    lightgallery: true # options: true, false
    justifiedgallery: true # options: true, false
    mathjax: true # options: true, false - to enable use Mathjax in your article
    google_analytics: # enter the tracking ID for your Google Analytics
    google_site_verification: # enter Google site verification code
    baidu_analytics: # enter Baidu Analytics hash key
    busuanzi_count: true # options: true, false - to enable busuanzi site pv statistics

# Miscellaneous
miscellaneous:
    open_graph: # see http://ogp.me
        fb_app_id:
        fb_admins:
        twitter_id:
        google_plus:
    links:
```

## 参考

[hexo-theme-Wikitten 中文文档](https://github.com/zthxxx/hexo-theme-Wikitten/blob/master/README_zh-CN.md#Configuration)