# 属性选择器

属性选择器是一种特殊类型的选择器，它根据元素的 [属性](https://developer.mozilla.org/en-US/docs/Glossary/attribute) 和属性值来匹配元素。它们的通用语法由方括号 \(`[]`\) 组成，其中包含属性名称，后跟可选条件以匹配属性的值。 属性选择器可以根据其匹配属性值的方式分为两类： 存在和值属性选择器和子串值属性选择器。

### 存在和值（Presence and value）属性选择器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors#%E5%AD%98%E5%9C%A8%E5%92%8C%E5%80%BC%EF%BC%88Presence_and_value%EF%BC%89%E5%B1%9E%E6%80%A7%E9%80%89%E6%8B%A9%E5%99%A8) <a id="&#x5B58;&#x5728;&#x548C;&#x503C;&#xFF08;Presence_and_value&#xFF09;&#x5C5E;&#x6027;&#x9009;&#x62E9;&#x5668;"></a>

这些属性选择器尝试匹配精确的属性值：

* `[attr]`：该选择器选择包含 attr 属性的所有元素，不论 attr 的值为何。
* `[attr=val]`：该选择器仅选择 attr 属性被赋值为 val 的所有元素。
* `[attr~=val]`：该选择器仅选择具有 attr 属性的元素，而且要求 `val` 值是 `attr` 值包含的被空格分隔的取值列表里中的一个。

让我们看一个特别的例子，下面是它的的HTML代码：

```text
我的食谱配料: <i lang="fr-FR">Poulet basquaise</i>
<ul>
  <li data-quantity="1kg" data-vegetable>Tomatoes</li>
  <li data-quantity="3" data-vegetable>Onions</li>
  <li data-quantity="3" data-vegetable>Garlic</li>
  <li data-quantity="700g" data-vegetable="not spicy like chili">Red pepper</li>
  <li data-quantity="2kg" data-meat>Chicken</li>
  <li data-quantity="optional 150g" data-meat>Bacon bits</li>
  <li data-quantity="optional 10ml" data-vegetable="liquid">Olive oil</li>
  <li data-quantity="25cl" data-vegetable="liquid">White wine</li>
</ul>
```

和一个简单的样式表：

```text
/* 所有具有"data-vegetable"属性的元素将被应用绿色的文本颜色 */
[data-vegetable] {
  color: green
}

/* 所有具有"data-vegetable"属性且属性值刚好为"liquid"的元素将被应用金色的背景颜色 */
[data-vegetable="liquid"] {
  background-color: goldenrod;
}

/* 所有具有"data-vegetable"属性且属性值包含"spicy"的元素，
即使元素的属性中还包含其他属性值，都会被应用红色的文本颜色 */
[data-vegetable~="spicy"] {
  color: red;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

**笔记**：本例中的 `data-*` 属性被称为 [数据属性](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes/data-*)。它们提供了一种在HTML属性中存储自定义数据的方法，由此，这些数据可以轻松地被提取和使用。有关详细信息，请参阅 [如何使用数据属性](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Using_data_attributes)。

### 子串值（Substring value）属性选择器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors#%E5%AD%90%E4%B8%B2%E5%80%BC%EF%BC%88Substring_value%EF%BC%89%E5%B1%9E%E6%80%A7%E9%80%89%E6%8B%A9%E5%99%A8) <a id="&#x5B50;&#x4E32;&#x503C;&#xFF08;Substring_value&#xFF09;&#x5C5E;&#x6027;&#x9009;&#x62E9;&#x5668;"></a>

这种情况的属性选择器也被称为“伪正则选择器”，因为它们提供类似 [regular expression](https://developer.mozilla.org/en-US/docs/Glossary/regular_expression) 的灵活匹配方式（但请注意，这些选择器并不是真正的正则表达式）：

* `[attr|=val]` : 选择attr属性的值是 `val` 或值以 `val-` 开头的元素（注意，这里的 “-” 不是一个错误，这是用来处理语言编码的）。
* `[attr^=val]` : 选择attr属性的值以 `val` 开头（包括 `val`）的元素。
* `[attr$=val]` : 选择attr属性的值以 `val` 结尾（包括 `val`）的元素。
* `[attr*=val]` : 选择attr属性的值中包含子字符串 `val` 的元素（一个子字符串就是一个字符串的一部分而已，例如，”cat“ 是 字符串 ”caterpillar“ 的子字符串）。

让我们继续我们前面的例子，并添加以下CSS规则：

```text
/* 语言选择的经典用法 */
[lang|="fr"] {
  font-weight: bold;
}

/* 
    具有"data-vegetable"属性含有值"not spicy"的所有元素,都变回绿色
*/
[data-vegetable*="not spicy"] {
  color: green;
}

/* 
   具有"data-quantity"属性其值以"kg"结尾的所有元素*/
[data-quantity$="kg"] {
  font-weight: bold;
}

/* 
   具有属性"data-quantity"其值以"optional"开头的所有元素 
*/
[data-quantity^="optional"] {
  opacity: 0.5;
}
```

有了这些新的规则，我们会得到这个：

在 CodePen 中打开在 JSFiddle 中打开

### 主动学习：给足球比赛结果添加样式[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E7%BB%99%E8%B6%B3%E7%90%83%E6%AF%94%E8%B5%9B%E7%BB%93%E6%9E%9C%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x7ED9;&#x8DB3;&#x7403;&#x6BD4;&#x8D5B;&#x7ED3;&#x679C;&#x6DFB;&#x52A0;&#x6837;&#x5F0F;"></a>

在这个积极的学习中，我们希望您尝试添加属性选择器到一些规则来创建一个简单的足球结果列表。 这里有三件事要做：

* 前三个规则分别在列表项的左侧添加英国，德国和西班牙国旗图标。 您需要填写适当的属性选择器，以便球队获得正确的国家标志，并配合语言。
* 规则4-6在列表项中添加背景颜色，以指示球队是否已经在联盟中升格（绿色，rgba（0,255,0,0.7）），向下（红色，rgba（255,0,0,0.5）） ），或者留在同一个地方（蓝色，rgba（0,0,255,0.5））。填写适当的属性选择器，以将正确的颜色与正确的队列匹配，并与inc，相同和dec字符串匹配 data-perf属性值。
* 规则7-8使得晋级的球队变得加粗，有降级危险的球队为斜体和灰色。 填写适当的属性选择器，将这些样式与正确的队列进行匹配，并与data-perf属性值中显示的pro和rel字符串进行匹配。

如果您犯了错误，您可以随时使用重置按钮重设。 如果您确实卡住了，请按显示解决方案按钮查看可行答案。

在 CodePen 中打开在 JSFiddle 中打开

### 相关链接[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors#%E7%9B%B8%E5%85%B3%E9%93%BE%E6%8E%A5) <a id="&#x76F8;&#x5173;&#x94FE;&#x63A5;"></a>

查看 [Attribute selectors](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Attribute_selectors) 参考页获取更多有用的例子。

### 接下来[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors#%E6%8E%A5%E4%B8%8B%E6%9D%A5) <a id="&#x63A5;&#x4E0B;&#x6765;"></a>

接下来，让我们再上一层楼，看看 [伪类和伪元素](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Selectors/Pseudo-classes_and_pseudo-elements)。

