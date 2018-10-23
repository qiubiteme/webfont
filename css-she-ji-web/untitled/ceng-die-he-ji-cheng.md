# 层叠和继承

在上一节中，我们学习了多种多样的CSS选择器。但在实际的工作中，我们可能还有些疑惑，当有多个选择器作用在一个元素上时，哪个规则最终会应用到元素上？其实这是通过层叠机制来控制的，这也和样式继承\(元素从其父元素那里获得属性值\)有关、在本节中中我们将定义什么是层叠，什么是特异，元素属性如何从不同的规则中继承以及其重要性。

| 前提条件 | 了解HTML基本知识，了解CSS 如何工作的。 |
| :--- | :--- |
| 目标 | 了解层叠及特异，以及CSS中继承是如何实现的。 |

元素的最终样式可以在多个地方定义，它们以复杂的形式相互影响。这些复杂的相互作用使CSS变得非常强大，但也使其非常难于调试和理解。这篇文章旨在明晰其中的部分复杂性；如果你不能立即理解，也没关系，这是CSS 理论中最复杂的地方。你可以现在就尝试学习，或在遇到关于层叠和继承问题的时候再来翻阅。

### 层叠[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E5%B1%82%E5%8F%A0) <a id="&#x5C42;&#x53E0;"></a>

CSS 是 _Cascading Style Sheets_ 的缩写，这暗示层叠（cascade）的概念是很重要的。在最基本的层面上，它表明CSS规则的顺序很重要，但它比那更复杂。什么选择器在层叠中胜出取决于三个因素（这些都是按重量级顺序排列的——前面的的一种会否决后一种）：

1. 重要性（Importance）
2. 专用性（Specificity）
3. 源代码次序（Source order）

#### 重要性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E9%87%8D%E8%A6%81%E6%80%A7) <a id="&#x91CD;&#x8981;&#x6027;"></a>

在CSS中，有一个特别的语法可以让一条规则_**总**_**是**优先于其他规则：`!important`。把它加在属性值的后面可以使这条声明有无比强大的力量。  

让我们看一下这个例子:

```text
<p class="better">This is a paragraph.</p>
<p class="better" id="winning">One selector to rule them all!</p>
```

```text
#winning {
  background-color: red;
  border: 1px solid black;
}

.better {
  background-color: gray;
  border: none !important;
}

p {
  background-color: blue;
  color: white;
  padding: 5px;
}
```

这将生成以下：

在 CodePen 中打开在 JSFiddle 中打开

让我们一起来看看发生了什么。

1. 你可以看到第三条规则 [`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color) 和 [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) 被运用了, 但 [`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color)没有，为什么？实际上，这三种情况都应该应用，因为在源顺序后面的规则通常会覆盖较早的规则。
2. 然而, 在前面的规则被运用了,因为 IDs/class 选择器优先于element选择器。 \(对此，你将在下一章中学到更多\)
3. 这两个元素都有 [`class`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-class)并带有 `better`属性, 但是第二个元素有 [`id`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-id) 值为`winning` 。 因为比起class而言id专用性更高\(在一个页面上id是唯一的, 但很多元素可以拥有相同的class — ID 选择器在它们的目标中是非常优先的\)，红色背景色和1pixel的黑色边框都应应用于第二元素，第一个元素获得灰色背景色，没有边框，如类所指定。
4. 第二个元素获得红色背景色，但没有边框。为什么？因为 `!important` 在第二条规则中的声明——在 `border: none`之后写入它意味着尽管id具有更高的优先性，该声明也将优先于前面规则中的边界值声明。

**注意**: 重载这个 `!important` 声明的唯一方法是在后面的源码或者是一个拥有更高专用性的源码中包含相同的 `!important` 特性的声明。

知道 `!important`存在是很有用的，这样当你在别人的代码中遇到它时，你就知道它是什么了。**但是！**我们建议你千万不要使用它，除非你绝对必须使用它。您可能不得不使用它的一种情况是，当您在CMS中工作时，您不能编辑核心的CSS模块，并且您确实想要重写一种不能以其他方式覆盖的样式。 但是，如果你能避免的话，不要使用它。由于 `!important` 改变了层叠正常工作的方式，因此调试CSS问题，尤其是在大型样式表中，会变得非常困难。

要注意一个CSS声明的重要性取决于它被指定在什么样式表内——用户可以设置自定义样式表覆盖开发者的样式，例如用户可能有视力障碍，想设置字体大小对所有网页的访问是双倍的正常大小，以便更容易阅读。

相互冲突的声明将按以下顺序适用，后一种将覆盖先前的声明：

