# 样式化链接

当为 [links](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks) 添加样式时, 理解利用伪类有效地建立链接状态是很重要的，以及如何为链接添加样式来实现常用的功能，比如说导航栏、选项卡。我们将在本文中关注所有这些主题。

| 学习本章节的前提: | 基本的计算机使用能力，HTML 基础 \(学习 [Introduction to HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)\), CSS 基础 \(学习 [Introduction to CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS)\), [CSS text and font fundamentals](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_text/Fundamentals). |
| :--- | :--- |
| 目的: | 学习如何将样式应用到链接状态，以及如何使用链接实现常见的 UI 功能，比如导航菜单。 |

### 让我们来看一些链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Styling_links#%E8%AE%A9%E6%88%91%E4%BB%AC%E6%9D%A5%E7%9C%8B%E4%B8%80%E4%BA%9B%E9%93%BE%E6%8E%A5) <a id="&#x8BA9;&#x6211;&#x4EEC;&#x6765;&#x770B;&#x4E00;&#x4E9B;&#x94FE;&#x63A5;"></a>

根据最佳实践  [创建超链接](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks) 中的练习，我们看到了如何在你的 HTML 中实现链接。在本篇文章中，我们会以这个知识为基础，向你展示将样式应用到链接的最佳实践。

#### 链接状态[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Styling_links#%E9%93%BE%E6%8E%A5%E7%8A%B6%E6%80%81) <a id="&#x94FE;&#x63A5;&#x72B6;&#x6001;"></a>

