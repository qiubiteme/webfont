# 伪类和伪元素

在选择器系列文章的第三篇中，我们讨论伪选择器 。该选择器不是选择元素，而是元素的某些部分，或仅在某些特定上下文中存在的元素。它们有两种主要类型 ： 伪类和伪元素。

### 伪类（Pseudo-class）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%E4%BC%AA%E7%B1%BB%EF%BC%88Pseudo-class%EF%BC%89) <a id="&#x4F2A;&#x7C7B;&#xFF08;Pseudo-class&#xFF09;"></a>

一个 CSS  [伪类（pseudo-class）](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) 是一个以冒号\(`:`\)作为前缀，被添加到一个选择器末尾的关键字，当你希望样式在特定状态下才被呈现到指定的元素时，你可以往元素的选择器后面加上对应的伪类（pseudo-class）。你可能希望某个元素在处于某种状态下呈现另一种样式，例如当鼠标悬停在元素上面时，或者当一个复选框被禁用或被勾选时，又或者当一个元素是它在 DOM 树中父元素的第一个子元素时。

*  [`:active`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:active)
* [`:any`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:any)
* [`:checked`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:checked)
* [`:default`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:default)
* [`:dir()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:dir)
* [`:disabled`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:disabled)
* [`:empty`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:empty)
* [`:enabled`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:enabled)
* [`:first`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:first)
* [`:first-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:first-child)
* [`:first-of-type`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:first-of-type)
* [`:fullscreen`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:fullscreen)
* [`:focus`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:focus)
* [`:hover`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:hover)
* [`:indeterminate`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:indeterminate)
* [`:in-range`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:in-range)
* [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid)
* [`:lang()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:lang)
* [`:last-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:last-child)
* [`:last-of-type`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:last-of-type)
* [`:left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:left)
* [`:link`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:link)
* [`:not()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:not)
* [`:nth-child()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-child)
* [`:nth-last-child()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-last-child)
* [`:nth-last-of-type()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-last-of-type)
* [`:nth-of-type()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-of-type)
* [`:only-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:only-child)
* [`:only-of-type`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:only-of-type)
* [`:optional`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:optional)
* [`:out-of-range`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:out-of-range)
* [`:read-only`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:read-only)
* [`:read-write`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:read-write)
*  [`:required`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:required)
* [`:right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:right)
*  [`:root`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:root)
* [`:scope`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:scope)
* [`:target`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:target)
*  [`:valid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:valid)
* [`:visited`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:visited)

我们不会立马深入讲解每一个伪类（pseudo-class），在学习领域中，详尽无遗地教给你每一件事不是目的。在适当的时候，你会更加详尽的了解一些内容。

#### 一个伪类（Pseudo-class）的例子[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%E4%B8%80%E4%B8%AA%E4%BC%AA%E7%B1%BB%EF%BC%88Pseudo-class%EF%BC%89%E7%9A%84%E4%BE%8B%E5%AD%90) <a id="&#x4E00;&#x4E2A;&#x4F2A;&#x7C7B;&#xFF08;Pseudo-class&#xFF09;&#x7684;&#x4F8B;&#x5B50;"></a>

现在，让我们来看一个简单的使用例子。首先是一个 HTML 片段：

```text
<a href="https://developer.mozilla.org/" target="_blank">Mozilla Developer Network</a>
```

然后，一些 CSS 样式：

```text
/* 这些样式将在任何情况下应用于我们
的链接 */

a {
  color: blue;
  font-weight: bold;
}

/* 我们想让被访问过的链接和未被访问
的链接看起来一样 */

a:visited {
  color: blue;
}

/* 当光标悬停于链接，键盘激活或锁定
链接时，我们让链接呈现高亮 */

a:hover,
a:active,
a:focus {
  color: darkred;
  text-decoration: none;
}
```

现在，我们可以跟修改了样式的链接愉快地玩耍了！

在 CodePen 中打开在 JSFiddle 中打开

#### 主动学习：一个条纹状的信息列表[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E4%B8%80%E4%B8%AA%E6%9D%A1%E7%BA%B9%E7%8A%B6%E7%9A%84%E4%BF%A1%E6%81%AF%E5%88%97%E8%A1%A8) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x4E00;&#x4E2A;&#x6761;&#x7EB9;&#x72B6;&#x7684;&#x4FE1;&#x606F;&#x5217;&#x8868;"></a>

又轮到你了。在这个主动学习环节中，我们希望你为信息列表增加条纹状效果，然后增加合适的伪类使得里面的链接在鼠标经过时显得不同。在这个练习中，你只需要修改最后的三条规则。一些提示：

1. 你应该已经知道怎样使用伪类实现悬停样式。
2. 对于条纹状效果，你需要用到一个伪类，如[`:nth-of-type()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-of-type)，通过给那两个颜色规则添加稍微不同的伪类，使得列表的奇数行和偶数行有着不同的样式效果。来看看你有没有找到实现的方法！

