# CSS 语法

接下来，我们将更详细的深入CSS语法，学习_属性_和_值如何_组成一个_声明，_多个声明构成的_声明块_，以及声明块和_选择器如何_构成完整的 _CSS 规则_。同时，我们也将介绍一些其他的CSS语法特征，例如注释和空白等。

| 前提： | 基本的计算机使用能力，[已安装基本的软件](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software)，[文件处理](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Dealing_with_files)的基本知识，以及 HTML 基础 （学习 [HTML入门](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML)），以及[CSS 如何工作](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works)的概念。 |
| :--- | :--- |
| 目标： | 详细学习基本的 CSS 语法结构 |

**注意：**CSS 是一种声明式语言，这令其语法相当简单直观且易于理解。此外，CSS还有着相当不错的错误修复系统，这一特性允许你犯一些错误但并不会造成什么异常影响 —— 比如，有可能你的某些声明浏览器并不理解，这时浏览器会直接忽略掉这些内容并继续执行渲染。当然这一特性也可能导致一些问题，比如一些异常情况出现的时候，可能在定位问题原因上造成一些障碍。随着阅读的深入，这些优势和缺点都将逐渐清晰。

### 认识些新名词[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#%E8%AE%A4%E8%AF%86%E4%BA%9B%E6%96%B0%E5%90%8D%E8%AF%8D) <a id="&#x8BA4;&#x8BC6;&#x4E9B;&#x65B0;&#x540D;&#x8BCD;"></a>

从最基本的层次来看，CSS是由两块内容组合而成的：

* **属性（Property）：**一些人类可理解的标识符，这些标识符指出你想修改哪一些样式，例如：字体，宽度，背景颜色等。
* **属性值（Value）**：每个指定的属性都需要给定一个值，这个值表示你想把那些样式特征修改成什么样，例如，你想把字体，宽度或背景颜色改成什么。

