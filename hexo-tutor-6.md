# Hexo 入门指南（六） - sitemap、rss 和部署

## sitemap & rss ##

切换到blog根目录下，输入：

```
$ npm install hexo-generator-feed
$ npm install hexo-generator-sitemap
```

之后重启博客，访问/atom.xml和/sitemap.xml，会发现已经生成了。可以把sitemap提交到搜索引擎的站长平台来增加收录。

## 部署 ##

首先按照前面教程（一）的gitcafe部分建立好代码仓库，这里假设你的用户名是your_name。由于ssh配置比较麻烦，这里采用https方式提交。

找到配置文件中# Deployment一节，修改：

```
type: github
repository: https://gitcafe.com/your_name/your_name.git 
branch: gitcafe-pages
```

之后输入：

```
hexo deploy --generate
```

或者

```
$ hexo generate --deploy
```

hexo会自动生成并部署。

如果之前已经生成过了，直接输入：

```
$ hexo deploy
```

部署即可。

当然，这个命令还有一些bug，比如windows下不能用cmd而是用gitshell。我自己一般会手动敲git代码覆盖提交。