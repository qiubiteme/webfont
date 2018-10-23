# HTML表单指南



这个模块提供了一系列帮助您掌握HTML表单的文章。HTML表单是与用户交互的强大工具;然而，由于历史和技术上的原因，如何充分发挥它们的潜力并不总是显而易见的。在本指南中，我们将介绍HTML表单的所有方面，从结构到样式，从数据处理到自定义小部件。

### 预备知识[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms#%E9%A2%84%E5%A4%87%E7%9F%A5%E8%AF%86) <a id="&#x9884;&#x5907;&#x77E5;&#x8BC6;"></a>

在开始这个模块之前，您至少应该完成我们[对HTML的介绍](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)。此时此刻，您应该会发现[基本指南](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms#%E5%9F%BA%E6%9C%AC%E6%8C%87%E5%8D%97)很容易理解，并且能够使用我们的[原生表单小部件](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets)指南。

但是模块的其余部分更高级一些，很容易将表单小部件放在页面上，但是如果不使用高级表单特性、CSS和JavaScript，就不能对它们做太多的工作。因此，在您查看其他部分之前，我们建议您先离开，先学习一些[CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS)和[JavaScript](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript)。

**注意：**如果您正在使用一个不能让您创建自己的文件的计算机/平板电脑/其它设备，那么您可以尝试\(大多数\)在线编码程序中的代码示例，例如[JSBin](http://jsbin.com/)或[Thimble](https://thimble.mozilla.org/)。

### 基本指南[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms#%E5%9F%BA%E6%9C%AC%E6%8C%87%E5%8D%97) <a id="&#x57FA;&#x672C;&#x6307;&#x5357;"></a>

[你的第一个HTML表单](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form)本系列的第一篇文章提供了您第一次创建HTML表单的经验，包括设计一个简单表单，使用正确的HTML元素实现它，通过CSS添加一些非常简单的样式，以及如何将数据发送到服务器。[如何构造HTML表单](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/How_to_structure_an_HTML_form)有了基础知识，我们现在更详细地了解了用于为表单的不同部分提供结构和意义的元素。

### 什么表单小部件可用?[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms#%E4%BB%80%E4%B9%88%E8%A1%A8%E5%8D%95%E5%B0%8F%E9%83%A8%E4%BB%B6%E5%8F%AF%E7%94%A8) <a id="&#x4EC0;&#x4E48;&#x8868;&#x5355;&#x5C0F;&#x90E8;&#x4EF6;&#x53EF;&#x7528;"></a>

[原生表单小部件](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets)现在，我们详细研究了不同表单部件的功能，查看了哪些选项可用于收集不同类型的数据。

### 验证和提交表单数据[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms#%E9%AA%8C%E8%AF%81%E5%92%8C%E6%8F%90%E4%BA%A4%E8%A1%A8%E5%8D%95%E6%95%B0%E6%8D%AE) <a id="&#x9A8C;&#x8BC1;&#x548C;&#x63D0;&#x4EA4;&#x8868;&#x5355;&#x6570;&#x636E;"></a>

[发送表单数据](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data)本文讨论当用户提交一个表单时，当用户提交一个表单时，会发生什么情况，当用户提交表单时，我们该如何处理?我们还研究了与发送表单数据相关的一些安全问题。[表单数据验证](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Form_validation)发送数据还不够，我们还需要确保数据用户填写表单的格式是正确的，我们需要成功地处理它，而且它不会破坏我们的应用程序。我们还希望帮助用户正确填写表单，在使用应用程序时不要感到沮丧。表单验证帮助我们实现这些目标，本文将告诉您需要了解的内容。

### 高级指南[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms#%E9%AB%98%E7%BA%A7%E6%8C%87%E5%8D%97) <a id="&#x9AD8;&#x7EA7;&#x6307;&#x5357;"></a>

[如何构建自定表单小组件](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/How_to_build_custom_form_widgets)在某些情况下，原生表单部件无法提供您需要的东西，例如，由于样式或功能。在这种情况下，您可能需要使用原生HTML构建自己的表单小部件。本文将说明您是如何做到这一点的，以及在实际案例研究中需要注意的事项。[通过JavaScript发送表单](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript)本文将讨论如何使用表单来组装HTTP请求，并通过定制的JavaScript发送它，而不是标准的表单提交。它还研究了为什么要这么做，以及这样做的意义。（请参阅使用FormData对象。）[遗留浏览器中的HTML表单](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers)文章覆盖特性检测等。这应该被重定向到跨浏览器测试模块，因为相同的东西在那里被更好地覆盖。

### 表单样式指南[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms#%E8%A1%A8%E5%8D%95%E6%A0%B7%E5%BC%8F%E6%8C%87%E5%8D%97) <a id="&#x8868;&#x5355;&#x6837;&#x5F0F;&#x6307;&#x5357;"></a>

[HTML表单样式](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Styling_HTML_forms)本文介绍了使用CSS的样式表单，包括您可能需要了解的基本样式任务的所有基础知识。[高级HTML表单样式](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms)在这里，我们将看到一些更高级的表单样式技术，这些技术需要在处理一些更难以风格的元素时使用。[表单部件的属性兼容性表](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets)这最后一篇文章提供了一个方便的参考，允许您查看哪些CSS属性与哪些表单元素是兼容的。

### 另见[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms#%E5%8F%A6%E8%A7%81) <a id="&#x53E6;&#x89C1;"></a>

* [HTML forms element reference](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element#Forms)
* [HTML &lt;input&gt; types reference](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)

