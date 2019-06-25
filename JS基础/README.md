# JS基础

冒泡排序 和 快速排序

- JS的编译和执行

JS的解析过程分为两个阶段：预编译期(预处理)与执行期。即：
js在执行的时候，先有一次预先检测的能力，检测声明（变量），然后第二次在执行整个js程序
预编译期JS会对本代码块(script)中的所有声明的变量和函数进行处理（类似与C语言的编译），但需要注意的是此时处理函数的只是声明式函数，而且变量也只是进行了声明但未进行初始化以及赋值。执行期就是在编译后的基础上开始从上到下执行脚本，遇到错误时中断。

```javascript
- 强制转换为整型：
sum=parseInt(hour/day);  
- 取小数部分的方法：
temps=parseInt(temps*1000)/1000;

Number()
0
Number('123')
123
Number('a')
NaN
Number('')
0

typeof null
"object"
typeof undefined
"undefined"

事件
onclick/ondblclick/onmouseover/onmouseout/onmousedown/onmouseup/
onmousemove/onkeydown/onkeyup/onfocus/onblur
onmousemove  <> onmouseout   
oninput    
它绑定于对象时，并非该对象所有属性改变都能触发事件，
它只在对象value值发生改变时奏效。 IE9以上浏览器。

JS响应回车事件（函数形参ev为了处理IE传过来的事件，如果是其他浏览器，
则不需要这个形参，即function method（）{var eVent=event;……};）

作用域
任何程序设计语言都有作用域的概念，简单的说，作用域就是变量与函数的可访问范围，即作用域控制着变量与函数的可见性和生命周期。

局部作用域和全局作用域（全局变量和局部变量）
在JavaScript中，变量的作用域有全局作用域和局部作用域两种。
全局作用域（变量）：整个程序都有效，即整个代码中都可以调用。
局部作用域（变量）：只对函数内部有效，即只能在本变量声明的函数内部调用。
在函数体内，局部变量的优先级高于同名的全局变量。

对象.onclick=function(){}
window.onload=function(){}

onchange 事件会在域的内容改变时发生。
	支持的HTML标签：textarea  input select
	支持该事件的JavaScript对象：fileUpload select text textarea

toUpperCase() 方法   把字符串转换为大写。
toLowerCase()
replace()  toUpperCase()  toLowerCase() 并不会改变原来的字符串。


html,body{      //禁止文字复制
				user-select:none;
				-ms-user-select: none;
				-moz-user-select: none;
				-webkit-user-select: none;
				}

Math 对象方法
方法	描述
abs(x)	返回数的绝对值。
acos(x)	返回数的反余弦值。
asin(x)	返回数的反正弦值。
atan(x)	以介于 -PI/2 与 PI/2 弧度之间的数值来返回 x 的反正切值。
atan2(y,x)	返回从 x 轴到点 (x,y) 的角度（介于 -PI/2 与 PI/2 弧度之间）。
ceil(x)	对数进行上舍入。
cos(x)	返回数的余弦。
exp(x)	返回 e 的指数。
floor(x)	对数进行下舍入。
log(x)	返回数的自然对数（底为e）。
max(x,y)	返回 x 和 y 中的最高值。
min(x,y)	返回 x 和 y 中的最低值。
pow(x,y)	返回 x 的 y 次幂。
random()	返回 0 ~ 1 之间的随机数。
round(x)	把数四舍五入为最接近的整数。
sin(x)	返回数的正弦。
sqrt(x)	返回数的平方根。
tan(x)	返回角的正切。
toSource()	返回该对象的源代码。
valueOf()	返回 Math 对象的原始值

数组的创建方式
	var arr=[];
	var arr=[1,2,3]
var arr=new Array();
var arr=new Array(1,2,3);
var  arr3=[[],[],[]]    //二维数组

数组的操作记忆
push	往数组中添加数据，并且是添加在最后一位数据
pop		从数组当中删除数据，并且是最后一位数据  
shift		在数组的第一位，删除数据
unshift	在数组的第一位，添加数据
splice(a,b)	删除数组中的某个第一个参数是数组的下标      第二个参数是删掉几个
slice(start,end)	取数据内容start数组开始的小标，end数组结尾的下标，
但是end不包括自己

a=[1,2,3,4,5,6]
// (6) [1, 2, 3, 4, 5, 6]
a.filter(value=>value%2)
// (3) [1, 3, 5]
a.filter(value=>value%2).map(value=>value*2)
// (3) [2, 6, 10]
a.filter(value=>value%2).map(value=>value*2).reduce((a,b)=>a+b)
// 18

// 注意输出的是一个对象
var str=new String('12345');
console.log(str)
VM3186:1 String {"12345"}0: "1"1: "2"2: "3"3: "4"4: "5"
length: 5__proto__: String[[PrimitiveValue]]: "12345"

对于一个字符串数组来说，如果字符串为数值，则parseInt（整个数组） 就等于parseInt（数组[0]）。

工资的数组[1500, 1200, 2000, 2100, 1800],把工资超过2000的删除
	var arr = [1500, 1200, 2000, 2100, 1800];
//利用filter()形成一个数组;return true;组成的数组;
var newArr = arr.filter(function (ele, i, array) {
  //2000以上返回false;
  if(ele<2000){
    return true;
  }else{
    return false;
  }
});
console.log(newArr); // [1500, 1200, 1800]

将一个字符串数组的元素的顺序进行反转。
["a", "b", "c", "d"] -> [ "d","c","b","a"]。使用两种种方式实现。
提示：第i个和第length-i-1个进行交换
// 数组.reverse() 方法
var arr = ["a", "b", "c", "d"];
console.log(arr.reverse()); // ["d", "c", "b", "a"]

// 三种：1.正向遍历，反向添加; 2.反向遍历，正向添加;  3.元数组元素交换位置;
for(var i=0;i<arr.length/2;i++){
var temp = arr[i];
arr[i] = arr[arr.length-1-i];
arr[arr.length-1-i] = temp;
}
console.log(arr);


数组清空：1. arr.length = 0; // (不好，伪数组无法清空)2. arr.splice(0); // 伪数组没有这个方法;3. arr = [];   // 可以操作伪数组; (推荐!)

// 伪数组: 就是长的像数组，但是没有数组的方法;也不能添加和删除元素;
例： // arguments
    fn(111,222,333);
    function fn(){
      arguments.length = 0; // 无法清空 返回 [1, 2, 3]
      arguments.splice(0); // 会报错 arguments.splice is not a function
      arguments = []; // 可以清空,返回空数组[] 
      console.log(arguments);
    }

sort( )
sort() // 数组中元素排序;(默认：从小到大)
// 默认：按照首个字符的Unicode编码排序;如果第一个相同那么就比较第二个...
例：
var arr = [4,5,1,3,2,7,6];
var aaa =arr.sort();
console.log(aaa);     // [1, 2, 3, 4, 5, 6, 7]
console.log(aaa === arr);// true 原数组被排序了(冒泡排序)
//默认还可以排列字母;
var arr2 = ["c","e","d","a","b"];
var bbb = arr2.sort();
console.log(bbb);     // ["a", "b", "c", "d", "e"]
console.log(bbb===arr2); // true 原数组被排序了(冒泡排序)

sort() //数值大小排序方法,需要借助回调函数;
例：
var arr = [4,5,1,13,2,7,6];
//回调函数里面返回值如果是：参数1-参数2;升幂；  参数2-参数1;降幂；
arr.sort(function (a,b) {
return a-b; //升序
//return b-a; //降序
//return b.value-a.value; //按照元素value属性的大小排序;
});
console.log(arr); // [1, 2, 4, 5, 6, 7, 13]

arr.sort();
    console.log(arr);//输出 [1, 2, 3, 4, 5, 59, 6] 注意：sort()默认是转换字符串再排序 所以按照数字大小排序不正确
    //正确方法 写比较函数
    arr.sort(function(a,b){return a-b}); //升序
    console.log(arr);//输出 [1, 2, 3, 4, 5, 6, 59]
    arr.sort(function(a,b){return b-a});//降序
console.log(arr);//输出[59, 6, 5, 4, 3, 2, 1]

数组.indexOf(元素);   // 给元素，查索引(从前往后)
数组.lastIndexOf(元素); // 给元素，查索引(从后往前)
例：
var arr = ["a","b","c","d","c","b","b"];
console.log(arr.indexOf("b"));    // 1 查到以后立刻返回
console.log(arr.lastIndexOf("b"));  // 6 找到以后立刻返回
console.log(arr.indexOf("xxx"));  // -1; 查不到就返回-1；

filter()数组遍历
//  对数组中每一项运行回调函数，该函数返回结果是true的项组成的新数组
//   新数组是有老数组中的元素组成的，return为ture的项;
例：
var arr = [111,222,333,444,555];
var newArr = arr.filter(function (element, index, array) {
//只要是奇数，就组成数组;(数组中辨别元素)
if(element%2 === 0){
return true;
}else{
return false;
}
})   // console.log(newArr); // [222, 444]

进制转换
var a=10
undefined
a.toString(16)
"a"

Math.round()：四舍五入取整数

10-20随机数
Math.floor(Math.random()*(10+1)+10)

BOM概念
BOM:BrowserObjectModel浏览器对象模型，描述与浏览器进行交互的方法和接口，ECMAscript是javascript的核心
BOM提供了很多对象，用于访问浏览器的功能，这些功能与任何网页内容无关。
由于浏览器提供商会按照各自的想法随意去扩展它，使得BOM缺乏一定的规范，于是浏览器之间共有的对象成为了事实上的标准。
window对象介绍
BOM的核心对象是window，它表示浏览器的一个实例。在浏览器中，window对象有双重角色，它既是通过JavaScript访问浏览器窗口的一个接口，又是ECMAScript规定的全局（global）对象。这意味着在网页中定义的任何一个对象、变量和函数，都以window作为其Global对象，因此有权访问parseInt()等方法。
与document的关系（扩展）
当浏览器下载到一个网页，通常是HTML，这个HTML就叫document（当然，这也是DOM树中的一个node），document通常是整个DOM树的根节点。这个document包含了标题（document.title）、URL（document.URL）、(document.body)等属性，可以直接在JS中	访问到。
DOM是为了操作文档出现的API，document是其的一个对象；
BOM是为了操作浏览器出现的API，window是其的一个对象。












```