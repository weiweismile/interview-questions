#### 行内元素、块级元素以及inline-block的区别？
#### js同源策略
     同源策略(Same-Origin Policy)。所谓的 同源 是指域名、协议、端口号 相同。不同的客户端脚本（JavaScript，ActionScript）在没有授权的情况下，不能读取对方资源。简单来说，浏览器允许包含在页面A的脚本访问第二个页面B的数据资源，这一切是建立在A和B页面是同源的基础上。
     
     同源策略
    同源策略 是由Netscape提出的一个著名的安全策略，现在所有支持JavaScript 的浏览器都会使用这个策略。实际上，这种策略只是一个规范，并不是强制要求，各大厂商的浏览器只是针对同源策略的一种实现。它是浏览器最核心也最基本的安全功能，如果缺少了同源策略，则浏览器的正常功能可能都会受到影响。
    
    跨域与跨域请求
    跨域 简单的来说，指的是两个资源非同源。出于安全方面的考虑，页面中的JavaScript在请求非同源的资源时就会出 跨域问题 ——即跨域请求，这时，由于同源策略，我们的请求会被浏览器禁止。也就出现了 我们常说的 跨域 问题。
#### 垂直水平居中
    http://www.cnblogs.com/haoyijing/p/5815394.html#css1
#### querySelector与document.getElementBy的区别

    1. W3C 标准querySelectorAll 属于 W3C 中的 Selectors API 规范 [1]。而 getElementsBy 系列则属于 W3C 的 DOM 规范 [2]。2. 浏览器兼容querySelectorAll 已被 IE 8+、FF 3.5+、Safari 3.1+、Chrome 和 Opera 10+ 良好支持 。getElementsBy 系列，以最迟添加到规范中的 getElementsByClassName 为例，IE 9+、FF 3 +、Safari 3.1+、Chrome 和 Opera 9+ 都已经支持该方法了。3. 接收参数querySelectorAll 方法接收的参数是一个 CSS 选择符。而 getElementsBy 系列接收的参数只能是单一的className、tagName 和 name。代码如下 [3]：var c1 = document.querySelectorAll('.b1 .c');
    var c2 = document.getElementsByClassName('c');
    var c3 = document.getElementsByClassName('b2')[0].getElementsByClassName('c');
需要注意的是，querySelectorAll 所接收的参数是必须严格符合 CSS 选择符规范的。所以下面这种写法，将会抛出异常。代码如下 [4]：try {
  var e1 = document.getElementsByClassName('1a2b3c');
  var e2 = document.querySelectorAll('.1a2b3c');
} catch (e) {
  console.error(e.message);
}
console.log(e1 && e1[0].className);
console.log(e2 && e2[0].className);
（CSS 选择器中的元素名，类和 ID 均不能以数字为开头。）4. 返回值大部分人都知道，querySelectorAll 返回的是一个 Static Node List，而 getElementsBy 系列的返回的是一个 Live Node List。看看下面这个经典的例子 [5]：// Demo 1
var ul = document.querySelectorAll('ul')[0],
    lis = ul.querySelectorAll("li");
for(var i = 0; i < lis.length ; i++){
    ul.appendChild(document.createElement("li"));
}

// Demo 2
var ul = document.getElementsByTagName('ul')[0], 
    lis = ul.getElementsByTagName("li"); 
for(var i = 0; i < lis.length ; i++){
    ul.appendChild(document.createElement("li")); 
}
因为 Demo 2 中的 lis 是一个动态的 Node List， 每一次调用 lis 都会重新对文档进行查询，导致无限循环的问题。而 Demo 1 中的 lis 是一个静态的 Node List，是一个 li 集合的快照，对文档的任何操作都不会对其产生影响。但为什么要这样设计呢？其实，在 W3C 规范中对 querySelectorAll 方法有明确规定 [6]：The NodeList object returned by the querySelectorAll() method must be static ([DOM], section 8). 那什么是 NodeList 呢？W3C 中是这样说明的 [7]：The NodeList interface provides the abstraction of an ordered collection of nodes, without defining or constraining how this collection is implemented. NodeList objects in the DOM are live.所以，NodeList 本质上是一个动态的 Node 集合，只是规范中对 querySelectorAll 有明确要求，规定其必须返回一个静态的 NodeList 对象。我们再看看在 Chrome 上面是个什么样的情况：document.querySelectorAll('a').toString();    // return "[object NodeList]"
document.getElementsByTagName('a').toString();    // return "[object HTMLCollection]"
这里又多了一个 HTMLCollection 对象出来，那 HTMLCollection 又是什么？HTMLCollection 在 W3C 的定义如下 [8]：An HTMLCollection is a list of nodes. An individual node may be accessed by either ordinal index or the node's name or id attributes.Note: Collections in the HTML DOM are assumed to be live meaning that they are automatically updated when the underlying document is changed.实际上，HTMLCollection 和 NodeList 十分相似，都是一个动态的元素集合，每次访问都需要重新对文档进行查询。两者的本质上差别在于，HTMLCollection 是属于 Document Object Model HTML 规范，而 NodeList 属于 Document Object Model Core 规范。这样说有点难理解，看看下面的例子会比较好理解 [9]：var ul = document.getElementsByTagName('ul')[0],
    lis1 = ul.childNodes,
    lis2 = ul.children;
console.log(lis1.toString(), lis1.length);    // "[object NodeList]" 11
console.log(lis2.toString(), lis2.length);    // "[object HTMLCollection]" 4
NodeList 对象会包含文档中的所有节点，如 Element、Text 和 Comment 等。HTMLCollection  对象只会包含文档中的 Element 节点。另外，HTMLCollection 对象比 NodeList 对象 多提供了一个 namedItem 方法。所以在现代浏览器中，querySelectorAll 的返回值是一个静态的 NodeList 对象，而 getElementsBy 系列的返回值实际上是一个 HTMLCollection 对象 。

####圣杯布局
http://www.cnblogs.com/tinyphp/p/4742922.html

#### HTTP协议
    http://network.chinabyte.com/240/13310240.shtml
