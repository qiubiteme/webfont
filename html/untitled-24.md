# 表单数据校验



表单验证帮助我们确保用户以正确格式填写表单数据，确保提交的数据能使我们的应用程序正常工作。本文将告诉您需要了解的有关表单验证的内容。

| 预备知识： | 计算机基础能力，对 [HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML)、[CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS) 和 [JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript) 有一定的理解。 |
| :--- | :--- |
| 目标： | 理解表单验证是什么，为什么它很重要，以及如何实现它。 |

### 什么是表单数据校验？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E4%BB%80%E4%B9%88%E6%98%AF%E8%A1%A8%E5%8D%95%E6%95%B0%E6%8D%AE%E6%A0%A1%E9%AA%8C%EF%BC%9F) <a id="&#x4EC0;&#x4E48;&#x662F;&#x8868;&#x5355;&#x6570;&#x636E;&#x6821;&#x9A8C;&#xFF1F;"></a>

访问任何一个带注册表单的网站，你都会发现，当你提交没有输入任何信息的表单时，注册页面都会给你提交一个反馈，它告诉你提交了错误的数据，这些信息可能看起来像下面这样的：

* “该字段是必填的”（该字段不能留空）
* “请输入你的电话号码，它的格式是：xxx-xxxx”（它要求你输入的数据格式为三个数字接一个横杠，然后再接着是四个数字）
* “请输入一个合法的邮箱地址”（如果你输入的数据不具有“somebody@example.com“的邮箱格式）
* “你的密码长度应该是8至30位的，并且至少应该包含一个大写字母、一个符号以及一个数字”

这就是**表单验证** —— 当你向 Web 应用提交数据时，应用会校验你输入的数据是否是正确的。如果验证通过，则这些数据可能会被保存至数据库中（通常都是这样的）或者执行下一步操作，如果校验未通过，则 Web 应用会提示你有错误的数据，并且一般都会明确的告诉你错误发生在哪里。表单验证可以通过许多不同的方式实现。

**译者注**：下面一段在英文原文中已经删除