1. 在用户代理样式表的声明 \(例如：浏览器在没有其他声明的默认样式\).
2. 用户样式表中的普通声明（由用户设置的自定义样式）。
3. 作者样式表中的普通声明（这是我们设置的样式，Web开发人员）。
4. 作者样式表中的重要声明
5. 用户样式表中的重要声明

Web开发者的样式表覆盖用户的样式表是合理的，所以设计可以保持预期，但是有时候用户有很好的理由来重写web开发人员样式，如上所述，这可以通过在用户的规则中使用`!important`。

#### 专用性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E4%B8%93%E7%94%A8%E6%80%A7) <a id="&#x4E13;&#x7528;&#x6027;"></a>

**专用性**基本上是衡量选择器的具体程度的一种方法——它能匹配多少元素。如上面所示的示例所示，元素选择器具有很低的专用性。类选择器具有更高的专用性，所以将战胜元素选择器。ID选择器有甚至更高的专用性, 所以将战胜类选择器. 战胜ID选择器的唯一方法是使用 `!important`。

一个选择器具有的专用性的量是用四种不同的值（或组件）来衡量的，它们可以被认为是千位，百位，十位和个位——在四个列中的四个简单数字：

1. 千位：如果声明是在[`style`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-style) 属性中该列加1分（这样的声明没有选择器，所以它们的专用性总是1000。）否则为0。
2. 百位：在整个选择器中每包含一个ID选择器就在该列中加1分。
3. 十位：在整个选择器中每包含一个类选择器、属性选择器、或者伪类就在该列中加1分。
4. 个位：在整个选择器中每包含一个元素选择器或伪元素就在该列中加1分。

**注意**: 通用选择器 \(`*`\), 复合选择器 \(`+`, `>`, `~`, ' '\) 和否定伪类 \(`:not`\) 在专用性中无影响。

下表显示了几个示例。试着通过这些，并确保你理解他们为什么具有我们给予他们的专用性。

| 选择器 | 千位 | 百位 | 十位 | 个位 | 合计值 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `h1` | 0 | 0 | 0 | 1 | 0001 |
| `#indentifier` | 0 | 1 | 0 | 0 | 0100 |
| `h1 + p::first-letter` | 0 | 0 | 0 | 3 | 0003 |
| `li > a[href*="zh-CN"] > .inline-warning` | 0 | 0 | 2 | 2 | 0022 |
| 没有选择器, 规则在一个元素的 [`<style>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/style) 属性里 | 1 | 0 | 0 | 0 | 1000 |

**注意**: 如果多个选择器具有相同的重要性和专用性，则选择哪一个选择器取决于 [Source order](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#Source_order).

在我们继续之前，让我们看看一个行动中的例子。这是我们将要使用的HTML：

```text
<div id="outer" class="container">
  <div id="inner" class="container">
    <ul>
      <li class="nav"><a href="#">One</a></li>
      <li class="nav"><a href="#">Two</a></li>
    </ul>
  </div>
</div>
```

下面是CSS的示例：

```text
/* specificity: 0101 */
#outer a {
  background-color: red;
}

/* specificity: 0201 */
#outer #inner a {
  background-color: blue;
}

/* specificity: 0104 */
#outer div ul li a {
  color: yellow;
}

/* specificity: 0113 */
#outer div ul .nav a {
  color: white;
}

/* specificity: 0024 */
div div li:nth-child(2) a:hover {
  border: 10px solid black;
}

/* specificity: 0023 */
div li:nth-child(2) a:hover {
  border: 10px dashed black;
}

/* specificity: 0033 */
div div .nav:nth-child(2) a:hover {
  border: 10px double black;
}

a {
  display: inline-block;
  line-height: 40px;
  font-size: 20px;
  text-decoration: none;
  text-align: center;
  width: 200px;
  margin-bottom: 10px;
}

ul {
  padding: 0;
}

li {
  list-style-type: none;
}
```

我们从这个代码中得到的结果如下：

在 CodePen 中打开在 JSFiddle 中打开

这里发生了什么?首先，我们只对本例的前七个规则感兴趣，正如您将注意到的，我们已经在每个注释中包含了它们的专用性值。

* 前两个选择器正在竞争链接的背景颜色的样式——第二个赢得并使背景色为蓝色，因为它有一个额外的ID选择器在链中：其专用性值为201比101。
* 第三个和第四个选择器在链接文本颜色的样式上进行竞争——第二个选择器获胜，使文本变白，因为缺少一个元素选择器，缺少的选择器被换成类选择器，它的值是十，而不是个位。所以专用性值为113和104。
* 选择器5 - 7在徘徊在链接附近时的样式进行竞争。选择器六明显地输给了了五，其专用性值为23和24——它在链中少了一个元素选择器。然而选择器七同时击败了五和六——它有与五相同数量的子选择器在链中，但一个元素已被换为了一个类选择器。所以获胜的专用性值是33比23和24。

**注意**:如果您还没有准备好，请再次复习所有选择器，以确保您理解为什么会授予特定的专用性值。

#### 源代码次序[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E6%BA%90%E4%BB%A3%E7%A0%81%E6%AC%A1%E5%BA%8F) <a id="&#x6E90;&#x4EE3;&#x7801;&#x6B21;&#x5E8F;"></a>

如上所述，如果多个相互竞争的选择器具有相同的重要性和专用性，那么第三个因素将帮助决定哪一个规则获胜——后面的规则将战胜先前的规则。例如:

```text
p {
  color: blue;
}

