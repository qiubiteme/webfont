# 高级区块效果

这篇文章展示了盒子的小技巧，提供了一些高级特性的介绍，这些特性不适合其他类别的样式，比如盒子阴影、混合模式和过滤器。

| 预备知识： | HTML 基础\(学习 [Introduction to HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)\) ，了解CSS工作原理 \(学习 [Introduction to CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS).\) |
| :--- | :--- |
| 目标： | 要了解如何使用高级的盒子效果，并了解一些在CSS语言中出现的新样式工具。 |

### 盒子阴影[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#%E7%9B%92%E5%AD%90%E9%98%B4%E5%BD%B1) <a id="&#x76D2;&#x5B50;&#x9634;&#x5F71;"></a>

回到我们的[样式化文本](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_text)模块，我们查看了[`text-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow)属性，它允许您将一个或多个阴影应用到元素的文本上。对于盒子来说，存在一个等价的属性——[`box-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow)允许您将一个或多个阴影应用到一个实际的元素盒子中。和文本阴影一样，盒子的阴影在各种浏览器中也得到了很好的支持，但只有在IE9+（IE9及更新版本）中可用。你的旧IE版本的用户可能只需要应付没有阴影的情况，所以只要测试一下你的设计，确保你的内容在没有他们的情况下是清晰可见的。

