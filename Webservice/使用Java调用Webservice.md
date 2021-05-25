# 如何使用 Java 调用 WebService

## 一、查看接口是否可用

这里使用翻译的 WebService 接口 [www.webxml.com.cn/WebServices/TranslatorWebService.asmx?wsdl](http://www.webxml.com.cn/WebServices/TranslatorWebService.asmx?wsdl)【2021-05-25 可用】

## 二、在 Java 项目某位置打开 powershell，输入命令：`wsimport -keep http://www.webxml.com.cn/WebServices/TranslatorWebService.asmx?wsdl`

输出以下内容则表示成功

![image-20210525095304232](E:\MarkdownFiles\Blogs\Webservice\使用Java调用Webservice.assets\1.png)

如果出现错误，比如下面的错误，则到网页访问该路径，然后**右键另存为 xml 文件**，这里文件名默认为 **TranslatorWebService.xml**

![image-20210525095440180](E:\MarkdownFiles\Blogs\Webservice\使用Java调用Webservice.assets\2.png)

继续使用命令 **`wsimport -keep .\TranslatorWebService.xml`**

![image-20210525101320118](E:\MarkdownFiles\Blogs\Webservice\使用Java调用Webservice.assets\3.png)

然后就可以在当前文件夹下看到生成的域名目录下存放的 **java 和 class 文件**

![image-20210525101533028](E:\MarkdownFiles\Blogs\Webservice\使用Java调用Webservice.assets\4.png)

## 三、测试

测试代码：

```java
// 获取服务
TranslatorWebService translatorWebService = new TranslatorWebService();
// 获取 soap
TranslatorWebServiceSoap translatorWebServiceSoap = translatorWebService.getTranslatorWebServiceSoap();
// 调用方法
String s = translatorWebServiceSoap.helloWebXml();
System.out.println(s);
ArrayOfString hello = translatorWebServiceSoap.getEnCnTwoWayTranslator("你好");
// 获取结果
List<String> string = hello.getString();
System.out.println(string);
```

测试结果：

```shell
Hello! WebXml.com.cn
[你好: [ n&#464 h&#462o ], 1. hello | 
2. how are you |]
```

## 小结：

博主测试时有时会出现超时的情况，初步猜测是请求频率太快的原因。



> **参考：**[WebService调用第三方服务(中英文翻译)_小思的博客-CSDN博客](https://blog.csdn.net/zeal9s/article/details/83060774)