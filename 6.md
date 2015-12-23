# Markdown + Pandoc

来源：[Markdown+Pandoc，打通写作界的任督二脉！](http://blog.csdn.net/duqi_yc/article/details/8974041)

Markdown+Pandoc，可以把自己的写作内容，变成世界上已有的任何格式的文件，包括很炫的slide，html5。没有人（或者我没看到）总结过这些内容，导致我走了很多弯路才最终打通任督二脉，特此纪念。

了解Markdwon以后，我的写作世界，只有它；看到Pandoc格式转换以后，对生成的slide和pdf羡慕的不行。那时，自己期望以后的写作是这样的：首先用Markdown把自己的想法写下来；其次，通过Pandoc，把写好的Markdown文件，转换成Slide或者PDF。如此而已。

Pandoc，这个不知道怎么发音，google也没找到。好吧，我就读做panda吧，谁让它是国宝。

Pandoc的运行，是在命令行里面。可是，没那么简单，不是任何一个cmd都可以。你必须要下载Pandoc，请参考[这里](http://pandoc.org/installing.html)。根据自己的os，选择Windows 或者其他。

安装以后，记得Pandoc的目录是啥，然后再到cmd里面去操作一些失传已久的doc命令，转换到pandoc的路径下。

我个人习惯，是把要转换的文件，比如test.md，放到pandoc的路径下，这样在使用pandoc转换的时候，不用输入太多的路径（尤其是我们很多路径是中文，怕可能有一些问题）。当然，也可以调用其他路径的文件，只要自己觉得舒服。

pandoc，就像linux下的iconv，可以把其他格式的文件，转化成自己想要的格式。具体的格式参考请看[这里](http://johnmacfarlane.net/pandoc/demos.html)。

个人常用的有两个格式转换：

+ a：md文件转换成html5
  
  ```
  pandoc -s --mathml -i -t dzslides test.md -o test.html
  ```
+ b：md文件转换成pdf
  
  ```
  pandoc -t beamer test.md -o test.pdf
  ```

这里强调一点，如果想转成PDF文件，要安装LATEX。推荐安装MiKTex。但是，中文转PDF，因latex支持中文差，转换有问题。对于Latex熟悉的人，可以参考这个，看是否能解决中文转slide pdf的问题。

文件转换完成以后，如果有一些地方不合适，可以调整原始的md文件，再转换一次。等熟练以后，从写，到转换就非常迅速了。 当然，Pandoc还有很多的转换格式，大家可以自己去研究发觉。

关于Pandoc的使用，我没有过多的去研究。只是把自己常用的几个功能熟悉了一下。时间，真的真的很宝贵，不知不觉就从指缝中溜走了。所以，我只能在满足自己需求情况下，去使用pandoc。

期待大家更多的分享！