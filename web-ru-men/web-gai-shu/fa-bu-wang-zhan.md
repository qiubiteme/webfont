# 发布网站



在你已经写好了代码并且整理好了你网站的全部文件后，你需要将它们全部上线，这样别人才能看到。这篇文章将向你展示如何轻松地将你简单的示例代码传到网上。

### 有哪些方法可供选择？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Publishing_your_website#%E6%9C%89%E5%93%AA%E4%BA%9B%E6%96%B9%E6%B3%95%E5%8F%AF%E4%BE%9B%E9%80%89%E6%8B%A9%EF%BC%9F) <a id="&#x6709;&#x54EA;&#x4E9B;&#x65B9;&#x6CD5;&#x53EF;&#x4F9B;&#x9009;&#x62E9;&#xFF1F;"></a>

发布一个网页并不是三言两语就能简单说明的，这主要是因为我们有太多方法去完成它了。在这篇文章里我们并不准备讲述所有方法。 反之我们准备从初学者的视角讨论一下三种常见的方式的利弊，然后带你看看我们将要使用的一种方法。

#### 获取主机服务和域名[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Publishing_your_website#%E8%8E%B7%E5%8F%96%E4%B8%BB%E6%9C%BA%E6%9C%8D%E5%8A%A1%E5%92%8C%E5%9F%9F%E5%90%8D) <a id="&#x83B7;&#x53D6;&#x4E3B;&#x673A;&#x670D;&#x52A1;&#x548C;&#x57DF;&#x540D;"></a>

如果你想要完全控制你发布的网页，那么你将需要花钱购置：

