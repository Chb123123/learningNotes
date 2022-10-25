# Web基础

### 块级元素，可以存放任何东西的小盒子

```html
<div>无语意</div> 
```



<html>       <!--用来告诉浏览器这是一个html文件-->

```html
<head>       <!..头部标记，存放文档基本信息，不可见元素-->
<meta charset=''utf-8/''>       <!--声明字符编码，防止乱码-->
<title>wyword</title>      <!--标题标签，指定网页的标题-->
<style tyle=''css/text''>
body{background-color}
h1{color:#fff;
text-align:center;
font-size:16px;
color:red;
}
</style>
</head>
```

<body>
<!--主体内容，放置文档可见内容-->

<em>标签设计斜体文字</em>
<br/>强制换行
<strong>将文字加粗</strong>
&nbsp;   表示一个空格
<ins>表示添加下滑线</ins>
<del>添加删除线</del>

```html
<p>块级元素，p标签单独占一行，不与其他标签并行显示
其他行类元素可以并行显示
块级元素装行类，行类不能装块级元素
横线屏占比width="55%"
横线粗细 size="4"
align="center" 内容居中  right 内容居右    left 图片据左
图片宽度和高度修改代码   width="图片宽度"   height="图片高度"
图片相邻左右的距离修改代码  hspace="图片左右距离"
图片上下距离修改代码 vspace="图片上下距离"
图片居中效果<p align="center"><img src="图片名称"/</p>
图片添加边框 border="边框粗细"
src里面的路径有两种方法：
```

### 查找图片由网页文件开始搜索

1：相对路径

a同级：  .html文件与图片在同一个文件里面
格式  <img src="加入图片名"/>

b下级：   .html文件与存放图片的文件夹在同一个文件夹里
<img src="添加文件夹以及文件名称"

c上级：  <img src="../文件名称"  ../表示返回上一级

绝对路径  <img src="文件路径"
一般不会使用

超链接：用于网页跳转
a标签为超链接
语法：

```html
<a href="跳转的目的地址">显示内容</a>
```

图片超链接
语法：

```html
<a href="跳转地址"><img src="图片地址"></a>
```

邮箱超链接:

```html
<a href="mailto:邮箱地址">显示内容</a>
```

文件下载超链接：

```html
<a href="文件名称">显示内容</a>
```

文件后缀不能为图片后缀名

<target="_blank"> 超链接打开一个新的网页，不覆盖原有网页
<targer="_self"> 覆盖原有网页，显示新的页面。

空链接：<a href="#"> 表示一个空链接

描点链接：超链接的一种，是在同一张网页内进行跳转。

```html
语法：<a href="#目的地址的id号"></a>
例如：<a href="#dibu">底部</a>
```



          <h4 id="dibu">底部</h4>

空链接的作用：跳转到网页最顶部



### 表格

表格：table
行：tr
单元格 ：td
表头： 每一列的列名th 
表格的标题为：<caption></caption>
表格的边框为：border="边框粗细"
表格边框颜色：bordercolor="颜色"
当表格没有高度和宽度，就是由单元格的内容大小
当单元格有宽度和高度，但是没有对行或列设置特定的高度和宽度，行和列就会平分表格的宽度和高度
对齐方式： table  align="left\center\right"
行列对齐：valign="top" top上对齐  middle居中对齐 bottom下对齐   baseline 基线对齐

```html
边距：cellspacing="单元格之间的间距"
填充：cellpadding="内容到单元格边框的间距"
单元格背景颜色：bgcolor="颜色"
行合并：colspan="行数" 
列合并：rowspan="列数"
```




                                                        列表

作用：用来页面布局让页面看起更加整洁有序
分类：有序列表（使用最多），无序列表（使用较少），自定义列表
（1）无序列表：<ul></ul> 
                  列表项<li></li>
语法：

```html
<ul>
<li>列表内容</li>
<li>列表内容</li>
</ul>
```

