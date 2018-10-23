# 响应式图片



在这篇文章中我们将学习关于响应式图片——一种可以在不同的屏幕尺寸和分辨率的设备上都能良好工作以及其他特性的图片，并且看看HTML提供了什么工具来帮助实现它们。响应式图片仅仅只是响应式web设计的一部分（奠定了响应式web设计的良好基础），我们会在未来的[CSS topic](https://developer.mozilla.org/en-US/docs/Learn/CSS)模块中学到更多关于这一主题的知识。

| 学习本章节的前提: | 你应该已经了解了 [HTML的基础](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML) 以及如何 [在网站上添加静态图片](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML). |
| :--- | :--- |
| 目的: | 学习如何使用 [`srcset`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-srcset) 以及  [`<picture>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/picture) 元素，来实现网页中的响应式图片处理方法。 |

### 为什么要用自适应的图片？[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E7%94%A8%E8%87%AA%E9%80%82%E5%BA%94%E7%9A%84%E5%9B%BE%E7%89%87%EF%BC%9F) <a id="&#x4E3A;&#x4EC0;&#x4E48;&#x8981;&#x7528;&#x81EA;&#x9002;&#x5E94;&#x7684;&#x56FE;&#x7247;&#xFF1F;"></a>

让我们来看一个典型的场景。一个典型的网站可能会有一张页首图片，这让访问者看起来感到愉快。图片下面可能会添加一些内容图像。页首图像的跨度可能是整个页首的宽度。而内容图像会适应内容纵列的某处。此处有个简单的例子：

![Our example site as viewed on a wide screen - here the first image works ok, as it is big enough to see the detail in the center.](https://mdn.mozillademos.org/files/12940/picture-element-wide.png)

这个网页在宽屏设备上表现良好，例如笔记本电脑或台式机（你可以[查看在线演示](http://mdn.github.io/learning-area/html/multimedia-and-embedding/responsive-images/not-responsive.html)并且在GitHub上查看[源代码](https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/responsive-images/not-responsive.html)）。我们不会在这一节课中讨论CSS，除了下面提到的那些：

* 正文内容被设置的最大宽度为1200像素——在高于该宽度的视口中，正文保持在1200像素，并将其本身置于可用空间的中间。在该宽度以下的视口中，正文将保持在视口宽度的100%。
* 页眉图像被设置为使其中心始终位于页眉的中心，无论页眉的宽度是多少。所以如果网站被显示在窄屏上，图片中心的重要细节（里面的人）仍然可以看到，而两边超出的部分都消失了。它的高度是200px。
* 内容图片已经被设置为如果body元素比图像更小，图像就开始缩小，这样图像总是在正文里，而不是溢出正文。

然而，当你尝试在一个狭小的屏幕设备上查看本页面时，问题就会产生。网页的页眉看起来还可以，但是页眉这张图片占据了屏幕的一大部分的高度，在这个尺寸下，你在第一张图片的内容里很难看到人。

![Our example site as viewed on a narrow screen; the first image has shrunk to the point where it is hard to make out the detail on it.](https://mdn.mozillademos.org/files/12936/non-responsive-narrow.png)

一个改进的方法是，当网站在狭窄的屏幕上观看时，显示一幅图片的包含了重要细节的裁剪版本，第二个被裁剪的图片会在像平板电脑这样的中等宽度的屏幕设备上显示，这就是众所周知的**艺术方向问题（art direction problem）**。

另外，如果是在小屏手机屏幕上显示网页，那么没有必要在网页上嵌入这样大的图片。这被称之为**分辨率切换问题（resolution switching problem）**—一张位图被设置为固定像素的宽和高。当我们看[矢量图形](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web)时，一张较小的位图看来会有颗粒感，如果位图显示的尺寸大于原始尺寸（然而矢量图不会这样）。

相反，没有必要在比图片实际尺寸小的屏幕上显示一张大图，这样做会浪费带宽——当可以在设备上使用小图像时，手机用户尤其不愿意因为下载用于桌面的大图像而浪费带宽。理想的情况是当访问网站时依靠不同的设备来提供不同的分辨率图片和不同尺寸的图片。

让事情变得复杂的是，有些设备有很高的分辨率，为了显示的更出色，可能需要超出你预料的更大的图像。这从本质上是一样的问题，但在环境上有一些不同。

你可能会认为矢量图形能解决这些问题，在某种程度上是这样的——它们无论是文件大小还是比例都合适，无论在哪里你都应该尽可能的使用它们。然而，它们并不适合所有的图片类型，虽然在简单图形、图案、界面元素等方面较好，但如果是有大量的细节的照片，创建矢量图像会变得非常复杂。像JPEG格式这样的位图会更适合上面例子中的图像。

当web第一次出现时，这样的问题并不存在，在上世纪90年代中期，仅仅可以通过笔记本电脑和台式机来浏览web页面，所以浏览器开发者和规范制定者甚至没有想到要实现这种解决方式（响应式开发）。最近应用的响应式图像技术，通过让浏览器提供多个图像文件来解决上述问题，比如使用相同显示效果的图片但包含多个不同的分辨率（分辨率切换），或者使用不同的图片以适应不同的空间分配（艺术方向）。

**注意**: 在这篇文章中讨论的新特性 — [`srcset`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-srcset)/[`sizes`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-sizes)/ [`<picture>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/picture) — 都已经被新版本的现代浏览器和移动浏览器所支持（包括Edge，而不是IE）。

### 怎样创建自适应的图片?[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E6%80%8E%E6%A0%B7%E5%88%9B%E5%BB%BA%E8%87%AA%E9%80%82%E5%BA%94%E7%9A%84%E5%9B%BE%E7%89%87) <a id="&#x600E;&#x6837;&#x521B;&#x5EFA;&#x81EA;&#x9002;&#x5E94;&#x7684;&#x56FE;&#x7247;"></a>

在这一部分中，我们将看看上面说明的两个问题，并且展示怎样用HTML的响应式图片来解决这些问题。需要注意的是，如以上示例所示，在本节中我们将专注于HTML的 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)，但网站页眉的图片仅是装饰性的，实际上应该要用CSS的背景图片来实现。[CSS是比HTML更好的响应式设计的工具](http://blog.cloudfour.com/responsive-images-101-part-8-css-images/)，我们会在未来的CSS模块中讨论。

#### 分辨率切换：不同的尺寸[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E5%88%86%E8%BE%A8%E7%8E%87%E5%88%87%E6%8D%A2%EF%BC%9A%E4%B8%8D%E5%90%8C%E7%9A%84%E5%B0%BA%E5%AF%B8) <a id="&#x5206;&#x8FA8;&#x7387;&#x5207;&#x6362;&#xFF1A;&#x4E0D;&#x540C;&#x7684;&#x5C3A;&#x5BF8;"></a>

那么，我们想要用分辨率切换解决什么问题呢？我们想要显示相同的图片内容，仅仅依据设备来显示更大或更小的图片——这是我们在示例中使用第二个内容图像的情况。标准的[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)元素传统上仅仅让你给浏览器指定唯一的资源文件。

```text
<img src="elva-fairy-800w.jpg" alt="Elva dressed as a fairy">
```

我们可以使用两个新的属性——[`srcset`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-srcset) 和 [`sizes`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-sizes)——来提供更多额外的资源图像和提示，帮助浏览器选择正确的一个资源。你可以看到 [reponsive.html](http://mdn.github.io/learning-area/html/multimedia-and-embedding/responsive-images/responsive.html) 的例子，也可以在GitHub上看到[source code](https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/responsive-images/responsive.html)：

```text
<img srcset="elva-fairy-320w.jpg 320w,
             elva-fairy-480w.jpg 480w,
             elva-fairy-800w.jpg 800w"
     sizes="(max-width: 320px) 280px,
            (max-width: 480px) 440px,
            800px"
     src="elva-fairy-800w.jpg" alt="Elva dressed as a fairy">
```

`srcset`和`sizes`属性看起来很复杂，但是如果你按照上图所示进行格式化，那么他们并不是很难理解，每一行有不同的属性值。每个值都包含逗号分隔的列表。列表的每一部分由三个子部分组成。让我们来看看现在的每一个内容：

**srcset**定义了我们允许浏览器选择的图像集，以及每个图像的大小。在每个逗号之前，我们写：

1. 一个**文件名** \(`elva-fairy-480w.jpg`.\)
2. 一个空格
3. **图像的固有宽度**（以像素为单位）（480w）——注意到这里使用`w`单位，而不是你预计的`px`。这是图像的真实大小，可以通过检查你电脑上的图片文件找到（例如，在Mac上，你可以在Finder上选择这个图像，然后按 Cmd + I 来显示信息）。

**`sizes`**定义了一组媒体条件（例如屏幕宽度）并且指明当某些媒体条件为真时，什么样的图片尺寸是最佳选择—我们在之前已经讨论了一些提示。在这种情况下，在每个逗号之前，我们写：

1. 一个**媒体条件**（`(max-width:480px)`）——你会在 [CSS topic](https://developer.mozilla.org/en-US/docs/Learn/CSS)中学到更多的。但是现在我们仅仅讨论的是媒体条件描述了屏幕可能处于的状态。在这里，我们说“当视窗的宽度是480像素或更少”。
2. 一个空格
3. 当媒体条件为真时，图像将填充的**槽的宽度**（`440px`）

**注意**: 对于槽的宽度，你也许会提供一个固定值 \(`px`, `em`\) 或者是一个相对于视口的长度\(`vw`\)，但不是百分比。你也许以及注意到最后一个槽的宽度是没有媒体条件的，它是默认的，当没有任何一个媒体条件为真时，它就会生效。 当浏览器成功匹配第一个媒体条件的时候，剩下所有的东西都会被忽略，所以要注意媒体条件的顺序。

所以，有了这些属性，浏览器会：

1. 查看设备宽度
2. 检查`sizes`列表中哪个媒体条件是第一个为真
3. 查看给予该媒体查询的槽大小
4. 加载`srcset`列表中引用的最接近所选的槽大小的图像

就是这样！所以在这里，如果支持浏览器以视窗宽度为480px来加载页面，那么`(max-width: 480px)`的媒体条件为真，因此`440px`的槽会被选择，所以`elva-fairy-480w.jpg`将加载，因为它的的固定宽度（`480w`）最接近于`440px`。800px的照片大小为128KB而480px版本仅有63KB大小—节省了65KB。现在想象一下，如果这是一个有很多图片的页面。使用这种技术会节省移动端用户的大量带宽。

老旧的浏览器不支持这些特性，它会忽略这些特征。并继续正常加载 [`src`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-src)属性引用的图像文件。

**注意**: 在 HTML 文件中的 [`<head>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/head) 标签里， 你将会找到这一行代码 `<meta name="viewport" content="width=device-width">`: 这行代码会强制地让手机浏览器采用它们真实视图的宽度来加载网页（有些手机浏览器会提供不真实的视图宽度, 然后加载比浏览器真实视图的宽度大的宽度的网页，然后再缩小加载的页面，这样的做法对响应式图片或其他设计，没有任何帮助。我们会在未来的模块教给你更多关于这方面的知识）。

#### 一些有用的开发工具[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E4%B8%80%E4%BA%9B%E6%9C%89%E7%94%A8%E7%9A%84%E5%BC%80%E5%8F%91%E5%B7%A5%E5%85%B7) <a id="&#x4E00;&#x4E9B;&#x6709;&#x7528;&#x7684;&#x5F00;&#x53D1;&#x5DE5;&#x5177;"></a>

这里有一些在浏览器中的非常实用的[开发者工具](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools)用来帮助制定重要的槽宽度，以及其他你可能会用到的场景。当我在设置槽宽度的时候，我先加载了示例中的无响应的版本（`not-responsive.html`），然后进入 [响应设计视图](https://developer.mozilla.org/en-US/docs/Tools/Responsive_Design_Mode) （_Tools &gt; Web Developer &gt; Responsive Design View），_这个工具允许你在不同设备的屏幕宽度场景下查看网页的布局。

我设置我的视图宽度为 320px，然后再改为 480px；每一次宽度的改变我就进入 [DOM 检查 ](https://developer.mozilla.org/en-US/docs/Tools/Page_Inspector)，点击我们感兴趣的 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素，然后在显示屏右侧的 Box Model 视图选项卡中查看它的大小。 你应该会看到，这种无响应式的做法会让你的图片在不同屏幕宽度下有着固定的宽度。

![A screenshot of the firefox devtools with an image element highlighted in the dom, showing its dimensions as 440 by 293 pixels.](https://mdn.mozillademos.org/files/12932/box-model-devtools.png)

接着, 你可以检查 `srcset` 是否正常工作，你需要将视图的宽度设置为你想要的，\(比如，把宽度设置的比较小，让页面看起来比较狭窄），打开网络检查（_Tools &gt; Web Developer &gt; Network），_然后重新加载页面。网络检查工具会给你一个列表，里面的文件都是已经被下载来构造网页的。然后你可以在这里看到哪个图像文件被下载了。

**注意**: 在 Chrome 中测试时，通过如下方式禁用缓存：打开 DevTools ，并选中下 Settings &gt; Preferences &gt; Network 的选择框。否则，Chrome 会优先选择缓存图片而不是恰好适配的那个。

![a screenshot of the network inspector in firefox devtools, showing that the HTML for the page has been downloaded, along with three images, which include the two 800 wide versions of the responsive images](https://mdn.mozillademos.org/files/12934/network-devtools.png)

#### 分辨率切换: 相同的尺寸, 不同的分辨率[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E5%88%86%E8%BE%A8%E7%8E%87%E5%88%87%E6%8D%A2_%E7%9B%B8%E5%90%8C%E7%9A%84%E5%B0%BA%E5%AF%B8_%E4%B8%8D%E5%90%8C%E7%9A%84%E5%88%86%E8%BE%A8%E7%8E%87) <a id="&#x5206;&#x8FA8;&#x7387;&#x5207;&#x6362;_&#x76F8;&#x540C;&#x7684;&#x5C3A;&#x5BF8;_&#x4E0D;&#x540C;&#x7684;&#x5206;&#x8FA8;&#x7387;"></a>

如果你支持多种分辨率显示，但希望每个人在屏幕上看到的图片的实际尺寸是相同的，你可以让浏览器通过`srcset`和x语法结合——一种更简单的语法——而不用`sizes`，来选择适当分辨率的图片。你可以看一个例子 [srcset-resolutions.html](http://mdn.github.io/learning-area/html/multimedia-and-embedding/responsive-images/srcset-resolutions.html)（或 [the source code](https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/responsive-images/srcset-resolutions.html)）：

```text
<img srcset="elva-fairy-320w.jpg,
             elva-fairy-480w.jpg 1.5x,
             elva-fairy-640w.jpg 2x"
     src="elva-fairy-640w.jpg" alt="Elva dressed as a fairy">
```

![A picture of a little girl dressed up as a fairy, with an old camera film effect applied to the image](https://mdn.mozillademos.org/files/12942/resolution-example.png)在这个例子中，下面的CSS会应用在图片上，所以它的宽度在屏幕上是320像素（也称作CSS像素）：

```text
img {
  width: 320px;
}
```

在这种情况下，`sizes`并不需要——浏览器只是计算出正在显示的显示器的分辨率，然后提供`srcset`引用的最适合的图像。因此，如果访问页面的设备具有标准/低分辨率显示，一个设备像素表示一个CSS像素，`elva-fairy-320w.jpg`会被加载（1x 是默认值，所以你不需要写出来）。如果设备有高分辨率，两个或更多的设备像素表示一个CSS像素，`elva-fairy-640w.jpg` 会被加载。640px的图像大小为93KB，320px的图像的大小仅仅有39KB。

#### 艺术方向[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E8%89%BA%E6%9C%AF%E6%96%B9%E5%90%91) <a id="&#x827A;&#x672F;&#x65B9;&#x5411;"></a>

回顾一下，**艺术方向问题**涉及要更改显示的图像以适应不同的图像显示尺寸。例如，如果在桌面浏览器上的一个网站上显示一张大的、横向的照片，照片中央有个人，然后当在移动端浏览器上浏览这个网站时，照片会缩小，这时照片上的人会变得非常小，看起来会很糟糕。这种情况可能在移动端显示一个更小的肖像图会更好，这样人物的大小看起来更合适。 [`<picture>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/picture)元素允许我们这样实现。

回到我们最初的例子 [not-responsive.html](http://mdn.github.io/learning-area/html/multimedia-and-embedding/responsive-images/not-responsive.html) ，我们有一张图片需要艺术方向：

```text
<img src="elva-800w.jpg" alt="Chris standing up holding his daughter Elva">
```

让我们改用  [`<picture>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/picture)！就像[`<video>`和`<audio>`](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)， [`<picture>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/picture)素包含了一些 [`<source>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/source)元素，它使浏览器在不同资源间做出选择，紧跟着的是最重要的[`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)元素。[responsive.html](http://mdn.github.io/learning-area/html/multimedia-and-embedding/responsive-images/responsive.html)的代码如下：

```text
<picture>
  <source media="(max-width: 799px)" srcset="elva-480w-close-portrait.jpg">
  <source media="(min-width: 800px)" srcset="elva-800w.jpg">
  <img src="elva-800w.jpg" alt="Chris standing up holding his daughter Elva">
</picture>
```

*  `<source>`元素包含一个`media`属性，这一属性包含一个媒体条件——就像第一个`srcset`例子，这些条件来决定哪张图片会显示——第一个条件返回真，那么就会显示这张图片。在这种情况下，如果视窗的宽度为799px或更少，第一个`<source>`元素的图片就会显示。如果视窗的宽度是800px或更大，就显示第二张图片。
* `srcset`属性包含要显示图片的路径。请注意，正如我们在`<img>`上面看到的那样，`<source>`可以使用引用多个图像的`srcset`属性，还有`sizes`属性。所以你可以通过一个 `<picture>`元素提供多个图片，不过也可以给每个图片提供多分辨率的图片。实际上，你可能不想经常做这样的事情。
* 在任何情况下，你都必须在 `</picture>`之前正确提供一个`<img>`元素以及它的`src`和`alt`属性，否则不会有图片显示。当媒体条件都不返回真的时候（你可以在这个例子中删除第二个`<source>` 元素），它会提供图片；如果浏览器不支持 `<picture>`元素时，它可以作为后备方案。

这样的代码允许我们在宽屏和窄屏上都能显示合适的图片，像下面展示的一样：

![Our example site as viewed on a wide screen - here the first image works ok, as it is big enough to see the detail in the center.](https://mdn.mozillademos.org/files/12940/picture-element-wide.png)![Our example site as viewed on a narrow screen with the picture element used to switch the first image to a portrait close up of the detail, making it a lot more useful on a narrow screen](https://mdn.mozillademos.org/files/12938/picture-element-narrow.png)

**注意**: 你应该仅仅当在艺术方向场景下使用media属性；当你使用media时，不要在sizes属性中也提供媒体条件。

#### 为什么我们不能使用 CSS 或 JavaScript 来做到这一效果?[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E4%B8%BA%E4%BB%80%E4%B9%88%E6%88%91%E4%BB%AC%E4%B8%8D%E8%83%BD%E4%BD%BF%E7%94%A8_CSS_%E6%88%96_JavaScript_%E6%9D%A5%E5%81%9A%E5%88%B0%E8%BF%99%E4%B8%80%E6%95%88%E6%9E%9C) <a id="&#x4E3A;&#x4EC0;&#x4E48;&#x6211;&#x4EEC;&#x4E0D;&#x80FD;&#x4F7F;&#x7528;_CSS_&#x6216;_JavaScript_&#x6765;&#x505A;&#x5230;&#x8FD9;&#x4E00;&#x6548;&#x679C;"></a>

当浏览器开始加载一个页面, 它会先下载 \(预加载\) 任意的图片，这是发生在主解析器开始加载和解析页面的 CSS 和 JavaScript 之前的。这是一个非常有用的技巧，平均来说，页面加载的时间少了 20%。但是, 这对响应式图片一点帮助都没有, 所以需要实现类似 `srcset`的方法。因为你不能先加载好 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素后, 再用 JavaScript 检测视图的宽度，如果觉得大小不合适，就动态地加载小的图片替换已经加载好的图片，这样的话, 原始的图像已经被加载了, 然后你也加载了小的图像, 这样的做法对于响应式图像的理念来说，是很糟糕的。

* 
#### 大胆的使用现代图像格式[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E5%A4%A7%E8%83%86%E7%9A%84%E4%BD%BF%E7%94%A8%E7%8E%B0%E4%BB%A3%E5%9B%BE%E5%83%8F%E6%A0%BC%E5%BC%8F) <a id="&#x5927;&#x80C6;&#x7684;&#x4F7F;&#x7528;&#x73B0;&#x4EE3;&#x56FE;&#x50CF;&#x683C;&#x5F0F;"></a>

有很多令人激动的新图像格式（例如WebP和JPEG-2000）可以在有高质量的同时有较低的文件大小。然而，浏览器对其的支持参差不齐。

`<picture>`让我们能继续满足老式浏览器的需要。你可以在`type`属性中提供MIME类型，这样浏览器就能立即拒绝其不支持的文件类型：

```text
<picture>
  <source type="image/svg+xml" srcset="pyramid.svg">
  <source type="image/webp" srcset="pyramid.webp"> 
  <img src="pyramid.png" alt="regular pyramid built from four equilateral triangles">
</picture>
```

* 不要使用`media`属性，除非你也需要艺术方向。
* 在`<source>` 元素中，你只可以引用在`type`中声明的文件类型。
* 像之前一样，如果必要，你可以在`srcset`和`sizes`中使用逗号分割的列表。

### 主动学习：实现属于你的响应式图像[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E4%B8%BB%E5%8A%A8%E5%AD%A6%E4%B9%A0%EF%BC%9A%E5%AE%9E%E7%8E%B0%E5%B1%9E%E4%BA%8E%E4%BD%A0%E7%9A%84%E5%93%8D%E5%BA%94%E5%BC%8F%E5%9B%BE%E5%83%8F) <a id="&#x4E3B;&#x52A8;&#x5B66;&#x4E60;&#xFF1A;&#x5B9E;&#x73B0;&#x5C5E;&#x4E8E;&#x4F60;&#x7684;&#x54CD;&#x5E94;&#x5F0F;&#x56FE;&#x50CF;"></a>

在这次主动学习中，我们希望你变得勇敢和自力更生……我们希望你把自己拍摄的艺术截图，通过 `<picture>`来实现在窄屏幕和宽屏幕下的显示，以及使用 `srcset`切换不同的分辨率。

1. 写一些简单 HTML 来包含你的代码（如果你喜欢，也可以使用 `not-responsive.html` 作为起点）。
2. 找一张漂亮的宽屏风景图像，其中需要包含一些细节。使用图像编辑器创建一个网页大小的版本。然后裁剪一下，显示一个更小的部分，其中包含放大的细节, 然后创建第二张图片 \(差不多 480px 宽度比较好。\)
3. 使用 `<picture>` 元素来实现艺术图片切换器！
4. 创建不同大小的多张图片, 每个图片的图像都是一样的。
5. 使用 `srcset`/`size` 来创建一个分辨率切换器示例, 可以在不同的分辨率的情况下，提供相同尺寸的图像, 或者在不同的视图大小的情况下，提供不同尺寸大小的图像。

**注意**: 使用浏览器开发工具来帮助你工作时可以得到你需要的视图大小，就像上文提到的。

### 小结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E5%B0%8F%E7%BB%93) <a id="&#x5C0F;&#x7ED3;"></a>

这章节中充满了响应式图像 — 我们希望你学习新技术的过程是享受的。概括来说，有两个不同的问题，文章中我们一直在讨论：

* **艺术方向**：当你想为不同布局提供不同剪裁的图片——比如在桌面布局上显示完整的、横向图片，而在手机布局上显示一张剪裁过的、突出重点的纵向图片，可以用  [`<picture>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/picture)元素来实现。
* **分辨率切换**：当你想要为窄屏提供更小的图片时，因为小屏幕不需要像桌面端显示那么大的图片；以及你想为高/低分辨率屏幕提供不同分辨率的图片时，都可以通过 [vector graphics](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web) \(SVG images\)、 [`srcset`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-srcset) 以及 [`sizes`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-sizes) 属性来实现。

此时整个[Multimedia and embedding](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding) 模块接近尾声！在继续下一个模块之前，你现在唯一要做的就是尝试我们的多媒体评估，看看你做得怎样。玩的开心。

### 参阅[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E5%8F%82%E9%98%85) <a id="&#x53C2;&#x9605;"></a>

* [Jason Grigsby对响应式图片的出色介绍](http://blog.cloudfour.com/responsive-images-101-definitions)
* [R响应式图片：如果你只是在改变分辨率，就用srcset](https://css-tricks.com/responsive-images-youre-just-changing-resolutions-use-srcset/) — 包含了更多关于浏览器如何选择显示图片的解释
* [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img)
*  [`<picture>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/picture)
*  [`<source>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/source)

### 在这个模块中[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%E5%9C%A8%E8%BF%99%E4%B8%AA%E6%A8%A1%E5%9D%97%E4%B8%AD) <a id="&#x5728;&#x8FD9;&#x4E2A;&#x6A21;&#x5757;&#x4E2D;"></a>

* [HTML中的图片](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)
* [音视频内容](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)
* [从&lt;object&gt; 到&lt;iframe&gt; — 其他嵌入技术](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies)
* [给网页添加矢量图](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web)
* [响应式图片](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)
* [Mozilla醒目页面](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page)

