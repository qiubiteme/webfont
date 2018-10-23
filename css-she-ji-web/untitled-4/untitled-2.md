# 搜索 基本文本和字体样式

在这篇文章中，我们将带你开始掌握 [CSS](https://developer.mozilla.org/en-US/docs/Glossary/CSS) 的文字样式的旅程。这里我们将详细介绍文本/字体样式的所有基本原理，包括设置文字的粗细，字体和样式，文字的属性简写，文字的对齐，和其他效果，以及行和字母间距。

| 先决条件： | 基本的电脑操作，HTML 基础 \(学习 [Introduction to HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)\)，CSS 基础 \(学习 [Introduction to CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS)\). |
| :--- | :--- |
| 目的: | 了解在网页上设计文本所需的基本属性和技术。 |

### CSS中的文字样式涉及什么？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#CSS%E4%B8%AD%E7%9A%84%E6%96%87%E5%AD%97%E6%A0%B7%E5%BC%8F%E6%B6%89%E5%8F%8A%E4%BB%80%E4%B9%88%EF%BC%9F) <a id="CSS&#x4E2D;&#x7684;&#x6587;&#x5B57;&#x6837;&#x5F0F;&#x6D89;&#x53CA;&#x4EC0;&#x4E48;&#xFF1F;"></a>

正如你已经在你使用 HTML 和 CSS 完成工作时所经历的一样，元素中的文本是布置在元素的内容框中。以内容区域的左上角作为起点 \(或者是右上角，是在 RTL 语言的情况下\)，一直延续到行的结束部分。一旦达到行的尽头，它就会进到下一行，然后继续，再接着下一行，直到所有内容都放入了盒子中。文本内容表现地像一些内联元素，被布置到相邻的行上，除非到达了行的尽头，否则不会换行，或者你想强制地，手动地造成换行的话，你可以使用  [`<br>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/br) 元素。

**注意**: 如果上面的段落让你感到困惑，没关系，在继续之前，可以重新看看我们的 [Box model](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Box_model) 文件，复习框模型的理论。

用于样式文本的 CSS 属性通常可以分为两类，我们将在本文中分别观察。

* **字体样式**: 作用于字体的属性，会直接应用到文本中，比如使用哪种字体，字体的大小是怎样的，字体是粗体还是斜体，等等。
* **文本布局风格**: 作用于文本的间距以及其他布局功能的属性，比如，允许操纵行与字之间的空间，以及在内容框中，文本如何对齐。

**注意**: 请记住，包含在元素中的文本是作为一个单一的实体。你不能将文字其中一部分选中或添加样式，如果你要这么做，那么你必须要用适合的元素来包装它们，比如 \( [`<span>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/span) 或者 [`<strong>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong)\), 或者使用伪元素，像[::first-letter](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::first-letter) \(选中元素文本的第一个字母\), [::first-line](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::first-line) \(选中元素文本的第一行\), 或者 [::selection](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::selection) \(当前光标双击选中的文本\)

### 字体[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E5%AD%97%E4%BD%93) <a id="&#x5B57;&#x4F53;"></a>

我们直接来看看样式字体的属性。在这个例子中，我们会在一个相同的 HTML 示例中应用一些不同的 CSS 属性，就像这样：

```text
<h1>Tommy the cat</h1>

<p>I remember as if it were a meal ago...</p>

<p>Said Tommy the Cat as he reeled back to clear whatever foreign matter
 may have nestled its way into his mighty throat. Many a fat alley rat 
had met its demise while staring point blank down the cavernous barrel of
 this awesome prowling machine. Truly a wonder of nature this urban 
predator — Tommy the cat had many a story to tell. But it was a rare 
occasion such as this that he did.</p>
```

你可以在这找到完成版本 [finished example on Github](http://mdn.github.io/learning-area/css/styling-text/fundamentals/) \(也可以看源码 [the source code](https://github.com/mdn/learning-area/blob/master/css/styling-text/fundamentals/index.html).\)

#### 颜色[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E9%A2%9C%E8%89%B2) <a id="&#x989C;&#x8272;"></a>

[`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color) 属性设置选中元素的前景内容的颜色 \(通常指文本，不过也包含一些其他东西，或者是使用 [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration) 属性放置在文本下方或上方的线 \(underline overline\)。

`color` 也可以接受任何合法的 [CSS 颜色单位](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Values_and_units#Colors), 比如:

```text
p {
  color: red;
}
```

这将导致段落变为红色，而不是标准的浏览器默认的黑色，如下所示：

在 CodePen 中打开在 JSFiddle 中打开

#### 字体种类[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E5%AD%97%E4%BD%93%E7%A7%8D%E7%B1%BB) <a id="&#x5B57;&#x4F53;&#x79CD;&#x7C7B;"></a>

要在你的文本上设置一个不同的字体，你可以使用 [`font-family`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-family)  属性，这个允许你为浏览器指定一个字体 \(或者一个字体的列表\)，然后浏览器可以将这种字体应用到选中的元素上。浏览器只会把在当前机器上可用的字体应用到当前正在访问的网站上；如果字体不可用，那么就会用浏览器默认的字体代替 [default font](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#Default_fonts). 下面是一个简单的例子:

```text
p {
  font-family: arial;
}
```

这段语句使所有在页面上的段落都采用 arial 字体，这个字体可在任何电脑上找到。

**网页安全字体**

说到字体可用性，只有某几个字体通常可以应用到所有系统，因此可以毫无顾忌地使用。这些都是所谓的 **网页安全字体**.

大多数时候，作为网页开发者，我们希望对用于显示我们的文本内容的字体有更具体的控制。问题在于，需要一个方法来知道当前正在浏览我们的网站网页的电脑，它有哪些可用字体。我们并不是总能在每种情况下都知道这一点，但是网络安全字体在几乎所有最常用的操作系统（Windows，Mac，最常见的Linux发行版，Android和iOS版本）中都可用。

实际的Web安全字体列表将随着操作系统的发展而改变，但是可以认为下面的字体是网页安全的，至少对于现在来说 \(它们中的许多都非常流行，这要感谢微软在90年代末和21世纪初期的倡议[_Core fonts for the Web_](https://en.wikipedia.org/wiki/Core_fonts_for_the_Web) \)：

| 字体名称 | 字体类型 | 注意 |
| :--- | :--- | :--- |
| Arial | sans-serif | 通常认为最佳做法还是添加 Helvetica 作为 Arial 的首选替代品，尽管它们的字体面几乎相同，但 Helvetica 被认为具有更好的形状，即使Arial更广泛地可用。 |
| Courier New | monospace | 某些操作系统有一个 Courier New 字体的替代（可能较旧的）版本叫Courier。使用Courier New作为Courier的首选替代方案，被认为是最佳做法。 |
| Georgia | serif |  |
| Times New Roman | serif | 某些操作系统有一个 Times New Roman 字体的替代（可能较旧的）版本叫 Times。使用Times作为Times New Roman的首选替代方案，被认为是最佳做法。 |
| Trebuchet MS | sans-serif | 您应该小心使用这种字体——它在移动操作系统上并不广泛。 |
| Verdana | sans-serif |  |

**注意**: 在各种资源中，[cssfontstack.com](http://www.cssfontstack.com/) 网站维护了一个可用在 Windows 和 Mac 操作系统上使用的网页安全字体的列表，这可以帮助决策网站的安全性。

**注意**: 有一个可以下载来自一个网页的自定义字体的方法，允许你通过任何你想要的方法来定制你使用的字体：**网页字体**。这个有一点复杂，我们将在这个模块中的另一篇文章中讨论这一点。

**默认字体**

CSS 定义了 5 个常用的字体名称:  `serif, sans-serif, monospace`, `cursive,`和 `fantasy.` 这些都是非常通用的，当使用这些通用名称时，使用的字体完全取决于每个浏览器，而且它们所运行的每个操作系统也会有所不同。这是一种糟糕的情况，浏览器会尽力提供一个看上去合适的字体。 `serif`, `sans-serif` 和 `monospace` 是比较好预测的，默认的情况应该比较合理，另一方面，`cursive` 和 `fantasy` 是不太好预测的，我们建议使用它们的时候应该稍微注意一些，多多测试。

五个名称定义如下：

| 名称 | 定义 | 示例 |
| :--- | :--- | :--- |
| `serif` | 有衬线的字体 （衬线一词是指字体笔画尾端的小装饰，存在于某些印刷体字体中） | My big red elephant |
| `sans-serif` | 没有衬线的字体。 | My big red elephant |
| `monospace` | 每个字符具有相同宽度的字体，通常用于代码列表。 | My big red elephant |
| `cursive` | 用于模拟笔迹的字体，具有流动的连接笔画。 | My big red elephant |
| `fantasy` | 用来装饰的字体 | My big red elephant |

**字体栈**

由于你无法保证你想在你的网页上使用的字体的可用性 \(甚至一个网络字体可能由于某些原因而出错\), 你可以提供一个**字体栈** \(**font stack**\)，这样的话，浏览器就有多种字体可以选择了。只需包含一个`font-family属性`，其值由几个用逗号分离的字体名称组成。比如

```text
p {
  font-family: "Trebuchet MS", Verdana, sans-serif;
}
```

在这种情况下，浏览器从列表的第一个开始，然后查看在当前机器中，这个字体是否可用。如果可用，就把这个字体应用到选中的元素中。如果不可用，它就移到列表中的下一个字体，然后再检查。

在字体栈的最后提供一个合适的通用的字体名称是个不错的办法，这样的话，即使列出的字体都无法使用，浏览器至少可以提供一个还算合适的选择。为了强调这一点，如果没有其他选项可用，那么段落将被赋予浏览器的默认衬线字体 - 通常是Time New Roman - 这对于 sans-serif 字体是不利的！

**注意**: 有一些字体名称不止一个单词，比如`Trebuchet MS` ，那么就需要用引号包裹。

**一个使用 font-family 的例子**

让我们把它添加到之前的例子上，给段落一个 sans-serif 的字体。

```text
p {
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}
```

这给我们以下结果：

在 CodePen 中打开在 JSFiddle 中打开

#### 字体大小[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E5%AD%97%E4%BD%93%E5%A4%A7%E5%B0%8F) <a id="&#x5B57;&#x4F53;&#x5927;&#x5C0F;"></a>

在我们之前的模块中的[CSS values and units](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units) 文章，我们回顾了[length and size units](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Values_and_units#Length_and_size). 字体大小 \(通过 [`font-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size) 属性设置\) 可以取大多数这些单位的值 \(以及其他，比如百分比 [percentages](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Values_and_units#Percentages)\)，然而你在调整字体大小时，最常用的单位是：

* `px` \(像素\): 将像素的值赋予给你的文本。这是一个绝对单位， 它导致了在任何情况下，页面上的文本所计算出来的像素值都是一样的。
* `em`s: 1em 等于我们设计的当前元素的父元素上设置的字体大小 \(更加具体的话，比如包含在父元素中的大写字母 M 的宽度\) 如果你有大量设置了不同字体大小的嵌套元素，这可能会变得棘手, 但它是可行的，如下图所示。为什么要使用这个麻烦的单位呢? 当你习惯这样做时，那么就会变得很自然，你可以使用`em`调整任何东西的大小，不只是文本。你可以有一个单位全部都使用 em 的网站，这样维护起来会很简单。
* `rem`s: 这个单位的效果和 `em`s 差不多，除了 1`rem` 等于 HTML 中的根元素的字体大小， \(i.e. [`<html>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/html)\) ，而不是父元素。这可以让你更容易计算字体大小，但是遗憾的是， `rem`s 不支持 Internet Explorer 8 和以下的版本。如果你的项目需要支持较老的浏览器，你可以坚持使用`em`s 或 `px`, 或者是 [polyfill](https://developer.mozilla.org/en-US/docs/Glossary/polyfill) 就像 [REM-unit-polyfill](https://github.com/chuckcarpenter/REM-unit-polyfill). 

元素的 `font-size` 属性是从该元素的父元素继承的。所以这一切都是从整个文档的根元素——[`<html>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/html)开始，浏览器的 `font-size` 标准设置的值为 16px。在根元素中的任何段落 \(或者那些浏览器没有设置默认大小的元素\)，会有一个最终的大小值：16px。其他元素也许有默认的大小，比如 [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1) 元素有一个 2ems 的默认值，所以它的最终大小值为 32px。当你开始更改嵌套元素的字体大小时，事情会变得棘手。比如，如果你有一个 [`<article>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/article) 元素在你的页面上，然后设置它的 font-size 为 `1.5em`s \(通过计算，可以得到大小为 24px\)，然后想让 `<article>` 元素中的段落获得一个计算值为 20px 的大小，那么你应该使用多少 em。

```text
<!-- document base font-size is 16px -->
<article> <!-- If my font-size is 1.5em -->
  <p>My paragraph</p> <!-- How do I compute to 20px font-size? -->
</article>
```

你需要将 em 的值设置为 20/24, 或者 `0.83333333em`s. 这个计算可能比较复杂，所以当你设置的时候，你需要仔细一些。如果可以使用 rems 的话，那实现起来就变得简单不少，避免在可能的情况下设置容器元素的字体大小。

**一个简单的 size 示例**

当调整你的文本大小时，将文档\(document\)的基础  `font-size` 设置为10px往往是个不错的主意，这样之后的计算会变得简单，所需要的 \(r\)em 值就是想得到的像素的值除以 10，而不是 16。做完这个之后，你可以简单地调整在你的 HTML 中你想调整的不同类型文本的字体大小。在样式表的指定区域列出所有`font-size`的规则集是一个好主意，这样它们就可以很容易被找到。

我们的新结果是这样的:

```text
html {
  font-size: 10px;
}

h1 {
  font-size: 2.6rem;
}

p {
  font-size: 1.4rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}
```

在 CodePen 中打开在 JSFiddle 中打开

#### 字体样式，字体粗细，文本转换和文本装饰[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E5%AD%97%E4%BD%93%E6%A0%B7%E5%BC%8F%EF%BC%8C%E5%AD%97%E4%BD%93%E7%B2%97%E7%BB%86%EF%BC%8C%E6%96%87%E6%9C%AC%E8%BD%AC%E6%8D%A2%E5%92%8C%E6%96%87%E6%9C%AC%E8%A3%85%E9%A5%B0) <a id="&#x5B57;&#x4F53;&#x6837;&#x5F0F;&#xFF0C;&#x5B57;&#x4F53;&#x7C97;&#x7EC6;&#xFF0C;&#x6587;&#x672C;&#x8F6C;&#x6362;&#x548C;&#x6587;&#x672C;&#x88C5;&#x9970;"></a>

CSS 提供了 4 种常用的属性来改变文本的样子：

* [`font-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-style): 用来打开和关闭文本 italic \(斜体\)。 可能的值如下 \(你很少会用到这个属性，除非你因为一些理由想将斜体文字关闭斜体状态\)：
  * `normal`: 将文本设置为普通字体 \(将存在的斜体关闭\)
  * `italic`: 如果当前字体的斜体版本可用，那么文本设置为斜体版本；如果不可用，那么会利用 oblique 状态来模拟 italics。
  * `oblique`: 将文本设置为斜体字体的模拟版本，也就是将普通文本倾斜的样式应用到文本中。
* [`font-weight`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-weight): 设置文字的粗体大小。这里有很多值可选，防止你有好几个可用的字体。 \(比如 _-light_, _-normal_, _-bold_, _-extrabold_, _-black_, 等等\), 不过事实上你很少会用到 `normal` 和 `bold`以外的值：
  * `normal`, `bold`: 普通或者**加粗**的字体粗细
  * `lighter`, `bolder`: 将当前元素的粗体设置为比其父元素粗体更细或更粗一步。`100`–`900`: 数值粗体值，如果需要，可提供比上述关键字更精细的粒度控制。
* [`text-transform`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform): 允许你设置要转换的字体。值包括：
  * `none`: 防止任何转型。
  * `uppercase`: 将所有文本转为大写。
  * `lowercase`: 将所有文本转为小写。
  * `capitalize`: 转换所有单词让其首字母大写。
  * `full-width`: 将所有字形转换成固定宽度的正方形，类似于等宽字体，允许对齐。拉丁字符以及亚洲语言字形（如中文，日文，韩文）
* [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration): 设置/取消字体上的文本装饰 \(你将主要使用此方法在设置链接时取消设置链接上的默认下划线。\) 可用值为：

  * `none`: 取消已经存在的任何文本装饰。
  * `underline`: 文本下划线.
  * `overline`: 文本上划线
  * `line-through`: 穿过文本的线 strikethrough over the text.

  你应该注意到 [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration) 可以一次接受多个值，如果你想要同时添加多个装饰值， 比如 `text-decoration: underline overline`.。同时注意 [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration)是一个缩写形式，它由 [`text-decoration-line`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration-line), [`text-decoration-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration-style) 和 [`text-decoration-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration-color) 构成。你可以使用这些属性值的组合来创建有趣的效果，比如 `text-decoration: line-through red wavy`.

我们来看一下这几个属性添加到我们的例子中：

我们的新结果是这样的：

```text
html {
  font-size: 10px;
}

h1 {
  font-size: 2.6rem;
  text-transform: capitalize;
}

h1 + p {
  font-weight: bold;
}

p {
  font-size: 1.4rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}
```

在 CodePen 中打开在 JSFiddle 中打开

#### 文字阴影[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E6%96%87%E5%AD%97%E9%98%B4%E5%BD%B1) <a id="&#x6587;&#x5B57;&#x9634;&#x5F71;"></a>

你可以为你的文本应用阴影，使用 [`text-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow) 属性。这最多需要 4 个值，如下例所示：

```text
text-shadow: 4px 4px 5px red;
```

4 个属性如下:

1. 阴影与原始文本的水平偏移，可以使用大多数的 CSS 单位 [length and size units](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Values_and_units#Length_and_size), 但是 px 是比较合适的。这个值必须指定。
2. 阴影与原始文本的垂直偏移;效果基本上就像水平偏移，除了它向上/向下移动阴影，而不是左/右。这个值必须指定。
3. 模糊半径 - 更高的值意味着阴影分散得更广泛。如果不包含此值，则默认为0，这意味着没有模糊。可以使用大多数的 CSS 单位 [length and size units](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Values_and_units#Length_and_size).
4. 阴影的基础颜色，可以使用大多数的 CSS 颜色单位 [CSS color unit](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Values_and_units#Colors). 如果没有指定，默认为 `black`.

**注意**: 正偏移值可以向右移动阴影，但也可以使用负偏移值来左右移动阴影，例如 `-1px -1px`.

**多种阴影**

您可以通过包含以逗号分隔的多个阴影值，将多个阴影应用于同一文本，例如：

```text
text-shadow: -1px -1px 1px #aaa,
             0px 4px 1px rgba(0,0,0,0.5),
             4px 4px 5px rgba(0,0,0,0.7),
             0px 0px 7px rgba(0,0,0,0.4);
```

如果我们把这个样式应用到我们 "Tommy the cat" 示例中的 [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1) 元素，就像这样：

在 CodePen 中打开在 JSFiddle 中打开

**注意**: 你可以看到更多有趣的关于 `text-shadow` 使用的示例在 [Moonlighting with CSS text-shadow](http://www.sitepoint.com/moonlighting-css-text-shadow/).

### 文本布局[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E6%96%87%E6%9C%AC%E5%B8%83%E5%B1%80) <a id="&#x6587;&#x672C;&#x5E03;&#x5C40;"></a>

有了基本的字体属性，我们来看看我们可以用来影响文本布局的属性。

#### 文本对齐[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E6%96%87%E6%9C%AC%E5%AF%B9%E9%BD%90) <a id="&#x6587;&#x672C;&#x5BF9;&#x9F50;"></a>

 [`text-align`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align) 属性用来控制文本如何和它所在的内容盒子对齐。可用值如下，并且在与常规文字处理器应用程序中的工作方式几乎相同：

* `left`: 左对齐文本。
* `right`: 右对齐文本。
* `center`: 居中文字
* `justify`: 使文本展开，改变单词之间的差距，使所有文本行的宽度相同。你需要仔细使用，它可以看起来很可怕。特别是当应用于其中有很多长单词的段落时。如果你要使用这个，你也应该考虑一起使用别的东西，比如 [`hyphens`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/hyphens)，打破一些更长的词语。

如果我们应用 `text-align: center;` 到我们例子中的 [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1) 元素中，结果如下：

在 CodePen 中打开在 JSFiddle 中打开

#### 行高[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E8%A1%8C%E9%AB%98) <a id="&#x884C;&#x9AD8;"></a>

 [`line-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height) 属性设置文本每行之间的高，可以接受大多数单位 [length and size units](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Values_and_units#Length_and_size)，不过也可以设置一个无单位的值，作为乘数，通常这种是比较好的做法。无单位的值乘以 [`font-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size) 来获得 `line-height`。当行与行之间拉开空间，正文文本通常看起来更好更容易阅读。推荐的行高大约是 1.5–2 \(双倍间距。\) 所以要把我们的文本行高设置为字体高度的1.5倍，你可以使用这个:

```text
line-height: 1.5;
```

把这个样式应用到我们示例中的 [`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 元素，结果如下：

在 CodePen 中打开在 JSFiddle 中打开

#### 字母和单词间距[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E5%AD%97%E6%AF%8D%E5%92%8C%E5%8D%95%E8%AF%8D%E9%97%B4%E8%B7%9D) <a id="&#x5B57;&#x6BCD;&#x548C;&#x5355;&#x8BCD;&#x95F4;&#x8DDD;"></a>

[`letter-spacing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing) 和 [`word-spacing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/word-spacing) 属性允许你设置你的文本中的字母与字母之间的间距、或是单词与单词之间的间距。你不会经常使用它们，但是可能可以通过它们，来获得一个特定的外观，或者让较为密集的文字更加可读。它们可以接受大多数单位 [length and size units](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Values_and_units#Length_and_size).

所以作为例子，如果我们把这个样式应用到我们的示例中的 [`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 段落的第一行：

```text
p::first-line {
  letter-spacing: 2px;
  word-spacing: 4px;
}
```

我们会得到下面的结果：

#### 其他一些值得看一下的属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E5%85%B6%E4%BB%96%E4%B8%80%E4%BA%9B%E5%80%BC%E5%BE%97%E7%9C%8B%E4%B8%80%E4%B8%8B%E7%9A%84%E5%B1%9E%E6%80%A7) <a id="&#x5176;&#x4ED6;&#x4E00;&#x4E9B;&#x503C;&#x5F97;&#x770B;&#x4E00;&#x4E0B;&#x7684;&#x5C5E;&#x6027;"></a>

以上属性让你了解如何开始在网页上设置文本， 但是你可以使用更多的属性。我们只是想介绍最重要的。一旦你习惯使用上面的内容，你还应该探索以下几点：

Font 样式:

* [`font-variant`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-variant): 在小型大写字母和普通文本选项之间切换。
* [`font-kerning`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-kerning): 开启或关闭字体间距选项。
* [`font-feature-settings`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-feature-settings): 开启或关闭不同的 [OpenType](https://en.wikipedia.org/wiki/OpenType) 字体特性。
* [`font-variant-alternates`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-variant-alternates): 控制给定的自定义字体的替代字形的使用。
* [`font-variant-caps`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-variant-caps): 控制大写字母替代字形的使用。
* [`font-variant-east-asian`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-variant-east-asian): 控制东亚文字替代字形的使用, 像日语和汉语。
* [`font-variant-ligatures`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-variant-ligatures): 控制文本中使用的连写和上下文形式。
* [`font-variant-numeric`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-variant-numeric): 控制数字，分式和序标的替代字形的使用。
* [`font-variant-position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-variant-position): 控制位于上标或下标处，字号更小的替代字形的使用。
* [`font-size-adjust`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size-adjust): 独立于字体的实际大小尺寸，调整其可视大小尺寸。
* [`font-stretch`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-stretch): 在给定字体的可选拉伸版本中切换。
* [`text-underline-position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-underline-position): 指定下划线的排版位置，通过使用 `text-decoration-line` 属性的`underline` 值。
* [`text-rendering`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-rendering): 尝试执行一些文本渲染优化。

文本布局样式：

* [`text-indent`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent): 指定文本内容的第一行前面应该留出多少的水平空间。
* [`text-overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow): 定义如何向用户表示存在被隐藏的溢出内容。
* [`white-space`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/white-space): 定义如何处理元素内部的空白和换行。
* [`word-break`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/word-break): 指定是否能在单词内部换行。
* [`direction`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/direction): 定义文本的方向 \(这取决于语言，并且通常最好让HTML来处理这部分，因为它是和文本内容相关联的。\)
* [`hyphens`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/hyphens): 为支持的语言开启或关闭连字符。
* [`line-break`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-break): 对东亚语言采用更强或更弱的换行规则。
* [`text-align-last`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align-last): 定义一个块或行的最后一行，恰好位于一个强制换行前时，如何对齐。
* [`text-orientation`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-orientation): 定义行内文本的方向。
* [`word-wrap`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/word-wrap): 指定浏览器是否可以在单词内换行以避免超出范围。
* [`writing-mode`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/writing-mode): 定义文本行布局为水平还是垂直，以及后继文本流的方向。

### Font 简写[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#Font_%E7%AE%80%E5%86%99) <a id="Font_&#x7B80;&#x5199;"></a>

许多字体的属性也可以通过 [`font`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font) 的简写方式来设置 . 这些是按照以下顺序来写的：  [`font-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-style), [`font-variant`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-variant), [`font-weight`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-weight), [`font-stretch`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-stretch), [`font-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size), [`line-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height), and [`font-family`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-family).

如果你想要使用 `font` 的简写形式，在所有这些属性中，只有 `font-size` 和 `font-family` 是一定要指定的。

[`font-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size) 和 [`line-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height) 属性之间必须放一个正斜杠。

一个完整的例子如下所示：

```text
font: italic normal bold normal 3em/1.5 Helvetica, Arial, sans-serif;
```

### 动手练习: 使用样式文本[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E5%8A%A8%E6%89%8B%E7%BB%83%E4%B9%A0_%E4%BD%BF%E7%94%A8%E6%A0%B7%E5%BC%8F%E6%96%87%E6%9C%AC) <a id="&#x52A8;&#x624B;&#x7EC3;&#x4E60;_&#x4F7F;&#x7528;&#x6837;&#x5F0F;&#x6587;&#x672C;"></a>

在这个动手练习中，我们没有任何具体的练习来做：我们只是希望你和一些字体/文本布局属性相处地愉快，看看你可以制作什么！你可以使用离线HTML / CSS文件进行此操作，也可以将代码输入到下面的实时可编辑示例中。

如果你犯了错误，你可以使用 Reset 按钮来复原。

在 CodePen 中打开在 JSFiddle 中打开

### 小结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals#%E5%B0%8F%E7%BB%93) <a id="&#x5C0F;&#x7ED3;"></a>

我们希望你在本篇文章中享受与文本在一起的时光！下篇文章会介绍所有你需要知道的关于 HTML 列表的样式。

