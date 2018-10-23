# HTML 基础

超文本标记语言  \(英语：**H**yper**t**ext **M**arkup **L**anguage，简称：HTML \)  是一种用来结构化 Web 网页及其内容的标记语言。例如，你的内容可以是一组段落或一个重点列表，甚至可以含有图片和数据表。这篇文章提供的内容，能使你对HTML语言及其功能有最基本的认识。

### 所以到底什么是 HTML？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E6%89%80%E4%BB%A5%E5%88%B0%E5%BA%95%E4%BB%80%E4%B9%88%E6%98%AF_HTML%EF%BC%9F) <a id="&#x6240;&#x4EE5;&#x5230;&#x5E95;&#x4EC0;&#x4E48;&#x662F;_HTML&#xFF1F;"></a>

HTML 并不是编程语言，它是一种用于定义内容结构的_标记语言_。HTML 由一系列的**元素（**[**elements**](https://developer.mozilla.org/en-US/docs/Glossary/element)**）**所组成，这些元素可以用来封装不同部分的内容，使其以某种方式呈现或者工作。 闭合标签（  [tags](https://developer.mozilla.org/en-US/docs/Glossary/tag)）可以使得一个文字或者一张图片超链接到其他地方，可以使得文字变为斜体，可让文字变大或者变小等等。 例如，键入下面一行内容：

```text
My cat is very grumpy
```

如果我们想要让这行单独呈现，我们可以将其封装成为一个段落（**p**aragraph）元素：

```text
<p>My cat is very grumpy</p>
```

#### 解析一个HTML元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E8%A7%A3%E6%9E%90%E4%B8%80%E4%B8%AAHTML%E5%85%83%E7%B4%A0) <a id="&#x89E3;&#x6790;&#x4E00;&#x4E2A;HTML&#x5143;&#x7D20;"></a>

让我们深入探索一下这个段落元素。

![](https://mdn.mozillademos.org/files/9347/grumpy-cat-small.png)

这个元素的主要部分有：

1. **开始标签**（The opening tag）：这里包含了元素的名称（本例为 p），被开、闭**尖括号**所包围。这表示元素从此开始或者开始起作用——在本例中即段落由此开始。
2. **闭合标签**（The closing tag）：与开始标签相似，只是其在元素名之前包含了一个斜杠。这表示着元素的结尾——这表示元素在此结束——在本例中即段落在此结束。初学者常常会犯忘记包含闭合标签的错误，这可能会产生一些奇怪的结果。
3. **内容**（The content）：这是一个元素的内容，这个例子中就是所输入的文本本身。
4. **元素**（The element）：开标签、闭标签与内容相结合，便是一个完整的元素。

元素也可以有属性，看起来像这样：

![](https://mdn.mozillademos.org/files/9345/grumpy-cat-attribute-small.png)

属性（Attribute）包含了关于元素的一些额外的信息，这些信息本身并不需要被显现在内容中。在这个例子中，`class` 是一个属性名称，`editor-note` 是属性的值 。`class` 属性允许你为元素提供一个标识名称，以便进一步为元素指定样式或进行其他操作时使用。

一个属性应该包含：

1. 在属性与元素名称（或上一个属性，如果有超过一个属性的话）之间的空格符。
2. 属性的名称，并接上一个等号。
3. 由引号所包围的属性值。

#### 嵌套元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E5%B5%8C%E5%A5%97%E5%85%83%E7%B4%A0) <a id="&#x5D4C;&#x5957;&#x5143;&#x7D20;"></a>

你也可以将一个元素置于其他元素之中——这被称作**嵌套**。如果你想表明你的猫**非常**的暴躁，我们可以将 “非常” 用 [`<strong>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong) 元素包裹，这意味着这个单词将被强调：

```text
<p>My cat is <strong>very</strong> grumpy.</p>
```

你必须保证你的元素被正确地嵌套：在这个例子中我们首先使用 p 标签，然后是 strong 标签，接着我们需要先闭合 strong 标签，最后再闭合 p 标签。下面是一个错误示范：

```text
<p>My cat is <strong>very grumpy.</p></strong>
```

元素必须正确地开始和闭合，才能清楚地显示出正确的嵌套。如果它们像上面这样，那么你的浏览器将尽量地猜测你想要表达的意思，但是你很大程度上不会得到你期望的结果。所以千万不要这样做！

#### 空元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E7%A9%BA%E5%85%83%E7%B4%A0) <a id="&#x7A7A;&#x5143;&#x7D20;"></a>

有一些元素并不包含内容，它们被称为空元素。看看我们 HTML 代码中已经存在的 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素：

```text
<img src="images/firefox-icon.png" alt="My test image">
```

它包含了两个属性，但是这里并没有 `</img>` 闭合标签，也没有内部内容。因为图像元素不需要包含内容来产生效果，它的作用是向其所在的位置嵌入一个图像。

#### 解析HTML文档[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E8%A7%A3%E6%9E%90HTML%E6%96%87%E6%A1%A3) <a id="&#x89E3;&#x6790;HTML&#x6587;&#x6863;"></a>

上面我们介绍了一些基本的 HTML 元素，但是它们自己不是很有用。现在我们看看如何将它们组合起来成为一个完整的 HTML 页面。让我们重新看看  `index.html` 示例里的内容（我们先前在[文件处理](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Dealing_with_files)里创建的）：

```text
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <img src="images/firefox-icon.png" alt="My test image">
  </body>
</html>
```

这里我们有：

* `<!DOCTYPE html>` — 文档类型。在 HTML 刚刚出现的时期里（大约是1991/2 年），文档类型是用来链接一些好的 HTML 应该遵守的规则，有点像自动校正等。然而现在已经没有人关心这些，只是因为历史原因必须它必须包含在代码中。现在你只需要知道这些就可以。
* `<html></html>` — [`<html>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/html) 元素。这个元素包含了整个页面的内容，有时也被称作根元素。
* `<head></head>` — [`<head>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/head) 元素。这个元素可以包含你想添加的所有内容，但是不会被用户所看到。这里面包括像想被搜索引擎搜索到的关键字（[keywords](https://developer.mozilla.org/en-US/docs/Glossary/keyword)）和页面描述，CSS 样式表和字符编码声明等。
* `<body></body>` — [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 元素。这个元素包含了你想让用户在访问你的页面时看到的内容，不管是文本，图像，视频，游戏，可播放的音轨或其他内容。
* `<meta charset="utf-8">` — 这个元素指定了你的文档需要使用的字符编码是 UTF-8 ，它包括了非常多人类已知语言的字符。基本上 UTF-8 可以处理任何文本内容。我们没有任何理由不去设定字符编码，而且也可以避免以后可能出现的问题。
* `<title></title>` —  [`<title>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/title) 元素。这个元素设置了页面的标题，标题显示在浏览器标签页上，而且在你将网页添加到收藏夹或喜爱中时将作为默认名称。

### 图像[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E5%9B%BE%E5%83%8F) <a id="&#x56FE;&#x50CF;"></a>

让我们重新回到 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素：

```text
<img src="images/firefox-icon.png" alt="My test image">
```

像我们之前说过的，它将图像嵌入到元素所在位置。它通过包含图像文件路径的 `src` \(source\) 属性实现这一功能。

但是这一元素也要包括 `alt` \(alternative\) 属性 —— 这个属性应该是图像的描述内容，当图像不能被某些用户看见时，可能是因为：

1. 他们是盲人或者有视觉障碍。某些有严重视觉损伤的用户经常使用屏幕阅读器来为他们读出 `alt` 属性里的内容。
2. 有些代码里的错误让图像不能被展示出来。举个例子，试着故意将 `src` 属性里的路径改错。如果你保存并且重新加载页面，你应该能在图像的位置看到：

![](https://mdn.mozillademos.org/files/9349/alt-text-example.png)

alt 属性的关键就是要“可以描述图像的文本”。当被读出来时， alt 里面的内容应该向用户传递足够图像表达的意思。所以我们现在的文本 "My test image" 并不合适。一个描述火狐Logo的更好的文本应该是 "The Firefox logo: a flaming fox surrounding the Earth."。

现在为你的图像尝试一些更好的 alt 文本。

提示： __点击 [MDN 无障碍着陆页](https://developer.mozilla.org/zh-CN/docs/Web/Accessibility) _查看更多_。

### 标记文本[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E6%A0%87%E8%AE%B0%E6%96%87%E6%9C%AC) <a id="&#x6807;&#x8BB0;&#x6587;&#x672C;"></a>

这一部分包含了一些基本的用来标记文本的 HTML 元素。

#### 标题（不同于页面标题 title）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E6%A0%87%E9%A2%98%EF%BC%88%E4%B8%8D%E5%90%8C%E4%BA%8E%E9%A1%B5%E9%9D%A2%E6%A0%87%E9%A2%98_title%EF%BC%89) <a id="&#x6807;&#x9898;&#xFF08;&#x4E0D;&#x540C;&#x4E8E;&#x9875;&#x9762;&#x6807;&#x9898;_title&#xFF09;"></a>

标题元素允许你指定内容的标题和子标题。就像一本书拥有主标题，然后每一章还有标题，然后还有更小的标题，HTML 文档也是一样。HTML 包括六个级别的标题， [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1)–[`<h6>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h6) ，虽然你可能只会用到 3-4 最多。

```text
<h1>My main title</h1>
<h2>My top level heading</h2>
<h3>My subheading</h3>
<h4>My sub-subheading</h4>
```

现在尝试一下，在你的 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素上面添加一个合适的标题。

#### 段落[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E6%AE%B5%E8%90%BD) <a id="&#x6BB5;&#x843D;"></a>

像上面解释过的一样，[`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 元素是用来指定段落的。你会经常使用它来指定常规的文本内容：

```text
<p>This is a single paragraph</p>
```

（从[你的网站看起来是什么样的？](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/What_will_your_website_look_like)）添加你的样本内容到一个或几个段落里，然后将它们放在 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素之下。

#### 列表[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E5%88%97%E8%A1%A8) <a id="&#x5217;&#x8868;"></a>

很多Web上的内容都是列表，所以 HTML 为它们准备了一些特别的列表元素。要标记列表通常包括至少两个元素。最常用的列表类型是有序列表（ ordered lists ）和无序列表（ unordered lists ）：

1. **无序列表** 中项目的顺序并不重要，就像购物列表。这些内容被包括在一个  [`<ul>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul) 元素里。
2. **有序列表** 中项目的顺序很重要，就像一个食谱。这些内容被包括在一个 [`<ol>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ol) 元素里。

列表内的每个项目被包括在一个 [`<li>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/li) \(list item\) 元素里。

所以，如果我们想要将下面的段落碎片改成一个列表：

```text
<p>At Mozilla, we’re a global community of technologists, thinkers, and builders working together ... </p>
```

我们可以这样更改标记：

```text
<p>At Mozilla, we’re a global community of</p>
    
<ul> 
  <li>technologists</li>
  <li>thinkers</li>
  <li>builders</li>
</ul>

<p>working together ... </p>
```

尝试添加一个有序列表和无序列表到你的示例页面。

### 链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E9%93%BE%E6%8E%A5) <a id="&#x94FE;&#x63A5;"></a>

链接非常重要 — 它们让 Web 成为了 WEB（万维网）。要植入一个链接，我们需要使用一个简单的元素 — [`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) — a 是 "anchor" （锚）的缩写。要将一些文本添加到链接中，只需如下几步：

1. 选择一些文本。我们选择“Mozilla Manifesto”。
2. 将文本包含在 [`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素内，就像这样：

   ```text
   <a>Mozilla Manifesto</a>
   ```

3. 赋予 [`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素一个 `href` 属性，就像这样：

   ```text
   <a href="">Mozilla Manifesto</a>
   ```

4. 把你想要链接的网址放到该属性内：

   ```text
   <a href="https://www.mozilla.org/en-US/about/manifesto/">Mozilla Manifesto</a>
   ```

如果你在网址开始部分省略了 `https://` 或者 `http://` 协议，你可能会得到错误的结果。在完成一个链接后，点击它并确保它去向了你指定的网址。

`href` __这个名字可能开始看起来有点晦涩难懂。如果你在记忆它的名字上有问题的话，记住它代表的是 _**h**ypertext **ref**erence_ （超文本引用）_。_

如果你还没有完成过上面的操作，现在就为你的页面添加一个链接吧。

### 结论[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/HTML_basics#%E7%BB%93%E8%AE%BA) <a id="&#x7ED3;&#x8BBA;"></a>

如果你一直跟着这篇文章里的指导做的话，你应该完成了一个像下面这样的页面。（你也可以[从这查看](http://mdn.github.io/beginner-html-site/)）：  
  
![A web page screenshot showing a firefox logo, a heading saying mozilla is cool, and two paragraphs of filler text](https://mdn.mozillademos.org/files/9351/finished-test-page-small.png)

如果你遇到困难，你可以将 Github 上的[完整示例代码](https://github.com/mdn/beginner-html-site/blob/gh-pages/index.html)上与你的文件进行比较。

在这里，我们只是介绍了一点点 HTML。要学习更多，访问我们的 [HTML 学习页](https://developer.mozilla.org/zh-CN/Learn/HTML) 。