你可以 [box-shadow.html](http://mdn.github.io/learning-area/css/styling-boxes/advanced_box_effects/box-shadow.html)在这部分找到例子 \(见[源码](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/advanced_box_effects/box-shadow.html)\)。

#### 一个简单的盒子阴影[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#%E4%B8%80%E4%B8%AA%E7%AE%80%E5%8D%95%E7%9A%84%E7%9B%92%E5%AD%90%E9%98%B4%E5%BD%B1) <a id="&#x4E00;&#x4E2A;&#x7B80;&#x5355;&#x7684;&#x76D2;&#x5B50;&#x9634;&#x5F71;"></a>

让我们看一个简单的例子来起步。首先,一些HTML：

```text
<article class="simple">
  <p><strong>Warning</strong>: The thermostat on the cosmic transcender has reached a critical level.</p>
</article>
```

现在是 CSS:

```text
p {
  margin: 0;
}

article {
  max-width: 500px;
  padding: 10px;
  background-color: red;
  background-image: linear-gradient(to bottom, rgba(0,0,0,0), rgba(0,0,0,0.25));
}  

.simple {
  box-shadow: 5px 5px 5px rgba(0,0,0,0.7);
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

你会看到，我们在`box-shadow`属性值中有4个项：

1. 第一个长度值是水平偏移量（**horizontal offset** ）——即向右的距离，阴影被从原始的框中偏移\(如果值为负的话则为左\)。
2. 第二个长度值是垂直偏移量（**vertical offset**）——即阴影从原始盒子中向下偏移的距离\(或向上，如果值为负\)。
3. 第三个长度的值是模糊半径（**blur radius**）——在阴影中应用的模糊度。
4. 颜色值是阴影的基本颜色（**base color**）。

你可以使用任何长度和颜色单位来定义这些值。

#### 多个盒子阴影[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#%E5%A4%9A%E4%B8%AA%E7%9B%92%E5%AD%90%E9%98%B4%E5%BD%B1) <a id="&#x591A;&#x4E2A;&#x76D2;&#x5B50;&#x9634;&#x5F71;"></a>

还可以在单个`box-shadow`声明中指定多个框阴影，用逗号分隔：

```text
p {
  margin: 0;
}

article {
  max-width: 500px;
  padding: 10px;
  background-color: red;
  background-image: linear-gradient(to bottom, rgba(0,0,0,0), rgba(0,0,0,0.25));
}  

.multiple {
  box-shadow: 1px 1px 1px black,
              2px 2px 1px black,
              3px 3px 1px red,
              4px 4px 1px red,
              5px 5px 1px black,
              6px 6px 1px black;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

我们在这里做了一些有趣的事情，创建了一个带有多个颜色图层的凸起的盒子，但是你可以用任何你想要的方式来使用它，例如，用基于多个光源的阴影来创建一个更加真实的外观。

#### 其他盒子阴影特点[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#%E5%85%B6%E4%BB%96%E7%9B%92%E5%AD%90%E9%98%B4%E5%BD%B1%E7%89%B9%E7%82%B9) <a id="&#x5176;&#x4ED6;&#x76D2;&#x5B50;&#x9634;&#x5F71;&#x7279;&#x70B9;"></a>

与[`text-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow)不同，[`box-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow)有一个`inset`关键字可用——把它放在一个影子声明的开始，使它变成一个内部阴影，而不是一个外部阴影。让我们看一看。

首先，我们将为这个例子使用一些不同的HTML：

```text
<button>Press me!</button>
```

```text
button {
  width: 150px;
  font-size: 1.1rem;
  line-height: 2;
  border-radius: 10px;
  border: none;
  background-image: linear-gradient(to bottom right, #777, #ddd);
  box-shadow: 1px 1px 1px black,
              inset 2px 3px 5px rgba(0,0,0,0.3),
              inset -2px -3px 5px rgba(255,255,255,0.5);
}

button:focus, button:hover {
  background-image: linear-gradient(to bottom right, #888, #eee);
}

button:active {
  box-shadow: inset 2px 2px 1px black,
              inset 2px 3px 5px rgba(0,0,0,0.3),
              inset -2px -3px 5px rgba(255,255,255,0.5);
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

在这里我们将focus/hover/active这些声明一起设置了按钮样式。这个按钮的默认状态下设置了一个简单的黑色盒阴影，并且加上了一对inset阴影，一个明的，一个暗的，位于按钮的两个对角上，以此给按钮一种很棒的阴影效果。

当按钮被按下时，这里的active声明将第一个盒阴影换成一个非常暗的inset阴影。给人一种按钮被按下的样子。

**注意**: 还有一个可以在box-shadow中设置的值 — 另外一个位于颜色值前面可选的长度值，即**spread radius**，如果设置了这个值，将会导致阴影变得比原始的阴影更大，这个值不是很常用，但是值得一提。

### Filters（过滤器）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#Filters%EF%BC%88%E8%BF%87%E6%BB%A4%E5%99%A8%EF%BC%89) <a id="Filters&#xFF08;&#x8FC7;&#x6EE4;&#x5668;&#xFF09;"></a>

CSS过滤器提供了一种过滤元素的方法，就好比你在诸如Photoshop这样的平面设计程序中过滤元素一样。有大量的不同的选项可以使用，你可以在[`filter`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/filter) 参考页面阅读所有相关的更多细节。在这篇文章中，我们将会向你介绍它的语法，并且向你展示将会发生多么有趣的结果。

基本上，过滤器可以应用在任何元素上，块元素（block）或者行内元素（inline）——你只需要使用`filter`属性，并且给他一个特定的过滤函数的值。有些可用的过滤器选项和其他CSS特性做的事情十分相似，例如`drop-shadow()`的工作方式以及产生的效果和 [`box-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow) 或[`text-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow)十分相似。然而过滤器真正出色的地方在于，它们作用于盒（box）内内容（content）的确切形状，而不仅仅将盒子本身作为一个大的块，这看起来会更棒，即使他们可能不会总是变成你想要的模样。让我们来举一个简单的例子来阐明我们的意思：

首先，一些简单的 HTML:

```text
<p class="filter">Filter</p>

<p class="box-shadow">Box shadow</p>
```

现在是一些CSS,用来给它们各自一个下降的阴影:

```text
p {
  margin: 1rem auto;
  padding: 20px;
  width: 100px;
  border: 5px dashed red;
}

.filter {
  -webkit-filter: drop-shadow(5px 5px 1px rgba(0,0,0,0.7));
  filter: drop-shadow(5px 5px 1px rgba(0,0,0,0.7));
}

.box-shadow {
  box-shadow: 5px 5px 1px rgba(0,0,0,0.7);
}
```

这给了我们一个如下的结果:

在 CodePen 中打开在 JSFiddle 中打开

正如你所看到的, drop-shadow过滤器跟随着文本和border dashes的确切形状。而盒阴影（box-shadow）仅仅跟随着盒的四方。

其他需要注意的事:

* 过滤器很新——它们可以被大多数的现代的浏览器支持，包括Microsoft Edge，但它们一点也不能被IE浏览器支持。因此如果你在你的设计中使用过滤器，你需要确保你的内容即使没有过滤器也是可用的。
* 你会看到我们在`filter`属性中通过`-webkit-`前缀包含了一个版本信息，这被称为一个 [Vendor Prefix](https://developer.mozilla.org/en-US/docs/Glossary/Vendor_Prefix)，有时会被浏览器使用，以在一个新特性完整实现之前，当它与无前缀版本没有冲突的时候支持并实验这个特性。Vendor prefixes永远都不被指望着被web开发人员使用，但是它们有时候确实会被在产品页面中使用，即当实验性的特性确实被需要时。在这个实例中，Chrome/Safari/Opera 目前要求这些属性的`-webkit-`版本，而Edge 和 Firefox则使用后者，无前缀版本。

**注意**: 如果你确实决定在你的代码中使用前缀，确保你包括了所有需要的前缀以及无前缀的版本，这样才会有尽可能多的浏览器能够使用这些特性，并且如果浏览器落下了前缀，它们也能够使用无前缀的版本。另外需要注意的是这些实验性的特性可能会有改变，这可能会导致你的代码被破坏，在前缀被去除之前，最好还是仅仅实验这些特性。

 你可以看到更多关于过滤器的例子，在 [filters.html](http://mdn.github.io/learning-area/css/styling-boxes/advanced_box_effects/filters.html) \(也可以看 [source code](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/advanced_box_effects/filters.html)\).

### Blend modes（混合模式）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#Blend_modes%EF%BC%88%E6%B7%B7%E5%90%88%E6%A8%A1%E5%BC%8F%EF%BC%89) <a id="Blend_modes&#xFF08;&#x6DF7;&#x5408;&#x6A21;&#x5F0F;&#xFF09;"></a>

CSS混合模式允许我们为元素添加一个混合模式 ，以当两个元素重叠时，指定一个混合的效果——最终每个像素所展示的颜色将会是原来像素中颜色和其下面一层相组合之后的结果，对于像Photoshop这样的图形程序的用户来说，混合模式应该也非常熟悉。

这里有两个在 CSS中用到的属性:

* [`background-blend-mode`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-blend-mode), 用来将单个元素的多重背景图片和背景颜色设置混合在一起。
* [`mix-blend-mode`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/mix-blend-mode), 用来将一个元素与它覆盖的那些元素各自所设置的背景（background）和内容\(content\)混合在一起。

你可以找到比这里用到的更多的例子，在我们的[blend-modes.html](http://mdn.github.io/learning-area/css/styling-boxes/advanced_box_effects/blend-modes.html) 示例页面 \(查看 [source code](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/advanced_box_effects/blend-modes.html)\), 或者在 [`<blend-mode>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/blend-mode) 参考页面。

**注意**: 混合模式（Blend modes ）同样也很新，而且略微不如过滤器（filter）的被支持度。至今也没有没Edge支持， 并且 Safari 也仅仅支持部分混合模式选项。

#### background-blend-mode[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#background-blend-mode) <a id="background-blend-mode"></a>

让我们再来看一些例子以帮助我们更好的理解这一点。首先，[`background-blend-mode`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-blend-mode)——在这里我们将展示一对简单的 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div)s，这样你就可以比较原始版本和混合版本：

