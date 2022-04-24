# Auto.js

> 需要先在vscode中开启`Auto.js:Start Sever `。
>
> 之后在安卓模拟器中打开Auto.js连接电脑(==注意：输出的地址要和电脑ID一致，且在同一WiFi下==)
>
> 按F5运行
>
> 注意：调试可以使用`toast(str)`方法

[toc]

## 一. 基于控件的操作

> 基于控件的操作依赖于无障碍服务，因此最好在脚本开头使用`auto()`函数来确保无障碍服务已经启用。

### 1. 基础入门函数

- click(text[, i])

  > **本函数可以模拟app内的点击操作**
  >
  > text {string} 			要点击的文本
  > i {number} 			  如果相同的文本在屏幕中出现多次，则i表示要点击第几个文本, i从0开始计算

  ~~~JavaScript
  launchApp('微信')						//打开微信
  while(!click("扫一扫"));			   //点击扫一扫，如果点击成功则退出循环
  ~~~

- longClick(text[, i]))

  > **本函数可以模拟app内的长按操作**
  >
  > text {string}           要长按的文本
  > i {number}            如果相同的文本在屏幕中出现多次，则i表示要长按第几个文本, i从0开始计算

- scrollUp([i])

  > **本函数可在列表视图下可以进行滑动操作。**如：微博，朋友圈
  >
  > `i` {number} 要滑动的控件序号
  >
  > 找到第i+1个可滑动控件上滑或**左滑**。当参数为0时，为滑动第一个可控插件。
  >
  > 另外不加参数时`scrollUp()`会寻找面积最大的可滑动的控件上滑或左滑，例如微信消息列表等。

- scrollDown([i])

  > `i` {number} 要滑动的控件序号
  >
  > 与`scrollUp([i])`类似，方向相反。

- setText([i, ]text)

  > **当页面有焦点(及有输入框被选中)时可填入文本。**
  >
  > i {number} 表示要输入的为第i + 1个输入框
  > text {string} 要输入的文本
  >
  > 不加参数i则会把所有输入框的文本都置为text。例如`setText("测试")`
  >
  > **注意：这里的输入不能追加，如果文本框中有内容，则会覆盖**

- input([i, ]text)

  > **与`setText([i, ]text)`类似，但该方法可以在文本框内追加文本。**
  >
  > 不加参数i则会把所有输入框的文本追加内容text。例如`input("测试")`

### 2. 控件选择器

> UiSelector即选择器，用于通过各种条件选取屏幕上的控件，再对这些控件进行点击、长按等动作。这里需要先简单介绍一下控件和界面的相关知识。

我们可以通过Auto.js的层次布局查看软件布局，以便于更好获取插件。通常一个控件的布局有如下信息：

