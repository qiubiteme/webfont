# HTML表格高级特性和可访问性

这个模块的第二篇文章中，我们来看一下 HTML 表格更高级的功能，比如像 表格的标题/摘要，以及将你表格中的各行分组成头部、正文、页脚部分，提高视力受损用户的可访问性。

| 学习本章节的前提条件: | HTML 的基础知识 \(see [Introduction to HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)\). |
| :--- | :--- |
| 目的: | 学习 HTML 表格进一步的功能，以及表格的无障碍访问性。 |

### 使用 &lt;caption&gt; 为你的表格增加一个标题[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E4%BD%BF%E7%94%A8_%3Ccaption%3E_%E4%B8%BA%E4%BD%A0%E7%9A%84%E8%A1%A8%E6%A0%BC%E5%A2%9E%E5%8A%A0%E4%B8%80%E4%B8%AA%E6%A0%87%E9%A2%98) <a id="&#x4F7F;&#x7528;_&lt;caption&gt;_&#x4E3A;&#x4F60;&#x7684;&#x8868;&#x683C;&#x589E;&#x52A0;&#x4E00;&#x4E2A;&#x6807;&#x9898;"></a>

你可以为你的表格增加一个标题，通过 [`<caption>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/caption) 元素，再把 [`<caption>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/caption) 元素放入 [`<table>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/table) 元素中. 你应该把它放在`<table>` 标签的下面。

```text
<table>
  <caption>Dinosaurs in the Jurassic period</caption>

  ...
</table>
```

从上面简单的例子可以推断，标题意味着包含对于表格内容的描述，这对那些希望可以快速浏览网页中的表格对他们是否有帮助的读者们来说，是非常好的功能。特别是盲人用户，不需要让屏幕阅读设备读出很多单元格的内容，来让用户了解这张表格讲的是什么，而是可以依靠标题的内容，来决定是否需要了解更详细的内容。

标题就放在 `<table>` 标签的下面。

**注意**: 这个 [`summary`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/table#attr-summary) 属性也可以在`<table>` 元素中使用，用来提供一段描述，同样可以被屏幕阅读设备阅读。我们推荐使用 `<caption>` 元素来代替使用，因为 `summary` 被 HTML5 规范， [deprecated](https://developer.mozilla.org/zh-CN/docs/Glossary/deprecated) \(废除了\)，也不能被视力正常的用户阅读。 \(它不会出现在页面上\)

#### 动手练习: 添加一个标题[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E5%8A%A8%E6%89%8B%E7%BB%83%E4%B9%A0_%E6%B7%BB%E5%8A%A0%E4%B8%80%E4%B8%AA%E6%A0%87%E9%A2%98) <a id="&#x52A8;&#x624B;&#x7EC3;&#x4E60;_&#x6DFB;&#x52A0;&#x4E00;&#x4E2A;&#x6807;&#x9898;"></a>

我们来试试看吧，回顾一下我们在之前的文章中第一次遇到的例子。.

1. 打开你的语言老师的学校时间表，就是 [HTML Table Basics](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics#Active_learning_colgroup_and_col) 结尾中的例子，或者把 [timetable-fixed.html](https://github.com/mdn/learning-area/blob/master/html/tables/basic/timetable-fixed.html) 文件复制下面.
2. 为表格添加一个合适的标题。
3. 保存你的代码，然后用浏览器打开，看看你的表格是什么样的。

**注意**:你也可以在 GitHub 上找到我们的版本 [timetable-caption.html](https://github.com/mdn/learning-area/blob/master/html/tables/advanced/timetable-caption.html) \([see it live also](http://mdn.github.io/learning-area/html/tables/advanced/timetable-caption.html)\).

### 添加 &lt;thead&gt;, &lt;tfoot&gt;, 和 &lt;tbody&gt; 结构[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E6%B7%BB%E5%8A%A0_%3Cthead%3E_%3Ctfoot%3E_%E5%92%8C_%3Ctbody%3E_%E7%BB%93%E6%9E%84) <a id="&#x6DFB;&#x52A0;_&lt;thead&gt;_&lt;tfoot&gt;_&#x548C;_&lt;tbody&gt;_&#x7ED3;&#x6784;"></a>

由于你的表格在结构上有点复杂，如果把它们定义得更加结构化，那会帮助我们更能了解结构。一个明确的方法是使用 [`<thead>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/thead),  [`<tfoot>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tfoot),和 [`<tbody>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/tbody), 这些元素允许你把表格中的部分标记为表头、页脚、正文部分。