```text
<div>
</div>
<div class="multiply">
</div>
```

现在来点 CSS — 我们正在给`<div>`添加一个背景图像和一个绿色的背景色：

```text
div {
  width: 250px;
  height: 130px;
  padding: 10px;
  margin: 10px;
  display: inline-block;
  background: url(https://mdn.mozillademos.org/files/13090/colorful-heart.png) no-repeat center 20px;
  background-color: green;
}

.multiply {
  background-blend-mode: multiply;
}
```

我们得到的结果是这样的——你可以看到左边的原始版本，以及右边的多层混合版本：

在 CodePen 中打开在 JSFiddle 中打开

#### mix-blend-mode[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#mix-blend-mode) <a id="mix-blend-mode"></a>

现在让我们看一看 [`mix-blend-mode`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/mix-blend-mode)。 这里我们将给出两个相同的`<div>`s，但是每个都位于一个有着紫色背景的简单的`<div>`上，来向你展示元素们将会怎样混合在一起：

```text
<article>
  No mix blend mode
  <div>
        
  </div>
  <div>
  </div>
</article>

<article>
  Multiply mix
  <div class="multiply-mix">
        
  </div>
  <div>
  </div>
</article>
```

这是我们将用来装饰它的CSS:

```text
article {
  width: 300px;
  height: 180px;
  margin: 10px;
  position: relative;
  display: inline-block;
}

div {
  width: 250px;
  height: 130px;
  padding: 10px;
  margin: 10px;
}

article div:first-child {
  position: absolute;
  top: 10px;
  left: 0;
  background: url(https://mdn.mozillademos.org/files/13090/colorful-heart.png) no-repeat center 20px;
  background-color: green;
}

article div:last-child {
  background-color: purple;
  position: absolute;
  bottom: -10px;
  right: 0;
  z-index: -1;
}

.multiply-mix {
  mix-blend-mode: multiply;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

你可以看到，多层混合（mix-blend）不仅混合了两种背景图像，还混合了在`<div>`下面的颜色。

**注意：**如果您不理解上面的一些布局属性，请不要担心，像 [`position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)， [`top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/top)， [`bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/bottom)， [`z-index`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index)等。我们将在[CSS Layout](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout)模块中详细地介绍这些内容。

