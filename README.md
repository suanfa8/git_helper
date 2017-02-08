# 项目说明

每一个 Git 仓库都建议有一个命名为 README.md 的文件，用于填写项目的相关声明。

README.md 文件应该放置在根目录下，这样别人在访问这个项目的时候，就能够直接看到。

> Git 是一个分布式版本控制软件，最初由林纳斯·托瓦兹（Linus Torvalds）创作。
 
> GitHub是一个通过Git进行版本控制的软件源代码托管服务，由GitHub公司（曾称Logical Awesome）的开发者Chris Wanstrath、PJ Hyett和Tom Preston-Werner使用Ruby on Rails编写而成。

我学习 Git 的感受：
1、不用联网就可以完成操作，等到网络通畅的时候一起往服务器上推送代码；
2、国内外有很多免费的代码托管服务，不用担心自己的资料会丢失；
3、使用 Git 的过程让我们对多分支并行开发有了概念和落地实践；
4、Git 可以在网页上查看代码；
5、可以通过 GitHub 等代码托管社区认识到很多牛人，向它们学习。

在 《Pro Git》 这本书中有这样一段话：
> 如果你希望后面的学习更顺利，记住下面这些关于 Git 的概念。 Git 有三种状态，你的文件可能处于其中之一：已提交（committed）、已修改（modified）和已暂存（staged）。 已提交表示数据已经安全的保存在本地数据库中。 已修改表示修改了文件，但还没保存到数据库中。 已暂存表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。

![Git 三个目录的示意图 ](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-21_105800.png)

> 1. 工作目录是对项目的某个版本独立提取出来的内容。 这些从 Git 仓库的压缩数据库中提取出来的文件，放在磁盘上供你使用或修改。
> 2. 暂存区域是一个文件，保存了下次将提交的文件列表信息，一般在 Git 仓库目录中。 有时候也被称作“索引”，不过一般说法还是叫暂存区域。
> 3. Git 仓库目录是 Git 用来保存项目的元数据和对象数据库的地方。 这是 Git 中最重要的部分，从其它计算机克隆仓库时，拷贝的就是这里的数据。

> 基本的 Git 工作流程如下：1、在工作目录中修改文件。2、暂存文件，将文件的快照放入暂存区域。3、提交更新，找到暂存区域的文件，将快照永久性存储到 Git 仓库目录。


参考资料：

1、[git - 简易指南][1]
[1]:http://www.bootcss.com/p/git-guide/

2、Pro Git
网址：https://git-scm.com/book/en/v2

3、阮一峰的网络日志：Git远程操作详解
http://www.ruanyifeng.com/blog/2014/06/git_remote.html

4、配置 ssh key
http://www.open-open.com/doc/view/a5b007eb017d49a79f38317ac68b2d10

这篇文章中提到的技巧很多
http://rongjih.blog.163.com/blog/static/335744612010112562833316/
http://rongjih.blog.163.com/blog/static/335744612010112562833316/
http://rongjih.blog.163.com/blog/static/335744612010112562833316/
