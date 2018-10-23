# 使用CSS的样式边框

再次，我们已经在这之前看过一些边界的简单的用法，如设置边界颜色和样式。 在这里，我们将提供一个简短的回顾，然后给出一个其他可用的方法，如圆角和边界图像。

| 准备条件: | HTML 基础 \(study [Introduction to HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)\), 以及CSS的工作原理\(study [Introduction to CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS).\) |
| :--- | :--- |
| 目的: | 了解有关元素边界的完整的用法。 |

### 边界回顾[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E8%BE%B9%E7%95%8C%E5%9B%9E%E9%A1%BE) <a id="&#x8FB9;&#x754C;&#x56DE;&#x987E;"></a>

正如您前面在课程中看到的，元素有一个边界，它位于元素的内边距\(padding\)和外边距\(margin\)之间。默认情况下，边界的大小为0，使其不可见，但可以设置边界的粗细、样式和颜色以使其显示出来。

#### 边界简写[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E8%BE%B9%E7%95%8C%E7%AE%80%E5%86%99) <a id="&#x8FB9;&#x754C;&#x7B80;&#x5199;"></a>

 [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)简写属性允许你一次将所有的这些都设置在四个边，例如：

```text
<p>I have a red border!</p>
```

```text
p {
  padding: 10px;
  background: yellow;
  border: 2px solid red;
}
```

在 CodePen 中打开在 JSFiddle 中打开

#### 普通写法选项[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E6%99%AE%E9%80%9A%E5%86%99%E6%B3%95%E9%80%89%E9%A1%B9) <a id="&#x666E;&#x901A;&#x5199;&#x6CD5;&#x9009;&#x9879;"></a>

`border`可以分解成许多不同的属性，以获得更具体的样式需求：

* [`border-top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top), [`border-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-right), [`border-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom), [`border-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-left): 设置边界一侧的宽度，样式和颜色。
* [`border-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-width), [`border-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-style), [`border-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-color): 设置边界宽度、样式或颜色，但是会设置边界的四个边。
* 您还可以单独三个属性中的一个并且设置其中一侧边界生效。 [`border-top-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top-width), [`border-top-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top-style), [`border-top-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top-color)等。

你可能想知道为什么有这么多的普通写法选项——好吧，让它们可用是很有用的，这样你就可以在不需要不断地重新定义每一种东西的情况下，重写或关闭单独的样式；从长远来看，它可以为您节省大量代码。同样值得知道的是，当没有明确设置值时，边界会默认使用文本的颜色，宽度为3px。

考虑到这一点，让我们来看看一个虚构书籍的写作进度计划的例子。每一章都由一个 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div)元素表示，该元素被设置为固定宽度，并包含章节号和标题。写作进度由以下关键字来表示：

* 未开始/不完整的章节是由点状的边界标记的。
* 那些已经写好但需要重新审视的章节，都是被虚线框所标记的。
* 完整的章节\(书面和回顾\)是由实线框标记的。
* 那些正在写的或是正在被评论的章节由红色粗实线框标记。

让我们来看看实现它的css：

```text
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

div {
  width: 220px;
  padding: 20px;
  margin: 10px;
  line-height: 2;
  background-color: yellow;
  text-align: center;
  display: inline-block;
}

.complete {
  border-style: solid;
}

.written {
  border-style: dashed;
}

.incomplete {
  border-style: dotted;
}

.writing, .review {
  border-bottom: 6px solid red;
}
```

这给了我们以下结果：

在 CodePen 中打开在 JSFiddle 中打开

我们没有使用太多的样式就完成这一任务。我们还没有在`div`规则上声明任何边界样式;  
我们只是使用了用来在编辑过程中传达不同点的特定类。我们依赖于边界的默认宽度和颜色，只是为`.complete`，`.written`和 `.incomplete`设置了样式。然后时那些有 `.writing` 或`.review` 的章节，我们必须为底部的边界指定整个属性集。这比为每个不同的框类型设置一个完整的边界更有效。

