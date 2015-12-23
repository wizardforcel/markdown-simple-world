# Hexo 入门指南（三） - 文章 & 草稿

## 文章 ##

命令行中输入：

```
$ hexo new "new article"
```

之后在source/_posts目录下面，多了一个new-article.md的文件。

打开之后我们会看到：

```
title: new article
date: 2014-11-01 20:10:33
tags:
---
```

文件的开头是属性，采用统一的yaml格式，用三条短横线分隔。下面是文章正文。

文章的正文支持markdown格式，建议你先学习一下它的语法。markdown不像html似的一大堆标签，很简单，只有几个符号。

新建、删除或修改文章后，不需要重启hexo server，刷新一下即可预览。

### 属性 ###

文章可以拥有如下属性：

| | | |
|-|-|-|
| Setting | Description | Default |
| layout | Layout | post或page |
| title | 文章的标题 | 
| date | 创建日期 | 文件的创建日期 |
| updated | 修改日期 | 文件的修改日期 |
| comments | 是否开启评论 | true |
| tags | 标签 | 
| categories | 分类 | 
| permalink | url中的名字 | 文件名 |

动态博客中通过发布文章页面设置的各种属性，在hexo里要这样设置。

## 分类和标签 ##

例如：

```
categories:
- 日记
tags:
- Hexo
- node.js
```

## 摘要 ##

同wordpress一样，<!--more-->之上的内容为摘要。

## layout ##

如果你修改了layout，在scaffolds文件夹里一定要有名字对应的模版文件，否则会采用默认模版。

## 文件名 ##

在配置文件中的new_post_name项可以设置文件名，默认为:title，也就是你在命令行输入的名字。

文件名可以为下面几个变量和字符串常量的任意组合：

| | |
|-|-|
| Variable | Description |
| :title | Escaped title (lower case and replace spaces with dash) |
| :year | Created year (4-digit) |
| :month | Created month (2-digit) |
| :i_month | Created month (Without leading zeros) |
| :day | Created day (2-digit) |
| :i_day | Created day (Without leading zeros) |

## 草稿 ##

草稿相当于很多博客都有的“私密文章”功能。

```
$ hexo new draft "new draft"
```

会在source/_drafts目录下生成一个new-draft.md文件。但是这个文件不被显示在页面上，链接也访问不到。也就是说如果你想把某一篇文章移除显示，又不舍得删除，可以把它移动到_drafts目录之中。

如果你希望强行预览草稿，更改配置文件：

```
render_drafts: true
```

或者，如下方式启动server：

```
$ hexo server --drafts
```

下面这条命令可以把草稿变成文章，或者页面：

```
$ hexo publish [layout] <filename>
```