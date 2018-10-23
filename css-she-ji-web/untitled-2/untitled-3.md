# 盒模型概要

我们已经在[CSS模块介绍](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS)中了解过[CSS盒模型](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model) 的基础知识。 本文将在这个问题上重述部分概念并且对一些知识细节进一步深入讲述。

| 前置知识: | HTML 基础\(学习 [HTML介绍](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)\),，明白CSS是如何工作的 \(学习 [CSS介绍](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS).\) |
| :--- | :--- |
| 目的: | 重述CSS盒模型的基础并掌握更多相关细节知识。 |

### 盒子的属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E7%9B%92%E5%AD%90%E7%9A%84%E5%B1%9E%E6%80%A7) <a id="&#x76D2;&#x5B50;&#x7684;&#x5C5E;&#x6027;"></a>

我们都知道，文档中每一个元素在页面布局结构中均呈现为一个矩形的盒子，我们简化为下面这个模型：

![](https://mdn.mozillademos.org/files/13647/box-model-standard-small.png)

* [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 和[`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) 设置了内容框的宽/高
* [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) 家族属性设置内边距的宽度\(别忘了普通属性比如 [`padding-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-bottom) ，一次设置一个边\).
* [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) 家族属性设置边界的宽度、样式和颜色\(许多可用的普通边界属性还有很多\)。
* [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin) 家族属性设置包围CSS盒子外部区域的宽度，这个属性推开布局中其他的CSS盒子（也有许多可用的普通属性比如  [`margin-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-bottom) ）。

其它一些值得记住的点：

* 如果盒子的高度被设置为百分比长度，那么盒子高度不会遵循这个设置了的百分比长度，而是总会采用盒子内容的高度，除非给它设置了一个绝对高度（例如，像素或者 em）。这比把页面上每个盒子的高度默认设置为视口高度的 100% 更方便。
* 边界（border）也会忽略百分比宽度设置。
* 外边距（margin）有一个特殊的行为，称为 [外边距塌陷](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)： 当两个盒子挨在一起时，二者之间的距离为两个挨着的外边距中最大的那个值，而不是二者的和。

**注意**: 有关更完整的概述和示例，请参阅[盒模型文章的部分 _Box属性_部分](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Box_model#Box_properties)。

#### 溢出[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E6%BA%A2%E5%87%BA) <a id="&#x6EA2;&#x51FA;"></a>

当用绝对的值设置盒子的大小时（比如，固定像素的 width 和 height），内容可能会超出设置的大小，此时内容就会溢出盒子。要控制这时候发生的事情，我们可以使用 [`overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow) 属性。 该属性有几个可能的取值，不过最常用的是：

* `auto`：如果内容太多，那么超出盒子大小的内容会被隐藏，滚动条显示出来，从而可以让用户滚动看到所有内容。
* `hidden`：如果内容太多，那么超出盒子大小的内容被隐藏了。
* `visible`：如果内容太多，超出盒子大小的内容显示在盒子之外（这通常是默认的行为）。

**注**：有关更完整的概述和示例，请参阅 [盒模型文章的 _“溢流”_ 部分](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Box_model#Overflow)

#### 背景剪裁[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E8%83%8C%E6%99%AF%E5%89%AA%E8%A3%81) <a id="&#x80CC;&#x666F;&#x526A;&#x88C1;"></a>

盒背景由颜色和图像组成，堆叠在彼此之间\([`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color)，[`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)\)。它们被应用于一个盒并在该盒子下画。默认情况下，背景延伸到边界的外边缘。这通常很好，但在某些情况下可能会令人烦恼\(如果您有一个平铺的背景图片，您只想扩展到内容的边缘呢?\)这种行为可以通过设置[`background-clip`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)属性。

**注**: 示例请参阅 [盒模型文章背景裁剪部分](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Getting_started/Boxes)。

#### 轮廓[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E8%BD%AE%E5%BB%93) <a id="&#x8F6E;&#x5ED3;"></a>

盒子的 [`outline`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline) 看起来像边框，但是它不是盒模型的一部分。它表现得像边框，但是是画在盒子之上，不会修改盒子的大小（具体来说，ouline 是画在边框之外，外边距区域之内）。

**注意**: 当使用 outline 属性时要当心。在某些情况下，为了可访问性的原因，它会用作凸显网站可点击（active）部分，例如用户点击时的链接。如果您要使用 ouline 属性，请确保不要让它看起来像是点击时的链接，因为这会让用户混淆。

### 盒子的高级属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E7%9B%92%E5%AD%90%E7%9A%84%E9%AB%98%E7%BA%A7%E5%B1%9E%E6%80%A7) <a id="&#x76D2;&#x5B50;&#x7684;&#x9AD8;&#x7EA7;&#x5C5E;&#x6027;"></a>

现在我们已经做了一个简单回顾，下面我们来看看一些有用的更高级的盒子属性。

#### 设置宽和高的约束[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E8%AE%BE%E7%BD%AE%E5%AE%BD%E5%92%8C%E9%AB%98%E7%9A%84%E7%BA%A6%E6%9D%9F) <a id="&#x8BBE;&#x7F6E;&#x5BBD;&#x548C;&#x9AD8;&#x7684;&#x7EA6;&#x675F;"></a>

其它一些属性可以用更灵活的方式控制内容盒的大小  —  是通过设置大小约束，而不是设置一个绝对大小。这是通过属性 [`min-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/min-width)、[`max-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/max-width)、[`min-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/min-height) 和 [`max-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/max-height) 实现的。

一个明显的用处是，如果你想通过设置将一个布局的外层容器的宽度设置为百分比，从而让布局的宽度变得灵活，不过又不想让它变得太宽或者太窄，因为这样布局就开始看起来很糟糕。一个选择是用响应式网页设计技术（之后我们会讲到），但是更简单的方法是给布局的宽度设置一个最大值和最小值限制：

```text
width: 70%;
max-width: 1280px;
min-width: 480px;
```

您可以将这段代码与以下代码结合，可以将应用这段代码的容器在它的父容器内居中：

```text
margin: 0 auto;
```

0会使顶部和底部边距为0，而 `auto`（在这种情况下）共享父容器左右边距之间的可用空间使它居中。 最终的呈现的效果是：当父容器在最小和最大宽度限制内时，它将填满整个视口宽度；当父容器超过1280px宽度时，布局将保持在1280px宽，并开始在可用空间内居中。 当宽度低于480px时，视口将小于容器，您必须滚动才能看得到完全的内容。

以上的代码示例请见 [min-max-container.html](https://mdn.github.io/learning-area/css/styling-boxes/box-model-recap/min-max-container.html) \([查看源码](https://github.com/mdn/learning-area/tree/master/css/styling-boxes/box-model-recap)\).

`max-width` 的另一个很好的用法是将媒体（例如图像和视频）限制在容器内部。回到上面的例子，图像会引起一个问题——起初它的显示正常，但当容器变得比图像更窄时，图像开始溢流容器（因为它是一个固定的宽度）。 要应对这类图像的问题，我们可以在其上设置以下声明：

```text
display: block;
margin: 0 auto;
max-width: 100%;
```

前两条样式规则可以使它的展示行为像一个块元素并且在父容器内居中。真正神奇的是第三条——这个限制了图像的宽度使它的最大宽度与父容器的宽度相等。因此，当父容器宽度缩小到小于图像的宽度时，图像会一起缩小。

您可以在 [min-max-image-container.html](https://mdn.github.io/learning-area/css/styling-boxes/box-model-recap/min-max-image-container.html) \([看代码](https://github.com/mdn/learning-area/tree/master/css/styling-boxes/box-model-recap)\) 尝试以上修改过的代码。

**注意**: 这种技术向前兼容可运行于 Internet Explorer 7，所以具有很好的跨浏览器性。

#### 完全改变盒模型[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E5%AE%8C%E5%85%A8%E6%94%B9%E5%8F%98%E7%9B%92%E6%A8%A1%E5%9E%8B) <a id="&#x5B8C;&#x5168;&#x6539;&#x53D8;&#x76D2;&#x6A21;&#x578B;"></a>

一个盒子的总宽度是它的[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width)， [`padding-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-right)，[`padding-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-left)，[`border-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-right)和[`border-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-left)属性之和。 在某些情况下比较麻烦（例如，要是您想要一个总宽度为50％的盒子，包括以像素表示的边框和内边距怎么办？）为了避免这种问题，可以使用属性[`box-sizing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing)调整盒模型。 用值 `border-box`，它将盒模型更改为这样新的模型：

![](https://mdn.mozillademos.org/files/13649/box-model-alt-small.png)

我们来看一个生动的例子。 我们将设置两个相同的 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div)元素，赋予每个元素相同的width，border和padding。 我们还将使用一些 JavaScript 脚本来打印出每个盒子宽度的计算值（最终屏幕上的像素值）。 唯一的区别是底部的盒子我们给出`box-sizing: border-box`，顶部的盒子留着默认行为。

首先，HTML为：

```text
<div class="one"></div>
<div class="two"></div>
```

然后CSS为：

```text
html {
  font-family: sans-serif;
  background: #ccc;
}

.one, .two {
  background: red;
  width: 300px;
  height: 150px;
  padding: 20px;
  border: 10px solid black;
  margin: 20px auto;
}

.two {
  box-sizing: border-box;
}
```

最后，我们用 JavaScript 脚本计算了两个框的计算宽度值：

```text
var one = document.querySelector('.one');
var two = document.querySelector('.two');

function outputWH(box) {
  var width = box.offsetWidth;
  var height = box.offsetHeight;
  box.textContent = 'Width: ' + width + 'px, Height: ' + height + 'px.'
}

outputWH(one);
outputWH(two);
```

由上面的例子得出以下结果：

在 CodePen 中打开在 JSFiddle 中打开

那么这里发生了什么？ 正如你所料，第一个框的宽度和高度等于content + padding + border。 然而，第二个框的宽度和高度等于通过CSS设置在 content 的宽度和高度。 padding 和 border 并没有添加到总宽度和高度上；反而，他们占用一些内容的空间，使内容更小，并保持总体尺寸相同。

您还可以看到此示例在 [box-sizing-example.html](https://mdn.github.io/learning-area/css/styling-boxes/box-model-recap/box-sizing-example.html) \([看代码](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/box-model-recap/box-sizing-example.html)\)上运行.

### 盒子显示类型[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E7%9B%92%E5%AD%90%E6%98%BE%E7%A4%BA%E7%B1%BB%E5%9E%8B) <a id="&#x76D2;&#x5B50;&#x663E;&#x793A;&#x7C7B;&#x578B;"></a>

迄今为止我们所说的都是针对块级元素的盒子。不过，CSS 还有元素行为不同的其它类型的盒子。元素的盒子类型是由 [`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 属性指定的。

#### 常见的显示类型[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E5%B8%B8%E8%A7%81%E7%9A%84%E6%98%BE%E7%A4%BA%E7%B1%BB%E5%9E%8B) <a id="&#x5E38;&#x89C1;&#x7684;&#x663E;&#x793A;&#x7C7B;&#x578B;"></a>

 [`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 可以有很多种不同的值, 其中三种常见的值为 `block`, `inline`, 和 `inline-block`。

* 块盒\(`block` box\)是被定义为堆放在其它盒子之上的盒子（即盒子之前以及之后的内容出现在不同的行上），并且可以给它设置高度和宽度。上面所述的整个盒模型都适用于块盒。
* 行内盒（`inline` box）与块盒相反：它跟随文档的文本流堆放（即，它会与周围的文本和其它行内元素出现在同一行，并且其内容会像段落中的文本行一样，随着文本流换行）。宽度和高度设置对行内盒无效；在行内盒上的所有内边距、外边距和边界设置会改变周围文本的位置，但是不会影响周围块盒的位置。
* 行内块盒（`inline-block` box）介于前两者之间： 它会像行内盒一样，跟随周围的文本流堆放，不会在其前后创建换行；不过，它可以像块盒一样，使用宽度和高度设置大小，并且维护其块完整性 — 它不会跨段落行换行（对于一行文本容纳不下的行内盒，会落到第二行上，因为第一行上没有足够的空间容纳它，并且不会跨两行换行）。

块级元素默认设置为 `display: block;` ，行内元素默认设置为 `display: inline;` 。

**Note**: See [The box model article's Types of CSS boxes section](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Box_model#Types_of_CSS_boxes) for a more complete overview and an example.

#### 不常见的显示类型[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E4%B8%8D%E5%B8%B8%E8%A7%81%E7%9A%84%E6%98%BE%E7%A4%BA%E7%B1%BB%E5%9E%8B) <a id="&#x4E0D;&#x5E38;&#x89C1;&#x7684;&#x663E;&#x793A;&#x7C7B;&#x578B;"></a>

同时， [`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 属性也有一些不常用的值，在以后你将会遇到。其中一些已经出现了有一段时间，并且可以很好的被支持, 而另一些则比较新，不能够被很好的支持。这些值通常是为了使创建网页/网页应用更简单而被创造出来。最被关注的有这些:

* `display: table` — 允许你像处理table布局那样处理非table元素，而不是滥用HTML的&lt;table&gt;标签来达到同样的目的。了解更多相关信息，请查看 [CSS tables](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Introduction#CSS_tables)。
* `display: flex` — 允许你处理一些困扰CSS已久的一些传统布局问题，例如布置一系列弹性等宽容器或者垂直居中内容。了解更多相关信息，请查看 [Flexbox](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Flexbox)。
* `display: grid` — 给出一种简单实现CSS网格系统的方式，而在传统上它依赖于一些棘手难以处理的CSS网格框架，我们的 [CSS Grids](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Grids) 文章讲述了如何去运用传统的CSS网格框架。

### 下一步[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Box_model_recap#%E4%B8%8B%E4%B8%80%E6%AD%A5) <a id="&#x4E0B;&#x4E00;&#x6B65;"></a>

在一小段快速的概览之后，我们看了一些更加高级的用来操纵框（box）的CSS特性，并且接触了一些高级的布局特性，结束了这篇文章。在掌握了这些之后，我们现在将继续下去，来看看背景（background）。

