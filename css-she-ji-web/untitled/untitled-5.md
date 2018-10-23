# 基本的CSS理解

你已经在这个模块中了解到了很多内容, 所以当你达到这个模块的最后一篇文章的时候，感觉一定非常不错吧！在你继续之前的最后一步，就是完成对于这个模块的测验。本次测验涉及到几个相关的练习，你必须按顺序完成，这样你才能设计出最终的成品：一张名片/游戏玩家卡片/社交媒体的简介。

| 学习本章的前提条件: | 在尝试这个测验之前，你应该已经完成了这个模块中所有文章的学习。 |
| :--- | :--- |
| 目标： | 来测试对 CSS 理论、语法、功能性的基本理解。 |

### 起点[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension#%E8%B5%B7%E7%82%B9) <a id="&#x8D77;&#x70B9;"></a>

在开始测验之前，你应该:

* 将 [HTML file for the exercise](https://github.com/mdn/learning-area/blob/master/css/introduction-to-css/fundamental-css-comprehension/index.html), 和 [associated image file](https://github.com/mdn/learning-area/blob/master/css/introduction-to-css/fundamental-css-comprehension/chris.jpg),拷贝到你的本地环境中。如果你想使用自己的图片文件以及把你的名字写进资料里面的话，也没有问题，不过需要保证你提供的图像是正方形的。
* 下载 [CSS resources text file](https://github.com/mdn/learning-area/blob/master/css/introduction-to-css/fundamental-css-comprehension/style-resources.txt) 到你的本地环境，这个文件包含了一组原始选择器和规则集。你需要学习并将他们组合，这是测验的一部分。

**注意**: 另外, 你可以使用一个网站比如 [JSBin](http://jsbin.com/) 或 [Thimble](https://thimble.mozilla.org/) 来做你的测验。你可以复制 HTML 和 CSS 到其中一个在线编辑器中，以及使用这个 [this URL](http://mdn.github.io/learning-area/css/introduction-to-css/fundamental-css-comprehension/chris.jpg) 来让 `<img>` 显示图片。如果你使用的在线编辑器无法让你链接 CSS 文件 \(没有单独的 CSS 面板\)，你也可以将 CSS 直接放入`<style>` 元素中。

### 项目概要[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension#%E9%A1%B9%E7%9B%AE%E6%A6%82%E8%A6%81) <a id="&#x9879;&#x76EE;&#x6982;&#x8981;"></a>

我们已经为你提供了一些原始的 HTML 和一张图片，然后需要编写必要的 CSS 来让其成为一个漂亮的网上小名片，可能大小是游戏玩家卡片或社交媒体简介的两倍。下面的段落描述了你需要做的事情。

基本设置:

* 首先，在你放 HTML 文件和图像文件的目录下，创建一个新的文件，把它命名为类似`style.css`。
* 通过 `<link>` 元素来将你的 CSS 链接到 HTML 文件中。
* 我们为你提供的 CSS 资源文本文件中，前两项规则集是我们设置好的，你可以直接使用，所以将他们复制粘贴到你的新 CSS 文件的顶部。同时也可以将这个作为测验，用来确认你是否正确链接了你的 CSS 文件到 HTML 中。
* 在以上的两条规则中添加一条 CSS 注释，注释中要包含一些文本来表明这是整体页面的一般样式。你可以在 CSS 文件底部添加 3 个或以上的注释，来明确地表明该样式是应用到卡片的容器，应用到标题和页脚的样式，和名片主要内容的样式。从现在开始，随后在样式表添加的样式都应该有组织地放置在合适的地方。

关注我们为你提供的选择器和规则集：

* 接下来, 我们希望你观察四个选择器，并计算每一个的专用性。将它们写在稍后可以找到的地方，例如在CSS顶部的注释中。
* 现在是时候把正确的选择器放在正确的规则集上了！你的CSS资源中有四对选择器和规则集需要匹配，现在就开始匹配，并将它们添加到你的CSS文件。你需要：
  * 为整体卡片的容器提供一个固定的宽/高，背景颜色，边框，以及边框圆角等等。
  * 为header提供一个渐变的背景颜色，从更暗到更亮，加上圆角，配合在卡片容器上设置的圆角。
  * 为footer提供一个渐变的背景颜色，从更亮到更暗，加上圆角，配合在卡片容器上设置的圆角。
  * 将图像向右浮动，使其粘贴在名片主要内容的右边，然后把它的 max-height 设置为 100% \(一个聪明的技巧，来确保它将放大/缩小，与父容器保持同样的高度，不管它变成什么高度。\)
* 注意！提供的规则集中有两个错误。使用你知道的任何技术找到这些错误并修复，然后再继续。

你需要写的新规则：

* 为卡片的标题编写一个规则集，以及卡片页脚，使他们的高度为 50px，其中包括 30px 的内容高度，和 10px 的 padding，不过需要使用`em`来表示。
* 浏览器会为`<h2>` 和 `<p>`元素应用默认的 margin，这会影响我们的设计，所以编写一个规则集，来将他们的 margin 设置为 0。
* 为了阻止图像溢出名片的主要内容 \( `<article>` 元素\)，我们需要给它设置一个明确的高度。设置 `<article>`的高度为 120px，但是使用 `em`来表示。还要给它一个半透明黑色的背景颜色，产生一个稍暗一点的阴影，让背景红色的颜色也会发光。
* 编写一个规则集，使 `<h2>` 有效的字体大小为20px \(使用 `em`表达\) 以及一个适当的行高将其放置在标题的内容框的中央。回想起来，内容框高度应该是30px，你所有需要的数字都已经给你了，所以可以计算出行高。
* 为页脚中的 `<p>` 编写一个规则集，使它的有效字体大小为 15px \(使用 `em`表达\) 以及一个适当的行高将其放置在页面的内容框的中央。回想起来，内容框高度应该是30px，你所有需要的数字都已经给你了，所以可以计算出行高。
* 最为最后一步, 为 `<article>` 中的段落设置一个合适的 padding 值，让它和 `<h2>` 以及页脚的段落左边缘对齐，并将其颜色设置得便于阅读。

**注意**: 记住第二条规则集会将 `font-size: 10px;` 设置在 `<html>` 元素上 — 这意味着 `<html>` 的任何后代中，一个em将会等于10px而不是默认的 16px 。\(这是当然的，如果在层次结构中，有不同的 `font-size` 设置于其上，问题中的后代没有任何的祖先位于 em元素和 `<html>` 之间。这可能会影响您所需要的值，尽管在这个简单的示例中，这不是问题。\)

其他事情要考虑：

* 如果你编写的CSS有比较好的可读性，并在每行上单独声明，你将得到奖励。
* 你应该在所有规则的选择器中都用 `.card` 作为开头，这样的好处是：如果将名片放在带有其他内容的页面的情况下，这些规则不会干扰其他元素的样式。

### 注意和提示[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension#%E6%B3%A8%E6%84%8F%E5%92%8C%E6%8F%90%E7%A4%BA) <a id="&#x6CE8;&#x610F;&#x548C;&#x63D0;&#x793A;"></a>

* 你不需要以任何方式编辑HTML，除了将CSS应用于你的HTML。
* 当使用 `em` 值代表一些你需要的像素长度的时候，想想 \(`<html>`\) 元素的基本字体大小，以及需要乘以什么才能获得所需的值。这将给你 em 的值，至少在这样一个简单的情况下。

### 示例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension#%E7%A4%BA%E4%BE%8B) <a id="&#x793A;&#x4F8B;"></a>

以下屏幕截图显示了完成设计应如下所示的示例：

![A view of the finished business card, show a reader header and footer, and a darker center panel containing the main details and image.](https://mdn.mozillademos.org/files/12616/business-card.png)

### 评估[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension#%E8%AF%84%E4%BC%B0) <a id="&#x8BC4;&#x4F30;"></a>

如果您将此评估作为有组织的课程的一部分，您应该能够将您的工作交给您的老师/导师进行标记。 如果您是自学习的，那么您可以通过询问  [Learning Area Discourse thread](https://discourse.mozilla-community.org/t/learning-web-development-marking-guides-and-questions/16294), 或在 [\#mdn](irc://irc.mozilla.org/mdn)的IRC频道 [Mozilla IRC](https://wiki.mozilla.org/IRC) 中轻松获得标记指南. 首先尝试练习 - 作弊没有什么可以获得的！

