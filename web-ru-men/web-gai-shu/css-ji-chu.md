# CSS 基础

层叠样式表（英语：**C**ascading **S**tyle **S**heet，简称：CSS）是你用来为网页添加样式的代码。这一节内容会带你了解你所需的基础知识。我们将解答像这样的问题：怎样将文本改成黑色或红色？怎样将内容在屏幕上这样或那样的地方显示？怎样用背景图片或背景颜色来装饰网页？

### 所以到底什么是CSS？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E6%89%80%E4%BB%A5%E5%88%B0%E5%BA%95%E4%BB%80%E4%B9%88%E6%98%AFCSS%EF%BC%9F) <a id="&#x6240;&#x4EE5;&#x5230;&#x5E95;&#x4EC0;&#x4E48;&#x662F;CSS&#xFF1F;"></a>

就像 HTML，CSS 也不是真正的编程语言。它也不是标记语言——是样式表语言。也就是说，它允许你有选择性地为 HTML 文档的元素添加样式。举例来说，要选择一个 HTML 页面里**所有**的段落元素，然后将它们的文本改成红色，在 CSS 中你应该这样写：

```text
p {
  color: red;
}
```

让我们动手操作一下：将这三行 CSS 代码粘贴到文本编辑器里的新文件中，然后保存文件名为  `style.css` ，保存到 `styles` 文件夹内。

但是我们还需要将 CSS 文件应用到 HTML 文档内，否则的话 CSS 代码不会影响到 HTML 文档在浏览器里的显示。（如果你没有完整地跟随我们的指导，在[文件处理](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Dealing_with_files)和 [HTML 基础](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics)中查看你所需的内容。）

1.  打开 `index.html` 文件，然后将下面一行粘贴到头部（也就是 `<head>` 和 `</head>` 标签之间）。

   ```text
   <link href="styles/style.css" rel="stylesheet" type="text/css">
   ```

2. 保存 `index.html` 并用浏览器将其打开。你应该看到这样的页面：

