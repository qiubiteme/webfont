# 样式化表格

设计一个 HTML表格不是世界上最迷人的工作，但有时我们必须这样做。本文提供了一个使HTML表格看起来不错的指南，其中一些功能在前面的文章中已作详细介绍。

| 预备知识： | HTML 基础\(学习 [Introduction to HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)\), HTML表格\(见HTML表各模块\(TBD\)\)，了解CSS工作原理\(study [Introduction to CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS).\) |
| :--- | :--- |
| 目标： | 学习如何有效地对HTML表格进行样式化。 |

### 一个典型的HTML表格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E4%B8%80%E4%B8%AA%E5%85%B8%E5%9E%8B%E7%9A%84HTML%E8%A1%A8%E6%A0%BC) <a id="&#x4E00;&#x4E2A;&#x5178;&#x578B;&#x7684;HTML&#x8868;&#x683C;"></a>

让我们从一个典型的HTML表格开始。恩，我说典型——大多数HTML表格都是关于鞋子，天气，或者员工的。我们决定通过制作英国著名的朋克乐队来让事情变得更有趣。标记看起来是这样的

```text
<table>
  <caption>A summary of the UK's most famous punk bands</caption>
  <thead>
    <tr>
      <th scope="col">Band</th>
      <th scope="col">Year formed</th>
      <th scope="col">No. of Albums</th>
      <th scope="col">Most famous song</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Buzzcocks</th>
      <td>1976</td>
      <td>9</td>
      <td>Ever fallen in love (with someone you shouldn't've)</td>
    </tr>
    <tr>
      <th scope="row">The Clash</th>
      <td>1976</td>
      <td>6</td>
      <td>London Calling</td>
    </tr>
       
      ... some rows removed for brevity

    <tr>
      <th scope="row">The Stranglers</th>
      <td>1974</td>
      <td>17</td>
      <td>No More Heroes</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row" colspan="2">Total albums</th>
      <td colspan="2">77</td>
    </tr>
  </tfoot>
</table>
```

