
待添加的内容：
添加 ssh key 。

git diff
git 版本回到过去和回到未来
git stash 
git 撤销只须要知道两个命令：git checkout -- <文件名>，和 git 版本回到过去和回到未来。
git commint --amend 可以合并到上一次提交，但不要在已经推送到远程仓库的版本库中做这个操作。
git rebase 两个作用：1、等价于 git merge 2、改写提交历史，同样不要在已经推送到远程仓库的版本库中做这个操作。



## 其它很有用的命令

### git reset --hard <某个提交 SHA 值>
使用该命令可以在当前分支的不同版本间来回切换。即可以回到过去，也可以回到未来。

![git reset --hard 使用示例](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-21_012508.jpg)

此时我们使用 git log 命令只能查看到当前指定提交到最原始提交的信息，我们看不到当前指定提交以后的提交的 SHA 值，难道我们就不能回到未来吗？此时可以使用

```
git reflog
```

命令，这个命令存储了我们的操作，我们可以通过这个命令找到回到过去之前的提交的 SHA 值。

![git reflog 使用示例](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-21_012520.jpg)




#### 后悔药

删除当前仓库内未受版本管理的文件：$ git clean -f
恢复仓库到上一次的提交状态：$ git reset --hard
回退所有内容到上一个版本：$ git reset HEAD^
回退a.py这个文件的版本到上一个版本：$ git reset HEAD^ a.py
回退到某个版本：$ git reset 057d 
将本地的状态回退到和远程的一样：$ git reset –hard origin/master  
向前回退到第3个版本：$ git reset –soft HEAD~3
修改最后的提交日志：$ git commit --amend
修改最后的提交日期为当前时间：$ git commit --amend  --date="$(date -R)"


#### Git 一键推送多个远程仓库
编辑本地仓库的.git/config文件：
[remote "all"]
    url = git@github.com:dragon/test.git
    url = git@gitcafe.com:dragon/test.git
这样，使用git push all即可一键Push到多个远程仓库中。


#### 追责

查看文件中的每一行的作者、最新的变更提交和提交时间

```
git blame [fileName]
```

IntelliJ IDEA 这个工具对 `git blame` 这个命令有着很好的支持。

![git blame 在 IntelliJ IDEA 工具中的使用](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-22_145400.png)



git log

有三个应该知道的选项。
--oneline - 压缩模式，在每个提交的旁边显示经过精简的提交哈希码和提交信息，以一行显示。
--graph - 图形模式，使用该选项会在输出的左边绘制一张基于文本格式的历史信息表示图。如果你查看的是单个分支的历史记录的话，该选项无效。
--all - 显示所有分支的历史记录


有选择的合并 - 这个功能最赞，没有之一
cherry-pick 可以从不同的分支中捡出一个单独的commit，并把它和你当前的分支合并。如果你以并行方式在处理两个或以上分支，你可能会发现一个在全部分支中都有的bug。如果你在一个分支中解决了它，你可以使用cherry-pick命令把它commit到其它分支上去，而不会弄乱其他的文件或commit。
$ git cherry-pick [commitHash]



12）多次修改后拆分提交 - 暂存文件的部分改动
一般情况下，创建一个基于特性的提交是比较好的做法，意思是每次提交都必须代表一个新特性的产生或者是一个bug的修复。如果你修复了两个bug，或是添加了多个新特性但是却没有提交这些变化会怎样呢？在这种情况下，你可以把这些变化放在一次提交中。但更好的方法是把文件暂存(Stage)然后分别提交。
例如你对一个文件进行了多次修改并且想把他们分别提交。这种情况下，可以在 add 命令中加上 -p 参数
$ git add -p [fileName]

13）压缩多个Commit
用rebase命令把多个commit压缩成一个
git rebase -i HEAD~[number_of_commits]
如果你想要压缩最后两个commit，你需要运行下列命令：
git rebase -i HEAD~2
Docs: 7.6 Git 工具 - 重写历史 、3.6 Git 分支 - 变基