\(事实上，没有人愿意填写表单 —— 很多证据表明，用户对填写表单这件事情都感到很烦恼，如果他们在填写表单的过程中遇到一些自己无法理解的问题，通常都会导致他们直接离开你的 Web 应用，简而言之，[表单是一个很烦人的东西](https://www.slideshare.net/jwegesin/forms-suck/)。\)

我们希望填写我们的表单时，越简单越好。所以，我们也需要坚持进行数据校验，这有三个最主要的原因：

* **我们希望以正确的格式获取到正确的数据** —— 如果用户提交的数据格式不正确或者数据不正确，我们的应用可能无法正常的运行，所以，当用户输入了数据不正确时，我们应该明确的告诉用户，哪里出了错误；
* **我们希望保护我们的用户** —— 如果他们真的输入了类似 123456 这样的简单的账户密码，亦或是压根就不设置密码，这会对他们的账户安全构成很大的威胁，这是我们不希望看到的；
* **我们希望保护我们自己** —— 有很多不正确或者不安全的数据提交都可能导致我们的应用崩溃（具体请参见[网站安全](https://developer.mozilla.org/zh-CN/docs/learn/Server-side/First_steps/Website_security)）。

#### 不同类型的表单数据校验[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E4%B8%8D%E5%90%8C%E7%B1%BB%E5%9E%8B%E7%9A%84%E8%A1%A8%E5%8D%95%E6%95%B0%E6%8D%AE%E6%A0%A1%E9%AA%8C) <a id="&#x4E0D;&#x540C;&#x7C7B;&#x578B;&#x7684;&#x8868;&#x5355;&#x6570;&#x636E;&#x6821;&#x9A8C;"></a>

在 Web 中，你可能会遇见各种不同的表单验证：

* 客户端验证发生在浏览器端，表单数据被提交之前，这种方式相较于服务器端校验来说，用户体验更好，它能实时的反馈用户的输入校验结果，这种类型的校验可以通过下面这些方式实现：
  * JavaScript 校验，这是可以完全自定义的实现方式；
  * HTML5 内置的校验，这不需要 JavaScript ，而且性能更好，但是不能自定义校验过程。
* 服务器端校验则是发生在浏览器提交数据并被服务器端程序接收之后 —— 通常服务器端校验都是发生在将数据写入数据库之前，如果数据有错误，则会直接从服务器端返回错误消息，并且告诉浏览器端发生错误的具体位置和原因，服务器校验不像浏览器端校验那样有好的用户体验，但是对于服务器端应用来说，它又是必须的 —— 这是你能保证数据正确性的最后一步了，在这之后，数据将被持久化至数据库。当今[所有的服务端框架](https://developer.mozilla.org/zh-CN/docs/learn/Server-side/First_steps/Web_frameworks)都提供了数据**校验**与**清洗**功能（让数据更安全）。

在真实的项目开发过程中，开发者一般都倾向于使用客户端校验与服务器端校验的组合校验方式以更好的保证数据的正确性与安全性。

### 使用内置表单数据验证[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E4%BD%BF%E7%94%A8%E5%86%85%E7%BD%AE%E8%A1%A8%E5%8D%95%E6%95%B0%E6%8D%AE%E9%AA%8C%E8%AF%81) <a id="&#x4F7F;&#x7528;&#x5185;&#x7F6E;&#x8868;&#x5355;&#x6570;&#x636E;&#x9A8C;&#x8BC1;"></a>

[HTML5](https://developer.mozilla.org/en-US/docs/HTML/HTML5) 一个特别有用的新功能就是，可以在不写一行脚本代码的情况下，即对用户的输入进行数据校验，这都是通过表单元素的[校验属性](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/HTML5/Constraint_validation)实现的，这些属性可以让你定义一些规则，用于限定用户的输入，比如某个输入框是否必须输入，或者某个输入框的字符串有最大长度限制，或者某个输入框必须输入一个数字、邮箱地址等，如果表单中输入的数据都符合这些限定规则，那么表示这个表单校验通过，否则则认为校验未通过。

当一个元素校验通过时：

* 该元素将可以通过 CSS 伪类  [`:valid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:valid) 进行特殊的样式化；
* 如果用户尝试提交表单，如果没有其它的控制来阻止该操作（比如JavaScript即可阻止提交），那么该表单的数据会被提交。

如果一个元素未校验通过：

* 该元素将可以通过 CSS 伪类 [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) 进行列表的样式化；
* 如果用户尝试提交表单，浏览器会展示出错误消息，并停止表单的提交。 

#### input 元素的验证约束 — starting simple[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#input_%E5%85%83%E7%B4%A0%E7%9A%84%E9%AA%8C%E8%AF%81%E7%BA%A6%E6%9D%9F_%E2%80%94_starting_simple) <a id="input_&#x5143;&#x7D20;&#x7684;&#x9A8C;&#x8BC1;&#x7EA6;&#x675F;_&#x2014;_starting_simple"></a>

在这一节，我们将会看到一些用于[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)元素验证的HTML5的特性。

让我们用一个简单的例子开始 — 一个input可以让你从香蕉或樱桃中选择你最喜欢的水果。 这个包含了一个简单的文本[`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 以及一个与其匹配的label，和 submit  [`<button>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)。你可以在GitHub [fruit-start.html](https://github.com/mdn/learning-area/blob/master/html/forms/form-validation/fruit-start.html)找到源码，在线例子如下:

在 CodePen 中打开在 JSFiddle 中打开

开始之前，先拷贝一份 `fruit-start.html` 放在你硬盘上的新目录里。

#### required 属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#required_%E5%B1%9E%E6%80%A7) <a id="required_&#x5C5E;&#x6027;"></a>

最简单的HTML5验证功能是 [`required`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-required)属性 — 如果要使输入成为必需的，则可以使用此属性标记元素。 当设置此属性时，如输入为空（输入也将被视为无效），该表单将不会提交（并将显示错误消息）。

添加一个 `required` 属性到你的 input 元素, 如下所示:

```text
<form>
  <label for="choose">Would you prefer a banana or cherry?</label>
  <input id="choose" name="i_like" required>
  <button>Submit</button>
</form>
```

同时注意在示例文件中包含的 CSS :

```text
input:invalid {
  border: 2px dashed red;
}

input:valid {
  border: 2px solid black;
}
```

以上样式效果为：在验证失败时 input 元素会有一个亮红色的虚线边框, 在验证通过时会有一个更微妙的黑色边框。在以下示例中尝试新的行为：

在 CodePen 中打开在 JSFiddle 中打开

#### 使用正则表达式验证[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E4%BD%BF%E7%94%A8%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F%E9%AA%8C%E8%AF%81) <a id="&#x4F7F;&#x7528;&#x6B63;&#x5219;&#x8868;&#x8FBE;&#x5F0F;&#x9A8C;&#x8BC1;"></a>

另一个常用的验证功能是 [`pattern`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-pattern) 属性, 以 [Regular Expression](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions) 作为 value 值. 正则表达式 \(regex\) 是一个可以用于匹配以字符组成的文本字符串的模式，所以它们是理想的表单验证器 \(以及 JavaScript 中其它许多的用途\)。 正则表达式相当复杂，我们不打算在本文中详尽地教你。

下面是一些例子，让你对它们的工作原理有个基本的了解：

* `a` — 匹配一个字符`a`\(不能匹配 `b`,  `aa`等等.\)
* `abc` — 匹配 `a`, 其次 `b`, 最后 by `c`.
* `a*` — 匹配字符 `a`, 0个或者多个 \(`+` 代表至少匹配一个或者多个\).
* `[^a]` — 匹配一个字符，但它**不能**是`a`.
* `a|b` — 匹配一个字符 `a` 或者 `b`.
* `[abc]` — 匹配一个字符，它可以是`a`,`b`或`c`.
* `[^abc]` — 匹配一个字符，但它**不可以**是`a`,`b`或`c`.
* `[a-z]` — 匹配字符范围 `a-z`且全部小写  \(你可以使用 `[A-z]` 涵盖大小写, 或 `[A-Z]` 来限制必须大写\).
* `a.c` — 匹配字符 `a`,中间匹配任意一个字符,最后匹配字符 `c`.
* `a{5}` — 匹配字符 `a`五次.
* `a{5,7}` — 匹配字符 `a`五到七次,不能多或者少.

你也可以在这些表达式中使用数字和其他字符, 例如:

* `[ |-]` — 匹配一个空格或者虚线.
* \[0-9\] — 匹配数字范围0~9.

你可以任意地组合这些，你可以任意指定不同的部分:

* `[Ll].*k` — 匹配一个大写`L`或者小写的`l`, 之后匹配一个或多个任意类型的字符, 最后匹配一个小写字母 k.
* `[A-Z][A-z|-|']+` — 一个大写字母后面跟着匹配一个大小写字母或者中划线或者撇号. 这个可以用于校验英语会话中城市或城镇名, 但这需要首字母以大写开头,不包括其他字符\(你可以添加额外的表达式来做到\). 就像 from the UK include Manchester, Ashton-under-lyne, and Bishop's Stortford. 你可以在表达式最后写上 `[A-z-' ]+` \(没有管道字符\), 但是不好阅读.
* `[0-9]{3}[ |-][0-9]{3}[ |-][0-9]{4}` — 简单的匹配一个美国内的电话号码 — 三个数字 0`-`9, 后面跟着一个空格或者中划线, 之后匹配三个数字 0`-`9, 再跟着一个空格或者中划线, 最后跟着四个数字 0`-`9. 但实际情况可能更加复杂,因为有些人会给号码加上括号什么的,这里的表达式只是用来做一个简单的演示.

不管怎么说, 让我们来实现这些例子 — 更新你的html文档表单增加一个 `pattern` 属性, 如下:

```text
<form>
  <label for="choose">Would you prefer a banana or a cherry?</label>
  <input id="choose" name="i_like" required pattern="banana|cherry">
  <button>Submit</button>
</form>
```

在 CodePen 中打开在 JSFiddle 中打开

这个例子中, 该 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 元素接受两个值中的一个: 字符串 "banana" 或者字符串"cherry".

在这个基础上, 改变`pattern` 属性内部的表达式 来支持上面的几个例子, 然后看看这表达式来确保输入哪些值来又小. 尝试写一些你自己的,尝试如何获取到.尝试一些关联的可能性.

**注意:** 一些 [`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 元素类型不需要[`pattern`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-pattern) 属性进行验证. 指定特定 `email`类型 就会使用匹配电子邮件格式的正则表达式来校验\(如果有 [`multiple`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-multiple) 属性请用逗号来分割多个邮箱\). 进一步来说, 字段 `url` 类型则会自动校验输入的是否为一个合法的链接.

**注意**: 该  [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea) 元素不支持[`pattern`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-pattern) 属性.

#### 强制条目的长度[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E5%BC%BA%E5%88%B6%E6%9D%A1%E7%9B%AE%E7%9A%84%E9%95%BF%E5%BA%A6) <a id="&#x5F3A;&#x5236;&#x6761;&#x76EE;&#x7684;&#x957F;&#x5EA6;"></a>

所有文本框 \([`<input>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 或  [`<textarea>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea)\) 可以强制使用[`minlength`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-minlength) 和 [`maxlength`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-maxlength) 属性. 如果值小于该字段 [`minlength`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-minlength) 的值或大于 [`maxlength`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-maxlength) 值则无效. 浏览器通常不会组织用户在文本字段中输入比预期更长的值，但是可以使用这种细粒度的控件来强制。

在数字条目中 \(i.e. `<input type="number">`\), 该 [`min`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-min) 和 [`max`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-max) 属性也能强制验证长度. 如何条目中的长度小于[`min`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-min) 属性提供的值或大于 [`max`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-max) 属性的值,该条目则无效.

让我来看看另外一个例子. 创建一个 [fruit-start.html](https://github.com/mdn/learning-area/blob/master/html/forms/form-validation/fruit-start.html) 文件副本.

现在删除内容中 `<body>` 元素, 接下来替换成这些:

```text
<form>
  <div>
    <label for="choose">Would you prefer a banana or a cherry?</label>
    <input id="choose" name="i_like" required minlength="6" maxlength="6">
  </div>
  <div>
    <label for="number">How many would you like?</label>
    <input type="number" id="number" name="amount" value="1" min="1" max="10">
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

* 这里我们看到 `text` 条目的属性`minlength` 和 `maxlength` 都为6 — 这 banana 和 cherry的长度都为6. 输入少于这个长度的字符显示无效, 并且在浏览器不能输入超过该限制的长度.
* 我们同时也能让 `number` 条目数值限制在 `min` 为 1 和 一个 `max` 为 10 中 — 输入超出范围则显示无效, 并且您将无法使用递增/递减箭头将该值改变到此范围之外。

这里是运行的例子:

在 CodePen 中打开在 JSFiddle 中打开

**注意**: `<input type="number">` \(或者其他类型, 像 `range`\) 也可以获取到一个[`step`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#attr-step) 属性, 指定了值在增减过程固定改变的值 \(像向上增加和向下减去的按钮\).

#### 完整的例子[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E5%AE%8C%E6%95%B4%E7%9A%84%E4%BE%8B%E5%AD%90) <a id="&#x5B8C;&#x6574;&#x7684;&#x4F8B;&#x5B50;"></a>

这里就是一个完整的展示 HTML 中使用验证属性的例子:

```text
<form>
  <p>
    <fieldset>
      <legend>Title<abbr title="This field is mandatory">*</abbr></legend>
      <input type="radio" required name="title" id="r1" value="Mr"><label for="r1">Mr.</label>
      <input type="radio" required name="title" id="r2" value="Ms"><label for="r2">Ms.</label>
    </fieldset>
  </p>
  <p>
    <label for="n1">How old are you?</label>
    <!-- The pattern attribute can act as a fallback for browsers which
         don't implement the number input type but support the pattern attribute.
         Please note that browsers that support the pattern attribute will make it
         fail silently when used with a number field.
         Its usage here acts only as a fallback -->
    <input type="number" min="12" max="120" step="1" id="n1" name="age"
           pattern="\d+">
  </p>
  <p>
    <label for="t1">What's your favorite fruit?<abbr title="This field is mandatory">*</abbr></label>
    <input type="text" id="t1" name="fruit" list="l1" required
           pattern="[Bb]anana|[Cc]herry|[Aa]pple|[Ss]trawberry|[Ll]emon|[Oo]range">
    <datalist id="l1">
      <option>Banana</option>
      <option>Cherry</option>
      <option>Apple</option>
      <option>Strawberry</option>
      <option>Lemon</option>
      <option>Orange</option>
    </datalist>
  </p>
  <p>
    <label for="t2">What's your e-mail?</label>
    <input type="email" id="t2" name="email">
  </p>
  <p>
    <label for="t3">Leave a short message</label>
    <textarea id="t3" name="msg" maxlength="140" rows="5"></textarea>
  </p>
  <p>
    <button>Submit</button>
  </p>
</form>
```

```text
body {
  font: 1em sans-serif;
  padding: 0;
  margin : 0;
}

form {
  max-width: 200px;
  margin: 0;
  padding: 0 5px;
}

p > label {
  display: block;
}

input[type=text],
input[type=email],
input[type=number],
textarea,
fieldset {
/* required to properly style form 
   elements on WebKit based browsers */
  -webkit-appearance: none;
  
  width : 100%;
  border: 1px solid #333;
  margin: 0;
  
  font-family: inherit;
  font-size: 90%;
  
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

input:invalid {
  box-shadow: 0 0 5px 1px red;
}

input:focus:invalid {
  outline: none;
}
```

在 CodePen 中打开在 JSFiddle 中打开

#### 自定义错误信息[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E8%87%AA%E5%AE%9A%E4%B9%89%E9%94%99%E8%AF%AF%E4%BF%A1%E6%81%AF) <a id="&#x81EA;&#x5B9A;&#x4E49;&#x9519;&#x8BEF;&#x4FE1;&#x606F;"></a>

正如我们上面所看到的例子, 每次我们输入无效的表单数据时, 浏览器总会显示错误的信息. 但是显示的信息取决于你所使用的浏览器.

这些自动抛出的错误有两个缺点:

* 没有标准可以让 CSS 来改变给人们看到的样子.
* 这依赖于他们使用的浏览器环境, 意味着你使用不同的语言页面得到的反馈信息也是不同语言的.

| 在英文页面上的法语反馈信息版本 |  |
| :--- | :--- |
| 浏览器 | 渲染 |
| Firefox 17 \(Windows 7\) | ![Example of an error message with Firefox in French on an English page](https://developer.mozilla.org/files/4329/error-firefox-win7.png) |
| Chrome 22 \(Windows 7\) | ![Example of an error message with Chrome in French on an English page](https://developer.mozilla.org/files/4327/error-chrome-win7.png) |
| Opera 12.10 \(Mac OSX\) | ![Example of an error message with Opera in French on an English page](https://developer.mozilla.org/files/4331/error-opera-macos.png) |

自定义这些消息的外观和文本, 你必须使用 JavaScript; 不能使用 HTML 和 CSS 来改变.

HTML5 提供 [the constraint validation API](http://www.w3.org/TR/html5/forms.html#the-constraint-validation-api) 来检测自定义表单元素的状态. 除此之外,他可以改变错误的文本信息. 让我们快速的看一个例子:

```text
<form>
  <label for="mail">I would like you to provide me an e-mail</label>
  <input type="email" id="mail" name="mail">
  <button>Submit</button>
</form>
```

在JavaScript 中, 你调用 [`setCustomValidity()`](https://developer.mozilla.org/en-US/docs/HTML/HTML5/Constraint_validation#Constraint_API's_element.setCustomValidity%28%29) 方法:

```text
var email = document.getElementById("mail");

email.addEventListener("input", function (event) {
  if (email.validity.typeMismatch) {
    email.setCustomValidity("I expect an e-mail, darling!");
  } else {
    email.setCustomValidity("");
  }
});
```

在 CodePen 中打开在 JSFiddle 中打开

###  使用 JavaScript校验表单[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E4%BD%BF%E7%94%A8_JavaScript%E6%A0%A1%E9%AA%8C%E8%A1%A8%E5%8D%95) <a id="&#x4F7F;&#x7528;_JavaScript&#x6821;&#x9A8C;&#x8868;&#x5355;"></a>

如果你想控制原生错误信息的外观和感觉，或者你想处理不支持HTML内置表单验证的浏览器，则必须使用 Javascript。

#### HTML5 用于校验约束的 API[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#HTML5_%E7%94%A8%E4%BA%8E%E6%A0%A1%E9%AA%8C%E7%BA%A6%E6%9D%9F%E7%9A%84_API) <a id="HTML5_&#x7528;&#x4E8E;&#x6821;&#x9A8C;&#x7EA6;&#x675F;&#x7684;_API"></a>

现在越来越多的浏览器支持约束验证API，并且它正在变得可靠。这些 API 由一组方法和属性组成，可在每个表单元素上调用。

**用于校验的 API 及属性**

| 属性 | 描述 |
| :--- | :--- |
| `validationMessage` | 一个本地化消息，描述元素不满足验证条件时（如果有的话）的文本信息。如果元素无需验证（`willValidate` 为 `false`），或元素的值满足验证条件时，为空字符串。 |
| `validity` | 一个 [`ValidityState`](https://developer.mozilla.org/zh-CN/docs/Web/API/ValidityState) 对象，描述元素的验证状态。 |
| `validity.customError` | 如果元素设置了自定义错误，返回 `true` ；否则返回`false`。 |
| `validity.patternMismatch` | 如果元素的值不匹配所设置的正则表达式，返回 `true`，否则返回 `false`。  当此属性为 `true` 时，元素将命中  [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) CSS 伪类。 |
| `validity.rangeOverflow` | 如果元素的值高于所设置的最大值，返回 `true`，否则返回 `false`。  当此属性为 `true` 时，元素将命中  [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) CSS 伪类。 |
| `validity.rangeUnderflow` | 如果元素的值低于所设置的最小值，返回 `true`，否则返回 `false`。  当此属性为 `true` 时，元素将命中  [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) CSS 伪类。 |
| `validity.stepMismatch` | 如果元素的值不符合 step 属性的规则，返回 `true`，否则返回 `false`。  当此属性为 `true` 时，元素将命中  [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) CSS 伪类。 |
| `validity.tooLong` | 如果元素的值超过所设置的最大长度，返回 `true`，否则返回 `false`。  当此属性为 `true` 时，元素将命中  [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) CSS 伪类。 |
| `validity.typeMismatch` | 如果元素的值出现语法错误，返回 `true`，否则返回 `false`。  当此属性为 `true` 时，元素将命中  [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) CSS 伪类。 |
| `validity.valid` | 如果元素的值不存在验证问题，返回 `true`，否则返回 `false`。  当此属性为 `true` 时，元素将命中   [`:valid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:valid) CSS 伪类，否则命中 [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) CSS 伪类。 |
| `validity.valueMissing` | 如果元素设置了 required 属性且值为空，返回 `true`，否则返回 `false`。  当此属性为 true 时，元素将命中  [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) CSS 伪类。 |
| `willValidate` | 如果元素在表单提交时将被验证，返回 `true`，否则返回 `false`。 |

**校验约束 API 的方法**

| 方法 | 描述 |
| :--- | :--- |
| `checkValidity()` | 如果元素的值不存在验证问题，返回 `true`，否则返回 `false`。如果元素验证失败，此方法会触发[`invalid`](https://developer.mozilla.org/zh-CN/docs/Web/Reference/Events/invalid) 事件。 |
| `setCustomValidity(`_`message`_`)` | 为元素添加一个自定义的错误消息；如果设置了自定义错误消息，则该元素被认为是无效的，并显示指定的错误。这允许你使用 JavaScript 代码来建立验证失败，而不是用标准约束验证 API 所提供的。在报告问题时，将向用户显示自定义消息。  如果参数为空，则清空自定义错误。 |

对于旧版浏览器，可以使用 [polyfill（例如 Hyperform](https://hyperform.js.org/)），来弥补其对约束验证 API 支持的不足。既然你已经使用 JavaScript，在您的网站或 Web 应用程序的设计和实现中使用 polyfill 并不是累赘。

**使用校验约束 API 的例子**

让我们看看如何使用这个 API 来构建自定义错误消息。首先，HTML：

```text
<form novalidate>
  <p>
    <label for="mail">
      <span>Please enter an email address:</span>
      <input type="email" id="mail" name="mail">
      <span class="error" aria-live="polite"></span>
    </label>
  </p>
  <button>Submit</button>
</form>
```

这个简单的表单使用 [`novalidate`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form#attr-novalidate) 属性关闭浏览器的自动验证；这允许我们使用脚本控制表单验证。但是，这并不禁止支持约束验证 API 的应用和以下 CSS 伪类： [`:valid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:valid)、[`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid)、[`:in-range`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:in-range) 、[`:out-of-range`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:out-of-range) 。这意味着，即使浏览器在发送数据之前没有自动检查表单的有效性，您仍然可以自己做，并相应地设置表单的样式。

[`aria-live`](https://developer.mozilla.org/en-US/docs/Accessibility/ARIA/ARIA_Live_Regions) 属性确保我们的自定义错误信息将呈现给所有人，包括使用屏幕阅读器等辅助技术的人。

**CSS**

以下 CSS 样式使我们的表单和其错误输出看起来更有吸引力。

```text
/* 仅为了使示例更好看 */
body {
  font: 1em sans-serif;
  padding: 0;
  margin : 0;
}

form {
  max-width: 200px;
}

p * {
  display: block;
}

input[type=email]{
  -webkit-appearance: none;

  width: 100%;
  border: 1px solid #333;
  margin: 0;

  font-family: inherit;
  font-size: 90%;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

/* 验证失败的元素样式 */
input:invalid{
  border-color: #900;
  background-color: #FDD;
}

input:focus:invalid {
  outline: none;
}

/* 错误消息的样式 */
.error {
  width  : 100%;
  padding: 0;
 
  font-size: 80%;
  color: white;
  background-color: #900;
  border-radius: 0 0 5px 5px;
 
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.error.active {
  padding: 0.3em;
}
```

**JavaScript**

以下 JavaScript 代码演示如何处理自定义错误验证。

```text
// 有许多方式可以获取 DOM 节点；在此我们获取表单本身和
// email 输入框，以及我们将放置错误信息的 span 元素。

var form  = document.getElementsByTagName('form')[0];
var email = document.getElementById('mail');
var error = document.querySelector('.error');

email.addEventListener("input", function (event) {
  // 当用户输入信息时，验证 email 字段
  if (email.validity.valid) {
    // 如果验证通过，清除已显示的错误消息
    error.innerHTML = ""; // 重置消息的内容
    error.className = "error"; // 重置消息的显示状态
  }
}, false);
form.addEventListener("submit", function (event) {
  // 当用户提交表单时，验证 email 字段
  if (!email.validity.valid) {
    
    // 如果验证失败，显示一个自定义错误
    error.innerHTML = "I expect an e-mail, darling!";
    error.className = "error active";
    // 还需要阻止表单提交事件，以取消数据传送
    event.preventDefault();
  }
}, false);
```

这是运行结果：

在 CodePen 中打开在 JSFiddle 中打开

约束验证 API 为您提供了一个强大的工具来处理表单验证，让您可以对用户界面进行极大的控制，而不仅仅是仅使用 HTML 和 CSS。

#### 不使用内建 API 时的表单验证[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E4%B8%8D%E4%BD%BF%E7%94%A8%E5%86%85%E5%BB%BA_API_%E6%97%B6%E7%9A%84%E8%A1%A8%E5%8D%95%E9%AA%8C%E8%AF%81) <a id="&#x4E0D;&#x4F7F;&#x7528;&#x5185;&#x5EFA;_API_&#x65F6;&#x7684;&#x8868;&#x5355;&#x9A8C;&#x8BC1;"></a>

有时，例如使用旧版浏览器或[自定义小部件](https://developer.mozilla.org/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets)，您将无法（或不希望）使用约束验证API。 在这种情况下，您仍然可以使用 JavaScript 来验证您的表单。 验证表单比真实数据验证更像是一个用户界面问题。

要验证表单，您必须问自己几个问题：我应该进行什么样的验证？你需要确定如何验证你的数据：字符串操作，类型转换，正则表达式等。这取决于你。 只要记住，表单数据总是文本，并总是以字符串形式提供给脚本。如果表单验证失败，我该怎么办?这显然是一个 UI 的问题。 您必须决定表单的行为方式：表单是否发送数据？ 是否突出显示错误的字段？是否显示错误消息？如何帮助用户纠正无效数据?为了减少用户的挫折感，提供尽可能多的有用的信息是非常重要的，以便引导他们纠正他们的输入。 您应该提供前期建议，以便他们知道预期的情况以及明确的错误消息。 如果您想深入了解表单验证用户界面要求，那么您应该阅读一些有用的文章：

* SmashingMagazine: [Form-Field Validation: The Errors-Only Approach](http://uxdesign.smashingmagazine.com/2012/06/27/form-field-validation-errors-only-approach/)
* SmashingMagazine: [Web Form Validation: Best Practices and Tutorials](http://www.smashingmagazine.com/2009/07/07/web-form-validation-best-practices-and-tutorials/)
* Six Revision: [Best Practices for Hints and Validation in Web Forms](http://sixrevisions.com/user-interface/best-practices-for-hints-and-validation-in-web-forms/)
* A List Apart: [Inline Validation in Web Forms](http://www.alistapart.com/articles/inline-validation-in-web-forms/)

**不使用校验约束API 的例子**

为了说明这一点，让我们重构一下前面的例子，以便它可以在旧版浏览器中使用：

```text
<form>
  <p>
    <label for="mail">
        <span>Please enter an email address:</span>
        <input type="text" class="mail" id="mail" name="mail">
        <span class="error" aria-live="polite"></span>
    </label>
  <p>
  <!-- Some legacy browsers need to have the `type` attribute
       explicitly set to `submit` on the `button`element -->
  <button type="submit">Submit</button>
</form>
```

正如你所看到的，HTML 几乎是一样的；我们只是关闭了 HTML 验证功能。 请注意，[ARIA](https://developer.mozilla.org/en-US/docs/Accessibility/ARIA) 是与 HTML5 无关的独立规范。

**CSS**

同样的，CSS也不需要太多的改动， 我们只需将 [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) 伪类变成真实的类，并避免使用不适用于 Internet Explorer 6 的属性选择器。

```text
/* 仅为了使示例更好看 */
body {
  font: 1em sans-serif;
  padding: 0;
  margin : 0;
}

form {
  max-width: 200px;
}

p * {
  display: block;
}

input.mail {
  -webkit-appearance: none;

  width: 100%;
  border: 1px solid #333;
  margin: 0;

  font-family: inherit;
  font-size: 90%;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

/* 验证失败的元素样式 */
input.invalid{
  border-color: #900;
  background-color: #FDD;
}

input:focus.invalid {
  outline: none;
}

/* 错误消息的样式 */
.error {
  width  : 100%;
  padding: 0;
 
  font-size: 80%;
  color: white;
  background-color: #900;
  border-radius: 0 0 5px 5px;
 
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.error.active {
  padding: 0.3em;
}
```

**JavaScript**

JavaScript 代码有很大的变化，需要做更多的工作。

```text
// 使用旧版浏览器选择 DOM 节点的方法较少
var form  = document.getElementsByTagName('form')[0];
var email = document.getElementById('mail');

// 以下是在 DOM 中访问下一个兄弟元素的技巧
// 这比较危险，很容易引起无限循环
// 在现代浏览器中，应该使用 element.nextElementSibling
var error = email;
while ((error = error.nextSibling).nodeType != 1);

// 按照 HTML5 规范
var emailRegExp = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/;

// 许多旧版浏览器不支持 addEventListener 方法
// 这只是其中一种简单的处理方法
function addEvent(element, event, callback) {
  var previousEventCallBack = element["on"+event];
  element["on"+event] = function (e) {
    var output = callback(e);
    
    // 返回 `false` 来停止回调链，并中断事件的执行
    if (output === false) return false;

    if (typeof previousEventCallBack === 'function') {
      output = previousEventCallBack(e);
      if(output === false) return false;
    }
  }
};

// 现在我们可以重构字段的验证约束了
// 由于不使用 CSS 伪类, 我们必须明确地设置 valid 或 invalid 类到 email 字段上
addEvent(window, "load", function () {
  // 在这里验证字段是否为空（请记住，该字段不是必需的）
  // 如果非空，检查它的内容格式是不是合格的 e-mail 地址
  var test = email.value.length === 0 || emailRegExp.test(email.value);
 
  email.className = test ? "valid" : "invalid";
});

// 处理用户输入事件
addEvent(email, "input", function () {
  var test = email.value.length === 0 || emailRegExp.test(email.value);
  if (test) {
    email.className = "valid";
    error.innerHTML = "";
    error.className = "error";
  } else {
    email.className = "invalid";
  }
});

// 处理表单提交事件
addEvent(form, "submit", function () {
  var test = email.value.length === 0 || emailRegExp.test(email.value);
 
  if (!test) {
    email.className = "invalid";
    error.innerHTML = "I expect an e-mail, darling!";
    error.className = "error active";

    // 某些旧版浏览器不支持 event.preventDefault() 方法
    return false;
  } else {
    email.className = "valid";
    error.innerHTML = "";
    error.className = "error";
  }
});
```

该结果如下:

在 CodePen 中打开在 JSFiddle 中打开

正如你所看到的，建立自己的验证系统并不难。 困难的部分是使其足够通用，以跨平台和任何形式使用它可以创建。 有许多库可用于执行表单验证; 你应该毫不犹豫地使用它们。 这里有一些例子：

* 独立的库（原生 Javascript 实现）：
  * [Validate.js](http://rickharrison.github.com/validate.js/)
* jQuery 插件:
  * [Validation](http://bassistance.de/jquery-plugins/jquery-plugin-validation/)
  * [Valid8](http://unwrongest.com/projects/valid8/)

 **远程校验**

在某些情况下，执行一些远程验证可能很有用。 当用户输入的数据与存储在应用程序服务器端的附加数据绑定时，这种验证是必要的。 一个用例就是注册表单，在这里你需要一个用户名。 为了避免重复，执行一个 AJAX 请求来检查用户名的可用性，而不是要求用户发送数据，然后发送带有错误的表单。

执行这样的验证需要采取一些预防措施：

* 它要求公开 API 和一些数据；您需要确保它不是敏感数据。
* 网络滞后需要执行异步验证。这需要一些用户界面的工作，以确保如果验证不正确执行，用户不会被阻止。

### 结论[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Data_form_validation#%E7%BB%93%E8%AE%BA) <a id="&#x7ED3;&#x8BBA;"></a>

表单验证不需要复杂的 JavaScript，但它确实需要仔细考虑用户。 一定要记住帮助您的用户更正他提供的数据。 为此，请务必：

* 显示明确的错误消息。
* 放宽输入格式。
* 指出错误发生的位置（特别是在大型表单中）。