由于[`scope`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/th#attr-scope)、[`<caption>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/caption)、[`<thead>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/thead)、[`<tbody>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tbody)等特性，表格被很好地标记了，易于使用，并且易于访问，不幸的是，它在屏幕上呈现时看起来不太好（见它的预览版 [punk-bands-unstyled.html](http://mdn.github.io/learning-area/css/styling-boxes/styling-tables/punk-bands-unstyled.html)）：

![](https://mdn.mozillademos.org/files/13064/table-unstyled.png)

它看起来很拥挤，很难阅读，也很无聊。我们需要使用一些CSS来解决这个问题。

### 自主学习：样式化我们的表格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0%EF%BC%9A%E6%A0%B7%E5%BC%8F%E5%8C%96%E6%88%91%E4%BB%AC%E7%9A%84%E8%A1%A8%E6%A0%BC) <a id="&#x81EA;&#x4E3B;&#x5B66;&#x4E60;&#xFF1A;&#x6837;&#x5F0F;&#x5316;&#x6211;&#x4EEC;&#x7684;&#x8868;&#x683C;"></a>

在这个自主学习部分中，我们将通过样式化我们的表格一起工作。

1. 首先，复制[实例标记](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/styling-tables/punk-bands-unstyled.html)的本地副本，下载这两个图像\([noise](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/styling-tables/noise.png)和 [leopardskin](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/styling-tables/leopardskin.jpg)\)，然后将三个结果文件放在本地计算机的某个工作目录中。
2. 接下来，创建一个名为`style.css`的新文件并将其保存在与其他文件相同的目录中。
3. 将CSS链接到HTML中，将下面的HTML代码放到HTML元素中[`<head>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/head)：

```text
<link href="style.css" rel="stylesheet" type="text/css">
```

#### 间距和布局[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E9%97%B4%E8%B7%9D%E5%92%8C%E5%B8%83%E5%B1%80) <a id="&#x95F4;&#x8DDD;&#x548C;&#x5E03;&#x5C40;"></a>

我们需要做的第一件事是整理出空间/布局——默认的表格样式是如此的拥挤！要做到这一点，请将以下CSS添加到您的 `style.css` 文件：

```text
/* spacing */

table {
  table-layout: fixed;
  width: 100%;
  border-collapse: collapse;
  border: 3px solid purple;
}

thead th:nth-child(1) {
  width: 30%;
}

thead th:nth-child(2) {
  width: 20%;
}

thead th:nth-child(3) {
  width: 15%;
}

thead th:nth-child(4) {
  width: 35%;
}

th, td {
  padding: 20px;
}
```

需要注意的最重要的部分如下：

* 在你的表上，给[`table-layout`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/table-layout)属性设置一个为`fixed`的值通常是一个好主意，因为它使表的行为在默认情况下更可预测。通常情况下，表列的大小会根据所包含的内容大小而变化，这会产生一些奇怪的结果。通过 `table-layout: fixed`，您可以根据标题的宽度来对列进行大小排序，然后根据适当的内容处理它们的内容。这就是为什么我们使用了`thead th:nth-child(`_`n`_`)` 选择了四个不同的标题\([`:nth-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-child)\)选择器（“选择第n个子元素，它是一个 [`<th>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/th)元素，在一个[`<thead>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/thead)元素中”）并给定了它们的百分比宽度。整个列宽度与标题的宽度是一样的，这是一种很好的方式来对表列进行大小。Chris Coyier在[Fixed Table Layouts](https://css-tricks.com/fixing-tables-long-strings/)中更详细地讨论了这一技术。  我们将它与一个100%的[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width)耦合在一起，这意味着该表将填充它放入的任何容器，并且响应得很好（虽然它仍然需要更多的工作来让它在窄屏宽度上看起来很好）。
* 一个[`border-collapse`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-collapse)属性的`collapse`值对于任何表样式的工作来说都是一个标准的最佳实践。默认情况下，当您在表元素上设置边框时，它们之间将会有间隔，如下图所示：![](https://mdn.mozillademos.org/files/13068/no-border-collapse.png)这看起来不太好\(虽然可能是你想要的样子，谁知道呢?\)。使用 `border-collapse: collapse;` ，让边框的间隔减少为一条，现在看起来好多了：![](https://mdn.mozillademos.org/files/13066/border-collapse.png)
* 我们在整个表中放置了一个[`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)，这是必要的，因为我们将在表页眉和页脚后面设置一些边框——当你在表格外面没有一个边界的时候，它看起来很奇怪，而且是不连贯的，最后会有空隙。
* 我们在 [`<th>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/th)和[`<td>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/td)元素上设置了一些[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)——这些元素使数据项有了一些空间，使表看起来更加清晰。

此刻，我们的表看起来好多了：

![](https://mdn.mozillademos.org/files/13070/table-with-spacing.png)

#### 一些简单的排版：[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E4%B8%80%E4%BA%9B%E7%AE%80%E5%8D%95%E7%9A%84%E6%8E%92%E7%89%88%EF%BC%9A) <a id="&#x4E00;&#x4E9B;&#x7B80;&#x5355;&#x7684;&#x6392;&#x7248;&#xFF1A;"></a>

现在我们把类型整理一下。

首先，我们在[Google Fonts](https://www.google.com/fonts)上找到了一种适合于朋克乐队的字体的字体。如果你愿意，你可以去那里找一个不同的。现在，您只需替换我们提供的[`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link)元素和定制的[`font-family`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-family)声明，并使用Google字体提供给您的内容。

首先，将下面的[`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link)元素添加到您的HTML头部，就在您现有的 `<link>` 元素之上：

```text
<link href='https://fonts.googleapis.com/css?family=Rock+Salt' rel='stylesheet' type='text/css'>
```

现在将下面的CSS添加到您的`style.css`文件，在之前的添加后：

```text
/* typography */

html {
  font-family: 'helvetica neue', helvetica, arial, sans-serif;
}

thead th, tfoot th {
  font-family: 'Rock Salt', cursive;
}

th {
  letter-spacing: 2px;
}

td {
  letter-spacing: 1px;
}

tbody td {
  text-align: center;
}

tfoot th {
  text-align: right;
}
```

这里没有什么特别的东西。我们通常会对字体样式进行调整，使其更易于阅读：

* 我们已经设置了一个全局无衬线字体;这纯粹是一种风格上的选择。我们还在[`<thead>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/thead)和 [`<tfoot>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tfoot)元素的标题上设置了自定义字体，这是一种很不错的、很有朋克风格的外观。
* 我们在标题和单元格上设置了一些[`letter-spacing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing)，因为我们觉得它有助于提高可读性。再次强调，这主要是一种风格上的选择。
* 我们在[`<tbody>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tbody)中的表格单元中对文本进行了居中对齐，使它们与标题对齐。默认情况下，单元格被赋予了一个[`text-align`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align)的`left`值，并且标题被赋予了一个`center`值，但是通常情况下，让两个组的对齐看起来更好。标题字体的默认粗体值足以区分它们的外观。
* 我们在 [`<tfoot>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tfoot)中对标题进行了右对齐，以便与它的数据点更好地关联。

结果看起来更整洁一些：

![](https://mdn.mozillademos.org/files/13072/table-with-typography.png)

#### 图形和颜色[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E5%9B%BE%E5%BD%A2%E5%92%8C%E9%A2%9C%E8%89%B2) <a id="&#x56FE;&#x5F62;&#x548C;&#x989C;&#x8272;"></a>

现在我们来画图形和颜色！因为表格上满是“朋克“和”态度“，我们需要给它一些鲜艳的造型来适应。别担心，你不必让你的表格”燥起来“，你可以选择一些更微妙、更有品位的东西。

首先将下面的CSS添加到`style.css`文件中，在底部添加:

```text
thead, tfoot {
  background: url(leopardskin.jpg);
  color: white;
  text-shadow: 1px 1px 1px black;
}

thead th, tfoot th, tfoot td {
  background: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(0,0,0,0.5));
  border: 3px solid purple;
}
```

同样，对于表格这里没有什么特别的，但有几件事值得注意。

我们已经将一个[`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)添加到[`<thead>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/thead)和 [`<tfoot>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tfoot)，并将页眉和页脚的所有文本颜色[`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color)更改为白色\(并给它一个[`text-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow)\)，这样它就可读了。你应该确保你的文字与你的背景形成鲜明的对比，使得它是可读的。

我们还为 [`<th>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/th)和 [`<td>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/td)添加了一个线性渐变，在页眉和页脚中添加了一个漂亮的纹理，同时也为这些元素提供了一个明亮的紫色边框。有多个嵌套的元素是很有用的，这样您就可以将样式层叠在一起。是的，我们可以在[`<thead>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/thead)和  [`<tfoot>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tfoot)元素上使用背景图像和线性渐变，但是我们决定分开使用，因为考虑到不支持多个背景图像或线性渐变的老浏览器。

**斑马条纹图案**

我们想用一个单独的部分来展示如何实现斑马条纹（**zebra stripes**）——在表中交替行不同的数据行可以更容易地进行解析和读取。将下面的CSS添加到您的 `style.css` 文件底部：

```text
tbody tr:nth-child(odd) {
  background-color: #ff33cc;
}

tbody tr:nth-child(even) {
  background-color: #e495e4;
}

tbody tr {
  background-image: url(noise.png);
}

table {
  background-color: #ff33cc;
}
```

* 您在前面看到了[`:nth-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-child)选择器用于选择特定的子元素。它也可以作为一个参数给出一个公式，所以它会选择一个元素序列。公式`2n-1`会选择所有奇数的子数\(1、3、5等\)，而公式`2n`会选择所有偶数的子数\(2、4、6等等\)。我们在代码中使用了`odd`和`even`的关键字，这与前面提到的公式完全相同。在这种情况下，我们给奇数行和偶数行不同的\(耀眼的\)颜色。
* 我们还为所有的行添加了一个重复的背景色块，其实就是加一点噪音（一个半透明的`.png`，有一点视觉上的扭曲）提供一些纹理。
* 最后，我们给整个表格提供了一个纯的背景颜色，这样浏览器不支持`:nth-child`选择器仍然有它们的正文行的背景。

这种颜色爆炸的结果如下：

![](https://mdn.mozillademos.org/files/13074/table-with-color.png)

现在，这可能有点过头不符合你的品味，但我们在这里想要指出的一点是，表格并非是枯燥无味的，学术性的。

#### 样式化标题[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E6%A0%B7%E5%BC%8F%E5%8C%96%E6%A0%87%E9%A2%98) <a id="&#x6837;&#x5F0F;&#x5316;&#x6807;&#x9898;"></a>

还有最后一件事要处理我们的表格——样式化标题。要做到这一点，请将以下内容添加到您的`style.css` 文件底部：

```text
caption {
  font-family: 'Rock Salt', cursive;
  padding: 20px;
  font-style: italic;
  caption-side: bottom;
  color: #666;
  text-align: right;
  letter-spacing: 1px;
}
```

这里没有什么值得注意的地方，除了 [`caption-side`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/caption-side)属性，它被赋予了一个底部`bottom`的值。这就导致标题被放置在表格的底部，与其他声明一起提供了最后的外观（见预览版[punk-bands-complete.html](http://mdn.github.io/learning-area/css/styling-boxes/styling-tables/punk-bands-complete.html)）：

![](https://mdn.mozillademos.org/files/13076/table-with-caption.png)

### 自主学习：样式化你自己的表格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0%EF%BC%9A%E6%A0%B7%E5%BC%8F%E5%8C%96%E4%BD%A0%E8%87%AA%E5%B7%B1%E7%9A%84%E8%A1%A8%E6%A0%BC) <a id="&#x81EA;&#x4E3B;&#x5B66;&#x4E60;&#xFF1A;&#x6837;&#x5F0F;&#x5316;&#x4F60;&#x81EA;&#x5DF1;&#x7684;&#x8868;&#x683C;"></a>

现在，我们希望您可以使用我们的示例表格HTML\(或者使用您自己的一些！\)，并将其样式设计成比我们的表更好的设计和不那么花哨的东西。

### 表格样式小贴士[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E8%A1%A8%E6%A0%BC%E6%A0%B7%E5%BC%8F%E5%B0%8F%E8%B4%B4%E5%A3%AB) <a id="&#x8868;&#x683C;&#x6837;&#x5F0F;&#x5C0F;&#x8D34;&#x58EB;"></a>

在继续之前，我们认为我们将为您提供一个快速列表，列出了上面提到的最有用的点：

* 使您的表格标记尽可能简单，并且保持灵活性，例如使用百分比，这样设计就更有响应性。
* 使用 [`table-layout`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/table-layout)`: fixed` 创建更可预测的表布局，可以通过在标题[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width)中设置[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width)来轻松设置列的宽度。
* 使用 [`border-collapse`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-collapse)`: collapse` 使表元素边框合并，生成一个更整洁、更易于控制的外观。
* 使用[`<thead>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/thead), [`<tbody>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tbody)和 [`<tfoot>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tfoot) 将表格分割成逻辑块，并提供额外的应用CSS的地方，因此如果需要的话，可以更容易地将样式层叠在一起。
* 使用斑马线来让其他行更容易阅读。
* 使用 [`text-align`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align)直线对齐您的 [`<th>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/th)和[`<td>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/td)文本，使内容更整洁、更易于跟随。

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/Styling_tables#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

现在，我们身后的表格样式令人炫目，令人兴奋，我们需要一些其他的东西来占据我们的时间。不要担心——下一章会介绍一些高级的方框效果，其中一些只在最近才出现在浏览器中\(比如混合模式和过滤器\)，还有一些已经比较成熟了（比如框阴影。）

