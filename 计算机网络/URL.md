# URL

[参考]: https://blog.csdn.net/weixin_53436351/article/details/123833107?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522169674339516800192297243%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&amp;request_id=169674339516800192297243&amp;biz_id=0&amp;utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-123833107-null-null.142^v95^chatgptT3_1&amp;utm_term=URL&amp;spm=1018.2226.3001.4187

## URL是什么

**URL（Uniform Resource Locator, 统一资源定位器）**

统一资源定位系统是专为标识Internet网上资源位置而设置的一种编址方式，平时所说的网页地址指的即是URL。互联网上的每个文件都有一个唯一的URL，它包含的信息指出文件的位置以及浏览器应该怎么处理它。

## URL组成/结构

**协议+域名(IP地址)+资源路径+查询参数**

还可以认为由7部分组成：

- **协议，域名，端口，虚拟目录，文件名，锚，参数**（大多时候端口会选择隐藏）

```
protocol :// hostname[:port] / path / [;parameters][?query]#fragment
[]内为可选项
```

- 协议（HTTP）：规定数据传输的方式。

- 域名（IP）：在网络环境中找到主机-------用 :// 与协议分隔开。

- 端口（port）：（常省略）在网络主机上，标识一个进程（应用程序）------用  :  与域名分隔开。

- 资源路径：标识网络资源（文件，图片，音视频，变量...）------用 :// 与端口分隔开。

- 查询参数：传递给资源路径对应的数据------用  ?  与资源路径分隔开，查询内部参数用  &  分隔多个键值对。

## 示例

**http默认端口80，https默认端口443，默认端口范围0~65535。**

```
https://blog.csdn.net/qq_51556066?type=blog

https协议+CSDN域名+资源路径qq_51556066+查询参数type=blog(key=value)
```

------

```
https://www.baidu.com/

协议：https
域名（IP）：www.baidu.com
端口（port）：443
资源路径：当没有资源路径时，可以默认是  /  ，在各个网站通常有默认的路径如index.html
```

## 注意事项

- URL 只能使用 ASCII 字符集来通过因特网进行发送——只能使用英文字母、阿拉伯数字和某些标点符号，不能使用其他文字和符号 。
- 端口不是一个URL必须的部分，如果省略端口部分，将采用默认端口。文件名部分也不是一个URL必须的部分，如果省略该部分，则使用默认的文件名。
- 一些浏览器和服务器对URL的长度有限制，通常在几千个字符左右。