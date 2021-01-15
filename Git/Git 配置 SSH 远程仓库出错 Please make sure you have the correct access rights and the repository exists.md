# Git 配置 SSH 远程仓库出错 Please make sure you have the correct access rights and the repository exists

报错信息是没有访问该仓库的权限，说明 SSH 没有配置正确，解决办法：

1. 重置用户名和邮箱

   - `git config --global user.name <name>`，`name` 是自己设置名字
   - `git config --global user.email <email>`，`email` 是自己的邮箱

2. 删除 `.ssh` 文件夹下的 `known_hosts`文件，若不放心删除，可先备份。`.ssh` 一般在 `C:\Users\电脑名`下

3. 在 `Git Bash`即 `Git`命令行中输入 `ssh-keygen -t rsa -C <email>`，`email` 是第一步中设置的。输入后一路 **`yes`** 或 **`回车`**，完成后会在 `.ssh`文件夹下生成 `id_rsa` 和 `id_rsa.pub` 两个文件（用文本编辑器打开 `id_rsa.pub`并复制里面全部内容），并出现类似如下提示：

   ```properties
   The key's randomart image is:
   +---[RSA 3072]----+
   |+oX=&.. .  . .E.|
   |o*B*.o . = . .o =|
   |o=@=o   .    . ..|
   |oo.=     .       |
   |  .     S .      |
   |   .   . + .     |
   |    . o . .      |
   |     . .         |
   |                 |
   +----[SHA256]-----+
   ```

   

4. 打开 `GitHub`，登录账号，进入设置：添加 SSH key，粘贴复制的内容

5. 在 `Git` 命令行中 输入 `ssh -T git@github.com`，提示输入 `[yes/no]`? 输入 `yes` 即可，完成后会提示：

   ```properties
   Hi xxxxx! You've successfully authenticated, but GitHub does not provide shell access.
   ```

   