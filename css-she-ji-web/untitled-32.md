# 选择器

在[CSS](https://developer.mozilla.org/en-US/docs/Glossary/CSS)中，选择器用于定位我们想要样式化的网页[HTML](https://developer.mozilla.org/en-US/docs/Glossary/HTML) 元素。各种各样可用的CSS选择器允许我们精确选择要样式化的元素。在接下来的几篇文章中，我们将详细介绍不同类型的选择器，看看它们是如何工作的。

| **前提**： | 基本的计算机使用能力，[已安装基本的软件](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software)，[文件处理](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Dealing_with_files)的基本知识，以及 HTML 基础 （学习 [HTML入门](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML)），以及[CSS 如何工作](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works)的概念。 |
| :--- | :--- |
| **目标：** | 详细学习 CSS 选择器如何工作 |

### 基础[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Selectors#%E5%9F%BA%E7%A1%80) <a id="&#x57FA;&#x7840;"></a>

在上篇文章中我们已经详细介绍了常规的 [CSS 语法和术语](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax) 。简而言之，选择器是 CSS 规则的一部分且位于 CSS 声明块前。

![](https://mdn.mozillademos.org/files/3668/css%20syntax%20-%20ruleset.png)

#### 不同种类的CSS选择器:[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Selectors#%E4%B8%8D%E5%90%8C%E7%A7%8D%E7%B1%BB%E7%9A%84CSS%E9%80%89%E6%8B%A9%E5%99%A8) <a id="&#x4E0D;&#x540C;&#x79CD;&#x7C7B;&#x7684;CSS&#x9009;&#x62E9;&#x5668;"></a>

选择器可以被分为以下类别：

* **简单选择器（Simple selectors）：**通过元素类型、[`class`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-class) 或 [`id`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-id) 匹配一个或多个元素。
* **属性选择器（Attribute selectors）**：通过 属性 / 属性值 匹配一个或多个元素。
* **伪类（Pseudo-classes）：**匹配处于确定状态的一个或多个元素，比如被鼠标指针悬停的元素，或当前被选中或未选中的复选框，或元素是DOM树中一父节点的第一个子节点。
* **伪元素（Pseudo-elements）**:匹配处于相关的确定位置的一个或多个元素，例如每个段落的第一个字，或者某个元素之前生成的内容。 
* **组合器（Combinators）**：这里不仅仅是选择器本身，还有以有效的方式组合两个或更多的选择器用于非常特定的选择的方法。例如，你可以只选择divs的直系子节点的段落，或者直接跟在headings后面的段落。
* **多重选择器（Multiple selectors）**：这些也不是单独的选择器；这个思路是将以逗号分隔开的多个选择器放在一个CSS规则下面， 以将一组声明应用于由这些选择器选择的所有元素。

### 选择器文章概览[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Selectors#%E9%80%89%E6%8B%A9%E5%99%A8%E6%96%87%E7%AB%A0%E6%A6%82%E8%A7%88) <a id="&#x9009;&#x62E9;&#x5668;&#x6587;&#x7AE0;&#x6982;&#x89C8;"></a>

接下来的四篇文章都探索了选择器的不同方面 —— 由于选择器有太多知识点，故我们已把这些知识打碎，我们希望这能使它不那么吓人，并且我们给出一些明确的要点来使你轻松学习。文章如下：

* [简单选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors)
* [属性选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors)
* [伪类和伪元素](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements)
* [组合器和多用选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors)

为防止你遗漏任何相关信息，强烈建议你首先学习[简单选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors)。

