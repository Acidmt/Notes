# 	HTML

[toc]

## 一 网页基本信息

```html
<!--DOCTYPE:告诉浏览器用的什么规范，默认HTML5-->
<html>
<!--head部分为头部-->
    <head>
        <meta http-equiv="content-type" content="textml charset=utf-8">
        <title>网页标题</title>
    </head>
<!--body代表网页主体部分-->
    <body>
    	文章内容
    </body>
</html>
```

>==标签也被称为节点==

### 1. meta标签

>1. meta:：描述性标签，用来描述网站的一些基本信息
>2. 标签位于文档的头部，不包含任何内容。<meta> 标签的属性定义了与文档相关联的名称/值对。

- 用法：

  ~~~html
  <!--上文代码meta部分在HTML5中可以简写为-->
  <meta charset="uft-8">
  ~~~

- 定义针对搜索引擎的关键词：

  ~~~html
  <!--定义keyword代表关键词，content代表属性值：定义界面涉及到的关键词。两者为键值对-->
  <meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript" >
  ~~~

- 定义页面的描述信息：

  ~~~html
  <!--description表示描述，conten代表的描述信息。两者为键值对-->
  <meta name="description" content=" html " />
  ~~~

-  定义页面每隔5秒刷新一次：

  ~~~html
  <meta http-equiv="refresh" content="5" />
  ~~~

### 2. 标题标签

> 1. h1 ~ h6 标签可定义标题。h1定义最大的标题。h6定义最小的标题。

- 用法：

  ```html
  <h1>标题 1</h1>
  <h1>标题 2</h1>
  <h2>标题 3</h2>
  <h4>标题 4</h4>
  <h5>标题 5</h5>
  <h6>标题 6</h6>
  ```

### 3.段落标签

> 1. < p > 标签定义段落开始，< /p >定义结束。
>
> 2. html中需要< p >标签来定义段落(==段落不同于换行==，段落的间距大于换行的间距。)

### 4.字体样式标签

- 用法：

  ~~~html
  <!--
  <strong>强调文本，将文本修饰为粗体。
  <em>强调文本，将文本修饰为斜体。
  <ins>强调文本，文本添加下划线。
  -->
  <strong>student</strong>
  <em>student</em>
  <ins>student</ins>
  ~~~

