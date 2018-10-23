# 表单组件兼容性列表

下面的兼容性表格尝试总结 HTML 表单的 CSS 支持状况。由于 CSS 和 HTML 表单的复杂性，不能把这些表格当作完善的参考。但是，它们可以让你很好地洞察什么能做什么不能做，这将会对你学习使用有很好地帮助。

### 如何阅读表格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#%E5%A6%82%E4%BD%95%E9%98%85%E8%AF%BB%E8%A1%A8%E6%A0%BC) <a id="&#x5982;&#x4F55;&#x9605;&#x8BFB;&#x8868;&#x683C;"></a>

#### 值[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#%E5%80%BC) <a id="&#x503C;"></a>

对于每个属性，有四种可能地取值：YES此属性具有相当一致的跨浏览器支持。在某些极端情况下，你可能仍然会面临奇怪的副作用。PARTIAL尽管这个属性会生效，你还是会经常面对奇怪的副作用和不一致性。你应该尽力避免这些属性，除非你已经深知那些副作用。NO此属性就是不工作或者表现得非常不一致，所以并不可靠。N.A.此属性对这种类型的组件没有意义。



#### 渲染[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#%E6%B8%B2%E6%9F%93) <a id="&#x6E32;&#x67D3;"></a>

对于每个属性有两种可能的渲染方式：N \(Normal\)表示这个属性会像设置的那样应用。T \(Tweaked\)表示这个属性需要通过下列的额外规则来使用：

```text
* {
/* This turn off the native look and feel on WebKit based browsers */
  -webkit-appearance: none;

/* This turn off the native look and feel on Gecko based browsers */
  -moz-appearance: none;

/* This turn off the native look and feel on several different browsers 
   including Opera, Internet Explorer and Firefox */
  background: none;
}
```



### 兼容性表格[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#%E5%85%BC%E5%AE%B9%E6%80%A7%E8%A1%A8%E6%A0%BC) <a id="&#x517C;&#x5BB9;&#x6027;&#x8868;&#x683C;"></a>

#### Global behaviors[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Global_behaviors) <a id="Global_behaviors"></a>

