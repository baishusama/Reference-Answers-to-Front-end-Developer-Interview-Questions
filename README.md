# Reference-Answers-to-Front-end-Developer-Interview-Questions

> 本文主要是对 GitHub 上的热门[前端工作面试问题](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/Translations/Chinese/README.md)（[Front-end-developer-interview-questions](http://h5bp.github.io/Front-end-Developer-Interview-Questions/)）的答案的搜集和整理。  
> 
> 本文的主要参考来源：  
> [最全前端开发面试问题及答案整理 - AutumnsWinds](https://github.com/baishusama/Front-end-questions-to-the-interview-stage)   
> [前端面试问题 - handyxuefeng的博客](http://handyxuefeng.blog.163.com/blog/static/454521722013111714040259/)  
> [前端工作面试问题 - caibaojian的博客](http://caibaojian.com/f2e-interview.html)  
> [前端开发面试题及答案 - 郑州网建](http://camnpr.com/archives/front-end-developer-interview-answers.html)  
> P.S.上面第一篇在GitHub上已删（原因不明）。我个人觉得这篇整理的相当地好啊……这里提供原po主的知乎 - [秋风](https://www.zhihu.com/people/autumnswind)。  
> 
> 由于本人还只是个前端萌新，以下内容多有疏漏和理解不当之处，仅供学习交流参考用。  
> ——献给和我一样在前端的路上前行的人们。共勉。

## HTML 相关问题 ##

### doctype(文档类型) 的作用是什么？ ###

1. `<!DOCTYPE>` 声明位于文档中的最前面，处于 `<html>` 标签之前。（这样一来，在浏览器解析 HTML 文档正文之前就可以确定当前文档的类型，以决定其需要采用的
渲染模式。）
2. `<!DOCTYPE>`声明不是 HTML 标签，它**是文档类型标签**。该标签是将特定的标准通用标记语言或者 XML 文档（网页就是其中一种）与文档类型定义（DTD）联系起来的指令。
3. 它的目的是要告诉标准通用标记语言解析器，它应该使用什么样的文档类型定义（DTD -  Document Type Declaration）来解析文档。**告知浏览器以何种模式来渲染文档**。（不同的渲染模式会影响到浏览器对于 CSS 代码甚至 JavaScript 脚本的解析）。
4. `DOCTYPE`不存在或格式不正确会导致文档以混杂模式呈现。 
5. 还与有效性验证有关——《精通CSS II》

> 在 HTML 4.01 中，`<!DOCTYPE>` 声明引用 DTD，因为 HTML 4.01 基于 SGML。DTD 规定了标记语言的规则，这样浏览器才能正确地呈现内容。  
> HTML5 不基于 SGML，所以不需要引用 DTD。
> 
> [HTML `<!DOCTYPE>` 标签 - w3school](http://www.w3school.com.cn/tags/tag_doctype.asp)

### 浏览器标准模式 (standards mode) 、几乎标准模式（almost standards mode）和怪异模式 (quirks mode) 之间的区别是什么？ ###

1. 标准模式（standards mode）（严格呈现模式）：用于呈现遵循最新标准的网页。其排版和`JS`运作模式以该浏览器支持的最高标准运行。
2. 几乎标准模式（almost standards mode）：在尽可能遵循标准的基础上兼容部分非标准代码，比如一些已经弃用的标签等。它实现传统的表格单元格的垂直尺寸(没有严格的遵照CSS2规范)。（见下面代码例子。）
3. 怪异模式（quirks mode）（包容模式，松散呈现模式，兼容模式，混杂模式）：用于呈现为传统浏览器而设计的网页。

```html5
<table style="border:1px solid blue;" cellspacing="0">
    <tr><td>
        <img style="border:1px solid red" width="364" height="126" src="images/logo.png"/>
    </td></tr>
</table>
```

"几乎标准模式"下，图片底部和table也是没空白的；而较新的浏览器在标准模式下图片底部和table会有个空白。

> [doctype声明、浏览器的标准、怪异等模式 - 雨中无伞](http://www.cnblogs.com/yuzhongwusan/archive/2012/02/17/2355695.html)：好像是个厉害的程序媛！日历下面的仓鼠动画好可爱_(:зゝ∠)_  
> 

### HTML 和 XHTML 有什么区别？ ###

1. 所有的标记都必须要有一个相应的结束标记——**标签必须被关闭**。
2. 所有的`XML`标记都**标签必须合理嵌套**。
3. 所有标签的元素和属性的名字都必须使用小写——**标签名属性名必须小写**。
4. 给所有属性赋一个值——所有**属性必须有一个值**——属性简写是不被允许的。
5. 所有的**属性值必须用引号""括起来**。
6. **用`id`属性来替代`name`属性**。（注意：为了向后兼容，应该同时使用`name`和`id`属性，并使它们两个的值相同。）
7. 所有**特殊符号`<`,`>`,`&`用编码表示**——`&lt;`，`&gt;`，`&amp;`。
8. **图片必须有`ALT`说明文字**。
9. 不要在注释内容中使`--`。


### 如果页面使用 `application/xhtml+xml`会有什么问题吗？ ###

一些老的浏览器并不兼容。

> 上面提过的[doctype声明、浏览器的标准、怪异等模式 - 雨中无伞](http://www.cnblogs.com/yuzhongwusan/archive/2012/02/17/2355695.html)这篇里，也有这部分内容。


### 如果网页内容需要支持多语言，你会怎么做？ ###

采用统一编码`UTF-8`模式。


### 在设计和开发多语言网站时，有哪些问题你必须要考虑？ ###

1. 应用字符集的选择
2. 语言书写习惯 & 导航结构
3. 数据库驱动型网站
4. 搜索引擎 & 市场推广

> [多语言网站设计需要注意的问题](http://handyxuefeng.blog.163.com/blog/static/454521722013111732534620/)


### 使用`data-`属性的好处是什么？ ###

`data-`是`HTML5`为前端开发者提供自定义的属性，这些属性集可以通过对象的`dataset`属性获取，不支持该属性的浏览器可以通过 `getAttribute`方法获取。ppk提到过使用`rel`属性，lightbox库推广了`rel`属性，`HTML5`提供了`data-`做替代，这样可以更好地使用自定义的属性。

```html5
<div data-author="imo" data-time="2016-04-14" data-comment-num="10" data-category="javascript">
    ... 
</div>
```

上面`HTML`代码提供了单个文章所拥有的一些属性。通过`JS`代码可以获得这些自定义的属性。

```script
var post = document.getElementsByTagName('div')[0];
post.dataset; //DOMStringMap
post.dataset.commentNum; //10
```

需要注意的是，`data-`之后的以连字符分割的多个单词组成的属性，获取的时候使用驼峰风格。

并不是所有的浏览器都支持`.dataset`属性~~，测试的浏览器中只有Chrome和Opera支持？~~。


### 如果把 HTML5 看作做一个开放平台，那它的构建模块有哪些？ ###

> 开放平台（Open Platform）
> 是指软件系统通过公开其应用程序编程接口（API）或函数（function）来使外部的程序可以增加该软件系统的功能或使用该软件系统的资源，而不需要更改该软件系统的源代码。

`<nav>`，`<header>`，`<section>`，`<footer>`

> [必须知道的七个HTML5新特性 - 郑州网建](http://camnpr.com/archives/must-know-the-seven-html5-features.html)


### 请描述 cookies、sessionStorage 和 localStorage 的区别。 ###

![cookies VS localStorage VS sessionStorage](https://raw.githubusercontent.com/baishusama/images-warehouse/master/images-learning/cookie_VS_localStorage_VS_sessionStorage.png)

（下面这几段和表格内容有重复，重点看加粗部分。P.S.表格是我自己做的XD）

Web Storage的概念和cookie相似，区别是它是为了更大容量存储设计的。Cookie的大小是受限的，并且**每次你请求一个新的页面的时候Cookie都会被发送过去，这样无形中浪费了带宽，另外cookie还需要指定作用域，不可以跨域调用。**  
除此之外，Web Storage拥有setItem,getItem,removeItem,clear等方法（也就是说localStorage和sessionStorage都具有这些方法），不像cookie需要前端开发者自己封装setCookie，getCookie。  
但是cookie也是不可以或缺的：**cookie的作用是与服务器进行交互，作为HTTP规范的一部分而存在** ，而Web Storage仅仅是为了在本地“存储”数据而生。  
浏览器的支持除了IE７及以下不支持外，其他标准浏览器都完全支持(ie及FF需在web服务器里运行)，值得一提的是IE总是办好事，例如IE7、IE6中的userData其实就是javascript本地存储的解决方案。通过简单的代码封装可以统一到所有的浏览器都支持web storage。  

> **cookie优点：极高的扩展性和可用性**
> 
> 1. 通过良好的编程，控制保存在cookie中的session对象的大小。
> 2. 通过加密和安全传输技术（SSL），减少cookie被破解的可能性。
> 3. 只在cookie中存放不敏感数据，即使被盗也不会有重大损失。
> 4. 控制cookie的生命期，使之不会永远有效。偷盗者很可能拿到一个过期的cookie。

> **cookie缺点**
> 
> 1. Cookie数量和长度的限制。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB，否则会被截掉。
> 2. 安全性问题。如果cookie被人拦截了，那人就可以取得所有的session信息。即使加密也与事无补，因为拦截者并不需要知道cookie的意义，他只要原样转发cookie就可以达到目的了。
> 3. 有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用。

> **cookie和session的区别**
> 
> 1. cookie数据存放在客户的浏览器上，session数据放在服务器上。
> 2. cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗
    考虑到安全应当使用session。
> 3. session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能
     考虑到减轻服务器性能方面，应当使用COOKIE。
> 4. 单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。
> 5. 所以个人建议：
    将登陆信息等重要信息存放为SESSION
    其他信息如果需要保留，可以放在COOKIE中

> **Web Storage带来的好处**
> 
> 1. 减少网络流量：一旦数据保存在本地后，就可以避免再向服务器请求数据，因此减少不必要的数据请求，减少数据在浏览器和服务器间不必要地来回传递。
> 2. 快速显示数据：性能好，从本地读数据比通过网络从服务器获得数据快得多，本地数据可以即时获得。再加上网页本身也可以有缓存，因此整个页面和数据都在本地的话，可以立即显示。
> 3. 临时存储：很多时候数据只需要在用户浏览一组页面期间使用，关闭窗口后数据就可以丢弃了，这种情况使用sessionStorage非常方便。


### 请解释 `<script>`、`<script async>` 和 `<script defer>` 的区别。 ###

> asynchronous 异步  
> deferred 延迟
> 
> “异步加载,可以理解为无阻塞并发处理。”  
> “对每个网站来说，阻塞都是一个巨大的性能瓶颈，而可以直接指定script文件异步加载无疑会加快web页面的速度。”

![script, async, defer](http://www.oseye.net/upload/attached/image/20120729/20120729212822_70253.jpg)

* `<script>`在浏览器继续解析页面之前，立即读取（加载）并执行脚本。
* `<script async>`立即下载脚本。脚本在 script 文件**下载完成后会立即执行**,并且其执行时间一定在 window 的 load 事件触发之前（但可能会在DOMContentLoaded事件触发之前或之后）。这意味着多个 async 脚本很可能不会按其在页面中的出现次序顺序执行（**乱序执行**）。对于那些可以不依赖任何脚本或不被任何脚本依赖的脚本来说非常合适。
* `<script defer>`浏览器确保多个 defer 脚本按其在HTML页面中的出现顺序**依次执行**,且执行时机为DOM解析完成后，document的DOMContentLoaded 事件触发之前。*但在现实当中，延迟脚本并不一定会按照顺序执行，也不一定会在DOMContentLoaded事件触发前执行，因此**最好只包含一个延迟脚本。** *脚本将**在页面完成解析时执行**。

defer 和 async 在网络读取（下载）这块儿是一样的，都是异步的（相较于 HTML 解析）。

**相同点**

* 加载文件时不阻塞页面渲染
* 对于inline的script无效——仅适用于外部脚本（只有在使用 src 属性时）
* 使用这两个属性的脚本中不能调用document.write方法
* 有脚本的onload的事件回调

**不同点**

* html的版本html4.0中定义了defer；html5.0中定义了async；这将造成由于浏览器版本的不同而对其支持的程度不同；
* 执行时刻 & 执行顺序

**代码示例**

`<script type="text/javascript" src="demo_async.js" async="async"></script>`

```html5
<!-- 指定async,以及 onload 回调 -->  <!-- 上面这种写法符合XHTML？？ -->
<script async src="siteScript.js" onload="myInit()"></script> 
```

除了基于Webkit的新版本浏览器,FireFox已经支持defer和onload属性很长时间了，而且从FF3.6开始添加了async属性。IE同样支持defer属性,但还不支持async属性，从IE9开始，onload属性也将被支持。  

> 参考  
> [HTML5 `<script>`元素async,defer异步加载](http://blog.csdn.net/renfufei/article/details/10210949)：这篇是对10年（大概是刚出async这个属性时候的？）一篇外文的翻译。  
> [HTML5 defer和async的区别](http://www.2cto.com/kf/201412/364116.html)：这篇最后的总结不错。  
> [引用JavaScript文件时的两个属性defer和async](http://www.oseye.net/user/kevin/blog/53)：图不错，“defer 和 async 的比较”不错。  
> [script的defer和async](http://www.cnblogs.com/henryhappier/archive/2013/02/22/2921478.html)：这篇有实际的测试。  


### 为什么通常推荐将 CSS `<link>` 放置在 `<head></head>`之间，而将 JS `<script>` 放置在 `</body>` 之前？你知道有哪些例外吗？ ###

与Javascript无阻塞加载具体方式有关。  
`<link>`放在head中，用以保证在js加载前，能加载出正常显示的页面。（保证在浏览器解析结构时，对页面进行渲染，以避免无样式闪烁（FOUC）。）  
`<script>`标签放在`</body>`前，将脚本放在底部，以保证js在页面基本解析完成后才加载和执行。

例外：有defer属性的脚本？。。


### 什么是渐进式渲染 (progressive rendering)？ ###

![progressive rendering](http://jbcdn2.b0.upaiyun.com/2014/05/1a973d0cf8a5870e3cc25678c0ddb227.png)

> 额外链接  
> [CSS提高渲染性能具体的实现方法*6](http://developer.51cto.com/art/201503/468647.htm)：比较简洁明了。  
> [CSS渲染速度改善的十个方法与建议](http://www.jb51.net/css/16465.html)：比上面更全，更详细。  
> [CSS渲染更高效的技巧](http://www.51edu.com/it/bckf/269585.html)：排版不太好。但是表述比较有个性。  
> 
> 附带找到的  
> [img标签下蜜汁空白BUG解决方法](http://www.51edu.com/it/bckf/269580.html)


### 你用过哪些不同的 HTML 模板语言？ ###

~~这题不太懂。。原谅我是个前端萌新，没用过。。~~


