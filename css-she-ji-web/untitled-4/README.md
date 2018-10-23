# 样式化文本



掌握了 CSS 语言的基础之后，对于您来说，下一个需要关心的 CSS 主题就是为文本添加样式——一个您将会最经常使用 CSS 做的事情。在这里，我们专注于为文本样式的基础，包括设置字体、粗细、斜体、行还有字符间距、阴影以及文本的其他特征。我们将会通过在您的网页中应用自定义字体、样式化列表以及链接来圆满地结束本模块。

### 前提[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F#%E5%89%8D%E6%8F%90) <a id="&#x524D;&#x63D0;"></a>

在开始这一模块之前，您应当像 [HTML 介绍](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML) 模块中所探讨的，已经熟悉了基本的HTML，以及像 [CSS 介绍](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS) 中所详述的，对自己的 CSS 基础感觉还满意。

**注意**: 如果您所使用的是不能创建自己的文件的电脑、平板电脑或其他设备的话，您可以在一个在线编码程序 [JSBin](http://jsbin.com/) 或 [Thimble](https://thimble.mozilla.org/) 中尝试（大部分的）代码例子。

### 导引[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F#%E5%AF%BC%E5%BC%95) <a id="&#x5BFC;&#x5F15;"></a>

这个模块包括了以下文章，这些文章将教会您所有的基本功以支持您为 HTML 文本内容添加样式。[基本的文本以及字体样式](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_text/Fundamentals)在本文章中，我们将通篇了解文本、字体样式的所有基础，包括设置字体粗细（ font weight ）、字体系列及样式（ family and style ）、字体缩写（ font shorthand ）、文本排列（ text alignment ）和其他的效果，还有行（ line ）以及字符间距（ letter spacing ）。[样式化列表](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_text/Styling_lists)对于大部分内容来说，列表的行为表现跟其他任何文本其实差不多，但您也需要了解还有一些专门用于列表的 CSS 样式以及考虑一些最好的实践方式。本文章将阐释这一切。[样式化链接](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_text/Styling_links)当您为链接添加样式时，很重要的一点是要去理解怎样有效地使用伪类去修饰链接的状态，以及怎么去修饰不同的接口功能例如导航菜单和面板中所使用的链接。我们将会在这篇文章中讨论这些话题。[网络字体](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_text/Web_fonts)在这里我们将会详细地探索网络字体——这会允许您与您的网页一同下载自定义字体，来实现更为不同的个性化字体样式。

### 评估[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F#%E8%AF%84%E4%BC%B0) <a id="&#x8BC4;&#x4F30;"></a>

以下的评估将会评测您对以上导引所涵盖的为文本添加样式的技术的理解。[对一个社区学校的主页进行排版](https://developer.mozilla.org/zh-CN/Learn/CSS/Styling_text/Typesetting_a_homepage)在这个评估中，我们通过让您为一个社区学校的主页添加文本样式来测试您对文本样式的理解程度。



