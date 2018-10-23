# HTML 入门

通过本文，我们将带领您从HTML最基础的部分开始学习 - 我们定义元素，属性以及您可能听到的其他重要术语，以及它们在语言中的合适位置。我们还告诉你HTML元素的结构组成，以及一个典型HTML页面的结构，当然也会解释其他一些重要的基本语言特性。学习的同时，我们会使用HTML做一些好玩的事情，让你对HTML更加感兴趣！

| 基础要求: | 基本的计算机素养,  基本软件安装, 和使用文件的基本知识. |
| :--- | :--- |
| 目的: | 要获得对HTML语言的基本熟悉，并获得一些练习写几个HTML元素。 |

### 什么是 HTML?[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E4%BB%80%E4%B9%88%E6%98%AF_HTML) <a id="&#x4EC0;&#x4E48;&#x662F;_HTML"></a>

[HTML](https://developer.mozilla.org/en-US/docs/Glossary/HTML) \(HyperText Markup Language\) 不是一种编程语言;它是一种标记语言，用于告诉您的浏览器如何构造您访问的网页。它可以像Web开发人员希望的那样复杂或简单。 HTML由一系列的 [元素](https://developer.mozilla.org/en-US/docs/Glossary/Element)组成, 您可以使用它来封装，包装或标记内容的不同部分，使其以某种方式显示，或以某种方式执行。封闭 [tags](https://developer.mozilla.org/en-US/docs/Glossary/Tag) 可以使一点内容成为超链接以链接到Web上的另一页面，斜体字等等。例如，采取以下行内容：

```text
My cat is very grumpy
```

如果我们想要自己的行，我们可以指定它是一个段落通过将它包含在段落标签\([`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p)\) 元素：

```text
<p>My cat is very grumpy</p>
```

注意：HTML中的标签是不区分大小写的。也就是说，当你输入标签时，你既可以使用大写字母也可以使用小写字母。例如，标签 [`<title>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/title)可以写作`<title>`，`<TITLE>`，`<Title>`，`<TiTlE>`，等等，它们都可以正常工作。不过，从一致性、可读性和其他各方面来说，最好仅使用小写字母。

### 剖析一个 HTML 元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%89%96%E6%9E%90%E4%B8%80%E4%B8%AA_HTML_%E5%85%83%E7%B4%A0) <a id="&#x5256;&#x6790;&#x4E00;&#x4E2A;_HTML_&#x5143;&#x7D20;"></a>

让我们进一步探讨我们的段落元素：

![](https://mdn.mozillademos.org/files/9347/grumpy-cat-small.png)

我们的元素的主要部分是：

1. **开始标签（Opening tag）：**包括元素的名称（在本例中，p），包裹在开始和结束尖括号中。这表示元素开始或开始生效 - 在这种情况下，表示了一个段落的开头。
2. **结束标签（Closing tag）：**这与开始标记相同，除了它在元素名称之前包含正斜杠。这表示元素结束的位置 - 在这种情况下，表示了一个段落的结尾. 没有包含结束标记是一个常见的初学者错误，并可能导致奇怪的结果。
3. **内容（Content）：**这是元素的内容，在这种情况下只是文本。
4. **元素（Element）：**开始标记，加结束标记，加内容，等于元素。

#### 实践学习: 创建你的第一个HTML文档[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%AE%9E%E8%B7%B5%E5%AD%A6%E4%B9%A0_%E5%88%9B%E5%BB%BA%E4%BD%A0%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AAHTML%E6%96%87%E6%A1%A3) <a id="&#x5B9E;&#x8DF5;&#x5B66;&#x4E60;_&#x521B;&#x5EFA;&#x4F60;&#x7684;&#x7B2C;&#x4E00;&#x4E2A;HTML&#x6587;&#x6863;"></a>

通过使用标签 `<em>` 和 `</em>` （在前面放置 `<em>` 打开元素，在后面放置 `</em>` 关闭元素）——这使得行内容变成斜体强调！您可以在“输出”区域中实时查看更改更新。

如果您犯了错误，您总是可以使用重置按钮重置。如果你真的卡住了，按显示解决方案按钮看到答案。

在 CodePen 中打开在 JSFiddle 中打开

#### 嵌套元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%B5%8C%E5%A5%97%E5%85%83%E7%B4%A0) <a id="&#x5D4C;&#x5957;&#x5143;&#x7D20;"></a>

你也可以把元素放到其它元素之中——这被称作嵌套。如果我们想要表明我们的小猫脾气很暴躁，可以将very嵌套在[`<strong>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong) 中，意味着这个单词被着重强调:

```text
<p>My cat is <strong>very</strong> grumpy.</p>
```

你需要确保元素被正确的嵌套：在上面的例子中我们先打开[`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p)元素，然后才打开[`<strong>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong)元素，因此必须先将[`<strong>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong)元素关闭，然后再去关闭[`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p)元素。下面的例子是错误的：

```text
<p>My cat is <strong>very grumpy.</p></strong>
```

所有的元素都需要正确的打开和关闭，这样才能按你所想的方式展现。如果像上述的例子一样进行了错误的嵌套，那么浏览器会去猜测你想要表达的意思，但很有可能会得出错误的结果。所以永远不要这么做！

#### 块级元素和内联元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%9D%97%E7%BA%A7%E5%85%83%E7%B4%A0%E5%92%8C%E5%86%85%E8%81%94%E5%85%83%E7%B4%A0) <a id="&#x5757;&#x7EA7;&#x5143;&#x7D20;&#x548C;&#x5185;&#x8054;&#x5143;&#x7D20;"></a>

在HTML中有两种你需要知道的重要元素类别，块级元素和内联元素。

* 块级元素在页面中以块的形式展现 —— 相对与其前面的内容它会出现在新的一行，其后的内容也会被挤到下一行展现。块级元素通常用于展示页面上结构化的内容，例如段落、列表、导航菜单、页脚等等。一个以block形式展现的块级元素不会被嵌套进内联元素中，但可以嵌套在其它块级元素中。
* 内联元素通常出现在块级元素中并包裹文档内容的一小部分，而不是一整个段落或者一组内容。内联元素不会导致文本换行：它通常出现在一堆文字之间例如超链接元素[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)或者强调元素[`<em>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/em)和 [`<strong>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong)。

看一看下面的例子：

```text
<em>first</em><em>second</em><em>third</em>

<p>fourth</p><p>fifth</p><p>sixth</p>
```

[`<em>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/em) 是一个内联元素，所以就像你在下方可以看到的，第一行代码中的三个元素都没有间隙的展示在了同一行。而[`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p)是一个块级元素，所以第二行代码中的每个元素分别都另起了新的一行展现，并且每个段落间都有一些间隔（这是因为默认的浏览器有着默认的展示[`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p)元素的 [CSS styling](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS) ）。

在 CodePen 中打开在 JSFiddle 中打开

**提示**: HTML5重新定义了元素的类别：见 [元素内容分类](http://www.whatwg.org/specs/web-apps/current-work/complete/section-index.html#element-content-categories)（链接已失效）。尽管这些新的定义更精确，但却比上述的 “块级元素” 和 “内联元素” 更难理解，因此在之后的讨论中仍使用旧的定义。

#### 空元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E7%A9%BA%E5%85%83%E7%B4%A0) <a id="&#x7A7A;&#x5143;&#x7D20;"></a>

不是所有元素都拥有开始标签，内容和结束标记. 一些元素只有一个标签，通常用来在此元素所在位置插入/嵌入一些东西 。例如：元素[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)是用来在元素[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)所在位置插入一张指定的图片。例子如下：

```text
<img src="https://raw.githubusercontent.com/mdn/beginner-html-site/gh-pages/images/firefox-icon.png">
```

显示如下：

在 CodePen 中打开在 JSFiddle 中打开

**提示**: Empty elements 有时也被叫作 _void elements_.

### 属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%B1%9E%E6%80%A7) <a id="&#x5C5E;&#x6027;"></a>

元素也可以拥有属性，如下：

![&amp;lt;p class=&quot;editor-note&quot;&amp;gt;My cat is very grumpy&amp;lt;/p&amp;gt;](https://mdn.mozillademos.org/files/9345/grumpy-cat-attribute-small.png)

属性包含元素的额外信息，这些信息不会出现在实际的内容中。在上述例子中，这个class属性给元素赋了一个识别的名字（id），这个名字此后可以被用来识别此元素的样式信息和其他信息。

一个属性必须包含如下内容：

1. 在元素和属性之间有个空格space \(如果有一个或多个已存在的属性，就与前一个属性之间有一个空格.\)
2. 属性后面紧跟着一个“=”符号.
3. 有一个属性值,由一对引号“ ”引起来.

#### 学习实践：为一个元素添加属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%AD%A6%E4%B9%A0%E5%AE%9E%E8%B7%B5%EF%BC%9A%E4%B8%BA%E4%B8%80%E4%B8%AA%E5%85%83%E7%B4%A0%E6%B7%BB%E5%8A%A0%E5%B1%9E%E6%80%A7) <a id="&#x5B66;&#x4E60;&#x5B9E;&#x8DF5;&#xFF1A;&#x4E3A;&#x4E00;&#x4E2A;&#x5143;&#x7D20;&#x6DFB;&#x52A0;&#x5C5E;&#x6027;"></a>

另一个例子是关于元素[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)的——元素[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)是锚，它使被标签包裹的内容成为一个超链接。此元素也可以添加大量的属性，其中几个如下：

* `href`: 这个属性声明超链接的web地址，当这个链接被点击浏览器会跳转至href声明的web地址。例如： `href="https://www.mozilla.org/"`。
* `title`: 标题`title` 属性为超链接声明额外的信息，比如你将链接至那个页面。例如： `title="The Mozilla homepage"`。当鼠标悬浮时，将出现一个工具提示。
* `target`: 目标`target` 属性指定将用于显示链接的浏览上下文。 例如， `target="_blank"` 将在新标签页中显示链接。如果你希望在目前标签页显示链接，只需忽略这个属性。 

在下面的文本框中内容，使之变成指向任一个你喜欢的web地址的链接。首先，添加&lt;a&gt;元素，然后为它添加href属性和title属性。你可以适时地在输出区域看到你改变的内容。你应该可以看到一个连接，当鼠标移上此链接时会显示title属性值，当点击此链接时会跳转到href指定的web地址。记住：在元素名和属性名之间以及两个属性之间要有一个空格space。

当你出错时，你可以用_Reset_ 按钮修改它。当你真正完成这个任务时，点击_Show solution_ 按钮观看答案。

在 CodePen 中打开在 JSFiddle 中打开

#### 布尔属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%B8%83%E5%B0%94%E5%B1%9E%E6%80%A7) <a id="&#x5E03;&#x5C14;&#x5C5E;&#x6027;"></a>

有时你会看到没有值的属性，它是合法的。这些属性被称为布尔属性，他们只能有跟它的属性名一样的属性值。例如 [`disabled`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-disabled) 属性，他们可以标记表单输入使之变为不可用\(变灰色\)，此时用户不能向他们输入任何数据。

```text
<input type="text" disabled="disabled">
```

采用如下简写更佳\(下面一句为可用可输入数据的文本框，以作为对比\)：

```text
<input type="text" disabled>

<input type="text">
```

上面两个文本框显示如下：

在 CodePen 中打开在 JSFiddle 中打开

#### 省略包围属性值的引号[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E7%9C%81%E7%95%A5%E5%8C%85%E5%9B%B4%E5%B1%9E%E6%80%A7%E5%80%BC%E7%9A%84%E5%BC%95%E5%8F%B7) <a id="&#x7701;&#x7565;&#x5305;&#x56F4;&#x5C5E;&#x6027;&#x503C;&#x7684;&#x5F15;&#x53F7;"></a>

当你浏览那些粗糙的web网站，你将会看见各种各样奇怪的标记风格，其中就有不给属性值添加引号。在某些情况下它是被允许的，但是其他情况下会破坏你的标记。例如，我们可以写一个只拥有一个href属性的链接，如下：

```text
<a href=https://www.mozilla.org/>favorite website</a>
```

然而，当我们再添加一个title属性时就会出错，如下：

```text
<a href=https://www.mozilla.org/ title=The Mozilla homepage>favorite website</a>
```

此时浏览器会误解你的标记，它会把title属性理解为三个属性——title的属性值为"The“，另外还有两个布尔属性“`Mozilla`”和“`homepage`”。看下面的例子，它明显不是我们所期望的，并且在这个编码里面它会报错或者出现异常行为。试一试把鼠标移动到连接上，看会显示什么title属性值!

在 CodePen 中打开在 JSFiddle 中打开

我们建议始终添加引号——这样可以避免很多问题，并且使代码更易读。

#### 单引号或者双引号？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%8D%95%E5%BC%95%E5%8F%B7%E6%88%96%E8%80%85%E5%8F%8C%E5%BC%95%E5%8F%B7%EF%BC%9F) <a id="&#x5355;&#x5F15;&#x53F7;&#x6216;&#x8005;&#x53CC;&#x5F15;&#x53F7;&#xFF1F;"></a>

在目前为止，本章内容所有的属性都是由双引号来包裹。也许在一些HTML中，你以前也见过单引号。这只是风格的问题，你可以从中选择一个你喜欢的。以下两种情况都可以：

```text
<a href="http://www.example.com">A link to my example.</a>

<a href='http://www.example.com'>A link to my example.</a>
```

但你应该注意单引号和双引号不能再一个属性值里面混用。下面的语法是错误的：

```text
<a href="http://www.example.com'>A link to my example.</a>
```

在一个HTML中已使用一种引号，你可以在此引号中嵌套另外一种引号：

```text
<a href="http://www.example.com" title="Isn't this fun?">A link to my example.</a>
```

如果你想将引号当作文本显示在html中，你就必须使用 [实体引用](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%AE%9E%E4%BD%93%E5%BC%95%E7%94%A8%EF%BC%9A_%E5%9C%A8HTML%E4%B8%AD%E5%8C%85%E5%90%AB%E7%89%B9%E6%AE%8A%E5%AD%97%E7%AC%A6) 。

### 分析HTML文档[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%88%86%E6%9E%90HTML%E6%96%87%E6%A1%A3) <a id="&#x5206;&#x6790;HTML&#x6587;&#x6863;"></a>

学习了一些HTML元素的基础知识，这些元素单独一个是没有意义的。现在我们来学习这些特定元素是怎么被结合起来，从而形成一个完整的HTML页面的：

```text
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```

分析如下:

1. `<!DOCTYPE html>`: 声明文档类型. 很久以前，早期的HTML\(大约1991年2月\)，文档类型声明类似于链接，规定了HTML页面必须遵从的良好规则，能自动检测错误和其他有用的东西。使用如下：

   ```text
   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
   "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
   ```

   然而现在没有人再这样写，需要保证每一个东西都正常工作已成为历史。你只需要知道`<!DOCTYPE html>是最短的有效的文档声明。`

2. `<html></html>`: `<html>`元素。这个元素包裹了整个完整的页面，是一个根元素。
3. `<head></head>`: `<head>元素`. 这个元素是一个容器，它包含了所有你想包含在HTML页面中但不想在HTML页面中显示的内容。这些内容包括你想在搜索结果中出现的关键字和页面描述，CSS样式，字符集声明等等。以后的章节能学到更多关于&lt;head&gt;元素的内容。
4. `<meta charset="utf-8">`: 这个元素设置文档使用utf-8字符集编码，utf-8字符集包含了人类大部分的文字。基本上他能识别你放上去的所有文本内容。毫无疑问要使用它，并且它能在以后避免很多其他问题。
5. `<title></title>`: 设置页面标题，出现在浏览器标签上，当你标记/收藏页面时它可用来描述页面。
6. `<body></body>`: `<body>`元素。 包含了你访问页面时所有显示在页面上的内容，文本，图片，音频，游戏等等。

#### 学习实践：为HTML文档添加一些特征[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%AD%A6%E4%B9%A0%E5%AE%9E%E8%B7%B5%EF%BC%9A%E4%B8%BAHTML%E6%96%87%E6%A1%A3%E6%B7%BB%E5%8A%A0%E4%B8%80%E4%BA%9B%E7%89%B9%E5%BE%81) <a id="&#x5B66;&#x4E60;&#x5B9E;&#x8DF5;&#xFF1A;&#x4E3A;HTML&#x6587;&#x6863;&#x6DFB;&#x52A0;&#x4E00;&#x4E9B;&#x7279;&#x5F81;"></a>

如果你想在你的本地练习写一些HTML页面，你可以这样做：

1. 复制上面的HTML页面例子。
2. 在编辑器创建一个新文件。
3. 粘贴代码到这个文件。
4. 保存为`index.html`.

**提示：**你也可以在[MDN Learning Area Github repo](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/getting-started/index.html)上找到这些基础的HTML示例

你可以打开浏览器看看这段代码的效果是什么样的，然后改变代码刷新浏览器看看新的结果。 最开始的代码是这样的效果：

![A simple HTML page that says This is my page](https://mdn.mozillademos.org/files/12279/template-screenshot.png)所以在这段练习中, 你可以用你的电脑在本地编写运行代码，如上所述, 你也可以在下面的简单可编辑窗口编辑它 \(此时这个简单的可编辑窗口仅显示&lt;body&gt;标签内的内容.\) 我们希望您能够实践以下步骤：

* 就在 [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 元素开始标签下方, 为这个文档添加一个主标题。这个主标题应该被包含在 `<h1>` 开始标签和 `</h1>`结束标签之间。
* 编辑这个段落以包含一些你感兴趣的文本。
* 把字词包含在开始标记 `<strong>`和结束标记 `</strong>` 之间可以使他们以粗体显示，从而突出任何重要的字词。
* 在你的文档中添加一个超文本链接，就像[explained earlier in the article](https://developer.mozilla.org/en-US/Learn/HTML/Introduction_to_HTML/Getting_started#Active_learning_Adding_attributes_to_an_element)。
* 在段落下方向你的文档添加一张图片，就像 [explained earlier in the article](https://developer.mozilla.org/en-US/Learn/HTML/Introduction_to_HTML/Getting_started#Empty_elements)。如果你尝试对不同的图片\(在你的本地电脑或是在Web的其他位置上\)添加链接，那你就更棒了。

当你出错时，你可以用 Reset 按钮修改它。当你真正完成这个任务时，点击 Show solution 按钮观看答案。

在 CodePen 中打开在 JSFiddle 中打开

#### HTML中的空白[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#HTML%E4%B8%AD%E7%9A%84%E7%A9%BA%E7%99%BD) <a id="HTML&#x4E2D;&#x7684;&#x7A7A;&#x767D;"></a>

在上面的例子中，你可能已经注意到了在代码中包含了很多的空格——这是没有必要的；下面的两个代码片段是等价的：

```text
<p>Dogs are silly.</p>

<p>Dogs        are
         silly.</p>
```

无论你用了多少空白\(包括空白字符，包括换行\), 当渲染这些代码的时候，HTML解释器会将连续出现的空白字符减少为一个单独的空格符。那么为什么我们会使用那么多的空白呢? 答案就是为了可读性 —— 如果你的代码被很好地进行格式化，那么就很容易理解你的代码是怎么回事, 反之就只有聚做一团的混乱. 在我们的HTML代码中，我们让每一个嵌套的元素以两个空格缩进。 你使用什么风格来格式化你的代码取决于你 \(比如所对于每层缩进使用多少个空格\),但是你应该坚持使用某种风格。

### 实体引用： 在HTML中包含特殊字符[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E5%AE%9E%E4%BD%93%E5%BC%95%E7%94%A8%EF%BC%9A_%E5%9C%A8HTML%E4%B8%AD%E5%8C%85%E5%90%AB%E7%89%B9%E6%AE%8A%E5%AD%97%E7%AC%A6) <a id="&#x5B9E;&#x4F53;&#x5F15;&#x7528;&#xFF1A;_&#x5728;HTML&#x4E2D;&#x5305;&#x542B;&#x7279;&#x6B8A;&#x5B57;&#x7B26;"></a>

在HTML中，字符 `<`, `>`,`"`,`'` 和 `&` 是特殊字符. 它们是HTML语法自身的一部分, 那么你如何将这些字符包含进你的文本中呢, 比如说如果你真的想要在文本中使用符号&或者小于号, 而不想让它们被浏览器视为代码并被解释?

我们必须使用字符引用 —— 表示字符的特殊编码, 它们可以在那些情况下使用. 每个字符引用以符号&开始, 以分号\(;\)结束.

| 原义字符 | 等价字符引用 |
| :--- | :--- |
| &lt; | &lt; |
| &gt; | &gt; |
| " | &quot; |
| ' | &apos; |
| & | &amp; |

在下面的例子中你可以看到两个段落，它们在谈论web技术:

```text
<p>In HTML, you define a paragraph using the <p> element.</p>

<p>In HTML, you define a paragraph using the &lt;p&gt; element.</p>
```

在下面的实时输出中，你会看到第一段是错误的，因为浏览器会认为第二个&lt;p&gt;是开始一个新的段落！  第二段是正确的，因为我们用字符引用来代替了角括号（'&lt;'和'&gt;'符号）.

在 CodePen 中打开在 JSFiddle 中打开

**提示**: 维基百科上有一个包含所有可用HTML字符实体引用的列表：[XML和HTML字符实体引用列表](http://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references)。

### HTML注释[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#HTML%E6%B3%A8%E9%87%8A) <a id="HTML&#x6CE8;&#x91CA;"></a>

如同大部分的编程语言一样，在HTML中有一种可用的机制来在代码中书写注释 —— 注释是被浏览器忽略的，而且是对用户不可见的，它们的目的是允许你描述你的代码是如何工作的和不同部分的代码做了什么等等。 如果你在半年后重新返回你的代码库，而且不能记起你所做的事情 —— 或者当你处理别人的代码的时候， 那么注释是很有用的.

为了将一段HTML中的内容置为注释，你需要将其用特殊的记号&lt;!--和--&gt;包括起来， 比如：

```text
<p>I'm not inside a comment</p>

<!-- <p>I am!</p> -->
```

正如你下面所见的那样，第一段出现在了实时输出中，但是第二段却没有。

在 CodePen 中打开在 JSFiddle 中打开

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

你已经来到了这篇文章的结尾 —— 希望你享受你的基础的HTML学习的旅程。 在这里你应该可以理解HTML语言的全貌， 它在基础的级别是如何工作，而且可以使用一些元素和属性。 在这个模块的后续文章中，我们会深入一些你已经见过的东西的细节，并且介绍一些新的HTML的特性。未完待续！

**提示**: 现在，你将开始学习更多关于HTML的知识，你可能也想了解一些层叠样式列表（[CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS)）的基础知识。CSS是一种用来设计网页样式的语言（比如，用它改变字体、颜色或页面布局等）。你很快就会发现，HTML和CSS能很好地协调配合。

