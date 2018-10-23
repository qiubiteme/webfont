# 创建我的第一个表单

本系列的第一篇文章提供了您第一次创建HTML表单的经验，包括设计一个简单表单，使用正确的HTML元素实现它，通过CSS添加一些非常简单的样式，以及如何将数据发送到服务器。

| 预备知识： | 基本计算机素养和[对HTML的基本理解](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)。 |
| :--- | :--- |
| 目标： | 为了熟悉HTML表单是什么，它们被用来做什么，如何设计它们，以及简单情况下需要的基本HTML元素。 |

### HTML表单是什么？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#HTML%E8%A1%A8%E5%8D%95%E6%98%AF%E4%BB%80%E4%B9%88%EF%BC%9F) <a id="HTML&#x8868;&#x5355;&#x662F;&#x4EC0;&#x4E48;&#xFF1F;"></a>

HTML表单是用户和web站点或应用程序之间交互的主要内容之一。它们允许用户将数据发送到web站点。大多数情况下，数据被发送到web服务器，但是web页面也可以自己拦截它并使用它。

HTML表单是由一个或多个小部件组成的。这些小部件可以是文本字段\(单行或多行\)、选择框、按钮、复选框或单选按钮。大多数情况下，这些小部件与描述其目的的标签配对——正确实现的标签能够清楚地指示视力正常的用户和盲人用户输入表单输入的内容。

HTML表单和常规HTML文档的主要区别在于，大多数情况下，表单收集的数据被发送到web服务器。在这种情况下，您需要设置一个web服务器来接收和处理数据。如何设置这样的服务器超出了本文的范围，但是如果您想了解更多，请参阅模块后面的[发送表单数据](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data)。

### 设计表单[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#%E8%AE%BE%E8%AE%A1%E8%A1%A8%E5%8D%95) <a id="&#x8BBE;&#x8BA1;&#x8868;&#x5355;"></a>

在开始编写代码之前，最好先退一步，花点时间考虑一下您的表单。设计一个快速的模型将帮助您定义您想要询问用户的正确的数据集。从用户体验\(UX\)的角度来看，要记住：表单越大，失去用户的风险就越大。保持简单，保持专注:只要求必要的数据。在构建站点或应用程序时，设计表单是非常重要的一步。这超出了本文的范围，涵盖了表单的用户体验，但是如果您想深入了解这个主题，您应该阅读下面的文章:

