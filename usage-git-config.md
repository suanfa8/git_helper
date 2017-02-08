### git config
我们在最开始使用 Git 的时候，使用了 

```
git config --global user.name "我的名字"
```

和 

```
git config --global user.email "我的邮箱"
```

配置全局的名字和邮箱，我们还可以在单个项目里使用

```
git config user.name "我的名字"
```

和 

```
git config user.email "我的邮箱"
```

为某个项目配置指定的名字和邮箱，这样就可以区分个人的项目和公司项目的提交人信息。
设置成功以后 Git 不会有任何提示信息，我们可以使用 `git config user.name` 和 `git config user.email` 来查看这两个信息是否设置正确。

> 另外，使用 `git config` 命令还可以配置命令别名，以解决我们记不住太多复杂参数的问题，特别在 git log 命令的使用中比较常见。
