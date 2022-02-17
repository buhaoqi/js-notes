# Web-related Terms

## Origin
- `origin`,即‘源’，'来源'。
- 在web领域，`origin`是针对Web 内容而言的。
- 一个文档内容的`origin`是由文档的URL的protocol,hostname,port定义的。
- 只有当protocol、hostname和port都匹配时，两个对象才具有相同的`origin`。

示例1：同源

```text
http://example.com/app1/index.html
http://example.com/app2/index.html
```

示例2：同源

```text
http://Example.com:80
http://example.com
```

示例3：不同源

```text
http://example.com/app1
https://example.com/app2

```

示例4：不同源

```text
http://example.com
http://www.example.com
http://myapp.example.com

```

示例5：不同源

```text
http://example.com
http://example.com:8080

```

## Cookie

在用户本地终端上储存的数据。


`Cookie`的原意“小甜饼”的意思。在这里指保存在客户机中的一个文本文件。这个文件是用户在访问某个特定的网页创建的。

`Cookie`的用途有两个：

1. 本地存储：以键值对的形式把数据存储在一个文本文件内。

2. 保持状态

典型应用场景：

1. 记住密码，下次自动登录

2. 购物车功能

3. 记录用户浏览数据，进行商品（广告）推荐

参考文章：
- [Cookies](https://blog.csdn.net/howgod/article/details/88988509?spm=1035.2023.3001.6557&utm_medium=distribute.pc_relevant_bbs_down.none-task-blog-2~default~OPENSEARCH~Rate-19.nonecase&depth_1-utm_source=distribute.pc_relevant_bbs_down.none-task-blog-2~default~OPENSEARCH~Rate-19.nonecase)


Cookie，有时也用其复数形式 Cookies。类型为“小型文本文件”，是某些网站为了辨别用户身份，进行Session跟踪而储存在用户本地终端上的数据（通常经过加密），由用户客户端计算机暂时或永久保存的信息。

举例来说, 一个 Web 站点可能会为每一个访问者产生一个唯一的ID, 然后以 Cookie 文件的形式保存在每个用户的机器上。如果使用浏览器访问 Web, 会看到所有保存在硬盘上的 Cookie。

在这个文件夹里：
- 每一个文件：都是一个由“名/值”对组成的文本文件
- 另外还有一个文件：保存有所有对应的 Web 站点的信息

在这里的每个 Cookie 文件都是一个简单而又普通的文本文件。
透过文件名, 就可以看到是哪个 Web 站点在机器上放置了Cookie(当然站点信息在文件里也有保存)
