# 解决 git 每次都输入账号密码问题

将 http 改为 ssh 方式：

1. 查看远程仓库地址：`git remote -v`
2. 移除 http 方式：`git remote rm <name>` , **`name`**是之前配置的仓库的名称，若没有则是默认的 **`origin`**
3. 重新添加仓库：`git remote add <name> <url>`, **`name`** 是仓库名称，**`url`** 是远程仓库地址，应使用 **`shh `** 方式的 