（2）：有序列表 <ol></ol>
语法：<ol>
<li>列表内容</li>
<li>列表内容</li>
<li>列表内容</li>
</ol>

type="disc" disc 实心圆 circle 空心圆 square 实心方块 none 无序列表符号

（3）：自定义列表包含两个内容，用来对某个术语进行解释说明：<dl></dl>
解释的名词，<dt></dt>
描述名词的项：<dd></dd>
语法：

<dl>
<dt>要解释的术语</dt>
<dd>解释</dd>
<dd>解释</dd>
<dd>解释</dd>
</dl>
在头部标签添加可以让列表内容与边框没有边距

```css
<style type="text/css">
*{
padding:0;
margin:0;
}
</style>
```

### 列表嵌套

```html
<h3>列表嵌套</h3>
<h3>手机排行榜</h3>
<ul>
<li>华为</li>
<li>小米</li>
<li>苹果</li>
<li>三星</li>
</ul>
```





用于用户与后台进行交互的页面：<form></form>
表单控件：input控件（单标签），通常与type属性连用，指定控件的功能。
语法

</form>

```css
textarea  文本域 一般用来装发表看法的多段文本
防止拖拽文本域 ：resize : none
type="text"    是单行文本框
type="password"    密码框
type="submit"   提交按钮
onclick="alert('保存成功')"   点击提交按钮弹出的消息框
type="reset"    重置按钮
type="file"    上传文件 默认上传一个文件        multiple="multiple"   上传多个文件
<input type="image" src="img/13.png">图片标签
```

### 表单域   from

```html
<form action="服务器地址" method="get/post">
<input type=""value=""name=""/>
</form>
```

get:提交的数据会附在网址后面，不安全
post:会将数据打包给服务器，等候服务器的读取

```css
autocomplete="off" / 指定表单是否自动完成输入功能。
size="数字" 文本框可见字符长度
maxlength="数字"  密码最多可以输入的字符长度
required="required"  输入内容不能为空
type=""radio" 单选按钮
checked="checked"  默认选中状态
type="checkbox"   复选框
placeholder="请输入正确的邮箱地址"  提示信息不需要手动删除
autofocus="autofocus"    打开网页自动获取光标
```


label标签：将文本和控件绑定
语法：
<label for="控件id号">男</label>



### 正则表达式

匹配行首^结尾$ \d=[0-9]数字字符\w(英文字母，汉字以及下划线)

3位数字：^[0-9]{3}$=^\d{3}$

下拉菜单<select></select>
语法：<select>
<option>	</option>
	</select>
datalist 标签：定义选项列表，通常与input标签配合使用
语法：
<input type="text" placeholder="输入你喜欢的明星" list="mx">

<datalist id="mx">
<option>刘德华</option>
<option>章若楠</option>
<option>张天爱</option>
</datalist>
多行文本框：

```html
<textarea rows="行数" cols="列数">
提升文本
</textarea>
```

### padding :内边距

行内式：作用范围在本标签里面
内嵌式:   作用在全局范围里面


                                                                   层叠性

对同一个对象且同一个属性设置了多个属性，去最近那个样式（就近原则）对同一个对象的多个属性设置多个样式且不冲突可以叠加。
				


选择器：基础选择器和复合选择器
基础选择器：是由单个选择器组成
标签选择器，内选择器，id选择器，通配符选择器。

标签选择器：用html的标签作为选择器
语法：标签名{css样式}
这个样式对整个页面的这一类标签都起效果，缺点不能个性化设计样式。

类选择器:单独选择一个或几个元素来设置样式
语法：.类名{css样式}定义

<标签名 class="类名">***<标签名>类样式的调用
样式点定义：结构类{class}调用，一个或多个

id选择器：选择唯一的标签进行设置样式
语法：定义样式
	#id名{样式}
	调用样式
	<p id="id名">****</p>

通配符选择器：选择页面中所有的对象
语法：*{样式}

