# Git 配置、提交到多个远程仓库

我知道的有两种方式：

1. 通过命令行`git remote set-url --add <主机名，如 origin> <远程仓库地址>` 添加。如：
   - 添加第一个仓库：`git remote add <主机名，如 origin> <远程仓库地址1>`
   - 添加第二个仓库：`git remote set-url --add <主机名，如 origin> <远程仓库地址2>`
2. 直接编辑配置文件`.git/config`，添加或修改：

```properties
[remote "origin"]
	url=<远程仓库地址1>
	fetch = +refs/heads/*:refs/remotes/origin/*
	url=<远程仓库地址2>
```

**提交方式：通过 `git push <主机名，如 origin> --all`**

****

> 原文地址：https://cloud.tencent.com/developer/article/1572090

### 注意：

当提交到不同的托管平台并且使用 ssh 方式时，需要不同的 public key

1. 生成名称不同的密钥对

2. 在 .ssh 目录下创建 config 文件，内容如下

   ```sh
   # gitee
   Host gitee.com
   HostName gitee.com
   IdentitiesOnly true
   IdentityFile C:/Users/xxx/.ssh/id_rsa_gitee
   
   # github
   Host github.com
   HostName github.com
   IdentitiesOnly true
   IdentityFile C:/Users/xxx/.ssh/id_rsa_github
   ```

   