- 运行结果：

  <img src="https://z3.ax1x.com/2021/09/26/4694k4.png" alt="4694k4.png" style="zoom:50%;" />

  ​																				[图片无法显示点击此处](https://z3.ax1x.com/2021/09/26/4694k4.png)

### 5.转义字符

> 详情参考[HTML转义字符对照表 ](https://getkit.cn/resources/commons/HTML-escape-character.html)

### 6.图像标签：

>常见的图片格式：JPG，GIF，PNG

- 用法：

  ~~~html
  <!--
  src：图像地址(必填项)
  alt：图像加载失败时的替代文字(必填项)
  title：鼠标悬停提示文字
  width：图像宽度
  height：图像高度
  -->
  <img src="path" alt="text" title="text" width="x" height="y"/>
  ~~~

- 实例：

  ~~~html
  <!--用相对路径插入名为‘1.jpg’的图片
  尽量用resources文件夹存放资源
  ../ -------表示返回上一级目录
  -->
  <img src="../resources/image/1.jpg" alt=""/>
  ~~~

### 7.链接标签

> 将链接插入文本。可分为页面间超链接、锚链接和功能性链接

- 页面链接用法：

  ~~~html
  <a herf="path" target="目标窗口位置">点击放入的链接文本或图像跳转网页</a>
  ~~~

  > ==herf==：该项必填项，为链接地址
  >
  > ==target==：表示窗口在哪里打开。常用参数：① _blank(表示链接在新标签页打开) ② _self(在当前页面打开，默认为此参数)

- 锚链接用法：

  > 1. 需要一个锚标记。使用'name'做标记
  > 2. 点击会跳转都标记位置。'#'+name跳转。类似goto语句。

  ~~~html
  <a name="top">顶部</a>
  <a href="#top">点击回到顶部</a>
  ~~~

- 锚链接进阶：

  ~~~html
  <!--点击跳转跳转到链接的top标记点处-->
  <a herf="链接地址#top">跳转</a>
  ~~~

- 功能性链接：

  > 常用的为邮箱链接。

  ~~~html
  <a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=&site=qq&menu=yes">
      <img border="0" src="http://wpa.qq.com/pa?p=2::53" alt="点击这里给我发消息" title="点击这里给我发消息"/></a>
  ~~~

  运行结果：

  <img src="https://z3.ax1x.com/2021/09/26/46c2Yn.png" alt="46c2Yn.png" style="zoom:50%;" />

  ​																				[图片无法显示点击此处](https://z3.ax1x.com/2021/09/26/46c2Yn.png)

### 8.列表

> 列表分为:
>
> 1. 有序列表：数字顺序排列。
>
> 2. 无序列表：圆点顺序排列
> 3. 自定义列表。

- 有序列表用法：

  ~~~html
  <ol>
      <li>JAVA</li>
      <li>C++</li>
      <li>PYTHON</li>
      <li>LINUX</li>
  </ol>
  ~~~

- 无序列表用法：

  ~~~html
  <ul>
      <li>JAVA</li>
      <li>C++</li>
      <li>PYTHON</li>
      <li>LINUX</li>
  </ul>
  ~~~

- 自定义列表：

  ~~~html
  <dl>
      <dt>学科</dt>
    	<li>JAVA</li>
      <li>C++</li>
      <li>PYTHON</li>
      <li>LINUX</li>
      
      <dt>班级</dt>
    	<li>2001</li>
      <li>2002</li>
      <li>2003</li>
      <li>2004</li>
  </dl>
  ~~~

  运行结果：

  <img src="https://z3.ax1x.com/2021/09/26/46439J.png" alt="46439J.png" style="zoom:50%;" />

  ​																					[图片无法显示点击此处](https://z3.ax1x.com/2021/09/26/46439J.png)

### 9.表格标签

~~~ html
<!--table代表标签
tr 行
td 列
border 边框
colspan 跨几列
rowspan 跨几行
-->
<table border="1px">
    <tr>
        <td colspan="4">数学</td>
    </tr>
     <tr>
        <td rowspan="2">英语</td>
         <td>1h</td>
         <td>2h</td>
         <td>3h</td>
    </tr>
    <tr>
    	<td>4h</td>
        <td>5h</td>
        <td>6h</td>
    </tr>
</table>
~~~

运行结果：

<img src="https://z3.ax1x.com/2021/09/26/46q3OH.png" alt="46q3OH.png" style="zoom:80%;" />

​																			[图片无法显示请点击此处](https://z3.ax1x.com/2021/09/26/46q3OH.png)

### 10.媒体标签

> 视频标签：<video>
>
> 音频标签：<audio>

- 视频标签基本用法：

  ~~~html
  <!--
  src:资源路径
  contros：视频控制条
  autoplay：自动播放
  -->
  <video src"路径" contros autoplay></video>
  ~~~

- 音频标签基本用法：

  ~~~html
  <!--
  src:资源路径
  contros：音频控制条
  autoplay：自动播放
  -->
  <audio src"路径" contros autoplay></audio>
  ~~~

### 11.iframe内联框架

> 内联框架：内联框架主要用于在网页中显示另一个网页，相当于在网页中嵌套了一个网页。

- 用法：

  ~~~html
  <!--
  src:网页路径
  name：网页框架标记名
  frameborder：是否显示嵌套网页的边框 0：为不显示，1：为显示
  wideth：网页宽度
  height：网页高度
  -->
  <iframe src="path" name=" " frameborder="0" wideth="" height=""></iframe>
  ~~~

### 12.表单

> 用户输入信息的模块统称为表单
>
> 表单用于搜集不同类型的用户输入，用<form>标签设置属性。
>
> input:标签定义输入字段，用户可在其中输入数据。
>
> name：用户输入的信息都需要name的值来接受。 
>
> hidden：隐藏域
>
> readonly：只读
>
> disabled：禁用

- 实例：

  ~~~html
  <!--
  action:用户输入信息之后提交的位置，可以是网站也可以是一个请求处理地址。
  method:提交方式，有两个参数 post：不能在url中看到用户提交的信息，安全，可传输大文件。
  			   			 get：可以在url中看到用户提交的信息，不安全，高效。
  type="submit"：提交按钮
  type="reset"：重置按钮
  type="image"：图片按钮
  type="button"：普通按钮
  checked：默认选择
  -->
  <form action="path" method="post/get">
      <p>用户名<input type="text" name="username"></p>
      <p>密码<input type="password" name="pwd"></p>
      <p>性别：
          <input name="sex" type="radio" value="boy">男
      	<input name="sex" type="radio" value="girl">女
      </p>
      <p>
      	<input type="submit">
          <input type="reset">
      </p>
  </form>
  ~~~

  运行结果：

  <img src="https://z3.ax1x.com/2021/09/26/4cdIHI.png" alt="4cdIHI.png" style="zoom:67%;" />

​																				[图片无法显示点击此处](https://z3.ax1x.com/2021/09/26/4cdIHI.png)

- 表单元素格式：

  |   属性    |                             说明                             |
  | :-------: | :----------------------------------------------------------: |
  |   type    | 指定元素的类型：text,password,checkbox(复选框),radio(单选框),submit,reset(重置),file,hidden,image,button,默认为text |
  |   name    |                      指定表单元素的名称                      |
  |   value   |          元素的初始值，type为radio时必须指定一个值           |
  |   size    | 指定表单元素的初始宽度。当type为text 或password时，文本框的长度大小，表单元素的大小以字符为单位。对于其他类型，宽度以像素为单位 |
  | maxlength |         type为text或 password时，能输入的最大字符数          |
  |  checked  |        type为radio或checkbox时，指定按钮是否是被选中         |
  |   link    |                         HTML引入标签                         |

### 13.下拉框和文本域

- 下拉框实例：

  ~~~HTML
  <!--
  select:下拉框	
  -->
  <p>国家：
  <select name="列表名称">
      <option value="值1">值1</option>
      <option value="值2">值2</option>
      <option value="值3">值3</option>
  </select>
  </p>
  ~~~

- 文本域实例：

  ~~~html
  <!--
  textarea:文本域
  cols:列
  rows：行
  -->
  <p>反馈：
      <textarea name=" " cols="50" rows="40"></textarea>
  </p>
  ~~~

- 文件域：

  ~~~html
  <!--
  input:标签定义输入字段，用户可在其中输入数据。
  files:文件
  -->
  <p>
      <input type="file" name="files"></inout>
  </p>
  ~~~

### 14.搜索框滑块和简单的验证

- 滑块：

  ~~~html
  <!--
  range:滑块属性
  step：步长，每次增加的数量
  -->
  <p>音量：
      <input type="range" name="voice" min="0" max="100" step="10">
  </p>
  ~~~

- 搜索框：

  ~~~html
  <!--search:搜索框-->
  <p>搜索
     <input type="search" name="serch"> 
  </p>
  ~~~

- 初级验证：

  > placeholder：提示信息
  >
  > required：非空判断
  >
  > pattern：正则表达式()

  [常用的正则表达式](https://www.jb51.net/tools/regex.htm)

- 实例：

  ~~~html
  <p>邮箱：
     <input type="text" name="name" placeholder="请输入邮箱" required="不能为空" pattern="[表达式]"> 
  </p>
  ~~~

## 二 正则表达式入门

- 限定符

  > 1. ？
  >
  >    说明：特殊字符，限定符：代表前面的字符出现0次或1次
  >
  >    用法：used？
  >
  >    结果：use、used
  >
  > 2. *
  >
  >    说明：限定符。匹配0个或多个字符
  >
  >    用法：use*d
  >
  >    结果：usd、used、useed.........
  >
  > 3. +
  >
  >    说明：匹配出现1次或以上的字符
  >
  >    用法：use+d
  >
  >    结果：used、useed...........
  >
  > 4. {num}
  >
  >    说明：更精确的匹配，自定义匹配字符出现的次数
  >
  >    用法：use{2,6}d---------->匹配2到6个e字符
  >
  >    ​			use{2,}d------------>匹配两次或以上e字符

- "或"运算符

  > 1. (|)
  >
  >    用法：a (cat|dog)
  >
  >    说明：先匹配a再匹配括号中的内容，要么是cat，要么是dog
  >
  > 2. |
  >
  >    用法：a cat|dog
  >
  >    说明：要么是a cat，要么是dog

- 字符类

  > 1. [abc]+
  >
  >    说明：匹配有abc组成的单词
  >
  > 2. [a-zA-Z0-9]+
  >
  >    说明：匹配所有字母和数字
  >
  > 3. ^
  >
  >    说明：匹配处^以外的所有字符
  >
  >    用法：[^0-9]匹配出所有的非数字字符，包括空格

- 元字符

  > \d：代表所有的数字字符
  >
  > \D：代表非数字字符
  >
  > \w：代表所有的英文字符，数字+下划线
  >
  > \W：代表非单词字符
  >
  > \s：代表空白符、包含TAB和换行符
  >
  > \S：代表非空白字符
  >
  > .：代表任意字符，但不包括换行符
  >
  > ^：匹配行首。如：^a------>匹配行首的a
  >
  > $：匹配行尾。如：`a$`-------->匹配行尾的a
  >
  > 

- 贪婪与懒惰匹配

  > 1. 默认为匹配尽可能多的字符
  >
  > 2. 懒惰匹配：
  >
  >    实例：<.+?>
  >
  >    说明：匹配HTML中的标签，但不会匹配标签中间的文本内容

# CSS

## 一.CSS基本格式及优势简介

> css的优势:
>
> 1、内容和表现分离
>
> 2、网页结构表现统一，可以实现复用
>
> 3、样式十分的丰富
>
> 4、建议使用独立于html的css文件
>
> 5、容易被搜索引擎收录

---

> 
>
> 格式：
>
> 选择器{
>
> ​	声明1；
>
> ​	声明2；
>
> }

###  CSS三种导入方式

1. 行内样式**(不用做开发，了解即可)**：

   > 使用HTML内嵌style标签也可以实现文本美化，不适合大的网站构建

   ~~~html
   <h1 style="color:red">aaaa</h1>
   ~~~

2. 内部样式表

   > 在HTML<head>标签中写入样式
   >
   > `<style>`里可以编写css代码，但不建议这样，一般为HTML+CSS+JS

   - 示例：

     ~~~html
     /*
     h1标题的文本颜色为red
     h1为选择器；
     color:red;为声明
     */
     <head>
     <style>
     h1{
         color:red;
     }
     </style>
     </head>
     ~~~

3. 外部样式

   > 最常用的方式。
   >
   > 可以分为：连接式(xhtml)和导入式(css2.1)
   >
   > 书写：在css文本中编写文本格式如字体颜色，大小等。之后再HTML文本中用link引用css链接，就可以实现美化文本。

   - 连接式：

   ~~~html
   <!--
   <link>为引入节点。
   href引入路径
   rel="stylesheet"基本格式。
   -->
   <link rel="stylesheet" type="text/css" href="style.css" />
   ~~~

   - 导入式：

   ~~~html
   <head>
       <style>
       	@import url("css/style.css")
       </style>
   </head>
   ~~~

- 优先级：就近原则

## 二.选择器

### 1. 标签选择器

   > 选择页面上的某一类元素，==先用选择器选择标签，再美化==
   >
   > 标签选择器会选择页面上的所  有相关标签元素。

### *2. 类选择器(class)

   > 可以选择一类标签进行更改样式。
   >
   > 可以归类多个标签，灵活性更高。

   ~~~html
   <!--
   格式：1.在<style>标签中.类名{}；
   	 2.文本标签后+class="类名"
   -->
   
   <style>
       .any{
   		color:blue;
       }
       .any2{
           color:red;
       }
   </style>
   <body>
       <h1 class="any1">标题1</h1>
       <h1 class="any1">标题2</h1>
       <h1 class="any2">标题3</h1>
   </body>
   ~~~

### *3. ID选择器
   > ID选择器必须唯一
   >
   > 可以精准定位一个元素

   ~~~html
   <!--
   格式：1.在<style>标签中#类名{}；
   	 2.文本标签后+id="ID名(全局唯一)"
   -->
   <style>
       #any{
   		color:blue;
       }
       #any2{
           color:red;
       }
   </style>
   <body>
       <h1 id="any1">标题1</h1>
       <h1 id="any2">标题2</h1>
       <h1 id="any3">标题3</h1>
   </body>
   ~~~

   **注意：选择器优先级不遵循就近原则。**

   **优先级大小：ID选择器>类选择器>标签选择器**

### 4. 层次选择器

- 后代选择器

  > 所有带<p>标签的都改为red样式。

  ~~~css
  body p{
  	background:red;
  }
  ~~~

  [运行结果](https://z3.ax1x.com/2021/09/28/4fRmlQ.png)：													  <img src="https://z3.ax1x.com/2021/09/28/4fRmlQ.png" alt="4fRmlQ.png" style="zoom:25%;" />

- 子选择器

  > 只选择下一级的直接标签改为greed样式
  >
  > 与**后代元素选择器**相比，**子元素选择器** 选取的一定是直系后代（儿子）

  ~~~css
  body>p{
      background:greed;
  }
  
  ~~~

  [运行结果](https://z3.ax1x.com/2021/09/28/4fRUX9.png)															<img src="https://z3.ax1x.com/2021/09/28/4fRUX9.png" alt="4fRUX9.png" style="zoom:30%;" />

  ~~~html
  <div class="box">
      <p>emmmmmmmmmm……</p>
      <p>23333333333333333……</p>
      <div>
      <p>wwwwwwwwwwww</p>
      <p id="aa">QQQQQQQQQQ</p>
      </div>    
  </div>
  ~~~

  ~~~css
  .box>p{  background: #aaf;}
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/03/29/qcZPIA.png)

  ​																[<img src="https://s1.ax1x.com/2022/03/29/qcZPIA.png" alt="qcZPIA.png" style="zoom: 50%;" />](https://imgtu.com/i/qcZPIA)

 - 相邻兄弟选择器	

   > 选择同级的下一个标签改为blue样式

   ~~~css
   .active + p{
       background:blue;
   }
   ~~~

   [运行结果](https://z3.ax1x.com/2021/09/28/4fRbcQ.png)															<img src="https://z3.ax1x.com/2021/09/28/4fRbcQ.png" alt="4fRbcQ.png" style="zoom:30%;" />

- 通用选择器

  > 选择同级的所有标签改为yellow样式

  ~~~css
  .active~p{
  	background:yellow;
  }
  ~~~

  [运行结果](https://z3.ax1x.com/2021/09/28/4fW99U.png)																<img src="https://z3.ax1x.com/2021/09/28/4fW99U.png" alt="4fW99U.png" style="zoom:30%;" />

### 5.结构伪类选择器

> 通过添加条件判断筛选标签。
>
> 如：first-child(第一个标签元素)
>
> ​		last-child(最后一个标签元素)

~~~css
/*选择ul的第一个子元素*/
ul li:first-child{
    background:red;
}
~~~

~~~css
/*选择ul的最后一个子元素*/
ul li:last-child{
    background:green;
}
~~~

~~~css
/*选中父元素下的p元素的第二个标签。*/
p:nth-of-type(2){
    background:yellow;
}
~~~

~~~css
/*选中链接时更改链接样式*/
a:hover{
    background:black;
}
/*被激活时的颜色*/
a:active{
    color:green;
}
<body>
	<a href="">aaaa</a>
</body>
~~~

~~~css
/*在p标签之后添加字符'aaa'*/
p:after{
    content:'aaa';
    
}
~~~

### ==6.属性选择器(较为常用)==

> 用条件匹配符合属性的标签
>
> 格式：节点[属性=值]{;}

- 实例：

  ~~~css
  /*匹配a节点中id为1的标签*/
  a[id="1"]{
  	background：red;
  }
  ~~~

  ~~~css
  /*匹配节点属性以http开头的标签*/
  a[href^=http]{
  	background:blue;
  }
  ~~~

## 三.网页元素的美化

> 意义：
>
> 1. 有效的传递网页信息。
> 2. 美化网页，吸引用户。
> 3. 凸显页面主题。
> 4. 提高用户体验。
> 5. ==span==标签：约定重点要突出的字。

### 1. 字体样式

> 格式：font-参数：参数值;

~~~css
font-family:微软雅黑;						 /*字体样式：楷体，宋体*/
font-size:10px;								/*字体大小*/
font-weight:bold;							/*字体粗细*/
font-color:blue;							/*字体颜色*/
~~~

> 以上代码一般简化为以下格式：
> font：字体风格	字体粗细	字体大小	字体样式；	

~~~css
/*字体为：斜体，变粗，20px，楷体*/
font:oblikue bolder 20px "楷体"
~~~

### 2.文本样式

1. 颜色：

   > 格式：color：颜色值；或：rgba(值1，值2，值3，值4)。
   >
   > 颜色参数：+#为rgb颜色。#xxxxxx
   >
   > RGB：代表红绿蓝三色。值有七位，#字开头，一色占两位。为十六进制(0~F)。
   >
   > RGBA：红绿蓝+透明度。透明度值：0~1。

2. 文本对齐方式：

   > text-align：排版

   ~~~css
   text-align:center;				/*文本居中*/
   ~~~

3. 首行缩进：

   ~~~css
   text-indent:2em;		   	 	/*首行缩进两字符*/
   ~~~

4. 行高：

   ~~~css
   height:300px;					/*设置行高*/
   line-height:300px;				/*设置百分比行高*/
   ~~~

5. 装饰：

   ~~~css
   text-decoration:none;			/*取消文本下滑线*/
   text-decoration:underline;		/*文本下划线*/
   text-decoration:line-through;	/*文本中划线*/
   text-decoration:overline;		/*文本上划线*/
   ~~~

   ~~~css
   /*图片与文字对齐*/
   img,span{
       vertical-align:middle;
   }
   ~~~

   [运行结果：](https://z3.ax1x.com/2021/09/28/4hAWWt.png)													![4hAWWt.png](https://z3.ax1x.com/2021/09/28/4hAWWt.png)

6. 文本阴影

   > text-shadow：阴影颜色，水平偏移，垂直偏移，阴影半径

   - 示例：

     ~~~css
     text-shadow:#ffffff 10px 10px 2px;
     ~~~

### 3.列表美化

~~~css
list-style:none;				/*取消列表前的黑点或数字*/
list-style:circle;				/*将列表改为空心圆*/
list-style:decimal;				/*将列表改为数字*/
list-style:square;				/*将列表改为正方形黑点*/
~~~

### 4.背景美化

- 边框：

  > border：边框
  >
  > 格式：border:边框粗细	边框样式	边框颜色; 

  ~~~css
  border:2px solid red;
  ~~~

- 背景图片：

  > background-image：背景图片
  >
  > 格式：background-image：url("路径")；

  ~~~css
  background-image:("ima/1.jpg");			/*默认背景为水平平铺*/
  background-repeat:repeat-x;				/*水平平铺*/
  background-repeat:repeat-y;				/*垂直平铺*/
  background-repeat:no-repeat;			/*取消背景平铺*/
  background-position:200px 100px			/*图片位置*/ 
  ~~~

  ~~~css
  /*综合方式*/
  /*属性值格式依次为：颜色  图片路径 图片位置 平铺方式*/
  background:red url("ima/1.jpg") 200px 100px no-repeat;
  ~~~

- 渐变：

  > 调色器设置为两种颜色
  >
  > linear-gradient：设置背景为多种颜色的组合。

  ~~~css
  /*linear-gradient(定义渐变的起点和方向或角度 color+值(%))......*/
  background-img:linear-gradient(45deg, #85FFBD 0%, #FFFB7D 100);
  ~~~

### 5.盒子模型

> margin：外边距
>
> border：外边框
>
> padding：内边距																										

<img src="https://z3.ax1x.com/2021/10/01/4Tx18P.png" alt="4Tx18P.png" style="zoom:55%;" />

​																											[图示](https://z3.ax1x.com/2021/10/01/4Tx18P.png)

1. 边框：

   > border的三个属性：边框粗细值	边框样式	边框颜色

   ~~~css
   border:3px solid black;
   ~~~

2. 外边距

   > 主要用来居中
   >
   > 要求：必须是一个有宽度的块元素，
   >
   > 值为：上	下	左	右

   ~~~css
   /*上下为0，左右自动对齐*/
   margin:(0,auto);
   /*值依次为：上 右 下 左	顺时针布局*/
   margin:(2px 3px 2px 2px);
   ~~~

3. 内边距

   > 同外边距格式一样

4. 盒子模型的计算方式

   > 这个元素的大小是多少
   >
   > border+margin+padding+文字内容大小=盒子的中间值(如：1446.86*524)

5. 圆角边框

   > border-radius：添加圆角边框
   >
   > 值也为顺时针布局

   ~~~css
   div{
   	width: 250px;
   	height:250px;
   	border:10px solid red;
   	border-radius:150px 150px;
   }
   ~~~

   <img src="https://z3.ax1x.com/2021/10/01/47kCUU.png" alt="47kCUU.png" style="zoom:35%;" />

   ​																										[运行结果](https://z3.ax1x.com/2021/10/01/47kCUU.png)

6. 阴影

   > box-shadow：水平阴影的位置	垂直阴影的位置	模糊距离/阴影的尺寸	阴影的颜色

   ~~~css
   box-shadow:0.625rem 0.625rem 3.125rem yellow;
   ~~~

   <img src="https://z3.ax1x.com/2021/10/01/47KOoR.png" alt="47KOoR.png" style="zoom:40%;" />

   ​																										[运行结果](https://z3.ax1x.com/2021/10/01/47KOoR.png)

### 6.display标签和浮动

- 标准文档流：

  > 块级元素：独占一行

  ~~~html
  <h>	<p>	<div>....
  ~~~

  > 行内元素：可以不占一行

  ~~~html
  <span> <a> <img> <string>....
  ~~~

  ==行内元素可以被包含再块级元素中。反之，则不行==

- display标签：

  > 标签参数值：
  >
  > block：块元素
  >
  > inline：行内元素
  >
  > inline-block：块行元素(保持块元素的特性，但可以布局在一行内)

  display标签属性：

  |         值         |                             描述                             |
  | :----------------: | :----------------------------------------------------------: |
  |        none        |                      此元素不会被显示。                      |
  |       block        |       此元素将显示为块级元素，此元素前后会带有换行符。       |
  |       inline       |     默认。此元素会被显示为内联元素，元素前后没有换行符。     |
  |    inline-block    |               行内块元素。（CSS2.1 新增的值）                |
  |     list-item      |                    此元素会作为列表显示。                    |
  |       run-in       |        此元素会根据上下文作为块级元素或内联元素显示。        |
  |      compact       | CSS 中有值 compact，不过由于缺乏广泛支持，已经从 CSS2.1 中删除。 |
  |       marker       | CSS 中有值 marker，不过由于缺乏广泛支持，已经从 CSS2.1 中删除。 |
  |       table        | 此元素会作为块级表格来显示（类似 `<table>`），表格前后带有换行符。 |
  |    inline-table    | 此元素会作为内联表格来显示（类似 `<table>`），表格前后没有换行符。 |
  |  table-row-group   |   此元素会作为一个或多个行的分组来显示（类似 `<tbody>`）。   |
  | table-header-group |   此元素会作为一个或多个行的分组来显示（类似 `<thead>`）。   |
  | table-footer-group |   此元素会作为一个或多个行的分组来显示（类似 `<tfoot>`）。   |
  |     table-row      |         此元素会作为一个表格行显示（类似 `<tr>`）。          |
  | table-column-group | 此元素会作为一个或多个列的分组来显示（类似 `<colgroup>`）。  |
  |    table-column    |         此元素会作为一个单元格列显示（类似 `<col>`）         |
  |     table-cell     |   此元素会作为一个表格单元格显示（类似 `<td> `和 `<th>`）    |
  |   table-caption    |       此元素会作为一个表格标题显示（类似 `<caption>`）       |
  |      inherit       |           规定应该从父元素继承 display 属性的值。            |

  ~~~css
  /*将div块元素改为块行布局*/
  div{
      width:100px;
      height:100px;
      border:1px solid red;
     	display:inline-block;
  }
  /*span标签变为块行布局*/
  span{
      width:100px;
      height:100px;
      border:1px solid red;
     	display:inline-block;
  }
  ~~~

  <img src="https://z3.ax1x.com/2021/10/01/471plV.png" alt="471plV.png" style="zoom:45%;" />

  ​																									[运行结果](https://z3.ax1x.com/2021/10/01/471plV.png)

- 浮动标签float

  > float：浮动方向

  ~~~css
  /*向右浮动*/
  float:right;
  ~~~

  标签属性：

  |   值    |                         描述                         |
  | :-----: | :--------------------------------------------------: |
  |  left   |                    元素向左浮动。                    |
  |  right  |                    元素向右浮动。                    |
  |  none   | 默认值。元素不浮动，并会显示在其在文本中出现的位置。 |
  | inherit |        规定应该从父元素继承 float 属性的值。         |

- 父级文档塌陷问题

  > 在文档流中，父元素的高度默认是被子元素撑开的，也就是子元素多高，父元素就多高。但是当子元素设置浮动之后，子元素会完全脱离文档流，此时将会导致子元素无法撑起父元素的高度，导致父元素的高度塌陷。

  [如图所示：](https://z3.ax1x.com/2021/10/01/4728EQ.png)

  <img src="https://z3.ax1x.com/2021/10/01/4728EQ.png" alt="4728EQ.png" style="zoom:100%;" />

  - 解决方法：

    1. *增加父级元素高度，使父级边框足以容纳内部的浮动元素*

       > 好处：简单
       >
       > 坏处:
       >
       > 1. 需要根据浮动元素的高度来调整；
       > 2. 如果父级边框的高度有限制，则无法应用此方法

       ~~~css
       #father {
           border: 1px #000 solid;
           height: 800px;
       }
       ~~~

       

    2. *增加空div*

       > 在浮动元素后面增加一个空的div（清除浮动、内外边距设为0）
       >
       > 好处：简单
       >
       > 坏处：需要修改页面代码（因为增加了一个div),为了文本规范，不建议添加空div

       ~~~css
       .clear {
           clear:both;
           margin:0;
           padding:0;
       }
       ~~~

    3. *给父级元素设置自动溢出*　

       > 在父级元素中增加一个 overflow:hidden;(溢出隐藏)

       overflow标签值一览：

       |   值    |                           描述                           |
       | :-----: | :------------------------------------------------------: |
       | visible |       默认值。内容不会被修剪，会呈现在元素框之外。       |
       | hidden  |          内容会被修剪，并且其余内容是不可见的。          |
       | scroll  | 内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。 |
       |  auto   | 如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。 |
       | inherit |         规定应该从父元素继承 overflow 属性的值。         |

       ~~~css
       #father{
           border:2px solid red;
           overflow:hidden;
       }
       ~~~

    4. *父级元素添加伪类（推荐）*

       > 避免了以上3个方法的缺点。
       > 本方法有点类似第2个方法增加空div，但是不需要修改页面代码

       ~~~css
       #content:after {
           content:'';
           display:block;
           clear:both;
       }
       ~~~

       clear标签属性一览：

       |   值    |                 描述                  |
       | :-----: | :-----------------------------------: |
       |  left   |        在左侧不允许浮动元素。         |
       |  right  |        在右侧不允许浮动元素。         |
       |  both   |     在左右两侧均不允许浮动元素。      |
       |  none   |   默认值。允许浮动元素出现在两侧。    |
       | inherit | 规定应该从父元素继承 clear 属性的值。 |

- 总结：
  - display：方向不可控
  - float：浮动起来会脱离标准文档流所以要解决父级边框塌陷的问题

### 7.定位

- 相对定位(relative)：

  > 说明：相对于自己原来的位置进行偏移。
  >
  > 格式：
  >
  > position：属性值；
  >
  > 方向值1：偏移值；
  >
  > 方向值2：偏移值；.......

  position标签属性：

  |    值    |                             描述                             |
  | :------: | :----------------------------------------------------------: |
  | absolute | 生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。 |
  |  fixed   | 生成固定定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。 |
  | relative | 生成相对定位的元素，相对于其正常位置进行定位。因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。 |
  |  static  | 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。 |
  | inherit  |           规定应该从父元素继承 position 属性的值。           |

  ~~~css
  /*反方向位移，不会脱离文档流，原来的位置会被保留*/
  #first{
      position:relative;
      top:20px;
      left:20px;
  }
  ~~~

- 绝对定位(absolute)

  > 1. 基于xxx定位，然后上下左右位移。
  >
  > 2. 假设父级元素存在定位，我们通常会相对于父级元素进行便宜。
  > 3. 在父级元素范围内进行移动。
  > 4. 相对于父级或浏览器的位置，进行指定的偏移，绝对定位的话，它不在标准文档流中，原来的位置不会被保留。

- 固定定位(fixed)

  > 固定的内容不随网页的滑动而改变。

### 8.z-index

> 设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。
>
> z-index值默认为0，最高无限层。

~~~css
z-index:999;			/*定位的属性在图层最上面*/
~~~

~~~css
/*从 0.0 （完全透明）到 1.0（完全不透明）*/
opacity:0.5;			/*设置定位标签半透明*/
~~~

### 9.动画拓展

参考网站

> [源码之家](http://www.codejia.com/)
>
> [HTML5动画平台](https://www.html5tricks.com/)
>
> [卡巴斯基地图](https://cybermap.kaspersky.com/cn)

### ==10. flexbox和Grid布局==



# JavaScript

> 脚本语言，严格区分大小写。

## 一.快速入门

### 1.HTML导入方式

- `<script>`标签导入

  > 书写在<head>和<body>标签都可以，<script>标签必须成对出现

  ~~~html
  <!--alert：弹窗-->
  <script>
  	alert("hello world");
  </script>
  ~~~

  [运行结果：](https://z3.ax1x.com/2021/10/02/4beVAI.png)

  <img src="https://z3.ax1x.com/2021/10/02/4beVAI.png" alt="4beVAI.png" style="zoom:50%;" />

- 创建js文件再进行导入(推荐)

  > 引入标签格式：
  >
  > <script src="路径"></script>

### 2. 输入输出语句

> 为了方便信息输入输出，JavaScript提供一下方法

|        方法        |             说明              |
| :----------------: | :---------------------------: |
|    alert('msg')    |       浏览器弹出警示窗        |
| console.log('msg') |   浏览器控制台打印输出信息    |
|   prompt('info')   | 浏览器弹出输入框,用户可以输入 |

### 3.基本语法入门

#### 1. 定义变量

  > 只有一个定义类型：var
  >
  > 局部变量定义：let
  >
  > 浏览器控制台打印变量：console.log(变量名)

变量的命名规范：

  > 1. 由字母(A-Za-z).数字(0-9)、 下划线( )、元符号($ )组成,不能以数字开头。如: usrAge, num01,_ name
  > 2. 严格区分大小写。var app;和var App;是两个变量
  > 3. 不能以数字开头。18age 是错误的
  > 4. 不能是关键字、保留字。例如:var、for. while
  > 5. 变量名必须有意义。
  > 6. 遵守驼峰命名法。首字母小写,后面单词的首字母需要大写。myFirstName

  ~~~js
  <script>
  var num=6;
  var name="shi";
  let num=1;
  console.log(name);
  </script>
  ~~~

- 变量存储

  ~~~javascript
  var myname=prompt('请输入你的名字');
  alert(myname);
  #用户输入名字后弹出的对话框会显示名字
  ~~~

- 同时声明多个变量

  > 同时声明多个变量时,只需要写一个var ，多个变量名之间使用英文逗号隔开。
  >
  > 没有声明的变量也可以使用，不会报错，但不建议这样使用。

  ~~~JavaScript
  var age=18,
      name='syb',
      email='1973295103@qq.com';
  ~~~

#### 2. 数据类型：

基本概念

> 在计算机中,不同的数据所需占用的存储空间是不同的,为了便于把数据分成所需内存大小不同的数据,分利用存储空间,于定义了不同的数据类型。
>
> 变量是用来存储值的所在处,它们有名字和数据类型。量的数据类型决定了如何将代表这些值的位存储到计算机的内存中。JavaScript 是一种弱类型或者说动态语言。这意味着不用提前声明变量的类型,在程序运行过程中, 类型会被自动确定。

JavaScript数据类型具有一下特性：

> 1. js的变量数据类型是只有程序在运行过程中，根据等号右边的值来确定的。
> 2. JavaScript是动态语言，变量的数据类型是可以变化的。 

> JavaScript中数字统一称为number类型。
>
> 八进制前面加0，十六进制加0x。
>
> number值可以是任何数(包括负数和自然数)。
>
> number类型中如果返回"NaN"表示不是一个数。
>
> 返回infinite表示该数无限大。
>
> 在JavaScript中同样可以将一种类型强转为另一种类型。

~~~js
<script type="text/javascript">
var test1= new Boolean(true);
var test2= new Boolean(false);
var test3= new Date();
var test4= new String("999");
var test5= new String("999 888");
document.write(Number(test1)+ "<br />");
document.write(Number(test2)+ "<br />");
document.write(Number(test3)+ "<br />");
document.write(Number(test4)+ "<br />");
document.write(Number(test5)+ "<br />");
</script>
//运行结果：
1
0
1256657776588
999
NaN
~~~

数字类型标识：

> Infinity , 代表无穷大,大于任何数值
> -Infinity ,代表无穷小,小于任何数值
> NaN，Not a number ,代表-个非数值

判断数据是否是数字方法

~~~JavaScript
console.log(isNAN(10));
//结果为false(是数字为false，不是数字则为true)
~~~

#### 3. 字符类型：

  > 字符串可以用" "或' '

  ~~~js
  var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  var txt01='ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  ~~~

  - 多行字符串编写：

    > ``用来编写多行字符串

    ~~~JavaScript
    var text=`
    	hello\t
    	world
    `
    //运行结果：
    hello	world
    ~~~

  - 字符串插值:

    > 模板字面量提供了一种将变量和表达式插入字符串的简单方法。该方法称为字符串插值。
    >
    > 语法：${...}

    ~~~JavaScript
    let firstName = "John";
    let lastName = "Doe";
    let text = `Welcome ${firstName}, ${lastName}!`;
    //运行结果：Welcome John, Doe!
    ~~~

  - 字符串长度及一些常用的方法：

    > 字符串不可变
    >
    > substring：字符串截取，包头不包尾

    ~~~JavaScript
    var student="study";
    console.log(student.length);
    console.log(student[0]);
    console.log(student.substring(1,3));
    //运行结果：5 s tu
    ~~~

- 字符串的拼接

  > 多个字符串之间可以使用"+"进行拼接，其拼接方式为：字符串+任意类型=新字符串。
  >
  > 拼接前会把与字符串相加的任何类型转化成字符串，再拼接成一个新的字符串。

  ~~~JavaScript
  console.log('ab'+'cd')					//abccd
  console.log('ab'+2)						//ab2
  console.log('ab'+true)					//abture
  
  var age = prompt( '请输入您的年龄');
  var str = '您今年已经'+ age +'岁了';
  alert(str);								//输出弹窗为用户输入的年龄
  ~~~

- 转义字符

  | 转义字符 | 解释说明  |
  | :------: | :-------: |
  |    \n    |   换行    |
  |   `\\`   | 斜杠`'\'` |
  |   `\"`   | 双引号""  |
  |    \t    |  制表符   |
  |    \b    |   空格    |

#### 4.布尔值

  > 值为：true和false。
  >
  > 数字类型为：0和1。

- typeof检测变量数据类型

  ~~~JavaScript
  var num=10;
  console.log(typeof num);
  //输出：number
  ~~~

#### 5. 数据类型转换

- 转换为字符串

  |        方式        |             说明             |               示例               |
  | :----------------: | :--------------------------: | :------------------------------: |
  |   toString()方法   |          转为字符串          | var run=1; alert(num.toString);  |
  |  String()强制转换  |          转成字符串          |  var run=1; alert(String(num));  |
  | ==加号拼接字符串== | 和字符串拼接的结果都是字符串 | var run=1; alert(num+'字符串')； |

- 转换为数字类型

  |              方法               |                          说明                          |        示例        |
  | :-----------------------------: | :----------------------------------------------------: | :----------------: |
  |      parselnt(string)函数       |              将string类型转换为整数数值型              |   parselnt('66')   |
  |     parseFloat(string)函数      |                  将string转换成浮点型                  | parseFloat('66.6') |
  |        Number()强制转换         |                将string类型转换为数值型                |    Number('6')     |
  | JavaScript隐式转换('-','*','/') | 利用算数运算转换为数值型(js会将字符先转化为整数再运算) |       '66'-0       |

  ~~~javascript
  var num1='10',num2='20',num=(num1*1)+(num2*1);
  console.log(num);
  //结果为number类型的30
  ~~~

- 转换为布尔型

  |   方式    |         说明         |       示例       |
  | :-------: | :------------------: | :--------------: |
  | Boolean() | 其他类型转换为布尔值 | Boolean('ture'); |

  > 代表空、否定的值会被转换为false , 如' '、0、NaN、null、 undefined
  > 其余值都会被转换为true

#### 6. 逻辑运算

  > &&：与。两个都为真则为真。
  >
  > ||：或。其中一个为真，则为真。
  >
  > ！：非。真及假，假及真。

- 逻辑中断(&&)

  ~~~JavaScript
  console.log(123 && 456);					//结果为456
  console.log(0 && 456);						//结果为0
  console.log('123' && '456');				//结果为'456'
  console.log('' && '456');					//结果为''
  ~~~

  > 逻辑与短路运算	如果表达式1结果为真，则返回表达式2；如果表达式1为假，则返回表达式1。

- 逻辑终端(||)

  > 逻辑或短路运算：如果表达式1的结果为真，则返回的是表达式1；如果表达式1结果为假，则返回表达式2。

  ~~~JavaScript
  console.log(123 || 456);					//结果为123
  console.log(0 || 456);						//结果为456
  console.log('123' || '456');				//结果为'123'
  console.log('' || '456');					//结果为'456'
  ~~~

- [运算符优先级：](https://z3.ax1x.com/2021/11/27/omwpaq.png)

  ​                      [<img src="https://z3.ax1x.com/2021/11/27/omwpaq.png" alt="omwpaq.png" style="zoom: 67%;" />](https://imgtu.com/i/omwpaq)

#### 7. 比较运算符

  > 大部分与Java类似。
  >
  > ==特别注意：==
  >
  > =：赋值。
  >
  > ==：等于。(类型不一样，值一样，也会判断为true)
  >
  > ===：绝对等于(类型一样，值一样，则为true)

  ~~~js
  <script>
  	var num=1;
  	var num1="1";
  	alert(num1==num);
  </script>
  //运行结果：
  true
  ~~~

  ~~~js
  <script>
  	var num=1;
  	var num1="1";
  	alert(num1===num);
  </script>
  //运行结果：
  false
  ~~~

  **注：**NaN与所有的数值都不想等，包括自己。只能通过isNaN(num);方法来判断值是否为NaN。

  **另：**表达式：1/3!=1-2/3;因为会存在精度丢失的问题，可以用math.abs(1/3-(1-2/3))<0.00000001；判断等式两边表达式是否相等。

#### 8. NULL和undefined

  > NULL：空
  >
  > undefined：未定义的

#### 9. 数组

  > JavaScript的数组中可以有任意类型。
  >
  > 注：给数组赋值，数组的大小就会发生改变，如果赋值过小元素就会丢失。

  ~~~js
  var arr = [1,2,3,4,5,"hello" ,nul1,true];
  //也可为：
  new Array(1,12,3,4,4,5,"he1lo");
  ~~~

- 新增数组元素

  - 方法一：修改length长度

    ~~~JavaScript
    var arr=['red','green','blue'];
    arr .length = 5; //把我们数组的长度修改为了5里面应该有5个元素
    console.1og(arr);
    console.log(arr[3]); // undefined
    console.log(arr[4]); // undefined
    ~~~

  - 方法二：新增数组元素修改索引号追加数组元素

    ~~~JavaScript
    var arr1 = ['red','green','blue'];
    arr1[3] = 'yellow' ;
    console.1og(arr1);
    arr1[4] = 'orange' ;
    console.1og(arr1);
    arr1[0] = 'yellow'; // 这里是替换原来的数组元素
    console.log(arr1);  //yellow,green,blue,yellow,orange
    ~~~

- 筛选数组(可以用来删除数组元素)

  ~~~JavaScript
  var arr=[2,0,6,1,77,0,52,0,25,7];
  var newArr=[];
  for(var i=0;i<arr.length;i++){
  	if (arr[i] > 10) {
  	newArr[newArr.length] = arr[i];
  	}
  }
  console.log(newArr);
  ~~~

  - indexof，通过元素获得数组下标

    ~~~JavaScript
    var arr = [1,2,3,4,5,"hello" ,nul1,true];
    arr.indexof("hello");
    //运行结果：5
    //注：1和"1"是不相同的
    ~~~

  - slice，截取字符串

    > 该方法与substring一样，包头不包尾。

  - push和pop

    > push：压栈，将元素放入数组尾部
    >
    > pop：弹栈，将数组尾部的一个元素取出

    ~~~JavaScript
    var arr = [1,2,3,4,5,"hello" ,nul1,true];
    arr.push("a","b");
    //运行结果：1,2,3,4,5,"hello" ,nul1,true,"a","b"
    //pop:与push相反
    ~~~

  - unshift和shift

    > 和push，pop相反，unshift和shift是将元素在数组头部。

  - concat，拼接数组

    > 将值与数组拼接,但不会修改数组

    ~~~JavaScript
    var arr = [1,2,3,4,5,"hello" ,nul1,true];
    arr.concat(1,2,3);
    //运行结果：1,2,3,4,5,"hello" ,nul1,true,1,2,3
    ~~~

#### 10. 严格检查模式

  > 介绍：因为JavaScript代码具有随意性，开启严格检查模式可以有效的预防一些问题的产生。

  ~~~js
  <script>
  	'use strict';
  	let num=1;
  </script>
  ~~~
#### 11. 对象

> 代表若干个键值对
>
> {......}表示一个对象，键值对描述xxx：xxx，多个属性之间使用逗号隔开，最后一个属性不加逗号。
>
> JavaScript中所有键都是字符串，值是任意对象

~~~JavaScript
//定义了一个person对象，它有四个属性
var person={
    name:"shi",
   	age:19,
    email:"23214343@qq.com",
    score:100
}
//对象赋值：
person.name="zhang"
~~~

- 数组对象

  ~~~JavaScript
  const todos = [
      {
  		id: 1,
  	 	text: 'Take out trash ' ,
          isCompleted: true
      }，
      {
  		id: 2,
  		text: 'Meeting with boss',
      	isCompleted: true
  	},
  	{
  		id: 3,
  		text: 'Dentist appt',
          isCompleted: false}
  ];
  console.log(todos[1].text);
  //输出：Meeting with boss
  ~~~

- 动态删减属性

  > 通过delete删除对象的属性

  ~~~JavaScript
  delete person.name				//删除person的name属性
  ~~~

- 动态添加属性

  > 直接给新的属性添加值即可

  ~~~javascript
  person.sex="男"					//给person添加了一个新属性sex
  ~~~

- 判断属性值是否在对象中

  > xxx in xxx

  ~~~JavaScript
  'sex' in person					//sex属性是否在person对象中
  ~~~

- 解构

  ~~~JavaScript
  const{firstname,lastname,address:{cinty}}=person
  console.log(firstname)
  //取出person里的firstname的值
  ~~~

#### 12 流程控制(判断和循环)

##### 12.1 判断语句

  > 同Java一样

- if else if多分支语句

  ~~~javascript
  if (条件表达式1) {
  //语句1;
  } else if (条件表达式2) {
  //语句2;
  } else if (条件表达式3) {
  //语句3;
  } else {
  //最后的语句;
  }
  ~~~

- 三元运算符

  > 格式：
  >
  > 条件表达式	？	表达式1：表达式2
  >
  > 如果条件表达式结果为真，则返回表达式1，否则返回表达式2。
  
  ~~~javascript
  var num=18;
  var result =num<20 ? 'yes':'no';
  console.log(result);				
  //结果为'yes'
  ~~~

- switch语句

  格式：

  ~~~JavaScript
  switch(表达式) { 
  case value1 :
  	//执行语句1;
  	break;
  case value2:
  	//执行语句2;
  	break;
  default:
  	//执行最后的语句;
  }
  ~~~

  > 执行思路 利用我们的表达式的值和case后面的选项值相匹配如果匹配上，就执行该case里面的语句如果都没有匹配上，那么执行default里 面的语句
  >
  > ==注意：==我们num的值和case 里面的值相匹配的时候是全等必 须是值和数据类型一致才可以num === 1。

##### 12.2 循环语句

  > 有while循环和for循环
  >
  > while：先判断再执行
  >
  > for：先判断再执行
  >
  > do{……}while()：先执行再判断(一定执行一次。)

- 数组循环

  - foreach循环(增强for循环)

    > foreach虽然是for循环的简化版本，但是并不是说foreach就比for更好用，foreach适用于循环次数未知，或者计算循环次数比较麻烦情况下使用效率更高，但是更为复杂的一些循环还是需要用到for循环效率更高。
    
    ~~~JavaScript
    var arr=[23,213,2,31,23,21,1,32];
    arr.foreach(funtion(value){
        console.log(value)
    });
    ~~~
    

##  二. 函数

### 1. 定义函数

  > 方法一：一旦执行到return语句，代表函数结束，返回结果。 (命名函数)

  ~~~JavaScript
  function abs(x){
      if(x>=0)
  		{
           	return x;
          }else{
              return -x;
          }
  }
  //结果：abs(-10)=10
  //return可以返回数组
  function getarr(num1,num2){
      return[num1+num2,num1-num2,num1*num2];
  }
  var arr=getarr(10,7);
  console.log(arr);
  ~~~

  > 方法二：function(x){…………}这是一个匿名函数，但是可以把结果赋值给abs，之后通过abs就可以调用函数。(匿名函数)

  ~~~JavaScript
  var abs=function(x){
  	if(x>=0)
  		{
           	return x;
          }else{
              return -x;
          }
  }
  //结果：同上
  ~~~

|       参数个数       |                结果                |
| :------------------: | :--------------------------------: |
|   实参个数等于形参   |              正常输出              |
| 实参个数大于形参个数 |           只取到形参个数           |
| 实参个数小于形参个数 | 多的形参定义为undefined，结果我NaN |

### 2. 调用函数

  > abs(10);						  //结果：10
  >
  > abs(-10);						//结果：10

### 3. JavaScript的作用域

> 通常来说, 一段程序代码中所用到的名字并不总是有效和可用的,而限定这个名字的可用性的代码范围就是这个名字的作用域。作用域的使用提高了程序逻辑的局部性,增强了程序的可靠性,减少了名字冲突。
>
> 作用域：就是代码名字(变量)在某个范围内起作用和效果。其目的是为了提高程序的可靠性。
>
> 作用域分两种：全局作用域和局部作用域。

- 局部作用域(指在函数内部的就是局部作用域)

  ~~~JavaScript
  function arr()
      //这里面的是局部作用域
  }
  ~~~

- 全局作用域(在函数外部，作用于整个script标签的)

  > ==注意：==如果在函数内部没有声明直接赋值的变量也属于全局变量。

  ~~~JavaScript
  var num=10;								//全局作用域				
  function num1(){
  	num1=20;							//这也是一个全局变量
  }
  ~~~

- 内部函数可以访问外部函数(这种访问方式被称为：链式查找方式)

  ~~~javascript
  var num = 10;
  function fn() { //外部函数
  	var num = 20;
  	function fun() { //内部函数
  		console.log(num);
  	}
      fun();
  }
  fn();								   //结果：20
  ~~~

### 4. JavaScript的运行机制——预解析

> JavaScript代码是由浏览器中的JavaScript解析器来执行的。JavaScript 解析器在运行JavaScript代码的时候分为两步：预解析和代码执行。
>
> 预解析：js引擎会把js里面所有的var还有function提升到当前作用域的最前面。
> 代码执行：按照代码书写的顺序从 上往下执行。

- 预解析

  1. 变量提升

     > 变量提升就是把所有的变量声明提升到当前的作用域最前面不提升赋值操作

     ~~~JavaScript
     console.log(num); 				// 结果：undefined
     var num = 10;
     //相当于执行了以下代码
     var num;
     console.log(num);
     num=10;
     ~~~

     ~~~JavaScript
     fun(); 							//结果：报错
     var fun = function() {
     console.1og(22);
     //相当于执行了以下代码
     var fun;
     fun();
     fun = function() {
     console.1og(22);
     }
     ~~~

  2. 函数提升

     > 函数提升就是把所有的函数声明提升到当前作用域的最前面不调用函数

     ~~~javascript
     fn();							//结果：11
     function fn() {
     	console .1og(11);
     }
     //相当于一下代码：
     function fn() {
     	console .1og(11);
     }
     fn();
     ~~~

  3. 总结

     > ==函数表达式调用必须写在函数表达式的下面。==

### 5. arguments获取参数

> arguments是一个关键字，它的作用是将传进来的参数，变为一个伪数组(没有真正数组的一些方法：pop、push等)。常用在不确定形参数目情况。

~~~JavaScript
var abs=function(x){
    console.log(x);
    for(var i=0;i<arguments.length;i++){
        console.log(arguments[i]);
    }
	if(x>=0)
		{
         	return x;
        }else{
            return -x;
        }
}
//将多余的参数输出
~~~

### 6. rest 

> arguments的升级版。可以获取除了已经定义参数之外的所有参数。

~~~JavaScript
function abs(x,y,...rest){
    console.log(x);
    console.log(y);
    console.log(rest);
}
//rest中会存放除了已经定义过的x,y的其他参数。
~~~

## 三. 对象

### 1. 对象简介

> 现实生活中:万物皆对象,对象是一个具体的事物 ,看得见摸得着的实物。例如,一本书、一辆汽车、 一个人可以是“对象”, 一个数据库、一张网页、一个与远程服务器的连接也可以是“对象”。
>
> 在JavaScript中,对象是一组无序的相关属性和方法的集合,所有的事物都是对象,例如字符串、数值、数组、函数等。
>
> 属性：事物的特征,在对象中用属性采表示(常用名词标识)
> 方法：事物的行为,在对象中用方法来表示(常用动词标识)

### 2. 创建对象方式

#### 1.1 创建对象的多种方式

- 利用字面量创建对象

  > 对象字面量:就是花括号{}里面包含了表达这个具体事物(对象)的属性和方法。
  >
  > (1) 里面的属性或者方法我们采取键值对的形式 属性名:属性值
  >
  > (2)多个属性或者方法中间用逗号隔开的
  >
  > (3)方法冒号后面跟的是一个匿名函数

  ~~~javascript
  var obj={
  	uname: '张三疯'，
  	age: 18,
  	sex :'男',
  	sayHi: function() {					//方法
  		console.1og('hi~');
  	}
  }
  ~~~

- 利用new创建对象

  > 使用new创建对象的时候要使用    等号    赋值的方法添加对象的属性和方法
  >
  > 每个属性和方法之间用    分号    结束

  ~~~javascript
  var obj=new Object();						//创建了一个空的对象
  obj.uname = '张三疯' ;
  obj.age = 18;
  obj.sex='男';
  obj.sayHi = function() {				//方法
  	console.1og('hi~' );
  }
  ~~~

- 利用构建函数创建对象

  > 前面两种创建对象的方式一次只能创建一个对象，利用构造函数可以重复对象里相同的属性和方法。
  >
  > 其本质就是将对象里一些相同的属性和方法抽象出来封装到函数里。

  语法规范：

  > function    构造函数名() {
  >     this.属性=值;
  >     this.方法= function() {}
  >
  > }
  >
  > new    构造函数名();    使用
  >
  > 1. 构造函数名字首字母要大写
  > 2. 构造函数不需要return就可以返回结果

  ~~~JavaScript
  function Star(uname, age, sex) {
  	this.name = uname ;
  	this.age = age;
  	this.sex = sex;
      this.sing = function(sang) {
  		console.log(sang);
  }
  var ldh = new Star('刘德华’，18, '男');			//调用函数类型结果是一个对象
  ldh.sing('冰雨');
  console.log(ldh.name);
  console.log(ldh.age);
  console.log(ldh.sex);
  ~~~

- 构造函数和对象区别

  |        构造函数        |        对象        |
  | :--------------------: | :----------------: |
  | 泛指一大类(java中的类) | 特质一个具体的事物 |

#### 1.2 对象的调用

> 调用对象的属性我们采取	对象名.属性名	的格式

~~~JavaScript
console.log (obj.uname);
~~~

> 调用属性还有一种方法	对象名['属性名']	的格式。

~~~JavaScript
console.log(obj['age']); 
~~~

#### 1.3 方法定义调用：

> 方法其实就是把函数放在对象里，对象只有两个东西：属性和方法。

~~~JavaScript
var shi={
    name:"shiyibo",
    birth:2000,
    age:function(){
        var year=new Data().getFu1lyear();
        return year-this.birth; 
    }
};
console.log(shi.age());
//结果：20
//属性：shi.name
//方法要带（）：shi.age()
~~~

#### 1.4 变量、属性、函数和方法的区别

- 变量和属性的区别

  <table>
       <tr>
    		<td></td> 
    		<td>相同</td> 
          <td>不同</td> 
      </tr>
      <tr> 
          <td><strong>变量</strong></td> 
          <td>他们都是用来存储数据的</td> 
          <td>变量单独声明并赋值,使用的时候直接写变量名,单独存在。<br>属性在对象里面的不需要声明</td>
     </tr>
      <tr> 
          <td><strong>属性</strong></td> 
          <td>都是实现某种功能，做某件事</td> 
          <td>函数是单独声明,并且调用方法是：函数名() 且单独存在<br>方法在对象的里面。调用的时候：对象.方法()
  </td>
     </tr>            
  </table>

### 3. new关键字执行过程

new在执行时会做四件事情

> 1. 在内存中创建一个 新的空对象。
> 2. 让this指向这个新的对象。
> 3. 执行构造函数里面的代码,给这个新对象添加属性和方法。
> 4. 返回这个新对象(所以构造函数里面不需要return)。

### 4. 遍历对象

格式：

> for(变量	in	对象){
>
> }

~~~JavaScript
var obj={
    name:'syb',
    age:19,
    sex:'男'
}
for(var key in obj){
    console.log(key);					//输出得到的是变量名
    console.log(obj[key]);				//输出得到的是属性值
}
~~~

### 5. 内置对象

> JavaScript中的对象分为3种：自定义对象、内置对象、浏览器对象(JavaScript API)
>
> 前两种对象是JavaScript的基础内容，属于ECMAScript；第三个浏览器对象属于我们JavaScript独有的。

> 内置对象就是JavaScript内嵌的属性和方法。JavaScript提供了多个内置对象: Math、Date 、Array、 string等

#### 5.1 随机数(random)

> `Math.random()` 函数返回一个浮点数,  伪随机数在范围从**0到**小于**1**，也就是说，从0（包括0）往上，但是不包括1（排除1），然后您可以缩放到所需的范围。实现将初始种子选择到随机数生成算法;它不能被用户选择或重置。

- 得到一个大于等于0，小于1之间的随机数

  ~~~javascript
  function getRandom() {
    return Math.random();
  }
  ~~~

- 得到一个两数之间的**随机数**

  ~~~javascript
  function getRandomArbitrary(min, max) {
    return Math.random() * (max - min) + min;
  }
  ~~~

- 得到一个两数之间的随机**整数**

  ~~~javascript
  function getRandomInt(min, max) {
    min = Math.ceil(min);									//Math.ceil()函数返回大于或等于一个给定数字最小整数。
    max = Math.floor(max);								//Math.floor()返回小于或等于一个给定数字的最大整数。
    return Math.floor(Math.random() * (max - min)) + min; //不含最大值，含最小值
  }
  ~~~

- 得到一个两数之间的**随机整数**，**包括两个数**在内

  ~~~javascript
  function getRandomIntInclusive(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min; //含最大值，含最小值 
  }
  ~~~

#### 5.2 日期对象(Date)

> Date对象他是一个构造函数,所以我们需要实例化后才能使用。
>
> Date对象主要用来处理日期和时间。

- 输出当前时间(无参数)

  ~~~JavaScript
  var now=new Date();
  console.log(now);
  ~~~

- 返回指定时间(有参数)

  > 如果括号里面有时间,就返回参数里面的时间。例如日期格式字符串为'2019-5-1' , 可以写成new Date('2019-5-1')
  > 或者new Date('2019/5/1')

  ~~~JavaScript
  var time=new Date('2019-05-01')
  console.log(time);
  ~~~


[Date日期方法：](https://s4.ax1x.com/2021/12/05/oB5lWt.png)

​								[<img src="https://s4.ax1x.com/2021/12/05/oB5lWt.png" alt="oB5lWt.png" style="zoom: 67%;" />](https://imgtu.com/i/oB5lWt)

- 返回当前时间(00:00:00)

  ~~~JavaScript
  function getTime() {
  	var time = new Date();
  	var h = time . getHours();
  	h=h<10 ? '0'+h:h;
  	var m = time.getMinutes( );
  	m = m<10 ? '0'+m:m;
  	var s = time . getSeconds();
  	s = s<10 ? '0'+ s:s;
  	return h +':'+m+':'+ s;
  }
  console.1og(getTime());
  ~~~

- 倒计时案例

  ~~~JavaScript
  function countDown(time) {
  	var nowTime = +new Date(); //返回的是当前时间总的毫秒数
  	var inputTime = +new Date(time); //返回的是用户输入时间总的毫秒数
  	var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数
  	var d = parseInt(times / 60 / 60 / 24); //天
  	d = d < 10 ? '0' + d : d;
  	var h = parseInt(times / 60 / 60 % 24); //时
  	h = h < 10 ? '0' + h : h;
  	var m = parseInt(times / 60 % 60); //分
  	m = m < 10 ? '0' + m : m;
  	var s = parseInt(times % 60); //当前的秒
  	s = s < 10 ? '0'+ s : s;
  	return  d + '天' + h + '时'+ m +'分' + s + '秒';
  }
  console.log(countDown('2021-12-5 18:00:00'));
  ~~~

#### 5.3 数组对象

- 添加删除数组元素

  [添加删除数组元素方法：](https://s4.ax1x.com/2021/12/05/oDS9T1.png)

​						[<img src="https://s4.ax1x.com/2021/12/05/oDS9T1.png" alt="oDS9T1.png" style="zoom: 67%;" />](https://imgtu.com/i/oDS9T1)

- 数组排序

  |  方法名   |            说明             |          是否修改原数组          |
  | :-------: | :-------------------------: | :------------------------------: |
  | reverse() | 颠倒数组中元素的顺序,无参数 | 该方法会改变原来的数组返回新数组 |
  |  sort()   |    对数组的元素进行排序     | 该方法会改变原来的数组返回新数组 |

	~~~JavaScript
	//数组翻转
	var arr = ['pink','red', 'blue'];
	arr.reverse( );
	console.log(arr);
	//数组排序(冒泡排序)
	var arr1 = [13, 4, 77, 1, 7];
	arr1. sort(function(a, b) {
		return a - b; 						//升序的顺序排列
		return b - a; 						//降序的顺序排列工
	});
	console.1og(arr1);
	~~~

- **数组去重**

  ~~~JavaScript
  function unique(arr) {
  	var newArr = [];
  	for(vari=0;i<arr.length;i++){
  		if (newArr.indexof(arr[i]) === -1) {
  			newArr.push(arr[i]);
  		}
  	}
  	return newArr ;
  }
  var demo =unique(['c','a','z','a','x','x','c','b']);
  console.log(demo);
  ~~~

- 数组转换为字符串

  |    方法名    |                     说明                     |     返回值     |
  | :----------: | :------------------------------------------: | :------------: |
  |  toString()  |      把数组转换成字符串，逗号分隔每-项       | 返回一个字符串 |
  | join(分隔符) | 方法用于把数组中的所有元素转换为一个字符串。 | 返回一个字符串 |

  ~~~JavaScript
  //1. toString
  var arr = [1, 2, 3];
  console. log(arr .toString()); 				// 1,2,3
  // 2. join(分隔符)
  var arr1 = ['green' ,'blue','pink'];
  console.1og(arr1.join()); 					// green, blue, pink
  console.log(arr1. join('-')); 				// green-blue-pink
  console.log(arr1.join('&')); 				// green&blue&pink
  ~~~

- 拼接数组

  |    方法名    |                 说明                  |                   返回值                    |
  | :----------: | :-----------------------------------: | :-----------------------------------------: |
  |   concat()   |    连接两个或多个数组不影响原数组     |              返回一个新的数组               |
  |   slice()    |       数组截取slice(begin, end)       |           返回被截取项目的新数组            |
  | **splice()** | 数组删除splice(第几个开始,要删除个数) | 返回被删除项目的新数组注意,这个会影响原数组 |

#### 5.4 字符串对象

> 简单数据类型可以通过包装转换为复杂数据类型，然后就可以使用复杂数据类型的方法和属性。
>
> 为了方便操作基本数据类型, JavaScript还提供了三个特殊的引用类型: String、Number和Boolean。

~~~JavaScript
var str ='andy';
console.1og(str.length);
//基本包装类型:上边两行代码等同于以下代码:
// (1) 把简单数据类型包装为复杂数据类型
var temp = new String ('andy');
// (2) 把临时变量的值给str
str = temp;
// (3) 销毁这个临时变量
temp = null;
~~~

- 根据字符返回位置

  |               方法               |                             说明                             |
  | :------------------------------: | :----------------------------------------------------------: |
  | indexOf(要查找的字符,开始的位置) | 返回指定内容在元字符串中的位置，如果找不到就返回-1,开始的位置是index索引号 |
  |          lastIndexOf()           |                 从后往前找，只找第一个匹配的                 |

  ~~~JavaScript
  //查找字符串"abcoefoxyozzopp"中所有o出现的位置以及次数
  var str ="abcoefoxyozzopp";
  var index = str.indexOf('o');
  while (index !== -1) {
  	console.log(index);
  	index = str .indexOf('o', index + 1);
  }
  ~~~


- 根据位置返回字符

  |      方法名       |                   说明                   |             使用              |
  | :---------------: | :--------------------------------------: | :---------------------------: |
  |   charAt(index)   | 返回指定位置的字符(index字符串的索引号)  |         str.charAt(0)         |
  | charCodeAt(index) | 获取指定位置处字符的ASCII码(index索引号) |       str.charCodeAt(0)       |
  |    str[index]     |            获取指定位置处字符            | HTML5, IE8+支持和charAt()等效 |

- **统计出现次数最多的字符**

  ~~~JavaScript
  var str ='abcoefoxyozzopp' ;
  var o={};
  for (var i = 0; i < str.length; i++) {
  	var chars = str.charAt(i);					// chars是字符串的每一个字符
  	if (o[chars]) {								// o[chars] 得到的是属性值
  		o[chars]++;
  	} else {
  		o[chars] = 1;
  	}
  }
  // 2.遍历对象
  var max = 0;
  var ch
  for(var k in o){
  	if (o[k] > max) {					// k得到是属性名										
  	max = o[k];							// o[k] 得到的是属性值
  	ch=k;
  }
  console.log(max);
  console.log('最多的字符是' + ch);
  ~~~

- **字符串操作方法**

  |          方法名           |                             说明                             |
  | :-----------------------: | :----------------------------------------------------------: |
  | concat(str1,str2,str3...) | concat()方法用于连接两个或多个字符串。拼接字符串,等效于+, +更常用 |
  | **substr(start,length)**  |          从start位置开始(索引号)，length是取的个数           |
  |     slice(start, end)     | 从start位置开始，截取到end位置，end取不到 (他们俩都是索引号) |
  |   substring(start, end)   | 从start位置开始，截取到end位置，end取不到基本和slice 相同但是不接受赋值 |

- 替换字符(replace和split)

  replace：

  ~~~JavaScript
  var str ='andyandy' ;
  console.log(str.replace('a', 'b'));					//把第一个a替换为b
  //有一个字符串' abcoefoxyozzopp' 要求把里面所有的0替换为*
  var str1 ='abcoefoxyozzopp' ;
  while (str1.index0f('o') !== -1) {
  	str1 =str1.replace('o','*');
  }
  console.log(str1);
  ~~~

  **split：**

  ~~~JavaScript
  var str2 = 'red,pink,blue' ;
  console.1og(str2.split(','));						//['red','pink','blue']
  var str3 = 'red&pink&blue';
  console.log(str3.split('&'));						//['red','pink','blue']
  ~~~

- 字符转换大小写

  |    方法名     |       说明       |                 使用示例                 |
  | :-----------: | :--------------: | :--------------------------------------: |
  | toUpperCase() | 将字符转换为大写 | console.log( "alphabet".toLowerCase() ); |
  | toLowerCase() | 将字符转换为小写 | console.log( "ALPHABET".toLowerCase() ); |

### 6. 栈和堆简介

> 1. 简单数据类型是存放在栈里面里面直接开辟一个空间，存放的是值。
> 2. 复杂数据类型首先在栈里面存放地址十六进制表示，然后这个地址指向堆里面的数据。

[栈和堆示意图：](https://s4.ax1x.com/2021/12/05/oDOQPS.png)

​							[<img src="https://s4.ax1x.com/2021/12/05/oDOQPS.png" alt="oDOQPS.png" style="zoom: 67%;" />](https://imgtu.com/i/oDOQPS)

补充：[JavaScript中{...}的作用：](https://www.php.cn/js-tutorial-483543.html#:~:text=%E5%9C%A8JavaScr,e%E2%80%9D%E7%9A%84%E6%96%B9%E5%BC%8F%E5%B1%95%E5%BC%80%E3%80%82)

## 四. Web APIs

### 1. Web APIs和JS基础关联性 

[JavaScript的组成：](https://s4.ax1x.com/2021/12/05/oDjknA.png)

​								[<img src="https://s4.ax1x.com/2021/12/05/oDjknA.png" alt="oDjknA.png" style="zoom:67%;" />](https://imgtu.com/i/oDjknA)

#### 1.1 API和WebAPI

- API

  > API ( Application Programming Interface,应用程序编程接口)是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力, 而无需访问源码，或理解内部工作机制的细节。
  >
  > 简单理解: API是给程序员提供的一种工具，以便能更轻松的实现想要完成的功能。

- WebAPI

  > Web API是浏览器提供的一套操作**浏览器功能**和**页面元素**的API( BOM和DOM)。
  >
  > 因为Web API很多,所以我们将这个阶段称为Web APIs。
  >
  >  Web API主要是针对于浏览器提供的接口，主要针对于浏览器做交互效果。
  > Web API 一般都有输入和输出(函数的传参和返回值) , Web API很多都是方法(函数)

### 2. DOM

#### 2.1 DOM简介

> W3C已经定义了一系列的DOM接口，通过这些DOM接口可以改变网页的内容、结构和样式。

- DOM树

  [DOM树：](https://s4.ax1x.com/2021/12/05/oDvLIx.png)

​				[<img src="https://s4.ax1x.com/2021/12/05/oDvLIx.png" alt="oDvLIx.png" style="zoom:67%;" />](https://imgtu.com/i/oDvLIx)

> 1. 文档:一个页面就是一个文档, DOM中使用document表示
> 2. 元素:页面中的所有标签都是元素, DOM中使用element表示
> 3. 节点:网页中的所有内容都是节点(标签、属性、文本、注释等) , DOM中使用node示。
> 4. **DOM把以上内容都看做是对象。**

#### 2.2 getElementByld获取元素(类似ID选择器)

~~~JavaScript
var element = document.getElementById(id);			//语法
~~~

> **`element`**是一个 [Element](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 对象。如果当前文档中拥有特定ID的元素不存在则返回null。
>
> **`id`**是大小写敏感的字符串，代表了所要查找的元素的唯一ID。
>
> 返回一个匹配到 ID 的 DOM [`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 对象。若在当前 [`Document`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document) 下没有找到，则返回 null。

~~~JavaScript
var timer = document.getElementById( 'time ' );
console.1og(timer);
console.1og(typeof timer);
console.din(timer );							// console.dir打印我们返回的元素对象更好的查看里面的属性和方法
~~~

#### 2.3 getElementsByTagName获取页面标签某类元素(类似标签选择器)

- 获取所有元素

  > 使用getElementsByTagName() 方法可以返回带有指定标签名的对象的集合，以伪数组形式存储。

  ~~~javascript
  var lis=document.getElementsByTagName('li');		//语法
  console.log(lis[0]);								//返回li标签的第一个元素内容
  ~~~

- 根据标签名获取

  > 还可以获取某个元素(父元素)内部所有指定标签名的子元素

  ~~~JavaScript
  var o1 = document.getElementById('ol');				//通过ID获取列表父元素
  console.log(ol.getElementsByTagName('li'));			//通过该方法获取父元素下所有li元素
  ~~~

#### 2.4 getElementsByClassName获取页面标签类元素

- 方法一

  > getElementsByClassName根据类名获得某些元素集合

  ~~~javascript
  var boxs = document.getElementsByClassName( 'box' );
  console.log(boxs);
  ~~~

- 方法二

  > querySelector返回指定选择器的第一个元素对象，可以是类，标签或者ID
  >
  > document.querySelector ('选择器');         // 根据指定选择器返回第一个元素对象

  ~~~JavaScript
  var firstBox = document.querySelector('.box' );		//获取类为'box'的第一个元素
  console.log(firstBox);												
  ~~~

- 方法三

  > querySelectorAll( )        返回指定选择器的所有元素对象集合
  >
  > document.querySelectorAll( '选择器');        // 根据指定选择器返回所有元素

  ~~~JavaScript
  var allBox = document.querySelectorAll('.box');		//与方法一一致，但该方法更灵活
  console.log(a11Box);
  ~~~

#### 2.5 获取body和html元素

- 获取body标签

  ~~~JavaScript
  var bodyEle = document.body; 
  console.log(bodyEle);
  ~~~

- 获取html元素

  ~~~JavaScript
  var htmlEle=document.documentElement;				//返回htm1元素对象
  console.log(htmlEle);
  ~~~

#### 2.6 其他方法

| 方法名 |                          作用                          |    示例     |
| :----: | :----------------------------------------------------: | :---------: |
| find() | 方法返回通过测试（函数内判断）的数组的第一个元素的值。 | find("div") |
|  eq()  |      方法将匹配元素集缩减值指定 index 上的一个。       |    eq(2)    |

### 3. DOM事件获取

> JavaScript使我们有能力创建动态页面,而事件是可以被JavaScript侦测到的行为。
> 简单理解:触发---响应机制。
> 网页中的每个元素都可以产生某些可以触发JavaScript的事件,例如,我们可以在用户点击某按钮时产生一个事件，然后去执行某些操作。

- 点击一个按钮，弹出对话框

  > 事件是有三部分组成：事件源、事件类型、事件处理程序、我们也称为事件三要素
  >
  > 1. 事件源：事件被触发的对象(按钮)
  > 2. 事件类型：如何触发这个事件，出发事件类型(常见的有：鼠标点击、鼠标经过、按下键盘指定案件等)
  > 3. 事件处理程序：通过一个函数赋值的方式来完成这个动作。

  ~~~html
  //点击一个按钮，弹出一个对话框
  <body>
  	<button id='btn'>按钮</button>    
  </body>
  <script>
  	var btn=document.getElementById('btn');			//1. 获取触发对象(事件源)
  	btn.onclick=function(){							//2. 鼠标点击属性为：onclick(事件类型)
          alert('这是一个按钮');						//3. 事件触发后执行什么(事件处理函数)
      }							
  </script>
  ~~~


- 常见鼠标事件

  |  鼠标事件   |     触发条件     |
  | :---------: | :--------------: |
  |   onclick   | 鼠标点击左键触发 |
  | onmouseover |   鼠标经过触发   |
  | onmouseout  |   鼠标离开触发   |
  |   onfocus   | 获得鼠标焦点触发 |
  |   onblur    | 失去鼠标焦点触发 |
  | onmousemove |   鼠标移动触发   |
  |  onmouseup  |   鼠标弹起触发   |
  | onmousedown |   鼠标按下触发   |

### 4. DOM操作页面元素

#### 4.1 修改元素的内容

  - element.innerText

    > 从起始位置到终止位置的内容,但它去除html标签，同时空格和换行也会去掉。

    ~~~JavaScript
    var btn = document.querySelector( 'button' );			//获取页面button标签
    var div = document.querySelector('div');				//获取页面div标签
    btn.onclick = function() {
    	div.innerText = getDate();							//点击按钮后会将事件传递给div并打印
    }
    function getDate() {
    	var date = new Date( ) ;
    	var year = date.getFullYear();
    	var month = date.getMonth() + 1;
    	var dates = date.getDate();
    	var arr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六'];
    	var day = date.getDay();
    	return '今天是:' + year + '年' +month + '月' + dates + '日' + arr[day];
    }
    ~~~

  - element.innerHTML

    > 起始位置到终止位置的全部内容,包括html标签,同时保留空格和换行。

    ~~~javascript
    var div = document.querySelector( 'div');				//获取页面div元素
    div.innerHTML = '<strong>今天是: </strong> 2021';		  
    ~~~

    > 上面输出为：**今天是：**2021
    >
    > 这里的`<strong>`标签生效。

#### 4.2 修改元素属性

> 1. 获取元素节点或id
> 2. 添加事件

~~~JavaScript
//修改元素属性 src
// 1.获取元素
var ldh = document . getElementById('ldh');
var zxy = document . getElementById('zxy');
var img = document . querySelector('img');
// 2.注册事件 处理程序
zxy .onclick = function() {
	img.src ='images/zxy.jpg';
	img.title = 'hello';
}
ldh.onclick = function() {
	img.src ='images/1dh.jpg' ;
	img.title = 'world';
}
~~~

#### 4.3 element.innerText和element.innerHTML区别

|  方法名   |                不同                |
| :-------: | :--------------------------------: |
| innerText |   不识别html标签，且为非标准方法   |
| innerHTML | **识别**html标签，且为官方推荐方法 |

#### 4.4 修改表单属性

> 表单元素的修改不能使用innerText和innerHTML。而是通过type、value、checked、selected、 disabled等来设置属性。

~~~JavaScript
var btn = document. querySelector('button');
var input = document . querySelector('input');
btn.onclick = function() {
input.value ='被点击了';								//表单里面的值文字内容是通过value来修改的
~~~

#### 4.5 修改样式属性

> 注意：
>
> 1.  JavaScript修改的样式为行内样式，权重高。
> 2. JavaScript样式采取驼峰命名法。如：fontSize、backgroundColor等

~~~JavaScript
var div = document . querySelector( 'div' );
div.onclick =function() {
this.style. backgroundColor = ' purple ';			   //this指向调用者('div')
this.style.width = '250px ';						   //点击后背景颜色改为'purple'，宽度改为'250px'
~~~

- 使用className修改样式属性(用于样式较多情况)

  ~~~JavaScript
  var test = document.querySelector('div'); 
  test.onclick = function() {
  	this.className = 'change';						//鼠标点击后将类名'change'赋值给test
  }
  ~~~
  
- 密码框验证消息

  ~~~JavaScript
  var ipt = document . querySelector('.ipt');
  var message = document . querySelector('.message' );
  //2. 注册事件失去焦点
  ipt.onblur = function() {
  //根据表单里面值的长度ipt. value. length
  	if (this. value.length < 6|| this. value.length > 16) {
  	message. className =' message wrong ' ;
  	message.innerHTML='您输入的位数不对要求6~16位”;
  } else {
  	message.className ='message right ' ;
  	message. innerHTML = ' 您输入的正确';
  	}
  }
  ~~~

#### 4.6 获取及移除自定义属性值

- 获取属性值

  > element.属性	获取属性值。
  > element .getAttribute('属性' ) ;

  - elemen获取属性值

    ~~~JavaScript
    var div = document . querySelector( 'div' );
    console. log(div.id);								//输出div的id属性值
    ~~~

  - getAttribute获取属性值

    ~~~JavaScript
    var div = ydocument . querySelector( 'div' );
    console.log(div. getAttribute( 'id')) 				//获取div的id属性值
    ~~~

  - 二者区别

    > element.属性获取        内置属性值(元素本身自带的属性)
    > element .getAttribute(属性');        主要获得自定义的属性 ( 标准)我们程序员自定义的属性自动属性规范：data-xxx

- 替换和移除属性值

  - 替换属性值

    > element . setAttribute('属性'，'值') ;

    ~~~javascript
    var div = ydocument . querySelector( 'div' );
    div . setAttribute( 'index',2); 
    div . setAttribute( ' class','footer');
    ~~~

  - 移除属性值

    ~~~JavaScript
    var div = ydocument . querySelector( 'div' );
    div . removeAttribute( ' index' ) ;
    ~~~

#### 4.6 操作元素总结

[操作元素总结：](https://s1.ax1x.com/2021/12/10/oIoOxI.png)

​	[<img src="https://s1.ax1x.com/2021/12/10/oIoOxI.png" alt="oIoOxI.png" style="zoom: 45%;" />](https://imgtu.com/i/oIoOxI)

### 5. 排他思想

> 如果有同一-组元素,我们想要某一个元素实现某种样式,需要用到循环的排他思想算法:
>
> 1. 所有元素全部清除样式(干掉其他人)
> 2. 给当前元素设置样式(留下我自己)
> 3. 注意顺序不能颠倒,首先干掉其他人,再设置自己。

~~~JavaScript
//点击更换按钮颜色
var btns = document . getElementsByTagName('button'); 
for (var i = 0; i < btns.length; i++) {
	btns [i].onclick = function() {
		for (var i = 0; i < btns.length; i++) {
			btns[i]. style. backgroundColor = '' ;				//当为''时，就为取消背景颜色
}
	this. style. backgroundColor = ' pink' ;
}
~~~

~~~JavaScript
//点击更换背景图片
var imgs = document . querySelector('. baidu' ). querySelectorAll('img');
for (var i = 0; i < imgs.length; i++) {
	imgs[i]. onclick =function() {
		document . body . style . backgroundImage = 'ur1l(' + this.src + ' )' ;
    }
}
~~~

### 6. 节点操作

> 节点操作也是为了获取页面元素。节点相对于DOM来说更简单。

|             DOM获取             |          节点获取          |
| :-----------------------------: | :------------------------: |
|    document.getElementByld()    | 利用父子兄节点关系获取元素 |
| document.getElementsByTagName() |  逻辑性强,但是兼容性稍差   |
|    document.querySelector等     |                            |
|      **逻辑性不强、繁琐**       |                            |

#### 6.1 节点概述

> 网页中的所有内容都是节点(标签、属性、文本、注释等) , 在DOM中,节点使用node来表示。HTML DOM树中的所有节点均可通过JavaScript进行访问,所有HTML元素(节点)坷被修改,也可以创建或删除。
>
> 一般地,节点至少拥有nodeType (节点类型)、nodeName (节点名称)和nodeValue (节点值)这三个基本属性。
>
> 1. 元素节点nodeType 为1
> 2. 属性节点nodeType为2
> 3. 文本节点nodeType为3 (文本节点包含文字空格、换行等)

#### 6.2 节点操作——父节点

> 1. parentNode属性可返回某节点的父节点,注意是最近的一个父节点
> 2. 如果指定的节点没有父节点则返回null
> 3. 语法：node.parentNode

~~~JavaScript
var erweima = document . querySelector('.erweima' );		//获取子节点
console .log(erweima . parentNode);							//获取子节点后直接用parentNode可以获取父节点
~~~

#### 6.2 节点操作——子节点

> 1. parentNode. children是一个只读属性,返回所有的子元素节点。它只返回子元素节点,賒节点不返回(这个是我们重点掌握的)。
> 2. 语法：parentNode. children

~~~JavaScript
var ul = document . querySelector('ul' );				//获取ul标签
console.log(u1.children);								//获取ul标签下的所有子节点
console.log(u1.children[1]);							//获取ul标签下的第二个子节点
~~~

#### 6.3 节点操作——获取第一个和最后一个元素

~~~JavaScript
node . firstElementChild								//获取第一个子节点(包括文本节点)
~~~

~~~JavaScript
node . lastElementChild									//获取最后一个子节点
~~~

#### 6.4 节点操作——兄弟节点

~~~JavaScript
node . nextElementSibling									
//nextsibling返回当前元素的下一个兄弟节点,找不到则返回null。同样,也是包含所有的节点。
node . previousElementSibling
//previoussibling返回当前元素上一个兄弟节点,找不到则返回null。同样,也是包含所有的节点。
~~~

#### 6.5 创建并添加节点

- 创建节点

  > document. createElement()方法创建由tagName指定的HTML元素。因为这些元素原先不存在,是根据我们的需求动态生成的,所以我们也称为动态创建元素节点。

  ~~~javascript
  document.createElement ('tagName ')
  ~~~

  ~~~JavaScript
  var li = document. createElement('li');				//创建一个'li'节点
  ~~~

- 添加节点

  > node. appendChild()方法将一个节点添加到指定父节点的子节点列表末尾。类似于css里面的
  > after伪元素。但只能追加在子元素之后。

  ~~~JavaScript
  node.appendChild (child);							//node要添加元素的父节点，child为子节点
  ~~~

  ~~~JavaScript
  var li = document.createElement('li');				//创建一个'li'节点
  var ul = document.querySelector('ul' );				//获取'ul'节点
  ul. appendChild(li);								//将'li'节点添加到'ul'节点中
  ~~~

- node . insertBefore将元素加载子元素之前

  > node . insertBefore(child,指定元素);

  ~~~JavaScript
  <ul>
  	<li>world</li>
  </ul>
  var li1i=document . createElement( 'li');			//创建元素
  ul. insertBefore(lili, ul.children[0]);				//将创建的'li'节点添加到'ul'的第一个节点前面,及'world'前
  ~~~

- 评论区案例

  ~~~JavaScript
  var btn = document . querySelector( ' button' );	//获取事件
  var text = document . querySelector('textarea');
  var ul = document . querySelector( 'ul' );
  btn.onclick = function() {							//点击提交按钮执行事件
  	if (text.value =='') {							//判断输入框里的内容是否为空，为空则退出函数
  		alert('您没有输入内容');
  		return false;
  	} else {									
  		var li = document . createElement('li');	//创建'li'节点
  		li.innerHTML=text.value+"<a href='javascript:;'>刪除</a>"; //将文本框里的内容赋值给新创建的'li'节点
  		ul. insertBefore(li, ul.children[0]);		//将'li'节点添加到'ul'节点最前面
          var as = document . querySelectorAll( 'a');	//绑定删除评论事件
  		for(var i=0;i<as.length;i++){
  			as[i].onclick = function() {
                  ul.removeChild(this.parentNode)		//点击后删除评论
              }	   
          }
      }
  }
  ~~~

#### 6.6 删除节点

> node. removeChild()方法从DOM中删除一个子节点,返回删除的节点。

~~~JavaScript
node . removeChild (child)
~~~

~~~JavaScript
var ul = document . querySelector('ul');				//点击按钮后删除一行
var btn = document . querySelector( ' button ');
btn.onclick=function(){
    if(ul.children.length==0){
        this.disabled=true;
    }else{
        ul.removeChild(ul.children[0]);
    }
}
~~~

#### 6.7 复制节点

> node. cloneNode ()方法返回调用该方法的节点的一个副本。也称为克隆节点/拷贝节点。
>
> 注意：如果括号参数为空或者为false ,则是浅拷贝,即只克隆复制节点本身,不克隆里面的子节点。
>
> ​			node. cloneNode(true);括号为true深拷贝复制标签复制里面的内容。

~~~JavaScript
node. cloneNode ();
~~~

#### 6.8 三种动态创建元素的区别

|                      document. write ()                      |                     element . innerHTML                      |               document . createElement ()                |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :------------------------------------------------------: |
| document .write是直接将内容写入页面的内容流,但是文档流执行完毕,则它会导致页面全部重绘 | innerHTML，创建多个元素效率更高(不要拼接字符串,采取数组形式拼接),结构稍微复杂 | createElement()创建多个元素效率稍低一点点,但是结构更清晰 |

#### 6.9 DOM基础事件总结

- 创建

  > 1. document.write
  > 2. innerHTML
  > 3. createElement

- 增

  > 1. appendChild(元素后添加)
  > 2. insertBefore(元素前添加)

- 删

  > removeChild

- 改

  > 主要修改dom的元素属性, dom元素的内容、属性,表单的值等
  >
  > 1. 修改元素属性: src、 href. title等
  > 2. 修改普通元素内容: innerHTML、innerText
  > 3. 修改表单元素: value、type、 disabled等
  > 4. 修改元素样式: style、 className

- 查

  > 主要查询页面元素
  >
  > 1. DOM提供的APl方法: getElementByld、 getElementsByTagName 古老用法不太推荐
  > 2. H5提供的新方法: querySelector、 querySelectorAll 提倡
  > 3. 利用节点操作获取元素:父(parentNode)、子(children)、 兄(previousElementSibling.nextElementSibling)提倡

- 属性操作

  > 主要针对于自定义属性。
  >
  > 1. setAttribute :设置dom的属性值
  > 2. getAttribute :得到dom的属性值
  > 3. removeAttribute移除属性

### 7. 高级事件

#### 7.1 DOM事件流

> 事件流描述的是从页面中接收事件的顺序。
>
> 事件发生时会在元素节点之间按照特定的顺序传播,这个传播过程即DOM事件流。
>
> **DOM事件流分为3个阶段:**
>
> 1. 捕获阶段(由DOM最顶层节点开始,然后逐级向下传播到到最具体的元素接收的过程。)
> 2. 当前目标阶段()
> 3. 冒泡阶段(事件开始时由最具体的元素接收,然后逐级向上传播到到DOM最顶层节点的过程。)
>
> **注意：**
>
> 1. JS代码中只能执行捕获或者冒泡其中的一个阶段。
> 2. onclick和attachEvent只能得到冒泡阶段。
> 3. 

[DOM事件流：](https://s4.ax1x.com/2021/12/12/oLCxD1.png)

​											[<img src="https://s4.ax1x.com/2021/12/12/oLCxD1.png" alt="oLCxD1.png" style="zoom: 67%;" />](https://imgtu.com/i/oLCxD1)

#### 7.2 监听注册事件

> 由于传统注册事件方式具有唯一性：对同一个元素同一个事件只能设置一个处理函数,最后注册的处理函数将会覆盖前面注册的处理函数，所以要用到**监听注册方式**(同一个元素同一个事件可以添加多个侦听器(事件处理程序))。

> eventTarget . addEventListener ()方法将指定的监听器注册到eventTarget (目标对象)上,当该对象触发指定的事件时,就会执行事件处理函数。
>
> 该方法接收三个参数：
>
> 1. type :事件类型字符串,比如click、mouseover , 注意这里不要带on。
> 2. listener :事件处理函数,事件发生时,会调用该监听函数。
> 3. useCapture :可选参数,是一个布尔值,默认是false。第三个参数如果是true ,表示在事件捕获阶段调用事件处理程序;如果是false (不写默认就是false ) , 表示在事件冒泡阶段调用事件处理程序。

~~~JavaScript
var btns = document . querySelectorAll( ' button' );
btns[1]. addEventListener( 'click', function() {				//注册鼠标点击事件
	alert(22);
})
btns[1] . addEventListener( 'click', function() {				//结果两个函数都会执行
	alert(33);
})
btns[1] . addEventListener( 'click',fn );						//不用匿名函数。这种方法也可以实现
function fn(){
    alert(44)
}
~~~

#### 7.3 删除事件

> eventTarget. removeEventListener (type，listener[, useCapture]) ;

移除监听事件：

~~~JavaScript
btns[1] . addEventListener( 'click',fn );						//移除监听事件
function fn(){
    alert(66);
    divs [1] . removeEventListener('click', fn);				//执行事件执行一次后移除
}
~~~

#### 7.4 事件对象

> 简单理解:事件发生后,跟事件相关的一系列信息数据的集合都放到这个对象里面,这个对象就是事件对象event ,它有很多属性和方法。
>
> 1. 事件对象只有有了事件才会存在，它是系统给我们自动创建的，不需要我们传递参数。
> 2. 事件对象是我们事件的一系列相关数据的集合跟事件相关的比如鼠标点击里面就包含了鼠标的相关信息，鼠标坐标，如果是键盘事件里面就包含的键盘事件的信息比如：判断用户按下了那个键。
> 3. 这个事件对象我们可以自己命名比如：event、evt、e

~~~JavaScript
eventTarget. onclick = function (event) {};
eventTarget . addEventListener('click', function(event) {})
//这个event就是事件对象，我们还喜欢的写成e或者evt
~~~

#### 7.5 定时器对象

> 定时器可以实现对函数的定时调用

- 间歇定时器的创建与清除`setInterval()`

  > 间歇定时器的创建使用 window 对象的 setInterval() 方法。在 JS 中，对象方法的调用格式通常为：对象名.方法，但由于 window 对象是全局对象，访问同一个窗口中的方法时，可以省略对象名“window”，所以对 window 对象方法，通常都是直接使用方法。格式如下：

  ~~~JavaScript
  [定时器对象ID = ]setInterval(函数调用｜函数定义,毫秒);
  ~~~

  > setInterval() 主要包含两个参数，第一个参数就是定时器需要定时执行的函数，该参数可以是一个用函数名表示的函数调用语句，也可以是一个函数定义语句。
  >
  > 第二参数是一个单位为毫秒的数值（表示执行第一个参数指定操作所需的等待时间）。该方法表示每隔由第二个参数设定的毫秒数，就执行第一个参数指定的操作。setInterval() 执行后将返回一个唯一的数值 ID。

  通过定时器返回的 ID，可以清除定时器。清除间歇定时器的格式如下：

  ~~~JavaScript
  clearInterval(定时器对象ID);
  ~~~

- 延迟定时器的创建和清除`setTimeout()`

  > 延迟定时器的创建使用 window 对象的 setTimeout() 方法，创建格式如下：

  ~~~javascript
  [定时器对象ID = ]setTimeout(函数调用｜函数定义,毫秒);
  ~~~

  > 第一个参数就是定时器需要定时执行的函数，该参数可以是一个用函数名表示的函数调用语句，也可以是一个函数定义语句；
  >
  > 第二个参数是一个单位为毫秒的数值（表示执行第一个参数指定操作所需的等待时间）。
  >
  > 该方法表示经过第二个参数所设定的时间后，执行一次第一个参数指定的操作。setTimeout() 执行后同样会返回一个唯一的数值 ID。

  延迟定时器也可以通过其返回的 ID 来清除。清除延迟定时器的格式如下：

  ~~~javascript
  clearTimeout(定时器对象ID);
  ~~~

- 两个方法不同之处

  |    方法名     |                             不同                             |
  | :-----------: | :----------------------------------------------------------: |
  | setInterval() | 按照指定的周期（以毫秒计）来调用函数或计算表达式。方法会不停地调用函数，直到 `clearInterval()` 被调用或窗口被关闭。 |
  | setTimeout()  |            在指定的毫秒数后调用函数或计算表达式。            |

  

 