如果你写错了，你可以使用 Reset 按钮进行重置。如果你实在不知道怎么实现，按 Show 按钮可以看到答案。

在 CodePen 中打开在 JSFiddle 中打开

### 伪元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%E4%BC%AA%E5%85%83%E7%B4%A0) <a id="&#x4F2A;&#x5143;&#x7D20;"></a>

[伪元素（Pseudo-element）](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)跟伪类很像，但它们又有不同的地方。它们都是关键字，但这次伪元素前缀是两个冒号 \(`::`\) ， 同样是添加到选择器后面去选择某个元素的某个部分。

* [`::after`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::after)
* [`::before`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::before)
* [`::first-letter`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::first-letter)
* [`::first-line`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::first-line)
* [`::selection`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::selection)
* [`::backdrop`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::backdrop)

它们都拥有特别的行为和有趣的特性，但我们不会在这里对它们都进行深入探究。

#### 一个伪元素（pseudo-element）例子[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%E4%B8%80%E4%B8%AA%E4%BC%AA%E5%85%83%E7%B4%A0%EF%BC%88pseudo-element%EF%BC%89%E4%BE%8B%E5%AD%90) <a id="&#x4E00;&#x4E2A;&#x4F2A;&#x5143;&#x7D20;&#xFF08;pseudo-element&#xFF09;&#x4F8B;&#x5B50;"></a>

我们在这里仅展示一个简单的 CSS 例子，就是如何在所有超链接元素后面的增加一个箭头：

```text
<ul>
  <li><a href="https://developer.mozilla.org/en-US/docs/Glossary/CSS">CSS</a> defined in the MDN glossary.</li>
  <li><a href="https://developer.mozilla.org/en-US/docs/Glossary/HTML">HTML</a> defined in the MDN glossary.</li>
</ul>
```

让我们加上 CSS 规则：

```text
/* 所有含有"href"属性并且值以"http"开始的元素，
将会在其内容后增加一个箭头（去表明它是外部链接）
*/

[href^=http]::after {
  content: '⤴';
}
```

我们可以得到这样的效果：

在 CodePen 中打开在 JSFiddle 中打开

#### 主动学习：一个很棒棒的段落[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E4%B8%80%E4%B8%AA%E5%BE%88%E6%A3%92%E6%A3%92%E7%9A%84%E6%AE%B5%E8%90%BD) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x4E00;&#x4E2A;&#x5F88;&#x68D2;&#x68D2;&#x7684;&#x6BB5;&#x843D;"></a>

下面是主动学习部分，我们有一个很棒棒的段落需要装饰！你需要做的事是给出两个规则集分别指定段落的第一行和第一个单词，可以使用伪元素 [`::first-line` ](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::first-line)和 [`::first-letter`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::first-letter) 得到需要的。元素需要的效果，是段落的第一行使用粗体字，它的第一个单词首字母大写并给它一种老式的感觉。

如果你写错了，你可以使用 Reset 按钮进行重置。如果你实在不知道怎么实现，按 Show 按钮可以看到答案。

在 CodePen 中打开在 JSFiddle 中打开

### 下一步[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%E4%B8%8B%E4%B8%80%E6%AD%A5) <a id="&#x4E0B;&#x4E00;&#x6B65;"></a>

我们将会从[选择符和多重选择器（Combinators and multiple selectors）](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors/Combinators_and_multiple_selectors)结束我们对 CSS 选择器的学习。

