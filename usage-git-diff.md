14）差异查看

直接写 git diff 是查看当前工具区的修改与暂存区的不同，使用 git add 以后，工作区和暂存区是一样的，所以什么都看不到。再在工作区添加一些文字，再使用 git diff 可以看到刚刚添加的文字被比对出来了。

$ git diff --name-status HEAD~2 HEAD~3 <-- 获得两个版本间所有变更的文件列表
$ git diff HEAD HEAD~1 <-- 查看最近两个提交之间的差异
$ git diff HEAD HEAD~2 <-- 查看第1个与第3个提交之间的差异
^ - 代表父提交，^n 表示第n个父提交，^相当于^1 git寻根：^和~的区别 - 分析得很到位
~ - 代表连续的提交，~n相当于连续的第n个提交
$ git diff master..test <-- 比较两个分支之间的差异
$ git diff master...test <-- 比较master、test的共有父分支和 test 分支之间的差异
$ git diff test <-- 比较当前工作目录与 test 分支的差异
$ git diff HEAD <-- 比较当前工作目录与上次提交的差异
$ git diff HEAD -- ./lib  <-- 比较当前工作目录下的lib目录与上次提交的差异
$ git diff --stat  <-- 统计一下有哪些文件被改动，有多少行被改动
$ git diff --cached  <-- 查看下次提交时要提交的内容(staged,添加到索引中)
