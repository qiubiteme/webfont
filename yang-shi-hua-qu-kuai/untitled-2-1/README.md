# 样式化区块

你好，欢迎来到“样式化CSS盒子”部分 —— 在上一部分，我们了解了盒子内部的内容；这个部分，我们将学习对盒子自身进行样式化，包括操纵其背景颜色、图像、边框和其他部分等。我们还将讨论其他主题，包括美化HTML表格和应用高级效果，如滤镜、混合模式。

### 准备条件[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes#%E5%87%86%E5%A4%87%E6%9D%A1%E4%BB%B6) <a id="&#x51C6;&#x5907;&#x6761;&#x4EF6;"></a>

 在开始此部分内容之前，你需要对HTML有基本的了解，具体参见[HTML入门](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)，且对CSS基础不会太陌生，具体参见[CSS 介绍](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS)。

**注意：** 如果你正在一台不能创建你自己的文件的电脑/平板或者其它设备上工作， 你可以在诸如[JSBin](https://jsbin.com/)或者[Thimble](https://thimble.mozilla.org/zh-CN/)这样的在线平台上试运行我们（绝大部分）的示例代码。

### 概览[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes#%E6%A6%82%E8%A7%88) <a id="&#x6982;&#x89C8;"></a>

**译者注：**由于不同志愿者的用词习惯，box有时候被翻译成“盒子”，有时候被翻译成“框”。又由于一篇文章有时候由好几位志愿者共同翻译，因此常常在一篇文章中既出现了“盒子”，又出现了“框”，这给读者造成了很大的困扰。在之前几个模块的本地化工作时，我个人认为“框”能更准确表达出box的意思。在W3C上，那里的译者也将box翻译成“框”。但是显然的，“盒子”比“框”更容易区分——“框”容易和“边框（border）”混淆。我在这里特地增加了一个译者注，是希望读者在之后的阅读中能够明白“框”=“盒子”=box，边框=“border”。诸如此类的，padding大部分人翻译成“内边距”，但是padding也有人翻译为“填充”。（我觉得padding不需要翻译，直接就是padding，简洁明了。）

这些文章将会用一种有趣而简单的方式教会你所有有关样式化CSS盒子的方式。[盒子模型概要](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap)我们已经在 [CSS 介绍](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS) 部分了解了[CSS盒子模型](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model)基础。本文将会对该部分进行概要回顾，并将深入讨论更多相关细节。[背景](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Backgrounds)在CSS中，你可以有很多的方式来为你的内容设置背景。我们已经看过一些例子，比如说基本的图片背景和颜色背景。本文将会向你讲述关于这个话题的一切，并且会了解一些高级特性，比如说多图背景，渐变色。[边框](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders)又一次，我们已经接触过边框了，简单的用法比如设置边框的颜色和样式。 在这里，我们将为您介绍可用的其他功能，例如圆角和边框图像。[样式化表格](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables)对HTML表格进行样式化并不是世界上最富有魅力的工作，但有时我们必须这样做。 本文提供了使HTML表格看起来不错的指南，前面的文章中详细介绍了这些工具。[高级盒子效果](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects)本文作为一个技巧，提供了一些可用于不适合上述其他类别的样式框的高级功能的介绍，如边框阴影，混合模式和过滤器。

### 评估[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes#%E8%AF%84%E4%BC%B0) <a id="&#x8BC4;&#x4F30;"></a>

以下评估将测试您对上述指南中所述的盒子造型技术的理解。[创建酷炫的信头纸](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Creating_fancy_letterheaded_paper)如果你想做出正确的印象，在一张漂亮的信头纸上写信可能是一个很好的开始。 在这个评估中，我们给您一个挑战——创建一个在线模板，以实现这一目的。[一个漂亮的盒子模型](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box)在这里，您将通过尝试创建一个引人注目的盒子来获得更多练习创建漂亮的盒子。

### 另请参加[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes#%E5%8F%A6%E8%AF%B7%E5%8F%82%E5%8A%A0) <a id="&#x53E6;&#x8BF7;&#x53C2;&#x52A0;"></a>

[创建酷炫的盒子模型](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Howto/create_fancy_boxes)更多酷炫的盒子模型风格样例。

