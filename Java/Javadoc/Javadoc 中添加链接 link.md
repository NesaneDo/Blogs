# Javadoc 中添加链接 link

1. 使用 **`@see`**

   ```java
   /**
    * 必须顶头写
    * @see java.util.HashMap
    * 如果不顶头就无效 @see java.util.HashMap
    */
   void hashMap();
   ```

   

2. 使用 **`@link`**

   ```java
   /**
    * 可以放在任何地方，用 {} 包起来
    * 顶头
    * {@link java.util.HashMap}
    * 不顶头  {@link java.util.HashMap}
    */
   void hashMap();
   ```

   