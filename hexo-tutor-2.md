# Hexo 入门指南（二） - 安装、初始化和配置

## 安装和初始化 ##

linux下打开bash，win下面打开cmd，输入：

```
$ npm install hexo -g
$ hexo init blog
$ cd blog
$ npm install
$ hexo server
```

访问[http://localhost:4000](http://localhost:4000)，会看到生成好的博客。

同时，在blog文件夹中，文件如下：

```
2014/11/01  19:45    <DIR>          .
2014/11/01  19:45    <DIR>          ..
2014/11/01  11:16                68 .gitignore
2014/11/01  17:33            13,767 db.json
2014/11/01  11:16    <DIR>          node_modules
2014/11/01  11:17               186 package.json
2014/11/01  11:23    <DIR>          public
2014/11/01  11:16    <DIR>          scaffolds
2014/11/01  17:31    <DIR>          source
2014/11/01  11:16    <DIR>          themes
2014/11/01  11:38             1,844 _config.yml
```

## 配置 ##

站点的配置文件是_config.yml，如果你不小心改花了，这里提供了一份默认的：

```
# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: Hexo
subtitle:
description:
author: John Doe
email:
language:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com
root: /
permalink: :year/:month/:day/:title/
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
permalink_defaults:

# Directory
source_dir: source
public_dir: public

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
highlight:
  enable: true
  line_number: true
  tab_replace:

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Archives
## 2: Enable pagination
## 1: Disable pagination
## 0: Fully Disable
archive: 2
category: 2
tag: 2

# Server
## Hexo uses Connect as a server
## You can customize the logger format as defined in
## http://www.senchalabs.org/connect/logger.html
port: 4000
server_ip: localhost
logger: false
logger_format: dev

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
## Plugins: https://github.com/hexojs/hexo/wiki/Plugins
## Themes: https://github.com/hexojs/hexo/wiki/Themes
theme: landscape
exclude_generator:

# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type:
```

[官方的页面](http://hexo.io/docs/configuration.html)上也提供了每一项详细的解释。

我们需要修改的只有Site部分，以及URL部分的url。Site部分每一项依次是标题、副标题、描述、作者、邮箱和语言（天朝大陆填zh-CN）。url改成网站的网址，如果你的网站放在某个子目录下，比如http://yoursite.com/child，root改成/child。

Server部分，如果之前你的服务器没有运行起来，则可能是端口被占了。把port改成别的数字，或者强行关掉占着端口的进程。

其它设置项先不用管，将会在接下来的文章中解释。

## 注意 ##

**如果页面中出现中文，应以UTF-8无BOM编码格式，所以不要用win自带的记事本，而是用notepad++这种支持编码转换的编辑器。**

由于google在天朝大陆被墙，进入themes\landscape\layout\_partial，打开head.ejs，删掉第31行fonts.googleapis.com的链接。

下载下来jquery-2.0.3.min.js，放到themes\landscape\source\js文件夹中。之后进入themes\landscape\layout\_partial，打开after-footer.ejs，将第17行的路径替换为/js/jquery-2.0.3.min.js。

至此大功告成。