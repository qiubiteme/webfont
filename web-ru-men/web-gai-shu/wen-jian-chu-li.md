# 文件处理

一个网站由文本、代码、样式表、媒体内容等等的各种文件组成。当你开发网站时，你需要以清晰的结构将它们存储在你的本地计算机中，保证这些文件之间的联系，使它们看起来正确，然后才能将它们[上传至服务器](https://developer.mozilla.org/zh-CN/Learn/Getting_started_with_the_web/Publishing_your_website)。本节将会讨论一些你需要注意的问题，这样你就能创建清晰的文件结构。

### 网站应该存放在计算机何处？ <a id="&#x7F51;&#x7AD9;&#x5E94;&#x8BE5;&#x5B58;&#x653E;&#x5728;&#x8BA1;&#x7B97;&#x673A;&#x4F55;&#x5904;&#xFF1F;"></a>

当你在你自己的本地计算机操作你的网站时，你应该将所有关联的文件放在一个能反映服务器上文件结构的单独的文件夹里。这个文件夹可以存放在任何你喜欢的位置，不过你应该将它放在你容易找到的位置，或许可以是你的桌面，你的主页，或是磁盘根目录。

1. 选择一个位置存放你的网站项目。创建一个文件夹（在本文中，我们将其命名为 `web-projects`）。这将是你所有网站项目存放的位置。
2. 在该文件夹里新建另一个文件夹来存放你的第一个网页。在本文中，我们将其命名为 `test-site` （或者其它更有想象力的名称）。

### 一些关于大小写和空格的提示 <a id="&#x4E00;&#x4E9B;&#x5173;&#x4E8E;&#x5927;&#x5C0F;&#x5199;&#x548C;&#x7A7A;&#x683C;&#x7684;&#x63D0;&#x793A;"></a>

你会注意到，文中所有的文件夹名和文件都使用小写字母，且没有空格。这是因为：

1. 很多计算机，特别是 Web 服务器，是对大小写敏感的。举个例子，如果你将一张图片放在 `test-site/MyImage.jpg`，然后在一个不同的文件里你试图以 `test-site/myimage.jpg`  引用这张图片，这将不会起作用。
2. 浏览器，Web服务器，还有编程语言不能一致处理空格。举个例子，如果你在文件名里使用空格，一些系统会把它这个文件名视为两个文件名。一些服务器将会把你的文件名里的空格替换为 “%20”（URI 里空格的编码），破坏你所有的链接。最好使用横线，而不是下划线来分离单词：对比 `my-file.html` 和 `my_file.html` 。

简单地说，你应该在文件名中使用连字符。谷歌搜索引擎把连字符当作一个词的分隔符， 但不会以这种方式处理下划线。基于这些原因，至少在你知道自己在做什么之前，最好养成在文件夹和文件名中使用小写，并且使用短横线而不是空格来分隔的习惯。这样可以避免你在以后碰到一些问题。

### 网站应该使用什么结构？ <a id="&#x7F51;&#x7AD9;&#x5E94;&#x8BE5;&#x4F7F;&#x7528;&#x4EC0;&#x4E48;&#x7ED3;&#x6784;&#xFF1F;"></a>

接下来，看看我们的测试网站应该拥有什么结构。我们创建的任何网站项目中最常使用的就是一个索引 HTML 文件和不同的包括图像，样式表和脚本文件的文件夹。让我们现在创建它们：

1. **`index.html`** ：这个文件通常将包括你的主页内容，也就是说，人们第一次进入你的网页看到的文本和图像。使用你的文本编辑器，创建一个名为 `index.html` 的新文件并将其保存在 `test-site` 文件夹。
2. **`images` 文件夹** ：这个文件夹包含你网页上所有使用的图像。在 `test-site` 文件夹内创建一个 `images` 文件夹。
3. **`styles` 文件夹** ：这个文件夹包含了为你的内容添加样式的样式表（比如，设置文本颜色和背景颜色）。在 `test-site` 文件夹内创建一个 `styles` 文件夹。
4. **`scripts` 文件夹** ：这个文件夹包含了所有为你网页添加交互功能的 JavaScript 代码（比如点击时读取数据的按钮）。在 `test-site` 文件夹内创建一个 `scripts` 文件夹。

提示：在 Windows 系统中，你可能在查看文件名时会遇到问题，因为 Windows 默认开启一个名叫“隐藏已知文件类型扩展名”的选项。要关闭这个选项，你可以打开 Windows 资源管理器，选择“文件夹选项”，单击“选项”，取消“隐藏已知文件类型扩展名”复选框，然后点击“确定”。对于涉及您的 Windows 版本的更多具体信息，您可以在网上搜索。

### 文件路径 <a id="&#x6587;&#x4EF6;&#x8DEF;&#x5F84;"></a>

为了关联不同文件，你需要为它们提供文件路径——基本上是一个路线让一个文件知道另一个文件在哪。为了实现，我们将插入一小段HTML代码到 `index.html` 文件，让其显示你在[你的网站看起来是什么样的？](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/What_will_your_website_look_like) 文章里选择的图像。

1. 复制你之前保存的图像到 `images` 文件夹。
2. 打开  `index.html` 文件，准确插入以下代码。现在不理解代码的意义也不用担心——我们将在以后详细讲解此结构的信息。

   ```text
   <!DOCTYPE html>
   <html>
     <head>
       <meta charset="utf-8">
       <title>My test page</title>
     </head>
     <body>
       <img src="" alt="My test image">
     </body>
   </html>
   ```

3. 这行代码 `<img src="" alt="My test image">` 是在页面里插入图像的 HTML 代码。我们需要告诉 HTML 图像在哪里。这张图片在 _images 目录下，_而 _images_ 目录与 `index.html` 处于同级目录。要从 `index.html` 所处一级目录进入图片所在目录，我们所需的文件路径是 `images/你的图像文件名` 。例如，我们的图像叫做 `firefox-icon.png` ，所以文件路径就是 `images/firefox-icon.png` 。
4. 在 HTML 代码里 `src＝""` 的双引号中插入文件路径。
5. 保存 HTML 文件，然后使用浏览器打开（双击文件）。你应该看到展示着你的图像的新网页！

![A screenshot of our basic website showing just the firefox logo - a flaming fox wrapping the world](https://mdn.mozillademos.org/files/9229/website-screenshot.png)

一些文件路径的通用规则：

* 要引用一个位于调用的 HTML 文件同级目录的目标文件，只需直接使用文件名，比如  `my-image.jpg` 。
* 要引用一个子目录的文件，在路径前写下目录名并加一个斜杠，比如 `subdirectory/my-image.jpg` 。
* 要引用一个位于调用的 HTML 文件的**父级**目录的目标文件，加上两个点。举个例子，如果 `index.html` 在  `test-site` 下面的一个子目录而 `my-image.png` 在 `test-site` 目录，你可以在 `index.html` 里使用 `../my-image.png` 引用 `my-image.png` 。
* 你可以随意组合以上方法，比如 `../subdirectory/another-subdirectory/my-image.png`.

到此为止，这就是你需要知道的全部内容。

提示：Windows 文件系统会使用反斜杠而不是斜杠，比如 `C:\windows` 。这在 HTML 里没什么关系，就算你在 Windows 上开发你的网页，你仍应该在你的代码中使用斜杠。

### 还有什么要做的？ <a id="&#x8FD8;&#x6709;&#x4EC0;&#x4E48;&#x8981;&#x505A;&#x7684;&#xFF1F;"></a>

我们差不多都做完了。你的文件夹结构应该像这样：

![A file structure in mac os x finder, showing an images folder with an image in, empty scripts and styles folders, and an index.html file](https://mdn.mozillademos.org/files/9231/file-structure.png)



