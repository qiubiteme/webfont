# CSS的值和单位

CSS的属性值可以有很多种类，可以是普通类型的数值，也可以是有特定作用的颜色和函数（比如内置的背景图片，或者旋转一个元素）。有些值通过特定的单位来指定与之相对应的值——你是想把你的盒子（box）宽度设置为30像素（pixel）， 30厘米（centimeter）还是30em呢？在本指导中，我们既会讨论常用的值像长度、颜色以及简单函数，也会探索一些不那么常用的单位像角度，甚至没有单位的纯数值。

| 预备知识: | 计算机基本技能, [安装必须的软件](https://developer.mozilla.org/zh-CN/Learn/Getting_started_with_the_web/Installing_basic_software),  了解[文件](https://developer.mozilla.org/zh-CN/Learn/Getting_started_with_the_web/Dealing_with_files)的基本操作, HTML基础 \(学习[HTML简介](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML)\), 知道CSS是如何起作用的 \(在[这里](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS)学习前一章.\) |
| :--- | :--- |
| 目标: | 学习最常用的CSS属性值以及相关的单位 |

在CSS中，值的类型有很多种，一些很常见，一些你却几乎没怎么遇到过。我们不会在这篇文档中面面俱到地描述他们，而只是这些对于掌握CSS可能最有用处的这些。本文将会涉及如下CSS的值：

* 数值: 长度值，用于指定例如元素宽度、边框（border）宽度或字体大小；以及无单位整数。用于指定例如相对线宽或运行动画的次数。
* 百分比: 可以用于指定尺寸或长度——例如取决于父容器的长度或高度，或默认的字体大小。
* 颜色: 用于指定背景颜色，字体颜色等。
* 坐标位置: 例如，以屏幕的左上角为坐标原点定位元素的位置。
* 函数: 例如，用于指定背景图片或背景图片渐变。

在接下来所有关于CSS的主题中，你都会看到这些单位的例子在不断展现，就像你在其他的CSS资源文件中看到的一样。很快你就会熟悉他们的。

**提示**: 你可以在[CSS手册](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference)中找到关于CSS单位的详尽描述; 关于单位的条目会用一对尖括号包起来，比如 [&lt;color&gt;](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value)。

### 数值[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E6%95%B0%E5%80%BC) <a id="&#x6570;&#x503C;"></a>

你会在很多地方看到CSS单位中使用到数值。这一部分将会讨论数值的最常用类别。

#### 长度和尺寸[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E9%95%BF%E5%BA%A6%E5%92%8C%E5%B0%BA%E5%AF%B8) <a id="&#x957F;&#x5EA6;&#x548C;&#x5C3A;&#x5BF8;"></a>

在CSS布局、排版等等的所有时候，你都会使用到长度/尺寸单位（比如参考 [&lt;length&gt;](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length)）。我们不妨先看一个简单的例子——先上HTML：

```text
 <p>This is a paragraph.</p>
<p>This is a paragraph.</p>
<p>This is a paragraph.</p>
```

然后是CSS：

```text
p {
  margin: 5px;
  padding: 10px;
  border: 2px solid black;
  background-color: cyan;
}

p:nth-child(1) {
  width: 150px;
  font-size: 18px;
}

p:nth-child(2) {
  width: 250px;
  font-size: 24px;
}

p:nth-child(3) {
  width: 350px;
  font-size: 30px;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

在这个例子中我们做了以下事情：

* 分别将每个段落的 [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)，[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) 和 [`border-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-width) 设置为5 pixels, 10 pixels 和 2 pixels。一个单独的margin/padding值表示所有的4个面都被设置成同样的值。边框也被设置成了 [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) 的缩写值。
* 为三个不同的段落设置越来越大的宽度（[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) ）像素值，也就是意味着越往下盒子越大。
* 为三个不同的段落设置越来越大字号（ [`font-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size)）像素值，也就是意味着越往下文本越大。`font-size代表字体/字形的高度。`

像素 \(px\) 是一种绝对单位（**absolute units**）**，** 因为无论其他相关的设置怎么变化，像素指定的值是不会变化的。其他的绝对单位如下：

* `mm`, `cm`, `in`: 毫米（Millimeters），厘米（centimeters），英寸（inches）
* `pt`, `pc`: 点（Points \(1/72 of an inch\)）， 十二点活字（ picas \(12 points.\)）

除了px之外，你很可能都不怎么使用其他的单位。

也有相对单位，他们是相对于当前元素的字号（ `font-size` ）或者视口（[viewport](https://developer.mozilla.org/en-US/docs/Glossary/viewport) ）尺寸。

* `em`:1em与当前元素的字体大小相同（更具体地说，一个大写字母M的宽度）。CSS样式被应用之前，浏览器给网页设置的默认基础字体大小是16像素，这意味着对一个元素来说1em的计算值默认为16像素。但是要小心—em单位是会继承父元素的字体大小，所以如果在父元素上设置了不同的字体大小，em的像素值就会变得复杂。现在不要过于担心这个问题，我们将在后面的文章和模块中更详细地介绍继承和字体大小设置。**em是Web开发中最常用的相对单位**。
* `ex`, `ch`: 分别是小写x的高度和数字0的宽度。这些并不像em那样被普遍使用或很好地被支持。
* `rem`: REM（root em）和em以同样的方式工作，但它总是等于默认基础字体大小的尺寸；继承的字体大小将不起作用，所以这听起来像一个比em更好的选择，虽然在旧版本的IE上不被支持（查看关于跨浏览器支持 [Debugging CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS).\)
* `vw`, `vh`: 分别是视口宽度的1/100和视口高度的1/100，其次，它不像rem那样被广泛支持。

使用相对单位是非常有用的-你可以相对于你的字体或视口大小来调整HTML元素的大小，这意味着，假设整个网站上的文本大小被视力障碍用户调整为原来的两倍，而网站的布局仍将保持正确。

#### 无单位的值[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E6%97%A0%E5%8D%95%E4%BD%8D%E7%9A%84%E5%80%BC) <a id="&#x65E0;&#x5355;&#x4F4D;&#x7684;&#x503C;"></a>

在CSS中，你有时会遇到一些无单位的数值——这并不总是意味着错误，在某些情况下，使用无单位的数值是完全允许的。例如，如果你想让一个元素完全去除外边框和内边框，你可以只使用无单位的0——因为0就是0，不管单位是什么！

```text
margin: 0;
```

**无单位的行高**

另一个例子是 [`line-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height)，设置元素中每行文本的高度。你可以使用单位设置特定的行的高度，但使用一个无单位的值往往更容易，它就像一个简单的乘法因子。例如，使用下面的HTML：

