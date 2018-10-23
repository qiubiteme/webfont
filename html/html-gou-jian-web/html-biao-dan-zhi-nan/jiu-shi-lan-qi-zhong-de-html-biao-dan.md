# 旧式浏览器中的HTML 表单

所有 web 开发者很快就会（有时候是痛苦地）发现网络是一个令人不快的地方。我们碰到的最恶毒的诅咒是旧式浏览器。好吧，让我们承认吧，当我们提到 “旧式浏览器” 时，脑海中出现就是 老版本的 Internet Explorer ……但是，这远远不是全部。只发布一年的 Firefox 比如 [the ESR version](http://www.mozilla.org/en-US/firefox/organizations/) 也是旧式浏览器。那么，在移动世界呢？当浏览器和 OS（操作系统） 都不能更新时？是的，有非常多老版本的 Android 手机或 iPhone 没有更新到最新的浏览器。它们同样是旧式浏览器。

可悲的是，处理这些传统浏览器的问题是工作的一部分。幸运的是，有一些技巧可以帮助您解决旧式浏览器导致的大约80％的问题。

### 了解这些问题[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E4%BA%86%E8%A7%A3%E8%BF%99%E4%BA%9B%E9%97%AE%E9%A2%98) <a id="&#x4E86;&#x89E3;&#x8FD9;&#x4E9B;&#x95EE;&#x9898;"></a>

实际上，最重要的事情是阅读那些浏览器的文档，并尝试理解通用的（解决）模式。例如，在许多情况下，HTML表单是否支持CSS是最大的问题。这是正确的开始，只需要检查你想用的元素或接口是否支持CSS即可。MDN有一个关于包含HTML中可用的元素、属性或API的兼容表单可查。 此外，仍有其他一些非常有用的资源：

#### 浏览器厂商的文档[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E6%B5%8F%E8%A7%88%E5%99%A8%E5%8E%82%E5%95%86%E7%9A%84%E6%96%87%E6%A1%A3) <a id="&#x6D4F;&#x89C8;&#x5668;&#x5382;&#x5546;&#x7684;&#x6587;&#x6863;"></a>

* Mozilla: 直接查看MDN即可
* Microsoft: [Internet Explorer Standards Support Documentation](http://msdn.microsoft.com/en-us/library/ff410218%28v=vs.85%29.aspx)
* WebKit: 由于有多个版本的引擎，稍微有点棘手.
  * [The WebKit blog](https://www.webkit.org/blog/) 和 [Planet WebKit](http://planet.webkit.org/) 聚合了Webki核心开发者的最佳文章.
  * [Chrome platform status site](https://www.chromestatus.com/features) 也十分重要
  * 同样重要的是 [the Apple web site.](https://developer.apple.com/technologies/safari/)

#### 独立文档[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E7%8B%AC%E7%AB%8B%E6%96%87%E6%A1%A3) <a id="&#x72EC;&#x7ACB;&#x6587;&#x6863;"></a>

* [Can I Use](http://caniuse.com/) 有关于是否支持最新技术的信息.
* [Quirks Mode](http://www.quirksmode.org/) 是关于浏览器兼容性的精彩资源. [mobile部分](http://www.quirksmode.org/mobile/)是当前最好的内容之一.
* [Position Is Everything](http://positioniseverything.net/) 关于旧式浏览器渲染bug以及解决办法（如果有）的最佳资源.
* [Mobile HTML5](http://mobilehtml5.org/) 有关于大量手机浏览器的兼容性信息，而不仅仅是是前五名（包括诺基亚，亚马逊和黑莓）.

### 让事情变得更简单[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E8%AE%A9%E4%BA%8B%E6%83%85%E5%8F%98%E5%BE%97%E6%9B%B4%E7%AE%80%E5%8D%95) <a id="&#x8BA9;&#x4E8B;&#x60C5;&#x53D8;&#x5F97;&#x66F4;&#x7B80;&#x5355;"></a>

由于[HTML forms](https://developer.mozilla.org/en-US/docs/HTML/Forms) 包含复杂的交互，所以有一条法则: [keep it as simple as possible](http://en.wikipedia.org/wiki/KISS_principle)。很多时候，我们想让表单更美观或想使用更高级的技术，然而，构建高效的HTML表单不只是设计和技术问题。记得花时间读一下这篇文章t [forms usability on UX For The Masses](http://www.uxforthemasses.com/forms-usability/).

#### 优雅地降级\(Graceful degradation\)是web开发者最好的朋友[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E4%BC%98%E9%9B%85%E5%9C%B0%E9%99%8D%E7%BA%A7%28Graceful_degradation%29%E6%98%AFweb%E5%BC%80%E5%8F%91%E8%80%85%E6%9C%80%E5%A5%BD%E7%9A%84%E6%9C%8B%E5%8F%8B) <a id="&#x4F18;&#x96C5;&#x5730;&#x964D;&#x7EA7;(Graceful_degradation)&#x662F;web&#x5F00;&#x53D1;&#x8005;&#x6700;&#x597D;&#x7684;&#x670B;&#x53CB;"></a>

[Graceful degradation and progressive enhancement](http://www.sitepoint.com/progressive-enhancement-graceful-degradation-choice/) 是一个开发模式，它允许你通过同时支持多种浏览器来构建优秀内容。当你为现代浏览器构建内容时，你想确保它能在旧式浏览器中以某种方式工作，这就是优雅地降级（graceful degradation）.

让我们看一些关于HTML表单的例子：

**HTML input 类型**

HTML5引入的新input类型十分酷，因为他们的降级\(degrade\)是高度可预测的。如果一个浏览器不能理解  [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素的 [`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type) 属性, 它将会后退到`text`一样的行为。

```text
<label for="myColor">
  Pick a color
  <input type="color" id="myColor" name="color">
</label>
```

| Chrome 24 | Firefox 18 |
| :--- | :--- |
| ![Screen shot of the color input on Chrome for Mac OSX](https://developer.mozilla.org/files/4575/color-fallback-chrome.png) | ![Screen shot of the color input on Firefox for Mac OSX](https://developer.mozilla.org/files/4577/color-fallback-firefox.png) |

**CSS 属性选择器**

[CSS属性选择器 ](https://developer.mozilla.org/en-US/docs/CSS/Attribute_selectors) 在 [HTML Forms](https://developer.mozilla.org/en-US/docs/HTML/Forms) 中十分有用，然而旧式浏览器不支持. 在那种情形下，一般会习惯性使用等价的class:

```text
<input type="number" class="number">
```

```text
input[type=number] {
  /* 这在一些浏览器中是不能执行的 */
}

input.number {
  /* 可以在任何浏览器中执行 */
}
```

注意下面的写法没有用（由于它是重复的），在某些浏览器中会失败:

```text
input[type=number],
input.number {
  /* 在某些浏览器中，这可能会失败，因为如果他们不理解其中任何一个选择器，则跳过整个规则 */
}
```

**表单按钮**

有两种定义HTML表单按钮的方式:

* [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 元素使用[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type) 属性并设置其值为`button`, `submit`, `reset` or `image`
*  [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button) 元素

如果你想通过元素选择器在按钮上应用CSS的话，采用 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 元素的方式会让事情变得稍微有点复杂:

```text
<input type="button" class="button" value="click me">
```

```text
input {
  /* 此规则关闭了input元素定义的按钮的默认渲染样式 */
  border: 1px solid #CCC;
}

input.button {
  /* 这条规则不会恢复默认渲染*/
  border: none;
}

input.button {
  /* 这条也不会(恢复)! 实际上在浏览器中没有标准方式实现这一目标 */
  border: auto;
}
```

 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button) 元素有两个问题令人困扰:

* 在某些旧版本的IE浏览器中有bug。当用户点击按钮时，它不是发送[`value`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button#attr-value)属性中的内容，而是发送[`value`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button#attr-value)开闭和标签内的HTML内容\(译者注：可能是按钮的名字\). 如果我们想发送值时，这是一个问题，例如发送的处理数据依赖于用户点击不同的按钮时.
* 一些旧浏览器不使用`submit` 作为 [`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button#attr-type) 属性的默认值, 所以建议总是在 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button) 元素上设置设置 [`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button#attr-type) 属性.

```text
<!-- 某些情形下，点击按钮将发送 "<em>Do A</em>" 而不是值"A" -->
<button type="submit" name="IWantTo" value="A">
  <em>Do A</em>
</button>
```

给予你的工程限制来选择上述任一种解决方案。

#### 让我们过一遍CSS[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E8%AE%A9%E6%88%91%E4%BB%AC%E8%BF%87%E4%B8%80%E9%81%8DCSS) <a id="&#x8BA9;&#x6211;&#x4EEC;&#x8FC7;&#x4E00;&#x904D;CSS"></a>

HTML表单和旧式浏览器最大的问题是CSS的兼容性。正如你可以从这篇文章 [Property compatibility table for form widgets](https://developer.mozilla.org/en-US/docs/Property_compatibility_table_for_form_widgets) 中看到的复杂性, 它非常的困难。即使仍然可以对文本元素（如大小、字体颜色等）进行一些调整，但那样做会有副作用。最好的办法还是不要美化HTML表单小组件。但你仍然可以将样式应用到表单周围的项目上。如果你是一个专业人士，并且你的客户需要那么做，在这种情况下，你可以研究一些硬件技术，如 [rebuilding widgets with JavaScript](https://developer.mozilla.org/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets)。但在那种情况下，最好还是毫不犹豫的[让客户收回这些愚蠢的决定](http://www.smashingmagazine.com/2011/11/03/%E2%80%9Cbut-the-client-wants-ie-6-support%E2%80%9D/)。

### 功能检测和模拟\(polyfills\)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E5%8A%9F%E8%83%BD%E6%A3%80%E6%B5%8B%E5%92%8C%E6%A8%A1%E6%8B%9F%28polyfills%29) <a id="&#x529F;&#x80FD;&#x68C0;&#x6D4B;&#x548C;&#x6A21;&#x62DF;(polyfills)"></a>

尽管JavaScript在现代浏览中是非常棒的技术，但在旧式浏览器中可能存在很多的问题。

#### Unobtrusive JavaScript[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#Unobtrusive_JavaScript) <a id="Unobtrusive_JavaScript"></a>

API的兼容性是最大的问题。由于这个原因，与"不引人注意的（unobtrusive）" JavaScript一起工作被认为是最佳实践（译者注：此处意思是说没有/忽略JS或JS出了问题也能工作）。这个开发模式定义了两个需求：

* 结构和行为之间的严格隔离
* 如果代码出错，内容和基本功能必须保持可访问和可用状态

[The principles of unobtrusive JavaScript](http://docs.webplatform.org/wiki/concepts/programming/the_principles_of_unobtrusive_javascript) \(最早是由Peter-Paul Koch为 Dev.Opera.com 所撰写，现在已转移到 Docs.WebPlatform.org\) 同样阐述了上述观点。

#### Modernizr 库[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#Modernizr_%E5%BA%93) <a id="Modernizr_&#x5E93;"></a>

有很多情形，好的"polyfill"能通过提供缺少的API以提供帮助。一个 [polyfill](http://remysharp.com/2010/10/08/what-is-a-polyfill/) 是一些JavaScript\(脚本\) 用于填补旧式浏览器中的功能缺失。虽然它们可以用来改进对任何功能的支持，并且使用它们Nederland风险小于CSS和HTML，然而，JS仍然会在很多情况下不工作（网络问题，脚本冲突等）。但是对于JavaScript，如果你总是记住和unobetructive的Javascript一起工作，不适用polyfill也没什么大不了。

最好的polyfill缺失API的方式是使用[Modernizr](http://modernizr.com/) 库以及它的子项目 [YepNope](http://yepnopejs.com/). Modernizr 库允许您测试功能可用性，以便采取相应的行动。YepNope 是一个条件加载库。

下面是一个例子:

```text
Modernizr.load({
  // 这会测试您的浏览器是否支持HTML5表单验证API
  test : Modernizr.formvalidation,
 
  // 如果浏览器不支持它，则会加载以下polyfill
  nope : form-validation-API-polyfill.js,
 
  // 无论如何，你的核心App文件依赖于该API被加载
  both : app.js,
 
  // 一旦加载了这两个文件，就会调用该函数来初始化应用程序
  complete : function () {
    app.init();
  }
});
```

Modernizr 团队按照惯例维护着[a list of great polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills)。仅仅按需使用即可。

**Note:** Modernizr还有其他很棒的功能可以帮助您处理unobstructive的JavaScript和优雅的降级技术。请阅读 [Modernizr documentation](http://modernizr.com/docs/).

#### 注意性能[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E6%B3%A8%E6%84%8F%E6%80%A7%E8%83%BD) <a id="&#x6CE8;&#x610F;&#x6027;&#x80FD;"></a>

尽管像Modernizr这样的脚本对性能非常敏感，但加载200千字节的polyfill仍然会影响程序的性能。这对旧式浏览器来说尤其重要，这些浏览器有处理速度非常慢的JavaScript引擎，让polyfills的执行对于用户来说变得很痛苦。性能本身就是一个主题，但旧式浏览器对它非常敏感：基本上，它们速度慢，需要的poliyfill越多，它们需要处理的JavaScript越多。与现代浏览器相比，它们承受双重负担。使用旧版浏览器测试你的代码，了解它们的实际表现。有时，放弃某些功能会带来更好的用户体验，而不是在所有浏览器中具有完全相同的功能。作为最后提醒，总是优先考虑用户。

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

正如你所看到的，处理旧式浏览器不仅仅是表单问题。而是一整套技术;但是掌握所有这些技术超出了本文的范围。

如果你阅读了[HTML Forms guide](https://developer.mozilla.org/en-US/docs/HTML/Forms)中的所有文章，你应该可以放心的使用表单了。如果你想探索新技术，请帮助[improve the guide](https://developer.mozilla.org/en-US/docs/Project:How_to_help).

