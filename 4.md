# Markdown + Gitbook

## 使用Gitbook制作电子书

Gitbook是一个命令行工具，可以把你的Markdown文件汇集成电子书，并提供PDF等多种格式输出。你可以把Gitbook生成的HTML发布出来，就形成了一个简单的静态网站。Gitbook还有一个同名的平台（gitbook.io），可以发布和销售电子书，并提供了一个Markdown客户端工具（支持Mac、Windows和Linux）帮助写作。以下是我在使用Gitbook中的笔记。

首先Gitbook和Git/Github都没有什么关系。它只是一个build book的工具而已。但它的Git前缀的确引起了许多人的迷惑，起初我认为至少它也是个和Github类似的Git平台吧，但其实没什么关系，你只要懂几条markdown语法，不必理解任何与Git相关的东西就能用Gitbook了，不要为其名字迷惑。

**第0步** 安装npm（Node Package Manager）。从node.js的[官网](http://nodejs.org/#download)上下载安装程序，即可完成Node.js和npm的安装。

**第1步** 通过npm安装Gitbook。

> $ npm install gitbook -g

完成后花10分钟阅读下Gitbook的[帮助文档](http://help.gitbook.io/)。如果你没耐心看手册，那就继续往下读吧 :D

**第2步** 了解Gitbook的基本规则。

Gitbook需要2个基本文件：

*   README.md
*   SUMMARY.md

README.md是关于你的书的介绍，而SUMMARY.md中则包含了书目，即章节结构，它的格式大致是：

```
*  [第1章](c1.md)  
  *  [第1节](c1s1.md)  
  *  [第2节](c1s2.md)  
*  [第2章](c2.md)
```

剩下的东西就很好理解了，你只需要编写相应章节即可。在编辑完README.md和SUMMARY.md后，你可以运行以下命令：

> $ gitbook serve -p 8080 .

Gitbook首先把你的Markdown文件编译为HTML文件，并根据SUMMARY.md生成书的目录。所有生存的文件都保存在当前目录下的一个名为_book的子目录中。完成这些工作后，Gitbook会作为一个HTTP Server运行，并在8080端口监听HTTP请求。

运行以上命令后，打开浏览器，在地址栏输入：`http://localhost:8080`即可看到你的书页了。

其中位于左侧书目顶部的`Introduction`一节就编译自README.md，而书目本身自编译自SUMMARY.md。你要在自己的网站上发布新书，只需把_book目录复制到服务器相应目录即可。至此Gitbook的基本用法就介绍完毕。下面简单讨论下Gitbook的其他应用，包括Gitbook的插件、与Github的融合、Gitbook客户端、Gitbook平台，以及Gitbook的问题。

**Gitbook的插件支持**

Gitbook可以生成HTML，因此它支持一些外部的JavaScript文件嵌入到HTML中，例如Google统计、Disqus评论系统等。以下以页面中嵌入Disqus评论为例。

首先是安装Gitbook的Disqus插件。

> $ npm install gitbook-plugin-disqus

然后建立一个book.json文件，其格式如下：

```
{  "plugins":  ["disqus"],  "pluginsConfig":  {  "disqus":  {  "shortName":  "NAME-FROM-DISQUS"  }  }  }
```

把上面的`NAME-FROM-DISQUS`修改为你在Disqus上的项目名即可。

再次运行命令：

> $ gitbook serve -p 8080 .

并刷新浏览器，即可看到附加了Disqus评论的页面。

**与Github的融合**

Gitbook的博客上说Github提供了对Gitbook的特殊支持，但我没有测试。只是依然把源文件保存在Github上，然后用Gitbook去编译。期待Gitbook做的更好。

**Gitbook客户端**

Gitbook客户端支持Mac、Windows、Linux。我在Mac和Windows简单尝试了这个客户端，总体而言可以用。但也仅仅是可以用而已。你可以在客户端里编辑Markdown文件，并提供一个实时的预览窗口；可以关联到你的Gitbook账户，并把内容同步到gitbook.io，并为你生成PDF等。说句题外话，如果你要Markdown的客户端的话，飞象马克更好用，至少Vim编辑模式你得支持啊。

**Gitbook的问题**

Gitbook网站的访问速度很慢。可以在生成_book目录后，把其中的HTML文件和gitbook子目录（包含字体和js文件等）复制到自己的网站上。

Gitbook提供的push功能不能用。push.gitbook.io这个地址无法访问，不知是否是临时性服务故障。

Gitbook生成PDF的中文字体极其难看。万分期待改进。话说Gitbook生存的HTML上的中文非常漂亮。

在我的手机上看Gitbook的页面时，会让浏览器挂掉。

## 使用Gitbook发布电子书

上次说到[用GitBook制作电子书](http://www.ituring.com.cn/article/127645)，侧重在使用gitbook这个命令行工具，今天要说的重点是GitBook这个平台。当你把书放到GitBook上后，可以设置书的价格（每笔交易GitBook抽走20%作为佣金），也可以设置为免费，以及接受捐赠。如果你要收费或接受捐赠，则需要一个PayPal账户。在开始前，我要友情提示一句，在国内访问GitBook的速度很慢，通过VPN访问才好。

**第-1步** 用git这个源代码管理工具来管理你的Markdown文件。最好有个GitHub账户，这样每次push到GitHub时，GitBook都会自动为你的更新build新的版本（同时生成HTML、PDF、ePUB、MOBI这4个版本）。

**第0步** 注册一个GitBook帐号。

**第1步** 在GitBook添加一本书，填写书名等基本信息即可。完成后，GitBook会为你生成一个git仓库，其格式为：

> https://push.gitbook.io/{author}/{book}.git

`author`即你的GitBook用户名，`book`即你的书名，如我创建的书的git仓库：

> https://push.gitbook.io/berlinix/guaidanuniversity.git

这样你可以在编写完Markdown后，通过`git push`同步到GitBook。

**第2步** 把你本地的Markdown文件push到GitBook。我发现`git push`时常失败（服务器返回5xx错误），因此还有一种方法就是把你的GitHub项目与GitBook关联。每次push到GitHub时，会通过GitBook的webhook自动同步到GitBook上。

在Book Setting中简单配置一下即可，如我的配置为：`berlinix/gdu` （GitHub用户名为berlinix，GitHub仓库名为gdu）

在第一次push后，就可以看到你在GitBook上的电子书了，其访问地址为：

> http://{author}.gitbooks.io/{book}/

这是你电子书的主页，从这个页面可以直接打开HTML版本，或下载PDF等电子书版本，一般用户也可以为你的书添加评论。如：

> http://berlinix.gitbooks.io/guaidanuniversity/

要直接访问HTML版本，可以通过链接：

> https://www.gitbook.io/read/book/{author}/{book}

直接访问，如：

> https://www.gitbook.io/read/book/berlinix/guaidanuniversity

至此，GitBook平台的基本用法就介绍完毕。下面是我的一些使用经验。

**个性化域名**

HTML版本的URL很复杂，可以使用个性化域名简化之。在域名注册商那里添加一条CNAME记录即可，如：

> CNAME gdu.berlinix.com www.gitbook.io 300

并把`gdu.berlinix.com`配置到Book Setting中去，这样可以通过简单的`gdu.berlinix.com`来取代`https://www.gitbook.io/read/book/berlinix/guaidanuniversity`。同理，电子书的主页也可设置个性化域名，就不再赘述。

**删除电子书**

同样是在Book Setting中，可以删除电子书。在电子书列表中没有删除接口。

**GitBook电子书封面**

可以为电子书添加封面。只需添加2个名为`cover.jpg`和`cover_small.jpg`的两个图片即可。官方建议cover.jpg尺寸1800*2360，cover_small.jpg尺寸200*262。花2元即可在淘宝上找个做封面的人为你制造一个简单的封面，做得好就要花更多一些了 :)

**GitBook帐号头像**

似乎只接受Gravatar.com的头像。把Gravatar帐号关联过去即可。Gravatar提供的服务是把你的邮箱和头像关联起来，当你在其他网站注册时就不用每次都上传同一个头像，只需简单与Gravatar帐号关联即可。这样替换头像也方便了，一次替换、处处生效。

**访问优化**

按GitBook的访问速度，如果真让人访问GitBook上的HTML页面真是自寻死路啊，因此最好是把GitBook编译后的HTML放在自己的网站上。同时，为自己网站的HTML生成Disqus支持。例如你可以访问我放到自己服务器后的页面（用手机访问效果也非常好）：

> http://www.berlinix.com/gdu/index.html

**电子书Bug**

上次说到GitBook生成PDF的中文字体非常丑陋，另外还有一个问题，那就是生成的PDF可能是残全不全的。我编译后发现内容只剩一半。我已邮件过去报告这个Bug，还在等回信 :)

总体而言，GitBook还是很好玩，比起其他写作平台而言，要自由、简单，并舒服得多，可以用Vim编辑，支持Markdown语法，用git管理，关联GitHub后每次push后还能自动编译，生成多种电子书格式。如果你的书极为畅销的话，还能获取到捐赠或购买，没有理由不尝试的呀。

## 注

来源：

+ [使用Gitbook制作电子书](http://www.ituring.com.cn/article/127645)
+ [使用GitBook平台发布电子书](http://www.ituring.com.cn/article/127744)