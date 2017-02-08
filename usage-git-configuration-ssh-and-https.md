
#### 配置 ssh key 的步骤

1. 在本机审查 是啥的公钥和私钥

```
ssh-keygen -t rsa -C "(我的邮箱)"
```

输入完成以后，直接回车（我记得是按三次回车），有遇到要选择的时候，选择 yes。

2. 验证是否配置成功：

```
ssh -T git@github.com
```

如果是 Git@OSC ，请输入 `ssh -T git@git.oschina.net`。


#### 缓存认证信息

```
git config credential.helper cache
```

git bash下用 https 的 clone 方式需要设置

```
git config --global credential.helper store
```

防止每次输入用户名密码。