---
title: 如何给 Hexo Blog 插入图片
date: 2019-08-21 18:59:05
tags: [Hexo,Blog]
categories: Hexo
---



当前个人推荐 Hexo 文章资源文件夹 加插件 `hexo-asset-image@0.0.2` 的方式，可以在 Typora 等 Markdown 编辑器下显示图片，方便阅读和编辑。

<!--more-->

## 图床

```
![alt](https://xxx.jpg "This is Pic")
```



## Hexo 文章资源文件夹

开启特性，站点配置文件 _config.yml :

```
post_asset_folder: true
```

Hexo 生成文章文件的同时会生成同名目录：

```
hexo new post "测试文章"
```

```
测试文章.md
测试图片-0.jpg
测试文章/
+-- 测试图片-1.png
+-- 测试图片-2.png
+-- 子目录/
|   +-- 测试图片-3.png
|   +-- 测试图片-4.png
```

安装插件

```bash
#任选其一

npm i --save hexo-asset-link
#代码块如果写入 html,CSS 代码会出现问题。--20190821

npm i --save hexo-asset-image@0.0.2
#升级其他版本会出现生成链接错误的问题，0.0.3 到 1.0.0都有。--20190821
#支持文章根目录和同名目录，不支持文章同名目录下的子目录。--20190821
```

编辑文章的图片写法

```bash
#hexo-asset-image:
![](./测试图片-0.jpg) #跟文章同一目录下
![](测试图片-1.png) #文章同名目录下，推荐用法
![](./测试文章/子目录/测试图片-3.png) #失败
![](测试文章/子目录/测试图片-4.png) #失败
<img src="./测试图片-0.jpg" />
<img src="测试文章/测试图片-1.png" />
<img src="./测试文章/测试图片-1.png" />
<img src="./测试文章/子目录/测试图片-3.png" /> #失败
<img src="测试文章/子目录/测试图片-3.png" /> #失败

#hexo-asset-link:
![](测试图片-1.png)
![](./测试图片-2.png)
![](子目录/测试图片-3.png)
![](./子目录/测试图片-4.png)
```



## 参考

[资源文件夹](https://hexo.io/zh-cn/docs/asset-folders.html#%E7%9B%B8%E5%AF%B9%E8%B7%AF%E5%BE%84%E5%BC%95%E7%94%A8%E7%9A%84%E6%A0%87%E7%AD%BE%E6%8F%92%E4%BB%B6)

[如何为-Hexo-博文加入图片](https://liolok.github.io/zh-CN/%E5%A6%82%E4%BD%95%E4%B8%BA-Hexo-%E5%8D%9A%E6%96%87%E5%8A%A0%E5%85%A5%E5%9B%BE%E7%89%87/)