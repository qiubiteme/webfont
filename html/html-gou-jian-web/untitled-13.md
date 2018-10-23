# 构建出有内容的网页

使用CSS构建一个准备好内容的页面是一个非常重要的技能，因此在这个评估中，您将会考虑到您构建页面可能最终查找的能力，并选择适当的结构语义来构建一个布局在上面。

| 先决条件: | 在尝试本评估前你应该已经学完了其余课程，特别是 [Document and website structure](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure). |
| :--- | :--- |
| 目标: | 检验网页结构知识，以及如何使用 HTML 标记呈现一个预期的布局设计。 |

### 起点[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Structuring_a_page_of_content#%E8%B5%B7%E7%82%B9) <a id="&#x8D77;&#x70B9;"></a>

开始本测验前，你应该先下载这个[包含了所有材料的zip压缩文件](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/structuring-a-page-of-content-start/assets.zip?raw=true)。该 zip 文件包含：

* 需要你补充结构标记的 HTML 文件。
* 给标记添加样式的 CSS 文件。
* 页面中使用的图片。

在你的本地电脑上创建示例，或者也可以使用像 [JSBin](http://jsbin.com/) 或 [Thimble](https://thimble.mozilla.org/) 这样的网站来完成你的测验。

### 项目简介[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Structuring_a_page_of_content#%E9%A1%B9%E7%9B%AE%E7%AE%80%E4%BB%8B) <a id="&#x9879;&#x76EE;&#x7B80;&#x4ECB;"></a>

本项目中，你的任务是为一个鸟类观察网站的主页内容添加结构化的元素，使其可以应用页面设计。它需要：

* 一个全宽度的页眉（header），包含网站主标题、网站 logo 和导航栏菜单。设计样式生效后标题和 logo 会在两边，导航栏在它们下面。
* 一个两列的主内容区域 — 一个包含欢迎信息的主块和一个包含图片缩略图的侧边栏。
* 一个包含版权信息和鸣谢的页脚（footer）。

你应该为以下内容添加合适的标签：

* 页眉
* 导航菜单
* 主要内容
* 欢迎语
* 图片侧边栏
* 页脚

你应该：

* 在已有的 link 标签下面添加另一个 [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link) 元素，来将提供的 CSS 文件添加到页面中。

### 要点和提示[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Structuring_a_page_of_content#%E8%A6%81%E7%82%B9%E5%92%8C%E6%8F%90%E7%A4%BA) <a id="&#x8981;&#x70B9;&#x548C;&#x63D0;&#x793A;"></a>

* 使用[W3C HTML validator](https://validator.w3.org/) 来验证你的 HTML；如果它尽可能多的验证，你会得到加分。\("googleapis" 一行用于从 Google Fonts 服务引入自定义字体到页面；这个不会被验证，所以不用担心。\)
* 你不需要知道任何 CSS 来做本测验；你只需要将提供的 CSS 通过 HTML 元素添加即可。
* 提供的 CSS 已经设计好了，所以当正确的结构元素被添加到标记中，就会如给定的页面一样是绿色的。
* 如果你卡住了并且不能设想添加元素到哪里，画一个简单的页面布局模块图通常很有帮助，然后添加一个你认为可以包裹每个块的元素。

### 示例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Structuring_a_page_of_content#%E7%A4%BA%E4%BE%8B) <a id="&#x793A;&#x4F8B;"></a>

添加标记后的主页的样子的一个可能示例，如以下截图所示：

![The finished example for the assessment; a simple webpage about birdwatching, including a heading of &quot;Birdwatching&quot;, bird photos, and a welcome message](https://mdn.mozillademos.org/files/12449/example-page.png)

### 评估[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Structuring_a_page_of_content#%E8%AF%84%E4%BC%B0) <a id="&#x8BC4;&#x4F30;"></a>

如果你将本测验作为有组织的课程的一部分，你应该将你的工作给你的老师/导师来打分。如果你是自学，你可以很容易地通过在 [discussion thread about this exercise](https://discourse.mozilla.org/t/structuring-a-page-of-content-assignment/24678) 获得标记帮助，或者在 [Mozilla IRC](https://wiki.mozilla.org/IRC) 的 [\#mdn](irc://irc.mozilla.org/mdn) IRC 频道。首先尝试自己做练习 — 作弊不会有任何收获！

