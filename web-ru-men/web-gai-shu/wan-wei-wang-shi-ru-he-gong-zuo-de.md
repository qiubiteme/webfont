# 万维网是如何工作的

这篇文章简单描述了你在计算机或手机上通过浏览器访问网页时发生了什么。

这个理论在短期内对你编写网页代码不会有实质性的帮助，但是不久之后你会真正从中受益。

### 客户端和服务器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/How_the_Web_works#%E5%AE%A2%E6%88%B7%E7%AB%AF%E5%92%8C%E6%9C%8D%E5%8A%A1%E5%99%A8) <a id="&#x5BA2;&#x6237;&#x7AEF;&#x548C;&#x670D;&#x52A1;&#x5668;"></a>

连接到互联网的计算机被称作客户端和服务器。下面是一个简单描述它们如何交互的图表：

![](https://mdn.mozillademos.org/files/8973/Client-server.jpg)

* 客户端是典型的Web用户入网设备（比如，你连接了Wi-Fi的电脑，或接入移动网络的手机）和设备上可联网的软件（通常使用像 Firefox 和 Chrome的浏览器）。
* 服务器是存储网页，站点和应用的计算机。当一个客户端设备想要获取一个网页时，一份网页的拷贝将从服务器上下载到客户端机器上来在用户浏览器上显示。

### 其他部分[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/How_the_Web_works#%E5%85%B6%E4%BB%96%E9%83%A8%E5%88%86) <a id="&#x5176;&#x4ED6;&#x90E8;&#x5206;"></a>

我们讲的客户端和服务器并不能完成全部工作。还有其他必要的部分，我们将在下面讲述。

现在，让我们假设 Web 就是一条路。路的一端是客户端，就像你的家。另一端则是服务器，就像你想去的商店。

![](https://mdn.mozillademos.org/files/9749/road.jpg)

除了客户端和服务器，我们还需要了解：

* **网络连接**: 允许你在互联网上发送和接受数据。基本上和你家到商店的街道差不多。
* **TCP/IP**: 传输控制协议和因特网互连协议是定义数据如何传输的通信协议。这就像你下订单，去商店和买东西时所使用的传输机制。这里就像是一辆汽车或自行车（或是你能想到的其他可能）。
* **DNS**: 域名系统服务器像是一本网站通讯录。当你在浏览器内输入一个网址时，浏览器获取网页之前将会查看域名系统。浏览器需要找到存放你想要的网页的服务器，才能发送 HTTP 请求到正确的地方。就像你要知道商店的地址才能到达那。
* **HTTP**: 超文本传输协议是一个定义客户端和服务器间交流的语言的协议（[protocol](https://developer.mozilla.org/en-US/docs/Glossary/Protocol) ）。就像你下订单时所说的话一样。
* **组成文件**: 一个网页由许多文件组成，就像商店里不同的商品一样。这些文件有两种类型：
  * **代码** : 网页大体由 HTML、CSS、JavaScript组成，不过你会在后面看到不同的技术。
  * **资源** : 这是其他组成网页的东西的集合，比如图像、音乐、视频、Word文档、PDF文件。

### 到底发生了什么？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/How_the_Web_works#%E5%88%B0%E5%BA%95%E5%8F%91%E7%94%9F%E4%BA%86%E4%BB%80%E4%B9%88%EF%BC%9F) <a id="&#x5230;&#x5E95;&#x53D1;&#x751F;&#x4E86;&#x4EC0;&#x4E48;&#xFF1F;"></a>

当你在浏览器里输入一个网址时（在我们的例子里就是走向商店的路上时）：

1. 浏览器在域名系统服务器上找出存放网页的服务器的实际地址（找出商店的位置）。
2. 浏览器发送 HTTP 请求信息到服务器来请拷贝一份网页到客户端（你走到商店并下订单）。这条消息，包括其他所有在客户端和服务器之间传递的数据都是通过互联网使用 TCP/IP 协议传输的。
3. 服务器同意客户端的请求后，会返回一个“200 OK”信息，意味着“你可以查看这个网页，给你～”，然后开始将网页的文件以数据包的形式传输到浏览器（商店给你商品，你将商品带回家）。
4. 浏览器将数据包聚集成完整的网页然后将网页呈现给你（商品到了你的门口 —— 新东西，好棒！）。

### DNS解析[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/How_the_Web_works#DNS%E8%A7%A3%E6%9E%90) <a id="DNS&#x89E3;&#x6790;"></a>

真正的网址看上去并不像你输入的那样美好、容易记忆。它们是一串数字，像 63.245.217.105。

这叫做 IP 地址，它代表了一个互联网上独特的位置。然而，它并不容易记忆，不是吗？那就是域名系统被发明的原因。它们是将你输入浏览器的地址与实际 IP 地址相匹配的特殊的服务器（像 "mozilla.org"）。

网页可以通过  [IP地址](https://developer.mozilla.org/en-US/docs/Glossary/IP_Address)直接访问。试试通过输入 `63.245.217.105` 来访问 Mozilla网站。能准确访问的IP是：63.245.215.20。

![A domain name is just another form of an IP address](https://mdn.mozillademos.org/files/8405/dns-ip.png)

### 数据包解析[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/How_the_Web_works#%E6%95%B0%E6%8D%AE%E5%8C%85%E8%A7%A3%E6%9E%90) <a id="&#x6570;&#x636E;&#x5305;&#x89E3;&#x6790;"></a>

前面我们用“包”来描述了数据从服务器到客户端传输的格式。这是什么意思？基本上，当数据在Web上传输时，是以成千上万的小 数据块 的形式传输的。大量不同的用户都可以在同时下载同一个网页。如果网页以单个大的 数据块 形式传输，一次就只有一个用户下载，无疑会让Web非常没有效率并且失去很多乐趣。

### 扩展阅读[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/How_the_Web_works#%E6%89%A9%E5%B1%95%E9%98%85%E8%AF%BB) <a id="&#x6269;&#x5C55;&#x9605;&#x8BFB;"></a>

* [How the Internet works](https://developer.mozilla.org/zh-CN/docs/learn/How_the_Internet_works)
* [HTTP — an Application-Level Protocol](https://dev.opera.com/articles/http-basic-introduction/)
* [HTTP: Let’s GET It On!](https://dev.opera.com/articles/http-lets-get-it-on/)
* [HTTP: Response Codes](https://dev.opera.com/articles/http-response-codes/)

### 感谢[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/How_the_Web_works#%E6%84%9F%E8%B0%A2) <a id="&#x611F;&#x8C22;"></a>

街景照片 : [Street composing](https://www.flickr.com/photos/kdigga/9110990882/in/photolist-cXrKFs-c1j6hQ-mKrPUT-oRTUK4-7jSQQq-eT7daG-cZEZrh-5xT9L6-bUnkip-9jAbvr-5hVkHn-pMfobT-dm8JuZ-gjwYYM-pREaSM-822JRW-5hhMf9-9RVQNn-bnDMSZ-pL2z3y-k7FRM4-pzd8Y7-822upY-8bFN4Y-kedD87-pzaATg-nrF8ft-5anP2x-mpVky9-ceKc9W-dG75mD-pY62sp-gZmXVZ-7vVJL9-h7r9AQ-gagPYh-jvo5aM-J32rC-ibP2zY-a4JBcH-ndxM5Y-iFHsde-dtJ15p-8nYRgp-93uCB1-o6N5Bh-nBPUny-dNJ66P-9XWmVP-efXhxJ), by [Kevin D](https://www.flickr.com/photos/kdigga/).

