---
title: 在github上开博客
date: 2016-09-24 20:00:33
tags: technology
category: technology
toc: true
---
# 在github上开博客
## 创建主页
按照github pages向导,很快的完成.
https://pages.github.com/

<!--more-->

**Tips**:

user 和 Orgnization 主页只能从 master 分支生成,project主页可以从 master,gh-pages分支生成(在settings中选择).

>Note: The publishing branch you use depends on the type of GitHub Pages site you have.

>For User or Organization pages, use the master branch.

>For Project pages, use the gh-pages or master branch. Alternatively, you can also publish your site from a /docs folder on the master branch. For more information, see "Configuring a publishing source for GitHub Pages."


我创建的是个人主页,所以github Settings 中有如下提示:
>User pages must be built from the master branch.

## 配置本地编辑环境(Jekyll) (可跳过最终选择了HEXO)

安装向导:
https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/

**Tips**:

1. 使用 ruby gem 安装 bundler没有速度

        解决方法:需要配置一下gem源,源地址及配置方法见:
        (传送门) https://gems.ruby-china.org/

1. Gemfile文件中 source 和 系统中gem配置相同的源
    >source 'https://gems.ruby-china.org'
    gem 'github-pages', group: :jekyll_plugins

1. 编写完Gemfile文件,使用bundle安装时 `budle install` 出错.

        错误信息:
    Make sure that `gem install ffi -v '1.9.14'` succeeds before bundling.

1. 直接运行 `sudo gem install ffi -v '1.9.14'` 报错.
        错误信息:
    mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h

    解决方法:
    `sudo apt-get install ruby2.3-dev`

1. 直接运行 `sudo gem install nokogiri -v '1.6.8'` 报错.
        错误信息:
    invalid gem: package is corrupt, exception while verifying: undefined method 'size' for nil:NilClass (NoMethodError) in /var/lib/gems/2.3.0/cache/nokogiri-1.6.8.gem

    解决方法:
    将`/var/lib/gems/2.3.0/cache/`目录删除

安装完成,运行 bundle exec jekyll serve
在浏览器中看到了可爱的 `hello world`

## 配置本地编辑环境(HEXO)
按照官网上的向导: https://hexo.io/

```
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```

很快就启动了一个强大的`hello world`

sudo npm install hexo-deployer-git --save

INFO  Deploy done: git

## HEXO 一些命令


hexo g = hexo generate  #生成
hexo s = hexo server  #启动本地预览
hexo d = hexo deploy  #远程部署
hexo n "文章标题" = hexo new "文章标题"  #新建一篇博文

hexo s -g  #等同先输入hexo g，再输入hexo s
hexo d -g  #等同先输入hexo g，再输入hexo d



hexo new draft 'draft is here'

http://qjzhixing.com/2015/08/26/


INFO  Generated: 2016/09/withimage/index.html
INFO  Generated: 2016/09/withimage/logo.jpg

<img src="withimage/logo.jpg" alt="test">
<img src="/2016/09/withimage/logo.jpg" alt="test">

在博客中插入图片
http://www.tuicool.com/articles/umEBVfI
https://github.com/CodeFalling/hexo-asset-image

npm install https://github.com/CodeFalling/hexo-asset-image --save

## 配置 HEXO 模板

https://www.haomwei.com/technology/maupassant-hexo.html


评论
disqus (disqus,facebook,Twitter,google)
http://duoshuo.com/create-site

rss
$ sudo npm install hexo-generator-feed --save
$ sudo npm install hexo-generator-baidu-sitemap --save

baidusitemap:
    path: sitemap.xml

http://www.jianshu.com/p/739bf1305e66
