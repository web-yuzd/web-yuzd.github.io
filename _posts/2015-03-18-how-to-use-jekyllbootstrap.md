---
layout: post
title: "如何使用jekyll bootstrap在github上建立个人博客"
description: "这是我用jekyll-bootstrap框架模板搭建的个人博客，本文主要记录了搭建的过程，希望大家可以借鉴学习"
category: ['work', 'code']
tags: ['技巧']
---
{% include JB/setup %}

最近一直研究如何使用jekyll和github pages在github上构建博客，但摸索了很久发现还是很麻烦的，学习成本太高。无意间了解到，可以用jekyll-bootstrap框架三分钟在github上建博客，大大方便了我们这种新手，现在我就和大家分享下我利用jekyll-bootstrap框架建立博客的过程。

大家可以参考下[jekyll-bootstrap](http://jekyllbootstrap.com/)的官网，我是根据官网构建的。

![有帮助的截图]({{ site.url }}/assets/jekyll-bootstrap.jpg)

## 1.在github上建立新的repository

进入你的[github.com](http://github.com/)，新建一个新的repository，命名为 USERNAME .github.com，其中 USERNAME 为你的用户名。如果用户名中有大写字母，命名repository时系统会将大写字母变小写。

## 2.安装Jekyll-Bootstrap
打开git bash，进入你想要创建博客的目录，执行以下操作命令：

<pre>
git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com

cd USERNAME.github.com

git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git

git push origin master
</pre>

注意USERNAME为你的用户名，如果其中有大写字母，应替换为小写。

过几分钟（并非立刻），你就可以访问http://USERNAME.github.com,就会显示默认几个页面。

## 3.安装jekyll，本地访问博客

如果你想在自己的机器上访问自己的博客，预览一下效果，你需要安装jekyll，最好的方式是通过RubyGems安装。关于如何安装Ruby，大家可以自行百度一下哈。安装好之后，启动Ruby的控制台，运行以下命令：

<pre>
gem install jekyll
</pre>
安装成功之后，找到你的博客目录：

<pre>cd USERNAME.github.com </pre>

然后在执行

<pre>jekyll serve</pre>
如果不出意外，http://localhost:4000/ 就可以访问了，也可以是http://127.0.0.1:4000/，这样就可进行本地预览了~

## 4.Jekyll 写博过程

### 配置_config.yml：

1) 修改标题：<code>title : My Blog</code>

2) 修改个人信息：
<pre>
author :

name : Name Lastname

email : blah@email.test

github : username

twitter : username

feedburner : feedname
</pre>

3) 引用：_config.yml中的键值均引用到其他页面；

### 写文章

按照_config.yml的格式permalink: /:categories/:year/:month/:day/:title，可以修改格式，创建markdown格式文件，就可以当初博客发布了。

### 发布

本地预览修改：运行jekyll –server，预览http:127.0.0.1:4000。

发布到github上：通过命令提交或者客户端提交。


到这里整个博客平台就搭建完了，更多的如何修改配置操作，还是要细看下jekyll官方文档的。完成后用git push上去之后，USERNAME.github.com就相应的更新了。在USERNAME.github.com这个目录下，_post文件夹中存放的是你的博文，每个博文对应一个静态md文件，编辑博客的话只需要在终端下用vim或其他文本编辑软件创建md文件，按照md的简单语法，就像写代码一样写博客，并且经过解析，形成的最终html的页面相当美观大方（当然你也可以定制自己的独特风格）。