* 粉碎杂志有[很好的关于表单用户体验的文章](http://uxdesign.smashingmagazine.com/tag/forms/)，但其中最重要的应该是他们的[Extensive Guide To Web Form Usability](http://uxdesign.smashingmagazine.com/2011/11/08/extensive-guide-web-form-usability/).
* UXMatters 也是一个非常有思想的资源，从基本的[最佳实践](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/%E4%B9%9F%E6%98%AF%E4%B8%80%E4%B8%AA%E9%9D%9E%E5%B8%B8%E6%9C%89%E6%80%9D%E6%83%B3%E7%9A%84%E8%B5%84%E6%BA%90%EF%BC%8C%E4%BB%8E%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5%E5%88%B0%E5%A4%8D%E6%9D%82%E7%9A%84%E9%97%AE%E9%A2%98%EF%BC%8C%E4%BE%8B%E5%A6%82%E5%A4%9A%E9%A1%B5%E8%A1%A8%E5%8D%95%EF%BC%8C%E9%83%BD%E6%9C%89%E5%BE%88%E5%A5%BD%E7%9A%84%E5%BB%BA%E8%AE%AE%E3%80%82)到复杂的问题如[多页表单](https://www.uxmatters.com/mt/archives/2010/03/pagination-in-web-forms-evaluating-the-effectiveness-of-web-forms.php)，都有很好的建议。

在本文中，我们将构建一个简单的联系人表单。让我们做一个粗略的草图。

![The form to build, roughly sketch](https://developer.mozilla.org/files/4579/form-sketch-low.jpg)

我们的表单将包含三个文本字段和一个按钮。我们向用户询问他们的姓名、电子邮件和他们想要发送的信息。点击这个按钮将把他们的数据发送到一个web服务器。

### 主动学习:实现我们的表单HTML[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%E5%AE%9E%E7%8E%B0%E6%88%91%E4%BB%AC%E7%9A%84%E8%A1%A8%E5%8D%95HTML) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#x5B9E;&#x73B0;&#x6211;&#x4EEC;&#x7684;&#x8868;&#x5355;HTML"></a>

好了，现在我们准备进入HTML代码并对表单进行编码。为了构建我们的联系人表单，我们将使用以下HTML元素:[`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form), [`<label>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label), [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input),  [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea), and  [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button).

在进一步讨论之前，先创建一个[简单HTML模板](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/getting-started/index.html)的本地副本—您将在这里输入您的表单HTML。

#### [`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form) 元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#%3Cform%3E_%E5%85%83%E7%B4%A0) <a id="&lt;form&gt;_&#x5143;&#x7D20;"></a>

所有HTML表单都以一个[`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form)元素开始：

```text
<form action="/my-handling-form-page" method="post">

</form>
```

这个元素正式定义了一个表单。就像 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div)元素或[`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p)元素，它是一个容器元素，但它也支持一些特定的属性来配置表单的行为方式。它的所有属性都是可选的，但至少要设置`action`属性和`method`属性，这被认为是最佳实践。

* `action` 属性定义了在提交表单时所收集的数据的位置\(URL\)。.
*  `method` 属性定义了发送数据的HTTP方法\(它可以是“get”或“post”\).

**注意:**如果您想深入了解这些属性是如何工作的，那么将在[发送表单数据](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data)文章中详细说明。

现在，将上面的[`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form) 元素添加到您的HTML主体中

#### [`<label>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label), [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 和  [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea) 元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#%3Clabel%3E_%3Cinput%3E_%E5%92%8C_%3Ctextarea%3E_%E5%85%83%E7%B4%A0) <a id="&lt;label&gt;_&lt;input&gt;_&#x548C;_&lt;textarea&gt;_&#x5143;&#x7D20;"></a>

我们的联系人表单非常简单，包含三个文本字段，每个字段都有一个标签。该名称的输入字段将是一个基本的单行文本字段，电子邮件的输入字段将是一个只接受电子邮件地址的单行文本字段，而消息的输入字段将是一个基本的多行文本字段。

就HTML代码而言，我们需要如下的东西来实现这些表单小部件：

```text
<form action="/my-handling-form-page" method="post">
    <div>
        <label for="name">Name:</label>
        <input type="text" id="name" />
    </div>
    <div>
        <label for="mail">E-mail:</label>
        <input type="email" id="mail" />
    </div>
    <div>
        <label for="msg">Message:</label>
        <textarea id="msg"></textarea>
    </div>
</form>
```

更新您的表单代码，使其看起来像上面的代码。

结果如下：

 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div) 元素可以方便地构造我们的代码，使样式更简单\(参见本文后面的文章\)。注意在所有[`<label>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label)元素上使用`for`属性；它是将标签链接到表单小部件的一种正式方式。这个属性引用相应的小部件的`id`。这样做有一些好处。最明显的一个好处是允许用户单击标签以激活相应的小部件。如果您想更好地理解这个属性的其他好处，您可以找到[如何构造HTML表单的详细信息](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/How_to_structure_an_HTML_form)。

在 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素中，最重要的属性是`type` 属性。这个属性非常重要，因为它定义了[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)属性的行为方式。它可以从根本上改变元素，所以要注意它。稍后您将在[原生表单挂件](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets)文章中找到更多关于此的内容。

* 在我们的简单示例中，我们使用值 `text` 作为第一个输入——这个属性的默认值。它表示一个基本的单行文本字段，接受任何类型的文本输入。
* 对于第二个输入，我们使用值`email`，它定义了一个只接受格式良好的电子邮件地址的单行文本字段。
* 最后一个值将一个基本的文本字段转换为一种“智能”字段，该字段将对用户输入的数据进行一些检查。在稍后的表单数据验证文章中，您将了解到[表单验证](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation)的更多信息。

最后但同样重要的是，要注意`<input />` 和 `<textarea></textarea>`的语法。这是HTML的一个奇怪之处。 `<input>` 标签是一个空元素，这意味着它不需要关闭标签。相反，  [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)不是一个空元素，因此必须使用适当的结束标记来关闭它。这对HTML表单的特定特性有影响:定义默认值的方式。要定义[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)的默认值，你必须使用`value` 属性，如下所示：

```text
<input type="text" value="by default this element is filled with this text" />
```

相反，如果您想定义 [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)的默认值，您只需在 [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)元素的开始和结束标记之间放置默认值，就像这样:

```text
<textarea>by default this element is filled with this text</textarea>
```

####  [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button) 元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#%3Cbutton%3E_%E5%85%83%E7%B4%A0) <a id="&lt;button&gt;_&#x5143;&#x7D20;"></a>

我们的表格已经快准备好了，我们只需要再添加一个按钮，让用户在填写完表单后发送他们的数据。这是通过使用  [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button) 元素完成的。在 `</form>`标签上添加以下内容：

```text
<div class="button">
<button type="submit">Send your message</button>
</div>
```

您将看到 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素也接受一个 `type`属性，它接受三个值中的一个:`submit`, `reset`或者 `button`。

* 单击 `submit` 按钮 发送表单的数据到[`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form)元素的`action` 属性所定义的网页。
* 单击 `reset` 按钮 将所有表单小部件重新设置为它们的默认值。从用户体验的角度来看，这被认为是一种糟糕的做法。
* 单击`button` 按钮……不会发生任何事！这听起来很傻，但是用JavaScript构建定制按钮非常有用。 

**注意：**您还可以使用相应类型的 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素来生成一个按钮，如 `<input type="submit">`。 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素的主要优点是， [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素只允许纯文本作为其标签，而 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素允许完整的HTML内容，允许更复杂、更有创意的按钮文本。

### 基本表单样式[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#%E5%9F%BA%E6%9C%AC%E8%A1%A8%E5%8D%95%E6%A0%B7%E5%BC%8F) <a id="&#x57FA;&#x672C;&#x8868;&#x5355;&#x6837;&#x5F0F;"></a>

现在您已经完成了表单的HTML代码，尝试保存它并在浏览器中查看它。  
现在，你会看到它看起来很丑。

![](https://developer.mozilla.org/files/4049/form-no-style.png)

**注意：** 如果你怀疑你的HTML代码不对，试着把它和我们完成的例子进行比较 —— [first-form.html](https://github.com/mdn/learning-area/blob/master/html/forms/your-first-HTML-form/first-form.html) \(你也可以观看[预览版](https://mdn.github.io/learning-area/html/forms/your-first-HTML-form/first-form.html)\)。

如何排布好表单是公认的难点。这超出了本文的讨论范围，所以现在我们只需要让您添加一些CSS来让它看起来很好。

首先，在您的HTML头部中添加一个 [`<style>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/style)元素。应该是这样的：

```text
<style>

</style>
```

在样式标签中，添加如下的CSS，如下所示:

```text
form {
  /* 居中表单 */
  margin: 0 auto;
  width: 400px;
  /* 显示表单的轮廓 */
  padding: 1em;
  border: 1px solid #CCC;
  border-radius: 1em;
}

form div + div {
  margin-top: 1em;
}

label {
  /* 确保所有label大小相同并正确对齐 */
  display: inline-block;
  width: 90px;
  text-align: right;
}

input, textarea {
  /* 确保所有文本输入框字体相同
     textarea默认是等宽字体 */
  font: 1em sans-serif;

  /* 使所有文本输入框大小相同 */
  width: 300px;
  box-sizing: border-box;

  /* 调整文本输入框的边框样式 */
  border: 1px solid #999;
}

input:focus, textarea:focus {
  /* 给激活的元素一点高亮效果 */
  border-color: #000;
}

textarea {
  /* 使多行文本输入框和它们的label正确对齐 */
  vertical-align: top;

  /* 给文本留下足够的空间 */
  height: 5em;
}

.button {
  /* 把按钮放到和文本输入框一样的位置 */
  padding-left: 90px; /* 和label的大小一样 */
}

button {
  /* 这个外边距的大小与label和文本输入框之间的间距差不多 */
  margin-left: .5em;
}
```

现在，它看起来没那么丑了。

![](https://developer.mozilla.org/files/4051/form-style.png)

**注意**: 你可以在GitHub上的这里找到它 [first-form-styled.html](https://github.com/mdn/learning-area/blob/master/html/forms/your-first-HTML-form/first-form-styled.html) \([也可以在这儿看运行结果](https://mdn.github.io/learning-area/html/forms/your-first-HTML-form/first-form-styled.html)\).

### 向您的web服务器发送表单数据[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#%E5%90%91%E6%82%A8%E7%9A%84web%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%8F%91%E9%80%81%E8%A1%A8%E5%8D%95%E6%95%B0%E6%8D%AE) <a id="&#x5411;&#x60A8;&#x7684;web&#x670D;&#x52A1;&#x5668;&#x53D1;&#x9001;&#x8868;&#x5355;&#x6570;&#x636E;"></a>

最后一部分，也许是最棘手的部分，是在服务器端处理表单数据。如前所述，大多数时候HTML表单是向用户请求数据并将其发送到web服务器的一种方便的方式。

[`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form) 元素将定义如何通过`action` 属性和 `method`属性来发送数据的位置和方式。

但这还不够。我们还需要为我们的数据提供一个名称。这些名字对双方都很重要：在浏览器端，它告诉浏览器哪个名称提供每个数据，在服务器端，它允许服务器按名称处理每个数据块。

要将数据命名为表单，您需要在每个表单小部件上使用 `name` 属性来收集特定的数据块。让我们再来看看我们的表单代码:

```text
<form action="/my-handling-form-page" method="post"> 
  <div>
    <label for="name">Name:</label>
    <input type="text" id="name" name="user_name" />
  </div>
  <div>
    <label for="mail">E-mail:</label>
    <input type="email" id="mail" name="user_email" />
  </div>
  <div>
    <label for="msg">Message:</label>
    <textarea id="msg" name="user_message"></textarea>
  </div>

  ...
```

在我们的例子中，表单会发送三个已命名的数据块 "`user_name`", "`user_email`", 和 "`user_message`"。这些数据将用使用[HTTP `POST`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST) 方法,把信息发送到URL为 "`/my-handling-form-page`"目录下。

在服务器端，位于URL"`/my-handling-form-page`" 上的脚本将接收的数据作为HTTP请求中包含的3个键/值项的列表。这个脚本处理这些数据的方式取决于您。每个服务器端语言\(PHP、Python、Ruby、Java、c等等\)都有自己的机制。深入到这个主题已经超出了本指南的范围，但是如果您想了解更多，我们已经在[发送表单数据](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data)文章中提供了一些示例。 

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Your_first_HTML_form#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

祝贺您，您已经构建了您的第一个HTML表单。它看起来就像这样:

在 CodePen 中打开在 JSFiddle 中打开

然而，这仅仅是开始，现在是时候深入研究了。HTML表单比我们在这里看到的要强大得多，本指南的其他文章将帮助您掌握其余部分。

