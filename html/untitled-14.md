# 标记字母

我们或早或晚都会学会如何写信，这也是一个不错的测试我们文本格式化技巧的例子！ 在此评估中，我们会给你一封写好的信用来标记，以测验你基础和高级的HTML文本格式化技巧，包括超链接。此外我们将测试你对一些HTML `<head>`内容的熟悉程度。

| 先决条件： | 在尝试此评估之前，你应该已经看过[Getting started with HTML](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Getting_started) 、[What’s in the head? Metadata in HTML](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML)、[HTML text fundamentals](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/HTML_text_fundamentals) 、[Creating hyperlinks](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)和[Advanced text formatting](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting)。 |
| :--- | :--- |
| 目的： | 测试基本和高级HTML文本格式和超链接技能，了解HTML &lt;head&gt;中的内容。 |

### 起点[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Marking_up_a_letter#%E8%B5%B7%E7%82%B9) <a id="&#x8D77;&#x70B9;"></a>

开始评估之前，你应该先复制一份[要标记的原始文本](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/marking-up-a-letter-start/letter-text.txt)，和HTML[需要导入的CSS代码](https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/marking-up-a-letter-start/css.txt)，然后 用你的文本编辑器创建一个新的`.html`文件来进行评估（或者用[JSBin](http://jsbin.com/)或[Thimble](https://thimble.mozilla.org/)等网站来进行评估）。

### 项目概要[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Marking_up_a_letter#%E9%A1%B9%E7%9B%AE%E6%A6%82%E8%A6%81) <a id="&#x9879;&#x76EE;&#x6982;&#x8981;"></a>

在这个项目里，你的任务是标记一封放在大学内网上的信，这封信是研究人员对一名未来的博士生的回复，关于他们在大学工作的申请。

块/结构语义：

* 你应该使用适当的结构来构造整体文档，包括doctype、[`<html>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/html) 、 [`<head>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/head)和[`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body)元素。
* 除下面提到的几点之外，这封信应该被标记成有着段落和标题的结构。 这封信有一个顶级标题（“Re：”那行）和三个二级标题。
* 使用适当类型的列表标记该学期的开学时间、学习科目和外国舞蹈。
* 那两个地址可以就放在段落中，且 [`<address>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/address)元素不适合他们——想一下为什么。此外，地址的每一行都应该另开新行，但不是新的段落。

内联语义：

* 显著标明发信人和收信人的姓名（以及“电话”和“电子邮件”）。
* 用适当的元素把文档中的四个日期标记成机器可读的日期。
* 把信中第一个地址和第一个日期的类属性设置成“sender-column”，这样你添加的CSS就可以使它们右对齐，就像经典的信件布局里的一样。
* 标记出信件正文中的五个首字母缩略词或缩写的扩展形式。
* 适当标注六个下标/上标。
* 用适当的字符实体引用来标记大于号、乘号和度符号。
* 试着标记至少两个适当的、具有很强重要性/重点（strong importance/emphasis）单词。
* 有两个地方应加上超链接，为它们添加适当的标题。链接指向http://example.com就行。
* 应该用适当的元素标记大学的座右铭引用和引文。

文档的头部：

* 用适当的meta标签把文档的字符集声明为utf-8。
* 用适当的meta标签说明信件的作者。
* 用适当的标签引入我们提供的CSS代码。

### 提示和技巧[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Marking_up_a_letter#%E6%8F%90%E7%A4%BA%E5%92%8C%E6%8A%80%E5%B7%A7) <a id="&#x63D0;&#x793A;&#x548C;&#x6280;&#x5DE7;"></a>

* 使用[W3C HTML验证器](https://validator.w3.org/)来验证HTML，如果验证通过，你会得到奖励积分。
* 完成这个评估不需要任何CSS知识，你只需要把已提供的CSS放到HTML元素里就好。

### 范例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Marking_up_a_letter#%E8%8C%83%E4%BE%8B) <a id="&#x8303;&#x4F8B;"></a>

下面的截图展示了这封信被标记完成之后可能会是什么样子。

![](https://mdn.mozillademos.org/files/12291/letter-screengrab.png)

### 评估[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Marking_up_a_letter#%E8%AF%84%E4%BC%B0) <a id="&#x8BC4;&#x4F30;"></a>

如果这个评估是一系列课程的一部分，你应该可以让你的老师或导师为你批改。 如果你是自学，可以很容易地在[Learning Area Discourse thread](https://discourse.mozilla-community.org/t/learning-web-development-marking-guides-and-questions/16294)或[Mozilla IRC](https://wiki.mozilla.org/IRC)的[\#mdn](irc://irc.mozilla.org/mdn) IRC频道回复得到批改指南。请先自己试着做——作弊学不到任何东西！

