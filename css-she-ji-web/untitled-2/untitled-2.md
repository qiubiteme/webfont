# 使用CSS改变背景样式



在CSS中，你可以做很多来设计你内容背后的背景。我们已经看了一些简单的用法，比如基本的背景颜色和图像。在本文中，我们将讲述整个故事，并查看一些高级的特性，比如多个背景图像和颜色梯度。

| 预备知识： | HTML基础 \(学习 [Introduction to HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)\)，以及明白CSS是如何工作的\(学习 [Introduction to CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS).\) |
| :--- | :--- |
| 目标： | 要详细了解样式元素的背景。 |

### 什么是背景？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E4%BB%80%E4%B9%88%E6%98%AF%E8%83%8C%E6%99%AF%EF%BC%9F) <a id="&#x4EC0;&#x4E48;&#x662F;&#x80CC;&#x666F;&#xFF1F;"></a>

元素的背景是指，在元素内容、内边距和边界下层的区域。默认情况下就是这样——在新的浏览器中，你可以使用 [`background-clip`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)属性改变背景所占用的区域（更多细节见 [CSS box model article background-clip coverage](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Box_model#Background_clip)）。

背景并不在外边距下层——外边距不是元素区域的一部分，而是元素外面的区域。

还有很多其他的属性可以用来操作元素的背景，其中一些已经在我们的课程中已经见过很多次了：

* [`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color): 为背景设置一个纯色。
* [`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image): 指定在元素的背景中出现的背景图像。 这可以是静态文件，也可以是生成的渐变。
* [`background-position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-position):指定背景应该出现在元素背景中的位置。
* [`background-repeat`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-repeat): 指定背景是否应该被重复\(平铺\)。
* [`background-attachment`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-attachment): 当内容滚动时，指定元素背景的行为，例如，它是滚动的内容，还是固定的?
* [`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background): 在一行中指定以上五个属性的缩写。
* [`background-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-size): 允许动态调整背景图像的大小。

**注意：**大多数的这些功能都有很好的浏览器支持，除了最后两个，支持的功能比较有限\(Internet Explorer 9+，Safari 7+，Android 4.4+\)和背景渐变\(Internet Explorer 9+\)。

在本文的其余部分中，我们将详细介绍如何使用这些特性。

### 基本内容：color, image, position, repeat[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E5%9F%BA%E6%9C%AC%E5%86%85%E5%AE%B9%EF%BC%9Acolor_image_position_repeat) <a id="&#x57FA;&#x672C;&#x5185;&#x5BB9;&#xFF1A;color_image_position_repeat"></a>

让我们来探索一个简单的例子，展示四个最基本的属性是如何工作的，您将在处理背景时使用这些属性。

#### 背景颜色[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%83%8C%E6%99%AF%E9%A2%9C%E8%89%B2) <a id="&#x80CC;&#x666F;&#x989C;&#x8272;"></a>

你会经常使用 [`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color)属性：

* 首先，大多数元素的默认背景颜色不是`white` \(白色，这可能如你所料\) 而是`transparent`（透明）——因此，如果您将一个元素的背景颜色设置为一些有趣的东西，但是希望它的子元素是白色的，那么您就必须明确地设置它。
* 此外，设置背景颜色作为后备也是很重要的。背景颜色在各处都得到了支持，而背景梯度等更奇异的特性只在较新的浏览器中得到支持，加上背景图像可能由于某种原因无法加载。因此，设置基本的背景颜色和指定这些特性是一个好主意，因此无论如何，元素的内容都是可读的。

让我们从构建一个示例开始。我们从一些简单的HTML开始：

```text
<p>Exciting box!</p>
```

我们给它一个背景色：

```text
p {
  font-family: sans-serif;
  padding: 20px;
  /* background properties */
  background-color: yellow;
}
```

其结果如下：

在 CodePen 中打开在 JSFiddle 中打开

#### 背景图像[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%83%8C%E6%99%AF%E5%9B%BE%E5%83%8F) <a id="&#x80CC;&#x666F;&#x56FE;&#x50CF;"></a>

 [`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image) 属性指定了在元素背景中显示的背景图像。该属性最简单的用法是使用 `url()` 函数——它以一个参数的路径作为参数——获取一个静态图像文件来插入。让我们为上面的例子添加一个背景图像：

```text
p {
  font-family: sans-serif;
  padding: 20px;
  /* background properties */
  background-color: yellow;
  background-image: url(https://mdn.mozillademos.org/files/13026/fire-ball-icon.png);
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

在默认情况下，图像在水平和垂直方向上都是重复的，这看起来不太好。我们可以使用[`background-repeat`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-repeat)来修复这个问题，我们将在下一节中对此进行讨论。

**注意：**[HTML 图像](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)支持的任何图像格式都在CSS背景图像中支持，包括SVG。

需要记住的一件重要的事情是，由于背景图像是使用CSS设置的，并且出现在内容的背景中，它们将会在屏幕阅读器之类的辅助技术中不可见。它们不是内容图片，只是为了装饰，如果你想在你的页面上包含一个图片，这是内容的一部分，那么你应该用[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)元素来做。

#### 背景重复[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%83%8C%E6%99%AF%E9%87%8D%E5%A4%8D) <a id="&#x80CC;&#x666F;&#x91CD;&#x590D;"></a>

[`background-repeat`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-repeat) 允许您指定背景图像是如何重复的。默认值是`repeat`，正如您在上面所看到的，它使图像一直重复，直到整个元素的背景被填充。在这种情况下，这不是我们想要的\(虽然可能在某些情况下是，例如，[repeating-background.html](http://mdn.github.io/learning-area/css/styling-boxes/backgrounds/repeating-background.html)\)。其他常见的和广泛支持的值是：

* `no-repeat`: 图像将不会重复:它只会显示一次。
* `repeat-x`: 图像将在整个背景中水平地重复。
* `repeat-y`: 图像会在背景下垂直地重复。
* `repeat`: 图像将在整个背景中水平和竖直地重复。

让我们解决我们的例子：

```text
p {
  font-family: sans-serif;
  padding: 20px;
  /* background properties */
  background-color: yellow;
  background-image: url(https://mdn.mozillademos.org/files/13026/fire-ball-icon.png);
  background-repeat: no-repeat;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

这当然看起来更好，但是图像的定位是关闭的，它现在重叠了文本。我们需要把它放在一个更好的地方。

#### 背景位置：[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%83%8C%E6%99%AF%E4%BD%8D%E7%BD%AE%EF%BC%9A) <a id="&#x80CC;&#x666F;&#x4F4D;&#x7F6E;&#xFF1A;"></a>

[`background-position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-position) 允许我们在背景中任意位置放置背景图像。通常，该属性将使用两个通过空格分隔的值，该空间指定了图像的水平\(x\)和垂直\(y\)坐标。图像的左上角是原点\(0,0\)。把背景想象成一个图形，x坐标从左到右，y坐标从上到下。

该属性可以接受许多不同的值类型，最常用的是：

* 像px这样的绝对值——比如 `background-position: 200px 25px`.
* 像rems 这样的相对值——比如 `background-position: 20rem 2.5rem`.
* 百分比 ——比如 `background-position: 90% 25%`.
* 关键字——比如 `background-position: right center`. 这两个值是直观的，可以分别取值比如 `left`，`center`， `right`和 `top`，`center`， `bottom`。

您应该注意，您可以混合并匹配这些值，比如 `background-position: 99% center`。还要注意，如果您只指定一个值，那么该值将被假定为水平值，而垂直值将默认为`center`。 

让我们来修正我们的例子：

```text
p {
  font-family: sans-serif;
  padding: 20px;
  /* background properties */
  background-color: yellow;
  background-image: url(https://mdn.mozillademos.org/files/13026/fire-ball-icon.png);
  background-repeat: no-repeat;
  background-position: 99% center;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

### 背景图像：渐变[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%83%8C%E6%99%AF%E5%9B%BE%E5%83%8F%EF%BC%9A%E6%B8%90%E5%8F%98) <a id="&#x80CC;&#x666F;&#x56FE;&#x50CF;&#xFF1A;&#x6E10;&#x53D8;"></a>

 [`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)还有另一组可用的值——颜色渐变，渐变就是在背景中平滑的颜色过渡。动态生成的渐变是在不久之前引入的，这是因为在web设计中使用渐变是非常受欢迎的，但是使用背景图像来实现渐变是相当不灵活的。目前有两种类型的渐变——线性渐变\(从一条直线到另一条直线\)和径向渐变\(从一个点发散出来\)。

在本文中，我们只关注第一种类型。第二种方法比较复杂，也不太常用。您可以在本文末尾的链接中找到更多关于两者的信息。

线性渐变是通过`linear-gradient()`函数传入的，它是一个[`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)属性的值。函数至少需要用逗号分隔的三个参数——背景中渐变的方向，开始的颜色和结尾的颜色。例如：

```text
div {
background-image: linear-gradient(to bottom, orange, yellow);
}
```

这个渐变将从上到下，从顶部的橙色开始，然后平稳过渡到底部的黄色。可以使用关键字来指定方向 （`to bottom`，`to right`， `to bottom right`等）， 或角度值 \(`0deg`相当于 `to top`，`90deg` 相当于 `to right`，直到 `360deg`，它再次相当于 `to top` ）。

你也可以在颜色定义的渐变中指定其他的点——这些被称为颜色站点\(**color stops\)，**浏览器会计算出每一组颜色站点之间的颜色渐变。比如：

```text
div {
background-image: linear-gradient(to bottom, yellow, orange 40%, yellow);
}
```

这个渐变会从上到下运行，从黄色开始，向下渐变到橙色的40%，然后再回到黄色，达到100%。您可以指定任意多个颜色站点，您也可以使用其他的单位来指定这些颜色站点的位置，例如`rem`，`px`等。

让我们为我们的例子添加一个线性渐变：

```text
p {
  font-family: sans-serif;
  padding: 20px;
  /* background properties */
  background-color: yellow;
  background-image: linear-gradient(to bottom, yellow, #dddd00 50%, orange);
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

注意，您还可以使用`repeating-linear-gradient()`函数来设置一个重复的线性渐变。它的工作方式完全相同，只不过你设置的模式会不断重复，直到背景的边沿。例如：

```text
background-image: repeating-linear-gradient(to right, yellow, orange 25px, yellow 50px);
```

这将会产生一个渐变，从黄色到橙色，再沿着渐变的每50个像素再回来。

### 背景附着[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%83%8C%E6%99%AF%E9%99%84%E7%9D%80) <a id="&#x80CC;&#x666F;&#x9644;&#x7740;"></a>

另一个可供选择的选项是指定当内容滚动时它们是如何滚动的。这是使用[`background-attachment`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-attachment)属性来控制的，该属性可以使用以下值：

* `scroll`: 会使元素的背景在页面滚动时滚动。如果元素内容滚动了，背景并不会滚动。实际上，背景固定在了页面上相同的位置，所以当页面滚动时它才滚动。
* `fixed`: 会使元素的背景相对于视口固定。因此不管当页面还是元素内容滚动时，它都不会滚动，它会始终保持在屏幕上相同的位置。
* `local`:这个值后来被添加了\(它只在Internet Explorer 9+中得到支持，而其他的则在IE4+中得到支持\)，因为`scroll`值相当混乱，并且在许多情况下并没有真正做您想要的事情。  `local` 值将背景设置为它所设置的元素的背景，因此当您滚动元素时，背景会随之滚动。

 [`background-attachment`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-attachment) 只有当有内容要滚动时，属性才会有效果，所以我们做了一个演示来演示这三个值之间的区别——你可以看 [background-attachment.html](http://mdn.github.io/learning-area/css/styling-boxes/backgrounds/background-attachment.html)（也可以在这里[看源码](https://github.com/mdn/learning-area/tree/master/css/styling-boxes/backgrounds)）。

### 背景简写[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%83%8C%E6%99%AF%E7%AE%80%E5%86%99) <a id="&#x80CC;&#x666F;&#x7B80;&#x5199;"></a>

可以通过使用[`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background)属性来声明上面讨论的所有属性值\(以及在更新的浏览器中的其他一些属性值\)。要做到这一点，你要使用和你在单个属性中所做的相同的值，但是你把它们都放在一个由空格分隔的行上，就像这样：

```text
div {
background: yellow linear-gradient(to bottom, orange, yellow) no-repeat left center scroll;
}
```

任何在简写中没有指定的属性都将被指定为默认值。您可以查看[`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background) 参考页面，以了解这些默认值是什么，以及可以包含在`background`简写中的其他属性。

让我们回到我们精彩的盒子示例，用简写替换现有的属性。我们可以替换所有这些属性：

```text
div {
background-color: yellow;
background-image: linear-gradient(to bottom, yellow, #dddd00 50%, orange);
background-repeat: no-repeat;
background-position: 99% center;
}
```

用这个：

```text
div {
background: yellow linear-gradient(to bottom, yellow, #dddd00 50%, orange) no-repeat 99% center;
}
```

最后的代码看起来是这样的：

```text
p {
  font-family: sans-serif;
  padding: 20px;
  /* background properties */
  background: yellow linear-gradient(to bottom, yellow, #dddd00 50%, orange) no-repeat 99% center;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

### 多个背景[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E5%A4%9A%E4%B8%AA%E8%83%8C%E6%99%AF) <a id="&#x591A;&#x4E2A;&#x80CC;&#x666F;"></a>

最近\(自从Internet Explorer 9\)，我们已经具备了将多个背景连接到单个元素的能力。这是一件好事，因为多重背景非常有用。用逗号分隔不同的背景定义：

```text
div {
background: url(image.png) no-repeat 99% center,
            url(background-tile.png),
            linear-gradient(to bottom, yellow, #dddd00 50%, orange);
background-color: yellow;
}
```

这些背景都是堆叠在一起的，第一个出现在顶部，第二个在下面，第三个，等等。这可能不是你所期待的，所以要小心。还要注意的是，我们已经将后备背景颜色放入一个单独的属性声明中，因为尝试将其包含在多个背景中似乎会破坏一些东西。

你也可以将多个值放入到普通写法的 `background-*`属性中，比如：

```text
background-image: url(image.png), url(background-tile.png);
background-repeat: no-repeat, repeat;
```

尽管使用`background` 简写可能更好——它不仅可以更快地编写，而且更容易查看哪些背景属性应用到哪个背景。

以前有多个背景时，web开发人员必须在他们的框中放置多个 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div)元素，然后对每个元素应用单独的背景图像：

```text
<div class="background1">
  <div class="background2">
    <div class="background3">
      <p>My content</p>
    </div>
  </div>
</div>
```

这是有效的，但是它导致了非常混乱的难以阅读的标记。如果您需要支持旧版本的Internet Explorer，您可能仍然需要这样做。

让我们把多个背景放在我们精彩的盒子上——我们想要看到渐变和火球，两者同时出现：

```text
p {
  font-family: sans-serif;
  padding: 20px;
  /* background properties */
  background-color: yellow;
  background: url(https://mdn.mozillademos.org/files/13026/fire-ball-icon.png) no-repeat 99% center,
              linear-gradient(to bottom, yellow, #dddd00 50%, orange);
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

**Note**: 你可以 [在Github上看到完整的示例](http://mdn.github.io/learning-area/css/styling-boxes/backgrounds/) \(也可以看[源码](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/backgrounds/index.html)\)。

### 背景尺寸[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%83%8C%E6%99%AF%E5%B0%BA%E5%AF%B8) <a id="&#x80CC;&#x666F;&#x5C3A;&#x5BF8;"></a>

正如我们之前提到的，有一个可用的属性——[`background-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-size) ——它允许你动态地改变背景图像的大小，使它更适合你的设计。这在很多方面都很有用，例如自动纠正没有正确上传的图标的大小。请记住，这并不支持Internet Explorer低于9的版本，所以如果您需要支持旧的浏览器，那么您就不能依赖它。对于每个背景图像，您需要包含两个背景大小值，一个用于水平维度，另一个用于垂直方向：

```text
background-image: url(myimage.png);
background-size: 16px 16px;
```

你可以使用你期望的所有长度单位来指定你想要的值——`px`，百分比， `rem`等。

你可以看到`background-size`在[Including icons on links](https://developer.mozilla.org/zh-CN/Learn/CSS/Styling_text/Styling_links#Including_icons_on_links)中使用的一个很好的例子。

### 自主学习： 玩转背景[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0%EF%BC%9A_%E7%8E%A9%E8%BD%AC%E8%83%8C%E6%99%AF) <a id="&#x81EA;&#x4E3B;&#x5B66;&#x4E60;&#xFF1A;_&#x73A9;&#x8F6C;&#x80CC;&#x666F;"></a>

这个自主学习阶段也没有正确的答案，我们想让你在你继续之前玩一些背景和玩一些有趣的游戏。你可以：

* 设置不同的背景颜色。
* 包含一个不同的背景图像，找到一个在`url()`函数中使用的图像的绝对路径。
* 应用背景渐变。
* 应用多个背景。
* 包括一个`background-size`的属性来改变你的背景图片的大小。

如果你是作为一个班级或学习小组的一员，你的老师或导师也可能会为你完成一些额外的任务。

如果犯了错误，你随时可以使用 _Reset_  按钮来重置它。

在 CodePen 中打开在 JSFiddle 中打开

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

这篇文章应该已经教会你大部分需要了解的关于样式元素背景的知识。希望你也能在这个过程中找到乐趣！在下一篇文章中，我们将讨论边界问题，并研究如何对其进行样式化。

### 另见[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/%E8%83%8C%E6%99%AF#%E5%8F%A6%E8%A7%81) <a id="&#x53E6;&#x89C1;"></a>

* [CSS Linear Gradients](https://dev.opera.com/articles/css3-linear-gradients/)
* [CSS3 Radial Gradients](https://dev.opera.com/articles/css3-radial-gradients/)