/* This rule will win over the first one */
p {
  color: red;
}
```

而在这个例子中的第一个规则将获胜，因为专用性高于源代码顺序：

```text
/* This rule will win */
.footnote {
  color: blue;
}

p {
  color: red;
}
```

#### 关于规则混合的一点注记[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E5%85%B3%E4%BA%8E%E8%A7%84%E5%88%99%E6%B7%B7%E5%90%88%E7%9A%84%E4%B8%80%E7%82%B9%E6%B3%A8%E8%AE%B0) <a id="&#x5173;&#x4E8E;&#x89C4;&#x5219;&#x6DF7;&#x5408;&#x7684;&#x4E00;&#x70B9;&#x6CE8;&#x8BB0;"></a>

在考虑所有这些层叠理论和什么样式优先于其他样式被应用时，你应该记住的一件事是，所有这些都发生在属性级别上——属性覆盖其他属性，但你不会让整个规则凌驾于其他规则之上。  
当多个CSS规则匹配相同的元素时，它们都被应用到该元素中。只有在这之后，任何相互冲突的属性才会被评估，以确定哪种风格会战胜其他类型。

让我们看一个例子。首先，一些HTML：

```text
<p>I'm <strong>important</strong></p>
```

现在一些CSS风格与它：

```text
/* specificity: 0002 */
p strong {
  background-color: khaki;
  color: green;
}

/* specificity: 0001 */
strong {
  text-decoration: underline;
  color: red;
}
```

Result:

在 CodePen 中打开在 JSFiddle 中打开

在这个例子中，因为专用性的关系，第一条规则中的[`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value)属性覆盖掉了第二条中的颜色值。但是，对于第一条中的 [`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color)和第二条中的[`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration) 的属性都在[`strong`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong)元素之中得到了体现。你也注意到了这个元素之中的字体是加粗的：这是浏览器默认的样式规则。

### 继承[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E7%BB%A7%E6%89%BF) <a id="&#x7EE7;&#x627F;"></a>

CSS继承是我们需要研究的最后一部分，以获取所有信息并了解什么样式应用于元素。其思想是，应用于某个元素的一些属性值将由该元素的子元素继承，而有些则不会。

* 例如，对 [`font-family`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-family) 和 [`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color) 进行继承是有意义的，因为这使得您可以很容易地设置一个站点范围的基本字体，方法是应用一个字体到 [`<html>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/html) 元素；然后，您可以在需要的地方覆盖单个元素的字体。如果要在每个元素上分别设置基本字体，那就太麻烦了。
* 再如，让 [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)，[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)，[`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) 和 [`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image) 不被继承是有意义的。想象一下，如果您将这些属性设置在一个容器元素上，并将它们继承到每个子元素，然后不得不将它们全部放在每个单独的元素上，那么将会出现的样式/布局混乱。

哪些属性默认被继承哪些不被继承大部分符合常识。如果你想确定，你可以参考[CSS参考资料](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference)—— 每个单独的属性页都会从一个汇总表开始，其中包含有关该元素的各种详细信息，包括是否被继承。

#### 控制继承[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E6%8E%A7%E5%88%B6%E7%BB%A7%E6%89%BF) <a id="&#x63A7;&#x5236;&#x7EE7;&#x627F;"></a>

CSS为处理继承提供了四种特殊的通用属性值：

* [`inherit`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/inherit)： 该值将应用到选定元素的属性值设置为与其父元素一样。
* [`initial`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/initial) ：该值将应用到选定元素的属性值设置为与浏览器默认样式表中该元素设置的值一样。如果浏览器默认样式表中没有设置值，并且该属性是自然继承的，那么该属性值就被设置为 `inherit`。
* [`unset`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/unset) ：该值将属性重置为其自然值，即如果属性是自然继承的，那么它就表现得像 `inherit`，否则就是表现得像 `initial`。
* [`revert`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/revert) ：如果当前的节点没有应用任何样式，则将该属性恢复到它所拥有的值。换句话说，属性值被设置成自定义样式所定义的属性（如果被设置）， 否则属性值被设置成用户代理的默认样式。