你可以在Github上找到这个例子[border-longhand.html](http://mdn.github.io/learning-area/css/styling-boxes/borders/border-longhand.html)（也可以看[源码](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/borders/border-longhand.html)）。

### 边界半径[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E8%BE%B9%E7%95%8C%E5%8D%8A%E5%BE%84) <a id="&#x8FB9;&#x754C;&#x534A;&#x5F84;"></a>

盒子上的圆角是网站上另一个非常受欢迎的功能——如此流行以至于浏览器实现了专门用于实现圆角的属性 : [`border-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius). 在此之前 \(需要用多个background images去完成\), 开发人员曾经要包裹每个盒子，他们希望在三个额外的&lt;div&gt;中加上圆角，并为这四个元素中的每个元素附加一个单独的圆角图形。 如果他们想要他们的盒子看起来灵动的，那就必须这么做。

**注意**: 你可能还必须这样做，如果你需要兼容旧的浏览器——[`border-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius)只支持Internet Explorer 9以上。但是缺少圆角不能阻止用户阅读你的内容，所以老浏览器的用户可以不用它们。

现在更容易了——您只需使用以下属性：

```text
border-radius: 20px;
```

在不同的角落放置不同大小的边界半径, 您可以指定两个，三个或四个值, 就像您使用 [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)and [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)一样:

```text
/* 1st value is top left and bottom right corners,
   2nd value is top right and bottom left  */
border-radius: 20px 10px;
/* 1st value is top left corner, 2nd value is top right
   and bottom left, 3rd value is bottom right  */
border-radius: 20px 10px 50px;
/* top left, top right, bottom right, bottom left */
border-radius: 20px 10px 50px 0;
```

作为最后一点，您还可以创建椭圆形角（x半径与y半径不同）。两个不同的半径用正斜杠（/）分隔，您可以将其与值的任意组合组合。例如:

```text
border-radius: 10px / 20px;
border-radius: 10px 30px / 20px 40px;
```

**注意** 您可以使用任何长度单位来指定边界半径，例如 ： px, rems, %.

**注意：** 还可以使用普通写法属性，分别设置框的每个角的边界半径：[`border-top-left-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top-left-radius)，[`border-top-right-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-top-right-radius)，[`border-bottom-left-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom-left-radius)和 [`border-bottom-right-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom-right-radius)。

#### 自主学习：玩转边界半径[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0%EF%BC%9A%E7%8E%A9%E8%BD%AC%E8%BE%B9%E7%95%8C%E5%8D%8A%E5%BE%84) <a id="&#x81EA;&#x4E3B;&#x5B66;&#x4E60;&#xFF1A;&#x73A9;&#x8F6C;&#x8FB9;&#x754C;&#x534A;&#x5F84;"></a>

对于这个自主学习，我们希望您在提供的元素上实现一些不同类型的边界半径。尝试添加：

* 每一个角落都有同样的圆角。
* 每个角落都有同样的椭圆角。
* 每个角落都有一个不同的圆角和椭圆角。
* 使用三个值语法使得每一个角落都有的圆角。
* 在左下角的一个圆角。
* 使用不同单位值的圆角，看它们的行为。百分比很有意思——为什么》

如果你犯了错误，你可以用Reset按钮来重置它。

在 CodePen 中打开在 JSFiddle 中打开

### 边界图像[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E8%BE%B9%E7%95%8C%E5%9B%BE%E5%83%8F) <a id="&#x8FB9;&#x754C;&#x56FE;&#x50CF;"></a>

最后，让我们看一下CSS中最新的\(和复杂的\)操作，用于操作边界—— [`border-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image)。这里的想法是，有时创建复杂的用户界面特性需要一个复杂的界面设计，而不仅仅是一个纯色。这可能是通过在另一个较大的元素的顶部覆盖一个元素，然后将背景图像应用到底部元素，伪造一个复杂的边界来创建的。或者在极端情况下，您甚至可能需要创建一个包含9个元素的3 x 3网格，其中的中心元素作为您的内容，以及周围的8个元素，将边界元素应用于它们。

[`border-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image)图像使实现复杂的图形边界变得容易得多，即使必须在现代浏览器中才能实现\(Internet Explorer 11+支持它，以及其他现代浏览器\)。让我们来看看它是如何工作的。

首先，您需要有一个映像应用到您的浏览器。这通常是3 x 3、4 x 4、5 x 5\(等等\)网格设计，如下所做的：

![](https://mdn.mozillademos.org/files/13060/border-image.png)

当这样的图像用于边界图像时，浏览器将图像分割为8个部分，如下一个图像所示：

![](https://mdn.mozillademos.org/files/13062/border-slices.png)这些角的图像会被插入到你的边界的角落里，而顶部、右边、底部和左边的部分将被用来填充你的边界的相应边\(通过拉伸或重复\)。我们需要告诉浏览器让这些片的大小正确——例如，这个图像是160px，还有一个4 x 4的网格，所以每个片都需要40px。

首先，我们需要一个盒子来应用边界。这需要指定一个边界，否则边界图像将没有显示的空间。我们还将使用[`background-clip`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)，使任何背景色只填充内容和内边距的区域，并且不扩展到边界\(您可能不希望这样做，但是在这样的情况下是有用的\)。

```text
border: 30px solid black;
background-clip: padding-box;
```

**注意：**您应该始终包括[`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)定义，以及任何使用[`border-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image)——如果浏览器不支持该特性，则该操作可以作为一个回退，以防止边界图像无法显示。

接下来,我们将使用 [`border-image-source`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-source)指定要使用的源图像作为边界图像。 它的工作原理和[`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)一样，能够接受一个`url()`函数或一个渐变作为一个值。

```text
border-image-source: url(border-image.png);
```

现在，我们将使用[`border-image-slice`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-slice)来设置所需大小的切片，如上所述：

```text
border-image-slice: 40;
```

如果所有的片都是相同的大小，那么这个属性可以取一个值，如果需要不同的大小，则可以使用多个值，以相同的方式使用[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)和[`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)：

* 两个值:上和下，左和右。
* 三个值:上、左和右、下。
* 四个值:上、右、下、左。

如果图像是光栅图形（像 `.png` 或 `.jpg`），就用像素来解释这个数字。如果图像是矢量图形（比如，`.svg`），那么这个数字将被解释为图形中的坐标。也可以使用百分比（使用单位 `%`）。查看 [`border-image-slice`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-slice)页面，获得更多的选项和详细信息。

**注意：**默认情况下，第9部分的中间部分被完全省略，而元素内容出现在剩下的空白中。如果您想要的是边界图像的中心，您可以通过在您的[`border-image-source`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-source)的末尾包含关键字`fill`，在这种情况下，它将扩展到适合背景区域。

最后，我们将使用[`border-image-repeat`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-repeat) t来指定我们希望图像如何填充边界。选项是：

* `stretch`：默认;侧面的图像被拉伸来填满边界。这通常看起来很糟糕和像素化，所以不推荐。
* `repeat`：边图像被重复，直到边界被填满。根据具体情况，这可能看起来不错，但您可能会看到一些难看的图像片段。
* `round`： 边的图像被重复，直到边界被填满，它们都被稍微拉伸，这样就不会出现碎片。
* `space`：边图像被重复，直到边界被填满，每个拷贝之间添加了少量的间隔，这样就不会出现任何片段。这个值只在Safari\(9+\)和Internet Explorer\(11+\)中得到支持。

我们决定使用`round`的值，因为它看起来是最有用和最灵活的：

```text
border-image-repeat: round;
```

#### 把这些结合在一起[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E6%8A%8A%E8%BF%99%E4%BA%9B%E7%BB%93%E5%90%88%E5%9C%A8%E4%B8%80%E8%B5%B7) <a id="&#x628A;&#x8FD9;&#x4E9B;&#x7ED3;&#x5408;&#x5728;&#x4E00;&#x8D77;"></a>

让我们将所有这些代码放在一起，以显示一个工作示例。首先,一些简单的HTML：

```text
<div>
  <p>Border image</p>
</div>
```

现在是我们的CSS：

```text
div {
  width: 300px;
  padding: 20px;
  margin: 10px auto;
  line-height: 3;
  background-color: #f66;
  text-align: center;
  /* border-related properties */
  border: 20px solid black;
  background-clip: padding-box;
  border-image-source: url(https://mdn.mozillademos.org/files/13060/border-image.png);
  border-image-slice: 40;
  border-image-repeat: round;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

有趣的是，你可能已经注意到，边界设置为20px宽，而图像的宽度为40——在这种情况下，浏览器只调整大小为20px宽，这样就可以了。

你可以在Github上找到本例 [border-image.html](http://mdn.github.io/learning-area/css/styling-boxes/borders/border-image.html) \(也可以见 [源码](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/borders/border-image.html) \)。 制作一份当地的拷贝，然后自己玩玩它。

#### 其他属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E5%85%B6%E4%BB%96%E5%B1%9E%E6%80%A7) <a id="&#x5176;&#x4ED6;&#x5C5E;&#x6027;"></a>

两个不常用的边界图像属性如下：

* [`border-image-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-width)：只调整边界图像，而不是边界——如果这个设置小于[`border-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-width)，它会在边界的外面，而不是填满它。如果它更大，那么它就会扩展到边界之外，并开始重叠在内边距/内容上。
* [`border-image-outset`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-outset)：定义边界内部和内边距之间的额外空间的大小——有点像“边界填充”。如果需要的话，这是一种简单的方法，可以将边界图像移出一点。

#### 简写[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E7%AE%80%E5%86%99) <a id="&#x7B80;&#x5199;"></a>

如您所料，有一个可用的简写属性， [`border-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image)，这允许您在一行中设置所有相关的值。见下面的代码行：

```text
border-image-source: url(border-image.png);
border-image-slice: 40;
border-image-repeat: round;
```

可以被这一行取代：

```text
border-image: url(border-image.png) 40 round;
```

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Borders#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

现在你理解了边界（border），对吧？它的意思不是国家的国界线而是元素的边界线。理解边界是很有用的，并且有许多不同的用途。在接下来的文章中，我们将采取一个横向的步骤，并探索样式表的最佳实践——这将展示我们目前在模块中所看到的一些技术的有用应用程序。

