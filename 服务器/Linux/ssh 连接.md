# 如何使用 SSH 连接远程服务器（免密连接）

### 一、在服务器上生成公钥和私钥

1. 使用以下命令生成公私钥：会生成 `id_rsa(私钥)` 和 `id_rsa.pub(公钥)`两个文件，步骤上有生成 `.ssh`目录，注意看下路径（一般会在用户的根目录生成），

   ```sh
   ssh-keygen -t rsa
   ```

2. 将 `id_rsa`  重命名为 `authorized_keys`

   ```sh
   mv id_rsa authorized_keys
   ```

3. 修改 `authorized_keys` 权限为 `600`

   ```sh
   chmod 600 authorized_keys
   ```

4. 修改 `.ssh`目录权限为 `700`

   ```sh
   chmod 700 ~/.ssh
   ```



### 二、主机间公私钥的关联

如：现在需要用 **主机1** 去连接 **主机a、主机b、主机c**，则需要将 **主机1** 的 `id_rsa.pub` 上传到 **主机a、主机b、主机c** 上，并将 `id_rsa.pub` 的内容追加到 **主机a、主机b、主机c** 的 `authorized_keys` 中

```sh
cat id_rsa.pub >> authorized_keys
```



### 三、连接

使用如下命令：<> 必填 [] 选填

```sh
ssh -i <私钥路径> [用户名@]<主机名>
如：ssh -i ~/.ssh/id_rsa root@192.168.1.20
```

