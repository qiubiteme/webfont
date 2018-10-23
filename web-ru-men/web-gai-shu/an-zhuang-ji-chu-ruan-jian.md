# 安装基础软件

在_安装基础软件_中, 我们将向你展示简单网页制作所需要的工具，以及如何正确安装它们。

### 专业人员使用哪些工具？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software#%E4%B8%93%E4%B8%9A%E4%BA%BA%E5%91%98%E4%BD%BF%E7%94%A8%E5%93%AA%E4%BA%9B%E5%B7%A5%E5%85%B7%EF%BC%9F) <a id="&#x4E13;&#x4E1A;&#x4EBA;&#x5458;&#x4F7F;&#x7528;&#x54EA;&#x4E9B;&#x5DE5;&#x5177;&#xFF1F;"></a>

* **计算机，**也许这对你来说是很明显的，但是你们中有些人们是通过手机或者图书馆的计算机来阅读这篇文章的。对于正经的 Web 开发，最好还是使用运行 Windows，Mac，或者 Linux 系统的台式计算机或笔记本电脑。
* **文本编辑器**，用来编写代码。这可以是纯文本编辑器，比如 [Sublime](https://www.sublimetext.com/)，[Brackets](http://brackets.io/)， [Atom](https://atom.io/) 或 [Visual Studio Code](https://code.visualstudio.com/)；也可以是混合的编辑器，如 [Dreamweaver](https://www.adobe.com/products/dreamweaver.html) 或者[WebStorm](https://www.jetbrains.com/webstorm/)。Office 文档编辑器不适合在此使用，因为他们依赖的隐藏元素会干扰浏览器渲染机制。
* **浏览器**，用来测试你的代码。如今使用最多的浏览器有 [Firefox](https://www.mozilla.org/en-US/firefox/new/)，[Chrome](https://www.google.com/chrome/browser/)，[Opera](http://www.opera.com/)， [Safari](https://www.apple.com/safari/)，[Internet Explorer](http://windows.microsoft.com/en-us/internet-explorer/download-ie) 和 [Microsoft Edge](https://www.microsoft.com/en-us/windows/microsoft-edge)。你同时需要在移动设备和任何你的目标用户可能使用的老式浏览器（如 IE 8-10）中测试你的网页表现如何。
* **图像编辑器**，像 [The GIMP](http://www.gimp.org/)，[Paint.NET](http://www.getpaint.net/)，或 [Photoshop](https://www.adobe.com/products/photoshop.html)，用来编辑你的网页所需的图像。
* **版本控制系统**，用来管理服务器文件，支持项目中的团队协作，共享代码与资源，以及避免编辑冲突。当今最流行的版本控制工具是 [Git](http://git-scm.com/)，同时 [GitHub](https://github.com/) 这个基于 Git 的代码托管服务网站也非常流行。 
* **FTP 工具软件**，在旧式使用网络账户管理的服务器上，通常我们使用 FTP 进行文件管理（[Git](http://git-scm.com/) 正在取代 FTP）。有很多 \(S\)FTP 工具软件，比如 [Cyberduck](https://cyberduck.io/)，[Fetch](http://fetchsoftworks.com/)，和 [FileZilla](https://filezilla-project.org/)。
* **自动化构建工具，** 比如 [Grunt](http://gruntjs.com/) 或 [Gulp](http://gulpjs.com/)，来自动完成重复的任务，例如压缩代码和运行测试。
* 模板，库，框架等等，任何用来加快编写常规功能的工具。
* 还有更多工具哟！

### 什么是我现在真正需要的工具？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software#%E4%BB%80%E4%B9%88%E6%98%AF%E6%88%91%E7%8E%B0%E5%9C%A8%E7%9C%9F%E6%AD%A3%E9%9C%80%E8%A6%81%E7%9A%84%E5%B7%A5%E5%85%B7%EF%BC%9F) <a id="&#x4EC0;&#x4E48;&#x662F;&#x6211;&#x73B0;&#x5728;&#x771F;&#x6B63;&#x9700;&#x8981;&#x7684;&#x5DE5;&#x5177;&#xFF1F;"></a>

上面的列表看起来可怕，不过幸运的是你刚接触 Web 开发时并不需要知道上面大部分内容。在这篇文章里，我们只要求你有最小的配备——一个文本编辑器和一些现代的浏览器。

#### 安装文本编辑器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software#%E5%AE%89%E8%A3%85%E6%96%87%E6%9C%AC%E7%BC%96%E8%BE%91%E5%99%A8) <a id="&#x5B89;&#x88C5;&#x6587;&#x672C;&#x7F16;&#x8F91;&#x5668;"></a>

你的电脑上可能已经安装了一个基本的文本编辑器。Windows 上默认安装了 [记事本](https://en.wikipedia.org/wiki/Notepad_%28software%29) 而 macOS 上则有 [TextEdit](https://en.wikipedia.org/wiki/TextEdit)。Linux 发行版众多，其中 Ubuntu 上是默认是 [gedit](https://en.wikipedia.org/wiki/Gedit)。

在Web开发中，你可以使用比记事本和 TextEdit 更好的工具。 我们推荐初学者使用 [Brackets](https://brackets.io/), 它提供了实时预览和代码提示等强大功能，而且免费。（译者_fan19900404_注：我个人更加倾向于使用 [Visual Studio Code](https://code.visualstudio.com/)，完美的原生中文支持，强大的插件体系，多平台支持，它是微软出品，开源免费）

#### 安装现代浏览器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software#%E5%AE%89%E8%A3%85%E7%8E%B0%E4%BB%A3%E6%B5%8F%E8%A7%88%E5%99%A8) <a id="&#x5B89;&#x88C5;&#x73B0;&#x4EE3;&#x6D4F;&#x89C8;&#x5668;"></a>

现在，我们只要安装几个桌面 Web 浏览器来测试我们的代码。在下面选择你的运行系统然后点击相应的链接来下载你最喜爱的浏览器的安装器：

* Linux: [Firefox](https://www.mozilla.org/en-US/firefox/new/)，[Chrome](https://www.google.com/chrome/browser/)，[Opera](http://www.opera.com/)。
* Windows: [Firefox](https://www.mozilla.org/en-US/firefox/new/)，[Chrome](https://www.google.com/chrome/browser/)，[Opera](http://www.opera.com/)，[Internet Explorer](http://windows.microsoft.com/en-us/internet-explorer/download-ie)，[Microsoft Edge](https://www.microsoft.com/en-us/windows/microsoft-edge) （Edge 是 Windows 10 的默认浏览器；如果你的系统版本是 Windows 7 或者更高，你可以安装 Internet Explorer 11；否则你应该安装另外一个浏览器）
* Mac: [Firefox](https://www.mozilla.org/en-US/firefox/new/)，[Chrome](https://www.google.com/chrome/browser/)，[Opera](http://www.opera.com/)，[Safari](https://www.apple.com/safari/) \(Safari 是 iOS 和 macOS 的默认浏览器\)

在继续我们的教程之前，你应该安装好以上至少两个浏览器，并准备用它们来测试你的代码。

#### 安装本地 Web 服务器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software#%E5%AE%89%E8%A3%85%E6%9C%AC%E5%9C%B0_Web_%E6%9C%8D%E5%8A%A1%E5%99%A8) <a id="&#x5B89;&#x88C5;&#x672C;&#x5730;_Web_&#x670D;&#x52A1;&#x5668;"></a>

一些示例需要通过 Web 服务器运行才能正常工作。你可以通过阅读[如何设置本地测试服务器？](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/set_up_a_local_testing_server)了解更多。