对许多浏览器来说，许多行为在全局范围内都是通用的：[`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border), [`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background), [`border-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius), [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)任意属性可能影响组件部分或全部的原生外观。小心使用。[`line-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height)不同浏览器支持不同，避免使用[`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration)Opera表单不支持[`text-overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow)Opera, Safari,  IE9 表单不支持[`text-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow)Opera 和 IE9 不支持

#### Text fields[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Text_fields) <a id="Text_fields"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">Partial[1][2]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>WebKit 浏览器 (主要在 Mac OSX and iOS 上) 的搜索域使用原生的样式和行为。因此，需要使用 <code>-webkit-appearance:none</code> 才能将这个属性应用到搜索域上。</li>
          <li>在 Windows 7, Internet Explorer 9 不会应用到边框上，除非 <code>background:none</code> 已应用。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">Partial[1][2]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>WebKit 浏览器 (主要在 Mac OSX and iOS 上) 的搜索域使用原生的样式和行为。因此，需要使用 <code>-webkit-appearance:none</code> 才能将这个属性应用到搜索域上。</li>
          <li>在 Windows 7, Internet Explorer 9 不会应用到边框上，除非 <code>background:none</code> 已应用。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">Partial[1][2]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>WebKit 浏览器 (主要在 Mac OSX and iOS 上) 的搜索域使用原生的样式和行为。因此，需要使用 <code>-webkit-appearance:none</code> 才能将这个属性应用到搜索域上。</li>
          <li>在 Windows 7, Internet Explorer 9 不会应用到边框上，除非 <code>background:none</code> 已应用。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>[1]</td>
      <td
      style="text-align:left">Yes</td>
        <td style="text-align:left">Yes</td>
        <td style="text-align:left">
          <ol>
            <li>如果 <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-color"><code>border-color</code></a> 属性没有设置，一些基于
              WebKit 的浏览器会将 <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a> 属性应用到边框上，颜色和
              <a
              href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea"><code>&lt;textarea&gt;</code>
                </a>的字体颜色一样。</li>
          </ol>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">查看有关 <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height"><code>line-height</code></a> 的注释</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">查看有关 Opera 的注释</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 只在 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea"><code>&lt;textarea&gt;</code></a> 上支持这个属性，而
            Opera 只在单行文本域中支持。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>WebKit 浏览器 (主要在 Mac OSX and iOS 上) 的搜索域使用原生的样式和行为。因此，需要使用 <code>-webkit-appearance:none</code> 才能将这个属性应用到搜索域上。</li>
          <li>在 Windows 7上, Internet Explorer 9 不会应用到边框上，除非 <code>background:none</code> 已应用。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">Partial[1][2]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>WebKit 浏览器 (主要在 Mac OSX and iOS 上) 的搜索域使用原生的样式和行为。因此，需要使用 <code>-webkit-appearance:none</code> 才能将这个属性应用到搜索域上。</li>
          <li>在 Windows 7上, Internet Explorer 9 不会应用到边框上，除非 <code>background:none</code> 已应用。</li>
          <li>在 Opera 上，只有当边框明确设定时 <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a> 属性才会应用</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 不支持这个属性</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>

#### Buttons[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Buttons) <a id="Buttons"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>这个属性不能应用于 Mac OSX or iOS 上基于 WebKit 的浏览器。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>这个属性不能应用于 Mac OSX or iOS 上基于 WebKit 的浏览器。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">查看<a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height"><code>line-height</code></a> 的注意事项。</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">Yes[1]</td>
      <td style="text-align:left">Yes[1]</td>
      <td style="text-align:left">
        <ol>
          <li>在 Opera 上，只有当边框明确设定时 <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a> 属性才会应用</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 不支持这个属性</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>#### Number[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Number) <a id="Number"></a>

在实现了 `number` 组件的浏览器上，并没有一种标准的方式改变数字组件的样式，值得注意的是 Safari 上的数字输入框不在这个范围内。

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>在 Opera 上，数字选择器缩小时，可能会隐藏域中内容。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>在 Opera 上，数字选择器缩小时，可能会隐藏域中内容。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">查看<a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height"><code>line-height</code></a> 的注意事项。</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">支持，但浏览器之间的不一致性太多，所以并不可靠。</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

#### Check boxes and radio buttons[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Check_boxes_and_radio_buttons) <a id="Check_boxes_and_radio_buttons"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>一些浏览器会添加额外的边缘，另一些会拉伸组件。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>一些浏览器会添加额外的边缘，另一些会拉伸组件。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>#### Select boxes \(single line\)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Select_boxes_%28single_line%29) <a id="Select_boxes_(single_line)"></a>

Firefox 不提供任何方式改变 [`<select>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select) 元素的下箭头。

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>这个属性在 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素上一切正常，但不能用于
            <a
            href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code>
              </a>或者 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup"><code>&lt;optgroup&gt;</code></a> 元素。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">Partial[2]</td>
      <td style="text-align:left">
        <ol>
          <li>属性可以应用，但 Mac OSX 上浏览器之间的以不一致的方向显示，所以并不可靠。</li>
          <li>这个属性在 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素上一切正常，但不能用于
            <a
            href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code>
              </a>或者 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup"><code>&lt;optgroup&gt;</code></a> 元素。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>在 Mac OSX 上， 基于 WebKit 的浏览器 不支持将这个属性用于原生组件。它们和 Opera, 在 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code></a> 和
            <a
            href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup"><code>&lt;optgroup&gt;</code>
              </a>元素上根本不支持这个属性。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>在 Mac OSX 上， 基于 WebKit 的浏览器 不支持将这个属性用于原生组件。它们和 Opera, 在 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code></a> 和
            <a
            href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup"><code>&lt;optgroup&gt;</code>
              </a>元素上根本不支持这个属性。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 不支持将这个属性用于 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a>,
            <a
            href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code>
              </a>, 和 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup"><code>&lt;optgroup&gt;</code></a> 元素；Mac
              OSX 上基于 WebKit 的浏览器不支持将这个属性应用于 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code></a> 和
              <a
              href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup"><code>&lt;optgroup&gt;</code>
                </a>元素。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>Windows 7 上的 IE9 和 Mac OSX 上基于 WebKit 的浏览器，不支持这个组件上的这个属性。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>只有 Firefox 提供了对这个属性的完全支持。Opera 根本不支持这个属性，而其他浏览器只提供了对 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素的支持。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">Partial[1][2]</td>
      <td style="text-align:left">Partial[1][2]</td>
      <td style="text-align:left">
        <ol>
          <li>大部分浏览器仅仅支持将这个属性用于 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素。</li>
          <li>IE9 不支持这个属性</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">Partial[1][2]</td>
      <td style="text-align:left">Partial[1][2]</td>
      <td style="text-align:left">
        <ol>
          <li>大部分浏览器仅仅支持将这个属性用于 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素。</li>
          <li>IE9 不支持这个属性</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>大部分浏览器仅仅支持将这个属性用于 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>大部分浏览器仅仅支持将这个属性用于 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

#### Select boxes \(multiline\)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Select_boxes_%28multiline%29) <a id="Select_boxes_(multiline)"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>Opera 在 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素上
            不支持 <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-top"><code>padding-top</code></a> 和
            <a
            href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-bottom"><code>padding-bottom</code>
              </a>。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">查看<a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height"><code>line-height</code></a> 的注意事项。</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 在 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a>,
            <a
            href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code>
              </a>, 和<a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup"><code>&lt;optgroup&gt;</code></a> 元素上不支持这个属性；Mac
              OSX 上基于 WebKit 的浏览器在 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code></a> 和
              <a
              href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/optgroup"><code>&lt;optgroup&gt;</code>
                </a>元素上不支持这个属性。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>Windows 7 上的 IE9 和 Mac OSX 上基于 WebKit 的浏览器，不支持这个组件上的这个属性。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>只被 Firefox and IE9+ 支持。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>大部分浏览器仅仅支持将这个属性用于 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> 元素。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">Yes[1]</td>
      <td style="text-align:left">Yes[1]</td>
      <td style="text-align:left">
        <ol>
          <li>在 Opera 上，只有当边框明确设定时 <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a> 属性才会应用</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 不支持这个属性</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>#### Datalist[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Datalist) <a id="Datalist"></a>

