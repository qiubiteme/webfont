# Mozilla醒目页面



在这个测验中，我们将测试你对于本模块文章所讨论的技术的掌握程度，让你将一些有关于 Mozilla 的图片和视频添加到一个漂亮的页面上！

| 学习本章节的要求: | 在开始这个测验之前，你应该了解了 [Multimedia and embedding](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding) 模块的其他文章. |
| :--- | :--- |
| 目的: | 测试这些知识的掌握程度：在页面中嵌入图片和视频，框架，和 HTML 响应式图片技术。 |

### 起点[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E8%B5%B7%E7%82%B9) <a id="&#x8D77;&#x70B9;"></a>

为了开始这次测验，你需要从[mdn-splash-page-start](https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/mdn-splash-page-start/)这个GitHub目录下下载HTML和图片。在你本地设备上新建一个 `index.html` 文件，并将  [index.html](https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/mdn-splash-page-start/index.html) 的内容复制到进去。 然后把 [pattern.png](https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/mdn-splash-page-start/pattern.png) 保存在同一目录下（右键图片有下载选项）。

访问 [originals](https://github.com/mdn/learning-area/tree/master/html/multimedia-and-embedding/mdn-splash-page-start/originals) 文件夹中不同的图片文件，然后用同样的方法将它们下载到本地。现在，你需要将这些图片文件保存到不同的目录下，因为在这些图片准备好被使用之前，你需要使用图像编辑器来处理这些图片.

**注意**: 这个示例的 HTML 文件包含一些页面的 CSS 样式。你不需要去碰 CSS 的内容，而只是 [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 元素中的 HTML 部分，只要你插入了正确的标记，样式就会正确显示。

### 项目概要[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E9%A1%B9%E7%9B%AE%E6%A6%82%E8%A6%81) <a id="&#x9879;&#x76EE;&#x6982;&#x8981;"></a>

在这个测验中，我们为你呈现了一个接近完成了的 Mozilla醒目页面，旨在说明一些关于Mozilla的有趣的事情，以及提供一些更一步的资源链接。但目前还没有添加任何视频或图片，这份工作就交给你了！你需要添加一些图片、视频等多媒体元素，好让页面变得更漂亮和更有意义。下一小节详细描述了你需要做的工作：

#### 准备图片[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E5%87%86%E5%A4%87%E5%9B%BE%E7%89%87) <a id="&#x51C6;&#x5907;&#x56FE;&#x7247;"></a>

使用你最爱的图片编辑器，创建下面几张图片的 400px 宽的版本和 120px 宽的版本：

* `firefox_logo-only_RGB.png`
* `firefox-addons.jpg`
* `mozilla-dinosaur-head.png`

给它们取个有意义的名字，例如`firefoxlogo400.png` 和`firefoxlogo120.png`。

这些图片将和 `mdn.svg` 一起作为`further-info`区内资源链接的图标和网站页眉的火狐图标。将这些图片副本保存在与 `index.html`文件的同一个目录下。 

接着，创建一个 1200px 宽的 `red-panda.jpg`风景图片版本，和一个 600px 宽的肖像版本，用来显示更近镜头下的熊猫. 同样地，为它们取一个你可以轻松分辨出来的名字. 将它们的副本保存在与 `index.html`文件相同的目录下。

**注意**：你应该在看起来还行的前提下尽量优化 JPG 和 PNG 图片的大小，[tinypng.com](https://tinypng.com/)为此提供了很好的服务。

#### 为 header 添加一个图标[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E4%B8%BA_header_%E6%B7%BB%E5%8A%A0%E4%B8%80%E4%B8%AA%E5%9B%BE%E6%A0%87) <a id="&#x4E3A;_header_&#x6DFB;&#x52A0;&#x4E00;&#x4E2A;&#x56FE;&#x6807;"></a>

在 [`<header>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/header) 元素中添加一个 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素，嵌入一个小尺寸版本的火狐图标。

#### 为主 article 添加一个视频[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E4%B8%BA%E4%B8%BB_article_%E6%B7%BB%E5%8A%A0%E4%B8%80%E4%B8%AA%E8%A7%86%E9%A2%91) <a id="&#x4E3A;&#x4E3B;_article_&#x6DFB;&#x52A0;&#x4E00;&#x4E2A;&#x89C6;&#x9891;"></a>

就在 [`<article>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/article) 元素中（开放标签下面），嵌入一个YouTube视频（[https://www.youtube.com/watch?v=ojcNcvb1olg](https://www.youtube.com/watch?v=ojcNcvb1olg)），使用合适YouTube工具来生成所需的代码。视频的宽度应该是 400px。

#### 为 further info 的链接添加响应式图片[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E4%B8%BA_further_info_%E7%9A%84%E9%93%BE%E6%8E%A5%E6%B7%BB%E5%8A%A0%E5%93%8D%E5%BA%94%E5%BC%8F%E5%9B%BE%E7%89%87) <a id="&#x4E3A;_further_info_&#x7684;&#x94FE;&#x63A5;&#x6DFB;&#x52A0;&#x54CD;&#x5E94;&#x5F0F;&#x56FE;&#x7247;"></a>

在`further-info`类的  [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div)里你会看到四个 [`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素，每个都指向一个有趣的、关于 Mozilla 的页面。为了完成这一部分，你需要在每个[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素里插入一个 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素，需要包含合适的 [`src`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-src)，[`alt`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-alt)，[`srcset`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-srcset) 和 [`sizes`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-sizes) 属性。

我们希望每张图片（除了某个本身就是响应式的）在浏览器的视口的宽度小于等于480px时使用的120px宽的图片，其他情况下选择400px 的版本.

确保正确的链接匹配了正确的图片！

**注意**: 为了正确的测试 `srcset`/`sizes` 示例，你需要把你的网站上传到服务器（使用 [Github pages](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Using_Github_pages) 是一个简单免费的方法），访问服务器上的网页，你就可以使用浏览器开发者工具来测试它们是否正常工作，如 [响应式图片：有用的开发工具](https://developer.mozilla.org/zh-CN/Learn/HTML/Multimedia_and_embedding/Responsive_images#Useful_developer_tools)中所说

#### 一个艺术方向性的红色熊猫[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E4%B8%80%E4%B8%AA%E8%89%BA%E6%9C%AF%E6%96%B9%E5%90%91%E6%80%A7%E7%9A%84%E7%BA%A2%E8%89%B2%E7%86%8A%E7%8C%AB) <a id="&#x4E00;&#x4E2A;&#x827A;&#x672F;&#x65B9;&#x5411;&#x6027;&#x7684;&#x7EA2;&#x8272;&#x718A;&#x732B;"></a>

在`red-panda`类的 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div) 中，我们希望插入一个 [`<picture>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/picture)元素，在视口宽度小于等于600px时使用那张比较小的纵向的熊猫图片，在其他情况下则使用大的横向的图片。

### 示例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E7%A4%BA%E4%BE%8B) <a id="&#x793A;&#x4F8B;"></a>

下面的截图展示了在正确标记后，醒目页面在宽屏和窄屏下的样子。

![A wide shot of our example splash page](https://mdn.mozillademos.org/files/12946/wide-shot.png)

![A narrow shot of our example splash page](https://mdn.mozillademos.org/files/12944/narrow-shot.png)

### 评估[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E8%AF%84%E4%BC%B0) <a id="&#x8BC4;&#x4F30;"></a>

如果这个评估是一系列课程的一部分，你应该可以让你的老师或导师为你批改。 如果你是自学，可以很容易地在 [discussion thread about this exercise](https://discourse.mozilla.org/t/mozilla-splash-page-assignment/24679)或[Mozilla IRC](https://wiki.mozilla.org/IRC)的[\#mdn](irc://irc.mozilla.org/mdn) IRC频道回复得到批改指南。请先自己试着做——作弊学不到任何东西！

### 在这个模块中[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page#%E5%9C%A8%E8%BF%99%E4%B8%AA%E6%A8%A1%E5%9D%97%E4%B8%AD) <a id="&#x5728;&#x8FD9;&#x4E2A;&#x6A21;&#x5757;&#x4E2D;"></a>

* [HTML中的图片](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)
* [音视频内容](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)
* [从&lt;object&gt; 到&lt;iframe&gt; — 其他嵌入技术](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies)
* [给网页添加矢量图](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web)
* [响应式图片](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)
* [Mozilla醒目页面](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page)

