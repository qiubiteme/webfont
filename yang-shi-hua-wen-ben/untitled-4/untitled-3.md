# 作业：排版社区大学首页

在本测评中，通过对社区学校主页的文本样式化，我们会测试你对所有本模块涉及到的文本样式化技术的理解。你或许也会从中获得乐趣。

| 预备条件: | 在本次测评前，你应该完成了本模块所有章节。 |
| :--- | :--- |
| 目标: | 测试对CSS文本样式化技术的理解。 |

### 开始[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Typesetting_a_homepage#%E5%BC%80%E5%A7%8B) <a id="&#x5F00;&#x59CB;"></a>

在本测评开始前，你应该:

* 获取本次练习的 [HTML](https://github.com/mdn/learning-area/blob/master/css/styling-text/typesetting-a-homepage-start/index.html) 和 [CSS](https://github.com/mdn/learning-area/blob/master/css/styling-text/typesetting-a-homepage-start/style.css) 文件以及提供的 [external link icon](https://github.com/mdn/learning-area/blob/master/css/styling-text/typesetting-a-homepage-start/external-link-52.png)。
* 在本地计算机中拷贝一份上述文件。

**注意**: 或者，你可以使用像 [JSBin](http://jsbin.com/) 或 [Thimble](https://thimble.mozilla.org/) 的网站完成你的测评。你可以把HTML和CSS粘贴到在线编辑器中，并使用[this URL](http://mdn.github.io/learning-area/css/styling-text/typesetting-a-homepage-start/external-link-52.png)指定背景图像。如果你使用的在线编辑器没有单独的CSS面板，你可以将其放在HTML文件的&lt;style&gt;元素中。

### 项目简介[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Typesetting_a_homepage#%E9%A1%B9%E7%9B%AE%E7%AE%80%E4%BB%8B) <a id="&#x9879;&#x76EE;&#x7B80;&#x4ECB;"></a>

你有一个虚构的社区大学主页的未处理HTML文件和一些CSS文件。这些CSS文件把网页分成两栏布局，提供了一些简单的样式化。你将在CSS文件底部的comment下写你的CSS，这样可以方便地标出你的工作。不要担心选择器一直重复；我们会帮你跳过这个问题。

字体：

* 首先，下载一些免费的字体。因为这是一所大学，字体应该严肃，正式，给人信任的感觉 —— 总体使用serif字体，对标题结合使用sans-serif 或者 slab serif会是不错的选择。
* 使用合适的服务对着两种字体生成无死角的`@font-face`代码。
* 将你的body字体应用到body，heading字体应用到heading。

文本样式化基础：

* 设置全站网页 `font-size` 为 `10px`。
* 使用相对单位（relative unit）为标题和其他元素的font-sizes设置合适的值。
* 为body文本设置合适的`line-height`。
* 居中页面顶级标题。
* 为标题设置 `letter-spacing` 避免字间太过拥挤。
* 为body文本设置合适的 `letter-spacing` 和 `word-spacing`。
* 为每个标题后、`<section>`元素中的第一段文字设置20px的文本缩进。

链接：

* 设置 link, visited, focus, 和 hover 状态设置颜色，与页面顶部和底部的水平线颜色相同。
* 设置链接默认带下划线，但hover和focus时下划线消失。
* 取消页面中所有链接focus时默认的外边线。
* 设置active时有显著不同的样式，使其又突出又与整体页面设计和谐。
* 在外部链接右侧插入外部链接图标。

列表：

* 确保列表和列表项与页面整体样式和谐。每个列表项应该有同样的与段落行相同的`line-height` 。每个列表上下间距应该与段落间距相同。
* 使用与页面设计匹配的bullet列表项符号。你可以选择自定义的bullet图像或者其他的喜欢的bullet符号。

导航栏菜单:

* 样式化你的导航栏菜单，使它拥有与页面整体相匹配的外观。

### 提示与技巧[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Typesetting_a_homepage#%E6%8F%90%E7%A4%BA%E4%B8%8E%E6%8A%80%E5%B7%A7) <a id="&#x63D0;&#x793A;&#x4E0E;&#x6280;&#x5DE7;"></a>

* 本练习中你不需要编辑HTML文件。
* 你不需要使导航栏菜单看起来像按钮，但它需要有一定的高度才不至于在页面侧边看起来很别扭；同时记得，你需要的是一个垂直导航栏菜单。

### 实例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Typesetting_a_homepage#%E5%AE%9E%E4%BE%8B) <a id="&#x5B9E;&#x4F8B;"></a>

下图展示了其中一种设计完成后的例子。

![](https://mdn.mozillademos.org/files/12994/example2.png)

### 测评[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Typesetting_a_homepage#%E6%B5%8B%E8%AF%84) <a id="&#x6D4B;&#x8BC4;"></a>

如果你将本测评作为课程的一部分，你应该能够将你的作品交给你的老师/指导员打分。如果你是自学的，你可以很轻松地在[discussion thread for this exercise](https://discourse.mozilla.org/t/typesetting-a-community-school-home-page-assessment/24683)，或者[Mozilla IRC](https://wiki.mozilla.org/IRC)的[\#mdn](irc://irc.mozilla.org/mdn) IRC 频道上获得打分。先尝试完成本次练习——作弊是学不到任何东西的！

