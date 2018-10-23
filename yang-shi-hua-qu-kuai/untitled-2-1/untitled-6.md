# 作业：酷炫外观区块

在这个评估里，通过尝试创造一个引人瞩目的盒子，你将得到更多关于如何创造酷炫盒子的练习。

| 前提条件： | 在开始这个评估之前你应该已经学习过这个模块里的所有其他文章。 |
| :--- | :--- |
| 目的： | 测试对CSS盒模型和其他盒相关特性的掌握程度，比如背景和边框。 |

### 起点[Edit](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box$edit#%E8%B5%B7%E7%82%B9)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box#%E8%B5%B7%E7%82%B9) <a id="&#x8D77;&#x70B9;"></a>

在开始评估之前，你需要：

* 复制一份[HTML](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/cool-information-box-start/index.html)和[CSS](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/cool-information-box-start/style.css)代码，并在一个新的目录下把它们保存为`index.html` 和 `style.css`。

**提醒**：或者你也可以用[JSBin](http://jsbin.com/)或[Thimble](https://thimble.mozilla.org/)这样的网站来做这个评估，把链接里的HTML和CSS代码贴到这些在线编辑器里就行。如果你在用的在线编辑器没有独立的CSS面板的话，把CSS代码放到HTML文档头部的`<style>`元素里就好。

### 项目简介[Edit](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box$edit#%E9%A1%B9%E7%9B%AE%E7%AE%80%E4%BB%8B)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box#%E9%A1%B9%E7%9B%AE%E7%AE%80%E4%BB%8B) <a id="&#x9879;&#x76EE;&#x7B80;&#x4ECB;"></a>

你的任务是创建一个酷炫的盒子，并探索CSS的乐趣。

#### 一般任务[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box#%E4%B8%80%E8%88%AC%E4%BB%BB%E5%8A%A1) <a id="&#x4E00;&#x822C;&#x4EFB;&#x52A1;"></a>

* 把CSS链接到HTML里。

#### 样式化盒子[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box#%E6%A0%B7%E5%BC%8F%E5%8C%96%E7%9B%92%E5%AD%90) <a id="&#x6837;&#x5F0F;&#x5316;&#x76D2;&#x5B50;"></a>

我们希望你样式已经写好的[`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p)，给它下面这些：

* 一个对于大按钮来说合理的宽度，200像素左右。
* 一个对于大按钮来说合理的高度，并使文本纵向居中。
* 居中文本。
* 用`rem`使字体稍大一点，大约17-18像素，在注释里说说你的值是怎么算出来的。
* 给你的设计定一个基础颜色，把它作为盒子的背景颜色。
* 把字体颜色设为同一个颜色，为了可读性给它一个黑色的文字阴影。
* 一个精巧的圆角边框。
* 一个跟基础颜色相近、1像素宽的实线边框，颜色要稍深一点。
* 一个指向右下角的黑色半透明线性渐变，让它在开始的时候完全透明，在30%的处渐变到0.2的不透明度，然后保持相同颜色到最后。
* 多个盒阴影：一个标准的盒阴影，使它看起来稍微从页面上浮起来；另外两个是内嵌（inset）的盒阴影，一个是左上角附近的白色半透明阴影和另一个是右下角附近的黑色半透明阴影，让盒子有一个漂亮的3D外观。

### 范例[Edit](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box$edit#%E8%8C%83%E4%BE%8B)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box#%E8%8C%83%E4%BE%8B) <a id="&#x8303;&#x4F8B;"></a>

完成之后的盒子可能会像下面的截图这样：

![](https://mdn.mozillademos.org/files/13148/fancy-box.png)

### 评估[Edit](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box$edit#%E8%AF%84%E4%BC%B0)[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_boxes/A_cool_looking_box#%E8%AF%84%E4%BC%B0) <a id="&#x8BC4;&#x4F30;"></a>

如果这个评估是一系列课程的一部分，你应该可以让你的老师或导师为你批改。 如果你是自学，可以很容易地在[Learning Area Discourse thread](https://discourse.mozilla-community.org/t/learning-web-development-marking-guides-and-questions/16294)或[Mozilla IRC](https://wiki.mozilla.org/IRC)的[\#mdn](irc://irc.mozilla.org/mdn) IRC频道回复得到批改指南。请先自己试着做——作弊学不到任何东西！