_与值配对的属性被称为_[_CSS声明_](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#CSS%20%E5%A3%B0%E6%98%8E)_。_CSS声明会被放置在一个_CSS声明块_中。最后，CSS声明块与_选择器_相结合形成一个_CSS规则集（或CSS规则）_。

在深入那些原理和书面解释之前，让我们先看一个具体的例子（和我们在上篇文章中看的非常相似）

```text
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>

    <ul>
      <li>This is</li>
      <li>a list</li>
    </ul>
  </body>
</html>
```

以及对应的 CSS 文件：

```text
h1 {
  color: blue;
  background-color: yellow;
  border: 1px solid black;
}

p {
  color: red;
}

p, li {
  text-decoration: underline;
}
```

两者的结合得到了如下的效果:

让我们来看看语法的更多细节。

#### CSS 声明[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#CSS_%E5%A3%B0%E6%98%8E) <a id="CSS_&#x58F0;&#x660E;"></a>

给 CSS 属性设置特定的值是 CSS 语言的核心功能。CSS 引擎会通过计算，将对应的 CSS 声明应用到页面的每一个元素上，从而使得元素们以适当的方式布局，并展示出适当的样式。特别需要记住的是，CSS 的属性和属性值都是区分大小写的。属性和属性值之间，用英文半角冒号 \(`:`\) 隔离，如下图所示。

![css &#x8BED;&#x6CD5; - &#x58F0;&#x660E;](https://mdn.mozillademos.org/files/16188/css_syntax_-_declaration.png)

CSS 有超过[300 个不同的属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference)以及几乎无穷无尽的属性值。属性和属性值不能任意组合：每个属性都有一个已经定义好的可用属性值范围。 

**重要**: 如果使用了未知属性，或者给属性赋予了无效值，该声明会被视为无效，浏览器的 CSS 引擎会完全忽略它。

**重要**: 在 CSS（和其他网络标准）中，使用美式拼写作为单词的标准写法。例如，颜色（见于上述代码所见）应始终拼写为 `color`。写成 `colour` 会无法正常工作。

**主动学习: 找出声明**

在上面的例子里, 有**五个**独立的CSS声明。你能找出其中无效的声明，并找出它无效的原因吗？

#### CSS 声明块[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#CSS_%E5%A3%B0%E6%98%8E%E5%9D%97) <a id="CSS_&#x58F0;&#x660E;&#x5757;"></a>

声明按**块**分组，每一组声明都用一对大括号包裹，用 \(`{`\) 开始，用 \(`}`\) `结束`。

**声明块**里的每一个声明必须用半角分号（`;`）分隔，否则代码会不生效（至少不会按预期结果生效）。声明块里的最后一个声明结束的地方，不需要加分号，但是最后加分号是个好习惯，因为可以防止在后续增加声明时忘记加分号。

![](https://mdn.mozillademos.org/files/3667/css%20syntax%20-%20declarations%20block.png)

**注意：**块有时候是可以嵌套的。这种情况下，每一对括号必须逻辑上嵌套，跟嵌套 HTML 元素的标签嵌套方式相同。最常见的例子是 _@-rules，_这是一种用 @ 标识开头的块，例如 [`@media`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media), [`@font-face`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@font-face)等（详见下述的 [_CSS 语句_](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#CSS%20%E8%AF%AD%E5%8F%A5)_）_。

**注意**：声明块的内容允许为空 —— 这完全有效。

**主动学习：声明块在哪？**

在上述的例子里，你能找到**三个**独立的 CSS 声明块吗？

#### CSS 选择器和规则[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#CSS_%E9%80%89%E6%8B%A9%E5%99%A8%E5%92%8C%E8%A7%84%E5%88%99) <a id="CSS_&#x9009;&#x62E9;&#x5668;&#x548C;&#x89C4;&#x5219;"></a>

我们的拼图还少了一块——我们需要讨论一下如何告知我们的声明块：哪些元素是它们需要应用的。通过在每个声明块前加上**选择器（selector）**来完成这一动作，选择器是一种模式，它能在页面上匹配一些元素**。**这将使相关的声明仅被应用到被选择的元素上。选择器加上声明块被称为**规则集（ruleset**），通常简称**规则**（**rule**）。

![](https://mdn.mozillademos.org/files/3668/css%20syntax%20-%20ruleset.png)

选择器可以很复杂 —— 你可以制作一个匹配多种元素的规则，这是通过把多个选择器囊括成用逗号分隔的选择器（一组,）来达成；选择器还可以被“链”在一起，例如_我要选择所有 class 是 "blah" 的元素, 但是当且仅当它在 &lt;article&gt; 元素里、并且仅当鼠标指针悬停在这个元素上的时候。_ 别担心：随着你在CSS上的经验变的更丰富，事情会变的更清晰，并且我们将会在下一篇文章[选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Selectors)里，详细地解释选择器。

一个元素可以被多个选择器所匹配，因此，一个给定的属性可能被多个规则设置多次。 CSS 定义了哪个规则比其它规则更具优先级，则更具优先级的规则必定被应用：这被称为**层叠算法（cascade algorithm）**，关于层叠算法的更多内容和运作原理见[层叠和继承](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance)。

**重要**：如果链或组中的某个选择器无效，比如使用了未知的伪元素或伪类，整个组的选择器仍然是有效的，除了这个无效的将被忽略的选择器。

**主动学习：找出选择器组**

在我们的例子中，你能找到能应用到**两种**不同类型的元素上的规则吗？

#### CSS 语句（CSS statements）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#CSS_%E8%AF%AD%E5%8F%A5%EF%BC%88CSS_statements%EF%BC%89) <a id="CSS_&#x8BED;&#x53E5;&#xFF08;CSS_statements&#xFF09;"></a>

CSS 规则是样式表的主要组成块 —— 是你在 CSS 中最常见的块。但这有一些其它类型的块，你以后偶尔会碰上 —— CSS 规则只是被称为 CSS 语句中的一种。其它类型如下：

* **@-规则\(At-rules\)**在CSS中被用来传递元数据、条件信息或其它描述性信息。它由（`@`）符号开始，紧跟着一个表明它是哪种规则的描述符，之后是这种规则的语法块，并最终由一个半角分号（`;`）结束。每种由描述符定义的[@-规则](https://developer.mozilla.org/zh-CN/docs/Web/CSS/At-rule)，都有其特有的内部语法和语义。一些例子如下：

  *  [`@charset`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@charset) 和 [`@import`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@import) （元数据）
  * [`@media`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media) 或 [`@document`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@document) （条件信息，又被称为嵌套语句，见下方。\)
  * [`@font-face`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@font-face) （描述性信息）

  具体语法示例：

  ```text
  @import 'custom.css';
  ```

  该@-规则向当前 CSS 导入其它 CSS 文件

* **嵌套语句** 是@-规则中的一种，它的语法是 CSS 规则的嵌套块，只有在特定条件匹配时才会应用到文档上。特定条件如下：

  * [`@media`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media) 只有在运行浏览器的设备匹配其表达条件时才会应用该@-规则的内容；
  * [`@supports`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@supports) 只有浏览器确实支持被测功能时才会应用该@-规则的内容；
  * [`@document`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@document) 只有当前页面匹配一些条件时才会应用该@-规则的内容。

  具体语法示例

  ```text
  @media (min-width: 801px) {
    body {
      margin: 0 auto;
      width: 800px;
    }
  }
  ```

  上述的嵌套语句只有在页面宽度超过801像素时才会应用。

你将会在本门课程的适当位置学习@-规则/嵌套语句的其他一些类型。

**重要**：任何不是规则集或@-规则或嵌套语句的 CSS 语句都是无效的，并会因此被忽略。

### 语法之外：使 CSS 更具可读性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#%E8%AF%AD%E6%B3%95%E4%B9%8B%E5%A4%96%EF%BC%9A%E4%BD%BF_CSS_%E6%9B%B4%E5%85%B7%E5%8F%AF%E8%AF%BB%E6%80%A7) <a id="&#x8BED;&#x6CD5;&#x4E4B;&#x5916;&#xFF1A;&#x4F7F;_CSS_&#x66F4;&#x5177;&#x53EF;&#x8BFB;&#x6027;"></a>

正如你所见的，CSS 语法并不难写：如果你写了一些错误的规则，它将仅被忽略。但是，即使有这样的机制，这也有一些值得了解的最佳实践，使您的CSS代码更易于使用和维护。

#### 空格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#%E7%A9%BA%E6%A0%BC) <a id="&#x7A7A;&#x683C;"></a>

空格实际上意味着一些空格，一些制表符以及一些新行。你可以通过添加空格使你的样式表更具可读性。

用与处理 HTML 的方式类似，浏览器会倾向于忽略你 CSS 中的许多空格；许多空格在那的意义仅仅是增加了可读性。在下面的第一个例子中，我们的每个声明（以及规则的开始 / 结束）都在自己各自的行上 —— 这可以说是编写 CSS 的好方法，因为它很容易维护和理解：

```text
body {
  font: 1em/150% Helvetica, Arial, sans-serif;
  padding: 1em;
  margin: 0 auto;
  max-width: 33em;
}

@media (min-width: 70em) {
  body {
    font-size: 130%;
  }
}

h1 {
  font-size: 1.5em;
}

div p, #id:first-line {
  background-color: red;
  background-style: none
}

div p {
  margin: 0;
  padding: 1em;
}

div p + p {
  padding-top: 0;
}
```

你可以编写跟这完全一样的CSS，并移除大部分空格，它在功能上和第一个例子完全相同，但我确信你会同意这样有些难读：

```text
body {font: 1em/150% Helvetica, Arial, sans-serif; padding: 1em; margin: 0 auto; max-width: 33em;}
@media (min-width: 70em) { body {font-size: 130%;} }

h1 {font-size: 1.5em;}

div p, #id:first-line {background-color: red; background-style: none}
div p {margin: 0; padding: 1em;}
div p + p {padding-top: 0;}
```

你选择的代码布局通常依据个人喜好，但当你开始在团队中工作时，你可能会发现团队已有自己的风格指南，约定了代码编写规范。

您在CSS中需要注意的空格是属性和属性值边上的空格。例如，以下是有效的CSS：

```text
margin: 0 auto;
padding-left: 10px;
```

但以下是无效的：

```text
margin: 0auto;
padding- left: 10px;
```

因为 `0auto` 不被解析为 margin 属性的有效值（`0`和`auto`是两个单独的值），并且浏览器不会将 `padding-` 解析为有效属性。因此，你应该始终确保至少用一个空格分隔不同的值，且保持属性名/值为一个连续的字符串。

#### 注释[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#%E6%B3%A8%E9%87%8A) <a id="&#x6CE8;&#x91CA;"></a>

与HTML一样，我们鼓励您在CSS中使用注释，以帮助您在几个月后遇上代码时了解代码如何工作，并帮助他人理解该代码。它同样对暂时注释某些部分的代码进行测试很有用，例如当您尝试查找是代码的哪一部分导致错误时。

CSS中的注释以 `/*` 开始并以 `*/` 结束。

```text
/* 基本元素样式 */
/* -------------------------------------------------------------------------------------------- */
body {font: 1em/150% Helvetica, Arial, sans-serif; padding: 1em; margin: 0 auto; max-width: 33em;}
@media (min-width: 70em) {
  /* 特别指明全局字体大小，在大屏或大窗口下加大字体大小以增加可读性 */
  body {font-size: 130%;}
}

h1 {font-size: 1.5em;}

/* 处理嵌套在DOM中的特定元素  */
/* -------------------------------------------------------------------------------------------- */
div p, #id:first-line {background-color: red; background-style: none}
div p                 {margin          :   0; padding         : 1em;}
div p + p             {padding-top     :   0;                       }
```

#### 简写[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#%E7%AE%80%E5%86%99) <a id="&#x7B80;&#x5199;"></a>

一些属性比如 [`font`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font)，[`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background)，[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)，[`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)，和 [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin) 被称为**简写属性** —— 这是由于它们允许你在一行设置多个属性，从而节省时间并使代码更整洁。

例如，像这行代码：

```text
/* 在padding和margin这样的简写属性中，值赋值的顺序是top、right、bottom、left。 
   它们还有其他简写方式，例如给padding两个值，则第一个值表示top/bottom，第二个值表示left/right */
padding: 10px 15px 15px 5px;
```

和以下的所有代码做了相同的工作：

```text
padding-top: 10px;
padding-right: 15px;
padding-bottom: 15px;
padding-left: 5px;
```

而这一行：

```text
background: red url(bg-graphic.png) 10px 10px repeat-x fixed;
```

和以下这些做了相同的事：

```text
background-color: red;
background-image: url(bg-graphic.png);
background-position: 10px 10px;
background-repeat: repeat-x;
background-scroll: fixed;
```

我们不会试图彻底全面地教导你这些东西 —— 你会在后续的课程中遇到很多例子，建议你通过简写属性的名称在我们的 [CSS参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference) 中查找以了解更多信息。

### 下一步做什么[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax#%E4%B8%8B%E4%B8%80%E6%AD%A5%E5%81%9A%E4%BB%80%E4%B9%88) <a id="&#x4E0B;&#x4E00;&#x6B65;&#x505A;&#x4EC0;&#x4E48;"></a>

到此为止，你应该已经了解编写一个易于维护的工作样式表所需的CSS语法的基本知识。在下一篇文章中，我们将深入[CSS选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Selectors)，查看可用的不同选择器以及它们的工作原理。

