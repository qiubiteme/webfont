# 原生表单部件



现在，我们将详细研究不同表单部件的功能，查看了哪些选项可用于收集不同类型的数据。这个指南有些详尽，涵盖了所有可用的原生表单小部件。

| 预备知识: | 计算机基础知识和对于[HTML的基本理解](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)。 |
| :--- | :--- |
| 目标: | 要了解在浏览器中可以使用什么类型的原生表单小部件来收集数据，以及如何使用HTML实现它们。 |

这里我们将关注浏览器内置的表单部件，但是因为HTML表单仍然相当有限并且实现的特性在不同的浏览器中可能是相当不同的，web开发人员有时建立自己的表单部件——关于这个的更多想法，参见本模块后面的[如何构建自定义表单部件](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/How_to_build_custom_form_widgets)的更多的想法。

**译者注：**widget在本页面中被统一翻译为部件，但在其他地方可能也被译为组件。

**注意：**本文中讨论的大多数特性都在浏览器中得到了广泛的支持;我们会注意到这一点。如果您想要更准确的细节，您应该参考我们的[HTML表单元素参考](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#Forms)，特别是我们的广泛的 [&lt;input&gt;](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)类型参考。

### 通用属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E9%80%9A%E7%94%A8%E5%B1%9E%E6%80%A7) <a id="&#x901A;&#x7528;&#x5C5E;&#x6027;"></a>

大部分用来定义表单小部件的元素都有一些他们自己的属性。然而，在所有表单元素中都有一组属性，它们可以对这些小部件进行控制。下面是这些通用属性的列表:

| 属性名称 | 默认值 | 描述 |
| :--- | :--- | :--- |
| `autofocus` | \(_false_\) | 这个布尔属性允许您指定当页面加载时元素应该自动具有输入焦点，除非用户覆盖它，例如通过键入不同的控件。文档中只有一个与表单相关的元素可以指定这个属性。 |
| `disabled` | \(_false_\) | 这个布尔属性表示用户不能与元素交互。如果没有指定这个属性，元素将从包含的元素继承它的设置，例如[`<fieldset>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/fieldset);如果没有包含`disabled`属性集的元素，那么就启用了元素。 |
| `form` |  | 小部件与之相关联的表单元素。属性值必需是同个文档中的[`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form) 属性的 `id`属性。理论上，它允许您在[`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form)元素之外设置一个表单小部件。然而，在实践中，没有任何支持该特性的浏览器。 |
| `name` |  | 元素的名称;这是用于表单数据提交的。 |
| `value` |  | 元素的初始值。 |

### 文本输入域[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E6%96%87%E6%9C%AC%E8%BE%93%E5%85%A5%E5%9F%9F) <a id="&#x6587;&#x672C;&#x8F93;&#x5165;&#x57DF;"></a>

文本输入域 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 是最基本的表单小部件。 这是一种非常方便的方式，可以让用户输入任何类型的数据。但是，一些文本字段可以专门用于满足特定的需求。我们已经看到了几个简单的例子。

**注意**: HTML表单文本字段是简单的纯文本输入控件。 这意味着您不能使用它们执行[富文本编辑](https://developer.mozilla.org/en-US/docs/Rich-Text_Editing_in_Mozilla)\(粗体、斜体等\)。将遇到的所有富文本编辑器（rich text editors）都有使用HTML、CSS和JavaScript创建的自定义小部件。

所有文本域都有一些通用规范：

* 它们可以被标记为 [`readonly`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-readonly) \(用户不能修改输入值\)甚至是 [`disabled`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-disabled) \(输入值永远不会与表单数据的其余部分一起发送\)。
* 它们可以有一个 [`placeholder`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-placeholder); 这是文本输入框中出现的文本，用来简略描述输入框的目的。
* 它们可以被限制在[`size`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-size) \(框的物理尺寸\) 和 [长度](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Input#attr-maxlength) \(可以输入的最大字符数\)。
* 如果浏览器支持的话，他们可以从[拼写检查](https://developer.mozilla.org/en-US/docs/HTML/Element/input#attr-spellcheck)中获益。

**注意：**  [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素是如此特别因为它几乎可以是任何东西。通过简单设置 `type` 属性，它可以彻底改变，它用于创建大多数类型的表单小部件，包括单行文本字段、没有文本输入的控件、时间和日期控件和按钮。 然而，也有一些例外，比如用来多行输入的  [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)。阅读这篇文章时，要注意这些。

#### 单行文本域[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%8D%95%E8%A1%8C%E6%96%87%E6%9C%AC%E5%9F%9F) <a id="&#x5355;&#x884C;&#x6587;&#x672C;&#x57DF;"></a>

使用[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素创建一个单行文本域，该元素的[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性值被设置为`text` （同样的，如果你不提供[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性，`text` 是默认值）。如果你指定的[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性的值在浏览器中是未知的（比如你指定 `type="date"`，但是浏览器不支持原生日期选择器），属性值`text`就是是备用值。

**注意：** 你可以在Github上的 [single-line-text-fields.html](https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/single-line-text-fields.html)找到所有单行文本域类型。\(你也可以直接看[预览版](https://mdn.github.io/learning-area/html/forms/native-form-widgets/single-line-text-fields.html)\)。

这是一个基本的单行文本域示例：

```text
<input type="text" id="comment" name="comment" value="I'm a text field">
```

单行文本域只有一个真正的约束：如果您输入带有换行符的文本，浏览器会在发送数据之前删除这些换行符。

![Screenshots of single line text fields on several platforms.](https://developer.mozilla.org/files/4273/all-single-line-text-field.png)

HTML5通过为[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性增加特殊值增强了基本单行文本域。这些值仍然将[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素转换为单行文本域，但它们为域（字段）添加了一些额外的约束和特性。

**E-mail 地址域**

该类型的域设置为 [`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性的  `email` 值。

```text
<input type="email" id="email" name="email" multiple>
```

当使用 `type`时， 用户需要在域中输入有效的电子邮件地址；任何其他内容都会导致浏览器在提交表单时显示错误。注意，这是客户端错误验证，由浏览器执行：

![An invalid email input showing the message Please enter an email address.](https://mdn.mozillademos.org/files/14781/email-invalid.png)

通过包括[`multiple`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-multiple)属性，它还可以让用户将多个电子邮件地址输入相同的输入\(以逗号分隔\)。

在一些设备上\(特别是在移动设备上\)，可能会出现一个不同的虚拟键盘，更适合输入电子邮件地址。

**注意**: 您可以在[表单数据验证](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Form_validation)文中找到关于表单验证的更多信息。

**密码域**

通过[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type) 属性的`password`值设置该类型域：

```text
<input type="password" id="pwd" name="pwd">
```

它不会为输入的文本添加任何特殊的约束，但是它会模糊输入到字段中的值\(例如，用点或小行星\)，这样它就不能被其他人读取。

请记住，这只是一个用户界面特性;除非你安全地提交你的表单，否则它会以明文发送，这不利于安全——恶意的一方可能会截获你的数据，窃取你的密码、信用卡信息，或者你提交的其他任何东西。保护用户不受此影响的最佳方式是在安全连接上托管任何涉及表单的页面\(例如:https://……地址\)，使得数据在发送之前就已加密。

现代浏览器认识到在不安全的连接上发送表单数据所带来的安全影响，并且已经实现了警告，以阻止用户使用不安全的表单。有关Firefox实现的更多信息，请参见[不安全的密码](https://developer.mozilla.org/en-US/docs/Web/Security/Insecure_passwords)。

**搜索域**

通过使用 [`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性的 `search` 值设置该类型域：

```text
<input type="search" id="search" name="search">
```

文本域和搜索域之间的主要区别是浏览器的样式——通常，搜索字段以圆角和/或给定一个“x”来清除输入的值。然而，还有另外一个值得注意的特性:它们的值可以自动保存到同一站点上的多个页面上自动完成。

![Screenshots of search fields on several platforms.](https://developer.mozilla.org/files/4269/all-search-field.png)

**电话号码域：**

通过 [`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性的 `tel` 值设置该类型域：

```text
<input type="tel" id="tel" name="tel">
```

由于世界范围内各种各样的电话号码格式，这种类型的字段不会对用户输入的值执行任何限制\(包括字母，等等\)。这主要是语义上的差异，尽管在一些设备上\(特别是在移动设备上\)，可能会出现一个不同的虚拟键盘，更适合输入电话号码。

**URL 域**

通过[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性的`url` 值设置该类型域：

```text
<input type="url" id="url" name="url">
```

它为字段添加了特殊的验证约束，如果输入无效的url，浏览器就会报告错误。**注意：**URL格式良好，但并不一定意味着它引用了一个实际存在的位置。

**注意：**有特殊约束和错误的域可以防止表单被发送；此外，还可以将它们设置为使错误更清晰。我们将在[数据表单验证](https://developer.mozilla.org/en-US/docs/HTML/Forms/Data_form_validation)中详细讨论这个问题。

#### 多行文本域[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%A4%9A%E8%A1%8C%E6%96%87%E6%9C%AC%E5%9F%9F) <a id="&#x591A;&#x884C;&#x6587;&#x672C;&#x57DF;"></a>

多行文本域专指使用  [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)元素，而不是使用[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 元素。

```text
<textarea cols="30" rows="10"></textarea>
```

textarea和常规的单行文本字段之间的主要区别是，允许用户输入包含硬换行符\(即按回车\)的文本。

![Screenshots of multi-lines text fields on several platforms.](https://developer.mozilla.org/files/4271/all-multi-lines-text-field.png)

**注意：**你可以在Github上的[multi-line-text-field.html](https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/multi-line-text-field.html)看到本例（你也可以看[预览版](https://mdn.github.io/learning-area/html/forms/native-form-widgets/multi-line-text-field.html)）。注意到在大多数浏览器中，文本区域在右下角有一个拖放操作，允许用户调整它的大小。这种调整能力可以通过使用[CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS)设置文本区域的[`resize`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/resize)性质为 `none` 来关闭。

 [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea) 还接受了一些额外的属性，以控制它在几行代码中呈现的效果 \(除此以外还有其他几个\)：

 [**`<textarea>`**](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea) **元素属性**

| 属性名 | 默认值 | 描述 |
| :--- | :--- | :--- |
| [`cols`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea#attr-cols) | `20` | 文本控件的可见宽度，平均字符宽度。 |
| [`rows`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea#attr-rows) |  | 控制的可见文本行数。 |
| [`wrap`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea#attr-wrap) | `soft` | 表示控件是如何包装文本的。可能的值：`hard` 或 `soft` |

注意， [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)元素与[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素的编写略有不同。[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素是一个空元素，这意味着它不能包含任何子元素。另一方面， [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)元素是一个常规元素，可以包含文本内容的子元素。

这里有两个关键点需要注意：

* 如果您想为[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素定义一个默认值，那么您必须使用`value`属性;另一方面，对于 [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)元素，您将默认的文本放在起始标记和 [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)的结束标记之间。
* 因为它的本质，  [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)元素只接受文本内容；这意味着将任何HTML内容放入 [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)中都呈现为纯文本内容。

### 下拉内容[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E4%B8%8B%E6%8B%89%E5%86%85%E5%AE%B9) <a id="&#x4E0B;&#x62C9;&#x5185;&#x5BB9;"></a>

下拉窗口小部件是一种简单的方法，可以让用户选择众多选项中的一个，而不需要占用用户界面的太多空间。HTML有两种类型的下拉内容:**select box**和**autocomplete box**。在这两种情况下，交互都是相同的——一旦控件被激活，浏览器就会显示用户可以选择的值列表。

**注意：**你可以在Github上的[drop-down-content.html](https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/drop-down-content.html)看到本例（你也可以看[预览版](https://mdn.github.io/learning-area/html/forms/native-form-widgets/drop-down-content.html)）。

#### 选择框[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E9%80%89%E6%8B%A9%E6%A1%86) <a id="&#x9009;&#x62E9;&#x6846;"></a>

一个选择框是用[`<select>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select)元素创建的，其中有一个或多个[`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option)元素作为子元素，每个元素都指定了其中一个可能的值。

```text
<select id="simple" name="simple">
  <option>Banana</option>
  <option>Cherry</option>
  <option>Lemon</option>
</select>
```

如果需要，可以使用[`selected`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option#attr-selected)属性在所需的[`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option)元素上设置选择框的默认值，然后在页面加载时选择该选项。[`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option)元素也可以嵌套在[`<optgroup>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup)元素中，以创建视觉相关的组值：

```text
<select id="groups" name="groups">
  <optgroup label="fruits">
    <option>Banana</option>
    <option selected>Cherry</option>
    <option>Lemon</option>
  </optgroup>
  <optgroup label="vegetables">
    <option>Carrot</option>
    <option>Eggplant</option>
    <option>Potato</option>
  </optgroup>
</select>
```

![Screenshots of single line select box on several platforms.](https://developer.mozilla.org/files/4517/all-select.png)

如果一个[`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option)元素设置了`value`属性，那么当提交表单时该属性的值就会被发送。如果忽略了`value`属性，则使用[`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option)元素的内容作为选择框的值。

在[`<optgroup>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup)元素中，`label`属性显示在值之前，但即使它看起来有点像一个选项，它也不是可选的。

#### 多选选择框[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%A4%9A%E9%80%89%E9%80%89%E6%8B%A9%E6%A1%86) <a id="&#x591A;&#x9009;&#x9009;&#x62E9;&#x6846;"></a>

默认情况下，选择框只允许用户选择一个值。通过将[`multiple`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select#attr-multiple)属性添加到[`<select>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select)元素，您可以允许用户通过操作系统提供的默认机制来选择几个值。 \(如， 同时按下 Cmd/Ctrl 并点击多个值\).

注意：在多个选项选择框的情况下，选择框不再显示值为下拉内容——相反，它们都显示在一个列表中。

```text
<select multiple id="multi" name="multi">
  <option>Banana</option>
  <option>Cherry</option>
  <option>Lemon</option>
</select>
```

![Screenshots of multi-lines select box on several platforms.](https://developer.mozilla.org/files/4559/all-multi-lines-select.png)**注意：**所有支持 [`<select>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select) 元素的浏览器也支持 [`multiple`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select#attr-multiple) 。

#### 自动补全输入框[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E8%87%AA%E5%8A%A8%E8%A1%A5%E5%85%A8%E8%BE%93%E5%85%A5%E6%A1%86) <a id="&#x81EA;&#x52A8;&#x8865;&#x5168;&#x8F93;&#x5165;&#x6846;"></a>

您可以使用[`<datalist>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/datalist)元素来为表单小部件提供建议的、自动完成的值，并使用一些[`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option)子元素来指定要显示的值。

然后使用[`list`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-list)属性将数据列表绑定到一个文本域\(通常是一个 `<input>` 元素\)。

一旦数据列表与表单小部件相关联，它的选项用于自动完成用户输入的文本;通常，这是作为一个下拉框向用户展示的，在输入框中输入可能匹配的内容。

```text
<label for="myFruit">What's your favorite fruit?</label>
<input type="text" name="myFruit" id="myFruit" list="mySuggestion">
<datalist id="mySuggestion">
  <option>Apple</option>
  <option>Banana</option>
  <option>Blackberry</option>
  <option>Blueberry</option>
  <option>Lemon</option>
  <option>Lychee</option>
  <option>Peach</option>
  <option>Pear</option>
</datalist>
```

**注意：** 根据[HTML规范](http://www.w3.org/TR/html5/common-input-element-attributes.html#attr-input-list)，[`list`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-list) 属性和[`<datalist>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/datalist)元素元素可以用于任何需要用户输入的小部件。但是，除了文本\(例如颜色或日期\)，它应该如何工作还不清楚，不同的浏览器在不同的情况下会有不同的表现。正因为如此，除了文本字段以外，要小心使用这个特性。![Screenshots of datalist on several platforms.](https://developer.mozilla.org/files/4593/all-datalist.png) 

**数据列表支持和后备**

[`<datalist>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/datalist)元素是HTML表单的最新补充，因此浏览器的支持比我们之前看到的要少一些。最值得注意的是，它在10以下的IE版本中不受支持，Safari在写作时仍然不支持它。

为了处理这个问题，这里有一个小技巧，可以为这些浏览器提供一个不错的备用：

```text
<label for="myFruit">What is your favorite fruit? (With fallback)</label>
<input type="text" id="myFruit" name="fruit" list="fruitList">
    
<datalist id="fruitList">
  <label for="suggestion">or pick a fruit</label>
  <select id="suggestion" name="altFruit">
    <option>Apple</option>
    <option>Banana</option>
    <option>Blackberry</option>
    <option>Blueberry</option>
    <option>Lemon</option>
    <option>Lychee</option>
    <option>Peach</option>
    <option>Pear</option>
  </select>
</datalist>
```

支持[`<datalist>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/datalist)元素的浏览器将忽略所有不是[`<option>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option)元素的元素，并按照预期工作。另一方面，不支持[`<datalist>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/datalist)元素的浏览器将显示标签和选择框。当然，还有其他方法可以处理[`<datalist>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/datalist) 元素的不足，但这是最简单的\(其他方法往往需要JavaScript\)。

| Safari 6 | ![Screenshot of the datalist element fallback with Safari on Mac OS](https://developer.mozilla.org/files/4583/datalist-safari.png) |
| :--- | :--- |
| Firefox 18 | ![Screenshot of the datalist element with Firefox on Mac OS](https://developer.mozilla.org/files/4581/datalist-firefox-macos.png) |

### 可选中项[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%8F%AF%E9%80%89%E4%B8%AD%E9%A1%B9) <a id="&#x53EF;&#x9009;&#x4E2D;&#x9879;"></a>

可选中项是状态可以通过单击它们来更改小部件。有两种可选中项：复选框和单选按钮。两者都使用[`checked`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-checked)属性，以指示该部件是否在默认情况下进行检查。

值得注意的是，这些小部件与其他表单小部件不一样。对于大多数表单部件，一旦表单提交，所有具有[`name`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-name)属性的小部件都会被发送，即使没有任何值被填。对于可选中项，只有在勾选时才发送它们的值。如果他们没有被勾选，就不会发送任何东西，甚至连他们的名字也没有。

**注意**: 你可以在Github上看到 [checkable-items.html](https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/checkable-items.html) \(你也可以看[预览版](https://mdn.github.io/learning-area/html/forms/native-form-widgets/checkable-items.html)\)。

为了获得最大的可用性和可访问性，建议您在[`<fieldset>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/fieldset)中包围每个相关项目的列表，并使用[`<legend>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/legend)提供对列表的全面描述。每个单独的[`<label>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label)/[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素都应该包含在它自己的列表项中\(或者类似的\)。正如在示例中显示的。

您还需要为这些类型的输入提供`value`属性，如果您想让它们具有意义——如果没有提供任何值，则复选框和单选按钮被赋予一个 `on`值。

#### 复选框[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%A4%8D%E9%80%89%E6%A1%86) <a id="&#x590D;&#x9009;&#x6846;"></a>

使用[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性值为`checkbox`的 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素来创建一个复选框。

```text
<input type="checkbox" checked id="carrots" name="carrots" value="carrots">
```

包含`checked`属性使复选框在页面加载时自动被选中。

![Screenshots of check boxes on several platforms.](https://developer.mozilla.org/files/4595/all-checkbox.png)

#### 单选按钮[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%8D%95%E9%80%89%E6%8C%89%E9%92%AE) <a id="&#x5355;&#x9009;&#x6309;&#x94AE;"></a>

使用[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性值为`radio`的 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素来创建一个单选按钮。

```text
<input type="radio" checked id="soup" name="meal">
```

几个单选按钮可以连接在一起。如果它们的[`name`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-name)属性共享相同的值，那么它们将被认为属于同一组的按钮。同一组中只有一个按钮可以同时被选；这意味着当其中一个被选中时，所有其他的都将自动未选中。如果没有选中任何一个，那么整个单选按钮池就被认为处于未知状态，并且没有以表单的形式发送任何值。

```text
<fieldset>
  <legend>What is your favorite meal?</legend>
  <ul>
    <li>
      <label for="soup">Soup</label>
      <input type="radio" checked id="soup" name="meal" value="soup">
    </li>
    <li>
      <label for="curry">Curry</label>
      <input type="radio" id="curry" name="meal" value="curry">
    </li>
    <li>
      <label for="pizza">Pizza</label>
      <input type="radio" id="pizza" name="meal" value="pizza">
    </li>
  </ul>
</fieldset>
```

![Screenshots of radio buttons on several platforms.](https://developer.mozilla.org/files/4597/all-radio.png)

### 按钮[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E6%8C%89%E9%92%AE) <a id="&#x6309;&#x94AE;"></a>

在HTML表单中，有三种按钮：Submit将表单数据发送到服务器。Reset将所有表单小部件重新设置为它们的默认值。Button没有自动生效的按钮，但是可以使用JavaScript代码进行定制。如果您省略了`type`属性，那么这就是默认值。

**注意**: 你可以在Github上看到[button-examples.html](https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/button-examples.html) \(你也可以看[预览版](https://mdn.github.io/learning-area/html/forms/native-form-widgets/button-examples.html)\)。

使用  [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素或者[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素来创建一个按钮。[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性的值指定显示什么类型的按钮。

#### submit[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#submit) <a id="submit"></a>

```text
<button type="submit">
    This a <br><strong>submit button</strong>
</button>

<input type="submit" value="This is a submit button">
```

#### reset[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#reset) <a id="reset"></a>

```text
<button type="reset">
    This a <br><strong>reset button</strong>
</button>

<input type="reset" value="This is a reset button">
```

#### button[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#button) <a id="button"></a>

```text
<button type="button">
    This an <br><strong>anonymous button</strong>
</button>

<input type="button" value="This is an anonymous button">
```

不管您使用的是 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素还是[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素，按钮的行为都是一样的。然而，有一些显著的不同之处：

* 从示例中可以看到， [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素允许您在它们的标签中使用HTML内容，这些内容被插入到打开和关闭`<button>` 标签中。另一方面，[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素是空元素;它们的标签被插入到`value`属性中，因此只接受纯文本内容。
* 使用 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素，可以有一个不同于按钮标签的值\(通过将其设置为`value`属性\)。这在IE 8之前的版本中是不可靠的。

![Screenshots of buttons on several platforms.](https://developer.mozilla.org/files/4599/all-buttons.png)

从技术上讲，使用 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素或[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素定义的按钮几乎没有区别。唯一值得注意的区别是按钮本身的标签。在[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素中，标签只能是字符数据，而在 [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)元素中，标签可以是HTML，因此可以相应地进行样式化。

### 高级表单部件[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E9%AB%98%E7%BA%A7%E8%A1%A8%E5%8D%95%E9%83%A8%E4%BB%B6) <a id="&#x9AD8;&#x7EA7;&#x8868;&#x5355;&#x90E8;&#x4EF6;"></a>

在本节中，我们将介绍那些让用户输入复杂或不寻常数据的小部件。这包括精确的或近似的数字，日期和时间，或颜色。

**注意**: 你可以在Github上看到[advanced-examples.html](https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/advanced-examples.html) \(你也可以看[预览版](https://mdn.github.io/learning-area/html/forms/native-form-widgets/advanced-examples.html)\)。

#### 数字[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E6%95%B0%E5%AD%97) <a id="&#x6570;&#x5B57;"></a>

用于数字的小部件是用[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素创建的，它的[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性设置为`number`。这个控件看起来像一个文本域，但是只允许浮点数，并且通常提供一些按钮来增加或减少小部件的值。

也可以：

* 通过设置[`min`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-min)和[`max`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-max)属性来约束该值。
* 通过设置[`step`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-step)属性来指定增加和减少按钮更改小部件的值的数量。

**例子**

```text
<input type="number" name="age" id="age" min="1" max="10" step="2">
```

这将创建一个数字小部件，其值被限制为1到10之间的任何值，而其增加和减少按钮的值将更改为2。

在10以下的Internet Explorer版本中不支持`number` 输入。

#### 滑块[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E6%BB%91%E5%9D%97) <a id="&#x6ED1;&#x5757;"></a>

另一种选择数字的方法是使用滑块。从视觉上讲，滑块比文本字段更不准确，因此它们被用来选择一个确切值并不重要的数字。

滑块是通过把[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素的[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性值设置为`range`来创建的。正确配置滑块是很重要的；为了达到这个目的，我们强烈建议您设置[`min`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-min)、[`max`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-max)和[`step`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-step)属性。

**例子**

```text
<input type="range" name="beans" id="beans" min="0" max="500" step="10">
```

这个例子创建了一个滑块，它可能的值在0到500之间，而它的递增/递减按钮改变值的值是+10和-10。

滑块的一个问题是，它们不提供任何形式的视觉反馈，以了解当前的值是什么。您需要使用JavaScript来添加这一点，但这相对来说比较容易。在本例中，我们添加了一个空的[`<span>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/span)元素，其中我们将写入滑块的当前值，并在更改时更新它。

```text
<label for="beans">How many beans can you eat?</label>
<input type="range" name="beans" id="beans" min="0" max="500" step="10">
<span class="beancount"></span>
```

可以使用一些简单的JavaScript实现

```text
var beans = document.querySelector('#beans');
var count = document.querySelector('.beancount');

count.textContent = beans.value;

beans.oninput = function() {
  count.textContent = beans.value;
}
```

这里我们将对范围输入的引用和两个变量的span存储在这里，然后我们立即将span的[`textContent`](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)设置为输入的当前`value`。最后，我们设置了一个`oninput`事件处理程序，以便每次移动范围滑块时，都会将span `textContent`更新为新的输入值。

在10以下的Internet Explorer版本中不支持`range` 。

#### 日期时间选择器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E6%97%A5%E6%9C%9F%E6%97%B6%E9%97%B4%E9%80%89%E6%8B%A9%E5%99%A8) <a id="&#x65E5;&#x671F;&#x65F6;&#x95F4;&#x9009;&#x62E9;&#x5668;"></a>

对于web开发人员来说，收集日期和时间值一直是一场噩梦。HTML5通过提供一种特殊的控制来处理这种特殊的数据，从而带来了一些增强。

使用[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素和一个[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性的适当的值来创建日期和时间控制，这取决于您是否希望收集日期、时间或两者。

**本地时间**

这将创建一个小部件来显示和选择一个日期，但是没有任何特定的时区信息。

```text
<input type="datetime-local" name="datetime" id="datetime">
```

**月**

这就创建了一个小部件来显示和挑选一个月。

```text
<input type="month" name="month" id="month">
```

**时间**

这将创建一个小部件来显示并选择一个时间值。

```text
<input type="time" name="time" id="time">
```

**星期**

这将创建一个小部件来显示并挑选一个星期号和它的年份。

```text
<input type="week" name="week" id="week">
```

所有日期和时间控制都可以使用[`min`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-min)和[`max`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-max)属性来约束。

```text
<label for="myDate">When are you available this summer?</label>
<input type="date" name="myDate" min="2013-06-01" max="2013-08-31" id="myDate">
```

警告——日期和时间窗口小部件仍然很不受支持。目前，Chrome、Edge和Opera都支持它们，但IE浏览器没有支持，Firefox和Safari对这些都没有太大的支持。

#### 拾色器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E6%8B%BE%E8%89%B2%E5%99%A8) <a id="&#x62FE;&#x8272;&#x5668;"></a>

颜色总是有点难处理。有很多方式来表达它们:RGB值\(十进制或十六进制\)、HSL值、关键字等等。颜色小部件允许用户在文本和可视的方式中选择颜色。

一个颜色小部件是使用[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素创建的，它的[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性设置为值`color`。

```text
<input type="color" name="color" id="color">
```

警告——颜色小部件支持它目前不是很好。IE中没有支持，Safari目前也不支持它。其他主要的浏览器都支持它。

### 其他小部件[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%85%B6%E4%BB%96%E5%B0%8F%E9%83%A8%E4%BB%B6) <a id="&#x5176;&#x4ED6;&#x5C0F;&#x90E8;&#x4EF6;"></a>

还有一些其他的小部件由于它们非常特殊的行为而不能很容易地分类，但是它们仍然非常有用。

**注意**: 你可以在Github上看到[other-examples.html](https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/other-examples.html)\(你也可以看[预览版](https://mdn.github.io/learning-area/html/forms/native-form-widgets/other-examples.html)\)。

#### 文件选择器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E6%96%87%E4%BB%B6%E9%80%89%E6%8B%A9%E5%99%A8) <a id="&#x6587;&#x4EF6;&#x9009;&#x62E9;&#x5668;"></a>

HTML表单能够将文件发送到服务器；在[发送和检索表单数据](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data)的文章中详细描述了这个特定的操作。文件选择器小部件是用户如何选择一个或多个文件来发送的。

要创建一个文件选择器小部件，您可以使用[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素，它的[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性设置为`file`。被接受的文件类型可以使用[`accept`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-accept)属性来约束。此外，如果您想让用户选择多个文件，那么可以通过添加[`multiple`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-multiple)属性来实现。

**例子**

在本例中，创建一个文件选择器，请求图形图像文件。在本例中，允许用户选择多个文件。

```text
<input type="file" name="file" id="file" accept="image/*" multiple>
```

#### 隐藏内容[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E9%9A%90%E8%97%8F%E5%86%85%E5%AE%B9) <a id="&#x9690;&#x85CF;&#x5185;&#x5BB9;"></a>

有时候，由于技术原因，有些数据是用表单发送的，但不显示给用户，这有时是很方便的。要做到这一点，您可以在表单中添加一个不可见的元素。要做到这一点，需要使用[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)和它的[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性设置为`hidden`值。

如果您创建了这样一个元素，就需要设置它的`name`和`value`属性：

```text
<input type="hidden" id="timestamp" name="timestamp" value="1286705410">
```

#### 图像按钮[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%9B%BE%E5%83%8F%E6%8C%89%E9%92%AE) <a id="&#x56FE;&#x50CF;&#x6309;&#x94AE;"></a>

图像按钮控件是一个与[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)元素完全相同的元素，除了当用户点击它时，它的行为就像一个提交按钮\(见上面\)。

图像按钮是使用[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素创建的，该元素的[`type`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-type)属性设置为`image`值。这个元素支持与[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)元素相同的属性，加上其他表单按钮支持的所有属性。

```text
<input type="image" alt="Click me!" src="my-img.png" width="80" height="30" />
```

如果使用图像按钮来提交表单，这个小部件不会提交它的值；相反，在图像上单击的X和Y坐标是被提交的\(坐标是相对于图像的，这意味着图像的左上角表示坐标0，0\)，坐标被发送为两个键/值对：

* X值键是[`name`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-name)属性的值，后面是字符串“.x”。
* Y值键是[`name`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-name)属性的值，后面是字符串“.y”。

例如，当您点击这个小部件的图像时，您将被发送到一个URL，如下所显示的

```text
http://foo.com?pos.x=123&pos.y=456
```

这是构建“热图”的一种非常方便的方式。，如何发送和检索这些值在[发送和检索表单数据](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data)文章中详细说明。

#### 仪表和进度条[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E4%BB%AA%E8%A1%A8%E5%92%8C%E8%BF%9B%E5%BA%A6%E6%9D%A1) <a id="&#x4EEA;&#x8868;&#x548C;&#x8FDB;&#x5EA6;&#x6761;"></a>

仪表和进度条是数值的可视化表示。

**进度条**

一个进度条表示一个值，它会随着时间的变化而变化到最大的值，这个值由[`max`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/progress#attr-max)属性指定。这样的一个bar是使用[`<progress>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/progress)元素创建的。

```text
<progress max="100" value="75">75/100</progress>
```

这是为了实现任何需要进度报告的内容，例如下载的总文件的百分比，或者问卷中填写的问题的数量。

[`<progress>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/progress)元素中的内容是不支持该元素的浏览器的回退，以及辅助技术对其发出的声音。

**仪表**

一个仪表表示一个固定值，这个值由一个[`min`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-min)和一个[`max`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-max)值所定。这个值是作为一个条形显示的，并且为了知道这个工具条是什么样子的，我们将这个值与其他一些设置值进行比较

*  [`low`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-low) 和 [`high`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-high) 值范围划分为三个部分：
  * 该范围的较低部分是在[`min`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-min)和[`low`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-low)值\(包括那些值\)之间。
  * 该范围的中间部分是在[`low`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-low)和[`high`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-high)值之间\(不包括那些值\)。
  * 该范围的较高部分是在[`high`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-high)和[`max`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-max)值\(包括那些值\)之间。
* [`optimum`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-optimum)值定义了[`<meter>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter)元素的最优值。在与htmlattrxref\(“low”、“meter”\)和[`high`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-high)值的联合中，它定义了该范围的哪个部分是优先的：
  * 如果[`optimum`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-optimum)\)值在较低的范围内，则较低的范围被认为是首选项，中等范围被认为是平均值，而较高的范围被认为是最坏的部分。
  * 如果[`optimum`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter#attr-optimum)值在该范围的中等部分，则较低的范围被认为是一个平均值，中等范围被认为是优先的部分，而较高的范围也被认为是平均值。
  * 如果htmlattrxref\(“optimum”、“meter”\)值在较高的范围内，则较低的范围被认为是最坏的部分，中等范围被认为是一般的部分，较高的范围被认为是优先的部分。

所有实现[`<meter>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter)元素的浏览器都使用这些值来改变米尺的颜色。

* 如果当前值位于该范围的优先部分，则该条是绿色的。
* 如果当前值位于该范围的平均部分，则该条是黄色的。
* 如果当前值处于最糟糕的范围，则该条是红色的。

这样的一个工具栏是使用[`<meter>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter)元素创建的。这是用于实现任何类型的仪表，例如一个显示磁盘上使用的总空间的条，当它开始满时，它会变成红色。

```text
<meter min="0" max="100" value="75" low="33" high="66" optimum="50">75</meter>
```

[`<meter>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter)元素中的内容是不支持该元素的浏览器的回退，以及辅助技术对其发出的声音。

对进度条和仪表的支持是相当不错的，在Internet Explorer中没有支持，但是其他浏览器支持它。

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

正如您将在上面看到的，有许多不同类型的可用表单元素——您不需要一次性记住所有这些细节，并且可以在您喜欢查看详细信息的情况下返回到本文。

### 另见[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/The_native_form_widgets#%E5%8F%A6%E8%A7%81) <a id="&#x53E6;&#x89C1;"></a>

要深入了解不同的表单小部件，您需要了解一些有用的外部资源:

* [The Current State of HTML5 Forms](http://wufoo.com/html5/) by Wufoo
* [HTML5 Tests - inputs](http://www.quirksmode.org/html5/inputs.html) on Quirksmode \(also [available for mobile](http://www.quirksmode.org/html5/inputs_mobile.html) browsers\)

