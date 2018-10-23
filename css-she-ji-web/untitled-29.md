# 组合器和多个选择器

在关于选择器的最后一篇文章中，我们将探讨组合器和选择器组 — 将多个选择器组合在一起以进一步利用其选择能力的两种方式。

### 组合器和选择器组[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#%E7%BB%84%E5%90%88%E5%99%A8%E5%92%8C%E9%80%89%E6%8B%A9%E5%99%A8%E7%BB%84) <a id="&#x7EC4;&#x5408;&#x5668;&#x548C;&#x9009;&#x62E9;&#x5668;&#x7EC4;"></a>

虽然一次使用一个选择器就很有用，但在某些情形中却可能效率低下。 CSS选择器在你开始组合他们进行细粒度选择的时候变得更具使用价值。基于元素之间的相互关联关系，CSS提供了几种方法来对元素进行选择。下表使用连接符展示了这些关联关系\(A和B代表前文所述的任意选择器\):

| 名称 | 组合器 | 选择 |
| :--- | :--- | :--- |
| 选择器组 | A,B | 匹配满足A（和/或）B的任意元素（参见下方 [同一规则集上的多个选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#%E5%90%8C%E4%B8%80%E8%A7%84%E5%88%99%E9%9B%86%E4%B8%8A%E7%9A%84%E5%A4%9A%E4%B8%AA%E9%80%89%E6%8B%A9%E5%99%A8)）. |
| 后代选择器 | A B A &gt;&gt; B | 匹配B元素，满足条件：B是A的后代结点（B是A的子节点，或者A的子节点的子节点） |
| 子选择器 | A &gt; B | 匹配B元素，满足条件：B是A的直接子节点 |
| 相邻兄弟选择器 | A + B | 匹配B元素，满足条件：B是A的下一个兄弟节点（AB有相同的父结点，并且B紧跟在A的后面） |
| 通用兄弟选择器 | A ~ B | 匹配B元素，满足条件：B是A之后的兄弟节点中的任意一个（AB有相同的父节点，B在A之后，但不一定是紧挨着A）      |

#### 组合器示例[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#%E7%BB%84%E5%90%88%E5%99%A8%E7%A4%BA%E4%BE%8B) <a id="&#x7EC4;&#x5408;&#x5668;&#x793A;&#x4F8B;"></a>

接下来看一个使用了组合器的例子:

```text
<table lang="en-US" class="with-currency">
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Qty.</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <th colspan="2" scope="row">Total:</th>
      <td>148.55</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Lawnchair</td>
      <td>1</td>
      <td>137.00</td>
    </tr>
    <tr>
      <td>Marshmallow rice bar</td>
      <td>2</td>
      <td>1.10</td>
    </tr>
    <tr>
      <td>Book</td>
      <td>1</td>
      <td>10.45</td>
    </tr>
  </tbody>
</table>
```

然后对该HTML文档应用下面的样式表:

```text
/* 基本的table样式 */
table {
  font: 1em sans-serif;
  border-collapse: collapse;
  border-spacing: 0;
}

/* 所有在table里的td以及th，这里的逗号不是一个组合器，
    它只是允许你把几个选择器对应到相同的CSS规则上.*/
table td, table th {
  border : 1px solid black;
  padding: 0.5em 0.5em 0.4em;
}

/* 所有table里的thead里的所有th */
table thead th {
  color: white;
  background: black;
}

/* 所有table里的tbody里的所有td（第一个除外），每个td都是由它上边的td选择 */
table tbody td + td {
  text-align: center;
}

/*table里所有的tbody里的td当中的最后一个 */
table tbody td:last-child {
  text-align: right
}

/* 所有table里的tfoot里的th */
table tfoot th {
  text-align: right;
  border-top-width: 5px;
  border-left: none;
  border-bottom: none;
}

/* 在table当中，所有的th之后的td */
table th + td {
  text-align: right;
  border-top-width: 5px;
  color: white;
  background: black;
}

/* 定位在“with-currency”类中拥有属性lang并且这个属性值为en-US的元素中的，最后td(:last-child)节点的前面（::before）*/
.with-currency[lang="en-US"] td:last-child::before {
  content: '$';
}

/* 定位在“with-currency”类中拥有属性lang并且这个属性值为fr的元素中的，最后td(:last-child)节点的后面（::after） */
.with-currency[lang="fr"] td:last-child::after {
  content: ' €';
}
```

这给了我们下面这个漂亮的表格样式:

在 CodePen 中打开在 JSFiddle 中打开

#### 主动学习: 写出属于你自己的组合器[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0_%E5%86%99%E5%87%BA%E5%B1%9E%E4%BA%8E%E4%BD%A0%E8%87%AA%E5%B7%B1%E7%9A%84%E7%BB%84%E5%90%88%E5%99%A8) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;_&#x5199;&#x51FA;&#x5C5E;&#x4E8E;&#x4F60;&#x81EA;&#x5DF1;&#x7684;&#x7EC4;&#x5408;&#x5668;"></a>

上面设计的例子是为了向你展示，你可以开始使用一些稍微复杂点的组合选择器。在这次的主动学习中，我们将会带你写点你自己的、更简单的组合选择器。在这个练习中，你需要在2~4规则集中添加选择器，来实现如下效果：

1. 设计链接的样式，但是只针对ul无序列表中的链接有效；
2. 设计ul列表里的链接样式，但是只当鼠标停留在上面时有效；
3. 设计只紧接着最大标题下的段落样式。                                                      

如果你遇到了错误, 可以点击“Reset”按钮进行重置。 要是真的被难住了, 按下“_Show solution_”按钮可以看到参考答案。

在 CodePen 中打开在 JSFiddle 中打开

###  应用同一规则的选择器组[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#%E5%BA%94%E7%94%A8%E5%90%8C%E4%B8%80%E8%A7%84%E5%88%99%E7%9A%84%E9%80%89%E6%8B%A9%E5%99%A8%E7%BB%84) <a id="&#x5E94;&#x7528;&#x540C;&#x4E00;&#x89C4;&#x5219;&#x7684;&#x9009;&#x62E9;&#x5668;&#x7EC4;"></a>

你已经遇见过这种做法的许多例子，但还是让我们来把它进一步阐释清楚。通过相互间用逗号分隔的多个选择器所形成的组，可以一次性将同一规则同时应用到多组选定元素。例如：

```text
p, li {
  font-size: 1.6em;
}
```

或者这样:

```text
h1, h2, h3, h4, h5, h6 {
  font-family: helvetica, 'sans serif';
}
```

### 接下来是什么[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#%E6%8E%A5%E4%B8%8B%E6%9D%A5%E6%98%AF%E4%BB%80%E4%B9%88) <a id="&#x63A5;&#x4E0B;&#x6765;&#x662F;&#x4EC0;&#x4E48;"></a>

恭喜,你已经来到了我们关于选择器学习的长途旅行的终点。即使是富有经验的web开发者仍然会惊讶于使用选择器所带来的可能性。所以，如果你无法记住所有选项的话，不必感到不快——把这个[选择器](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors)主页面添加到书签，方便你日后需要时进行回顾。

在我们的下一篇文章里，我们将会转向另一个非常重要的基础CSS话题——属性的值有哪些种类，以及表示长度、颜色或者其他你想要的值时可以用的单位。让我们来探索[CSS的值和单位](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units)。