[布局分析：](https://s4.ax1x.com/2022/02/14/H67IfS.png)

​						[<img src="https://s4.ax1x.com/2022/02/14/H67IfS.png" alt="H67IfS.png" style="zoom:50%;" />](https://imgtu.com/i/H67IfS)

> 有时候只靠一个属性并不能唯一确定一个控件，这时需要通过属性的组合来完成定位，例如`className("ImageView").depth(10).findOne().click()`，通过链式调用来组合条件。

同时也可以使用布局分析的"生成代码"功能来尝试生成一些选择器代码。接下来的问题便是对选取的控件进行操作包括：

- `click()` 点击。点击一个控件，前提是这个控件的clickable属性为true
- `longClick()` 长按。长按一个控件，前提是这个控件的longClickable属性为true
- `setText()` 设置文本，用于编辑框控件设置文本。
- `scrollForward()`, `scrollBackward()` 滑动。滑动一个控件(列表等), 前提是这个控件的scrollable属性为true
- `exits()` 判断控件是否存在
- `waitFor()` 等待控件出现

#### 2.1 文本选择器

- text(str)

  > **该方法是返回应用内对应的文本控件，但不会去选择这个控件，控件的选择需要用到`Find`方法。**
  >
  > str {string} 控件文本
  >
  > 控件的text(文本)属性是文本控件上的显示的文字，例如微信左上角的"微信"文本。

- textContains(str)

  > **为当前选择器附加控件"text需要包含字符串str"的筛选条件。**
  >
  > 例如QQ动态页和微博发现页上方的"大家都在搜...."的控件可以用`textContains("大家都在搜").findOne()`来获取。

#### 2.2 描述选择器

- desc(str)

  > **描述选择器，有的控件(图片等)没有text信息，则可以用控件描述信息查找**
  >
  > 控件的desc(描述，全称为Content-Description)属性是对一个控件的描述，例如网易云音乐右上角的放大镜图标的描述为搜索。要查看一个控件的描述，同样地可以借助悬浮窗查看。

  ~~~javascript
  desc("空间描述文本").findOne().click()		//点击页面查找到的第一个与描述文本相符合的控件
  ~~~

#### 2.3 ID选择器

- id(str)

  > id选择器，对应一些经常维护的软件比较难用。

#### 2.4 类选择器

- className(str)

  > 类选择器。通常用于链式组合。

#### 2.5 bounds选择器

- bounds(left, top, right, bottom)

  > **该选择器可以精准得定位到一个控件**
  >
  > - `left` {number} 控件左边缘与屏幕左边的距离
  > - `top` {number} 控件上边缘与屏幕上边的距离
  > - `right` {number} 控件右边缘与屏幕左边的距离
  > - `bottom` {number} 控件下边缘与屏幕上边的距离

  ~~~JavaScript
  bounds(951, 67, 1080, 196).clickable().click()				//clickable要为True
  ~~~

### 3. 查找控件

#### 3.1 find查找

- findOne()查找

  > **当前页面查找选择器所指定信息的第一个控件，并返回该控件。**
  >
  > 该方法不会返回NUll，所以会一直进行查询操作。
  >
  > 括号内可以增加时间参数，单位毫秒。此时会指定搜索时间，如果超时还没有找到控件，就会退出寻找。

  ~~~JavaScript
  desc("空间描述文本").findOne().click()		//点击页面查找到的第一个与描述文本相符合的控件	
  desc("空间描述文本").findOne(3000).click()	//控件查找时间为3秒	
  ~~~

- find()查找

  > **将符合选择器条件的所有控件遍历出来**

#### 3.2 判断某个控件是否存在

- UiSelector.exists()

  > **判断屏幕上是否存在控件符合选择器所确定的条件。**
  >
  > 例如要判断某个文本出现就执行某个动作，可以用：

  ~~~JavaScript
  if(text("文本选择").exists()){
      //要支持的动作
  }
  ~~~

#### 3.3 等待某个空间出现

- UiSelector.waitFor()

  > 等待屏幕上出现符合条件的控件；在满足该条件的控件出现之前，该函数会一直保持阻塞。

  ~~~javascript
  textContains("哈哈哈").waitFor();				//等待包含"哈哈哈"的文本控件出现
  ~~~

#### 3.4 过滤条件查找

- UiSelector.filter(f)

  > **当前选择器附加自定义的过滤条件。**
  >
  > f {Function} 过滤函数，参数为UiObject，返回值为boolean

  ~~~javascript
  var uc = className("TextView").filter(function(w){
      return w.text().length == 10;
  });											//找出屏幕上所有文本长度为10的文本控件
  ~~~

### 4. 对象操作

> 对象操作就是在选择器找到控件之后该做什么操作。

#### 4.1 点击对象

- UiObject.click()

  > 返回 {Boolean}
  > **点击该控件，并返回是否点击成功。**
  >
  > 如果该函数返回false，可能是该控件不可点击(clickable为false)，当前界面无法响应该点击等（这种情况下可以使clickCenter()代替）。

  ~~~JavaScript
  desc("空间描述文本").findOne().click()		//点击页面查找到的第一个与描述文本相符合的控件
  ~~~

- UiObject.scrollUp()/scrollDown()/scrollLeft()/scrollRight()

  > **对集合中所有控件进行滑动操作。** 

  ~~~JavaScript
  className("List").findOne().scrollUp()		//列表控件向上翻动一页
  ~~~

#### 4.2 children对象

- children

  > 返回该控件的所有子控件组成的控件集合。可以用于遍历一个控件的子控件，例如：

  ~~~JavaScript
  className("AbsListView").findOne().children()
      .forEach(function(child){
          log(child.className());
      });
  ~~~

- parent()

  > 返回该控件的父控件。如果该控件没有父控件，返回`null`。

- bounds()

  > **返回控件在屏幕上的范围，其值是一个Rect对象。**

  ~~~javascript
  var b = text("Auto.js").findOne().bounds();
  toast("控件在屏幕上的范围为" + b);
  ~~~

  如果一个控件本身无法通过`click()`点击，那么我们可以利用`bounds()`函数获取其坐标，再利用坐标点击。例如：

  ~~~javascript
  var b = desc("打开侧拉菜单").findOne().bounds();
  click(b.centerX(), b.centerY());
  ~~~

### 5. 控件集合的操作方法

> 有的方法会返回一个集合：['控件一'，'控件二'，'控件三']，实际上是一个UiObject的数组，因此可以使用数组的函数和属性，例如使用length属性获取UiCollection的大小，使用forEach函数来遍历UiCollection。

~~~JavaScript
console.show();
className("TextView").find().forEach(function(tv){
    if(tv.text() != ""){
        log(tv.text());
    }
});														//遍历屏幕上所有的文本控件并打印出文本内容
~~~

> 如果想要对该集合的所有元素进行操作，可以直接在集合上调用相应的函数，例如`uc.click()`，该代码会对集合上所有UiObject执行点击操作并返回是否全部点击成功。
>
> 因此，UiCollection具有所有UiObject对控件操作的函数，包括`click()`, `longClick()`, `scrollForward()`等等
>
> 另外`back()`方法可以返回

## 二. 颜色与图片

> 在Auto.js有两种方式表示一个颜色。
>
> 一种是使用一个字符串"#AARRGGBB"或"#RRGGBB"，其中 AA 是Alpha通道(透明度)的值，RR 是R通道(红色)的值，GG 是G通道(绿色)的值，BB是B通道(蓝色)的值。例如"#ffffff"表示白色, "#7F000000"表示半透明的黑色。
>
> 另一种是使用一个16进制的"32位整数" 0xAARRGGBB 来表示一个颜色，例如 `0xFF112233`表示颜色"#112233", `0x11223344`表示颜色"#11223344"。

### 1. 判断颜色是否相似或相等

~~~JavaScript
//返回两个颜色是否相似。
colors. issimilar(num|str，num|str[， thresholdNum, algorithm])
//返回两个颜色是否相等。*注意该函数会忽略Alpha通道的值进行比较。
colors. equals (num|str, num|str)
~~~

### 2. 防止内存泄漏(图片回收机制)

~~~javascript
//读取图片
var img = images.read(". /1. png");
//对图片进行操作
//回收图片
img.recycle();
~~~

例外的是，caputerscreen() 返回的图片不需要回收。

### 3. 读取图片

~~~javascript
//返回Image对象/ nu11
images.read(path)
//返回Image对象/ nu11
images.load(ur1)
//返回Image对象
images.copy(img)
~~~

### 4. Img对象

~~~javascript
Image. getwidth() //返回 以像素为单位图片宽度。
Image. getHeight() //返 回以像素为单位的图片高度。
Image. saveTo(path) //把图片保存到路径path。(如果文件存 在则覆盖) 
Image.pixe1(x,y) //返 回图片image在点(x，y)处的像素的ARGB值。
~~~

### 3. 图片对象的保存方法.

~~~javascript
Image.saveTo(path) //把图片保存到路径path(如果文件存在则覆盖)
images.save(image, path[,format = "png",quality = 100]) //如果文件不存在会被创建; 文件存在会被覆盖。
~~~

> format：图片类型
>
> quality：图片质量，一般越大，质量越好

### 4. 图片的编码转换

~~~javascript
images.fromBase64(base64) //返回img对象
images.toBase64(img[,format = "png", quality = 100]) //返回base64数据
images.fromBytes (bytes) //返回img对象
images.toBytes(img[,format = "png", quality = 100]) //返回字节
~~~

### 5. 封装屏幕小图的函数

> **images.clip(img, x, y, w, h)**
>
> - `img` {Image} 图片
> - `x` {number} 剪切区域的左上角横坐标
> - `y` {number} 剪切区域的左上角纵坐标
> - `w` {number} 剪切区域的宽度
> - `h` {number} 剪切区域的高度
> - 返回 {Image}
>
> 从图片img的位置(x, y)处剪切大小为w * h的区域，并返回该剪切区域的新图片。

示例：

~~~JavaScript
var src = images.read("/sdcard/1.png");
var clip = images.clip(src, 100, 100, 400, 400);
images.save(clip, "/sdcard/clip.png");
~~~

完整示例：

~~~javascript
function getImg(x1 ,y1 , x2 ,y2,path){
    var img = images.capturescreen()
    var imgs = images.clip(img, x1, y1, x2-x1, y2-y1)
    imgs.saveTo(path)
    img.recycle();
}
~~~

### 6. 请求截图权限

> **images.requestScreenCapture([1 andscape] )**
>
> - `landscape` {boolean} 布尔值， 表示将要执行的截屏是否为横屏。如果landscape为false, 则表示竖屏截图; true为横屏截图。
>
> 向系统申请屏幕截图权限，返回是否请求成功。
>
> 第一次使用该函数会弹出截图权限请求，建议选择“总是允许”。（某些系统没有总是允许选项）
>
> 这个函数只是申请截图权限，并不会真正执行截图，真正的截图函数是`captureScreen()`。

示例1：

~~~javascript
//请求截图
if(!requestscreenCapture(){
   toast("请求截图失败");
	exit();
}
~~~

示例2(多线程执行)：

~~~JavaScript
threads.start(function(){
    //在新线程执行的代码
    while(true){
        if(text('立即开始'). find0nce()) {
            text('立即开始'). findOnce().click()
            break;
        }else{
            sleep( 3000)
        }
    }
});

//请求截图
if(!requestScreenCapture()){
   toast("请求截图失败");
	exit();
}
~~~

### 7. 截图功能

> **images.captureScreen()**
>
> 截取当前屏幕并返回一个Image对象。
>
> 该函数不会返回null，两次调用可能返回相同的Image对象。这是因为设备截图的更新需要一定的时间，短时间内（一般来说是16ms）连续调用则会返回同一张截图。
>
> **该函数不需要进行垃圾回收**

~~~javascript
// 请求横屏截图
requestScreenCapture(true);
// 截图
var img = captureScreen();
// 获取在点(100, 100)的颜色值
var color = images.pixel(img, 100, 100);
// 显示该颜色值
toast(colors.toString(color));
~~~

### 8. 获取某点处的颜色

> **images.pixel(image, x, y)**
>
> - `image` {Image} 图片
> - `x` {number} 要获取的像素的横坐标。
> - `y` {number} 要获取的像素的纵坐标。
>
> 返回图片image在点(x, y)处的像素的ARGB值。
>
> 该值的格式为0xAARRGGBB，是一个"32位整数"(虽然JavaScript中并不区分整数类型和其他数值类型)。
>
> 坐标系以图片左上角为原点。以图片左侧边为y轴，上侧边为x轴。

示例：

~~~JavaScript
// 请求横屏截图
requestScreenCapture(true);
// 截图
var img = captureScreen();
// 获取在点(100, 100)的颜色值
var color = images.pixel(img, 100, 100);
// 显示该颜色值
toast(colors.toString(color));
~~~

### 9. 在图片中寻找颜色及Point对象讲解

> **images.findColor(image, color, options)**
>
> - `image` {Image} 图片
> - `color` {number | string} 要寻找的颜色的RGB值。如果是一个整数，则以0xRRGGBB的形式代表RGB值（A通道会被忽略）；如果是字符串，则以"#RRGGBB"代表其RGB值。
> - `options` {Object} 选项
>
> 在图片中寻找颜色color。找到时返回找到的点Point，找不到时返回null。
>
> 选项包括：
>
> - `region` {Array} 找色区域。是一个两个或四个元素的数组。(region[0], region[1])表示找色区域的左上角；region[2]*region[3]表示找色区域的宽高。如果只有region只有两个元素，则找色区域为(region[0], region[1])到图片右下角。如果不指定region选项，则找色区域为整张图片。
> - `threshold` {number} 找色时颜色相似度的临界值，范围为0 ~ 255（越小越相似，0为颜色相等，255为任何颜色都能匹配）。默认为4。threshold和浮点数相似度(0.0~1.0)的换算为 similarity = (255 - threshold) / 255.

### 10. 图片中某个位置是否是特定颜色

> **images.detectsColor(image, color, x, y[, threshold = 16, algorithm = "diff"])**
>
> - `image` {Image} 图片
> - `color` {number | string} 要检测的颜色
> - `x` {number} 要检测的位置横坐标
> - `y` {number} 要检测的位置纵坐标
> - `threshold` {number} 颜色相似度临界值，默认为16。取值范围为0 ~ 255。
> - `algorithm` {string} 颜色匹配算法，包括:
>   - "equal": 相等匹配，只有与给定颜色color完全相等时才匹配。
>   - "diff": 差值匹配。与给定颜色的R、G、B差的绝对值之和小于threshold时匹配。
>   - "rgb": rgb欧拉距离相似度。与给定颜色color的rgb欧拉距离小于等于threshold时匹配。
>   - "rgb+": 加权rgb欧拉距离匹配([LAB Delta E](https://en.wikipedia.org/wiki/Color_difference))。
>   - "hs": hs欧拉距离匹配。hs为HSV空间的色调值。
>
> 返回图片image在位置(x, y)处是否匹配到颜色color。用于检测图片中某个位置是否是特定颜色。

示例：

~~~JavaScript
requestScreenCapture();
// 找到点赞控件
var like = id("ly_feed_like_icon").findOne();
// 获取该控件中点坐标
var x = like.bounds().centerX();
var y = like.bounds().centerY();
// 截图
var img = captureScreen();
// 判断在该坐标的颜色是否为橙红色
if(images.detectsColor(img, "#fed9a8", x, y)){
    // 是的话则已经是点赞过的了，不做任何动作
}else{
    // 否则点击点赞按钮
    like.click();
}
~~~

