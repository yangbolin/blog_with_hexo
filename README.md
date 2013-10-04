title: hello-world
date: 2013-10-03 14:49:14
tags:
- hexo
categories:
- computer
---

配置hexo写博客
==========

Welcome to [Hexo](http://zespia.tw/hexo)! This is a very fast, simple & powerful blog post, powered by Node.js. Check [documentation](http://zespia.tw/hexo/docs) to learn how to use.

<!--more-->

一、安装hexo
--------

  首先，安装`hexo`的依赖`git`和`node.js`，archlinux下包的名称为`git`和`nodejs`。然后，有两种方式安装`hexo`：  
  (1)用`npm`安装;  
  (2)安装AUR上的`nodejs-hexo`。
  ```
  $ sudo pacman -S git nodejs
  $ npm install -g hexo #(1)
  $ yaourt -S nodejs-hexo #(2)
  ```
  以上也可以一步到位：
  ```
  $ yaourt -S git nodejs nodejs-hexo
  ```

  安装好之后，便可以初始化一个工作目录。执行
  ```
  $ hexo init target_dir
  ```
  或者，
  ```
  $ cd target_dir
  $ hexo init
  ```

二、安装hexo插件
----------

  `hexo`使用时，需要一些plugins，记录如下。更多plugins请查看[这里](https://github.com/tommy351/hexo/wiki/Plugins)。  
  注意：以下命令都是在hexo建立的工作目录下执行。安装完成，如果要启用，请将其添加到总配置文件`_config.yml`，下文会提到。

  RSS Feed：
  ```
  $ npm install hexo-generator-feed --save
  ```
  Sitemap：
  ```
  $ npm install hexo-generator-sitemap --save
  ```
  Migrate from wordpress:
  ```
  $ npm install hexo-migrator-wordpress --save
  ```
  Use vim to highlight code in your markdown source:
  ```
  $ npm install hexo-tag-vimhighlight --save
  ```
  Automatic summarization：
  ```
  $ npm install git://github.com/vfasky/hexo-summarizer.git
  ```
  gzip hexo static files, in order to avoid Apache2/Nginx gzipping at the fly (better performance)
  ```
  $ npm install hexo-gzip --save
  ```

三、安装hexo主题
----------

  主页：https://github.com/tommy351/hexo/wiki/Themes

  选择：`light`（默认自带）、`greyshade`（修改使用）、`modernist`（显示代码不错）
  ```
  $ cd target_dir
  $ git clone https://github.com/nuklly/hexo-theme-greyshade.git themes/greyshade
  $ git clone git://github.com/heroicyang/hexo-theme-modernist.git themes/modernist
  ```

四、hexo配置
--------

  这是主要部分，配置加修改，所有工作目录下的文件（不包括生成的发布内容），都保存到github上的此repo中，生成的静态网站发布到指定位置。

####1. 配置 _config.yml
 
  主要是设定站点、插件、主题、发布地址等。

  结果：
```
# Hexo Configuration
## Docs: http://zespia.tw/hexo/docs/configure.html
## Source: https://github.com/tommy351/hexo/

# Site
title: 两情久长，一起走过
subtitle: 处严寒而以香袭人，受咏赞却与世无言
description: 处严寒而以香袭人，受咏赞却与世无言
author: Shmilee
email: shmilee.zju@gmail.com
language: zh-CN

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://shmilee.github.io
root: /
permalink: :year/:month-:day-:title.html
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code

# Writing
new_post_name: :year/:month-:day-:title.md # File name of new posts
default_layout: post
auto_spacing: false # Add spaces between asian characters and western characters
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
max_open_file: 100
multi_thread: true
filename_case: 0 #Transform filename into (1) lower case or (2) upper case
highlight:
  enable: true
  line_number: true
  tab_replace:

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Archives 默认2,修改为1,只列出标题
## 2: Enable pagination
## 1: Disable pagination
## 0: Fully Disable
archive: 1
category: 1
tag: 1

# Server
## Hexo uses Connect as a server
## You can customize the logger format as defined in
## http://www.senchalabs.org/connect/logger.html
port: 4000
logger: false
logger_format:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: MMM D YYYY
time_format: H:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Disqus
disqus_shortname:

# Extensions
## Plugins: https://github.com/tommy351/hexo/wiki/Plugins
## Themes: https://github.com/tommy351/hexo/wiki/Themes
theme: greyshade #light #modernist
exclude_generator:

plugins:
- hexo-generator-feed
- hexo-generator-sitemap

# Deployment
## Docs: http://zespia.tw/hexo/docs/deploy.html
# 虽然推荐github的repository用https，但SSH clone URL可以避免每次输密码
deploy:
  type: github
  repository: git@github.com:shmilee/shmilee.github.io.git
  branch: master
```

####2. 多说评论

1. 注册:http://duoshuo.com/ , 获得通用代码.

2. 主题目录内一般自带disqus,比照相关代码添加duoshuo

 + [greyshade添加参考](https://github.com/shmilee/blog_with_hexo/commit/554a7e01f21f4927c42f93a316b8d750e5bb2704)

####3. 百度分享

1. 到[百度分享](http://share.baidu.com/code),获取代码.

2. 添加到主题, [greyshade参考](https://github.com/shmilee/blog_with_hexo/commit/94877388292384854fcd493c8bf1628750e55092)

####4. theme杂项

####5. 微博秀

####6. 网站统计：百度或google


五、hexo常用命令简介
----------
  来自：http://zespia.tw/hexo/docs/commands.html

  ```
  $ hexo init [folder] # 初始化一个网站
  $ hexo new [layout] <title> # 创建新文章
  $ hexo generate # 生成静态网页
  $ hexo server # 启动服务，以便本地查看
  $ hexo deploy # 发布你的blog
  $ hexo migrate wordpress wordpress.2013-10-03.xml # 从wp迁移，效果差，仍需要手动调整
  $ hexo clean # 清理缓存(db.json)和生成的文件(public)
  ```

* `init`：
  If folder isn't defined, Hexo will setup the website at the current directory. Hexo has 3 default layouts: `post`, `page` and `draft`. Other layouts will be saved in source/_posts by default.

* `new`：
  If layout isn't defined, it’ll be default_layout setting. If the title is more than one word, wrap it with quotation marks.

* `generate` option：
  `-d` Deploy after generate done; `-w` Watch file changes.

* `deploy` option：
  `--setup` Setup without deployment; `--generate` Generate before deployment.
