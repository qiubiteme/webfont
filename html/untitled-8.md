# 在网页中添加矢量图形



矢量图形在很多情况下非常有用 — 它们拥有较小的文件尺寸，却高度可缩放，所以它们不会在镜头拉近或者放大图像时像素化。在这篇文章中，我们将为您呈现如何在网页中添加矢量图形。

| 前提： | 你需要了解 [HTML的基本知识](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML) 并且知道如何 [在你的文档中插入图片](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML). |
| :--- | :--- |
| 目标： | 了解如何嵌入 SVG \(矢量\) 图形到网页中。 |

**提示：** 本文的目的并不是教你 SVG；仅仅是告诉你它是什么，以及如何在网页中添加它。

### 什么是矢量图形？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E4%BB%80%E4%B9%88%E6%98%AF%E7%9F%A2%E9%87%8F%E5%9B%BE%E5%BD%A2%EF%BC%9F) <a id="&#x4EC0;&#x4E48;&#x662F;&#x77E2;&#x91CF;&#x56FE;&#x5F62;&#xFF1F;"></a>

在网上，你会和两种类型的图片打交道 — 位图和矢量图:

* 位图使用像素网格来定义 — 一个位图文件精确得包含了每个像素的位置和它的色彩信息。流行的位图格式包括 Bitmap \(`.bmp`\), PNG \(`.png`\), JPEG \(`.jpg`\), and GIF \(`.gif`.\)
* 矢量图使用算法来定义 — 一个矢量图文件包含了图形和路径的定义，电脑可以根据这些定义计算出当它们在屏幕上渲染时应该呈现的样子。 [SVG](https://developer.mozilla.org/en-US/docs/Glossary/SVG) 格式可以让我们创造用于 Web 的精彩的矢量图形。

为了让你清楚的认识到两者的区别，我们来一个例子。你可以在我们的 Github 仓库中在线查看这个例子：[vector-versus-raster.html](http://mdn.github.io/learning-area/html/multimedia-and-embedding/adding-vector-graphics-to-the-web/vector-versus-raster.html) — 它并排展示了两个看起来一致的图像，一个红色的五角星以及黑色的阴影。不同的是，左边的是 PNG，而右边的是 SVG 图像。

当你放大网页的时候，区别就会变得明显起来 — 随着你的放大，PNG 图片变得像素化了，因为它存储是每个像素的颜色和位置信息 — 当它被放大时，每个像素就被放大以填满屏幕上更多的像素，所以图像就会开始变得马赛克感觉。矢量图像看起来仍然效果很好且清晰，因为无论它的尺寸如何，都使用算法来计算出图像的形状，仅仅是根据放大的倍数来调整算法中的值。

![Two star images, one raster and one vector. At their default size they look identical](https://mdn.mozillademos.org/files/12866/raster-vector-default-size.png)

![Two star images zoomed in. The raster one on the left starts to look pixellated, whereas the vector one still looks crisp.](https://mdn.mozillademos.org/files/12868/raster-vector-zoomed.png)

**注意**: 上面的图片实际上都是 PNG 图片 —— 每个例子中左边的图片代表光栅图片，右边的星星代表矢量图。还有，访问 [vector-versus-raster.html](http://mdn.github.io/learning-area/html/multimedia-and-embedding/adding-vector-graphics-to-the-web/vector-versus-raster.html) 示例来查看真正的例子！

此外，矢量图形相较于同样的位图，通常拥有更小的体积，因为它们仅需储存少量的算法，而不是逐个储存每个像素的信息。

### SVG是什么？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#SVG%E6%98%AF%E4%BB%80%E4%B9%88%EF%BC%9F) <a id="SVG&#x662F;&#x4EC0;&#x4E48;&#xFF1F;"></a>

[SVG](https://developer.mozilla.org/zh-CN/docs/Web/SVG) 是用于描述矢量图像的[XML](https://developer.mozilla.org/en-US/docs/Glossary/XML)语言。 它基本上是像HTML一样的标记，除了你有许多不同的元素来定义你想要出现在图像中的形状，以及你想要应用于这些形状的效果。 SVG用于标记图形，而不是内容。 非常简单，你有一些元素来创建简单图形，如[`<circle>`](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Element/circle) 和[`<rect>`](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Element/rect)。更高级的SVG功能包括 [`<feColorMatrix>`](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Element/feColorMatrix)（使用变换矩阵转换颜色）[`<animate>`](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Element/animate) （矢量图形的动画部分）和 [`<mask>`](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Element/mask)（在图像顶部应用蒙版）

作为一个简单的例子，以下代码创建一个圆和一个矩形：

```text
<svg version="1.1"
     baseProfile="full"
     width="300" height="200"
     xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="black" />
  <circle cx="150" cy="100" r="90" fill="blue" />
</svg>
```

这将创建以下输出：

从上面的例子可以看出，SVG很容易手工编码。 是的，您可以在文本编辑器中手动编写简单的SVG，但是对于复杂的图像，这很快就开始变得非常困难。 为了创建SVG图像，大多数人使用矢量图形编辑器，如 [Inkscape](https://inkscape.org/en/) 或 [Illustrator](https://en.wikipedia.org/wiki/Adobe_Illustrator)。 这些软件包允许您使用各种图形工具创建各种插图，并创建照片的近似值（例如Inkscape的跟踪位图功能）。

SVG除了迄今为止所描述的以外还有其他优点：

* 矢量图像中的文本仍然可访问（这也有利于 [SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO)\)）。
* SVG 可以很好地适应样式/脚本，因为图像的每个组件都是可以通过CSS或通过JavaScript编写的样式的元素。

那么为什么会有人想使用光栅图形而不是SVG？ 其实 SVG 确实有一些缺点：

* SVG非常容易变得复杂，这意味着文件大小会增加; 复杂的SVG也会在浏览器中占用很长的处理时间。
* SVG可能比栅格图像更难创建，具体取决于您尝试创建哪种图像。
* 旧版浏览器不支持SVG，因此如果您需要在网站上支持旧版本的 IE，则可能不适合（SVG从IE9开始得到支持）。

由于上述原因，光栅图形更适合照片那样复杂精密的图像。

**注意：**在Inkscape中，将文件保存为纯SVG以节省空间。 另请参阅[如何为Web准备SVG](http://tavmjong.free.fr/INKSCAPE/MANUAL/html/Web-Inkscape.html)。

### 将SVG添加到页面[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E5%B0%86SVG%E6%B7%BB%E5%8A%A0%E5%88%B0%E9%A1%B5%E9%9D%A2) <a id="&#x5C06;SVG&#x6DFB;&#x52A0;&#x5230;&#x9875;&#x9762;"></a>

在本节中，我们将介绍将SVG矢量图形添加到网页的不同方式。

#### 快捷方式：[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F%EF%BC%9A%3Cimg%3E) <a id="&#x5FEB;&#x6377;&#x65B9;&#x5F0F;&#xFF1A;&lt;img&gt;"></a>

要通过 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)元素嵌入SVG，你只需要按照预期的方式在 src 属性中引用它。你将需要一个`height`或`width`属性（或者如果您的SVG没有固有的宽高比）。如果还没有这样做，请阅读[HTML中的图片](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML) 。

```text
<img 
    src="equilateral.svg" 
    alt="triangle with all three sides equal"
    height="87px"
    width="100px" />
```

**优点**

* 快速，熟悉的图像语法与`alt`属性中提供的内置文本等效。
* 可以通过在[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)元素嵌套`<img>`，使图像轻松地成为超链接。

**缺点**

* 无法使用JavaScript操作图像。
* 如果要使用CSS控制SVG内容，则必须在SVG代码中包含内联CSS样式。 （从SVG文件调用的外部样式表不起作用）
* 不能用CSS伪类来重设图像样式（如`:focus`）。

#### 疑难解答和跨浏览器支持[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E7%96%91%E9%9A%BE%E8%A7%A3%E7%AD%94%E5%92%8C%E8%B7%A8%E6%B5%8F%E8%A7%88%E5%99%A8%E6%94%AF%E6%8C%81) <a id="&#x7591;&#x96BE;&#x89E3;&#x7B54;&#x548C;&#x8DE8;&#x6D4F;&#x89C8;&#x5668;&#x652F;&#x6301;"></a>

对于不支持SVG（IE 8及更低版本，Android 2.3及更低版本）的浏览器，您可以从`src`属性引用PNG或JPG，并使用[`srcset`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-srcset)属性 只有最近的浏览器才能识别）来引用SVG。 在这种情况下，仅支持浏览器将加载SVG - 较旧的浏览器将加载PNG：

```text
<img src="equilateral.png" alt="triangle with equal sides" srcset="equilateral.svg">
```

您还可以使用SVG作为CSS背景图像，如下所示。 在下面的代码中，旧版浏览器会坚持他们理解的PNG，而较新的浏览器将加载SVG：

```text
background: url("fallback.png") no-repeat center;
background-image: url("image.svg");
background-size: contain;
```

像上面描述的`<img>`方法一样，使用 CSS 背景图像插入SVG 意味着它不能被 JavaScript 操作，并且也受到相同的 CSS 限制。

如果 SVG 根本没有显示，可能是因为你的服务器设置不正确。 如果是这个问题，[这篇文章](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Getting_Started#A_Word_on_Webservers)将告诉你正确方向。

#### 如何在HTML中引入SVG代码[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E5%A6%82%E4%BD%95%E5%9C%A8HTML%E4%B8%AD%E5%BC%95%E5%85%A5SVG%E4%BB%A3%E7%A0%81) <a id="&#x5982;&#x4F55;&#x5728;HTML&#x4E2D;&#x5F15;&#x5165;SVG&#x4EE3;&#x7801;"></a>

  
你还可以在文本编辑器中打开SVG文件，复制SVG代码，并将其粘贴到HTML文档中 - 这有时称为将**SVG内联**或**内联SVG**。确保您的SVG代码在[`<svg></svg>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg)标签中（不要在外面添加任何内容）。这是一个非常简单的示例，您可以粘贴到文档中：

```text
<svg width="300" height="200">
    <rect width="100%" height="100%" fill="green" />
</svg>
```

**优点**

* 将 SVG 内联减少 HTTP 请求，可以减少加载时间。
* 您可以为 SVG 元素分配`class`和`id`，并使用 CSS 修改样式，无论是在SVG中，还是 HTML 文档中的 CSS 样式规则。 实际上，您可以使用任何 [SVG外观属性](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Attribute#Presentation_attributes) 作为CSS属性。
* 内联SVG是唯一可以让您在SVG图像上使用CSS交互（如`:focus`）和CSS动画的方法（即使在常规样式表中）。
* 您可以通过将 SVG 标记包在[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)元素中，使其成为超链接。

**缺点**

* 这种方法只适用于在一个地方使用的SVG。多次使用会导致资源密集型维护（resource-intensive maintenance）。
* 额外的 SVG 代码会增加HTML文件的大小。
* 浏览器不能像缓存普通图片一样缓存内联SVG。
* 您可能会在[`<foreignObject>`](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Element/foreignObject) 元素中包含回退，但支持 SVG 的浏览器仍然会下载任何后备图像。你需要考虑仅仅为支持过时的浏览器，而增加额外开销是否真的值得。
* 
#### 如何使用  [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe) 嵌入SVG[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8_%3Ciframe%3E_%E5%B5%8C%E5%85%A5SVG) <a id="&#x5982;&#x4F55;&#x4F7F;&#x7528;_&lt;iframe&gt;_&#x5D4C;&#x5165;SVG"></a>

您可以在浏览器中打开 SVG 图像，就像网页一样。 因此，使用`<iframe>`嵌入 SVG 文档就像我们在 [从对象到iframe - 其他嵌入技术](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/%E5%85%B6%E4%BB%96%E5%B5%8C%E5%85%A5%E6%8A%80%E6%9C%AF) 中进行研究一样。

这是一个快速回顾：

```text
<iframe src="triangle.svg" width="500" height="500" sandbox>
    <img src="triangle.png" alt="Triangle with three unequal sides" />
</iframe>
```

这绝对不是最好的方法：

**缺点**

* 如你所知， `iframe`有一个回退机制，如果浏览器不支持`iframe`，则只会显示回退。
* 此外，除非 SVG 和您当前的网页具有相同的 [origin](https://developer.mozilla.org/en-US/docs/Glossary/origin)，否则你不能在主页面上使用 JavaScript 来操纵 SVG。

### 动手学习：使用SVG[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E5%8A%A8%E6%89%8B%E5%AD%A6%E4%B9%A0%EF%BC%9A%E4%BD%BF%E7%94%A8SVG) <a id="&#x52A8;&#x624B;&#x5B66;&#x4E60;&#xFF1A;&#x4F7F;&#x7528;SVG"></a>

在这个动手学习部分中，我们希望你能够体验一下 SVG 的乐趣。 在下面的“input”部分，您将看到我们已经提供了一些样例来开始使用。 您还可以访问 [SVG元素参考](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Element)，了解更多关于SVG可以使用的其他玩具的细节，也可以尝试一下。 这部分都是为了锻炼你的研究技巧，并且有一些乐趣。

如果你卡住了，无法使你的代码工作，你可以随时使用 Reset 按钮进行重置。

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

本文提供了一个矢量图形和 SVG 的快速浏览，让你了解他们的作用，以及如何在网页中引入 SVG。 它从来没有打算成为学习 SVG 的完整教程，只是一个指南，让你在网上遇到 SVG 时知道它是什么。 所以不要觉得你不是一个 SVG 专家而担心。如果你想了解更多关于它的工作原理，我们在下面列出了一些可能会帮助您的信息。

在本模块的最后一篇文章中，我们将详细探索响应式图像，查看 HTML 可以让您的图像在不同设备上更好地适配。

### 相关链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web#%E7%9B%B8%E5%85%B3%E9%93%BE%E6%8E%A5) <a id="&#x76F8;&#x5173;&#x94FE;&#x63A5;"></a>

* [SVG tutorial](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Getting_Started) on MDN
* [Quick tips for responsive SVGs](http://thenewcode.com/744/Making-SVG-Responsive)
* [Sara Soueidan's tutorial on responsive SVG images](http://tympanus.net/codrops/2014/08/19/making-svgs-responsive-with-css/)
* [Accessibility benefits of SVG](http://www.w3.org/TR/SVG-access/)
* [How to scale SVGs ](https://css-tricks.com/scale-svg/) （它不像光栅图形那么简单！）

