# 简单选择器

在我们的第一篇选择器文章中，我们将学习“简单”选择器，之所以这么称呼它是因为它们基于元素的类型（或其 `class`或 id）直接匹配文档的一个或多个元素。

### 类型选择器（又名元素选择器）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#%E7%B1%BB%E5%9E%8B%E9%80%89%E6%8B%A9%E5%99%A8%EF%BC%88%E5%8F%88%E5%90%8D%E5%85%83%E7%B4%A0%E9%80%89%E6%8B%A9%E5%99%A8%EF%BC%89) <a id="&#x7C7B;&#x578B;&#x9009;&#x62E9;&#x5668;&#xFF08;&#x53C8;&#x540D;&#x5143;&#x7D20;&#x9009;&#x62E9;&#x5668;&#xFF09;"></a>

此选择器只是一个选择器名和指定的HTML元素名的不区分大小写的匹配。这是选择所有指定类型的最简单方式。让我们一起看看下面这个例子:

这是HTML:

```text
<p>What color do you like?</p>
<div>I like blue.</div>
<p>I prefer red!</p>
```

这是样式表:

```text
/* All p elements are red */
p {
  color: red;
}

/* All div elements are blue */
div {
  color: blue;
}
```

我们将得到这个：

在 CodePen 中打开在 JSFiddle 中打开

### 主动学习：选取不同的元素[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E9%80%89%E5%8F%96%E4%B8%8D%E5%90%8C%E7%9A%84%E5%85%83%E7%B4%A0) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x9009;&#x53D6;&#x4E0D;&#x540C;&#x7684;&#x5143;&#x7D20;"></a>

在主动学习中，我们希望你尝试在简单的CSS规则上修改选择器，将样式渲染到例子中的不同元素上。你知道怎样写一个选择器将一组规则同时应用到多个元素上吗？

如果你犯了错误，你可以随时使用“重置”按钮。如果你有点不知所措，按下“显示”按钮可以看到可能的答案。

在 CodePen 中打开在 JSFiddle 中打开

### 类选择器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8) <a id="&#x7C7B;&#x9009;&#x62E9;&#x5668;"></a>

类选择器由一个点“.”以及类后面的类名组成。类名是在HTML [`class`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-class)文档元素属性中没有空格的任何值。由你自己选择一个名字。同样值得一提的是，文档中的多个元素可以具有相同的类名，而单个元素可以有多个类名\(以空格分开多个类名的形式书写\)。以下是一个简单的例子：

这是一些HTML：

```text
<ul>
  <li class="first done">Create an HTML document</li>
  <li class="second done">Create a CSS style sheet</li>
  <li class="third">Link them all together</li>
</ul>
```

这是一些CSS样式:

```text
/* The element with the class "first" is bolded */
.first {
  font-weight: bold;
}

/* All the elements with the class "done" are strike through */
.done {
  text-decoration: line-through;
}
```

我们得到这样一个结果:

在 CodePen 中打开在 JSFiddle 中打开

### 主动学习：处理多个类[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E5%A4%84%E7%90%86%E5%A4%9A%E4%B8%AA%E7%B1%BB) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x5904;&#x7406;&#x591A;&#x4E2A;&#x7C7B;"></a>

在本次主动学习中，我们想尝试更改段落元素上的类属性，以便您可以同时应用多个效果。 尝试应用类base-box，并附加一个role类（类名是editor-note或warning），用来表示这个框非常重要。 想想这种规则集允许你建立一个模块化的风格系统。

如果您犯了错误，您可以随时使用重置按钮重设。 如果您确实卡住了，请按显示解决方案按钮查看潜在答案。

在 CodePen 中打开在 JSFiddle 中打开

### ID 选择器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#ID_%E9%80%89%E6%8B%A9%E5%99%A8) <a id="ID_&#x9009;&#x62E9;&#x5668;"></a>

ID选择器由哈希/磅符号 \(`#`\)组成，后面是给定元素的ID名称。 任何元素都可以使用[`id`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-id)属性设置唯一的ID名称。 由你自己选择的ID是什么。 这是选择单个元素的最有效的方式。

**重要提示**：一个ID名称必须在文件中是唯一的。关于重复ID的行为是不可预测的，比如在一些浏览器只是第一个实例计算，其余的将被忽略。

我们来看一个简单的例子 - 这是HTML：

```text
<p id="polite"> — "Good morning."</p>
<p id="rude"> — "Go away!"</p>
```

这是样式表：

```text
#polite {
  font-family: cursive;
}

#rude {
  font-family: monospace;
  text-transform: uppercase;
}
```

而我们得到这个作为输出：

在 CodePen 中打开在 JSFiddle 中打开

### 主动学习：依据不同 ID 分配获胜者的颜色[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E4%BE%9D%E6%8D%AE%E4%B8%8D%E5%90%8C_ID_%E5%88%86%E9%85%8D%E8%8E%B7%E8%83%9C%E8%80%85%E7%9A%84%E9%A2%9C%E8%89%B2) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x4F9D;&#x636E;&#x4E0D;&#x540C;_ID_&#x5206;&#x914D;&#x83B7;&#x80DC;&#x8005;&#x7684;&#x989C;&#x8272;"></a>

在本次主动学习中，我们希望您通过2-4个合适的基于相关ID的CSS选择器规则，使冠军、亚军、季军显示对应的金、银、铜三种颜色。

如果你犯了一个错误，你可以使用_重置_按钮。如果你得到真正卡住，按_显示的解决方案_按钮，看到一个可行的答案。

在 CodePen 中打开在 JSFiddle 中打开

### 通用选择器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#%E9%80%9A%E7%94%A8%E9%80%89%E6%8B%A9%E5%99%A8) <a id="&#x901A;&#x7528;&#x9009;&#x62E9;&#x5668;"></a>

通用选择（`*`）是最终的王牌。它允许选择在一个页面中的所有元素。由于给每个元素应用同样的规则几乎没有什么实际价值，更常见的做法是与其他选择器结合使用\(参考下面 [组合](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#%E7%BB%84%E5%90%88) .\)

**重要提示**：使用通用选择时小心。因为它适用于所有的元素，在大型网页利用它可能对性能有明显的影响：网页可能显示比预期要慢。大多数情况下，你都不会使用这个选择器。

例如，这是HTML：

```text
<div>
  <p>I think the containing box just needed
  a <strong>border</strong> or <em>something</em>,
  but this is getting <strong>out of hand</strong>!</p>
</div>
```

这是样式表：

```text
* {
  padding: 5px;
  border: 1px solid black;
  background: rgba(255,0,0,0.25)
}
```

组合在一起，会得到这样的结果：

在 CodePen 中打开在 JSFiddle 中打开

### 下一篇文章[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors#%E4%B8%8B%E4%B8%80%E7%AF%87%E6%96%87%E7%AB%A0) <a id="&#x4E0B;&#x4E00;&#x7BC7;&#x6587;&#x7AE0;"></a>

干得好！我们的第一篇选择器教程结束了！希望你找到你的乐趣。现在我们已经学习了我们最常使用简单的核心选择器，让我们开始学习一些更先进的功能：[属性选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors)。

