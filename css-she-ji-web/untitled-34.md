# CSS如何工作

[**CSS**](https://developer.mozilla.org/en-US/docs/Glossary/CSS) （层叠样式表）允许你创建好看的网页，但它在底层是如何工作的？这篇文章解释了什么是 CSS，浏览器是怎么把 HTML 转换为文档对象模型  \([DOM](https://developer.mozilla.org/en-US/docs/Glossary/DOM)\)， CSS是怎样被应用于 DOM 各个部分的，一些语法非常基础的例子和我们网页实际上用什么代码来包含我们的 CSS 。

| 前提： | 基本的计算机使用能力，[已安装基本的软件](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software)，[文件处理](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/Dealing_with_files)的基本知识，以及 HTML 基础 （学习 [HTML入门](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML)。） |
| :--- | :--- |
| 目标： | 学习什么是 CSS， 以及它在基本层面上如何工作。 |

### 什么是 CSS?[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E4%BB%80%E4%B9%88%E6%98%AF_CSS) <a id="&#x4EC0;&#x4E48;&#x662F;_CSS"></a>

正如我们之前提到的，CSS是一种用于向用户指定文档如何呈现的语言 — 它们如何被指定样式、布局等。

**文档**通常是用标记语言结构化的文本文件 — [HTML](https://developer.mozilla.org/en-US/docs/Glossary/HTML) 是最常用的标记语言, 但你依然可以遇见一些其他的标记语言，比如 [SVG](https://developer.mozilla.org/en-US/docs/Glossary/SVG) 或者 [XML](https://developer.mozilla.org/en-US/docs/Glossary/XML)。

**呈现**文档给用户意味着将其转换为用户可用的形式。[浏览器](https://developer.mozilla.org/en-US/docs/Glossary/browser)，比如 [Firefox](https://developer.mozilla.org/en-US/docs/Glossary/Mozilla_Firefox), [Chrome](https://developer.mozilla.org/en-US/docs/Glossary/Google_Chrome) 或者 [Internet Explorer](https://developer.mozilla.org/en-US/docs/Glossary/Microsoft_Internet_Explorer)，被设计用于可视化呈现文档，例如，在计算机屏幕，投影仪或打印机上。

### CSS如何影响HTML？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#CSS%E5%A6%82%E4%BD%95%E5%BD%B1%E5%93%8DHTML%EF%BC%9F) <a id="CSS&#x5982;&#x4F55;&#x5F71;&#x54CD;HTML&#xFF1F;"></a>

Web浏览器将CSS规则应用于文档以影响它们的显示方式。一个CSS规则由以下组成：

* 一组 [属性](https://developer.mozilla.org/en-US/docs/Glossary/property/CSS) ，属性的值更新了 HTML 的内容的显示方式。比如，我想让元素的宽度是其父元素的50％，或者元素背景变为红色。
* 一个 [选择器](https://developer.mozilla.org/en-US/docs/Glossary/CSS_Selector)，它选择元素，这（些）元素是你想应用这些最新的属性值于其上的元素。比如，我想将我的CSS规则应用到我HTML文档中的所有段落上。

**样式表**中的一组CSS规则确定了网页如何显示，你将在下一篇文章中了解更多关于CSS语法的内容 — [CSS 语法](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax)。

#### 一个CSS快速示例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E4%B8%80%E4%B8%AACSS%E5%BF%AB%E9%80%9F%E7%A4%BA%E4%BE%8B) <a id="&#x4E00;&#x4E2A;CSS&#x5FEB;&#x901F;&#x793A;&#x4F8B;"></a>

上面的描述可能不太清楚，所以让我们通过一个快速示例来确保清楚事物。首先，我们使用一个简单的HTML文档，包含一个 [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1) 元素和一个 [`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 元素（\(注意到通过使用一个 [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link) 元素将样式表应用到了 HTML 上）：

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
  </body>
</html>
```

现在让我们来看一个包含了两个规则的非常简单的CSS例子：

```text
h1 {
  color: blue;
  background-color: yellow;
  border: 1px solid black;
}

p {
  color: red;
}
```

第一条规则从 `h1` 选择器开始，这意味着它将其属性值应用到 [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1) 元素上，它包含三个属性和属性各自的值（每个 属性/值 对称为一个声明）：

1. 第一个声明将文本颜色设置为蓝色；
2. 第二个声明将背景颜色设置为黄色；
3. 第三个声明将标题（h1是标题元素）边框（border）设置为：1像素宽、实线（不是虚线、点线等）、颜色黑色。

第二个规则从 p 选择器开始，这意味着它将其属性值应用到 [`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 元素上。它包含一条声明，该声明设置字体颜色为红色。

在Web浏览器中，上面的代码将产生以下输出：

![A simple webpage containing a header of Hello World, and a paragraph that says This is my first CSS example](https://mdn.mozillademos.org/files/12537/first-example.png)

这不怎么好看，但至少让你开始有了点 CSS 如何工作的概念。

#### 主动学习：编写你的第一个 CSS[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E7%BC%96%E5%86%99%E4%BD%A0%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA_CSS) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x7F16;&#x5199;&#x4F60;&#x7684;&#x7B2C;&#x4E00;&#x4E2A;_CSS"></a>

现在我们给你个机会来编写一些你自己的 CSS。你可以使用下面的实时可编辑示例的输入区域完成这些。与上面所看到的类似，您有一些简单的HTML元素和一些CSS属性。试着添加一些简单的声明到你的CSS来定义 HTML 的样式。

如果写错了，你可以随时点击 “重置” 按钮重置。如果你真的不知道怎么写，点击显示结果按钮查看一个可行的解答。

在 CodePen 中打开在 JSFiddle 中打开

### CSS 实际上如何工作？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#CSS_%E5%AE%9E%E9%99%85%E4%B8%8A%E5%A6%82%E4%BD%95%E5%B7%A5%E4%BD%9C%EF%BC%9F) <a id="CSS_&#x5B9E;&#x9645;&#x4E0A;&#x5982;&#x4F55;&#x5DE5;&#x4F5C;&#xFF1F;"></a>

当浏览器显示文档时，它必须将文档的内容与其样式信息结合。它分两个阶段处理文档：

1. 浏览器将 [HTML](https://developer.mozilla.org/en-US/docs/Glossary/HTML) 和 [CSS](https://developer.mozilla.org/en-US/docs/Glossary/CSS) 转化成 [DOM](https://developer.mozilla.org/en-US/docs/Glossary/DOM) （_文档对象模型_）。DOM在计算机内存中表示文档。它把文档内容和其样式结合在一起。
2. 浏览器显示 DOM 的内容。

![](https://mdn.mozillademos.org/files/11781/rendering.svg)

### 关于 DOM[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E5%85%B3%E4%BA%8E_DOM) <a id="&#x5173;&#x4E8E;_DOM"></a>

DOM是一种树形结构. 标记语言中的每个元素,属性,文本片段都变为一个 [DOM 节点](https://developer.mozilla.org/en-US/docs/Glossary/Node/DOM)。这些节点由它们与其它 DOM 节点的关系来定义。有的元素是某些子节点的父节点，且这些子节点有兄弟（节点）。

由于 DOM 是 CSS 与文档内容的相遇之处，理解 DOM 有助于设计，调试和维护你的 CSS 文件。

#### 表示DOM[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E8%A1%A8%E7%A4%BADOM) <a id="&#x8868;&#x793A;DOM"></a>

相对于漫长而无聊的解释，让我们通过一个例子来看一下 DOM 和 CSS 如何一同工作。

让我们假定下面这段HTML代码：

```text
<p>
  Let's use:
  <span>Cascading</span>
  <span>Style</span>
  <span>Sheets</span>
</p>
```

在该 DOM 中，我们的 `<p>` 元素所对应的节点是父节点。它的子节点是一个文本节点和我们的一些 `<span>` 元素对应的节点。这些 `SPAN` 结点也是父节点，它们各自的文本节点就是它们的子节点：

```text
P
├─ "Let's use:"
├─ SPAN
|  └─ "Cascading"
├─ SPAN
|  └─ "Style"
└─ SPAN
   └─ "Sheets"
```

这就是浏览器解释先前的HTML片段的过程 —它渲染上述的DOM树，之后在浏览器中像这样输出它。

在 CodePen 中打开在 JSFiddle 中打开

#### 应用 CSS 到 DOM[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E5%BA%94%E7%94%A8_CSS_%E5%88%B0_DOM) <a id="&#x5E94;&#x7528;_CSS_&#x5230;_DOM"></a>

假设我们要添加一些 CSS 到我们的文档上，使其更具风格。再一次，HTML 如下所示：

```text
<p>
  Let's use:
  <span>Cascading</span>
  <span>Style</span>
  <span>Sheets</span>
</p>
```

如果我们将下面 CSS 应用到它上：

```text
span {
  border: 1px solid black;
  background-color: lime;
}
```

浏览器会解析 HTML 并通过它创建 DOM，之后解析 CSS。由于 CSS 只有一个可用的规则，该规则有一个span选择器，它会将这个规则应用到这三个`<span>`的每一个上。更新后的输出如下所示：

在 CodePen 中打开在 JSFiddle 中打开

### 如何将你的 CSS 应用到你的 HTML 上[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E5%A6%82%E4%BD%95%E5%B0%86%E4%BD%A0%E7%9A%84_CSS_%E5%BA%94%E7%94%A8%E5%88%B0%E4%BD%A0%E7%9A%84_HTML_%E4%B8%8A) <a id="&#x5982;&#x4F55;&#x5C06;&#x4F60;&#x7684;_CSS_&#x5E94;&#x7528;&#x5230;&#x4F60;&#x7684;_HTML_&#x4E0A;"></a>

这有你常见的三种不同方式将 CSS 应用到 HTML 文档上，有的方式比其他方式更有用。在这里，我们将简要回顾一下每一种方式：

#### 外部样式表[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E5%A4%96%E9%83%A8%E6%A0%B7%E5%BC%8F%E8%A1%A8) <a id="&#x5916;&#x90E8;&#x6837;&#x5F0F;&#x8868;"></a>

你已经在这篇文章看到了外部样式表，但是并不知道它的名字。外部样式表是指：当你将你的 CSS 保存在一个独立的扩展名为 .css 的文件中，并从HTML的 [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link) 元素中引用它。此时 HTML 文件看起来像这样：

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
  </body>
</html>
```

以及下面的 CSS 文件

```text
h1 {
  color: blue;
  background-color: yellow;
  border: 1px solid black;
}

p {
  color: red;
}
```

这种方法可以说是最好的，因为你可以使用一个样式表来设置多个文档的样式，并且需要更新 CSS 的时候只要在一个地方更新。

#### 内部样式表[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E5%86%85%E9%83%A8%E6%A0%B7%E5%BC%8F%E8%A1%A8) <a id="&#x5185;&#x90E8;&#x6837;&#x5F0F;&#x8868;"></a>

内部样式表是指不使用外部 CSS 文件，而是将你的 CSS 放置在[`<style>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/style) 元素中，该元素包含在 [HTML head](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML) 内。此时HTML看起来像这样：

```text
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }

      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

这在某些情况下很有用（也许你正在使用一个内容管理系统，不能直接修改 CSS 文件），但它不如外部样式表高效 —— 在网站中，CSS 将需要在每个页面重复，并且需要更新时要更改的多个位置。

#### 内联样式[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E5%86%85%E8%81%94%E6%A0%B7%E5%BC%8F) <a id="&#x5185;&#x8054;&#x6837;&#x5F0F;"></a>

内联样式是仅影响一个元素的CSS声明，被 [`style`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-style) 属性包括着:

```text
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
  </head>
  <body>
    <h1 style="color: blue;background-color: yellow;border: 1px solid black;">Hello World!</h1>
    <p style="color:red;">This is my first CSS example</p>
  </body>
</html>
```

除非有必要，否则不要这么做！这很难维护（你可能不得不在每份文档里更新多次同样的信息），并且它还混合了 CSS 表示的样式信息和 HTML 的结构信息，使 CSS 难以阅读和理解。保持不同类型代码的分离和纯净使处理该代码的任何人工作更为容易。

您唯一可能需要使用内联样式是当您的工作环境真的非常受限（也许您的CMS只允许您编辑 HTML 的 body）。

### 下一步[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works#%E4%B8%8B%E4%B8%80%E6%AD%A5) <a id="&#x4E0B;&#x4E00;&#x6B65;"></a>

到了这里你应该理解了 CSS 的基本工作原理和你的浏览器如何处理 CSS。接下来你将会学习 [CSS语法](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Syntax)。

