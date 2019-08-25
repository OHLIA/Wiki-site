---
title: 如何给 Hexo 文章加密
date: 2019-08-20 00:05:33
tags: [Hexo,Blog]
categories: [Hexo,Blog]
---



<!--more-->

1. 安装 `Hexo-blog-encrypt` 插件

2. 修改 _config.yml ,

```yaml
# Security
encrypt:
    enable: true # 开启为true，关闭为false
    default_abstract: 这是篇受保护的文章！#默认文章描述，可选
    default_message: 请输入文章密码！#默认密码输入提示，可选
    default_template: 
                    <script src="//cdn.bootcss.com/jquery/1.11.3/jquery.min.js"></script>
                    <div id="security">
                        <div class="input-container">
                            <input type="password" class="form-control" id="pass" placeholder=" {{message}} " />
                            <label for="pass"> {{message}} </label>
                            <div class="bottom-line"></div>
                        </div>
                    </div>
                    <div id="encrypt-blog" style="display:none">
                        {{content}}
                    </div>
                    #默认的文章详情页密码输入提示框，可选
```

​	`default_template` ，这个是指在文章详情页，我们看到的输入密码阅读的模板，同理，这个也是针对所有文章的。
​	最后的 `content` 显示 `div` 的 `id` 必须 是 `encrypt-blog`同时为了好看，也希望进行隐藏。
​	必须要有一个 `input` 输入框，`id` 必须是`"pass"`，用来供用户输入密码。
​	输入密码之后，务必要有一个触发器，用来调用`decryptAES` 函数。样例中以 `button` 来触发。

3. 针对某篇文章加密
   1. 在Front-Matter添加`password: 密码`即可。
   2. 或者如下：

```yaml
---
title: hello world
date: 
tags:
    - tags1
    - tags2
password: password #此项必需，下面信息为可选
abstract: 这是篇受保护的文章！
message: 请输入文章密码！
template:
        <script src="//cdn.bootcss.com/jquery/1.11.3/jquery.min.js"></script>
        <div id="security">
            <div class="input-container">
                <input type="password" class="form-control" id="pass" placeholder=" {{message}} " />
                <label for="pass"> {{message}} </label>
                <div class="bottom-line"></div>
            </div>
        </div>
        <div id="encrypt-blog" style="display:none">
            {{content}}
        </div>
---
```

4. 其他
   1. 跟 aplayer 或者 dplayer 插件有冲突。文章如果需要加密，无法使用以上两款播放器。–-20190821