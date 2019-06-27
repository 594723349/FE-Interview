# Promise

当有多个请求之间有相互依赖关系（紧接着的请求需要上一次请求的返回结果），这时	promise的作用就凸显出来了。
	如果不用promise，常规做法只能callback层层嵌套，俗称callback hell，可读性	和维护性都很差的。
每次 then 调用都会以之前的 then 调用的返回值为参数。
如果一个 promise 已经执行完成，单then 被再次调用时，回调动作将会被再次执行。而如果这个 promise 里执行的是reject 回调函数，这是再调用 then 方法，回调函数将不会被执行。
Promise的用法，简单说就是一句话：使用then方法添加回调函数。
Promise是一个构造函数，自己身上有all、race、reject、resolve这几个眼熟的方法，原型上有then、catch等同样很眼熟的方法。这么说用Promise new出来的对象肯定就有then、catch方法喽，没错。
 promise的参数resolve，resolve可以替代return，用来返回参数或者错误
promise最主要作用是链式操作
在使用链式操作then时，promise会以从上往下顺序执行，其中一个方法报错，后面的不会会执行
Promise的all方法提供了并行执行异步操作的能力，并且在所有异步操作执行完后才执行回调。
all方法的效果实际上是「谁跑的慢，以谁为准执行回调，那么相对的就有另一个方法「谁跑的快，以谁为准执行回调」，这就是race方法，这个词本来就是赛跑的意思。  race的用法与all一样

什么是Promise
所谓 Promise，就是一个对象，用来传递异步操作的消息。它代表了某个未来才会知道结果的事件（通常是一个异步操作），

Promise的作用
Promise的出现主要是解决地狱回调的问题，比如你需要结果需要请求很多个接口，这些接口的参数需要另外那个的接口返回的数据作为依赖，这样就需要我们一层嵌套一层，但是有了Promise 我们就无需嵌套


Promise的本质
我认为Promise的本质就是分离了异步数据获取和业务逻辑


```javascript
ajax传统的写法：
getData(method, url, successFun, failFun){
  var xmlHttp = new XMLHttpRequest();
  xmlHttp.open(method, url);
  xmlHttp.send();
  xmlHttp.onload = function () {
    if (this.status == 200 ) {
      successFun(this.response);
    } else {
      failFun(this.statusText);}
  };
  xmlHttp.onerror = function () {
    failFun(this.statusText);};}
改为 Promise写法：
getData(method, url){
  return new Promise(function(resolve, reject){
    var xmlHttp = new XMLHttpRequest();
    xmlHttp.open(method, url);
    xmlHttp.send();
    xmlHttp.onload = function () {
      if (this.status == 200 ) {
        resolve(this.response);
      } else {
        reject(this.statusText);  }
    };
    xmlHttp.onerror = function () {
      reject(this.statusText);  };})}
 
getData('get','www.xxx.com').then(successFun, failFun)

```

不管是then或者catch返回的都是一个新的Promise实例！而每个Primise实例都有最原始的Pending（进行中）到Resolve（已完成），或者Pending（进行中）到Reject（已失败）的过程。

Promise相关
	then方法里面第一个回调函数表示成功状态，也就是resolve，第二个是失败状态-reject，如果默认写一个参数的话，默认resolve
---- then(fn).catch(fn)，相当于 then(fn).then(null, fn)；
----用Promise.all来执行，all接收一个数组参数，里面的值最终都算返回Promise对象。这样，三个异步操作的并行执行的，等到它们都执行完后才会进到then里面。那么，三个异步操作返回的数据哪里去了呢？都在then里面呢，all会把所有异步操作的结果放进一个数组中传给then
（有了all，你就可以并行执行多个异步操作，并且在一个回调中处理所有的返回数据，是不是很酷？有一个场景是很适合用这个的，一些游戏类的素材比较多的应用，打开网页时，预先加载需要用到的各种资源如图片、flash以及各种静态文件。所有的都加载完后，我们再进行页面的初始化。
）


resolve函数的参数是一个promise实例 ???

```javascript
立即resolve的Promise对象，是在本轮“事件循环”（event loop）的结束时，而不是在下一轮“事件循环”的开始时。 

执行顺序
立即resolve的Promise对象，是在本轮“事件循环”（event loop）的结束时，而不是在下一轮“事件循环”的开始时。
看一下老师这个例子，
setTimeout(function () {
  console.log('three');}, 0);
Promise.resolve().then(function () {
  console.log('two');});
console.log('one');
// one
// two
// three
// setTimeout(fn, 0)在下一轮“事件循环”开始时执行，
// Promise.resolve()在本轮“事件循环”结束时执行，
// console.log('one')则是立即执行，因此最先输出。

如果希望得到一个Promise对象，比较方便的方法就是直接调用Promise.resolve方法。
var p = Promise.resolve();
p.then(function () {
  // ...
});

var p = Promise.resolve();
p.then(function () {
  console.log(11111)});
console.log(22222)

// VM4153:4 22222
// VM4153:3 11111

Promise.resolve（）
将现有对象转为Promise对象:

Promise.resolve('foo')
// 等价于
new Promise(resolve => resolve('foo'))

```

Promise.all 和Promise.race
异同：
1.	同： 只要有一个实例状态是rejected，他的状态就是rejected
2.	异： Promise.all（）全部实例状态为resolved，它的状态才为resolved，Promise.race（）只要有一个实例状态为resolved，他的状态就是resolved
---- Promise的作用是解决回调金字塔的问题，对于控制异步流程实际上没有起到很大的作用。真正使用Promise对异步流程进行控制，我们还要借助ES6 generator函数。

