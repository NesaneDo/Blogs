# MySQL 格式化日期函数及占位符

MySQL 中有两个函数用于格式化日期：

1. **DATE_FORMAT(date, format)** ：格式化日期，两个参数必填

   ```mysql
   -- e.g.1.
   SELECT DATE_FORMAT(NOW(),'%Y-%m-%d %H:%i:%s');
   -- 2021-01-24 21:28:33
   
   -- e.g.2.
   SELECT DATE_FORMAT(NOW(),'%m-%d-%Y');
   -- 01-24-2021
   ```

   

2. **FROM_UNIXTIME(timestamp,format='%Y-%m-%d %H:%i:%s')**：格式化时间戳，`format` 参数默认为 `'%Y-%m-%d %H:%i:%s'`

   ```mysql
   -- e.g.1.
   SELECT FROM_UNIXTIME(UNIX_TIMESTAMP(NOW()),'%Y-%m-%d %H:%i:%s');
   -- 2021-01-24 21:32:39
   
   -- e.g.2.
   SELECT FROM_UNIXTIME(UNIX_TIMESTAMP(NOW()));
   -- 2021-01-24 21:34:01
   ```

   **扩展：** UNIX_TIMESTAMP(date) 是将日期转成时间戳的函数

**各种占位符：**

| 占位符 | 含义                                           |
| :----- | :--------------------------------------------- |
| %a     | 缩写星期名（Sun-Mon）                          |
| %b     | 缩写月名（Jan-Dec）                            |
| %c     | 月，数值（1-12）                               |
| %D     | 用英文方式表示的天（1st、2nd、3rd、4th...）    |
| %d     | 天，数值（00-21）                              |
| %e     | 同 **%d** ：天，数值（00-21）                  |
| %f     | 微秒                                           |
| %H     | 小时 (00-23)                                   |
| %h     | 小时 (01-12)                                   |
| %I     | 同 **%h** ：小时 (01-12)                       |
| %i     | 分钟，数值(00-59)                              |
| %j     | 年的天 (001-366)                               |
| %k     | 小时 (0-23)                                    |
| %l     | 小时 (1-12)                                    |
| %M     | 英文月名（January-December）                   |
| %m     | 月，数值(00-12)                                |
| %p     | AM 或 PM                                       |
| %r     | 时间，12-小时（hh:mm:ss AM 或 PM）             |
| %S     | 秒(00-59)                                      |
| %s     | 同 **%S** ：秒(00-59)                          |
| %T     | 时间, 24-小时 (hh:mm:ss)                       |
| %U     | 周 (00-53) 星期日是一周的第一天                |
| %u     | 周 (00-53) 星期一是一周的第一天                |
| %V     | 周 (01-53) 星期日是一周的第一天，与 %X 使用    |
| %v     | 周 (01-53) 星期一是一周的第一天，与 %x 使用    |
| %W     | 星期名                                         |
| %w     | 周的天 （0=星期日, 6=星期六）                  |
| %X     | 年，其中的星期日是周的第一天，4 位，与 %V 使用 |
| %x     | 年，其中的星期一是周的第一天，4 位，与 %v 使用 |
| %Y     | 年，4 位                                       |
| %y     | 年，后 2 位                                    |