| Property | N | T | Note |
| :--- | :--- | :--- | :--- |
| _CSS box model_ |  |  |  |
| [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) | No | No |  |
| [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) | No | No |  |
| [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) | No | No |  |
| [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin) | No | No |  |
| [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) | No | No |  |
| _Text and font_ |  |  |  |
| [`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color) | No | No |  |
| [`font`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font) | No | No |  |
| [`letter-spacing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing) | No | No |  |
| [`text-align`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align) | No | No |  |
| [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration) | No | No |  |
| [`text-indent`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent) | No | No |  |
| [`text-overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow) | No | No |  |
| [`text-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow) | No | No |  |
| [`text-transform`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform) | No | No |  |
| _Border and background_ |  |  |  |
| [`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background) | No | No |  |
| [`border-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius) | No | No |  |
| [`box-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow) | No | No |  |

#### File picker[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#File_picker) <a id="File_picker"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>支持，但浏览器之间的不一致性太多，所以并不可靠。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>许多浏览器将这个属性应用到选择按钮上。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>它表现的或多或少的像一个组件左侧的边缘。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>支持，但浏览器之间的不一致性太多，所以并不可靠。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 不支持这个属性</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>#### Date pickers[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Date_pickers) <a id="Date_pickers"></a>

许多属性都支持但是浏览器之间的不一致性太多，所以并不可靠。

| Property | N | T | Note |
| :--- | :--- | :--- | :--- |
| _CSS box model_ |  |  |  |
| [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) | No | No |  |
| [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) | No | No |  |
| [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) | No | No |  |
| [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin) | Yes | Yes |  |
| [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) | No | No |  |
| _Text and font_ |  |  |  |
| [`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color) | No | No |  |
| [`font`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font) | No | No |  |
| [`letter-spacing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing) | No | No |  |
| [`text-align`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align) | No | No |  |
| [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration) | No | No |  |
| [`text-indent`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent) | No | No |  |
| [`text-overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow) | No | No |  |
| [`text-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow) | No | No |  |
| [`text-transform`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform) | No | No |  |
| _Border and background_ |  |  |  |
| [`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background) | No | No |  |
| [`border-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius) | No | No |  |
| [`box-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow) | No | No |  |



#### Color pickers[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Color_pickers) <a id="Color_pickers"></a>

There is currently not enough implementation to get realiable behaviors.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>Opera 将它像一个选择组件一样，以同样的限制处理。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li>Opera 将它像一个选择组件一样，以同样的限制处理。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>支持，但浏览器之间的不一致性太多，所以并不可靠。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>#### Meters and progress[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Meters_and_progress) <a id="Meters_and_progress"></a>

There is currently not enough implementation to get realiable behaviors.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">Partial</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>当 <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a> 属性应用于一个
            tweaked 元素时，Chrome 会隐藏 <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/progress"><code>&lt;progress&gt;</code></a> 和
            <a
            href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meter"><code>&lt;meter&gt;</code>
              </a>元素。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>支持，但浏览器之间的不一致性太多，所以并不可靠。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>#### Range[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Range) <a id="Range"></a>

There is no standard way to change the style of the range grip and Opera has no way to tweak the default rendering of the range widget.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>Chrome 和 Opera 在组件周围添加了一些额外的空白，而 Windows 7 上的 Opera 则拉伸范围选择器的滑块。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <ol>
          <li> <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a> 属性被运用，但是没有任何的视觉效果。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">
        <ol>
          <li>支持，但浏览器之间的不一致性太多，所以并不可靠。</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left">No[1]</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

#### Image buttons[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets#Image_buttons) <a id="Image_buttons"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">N</th>
      <th style="text-align:left">T</th>
      <th style="text-align:left">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em>CSS box model</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/width"><code>width</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/height"><code>height</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border"><code>border</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin"><code>margin</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding"><code>padding</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Text and font</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/color"><code>color</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/font"><code>font</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing"><code>letter-spacing</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-align"><code>text-align</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration"><code>text-decoration</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-indent"><code>text-indent</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-overflow"><code>text-overflow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow"><code>text-shadow</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-transform"><code>text-transform</code></a>
      </td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left">N.A.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Border and background</em>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background"><code>background</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius"><code>border-radius</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 不支持这个属性</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow"><code>box-shadow</code></a>
      </td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">Partial[1]</td>
      <td style="text-align:left">
        <ol>
          <li>IE9 不支持这个属性</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>