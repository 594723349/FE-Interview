# 第二部分

```javascript
typeof NaN
"number"

 javaScript中一些常见的兼容性问题整理
1） 滚动条：
document.documentElement.scrollTop||document.body.scrollTop
2) 获取样式兼容
function getStyle(dom, styleName){
return dom.currentStyle?
dom.currentStyle[styleName]
getComputedStyle(dom)[styleName];
}
3) 网页可视区域兼容
window.innerHeight || document.documentElement.clientHeight
window.innerWidth || document.documentElement.clientWidth
4） 事件对象兼容
evt = evt || window.event;
5） 阻止事件冒泡兼容
event.stopPropagation?
     event.stopPropagation():event.cancelBubble=true;
6）阻止默认行为兼容
evt.preventDefault?evt.preventDefault():evt.returnValue=false;
7）事件监听兼容
if(document.all){
    dom.attactEvent(“onclick”, fn);
} else {
    dom.addEventListener(“click”, fn);}
8）事件目标对象兼容
var t = event.target || event.srcElement;


```
 	ajax的概念和优势
	AJAX即“Asynchronous Javascript And XML”（异步JavaScript和XML），是指一种创建交互式网页应用的网页开发技术。
	通过在后端与服务器进行少量数据交换，AJAX 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。传统的网页（不使用 AJAX）如果需要更新内容，必须重载整个网页面。
	可以把一部分以前由服务器负担的工作转移到客户端，利用客户端的闲置的资源进行处理，减轻服务器和带宽的负担，节约空间和成本.
	无刷新更新页面，不需要等待，只需发送请求并得到服务器的响应，在不需要重新载入页面的情况下，就可以通过DOM及时将更新的内容显示在网页上。
	可以调用xml、json等外部数据。
	没有平台限制。Ajax把服务器的角色由原本传输内容转变为传输数据，而数据格式则可以使纯文本格式和xml、json格式，这几种格式没有平台限制。

```javascript
 	编写步骤
	创建请求对象
var request = new XMLHttpRequest();
var request = new ActiveXObject("Microsoft.XMLHTTP")
	ajax的两个方法和设置请求参数
request.open("get", "http://10.0.152.17/AJAX/ajaxtest", true);
request.send( )
当该boolean值为true时，服务器请求是异步进行的，
也就是脚本执行send（）方法后不等待 
服务器的执行结果，而是继续执行脚本代码； 
当该boolean值为false时，服务器请求是同步进行的，
也就是脚本执行send（）方法后等待 
服务器的执行结果的返回，若在等待过程中超时，则不再等待，
继续执行后面的脚本代码！
readyState:就绪状态--0(初始化) 1(请求建立) 2(发送完成) 3(解析) 4(完成)
0：请求初始化（还没有调用 open()）。
1：请求已经建立，但是还没有发送（还没有调用 send()）。
2：请求已发送，正在处理中（通常现在可以从响应中获取内容头）。
3：请求在处理中；通常响应中已有部分数据可用，但是服务器还没有完成响应的生成。
4：响应已完成；您可以获取并使用服务器的响应了。

	设置回调函数
request.onreadystatechange = function(){
	if(request.readyState == 4) {
		alert(request.responseText);
	}
}

onreadystatechange当状态值(readyState)发生改变的事件
ajax.readyState==4 代表ajax的工作状态：代表发送完成，但不一定发送成功
共5个值
ajax.status==200 服务器状态(http状态码);	200 代表发送成功
操作内容：
responseText: ajax请求返回的内容就被存放到这个属性下面,返回获取的内容,string	
responseXML返回xml文件

•	返回JSON格式数据
json_encode()  对变量进行JSON编码 （数组转换为json格式数据）
json_decode()  对JSON格式的字符串进行解码   

```

 	JS解析JSON
eval()和json.parse()的区别
我们将一个字符串解析成json对象时可以使用两种方法：
假设我们有一个json格式的字符串：
 
'{
    "student" : [
        {"name":"鸣人","age":17}, 
        {"name":"小樱","age":17},
        {"name":"佐助","age":17}
    ]
}'
 
然后我们需要把它解析成json对象
1、eval（）代码如下：
var data = '{"student" : [{"name":"鸣人","age":17}, {"name":"小樱","age":17},{"name":"佐助","age":17}]}';
eval('(' + data + ')');
2、JSON.parse()代码如下：
var data = '{"student" : [{"name":"鸣人","age":17}, {"name":"小樱","age":17},{"name":"佐助","age":17}]}';
JSON.parse(data);
区别：eval方法不会去检查给的字符串时候符合json的格式~同时如果给的字符串中存在js代码eval也会一并执行~比如如果上面的json格式的字符串改为：(注意红色部分)
var data = '{"student" : [{"name":"鸣人","age":17}, {"name":"小樱","age":alert("hehe")},{"name":"佐助","age":17}]}';
此时执行eval方法后会先弹出一个提示框输出hehe的字符串~
但是使用JSON.parse()就会报错~显示错误信息为当前字符串不符合json格式~即JSON.parse()方法会检查需要转换的字符串是否符合json格式~
相比较而言eval方法是很危险的~特别是当涉及到第三方时我们需要确保传给eval的参数是我们可以控制的~不然里面插入比如window.location~指向一个恶意的连接~那叫叫天啦
从这个层面讲~还是推荐使用JSON.parse来实现json格式字符串的解析

