# 框模型



CSS框模型（译者注：也被称为“盒模型”）是网页布局的基础 ——每个元素被表示为一个矩形的方框，框的内容、内边距、边界和外边距像洋葱的膜那样，一层包着一层构建起来。浏览器渲染网页布局时，它会算出每个框的内容要用什么样式，周围的洋葱层有多大，以及框相对于其它框放在哪里。在理解如何创建 CSS 布局之前，你需要理解框模型——这就是本文中我们将要学习的内容。

| 预备知识： | 基本计算机素养，[基本的软件安装](https://developer.mozilla.org/zh-CN/Learn/Getting_started_with_the_web/Installing_basic_software)，对于[处理文件](https://developer.mozilla.org/zh-CN/Learn/Getting_started_with_the_web/Dealing_with_files)的基本理解，HTML基础（学习[HTML入门](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)），以及明白CSS的工作原理（学习[本模块](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS)之前的文章）。 |
| :--- | :--- |
| 目标： | 学习CSS框模型是如何工作的，以及如何在页面上布局单个元素。 |

### 框属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#%E6%A1%86%E5%B1%9E%E6%80%A7) <a id="&#x6846;&#x5C5E;&#x6027;"></a>

文档的每个元素被构造成文档布局内的一个矩形框，框每层的大小都可以使用一些特定的CSS属性调整。相关属性如下:

![](https://mdn.mozillademos.org/files/13647/box-model-standard-small.png)[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 和 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)

[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 和 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) 设置**内容框（content box）**的宽度和高度。内容框是框内容显示的区域——包括框内的文本内容，以及表示嵌套子元素的其它框。

**注意**: 还有其他属性可以更巧妙地处理内容的大小——设置大小约束而不是绝对的大小。这些属性包括[`min-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/min-width)、[`max-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/max-width)、[`min-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/min-height) 和 [`max-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/max-height)。[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)**padding** 表示一个 CSS 框的**内边距** ——这一层位于内容框的外边缘与边界的内边缘之间。该层的大小可以通过简写属性[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) 一次设置所有四个边，或用 [`padding-top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-top)、[`padding-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-right)、[`padding-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-bottom) 和 [`padding-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-left) 属性一次设置一个边。[`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)CSS 框的**边界**（border）是一个分隔层，位于内边距的外边缘以及外边距的内边缘之间。边界的默认大小为0——从而让它不可见——不过我们可以设置边界的厚度、风格和颜色让它出现。 [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) 简写属性可以让我们一次设置所有四个边，例如  _`border: 1px solid black;`_ 但这个简写可以被各种普通书写的更详细的属性所覆盖：

* [`border-top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top), [`border-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-right), [`border-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom), [`border-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-left): 分别设置某一边的边界厚度／风格／颜色。
* [`border-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-width), [`border-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-style), [`border-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-color): 分别仅设置边界的厚度／风格／颜色，并应用到全部四边边界。
* 你也可以单独设置某一个边的三个不同属性，如 [`border-top-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top-width), [`border-top-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top-style), [`border-top-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top-color)，等。 

[`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)

外边距（margin）代表 CSS 框周围的外部区域，称为**外边距**，它在布局中推开其它 CSS 框。其表现与 padding 很相似；简写属性为 [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)，单个属性分别为 [`margin-top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-top)、[`margin-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-right)、 [`margin-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-bottom) 和 [`margin-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-left)。

**注意**: 外边距有一个特别的行为被称作[外边距塌陷（margin collapsing）](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)：当两个框彼此接触时，它们的间距将取两个相邻外边界的最大值，而非两者的总和。 

### 自主学习： 玩转框[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0%EF%BC%9A_%E7%8E%A9%E8%BD%AC%E6%A1%86) <a id="&#x81EA;&#x4E3B;&#x5B66;&#x4E60;&#xFF1A;_&#x73A9;&#x8F6C;&#x6846;"></a>

在这里, 让我们进入主动学习部分，并通过进行一些练习来说明一些上面讨论的框模型的细节。 您可以在下面的实时编辑器中尝试这些练习，但是如果您在本地创建单独的HTML和CSS文件，并在单独的浏览器窗口中尝试，可能会更容易看到某些效果。您可以[在Github上找到示例代码](https://github.com/mdn/learning-area/tree/master/css/introduction-to-css/box-model)。

如果你犯了错误，你可以随时使用“重置”按钮。如果你有点不知所措，按下“显示”按钮可以看到可能的答案。

在下面可编辑的示例中，有三个框，它们都包含文本内容并且已经已经被设计为覆盖整个body的宽度。它们由 [`<header>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/header), [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main),和 [`<footer>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/footer) 这些元素来标记表示。 我们希望您专注于底部的三个CSS规则，即用于每个单独框的规则，并尝试以下操作：  

* 通过打开浏览器开发工具并单击DOM检查器中的元素，查看页面上各个元素的盒子模型。有关如何执行此操作的帮助，请参阅[探索浏览器开发工具](https://developer.mozilla.org/zh-CN/docs/Learn/Discover_browser_developer_tools)。每个浏览器都有一个框模型查看器，它可以准确显示应用于每个盒子的margin，border和padding，内容框（content box）的大小以及元素占用的总空间。
* 给[`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main)元素的 [`margin-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-bottom)赋值，比如说20px。然后给 [`<footer>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/footer) 元素的 [`margin-top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-top) 赋值，比如说15px。注意，第二个操作对布局没有任何影响——这就是外边距塌陷；较小的margin有效宽度为0，只留下值较大的margin。
* 将[`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main)元素的每一边的 [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)和 [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)设置为30px——注意元素的margin和padding都增加了，导致content占据的空间变小。同样，使用浏览器开发工具来查看这个问题。
* 将 [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main) 元素的每一边设置一个更大的边界，比如说40px，然后注意这是如何从内容（content）而不是外边距和内边距获得空间的。您可以通过 [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)属性为宽度、样式和颜色设置一整套新的值来实现这一点，比如 `60px dashed red`，但是既然之前的规则已经设置好了属性，你也可以只设置一个新的[`border-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-width)。
* 默认情况下，content的[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 被设置为可用空间的100%（在margin, border, padding占据了它们的空间后剩下的空间的宽度）——如果您更改了浏览器窗口的宽度，那么这些框将会变大或变小，以保持包含在示例输出窗口中。 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)默认设置为content的高度。
* 尝试给 [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main)元素设置一个新的宽度和高度——我们一开始可以设置为400px宽和200px高——然后看看效果！您会注意到，宽度不再随着浏览器窗口的大小而改变。
* 尝试设置[`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main)元素一个百分比的宽度——比如说60%——然后看看效果！您应该看到，随着浏览器窗口的大小调整，宽度现在又发生了变化。现在，删除 [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main)元素的 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)设置。
* 尝试设置你的 [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main)元素的内边距和外边距的各个边为5%，然后观察结果。如果您使用浏览器开发工具来查看示例输出窗口的宽度，并将其与内边距和外边距的宽度进行比较，你会发现这个5%意味着“包含的元素宽度的5%”。因此随着示例输出窗口的大小增加，内边距和外边距也增加了。
* 外边距可以接受负数，这可以用来引起元素框的重叠。尝试在 [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main)元素设置margin-top: -50px 然后看看效果。
* 继续尝试！

在 CodePen 中打开在 JSFiddle 中打开

一些提示及想法:

* 默认情况下[`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color)/[`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image) 延伸到了border的外边缘。该行为可以使用将在[Background\_clip](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#Background_clip) 章中学到的[`background-clip`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip) 属性来改变。
* 如果content框变得比示例输出窗口大，它将从窗口溢出，此时会出现滚动条，你可以滚动窗口来查看盒子剩余的内容 。你可以使用[`overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow)属性来控制溢出——参看下边的 [Overflow](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#Overflow) 章节。
* 框的高度不遵守百分比的长度；框的高度总是采用框内容的高度，除非指定一个绝对的高度（如：px 或者em），它会比在页面上默认是100%高度更实用。
* border也忽略百分比宽度设置。
* 你应该注意的是框的总宽度是[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width), [`padding-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-right), [`padding-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-left), [`border-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-right), 以及 [`border-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-left) 属性之和。在一些情况下比较恼人（例如，假使你想要一个框占窗口宽度的50%，但边界和内边距是用像素来表示时该怎么办？），为了避免这种问题，有可能使用属性[`box-sizing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing)来调整框模型。使用值`border-box`，它将框模型更改成这个新的模型：

![](https://mdn.mozillademos.org/files/13649/box-model-alt-small.png)

### 高级的框操作[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#%E9%AB%98%E7%BA%A7%E7%9A%84%E6%A1%86%E6%93%8D%E4%BD%9C) <a id="&#x9AD8;&#x7EA7;&#x7684;&#x6846;&#x64CD;&#x4F5C;"></a>

在设置框的width, height, border, padding 及margin之外， 还有一些其他的属性可以改变它们的行为。本节讨论这些其他的属性。

#### 溢流[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#%E6%BA%A2%E6%B5%81) <a id="&#x6EA2;&#x6D41;"></a>

当你使用绝对的值设置了一个框的大小（如，固定像素的宽/高），允许的大小可能不适合放置内容，这种情况下内容会从盒子溢流。我们使用[`overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow)属性来控制这种情况的发生。它有一些可能的值，但是最常用的是：

* `auto`: 当内容过多，溢流的内容被隐藏，然后出现滚动条来让我们滚动查看所有的内容。
* `hidden`: 当内容过多，溢流的内容被隐藏。
* `visible`: 当内容过多，溢流的内容被显示在盒子的外边（这个是默认的行为）

该示例展示了这些设置是如何工作的：

首先是HTML代码：

```text
<p class="autoscroll">
   Lorem ipsum dolor sit amet, consectetur adipiscing elit.
   Mauris tempus turpis id ante mollis dignissim. Nam sed
   dolor non tortor lacinia lobortis id dapibus nunc. Praesent
   iaculis tincidunt augue. Integer efficitur sem eget risus
   cursus, ornare venenatis augue hendrerit. Praesent non elit
   metus. Morbi vel sodales ligula.
</p>

<p class="clipped">
   Lorem ipsum dolor sit amet, consectetur adipiscing elit.
   Mauris tempus turpis id ante mollis dignissim. Nam sed
   dolor non tortor lacinia lobortis id dapibus nunc. Praesent
   iaculis tincidunt augue. Integer efficitur sem eget risus
   cursus, ornare venenatis augue hendrerit. Praesent non elit
   metus. Morbi vel sodales ligula.
</p>

<p class="default">
   Lorem ipsum dolor sit amet, consectetur adipiscing elit.
   Mauris tempus turpis id ante mollis dignissim. Nam sed
   dolor non tortor lacinia lobortis id dapibus nunc. Praesent
   iaculis tincidunt augue. Integer efficitur sem eget risus
   cursus, ornare venenatis augue hendrerit. Praesent non elit
   metus. Morbi vel sodales ligula.
</p>
```

然后是应用到HTML的CSS代码：

```text
p {
  width  : 400px;
  height : 2.5em;
  padding: 1em 1em 1em 1em;
  border : 1px solid black;
}

.autoscroll { overflow: auto;    }
.clipped    { overflow: hidden;  }
.default    { overflow: visible; }
```

上边的代码给出了以下的结果：

在 CodePen 中打开在 JSFiddle 中打开

#### 背景裁剪（Background clip）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#%E8%83%8C%E6%99%AF%E8%A3%81%E5%89%AA%EF%BC%88Background_clip%EF%BC%89) <a id="&#x80CC;&#x666F;&#x88C1;&#x526A;&#xFF08;Background_clip&#xFF09;"></a>

框的背景是由颜色和图片组成的，它们堆叠在一起（[`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color), [`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)）。 它们被应用到一个盒子里，然后被画在盒子的下面。默认情况下，背景延伸到了边界外沿。这通常是OK的，但是在一些情况下比较讨厌（假使你有一个平铺的背景图，你只想要它延伸到内容的边沿会怎么做？），该行为可以通过设置盒子的[`background-clip`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)属性来调整。

让我们通过一个示例来看看这个是怎么工作的。首先是我们的HTML代码：

```text
<div class="default"></div>
<div class="padding-box"></div>
<div class="content-box"></div>
```

然后是CSS代码:

```text
div {
  width  : 60px;
  height : 60px;
  border : 20px solid rgba(0, 0, 0, 0.5);
  padding: 20px;
  margin : 20px 0;

  background-size    : 140px;
  background-position: center;
  background-image   : url('https://mdn.mozillademos.org/files/11947/ff-logo.png');
  background-color   : gold;
}

.default     { background-clip: border-box;  }
.padding-box { background-clip: padding-box; }
.content-box { background-clip: content-box; }
```

上述代码产生以下结果：

在 CodePen 中打开在 JSFiddle 中打开

#### 轮廓\(Outline\)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#%E8%BD%AE%E5%BB%93%28Outline%29) <a id="&#x8F6E;&#x5ED3;(Outline)"></a>

最后，还有重要的一点， 一个框的 [`outline`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline) 是一个看起来像是边界但又不属于框模型的东西。它的行为和边界差不多，但是并不改变框的尺寸（更准确的说，轮廓被勾画于在框边界之外，外边距区域之内）

**Note**: 使用 outline 属性的时候要注意，它一般只在需要可用性的一些情况才被使用，例如在一些用户点击它的时候使用 outline 来表示高亮、可用，如果你要使用 outline，请确保不要因为它看起来像链接的高亮让用户迷惑。

### CSS 框类型[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#CSS_%E6%A1%86%E7%B1%BB%E5%9E%8B) <a id="CSS_&#x6846;&#x7C7B;&#x578B;"></a>

之前我们说的所有对于框的应用都表示的是块级元素的，然而，CSS还有一些表现不同的其他框类型。我们可以通过[`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display)属性来设定元素的框类型。[`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display)属性有很多的属性值。在本篇文章，我们将关注三个最常见的类型：`block`, `inline`, and `inline-block。`

* 块框（ `block` box）是定义为堆放在其他框上的框（例如：其内容会独占一行），而且可以设置它的宽高，之前所有对于框模型的应用适用于块框 （ `block` box）
* 行内框（ `inline` box）与块框是相反的，它随着文档的文字（例如：它将会和周围的文字和其他行内元素出现在同一行，而且它的内容会像一段中的文字一样随着文字部分的流动而打乱），对行内盒设置宽高无效，设置padding, margin 和 border都会更新周围文字的位置，但是对于周围的的块框（ `block` box）不会有影响。
* 行内块状框（`inline-block` box） 像是上述两种的集合：它不会重新另起一行但会像行内框（ `inline` box）一样随着周围文字而流动，而且他能够设置宽高，并且像块框一样保持了其块特性的完整性，它不会在段落行中断开。（在下面的示例中，行内块状框会放在第二行文本上，因为第一行没有足够的空间，并且不会突破两行。然而，如果没有足够的空间，行内框会在多条线上断裂，而它会失去一个框的形状。）

**注意：**默认状态下display属性值，块级元素`display: block` ，行内元素`display: inline`

这些东西在短时间听起来可能让你很混乱，现在让我们来看一些简单的小例子。

首先，HTML代码：

```text
<p>
   Lorem ipsum dolor sit amet, consectetur adipiscing elit.
   <span class="inline">Mauris tempus turpis id ante mollis dignissim.</span>
   Nam sed dolor non tortor lacinia lobortis id dapibus nunc.
</p>

<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit.
  <span class="block">Mauris tempus turpis id ante mollis dignissim.</span>
  Nam sed dolor non tortor lacinia lobortis id dapibus nunc.
</p>

<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit.
  <span class="inline-block">Mauris tempus turpis id ante mollis dignissim.</span>
  Nam sed dolor non tortor lacinia lobortis id dapibus nunc.
</p>
```

现在我们加一些CSS:

```text
p {
  padding : 1em;
  border  : 1px solid black;
}

span {
  padding : 0.5em;
  border  : 1px solid green;

  /* That makes the box visible, regardless of its type */
  background-color: yellow;
}

.inline       { display: inline;       }
.block        { display: block;        }
.inline-block { display: inline-block; }
```

上面的代码给出了这个结果，说明了显示类型的不同效果：

在 CodePen 中打开在 JSFiddle 中打开

### 下一步[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#%E4%B8%8B%E4%B8%80%E6%AD%A5) <a id="&#x4E0B;&#x4E00;&#x6B65;"></a>

在这一点上，您应该对CSS框及其工作方式有一定的了解。如果你现在还没有完全理解所有这些，不要担心，你可以重新阅读这篇文章以获得更好的理解，并且当你开始学习一些更实际的例子时，你会开始更好地理解事物。接下来，我们将介绍一下[调试CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS)。

### 另见[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model#%E5%8F%A6%E8%A7%81) <a id="&#x53E6;&#x89C1;"></a>

* [块格式化上下文（Block Formatting Context，BFC）](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context): The technical term for a CSS box laid out on a web page.
* [Visual formatting model](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Visual_formatting_model): An in depth explanation of the algorithm that lays out CSS boxes on a web page.

