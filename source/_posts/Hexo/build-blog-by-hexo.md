---
title: 使用 Hexo 搭建博客
date: 2018-03-04 11:58:16
tags: [Hexo,Blog,Note]
categories: [Hexo,Blog]
---

# 使用Hexo搭建博客

[TOC]

## 安装

### GIT

- Windows：下载并安装 [git](https://git-scm.com/download/win).
- Mac：使用 [Homebrew](http://mxcl.github.com/homebrew/), [MacPorts](http://www.macports.org/) ：`brew install git`;或下载 [安装程序](http://sourceforge.net/projects/git-osx-installer/) 安装。
- Linux (Ubuntu, Debian)：`sudo apt-get install git-core`
- Linux (Fedora, Red Hat, CentOS)：`sudo yum install git-core`
- Linux (Arch 系列)：`sudo pacman -S git`

### Node.js

- 下载 [安装程序](http://nodejs.org/) 来安装。

### HEXO

```
$ npm install -g hexo-cli
```



## 配置

### 建立网站

创建博客文件夹

```
mkdir <blog_name>
```

在此文件夹初始化

```
hexo init <blog_name>
```

###　配置 Hexo

**网站**

```
# Site
title:            
subtitle: 
description: 
keywords:
author: 
language: 
timezone: 
```

| 参数          | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| `title`       | 网站标题                                                     |
| `subtitle`    | 网站副标题                                                   |
| `description` | 网站描述                                                     |
| `keywords`    | 网站关键词                                                   |
| `author`      | 作者名字                                                     |
| `language`    | 网站使用的语言                                               |
| `timezone`    | 网站时区：详见[时区列表](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) |

#### URL

```yaml
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: 
root: 
permalink: :year/:month/:day/:title/
permalink_defaults:
```

| 参数                 | 描述                     |
| -------------------- | ------------------------ |
| `url`                | 网址                     |
| `root`               | 网站根目录               |
| `permalink`          | 文章的永久链接格式       |
| `permalink_defaults` | 永久链接中各部分的默认值 |

> 提醒
>
> 1. 如果你的网站在子目录中，如：`https://yoursite.com/blog` ，就把你的 `url` 设为 `http://yoursite.com/blog` 并把 `root` 设为 `/blog/`。 
>
> 2. 不设置 URL，会回报以下错误
>
>    > $ hexo clean && hexo g && hexo s
>    >
>    > FATAL Cannot read property 'replace' of null
>    >
>    > TypeError: Cannot read property 'replace' of null



**目录**

```yaml
# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render: README.md
```

| 参数           | 描述                |
| -------------- | ------------------- |
| `source_dir`   | 资源文件夹          |
| `public_dir`   | 公共文件夹          |
| `tag_dir`      | 标签文件夹          |
| `archive_dir`  | 归档文件夹          |
| `category_dir` | 分类文件夹          |
| `code_dir`     | Include code 文件夹 |
| `i18n_dir`     | 国际化文件夹        |
| `skip_render`  | 跳过文件的渲染      |

**文章**

```yaml
# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: true
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
```

| 参数                | 描述                                                         |
| ------------------- | ------------------------------------------------------------ |
| `new_post_name`     | 新文章的文件名称                                             |
| `default_layout`    | 预设布局                                                     |
| `auto_spacing`      | 在中文和英文之间加入空格                                     |
| `titlecase`         | 把标题转换为 title case                                      |
| `external_link`     | 在新标签中打开链接                                           |
| `filename_case`     | 把文件名称转换为 (1) 小写或 (2) 大写                         |
| `render_drafts`     | 显示草稿                                                     |
| `post_asset_folder` | 启动 [Asset 文件夹](https://hexo.io/zh-cn/docs/asset-folders) |
| `relative_link`     | 把链接改为与根目录的相对位址                                 |
| `future`            | 显示未来的文章                                               |
| `highlight`         | 代码块的设置                                                 |



## 部署

```yaml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: 
  repo:
```



## 基本功能

```bash
#打开 Git bash
#清除生成的网页文件
hexo clean
#生成网页文件
hexo g
#上次网页文件到 Github page
hexo d
```



## 常用页面添加

- 新增一个 404 页面：`hexo new page 404`
- 新增一个 about 页面：`hexo new page about`
- 新增一个分类页面：`hexo new page categories`
- 新增一个 tag 标签云页面：`hexo new page tags`

  在 `source/tags/index.md` 编辑:

  ```bash
  ---
  title: tags
  date: 2018-03-05 11:11:11
  type: "tags"
  ---
  ```

##  插件使用

插件官网：<https://hexo.io/plugins/>

### 基本命令

- 安装插件：`npm install 插件名 --save`
- 卸载插件：`npm uninstall 插件名 --save`
- 更新插件和博客框架（需要在 hexo 目录下）：

  ```
  npm update
  ```

  - 实质是通过根目录下 package.json 文件更新各大组件

### 必备插件

- 支持RSS：`npm install hexo-generator-feed --save`

- 文章加密：`npm install hexo-blog-encrypt`

- 本地搜索支持，需要主题有对应的设置：`npm install hexo-generator-search --save`

- TOC设置`npm install hexo-renderer-markdown-it-plus`

- HTML 压缩：`npm install hexo-html-minifier --save`

- JavaScript 压缩：`npm install hexo-uglify --save`

- CSS 压缩插件：`npm install hexo-clean-css --save`

- 图片懒加载法案一：`npm install hexo-lazyload-image --save`

  __选择性__


- SEO优化：`npm install hexo-generator-seo-friendly-sitemap --save`
- 生成站点地图：`npm install hexo-generator-sitemap --save`
- 生成百度站点地图：`npm install hexo-generator-baidu-sitemap --save`
- 图片懒加载方案二：`npm install hexo-renderer-marked-lazy --save` 
  - 可能会导致无法显示外链图片

## 功能实现

### 版权声明

打开 Next 主题目录下的 `_config.yml` 文件，`post_copyright` 设置 `enable: true`。



### 打赏功能

1. 打开 Next 主题目录下的 `_config.yml` 文件，设置如下：

```
# Reward
reward_comment: Donate comment here
wechatpay: /images/wechatpay.jpg
alipay: /images/alipay.jpg
bitcoin: /images/bitcoin.png
```

2. 将二维码图片放置在主题目录下的 `.\source\images`目录下。



###  RSS订阅

在 hexo 的 _config.yml 添加：

```bash
#RSS 订阅插件
plugin:
- hexo-generator-feed
#RSS 插件配置
feed:
  type: rss2
  path: atom.xml #atom.xml或者rss.xml，放根目录下
  limit: 20
  hub:
  content: true
```

###  目录功能

[参考文章](http://knowhard.com/2017/10/01/Hexo-Theme-NexT/#6-toc-%E8%AE%BE%E7%BD%AE)

- 安装hexo-renderer-markdown-it-plus

```bash
npm un hexo-renderer-marked --save
npm i hexo-renderer-markdown-it-plus --save
```

- 站点配置文件_config.yml

```
markdown_it_plus:
     highlight: true
     html: true
     xhtmlOut: true
     breaks: true
     langPrefix:
     linkify: true
     typographer:
     quotes: “”‘’
     pre_class: highlight
```

- 在文档任意位置输入：`@[TOC]`，即可生成目录和锚点



###  图片懒加载

安装 `Hexo-lazyload-image` 插件

修改  `_config.yml` 文件，设置懒加载用图

```
lazyload:
  enable: true 
  onlypost: false
  loadingImg: # eg. ./images/loading.png 
```



###  本地搜索

安装 `hexo-generator-search` 插件

站点 _config.yml 添加:

```
search:
  path: search.xml
  field: post
```

- **path** - file path. By default is `search.xml` . If the file extension is `.json`, the output format will be JSON. Otherwise XML format file will be exported.
- __field__ - the search scope you want to search, you can chose:
  - **post** (Default) - will only covers all the posts of your blog. 只索引文章(post)
  - **page** - will only covers all the pages of your blog. 只索引页面
  - **all** - will covers all the posts and pages of your blog. 全部索引







### 在线管理

无法直接在 Github pages 等托管中工作，需要搭配服务器使用

安装 `hexo-admin` 插件

在 hexo 的 _config.yml 添加

```bash
  admin:
    username: myfavoritename #登录名
    password_hash: xxxxx #密码对应的md5 hash值
    secret: a secret something #用于保证cookie安全
```

域名/admin，进入后台



### 本地文件夹

用于插入本地图片/音乐/视频

- 配置文件`_config.yml` 的`post_asset_folder`设置为`true`
- Hexo 目录下执行`npm install hexo-asset-link --save`
- 再运行`hexo n "xxxx"`来生成md文件时，`/source/_posts`文件夹内除了`xxxx.md`文件还有一个**同名的文件夹**，用来放入图片
- 插入图片格式： 
  - ```markdown
    ![Alt Text](./2019-02-14-Test-Post/Test-Image.png "Title Text")
    ![Alt Text](2019-02-14-Test-Post/Test-Image.png "Title Text")
    ```

  - ```html
    <img src="图片所在目录/图片名.jpg" />
    ```



### 点击特效

点击红心特效：

1. 在`/themes/next/source/js/src`下新建文件 `clicklove.js` ，接着把该[链接](http://7u2ss1.com1.z0.glb.clouddn.com/love.js)下的代码拷贝粘贴到 `clicklove.js` 文件中。

```js
!function(e,t,a){function n(){c(".heart{width: 10px;height: 10px;position: fixed;background: #f00;transform: rotate(45deg);-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);}.heart:after,.heart:before{content: '';width: inherit;height: inherit;background: inherit;border-radius: 50%;-webkit-border-radius: 50%;-moz-border-radius: 50%;position: fixed;}.heart:after{top: -5px;}.heart:before{left: -5px;}"),o(),r()}function r(){for(var e=0;e<d.length;e++)d[e].alpha<=0?(t.body.removeChild(d[e].el),d.splice(e,1)):(d[e].y--,d[e].scale+=.004,d[e].alpha-=.013,d[e].el.style.cssText="left:"+d[e].x+"px;top:"+d[e].y+"px;opacity:"+d[e].alpha+";transform:scale("+d[e].scale+","+d[e].scale+") rotate(45deg);background:"+d[e].color+";z-index:99999");requestAnimationFrame(r)}function o(){var t="function"==typeof e.onclick&&e.onclick;e.onclick=function(e){t&&t(),i(e)}}function i(e){var a=t.createElement("div");a.className="heart",d.push({el:a,x:e.clientX-5,y:e.clientY-5,scale:1,alpha:1,color:s()}),t.body.appendChild(a)}function c(e){var a=t.createElement("style");a.type="text/css";try{a.appendChild(t.createTextNode(e))}catch(t){a.styleSheet.cssText=e}t.getElementsByTagName("head")[0].appendChild(a)}function s(){return"rgb("+~~(255*Math.random())+","+~~(255*Math.random())+","+~~(255*Math.random())+")"}var d=[];e.requestAnimationFrame=function(){return e.requestAnimationFrame||e.webkitRequestAnimationFrame||e.mozRequestAnimationFrame||e.oRequestAnimationFrame||e.msRequestAnimationFrame||function(e){setTimeout(e,1e3/60)}}(),n()}(window,document);
```

2. 在`\themes\next\layout\_layout.swig`文件末尾添加：

```html
\<!-- 页面点击小红心 -->
<script type="text/javascript" src="/js/src/clicklove.js"></script>
```



### 插入多媒体

- 插入视频

  - 同网易云音乐，生成iframe类型外链播放器来引用。

- 插入音乐

  - 网易云音乐网页端，生成外链播放器，将代码复制到博文任意位置
  
```php+HTML
#本文的范例
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=1859310&auto=1&height=66"></iframe>
```

- 插入图片

  - 博文中引用外链图片 `![标题，可选](图片链接)`



### Gitment评论系统

[Hexo-Next 添加 Gitment 评论系统](https://ryanluoxu.github.io/2017/11/27/Hexo-Next-%E6%B7%BB%E5%8A%A0-Gitment-%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F/)

[Hexo博客Next主题添加Gitment评论系统坑点](https://github.com/swlfigo/Study/wiki/Hexo%E5%8D%9A%E5%AE%A2Next%E4%B8%BB%E9%A2%98%E6%B7%BB%E5%8A%A0Gitment%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F%E5%9D%91%E7%82%B9)



### Live2D 模型

[hexo-helper-live2d](<https://github.com/EYHN/hexo-helper-live2d>)

1. 安装插件

`npm install --save hexo-helper-live2d`

2. 安装模型

`npm install live2d-widget-model-hijiki`

3. 配置

```
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  debug: false
  model:
    use: live2d-widget-model-hijiki
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: false
```

4. 补充

[live2D 模型预览](https://huaji8.top/post/live2d-plugin-2.0/)



### 文章摘要

- 正文使用 `<!--more-->`截断，首页摘要只显示该标记之前的内容，包括图片。

- YAML 添加 `photos` 属性，用于摘要显示图片。

  ```
  ---
  title: 
  date: 
  tags: 
  categories: 
  photos:
      - "https://xxx.jpg"
  ---
  ```



### PDF 插件

1. 安装
   `npm install --save hexo-pdf`
2. 

```bash
安装
npm install --save hexo-pdf

使用
网络引用：
{% pdf http://xxx.pdf %}
本地文件夹：
{% pdf  test.pdf %}
```



###  HTML5 音乐播放器 aplayer

[项目地址](https://github.com/MoePlayer/hexo-tag-aplayer)


```bash
#安装
npm install hexo-tag-aplayer --save

#需要音乐的地方插入
{% aplayer "歌曲名称" "作者" "音乐_url" "封面图片_url" "autoplay" %}

#本地文件夹开启情况下
{% aplayer "Black Flies" "Ben Howard" "Black Flies - Ben Howard.mp3" "http://p1.music.126.net/GIM5l9xNmtudCJ72afnzeQ==/18494885093016151.jpg" %}
```

### HTML5 视频播放器 dplayer

[项目地址](https://github.com/MoePlayer/hexo-tag-dplayer)

```bash
#安装
npm install hexo-tag-dplayer --save

#插入视频

#网络地址
{% dplayer "url=http://home.ustc.edu.cn/~mmmwhy/GEM.mp4" "pic=http://home.ustc.edu.cn/~mmmwhy/GEM.jpg" "loop=yes" "theme=#FADFA3" "autoplay=false" "token=tokendemo" %}

#本地文件夹功能开启情况下
{% dplayer "url=广州沙面.20190405.540P.简化.mp4"  "pic=广州沙面.20190405.540P.简化.png" "loop=yes" "theme=#FADFA3" "autoplay=false" "token=tokendemo" %}
```



## 我的博客

__网站__
- [x] Theme: Next
- [x] Tags
- [x] Categories
- [x] RSS
- [x] 本地搜索文章
- [ ] hexo-admin 后台管理

__文章功能__
- [x] TOC设置
- [x] 加密模块
- [x] 图片懒加载（非必要不安装）
- [x] 本地图片
- [x] Aplayer 本地多媒体播放


__其他__

- [x] SNS: Github, E-mail
- [x] 公益404
- [x] Donate
- [x] Gitment评论系统
- [x] 点击红心特效

---

## 参考链接

[Easy Hexo](https://easyhexo.com/)

[使用 Github 空间搭建 Hexo 技术博客](http://www.youmeek.com/hexo/)

[Hexo-lazyload-image图片懒加载](https://www.jianshu.com/p/cb2f0a882d08)

[使用Encrypt插件给Hexo博客文章加密](https://wenzizhou.com/%E4%BD%BF%E7%94%A8Encrypt%E6%8F%92%E4%BB%B6%E7%BB%99Hexo%E5%8D%9A%E5%AE%A2%E6%96%87%E7%AB%A0%E5%8A%A0%E5%AF%86/)

[hexo之加密插件hexo-blog-encrypt](http://cocofe.cn/2016/11/13/hexo%E4%B9%8B%E5%8A%A0%E5%AF%86%E6%8F%92%E4%BB%B6hexo-blog-encrypt/)

[Hexo 主题 —— NexT 设置](http://knowhard.com/2017/10/01/Hexo-Theme-NexT/#6-toc-%E8%AE%BE%E7%BD%AE)

[Hexo Next如何在文章摘要展示图片](https://faithlove.github.io/2018/07/18/Hexo-Next%E5%A6%82%E4%BD%95%E5%9C%A8%E6%96%87%E7%AB%A0%E6%91%98%E8%A6%81%E5%B1%95%E7%A4%BA%E5%9B%BE%E7%89%87/)

[如何为 Hexo 博文加入图片](https://liolok.github.io/zh-CN/%E5%A6%82%E4%BD%95%E4%B8%BA-Hexo-%E5%8D%9A%E6%96%87%E5%8A%A0%E5%85%A5%E5%9B%BE%E7%89%87/)

[Hexo博客yilia主题首页添加helper-live2d模型插件](https://blog.csdn.net/Aoman_Hao/article/details/82049821)

[GitHub中Hexo next主题下搭建的博客中增加PDF插件](https://blog.csdn.net/lihangll/article/details/80516085)

