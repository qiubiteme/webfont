# 建立超链接

超链接非常重要 ——它们使互联网成为一个互联的网络。本文介绍了创建链接所需的语法，并且讨论了链接的最佳实现方法。

| 前提: | 熟悉基本HTML（包含在 [Getting started with HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)中），HTML 文本格式（包含在 [HTML text fundamentals](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals) 中）。 |
| :--- | :--- |
| 目标: | 学习如何实现一个有效地把多个文件链接在一起的超文本链接。 |

### 什么是超链接?[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E4%BB%80%E4%B9%88%E6%98%AF%E8%B6%85%E9%93%BE%E6%8E%A5) <a id="&#x4EC0;&#x4E48;&#x662F;&#x8D85;&#x94FE;&#x63A5;"></a>

超链接是互联网提供的最令人兴奋的创新之一，它们从一开始就一直是互联网的一个功能，使互联网成为互联的网络。超链接使我们能够将我们的文档链接到任何其他文档（或其他资源），也可以链接到文档的指定部分，我们可以在一个简单的网址上提供应用程序（与必须先安装的本地应用程序或其他东西相比）。几乎任何网络内容都可以转换为链接，点击（或激活）超链接将使网络浏览器转到另一个网址（[URL](https://developer.mozilla.org/en-US/docs/Glossary/URL)）。

注意：URL可以指向HTML文件、文本文件、图像、文本文档、视频和音频文件以及可以在网络上保存的任何其他内容。 如果浏览器不知道如何显示或处理文件，它会询问您是否要打开文件（需要选择合适的本地应用来打开或处理文件）或下载文件（以后处理它）。

例如，BBC 主页包含大量的链接，不仅指向多个新闻故事，而且指向网站的不同区域（导航功能），登录/注册页面（用户工具）等等。

![frontpage of bbc.co.uk, showing many news items, and navigation menu functionality](https://mdn.mozillademos.org/files/12405/bbc-homepage.png)

### 链接的解析[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E9%93%BE%E6%8E%A5%E7%9A%84%E8%A7%A3%E6%9E%90) <a id="&#x94FE;&#x63A5;&#x7684;&#x89E3;&#x6790;"></a>

通过将文本（或其他内容，见[块级链接](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E5%9D%97%E7%BA%A7%E9%93%BE%E6%8E%A5)\)转换为[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)元素内的链接来创建基本链接， 给它一个[`href`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a#attr-href)属性（也称为目标），它将包含您希望链接指向的网址。

```text
<p>I'm creating a link to
<a href="https://www.mozilla.org/en-US/">the Mozilla homepage</a>.
</p>
```

结果如下所示：  
I'm creating a link to [the Mozilla homepage](https://www.mozilla.org/en-US/).

#### 使用title属性添加支持信息[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E4%BD%BF%E7%94%A8title%E5%B1%9E%E6%80%A7%E6%B7%BB%E5%8A%A0%E6%94%AF%E6%8C%81%E4%BF%A1%E6%81%AF) <a id="&#x4F7F;&#x7528;title&#x5C5E;&#x6027;&#x6DFB;&#x52A0;&#x652F;&#x6301;&#x4FE1;&#x606F;"></a>

您可能要添加到您的链接的另一个属性是标题；这旨在包含关于链接的补充有用信息，例如页面包含什么样的信息或需要注意的事情。 例如：

```text
<p>I'm creating a link to
<a href="https://www.mozilla.org/en-US/"
   title="The best place to find more information about Mozilla's
          mission and how to contribute">the Mozilla homepage</a>.
</p>
```

结果如下（当链接悬停在其上时，标题将作为工具提示出现）：  
  
I'm creating a link to [the Mozilla homepage](https://www.mozilla.org/en-US/).

注意：连接的标题仅当鼠标悬停在其上时才会显示，这意味着使用键盘来导航网页的人很难获取到标题信息。如果标题信息对于页面非常重要，你应该使用所有用户能都方便获取的方式来呈现，例如放在常规文本中。

#### 主动学习：创建您自己的示例链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E5%88%9B%E5%BB%BA%E6%82%A8%E8%87%AA%E5%B7%B1%E7%9A%84%E7%A4%BA%E4%BE%8B%E9%93%BE%E6%8E%A5) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x521B;&#x5EFA;&#x60A8;&#x81EA;&#x5DF1;&#x7684;&#x793A;&#x4F8B;&#x94FE;&#x63A5;"></a>

主动学习时间：我们希望您使用本地代码编辑器创建一个HTML文档（我们的 [getting started template](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/getting-started/index.html)会很好）

* 在HTML内，尝试添加一个或者多个段落或其他你知道类型的内容。
* 将某些内容转换为链接。
* 包含标题属性。

#### 块级链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E5%9D%97%E7%BA%A7%E9%93%BE%E6%8E%A5) <a id="&#x5757;&#x7EA7;&#x94FE;&#x63A5;"></a>

如上所述，你可以将一些内容转换为链接，甚至是 [块级元素](https://developer.mozilla.org/en-US/Learn/HTML/Introduction_to_HTML/Getting_started#Block_versus_inline_elements)。如果你想要将一个图像转换为链接，你只需把图像放到`<a></a>`标签中间。

```text
<a href="https://www.mozilla.org/en-US/">
  <img src="mozilla-image.png" alt="mozilla logo that links to the mozilla homepage">
</a>
```

**注意**: 你会在未来的文章中发现更多在Web中使用图像的例子。

### 统一资源定位器\(URL\)与路径\(path\)快速入门[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E7%BB%9F%E4%B8%80%E8%B5%84%E6%BA%90%E5%AE%9A%E4%BD%8D%E5%99%A8%28URL%29%E4%B8%8E%E8%B7%AF%E5%BE%84%28path%29%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8) <a id="&#x7EDF;&#x4E00;&#x8D44;&#x6E90;&#x5B9A;&#x4F4D;&#x5668;(URL)&#x4E0E;&#x8DEF;&#x5F84;(path)&#x5FEB;&#x901F;&#x5165;&#x95E8;"></a>

要全面地了解链接目标，你需要了解统一资源定位器和文件路径。本小节将介绍相关的信息。

统一资源定位器（英文：**U**niform **R**esource **L**ocator，简写：URL）是一个定义了在网络上的位置的一个文本字符串。例如Mozilla的英文主页定位在`https://www.mozilla.org/en-US/`.

URL使用路径查找文件。路径指定文件系统中您感兴趣的文件所在的位置。看一下一个简单的目录结构的例子 \(see the [creating-hyperlinks](https://github.com/mdn/learning-area/tree/master/html/introduction-to-html/creating-hyperlinks) directory.\)

![A simple directory structure. The parent directory is called creating-hyperlinks and contains two files called index.html and contacts.html, and two directories called projects and pdfs, which contain an index.html and a project-brief.pdf file, respectively](https://mdn.mozillademos.org/files/12409/simple-directory.png)

此目录结构的根目录称为`creation-hyperlinks`。当在网站上工作时， 你会有一个包含整个网站的目录。在根目录，我们有一个`index.html`和一个`contacts.html`文件。在真实的网站上，`index.html` 将会成为我们的主页或登录页面。

我们的根目录还有两个目录—— `pdfs` 和`projects`，它们分别包含一个 PDF \(`project-brief.pdf`\) 文件和一个`index.html` 文件。请注意你可以有两个`index.html`文件，前提是他们在不同的目录下，许多网站就是如此。第二个`index.html`或许是项目相关信息的主登录界面。

* **指向相同目录：**如果`index.html`（顶层的`index.html`）想要包含一个超链接指向`contacts.html`，你只需要指定想要链接的文件名，因为它与当前文件是在同一个目录的. 所以你应该使用的URL是`contacts.html`:

  ```text
  <p>Want to contact a specific staff member?
  Find details on our <a href="contacts.html">contacts page</a>.</p>
  ```

* **指向子目录：**如果你想要包含一个超链接到`index.html` （顶层`index.html`\)）指向 `projects/index.html`，您需要进入项目目录，然后指明要链接到的文件。 通过指定目录的名称，然后是正斜杠，然后是文件的名称。因此您要使用的URL是`projects / index.html`：

  ```text
  <p>Visit my <a href="projects/index.html">project homepage</a>.</p>
  ```

* **指向上级目录：** 如果你想在`projects/index.html`中包含一个指向`pdfs/project-brief.pdf`的超链接，你必须返回上级目录，然后再回到`pdf`目录。“返回上一个目录级”使用两个英文点号表示 — `..` — 所以你应该使用的URL是 `../pdfs/project-brief.pdf`：

  ```text
  <p>A link to my <a href="../pdfs/project-brief.pdf">project brief</a>.</p>
  ```

注意：如果需要的话，你可以将这些功能的多个例子和复杂的url结合起来。例如：`../../../complex/path/to/my/file.html`.

#### 文档片段[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E6%96%87%E6%A1%A3%E7%89%87%E6%AE%B5) <a id="&#x6587;&#x6863;&#x7247;&#x6BB5;"></a>

超链接可以链接到html文档的特定部分（被称为**文档片段**），而不仅仅是文件的顶部。要做到这一点你必须首先分配一个[`id`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-id)属性的元素到链接。通常链接到一个特定的标题是有意义的，所以这看起来像下面的内容：

```text
<h2 id="Mailing_address">Mailing address</h2>
```

然后链接到那个特定的`id`，您可以在URL的结尾包含它，前面是一个井号（\#），例如：

```text
<p>Want to write us a letter? Use our <a href="contacts.html#Mailing_address">mailing address</a>.</p>
```

你甚至可以用它自己的文档片段参考链接到同一份文件的另一部分：

```text
<p>The <a href="#Mailing_address">company mailing address</a> can be found at the bottom of this page.</p>
```

#### 绝对链接和相对链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E7%BB%9D%E5%AF%B9%E9%93%BE%E6%8E%A5%E5%92%8C%E7%9B%B8%E5%AF%B9%E9%93%BE%E6%8E%A5) <a id="&#x7EDD;&#x5BF9;&#x94FE;&#x63A5;&#x548C;&#x76F8;&#x5BF9;&#x94FE;&#x63A5;"></a>

你在网络上遇到的两个术语是绝对URL和相对URL：

绝对URL： 指向由其在Web上的绝对位置定义的位置，包括 [协议](https://developer.mozilla.org/zh-CN/docs/Glossary/%E5%8D%8F%E8%AE%AE) and [域名](https://developer.mozilla.org/zh-CN/docs/Glossary/%E5%9F%9F%E5%90%8D). 像下面的例子,如果`index.html` 页面上传到`projects`这一个目录 。`project`位于web服务站点的根目录, web站点的域名为`http://www.example.com`, 这个页面可以通过`http://www.example.com/projects/index.html`访问 \( 或者仅仅通过`http://www.example.com/projects/`来访问, 因为大多数web服务通过访问`index.html`这样的页面来加载，如果没有特定的URL的话\)

绝对URL总是指向相同的位置，不管它在哪里使用。

相对URL： 指向与您链接的文件相关的位置，更像我们在前面一节中所看到的位置。例如，如果我们想从示例文件链接`http://www.example.com/projects/index.html`转到相同目录下的一个PDF文件, URL就是文件名URL — 例如 `project-brief.pdf` —没有其他的信息要求. 如果PDF文件能够在`projects`的子目录`pdfs`中访问到, 相对路径就是`pdfs/project-brief.pdf` \(对应的绝对URL就是 `http://www.example.com/projects/pdfs/project-brief.pdf`.\)

一个相对URL将指向不同的位置，这取决于它所在的文件所在的位置——例如，如果我们把`index.html` 文件 从 `projects` 目录移动出来并进入Web站点的根目录（最高级别，而不是任何目录中），  `pdfs/project-brief.pdf` 的相对URL将会指向`http://www.example.com/pdfs/project-brief.pdf`, 而不是`http://www.example.com/projects/pdfs/project-brief.pdf`.

### 链接最佳实践[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E9%93%BE%E6%8E%A5%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5) <a id="&#x94FE;&#x63A5;&#x6700;&#x4F73;&#x5B9E;&#x8DF5;"></a>

在写链接时有一些最好的做法。现在让我们看看这些。

* 
#### 用清晰的链接措辞[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E7%94%A8%E6%B8%85%E6%99%B0%E7%9A%84%E9%93%BE%E6%8E%A5%E6%8E%AA%E8%BE%9E) <a id="&#x7528;&#x6E05;&#x6670;&#x7684;&#x94FE;&#x63A5;&#x63AA;&#x8F9E;"></a>

把链接放在你的页面上很容易。这还不够。我们需要让所有的读者都可以使用链接，不管他们当前的环境和哪些工具。例如：

* 使用屏幕阅读器的用户喜欢从页面上的一个链接跳到另一个链接，并且脱离上下文来阅读链接。
* 搜索引擎使用链接文本为索引目标文件所以，在链接文本中包含关键词是一个很好的主意，以有效地描述与之相关的信息。
* 读者往往会浏览页面而不是阅读每一个字，他们的眼睛会被页面的特征所吸引，比如链接。他们会找到描述性的链接。

让我们来看一个具体的例子：

_**好**链接文本:_ [Download Firefox](https://firefox.com/)

```text
<p><a href="https://firefox.com/">
  Download Firefox
</a></p>
```

_**坏**链接文本:_ [Click here](https://firefox.com/) to download Firefox

```text
<p><a href="https://firefox.com/">
  Click here
</a>
to download Firefox</p>
```

其他提示：

* 不要重复URL作为链接文本的一部分 — URL看起来很丑，当屏幕朗读器一个字母一个字母的读出来的时候听起来就更丑了。
* 不要在链接文本中说“link”或“links to”——它只是噪音。屏幕阅读器告诉人们有一个链接。可视化用户也会知道有一个链接，因为链接通常是用不同的颜色设计的，并且存在下划线（这个惯例一般不应该被打破，因为用户习惯了它。）
* 保持你的链接标签尽可能短-长链接尤其惹恼屏幕阅读器用户，他们必须听到整件事读出来。

#### 尽可能使用相对链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E5%B0%BD%E5%8F%AF%E8%83%BD%E4%BD%BF%E7%94%A8%E7%9B%B8%E5%AF%B9%E9%93%BE%E6%8E%A5) <a id="&#x5C3D;&#x53EF;&#x80FD;&#x4F7F;&#x7528;&#x76F8;&#x5BF9;&#x94FE;&#x63A5;"></a>

从上面的描述中，您可能认为始终使用绝对链接是一个好主意；毕竟，当页面像相对链接那样移动时，它们不会中断。但是，当链接到同一网站的其他位置时，你应该使用相关链接（当链接到另一个网站时，你需要使用绝对链接）：

* 首先，检查代码要容易得多——相对URL通常比绝对URL短得多，这使得阅读代码更容易。
* 其次，在可能的情况下使用相对URL更有效。当使用绝对URL时，浏览器首先通过查询域名（使用“DNS”）}查找服务器的真实位置，然后再转到该服务器并查找所请求的文件。另一方面，相对URL，浏览器只在同一服务器上查找被请求的文件。因此，如果你使用相对URL做的绝对URL，你就不断地让你的浏览器做额外的工作，这意味着它的效率会降低。

#### 链接到非html资源 ——留下清晰的指示[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E9%93%BE%E6%8E%A5%E5%88%B0%E9%9D%9Ehtml%E8%B5%84%E6%BA%90_%E2%80%94%E2%80%94%E7%95%99%E4%B8%8B%E6%B8%85%E6%99%B0%E7%9A%84%E6%8C%87%E7%A4%BA) <a id="&#x94FE;&#x63A5;&#x5230;&#x975E;html&#x8D44;&#x6E90;_&#x2014;&#x2014;&#x7559;&#x4E0B;&#x6E05;&#x6670;&#x7684;&#x6307;&#x793A;"></a>

当链接到一个需要下载的资源（如PDF或Word文档）或流媒体（如视频或音频）或有另一个潜在的意想不到的效果（打开一个弹出窗口，或加载Flash电影），你应该添加明确的措辞，以减少任何混乱。如下的例子会让人反感：

* 如果你是在低带宽连接，点击一个链接，然后就开始下载大文件。
* 如果你没有安装Flash播放器，点击一个链接，然后突然被带到一个需要Flash的页面。

让我们看看一些例子，看看在这里可以使用什么样的文本：

```text
<p><a href="http://www.example.com/large-report.pdf">
  Download the sales report (PDF, 10MB)
</a></p>

<p><a href="http://www.example.com/video-stream/">
  Watch the video (stream opens in separate tab, HD quality)
</a></p>

<p><a href="http://www.example.com/car-game">
  Play the car game (requires Flash)
</a></p>
```

#### 在下载链接时使用下载属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E5%9C%A8%E4%B8%8B%E8%BD%BD%E9%93%BE%E6%8E%A5%E6%97%B6%E4%BD%BF%E7%94%A8%E4%B8%8B%E8%BD%BD%E5%B1%9E%E6%80%A7) <a id="&#x5728;&#x4E0B;&#x8F7D;&#x94FE;&#x63A5;&#x65F6;&#x4F7F;&#x7528;&#x4E0B;&#x8F7D;&#x5C5E;&#x6027;"></a>

当您链接到要下载的资源而不是在浏览器中打开时，您可以使用下载属性来提供一个默认的保存文件名。下面是一个下载链接到Firefox 的 Windows最新版本的示例：

```text
<a href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=en-US"
   download="firefox-latest-64bit-installer.exe">
  Download Latest Firefox for Windows (64-bit) (English, US)
</a>
```

### 主动学习：创建一个导航菜单[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AA%E5%AF%BC%E8%88%AA%E8%8F%9C%E5%8D%95) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x521B;&#x5EFA;&#x4E00;&#x4E2A;&#x5BFC;&#x822A;&#x83DC;&#x5355;"></a>

在这个练习中，我们希望你把一些页面和导航菜单链接起来，创建一个多页面的网站。这是创建网站的一种常见方式——每一页都使用相同的页面结构，包括相同的导航菜单，所以当链接被点击时，它给人的印象是你停留在同一个地方，不同的内容正在被提出来。

您需要将以下四页的本地副本放在同一目录中。 \(see the [navigation-menu-start](https://github.com/mdn/learning-area/tree/master/html/introduction-to-html/navigation-menu-start)directory if you want a the full listing\):

* [index.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/navigation-menu-start/index.html)
* [projects.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/navigation-menu-start/projects.html)
* [pictures.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/navigation-menu-start/pictures.html)
* [social.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/navigation-menu-start/social.html)

你应该:

1. 在一个页面上的指定位置添加一个无序列表，其中包含要链接到的页面的名称。导航菜单通常只是一个链接列表，因此这在语义上是确定的。
2. 将每个页面名称转换为该页的链接。
3. 将导航菜单复制到每个页面。
4. 在每一页上，只删除同一页的链接——一个页面包含自己的链接是令人困惑和毫无意义的，而缺少链接会对你当前的页面起到很好的视觉提示作用。

最终的例子应该是这样的：

![An example of a simple HTML navigation menu, with home, pictures, projects, and social menu items](https://mdn.mozillademos.org/files/12411/navigation-example.png)

**注意**: 如果你卡住了，或者不确定你是否正确，你可以检查导航菜单上的目录，看看正确的答案。

### 电子邮件链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E7%94%B5%E5%AD%90%E9%82%AE%E4%BB%B6%E9%93%BE%E6%8E%A5) <a id="&#x7535;&#x5B50;&#x90AE;&#x4EF6;&#x94FE;&#x63A5;"></a>

当点击一个链接或按钮时，打开一个新的电子邮件发送信息而不是连接到一个资源或页面，这种情况是可能做到的。这样做是使用[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)元素和`mailto`：URL的方案。  
其最基本和最常用的使用形式为一个`mailto`:link （链接），链接简单说明收件人的电子邮件地址。例如:

```text
<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
```

这会创建一个链接，看起来像这样： [Send email to nowhere](mailto:nowhere@mozilla.org).

实际上，邮件地址甚至是可选的。如果你忘记了（也就是说，你的[`href`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a#attr-href)仅仅只是简单的"`mailto:`"），一个新的发送电子邮件的窗口也会被用户的邮件客户端打开，只是没有收件人的地址信息，这通常在“分享”链接是很有用的，用户可以发送给他们选择的地址邮件

#### 具体细节[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E5%85%B7%E4%BD%93%E7%BB%86%E8%8A%82) <a id="&#x5177;&#x4F53;&#x7EC6;&#x8282;"></a>

除了电子邮件地址，您还可以提供其他信息。事实上，任何标准的邮件头字段可以被添加到邮件的URL你提供。 其中最常用的是主题\(subject\)、抄送\(cc\)和主体\(body\) \(这不是一个真正的头字段，但允许您为新邮件指定一个短内容消息\)。 每个字段及其值被指定为查询项。

下面是一个包含cc、bcc、主题和主体的示例：

```text
<a href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&amp;subject=The%20subject%20of%20the%20email &amp;body=The%20body%20of%20the%20email">
  Send mail with cc, bcc, subject and body
</a>
```

**注意:** 每个字段的值必须是URL编码的。 也就是说，不能有非打印字符（不可见字符比如制表符、换行符、分页符）和空格 [percent-escaped](http://en.wikipedia.org/wiki/Percent-encoding). 同时注意使用问号（`?`）来分隔主URL与参数值，以及使用&符来分隔`mailto:`中的各个参数。 这是标准的URL查询标记方法。阅读 [The GET method](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data#The_GET_method) 以了解哪种URL查询标记方法是更常用的。

这里有一些其他的示例`mailto`链接：

* [mailto:](mailto:)
* [mailto:nowhere@mozilla.org](mailto:nowhere@mozilla.org)
* [mailto:nowhere@mozilla.org,nobody@mozilla.org](mailto:nowhere@mozilla.org,nobody@mozilla.org)
* [mailto:nowhere@mozilla.org?cc=nobody@mozilla.org](mailto:nowhere@mozilla.org?cc=nobody@mozilla.org)
* [mailto:nowhere@mozilla.org?cc=nobody@mozilla.org&subject=This%20is%20the%20subject](mailto:nowhere@mozilla.org?cc=nobody@mozilla.org&subject=This%20is%20the%20subject)

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

这就是链接！当您开始查看样式时，您将在稍后的课程中返回链接。接下来是HTML，我们将返回文本语义，并查看一些更高级/不寻常的功能，您会发现有用的-高级文本格式是您的下一站。

