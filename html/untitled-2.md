# 文档与网站架构



除了定义网页的各个部分（例如“段落”或“图片”）外，[HTML](https://developer.mozilla.org/en-US/docs/Glossary/HTML)还拥有一些用于定义网站区域的块级元素\(例如“头部”，“导航菜单”，“主要内容列”\)。本文将探讨如何规划基本的网站结构，并通过编写HTML来表示这种网站结构。

| 要求： | 熟悉基础的HTML，如[Getting started with HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started)所述；HTML文本格式，如[HTML text fundamentals](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals)所述。了解超链接如何工作，如[Creating hyperlinks](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)所述。 |
| :--- | :--- |
| 目标: | 了解如何使用语义标签来构建文档，以及如何制定简单网站的结构 |

### 文档的基本部分[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E6%96%87%E6%A1%A3%E7%9A%84%E5%9F%BA%E6%9C%AC%E9%83%A8%E5%88%86) <a id="&#x6587;&#x6863;&#x7684;&#x57FA;&#x672C;&#x90E8;&#x5206;"></a>

网页可以看起来彼此不同，但它们都倾向于使用类似的标准组件，除非页面显示全屏视频或游戏，或是某种艺术项目的一部分，或者是结构不当：标题通常在顶部有一个大标题和（或）图标。 这是一个网站的主要常见信息，通常存在于每一个网页。导航链接到网站的主要部分；通常由菜单按钮、链接或选项卡表示。与标题一样，这些内容通常在一个网页与另一个网页之间保持一致——在您的网站上导航不一致只会使人疑惑和恼火。许多网页设计师认为导航栏是标题的一部分，而不是独立的组件，但这并不是一个硬性规定；实际上有些人认为，两个独立的会有更好的[可访问性](https://developer.mozilla.org/zh-CN/docs/learn/Accessibility)，因为如果它们互相独立，屏幕阅读器可以更好地阅读两个功能。主要内容中心的一个大区域，包含给定网页的大部分独特内容，例如您要观看的视频，或您正在阅读的主要故事，或您要查看的地图，或新闻标题等......这是网站的一部分，绝对会因页面而异。侧栏一些次要信息、链接、引言、广告等。通常这是与主要内容中包含的内容相关（例如在新闻文章页面上，侧边栏可能包含作者的个人信息或相关文章的链接），但有在一些情况下，你会发现一些重复的元素，如辅助导航系统。页脚横跨页面底部的条纹，通常包含精美的打印、版权通知或联系信息。 它是一个放置公共信息（如标题）的地方，但通常该信息对网站来说不是特别重要。 通过提供用于快速访问热门内容的链接，页脚有时也用于[SEO](https://developer.mozilla.org/zh-CN/docs/Glossary/SEO)目的。

一个“典型的网站”可能会这样布局：

![a simple website structure example featuring a main heading, navigation menu, main content, side bar, and footer.](https://mdn.mozillademos.org/files/12417/sample-website.png)

### 用于结构化网站的HTML[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E7%94%A8%E4%BA%8E%E7%BB%93%E6%9E%84%E5%8C%96%E7%BD%91%E7%AB%99%E7%9A%84HTML) <a id="&#x7528;&#x4E8E;&#x7ED3;&#x6784;&#x5316;&#x7F51;&#x7AD9;&#x7684;HTML"></a>

上面显示的简单示例不是很漂亮，但是非常适合用于说明典型的网站布局。 一些网站有更多的列，有些网站更复杂，但你会有你的想法。使用正确的CSS，您可以使用几乎任何元素来装饰不同的部分，并得到您想要的结果，但如前所述，我们需要遵守语义，并**使用正确的元素进行语义化工作**。

这是因为视觉效果并不能说明一切。 我们可以对内容最有用的部分使用颜色和字体大小来吸引用户的关注，例如导航菜单和相关链接，但是视觉障碍的人该怎么办，这难道也对那些没有“粉红色”和“大”的概念的人来说非常有用吗？

**Note**: 色盲患者大概[占了世界人口的 8%](http://www.color-blindness.com/2006/04/28/colorblind-population/)，盲人和视障人士占世界人口的4-5％左右（2012年全球[有2.85亿人](https://en.wikipedia.org/wiki/Visual_impairment), 总人口[约70亿](https://en.wikipedia.org/wiki/World_human_population#/media/File:World_population_history.svg)）。

在您的HTML代码中，您可以根据其功能标记内容部分 - 您可以明确地使用表示上述内容部分的元素，屏幕阅读器等辅助技术可以识别这些元素，并帮助执行“找到主导航 “或”找到主要内容“。 正如我们前面提到的那样，[没有使用正确的元素结构和语义去构建网页会有很多的不良影响](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/HTML_text_fundamentals#%E4%B8%BA%E4%BB%80%E4%B9%88%E6%88%91%E4%BB%AC%E9%9C%80%E8%A6%81%E7%BB%93%E6%9E%84%E5%8C%96)。

为了实现这样的语义标记，HTML提供了可以用来表示这些部分的专用标签，例如：

* **标题:** [`<header>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/header).
* **导航栏:** [`<nav>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/nav).
* **主要内容:** [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main), 具有代表性的内容段落主题可以使用 [`<article>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/article), [`<section>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/section), 和  [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div) 元素.
* **侧栏:**  [`<aside>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/aside); 经常嵌套在 [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main) 中.
* **页脚:**  [`<footer>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/footer).

#### 自主学习: 探索例子的代码[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0_%E6%8E%A2%E7%B4%A2%E4%BE%8B%E5%AD%90%E7%9A%84%E4%BB%A3%E7%A0%81) <a id="&#x81EA;&#x4E3B;&#x5B66;&#x4E60;_&#x63A2;&#x7D22;&#x4F8B;&#x5B50;&#x7684;&#x4EE3;&#x7801;"></a>

我们上面所看到的例子用下面的代码表示（你也可以在[我们的GitHub repo](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/document_and_website_structure/index.html)上找到），我们希望你看看上面的例子，然后看看下面的列表，观察哪些部分组成上面所讨论的内容（标题、导航栏、主要内容、侧栏、页脚）。

```text
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">

    <title>My page title</title>
    <link href="https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300|Sonsie+One" rel="stylesheet" type="text/css">
    <link rel="stylesheet" href="style.css">

    <!-- the below three lines are a fix to get HTML5 semantic elements working in old versions of Internet Explorer-->
    <!--[if lt IE 9]>
      <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
    <![endif]-->
  </head>

  <body>
    <!-- Here is our main header that is used accross all the pages of our website -->

    <header>
      <h1>Header</h1>
    </header>

    <nav>
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Our team</a></li>
        <li><a href="#">Projects</a></li>
        <li><a href="#">Contact</a></li>
      </ul>

       <!-- A Search form is another commmon non-linear way to navigate through a website. -->

       <form>
         <input type="search" name="q" placeholder="Search query">
         <input type="submit" value="Go!">
       </form>
     </nav>

    <!-- Here is our page's main content -->
    <main>

      <!-- It contains an article -->
      <article>
        <h2>Article heading</h2>

        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Donec a diam lectus. Set sit amet ipsum mauris. Maecenas congue ligula as quam viverra nec consectetur ant hendrerit. Donec et mollis dolor. Praesent et diam eget libero egestas mattis sit amet vitae augue. Nam tincidunt congue enim, ut porta lorem lacinia consectetur.</p>

        <h3>subsection</h3>

        <p>Donec ut librero sed accu vehicula ultricies a non tortor. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aenean ut gravida lorem. Ut turpis felis, pulvinar a semper sed, adipiscing id dolor.</p>

        <p>Pelientesque auctor nisi id magna consequat sagittis. Curabitur dapibus, enim sit amet elit pharetra tincidunt feugiat nist imperdiet. Ut convallis libero in urna ultrices accumsan. Donec sed odio eros.</p>

        <h3>Another subsection</h3>

        <p>Donec viverra mi quis quam pulvinar at malesuada arcu rhoncus. Cum soclis natoque penatibus et manis dis parturient montes, nascetur ridiculus mus. In rutrum accumsan ultricies. Mauris vitae nisi at sem facilisis semper ac in est.</p>

        <p>Vivamus fermentum semper porta. Nunc diam velit, adipscing ut tristique vitae sagittis vel odio. Maecenas convallis ullamcorper ultricied. Curabitur ornare, ligula semper consectetur sagittis, nisi diam iaculis velit, is fringille sem nunc vet mi.</p>
      </article>

      <!-- the aside content can also be nested within the main content -->
      <aside>
        <h2>Related</h2>

        <ul>
          <li><a href="#">Oh I do like to be beside the seaside</a></li>
          <li><a href="#">Oh I do like to be beside the sea</a></li>
          <li><a href="#">Although in the North of England</a></li>
          <li><a href="#">It never stops raining</a></li>
          <li><a href="#">Oh well...</a></li>
        </ul>
      </aside>

    </main>

    <!-- And here is our main footer that is used across all the pages of our website -->

    <footer>
      <p>©Copyright 2050 by nobody. All rights reversed.</p>
    </footer>

  </body>
</html>
```

花一些时间来查看代码并理解它 - 代码中的注释也应该帮助您理解它。 我们不要求你在这篇文章中做很多其他事情，因为理解文档布局的关键是编写一个完整的HTML结构，然后用CSS布局。等你学习到 CSS 部分的时候才能完全理解上面代码。

### HTML布局元素细节[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#HTML%E5%B8%83%E5%B1%80%E5%85%83%E7%B4%A0%E7%BB%86%E8%8A%82) <a id="HTML&#x5E03;&#x5C40;&#x5143;&#x7D20;&#x7EC6;&#x8282;"></a>

从总体详细的理解HTML的元素是不错的——随着你web开发经验的逐渐积累，你将会逐渐理解HTML的元素。你可以通过查阅[HTML元素参考](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)找到更多的细节。现在，你需要理解这些主要的元素定义：

* [`<main>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/main) 展现了页面内容的独特性。只可以在每一个页面上使用一次&lt;main&gt;，直接把它放到[`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body)中。在理想情况下，不应该把它嵌套进其他的元素中。
* [`<article>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/article) 闭合一块与自身相关的内容，这块内容能够解释它自身而不是页面上其他的内容（例如一篇单独的博客）。
* [`<section>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/section) 近似于&lt;article&gt;，但是它更多的是伴随着由一个单独功能构成的页面（例如一个小型的地图，或者是一组文章的标题和摘要）。它被认为最好的实际应用是用[标题](https://developer.mozilla.org/en-US/Learn/HTML/Howto/Set_up_a_proper_title_hierarchy)作为每一部分（section）的开头；也要注意的是你可以把不同的&lt;article&gt;分到不同的&lt;section&gt;中，或者把不同的&lt;section&gt;分到不同的&lt;article&gt;中，这要取决于内容。
*  [`<aside>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/aside) 包含的内容并不与主要内容有直接的联系，但是它可以提供额外的不直接有联系的信息（术语表条目，作者简介，相关链接等等）。
* [`<header>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/header) 展现了一系列的介绍性内容。如果它是[`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 的子元素,它就定义了网站的全局页眉。但是如果它是 [`<article>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/article) 或[`<section>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/section) 的子元素，它就定义了这些部分的特定的页眉\(不要把这些与[titles and headings](https://developer.mozilla.org/en-US/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#Adding_a_title)混淆\)。
* [`<nav>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/nav) 包含了页面主要的导航功能。二级链接等，不会进入导航功能部分。
*  [`<footer>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/footer) 包含了页面的页脚部分。

#### 没有特定语义的装饰元素[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E6%B2%A1%E6%9C%89%E7%89%B9%E5%AE%9A%E8%AF%AD%E4%B9%89%E7%9A%84%E8%A3%85%E9%A5%B0%E5%85%83%E7%B4%A0) <a id="&#x6CA1;&#x6709;&#x7279;&#x5B9A;&#x8BED;&#x4E49;&#x7684;&#x88C5;&#x9970;&#x5143;&#x7D20;"></a>

有时候，你会遇到一种情况——你找不到理想的语义元素来包含项目或内容。有时候你可能只想仅仅用[CSS](https://developer.mozilla.org/en-US/docs/Glossary/CSS)或[JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript)将一组元素作为一个单独的实体来修饰。为了应对这种情况，HTML提供了 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div)和[`<span>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/span)元素。你应该最好使用[`class`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-class)属性来提供一些标签，这样他们就能容易的被找到。

[`<span>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/span) 是一个行内无语义元素，你应该仅仅当无法找到更好的语义元素包含内容时使用，或者不想增加特定的含义。例如：

```text
<p>The King walked drunkenly back to his room at 01:00, the beer doing nothing to aid
him as he staggered through the door <span class="editor-note">[Editor's note: At this point in the
play, the lights should be down low]</span>.</p>
```

在这种情况中，the editor’s note 应该仅仅是提供额外的对编辑器的说明；它没有额外的语义。对于用户来说，CSS可能用于从主文本中抽离这些note。

 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div) 是一个块级无语义元素，你应该仅仅当找不到更好的块级元素时使用，或者不想增加特定的意义。例如，想象当你浏览一个电子商务网站时，有一个购物车部件一直都在你可以选择的地方。

```text
<div class="shopping-cart">
  <h2>Shopping cart</h2>
  <ul>
    <li>
      <p><a href=""><strong>Silver earrings</strong></a>: $99.95.</p>
      <img src="../products/3333-0985/" alt="Silver earrings">
    </li>
    <li>
      ...
    </li>
  </ul>
  <p>Total cost: $237.89</p>
</div>
```

这并不是一个`<aside>`, 因为它和主要内容并没有必要的联系（你想在任何地方都能看到它。它甚至不能用`<section>`来特定的指定，因为它不是页面上主要内容的一部分。所以在这种情况下用`<div>`是合适的, 我们还需添加一个head标签帮助屏幕阅读者找到它。

**警告**: Divs用起来非常便利以至于很容易被滥用。因为它们不携带语义值，所以会让你的HTML代码变的混乱。要小心的使用它们，只有当没有更好的语义解决方案才能使用，而且要尽可能把它的使用量降到最低，否则，当你升级和维护你的文档时会非常困难。

#### 换行与水平分割线[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E6%8D%A2%E8%A1%8C%E4%B8%8E%E6%B0%B4%E5%B9%B3%E5%88%86%E5%89%B2%E7%BA%BF) <a id="&#x6362;&#x884C;&#x4E0E;&#x6C34;&#x5E73;&#x5206;&#x5272;&#x7EBF;"></a>

 [`<br>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/br) 和[`<hr>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/hr)将会是你偶尔使用并且想要了解的两个元素:

`<br>`在一个段落中创建一个换行；在你想要生成一系列的短行的地方，`<br>`是唯一能够生成这种结构的元素。例如一个邮寄地址或一首诗。比如：

```text
<p>There once was a girl called Nell<br>
Who loved to write HTML<br>
But her structure was bad, her semantics were sad<br>
and her markup didn't read very well.</p>
```

没有`<br>`元素，这一段会直接表示在一行中（正如我们之前在课程中看到的，[HTML会忽视大部分空格](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Getting_started#HTML%E4%B8%AD%E7%9A%84%E7%A9%BA%E7%99%BD)）；有了`<br>`元素，会生成下面这样的：

There once was a girl called Nell  
Who loved to write HTML  
But her structure was bad, her semantics were sad  
and her markup didn't read very well.

`<hr>`元素在文档中生成一条水平分割线，表示文本中主题的变化（例如主题或场景的变化）。看起来就是一条水平线。像下面的例子：

```text
<p>Ron was backed into a corner by the marauding netherbeasts. Scared, but determined to protect his friends, he raised his wand and prepared to do battle, hoping that his distress call had made it through.</p>
<hr>
<p>Meanwhile, Harry was sitting at home, staring at his royalty statement and pondering when the next spin off series would come out, when an enchanted distress letter flew through his window and landed in his lap. He read it hasily, and lept to his feet; "better get back to work then", he mused.</p>
```

将会表示成这样：

Ron was backed into a corner by the marauding netherbeasts. Scared, but determined to protect his friends, he raised his wand and prepared to do battle, hoping that his distress call had made it through.

Meanwhile, Harry was sitting at home, staring at his royalty statement and pondering when the next spin off series would come out, when an enchanted distress letter flew through his window and landed in his lap. He read it hasily and sighed; "better get back to work then", he mused.

### 设计一个简单的网站[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E8%AE%BE%E8%AE%A1%E4%B8%80%E4%B8%AA%E7%AE%80%E5%8D%95%E7%9A%84%E7%BD%91%E7%AB%99) <a id="&#x8BBE;&#x8BA1;&#x4E00;&#x4E2A;&#x7B80;&#x5355;&#x7684;&#x7F51;&#x7AD9;"></a>

一旦你设计好了一个简单网站的所有内容，按照正常的逻辑思维，我们应该尝试制定出你想要放在整个网站上的内容，哪些页面是你需要的，这些页面应该如何排列，以及如何互相链接，带给用户最好的使用体验。这就是所谓的 [Information architecture](https://developer.mozilla.org/en-US/docs/Glossary/Information_architecture).。在一个结构庞大、复杂的网站里，大多数设计都可以参照上述的 information architecture（信息架构），不过对于一个只有几个页面的简单网站，设计过程可以更简单，更有趣！

1. 记住, 你的大多数（不是全部）页面会使用一些相同的元素 — 例如导航菜单，以及页脚。如果你的网站是一个商业网站，那么你就可以在每个页面都使用相同的页脚，页脚内容可以包括你的联系方式，这或许是一个不错的主意。所以说，如果在你的设计中，每个页面都有一些内容是重复的，你可以先把这些重复的内容记录下来。![the common features of the travel site to go on every page: title and logo, contact, copyright, terms and conditions, language chooser, accessibility policy](https://mdn.mozillademos.org/files/12423/common-features.png)
2. 接下来，你可以通过画一个草图的方式来说明你希望的每个页面的结构的样子，（或许你画出来的草图和我们上文中提到的示例页面比较像），在空白段落上做上标记，来说明之后要填充在这里的内容。![A simple diagram of a sample site structure, with a header, main content area, two optional sidebars, and footer](https://mdn.mozillademos.org/files/12429/site-structure.png)
3. 现在，所有的网站设计人员可以一起讨论，还希望网站上显示哪些内容 （不包括每个页面的重复页面）— 以列表的形式写下来。![A long list of all the features that we could put on our travel site, from searching, to special offers and country-specific info](https://mdn.mozillademos.org/files/12425/feature-list.png)
4. 接着，尝试把这些内容进行分组，这样可以让你了解哪些内容可以放在一个相同的页面上。这种做法和 [Card sorting](https://developer.mozilla.org/en-US/docs/Glossary/Card_sorting) 非常相似。![The items that should appear on a holiday site sorted into 5 categories: Search, Specials, Country-specific info, Search results, and Buy things](https://mdn.mozillademos.org/files/12421/card-sorting.png)
5. 现在，尝试着再画一个网站的草图 — 每个气泡代表网站的一个页面，在气泡与气泡之间用连线的方式，来说明它们之间的联系。主页面可能位于中心位置，并且链接到其他的大多数页面；对于一个小型网站，大多数页面都可以从主页的导航栏中链接跳转，虽然也存在例外。你可能也希望记录下内容将如何显示的笔记。![A map of the site showing the homepage, country page, search results, specials page, checkout, and buy page](https://mdn.mozillademos.org/files/12427/site-map.png)

#### 主动学习：创建你自己的站点地图[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E5%88%9B%E5%BB%BA%E4%BD%A0%E8%87%AA%E5%B7%B1%E7%9A%84%E7%AB%99%E7%82%B9%E5%9C%B0%E5%9B%BE) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x521B;&#x5EFA;&#x4F60;&#x81EA;&#x5DF1;&#x7684;&#x7AD9;&#x70B9;&#x5730;&#x56FE;"></a>

尝试对你自己创造的网站进行上述步骤的练习。你想要做一个关于什么的网站？

**注意**: 将你的工作成果保存在任意的地方，之后你可能还会需要它。

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

通过本文，你应该对于如何构建一个网页/网站有了更好的理解。在本单元的最后一篇文章中，我们将学习如何调试 HTML。

### 相关链接[Section](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/%E6%96%87%E4%BB%B6%E5%92%8C%E7%BD%91%E7%AB%99%E7%BB%93%E6%9E%84#%E7%9B%B8%E5%85%B3%E9%93%BE%E6%8E%A5) <a id="&#x76F8;&#x5173;&#x94FE;&#x63A5;"></a>

* [Using HTML sections and outlines](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_HTML_sections_and_outlines): 进一步的指南: HTML5 的元素语义和大纲算法.

