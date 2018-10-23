# 从对象到iframe - 其他嵌入技术

到目前为止，您应该掌握了将图像、视频和音频嵌入到网页上的诀窍了。此刻，让我们继续深入学习，来看一些能让您在网页中嵌入各种内容类型的元素：  [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe),  [`<embed>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed) 和 [`<object>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/object) 元素。`<iframe>`用于嵌入其他网页，另外两个元素则允许您嵌入PDF，SVG，甚至Flash — 一种正在被淘汰的技术，但您仍然会时不时的看到它。

| 先决条件: | 基本的计算机素养，[安装的基本软件](https://developer.mozilla.org/en-US/Learn/Getting_started_with_the_web/Installing_basic_software)，[使用文件](https://developer.mozilla.org/en-US/Learn/Getting_started_with_the_web/Dealing_with_files)的基本知识，熟悉HTML基础知识（参考HTML [入门](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)）以及本模块中以前的文章。 |
| :--- | :--- |
| 目的: | 要了解如何使用[`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)`、`[`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed)以及[`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)在网页中嵌入部件，例如Flash电影或其他网页。 |

### 嵌入的简史[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF#%E5%B5%8C%E5%85%A5%E7%9A%84%E7%AE%80%E5%8F%B2) <a id="&#x5D4C;&#x5165;&#x7684;&#x7B80;&#x53F2;"></a>

很久以前，很流行在网络上使用**框架**创建网站 — 网站的一小部分存储于单独的HTML页面中。这些被嵌入在一个称为**框架集**的主文档中，它允许您指定每个框架能够填充在屏幕上的区域，而不像调整表格的列和行的大小。这些做法在90年代中期至90年代后期被认为是比较酷的，有证据表明，将网页分解成较小的块，这样有利于下载速度 —值得注意的是当时网络连接速度十分缓慢。然而，这些技术有很多问题，随着网络速度越来越快，这些技术带来的问题远超过它们带来的积极因素，所以你再也看不到它们被使用了。

一小段时间之后（20世纪90年代末，21世纪初），插件技术变得非常受欢迎，例如[Java Applet](https://developer.mozilla.org/en-US/docs/Glossary/Java)和[Flash](https://developer.mozilla.org/en-US/docs/Glossary/Adobe_Flash) — 这些技术允许网络开发者将丰富的内容嵌入到网页中，例如视频和动画等，这些内容不能通过HTML单独实现。嵌入这些技术是通过诸如[`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)和较少使用[`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed)的元素来实现的，当时它们非常有用。由于许多问题，包括可访问性、安全性、文件大小等，它们已经过时了; 如今，大多数移动设备不再支持这些插件，桌面端也逐渐不再支持。

最后，[`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)元素出现了（连同其他嵌入内容的方式，如[`<canvas>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas)，[`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)等），它提供了一种将整个web页嵌入到另一个网页的方法，看起来就像那个web页是另一个网页的一个[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)或其他元素一样。 [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe)现在经常被使用。

了解完历史之后，让我们继续往下看以了解如何使用它们。

### 自主学习：嵌入类型的使用[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF#%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0%EF%BC%9A%E5%B5%8C%E5%85%A5%E7%B1%BB%E5%9E%8B%E7%9A%84%E4%BD%BF%E7%94%A8) <a id="&#x81EA;&#x4E3B;&#x5B66;&#x4E60;&#xFF1A;&#x5D4C;&#x5165;&#x7C7B;&#x578B;&#x7684;&#x4F7F;&#x7528;"></a>

在这篇文章中，我们将直接进入自主学习部分，让你立即体会到嵌入技术的实用性。大家都非常熟悉[Youtube](https://www.youtube.com/)，但很多人不了解它所提供的一些分享功能。让我们来看看Youtube如何让我们通过[`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)在页面中嵌入喜欢的视频。

1. 首先，去Youtube找一个喜欢的视频。
2. 在视频下方，您会看到一个_共享_按钮 - 点击查看共享选项。
3. 选择“ _嵌入”_选项卡，您将得到一些`<iframe>`代码 - 复制一下。
4. 粘贴到下面的_输入_框里，看看_输出_结果是什么。

此外，您还可以试试在示例中嵌入[Google地图](https://www.google.com/maps/)：

1. 去Google地图找一个喜欢的地图。
2. 点击UI左上角的“汉堡菜单”（三条水平线）。
3. 选择_共享或嵌入地图_选项。
4. 选择嵌入地图选项，这将给你一些`<iframe>`代码 - 复制一下。
5. 粘贴到下面的_输入_框，看看_输出_结果是什么。

如果你犯了某些错误，你可以点击_Reset按钮以重置编辑器。_如果你确实被卡住了， 按下Show _solution按钮以借鉴答案。_

在 CodePen 中打开在 JSFiddle 中打开

### Iframe详解[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF#Iframe%E8%AF%A6%E8%A7%A3) <a id="Iframe&#x8BE6;&#x89E3;"></a>

是不是很简单又有趣呢？[`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)元素旨在允许您将其他Web文档嵌入到当前文档中。这很适合将第三方内容纳入您的网站，您可能无法直接控制，也不希望实现自己的版本 - 例如来自在线视频提供商的视频，[Disqus](https://disqus.com/)等评论系统，在线地图提供商，广告横幅等。您通过本课程使用的实时可编辑示例就是使用`<iframe>` 实现的。

我们会在后面提到，关于`<iframe>`有一些严重的[安全隐患](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF#%E5%AE%89%E5%85%A8%E9%9A%90%E6%82%A3)需要考虑，但这并不意味着你不应该在你的网站上使用它们 — 它只需要一些知识和仔细地思考。让我们更详细地探索这些代码。假设您想在其中一个网页上加入MDN词汇表，您可以尝试以下方式：

```text
<iframe src="https://developer.mozilla.org/en-US/docs/Glossary"
        width="100%" height="500" frameborder="0"
        allowfullscreen sandbox>
  <p> <a href="https://developer.mozilla.org/en-US/docs/Glossary">
    Fallback link for browsers that don't support iframes
  </a> </p>
</iframe>
```

此示例包括使用以下所需的`<iframe>`基本要素：[`allowfullscreen`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-allowfullscreen)如果设置，`<iframe>`则可以通过[全屏API](https://developer.mozilla.org/en-US/docs/Web/Apps/Fundamentals/User_notifications/Full_screen_api)设置为全屏模式（稍微超出本文的范围）。[`frameborder`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-frameborder)如果设置为1，则会告诉浏览器在此框架和其他框架之间绘制边框，这是默认行为。0删除边框。不推荐这样设置，因为在[CSS中](https://developer.mozilla.org/en-US/docs/Glossary/CSS)可以更好地实现相同的效果。[`border`](https://developer.mozilla.org/en-US/docs/Web/CSS/border)`: none;`[`src`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-src)该属性与[`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)/[`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)一样包含指向要嵌入文档的URL路径。[`width`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-width) 和 [`height`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-height)这些属性指定您想要的iframe的宽度和高度。备选内容与[`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)等其他类似元素相同，您可以在`<iframe></iframe>`标签之间包含备选内容，如果浏览器不支持`<iframe>`，将会显示备选内容，这种情况下，我们已经添加了一个到该页面的链接。现在您几乎不可能遇到任何不支持`<iframe>`的浏览器。[`sandbox`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-sandbox)该属性需要在已经支持其他`<iframe>`功能（例如IE 10及更高版本）但稍微更现代的浏览器上才能工作，该属性可以提高安全性设置; 我们将在下一节中更加详细地谈到。

**注意**：为了提高速度，在主内容完成加载后，使用JavaScript设置iframe的`src`属性是个好主意。这使您的页面可以更快地被使用，并减少您的官方页面加载时间（重要的[SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO)指标）。

#### 安全隐患[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF#%E5%AE%89%E5%85%A8%E9%9A%90%E6%82%A3) <a id="&#x5B89;&#x5168;&#x9690;&#x60A3;"></a>

以上我们提到了安全问题 - 现在我们来详细介绍一下这一点。我们并不期望您第一次就能完全理解所有内容; 我们只想让您意识到这一问题，在您更有经验并开始考虑在您的实验和工作中使用`<iframe>`时为你提供参考。此外，没有必要害怕和不使用`<iframe>`—你只需要谨慎一点。继续看下去吧...

浏览器制造商和Web开发人员了解到网络上的坏人（通常被称为**黑客**，或更准确地说是**破解者**），如果他们试图恶意修改您的网页或欺骗人们进行不想做的事情时常通过iframe作为共同目标来攻击（官方术语：**攻击向量**），例如显示用户名和密码等敏感信息。因此，规范工程师和浏览器开发人员已经开发了各种安全机制，使`<iframe>`更加安全，这有些最佳方案值得我们考虑 - 我们将在下面介绍其中的一些。

[单击劫持](https://en.wikipedia.org/wiki/Clickjacking)是一种常见的iframe攻击，黑客将隐藏的iframe嵌入到您的文档中（或将您的文档嵌入到他们自己的恶意网站），并使用它来捕获用户的交互。这是误导用户或窃取敏感数据的常见方式。

一个快速的例子 — 尝试在浏览器中加载上面的例子 - 你也可以[在Github上找到它](http://mdn.github.io/learning-area/html/multimedia-and-embedding/other-embedding-technologies/iframe-detail.html)（[参见源代码](https://github.com/mdn/learning-area/blob/gh-pages/html/multimedia-and-embedding/other-embedding-technologies/iframe-detail.html)）。你将不会看到任何内容，但如果你点击[浏览器开发者工具](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools)中的_控制台_，你会看到一条消息，告诉你为什么没有显示内容。在Firefox中，您会_被告知：“X-Frame-Options拒绝加载https://developer.mozilla.org/en-US/docs/Glossary”_。这是因为构建MDN的开发人员已经在网站页面的服务器上设置了一个不允许被嵌入到`<iframe>`的设置（请参阅[配置CSP指令](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#%E9%85%8D%E7%BD%AECSP%E6%8C%87%E4%BB%A4)）这是有必要的 — 整个MDN页面被嵌入在其他页面中没有多大意义，除非您想要将其嵌入到您的网站上并将其声称为自己的内容，或尝试通过单击劫持来窃取数据，这都是非常糟糕的事情。此外，如果每个人都这样做，所有额外的带宽将花费Mozilla很多资金。

**只有在必要时嵌入**

有时嵌入第三方内容（例如YouTube视频和地图）是有意义的，但如果您只在完全需要时嵌入第三方内容，您可以省去很多麻烦。网络安全的一个很好的经验法则是_“你怎么谨慎都不为过，如果你决定要做这件事，多检查一遍；如果是别人做的，在被证明是安全的之前，都假设这是危险的。”_

除了安全问题，你还应该意识到知识产权问题。无论在线内容还是离线内容，绝大部分内容都是有版权的，甚至是一些你没想到有版权的内容（例如，[Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page)上的大多数图片）。不要在网页上展示一些不属于你的内容，除非你是所有者或所有者给了你明确的、书面的许可。对于侵犯版权的惩罚是严厉的。再说一次，你再小心也不为过。

如果内容获得许可，你必须遵守许可条款。例如，MDN上的内容是[在CC-BY-SA下许可的](https://developer.mozilla.org/zh-CN/docs/MDN/About#%E7%89%88%E6%9D%83%E5%92%8C%E8%AE%B8%E5%8F%AF)，这意味着，如果你要引用我们的内容，就必须[用适当的方式注明来源](https://wiki.creativecommons.org/wiki/Best_practices_for_attribution)，即使你对内容做了实质性的修改。

**使用 HTTPS**

[HTTPS](https://developer.mozilla.org/en-US/docs/Glossary/HTTPS)是[HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP)的加密版本。您应该尽可能使用HTTPS为您的网站提供服务：

1. HTTPS减少了远程内容在传输过程中被篡改的机会，
2. HTTPS防止嵌入式内容访问您的父文档中的内容，反之亦然。

使用HTTPS需要一个安全证书，这可能是昂贵的（尽管[Let's Encrypt](https://letsencrypt.org/)让这件事变得更容易），如果你没有，可以使用HTTP来为你的父文档提供服务。但是，由于HTTPS的第二个好处，_无论成本如何，您绝对不能使用HTTP嵌入第三方内容_（在最好的情况下，您的用户的Web浏览器会给他们一个可怕的警告）。所有有声望的公司，例如Google Maps或Youtube，当您嵌入内容时，`<iframe>`将通过HTTPS提供 - 查看`<iframe>` `src`属性内的URL。

**注意**：[Github页面](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Using_Github_pages)允许默认情况下通过HTTPS提供内容，因此对托管内容很有用。如果您正在使用不同的托管，并且不确定，请向您的托管服务商询问。

**始终使用sandbox属性**

你想给攻击者尽可能少的机会在你的网站上做坏事，那么你应该只给嵌入式内容_工作所需的权限。_当然，这也适用于你自己的内容。一个代码可以适当使用或用于测试的容器，但不能对其他代码库（意外或恶意）造成任何损害称为[沙盒](https://en.wikipedia.org/wiki/Sandbox_%28computer_security%29)。

未沙盒化\(Unsandboxed\)内容可以做得太多（执行JavaScript，提交表单，弹出窗口等）默认情况下，您应该使用没有参数的`sandbox`属性来强制执行所有可用的限制，如我们前面的示例所示。

如果绝对需要，您可以逐个添加权限（`sandbox=""`属性值内） - 请参阅[`sandbox`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-sandbox)所有可用选项的参考条目。其中重要的一点是，你_永远不_应该同时添加`allow-scripts`和`allow-same-origin`到你的`sandbox`属性中-在这种情况下，嵌入的内容可以绕过，从执行脚本停止网站同源安全策略，并使用JavaScript来关闭完全沙盒。

**注意**：如果攻击者可以直接（外部`iframe`）愚弄人们访问恶意内容，Sandboxing不提供任何保护。如果某些内容有可能是恶意的（例如，用户生成的内容），请将其从不同的[域服务](https://developer.mozilla.org/en-US/docs/Glossary/domain)到您的主要网站。

**配置CSP指令**

[CSP](https://developer.mozilla.org/en-US/docs/Glossary/CSP)代表[**内容安全策略**](https://developer.mozilla.org/en-US/docs/Web/Security/CSP)，它提供[一组HTTP标头](https://developer.mozilla.org/en-US/docs/Web/Security/CSP/CSP_policy_directives)（由web服务器发送时与元数据一起发送的元数据），旨在提高HTML文档的安全性。在`<iframe>`s安全性方面，您可以[_将服务器配置为发送适当的`X-Frame-Options`  标题。_](https://developer.mozilla.org/en-US/docs/Web/HTTP/X-Frame-Options)这样做可以防止其他网站在其网页中嵌入您的内容（这将导致[点击](https://en.wikipedia.org/wiki/clickjacking)和一系列其他攻击），正如我们之前看到的那样，MDN开发人员已经做了这些工作。

**注意**：您可以阅读Frederik Braun的帖子[在X-Frame-Options安全性头上](https://blog.mozilla.org/security/2013/12/12/on-the-x-frame-options-security-header/)来获取有关此主题的更多背景信息。显然，在这篇文章中已经解释得很清楚了。

### &lt;embed&gt;和&lt;object&gt;元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF#%3Cembed%3E%E5%92%8C%3Cobject%3E%E5%85%83%E7%B4%A0) <a id="&lt;embed&gt;&#x548C;&lt;object&gt;&#x5143;&#x7D20;"></a>

[`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed)和[`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)元素的功能不同于[`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)—— 这些元素是用来嵌入多种类型的外部内容的通用嵌入工具，其中包括像Java小程序和Flash，PDF（可在浏览器中显示为一个PDF插件）这样的插件技术，甚至像视频，SVG和图像的内容！

**注意**：**插件**是一种对浏览器原生无法读取的内容提供访问权限的软件。

然而，您不太可能使用这些元素 - Applet几年来一直没有被使用；由于许多原因，Flash不再受欢迎（见下面的[插件案例](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#The_case_against_plugins)）；PDF更倾向于被链接而不是被嵌入；其他内容，如图像和视频都有更优秀、更容易元素来处理。插件和这些嵌入方法真的是一种传统技术，我们提及它们主要是为了以防您在某些情况下遇到问题，比如内部网或企业项目等。

如果您发现自己需要嵌入插件内容，那么您至少需要一些这样的信息：

|  |  [`<embed>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed) |  [`<object>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/object) |
| :--- | :--- | :--- |
| 嵌入内容的[网址](https://developer.mozilla.org/en-US/docs/Glossary/URL) | [`src`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed#attr-src) | [`data`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/object#attr-data) |
| 嵌入内容的_准确_[媒体类型](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type) | [`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed#attr-type) | [`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/object#attr-type) |
| 由插件控制的框的高度和宽度（以CSS像素为单位） | [`height`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed#attr-height) [`width`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed#attr-width) | [`height`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/object#attr-height) [`width`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/object#attr-width) |
| 名称和值，将插件作为参数提供 | 具有这些名称和值的ad hoc属性 | 单标签[`<param>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/param)元素，包含在内`<object>` |
| 独立的HTML内容作为不可用资源的回退 | 不支持（`<noembed>`已过时） | 包含在元素`<object>`之后`<param>` |

**注意**：`<object>`需要`data`属性，`type`属性或两者。如果您同时使用这两个，您也可以使用该[`typemustmatch`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object#attr-typemustmatch)属性（仅在Firefox中实现，在本文中）。`typemustmatch`保持嵌入文件不运行，除非`type`属性提供正确的媒体类型。`typemustmatch`因此，当您嵌入来自不同[来源的](https://developer.mozilla.org/en-US/docs/Glossary/origin)内容（可以防止攻击者通过插件运行任意脚本）时，可以赋予重要的安全优势。

下面是一个使用该[`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed)元素嵌入Flash影片的示例（请参阅此处的[Github](http://mdn.github.io/learning-area/html/multimedia-and-embedding/other-embedding-technologies/embed-flash.html)，并[检查源代码](https://github.com/mdn/learning-area/blob/gh-pages/html/multimedia-and-embedding/other-embedding-technologies/embed-flash.html)）：

```text
<embed src="whoosh.swf" quality="medium"
       bgcolor="#ffffff" width="550" height="400"
       name="whoosh" align="middle" allowScriptAccess="sameDomain"
       allowFullScreen="false" type="application/x-shockwave-flash"
       pluginspage="http://www.macromedia.com/go/getflashplayer">
```

很可怕，不是吗 。Adobe Flash工具生成的HTML往往更糟糕，使用嵌入`<object>`元素的`<embed>`元素来覆盖所有的基础（查看一个例子）。甚至有一段时间，Flash被成功地用作HTML5视频的备用内容，但是这种情况越来越被认为是不必要的。

现在来看一个`<object>`将PDF嵌入一个页面的例子（参见[实例](http://mdn.github.io/learning-area/html/multimedia-and-embedding/other-embedding-technologies/object-pdf.html)和[源代码](https://github.com/mdn/learning-area/blob/gh-pages/html/multimedia-and-embedding/other-embedding-technologies/object-pdf.html)）：

```text
<object data="mypdf.pdf" type="application/pdf"
        width="800" height="1200" typemustmatch>
  <p>You don't have a PDF plugin, but you can <a href="myfile.pdf">download the PDF file.</a></p>
</object>
```

PDF是纸与数据之间重要的阶梯，但它们[在可访问性上有些问题](http://webaim.org/techniques/acrobat/acrobat)[，](http://webaim.org/techniques/acrobat/acrobat)并且可能难以在小屏幕上阅读。它们在一些圈子中仍然受欢迎，我们最好是用链接指向它们，而不是将其嵌入到网页中，以便它们可以在单独的页面上被下载或被阅读。

#### 针对插件的情况[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF#%E9%92%88%E5%AF%B9%E6%8F%92%E4%BB%B6%E7%9A%84%E6%83%85%E5%86%B5) <a id="&#x9488;&#x5BF9;&#x63D2;&#x4EF6;&#x7684;&#x60C5;&#x51B5;"></a>

以前，插件在网络上是不可或缺的。还记得你必须安装Adobe Flash Player才能在线观看电影的日子吗？并且你还会不断地收到关于更新Flash Player和Java运行环境的烦人警报。Web技术已经变得更加强大，那些日子已经结束了。对于大多数应用程序，现在是停止依赖插件传播内容，开始利用Web技术的时候了。

* **扩大你对大家的影响力。**每个人都有一个浏览器，但插件越来越少，特别是在移动用户中。由于Web在很大程度上不需要依赖插件而运行，所以人们宁愿只是去竞争对手的网站而不是安装插件。
* **从Flash和其他插件附带的**[**额外的可访问性问题**](http://webaim.org/techniques/flash/)**中摆脱。**
* **避免额外的安全隐患。**即使经过无数次补丁[，](http://www.cvedetails.com/product/6761/Adobe-Flash-Player.html?vendor_id=53) Adobe Flash也是[非常不安全的](http://www.cvedetails.com/product/6761/Adobe-Flash-Player.html?vendor_id=53)。2015年，Facebook的首席安全官Alex Stamos甚至[要求Adobe停止Flash。](http://www.theverge.com/2015/7/13/8948459/adobe-flash-insecure-says-facebook-cso)

那你该怎么办？如果您需要交互性，HTML和[JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript)可以轻松地为您完成工作，而不需要Java小程序或过时的ActiveX / BHO技术。您可以使用[HTML5视频](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Add_audio_or_video_content_to_a_webpage)来满足媒体需求，矢量图形[SVG](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Add_vector_image_to_a_webpage)，以及复杂图像和动画[画布](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial)。[彼得·埃尔斯特（Peter Elst）几年前已经提到](https://plus.google.com/+PeterElst/posts/P5t4pFhptvp)，对于工作Adobe Flash极少是正确的工具，除了专门的游戏和商业应用。对于ActiveX，即使微软的[Edge](https://developer.mozilla.org/en-US/docs/Glossary/Microsoft_Edge)浏览器也不再支持。

### 概要[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF#%E6%A6%82%E8%A6%81) <a id="&#x6982;&#x8981;"></a>

在Web文档中嵌入其他内容这一主题可以很快变得非常复杂，因此在本文中，我们尝试以一种简单而熟悉的方式来介绍它，这种介绍方式将立即显示出相关性，同时仍暗示了一些涉及更高级功能的技术。刚开始，除了嵌入第三方内容（如地图和视频），您不太可能在网页上使用到嵌入技术。当你变得更有经验时，你可能会开始为他们找到更多的用途。

除了我们在这里讨论的那些外，还有许多涉及嵌入外部内容的技术。我们看到了一些在前面的文章中出现的，如[`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)，[`<audio>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio)和[`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)，但还有其它的有待关注，如  [`<canvas>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas)用于JavaScript生成的2D和3D图形，[`<svg>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg)用于嵌入矢量图形。我们将在此学习模块的下一篇文章中学习[SVG](https://developer.mozilla.org/en-US/docs/Web/SVG)。

