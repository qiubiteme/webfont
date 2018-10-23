# 高级文字格式

HTML中有许多其他元素可以用于格式化文本，我们没有在[HTML 文字处理基础](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals)中提到它们。本文中所描述的元素虽然少有人知，但仍然值得去学习（尽管仍然不是完整的列表）。在这里你将了解标记引文、描述列表、计算机代码和其他相关文本、下标和上标、联系信息等。

| 预备知识: | 熟悉基础的HTML（包含在 [Getting started with HTML](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Getting_started) 中）、HTML文本格式（包含在 [HTML text fundamentals](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/HTML_text_fundamentals) 中）。 |
| :--- | :--- |
| 目标: | 学习如何使用不太知名的HTML元素来标记高级语义特征。 |

### 描述列表[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E6%8F%8F%E8%BF%B0%E5%88%97%E8%A1%A8) <a id="&#x63CF;&#x8FF0;&#x5217;&#x8868;"></a>

在 HTML 基础部分，我们讨论了如何在 HTML 中[标记基本的列表](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals#%E5%88%97%E8%A1%A8_Lists)，但是我们没有提到你偶尔会遇到的第三种类型的列表—**描述列表** \(description list\) **。**这种列表的目的是标记一组项目及其相关描述，例如术语和定义，或者是问题和答案等。让我们看一组术语和定义的示例：

```text
soliloquy
In drama, where a character speaks to themselves, representing their inner thoughts or feelings and in the process relaying them to the audience (but not to other characters.)
monologue
In drama, where a character speaks their thoughts out loud to share them with the audience and any other characters present.
aside
In drama, where a character shares a comment only with the audience for humorous or dramatic effect. This is usually a feeling, thought or piece of additional background information
```

描述列表使用与其他列表类型不同的闭合标签—  [`<dl>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/dl); 此外，每一项都用   [`<dt>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/dt) \(description term\)  元素闭合。每个描述都用 [`<dd>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/dd) \(description description\) 元素闭合。让我们来完成下面的标记例子:

```text
<dl>
  <dt>soliloquy</dt>
  <dd>In drama, where a character speaks to themselves, representing their inner thoughts or feelings and in the process relaying them to the audience (but not to other characters.)</dd>
  <dt>monologue</dt>
  <dd>In drama, where a character speaks their thoughts out loud to share them with the audience and any other characters present.</dd>
  <dt>aside</dt>
  <dd>In drama, where a character shares a comment only with the audience for humorous or dramatic effect. This is usually a feeling, thought or piece of additional background information.</dd>
</dl>
```

浏览器的默认样式会在**描述列表的描述部分**（description description）和**描述术语**（description terms）之间产生缩进。MDN非常严密地遵循这一惯例，同时也鼓励关于术语的其他更多的定义（but also embolden the terms for extra definition）。

下面是前述代码的显示结果：soliloquyIn drama, where a character speaks to themselves, representing their inner thoughts or feelings and in the process relaying them to the audience \(but not to other characters.\)monologueIn drama, where a character speaks their thoughts out loud to share them with the audience and any other characters present.asideIn drama, where a character shares a comment only with the audience for humorous or dramatic effect. This is usually a feeling, thought or piece of addtional background information.

请注意：一个术语&lt;dt&gt;可以同时有多个描述`<dd>`，比如说：asideIn drama, where a character shares a comment only with the audience for humorous or dramatic effect. This is usually a feeling, thought or piece of additional background information.In writing, a section of content that is related to the current topic, but doesn't fit directly into the main flow of content so is presented nearby \(often in a box off to the side.\)

#### 主动学习: 标记一组定义[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0_%E6%A0%87%E8%AE%B0%E4%B8%80%E7%BB%84%E5%AE%9A%E4%B9%89) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;_&#x6807;&#x8BB0;&#x4E00;&#x7EC4;&#x5B9A;&#x4E49;"></a>

现在是时候尝试一下描述列表了; 在输入区域的原始文本里添加相应的元素，使得它在输出区域是以描述列表的形式出现。如果你喜欢，你也可以使用你自己的描述术语和描述。

如果在这其中犯了错误，你可以使用Reset按钮来复原，如果你实在不知道怎么做，你可以按下Show solution按钮看答案。

### 引用[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E5%BC%95%E7%94%A8) <a id="&#x5F15;&#x7528;"></a>

HTML也有用于标记引用的特性，至于使用哪个元素标记，取决于你引用的是一块还是一行。

#### 块引用[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E5%9D%97%E5%BC%95%E7%94%A8) <a id="&#x5757;&#x5F15;&#x7528;"></a>

如果一个块级内容（一个段落、多个段落、一个列表等）从其他地方被引用，你应该把它用[`<blockquote>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/blockquote)元素包裹起来表示，并且在[`cite`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/blockquote#attr-cite)属性里用URL来指向引用的资源。例如，下面的例子就是引用的MDN的`<blockquote>`元素页面：

```text
<p>The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block
Quotation Element</em>) indicates that the enclosed text is an extended quotation.</p>
```

要把这些转换为块引用，我们要这样做：

```text
<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
  <p>The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block
  Quotation Element</em>) indicates that the enclosed text is an extended quotation.</p>
</blockquote>
```

浏览器在渲染块引用时默认会增加缩进，作为引用的一个指示符；MDN是这样做的，但是也增加了额外的样式：

> The **HTML `<blockquote>` Element** \(or _HTML Block Quotation Element_\) indicates that the enclosed text is an extended quotation.

#### 行内引用[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E8%A1%8C%E5%86%85%E5%BC%95%E7%94%A8) <a id="&#x884C;&#x5185;&#x5F15;&#x7528;"></a>

行内元素用同样的方式工作，除了使用[`<q>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/q)元素。例如，下面的标记包含了从MDN`<q>`页面的引用：

```text
<p>The quote element — <code>&lt;q&gt;</code> — is <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">intended
for short quotations that don't require paragraph breaks.</q></p>
```

浏览器默认将其作为普通文本放入引号内表示引用，就像下面：

The quote element — `<q>` — is intended for short quotations that don't require paragraph breaks.\(&lt;q&gt;元素旨在用于不需要分段的短引用\)

#### 引文[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E5%BC%95%E6%96%87) <a id="&#x5F15;&#x6587;"></a>

[`cite`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/blockquote#attr-cite)属性的内容听起来很有用，但不幸的是，浏览器、屏幕阅读器等等不会真的关心它，如果不使用JavaScript或CSS，浏览器不会显示`cite`的内容。如果你想要确保引用的资源在页面上是可用的，更好的方法是把[`<cite>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/cite)元素放到引用元素旁边。这就意味着包含引用资源的名称——即引用的书的名字，或人的名字——但并不表示你不可以用同样的方式把要链接的文本放到`<cite>`元素中：

```text
<p>According to the <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
<cite>MDN blockquote page</cite></a>:
</p>

<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
  <p>The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block
  Quotation Element</em>) indicates that the enclosed text is an extended quotation.</p>
</blockquote>

<p>The quote element — <code>&lt;q&gt;</code> — is <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">intended
for short quotations that don't require paragraph breaks.</q> -- <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">
<cite>MDN q page</cite></a>.</p>
```

引文默认的字体样式为斜体。你可以在[quotations.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/advanced-text-formatting/quotations.html)中参看代码。

#### 主动学习：是谁说的？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E6%98%AF%E8%B0%81%E8%AF%B4%E7%9A%84%EF%BC%9F) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x662F;&#x8C01;&#x8BF4;&#x7684;&#xFF1F;"></a>

到了主动学习的时间！在这个例子中我们想要你：

1. 把中间的段落变成块引用，它要包含`cite`属性
2. 把第三个段落的一部分变成行内引用，它要包含`cite`属性
3. 每一个引用都要包含`<cite>`元素

你需要的引用源：

* http://www.brainyquote.com/quotes/authors/c/confucius.html 对应the Confucius quote
* http://www.affirmationsforpositivethinking.com/index.htm 对应 "The Need To Eliminate Negative Self Talk".

如果你做错了，你总可以使用Reset按钮重置。如果你真的不会了，按下Show solution按钮来看答案。

### 缩略语[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E7%BC%A9%E7%95%A5%E8%AF%AD) <a id="&#x7F29;&#x7565;&#x8BED;"></a>

另一个你在web上看到的相当常见的元素是[`<abbr>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/abbr)——它常被用来包裹一个缩略语或缩写，并且提供缩写的解释（包含在[`title`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-title)属性中）。让我们看看下面两个例子：

```text
<p>We use <abbr title="Hypertext Markup Language">HTML</abbr> to structure our web documents.</p>

<p>I think <abbr title="Reverend">Rev.</abbr> Green did it in the kitchen with the chainsaw.</p>
```

这些代码的显示效果如下（当光标移动到项目上时会出现提示）：

We use HTML to structure our web documents.

I think Rev. Green did it in the kitchen with the chainsaw.

**Note**: 还有另一个元素&lt;acronym&gt;，它基本上与&lt;abbr&gt;相同，专门用于首字母缩略词而不是缩略语。 然而，这已经被废弃了 - 它在浏览器的支持中不如&lt;abbr&gt;，并且具有类似的功能，所以没有意义。 只需使用&lt;abbr&gt;。

#### 主动学习：标记一个引用[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E6%A0%87%E8%AE%B0%E4%B8%80%E4%B8%AA%E5%BC%95%E7%94%A8) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x6807;&#x8BB0;&#x4E00;&#x4E2A;&#x5F15;&#x7528;"></a>

在这个简单的主动学习任务中，我们希望你简单地标记一个缩写。你可以使用下面的示例，或者用自己的示例来替换。

### 标记联系方式[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E6%A0%87%E8%AE%B0%E8%81%94%E7%B3%BB%E6%96%B9%E5%BC%8F) <a id="&#x6807;&#x8BB0;&#x8054;&#x7CFB;&#x65B9;&#x5F0F;"></a>

HTML有个用于标记联系方式的元素——[`<address>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/address)。它仅仅包含你的联系方式，例如：

```text
<address>
  <p>Chris Mills, Manchester, The Grim North, UK</p>
</address>
```

但要记住的一点是，`<address>`元素是为了标记编写HTML文档的人的联系方式，而不是任何其他的内容。因此，如果这是Chris写的文档，上面的内容将会很好。注意，下面的内容也是可以的：

```text
<address>
  <p>Page written by <a href="../authors/chris-mills/">Chris Mills</a>.</p>
</address>
```

### 上标和下标[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E4%B8%8A%E6%A0%87%E5%92%8C%E4%B8%8B%E6%A0%87) <a id="&#x4E0A;&#x6807;&#x548C;&#x4E0B;&#x6807;"></a>

当你使用日期、化学方程式、和数学方程式时会偶尔使用上标和下标。 [`<sup>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/sup) 和[`<sub>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/sub)元素可以解决这样的问题。例如：

```text
<p>My birthday is on the 25<sup>th</sup> of May 2001.</p>
<p>Caffeine's chemical formula is C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>.</p>
<p>If x<sup>2</sup> is 9, x must equal 3 or -3.</p>
```

这些代码输出的结果是：

My birthday is on the 25th of May 2001.

Caffeine's chemical formula is C8H10N4O2.

If x2 is 9, x must equal 3 or -3.

### 展示计算机代码[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E5%B1%95%E7%A4%BA%E8%AE%A1%E7%AE%97%E6%9C%BA%E4%BB%A3%E7%A0%81) <a id="&#x5C55;&#x793A;&#x8BA1;&#x7B97;&#x673A;&#x4EE3;&#x7801;"></a>

有大量的HTML元素可以来标记计算机代码：

*  [`<code>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/code): 用于标记计算机通用代码。
* [`<pre>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/pre): 对保留的空格（通常是代码块）——如果您在文本中使用缩进或多余的空白，浏览器将忽略它，您将不会在呈现的页面上看到它。但是，如果您将文本包含在`<pre></pre>`标签中，那么空白将会以与你在文本编辑器中看到的相同的方式渲染出来。
* [`<var>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/var): 用于标记具体变量名。
* [`<kbd>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/kbd): 用于标记输入电脑的键盘（或其他类型）输入。
* [`<samp>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/samp): 用于标记计算机程序的输出。

让我们看看一些例子。你应该尝试运行一下（尝试运行一下[other-semantics.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/advanced-text-formatting/other-semantics.html)样例文件的拷贝）：

```text
<pre><code>var para = document.querySelector('p');

para.onclick = function() {
  alert('Owww, stop poking me!');
}</code></pre>

<p>You shouldn't use presentational elements like <code>&lt;font&gt;</code> and <code>&lt;center&gt;</code>.</p>

<p>In the above JavaScript example, <var>para</var> represents a paragraph element.</p>


<p>Select all the text with <kbd>Ctrl</kbd>/<kbd>Cmd</kbd> + <kbd>A</kbd>.</p>

<pre>$ <kbd>ping mozilla.org</kbd>
<samp>PING mozilla.org (63.245.215.20): 56 data bytes
64 bytes from 63.245.215.20: icmp_seq=0 ttl=40 time=158.233 ms</samp></pre>
```

上面的代码显示效果如下：

### 标记时间和日期[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E6%A0%87%E8%AE%B0%E6%97%B6%E9%97%B4%E5%92%8C%E6%97%A5%E6%9C%9F) <a id="&#x6807;&#x8BB0;&#x65F6;&#x95F4;&#x548C;&#x65E5;&#x671F;"></a>

HTML 还支持将时间和日期标记为可供机器识别的格式的 [`<time>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/time) 元素。例如：

```text
<time datetime="2016-01-20">20 January 2016</time>
```

为什么需要这样做？因为世界上有许多种书写日期的格式，上边的日期可能被写成：

* 20 January 2016
* 20th January 2016
* Jan 20 2016
* 20/06/16
* 06/20/16
* The 20th of next month
* 20e Janvier 2016
* 2016年1月20日
* And so on

但是这些不同的格式不容易被电脑识别 — 假如你想自动抓取页面上所有事件的日期并将它们插入到日历中， [`<time>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/time) 元素允许你附上清晰的、可被机器识别的 时间/日期来实现这种需求。

上述基本的例子仅仅提供了一种简单的可被机器识别的日期格式，这里还有许多其他支持的格式，例如：

```text
<!-- Standard simple date -->
<time datetime="2016-01-20">20 January 2016</time>
<!-- Just year and month -->
<time datetime="2016-01">January 2016</time>
<!-- Just month and day -->
<time datetime="01-20">20 January</time>
<!-- Just time, hours and minutes -->
<time datetime="19:30">19:30</time>
<!-- You can do seconds and milliseconds too! -->
<time datetime="19:30:01.856">19:30:01.856</time>
<!-- Date and time -->
<time datetime="2016-01-20T19:30">7.30pm, 20 January 2016</time>
<!-- Date and time with timezone offset-->
<time datetime="2016-01-20T19:30+01:00">7.30pm, 20 January 2016 is 8.30pm in France</time>
<!-- Calling out a specific week number-->
<time datetime="2016-W04">The fourth week of 2016</time>
```

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

到这里你就完成了 HTML 语义文本元素的学习。但要记住，你在本课程中学到的并不是 HTML 文本元素的详细列表 — 我们想要尽量覆盖主要的、通用的、常见的，或者至少是有趣的部分。如果你想找到更多的 HTML 元素，可以看一看我们的[HTML 元素参考](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)（从 [内联文本语义](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element#%E5%86%85%E8%81%94%E6%96%87%E6%9C%AC%E8%AF%AD%E4%B9%89)部分开始会是一个好的选择） 。在下一篇文章中我们将会学习用来组织 HTML 文档不同部分的 HTML 元素。

