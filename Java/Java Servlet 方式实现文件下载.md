# Java Servlet 方式实现文件下载

使用 Servlet 实现文件下载，6 步完成：

1. 读取文件

2. 获取文件输入流

3. 设置响应方式

4. 获取响应输出流

5. 复制文件输入流到响应输出流

6. 关闭流

   ```java
   // 读取文件
   File file = new File(realPath, fileName);
   // 获取文件输入流
   FileInputStream fileInputStream = new FileInputStream(file);
   // 附件形式下载(重点)
   response.setHeader("content-disposition", "attachment; fileName=" + fileName);
   // 获取响应输出流
   ServletOutputStream outputStream = response.getOutputStream();
   // 文件 copy
   org.apache.commons.io.IOUtils.copy(fileInputStream, outputStream);
   // 关闭流
   org.apache.commons.io.IOUtils.closeQuietly(outputStream);
   org.apache.commons.io.IOUtils.closeQuietly(fileInputStream);
   ```

   ```html
   <!-- 前端用一个 a 标签测试下载文件名为 test.txt 的文件-->
   <a th:href="download?fileName=test.txt">下载</a>
   ```

**可能的疑问：** 

文件怎么获取：通过前端传到后端的文件名，想办法从项目的资源中获取

**注意：** 

流使用完记得关闭