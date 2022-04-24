# Java脚本开发部分

[toc]

## 一. 外挂分类

> 游戏也就是程序。需要运行在内存中。以直接修改游戏内存中玩家信息为主的外挂。

### 1. 内存级外挂

> 该外挂通常只能用于单机游戏，因为网络游戏中你最多也只能修改自己电脑客户端的内存而已，而最终的关键性数据都是存放于服务器端的内存中或者硬
> 盘上。
> 该类外挂常见的有:游戏金手指
>
> 通常使用C++完成。

### 2. 数据流及网络

> ==以拦截客户端向服务器发送的请求信息，并进行放大或修改。==
> 该外挂通常用于网络游戏中。极大的影响了游戏的平衡。
> 该类外挂常见的有:传奇霸主、变速齿轮、变速精灵、各种脱机外挂等。

[数据外挂示意图：](https://s4.ax1x.com/2022/03/02/b35Emd.png)

​									[![b35Emd.png](https://s4.ax1x.com/2022/03/02/b35Emd.png)](https://imgtu.com/i/b35Emd)

### 3. 脚本级外挂

> 不影响游戏平衡，只是利用程序替代玩家的游戏操作，解放双手。
> 通常又叫做绿色外挂、绿色脚本、绿色挂机脚本、绿色游戏辅助工具等。
> 该类外挂常见的有:按键精灵、简单游等。

## 二. Java语言制作外挂的优缺点

> 为什么使用Java制作(优点)：
>
> 1. 按键精灵，简单游等流行软件的进程名子已经列入各大游戏的黑名单了，在游戏启动的时候，大部分都会进行检查。
> 2. lua(专门制作游戏插件的外挂), vbs(基于VB语法的脚本语言) 等脚本语言编写的挂机程序,因为它们多用于写游戏外挂脚本，威名远播，也很有可能也会被游戏盾察觉。
> 3. java是在jvm (java虚拟机)中运行的，由jvm去通知windows操作系统，从而控制键盘鼠标。而游戏外挂检查软件是无法知道，此jvm虚拟机在内存中到底是起什么样的作用。
>
> 简单来说：使用VBS等编写的外挂是直接操作Windows系统。而使用java是先操作jvm再由jvm通知操作系统来完成操作，而此时游戏盾检测不会因为后台有一个运行的jvm而判定用户使用脚本。
>
> 使用java开发的缺点：
>
> 1. 需要电脑安装jvm和jdk的环境
> 2. 目前暂时无法实现钩子功能。钩子功能： 在游戏界面最小化的时候，按键操作及其它功能只会对该游戏生效，不会影响用户其它操作。

## 三. 基础

### 1. Java中Robot介绍

> 很多时候，我们希望能为我们的JAVA程序实现自动测试，自动演示功能， 或者是其它的一些鼠标和键盘控制的应用。出于这样的目的，自从JDK1.3开始，它就为我们提供了一个用来产生本机输入事件的机器人类-- java.awt.Robot。该类是在java的GUI中封装的。

~~~java
//java.awt.Robot的常用API

//用来将当前的程序(thread)休眠(sleep)若干毫秒(ms)。可用来控制程序的延时。
void delay(int ms)	
    
//取得给定屏幕坐标像素位置的颜色值.用处就不多说了(比如获取游戏血条，当血条变色时执行相对应的操作等).
color getPixelColor(int x,int y)
    
//这两个方法的作用一看便知，用来产生指定键的按键按下与抬起动作,相当于Win32 API 的keyb_ event 函数.可用于程序的自动演示、测试等.
void keyPress(int keycode)
void keyRelease( int keycode)
    
//将鼠标光标移动到指定的屏幕坐标.可用于程序的自动演示、测试等.
void mouseMove(int x, int y)

//下面的三种方法，产生指定鼠标按钮的按下，抬起，及滚轮动作.一样也可用于程序的自动演示、测试等.
void mousePress(int buttons)
void mouseRelease(int buttons )
void mouseWheel( int wheelAmt)
~~~

### 2. 模拟按键

> void keyPress(int keycode)
> void keyRelease( int keycode)
>
> 用来产生指定键的按键按下与抬起动作,相当于Win32 API 的keyb_ event 函数.可用于程序的自动演示、测试等.

~~~java
public static void main(String[] args) throws AWTException {
	//创建 一个java机器人对象
	Robot robot = new Robot();
	//按下k键
	robot.keyPress (KeyEvent.VK_K);	
	//弹起k键
	robot.keyRelease(KeyEvent.VK_K);
}
~~~

> KeyEvent方法用于寻找对应的键盘值

### 3. 延时函数

> void delay(int ms)
> 用来将当前的程序(thread)休眠(sleep)若干毫秒(ms)。可用来控制程序的延时。

~~~java
public static void main(String[] args) throws AWTException {
	//创建 一个java机器人对象
	Robot robot = new Robot();
    robit.delay(5000);
	//按下k键
	robot.keyPress (KeyEvent.VK_K);	
    //按下后0.3秒弹起
    robit.delay(300);
    //弹起k键
	robot.keyRelease(KeyEvent.VK_K);
}
~~~

> `robit.delay(5000);`用于启动程序后延时5秒执行程序。
>
> 我们为了更好默认人按键的动作，同时也需要在按下方法和弹起方法之间设置延迟。

### 4. 使用循环

> 脚本一般都是在死循环里一直执行

~~~java
public static void main(String[] args) throws AWTException {
	//创建 一个java机器人对象
	Robot robot = new Robot();
    robit.delay(5000);
    while(true){        
		//按下k键
		robot.keyPress (KeyEvent.VK_K);	
    	//按下后0.3秒弹起
   		robit.delay(300);
    	//弹起k键
		robot.keyRelease(KeyEvent.VK_K);
        robit.delay(3000);
    } 
}
~~~

> 上面的程序相当于每隔3秒按下"k"键。

### 5. 随机函数作用

> 上面的程序还不能很好的模拟用户的案件。
>
> 因为谁也无法保证，可以每隔3秒准确无误的按下键盘。所以就要使用随机函数来更好模拟案件操作。

~~~java
public static void main(String[] args) throws AWTException {
	//创建 一个java机器人对象
	Robot robot = new Robot();
    //创建随机函数对象
    Random random =new Random();
    robit.delay(5000);
    while(true){
        double V = 0.2 + random.nextDouble()*(0.4-0.2);
        double V2 = 2 + random.nextDouble()*(4-2);
        v*=1000;
		//按下k键
		robot.keyPress (KeyEvent.VK_K);	
    	//按下后0.3秒弹起
   		robit.delay(int(v));
    	//弹起k键
		robot.keyRelease(KeyEvent.VK_K);
        robit.delay(v2);
    } 
}
~~~

> 上面的程序可以起到每隔4到2秒，按下"k"键。

### 6. 鼠标的操作

> void mouseMove(int x，int y)
> 将鼠标光标移动到指定的屏幕坐标.可用于程序的自动演示、测试等.

~~~java
public static void main(String[] args) throws AWTException {
	//创建-个java机器 人对象
	Robot robot = new Robot();
	//延时5秒钟执行
	robot. delay(5000) ;
	//移动鼠标到右下角
	robot . mouseMove(980, 700) ;
}
~~~

### 7. 鼠标的点击

> 下面的三种方法，产生指定鼠标按钮的按下，抬起，及滚轮动作.一样也可用于程序的自动演示、测试等.
> void mousePress(int buttons)
> void mouseRelease(int buttons )
> void mouseWheel( int wheelAmt)

~~~java
public static void main(String[] args) throws AWTException {
	//创建-个java机器 人对象
	Robot robot = new Robot();
    Random random =new Random();
	//延时5秒钟执行
	robot. delay(5000) ;
	//移动鼠标到右下角
	robot . mouseMove(980, 700) ;
    //按下起鼠标
    robot.mousePress (InputEvent.BUTTON1_DOWIN_MASK);
    //弹起鼠标
	robot.mouseRelease(InputEvent . BUTTON1_ ,DOWN_ .MASK) ;
}
~~~

> InputEvent方法用于寻找对应的鼠标值(中键，左键，右键)

# Python脚本开发部分

> 下载pyautogui