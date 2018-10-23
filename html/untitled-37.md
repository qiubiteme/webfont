# 样式化 HTML 表单

在这篇文章中，用户将学习如何使用HTML表单和CSS以使页面更加美观。令人惊讶的是，这可能有点棘手。由于历史和技术的原因，表单部件不能很好地与CSS配合工作。 由于这些困难，许多开发人员选择[构建自己的HTML小部件](https://developer.mozilla.org/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets)以获得更好的控制和视觉观感。 然而，在现代浏览器中，web设计者越来越多地控制表单元素的设计。让我们深入研究。

### 为什么使用CSS美化表单组件这么困难？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BD%BF%E7%94%A8CSS%E7%BE%8E%E5%8C%96%E8%A1%A8%E5%8D%95%E7%BB%84%E4%BB%B6%E8%BF%99%E4%B9%88%E5%9B%B0%E9%9A%BE%EF%BC%9F) <a id="&#x4E3A;&#x4EC0;&#x4E48;&#x4F7F;&#x7528;CSS&#x7F8E;&#x5316;&#x8868;&#x5355;&#x7EC4;&#x4EF6;&#x8FD9;&#x4E48;&#x56F0;&#x96BE;&#xFF1F;"></a>

在1995年左右的Web早期，表单组件\(或控件\)在 [HTML 2规范](http://www.ietf.org/rfc/rfc1866.txt)中被添加到HTML。由于表单组件的复杂性，实现者选择依靠底层操作系统来管理和渲染它们。

若干年后，CSS被创建出来了，那么技术上的必要性，就是使用原生组件来实现表单控制，这是因为风格的要求。在CSS的早期，表单样式控制不是优先事项。

由于用户习惯于各自平台的视觉外观，浏览器厂商不愿意对表单控件样式进行调整;到目前为止，要重建所有控件以使它们可美化仍然是非常困难的。

即使在今天，仍然没有一个浏览器完全实现了CSS 2.1。然而，随着时间的推移，浏览器厂商已经改进了对表单元素的CSS支持，尽管可用性的声誉不好，但现在已经可以使用CSS来设计[HTML表单](https://developer.mozilla.org/en-US/docs/HTML/Forms)。

#### 涉及到CSS，并非所有组件都是平等的[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E6%B6%89%E5%8F%8A%E5%88%B0CSS%EF%BC%8C%E5%B9%B6%E9%9D%9E%E6%89%80%E6%9C%89%E7%BB%84%E4%BB%B6%E9%83%BD%E6%98%AF%E5%B9%B3%E7%AD%89%E7%9A%84) <a id="&#x6D89;&#x53CA;&#x5230;CSS&#xFF0C;&#x5E76;&#x975E;&#x6240;&#x6709;&#x7EC4;&#x4EF6;&#x90FD;&#x662F;&#x5E73;&#x7B49;&#x7684;"></a>

目前，在使用表单时使用CSS仍然有一些困难。这些问题可以分为三类： 

**好的**

有些元素在跨平台上时很少出现问题。包括以下结构元素：

1. [`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form)
2. [`<fieldset>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/fieldset)
3. [`<label>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label)
4. [`<output>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/output)

这还包括所有文本字段小部件（单行和多行）和按钮。

**不好的**

一些元素难以被美化，并且可能需要一些复杂的技巧，偶尔需要高级的CSS3知识。

这些包括[`<legend>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/legend)元素，但不能在所有平台上正确定位。 Checkbox和radio按钮也不能直接应用样式，但是，感谢CSS3，你可以解决这个问题。[`placeholder`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-placeholder) 的内容不能以任何标准方式应用样式，但是实现它的所有浏览器也都实现了私有的CSS伪元素或伪类，让你可以对其定义样式。

我们会在[Advanced styling for HTML forms](https://developer.mozilla.org/en-US/docs/Advanced_styling_for_HTML_forms)一文中讲述如何处理更多特定的问题。

**丑陋的**

有些元素根本不能用应用CSS样式。 这些包括：所有高级用户界面小部件，如范围，颜色或日期控件; 和所有下拉小部件，包括[`<select>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select), [`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option), [`<optgroup>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup)和[`<datalist>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/datalist) 元素。 文件选择器小部件也被称为不可风化。 新的[`<progress>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/progress)和[`<meter>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter) 元素也属于这个类别。

所有这些小部件的主要问题来自于它们具有非常复杂的结构，而CSS目前还不足以表达这些小部件的所有细微部分。 如果你想定制这些小部件，你必须依靠JavaScript来构建一个你能够应用样式的DOM树。我们会在 [How to build custom form widgets](https://developer.mozilla.org/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets)一文中探索如何实现这一点。

### 基本样式美化[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E5%9F%BA%E6%9C%AC%E6%A0%B7%E5%BC%8F%E7%BE%8E%E5%8C%96) <a id="&#x57FA;&#x672C;&#x6837;&#x5F0F;&#x7F8E;&#x5316;"></a>

为了使用CSS美化容易被美化的元素，你并不会碰到任何困难，因为它们的大部分行为同其他HTML元素差不都。但是，每个浏览器的用户代理样式表可能会有点不一致，所以有一些技巧可以帮助您更轻松地设计它们。

#### Search字段[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#Search%E5%AD%97%E6%AE%B5) <a id="Search&#x5B57;&#x6BB5;"></a>

搜索框是唯一一种应用CSS样式有点棘手的文本字段。 在基于WebKit的浏览器（Chrome，Safari等）上，您必须使用`-webkit-appearance`专有属性来调整它。 我们在文章中进一步讨论这个属性：[HTML表单的高级样式](https://developer.mozilla.org/en-US/docs/Advanced_styling_for_HTML_forms)。

**Example**

```text
<form>
  <input type="search">
</form>
```

```text
input[type=search] {
  border: 1px dotted #999;
  border-radius: 0;

  -webkit-appearance: none;
}
```

![This is a screenshot of a search filed on Chrome, with and without the use of -webkit-appearance](https://developer.mozilla.org/files/4153/search-chrome-macos.png)

正如你在截图中所见，Chrome浏览器中的搜索字段两个字段在我们的例子中被设置为有边框。第一个字段没有使用`-webkit-appearance`渲染，而第二个使用 `-webkit-appearance:none`. 两者的不同显而易见。

#### 字体和文本[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E5%AD%97%E4%BD%93%E5%92%8C%E6%96%87%E6%9C%AC) <a id="&#x5B57;&#x4F53;&#x548C;&#x6587;&#x672C;"></a>

CSS font和text功能能被很容易的应用到任何组件上（当然你可以在form组件上使用[`@font-face`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@font-face) ）。然而，浏览器的行为经常不一致。默认情况下，一些组件不不会从它们的父元素继承 [`font-family`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-family)和 [`font-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size) 。相反，许多浏览器使用系统默认的字体和文本。为了让form表单的外观和其他内容保持一致，你可以在你的样式表中增加以下内容:

```text
button, input, select, textarea {
  font-family : inherit;
  font-size   : 100%;
}
```

下面的截图显示了不同之处; 左边是Mac OS X上Firefox中元素的默认渲染，其中使用了平台的默认字体样式。 在右边是相同的元素，应用了我们的字体统一样式规则。

![This is a screenshot of the main form widgets on Firefox on Mac OSX, with and without font harmonization](https://developer.mozilla.org/files/4157/font-firefox-macos.png)

关于使用系统默认样式的表单还是使用设计用于匹配内容的自定义样式表单，有很多争议。 作为网站或Web应用程序的设计者，您可以自己做出决定。

#### 盒子模型[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8B) <a id="&#x76D2;&#x5B50;&#x6A21;&#x578B;"></a>

所有文本字段都完全支持与CSS盒模型相关的每个属性\([`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width), [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height), [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding), [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin), 和 [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)\)。 但是，像以前一样，浏览器在显示这些小部件时依赖于系统默认的样式。 您需要定义如何将其融入到您的内容中。 如果你既想保持小部件的原生外观和感觉，又想给他们一个一致的尺寸，那么你会遇到一些困难\(如果你想保持组件的原生观感，又想给它们一致的大小，你会面临一些困难\)。

**这是因为每个小部件都有自己的边框，填充和边距的规则。** 所以如果你想给几个不同的小部件相同的大小，你必须使用[`box-sizing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing) 属性：

```text
input, textarea, select, button {
  width : 150px;
  margin: 0;

  -webkit-box-sizing: border-box; /* For legacy WebKit based browsers */
     -moz-box-sizing: border-box; /* For legacy (Firefox <29) Gecko based browsers */
          box-sizing: border-box;
}
```

![This is a screenshot of the main form widgets on Chrome on Windows 7, with and without the use of box-sizing.](https://developer.mozilla.org/files/4161/size-chrome-win7.png)

在上面的屏幕截图中，左侧的列没有[`box-sizing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing)，而右侧的列使用了这个属性和`border-box`。 请注意我们是怎样确保所有元素都占用相同的空间量，尽管平台对每种窗口小部件都有默认规则。

#### 定位（Positioning）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E5%AE%9A%E4%BD%8D%EF%BC%88Positioning%EF%BC%89) <a id="&#x5B9A;&#x4F4D;&#xFF08;Positioning&#xFF09;"></a>

HTML表单部件的定位通常不是问题; 但是，您应该特别注意两点：

**legend**

[`<legend>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/legend)元素易于应用CSS，除了定位。在所有浏览器中， [`<legend>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/legend) 元素定位是其 [`<fieldset>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/fieldset) 父元素的上边框的最顶端。在HTML流中无法改变它的绝对位置，无法让其远离顶部边框。然而，你可以使用 [`position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position) 属性将其位置设置为绝对或相对。除此之外，它近几年是fieldset边框的一部分。

由于[`<legend>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/legend)元素对可访问性非常重要，因为它能被无障碍技术作为每个fieldset中的表单元素的标签读出来，它通常与标题配对，并且在无障碍中被隐藏 。例如:

**HTML**

```text
<fieldset>
  <legend>Hi!</legend>
  <h1>Hello</h1>
</fieldset>
```

**CSS**

```text
legend {
  width: 1px;
  height: 1px;
  overflow: hidden;
}
```

**textarea**

默认情况下，所有浏览器都认为 [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea) 元素是inline block，与文本底线对齐。 这很少是我们真正想看到的。 要将内联\(`inline-block`\)块更改为块\(`block`\)，使用[`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display)属性非常简单。 但是如果你想以inline方式使用它，通常改变垂直对齐方式：

```text
textarea {
  vertical-align: top;
}
```

### 示例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E7%A4%BA%E4%BE%8B) <a id="&#x793A;&#x4F8B;"></a>

让我们来看一个样式化 HTML 表单的实际的案例。这有助于厘清这里面的许多概念。我们将构建下面的"明信片" 联系人表单：

![This is what we want to achieve with HTML and CSS](https://developer.mozilla.org/files/4149/screenshot.png)

如果你想继续关注这个例子，复制我们的 postcard-start.html 文件，并遵循接下来的指导操作。

#### The HTML[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#The_HTML) <a id="The_HTML"></a>

HTML 只比我们在 [the first article of this guide](https://developer.mozilla.org/en-US/docs/HTML/Forms/My_first_HTML_form) 中涉及到的多一些；它只有一些额外的 id 和 title。

```text
<form>
  <h1>to: Mozilla</h1>

  <div id="from">
    <label for="name">from:</label>
    <input type="text" id="name" name="user_name">
  </div>

  <div id="reply">
    <label for="mail">reply:</label>
    <input type="email" id="mail" name="user_email">
  </div>

  <div id="message">
    <label for="msg">Your message:</label>
    <textarea id="msg" name="user_message"></textarea>
  </div>
 
  <div class="button">
    <button type="submit">Send your message</button>
  </div>
</form>
```

将上面的代码添加到你 HTML 的 body 中。

#### 组织你的静态文件[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E7%BB%84%E7%BB%87%E4%BD%A0%E7%9A%84%E9%9D%99%E6%80%81%E6%96%87%E4%BB%B6) <a id="&#x7EC4;&#x7EC7;&#x4F60;&#x7684;&#x9759;&#x6001;&#x6587;&#x4EF6;"></a>

好戏要开始了! 在开始写代码之前，我们需要三个额外的静态文件：

1. 明信片的[背景](https://developer.mozilla.org/files/4151/background.jpg)——下载这幅图片，把它和你的 HTML 文件保存在相同目录下。
2. 打字机字体：[源自 fontsquirrel.com 的 "Secret Typewriter“ 字体](http://www.fontsquirrel.com/fonts/Secret-Typewriter)——将TTF文件下载到和上面相同的文件夹里。
3. 手绘字体：[源自 fontsquirrel.com 的 The "Journal" 字体 ](http://www.fontsquirrel.com/fonts/Journal) —— 将TTF文件下载到和上面相同的文件夹里。

在你开始之前需要对字体做一些处理：

1. 打开 fontsquirrel [网络字体生成器](https://www.fontsquirrel.com/tools/webfont-generator).
2. 使用表单，上传你的字体文件并生成一个网络字体包，将这个包下载到你的电脑上。
3. 解压提供的 zip 文件。
4. 再解压后的文件内容里你会找到两个  `.woff` 文件和两个`.woff2` 文件。将这四个文件拷贝到一个叫 fonts 的文件夹里，而fonts 文件夹位于和上面相同的文件夹里。我们为每种字体使用两个不同的文件以最大限度地保证浏览器兼容性。查看我们的 [Web 字体](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Web_fonts) 一文获取更多信息。

#### CSS[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#CSS_2) <a id="CSS_2"></a>

现在我们可以深入探究本例的 CSS 了。将下面所有的代码块一个接一个地加到[`<style>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/style) 元素里。

首先，我们要准备一些基础。这需要定义 [`@font-face`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@font-face) 规则，以及所有的 [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) 元素和 [`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form) 元素基本规则：

```text
@font-face {
    font-family: 'handwriting';
    src: url('fonts/journal-webfont.woff2') format('woff2'),
         url('fonts/journal-webfont.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

@font-face {
    font-family: 'typewriter';
    src: url('fonts/veteran_typewriter-webfont.woff2') format('woff2'),
         url('fonts/veteran_typewriter-webfont.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

body {
  font  : 21px sans-serif;

  padding : 2em;
  margin  : 0;

  background : #222;
}

form {
  position: relative;

  width  : 740px;
  height : 498px;
  margin : 0 auto;

  background: #FFF url(background.jpg);
}
```

现在我们可以定位我们的元素，包括标题和其他表单元素：

```text
h1 {
  position : absolute;
  left : 415px;
  top  : 185px;
 
  font : 1em "typewriter", sans-serif;
}

#from {
  position: absolute;
  left : 398px;
  top  : 235px;
}

#reply {
  position: absolute;
  left : 390px;
  top  : 285px;
}

#message {
  position: absolute;
  left : 20px;
  top  : 70px;
}
```

现在我们开始处理表单元素本身。首先，让我们确保 [`<label>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label) 被赋予了正确的字体：

```text
label {
  font : .8em "typewriter", sans-serif;
}
```

文本域需要一些通用的规则，我们只需简单的移除 [`borders`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) 和 [`backgrounds`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background), 并重新定义其[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) 和 [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)：

```text
input, textarea {
  font    : .9em/1.5em "handwriting", sans-serif;

  border  : none;
  padding : 0 10px;
  margin  : 0;
  width   : 240px;

  background: none;
}
```

当其中的一个域获得焦点后，我们用浅灰色、半透明的背景高亮它们，注意添加[`outline`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline) 属性非常重要，这样可以移除由某些浏览器添加的默认高亮效果：

```text
input:focus, textarea:focus {
  background   : rgba(0,0,0,.1);
  border-radius: 5px;
  outline      : none;
}
```

现在我们的文本域已经完成了，我们需要调整单行和多行文本域的显示，使其能够匹配，因为通常情况下它们不会以默认的设置而具有一样的外观。

单行文本需要一些调整才能在 Internet Explorer 中渲染良好。Internet Explorer 没有定义基于字体的自然高度定义文本域的高度。\(而这是所有其他浏览器都有的行为\)。为了修正这个问题，我们需要给域添加一个确定的高度，像下面这样：

```text
input {
    height: 2.5em; /* for IE */
    vertical-align: middle; /* This is optional but it makes legacy IEs look better */
}
```

 [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea) 元素默认地被渲染成一个块级元素。这里有重要地两点是 [`resize`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/resize) 和 [`overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow)属性。因为我们的设计是一个固定大小的设计，所以我们会使用 `resize` 属性来防止用户调整我们的多行文本域的大小。[`overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow) 属性是用来让域在不同的浏览器上渲染得更一致。一些浏览器默认值为 `auto`，而一些将默认值设为 `scroll`。在我们得例子中，最好确定每个浏览器都使用 `auto`：

```text
textarea {
  display : block;

  padding : 10px;
  margin  : 10px 0 0 -10px;
  width   : 340px;
  height  : 360px;

  resize  : none;
  overflow: auto;
}
```

 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button) 元素上使用 CSS 非常方便；你可以做你任何想做得事情，甚至包括使用 [伪元素](https://developer.mozilla.org/en-US/docs/CSS/Pseudo-elements)：

```text
button {
  position     : absolute;
  left         : 440px;
  top          : 360px;

  padding      : 5px;

  font         : bold .6em sans-serif;
  border       : 2px solid #333;
  border-radius: 5px;
  background   : none;

  cursor       : pointer;

-webkit-transform: rotate(-1.5deg);
   -moz-transform: rotate(-1.5deg);
    -ms-transform: rotate(-1.5deg);
     -o-transform: rotate(-1.5deg);
        transform: rotate(-1.5deg);
}

button:after {
  content: " >>>";
}

button:hover,
button:focus {
  outline   : none;
  background: #000;
  color   : #FFF;
}
```

瞧！

**注意：如果你的例子没有像你预期的那样工作，你想将它同我们的版本检查对比，**你可以在Github 上找到它 —— 查看 [在线演示](https://mdn.github.io/learning-area/html/forms/postcard-example/) \(也可以查看[源代码](https://github.com/mdn/learning-area/tree/master/html/forms/postcard-example)\)。

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

如你所见，若我们想构建只包含文本域和按钮的表单，用 CSS 美化它们非常容易。如果你想要知道更多能够让你的处理表单组件时更轻松的 CSS 小技巧，看一看 [normalize.css](http://necolas.github.com/normalize.css) 项目的表单部分。

[下一篇文章中](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms/Advanced_styling_for_HTML_forms)，我们将会看到如何处理落入"不好的" 和"丑陋的" 分类的表单组件。

