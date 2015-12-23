# Hexo 入门指南（七） - 评论 & 分享

## 评论 ##

hexo默认集成了disqus，但是在天朝明显多说更受欢迎一点。

首先到多说官网去注册一个账号。然后点击进入添加站点页面，填写所有信息。注意，多说域名的前缀就是站点的短网址，下面要用到，这里假设为short_name。

在_config.yml中添加多说的配置：

```
duoshuo_shortname: short_name
```

修改themes\<theme_name>\layout\_partial\article.ejs，把第38行到41行的如下代码：

```
<% if (!index && post.comments && config.disqus_shortname){ %>
<section id="comments">
  <div id="disqus_thread">
    <noscript>Please enable JavaScript to view the <a href="//disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
  </div>
</section>
<% } %>
```

替换成：

```
<% if (!index && post.comments && config.duoshuo_shortname){ %>
<section id="comments">
  <!-- 多说评论框 start -->
  <div class="ds-thread" data-thread-key="<%= post.layout %>-<%= post.slug %>" data-title="<%= post.title %>" data-url="<%= page.permalink %>"></div>
  <!-- 多说评论框 end -->
  <!-- 多说公共JS代码 start (一个网页只需插入一次) -->
  <script type="text/javascript">
  var duoshuoQuery = {short_name:'<%= config.duoshuo_shortname %>'};
    (function() {
      var ds = document.createElement('script');
      ds.type = 'text/javascript';ds.async = true;
      ds.src = (document.location.protocol == 'https:' ? 'https:' : 'http:') + '//static.duoshuo.com/embed.js';
      ds.charset = 'UTF-8';
      (document.getElementsByTagName('head')[0] 
       || document.getElementsByTagName('body')[0]).appendChild(ds);
    })();
  </script>
  <!-- 多说公共JS代码 end -->
</section>
<% } %>
```

之后，找到第27到29行：

```
<% if (post.comments && config.disqus_shortname){ %>
  <a href="<%- post.permalink %>#disqus_thread" class="article-comment-link">Comments</a>
<% } %>
```

替换成：

```
<% if (post.comments && config.duoshuo_shortname){ %>
  <a href="<%- url_for(post.path) %>#comments" class="article-comment-link">留言</a>
<% } %>
```

## 分享 ##

hexo默认提供的那四个在国内也被墙了。这里替换成百度一键分享。

找到themes\landscape\layout\_partialarticle.ejs26行：

```
<a data-url="<%- post.permalink %>" data-id="<%= post._id %>" class="article-share-link">分享</a>
```

替换成：

```
<a data-url="<%- post.permalink %>" data-id="<%= post._id %>" class="article-share-link bdsharebuttonbox" data-cmd="more">分享</a>
<script>window._bd_share_config={"common":{"bdSnsKey":{},"bdText":"","bdMini":"1","bdMiniList":false,"bdPic":"","bdStyle":"2","bdSize":"16"},"share":{}};with(document)0[(getElementsByTagName('head')[0]||body).appendChild(createElement('script')).src='http://bdimg.share.baidu.com/static/api/js/share.js?v=89860593.js?cdnversion='+~(-new Date()/36e5)];</script>
```

之后打开themes\landscape\source\js\script.js，35~86行全部注释掉。

## 后记 ##

仅以此教程，悼念Aaron Swartz，RSS和Markdown的联合创始人。没有他，开源博客界就不会有今天。