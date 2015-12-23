# Hexo 入门指南（四） - 页面、导航、边栏、底栏

## 页面 ##

命令行键入：

```
$ hexo new page about
```

会在source/about中生成index.html。这个就叫做页面，不在文章列表显示，可以通过[http://localhost/about](http://localhost/about)浏览。

页面支持文章的大部分属性，除了分类和标签。

## 导航 ##

打开主题中的设置文件，即themes\<theme_name>\_config.yml（其中<theme_name>是当前主题的名字，默认为landscape，下同），找到menu:，在列表的末端添加About: 关于。刷新页面，导航栏上就出现了关于链接。

## 边栏 ##

进入themes\<theme_name>\layout\_widget目录中，创建about.ejs文件，模仿其他文件中的模版，输入以下内容：

```
<% if (site.tags.length){ %>
  <div class="widget-wrap">
    <h3 class="widget-title">About</h3>
    <div class="widget">
      邮箱：xxx@xxx.com<br />
      微博：@xxxxx
    </div>
  </div>
<% } %>
```

打开themes\<theme_name>\_config.yml，找到#Sidebar，在最后面添加- about。刷新页面。

## 底栏 ##

打开themes\<theme_name>\layout\_partial\footer.ejs修改。

## -banner- ##

打开themes\<theme_name>\source\css\images，把banner.jpg换掉。