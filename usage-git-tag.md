

#### 版本(tag)操作相关命令

| 命令名称 | 解释 | 示例 |
| --- |:---:| --- |
| git tag | 查看版本 |  |
| git tag [name] | 创建版本 |  |
| git tag -d [name] | 删除版本 |  |
| git tag -r | 查看远程版本 |  |
| git push origin [name] | 创建远程版本(本地版本push到远程) |  |
| git push origin :refs/tags/[name] | 删除远程版本 |  |
| git pull origin --tags | 合并远程仓库的 tag 到本地 |  |
| git push origin --tags | 上传本地 tag 到远程仓库 |  |
| git tag -a [name] -m 'yourMessage' | 创建带注释的 tag |  |