这些元素不会使表格更易于屏幕阅读器用户访问，也不会造成任何视觉上的改变。然而，它们在应用样式和布局上会起到作用，可以更好地让 CSS 应用到表格上。给你一些有趣的例子，在长表格的情况下，你可以在每个打印页面上使表格页眉和页脚重复，你也可以让表格的正文部分显示在一个单独的页面上，并通过上下滚动来获得内容。

试着使用它们:

*  `<thead>` 需要嵌套在 table 元素中，放置在头部的位置，因为它通常代表第一行，第一行中往往都是每列的标题，但是不是每种情况都是这样的。如果你使用了 [`<col>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/col)/[`<colgroup>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/colgroup) 元素，那么 `<thead>`元素就需要放在它们的下面。
*  `<tfoot>` 需要嵌套在 table 元素中，放置在底部 \(页脚\)的位置，一般是最后一行，往往是对前面所有行的总结，比如，你可以按照预想的方式将`<tfoot>`放在表格的底部，或者就放在 `<thead>` 的下面。\(浏览器仍将它呈现在表格的底部\)
*  `<tbody>` 需要嵌套在 table 元素中，放置在 `<thead>`的下面或者是 `<tfoot>` 的下面，这取决于你如何设计你的结构。\(`<tfoot>`放在`<thead>`下面也可以生效.\)

**注意**: `<tbody>` 总是包含在每个表中，如果你没有在代码中指定它，那就是隐式的。可以来验证一下，打开一个你之前没有包含 `<tbody>` 的例子，然后在你的 [browser developer tools](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools) 中观察你的代码，你会看到浏览器为你添加了这个标签。你也许会想问，为什么你应该在所有表中都需要这个元素，因为它可以让你更好地控制表格结构和样式。

#### 动手练习: 添加表格结构[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E5%8A%A8%E6%89%8B%E7%BB%83%E4%B9%A0_%E6%B7%BB%E5%8A%A0%E8%A1%A8%E6%A0%BC%E7%BB%93%E6%9E%84) <a id="&#x52A8;&#x624B;&#x7EC3;&#x4E60;_&#x6DFB;&#x52A0;&#x8868;&#x683C;&#x7ED3;&#x6784;"></a>

让我们动手使用这些新元素。

