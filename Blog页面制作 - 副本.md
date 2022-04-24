# 整体布局

> 页面整体布局分为五个部分：
>
> 1. 最上面的区域为显示目录
> 2. 第二部分展示网页主题Boke四个字母和底部的打字机效果
> 3. 第三部分有头部栏、轮播页、轮播页底部按钮和主题调色等模块组成
> 4. 第四部分为部分笔记简介
> 5. 最后一部分是页脚
>
> 页面背景用canvas标签绘制，当然这东西以我现在水平肯定弄不出来，实训就一周时间。所以我直接引用[插件库里的代码](https://www.jq22.com/code4126)

## 一. 目录区域

> 列表部分由一个按钮加一个div盒子组成。按钮用来控制div是否隐藏(后期添加点击打开目录效果)。div盒子里放笔记链接。
>
> 之后用fixed实现页面固定。剩下就用css实现就完成第一步。

[目录区域位置布局示意图：](https://s4.ax1x.com/2021/12/18/TEzUZq.png)

​											[<img src="https://s4.ax1x.com/2021/12/18/TEzUZq.png" alt="TEzUZq.png" style="zoom:50%;" />](https://imgtu.com/i/TEzUZq)

### 1. 实现代码及原理

html部分：

> 由上面可以看出代码主要分两部分，列表区域用大盒子`div`包裹里面为一行一行链接。最后的小`div`用来装一个计时器。
>
> 下面的button按钮用来显示列表

~~~html
<div class="bg-lis" id="liss">
			<h2>笔记一览</h2>
			<h4><a href="./study/WEB表示层.html">WEB表示层</a></h4>
			<h4><a href="./study/软件迁移初识.html">软件迁移初识</a></h4>
			<h4><a href="./study/Java扫雷应用.html">Java扫雷应用</a></h4>
			<h4><a href="./study/Linux+Docker+Git.html">Linux+Docker+Git</a></h4>
			<h4><a href="./study/数据库语法(语法速记).html">数据库语法(语法速记)</a></h4>
			<h4><a href="./study/MySQL 语法(基础入门).html">MySQL 语法(基础入门)</a></h4>
			<h4><a href="./study/计算机组成原理.html">计算机组成原理</a></h4>
			<h4><a href="./study/正则表达式.html">正则表达式</a></h4>
			<h4><a href="">sss</a></h4>
			<h4><a href="./study/Java扫雷.html">sss</a></h4>
			<div id="time"></div>
</div>
<button class="btn btn1" id="btn">LIST</button>
~~~

css：

> 大致实现原理是先将按钮用`position`固定定位到屏幕右上角，然后设置边框样式。在按钮里左边插入列表图片，对图片位置进行修改。右边是按钮文字，设置文字样式之后就完成按钮排版。
>
> 列表区域先用固定定位移动到屏幕中间位置，方便之后使用js动画效果。然后就是对文字样式和边框进行修改。

***代码查看链接：github.com/Acidmt/web-Blog.git***

### 2 .js添加特性

> 特效也不难实现，我们只要完成两步：点击按钮后显示列表，添加移动的动画效果。这里一定要给列表添加`position`属性。
>
> ==点击按钮实现：==
>
> 1. 通过css的`display:none`将列表目录区域改为隐藏。
> 2. 获取`button`按钮的标签节点
> 3. 添加鼠标焦点事件，移动到列表按钮上面之后将css列表目录的`display`属性改为`block`，显示目录列表。
> 4. 添加文档点击事件，点击页面其他区域后重新将列表目录的`display`属性改为`none`隐藏列表目录。
>
> ==移动动画效果：==
>
> 1. 通过目录ID获取列表节点。
> 2. 封装一个动画函数，里面用到四个形参。一个是要移动的对象，第二个是移动多长距离，第三个是该元素的`opacity`属性值(通过该属性给元素移动过程添加渐变显示效果)，最后一个是移动到指定距离后会执行哪个函数
> 3. 触发鼠标焦点事件后，调用动画函数，通过给列表目录的`left`属性叫上25px距离为一次执行结果。用定时器不断调用该函数。直到移动至指定距离。
> 4. 移动到指定位置后，点击文档其他位置，调用函数实现回退效果。

js代码：

~~~JavaScript
var btn = document.getElementsByClassName('btn1');
var lis = document.getElementById('liss');
var bg= document.querySelector('.bg-bottom').querySelectorAll('div');
var ul=document.querySelector('.them-body').querySelector('ul');
// 目录移动步长
var bodywidth=(document.body.offsetWidth-300)+(Math.ceil(document.body.offsetWidth*0.02));
function active_l_r(obj, pes, bg, fun, dis) {
	clearInterval(obj.timer);
	var t = 0.046;
	obj.timer = setInterval(function() {
		var seep = 25;
		if (obj.offsetLeft > pes) {
			clearInterval(obj.timer);
			if (fun) {
				fun();
			}
		} else {
			bg += t;
			obj.style.left = obj.offsetLeft + seep + 'px';
			obj.style.opacity = bg;
		}
	},1);
}
// 退步
function active_l_l(obj, pes, bg, fun) {
	clearInterval(obj.timer)
	var t = -0.046;
	obj.timer = setInterval(function() {
		var seep = -20;
		if (obj.offsetLeft < pes) {	
			clearInterval(obj.timer);		
			obj.style.display = 'none';
			if (fun) {
				fun();
			}
		} else {
			bg += t;
			obj.style.left = obj.offsetLeft + seep + 'px';
			obj.style.opacity = bg;
		}
	},1);
}
// 列表移动
lis.style.display = 'block';
var lissep=lis.offsetLeft;
lis.style.display = 'none';
for (var i = 0; i < btn.length; i++) {
	btn[i].addEventListener('mouseenter', function() {
		lis.style.display = 'block';		
		active_l_r(lis, bodywidth, 0, function() {
			document.addEventListener('mouseup', function() {		
				active_l_l(lis, lissep, 1);
			})
		})
	});
}
~~~

> 上面封装了两个函数active_l_r和active_l_l。active_l_r可以实现元素移动到指定位置，active_l_l为回退函数，及点击屏幕其他位置后，重新回退到初始位置。代码结构和active_l_r一致。
>
> 其中bodywidth变量用来获取目录移动步长，结果向上取整。

### 3. 实现结果

[目录区域：](https://s4.ax1x.com/2021/12/18/TVKgIO.png)

​																			[<img src="https://s4.ax1x.com/2021/12/18/TVKgIO.png" alt="TVKgIO.png" style="zoom:25%;" />](https://imgtu.com/i/TVKgIO)

## 二 . 标题区域

> 该区域组成十分简单：由网页主题Boke四个字母和底部的打字机效果组成。

### 1. 实现原理

html部分：

> 大盒子`div`包裹网页标题和显示打字机`p`标签部分组成

~~~HTML
<div class="titles">
	<h1>Boke</h1><br><br><br><br><br><br>
	<p>
		&lt;!--
		<span id="titles-zhushi"></span>
		--&gt;
	</p>
</div>
~~~

css：

> 先设置`h1`标签整体样式。
>
> 接着用给`p`标签区域添加打字机特性。文字输入输出在`span`标签内。

***代码查看链接：github.com/Acidmt/web-Blog.git***

### 2. js实现打字机特性

> 这一部分我本来是想用循环打印字符串，用`slice`方法拼接字符串，长度依次递增，方式实现。但打开页面后效果只能显示一次。而且缺陷较多。所以在折腾大半天后，我还是选择调用js动态库来实现。

js：

~~~JavaScript
<script src="https://cdn.jsdelivr.net/npm/typed.js@2.0.11"></script>			//该部分引用在在html头部
var typed = new Typed("#titles-zhushi", {
	strings: ['I like HTML ❤❤ ❤❤', 'good good study,day day up！！'],
	startDelay: 0,
	typeSpeed: 100,
	backSpeed: 100,
	loop: true,
	showCursor: true,
	shuffle: false
});
~~~

> 所以事实证明别人的永远是最香的。。

### 3. 实现结果

[标题部分：](https://s4.ax1x.com/2021/12/18/TV1a01.png)

​																		[<img src="https://s4.ax1x.com/2021/12/18/TV1a01.png" alt="TV1a01.png" style="zoom:25%;" />](https://imgtu.com/i/TV1a01)

## 三. 轮播页主体区域

> 该区域实现较为复杂，最外层是一个class为`head-top`的`div`盒子。该盒子最上面是头部栏，中间是轮播主页，下边是轮播切换按钮
>
> 最下边是切换主题部分。

### 1. 结构原理

> 头部导航栏用`ul、li`标签，为其设置`float`效果实现布局。
>
> 下边的轮播页切换按钮和背景主题切换按钮，都是用`ul`加css的`display:flex`弹性盒子实现。这样布局简单高效。
>
> 最后的轮播页实现复杂。用无序列表实现滚动布局，这里用了四张轮播页面，==所以轮播页设置为屏幕宽度的4倍，注意`ul`的宽度，及`width=400%`==(因为百分宽度比要看父类节点，所以这里的实际大小要根据布局来定)。之后用定位将`img`的右滑图片按钮，摆放到轮播主页的右中间部分。四张轮播页都要添加这个图片按钮。轮播主页第一页上随便放了点东西。之后三张，实在想不到要放什么了，希望老师见谅 :pray:

[轮播页面主页结构：](https://s4.ax1x.com/2021/12/18/TVtSOg.png)

​												[<img src="https://s4.ax1x.com/2021/12/18/TVtSOg.png" alt="TVtSOg.png" style="zoom: 67%;" />](https://imgtu.com/i/TVtSOg)

html代码：

***代码查看链接：github.com/Acidmt/web-Blog.git***

css:

> 这里注意图层关系。用`z-index`设置每个部分图层大小。
>
> 轮播页面底部切换按钮和主题切换按钮用`display:flex`设置，其属性`text-align`和`align-items`都设置为`center`，这样达到页面垂直居中效果。注意，这里虽说都是按钮，但是按钮属性设置对布局影响很大，所以这里都是用`div`代替按钮。之后为`div`添加点击特效，效果一样。
>
> 轮播页，按钮箭头，通过定位设置。剩下的轮播也内容，`dt、dl`布局。

***代码查看链接：github.com/Acidmt/web-Blog.git***

### 2. js特效

> 这里js特效是整个页面核心。
>
> 由于该部分大部分背景色都为透明的原因。首先第一二部分里的所有元素，都要记录文档在窗口y轴垂直方向滚动的像素。及达到一定数值后将其隐藏。接着头部导航栏，设置该部分结束后取消`position`的`sticky`粘黏属性。
>
> 底部主题切换按钮，通过添加点击事件，点击后获取页面前三个部分的大`div`盒子(最外层父盒子)。之后为其设置相对应的背景色。控制主题切换`div`，通过自定义color索引，为其设置相对于的`background-color`值，随后通过`getAttribute`获取color的值，赋值给对应的三部分的背景色。这里由于时间关系，并没有封装切换颜色函数。所以代码冗长。

~~~JavaScript
// 背景主题隐藏
var h = document.querySelectorAll('h1');
var p = document.querySelectorAll('p');
var bttn = document.querySelectorAll('button');
var img = document.querySelector('.head');
var headimg=document.querySelector('.head-left');
document.addEventListener('scroll', function() {
	if (window.pageYOffset > 600) {
		h[0].innerHTML = '';
		p[0].style.display = "none";
	} else {
		h[0].innerHTML = 'Boke';
		p[0].style.display = "inline-block"	
	}
	window.pageYOffset>600&& window.pageYOffset<1900? bttn[0].style.display = 'none':bttn[0].style.display = 'inline-block';
})
// lis隐藏控制
document.addEventListener('scroll',function(){
	if(window.pageYOffset<700){
		bttn[0].style.display = 'inline-block';
	}else if(window.pageYOffset>600&&window.pageYOffset<1900){
		bttn[0].style.display = 'none'
	}else if(window.pageYOffset>1900&&window.pageYOffset<2500){
		bttn[0].style.display = 'inline-block';
	}else if(window.pageYOffset>3300){
		bttn[0].style.display = 'none'
	}
})
document.addEventListener('scroll', function() {
	if (window.pageYOffset < 910) {
		img.style.opacity = '1';

	} else if(window.pageYOffset>910&&window.pageYOffset<1500){
		img.style.opacity = '0.8';
		
	}else{		
		img.style.opacity = '0.8';
	}
})
//背景更换
var body = document.body;
var color = document.querySelector('.them-bottom-color').querySelectorAll('div');
var them = document.querySelector('.them');
var thembody = document.querySelector('.them-body');
var thembottom = document.querySelector('.them-bottom');
var bottombodytop = document.querySelector('.bottom-body-top');
var bottombody = document.querySelector('.bottom-body');
var bglis = document.querySelector('.bg-lis');
for (var i = 0; i < color.length; i++) {
	color[i].addEventListener('click', function() {
		console.log(i)
		for (var j = 0; j < color.length; j++) {
			// img为head标签
			img.style.backgroundColor = '';
			img.style.backgroundImage = '';
			//bglis为列表目录
			bglis.style.backgroundColor = '';
			bglis.style.backgroundImage = '';
			// them为轮播页主体标签
			them.style.backgroundColor = '';
			them.style.backgroundImage = '';
			//thembody为轮播页主页
			thembody.style.backgroundColor = '';
			thembody.style.backgroundImage = '';
			// thembottom为轮播页底部按钮
			thembottom.style.backgroundColor = '';
			thembottom.style.backgroundImage = '';
			// bottombodytop为间隔节点
			bottombodytop.style.backgroundColor = '';
			bottombodytop.style.backgroundImage = '';
			// bottombody为Boke页面
			bottombody.style.backgroundColor = '';
			bottombody.style.backgroundImage = '';
		}
		// img为head标签
		img.style.backgroundColor = this.getAttribute('color');
		img.style.backgroundImage = this.getAttribute('color');
		// them为轮播页主体标签
		them.style.backgroundColor = this.getAttribute('color');
		them.style.backgroundImage = this.getAttribute('color');
		//thembody为轮播页主页
		thembody.style.backgroundColor = this.getAttribute('color');
		thembody.style.backgroundImage = this.getAttribute('color');
		// thembottom为轮播页底部按钮
		thembottom.style.backgroundColor = this.getAttribute('color');
		thembottom.style.backgroundImage = this.getAttribute('color');
		// bottombodytop为间隔节点
		bottombodytop.style.backgroundColor = this.getAttribute('color');
		bottombodytop.style.backgroundImage = this.getAttribute('color');
		// bottombody为Boke页面
		bottombody.style.backgroundColor = this.getAttribute('color');
		bottombody.style.backgroundImage = this.getAttribute('color');
		//bglis为列表目录
		bglis.style.backgroundColor = this.getAttribute('color');
		bglis.style.backgroundImage = this.getAttribute('color');
	})
~~~

> 轮播页面实现主要由四个步骤：
>
> 1. 封装一个能自增的步长函数`anmmi`，这样轮播页能加快滚动速度，同时可以进行轮播页面左滑动和右滑动。
> 2. 将右侧的滑动按钮和底部轮播页按钮绑定，及两个元素的索引值相等。这样不会出现滑动页面和底部轮播按钮不对应情况。然后设置右侧滑动按钮的点击样式。
> 3. 与上面的列表目录动画实现原理类似，这里有四张滑动页面。在滑动到，最后一张的时候，我们要克隆第一张页面,用`cloneNode`方法进行深克隆。所以之前的`ul`的`width`值要改为500%。克隆第一张一面是为了当滚动页面的索引值为4(从0开始)时，轮播页面的`left`值改为0.这样就可以直接到达第一张轮播页。以此实现轮播页面的循环。
> 4. 通过定时器实现每隔五秒自动点击轮播页右侧的轮播按钮。

实现代码：

~~~JavaScript
window.addEventListener('load', function() {
	var bg = document.querySelector('.bg-bottom').querySelectorAll('div');
	var ul = document.querySelector('.them-body').querySelector('ul');
	var first=ul.children[0].cloneNode(true)
	ul.appendChild(first);
	var MyBoke = document.querySelector('.MyBoke-left');
	var sql = document.querySelector('.them-body');
	var btn_ri = document.querySelector('.them-body').querySelectorAll('button');
	var sql_ri = document.querySelectorAll('.btn-img');
	var btnimg = document.querySelectorAll('.btn-imgs');
	var ulwidth = -MyBoke.offsetWidth;
	var num = 0,
		ind = 0,
		index,timer;
	// 轮播页右侧按钮滚动
	for (var i = 0; i < sql_ri.length; i++) {
		btn_ri[i].addEventListener('click', function() {
			num++;
			num == 4 ? num = 0 : num;
			var ulwidth = -MyBoke.offsetWidth;
			var seep = num * ulwidth;
			anmmi(ul, seep, 0);
			ind++;
			ind == 4 ? ind = 0 : ind;
			for (var j = 0; j < bg.length; j++) {
				bg[j].style.border = "1px solid";
			}
			bg[ind].style.border = "3px solid";
		})
	
	}
	// 轮播栏底部
	for (var i = 0; i < bg.length; i++) {
		bg[i].addEventListener('click', function() {
			for (var j = 0; j < bg.length; j++) {
				bg[j].style.border = "1px solid";
			}
			this.style.border = "3px solid";	
			index = this.getAttribute('index');
			num = index;
			ind=index;
			anmmi(ul, index * ulwidth, 0)
			
		})
	}
	// 轮播页右侧箭头变化
	for (var i = 0; i < sql_ri.length; i++) {
		
		sql_ri[i].addEventListener('mouseleave', function() {
			for (var j = 0; j < sql_ri.length; j++) {
				btnimg[j].src = "images/右箭头.png";
			}
			timer=setInterval(function(){
				for(var i=0;i<sql_ri.length;i++){
					btn_ri[i].click();
				}	
			},3000)
		})
		sql_ri[i].addEventListener('mouseenter', function() {
			for (var j = 0; j < sql_ri.length; j++) {
				btnimg[j].src = "images/向右箭头2.png";
			}
			clearInterval(timer);
		})
	}

	// 轮播页右侧按钮隐藏
	sql.addEventListener('mouseover', function() {
		for (var i = 0; i < sql_ri.length; i++) {
			btn_ri[i].style.opacity = '1';
		}
	})
	sql.addEventListener('mouseout', function() {
		for (var i = 0; i < sql_ri.length; i++) {
			btn_ri[i].style.opacity = '0.2';
		}
	})
	// 设置轮播页自动播放
	timer=setInterval(function(){
		for(var i=0;i<sql_ri.length;i++){
			btn_ri[i].click();
		}	
	},5000)
}
~~~

### 3. 实现结果

[轮播主页：](https://s4.ax1x.com/2021/12/18/TVcfMj.png)

​				[<img src="https://s4.ax1x.com/2021/12/18/TVcfMj.png" alt="TVcfMj.png" style="zoom: 25%;" />](https://imgtu.com/i/TVcfMj)

[轮播页面切换背景主题：](https://s4.ax1x.com/2021/12/18/TVcqWF.png)

​				[<img src="https://s4.ax1x.com/2021/12/18/TVcqWF.png" alt="TVcqWF.png" style="zoom: 25%;" />](https://imgtu.com/i/TVcqWF)

实在找不到好看的颜色了。。

## 四. 笔记展示部分

> 这里实现不难，出去最上面的留白部分。该部分也是大`div`里面套上五个小div的传统结构。
>
> 实际上后来一一想，这里应该用`ul`来布局会更加简单。自上而下，最合理的布局。可惜当时实在没有想到。

### 1. 实现代码

> 这里文字较多。大部分用来介绍笔记。有五个小`div`包裹。
>
> 每个`div`里有一个`p`标签(里面有一个`a`标签进行跳转页面)用来设置标题、`span`标签用来介绍笔记、`a`标签链接笔记
>
> `div`用`hr`标签来换行。

[笔记展示部分结构：](https://s4.ax1x.com/2021/12/19/TVhmPx.png)

​							[<img src="https://s4.ax1x.com/2021/12/19/TVhmPx.png" alt="TVhmPx.png" style="zoom: 50%;" />](https://imgtu.com/i/TVhmPx)

html：

***代码查看链接：github.com/Acidmt/web-Blog.git***

css

> css的实现主要有三点：
>
> 1. 设置每个标签的公有样式
> 2. 调整`div`之间的间距。
> 3. 用伪类设置选中链接之后样式。这里是字体变大。

~~~css
/* 留白 */
.bottom-body-top {
	width: 100%;
	height: 130px;
	z-index: 5;
	margin-bottom: 1px;
	background-size: 100%;
	background-color: rgba(255, 255, 255, 0.8);
}

/*底部栏*/
.bottom-body {
	width: 70%;
	height: 1500px;
	margin: 0 auto;
	background-color: rgba(255, 255, 255, 0.92);
	z-index: 20;
	border-radius: 35px;
	box-shadow: 0 0 20px 10px rgb(220 220 220 / 30%);
}

/* 文字排版 */
.js1 {
	width: 100%;
	height: 10px;
}

/* 公有样式 */
.js {
	width: 100%;
	height: 150px;
	margin: auto 25px;
	padding-bottom: 6.3rem;
	word-wrap: break-word;
	color: #555 !important;
}

.js p {
	font-size: 40px;
	line-height: 80px;
	color: #4a4a4a;
}

.js a:hover {
	text-decoration: underline;
	font-size: 50px;
}

.js .a a {
	font-size: 20px;
}

.js span {
	width: 90%;
	font-size: 20px;
	color: #667279;
	display: block;
}

~~~

### 2. 实现结果

[笔记简介部分：](https://s4.ax1x.com/2021/12/18/TVRwM4.png)

​			[<img src="https://s4.ax1x.com/2021/12/18/TVRwM4.png" alt="TVRwM4.png" style="zoom: 25%;" />](https://imgtu.com/i/TVRwM4)

[这个颜色护眼：](https://s4.ax1x.com/2021/12/18/TVRyIx.png)

​			[<img src="https://s4.ax1x.com/2021/12/18/TVRyIx.png" alt="TVRyIx.png" style="zoom: 25%;" />](https://imgtu.com/i/TVRyIx)

## 五. 页脚部分

> 页脚的上面有一个留白区域
>
> 下边是整个页脚框，页脚分为上下两部分：
>
> 1. 上部分显示留言区域
> 2. 下部分展示个人信息

[页脚结构图：](https://s4.ax1x.com/2021/12/19/TVhXQO.png)

​									[<img src="https://s4.ax1x.com/2021/12/19/TVhXQO.png" alt="TVhXQO.png" style="zoom:50%;" />](https://imgtu.com/i/TVhXQO)

### 1. 代码实现

> 通过`textarea`和`input`绘制留言区域，留言区域左侧放头像图片
>
> 中间用一个`hr`标签隔开
>
> 下边个人信息展示区域用三个`div`布局

html：

***代码查看链接：github.com/Acidmt/web-Blog.git***

css：

> 上边的表单部分出去上左右三个边框，留下底面边框，并为其设置样式。通过定位将svg移动到留言左侧。
>
> 下边的个人介绍部分用`display:flex`将该区域分为三等份，并用`justify-content:center`属性设置文本居中对齐。

***代码查看链接：github.com/Acidmt/web-Blog.git***

### 2. 结果

[页脚部分结果：](https://s4.ax1x.com/2021/12/19/TV5V9x.png)

​						[<img src="https://s4.ax1x.com/2021/12/19/TV5V9x.png" alt="TV5V9x.png" style="zoom: 25%;" />](https://imgtu.com/i/TV5V9x)

# 结语

以上就是我本次的web实践作业了。其中有很多地方可能布局不是很合理，或者有错误的地方。本人对web前端很感兴趣，之前因为参加培训，所以有一个月时间没有上课。其实得感谢期中考试，要不是真担心考不好，我也不会被逼到一个星期学完HTML+CSS。之后发现学习起来真挺好玩的。又花了两个星期学习JavaScript。内容很多，正好这次实训能巩固知识。把之前所学到的和一些书上没有讲到的东西全部用上。结果，大出意料。至少比我想象的要好太多，==至少页面的元素不会乱==。最后祝老师身体健康，心想事成、顺风顺水^^