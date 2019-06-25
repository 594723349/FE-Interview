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

JS响应回车事件（函数形参ev为了处理IE传过来的事件，如果是其他浏览器，则不需要这个形参，即function method（）{var eVent=event;……};）

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
slice(start,end)	取数据内容start数组开始的小标，end数组结尾的下标，但是end不包括自己

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
VM3186:1 String {"12345"}0: "1"1: "2"2: "3"3: "4"4: "5"length: 5__proto__: String[[PrimitiveValue]]: "12345"

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

将一个字符串数组的元素的顺序进行反转。["a", "b", "c", "d"] -> [ "d","c","b","a"]。使用两种种方式实现。提示：第i个和第length-i-1个进行交换
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














```