---
layout: post
title: 'Jekyll + Github 构建个人 Blog'
date: 2019-03-11 16:01:00 +0800
author: 花样
color: rgb(255,210,32)
cover: '../assets/picture/20190311/blog.jpg'
tags: Jekyll Github Blog
subtitle: '搭建一个属于自己的博客'
---
## 写在前面

一直以来都想搭建一个自己的博客，沉淀知识的同时也提高一下自己的写作水平。由于博主有选择困难症，一直没想到用什么搭博客更好，这期间自己基于Java SSM框架写过博客系统，购买了腾讯云服务器并搭建开发环境部署，但是维护起来比较麻烦，而且自己写的页面也着实难看，后来在Github上看到了 Jekyll + Github 搭建的个人博客，维护很方便，简洁美观，Github托管，让我们更专注于写作。

## Jekyll 是什么？

> _引用自官网_
> Jekyll is a simple, extendable, static site generator. You give it text written in your favorite markup language and it churns through layouts to create a static website. Throughout that process you can tweak how you want the site URLs to look, what data gets displayed in the layout, and more.

翻译过来就是：Jekyll是一个简单，可扩展的静态站点生成器。 您可以使用自己喜欢的标记语言编写文本，然后通过布局来创建静态网站。 在整个过程中，您可以调整网站URL的显示方式，布局中显示的数据等。

## 安装Jekyll环境

博主是基于 Mac OSX 系统，网上对于 Mac OSX 系统搭建Jekyll的文章寥寥无几，搭建过程中踩了很多坑。过程中如果有文件目录权限不足的情况，则修改文件目录权限。

```
chmod -R 777 目录文件
```

### 安装brew

brew 又叫Homebrew，是Mac OSX上的软件包管理工具，能在Mac中方便的安装软件或者卸载软件， 只需要一个命令， 非常方便。

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```


将以上命令粘贴至终端或者iTerm，脚本会在执行前暂停，并说明将它将做什么，按照提示执行即可。

### 安装ruby

```
brew install ruby
```

### 安装gem

Mac自带gem，更换一下安装源

```
# 将默认安装源移除
gem sources --remove https://rubygems.org/
# 添加国内安装源(注意国内网址后缀已经更换为.com)
gem sources --add https://gems.ruby-china.com/
# 缓存
gem sources -u 
```

### 安装Jekyll

```
gem install jekyll
gem install bundler
gem install jekyll-paginate
gem install jekyll-gist
```
执行以上命令安装jekyll。

## 创建博客

首先进入到自己想创建命令的目录下执行

```
jekyll new myBlog
```

创建完成后进入到 myBlog 目录内执行

```
jekyll serve
```

将 http://127.0.0.1:4000 复制到浏览器打开，就可以看到最原始的博客页面。

## 创建Github

注册Github什么的就不说啦，直接到 **Repositories** **New** 一个仓库，Repository name 为 **用户名.github.io** 。
Description 可填可不填写，创建完成后复制仓库地址。

## 创建博客

可以在 Github 上搜索 jekyll 主题或者去 jekyll [官方主题](http://jekyllthemes.org/) 选择自己喜欢的主题。我这是下载的 Github 上 xukimseven 的 [HardCandy-Jekyll](https://github.com/xukimseven/HardCandy-Jekyll) 一款清新 糖果色🍬 的 ‘Jekyll’ 主题。

进入到 myBlog 目录内执行以下命令

```
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:用户名/用户名.github.io.git
git push -u origin master
```

执行完后将 myBlog 文件内非隐藏文件删除，将下载的 jekyll 主题文件夹内的所有文件复制到 myBlog 文件夹内

```
cp -R HardCandy-Jekyll-master/* /目录/myBlog
```
 
执行Git命令，推送到 Github 上

```
git add .
git commit -m'相关注释文字'
git push -u origin master
```

在浏览器上打开 https://用户名.github.io/ 就可以看到博客啦，后续博客系统的设置可以看博主博客的 [README.md](https://github.com/fengfl/fengfl.github.io) 。