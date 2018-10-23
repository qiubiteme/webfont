# 调试 CSS

在本模块的最后一篇文章中，我们会看看调试 CSS 的基础知识，包括探索应用 CSS 的页面，以及其它可以帮你在你的 CSS 代码中查找错误的工具。

| 预备知识： | 基本计算机素养，[基本的软件安装](https://developer.mozilla.org/zh-CN/Learn/Getting_started_with_the_web/Installing_basic_software)，对于[处理文件](https://developer.mozilla.org/zh-CN/Learn/Getting_started_with_the_web/Dealing_with_files)的基本理解，HTML基础（学习[HTML入门](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)），以及明白CSS的工作原理（学习[本模块](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS)之前的文章）。 |
| :--- | :--- |
| 目标： | 学习如何调试 CSS 的基础知识。 |

就像调试HTML一样，调试CSS并不比调试许多其他类型的代码要可怕。我们建议您在继续之前\(重新\)阅读[调试并不可怕](https://developer.mozilla.org/zh-CN/Learn/HTML/Introduction_to_HTML/Debugging_HTML#Debugging_isn%27t_scary)。

### CSS 和 调试[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS#CSS_%E5%92%8C_%E8%B0%83%E8%AF%95) <a id="CSS_&#x548C;_&#x8C03;&#x8BD5;"></a>

就像HTML一样，CSS是宽容的（在继续阅读前阅读[宽容代码](https://developer.mozilla.org/zh-CN/Learn/HTML/Introduction_to_HTML/Debugging_HTML#Permissive_code)。）在CSS的情况下，如果一个声明是无效的（包含语法错误，或者浏览器不支持该特性），浏览器完全忽略了它，然后转向它找到的下一个。

如果选择器是无效的，那么它就不会选择任何东西，而整个规则也不会再做任何事情，浏览器只会继续执行下一个规则。

这在很多情况下都是很好的，在大多数情况下，你的内容会显示给你的用户，即使它不是很正确。但是，当您试图调试这个问题时，这并不是很有帮助，您甚至没有得到任何错误消息来帮助您找到它。当你的用户无法看到内容的时候，这就更令人头疼了——也许关键的风格没有被应用，导致布局出现了严重的错误？

幸运的是，有一些工具可以帮助您。让我们看看这些。

#### 检查 DOM 和 CSS[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS#%E6%A3%80%E6%9F%A5_DOM_%E5%92%8C_CSS) <a id="&#x68C0;&#x67E5;_DOM_&#x548C;_CSS"></a>

现在，所有的web浏览器都提供了帮助您检查和理解web页面的开发工具。在他们提供的各种工具中，有两种可以在所有浏览器中使用:DOM检查器和CSS编辑器，它们都可以在Firefox的[page inspector tool](https://developer.mozilla.org/zh-CN/docs/Tools/Page_Inspector)中找到。我们已经在[调试HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML)中查看了DOM检查器，以及如何使用它来检查HTML。在这里，我们将看到这个和CSS编辑器，以及如何将它们一起使用来调试CSS问题。

**注意：**在下面的示例中，我们正在使用 [Firefox](https://www.mozilla.org/firefox/new)，但是所有的浏览器都提供了相同的工具，它们可能只是在稍微不同的地方使用。阅读 [Discover browser developer tools](https://developer.mozilla.org/zh-CN/docs/Learn/Discover_browser_developer_tools) 找到更多关于在不同的浏览器中访问它们的信息。

在这个示例中，我们首先希望您在一个新的浏览器选项卡中打开我们的[CSS调试示例](http://mdn.github.io/learning-area/css/introduction-to-css/debugging-css/)。如果您想要完成并修复代码问题，以创建示例的最终版本，我们建议您复制[HTML和CSS文件](https://github.com/mdn/learning-area/tree/master/css/introduction-to-css/debugging-css)，并在本地实现修复。

它是一个简单、清晰的专栏网页，包含了一篇简单的文章。

![our example webpage with the problems fixed. The Firefox logo has been floated to the right, and the main heading and body text are now visible and well placed.](https://mdn.mozillademos.org/files/12614/page-fixed.png)

但现在它有点乱了：

![Our example webpage in a broken state. There is a heading of My article in the middle and a Firefox logo, but everything else is small and not easily visible.](https://mdn.mozillademos.org/files/12612/page-broken.png)

让我们开始用页面检查器的特性来研究页面。在火狐中你可以使用 Cmd/Ctrl + I 打开页面检查器（或者通过在菜单中选择_Tools &gt; Web Developer &gt; Inspector_），这将会给你一组工具在浏览器底部的窗口中打开，就像这样：

![The Firefox page inspector, showing the DOM inspector on the left, and the CSS editor on the right. invalid CSS is crossed out and has a warning symbol ](https://mdn.mozillademos.org/files/12604/page-inspector.png)

如果单击左边的DOM检查器中的一个元素，右边的CSS编辑器将更新显示应用到该元素的所有CSS规则。这是非常有用的，特别是当任何无效的属性出现在它们的一行和旁边的一个警告符号的时候。这将会很方便！

![A close up of the Firefox page inspector, showing the DOM inspector on the left, and the CSS editor on the right. invalid CSS is crossed out and has a warning symbol ](https://mdn.mozillademos.org/files/12606/show-invalid-property.png)

**注意：**每个属性旁边还有一个复选框，可以选择checked/unchecked来启用/禁用您的CSS属性。这对于找出可能导致错误的原因也非常有用。

#### 主动学习：发现一些错误！[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E5%8F%91%E7%8E%B0%E4%B8%80%E4%BA%9B%E9%94%99%E8%AF%AF%EF%BC%81) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x53D1;&#x73B0;&#x4E00;&#x4E9B;&#x9519;&#x8BEF;&#xFF01;"></a>

因此，使用工具基础知识，让我们试着找出我们的错误。在每种情况下，您应该尝试单击故障所在的元素，以查看应用的CSS是什么样的。

1.  [`<header>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/header)和  [`<footer>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/footer)元素应该有背景色，但是没有颜色出现。
2.  在页脚的[`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1)和 [`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 在页面上的内容都太高了——在 `<h1>`中这点尤其明显，这几乎是在屏幕上！ 你可以尝试单击 `<h1>` 并且取消对应用声明的勾选，以找出导致问题的原因。
3.  [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 应该是向右浮动的，所以它是在一些文本的右边，但它不是——它直接在所有文本之上。
4. [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main) 内容区域的文本太小了——段落和列表项应该有更大的字体大小，但似乎也没有被应用到其中。提示:这个有点难，因为它是选择器而不是属性的问题。你可能需要研究源代码才能找到这个——您可以在Firefox开发人员工具的[样式编辑器](https://developer.mozilla.org/zh-CN/docs/Tools/Style_Editor)中找到它。

如果你被困住了，你可以看看 [fixed source code on Github](https://github.com/mdn/learning-area/blob/master/css/introduction-to-css/debugging-css-finished/style.css)。

#### CSS 验证[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS#CSS_%E9%AA%8C%E8%AF%81) <a id="CSS_&#x9A8C;&#x8BC1;"></a>

我们已经看到了[W3C HTML验证器](https://validator.w3.org/)，但是它们也有一个[CSS验证器](http://jigsaw.w3.org/css-validator/)。它的工作方式是相同的，允许您在[特定的URL](http://jigsaw.w3.org/css-validator/#validate_by_uri)上验证CSS，通过[上传本地文件](http://jigsaw.w3.org/css-validator/#validate_by_upload)，或者[直接使用CSS输入](http://jigsaw.w3.org/css-validator/#validate_by_input)。

![a visual of the CSS Validation Service mentioned and linked to nearby](https://mdn.mozillademos.org/files/12602/css-validator.png)

#### 主动学习：验证我们的 CSS[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E9%AA%8C%E8%AF%81%E6%88%91%E4%BB%AC%E7%9A%84_CSS) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x9A8C;&#x8BC1;&#x6211;&#x4EEC;&#x7684;_CSS"></a>

让我们试着将CSS注入到验证器中，看看它会有什么结果。

1. 通过[直接输入验证](http://jigsaw.w3.org/css-validator/#validate_by_input)查看CSS验证服务。
2. 将我们的错误填充的CSS复制到验证服务的文本区域。
3. 按检查按钮。

现在，您将看到一个错误列表。只有两个返回：

![The validator results as they appear on the CSS validation service. ](https://mdn.mozillademos.org/files/12610/validator-results.png)

这些都是有用的消息，特别是当它们包含行号和在每个情况下选择的选择器时。我们来看看如何解释这些。

* _Property background-colour doesn't exist : teal_ ——简单的;这告诉我们一个属性是不存在的，这就明确了需要做什么。
* _Value Error : float attempt to find a semi-colon before the property name. add it_ ——这告诉我们一个分号缺失了。观察这一情况的行数，可以很容易地找到。

你可能会认为这没浏览器开发工具有用——它不允许您在引用错误的情况下查看已呈现的代码，如果选择器是不正确的，或者语法是正确的，并且您只是为您的设计选择了一个不正确的值，那么这就不好了。但是，我们认为对于一个大型的样式表，首先要通过这个服务来消除任何基本的语法错误，然后再依赖浏览器开发人员工具来确定其他问题。

**注意：**[CSS Lint](http://csslint.net/)是一个类似的工具，用于验证CSS和发现错误，它也可以提供一些有用的提示并给出有趣的警告。

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

完成了第一个CSS模块的最后一篇文章！现在您已经完成了这一工作，您可以完成我们的[CSS评估](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension)，然后开始探索其他的CSS和HTML模块。