复合选择器：由多个基础选择器组成，是为了更精确的选择某个对象
语法： .父级.后代{样式}样式只对后代起作用
子选择器：选择父级中的最近一级
语法：父级>子级{样式}

并集选择器：对多个对象设置相同的样式
语法：标签1，标签2，标签3{样式}

伪类选择器：用于对某些选择器添加特殊的效果
链接伪类选择器：
a:link(选择所有没有被访问的链接)
a:visited(选择所有已经被访问的链接)
a：hover(选择经过的链接)
a:active(选择激活状态的链接)

常用选择器     a 和 a:hover
元素的显示模式
块元素：独占一行（div  h1-h6 p ul  li ol）
行内元素：并行显示（span strong a ）

块级元素的特点：独占一行 ，可以设置宽高
display block 将行内元素转换为块级元素



### 字体样式

```css
font-size:字体大小;
font-family(字体): "宋体"," 黑体"   有空格的英文需要添加引号
设置字体时：最好使用Unicode编码，可以有效的防止浏览器不同而导致的乱码
font-weight:(字体粗细);   norma(默认字体)   bold（粗体）bolder（更粗）
font-style(字体风格);     normall(默认风格)  italic(斜体)
添加样式可以并行显示，属性顺序不能随意调换，否则没有效果。
text-decoration:none
white-space{空白符处理}； normal{默认值}； nowrap{强制不换行} pre{保留格式显示}	

overflow:内容溢出显示方式   visible（不裁减，默认） hidden(裁剪溢出内容)         scroll(滚动显示)      auto（按照内容自动选择显示效果）
text-overflow(超出文本显示方式)  clip(不显示省略号)   ellipsis（超出部分显示省略号）
```

### 文字滚动效果

```html
<marquee  align="left" behavior="scroll" bgcolor="#FF0000" direction="up" height="300" width="200" hspace="50" vspace="20" loop="1" scrollamount="100" scrolldelay="100" onMouseOut="this.start()" onMouseOver="this.stop()">hello worid!</marquee>
```

```css
text-indent(首行缩进)  12px/2em/150%
text-decoration(文本修饰)：
none(默认没有修饰线)
underline(将文本添加下划线)
line-through:将文本添加删除线
line-height  (行高)=height时内容会垂直居中
```

```css
background-color：(背景颜色)/rgb(200,130,255);
background-color:transparent(默认透明)
background-image: url(img/14.jpg); 设置背景图片
background-size: cover;设置背景大小 cover 全部覆盖
背景不透明模式：rgba()
background-color:bgba(r,g,b,a(0-1)) a为透明度效果
opacity:对任何对象都可以设置透明效果
opacity：0-1
background-repeat:no-repeat/tepeat-x/tepeat-y
背景图像位置：
background-positlon:left/center/right   top/center/bottom; 上/中/下
背景图像固定：
background-attachment: scroll;     scroll/ffxed
background-color image repeat attachment position 可以不按顺序
盒子模型
1，组成内容区，内边距，内边框， 边框，外边距
2，边框：粗细，样式，颜色
border：2px/solid(实现) double(双实线) dashed(虚线) dotted(点实线)/red
3，内边距：padding.是内容到边距的距离
padding:20px  上下左右内边距都是20px
padding:10px 20px  上下为10px  左右为20px
padding:5px 10px 15px 20px 上5px 右10px 下15px 左20px 
4，外边距（margin）:元素与元素之间
margin:10px  外边距都为10px
外边距合并时，取较大的值而不是两外边距相加
当盒子嵌套另一个盒子时，同时设置外边距会出现外边距塌陷，可以对父元素加边框
margin：0px auto；对盒子设置水平居中 只对块级元素有效
```



### 盒子的浮动效果

浮动：（float）
语法：选择器{float:left/center/right/none}
浮动会影响后面的标准流，所以要取消浮动
语法：
选择器{cleat:left/right/both(常用):}
方法一：为浮动的元素添加一个兄弟为空元素，设这个空元素的样式为cleat:left/right/both;
方法二：对浮动元素的父盒子加overflow:hidden;样式
圆角边框（border-redius）
语法：选择器{border-radius:1-4logth(水平半径)|%/1-4logth|%(垂直半径)}
正圆：先有一个正方形，再设置圆角border-radius：边长的一半
长方形左右半圆：现有一个长方形：再设置左右半圆的一半

