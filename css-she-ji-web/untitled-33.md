# CSS 介绍

CSS 是用来样式化和排版你的网页的 —— 例如更改网页内容的字体、颜色、大小，将内容分割成多列或者加入动画以及别的装饰型效果。本文将通过讲述CSS 的工作原理，包括选择器是什么，属性是什么，如何撰写CSS规则，如何将CSS应用到HTML，CSS中如何描述长度、颜色以及其他属性的计量单位，关于层叠与继承的知识和如何进行CSS的调试工作，带你走上掌握CSS的道路。 

### 前提要求[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS#%E5%89%8D%E6%8F%90%E8%A6%81%E6%B1%82) <a id="&#x524D;&#x63D0;&#x8981;&#x6C42;"></a>

在开始阅读文章前，你应该有：

1. 熟悉基本的电脑操作，以及使用过Web的经历（即查看一些网页，并获取其内容）。
2. 最基础的工作环境，并且了解如何创建与管理、编辑文件，比如 [Installing basic software](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software)（安装基础软件），[Dealing with files](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Dealing_with_files)（处理文件）。
3. 对HTML有一些基础的了解------如 [Introduction to HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)（HTML简介）。

**注意：**如果您正在电脑/平板电脑/其他设备或者其他不能够创建自己的文件的环境，你可以尝试一下在线开发环境如 [JSBin](http://jsbin.com/) 或者 [Thimble](https://thimble.mozilla.org/)（译者注：这是两个可以在线编辑html/css/js并且执行的网站）。

**译者注：**由于不同志愿者的用词习惯，box有时候被翻译成“盒子”，有时候被翻译成“框”。又由于一篇文章有时候由好几位志愿者共同翻译，因此常常在一篇文章中既出现了“盒子”，又出现了“框”，这给读者造成了很大的困扰。在之前几个模块的本地化工作时，我个人认为“框”能更准确表达出box的意思。在W3C上，那里的译者也将box翻译成“框”。但是显然的，“盒子”比“框”更容易区分——“框”容易和“边框（border）”混淆。我在这里特地增加了一个译者注，是希望读者在之后的阅读中能够明白“框”=“盒子”=box，边框=“border”。诸如此类的，padding大部分人翻译成“内边距”，但是padding也有人翻译为“填充”。对于刚开始的同学，如果你还没有遇到这些词，请不要着急，后面马上就会出现。

### 指南[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS#%E6%8C%87%E5%8D%97) <a id="&#x6307;&#x5357;"></a>

这些模块将带你了解CSS的基础知识，并提供充足的机会让你测试一些技术。[CSS是怎么工作的](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works)首先，我们先从基础讲起来说明什么是CSS，HTML是如何被浏览器转换成 [DOM](https://developer.mozilla.org/en-US/docs/Glossary/DOM) 的，以及CSS样式是如何被应用到DOM里的，这里有一些最基本的语法示例，这些代码就是被用于我们所游览网页上的代码。[CSS 语法](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax) 接下来，我们将深入了解CSS语法更多的细节，了解属性及其值会形成声明，多个声明形成声明块，声明块和选择器形成完整的CSS规则。此外我们还会了解其他的CSS模块，如注释和空白。[选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Selectors)选择器是在前一篇文章中已经提到过的，但在这个章节会引导我们深入更多的细节，通过这篇文字可以了解所有选择器类型和它们是如何工作的。[CSS  的值和单位 ](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units)有许多类型的CSS属性值需要学习，从数值颜色函数执行某一动作\(如嵌入一个背景图像，或旋转一个元素\)。而这些依赖于特定单位指定的确切值代表的是什么？列如你想让你的盒子是30像素宽，或30厘米，或30 ems吗？这个章节会指导我们了解更多的CSS数值、CSS颜色和简单的CSS函数，以及探索不太常见的单位比如度，甚至没有单位的数值。[层叠和继承](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance)CSS有两种不同但相关的方式解决选择器冲突（不同的选择器选择了相同的元素，哪个会被应用？）及元素嵌套的情况（有些子元素适合继承父元素的样式，有些则不适合）。这篇文章涵盖了使用这两种方式足够用的内容，但不是所有的内容。[框模型](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model)CSS框模型是网络布局的基础——每个元素表示为一个矩形框，矩形框的content、padding、border和margin像是洋葱一样嵌套（或者说是一个4层的俄罗斯套娃）。浏览器显示一个页面，它会把那些样式应用到每个框中，周围的“洋葱层”有多大，框位置间的关系。在建立CSS布局之前，您需要理解这个框模型。[调试 CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS) 在这个模块的最后一篇文章中，我们看看CSS调试的基本知识，包括探索CSS应用到一个页面和其他一些游览器工具，可以帮助你找到你的CSS代码中的错误。

### 测验[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS#%E6%B5%8B%E9%AA%8C) <a id="&#x6D4B;&#x9A8C;"></a>

下面测验将用于检测你对上述内容的学习情况。[Fundamental CSS comprehension](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension)（基本CSS理解）这个精心设计的测验将帮助测试你对CSS的理解。

### 另请参阅[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS#%E5%8F%A6%E8%AF%B7%E5%8F%82%E9%98%85) <a id="&#x53E6;&#x8BF7;&#x53C2;&#x9605;"></a>

[Intermediate Web Literacy 1: Intro to CSS](https://teach.mozilla.org/activities/intermediate-web-lit/)一个优秀的Mozilla基金会，探索和测试的很多技能在引言中讨论CSS模块。学习HTML元素在网页中如何使用CSS选择器，属性和值。

