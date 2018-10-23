# 高级设计 HTML 表单



在本文中，我们将看到[HTML](https://developer.mozilla.org/en-US/docs/HTML)表单怎样使用[CSS](https://developer.mozilla.org/en-US/docs/CSS)装饰难以定制的表单小部件。如[前面章节](https://developer.mozilla.org/en-US/docs/HTML/Forms/Styling_HTML_forms)所示，文本域和按钮完全可以使用CSS，现在我们将深入探索HTML表单样式。

在继续之前，让我们回忆一下两种表单小部件：bad这个元素很难设计，需要一些复杂的技巧，有时还涉及到高级的CSS3的知识。ugly忘记使用CSS来设计这些元素吧。你最多能做一点点事情，还不能保证可以跨浏览器，而且在它们出现时永远不能做到完全的受控。

### CSS表现力[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms#CSS%E8%A1%A8%E7%8E%B0%E5%8A%9B) <a id="CSS&#x8868;&#x73B0;&#x529B;"></a>

除了文本框和按钮之外，使用其他表单小部件的主要问题是在许多情况下，CSS的表现不能满足设计复杂的小部件的要求。

HTML和CSS最新的发展扩展了CSS的表现力：

* [CSS 2.1](http://www.w3.org/TR/CSS21/selector.html#dynamic-pseudo-classes) 非常受限，只给出三个伪类：
  *  [`:active`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:active)
  * [`:focus`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:focus)
  * [`:hover`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:hover)
* [CSS Selector Level 3](http://www.w3.org/TR/css3-selectors/) 增加了三个与HTML表单相关的伪类：
  * [`:enabled`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:enabled)
  * [`:disabled`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:disabled)
  * [`:checked`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:checked)
  * [`:indeterminate`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:indeterminate)
* [CSS Basic UI Level 3](http://dev.w3.org/csswg/css3-ui/#pseudo-classes) 也增加了几个伪类用于描述小部件的状态：
  * [`:default`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:default)
  *  [`:valid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:valid)
  * [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid)
  * [`:in-range`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:in-range)
  * [`:out-of-range`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:out-of-range)
  *  [`:required`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:required)
  * [`:optional`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:optional)
  * [`:read-only`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:read-only)
  * [`:read-write`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:read-write)
* [CSS Selector Level 4](http://dev.w3.org/csswg/selectors4/) 目前处于积极应用和重点讨论的状态，但并不打算为表单做更多的改善：
  * [`:user-error`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:user-error) 只是改进了伪类[`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid)。

所有这一切是一个好的开端，但是有两个问题。首先，一些浏览器不需要实现CSS 2.1之上的特性。其次在设计像日期选择器这样的复杂的小部件时，这些实在不够好。

浏览器厂家在CSS表现力在表单方面的扩展做了一些尝试，在某些情况下，知道什么可用也挺不错的。

**警告：** 尽管 这些尝试很有趣，但**它们是非标准的，也就是不可靠的。**. 如果你使用它们\(也许你并不常用\)，你要自己承担风险，使用非标准的属性[对于Web并不是好事](http://www.alistapart.com/articles/every-time-you-call-a-proprietary-feature-css3-a-kitten-dies/) 。

* [Mozilla CSS 扩展](https://developer.mozilla.org/en-US/docs/CSS/CSS_Reference/Mozilla_Extensions)
  * [`:-moz-placeholder`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:-moz-placeholder)
  * [`:-moz-submit-invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:-moz-submit-invalid)
  * [`:-moz-ui-invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:-moz-ui-invalid)
  * [`:-moz-ui-valid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:-moz-ui-valid)
* [WebKit CSS 扩展](https://developer.mozilla.org/en-US/docs/CSS/CSS_Reference/Webkit_Extensions)
  * [`::-webkit-input-placeholder`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::-webkit-input-placeholder)
  * [其他](http://trac.webkit.org/wiki/Styling%20Form%20Controls)
* [Microsoft CSS 扩展](http://msdn.microsoft.com/en-us/library/ie/hh869403%28v=vs.85%29.aspx)
  * [`:-ms-input-placeholder`](http://msdn.microsoft.com/en-us/library/ie/hh772745%28v=vs.85%29.aspx)

#### 控制表单元素的外观[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms#%E6%8E%A7%E5%88%B6%E8%A1%A8%E5%8D%95%E5%85%83%E7%B4%A0%E7%9A%84%E5%A4%96%E8%A7%82) <a id="&#x63A7;&#x5236;&#x8868;&#x5355;&#x5143;&#x7D20;&#x7684;&#x5916;&#x89C2;"></a>

基于WebKit\(Chrome, Safari\)和 Gecko\(Firefox\)的浏览器提供更高级的HTML部件定制。它们也实现了跨平台，因此需要一种方式把原生小部件转换为用户可设置样式的小部件。

为此，它们使用了专有属性：[`-webkit-appearance`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/-webkit-appearance)或[`-moz-appearance`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/-moz-appearance)。**那些属性是非标准的，不应该使用。**事实上，它们在WebKit 和Gecko中的表现也是不相同的。然而，有一个值很好用：`none`，用这个值，你（几乎完全）能控制一个已知小部件的样式。

因此，如果你在应用一个元素的样式时遇到麻烦，可以尝试使用那些专有属性。我们下面有一些例子，这个属性最成功的例子是WebKit浏览器中的搜索域的样式：

```text
<form>
    <input type="search">
</form>
```

```text
<style>
input[type=search] {
    border: 1px dotted #999;
    border-radius: 0;
    
    -webkit-appearance: none;
}
</style>
```

**注意：**当我们谈及Web技术的时总是很难预测未来。扩展CSS表现力是很困难的，其他规范也做了一些探索性的工作，如[Shadow DOM](http://dvcs.w3.org/hg/webcomponents/raw-file/tip/spec/shadow/index.html)提供了一些观点。可完全设置样式的表单的问题还远未结束。

### 举例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms#%E4%B8%BE%E4%BE%8B) <a id="&#x4E3E;&#x4F8B;"></a>

#### 复选框和单选按钮[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms#%E5%A4%8D%E9%80%89%E6%A1%86%E5%92%8C%E5%8D%95%E9%80%89%E6%8C%89%E9%92%AE) <a id="&#x590D;&#x9009;&#x6846;&#x548C;&#x5355;&#x9009;&#x6309;&#x94AE;"></a>

独自设计复选框或单选按钮的样式是让人抓狂的。例如由于浏览器反应各不相同，在修改复选框和单选按钮的大小时，并不保证确实能改变它们。

**一个简单的测试用例**

让我们研究一下下面的测试用例：

```text
<span><input type="checkbox"></span>
```

```text
span {
    display: inline-block;
    background: red;
}

input[type=checkbox] {
    width : 100px;
    height: 100px;
}
```

这里是不同的浏览器的处理方式：

| 浏览器 | 视图 |
| :--- | :--- |
| Firefox 57 \(Mac OSX\) | ![](https://mdn.mozillademos.org/files/15671/firefox-mac-checkbox.png) |
| Firefox 57 \(Windows 10\) | ![](https://mdn.mozillademos.org/files/15691/firefox-windows-checkbox.png) |
| Chrome 63 \(Mac OSX\) | ![](https://mdn.mozillademos.org/files/15676/chrome-mac-checkbox.png) |
| Chrome 63 \(Windows 10\) | ![](https://mdn.mozillademos.org/files/15681/chrome-windows-checkbox.png) |
| Opera 49 \(Mac OSX\) | ![](https://mdn.mozillademos.org/files/15701/opera-mac-checkbox.png) |
| Internet Explorer 11 \(Windows 10\) | ![](https://mdn.mozillademos.org/files/15696/ie11-checkbox.png) |
| Edge 16 \(Windows 10\) | ![](https://mdn.mozillademos.org/files/15686/edge-checkbox.png) |

**更复杂的例子**

由于Opera和Internet Explorer没有像[`-webkit-appearance`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/-webkit-appearance)或[`-moz-appearance`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/-moz-appearance)这样的特性，使用它们是不合适的。幸运的是，CSS有足够多的表现方式可以找到解决方法。让我们做一个很普通的例子：

```text
<form>
  <fieldset>
    <p>
      <input type="checkbox" id="first" name="fruit-1" value="cherry">
      <label for="first">I like cherry</label>
    </p>
    <p>
      <input type="checkbox" id="second" name="fruit-2" value="banana" disabled>
      <label for="second">I can't like banana</label>
    </p>
    <p>
      <input type="checkbox" id="third" name="fruit-3" value="strawberry">
      <label for="third">I like strawberry</label>
    </p>
  </fieldset>
</form>
```

带有一些基本的样式：

```text
body {
  font: 1em sans-serif;
}

form {
  display: inline-block;

  padding: 0;
  margin : 0;
}

fieldset {
  border : 1px solid #CCC;
  border-radius: 5px;
  margin : 0;
  padding: 1em;
}

label {
  cursor : pointer;
}

p {
  margin : 0;
}

p+p {
  margin : .5em 0 0;
}
```

现在，让我们设计一个定制复选框的样式

计划用自己的图像替换原生的复选框，首先需要准备复选框在所有状态下的图像，那些状态是：未选、已选、禁用不选、禁用已选。该图像将用作CSS精灵：

![Check box CSS Sprite](https://developer.mozilla.org/files/4173/checkbox-sprite.png)

一开始要隐藏初始复选框。可以简单的把它们从页面视图中拿开。这里要考虑两个重要的事情：

* 不能用`display:none`来隐藏复选框，因为后面我们需要把复选框对用户可见。而使用`display:none`，用户不能再访问这个复选框，这就表示复选框不能选择或不选择。
* 我们将使用CSS3选择器来实现定制的样式，为了支持旧版浏览器，可以在所有选择器前设置 [`:root`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:root)伪类。目前所有我们需要支持的浏览器都支持 [`:root`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:root)伪类，但是其他的并不能保证。这是一个过滤旧的Internet Explorer的便利方式的例子。那些旧版浏览器将看到传统的复选框，而新式的浏览器可以看到定制的复选框。

```text
:root input[type=checkbox] {
  /* original check box are push outside the viexport */
  position: absolute;
  left: -1000em;
}
```

现在加上自己的图像就可以摆脱原来的复选框了，为此，要在初始的复选框后面加上[`<label>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label)元素，并使用它的[`:before`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:before)伪元素。因此在下面章节中，要使用[selector属性](https://developer.mozilla.org/en-US/docs/CSS/Attribute_selectors)来选择复选框，然后使用[adjacent sibling selector](https://developer.mozilla.org/en-US/docs/CSS/Adjacent_sibling_selectors)来选择原有复选框后面的`label`。最后，访问[`:before`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:before)伪元素来设计复选框显示定制样式。

```text
:root input[type=checkbox] + label:before {
  content: "";
  display: inline-block;
  width  : 16px;
  height : 16px;
  margin : 0 .5em 0 0;
  background: url("https://developer.mozilla.org/files/4173/checkbox-sprite.png") no-repeat 0 0;

/* The following is used to adjust the position of 
   the check boxes on the text baseline */

  vertical-align: bottom;
  position: relative;
  bottom: 2px;
}
```

在初始复选框上使用[`:checked`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:checked)和[`:disabled`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:disabled)伪类来改变定制复选框的状态。因为使用了CSS精灵，我们需要做的只是修改背景的位置。

```text
:root input[type=checkbox]:checked + label:before {
  background-position: 0 -16px;
}

:root input[type=checkbox]:disabled + label:before {
  background-position: 0 -32px;
}

:root input[type=checkbox]:checked:disabled + label:before {
  background-position: 0 -48px;
}
```

最后一件（但是很重要的）事情：当用户使用键盘从一个表单小部件导航到另一个表单小部件时，每个小部件都应该被显式聚焦。因为我们隐藏了初始的复选框，我们必须自己实现这个特性，让用户知道定制复选框在表单中的位置，下列的CSS实现了它们聚焦。

```text
:root input[type=checkbox]:focus + label:before {
  outline: 1px dotted black;
}
```

你可以在线查看结果：

#### Dealing with the select nightmare[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms#Dealing_with_the_select_nightmare) <a id="Dealing_with_the_select_nightmare"></a>

[`<select>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select) 元素被认为是一个 "丑陋的" 组件，因为不可能保证它在跨平台时样式化的一致性。然而，有些事情是可能的。废话少说，让我们来看一个例子：

```text
<select>
  <option>Cherry</option>
  <option>Banana</option>
  <option>Strawberry</option>
</select>
```

```text
select {
  width   : 80px;
  padding : 10px;
}

option {
  padding : 5px;
  color   : red;
}
```

下面的表格显示了在两种情况下不同浏览器的处理方式。头两列就是上面的例子。后面两列使用了其他的定制CSS，可以对小部件的外观进行更多的控制：

```text
select, option {
  -webkit-appearance : none; /* To gain control over the appearance on WebKit/Chromium */
  -moz-appearance : none; /* To gain control over the appearance on Gecko */

  /* To gain control over the appearance on and Trident (IE)
     Note that it also works on Gecko and has partial effects on WebKit */  
  background : none;
}
```

| Browser | Regular rendering | Tweaked rendering |  |  |
| :--- | :--- | :--- | :--- | :--- |
| closed | open | closed | open |  |
| Firefox 57 \(Mac OSX\) | ![](https://mdn.mozillademos.org/files/15672/firefox-mac-select-1-closed.png) | ![](https://mdn.mozillademos.org/files/15673/firefox-mac-select-1-open.png) | ![](https://mdn.mozillademos.org/files/15674/firefox-mac-select-2-closed.png) | ![](https://mdn.mozillademos.org/files/15675/firefox-mac-select-2-open.png) |
| Firefox 57 \(Windows 10\) | ![](https://mdn.mozillademos.org/files/15692/firefox-windows-select-1-closed.png) | ![](https://mdn.mozillademos.org/files/15693/firefox-windows-select-1-open.png) | ![](https://mdn.mozillademos.org/files/15694/firefox-windows-select-2-closed.png) | ![](https://mdn.mozillademos.org/files/15695/firefox-windows-select-2-open.png) |
| Chrome 63 \(Mac OSX\) | ![](https://mdn.mozillademos.org/files/15677/chrome-mac-select-1-closed.png) | ![](https://mdn.mozillademos.org/files/15678/chrome-mac-select-1-open.png) | ![](https://mdn.mozillademos.org/files/15684/chrome-windows-select-2-closed.png) | ![](https://mdn.mozillademos.org/files/15680/chrome-mac-select-2-open.png) |
| Chrome 63 \(Windows 10\) | ![](https://mdn.mozillademos.org/files/15682/chrome-windows-select-1-closed.png) | ![](https://mdn.mozillademos.org/files/15683/chrome-windows-select-1-open.png) | ![](https://mdn.mozillademos.org/files/15684/chrome-windows-select-2-closed.png) | ![](https://mdn.mozillademos.org/files/15685/chrome-windows-select-2-open.png) |
| Opera 49 \(Mac OSX\) | ![](https://mdn.mozillademos.org/files/15702/opera-mac-select-1-closed.png) | ![](https://mdn.mozillademos.org/files/15703/opera-mac-select-1-open.png) | ![](https://mdn.mozillademos.org/files/15704/opera-mac-select-2-closed.png) | ![](https://mdn.mozillademos.org/files/15705/opera-mac-select-2-open.png) |
| IE11 \(Windows 10\) | ![](https://mdn.mozillademos.org/files/15697/ie11-select-1-closed.png) | ![](https://mdn.mozillademos.org/files/15698/ie11-select-1-open.png) | ![](https://mdn.mozillademos.org/files/15699/ie11-select-2-closed.png) | ![](https://mdn.mozillademos.org/files/15700/ie11-select-2-open.png) |
| Edge 16 \(Windows 10\) | ![](https://mdn.mozillademos.org/files/15687/edge-select-1-closed.png) | ![](https://mdn.mozillademos.org/files/15688/edge-select-1-open.png) | ![](https://mdn.mozillademos.org/files/15689/edge-select-2-closed.png) | ![](https://mdn.mozillademos.org/files/15690/edge-select-2-open.png) |

如你所见，计时使用了`-*-appearance`属性的帮助，任然有一些遗留的问题：

* 不同的操作系统和浏览器对属性[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) 属性的处理各不相同。
* Internet Explorer旧版本不允许平滑样式
* Firefox没有实现下拉箭头的样式。
* 如果要在下拉列表内实现[`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option)元素样式，Chrome和Opera浏览器的表现在不同的系统中是不一样的。

在我们的例子中，只使用了三个CSS属性，在考虑使用更多CSS属性时，可以想象是很混乱的。正如我们看到的，CSS始终不适合用来修改这些小部件的外观，但是仍然可以用来稍微做一些事情。如果愿意的话，可以演示一下在不同操作系统和浏览器之间的区别。

我们也可以帮助了解在下一章节中哪个属性更合适：[Properties compatibility table for form widgets](https://developer.mozilla.org/en-US/docs/Properties_compatibility_table_for_forms_widgets)

### 走向更完美表单之路：有用的库和polyfills（腻子）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms#%E8%B5%B0%E5%90%91%E6%9B%B4%E5%AE%8C%E7%BE%8E%E8%A1%A8%E5%8D%95%E4%B9%8B%E8%B7%AF%EF%BC%9A%E6%9C%89%E7%94%A8%E7%9A%84%E5%BA%93%E5%92%8Cpolyfills%EF%BC%88%E8%85%BB%E5%AD%90%EF%BC%89) <a id="&#x8D70;&#x5411;&#x66F4;&#x5B8C;&#x7F8E;&#x8868;&#x5355;&#x4E4B;&#x8DEF;&#xFF1A;&#x6709;&#x7528;&#x7684;&#x5E93;&#x548C;polyfills&#xFF08;&#x817B;&#x5B50;&#xFF09;"></a>

虽然对于复选框和单选按钮而言，CSS的表示方式足够丰富，但是对更高级的小部件来说差距仍然很大。即使可以用[`<select>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select)元素作一些事情，但是对file小部件的样式完全没用。对于日期选择器也同样如此。

要实现对表单小部件的完全控制，你别无选择，只能选择依靠JavaScript。在文章[How to build custom form widgets](https://developer.mozilla.org/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets)中，我们将看到具体的做法，其中还有一些非常有用的库：

* [Uni-form](http://sprawsm.com/uni-form/)是一个对采用CSS样式的表单标记实现标准化的框架，在使用jQuery时，还提供一些附加特性，但这是可选的。
* [Formalize](http://formalize.me/)是对公共JavaScript框架的扩展（如jQuery, Dojo, YUI等），有助于规范和定制表单。
* [Niceforms](http://www.emblematiq.com/lab/niceforms/)是一个独立的JavaScript方法，能提供web表单的完整定制。

下面的库不止应用于表单，他们在处理HTML表单时是非常有趣的：

* [jQuery UI](http://jqueryui.com/)做了一些有趣的改进，可以定制象日期选择器（特别关注可访问性）这样的小部件。
* [Twitter Bootstrap](http://twitter.github.com/bootstrap/base-css.html#forms)在规范表单时是非常有用的。
* [WebShim](http://afarkas.github.com/webshim/demos/demos/webforms.html)是一个大型工具，可以用来处理浏览器对HTML5的支持。对web表单部分确实有用。

记住，使用CSS和JavaScript是有副作用的。所以在选择使用那些库时，应该在脚本失败的情况下能回滚样式表。脚本失败的原因很多，尤其在手机应用中，因此你需要尽可能好的设计你的Web站点或应用。

### 相关链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms#%E7%9B%B8%E5%85%B3%E9%93%BE%E6%8E%A5) <a id="&#x76F8;&#x5173;&#x94FE;&#x63A5;"></a>

虽然HTML表单使用CSS仍有一些黑洞，但通常也有方法绕过它们。即使没有清楚的，通用的解决方案，但新式的浏览器也提供了新的可能性。目前最好的方法是更多的学习不同浏览器支持CSS的方式，并应用于HTML表单小部件。

在本指南的下一章节中，我们将探讨不同的HTML表单小部件怎样很好的支持更重要的CSS属性：[Properties compatibility table for form widgets](https://developer.mozilla.org/en-US/docs/Properties_compatibility_table_for_forms_widgets).

### 相关链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms#%E7%9B%B8%E5%85%B3%E9%93%BE%E6%8E%A5_2) <a id="&#x76F8;&#x5173;&#x94FE;&#x63A5;_2"></a>

* [Dive into HTML5: Forms](http://diveintohtml5.info/forms.html)
* [Useful ideas and guidelines for good web form design](http://www.smashingmagazine.com/2011/06/27/useful-ideas-and-guidelines-for-good-web-form-design/)