### 元素的定位

定位得组成：定位模式和边偏移
定位模式：静态（static）/相对定位（relative）/绝对定位（absolute）/固定（fixed）; 

**子绝父相**

```css
"选择器"{
	position:absolute;
    top:20px;
    right:30px;
}
```

### 固定定位（fixed）

以浏览器窗口为参照点，更父元素没有关系，不随滚动条滚动。

                                                                           精灵图
需要先设置盒子的宽和高，右边的坐标为负，下方的盒子为符
background-position  使用X轴和Y轴来实现定位

### 更改鼠标样式

鼠标样式： cursor：pointer/小手  text/文本  move/移动  not-allowed/禁止

### 定位的层级设置 z-index

 z-index：数字；数字越大，层次越高

```css
对齐方式
vertical-align :元素的对齐方式，只针对行内元素或行内块级元素有效，对块级元素无效
vertical-align：middle 表示垂直居中 /bottom 表示基线对齐 / top 表示顶部对齐
```

### 行内原生的对齐方式

用标签装着图片时，有时底部会有一些间距，这是因为行内块级元素默认与文字基线对齐，可以通过上面的方法解决

```css
1:给图片添加 vertical-align:middle /top/bottom 
2:把图片转换为块级元素 display :black
```

### 超出的内容以省略号的形式存在

```css
overflow: hidden;      超出的部分省略
white-space: nowrap;     强制不换行
text-overflow: ellipsis;    超出的部分以省略号的形式存在
```

?                                                     

弹性伸缩盒子模型显示
display:-webkit-box;
/*限制在一个块元素显示的文本的行数*/
-webkit-line-clamp: 2;                   2表示想在多少行显示省略号
/*设置或检索伸缩盒对象的子元素的排列方式*/
-webkit-box-orient: vertical;

                                                         盒子排列的优先级

如果盒子没有定位，则鼠标经过时添加相对定位即可，如果都有定位，则需要设置优先级 z-index

### 将盒子设为三角形

盒子制作三角形，不需要给盒子宽高：border：10px soild  trasparent;  把盒子设为透明
需要哪边显示三角形就给哪边设置 border-方向-颜色：颜色；

```css
盒子不需要给宽高，边框有多粗，三角形就有多高
	width:0;
	height:0;
	border-bottom: 50px solid pink;
	border-right: 50px solid blue;
	border-top: 50px solid red;
	border-left: 50px solid green;
直角三角形设置代码
	width:0;
	height:0;
	border-bottom: 0px solid pink;
	border-right: 50px solid blue;
	border-top: 100px solid transparent;
	border-left: 0px solid green;
也可以写成：
	width:0;
	height:0;
	border-color:transparent pink transparent transparent;
	border-style: solid;
	border-width: 100px 50px 0 0;
```

visibility:inherit 继承父类对象的可见性 /visible 对象可视 /hidden 对象隐藏

```html
<div style="background: #000;height:127px;width:209px;top:0px;left:0px;"></div>
```

```css
style="display: none;background:rgba(0,0,0,0.6);height:127px;width:209px;top:0px;left:0px;"><div style="height:44px;width:46px;background:url(img/index.png) -189px -62px;margin-top:45px;margin-left: 80px;"
```



### 背景渐变

背景渐变必须添加浏览器私有前缀

```css
background: -webkit-linear-gradient(方位top/bottom/left/right， 起始颜色，颜色1，颜色2，。。。);
```

### 将字符串更改为数组

split(" ") 括号里面是以什么作为分割符 ， 。 ‘’ 

```javascript

```

### 将字符串转换为大写  toUpperCase()

### 点击搜索框 不显示选中效果

input{outline:none}
