# Hexo 入门指南（一） - 简介 & 准备

Hexo是一个开源的静态博客生成器，用node.js开发，作者是台湾大学生tommy351。

## 为什么是博客 ##

对于个人网站来说，没有比博客更合适的形式了。在博客中，文章才是最主要的，一切都显得主次分明，干净利落。相比之下，论坛中主题和回复鱼龙混杂，阅读体验非常差。同时，博客比论坛的数据库小很多，便于维护。

## 为什么是静态博客 ##

很多人选择在虚拟主机或vps上面搭建动态博客。但是这些主机商通常“免费的不稳定，稳定的不免费”。前一段时间，我观察了我的个人博客友链上面的几个站点，一部分在十几天之后就销声匿迹了。独立博客如此麻烦的维护工作，能不能减轻一些呢？正如阮一峰前辈所说，blogger分为三个阶段。最开始，是门户博客。之后，是独立博客。最后，觉得独立博客自己管理起来费劲，便找个别人来管的空间，自己负责写就好。如果我们能够找到这样的空间，在自己保留最大控制权前提下，由别人托管，会省去不少事情。

静态博客编译之后是纯html页面，优点就是支持它的环境十分好找，例如github、gitcafe、七牛云存储等站点都支持静态页面托管，自然是我们的首选了。由于github page在国内访问较慢，这篇文章用gitcafe做示范。gitcafe是天朝本地化的github，同样提供展示页和域名绑定功能，不需要备案，就是爽。

但是静态博客并非没有缺点。动态博客更新文章时，脚本是不变的，只需要更新数据库。静态博客要频繁改动文件，不支持增量式上传的东西，比如ftp，就难于管理。此外，还要十分熟悉git各种命令，才能部署页面。

## 准备工作 ##

+ git
+ node.js
+ markdown编辑器
+ gitcafe
+ 域名

markdown编辑器是非必须的，只要你熟悉语法，随便一个编辑器来写都不是问题。

域名也是非必须的，gitcafe pages服务提供免费的二级域名。注册域名的教程这里就不写了。

## 安装 git ##

git的客户端，本人推荐git-scm。

linux下面，在bash中键入：

(Ubuntu, Debian)

```
$ sudo apt-get install git
```

(Fedora, Red Hat, CentOS)

```
$ sudo yum install git
```

windows或mac下，直接到[git-scm官网](http://git-scm.com/)下载安装。

## 安装 node.js ##

linux下：

```
$ sudo apt-get install nodejs
$ sudo apt-get install npm
```

yum同理。

windows或者mac下，直接到[node.js官网](http://nodejs.org/download/)下载安装。
windows还要设置环境变量，把node.js安装路径写进path里面，用半角分号分隔。

## markdown 编辑器 ##

windows下推荐[markdown pad](http://markdownpad.com/)。

mac下推荐[mou](http://25.io/mou/)。

## gitcafe ##

首先注册一个账号，之后点击查看[如何使用pages服务](https://gitcafe.com/GitCafe/Help/wiki/Pages-%E7%9B%B8%E5%85%B3%E5%B8%AE%E5%8A%A9)。

## 相关网页 ##

+ [Hexo主页](http://blog.csdn.net/wizardforcel/article/details/hexo.io)
+ [Hexo github 地址](https://github.com/hexojs/hexo)
+ [git book](http://git-scm.com/book/zh/v1)