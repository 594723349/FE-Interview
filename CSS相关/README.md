# CSS 相关

- html上标<sup>与下标注<sub>标签元素
- <b>加粗内容</b>
- <strong>加粗内容</strong>
- 倾斜<em></em> ,<i></i>

> 插入图片
<img src="目标文件路径及全称" alt="图片替换文本" title="图片标题" />
注:所要插入的图片必须放在站点下
①	title的作用: 在你鼠标悬停在该图片上时显示一个小提示，鼠标离开就没有了，HTML的绝大多数标签都支持title属性，title属性就是专门做提示信息的
②	alt的作用:alt属性是在你的图片因为某种原因不能加载时在页面显示的提示信息，它会直接输出在原本加载图片的地方。

数据表格的作用及组成  
作用：显示数据 
表格组成
<table width="value" height="value" border="value" bgcolor="value" cellspacing="value" cellpadding="value">
<tr>
<td></td>
<td></td>  
</tr>
</table>
6）cellspacing="单元格与单元格之间的间距" 
7）cellpadding="单元格与内容之间的空隙"
9)合并单元格属性： 
colspan=“所要合并的单元格的列数"合并列;  rowspan=“所要合并单元格的行数”合并行; 
合并之后需要把多余的单元格删除

- 表单框<input type="reset" value="按钮内容" />
- 重置按钮<form name="表单名称" method="post/get" action=""></form> 

## 样式种类
1）、内部样式 
语法：
<style type="text/css">
/*css语句*/
</style>
注：使用style标记创建样式时，最好将该标记写在<head></head>;

2）、外部样式之link标签引入 
*方法一：外部样式表的创建：
<link rel="stylesheet" type="text/css" href="目标文件的路径及文件名全称" />
说明：
使用link元素导入外部样式表时，需将该元素写在文档头部，即<head>与</head>之间。
rel（relation）：用于定义文档关联，表示关联样式表；  type：定义文档类型； 
3）、外部样式之@import 
<style type="text/css">
	@import url(目标文件的路径及文件名全称);
</style>
注：@和import之间没有空格 url和小括号之间也没有空格；必须结尾以分号结束；
4）、内联样式 
	<div style=“width:200px; height:400px;”></div> 


## CSS选择符（选择器） 
1） 元素选择符/类型选择符（element选择器	)  语法：元素名称{属性：属性值；}
2） class选择符    语法：.class名称{属性：属性值；}
3） id选择符      语法：#id名称{属性：属性值；}
4） 通配符     语法：*{属性：属性值；}
5）群组选择器
语法：选择符1，选择符2，选择符3{属性：属性值;} 
6） 包含选择器     语法：选择符1（父元素）       选择符2（子元素）{属性：属性值;}
7） 伪类选择器(伪类选择符)
语法 ：
a:link{属性：属性值;}超链接的初始状态;
a:visited{属性：属性值;}超链接被访问后的状态;
a/div/p:hover{属性：属性值;}鼠标悬停，即鼠标划过超链接时的状态;
a:active{属性：属性值;}超链接被激活时的状态，即鼠标按下时超链接的状态;
要让他们遵守一个爱恨原则LoVe/HAte,也就是Link--visited--hover--active。;
7） 伪类选择器(伪类选择符)
说明：
A）当这4个超链接伪类选择符联合使用时，应注意他们的顺序，正常顺序为：
a:link,a:visited,a:hover,a:active,错误的顺序有时会使超链接的样式失效；
B）为了简化代码，可以把伪类选择符中相同的声明提出来放在a选择符中；
例如：a{color:red;} a:hover{color:green;} 表示超链接的三种状态都相同，只有鼠标划过变颜色。 

css中用四位数字表示权重，权重的表达方式如：0，0，0，0
①	类型选择符的权重为1
②	class选择符的权重为10
③	id选择符的权重为100
④	属性选择符的权重为10
⑤	伪类选择符的权重为10 
⑥	伪元素选择符的权重为1 
⑦	包含选择符的权重：为包含选择符的权中之和            
⑧	内联样式的权重为1000

* 当不同选择符的样式设置有冲突的时候，高权重选择 符的样式会覆盖低权重选择符的样式。
例如：b .demo的权重是1+10=11
.demo的权重是10
所以经常会发生.demo的样式失效
* 相同权重的选择符，样式遵循就近原则：哪个选择符最后定义，就采用哪个选择符样式。 
（注意：是css样式中定义该选择符的先后，而不是html中使用先后）

- 确定16px/ppi为标准字体大小默认值,即1em.默认情况下，1em=16px,0.75em=12px;
- 文本字体：{font-family:字体1，字体2，字体3；}
浏览器首先会寻找字体1、如存在就使用改字体来显示内容，如在字体1不存在的情况下，则会寻找字体2，如字体2也不存在，按字体3显示内容，如果字体3 也不存在；则按系统默认字体显示； 
A、当字体是中文字体时，需加双引号；
B、当英文字体中有空格时，需加双引号如（“Times New Roman”）
C、当英文字体只有一个单词组成是不加双引号；如：（Arial）；
Windows中文版本操作系统下，中文默认字体为宋体或者新宋体，英文字体默认为Arial.

- 文字加粗：{font-weight:bolder(更粗的)/bold（加粗）/normal（常规）/100—900;}
在css规范中，把字体的粗细分为9个等级，分别为100——900
100-400 一般    500常规字体     600-900加粗字体 

- 文字倾斜 ：{font-style：italic/oblique(两者无区别)/normal（取消倾斜，常规显示）;}
italic和oblique都是向右倾斜的文字, 但区别在于Italic是指斜体字，而Oblique是倾斜的文字，对于没有斜体的字体应该使用Oblique属性值来实现倾斜的文字效果.
-水平对齐方式：{text-align:left/right/center/justify;} 
text-align:justify（两端对齐对/纯数字/纯字母不起作用）;
中文可以

- 文字行高 {line-height:normal/value;}
normal：默认值 
number：设置数字，此数字会与当前的字体尺寸相乘来设置行间距。1  2  3 
length：设置固定的行间距px。        %：基于当前字体尺寸的百分比行间距。

- font属性的简写：
说明:font的属性值应按以下次序书写(各个属性之间用空格隔开)
顺序: font-style font-weight font-size / line-height font-family
(1)简写时 , font-size和line-height只能通过斜杠/组成一个值，不能分开写。
(2) 顺序不能改变 ,这种简写法只有在同时指定font-size和font-family属性时才起作用,而且,你没有设定font-weight , font-style , 他们会使用缺省值（默认值）。



