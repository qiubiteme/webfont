# 使用JavaScript发送表单



正如在[前面的文章](https://developer.mozilla.org/en-US/docs/HTML/Forms/Sending_and_retrieving_form_data)中讲到的，HTML表单可以声明式地发送一个HTTP请求。 但表单也可以通过JavaScript来准备一个用于发送的HTTP请求。 本文探讨如何做到这一点。

### 一个表单并不总是一个表单[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E4%B8%80%E4%B8%AA%E8%A1%A8%E5%8D%95%E5%B9%B6%E4%B8%8D%E6%80%BB%E6%98%AF%E4%B8%80%E4%B8%AA%E8%A1%A8%E5%8D%95) <a id="&#x4E00;&#x4E2A;&#x8868;&#x5355;&#x5E76;&#x4E0D;&#x603B;&#x662F;&#x4E00;&#x4E2A;&#x8868;&#x5355;"></a>

随着[开放Web应用程序](https://developer.mozilla.org/en-US/docs/Open_Web_apps_and_Web_standards)的兴起，使用[HTML forms](https://developer.mozilla.org/en-US/docs/HTML/Forms)而不是文字表单\(literal forms for humans\)日益普遍 - 越来越多的开发人员正在控制传输数据。

#### 获得整体界面的控制[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E8%8E%B7%E5%BE%97%E6%95%B4%E4%BD%93%E7%95%8C%E9%9D%A2%E7%9A%84%E6%8E%A7%E5%88%B6) <a id="&#x83B7;&#x5F97;&#x6574;&#x4F53;&#x754C;&#x9762;&#x7684;&#x63A7;&#x5236;"></a>

标准的HTML表单提交加载URL，这个URL是数据要发送的位置，这意味着浏览器窗口以整页加载进行导航。 避免整页加载可以通过隐藏闪烁和网络滞后来提供更平滑的体验。

许多现代用户界面只使用HTML表单来收集用户的输入。 当用户尝试发送数据时，应用程序将在后台异步控制和传输数据，只更新UI中需要更改的部分。

异步地发送任何数据被称为[AJAX](https://developer.mozilla.org/zh-CN/docs/AJAX), 代表"Asynchronous JavaScript And XML"。

#### 表单提交和AJAX请求之间的区别?[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E8%A1%A8%E5%8D%95%E6%8F%90%E4%BA%A4%E5%92%8CAJAX%E8%AF%B7%E6%B1%82%E4%B9%8B%E9%97%B4%E7%9A%84%E5%8C%BA%E5%88%AB) <a id="&#x8868;&#x5355;&#x63D0;&#x4EA4;&#x548C;AJAX&#x8BF7;&#x6C42;&#x4E4B;&#x95F4;&#x7684;&#x533A;&#x522B;"></a>

AJAX 技术主要依靠 [`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest) \(XHR\) DOM 对象。它可以构造HTTP请求，并获取请求结果。

**注意:** 老的 AJAX 技术可能不依赖 [`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest). 例如, [JSONP](http://en.wikipedia.org/wiki/JSONP) 结合 [`eval()`](https://developer.mozilla.org/en-US/docs/Core_JavaScript_1.5_Reference:Global_Functions:eval) 函数. 它可以使用, 但是因其严重的安全问题不推荐使用。使用它的唯一原因是老的浏览器不支持 [`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest) 或 [JSON](https://developer.mozilla.org/en-US/docs/JSON), 但是那些确实是非常古老的浏览器！**避免使用这种技术.**

创建之初, [`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest) 被提出是打算将 [XML](https://developer.mozilla.org/zh-CN/docs/XML) 做为传输数据的格式。不过，JSON已经取代了XML，而且今天已经非常普遍了。

但是XML和JSON都不适合表单数据请求编码。 表单数据\(`application/x-www-form-urlencoded`\)由URL编码的键/值对列表组成。为了传输二进制数据，HTTP请求被重新整合成`multipart/form-data`。

如果您控制前端（在浏览器中执行的代码）和后端（在服务器上执行的代码），则可以发送JSON / XML并根据需要处理它们。

但是，如果你想使用第三方服务，这并不容易。 有些服务只接受表单数据。 也有使用表单数据更简单的情况。 如果数据是键/值对或原始二进制数据，现有的后端工具可以处理它，而不需要额外的代码。

那么如何发送这样的数据呢？

### 发送表单数据[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E5%8F%91%E9%80%81%E8%A1%A8%E5%8D%95%E6%95%B0%E6%8D%AE) <a id="&#x53D1;&#x9001;&#x8868;&#x5355;&#x6570;&#x636E;"></a>

一共有三种方式来发送表单数据:包括两种传统的方法和一种利用[`formData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData)对象的新方法.让我们仔细看一下:

#### 在DOM中构建一个隐藏的iframe[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E5%9C%A8DOM%E4%B8%AD%E6%9E%84%E5%BB%BA%E4%B8%80%E4%B8%AA%E9%9A%90%E8%97%8F%E7%9A%84iframe) <a id="&#x5728;DOM&#x4E2D;&#x6784;&#x5EFA;&#x4E00;&#x4E2A;&#x9690;&#x85CF;&#x7684;iframe"></a>

异步发送表单数据的最古老方法是用DOM API构建表单，然后将其数据发送到隐藏的 [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe)。 要访问提交的结果，请获取 [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe)的内容。

**警告:** **避免使用这项技术.** 有第三方服务的安全风险，因为它使你暴露在 [脚本注入攻击](http://en.wikipedia.org/wiki/Cross-site_scripting) 中. 如果你使用 HTTPS，它可以影响 [同源策略](https://developer.mozilla.org/en-US/docs/JavaScript/Same_origin_policy_for_JavaScript), 可以提供不可用的  [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe) 内容。然而，该方法可能是你需要支持很古老的浏览器的唯一选择。

下面是个简单的例子:

```text
<button onclick="sendData({test:'ok'})">点击我！</button>
```

所有操作都在下面这段脚本里:

```text
// 首先创建一个用来发送数据的iframe.
var iframe = document.createElement("iframe");
iframe.name = "myTarget";

// 必须把这个iframe插入当前文档.
window.addEventListener("load", function () {
  iframe.style.display = "none";
  document.body.appendChild(iframe);
});

// 下面这个函数是真正用来发送数据的.
// 它只有一个参数,一个包含键值对数据格式的对象.
function sendData(data) {
  var name,
      form = document.createElement("form"),
      node = document.createElement("input");

  // 注册iframe的load事件处理程序,如果你需要在响应返回时执行一些操作的话.
  iframe.addEventListener("load", function () {
    alert("Yeah! Data sent.");
  });
    
  form.action = "http://www.cs.tut.fi/cgi-bin/run/~jkorpela/echo.cgi";
  form.target = iframe.name;

  for(name in data) {
    node.name  = name;
    node.value = data[name].toString();
    form.appendChild(node.cloneNode());
  }

  // 表单元素需要添加到主文档中.
  form.style.display = "none";
  document.body.appendChild(form);

  form.submit();

  // 表单提交后,就可以删除这个表单,不影响下次的数据发送.
  document.body.removeChild(form);
}
```

在线演示:

在 CodePen 中打开在 JSFiddle 中打开

#### 手动构建XMLHttpRequest[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E6%89%8B%E5%8A%A8%E6%9E%84%E5%BB%BAXMLHttpRequest) <a id="&#x624B;&#x52A8;&#x6784;&#x5EFA;XMLHttpRequest"></a>

[`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest)是进行HTTP请求的最安全和最可靠的方式。 要使用[`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest)发送表单数据，请通过对URL进行编码来准备数据，并遵守表单数据请求的具体内容。

**注:** 如果你想要了解更多关于XMLHttpRequest的知识，这里有两篇文章你可能会感兴趣:[An introductory article to AJAX](https://developer.mozilla.org/zh-CN/docs/AJAX/Getting_Started) 和更高级点的[using XMLHttpRequest](https://developer.mozilla.org/zh-CN/docs/DOM/XMLHttpRequest/Using_XMLHttpRequest).

还是上一节的这个例子:

```text
<button type="button" onclick="sendData({test:'ok'})">点击我！</button>
```

正如你所看到的，HTML并没有改变。 但是，JavaScript是完全不同的：

```text
function sendData(data) {
  var XHR = new XMLHttpRequest();
  var urlEncodedData = "";
  var urlEncodedDataPairs = [];
  var name;

  // 将数据对象转换为URL编码的键/值对数组。
  for(name in data) {
    urlEncodedDataPairs.push(encodeURIComponent(name) + '=' + encodeURIComponent(data[name]));
  }

  // 将配对合并为单个字符串，并将所有%-编码空间替换为
  // “+”字符；匹配浏览器窗体提交的行为。
  urlEncodedData = urlEncodedDataPairs.join('&').replace(/%20/g, '+');

  // 定义成功数据提交时发生的情况
  XHR.addEventListener('load', function(event) {
    alert('Yeah! Data sent and response loaded.');
  });

  // 定义错误提示
  XHR.addEventListener('error', function(event) {
    alert('哎呀！出了问题。');
  });

  // 建立我们的请求
  XHR.open('POST', 'https://example.com/cors.php');

  // 为表单数据POST请求添加所需的HTTP头
  XHR.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');

  // 最后，发送我们的数据。
  XHR.send(urlEncodedData);
}
```

在线演示:

在 CodePen 中打开在 JSFiddle 中打开

**注:** 使用[`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest)会受到同源策略的影响,如果你需要执行跨域请求,你需要熟悉一下[CORS和HTTP访问控制](https://developer.mozilla.org/zh-CN/docs/HTTP/Access_control_CORS).

#### 使用 XMLHttpRequest 和 the FormData object（表单对象）[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E4%BD%BF%E7%94%A8_XMLHttpRequest_%E5%92%8C_the_FormData_object%EF%BC%88%E8%A1%A8%E5%8D%95%E5%AF%B9%E8%B1%A1%EF%BC%89) <a id="&#x4F7F;&#x7528;_XMLHttpRequest_&#x548C;_the_FormData_object&#xFF08;&#x8868;&#x5355;&#x5BF9;&#x8C61;&#xFF09;"></a>

手动建立一个HTTP请求可能是一个巨大的挑战（can be overwhelming）。 幸运的是，最近的[XMLHttpRequest 规范](http://www.w3.org/TR/XMLHttpRequest/)提供了一种方便简单的方法来处理带有[`FormData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData)对象的表单数据请求。

可以使用 [`FormData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData) 对象来构建用于传输的表单数据，或者获取表单元素中的数据来管理它的发送方式。 请注意，[`FormData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData) 对象是“只写”，这意味着您可以更改它们，但不检索其内容。

使用这个对象在[Using FormData Objects](https://developer.mozilla.org/en-US/docs/DOM/XMLHttpRequest/FormData/Using_FormData_Objects)中有详细的介绍，但是这里有两个例子：

**向FormData对象中手动添加数据**

```text
<button type="button" onclick="sendData({test:'ok'})">点击我！</button>
```

你应该对那个HTML示例感到熟悉。

```text
function sendData(data) {
  var XHR = new XMLHttpRequest();
  var FD  = new FormData();

  // 把我们的数据添加到这个FormData对象中
  for(name in data) {
    FD.append(name, data[name]);
  }

  // 定义数据成功发送并返回后执行的操作
  XHR.addEventListener('load', function(event) {
    alert('Yeah! Data sent and response loaded.');
  });

  // 定义发生错误时执行的操作
  XHR.addEventListener('error', function(event) {
    alert('Oups! Something goes wrong.');
  });

  // 设置请求地址和方法
  XHR.open('POST', 'http://ucommbieber.unl.edu/CORS/cors.php');

  // 发送这个formData对象,HTTP请求头会自动设置
  XHR.send(FD);
}
```

在线演示:

在 CodePen 中打开在 JSFiddle 中打开

**使用绑定到表单元素上的 FormData** 

你也可以绑定一个 `FormData` 对象到一个 [`<form>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form) 元素上。这会创建一个 `FormData` ，代表表单中包含的元素。

这段HTML是典型的情况：

```text
<form id="myForm">
  <label for="myName">告诉我你的名字：</label>
  <input id="myName" name="name" value="John">
  <input type="submit" value="提交">
</form>
```

但是JavaScript接管了这个表单：

```text
window.addEventListener("load", function () {
  function sendData() {
    var XHR = new XMLHttpRequest();

    // 我们把这个 FormData 和表单元素绑定在一起。
    var FD  = new FormData(form);

    // 我们定义了数据成功发送时会发生的事。
    XHR.addEventListener("load", function(event) {
      alert(event.target.responseText);
    });

    // 我们定义了失败的情形下会发生的事
    XHR.addEventListener("error", function(event) {
      alert('哎呀！出了问题。');
    });

    // 我们设置了我们的请求
    XHR.open("POST", "http://ucommbieber.unl.edu/CORS/cors.php");

    // 发送的数据是由用户在表单中提供的
    XHR.send(FD);
  }
 
  // 我们需要获取表单元素
  var form = document.getElementById("myForm");

  // 接管表单的提交事件
  form.addEventListener("submit", function (event) {
    event.preventDefault();

    sendData();
  });
});
```

在线演示:

在 CodePen 中打开在 JSFiddle 中打开

### 发送二进制数据[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E5%8F%91%E9%80%81%E4%BA%8C%E8%BF%9B%E5%88%B6%E6%95%B0%E6%8D%AE) <a id="&#x53D1;&#x9001;&#x4E8C;&#x8FDB;&#x5236;&#x6570;&#x636E;"></a>

如果你用来初始化[`formData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData)对象的那个表单中包含了一个文件输入框\(type=file的input元素\),则在发送AJAX时,用户在这个文件输入框中选定的文件也会被发送,和正常的表单提交一样.而且即使你没有用表单初始化这个formData对象,你同样可以手动向这个formData对象中添加若干个二进制数据.

二进制数据的来源主要有三种:[`FileReader`](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader) API,[`Canvas`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement) API,[WebRTC](https://developer.mozilla.org/zh-CN/docs/WebRTC/navigator.getUserMedia) API.不幸的是,在一些旧的浏览器中,我们没有能力访问二进制数据,或者需要一些很繁杂的解决办法才能实现.访问二进制数据已经超出了本文的介绍范围.如果你想知道更多关于`FileReader` API的知识,你可以阅读:[如何在web应用程序中使用文件](https://developer.mozilla.org/zh-CN/docs/Using_files_from_web_applications).

使用[`formData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData)发送二进制数据非常简单,只需要调用`append方法将你需要发送的File对象或者Blob对象添加进去`.

在下面的例子中,我们使用了[`FileReader`](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader) API来访问二进制数据,然后发送这个请求:

```text
<form id="myForm">
  <p>
    <label for="i1">文本数据：</label>
    <input id="i1" name="myText" value="一些文本数据">
  </p>
  <p>
    <label for="i2">文件数据：</label>
    <input id="i2" name="myFile" type="file">
  </p>
  <button>提交</button>
</form>
```

上面是一个普通的表单,包含一个文件输入框,下面是要执行的JavaScript代码.

```text
// 因为我们想获取DOM节点,
// 我们在页面加载时初始化我们的脚本.
window.addEventListener('load', function () {

  // 这些变量用于存储表单数据
  var text = document.getElementById("i1");
  var file = {
        dom    : document.getElementById("i2"),
        binary : null
      };
 
  // 使用 FileReader API 获取文件内容
  var reader = new FileReader();

  // 因为 FileReader 是异步的, 会在完成读取文件时存储结果
  reader.addEventListener("load", function () {
    file.binary = reader.result;
  });

  // 页面加载时, 如果一个文件已经被选择, 那么读取该文件.
  if(file.dom.files[0]) {
    reader.readAsBinaryString(file.dom.files[0]);
  }

  // 如果没有，一旦用户选择了它，就读取文件。
  file.dom.addEventListener("change", function () {
    if(reader.readyState === FileReader.LOADING) {
      reader.abort();
    }
    
    reader.readAsBinaryString(file.dom.files[0]);
  });

  // 在我们的主函数中发送数据
  function sendData() {
    // 如果存在被选择的文件，等待它读取完成
    // 如果没有, 延迟函数的执行
    if(!file.binary && file.dom.files.length > 0) {
      setTimeout(sendData, 10);
      return;
    }

    // 要构建我们的多部分表单数据请求,
    // 我们需要一个XMLHttpRequest 实例
    var XHR = new XMLHttpRequest();

    // 我们需要一个分隔符来定义请求的每一部分。
    var boundary = "blob";

    // 将我们的请求主体存储于一个字符串中
    var data = "";

    // 所以，如果用户已经选择了一个文件
    if (file.dom.files[0]) {
      // 在请求体中开始新的一部分
      data += "--" + boundary + "\r\n";

      // 把它描述成表单数据
      data += 'content-disposition: form-data; '
      // 定义表单数据的名称
            + 'name="'         + file.dom.name          + '"; '
      // 提供文件的真实名字
            + 'filename="'     + file.dom.files[0].name + '"\r\n';
      // 和文件的MIME类型
      data += 'Content-Type: ' + file.dom.files[0].type + '\r\n';

      // 元数据和数据之间有一条空行。
      data += '\r\n';
      
      // 添加二进制数据到请求体中
      data += file.binary + '\r\n';
    }

    // 文本数据是简单的
    // 开始一个新的部分在请求体中
    data += "--" + boundary + "\r\n";

    // 说它是表单数据，并命名它
    data += 'content-disposition: form-data; name="' + text.name + '"\r\n';
    // 元数据和数据之间有一条空行。
    data += '\r\n';

    // 添加文本数据到请求体中
    data += text.value + "\r\n";

    // 一旦完成，关闭请求体
    data += "--" + boundary + "--";

    // 定义成功提交数据执行的语句
    XHR.addEventListener('load', function(event) {
      alert('✌！数据已发送且响应已加载。');
    });

    // 定义发生错误时做的事
    XHR.addEventListener('error', function(event) {
      alert('哎呀！出了问题。');
    });

    // 建立请求
    XHR.open('POST', 'https://example.com/cors.php');

    // 添加需要的HTTP报头来处理多部分表单数据POST请求
    XHR.setRequestHeader('Content-Type','multipart/form-data; boundary=' + boundary);

    // 最后，发送数据。
    XHR.send(data);
  }

  // 访问表单…
  var form = document.getElementById("myForm");

  // ……接管提交事件
  form.addEventListener('submit', function (event) {
    event.preventDefault();
    sendData();
  });
});
```

在线演示:

在 CodePen 中打开在 JSFiddle 中打开

### 总结[Section](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript#%E6%80%BB%E7%BB%93) <a id="&#x603B;&#x7ED3;"></a>

取决于不同的浏览器，通过JavaScript发送数据可能会很简单，也可能会很困难。[`FormData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData) 对象是通用的答案, 所以请毫不犹豫的在旧浏览器上通过polyfill使用它:

* 此[ gist](https://gist.github.com/3120320) 通过[`Web Workers`](https://developer.mozilla.org/zh-CN/docs/Web/API/Using_web_workers) polyfill 了 `FormData` 。
* [HTML5-formdata](https://github.com/francois2metz/html5-formdata) 试图 polyfill `FormData` 对象, 但是需要 [File API](http://www.w3.org/TR/FileAPI/)
* 这个[polyfill](https://github.com/jimmywarting/FormData) 提供了 FormData 所有的大部分新方法 \(entries, keys, values, 以及对 `for...of` 的支持\)