![A mozilla logo and some paragraphs. The paragraph text has been styled red by our css.](https://mdn.mozillademos.org/files/9435/website-screenshot-styled.png)如果你的段落文字现在是红色的了，那么祝贺你，你已经成功地写下了你的第一句 CSS 代码！

#### 解析CSS规则集[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E8%A7%A3%E6%9E%90CSS%E8%A7%84%E5%88%99%E9%9B%86) <a id="&#x89E3;&#x6790;CSS&#x89C4;&#x5219;&#x96C6;"></a>

让我们仔细看一看 CSS ：

![](https://mdn.mozillademos.org/files/9461/css-declaration-small.png)

整个结构称为 CSS 的**规则集**（通常被简称为“规则”），注意里面单独的部分也是一样：选择器（**Selector**）HTML 元素的名称位于规则集开始。它选择了一个或多个需要添加样式的元素（在这个例子中就是 `p` 元素）。要给不同元素添加样式只需要更改选择器就行了。声明（**Declaration**）一个单独的规则比如 `color: red;` 这指定了你想要添加样式元素的**属性**。属性（**Properties**）这是你改变 HTML 元素样式的方法。（在这个例子中 `color` 就是 [`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 元素的属性。）在 CSS 中，你通过选择合适的属性来改变你的规则。属性值（Property value）在属性的右边，冒号后面，我们拥有**属性值**，用于从指定的属性里的非常多的外观中选择一个值（我们除了 `red` 之外还有很多属性值可以用于 `color` ）。

注意其他重要的语法：

* 每个规则集（除了选择器的部分）都应该包含在成对的大括号里（`{}`）。
* 在每个声明里，你应该用冒号（`:`）分离开属性与属性值。
* 在每个规则集里，你应该用分号（`;`）分离开各个声明。

如果要同时修改多个属性，你只需要将它们用分号隔开，就像这样：

```text
p {
  color: red;
  width: 500px;
  border: 1px solid black;
}
```

#### 选择多个元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E9%80%89%E6%8B%A9%E5%A4%9A%E4%B8%AA%E5%85%83%E7%B4%A0) <a id="&#x9009;&#x62E9;&#x591A;&#x4E2A;&#x5143;&#x7D20;"></a>

你也可以选择多种类型的元素然后为它们添加一组相同的样式。将不同的选择器用逗号分开。例如：

```text
p, li, h1 {
  color: red;
}
```

#### 不同类型的选择器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E4%B8%8D%E5%90%8C%E7%B1%BB%E5%9E%8B%E7%9A%84%E9%80%89%E6%8B%A9%E5%99%A8) <a id="&#x4E0D;&#x540C;&#x7C7B;&#x578B;&#x7684;&#x9009;&#x62E9;&#x5668;"></a>

选择器有许多不同的类型。在上面我们只看到了**元素选择器**，它被用来选择 HTML 文档中给定的元素。但是我们可以做出更加具体的选择。下面是一些常用的选择器类型：

| 选择器名称 | 选择的内容 | 示例 |
| :--- | :--- | :--- |
| 元素选择器（有时也称作标签或类型选择器） | 所有指定类型的 HTML 元素 | `p` 选择 `<p>` |
| 标识（ID）选择器 | 页面中指定标识的元素（在一个 HTML 页面中，每个标识只被允许指定到一个元素） | `#my-id` 选择 `<p id="my-id">` 或 `<a id="my-id">` |
| 类别选择器 | 页面中指定类别的元素（一个页面中可以出现多个类别实例） | `.my-class` 选择 `<p class="my-class">` 和 `<a class="my-class">` |
| 属性选择器 | 页面中拥有指定属性的元素 | `img[src]` 选择 `<img src="myimage.png">` 而不是 `<img>` |
| 伪类选择器 | 指定的元素，但是需要在特殊的状态，比如悬停 | `a:hover` 选择 `<a>`, 但是只在鼠标悬停在链接上时 |

这里有更多选择器可供探索，在[选择器指南](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Selectors)中你可以查看更多详细的信息。

### 字体和文本[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E5%AD%97%E4%BD%93%E5%92%8C%E6%96%87%E6%9C%AC) <a id="&#x5B57;&#x4F53;&#x548C;&#x6587;&#x672C;"></a>

既然我们已经探索了一些 CSS 基础，现在就让我们开始添加更多规则和信息到我们的 `style.css` 文件中来让我们的示例更加美观。首先，让我们的字体和文本变得更加漂亮。

1. 首先，找到我们在之前访问 Google Fonts ****中[保存的内容](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/What_should_your_web_site_be_like#Font)。在 `index.html` 的头部中任意位置添加 [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link) 元素（注意：在 `<head>` 和 `</head>` 之间的任意位置）。它将看起来像下面这样：

   ```text
   <link href='http://fonts.googleapis.com/css?family=Open+Sans' rel='stylesheet' type='text/css'>
   ```

2. 接下来，删除 `style.css` 文件中已有的规则。那是一次好的尝试，不过红色的文字看起来并不太舒服。
3. 将下列代码添加到相应的位置，用你在 Google Fonts 找到的字体替代  `font-family` 中的占位行。（ `font-family` 意味着你想要你的文本使用的字体。）这条规则首先为整个页面设定了一个全局字体和字号（因为 `<html>` 是整个页面的父元素，而且它所有的子元素都会继承相同的 ****`font-size` 和 `font-family`）：

   ```text
   html {
     font-size: 10px; /* px 表示 “像素（pixels）”: 这个基础字号现在高10像素 */
     font-family: 'Open Sans', sans-serif; /* 剩下的部分是你从 Google fonts 上获取的输出 */
   }
   ```

   注意：在 CSS 文档中所有位于 `/*` 和 `*/` 之间的内容都是 CSS 注释，它会被浏览器在渲染代码时忽略。你可以在这里写下对你现在要做的事情有帮助的笔记。

4. 现在我们将要为 HTML 中 body 元素内的 \([`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1), [`<li>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/li), 和 [`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p)\)元素设置字号。我们也会将标题居中显示，同时为 body 元素内的内容设置行高和间距，来让页面可读性更高。

   ```text
   h1 {
     font-size: 60px;
     text-align: center;
   }

   p, li {
     font-size: 16px;    
     line-height: 2;
     letter-spacing: 1px;
   }
   ```

你可以调整这些 `px` ****值到任何你喜欢的值来让你的设计更符合你的心意，不过通常你的设计应该看起来像这样：

![a mozilla logo and some paragraphs. a sans-serif font has been set, the font sizes, line height and letter spacing are adjusted, and the main page heading has been centered](https://mdn.mozillademos.org/files/9447/website-screenshot-font-small.png)

### 盒子，盒子，一切都与盒子有关[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E7%9B%92%E5%AD%90%EF%BC%8C%E7%9B%92%E5%AD%90%EF%BC%8C%E4%B8%80%E5%88%87%E9%83%BD%E4%B8%8E%E7%9B%92%E5%AD%90%E6%9C%89%E5%85%B3) <a id="&#x76D2;&#x5B50;&#xFF0C;&#x76D2;&#x5B50;&#xFF0C;&#x4E00;&#x5207;&#x90FD;&#x4E0E;&#x76D2;&#x5B50;&#x6709;&#x5173;"></a>

在你写 CSS 时你会发现它大部分都是关于盒子——设置它们的尺寸，颜色，位置等等。你的页面里大部分 HTML 元素都可以被看作一个一个层叠的盒子。

![a big stack of boxes or crates sat on top of one another](https://mdn.mozillademos.org/files/9441/boxes.jpg)

并不意外，CSS 布局主要就是基于盒模型的。每个占据你页面空间的块都有这样的属性：

* **内边距**（`padding`），围绕着内容的空间（比如围绕段落的空间）
* **边框**（`border`），紧接着内边距的实体线段
* **外边距**（`margin`），围绕元素外部的空间

![three boxes sat inside one another. From outside to in they are labelled margin, border and padding](https://mdn.mozillademos.org/files/9443/box-model.png)

在这一部分我们用：

* `width` （属于一个元素的）
* `background-color` ，元素内容和内边距之后的颜色
* `color` ，元素内容的颜色（通常是文本）
* `text-shadow` ，为元素内的文本设置阴影
* `display` ，设置元素的显示模式（暂时不用关心这部分内容）

让我们赶紧开始添加更多的 CSS 到页面中吧！将这些新规则都添加到页面的底部，不要害怕改变了属性的值会造成什么结果，赶紧去尝试吧！

#### 更改页面颜色[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E6%9B%B4%E6%94%B9%E9%A1%B5%E9%9D%A2%E9%A2%9C%E8%89%B2) <a id="&#x66F4;&#x6539;&#x9875;&#x9762;&#x989C;&#x8272;"></a>

```text
html {
  background-color: #00539F;
}
```

这条规则设置了整个页面的背景颜色。将上面颜色的代码改成你在[你的网站呈现什么样子？](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/What_will_your_website_look_like)中选择的主题颜色。

#### 解析 body 元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E8%A7%A3%E6%9E%90_body_%E5%85%83%E7%B4%A0) <a id="&#x89E3;&#x6790;_body_&#x5143;&#x7D20;"></a>

```text
body {
  width: 600px;
  margin: 0 auto;
  background-color: #FF9500;
  padding: 0 20px 20px 20px;
  border: 5px solid black;
}
```

现在是 [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 元素。这里有几条声明，所以我们一条一条看：

* `width: 600px;` — 强制页面永远保持600像素宽。
* `margin: 0 auto;` — 当你在像 `margin` 或 `padding` 这样的属性中设置两个值时，第一个值代表元素的上方**和**下方（在这个例子中设置为 `0`），而第二个值代表左边**和**右边（在这里，`auto` ****是一个特殊的值，意思是水平方向上左右对称）。你也可以使用一个，三个或四个值，参考[这里](https://developer.mozilla.org/en-US/docs/Web/CSS/margin#Values) 。
* `background-color: #FF9500;` — 之前说过，指定元素的背景颜色。我们给 body 元素用了一种略微偏红的橘色以与深蓝色的 [`<html>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/html) 元素形成反差，但你也可以继续试验其它颜色。
* `padding: 0 20px 20px 20px;` — 我们给内边距设置了四个值来让内容四周产生一点空间。这一次我们不设置上方的内边距，设置右边，下方，左边的内边距为20像素。值以上、右、下、左的顺序排列。
* `border: 5px solid black;` — 简单地为页面四周设置了5像素的黑色实线边框。

#### 为页面主标题定位和添加样式[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E4%B8%BA%E9%A1%B5%E9%9D%A2%E4%B8%BB%E6%A0%87%E9%A2%98%E5%AE%9A%E4%BD%8D%E5%92%8C%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F) <a id="&#x4E3A;&#x9875;&#x9762;&#x4E3B;&#x6807;&#x9898;&#x5B9A;&#x4F4D;&#x548C;&#x6DFB;&#x52A0;&#x6837;&#x5F0F;"></a>

```text
h1 {
  margin: 0;
  padding: 20px 0;    
  color: #00539F;
  text-shadow: 3px 3px 1px black;
}
```

你可能发现了我们在页面上方有一个可怕的间隙。那是因为浏览器会在你没有提供任何 CSS 代码的情况下应用一些 **默认样式** 给 [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1) 元素。那可能听起来不是个好主意，但是我们希望一个没有任何样式的网页也有基本的可读性。为了去掉那个间隙，我们通过设置 `margin: 0;` 覆盖掉默认样式。

至此，我们已经设置了标题的上内边距和下内边距为20像素，并且将标题文本与 html ****的背景颜色设为一致。

我们在这里使用了的一个非常有趣的属性是 `text-shadow`  ，它为元素内容的文本内容提供了阴影。它的四个值如下：

* 第一个像素值设置了**水平对齐**——它的横向偏移；一个负值会导致向左偏移。
* 第二个像素值设置了**垂直对齐**——它的纵向偏移；一个负值会导致向上偏移。
* 第三个像素值设置了阴影的**模糊半径**——越大的值会产生越模糊的阴影。
* 第四个值设置了阴影的基色。

 请尝试不同的值看看你会得出什么样的结果！

#### 居中图像[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E5%B1%85%E4%B8%AD%E5%9B%BE%E5%83%8F) <a id="&#x5C45;&#x4E2D;&#x56FE;&#x50CF;"></a>

```text
img {
  display: block;
  margin: 0 auto;
}
```

最后，我们将使图像居中来让它变得更美观。我们可以重新使用之前应用到 body 的 `margin: 0 auto` ，但是我们还要做其他调整。 [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 元素是**块级**元素，意味着它占据了页面的空间并且能够赋予外边距和其他改变间距的值。与之对应的是**行内**元素，意味着它不能。所以为了使图像有外边距，我们必须使用 `display: block` 给予其块级行为。

提示：如果你暂时不能理解 __`display: block` 和块级元素与行内元素的差别也没关系；随着你对 CSS 学习的深入，你将明白这个问题。要了解更多 `display` 属性的值请查看[显示参考页面](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 。

### 结论[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics#%E7%BB%93%E8%AE%BA) <a id="&#x7ED3;&#x8BBA;"></a>

如果你一直跟随我们的说明，那么到最后你应该得到一个这样的页面（你也可以在[这里](http://mdn.github.io/beginner-html-site-styled/)查看我们的版本）：

![a mozilla logo, centered, and a header and paragraphs. It now looks nicely styled, with a blue background for the whole page and orange background for the centered main content strip.](https://mdn.mozillademos.org/files/9455/website-screenshot-final.png)

如果你有遇到问题，你可以将你的代码与我们GitHub上的[完整示例代码](https://github.com/mdn/beginner-html-site-styled/blob/gh-pages/styles/style.css)做对比。

在这里，我们只提到了非常有限的 CSS 知识，要查看更多，请访问我们的[CSS学习页面](https://developer.mozilla.org/zh-CN/Learn/CSS)。

