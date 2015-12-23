# Hexo 入门指南（五） - 搬家 & 备份

## 搬入hexo ##

首先，需要拿到原博客数据的xml文件。

wordpress的话，后台“工具->导出”就可以生成。点点和lofter也支持类似操作。如果遇到不支持导出xml的博客，先用[http://www.diandian.com/transfer/](http://www.diandian.com/transfer/)转到点点，再用[http://www.diandian.com/backup](http://www.diandian.com/backup)导出XML文件。

之后，安装hexo-migrator-wordpress这个插件

```
npm install hexo-migrator-wordpress --save
```

运行

```
hexo migrate wordpress wordpress.xml
```

xml中的数据就导入到source中了。最后的工作是修复链接什么的。

## 搬出hexo ##

没有什么好的办法。可以写个脚本遍历public文件夹，之后post到指定目录或者制作成xml文件。

## 备份 ##

有句话说得好，数据恢复的最佳方案永远是“备份备份再备份”。

个人建议，分别备份站点配置和文章。站点配置包括blog根目录除了source和public文件夹的所有内容，文章就是source文件夹的全部内容。站点配置不经常变的话可以不用经常备份。