第一件需要理解的事情是链接状态的概念，链接存在时处于不同的状态，每一个状态都可以用对应的 [伪类](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Selectors#Pseudo-classes) 来应用样式:

* **Link \(没有访问过的\)**: 这是链接的默认状态，当它没有处在其他状态的时候，它可以使用[`:link`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:link) 伪类来应用样式。
* **Visited**: 这个链接已经被访问过了\(存在于浏览器的历史纪录\), 它可以使用 [`:visited`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:visited) 伪类来应用样式。
* **Hover**: 当用户的鼠标光标刚好停留在这个链接，它可以使用 [`:hover`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:hover) 伪类来应用样式。
* **Focus**: 一个链接当它被选中的时候 \(比如通过键盘的 Tab  移动到这个链接的时候，或者使用编程的方法来选中这个链接 [`HTMLElement.focus()`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLElement/focus)\) 它可以使用 [`:focus`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:focus) 伪类来应用样式。
* **Active**: 一个链接当它被激活的时候 \(比如被点击的时候\)，它可以使用  [`:active`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:active) 伪类来应用样式。

#### 默认的样式[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Styling_links#%E9%BB%98%E8%AE%A4%E7%9A%84%E6%A0%B7%E5%BC%8F) <a id="&#x9ED8;&#x8BA4;&#x7684;&#x6837;&#x5F0F;"></a>

下面的例子说明了一个链接的默认行为表现 \(这里的 CSS 仅仅是为了放大和居中文本，使内容更加突出\)

```text
<p><a href="https://mozilla.org">A link to the Mozilla homepage</a></p>
```

```text
p {
  font-size: 2rem;
  text-align: center;
}
```

在 CodePen 中打开在 JSFiddle 中打开

当你观察默认样式的时候，你也许会注意到一些东西:

* 链接具有下划线。
* 未访问过的 \(Unvisited\) 的链接是蓝色的。
* 访问过的 \(Visited\) 的链接是紫色的.
* 悬停 \(Hover\) 在一个链接的时候鼠标的光标会变成一个小手的图标。
* 选中 \(Focus\) 链接的时候，链接周围会有一个轮廓，你应该可以按 tab 来选中这个页面的链接 \(在 Mac 上, 你可能需要使用_Full Keyboard Access: All controls_ 选项，然后再按下 Ctrl + F7 ，这样就可以起作用\)
* 激活 \(Active\) 链接的时候会变成红色 \(当你点击链接时，请尝试按住鼠标按钮。\)

有趣的是，这些默认的样式与20世纪90年代中期浏览器早期的风格几乎相同。这是因为用户知道以及期待链接就是这样变化的，如果链接的样式不同，就会让一些人感到奇怪。不过这不意味着你不应该为链接添加任何样式，只是你的样式不应该与用户预期的相差太大，你应该至少：

* 为链接使用下划线，但是不要在其他内容上也用下划线，以作区分。如果你不想要带有下划线的链接，那你至少要用其他方法来高亮突出链接。
* 当用户悬停或选择 \(hover 或者 focused\) 的时候，使链接有相应的变化，并且在链接被激活\(active\) 的时候，变化会有一些不同。可以使用以下CSS属性关闭/更改默认样式：
* [`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color) 文字的颜色
* [`cursor`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/cursor) 鼠标光标的样式，你不应该把这个关掉，除非你有非常好的理由。
* [`outline`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline) 文字的轮廓 \(轮廓有点像边框，唯一的区别是边框占用了盒模型的空间，而轮廓没有； 它只是设置在背景图片的顶部\)。outline 有一个有用的辅助功能，所以在把它关掉之前考虑清楚；你应该至少将 选中 \(focus\) 状态上链接悬停 \(hover\) 状态的样式加倍。

**注意**: 你不仅仅只限于上述属性来把样式应用到你的链接上，你可以用任何你喜欢的属性，就是不要搞得太疯狂！

#### 将样式应用到一些链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Styling_links#%E5%B0%86%E6%A0%B7%E5%BC%8F%E5%BA%94%E7%94%A8%E5%88%B0%E4%B8%80%E4%BA%9B%E9%93%BE%E6%8E%A5) <a id="&#x5C06;&#x6837;&#x5F0F;&#x5E94;&#x7528;&#x5230;&#x4E00;&#x4E9B;&#x94FE;&#x63A5;"></a>

现在我们已经详细地看了默认的状态，让我们看一下典型的链接样式的设置。

开始之前，我们先写出我们的空规则集：

```text
a {

}


a:link {

}

a:visited {

}

a:focus {

}

a:hover {

}

a:active {

}
```

这个顺序是重要的，因为链接的样式是建立在另一个样式之上的，比如第一个规则的样式会应用到所有后续的样式，如果当一个链接被激活 \(activated\) 的时候，它也是处于悬停 \(hover\) 状态的。如果你搞错了顺序，那么就可能不会产生正确的效果。要记住这个顺序，你可以尝试这样帮助记忆：**L**o**V**e **F**ears **HA**te.

现在让我们添加一些更多的信息来正确地得到这个样式：

```text
body {
  width: 300px;
  margin: 0 auto;
  font-size: 1.2rem;
  font-family: sans-serif;
}

p {
  line-height: 1.4;
}

a {
  outline: none;
  text-decoration: none;
  padding: 2px 1px 0;
}

a:link {
  color: #265301;
}

a:visited {
  color: #437A16;
}

a:focus {
  border-bottom: 1px solid;
  background: #BAE498;
}

a:hover {
  border-bottom: 1px solid;     
  background: #CDFEAA;
}

a:active {
  background: #265301;
  color: #CDFEAA;
}
```

我们还将提供一些示例HTML来应用CSS：

```text
<p>There are several browsers available, such as <a href="https://www.mozilla.org/zh-CN/firefox/">Mozilla
Firefox</a>, <a href="https://www.google.com/chrome/index.html">Google Chrome</a>, and
<a href="https://www.microsoft.com/zh-CN/windows/microsoft-edge">Microsoft Edge</a>.</p>
```

把这两个放在一起，我们得到这个结果：

在 CodePen 中打开在 JSFiddle 中打开

那么我们在这里做了什么? 这个肯定看起来和默认的风格不同，但它仍然提供了一个熟悉的感觉，好让用户知道发生了什么：

* 第一和第二条规则和本次讨论关系不大。
* 第三个规则使用了 `a` 选择器取消了默认的文本下划线和链接被选中 \(focus\) 时的轮廓 \(outline\)  \(不同的浏览器默认的行为可能不同，不过这里是取消了\)，并为每个链接添加了少量的内边距\(padding\)，所有这一切将在之后变得明确。
* 接着, 我们使用  `a:link` 和 `a:visited` 选择器来设置未访问 \(unvisited\)链接和访问过 \(visited\) 的链接上的一些颜色变化，当然它们是不同的。
* 下面两条规则使用 `a:focus` 和 `a:hover` 来设置选中 \(focus\) 和悬停 \(hover\) 的链接有不同的背景颜色，加上一个下划线，使链接更加突出。这里有两点需要注意：
  * 下划线是使用 [`border-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom) 创造的, 而不是 [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration)，有一些人喜欢这个，因为前者比后者有更好的样式选项， 并且绘制的位置会稍微低一点，所以不会穿过字母 \(比如 字母 g 和 y 底部\).
  * 这个 [`border-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom) 值被设置为`1px solid`, 没有明确的颜色。这样做可以使边框采用和元素文本一样的颜色，这在这样的情况下是很有用的，因为链接的每种状态下，文本是不同的颜色。
* 最后, `a:active` 用来给链接一个不同的配色方案，当链接被激活 \(activated\) 时，让链接被激活的时候更加明显。

#### 动手练习: 为你的链接添加样式[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Styling_links#%E5%8A%A8%E6%89%8B%E7%BB%83%E4%B9%A0_%E4%B8%BA%E4%BD%A0%E7%9A%84%E9%93%BE%E6%8E%A5%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F) <a id="&#x52A8;&#x624B;&#x7EC3;&#x4E60;_&#x4E3A;&#x4F60;&#x7684;&#x94FE;&#x63A5;&#x6DFB;&#x52A0;&#x6837;&#x5F0F;"></a>

在这个动手练习部分，我们希望你使用我们的空规则集，然后添加你自定义的规则，从而使链接看上去比较酷。发挥你的想象力，大胆地做吧。我们相信你可以想出一些更酷的东西，就像我们上面的例子一样。

如果你犯了错误，你都可以使用 _Reset 按钮来重置。_ 如果你遇到了困难，可以按 _Show solution_ 按钮来显示我们上文中的例子。

在 CodePen 中打开在 JSFiddle 中打开

### 在链接中包含图标[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Styling_links#%E5%9C%A8%E9%93%BE%E6%8E%A5%E4%B8%AD%E5%8C%85%E5%90%AB%E5%9B%BE%E6%A0%87) <a id="&#x5728;&#x94FE;&#x63A5;&#x4E2D;&#x5305;&#x542B;&#x56FE;&#x6807;"></a>

一个常见的做法是在链接中包含图标，使链接提供更多关于链接指向的内容的信息。让我们来看一个简单的例子，例子中为一个外部链接 \(链接指向的不是本站，而是外部站点\)。这样的图标通常看起来像一个指向盒子的小箭头，比如, 我们会使用 [this great example from icons8.com](https://icons8.com/web-app/741/external-link).

让我们来看一些能给我们这个效果的 HTML 和 CSS。首先，一些简单的 HTML 样式：

```text
<p>For more information on the weather, visit our <a href="weather.html">weather page</a>,
look at <a href="https://en.wikipedia.org/wiki/Weather">weather on Wikipedia</a>, or check
out <a href="http://www.extremescience.com/weather.htm">weather on Extreme Science</a>.</p>
```

接着是 CSS:

```text
body {
  width: 300px;
  margin: 0 auto;
  font-family: sans-serif;
}

p {
  line-height: 1.4;
}

a {
  outline: none;
  text-decoration: none;
  padding: 2px 1px 0;
}

a:link {
  color: blue;
}

a:visited {
  color: purple;
}

a:focus, a:hover {
  border-bottom: 1px solid;
}

a:active {
  color: red;
}

a[href*="http"] {
  background: url('https://mdn.mozillademos.org/files/12982/external-link-52.png') no-repeat 100% 0;
  background-size: 16px 16px;
  padding-right: 19px;
}
```

在 CodePen 中打开在 JSFiddle 中打开

那么这里发生了什么? 我们将跳过大部分的 CSS，因为那些只是你之前看过的相同的信息。最后一条规则很有趣，这里我们在外部链接上插入了一个自定义背景图片，这和上篇 [custom bullets on list items](https://developer.mozilla.org/zh-CN/Learn/CSS/Styling_text/Styling_lists#Using_a_custom_bullet_image) 文章的做法很像。这次我们使用了 [`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background) 简写代替了使用多个属性。我们设置了我们想要插入的图片的路径，指定 `no-repeat` ，所以我们只得到了一个插入的副本，然后指定位置是 100% 使其出现在内容的右边，然后距离上方是 0 px。

我们也使用 [`background-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-size) 来指定要显示的背景图像的大小，这样对有一个大的图标，然后重新调整它的大小是很有帮助的，也是响应式网站设计的需要。但是，这仅适用于IE 9及更高版本。所以你如果需要支持那些老的浏览器，你只需要调整图像大小，然后插入它。

最后，我们在链接上设置 [`padding-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-right) ，为背景图片留出空间，所以我们不会和文本重叠。

最后一句话，我们是如何只选中了外部链接的？如果你正确写了你的 [HTML links](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks) ，你应该只会在外部链接上使用绝对 URL，如果链接是链接你的站点的其他部分，那么使用相对链接是更加高效的。因此 "http" 文本应该只出现在外部链接上，所以我们可以使用一个属性选择器 [attribute selector](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Selectors#Attribute_selectors): `a[href*="http"]` 选中 [`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素，但是只会选中那些拥有 [`href`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a#attr-href) 属性，且属性的值包含 "http" 的 [`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)的元素。

就这样啦，尝试重新审视上面的动手练习部分，尝试这种新技术！

**注意**: 不要担心，如果你目前不熟悉 [backgrounds](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes) 和 [responsive web design](https://developer.mozilla.org/zh-CN/docs/Web/Apps/Progressive/Responsive/responsive_design_building_blocks) ; 这些会在其他地方解释。

### 样式化链接为按钮[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Styling_links#%E6%A0%B7%E5%BC%8F%E5%8C%96%E9%93%BE%E6%8E%A5%E4%B8%BA%E6%8C%89%E9%92%AE) <a id="&#x6837;&#x5F0F;&#x5316;&#x94FE;&#x63A5;&#x4E3A;&#x6309;&#x94AE;"></a>

目前在本文中探索的用法也可以用在其他方面。比如，悬停 \(hover\) 的状态可以为不同的元素应用样式，不只是链接，你也许会想添加悬停状态的样式到段落、列表项、或者是其他东西。

此外，在某些情况下，链接通常会应用样式，使它看上去的效果和按钮差不多，一个网站导航菜单通常是标记为一个列表，列表中包含链接，这可以很容易地被设计为看起来像一组控制按钮或是选项卡，主要是用于让用户可以访问站点的其他部分，现在让我们来看一看。

首先，一些 HTML:

```text
<ul>
  <li><a href="#">Home</a></li><li><a href="#">Pizza</a></li><li><a href="#">Music</a></li><li><a href="#">Wombats</a></li><li><a href="#">Finland</a></li>
</ul>
```

接着，是我们的 CSS:

```text
body,html {
  margin: 0;
  font-family: sans-serif;
}

ul {
  padding: 0;
  width: 100%;
}

li {
  display: inline;
}

a {
  outline: none;
  text-decoration: none;
  display: inline-block;
  width: 19.5%;
  margin-right: 0.625%;
  text-align: center;
  line-height: 3;
  color: black;
}

li:last-child a {
  margin-right: 0;
}

a:link, a:visited, a:focus {
  background: yellow;
}

a:hover {     
  background: orange;
}

a:active {
  background: red;
  color: white;
}
```

这给我们以下结果：

在 CodePen 中打开在 JSFiddle 中打开

让我们来解释一下这里发生了什么，主要是几个有趣的部分:

* 我们的第二条规则删除了  [`<ul>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul) 元素的默认的 [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)，然后设置了它的宽度是外部容器  [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) \(在这次条件下\) 的 100% 。
* [`<li>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/li) 元素通常默认是块元素 \(可见 [types of CSS boxes](https://developer.mozilla.org/zh-CN/Learn/CSS/Introduction_to_CSS/Box_model#Types_of_CSS_boxes) 回顾\)，意味着它们各自会占用一行。在这个例子中，我们创建了一组水平列表的链接，所以在第三条规则中，我们设置了 [`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 属性为 inline，这会导致列表中的每项内容都会一起出现在同一行，它们现在表现得就像内联元素。
* 第四条规则，主要是 [`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素的样式，这里比较复杂; 让我们一步一步来看：
  * 和前面的例子一样，我们首先关掉了 [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration) 和 [`outline`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline)，我们不希望这些破坏我们链接的样子。
  * 接着，我们设置 [`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 为 `inline-block` ，[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素默认为内联元素，而且我们不希望它们像值为 `block` 时一样，线条超出自己的内容，我们确实想要控制它们的大小`inline-block` 允许我们这样做。
  * 接着是尺寸的设置! 我们要填满整个  [`<ul>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul) 的宽度，为按钮之间留一些间距 \(margin\)  \(但不是右边边缘的间距\)，我们有 5 个按钮需要容纳，所以它们的大小应该一样。为了做到这一点，我们设置 [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 为 19.5%，然后 [`margin-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-right) 为 0.625%. 你会注意到所有宽度加起来是 100.625%, 这样会让最后一个按钮溢出 `<ul>` ，然后显示到下一行中。但是，我们使用了下一条规则让它恢复到了 100%，这条规则选中了列表中的最后一个 `<a>`元素，然后删除了它的间距 \(margin\)。完成!
  * 最后三条声明就比较简单了，主要是为链接各个状态添加了颜色。我们居中了每个链接中的文本，设置 [`line-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height) 为 3， 让按钮有一些高度 \(这也具有垂直居中文本的优点\)，并设置文本的颜色为黑色。

**注意**: 你也许会注意到 HTML 中的列表的每项内容都在同一行上，这是因为 inline-block 元素在页面上创建的空格换行符，就像几个字之间的空格，这样的空隙也许会破坏我们的水平导航菜单布局。所以我们删除了空格。你可以在  [Fighting the space between inline block elements](https://css-tricks.com/fighting-the-space-between-inline-block-elements/) 找到有关此问题的更多信息（和解决方案）。

### 小结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Styling_links#%E5%B0%8F%E7%BB%93) <a id="&#x5C0F;&#x7ED3;"></a>

我们希望本文为你提供有关链接的所有知识——目前！我们的样式文本模块中的最后一篇文章详细介绍了如何在你的网站上使用自定义字体，或者更熟悉网络字体。