* 主机服务 — 在主机服务提供商的 [Web 服务器](https://developer.mozilla.org/en-US/Learn/What_is_a_web_server)上租用文件空间。将你网站的文件上传到这里，然后服务器会提供 Web 用户需求的内容。
* [域名](https://developer.mozilla.org/en-US/Learn/Understanding_domain_names)——一个可以让人们访问的独一无二的地址，像 `http://www.mozilla.org`，或 `http://www.bbc.co.uk` 。你可以从**域名注册商**租借域名 。

许多专业的网站通过这种方法接入互联网。

此外，你将需要一个 [文件传输协议](https://developer.mozilla.org/en-US/docs/Glossary/FTP) 程序 \( 点击[钻研在网络上做某些事情要花费多少：软件](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/How_much_does_it_cost#%E8%BD%AF%E4%BB%B6)查看详细信息 \) 来将网站文件上传到服务器。不同的 FTP 程序涵盖了不同的范围， 但是你通常需要使用主机服务提供商给你的详细信息（比如用户名、密码、主机名）登录到 Web 服务器 。然后程序在两个窗口里分别显示本地文件和服务器文件，这样你就可以在它们之间进行传输：

![](https://mdn.mozillademos.org/files/9469/ftp.jpg)

**寻找主机服务和域名的建议**

* 我们不会推荐任何商业化的主机公司。要找到主机公司和域名注册商，只需要搜索 "网络主机服务" 和 "域名" 来找到一家出售域名的公司。 所有这种类型的公司都允许你查看你想要的域名是否可用。
* 你的家庭或办公 [网络服务提供商](https://developer.mozilla.org/en-US/docs/Glossary/ISP) 可能会提供一些受限制的的小型主机空间。它们的能使用的功能都会受到限制，但是它们会非常适合你的第一个实验的——联系一下他们！
* 有一些免费服务比如 [Neocities](https://neocities.org/) ， [Blogspot](https://www.blogger.com/) ，和 [Wordpress](https://wordpress.com/) 。重复一遍， 一分钱一分货，不过它们对于你的初次实验可能会是很理想的。 免费服务大部分也不需要 FTP 软件来上传文件 — 你只需要将文件拖入到它们网页的界面里。
* 有时公司会打包提供主机服务和域名。

#### 使用在线工具如 GitHub 或 Google App Engine[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Publishing_your_website#%E4%BD%BF%E7%94%A8%E5%9C%A8%E7%BA%BF%E5%B7%A5%E5%85%B7%E5%A6%82_GitHub_%E6%88%96_Google_App_Engine) <a id="&#x4F7F;&#x7528;&#x5728;&#x7EBF;&#x5DE5;&#x5177;&#x5982;_GitHub_&#x6216;_Google_App_Engine"></a>

有一些工具能使你在线发布网站 :

* [GitHub](https://github.com/) 是一个“社交编程”网站。它允许你上传代码库并储存在 [Git](http://git-scm.com/) 版本控制系统里。 然后你可以协作代码项目，系统是默认开源的，意味着世界上任何人都可以找到你 GitHub 上的代码。去使用 GitHub，从中学习并且提高自己吧！ 你也可以对别人的代码那样做！ 这是一个非常重要、有用的社区，而且 Git/GitHub 是非常流行的 [version control system](http://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) — 大部分科技公司在工作中使用它。 GitHub 有一个非常有用的特点叫 [GitHub pages](https://pages.github.com/)，允许你将网站代码放在网上。
* Google App Engine

不像大部分其它主机服务，这类工具通常是免费的，不过你只能使用有限的功能。

#### 使用像 Thimble 的基于 Web 的集成开发环境[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Publishing_your_website#%E4%BD%BF%E7%94%A8%E5%83%8F_Thimble_%E7%9A%84%E5%9F%BA%E4%BA%8E_Web_%E7%9A%84%E9%9B%86%E6%88%90%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83) <a id="&#x4F7F;&#x7528;&#x50CF;_Thimble_&#x7684;&#x57FA;&#x4E8E;_Web_&#x7684;&#x96C6;&#x6210;&#x5F00;&#x53D1;&#x73AF;&#x5883;"></a>

有许多web应用能够仿真一个网站开发环境，允许你输入 HTML、CSS 和 JavaScript 然后显示代码的结果 —— 全部在一个标签页里！通常这些工具都很简单，对学习很有帮助，而且是免费的（基本功能），它们在一个独特的地址显示你提交的网页。不过，基础功能是很有限的，而且这些应用通常不提供如图像的内容的主机空间。

使用一下以下几种工具，看看你最喜欢哪一个：

* [JSFiddle](https://jsfiddle.net/)
* [Thimble](https://thimble.webmaker.org/)
* [JSBin](http://jsbin.com/)
* [CodePen](https://codepen.io/)

![](https://mdn.mozillademos.org/files/9471/jsbin-screen.png)

### 通过GitHub发布[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Publishing_your_website#%E9%80%9A%E8%BF%87GitHub%E5%8F%91%E5%B8%83) <a id="&#x901A;&#x8FC7;GitHub&#x53D1;&#x5E03;"></a>

现在，让我们通过Github页面告诉你公布的你的代码是如此的简单。

1. 首先， [注册一个GitHub账号，](https://github.com/join) 并确认你的邮箱地址。
2. 接下来，你需要创建一个新的资源库\( repository \)来存放你的文件。
3. 在这个页面上，在 _Repository name_ 输入框里输入  _username_.github.io，username 是你的用户名。比如，我们的朋友 bobsmith 会输入  _bobsmith.github.io。同时勾选_ _Initialize this repository with a README_ ，然后点击 _Create repository_。![](https://mdn.mozillademos.org/files/9479/github-create-repo.png)
4. 然后，将你的网页文件夹拖拽到你的资源库\( repository \)，再点击 _Commit changes_。

   **提示**: 确保你的文件夹有一个 _index.html_ 文件.

5. 现在将你的浏览器转到 _username_.github.io 来在线查看你的网站。比如，_如果用户名为chrisdavidmills_, 请转到 [chrisdavidmills.github.io](http://chrisdavidmills.github.io/)。

   **提示**: 你的网站可能需要几分钟的时间才能投入使用。 如果它不能立即工作，你可能需要等待几分钟，然后再试一次。

想要了解更多，请看 [GitHub Pages Help](https://help.github.com/categories/github-pages-basics/).

### 延展阅读[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Publishing_your_website#%E5%BB%B6%E5%B1%95%E9%98%85%E8%AF%BB) <a id="&#x5EF6;&#x5C55;&#x9605;&#x8BFB;"></a>

* [What is a web server](https://developer.mozilla.org/en-US/Learn/What_is_a_web_server)
* [Understanding domain names](https://developer.mozilla.org/en-US/Learn/Understanding_domain_names)
* [How much does it cost to do something on the web?](https://developer.mozilla.org/en-US/Learn/How_much_does_it_cost)
* [Deploy a Website](https://www.codecademy.com/learn/deploy-a-website)
* [Cheap or free static web hosting](http://alignedleft.com/resources/cheap-web-hosting) by Scott Murray has some useful ideas on available services.