```text
<p>Blue ocean silo royal baby space glocal evergreen relationship housekeeping
native advertising diversify ideation session. Soup-to-nuts herding cats resolutionary
virtuoso granularity catalyst wow factor loop back brainstorm. Core competency 
baked in push back silo irrational exuberance circle back roll-up.</p>
```

下面的CSS：

```text
p {
  line-height: 1.5;
}
```

这将产生以下输出：

在 CodePen 中打开在 JSFiddle 中打开

这里`font-size`的值为16px; 行高为`font-size`值的1.5倍，也就是24px。

**动画的数值**

[CSS动画](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Animations)能够让页面上的HTML元素动起来。我们来看一个例子，当我们把鼠标浮动到一个段落上的时候，它能够旋转起来。这个例子的HTML代码很简单： 

```text
<p>Hello</p>
```

CSS有点复杂：

```text
@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

p {
  color: red;
  width: 100px;
  font-size: 40px;
  transform-origin: center;
}

p:hover {
  animation-name: rotate;
  animation-duration: 0.6s;
  animation-timing-function: linear;
  animation-iteration-count: 5;
}
```

这里你可可以看到一些我们我们之前没有明确提到的有趣单位 \([&lt;angle&gt;](https://developer.mozilla.org/zh-CN/docs/Web/CSS/angle)s、 [&lt;time&gt;](https://developer.mozilla.org/zh-CN/docs/Web/CSS/time)s、 [&lt;timing-function&gt;](https://developer.mozilla.org/zh-CN/docs/Web/CSS/timing-function)s、 [&lt;string&gt;](https://developer.mozilla.org/zh-CN/docs/Web/CSS/string)s...\)，但是我们感兴趣的是这一行 `animation-iteration-count: 5;` ——此行控制着动画启动（这里是指光标浮动至段落上时）后会执行多少次，而且这是一个简短无单位纯数字（计算机中称之为整型）。

以下是代码的实际效果：

在 CodePen 中打开在 JSFiddle 中打开

### 百分比[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E7%99%BE%E5%88%86%E6%AF%94) <a id="&#x767E;&#x5206;&#x6BD4;"></a>

大部分使用特定数值指定的内容同样可以使用百分比来指定。这使的我们可以创建那些，例如，其宽度总是会被调整到其父容器宽度一定百分比的盒子。反观那些宽度被设置为某个固定单位值（如px或em）的盒子，它们总是保持固定的尺寸，即使它们父容器的宽度发生变化。

让我们举个例子来说明这个问题。

首先，使用HTML标记创建两个相似的盒子：

```text
<div>
  <div class="boxes">Fixed width layout with pixels</div>
  <div class="boxes">Liquid layout with percentages</div>
</div>
```

然后是一些CSS来装饰这些盒子：

```text
div .boxes {
  margin: 10px;
  font-size: 200%;
  color: white;
  height: 150px;
  border: 2px solid black;
}

.boxes:nth-child(1) {
  background-color: red;
  width: 650px;
}

.boxes:nth-child(2) {
  background-color: blue;
  width: 75%;
}
```

这给了我们以下结果：

在 CodePen 中打开在 JSFiddle 中打开

在这里，我们给两个div设置了一些 [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin), [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height), [`font-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-size), [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) and [`color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color) 。 然后我们给第一个div和第二个div不同的 [`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color)，所以我们可以很容易地区分它们。 我们还将第一个div的 [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 设置为650px，将第二个div的宽度设置为75％。 这样做的效果是，第一个div始终具有相同的宽度，即使视口大小被调整（当视口变得比屏幕更窄时，它将从屏幕上消失），而第二个div的宽度随着视口（viewport ）的变化而变化，使其始终保持其父元素宽度的75％。 在这个例子中，div的父元素是&lt;body&gt;元素，默认情况下宽度是视口宽度的100％。

**注意**: 您可以通过调整本文中的浏览器窗口来看到这种效果； [raw examples found on Github](http://mdn.github.io/learning-area/css/introduction-to-css/css-values-and-units/).

我们也可以设置`font-size`的百分比为200%。它将和你预计的工作方式有一点不同，但这是讲得通的，它的新大小是相对于父容器的字体大小的，就像`em`一样。在这种情况下，父容器的字体大小为16px——页面的默认值，所以计算的值为16px的200%，即32px。这和`em`的风格确实很类似——200%基本上和2`em`一样。

这两种不同的框布局类型通常被称为**动态（流体）布局**（跟随浏览器视口大小的变化）和**固定宽度布局**（不管怎样都保持不变），两种布局方式有着不同的应用场景：

* 可以使用动态布局来确保标准文档始终适合于屏幕，并且可以在不同大小的移动设备屏幕上表现良好。
* 一个固定宽度的布局可以用来保持在线地图的大小相同；浏览器视口可以在地图上滚动，只在一个时间内查看一定数量的地图。您可以立即看到的量取决于您的视口有多大。

你会在后面的课程中学习到更多关于网页的布局，在CSS布局和响应式设计模块（待定）

### 主动学习: 拿长度length练练手[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0_%E6%8B%BF%E9%95%BF%E5%BA%A6length%E7%BB%83%E7%BB%83%E6%89%8B) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;_&#x62FF;&#x957F;&#x5EA6;length&#x7EC3;&#x7EC3;&#x624B;"></a>

这次的主动学习没有正确答案。我们只是简单地希望你能体验一下，改变 `.inner` 和 `.outer`的 width/height 的值，会带来什么变化。尝试一下设置 `.inner` 的 width/height 的值为百分比，然后调整 `.outer` 的 width ，看看它是如何变化的。同时也可以试试其他固定的值，比如 `px` 或者 `em`。

如果你犯了一个错误，你可以用重置按钮重新设置它。

在 CodePen 中打开在 JSFiddle 中打开

### 颜色[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E9%A2%9C%E8%89%B2) <a id="&#x989C;&#x8272;"></a>

CSS中指定颜色的方法有很多，其中一些是最近实现的。CSS中到处都可以使用相同的颜色值，无论是指定文本颜色、背景颜色，还是其他任何颜色。

现代计算机中可用的标准颜色系统是24位，通过不同的红、绿、蓝通道，每个通道有256种不同的值，从而显示出大约1670万种不同的颜色。  \(256 x 256 x 256 = 16,777,216.\)

让我们运行不同的可用类型的颜色值。

**注意**:要在下面讨论的不同颜色系统之间转换，您需要一个颜色转换器。有很多简单的在线转换器，如 [HSL to RGB / RGB to HSL / Hex Colour Converter](http://serennu.com/colour/hsltorgb.php).

#### 关键词[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E5%85%B3%E9%94%AE%E8%AF%8D) <a id="&#x5173;&#x952E;&#x8BCD;"></a>

CSS中最简单、最古老的颜色类型就是颜色关键词。这些都是代表特定颜色值的特定字符串。例如，下面的代码:

```text
<p>This paragraph has a red background</p>
```

```text
p {
  background-color: red;
}
```

给出这个结果：

在 CodePen 中打开在 JSFiddle 中打开

这很容易理解，尽管它只能让我们指定明显的基础颜色。有大约165个不同的关键字可用于现代Web浏览器-见 [full color keyword list](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value#Color_keywords).

你可能会在工作中经常使用诸如红色、黑色和白色这样的纯颜色，但除此之外，你还需要使用另一种颜色系统。

#### 十六进制值[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E5%8D%81%E5%85%AD%E8%BF%9B%E5%88%B6%E5%80%BC) <a id="&#x5341;&#x516D;&#x8FDB;&#x5236;&#x503C;"></a>

下一个常用的颜色系统是十六进制颜色或十六进制代码。每个颜色包括一个哈希/磅符号（\#）和其后面紧跟的六个十六进制数，其中每个十六进制数可以是0和F之间的一个值（一共16个），0123456789abcdef。每对十六进制数代表一个通道（红色、绿色或者蓝色）允许我们指定256个可用值。 \(16 x 16 = 256.\)  

例如，这个代码：

```text
<p>This paragraph has a red background</p>
<p>This paragraph has a blue background</p>
<p>This paragraph has a kind of pinky lilac background</p>
```

```text
/* equivalent to the red keyword */
p:nth-child(1) {
  background-color: #ff0000;
}

/* equivalent to the blue keyword */
p:nth-child(2) {
  background-color: #0000ff;
}

/* has no exact keyword equivalent */
p:nth-child(3) {
  background-color: #e0b0ff;
}
```

给出以下结果：

在 CodePen 中打开在 JSFiddle 中打开

这些值比较复杂，不太容易理解，但是它们比关键字更灵活——您可以使用十六进制值来表示您想要在颜色方案中使用的任何颜色。.

#### RGB[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#RGB) <a id="RGB"></a>

我们要讨论的第三个方案是RGB。一个RGB值是一个函数——rgb\(\) ——给定的三个参数，分别表示红色，绿色和蓝色通道的颜色值，这与十六进制值的工作方式大致相同。区别在于，RGB中每个通道不是由两个十六进制数字表示的，而是由0到255之间的十进制数表示的。

让我们使用RGB颜色值来重写最后一个例子：

```text
<p>This paragraph has a red background</p>
<p>This paragraph has a blue background</p>
<p>This paragraph has a kind of pinky lilac background</p>
```

```text
/* equivalent to the red keyword */
p:nth-child(1) {
  background-color: rgb(255,0,0);
}

/* equivalent to the blue keyword */
p:nth-child(2) {
  background-color: rgb(0,0,255);
}

/* has no exact keyword equivalent */
p:nth-child(3) {
  background-color: rgb(224,176,255);
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

RGB值的支持度与十六进制不相上下，在你的工作中你可能不会遇到不支持它们的浏览器。

RGB值可以说比十六进制值更直观，更容易理解。

**注意**: 为什么是0-255而不是1-256？计算机系统倾向于从0计算，而不是从1计算。所以允许256个可能的值，RGB颜色在0-255范围内取值。

#### HSL[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#HSL) <a id="HSL"></a>

支持度比RGB稍微差一点的是HSL（旧版本的IE浏览器不支持），这是在众多开发者对其产生兴趣之后才实现的——`hsl()`函数接受三个表示**色调**、**饱和度**以及**明度**的参数，使用与上述三种不同的方式来区分大约1670万种颜色：

1. **色调**：颜色的底色调。这个值在0到360之间，表示色轮的角度。
2. **饱和度**：饱和度是多少？这需要一个从0-100%的值，其中0是没有颜色（它将显示为灰色），100%是全彩色饱和度。
3. **明度**：颜色有多亮或明亮？这需要一个从0-100%的值，其中0是无光（它会出现全黑的），100%是充满光的（它会出现全白）。

**Note**: 一个HSL圆柱体对于可视化此颜色模型的工作方式非常有用，在Wikipedia上查看 [HSL and HSV article](https://en.wikipedia.org/wiki/HSL_and_HSV#Basic_principle) 。

现在我们用HSL颜色重写例子:

```text
<p>This paragraph has a red background</p>
<p>This paragraph has a blue background</p>
<p>This paragraph has a kind of pinky lilac background</p>
```

```text
/* equivalent to the red keyword */
p:nth-child(1) {
  background-color: hsl(0,100%,50%);
}

/* equivalent to the blue keyword */
p:nth-child(2) {
  background-color: hsl(240,100%,50%);
}

/* has no exact keyword equivalent */
p:nth-child(3) {
  background-color: hsl(276,100%,85%);
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

HSL颜色模型对于常使用这样模型的设计师来说非常直观。例如,找到一组色调以单配色方式使用是非常有用的。

```text
/* three different shades of red*/
background-color: hsl(0,100%,50%);
background-color: hsl(0,100%,60%);
background-color: hsl(0,100%,70%);
```

#### RGBA 和 HSLA[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#RGBA_%E5%92%8C_HSLA) <a id="RGBA_&#x548C;_HSLA"></a>

RGB和HSL都有相应的模式——RGBA和HSLA——不仅允许您设置想要显示的颜色,还有此颜色的**透明度（** **transparency** ）。它们和与之相应的函数采用同样的参数,再加上第四个范围在0-1的值——设置透明度,或者说**alpha通道**。0是完全透明的,1是完全不透明的。

让我们展示另一个简单的例子,第一个HTML:

```text
<p>This paragraph has a transparent red background</p>
<p>This paragraph has a transparent blue background</p>
```

现在CSS——我们正在第一段向下定位,显示段落重叠的效果\(以后你会了解更多关于定位的知识\):

```text
p {
  height: 50px;
  width: 350px;
}

/* Transparent red */
p:nth-child(1) {
  background-color: rgba(255,0,0,0.5);
  position: relative;
  top: 30px;
  left: 50px;
}

/* Transparent blue */
p:nth-child(2) {
  background-color: hsla(240,100%,50%,0.5);
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

透明色对于产生更丰富的视觉效果非常有用——例如混合的背景,半透明的UI元素等等。

**注意**: [CSS 中的定位](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Positioning) 会在随后的课程中讨论。

#### 不透明度（Opacity）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E4%B8%8D%E9%80%8F%E6%98%8E%E5%BA%A6%EF%BC%88Opacity%EF%BC%89) <a id="&#x4E0D;&#x900F;&#x660E;&#x5EA6;&#xFF08;Opacity&#xFF09;"></a>

还有另一种方法来指定透明度，通过CSS——[`opacity`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/opacity) 属性。与设置某个特定颜色的透明度相比，这会设置所有选定元素以及它们的孩子节点的不透明度。为了看出他们的区别，我们来研究下面这个例子：

```text
<p>This paragraph is using RGBA for transparency</p>
<p>This paragraph is using opacity for transparency</p>
```

现在CSS是：

```text
/* Red with RGBA */
p:nth-child(1) {
  background-color: rgba(255,0,0,0.5);
}

/* Red with opacity */
p:nth-child(2) {
  background-color: rgb(255,0,0);
  opacity: 0.5;
}
```

结果如下：

在 CodePen 中打开在 JSFiddle 中打开

注意区别——第一个盒子使用RGBA颜色，只有一个半透明的背景。而一切在第二个盒子里的都是透明的，包括文本。您要仔细思考使用两者的时机——例如，当您想创建一个覆盖图片的标题，图片能透过标题显示，且标题的文本显示不受影响，此时应该使用RGBA修改标题背景色的透明度；另一方面，当您想要创建一个动画效果，让整个UI元素从完全隐藏到可见，此时应该使用不透明度（Opacity）。

### 进阶学习：拿颜色来练手[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E8%BF%9B%E9%98%B6%E5%AD%A6%E4%B9%A0%EF%BC%9A%E6%8B%BF%E9%A2%9C%E8%89%B2%E6%9D%A5%E7%BB%83%E6%89%8B) <a id="&#x8FDB;&#x9636;&#x5B66;&#x4E60;&#xFF1A;&#x62FF;&#x989C;&#x8272;&#x6765;&#x7EC3;&#x624B;"></a>

这个主动学习也没有正确的答案，我们只是想要你改变下面三个盒子的背景颜色值。尝试一下关键词，十六进制，RGB / HSLA / RGBA / HSLA 和不透明属性。看看你能找到哪些乐趣。

如果你犯了错,你可以使用reset按钮重置它。

在 CodePen 中打开在 JSFiddle 中打开

### 函数[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E5%87%BD%E6%95%B0) <a id="&#x51FD;&#x6570;"></a>

在程序中， [functions](https://developer.mozilla.org/zh-CN/docs/Glossary/functions)是代码中的可重复使用的部分，它可以多次运行，以便使开发人员和计算机以最小的代价完成重复的任务。函数通常存在于JavaScript，Python，C++等语言，但它也作为属性值存在于CSS中。我们已经在[Colors](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#Colors)部分中看到函数了，例如 [`rgb()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value#rgb%28%29)， [`hsl()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value#hsl%28%29)：

```text
background-color: rgba(255,0,0,0.5);
background-color: hsla(240,100%,50%,0.5);
```

这些函数用来计算使用什么颜色。

但是你在其他地方也会看到函数——每当你看到一个名字后跟着括号,括号里包含用逗号分隔的一个或多个值,那么你所使用的就是一个函数。例如:

```text
/* calculate the new position of an element after it has been rotated by 45 degress */
transform: rotate(45deg);
/* calculate the new position of an element after it has been moved across 50px and down 60px */
transform: translate(50px, 60px);
/* calculate the computed value of 90% of the current width minus 15px */
width: calc(90%-15px);
/* fetch an image from the network to be used as a background image */
background-image: url('myimage.png');
```

CSS有许多令人兴奋的功能，你将在适当的时候了解！

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Values_and_units#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

我们希望你已经了解了CSS值和单位——如果现在并不是完全明白，别担心；接下来你会在 CSS 语法部分得到更多的实践和学习。

