# 给 Eclipse 安装 Axis2 Code Generator 插件

## 一、下载相关文件

- [链接： https://axis.apache.org/axis2/java/core/download.html](https://axis.apache.org/axis2/java/core/download.html)

## 二、安装步骤

1. 如果是 p2 版本的 Eclipse`（检查 Eclipse 安装目录有无 dropins 文件夹，若有则为 p2 版本的）`，将下载下来的 zip 文件解压得到的 jar 文件放到 Eclipse 安装目录下的 dropins 中

   ![image-20210712175818168](https://nesanedo.github.io/pics_bed_static/img/picbed/blog/eclipse_install_axis2_plugin/1.png)

2. 重启 Eclipse

## 三、检查是否安装成功

1. **File -> New -> Other** 下是否有 **Axis2 Wizards** 目录**（我这里就没有，请往下看）**

   ![image-20210712180036022](https://nesanedo.github.io/pics_bed_static/img/picbed/blog/eclipse_install_axis2_plugin/2.png)

2. 若没有，则没有安装成功，关闭 Eclipse

3. 使用 **`-console`** 命令启动 Eclipse

   ![image-20210712180317103](E:\MarkdownFiles\Blogs\踩坑\Eclipse\给 Eclipse 安装 Axis2 Code generator 插件.assets\3.png)

4. 出现如下界面

   ![image-20210712180445539](https://nesanedo.github.io/pics_bed_static/img/picbed/blog/eclipse_install_axis2_plugin/4.png)

5. 回车后可以输入命令：**install file:文件路径** `（注意：使用 / 而非 \，否则会报错，\\ 也不行）`

   ![image-20210712180829465](https://nesanedo.github.io/pics_bed_static/img/picbed/blog/eclipse_install_axis2_plugin/5.png)

6. 回车后会出现 **Bundle ID**，使用 **start 这个ID** 命令，如下图：

   ![image-20210712181106861](https://nesanedo.github.io/pics_bed_static/img/picbed/blog/eclipse_install_axis2_plugin/6.png)

7. 回车后再去看 Eclipse 中已经存在 Axis2 Wizards 了

   ![image-20210712181216133](https://nesanedo.github.io/pics_bed_static/img/picbed/blog/eclipse_install_axis2_plugin/7.png)

## 小结：

重新启动后仍然没有，暂时没有找到解决办法。



++++

**原文地址：**

> [Apache Axis2 – Eclipse plugin installation](https://axis.apache.org/axis2/java/core/tools/eclipse/plugin-installation.html)