### -webkit-background-clip: text[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#-webkit-background-clip_text) <a id="-webkit-background-clip_text"></a>

另一个我们认为在继续之前会提到的新特性\(目前支持Chrome、Safari和Opera,和在Firefox正在实现\)是[`background-clip`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)的 `text` 值。当与专有 `-webkit-text-fill-color: transparent;` 特性一起使用时，这允许您将背景图像剪贴到元素文本的形状，从而产生一些不错的效果。这不是一个正式的标准，但是已经在多个浏览器中实现了，因为它很流行，并且被开发人员广泛使用。在这种情况下，这两种属性都需要一个`-webkit-`供应商前缀，甚至对于非webkit/Chrome-based的浏览器来说也是如此。

```text
.text-clip {
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
```

那么为什么其他浏览器会实现一个`-webkit-`前缀？主要是为了浏览器兼容性——许多web开发人员已经开始使用`-webkit-`前缀来实现web站点，它开始看起来像其他的浏览器一样被破坏了，而实际上他们遵循的是标准。因此，他们被迫实施了一些这样的功能。这就凸显了在你的工作中使用非标准和/或带前缀的CSS特性的危险——这不仅会导致浏览器兼容性问题，而且还会发生变化，因此你的代码随时可能崩溃。坚持标准要好得多。

如果您确实希望在您的生产工作中使用这些特性，请确保在浏览器中进行彻底的测试，并检查这些特性不工作的地方，站点仍然可用。

**注意：**对于一个完整的`-webkit-background-clip: text`代码示例，见[background-clip-text.html](http://mdn.github.io/learning-area/css/styling-boxes/advanced_box_effects/background-clip-text.html)（也可以见[源码](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/advanced_box_effects/background-clip-text.html)）。

### 自主学习:尝试一些效果[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0%E5%B0%9D%E8%AF%95%E4%B8%80%E4%BA%9B%E6%95%88%E6%9E%9C) <a id="&#x81EA;&#x4E3B;&#x5B66;&#x4E60;&#x5C1D;&#x8BD5;&#x4E00;&#x4E9B;&#x6548;&#x679C;"></a>

现在轮到你了。对于这种自主学习，我们希望您使用下面所提供的代码来试验上面所读到的一些效果。

如果你犯了一个错误，你可以用_Reset_按钮来重置这个例子。

在 CodePen 中打开在 JSFiddle 中打开

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Advanced_box_effects#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

我们希望这篇文章被证明是很有趣的——玩着闪亮的玩具通常是很有趣的，而且看看什么样的工具在尖端的浏览器中是可以得到的是我们很感兴趣的。您已经到达了样式盒文章的末尾，因此，接下来您将通过我们的评估来测试您的box syling技能。