1. 首先，把 [spending-record.html](https://github.com/mdn/learning-area/blob/master/html/tables/advanced/spending-record.html) 和 [minimal-table.css](https://github.com/mdn/learning-area/blob/master/html/tables/advanced/minimal-table.css) 拷贝到你的本地环境。
2. 尝试在浏览器中打开它，你会发现看起来不错，但是它可以被改善得更好。 "SUM" 行包含了已经使用的金额的总和，不过它出现在了错误的位置，以及代码中还遗失了一些细节。
3. 将明显的标题行改为使用 `<thead>` 元素，"SUM" 行使用 `<tfoot>` 元素，剩余的内容使用 `<tbody>` 元素。
4. 先保存，再刷新。你会看到，添加了 `<tfoot>` 元素后，导致 "SUM" 这行跑到了表格的底部。
5. 接着, 添加一个 [`colspan`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/td#attr-colspan) 属性，使 "SUM" 单元格占 4 个单元格的位置，所以实际数字是显示在 “Cost” 列的底部。
6. 让我们为表格添加一些简单的额外属性，能够让你理解这些属性是如何帮助更好地让表格应用 CSS 的。在你的 HTML 文件的 head 标签部分，你会看到一个空的 [`<style>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/style) 元素. 在 style 元素中添加下列 CSS 代码：

   ```text
   tbody {
     font-size: 90%;
     font-style: italic;
   }

   tfoot {
     font-weight: bold;
   }
   ```

7. 先保存，再刷新，然后观察一下结果。如果没有 `<tbody>` 和 `<tfoot>` 元素，你也许会写更加复杂的选择器来应用同样的样式。

**注意**: 我们并不期望目前你可以理解所有 CSS 的内容。当你经过我们的 CSS 模块的时候，你应该会了解更多 \([Introduction to CSS](https://developer.mozilla.org/zh_CN/docs/Learn/CSS/Introduction_to_CSS) 是一个好的起点；我们也有专门的文章 [styling tables](https://developer.mozilla.org/zh_CN/docs/Learn/CSS/Styling_boxes/Styling_tables)\).

你完成的表格应该如下所示：

**注意**: 你也可以在 GitHub 上找到 [spending-record-finished.html](https://github.com/mdn/learning-area/blob/master/html/tables/advanced/spending-record-finished.html) \([see it live also](http://mdn.github.io/learning-area/html/tables/advanced/spending-record-finished.html)\).

### 嵌套表格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E5%B5%8C%E5%A5%97%E8%A1%A8%E6%A0%BC) <a id="&#x5D4C;&#x5957;&#x8868;&#x683C;"></a>

在一个表格中嵌套另外一个表格是可能的，只要你包含完整的结构，包括 `<table>` 元素。这样通常是不建议的，因为这种做法会使标记看上去很难理解，对使用屏幕阅读的用户来说，可访问性也降低了。以及在很多情况下，也许你只需要插入额外的 单元格/行/列 到已有的表格中。然而有时候是必要的，比如你想要从其他资源中更简单地导入内容。

下面的代码演示了一个简单的嵌套表格:

```text
<table id="table1">
  <tr>
    <th>title1</th>
    <th>title2</th>
    <th>title3</th>
  </tr>
  <tr>
    <td id="nested">
      <table id="table2">
        <tr>
          <td>cell1</td>
          <td>cell2</td>
          <td>cell3</td>
        </tr>
      </table>
    </td>
    <td>cell2</td>
    <td>cell3</td>
  </tr>
  <tr>
    <td>cell4</td>
    <td>cell5</td>
    <td>cell6</td>
  </tr>
</table>
```

输出看起来是这样的：

| title1 | title2 | title3 |
| :--- | :--- | :--- |
|  | cell2 | cell3 |
| cell4 | cell5 | cell6 |

### 对于视力受损的用户的表格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E5%AF%B9%E4%BA%8E%E8%A7%86%E5%8A%9B%E5%8F%97%E6%8D%9F%E7%9A%84%E7%94%A8%E6%88%B7%E7%9A%84%E8%A1%A8%E6%A0%BC) <a id="&#x5BF9;&#x4E8E;&#x89C6;&#x529B;&#x53D7;&#x635F;&#x7684;&#x7528;&#x6237;&#x7684;&#x8868;&#x683C;"></a>

让我们简要回顾一下如何使用数据表。一个表格可以是一个便利的工具，或者让我们快速访问数据，并允许我们查找不同的值。比如，你只需要稍微看一眼下列的表格，你就能得知 2016 年 8 月份在 Gent 出售了多少个 Rings \(戒指\)。为了理解信息，我们让数据与列标题或行标题之间建立视觉联系。

| Items Sold August 2016 |  |  |  |  |  |  |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
|  |  | Clothes | Accessories |  |  |  |
|  |  | Trousers | Skirts | Dresses | Bracelets | Rings |
| Belgium | Antwerp | 56 | 22 | 43 | 72 | 23 |
| Gent | 46 | 18 | 50 | 61 | 15 |  |
| Brussels | 51 | 27 | 38 | 69 | 28 |  |
| The Netherlands | Amsterdam | 89 | 34 | 69 | 85 | 38 |
| Utrecht | 80 | 12 | 43 | 36 | 19 |  |

但假设你无法通过视觉关联这些数据呢? 那么你应该如何阅读上述的表格? 视力受损的用户经常使用一个屏幕阅读设备来为他们读出网页上的信息。对于盲人来说，阅读简单的文字没有什么问题，但是要理解一张表格的内容，这就有一些难度了。虽然，使用正确的标记，我们可以用程序化来代替视觉关联。

**注意**: 根据[世界卫生组织 2017 年的数据](http://www.who.int/zh/news-room/fact-sheets/detail/blindness-and-visual-impairment)，大约有 2.53 亿人患有视觉障碍。

本篇文章提供了更一步的技术来使表格的可访问性尽可能地提高。

#### 使用列和行的标题[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E4%BD%BF%E7%94%A8%E5%88%97%E5%92%8C%E8%A1%8C%E7%9A%84%E6%A0%87%E9%A2%98) <a id="&#x4F7F;&#x7528;&#x5217;&#x548C;&#x884C;&#x7684;&#x6807;&#x9898;"></a>

屏幕阅读设备会识别所有的标题，然后在它们和它们所关联的单元格之间产生编程关联。列和行标题的组合将标识和解释每个单元格中的数据，以便屏幕阅读器用户可以类似于视力正常的用户的操作来理解表格。

我们之前的文章就提到过这一点，可见 [Adding headers with &lt;th&gt; elements](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics#Adding_headers_with_%3Cth%3E_elements).

#### scope 属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#scope_%E5%B1%9E%E6%80%A7) <a id="scope_&#x5C5E;&#x6027;"></a>

本篇文章的一个新话题是 [`scope`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/th#attr-scope) 属性，可以添加在`<th>` 元素中，用来帮助屏幕阅读设备更好地理解那些标题单元格，这个标题单元格到底是列标题呢，还是行标题。比如： 回顾我们早期的支出记录示例，您可以明确地将列标题这样定义：

```text
<thead>
  <tr>
    <th scope="col">Purchase</th>
    <th scope="col">Location</th>
    <th scope="col">Date</th>
    <th scope="col">Evaluation</th>
    <th scope="col">Cost (€)</th>
  </tr>
</thead>
```

以及每一行都可以这样定义一个行标题 \(如果我们已经使用了 th 和 td 元素\):

```text
<tr>
  <th scope="row">Haircut</th>
  <td>Hairdresser</td>
  <td>12/09</td>
  <td>Great idea</td>
  <td>30</td>
</tr>
```

屏幕阅读设备会识别这种结构化的标记，并一次读出整列或整行，比如：

`scope` 还有两个可选的值 ： `colgroup` 和 `rowgroup`。这些用于位于多个列或行的顶部的标题。 如果你回顾一些文章开始部分的 "Items sold..." 表格。你会看到 "Clothes" 单元格在"Trousers", "Skirts", 和 "Dresses" 单元格的上面，且包括了它们三个。像 "Clothes" 这种单元格应该被标记为 \(`<th>`\)，但是 "Clothes" 是一个位于顶部的标题，且定义了其他三个子标题。 因此 "Clothes" 应该有一个 `scope="colgroup"`属性，而另外三个子标题应该用 `scope="col"`属性。

#### id 和标题属性[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#id_%E5%92%8C%E6%A0%87%E9%A2%98%E5%B1%9E%E6%80%A7) <a id="id_&#x548C;&#x6807;&#x9898;&#x5C5E;&#x6027;"></a>

如果要替代 `scope` 属性，可以使用 [`id`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-id) 和 [`headers`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/td#attr-headers) 属性来创造标题与单元格之间的联系。使用方法如下:

1. 为每个`<th>` 元素添加一个 `id` \(id 不能重复\)。
2. 为每个 `<td>` 元素添加一个 `headers` 属性。每个 `headers` 属性需要包含 th 元素的 `id` 。 如果这个单元格是属于一个 th 元素下的，那么就需要包含 th 元素的 id 的值，如果属于多个 th 元素，那么可以用空格分隔这些 id。

这给你的HTML表格一个明确的定义，关于表格中每个单元格的位置。通过 headers 属性来定义属于哪些行或列。像一个电子表格，为了正常工作，该表确实需要列和行标题。

回到我们的花费成本示例，前两个片段可以重写为：

```text
<thead>
  <tr>
    <th id="purchase">Purchase</th>
    <th id="location">Location</th>
    <th id="date">Date</th>
    <th id="evaluation">Evaluation</th>
    <th id="cost">Cost (€)</th>
  </tr>
</thead>
<tbody>
<tr>
  <th id="haircut">Haircut</th>
  <td headers="location haircut">Hairdresser</td>
  <td headers="date haircut">12/09</td>
  <td headers="evaluation haircut">Great idea</td>
  <td headers="cost haircut">30</td>
</tr>

  ...

</tbody>
```

**注意**: 这个放进为标题单元格和数据单元格之间创造了非常精确的联系。但是这个方法使用了大量的标记，所以容错率比较低。使用 `scope` 的方法对于大多数表格来说，也够用了。

#### 动手练习: 使用 scope 和 headers[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E5%8A%A8%E6%89%8B%E7%BB%83%E4%B9%A0_%E4%BD%BF%E7%94%A8_scope_%E5%92%8C_headers) <a id="&#x52A8;&#x624B;&#x7EC3;&#x4E60;_&#x4F7F;&#x7528;_scope_&#x548C;_headers"></a>

1. 对于这个最后的练习，首先把 [items-sold.html](https://github.com/mdn/learning-area/blob/master/html/tables/advanced/items-sold.html) 和 [minimal-table.css](https://github.com/mdn/learning-area/blob/master/html/tables/advanced/minimal-table.css),拷贝到你的本地环境。
2. 现在尝试添加适当的 `scope` 属性来让表格变得更加恰当。
3. 最后，尝试把未添加 `scope` 属性的源文件再复制一份。这次使用 `id` 和 `headers` 属性让表格变得更加恰当。

**注意**: 你可以根据我们完成的例子检查你的工作，请看 [items-sold-scope.html](https://github.com/mdn/learning-area/blob/master/html/tables/advanced/items-sold-scope.html) \([also see this live](http://mdn.github.io/learning-area/html/tables/advanced/items-sold-scope.html)\) 和 [items-sold-headers.html](https://github.com/mdn/learning-area/blob/master/html/tables/advanced/items-sold-headers.html) \([see this live too](http://mdn.github.io/learning-area/html/tables/advanced/items-sold-headers.html)\).

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Tables/Advanced#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

关于 HTML 表格你还可以学习其他一些东西，但是我们目前已经把大部分你需要知道的内容都告诉你了。在此刻，如果你想学习关于 HTML 表格的样式，可以阅读 [Styling Tables](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_boxes/Styling_tables).