**注意**: `initial` 和 `unset` 不被IE支持。

`inherit` 值是最有趣的——它允许我们显式地让一个元素从其父类继承一个属性值。

让我们看一个例子。首先有以下一段HTML：

```text
<ul>
  <li>Default <a href="#">link</a> color</li>
  <li class="inherit">Inherit the <a href="#">link</a> color</li>
  <li class="initial">Reset the <a href="#">link</a> color</li>
  <li class="unset">Unset the <a href="#">link</a> color</li>
</ul>
```

现在用CSS给它添加样式：

```text
body {
  color: green;
}

.inherit a {
  color: inherit;
}

.initial a {
  color: initial
}

.unset a {
  color: unset;
}
```

Result:

在 CodePen 中打开在 JSFiddle 中打开

让我们解释这里发生了什么：

*  我们首先设置[`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 的[`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color)为绿色。
* 由于`color`属性是自然继承的，所有的body子元素都会有相同的绿色。需要注意的是默认情况下浏览器设置链接的颜色为蓝色，而不是自然继承color属性，因此在我们列表中的第一个链接是蓝色的。
* 第二个规则设置一个类 `inherit` 的元素内的链接，并从父类继承它的颜色。在这种情况下, 意思是说链接继承了父元素[`<li>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/li)的颜色，默认情况下[`<li>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/li)的颜色来自于它的父元素  [`<ul>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul) , 最后 [`<ul>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul) 继承自 [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body)元素，而[`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body)的[`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color) 根据第一条规则设置成了绿色。
* 第三个规则选择了在元素上使用类 `initial` 的任意链接然后设置他们的颜色为 `initial` 。通常， `initial` 的值被浏览器设置成了黑色，因此该链接被设置成了黑色。
* 最后一个规则选择了在元素上使用类 `unset` 的所有链接然后设置它们的颜色为 `unset`  ——即我们不设置值。因为color属性是一个自然继承的属性，它实际上就像把值设置成 `inherit` 一样。结果是，该链接被设置成了与body一样的颜色——绿色。

#### 重新设置所有的属性值[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E9%87%8D%E6%96%B0%E8%AE%BE%E7%BD%AE%E6%89%80%E6%9C%89%E7%9A%84%E5%B1%9E%E6%80%A7%E5%80%BC) <a id="&#x91CD;&#x65B0;&#x8BBE;&#x7F6E;&#x6240;&#x6709;&#x7684;&#x5C5E;&#x6027;&#x503C;"></a>

CSS速写属性 [`all`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/all) 能够被应用到每一个继承属性，一次性应用所有的继承属性。这里的值可以是继承属性里的任何一个 \(`inherit`, `initial`, `unset`, or `revert`\)。对于撤销对样式的修改，这是非常方便的一种方式。然后你就可以在开始新的修改之前，返回到一个已知的开始点。

### 主动学习: 玩转层叠[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0_%E7%8E%A9%E8%BD%AC%E5%B1%82%E5%8F%A0) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;_&#x73A9;&#x8F6C;&#x5C42;&#x53E0;"></a>

在这个主动学习中，我们希望您尝试编写一个新的规则，它将覆盖我们在默认情况下应用到链接的颜色和背景颜色。你是否可以使用我们在[控制继承](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E6%8E%A7%E5%88%B6%E7%BB%A7%E6%89%BF) 块中看到一个特殊值之一来在新规则中写入一个声明，该规则将把背景颜色重新设置为白色，而不使用实际的颜色值。

如果你犯了一个错误，你可以用重置按钮重新设置它。如果你真的卡住了，点击 _Show solution_ 按钮查看参考答案。

在 CodePen 中打开在 JSFiddle 中打开

### 下一步是什么[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance#%E4%B8%8B%E4%B8%80%E6%AD%A5%E6%98%AF%E4%BB%80%E4%B9%88) <a id="&#x4E0B;&#x4E00;&#x6B65;&#x662F;&#x4EC0;&#x4E48;"></a>

如果你理解了这篇文章的大部分内容，那么你已经开始熟悉CSS的基本原理了。最后一点的核心理论是盒子模型，我们将在下一章中讨论。

如果你没有完全理解层叠，专用性和继承性，不用担心！这绝对是我们迄今为止所涉及到的最复杂的事情，甚至是专业的Web开发人员有时也会发现棘手的问题。我们建议你在继续进行这门课的过程中几次回到这篇文章，并继续思考它。如果您开始遇到样式应用不如你意的问题，请返回这里。它可能是专用性问题。

