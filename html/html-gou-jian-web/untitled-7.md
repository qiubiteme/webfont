# &lt;head&gt;标签里有什么? Metadata-HTML中的元数据

在页面加载完成的时候，标签[head](https://developer.mozilla.org/en-US/docs/Glossary/Head)里的内容，是不会在页面中显示出来的。它包含了像页面的 [`<title>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/title)\(标题\) ,[CSS](https://developer.mozilla.org/en-US/docs/Glossary/CSS)\(如果你选择用 CSS 来为 HTML 内容添加样式\)，指向自定义图标的链接和其他的元数据\(比如 作者，和描述文档的关键词\)。在本文中，我们将包含所有上述的事情，为您在脑海中营造一个很好的基础和代码印象。

| 先决条件: | 熟悉HTML,可以去 [Getting started with HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started).了解 |
| :--- | :--- |
| 目的: | 学习head标签，它的目的是什么，包含哪些元素以及它对页面有什么影响 |

### 什么是Head标签?[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E4%BB%80%E4%B9%88%E6%98%AFHead%E6%A0%87%E7%AD%BE) <a id="&#x4EC0;&#x4E48;&#x662F;Head&#x6807;&#x7B7E;"></a>

让我们简单的回顾下上一章提到的HTML

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

head 标签是 [`<head>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/head) 元素的内容。不像 [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 元素的内容可以显示在浏览器中，head 的内容不会在浏览器中显示，它的作用是包含一些页面的 [元数据](https://developer.mozilla.org/en-US/docs/Glossary/Metadata)。在下面的例子中，head 的内容很少。

```text
<head>
  <meta charset="utf-8">
  <title>My test page</title>
</head>
```

当然，在大型的页面中，head 会包含很多的元数据。你可以用 [developer tools](https://developer.mozilla.org/en-US/docs/Learn/Discover_browser_developer_tools) 去查看你喜欢的网页的 head 的内容。 在这里，我们不打算将所有能够包含在 head 里的内容都告诉你，而是会告诉你如何使用你将要包含在 head 里的主要元素，并给你一些相似的例子。让我们开始吧。

### 增加一个标题[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%A2%9E%E5%8A%A0%E4%B8%80%E4%B8%AA%E6%A0%87%E9%A2%98) <a id="&#x589E;&#x52A0;&#x4E00;&#x4E2A;&#x6807;&#x9898;"></a>

我们之前已经看到了  [`<title>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/title)，它可以用来给 html 文档添加一个标题。你可能会将它和给 body 添加标题的 [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1) 元素混淆，有些时候 h1 也会被称作网页标题。但是它们是不同的。

* 当被加载到浏览器中的时候，元素 [`<h1>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/h1)  会出现在页面中 —— 通常它应该在一个页面中只被使用一次, 它被用来标记你的页面内容的标题\(故事的标题，新闻标题或者任何适当的方式）
* 元素  [`<title>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/title) 是用来表示整个HTML文档大致内容的元数据\(不是文档的内容.\)

#### 交互式学习：检查一个简单的例子[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E4%BA%A4%E4%BA%92%E5%BC%8F%E5%AD%A6%E4%B9%A0%EF%BC%9A%E6%A3%80%E6%9F%A5%E4%B8%80%E4%B8%AA%E7%AE%80%E5%8D%95%E7%9A%84%E4%BE%8B%E5%AD%90) <a id="&#x4EA4;&#x4E92;&#x5F0F;&#x5B66;&#x4E60;&#xFF1A;&#x68C0;&#x67E5;&#x4E00;&#x4E2A;&#x7B80;&#x5355;&#x7684;&#x4F8B;&#x5B50;"></a>

1. 为了开始这个交互式学习，我们希望你到我们的Github库中下载一份我们的 [title-example.html page](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/the-html-head/title-example.html). 要做到这一点, 你可以
   1. 使用你的代码编辑器，从页面中拷贝粘贴代码到一个新的文本文件中，然后将其保存到一个适当的地方。
   2. 按下页面中的 "Raw" 按钮, 从浏览器的菜单中选择 _File &gt; Save Page As..._ , 然后选择一个地方来保存这个文件.
2. 在浏览器中打开文件，你会看到类似这样效果:

   ![A simple web page with the title set to &amp;lt;title&amp;gt; element, and the&amp;lt;h1&amp;gt; set to&amp;lt;h1&amp;gt; element.](https://mdn.mozillademos.org/files/12323/title-example.png)现在很明显的可以看到 `<h1>` 出现的地方, 和  `<title>` 出现的地方!

3. 你应该尝试着在你的代码编辑器中打开这些代码，编辑这些元素的内容，然后在你的浏览器中刷新页面。祝你玩得开心。

元素 `<title>` 也被以其他的方式使用着. 比如说，如果你尝试为某个页面添加书签，\(_Bookmarks &gt; Bookmark This Page_, 在火狐浏览器中\), 你会看到 `<title>` 的内容被作为建议的书签名.

![A webpage being bookmarked in firefox; the bookmark name has been automatically filled in with the contents of the &amp;lt;title&amp;gt; element ](https://mdn.mozillademos.org/files/12337/bookmark-example.png)

元素 `<title>` 的内容也被用在搜索的结果中，正如你下面看到的那样。

### 元数据：&lt;meta&gt;元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%85%83%E6%95%B0%E6%8D%AE%EF%BC%9A%3Cmeta%3E%E5%85%83%E7%B4%A0) <a id="&#x5143;&#x6570;&#x636E;&#xFF1A;&lt;meta&gt;&#x5143;&#x7D20;"></a>

元数据就是描述数据的数据，而HTML有一个“官方的”方式来为一个文档添加元数据，——  [`<meta>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta) 元素. 当然，其他在这篇文章中提到的东西也可以被当作元数据。 有很多不同种类的 `<meta>` 元素可以被包含进你的页面的&lt;head&gt;元素, 但是现在我们还不会尝试去解释所有类型, 这只会引起混乱。 我们会解释一些你常会看到的类型，先让你有个概念。

#### 指定你的文档中字符的编码[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E6%8C%87%E5%AE%9A%E4%BD%A0%E7%9A%84%E6%96%87%E6%A1%A3%E4%B8%AD%E5%AD%97%E7%AC%A6%E7%9A%84%E7%BC%96%E7%A0%81) <a id="&#x6307;&#x5B9A;&#x4F60;&#x7684;&#x6587;&#x6863;&#x4E2D;&#x5B57;&#x7B26;&#x7684;&#x7F16;&#x7801;"></a>

在上面的例子中，这行是被包含的：

```text
<meta charset="utf-8">
```

这个元素简单的指定了文档的字符编码 —— 在这个文档中被允许使用的字符集。 `utf-8` 是一个通用的字符集，它包含了任何人类语言中的大部分的字符。 这意味着你的web页面可以显示任意的语言; 所以对于你的每一个页面，使用这个设置是很好的! 比如说，你的页面可以很好的处理英语和日语:

![a web page containing English and Japanese characters, with the character encoding set to universal, or utf-8. Both languages display fine,](https://mdn.mozillademos.org/files/12343/correct-encoding.png)比如说，如果你将你的字符集设置为 `ISO-8859-1` \(拉丁字母的字符集\), 那么你的页面会是乱码的:

![a web page containing English and Japanese characters, with the character encoding set to latin. The Japanese characters don&apos;t display correctly](https://mdn.mozillademos.org/files/12341/bad-encoding.png)

#### 交互式学习： 体验字符集[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E4%BA%A4%E4%BA%92%E5%BC%8F%E5%AD%A6%E4%B9%A0%EF%BC%9A_%E4%BD%93%E9%AA%8C%E5%AD%97%E7%AC%A6%E9%9B%86) <a id="&#x4EA4;&#x4E92;&#x5F0F;&#x5B66;&#x4E60;&#xFF1A;_&#x4F53;&#x9A8C;&#x5B57;&#x7B26;&#x96C6;"></a>

为了进行这个练习，回到你在前面&lt;title&gt;章节中获取的HTML模板 \( [title-example.html page](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/the-html-head/title-example.html)\), 试着改变其字符集的值为`ISO-8859-1`, 然后将日语添加到页面中. 这就是我们使用的代码:

```text
<p>Japanese example: ご飯が熱い。</p>
```

#### 添加作者和描述[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E6%B7%BB%E5%8A%A0%E4%BD%9C%E8%80%85%E5%92%8C%E6%8F%8F%E8%BF%B0) <a id="&#x6DFB;&#x52A0;&#x4F5C;&#x8005;&#x548C;&#x63CF;&#x8FF0;"></a>

许多`<meta>` 元素包含了`name` 和 `content` 特性:

* `name` 特性指定了meta 元素的类型; 说明该元素包含了什么类型的信息。
* `content` 指定了实际的元数据内容。

这两个meta 元素对于定义你的页面的作者和提供页面的内容描述是很有用的 。 让我们看一个例子：

```text
<meta name="author" content="Chris Mills">
<meta name="description" content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications.">
```

指定作者在某些情况下是很有用的：如果你需要联系页面的作者，问一些关于页面内容的问题。 一些内容管理系统能够自动获取页面作者的信息，然后用于某种目的。

指定包含关于页面内容的关键字的页面内容的描述是很有用的，因为它可能或让你的页面在搜索引擎的相关的搜索出现得更多 \(这些行为术语上被称为 [Search](https://developer.mozilla.org/en-US/docs/Glossary/SEO)[ Engine Optimization](https://developer.mozilla.org/en-US/docs/Glossary/SEO), or [SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO).\)

#### 实践操作: 在搜索引擎中description的使用[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%AE%9E%E8%B7%B5%E6%93%8D%E4%BD%9C_%E5%9C%A8%E6%90%9C%E7%B4%A2%E5%BC%95%E6%93%8E%E4%B8%ADdescription%E7%9A%84%E4%BD%BF%E7%94%A8) <a id="&#x5B9E;&#x8DF5;&#x64CD;&#x4F5C;_&#x5728;&#x641C;&#x7D22;&#x5F15;&#x64CE;&#x4E2D;description&#x7684;&#x4F7F;&#x7528;"></a>

description也被使用在搜索引擎显示的结果页中。 下面通过一个例子来说明

1. 到[front page of The Mozilla Developer Network](https://developer.mozilla.org/en-US/).
2. 查看网页源代码\(_通过鼠标右键点击网页在弹出的菜单中选择\[查看网页源代码\]_\)
3. 找到description的meta标签. 就和如下展示的这样:

   ```text
   <meta name="description" content="The Mozilla Developer Network (MDN) provides
   information about Open Web technologies including HTML, CSS, and APIs for both
   Web sites and HTML5 Apps. It also documents Mozilla products, like Firefox OS.">
   ```

4. 现在，在你喜欢的搜索引擎里搜索”Mozilla Developer Network“ \(下图展示的是在雅虎搜索里的情况.\) 。你会看到description `<meta>` and `<title>` 元素如何在搜索结果里显示— 很值得这样做哦！

![](https://mdn.mozillademos.org/files/15780/Screen%20Shot%202018-01-24%20at%2017.35.04.png)

**Note**:在谷歌搜索里，在主页面链接下面，你将看到一些相关子页面 — 这些是站点链接,可以在 [Google's webmaster tools](http://www.google.com/webmasters/tools/) 配置— 一种可以使你你的的站点对搜索引擎更友好的方式。

**Note**: 许多 `<meta>` 特性已经不再使用. 例如, keyword `<meta>` 元素— 提供关键词给搜索引擎，根据不同的搜索词，查找到相关的网站 — 被搜索引擎忽略了， 因为作弊者填充了大量关键词到keyword, 错误地引导搜索结果。

#### 其他类型的 metadata[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%85%B6%E4%BB%96%E7%B1%BB%E5%9E%8B%E7%9A%84_metadata) <a id="&#x5176;&#x4ED6;&#x7C7B;&#x578B;&#x7684;_metadata"></a>

当你在网站上查看源码时，你也会发现其他类型的元数据。你在网站上看到的许多功能都是专有创作，旨在向某些网站\(如社交网站\)提供可使用的特定信息。

例如，Facebook 编写的元数据协议 [Open Graph Data](http://ogp.me/) 为网站提供了更丰富的元数据。在 MDN 源代码中，你会发现：

```text
<meta property="og:image" content="https://developer.cdn.mozilla.net/static/img/opengraph-logo.dc4e08e2f6af.png">
<meta property="og:description" content="The Mozilla Developer Network (MDN) provides
information about Open Web technologies including HTML, CSS, and APIs for both Web sites
and HTML5 Apps. It also documents Mozilla products, like Firefox OS.">
<meta property="og:title" content="Mozilla Developer Network">
```

上面代码展现的一个效果就是，当你在 Facebook 上链接到 MDN 时，该链接将显示一个图像和描述：这为用户提供更丰富的体验。

![Open graph protocol data from the MDN homepage as displayed on facebook, showing an image, title, and description.](https://mdn.mozillademos.org/files/12349/facebook-output.png)Twitter 还拥有自己的类型的专有元数据协议，当网站的 URL 显示在 twitter.com 上时，它具有相似的效果。例如下面：

```text
<meta name="twitter:title" content="Mozilla Developer Network">
```

### 在你的站点增加自定义图标[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%9C%A8%E4%BD%A0%E7%9A%84%E7%AB%99%E7%82%B9%E5%A2%9E%E5%8A%A0%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9B%BE%E6%A0%87) <a id="&#x5728;&#x4F60;&#x7684;&#x7AD9;&#x70B9;&#x589E;&#x52A0;&#x81EA;&#x5B9A;&#x4E49;&#x56FE;&#x6807;"></a>

为了进一步丰富你的网站设计，你可以在元数据中添加对自定义图标的引用，这些将在特定的场合中显示。

这个不起眼的图标已经存在很多很多年了，16 x 16 像素是这种图标的第一种类型。你可以看见这些图标出现在浏览器每一个打开的页面中的标签页中中以及在书签面板中的书签页面中。

页面添加图标的方式有：

1. 将其保存在与网站的索引页面相同的目录中，以.ico格式保存（大多数浏览器将支持更通用的格式，如.gif或.png，但使用ICO格式将确保它能在如Internet Explorer 6一样久远的浏览器显示）
2. 将以下行添加到HTML &lt;head&gt;中以引用它：

   ```text
   <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
   ```

现代浏览器在各种场合使用favicons，如打开的页面标签页和书签面板中的书签页面。下面是一个favicon 出现在书签面板中的例子：![The Firefox bookmarks panel, showing a bookmarked example with a favicon displayed next to it.](https://mdn.mozillademos.org/files/12351/bookmark-favicon.png)

如今还有很多其他的图标类型可以考虑。 例如，你可以在 MDN 主页的源代码中找到它：

```text
<!-- third-generation iPad with high-resolution Retina display: -->
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="https://developer.cdn.mozilla.net/static/img/favicon144.a6e4162070f4.png">
<!-- iPhone with high-resolution Retina display: -->
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="https://developer.cdn.mozilla.net/static/img/favicon114.0e9fabd44f85.png">
<!-- first- and second-generation iPad: -->
<link rel="apple-touch-icon-precomposed" sizes="72x72" href="https://developer.cdn.mozilla.net/static/img/favicon72.8ff9d87c82a0.png">
<!-- non-Retina iPhone, iPod Touch, and Android 2.1+ devices: -->
<link rel="apple-touch-icon-precomposed" href="https://developer.cdn.mozilla.net/static/img/favicon57.a2490b9a2d76.png">
<!-- basic favicon -->
<link rel="shortcut icon" href="https://developer.cdn.mozilla.net/static/img/favicon32.e02854fdcf73.png">
```

这些注释解释了每个图标的用途 - 这些元素涵盖的东西提供一个高分辨率图标，这些高分辨率图标当网站保存到iPad的主屏幕时使用。

不用担心现在实现所有这些类型的图标 - 这是一个相当先进的功能，你将不会被要求在这个课堂上学习这个知识点。 这里的主要目的是让你提前了解有这一样东西以防当你浏览其他网站的源代码时不理解源代码的含义。

### 在HTML中应用CSS和JavaScript[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%9C%A8HTML%E4%B8%AD%E5%BA%94%E7%94%A8CSS%E5%92%8CJavaScript) <a id="&#x5728;HTML&#x4E2D;&#x5E94;&#x7528;CSS&#x548C;JavaScript"></a>

如今，几乎你使用的所有网站都会使用 [CSS](https://developer.mozilla.org/en-US/docs/Glossary/CSS) 让网页更加炫酷, 使用[JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript)让网页有交互功能, 比如视频播放器，地图，游戏以及更多功能。这些应用在网页中很常见，它们分别使用 [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link)元素以及 [`<script>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/script) 元素。

*  [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link) 元素经常位于文档的头部，它有2个属性， rel="stylesheet"，表明这是文档的样式表，而 href,包含了样式表文件的路径：

  ```text
  <link rel="stylesheet" href="my-css-file.css">
  ```

* [`<script>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/script) 部分没必要非要放在文档头部; 实际上，把它放在文档的尾部（在 `</body>标签之前`）是一个更好的选择 ，这样可以确保在加载脚本之前浏览器已经解析了HTML内容（如果脚本加载某个不存在的元素，浏览器会报错）。

  ```text
  <script src="my-js-file.js"></script>
  ```

  **注意：** &lt; script &gt;元素看起来像一个空元素，但它并不是，因此需要一个结束标记。您还可以选择将脚本放入&lt; script &gt;元素中，而不是指向外部脚本文件。

#### 实践操作: 在网页中应用CSS和JavaScript[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%AE%9E%E8%B7%B5%E6%93%8D%E4%BD%9C_%E5%9C%A8%E7%BD%91%E9%A1%B5%E4%B8%AD%E5%BA%94%E7%94%A8CSS%E5%92%8CJavaScript) <a id="&#x5B9E;&#x8DF5;&#x64CD;&#x4F5C;_&#x5728;&#x7F51;&#x9875;&#x4E2D;&#x5E94;&#x7528;CSS&#x548C;JavaScript"></a>

1. 开始操作之前， 先拷贝我们的 [meta-example.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/the-html-head/meta-example.html), [script.js](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/the-html-head/script.js) 和 [style.css](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/the-html-head/style.css) 文件，并把它们保存到本地电脑的同一目录下，确保使用了正确的文件名和文件格式。
2. 使用浏览器和文字编辑器同时打开你的HTML文件。
3. 根据上面的信息，添加 [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link)和 [`<script>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/script)部分到您的HTML文件中, 这样你的HTML就可以应用CSS和JavaScript了。

如果按照上述步骤正确地执行, 当你保存HTML文件并重新刷新浏览器的话，你会发现页面已经变样了：

![Example showing a page with CSS and JavaScript applied to it. The CSS has made the page go green, whereas the JavaScript has added a dynamic list to the page.](https://mdn.mozillademos.org/files/12359/js-and-css.png)

* JavaScript在页面中添加了一个空列表。现在当你点击列表中的任何地方，浏览器会弹出一个对话框要求你为新列表项输入一些文本内容。 当你点击OK按钮，刚刚那个新的列表项会添加到页面上，当你点击那些已有的列表项，会弹出一个对话框允许你修改列表项的文本。
* CSS使页面背景变成了绿色，文本变得大了一点。它还将JavaScript添加到页面中的一些内容进行了样式化，（带有黑色边框的红色条是CSS添加到js生成的列表中的样式。）

**注意**：如果你卡在这个练习当中，无法正常应用CSS和JavaScript，试着查看一下我们的  [css-and-js.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/the-html-head/css-and-js.html) 页面实例。

### 为文档设定主语言[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E4%B8%BA%E6%96%87%E6%A1%A3%E8%AE%BE%E5%AE%9A%E4%B8%BB%E8%AF%AD%E8%A8%80) <a id="&#x4E3A;&#x6587;&#x6863;&#x8BBE;&#x5B9A;&#x4E3B;&#x8BED;&#x8A00;"></a>

最后，值得一提的是你可以（而且确实应该）为你的站点设定语言， 这个可以通过添加lang属性到HTML开始标签中来实现 \(参考 [meta-example.html](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/the-html-head/meta-example.html)\)，如下所示：

```text
<html lang="en-US">
```

这在很多方面都很有用。如果你的HTML文档的语言设置好了，那么你的HTML文档就会被搜索引擎更有效地索引 \(例如，允许它在特定于语言的结果中正确显示\),对于那些使用屏幕阅读器的视障人士也很有用\(比如, 法语和英语中都有“six”这个单词，但是发音却完全不同\)。

你还可以将文档的分段设置为不同的语言。例如， 我们可以把日语部分设置为日语， 如下所示：

```text
<p>Japanese example: <span lang="jp">ご飯が熱い。</span>.</p>
```

这些codes根据 [ISO 639-1](https://en.wikipedia.org/wiki/ISO_639-1) 标准定义的. 你可以在[Language tags in HTML and XML](https://www.w3.org/International/articles/language-tags/)找到更多相关的。

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

已经到了我们快速学习HTML head的尾声 — 你还能学到更多的相关的, 但是现阶段详尽的讲的太多会无聊且迷惑, 我们只希望你现在在这学到最基本的概念! 下一篇我们将要学习 HTML text 基础.

