# JavaScript基础

JavaScript 是一门为你的网站添加交互功能的编程语言。（例如：游戏，响应按钮被按下或者以表单输入的数据，动态样式，动画等）。本文可以帮助你开始使用这种令人兴奋的语言，并让你明白能做什么。

### 所以到底什么是 JavaScript？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E6%89%80%E4%BB%A5%E5%88%B0%E5%BA%95%E4%BB%80%E4%B9%88%E6%98%AF_JavaScript%EF%BC%9F) <a id="&#x6240;&#x4EE5;&#x5230;&#x5E95;&#x4EC0;&#x4E48;&#x662F;_JavaScript&#xFF1F;"></a>

[JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript)（缩写：JS）是一门成熟的[动态编程语言](https://developer.mozilla.org/en-US/docs/Glossary/Dynamic_programming_language)。当应用于 [HTML](https://developer.mozilla.org/en-US/docs/Glossary/HTML) 文档时，它可以在网站上提供动态交互性。它是 Mozilla 项目联合创始人， Mozilla 基金会和 Mozilla 公司的 Brendan Eich 发明的。

JavaScript 是非常通用的。你可以从简单的交互，比如轮播、相册、浮动布局和按钮点击事件做起。随着你学习的深入，你可以创建游戏、二维和三维动画、数据库驱动的综合应用程序，以及更多！

JavaScript 本身是相当简洁却非常灵活的。开发者们在 JavaScript 核心之上编写了非常多的工具，从而花最小的代价获得大量额外的功能。这些功能包括：

* 浏览器**应用编程接口** \([API](https://developer.mozilla.org/en-US/docs/Glossary/API)\) 。API 内置于浏览器中，它们提供像动态编写 HTML 和设置 CSS 样式，采集并操控用户摄像头的数据流和生成三维图像与音频样本等功能。
* 第三方 API 允许开发者将来自其它内容提供者，如 Twitter 或 Facebook ，的功能整合到自己的网站里。
* 你可以在你的 HTML 里应用第三方框架和库以快速构建网站和应用。

因为这篇文章只会简单介绍 JavaScript ，所以我们并不打算在这个阶段过于详细地介绍 JavaScript 语言以及前面提及的各式工具。你可以之后在 [JavaScript 学习区](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript)和 MDN 的其它地方学习更多细节。

下面我们将介绍语言的一些核心部分，你也可以看看如何使用一些浏览器 API 。

### 一个 “Hello World”示例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E4%B8%80%E4%B8%AA_%E2%80%9CHello_World%E2%80%9D%E7%A4%BA%E4%BE%8B) <a id="&#x4E00;&#x4E2A;_&#x201C;Hello_World&#x201D;&#x793A;&#x4F8B;"></a>

上面的内容听起来非常激动人心，而且也应该如此—— JavaScript 是最让人激动的 Web 技术之一，而且当你对它掌握的加深，你的网页将进入一个更有创造力和更加强大的层次。

然而，JavaScript 比 HTML 和 CSS 学习起来更加复杂一点，所以你需要一步一步谨慎地走。首先，我们将向你展示怎么在你的页面中添加一些基本的 JavaScript 脚本来创造一个 “hello world” 示例（[编程世界的标准示例](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program)）。

注意：如果你没有学习我们之前的课程，[点击下载示例代码](https://github.com/mdn/beginner-html-site-styled/archive/gh-pages.zip)然后将其作为你的出发点。

1. 首先，前往你的测试目录并创建一个叫做 `scripts` 的文件夹。然后在这个文件夹下创建一个新的 `main.js` 文件并保存。
2. 接下来，打开你的 `index.html` 文件，在 `</body>` 闭合标签之前输入这一行代码：

   ```text
   <script src="scripts/main.js"></script>
   ```

3. 这基本上与引入 CSS 的 [`<link>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link) 元素功能相同——它将 JavaScript 引入了页面，所以它将影响 HTML （包括 CSS 和其它页面上的其它任何内容）。 
4. 现在将下面的代码添加到 `main.js` 文件中:

   ```text
   var myHeading = document.querySelector('h1');
   myHeading.textContent = 'Hello world!';
   ```

5. 最后，确保 HTML 和 JavaScript 文件已经保存好，然后用浏览器打开 `index.html` 。你应该看到如下内容：![](https://mdn.mozillademos.org/files/9543/hello-world.png)

提示：我们之所以将 __[_`<script>`_](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/script) __元素放在 HTML 文件底部，是因为浏览器会按照代码在文件中的顺序解析 HTML。如果应该要影响下面 HTML 的 JavaScript 先被加载，那么它可能由于 HTML 尚未被加载而失效。所以将 JavaScript 代码放在靠近 HTML 页面底部的位置是通常最好的选择。

#### 发生了什么？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E5%8F%91%E7%94%9F%E4%BA%86%E4%BB%80%E4%B9%88%EF%BC%9F) <a id="&#x53D1;&#x751F;&#x4E86;&#x4EC0;&#x4E48;&#xFF1F;"></a>

你的标题通过 JavaScript 被更改为了 “Hello world!” 。我们首先使用一个叫做[`querySelector()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/querySelector) 的函数来获取标题，然后将其储存在一个叫 `myHeading` 的变量中。这与我们使用 CSS 选择器进行的操作非常相像。如果你想对某个元素进行操作，首先你得先选择它。

之后我们将 `myHeading` 变量的属性 [`textContent`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/textContent) （代表这个标题的内容）赋值为 “Hello world!” 。

**提示**：以上两个用到的特性都是[文档对象模型 \(DOM\) API](https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model) 的一部分， 它可以使你控制文档。

### 语言基础速览[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E8%AF%AD%E8%A8%80%E5%9F%BA%E7%A1%80%E9%80%9F%E8%A7%88) <a id="&#x8BED;&#x8A00;&#x57FA;&#x7840;&#x901F;&#x89C8;"></a>

让我们来解释一下 JavaScript 这门语言的一些核心特性，以便让你们更好地了解它是怎么运作的。更棒的是，这些特性对所有编程语言来说都很常见。如果你能够掌握这些基础，你就能更好地在编程的世界里徜徉！

注意：在学习这篇文章时，将示例代码输入到你的 JavaScript 控制台里看看会发生什么。要查看更多关于 JavaScript 控制台的信息，点击[探索浏览器开发者工具](https://developer.mozilla.org/zh-CN/Learn/Discover_browser_developer_tools)。

#### 变量[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E5%8F%98%E9%87%8F) <a id="&#x53D8;&#x91CF;"></a>

[变量](https://developer.mozilla.org/en-US/docs/Glossary/Variable)是你存储值的容器。要声明一个变量你需要首先使用关键字 `var` ，然后输入任何你想要的名称：

```text
var myVariable;
```

提示：行末的分号表示语句结束，不过这个分号只有在单行内需要分割语句时才是必须的。然而，一些人认为在每个语句后面加分号是一种好的风格。这里为你提供了更多关于是否应该加分号的规则 — 查看 [Your Guide to Semicolons in JavaScript](http://news.codecademy.com/your-guide-to-semicolons-in-javascript/) 获取更多细节。

提示：你几乎可以以任何名称来命名一个变量，不过我们有一些限制（点击这里查看[变量命名规则](http://www.codelifter.com/main/tips/tip_020.shtml)）。如果你不确定，你可以[验证你的变量名](https://mothereff.in/js-variables)查看是否有效。

提示：JavaScript 是对大小写敏感的—— `myVariable` __与 `myvariable` 是不同的。如果你的代码出现问题了，查看一下大小写有没有错误！

定义一个变量之后，你可以赋予它一个值：

```text
myVariable = 'Bob';
```

你也可以将这些操作写在同一行：

```text
var myVariable = 'Bob';
```

你可以通过变量名称读取变量的值：

```text
myVariable;
```

在给变量赋值之后，你可以更改这个变量的值：

```text
var myVariable = 'Bob';
myVariable = 'Steve';
```

注意变量有不同的 [数据类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures) ：

| 变量 | 解释 | 示例 |
| :--- | :--- | :--- |
| [String](https://developer.mozilla.org/en-US/docs/Glossary/String) | 字符串（文字序列）。 要表示变量的值是字符串，你必须将它们用引号包裹起来。 | `var myVariable = 'Bob';` |
| [Number](https://developer.mozilla.org/en-US/docs/Glossary/Number) | 数字。不用引号包围。 | `var myVariable = 10;` |
| [Boolean](https://developer.mozilla.org/en-US/docs/Glossary/Boolean) | 布尔\(逻辑\)值。一个 True/False （真 / 假）值。 `true`/`false` 是 JS 里的特殊关键字，不需要引号。 | `var myVariable = true;` |
| [Array](https://developer.mozilla.org/en-US/docs/Glossary/Array) | 数组，一种允许你存储多个值在一个引用里的结构。 | `var myVariable = [1,'Bob','Steve',10];` 引用数组的元素只需：`myVariable[0]`, `myVariable[1]`, 等等. |
| [Object](https://developer.mozilla.org/en-US/docs/Glossary/Object) | 对象，基本上 JavaScript 里的任何东西都是对象，而且都可以被储存在变量里。将这个牢记于心。 | `var myVariable = document.querySelector('h1');` 上面所有示例都是对象。 |

那么为什么我们需要变量呢？好吧，在编程时要做任何有趣的事我们必须用到变量。如果值无法被改变，那么你将无法动态地做任何事，就像个性化一条祝福信息或是改变在图片库里展示的图片。

#### 注释[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E6%B3%A8%E9%87%8A) <a id="&#x6CE8;&#x91CA;"></a>

你可以在 JavaScript 中添加注释，就像你在 CSS 中做过的一样。

```text
/*
Everything in between is a comment.
*/
```

如果你的注释只有一行，我们经常将它们更简单地放在两个斜杠之后，就像这样：

```text
// This is a comment
```

#### 运算符[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E8%BF%90%E7%AE%97%E7%AC%A6) <a id="&#x8FD0;&#x7B97;&#x7B26;"></a>

 [运算符](https://developer.mozilla.org/en-US/docs/Glossary/Operator)是一个根据两个值（或变量）产生结果的数学符号。在下面的表格里你可以看到一些最简单的运算符，后面的示例你可以在浏览器控制台里尝试一下。

<table>
  <thead>
    <tr>
      <th style="text-align:left">运算符</th>
      <th style="text-align:left">解释</th>
      <th style="text-align:left">符号</th>
      <th style="text-align:left">示例</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">加/连接</td>
      <td style="text-align:left">用来相加两个数字，或者连接两个字符串。</td>
      <td style="text-align:left"><code>+</code>
      </td>
      <td style="text-align:left"><code>6 + 9;<br />&quot;Hello &quot; + &quot;world!&quot;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">减、乘、除</td>
      <td style="text-align:left">这些运算符操作将与你期望它们在基础数学中所做的一样。</td>
      <td style="text-align:left"><code>-</code>, <code>*</code>, <code>/</code>
      </td>
      <td style="text-align:left"><code>9 - 3;<br />8 * 2; // JS&#x4E2D;&#x7684;&#x4E58;&#x662F;&#x4E00;&#x4E2A;&quot;*&quot;&#x53F7;;<br />9 / 3;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">赋值运算符</td>
      <td style="text-align:left">你之前已经见过这个符号了：它将一个值赋给一个变量</td>
      <td style="text-align:left"><code>=</code>
      </td>
      <td style="text-align:left"><code>var myVariable = &apos;Bob&apos;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">相等</td>
      <td style="text-align:left">它将测试两个值是否相等，而且会返回一个 <code>true</code>/<code>false</code> （布尔型）值。</td>
      <td
      style="text-align:left"><code>===</code>
        </td>
        <td style="text-align:left"><code>var myVariable = 3;<br />myVariable === 4;</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">非，不等</td>
      <td style="text-align:left">经常与相等运算一起使用，非运算符在JS中表示逻辑非——它也返回一个布尔值。</td>
      <td style="text-align:left"><code>!</code>, <code>!==</code>
      </td>
      <td style="text-align:left">
        <p>原本的值是 <code>true</code> ，但是返回了 <code>false</code> 因为之后我们做了非运算：</p>
        <p><code>var myVariable = 3;<br />!myVariable === 3;</code>
        </p>
        <p>这里我们测试了" <code>myVariable</code> 是否等于 3"。这里返回了 <code>false</code> ，因为它等于 3。</p>
        <p><code>var myVariable = 3;</code>
          <br />myVariable !== 3;</p>
      </td>
    </tr>
  </tbody>
</table>还有很多运算符供我们探索，不过暂时我们只需要这么多。你可以在[表达式和运算符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators)查看完整列表。

提示：计算时如果混合不同的数据类型可能导致奇怪的结果，所以请谨慎地正确引用你的变量，然后得出你期望的结果。比如输入 `"35" + "25"` __到控制台。为什么结果与你想象的不同？因为引号将数字转换成了字符串，所以最终会连接两个字符串而不是相加数字。如果你输入 __`35 + 25`，你会得到正确的结果。

#### 条件句[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E6%9D%A1%E4%BB%B6%E5%8F%A5) <a id="&#x6761;&#x4EF6;&#x53E5;"></a>

条件句是能够让你测试一个表达式是否返回 `true` 然后根据结果运行不同的代码的代码结构。一个常用的条件句形式是 `if ... else` 语句。下面是一个例子：

```text
var iceCream = 'chocolate';
if (iceCream === 'chocolate') {
  alert('Yay, I love chocolate ice cream!');    
} else {
  alert('Awwww, but chocolate is my favorite...');    
}
```

 `if ( ... )` 里面的表达式就是测试——这里使用了（上面所提到的）相等运算符来比较变量 `iceCream` 与字符串 `chocolate` 是否相等。 如果返回 `true`，运行第一块代码；如果返回 `false`，跳过第一块直接运行 `else` 之后的第二块代码。

#### 函数[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E5%87%BD%E6%95%B0) <a id="&#x51FD;&#x6570;"></a>

[函数](https://developer.mozilla.org/en-US/docs/Glossary/Function)是一种封装你想重复使用的功能的方法，这样你就可以需要使用其中的功能的时候通过函数名称来调用函数，而不用老是重复写下整段代码。你在上面已经见过一些函数了，比如：

1. ```text
   var myVariable = document.querySelector('h1');
   ```
2. ```text
   alert('hello!');
   ```

这些函数 `document.querySelector` 和 `alert` 是浏览器内置的，你可以在任何时候使用。

如果你看到一些东西长得像变量名但是有括号——`()`——在后面，这可能就是一个函数。函数通常包括[参数](https://developer.mozilla.org/en-US/docs/Glossary/Argument)——一些必要的数据。它们在括号内部，如果有一个以上参数则使用逗号分开。

比如， `alert()` 函数在浏览器窗口内弹出一个警告框，但是我们需要给函数提供一个字符串作为参数以告诉函数应该在警告框里写什么。

好消息是你可以定义你自己的函数——在下一个例子里我们会写一个简单的需要两个参数来做乘法运算的函数。

```text
function multiply(num1, num2) {
  var result = num1 * num2;
  return result;
}
```

尝试在控制台运行这个函数，然后自己尝试几次不同的参数，比如：

```text
multiply(4, 7);
multiply(20, 20);
multiply(0.5, 3);
```

**提示**：[`return`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/return) 语句告诉浏览器返回 `result` 变量以便使用。这是很有必要的，因为函数内定义的变量只能在函数内使用。这叫做变量[作用域](https://developer.mozilla.org/en-US/docs/Glossary/Scope)。（详见[变量作用域](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Values,_variables,_and_literals#Variable_scope)）

#### 事件[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E4%BA%8B%E4%BB%B6) <a id="&#x4E8B;&#x4EF6;"></a>

你需要使用事件在网页上创建真正的交互——事件是能够捕捉浏览器操作并且允许你运行代码进行响应的代码结构。最明显的事件是[点击事件](https://developer.mozilla.org/zh-CN/docs/Web/Events/click)，它会在鼠标点击什么的时候被浏览器唤醒。 为了演示这个操作，尝试将下面的代码输入到控制台，然后在当前网页点击：

```text
document.querySelector('html').onclick = function() {
    alert('Ouch! Stop poking me!');
}
```

我们有许多方法来将一个事件与元素绑定。在这里我们选择了 [`<html>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/html) 元素，然后将 [`onclick`](https://developer.mozilla.org/zh-CN/docs/Web/API/GlobalEventHandlers.onclick) 属性设置成包含单击时我们想要运行的代码的匿名函数。

注意到

```text
document.querySelector('html').onclick = function() {};
```

相当于

```text
var myHTML = document.querySelector('html');
myHTML.onclick = function() {};
```

只是更加简洁。

### 改善示例网页[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E6%94%B9%E5%96%84%E7%A4%BA%E4%BE%8B%E7%BD%91%E9%A1%B5) <a id="&#x6539;&#x5584;&#x793A;&#x4F8B;&#x7F51;&#x9875;"></a>

现在我们已经讲述了一点 JavaScript 的基础了，让我们添加一些更酷的特性到示例网页里来看看我们能做什么。

#### 添加一个图像切换器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E6%B7%BB%E5%8A%A0%E4%B8%80%E4%B8%AA%E5%9B%BE%E5%83%8F%E5%88%87%E6%8D%A2%E5%99%A8) <a id="&#x6DFB;&#x52A0;&#x4E00;&#x4E2A;&#x56FE;&#x50CF;&#x5207;&#x6362;&#x5668;"></a>

这一部分我们将用更多 DOM API 特性添加另一张图片到我们的网站，并且添用一些 JavaScript 使图片被点击时进行切换。

1. 首先，找到另一个你想用来装饰你的网页的图片。确保它与你第一张图片尺寸相同，或者尽可能相似。
2. 将图片保存在 `images` 文件夹。
3. 重命名图片为 `firefox2.png` 。
4. 打开 `main.js` 文件，输入下面的 JavaScript 代码 \( 如果你的 "hello world" JavaScript 仍然在这个文件中，删除它们 \) :

   ```text
   var myImage = document.querySelector('img');

   myImage.onclick = function() {
       var mySrc = myImage.getAttribute('src');
       if(mySrc === 'images/firefox-icon.png') {
         myImage.setAttribute('src', 'images/firefox2.png');
       } else {
         myImage.setAttribute('src', 'images/firefox-icon.png');
       }
   }
   ```

5. 保存所有文件然后用浏览器打开 `index.html` 。当你点击图片时，它应该会切换成另一张图片！

在这里，我们将 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素的引用存放在 `myImage` 变量里。接下来，我们将这个变量的 `onclick` 事件与一个匿名函数绑定。选择，每次图片被点击时：

1. 我们获取这张图片的 `src` 属性的值。
2. 我们使用一个条件句来判断 `src` 的值是否等于原始图像的路径:
   1. 如果是，我们将 `src` 的值改为第二张图片的路径，强制在 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 内读取另一张图片。
   2. 如果不是（意味着它肯定已经被更改过）, 我们把 `src` 的值重新设置为原始图片的路径，即原来的状态。

#### 添加个性化的欢迎信息[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E6%B7%BB%E5%8A%A0%E4%B8%AA%E6%80%A7%E5%8C%96%E7%9A%84%E6%AC%A2%E8%BF%8E%E4%BF%A1%E6%81%AF) <a id="&#x6DFB;&#x52A0;&#x4E2A;&#x6027;&#x5316;&#x7684;&#x6B22;&#x8FCE;&#x4FE1;&#x606F;"></a>

接下来我们会添加另一段代码，在用户初次进入站点时将网页的标题改成一段个性化的欢迎信息。欢迎信息会由 [Web Storage API](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Storage_API) 保存下来，即使用户关闭页面之后再重新打开此页面，我们仍然可以得到之前的信息。我们还会添加一个选项来在必要的时候改变用户并且改变欢迎信息。

1. 在 `index.html` 里， 在 [`<script>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/script) 元素前添加下一行代码：

   ```text
   <button>Change user</button>
   ```

2. 在 `main.js 里，`在文件底部添加下面的代码，必须一字不漏——这会分别抓取按钮和标题的引用并将其存放在变量里：

   ```text
   var myButton = document.querySelector('button');
   var myHeading = document.querySelector('h1');
   ```

3. 现在添加下面的函数来设置个性化内容——这暂时不会起任何作用，不过我们后面会用到：

   ```text
   function setUserName() {
     var myName = prompt('Please enter your name.');
     localStorage.setItem('name', myName);
     myHeading.textContent = 'Mozilla is cool, ' + myName;
   }
   ```

   函数包含了一个 [`prompt()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window.prompt) 函数， 它会像 `alert()` 一样弹出一个对话框。只不过 `prompt()` 需要用户输入数据,，而且在用户点击确定后将数据存储在变量里。在这里，我们要求用户输入姓名。接下来我们调用一个叫 `localStorage` 的 API ，它允许我们将数据存储在浏览器里以供后续获取。我们使用 localStorage 的 `setItem()` 函数来创建并将数据存储在名为 `'name'` 的参数里，然后将它的值设置为包含用户输入的姓名的 `myName` 变量。 最后，我们将标题的 `textContent` 属性设置成加上用户姓名的字符串。

4. 接下来，添加这个 `if else` 块——我们将这称作初始化代码，因为它在初次读取时构造了这个应用程序：

   ```text
   if(!localStorage.getItem('name')) {
     setUserName();
   } else {
     var storedName = localStorage.getItem('name');
     myHeading.textContent = 'Mozilla is cool, ' + storedName;
   }
   ```

   这段代码首先用一个非运算符（逻辑非，用 ! 表示）来检查 `name` 数据是否存在。如果不存在， `setUserName()` 函数就会被运行来创建它。如果存在（用户之前创建过），我们通过 `getItem()` 调用存储过的姓名然后将 `textContent` 设置为加上用户姓名的字符串，就像在 `setUserName()` 里做过的一样。

5. 最后，将下面的 `onclick` 事件处理器绑定到按钮上，这样当我们点击按钮时， `setUserName()` 函数就会被运行。这样用户就可以随时通过点击按钮来设置新的姓名。

   ```text
   myButton.onclick = function() {
     setUserName();
   }
   ```

现在当你第一次访问网页时，它将询问你的用户名然后向你发出一段个性化的信息。你可以在任何时候通过点击按钮来改变用户名 。告诉你一个额外的福利，因为用户名是存放在 localStorage 里的，它会持续到网站关闭，所以这段个性化的信息在你重新打开浏览器时将仍然在这！

### 结论[Section](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics#%E7%BB%93%E8%AE%BA) <a id="&#x7ED3;&#x8BBA;"></a>

如果你一直跟随我们的指导，那么到最后你应该得到如下页面（你也可以在[这里](https://mdn.github.io/beginner-html-site-scripted/)查看我们的版本）：

![](https://mdn.mozillademos.org/files/9539/website-screen-scripted.png)

如果你有遇到问题，你可以将你的代码与我们GitHub上的[完整示例代码](https://github.com/mdn/beginner-html-site-scripted/blob/gh-pages/scripts/main.js)做对比。

在这里，我们只提到了非常有限的 JavaScript 知识。要查看更多，请访问我们的 [JavaScript指南](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript)。

