# 使用 vue ui 打开可视化界面失败

**原因：**在前几次都正常打开的情况下，这一次突然启动报错：

```xml
Error: spawn vue-cli-service ENOENT
ERROR  Failed to get response from https://registry.yarnpkg.com/vue-cli-version-marker
```

我简直一脸懵逼啊！什么情况，啪的一下，很突然啊！然后网上各种找原因，重装 `npm` 啊，重装 `vue` 啊、修改 `.vuerc` 配置文件啊 ...... 各种试，各种没用。

**解决：**然后在使用命令行启动项目的时候，又啪的一下，很快啊，就报错了，说我的 **语法** 有问题 ?! 我又很懵逼啊，然后就解决了。平平无奇的一次经历！

**总结：**所以还是推荐使用命令行干各种事情，有啥错误直接给你报出来让你改。好了告辞！