JSONP有什么用？
由于同源策略的限制，XmlHttpRequest只允许请求当前源（域名、协议、端口）的	资源，为了实现跨域请求，可以通过script标签实现跨域请求，然后在服务端输出JSON数据并执行回调函数，从而解决了跨域的数据请求。


3、如何使用JSONP？
首先在客户端注册一个callback, 然后把callback的名字传给服务器。此时，服务器	先生成 json 数据。然后以 javascript 语法的方式，生成一个function , 	function 名字就是传递上来的参数.
jsonp.最后将 json 数据直接以入参的方式，放置到 function 中，这样就生成了一段 	js 语法的文档，返回给客户端。
客户端浏览器，解析script标签，并执行返回的 javascript 文档，此时数据作为参数，	传入到了客户端预先定义好的 callback 函数里.（动态执行回调函数）


1.建立本地 web 服务器

新建文件夹 jsonp, 进入该文件夹内打开命令行工具

npm install koa koa-static
新建 index.js 文件

// index.js
const Koa = require('koa')
const app = new Koa()
app.use(require('koa-static')(__dirname + '/public'))
app.listen(3000)
2.新建 public 文件夹后进入文件夹，创建 index.html, somejsonp.js文件

// index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <script src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
  <script>
    var localHandler = function(data){
      alert('我是本地函数，可以被跨域的remote.js文件调用，远程js带来的数据是：' + data.result);
    };
  </script>
  <script type="text/javascript" src="./somejsonp.js"></script>
</body>
</html>
// somejsonp.js
localHandler({"result":"我是远程js带来的数据"});
3.然后回到 jsonp 文件夹，输入命令node index.js后，用浏览器打开http://localhost:3000即可看到浏览器窗口弹出js文件中的result，也就是我们获取到了js的数据。这便是jsonp的基本原理

返回一个文档中所有的class为"note"或者 "alert"的div元素.
var matches = document.querySelectorAll("div.note, div.alert");
----获取文档中 id="demo" 的元素：
	document.querySelector("#demo");
	获取文档中第一个 <p> 元素：
	document.querySelector("p");
	获取文档中 class="example" 的第一个 <p> 元素:
	document.querySelector("p.example");
	获取文档中有 "target" 属性的第一个 <a> 元素：
	document.querySelector("a[target]");

当有多个请求之间有相互依赖关系（紧接着的请求需要上一次请求的返回结果），这时	promise的作用就凸显出来了。
	如果不用promise，常规做法只能callback层层嵌套，俗称callback hell，可读性	和维护性都很差的。

----作用域
子函数会一级一级地向上寻找所有父函数的变量。所以，父函数的所有变量，对子函数都是可见的，反之则不成立。


### document.ready和onload的区别——JavaScript文档加载完成事件
页面加载完成有两种事件
一是ready，表示文档结构已经加载完成（不包含图片等非文字媒体文件）
二是onload，指示页面包含图片等文件在内的所有元素都加载完成。

用jQ的人很多人都是这么开始写脚本的：
$(function(){
// do something
});
其实这个就是jq ready()的简写，他等价于：
$(document).ready(function(){
//do something
})
//或者下面这个方法，jQuery的默认参数是：“document”；
$().ready(function(){
//do something
})
这个就是jq ready()的方法就是Dom Ready，他的作用或者意义就是:在DOM加载完成后就可以可以对DOM进行操作。
一般情况先一个页面响应加载的顺序是：域名解析-加载html-加载js和css-加载图片等其他信息。
那么Dom Ready应该在“加载js和css”和“加载图片等其他信息”之间，就可以操作Dom了。


1.window.onload方法

⑴执行时机:
在网页中所有元素(包括元素的所有关联文件)完全加载到浏览器后才执行，即JavaScript 此时可以访问网页中的所有元素。
window.onload=function(){ $(window).load(function(){
//编写代码 等价于 //编写代码
} });

⑵多次使用:
JavaScript的onload事件一次只能保存对一个函数的引用，他会自动用最后面的函数覆盖前面的函数。
function one(){
alert("one");
}
function two(){
alert("two");
}
window.onload=one;
window.onload=two;
//运行代码后只有 two
2.$(document).ready()方法

⑴执行时机:在DOM完全就绪时就可以被调用。(这并不意味着这些元素关联的文件都已经下载完毕)
举个例子:$(document).ready()方法明知要DOM就绪就可以操作了，不需要等待所有图片下载完毕。

⑵多次使用:
function one(){
alert("one");
}
function two(){
alert("two");
}
$(document).ready(function(){
one();
});
$(document).ready(function(){
two();
});
//运行代码后
//先是：one
//先是：two


