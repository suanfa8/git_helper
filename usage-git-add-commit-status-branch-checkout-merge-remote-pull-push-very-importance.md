

## 高频命令

### 本地操作

| 命令名称 | 解释 | 示例 |
| --- |:---:| --- |
| git init | 在本地初始化 git 目录 | 在文件夹的根目录下执行 |
| git status | 查看当前工作空间的版本控制状态 | **非常常用且人性化的命令，可以帮助我们学习 Git 的常用操作** |
| git add 文件名 | 将指定文件添加到暂存区 | git add README.md |
| git commit | 将暂存区的文件一次性添加到本地仓库 | git commit -m "fixed #issues1" |

### 分支操作

| 命令名称 | 解释 | 示例 |
| --- |:---:| --- |
| git branch | 查看当前分支 | 不带参数执行 |
| git branch 新分支名 | 基于当前分支创建一个新分支 | git branch develop，注意：新建分支以后并不会将当前分支切换到刚新建的分支 |
| git branch -r | 仅列出远程分支 | 记忆要点：r 表示 remote |
| git branch -a | 仅列出本地分支和远程分支 | 记忆要点：a 表示 all |
| git branch -d 已有分支名 | 删除本地分支 | 记忆要点：d 表示 delete，如果这个分支还未合并， Git 会有相应的提示。即只能删除已经参与了合并的分支，对于未合并的分支是无法删除的。如果想强制删除一个分支，可以使用-D选项 |
| git checkout 本地分支名 | 切换分支 |  |
| git checkout -b 新分支名 <已有分支名> | 基于一个已有的分支创建一个新分支，并将当前分支切换到这个新分支上 |  |
| git merge 分支名 | 将一个已有分支与当前分支合并 |  |
| git rebase -i HEAD~2 ---- 数字2按需修改即可（如果需提交到远端$ git push -f origin master 慎用！） |  |  |

### 远程操作

| 命令名称 | 解释 | 示例 |
| --- |:---:| --- |
| git clone 远程主机url | 从一个远程版本库克隆一个版本库到本地，该命令会在本地主机生成一个目录，与远程主机的版本库同名 | 默认的远程主机名为 origin |
| git remote add 远程主机名 远程主机url | 将本地版本库与一个远程主机上的版本库关联 | 非常常用的命令，在 pull request 流程中经常要添加上游分支，就通过该命令 |
| git pull 远程主机名 远程分支名:本地分支名 | 将远程主机上的指定分支拉取到本地并做合并 | 一般省略冒号及其以后的部分，有可能会产生一个新的提交 |
| git push 远程主机名 本地分支名:远程主机名 | 将本地分支推送到远程主机上的指定分支 | 一般省略冒号及其以后的部分，有可能会先要求你 pull ，再 push |


---

下面是对以上常用命令的解释：

## git status
这是最最常用的命令，查看当前工作空间的文件状态，并且 Git 会给出一些操作提示。

## git init
在一个文件夹的根目录下初始化一个 Git 仓库。

## git add .
把工作空间的所有文件添加到暂存区。

## git commit -m "我是提交说明"
把暂存区的所有文件提交到本地版本库。

## git remote add origin 一个网址
给当前版本库添加一个远程仓库，以后就可以使用 `git push origin master` 推送新版本和 `git pull origin master` 拉取新版本。
相应地，使用 `git remote ` 查看当前版本库的远程仓库别名。
使用 `git remote -v` 查看当前版本库的远程仓库的详细 url 。

![git remote 使用示例](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-20_231903.jpg)

其它关于 git remote 的用法：

git remote -v ：显示所有的远程仓库。
git remote rename origin github ： 将远程仓库名 origin 更改为 github。
git remote rm <远程主机名> ： 删除与远程仓库的连接。

## git branch
### git branch
仅查看当前分支，**该命令非常常用**。

![git branch 使用示例](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-21_002154.jpg)

### git branch -r
仅查看远程分支。

![git branch 使用示例](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-21_002227.jpg)

### git branch -a 
查看所有分支（包括当前分支和远程分支）。

![git branch 使用示例](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-21_002117.jpg)

## git fetch <远程主机名>
取回某个远程主机所有分支（branch）的更新。如果只想取回特定分支的更新，可以指定分支名。

```
git fetch <远程主机名> <分支名>
```

> 所取回的更新，在本地主机上要用“远程主机名/分支名”的形式读取。比如 origin 主机的 master 分支，就要用 `origin/master` 读取。

示例：

![git fetch 使用示例](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-21_102000.jpg)

![git fetch 使用示例](https://github.com/liwei1419/git_helper/raw/master/images/2017-01-21_102100.jpg)


使用场景1：我们经常使用下面的命令**基于一个远程分支创建本地分支**

```
git checkout -b develop origin/develop
```

上面命令表示，在 origin/develop 的基础上，创建一个新分支 develop 。

使用场景2：**在本地分支上合并远程分支**

```
git merge origin/master
```

上面的命令表示，将远程分支 origin/master 合并到当前分支。
补充说明：`git fetch origin master` 和 `git merge origin/master` 加起来等价于 `git pull origin master`。 


## git push
git push 将本地分支的更新推送到远程主机。它的格式是：

```
git push <远程主机名> <本地分支名>:<远程分支名>
```
> 记忆要点：pull 表示推送，从“本地”到“远程”。多数情况，我们省略冒号后面的部分，表示推送本地指定的远程分支到远程仓库，如果该远程分支不存在，则会被创建。

只要记住了上面的完整格式，我们就可以完成删除远程主机上的分支的操作，即：省略本地分支名，表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。

```
git push origin :develop
```

等价于

```
git push origin --delete develop
```

特别注意：1、如果远程主机的版本比本地版本更新，推送时 Git 会报错，要求先在本地做 `git pull` 合并差异，然后再推送到远程主机；
2、`git push` 不会推送标签（tag），除非使用 `--tags` 选项。

## git pull
`git pull` 命令的作用是：取回远程主机的某个分支的更新，再与本地指定的分支合并。
它的完整格式是：

```
git pull <远程主机名> <远程分支名>:<本地分支名>
```

> 记忆要点：pull 表示拉取，从“远程”到“本地”。多数情况，我们省略冒号后面的部分，表示拉取指定的远程分支合并到当前分支。

例如：我们要将远程分支 master 新的提交合并到当前分支（可能是 master ，也可能是 develop），我们可以这样写：

```
git pull origin master
```

事实上，这条命令等价于先 `git fetch origin master` 再 `git merge origin/master`。
