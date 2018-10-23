# HTML 调试

写HTML是非常容易的，但如果某部分出了问题并且你找不到错误代码在哪里的时候，本文将向您介绍一些可以帮助您查找和修复HTML中的错误的工具。

| 先决条件: | 熟悉HTML ，例如已经阅读了 [Getting started with HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Getting_started)，[HTML text fundamentals](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals)，和 [Creating hyperlinks](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)。 |
| :--- | :--- |
| 目标: | 学习基础使用调试工具查找HTML中的错误。 |

### 调试并不可怕[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML#%E8%B0%83%E8%AF%95%E5%B9%B6%E4%B8%8D%E5%8F%AF%E6%80%95) <a id="&#x8C03;&#x8BD5;&#x5E76;&#x4E0D;&#x53EF;&#x6015;"></a>

在编写某种代码时，通常一切都是正常的，直到你犯了某个错误那可怕的时刻便发生了，你的代码无效了 — 无论这是不是你想要的。例如下面，当我们想用[compile](https://developer.mozilla.org/en-US/docs/Glossary/compile)Rust语言去写一个简单的程序的时候，错误报告便会出现。

![A console window showing the result of trying to compile a rust program with a missing quote around a string in a print statement. The error message reported is error: unterminated double quote string.](https://mdn.mozillademos.org/files/12435/error-message.png)这里错误信息比较容易理解 — "双引号字符串未闭合"。如果你查看列表，你大概会看到`(Hello, world!");` 这里缺少了一个双引号 ，然而当程序变庞大的时候错误信息也会变得更复杂和更难解释，甚至上面这样简单的例子对于不了解Rust语言的人来说就会有点吓人。

调试没有那么可怕 —  编写和调试任何编程语言的关键是熟悉这门语言和工具。

### HTML和调试[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML#HTML%E5%92%8C%E8%B0%83%E8%AF%95) <a id="HTML&#x548C;&#x8C03;&#x8BD5;"></a>

HTML并不像Rust语言那么难以理解 — 在浏览器解析和显示它之前HTML不会被编译成其他形式  \(这是解析而不是编译\) HTML的[element](https://developer.mozilla.org/en-US/docs/Glossary/element) 语法可以说比“像Rust的”[JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript) 或 [Python](https://developer.mozilla.org/en-US/docs/Glossary/Python)这样“真正的编程语言”更容易理解. 然而浏览器运行HTML比编程语言的运行更宽松，这可以说是好事也是坏事。

#### 宽容模式代码[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML#%E5%AE%BD%E5%AE%B9%E6%A8%A1%E5%BC%8F%E4%BB%A3%E7%A0%81) <a id="&#x5BBD;&#x5BB9;&#x6A21;&#x5F0F;&#x4EE3;&#x7801;"></a>

宽容的意思是什么呢？通常当你写错代码的时候，你会遇到以下两种主要类型的错误：

* **语法错误**: 由于拼写错误导致程序无法运行，就像上面Rust的例子. 修正这些错误是没问题的，只要你熟悉正确的使用工具和知道错误信息的意思。
* **逻辑错误**: 实际上语法是正确的，但代码不是你想要的，这意味着程序运行不正确. 逻辑错误通常比语法错误更难修复，因为没有一个错误信息指示你到错误的来源。

HTML本身不容易因语法错误出错，因为浏览器是以宽松模式来运行，这意味着即使出现语法错误浏览器依然会运行。浏览器通常都有自己的规则来解析语法错误的标记语言，所以程序仍然会运行，尽管可能不是你预期的样子。这样当然仍然会带来问题。

**注意**: HTML可以自由的运行，是因为在 Web 创建之初，它的宗旨就是：允许人们获取他们发布的内容比确保所有语法完全正确更重要。如果当初 Web 在一开始就更加严格的话，也许 Web 就不会像今天这样流行了。

#### 主动学习: 学习宽容式代码风格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0_%E5%AD%A6%E4%B9%A0%E5%AE%BD%E5%AE%B9%E5%BC%8F%E4%BB%A3%E7%A0%81%E9%A3%8E%E6%A0%BC) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;_&#x5B66;&#x4E60;&#x5BBD;&#x5BB9;&#x5F0F;&#x4EE3;&#x7801;&#x98CE;&#x683C;"></a>

现在到你自己学习 HTML 代码宽松特性的时候了。

1. 首先，找到我们的 [debug-example demo](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/debugging-html/debug-example.html) 副本并保存到本地。这里故意写了一些错误在代码中，以便我们探究（HTML 标记被写成了**糟糕的格式**，与 **良好的格式**相反）。
2. 接着，在浏览器中打开—你会看到下面的样子：![A simple HTML document with a title of HTML debugging examples, and some information about common HTML errors, such as unclosed elements, badly nested elements, and unclosed attributes. ](https://mdn.mozillademos.org/files/12437/badly-formed-html.png)
3. 这看起来一点儿也不好；让我们来看看源代码，看看我们是否能找出为什么（只显示了 body 的内容）：

   ```text
   <h1>HTML debugging examples</h1>

   <p>What causes errors in HTML?

   <ul>
     <li>Unclosed elements: If an element is <strong>not closed properly,
         then its effect can spread to areas you didn't intend

     <li>Badly nested elements: Nesting elements properly is also very important
         for code behaving correctly. <strong>strong <em>strong emphasised?</strong>
         what is this?</em>

     <li>Unclosed attributes: Another common source of HTML problems. Let's
         look at an example: <a href="https://www.mozilla.org/>link to Mozilla
         homepage</a>
   </ul>
   ```

4. 让我们检查一下这里看到的问题：
   * [paragraph](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 和 [list item](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/li) 元素没有结束标签。看看上面的图片，看起来对标记并没有导致太严重的影响，因为很容易推断出一个元素应该在哪里结束，在哪里开始。
   * 第一个 [`<strong>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong) 元素没有结束标签。这问题有一点大，因为不太容易确定元素在哪里结束。事实上，整个剩下的文本都被加粗强调了。
   * 这部分代码嵌套很糟糕：`<strong>strong <em>strong emphasised?</strong> what is this?</em>`。由于之前的问题，要解释这是如何解析的并不容易。
   * [`href`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a#attr-href) 属性缺少了一个双引号。这导致了最大的问题—链接完全没有解析出来。
5. 现在我们看看浏览器渲染出来的标记语言，而不是源代码中的标记语言。我们打开浏览器的开发者工具。如果你对这个不太熟悉的话，先浏览一下[Discover browser developer tools](https://developer.mozilla.org/zh-CN/docs/Learn/Discover_browser_developer_tools)。
6. 在开发者模式中的审查器件，你可以看到被渲染出来的标记语言会像这样。![The HTML inspector in Firefox, with our example&apos;s paragraph highlighted, showing the text &quot;What causes errors in HTML?&quot; Here you can see that the paragraph element has been closed by the browser.](https://mdn.mozillademos.org/files/12439/html-inspector.png)
7. 使用开发者模式下的审查器，可以非常清楚地看到浏览器尝试修补我们的代码错误（下面是火狐浏览器中的情况，其他浏览器也会进行修补）
   * 段落和类表元素被加上了闭合标签。
   * 第一个&lt;strong&gt;标签闭合的位置并不明确，因此浏览器用自己的&lt;strong&gt;标签将每一块分离的文本包括了进来，就在文档的底部。
   * 浏览器像下面这样修补嵌套错误：

     ```text
     <strong>strong
       <em>strong emphasised?</em>
     </strong>
     <em> what is this?</em>
     ```

   * 有错误属性的链接整个被删掉了。最后一个列表元素就像这样：

     ```text
     <li>
       <strong>Unclosed attributes: Another common source of HTML problems.
       Let's look at an example: </strong>
     </li>
     ```

#### HTML验证[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML#HTML%E9%AA%8C%E8%AF%81) <a id="HTML&#x9A8C;&#x8BC1;"></a>

看了上面的例子之后，你应该会希望自己的HTML格式正确。那么应该如何做呢？上面的例子都是一些非常小的错误，因此稍微浏览一下自己的代码就可以发现，但是如果是一个非常庞大、复杂的HTML文档呢？

最好的方法就是让你的HTML页面通过 [Markup Validation Service](https://validator.w3.org/) — 由W3C创立并维护的，这个网站紧跟定义 HTML，CSS，和其他网络技术的具体内容. 这个网页将 HTML 文档作为输入,并运行 ，然后给你一个报告告诉你你的 HTML 有哪些错误.

![The HTML validator homepage](https://mdn.mozillademos.org/files/12441/validator.png)

为了确定需要验证的HTML，你可以输入一个指向该HTML页面的网址，或者上传一份HTML文件，或者直接输入一些HTML代码。

#### 主动学习：验证一份HTML文档[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E9%AA%8C%E8%AF%81%E4%B8%80%E4%BB%BDHTML%E6%96%87%E6%A1%A3) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x9A8C;&#x8BC1;&#x4E00;&#x4EFD;HTML&#x6587;&#x6863;"></a>

让我们用[sample document](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/debugging-html/debug-example.html)尝试一下：

1. 在浏览器中打开 [Markup Validation Service](https://validator.w3.org/) 。
2. 点击或者激活 [Validate by Direct Input](https://validator.w3.org/#validate_by_input) 栏。
3. 将整个示范文档的代码（不仅仅是body部分）复制粘贴到在Markup Validation Service中显示的巨大的文本框。
4. _点击Check按钮。_

然后就会出现一张列表，显示了文档中的错误或者其他信息。

![A list of of HTML validation results from the W3C markup validation service](https://mdn.mozillademos.org/files/12443/validation-results.png)

**解析错误信息**

展示在你眼前的错误信息列表可能会很有用，也可能并没有帮助。经过一点点练习你就会知道如何解析这些错误从而修复错误。让我们来浏览一下这些错误信息的含义。你会看到每一行都有一个数字和信息栏，来帮助你轻松定位错误。

* End tag `li` implied, but there were open elements（隐含着结束标签 `li` ，但却出现了元素的开始标签；共两个）: 这条信息表明一个元素的开始标签应该对应着一个结束标签，结束标签是隐含的，但实际上并不存在。行/列（line/column）信息指出那一行代码的下一行是结束标签应该出现的地方，这已经足够看出问题所在了。
* Unclosed element `strong`（未闭合标签 `strong` ）：这是非常容易理解的，一个[`<strong>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/strong)元素没有闭合，行/列信息指出了它所在之处。
* End tag `strong` violates nesting rules（结束标签 `strong` 违反了嵌套规则）：指出了错误嵌套的元素，行/列信息表明了错误所在。
* End of file reached when inside an attribute value. Ignoring tag（在属性值内达到文件末尾。忽略标签）: 这个比较难懂，它说的是在某个地方有一个属性的值没有正确构成，估计是在文件末尾附近，因为文件的结尾（EOF）出现在了一个属性值里。事实上浏览器没有渲染超链接就已经告诉我们错误出在哪个元素了。
* End of file seen and there were open elements（文件结尾有未闭合的元素）：这个有点意义不明，但基本上表明了有元素没有正确闭合。行号指向文件最后几行，且错误信息给出了一个这种错误的案例：

  ```text
  example: <a href="https://www.mozilla.org/>link to Mozilla homepage</a> ↩ </ul>↩ </body>↩</html>
  ```

  **注意**: 一个缺少结束引号标记的属性会导致一个未闭合的元素，因为其余的文档被解析为了属性的内容。

* Unclosed element `ul`（未闭合元素 `ul`）：这个不是很有帮助，因为 [`<ul>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul)已经正确闭合了。出现这个错误是因为那个[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)元素因少了右引号而没有闭合。

如果你不能一次弄懂所有的错误，别着急，你可以试试先修复那些你已经弄懂的错误，然后再申请验证，看看剩下的错误是哪些。有时候最先修复的错误可能让你摆脱了后面一系列的错误——因为一个小问题可能引发好几个错误，就像连锁反应。

当你所有的错误都修复之后，会得到下面的输出。

![Banner that reads &quot;The document validates according to the specified schema\(s\) and to additional constraints checked by the validator.&quot;](https://mdn.mozillademos.org/files/12445/valid-html-banner.png)

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

这就是我们关于HTML调试的介绍，这应该也会帮助你调试CSS和JavaScript，或者你未来遇到的任何一种语言。这也是HTML模块学习的最后一篇文章，现在你可以用我们给你布置的任务来测试一下自己：下面的第一个链接。

