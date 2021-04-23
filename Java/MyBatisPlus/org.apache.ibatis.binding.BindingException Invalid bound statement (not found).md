# 出现 org.apache.ibatis.binding.BindingException: Invalid bound statement (not found) 的几种情况

1. **mapper （dao)** 文件与 **xml** 文件没有对应上，即 **xml **文件中的 **namespace **指定不对。如果指定准确，使用 **Mybatis-plus** 插件后，**xml **文件会出现红色小鸟，**mapper （dao）**会出现蓝色小鸟，点击可以在两个文件中切换

2. 配置文件中配置 **entity **或 **xml **的路径不对，参考配置如下，笔者使用 **mybatis-plus**，若是使用 **mybatis**，则把 **mybatis-plus **换成 **mybatis **即可。然后在 **resources **下新建普通文件夹：点击 **New -> Directory**，然后输入 **com/xx/xxx/mapper**，是用 **"/"** 分隔，而不是用 **"."**，从而引出第 3 个情况：

   ```properties
   mybatis-plus.mapper-locations=classpath:/com/xx/xxx/mapper/*.xml
   mybatis-plus.type-aliases-package=com.xx.xxx.entity
   ```

3. **xml **存放位置不对，在 **idea** 中**resources** 下的文件夹，如果设置了折叠空文件夹，则会用 **"." **将各空文件夹折叠起来，但是会出现这种情况，该文件夹不是你自己建的，所以你不知道是用的 **"/"** 还是 **"."**，所以这个文件夹名就有可能是  **com.xx.xxx**，而没有分级