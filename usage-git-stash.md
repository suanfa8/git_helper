### git stash

使用场景：要切换分支，但手上的工作又还没完成，此时不适合执行 git add 、 git commit 操作的时候。

注意事项：不要频繁暂存，尽量不要使得 Git 栈的深度大于 1 。 stash 处理完紧急的事情以后使用 `git stash pop` 命令，马上弹出 Git 栈，以免时间久了以后，还要去管理 Git 栈中的内容，降低工作效率。

1、git stash
备份当前的工作区的内容，从最近的一次提交中读取相关内容，让工作区保证和上次提交的内容一致。同时，将当前的工作区内容保存到 Git 栈中；

2、git stash pop: 从 Git 栈中读取最近一次保存的内容，恢复工作区的相关内容。由于可能存在多个 stash 的内容，所以用栈来管理，pop 会从最近的一个 stash 中读取内容并恢复；

3、git stash list: 显示 Git 栈内的所有备份，可以利用这个列表来决定从那个地方恢复。


stash未提交的更改
正在修改某个bug或者某个特性，又突然被要求展示工作。而现在所做的工作还不足以提交，这个阶段还无法进行展示（不能回到更改之前）。在这种情况下， git stash可以帮到忙了。stash在本质上会取走所有的变更并存储它们以备将来使用。

git stash
检查 stash 列表：

git stash list

想解除 stash 并且恢复未提交的变更，就进行 apply stash

git stash apply

如果只想留有余地进行 apply stash，给 apply 添加特定的标识符：$ git stash apply stash@{0}
