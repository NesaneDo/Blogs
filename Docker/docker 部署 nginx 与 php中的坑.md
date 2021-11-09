# docker 部署 nginx 与 php中的坑



1. 最麻烦，耗时最长的：配置 nginx 中 server 节点时，需要将 root 指定为放置网站的路径，如数据卷配置为 

   ```xml
   ./nginx/www:/home/www
   ```

   则 nginx.conf 中

   ```xml
   server{
   	......
   	root /home/www; # 就是指定容器内网站位置，不能使用其他路径，否则要么报 file not found 要么显示不正常
   }
   ```

   

   