# 	一. 输出函数的使用

## 1. print函数

> 可以输出数字，字符，含有运算符的表达式。
>
> 参数：
>
> 1. sep -- 用来间隔多个对象，默认值是一个空格。
> 2. end -- 用来设定以什么结尾。默认值是换行符 \n，我们可以换成其他字符串。
> 3. file -- 要写入的文件对象。
> 4. flush -- 输出是否被缓存通常决定于 file，但如果 flush 关键字参数为 True，流会被强制刷新。

~~~python
print(100) 							#输出：100
print("hello") 						#输出：hello
print(1+2) 							#输出：3
print('hello','world') 				#输出：hello world
print('hello',end='!') 				#输出：hello！
print("www","runoob","com",sep=".") #输出：www.runoob.com	sep设置间隔符
~~~

## 2. open函数

> 将数据输出到指定文件中
>
> 注意:
>
> 1. 指定的盘符一定要存在。
> 2. 必须使用`file=文件赋值名`这样的格式。
> 3. 最后一定要关闭文件读写流。

~~~python
fp=open('D:/text.txt','a+') 		#'a+'表示如果文件不存在就创建，存在的话就再文件里面追加。
print('helloworld',file=fp)  		#与C语言类似
fp.close() 							#关闭文件读写流。
~~~

# 二. 常见的数据类型

> 注意：python中的变量在内存中三部分构成：id(变量所在的内存地址)、type(变量类型)、value(变量值)三部分构成。

## 1. 整数类型

> 用关键字`int`定义，可以表示正数、负数和0。
>
> 正数的不同进制表示方式：
>
> 1. 十进制：默认的进制
> 2. 二进制：0b开头
> 3. 八进制：0o开头
> 4. 十六进制：0x开头

## 2. 浮点类型

> 浮点数由整数部分和小数部分构成。
>
> 注意：浮点数不精确，计算时可能出现小数位数不确定的情况。

解决小数位数不精确的解决方案：

~~~python
from decimal import Decimal
print(Decimal('1.1')+Decimal('2.2'))		#导入模块Decimal来解决。
#输出结果为：3.3
~~~

## 3. 布尔类型

> 布尔类型用来表示真或假。
>
> True为真、False为假
>
> 布尔值可以转化为整数进行运算。(Ture为1，False为0)

## 4. 字符串类型

> 可以使用单引号''、双引号""、三引号'""'或""" """来定义。
>
> 单引号和双引号定义的字符串必须在一行。
>
> 三引号定义的字符串可以分布在连续的多行。

~~~python
str1="""人生苦短，
我用python""" 
str='''人生苦短，
我用python'''；
#上面的结果输出都为：人生苦短，我用python
~~~

## 5. 数据类型转换

> 数据类型转换是为了将不同的数据拼接在一起。

[数据类型转换方法：](https://s4.ax1x.com/2022/01/02/T7SKxg.png)

​								[<img src="https://s4.ax1x.com/2022/01/02/T7SKxg.png" alt="T7SKxg.png" style="zoom:50% " />](https://imgtu.com/i/T7SKxg)

~~~python
name='张三' 
age=20 
print(name+str(age)+'了') 			#输出结果为：张三20了
~~~

## 6. 总结

[本章总结：](https://s4.ax1x.com/2022/01/02/T79egS.png)

​			[<img src="https://s4.ax1x.com/2022/01/02/T79egS.png" alt="T79egS.png" style="zoom: 67% " />](https://imgtu.com/i/T79egS)

# 三. 输入函数input的使用

> 用户输入的类型默认为str类型。需要使用变量来接收。
>
> 用法：
>
> 接收变量=input('输入提示语句')；

~~~python
str=input('请输出语句') 
print(str)						#输出的就是用户输入的内容。
~~~

~~~python
#两数相加
a=int(input('请输入第一个数：')) 
b=int(input('请输入第二个数：')) 
print(a+b) 
~~~

# 四. 运算符的使用

## 1. 算数运算符

> 算数运算符有三类：
>
> 1. 标准算数运算符：+、-、*、//(整除运算，没有小数)、/.....
> 2. 取余运算：%
> 3. 幂运算：**(2`**`3表示2^3^)

[算数运算：](https://s4.ax1x.com/2022/01/02/T7iRrF.png)

​														[<img src="https://s4.ax1x.com/2022/01/02/T7iRrF.png" alt="T7iRrF.png" style="zoom:67% " />](https://imgtu.com/i/T7iRrF)

~~~python
#注意负数
#一正一负的整除，向下取整
print(9//-4)				#结果为-3
print(-9//4)				#结果为-3			
#一正一负取余，要遵循：余数=被除数-除数*商的公式。
print(9%-4)					#结果：-3				9-(-4)*(9//-4)=-3	
print(-9%4)					#结果：3				9-4*(9//-4)=3
~~~

## 2. 赋值运算符

> 执行顺序是从右往左。
>
> 特点：
>
> 1. 支持链式赋值：a=b=c=20
> 2. 支持参数赋值：+=、-=
> 3. 支持系类解包赋值：a,b,c=20,30,40

系类解包赋值交换变量的值：

~~~python
a,b=20,30 
a,b=b,a
print(a,b)					#结果：30 20
~~~

## 3. 比较运算符

> 注意：
>
> 1. 比较运算符的`==`是判断变量的value是否相同
> 2. `is`运算符判断的是变量的id是否相同。
> 3. `is not`与`！=`作用相对应。
> 4. 这里与Java的`==`(判断变量id是否相同)、equals(该方法判断变量内容是否相同)相反。

## 4. 逻辑运算符

|                and                 |                    or                    |             not             |
| :--------------------------------: | :--------------------------------------: | :-------------------------: |
| 当两个运算数都为True时，结果为True | 当两个运算数其中一个为Ture，则结果为Ture | 运算数为false时，结果为Ture |

> 新增的`in`和`not in`
>
> in：运算数是否在变量里边，在则为True，否则为False
>
> not in：运算数是否不在变量里，不在则为Ture，否则为Flash

~~~python
str='hello world' 
print('w' in str) 						#结果：True
print('w' not in str) 					#结果：False
~~~

## 5. 位运算

|                &(按位与)                |               `|`(按位或)               |       <<(左移)        |       >>(右移)        |
| :-------------------------------------: | :-------------------------------------: | :-------------------: | :-------------------: |
| 对应的数位都是1，结果数位才是1，否则为0 | 对应的数位都是0，结果数位才是0，否则为1 | 高位溢出舍去，低位补0 | 低位溢出舍去，高位补0 |

[按位与：](https://s4.ax1x.com/2022/01/02/T7e2Wj.png)

​										[<img src="https://s4.ax1x.com/2022/01/02/T7e2Wj.png" alt="T7e2Wj.png" style="zoom:67% " />](https://imgtu.com/i/T7e2Wj)

[按位或：](https://s4.ax1x.com/2022/01/02/T7ebY4.png)

​										[<img src="https://s4.ax1x.com/2022/01/02/T7ebY4.png" alt="T7ebY4.png" style="zoom:67% " />](https://imgtu.com/i/T7ebY4)

[左移：](https://s4.ax1x.com/2022/01/02/T7mwh4.png)

​										[<img src="https://s4.ax1x.com/2022/01/02/T7mwh4.png" alt="T7mwh4.png" style="zoom:67% " />](https://imgtu.com/i/T7mwh4)

[右移：](https://s4.ax1x.com/2022/01/02/T7mzgs.png)

​										[<img src="https://s4.ax1x.com/2022/01/02/T7mzgs.png" alt="T7mzgs.png" style="zoom:67% " />](https://imgtu.com/i/T7mzgs)

> **左移一位相当于乘2**
>
> **右移一位相当于除2**

~~~python
print(4<<2)				#4向左移两位
print(4>>2)				#4向右移动两位
~~~

# 五. 分支结构

## 1. 选择分支结构

> 语法结构：
>
> if	条件表达式：
>
> ​			条件执行体1
>
> else：
>
> ​			条件执行体2

### 1.1 多分支结构

> 语法结构：
>
> if	条件表达式1：
>
> ​	条件执行体1
>
> elif	条件表达式2：
>
> ​	条件执行体2
>
> elif	条件表达式3：
>
> ​	条件表达式3
>
> else:
>
> ​	条件执行体N+1

~~~python
#成绩评级
score = int(input(' 请输入一个成绩:’))
if score>=90 and score<=100 :					#这里等同于：90<=score<=100:
	print(' A级')
elif score>=80 and score <=89 :
	print(' B级')
elif score>=70 and score<=79 :
	print(' C级’)
elif score>=60 and score <= 69 :
	print(' D级')
elif score>=0 and score < =59 :
	print(' E级’)
else:
	print('对不起，成绩有误，不在成绩的有效范围’)
~~~

### 1.2 嵌套的if

> if 条件表达式1:
> 	if	内层条件表达式: 
> 			内存条件执行体1
> 	else:
> 			内存条件执行体2
> else:
> 		条件执行体

## 2. 条件表达式

> 语法结构：
>
> 执行a	if	条件判断	else	执行b
>
> 如果条件判断位True，则执行语句a，否则执行语句b

~~~python
#判断两个数大小
a = int( input("Input a: ") )
b = int( input("Input b: ") )
print("a大于b") if a>b else ( print("a小于b") if a<b else print("a等于b") )
~~~

## 3. pass语句

> pass语句什么都不做，只是一个占位符，用在语法上需要语句的地方
>
> 1. 什么时候使用：先搭建语法结构，还没想好代码怎么写的时候
> 2. 可以和哪些语句一起使用：if语句的条件执行体、for -in语句的循环体、定义函数时的函数体

[选择结构总结：](https://s4.ax1x.com/2022/01/05/TjxwB8.png)

​			[<img src="https://s4.ax1x.com/2022/01/05/TjxwB8.png" alt="TjxwB8.png" style="zoom: 50% " />](https://imgtu.com/i/TjxwB8)

## 4. range()函数

> 该函数用于生成一个整数数列。其中有三个参数：start、stop、step。
>
> range类型的优点:不管range对象表示的整数序列有多长，所有range对象占用的内存空间都是相同的，因为仅仅需要存储start,stop和step(及三个参数)，只有当用到range对象时，才会去计算序列中的相关元素。
> in与not in用来判断整数序列中是否存在(不存在)指定的整数。

range的三种创建方式：

- 只有一个参数：

  ~~~python
  range(10) 		#表示从0开始到9结束。且步长为1，每次增加1。
  ~~~

- 两个参数：

  ~~~python 
  range(1,10)		#从1开始到10结束(包头不包尾)。步长为1.
  ~~~

- 三个参数：

  ~~~python
  range(1,10,2)	#从1开始到10结束。步长为2(每次增加2)。
  ~~~

## 5. 循环结构

### 5.1 while循环

> 语法结构：
>
> while	条件表达式：
>
> ​			条件执行体(循环体)

~~~python
num=0,i=1 
while i<5:
    num+=i 
    i+=1 
print(num) 
~~~

### 5.2 for in 循环

> in表达从(字符串、序列等)中依次取值，又称为遍历。
>
> for-in遍历的对象必须是可迭代的对象。
>
> for-in语法结构：
>
> for	自定义的变量	in	可迭代的对象：
>
> ​		循环体

~~~python
for item in 'python':				#将'python'中的字符一个一个取出来赋值给item
    print(item) 		
~~~

> 如果没有变量去接受in后面的对象则直接进行循环次数。

~~~python
for _ in range(5):					#结果循环打印五次'hello'
    print(hello)
~~~

~~~python
#判断1000以内的水仙花数
for item in range(100,1000):
    arr1=item%10 								#个位
    arr2=item//10%10 							#十位
    arr3=item//100 								#百位
    if arr3**3+arr2**3+arr1**3==item:
        print(item) 
~~~

~~~python
#打印99乘法表
for i in range(1,10):
    for j in range(1,i+1):
        print(j,'*',i,'=',i*j,end='\t') 
    print() 
~~~

# 六. 列表

> 列表的特点：
>
> - 变量可以存储一个元素，而列表是一个“大容器”可以存储N多个元素，程序可以方便地对这些数据进行整体操作。
> - 列表相当于其它语言中的数组
> - 列表中可以是任何数据类型
> - 可以存储相同的数据
> - 可以根据需要动态分配和回收内存
> - 存储元素从左往右索引从小到大。可以使用负数

## 1. 列表的创建

> - 使用中括号：lis=['hello','world']
> - 调用内置函数list()：lis2=list(['hello','world'])

## 2. 列表的idnex()方法

> 语法格式：
>
> 列表名.index(查找元素)
>
> 特点：
>
> - 如果查询中存在N个相同的元素，则返回第一个的索引值
> - 也可以给两个参数(查找元素,start,stop)，在参数之间查找。遵循包头不包尾原则。

~~~python
lis=['hello','world',100]
print(lis.index('hello',0,2))					#结果：0
~~~

## 3. 列表切片操作

> 与之前的range()方法类似。
>
> 语法结构：
>
> lis[start：stop：step]
>
> 特点：
>
> - 切出的列表是新变量(是复制拷贝)
> - 切片默认从start处元素开始往后根据步长复制元素。

~~~python
lis=[1,2,3,4,5,6,7,8]
print(lis[0:7:2])								#结果：1，3，5
~~~

## 4. 判断元素在列表中是否存在及遍历

> 可以用`in`和`not in`来判断元素是否在列表中
>
> 也可以用`for in`循环遍历列表

~~~python
lis=[1,2,3,4,5,6]
for item in lis:
   print(item)  								#结果：1,2,3,4,5,6
~~~

## 5. 列表的增删改查

### 5.1 增加

|         append()         | extend()                     | insert()                     | 切片                             |
| :----------------------: | ---------------------------- | ---------------------------- | -------------------------------- |
| 在列表的末尾增加一个元素 | 在列表的末尾至少添加一个元素 | 在列表的任意位置添加一个元素 | 在列表的任意位置至少添加一个元素 |

- append添加：

  ~~~python
  lis=[10,20,30,40,50]
  lis.append(100)
  print(lis)									#结果：[10,20,30,40,50,60]
  ~~~

- extend添加多个元素：

  ~~~python
  lis2=['hello','world']
  lis.extend(lis2)
  print(lis)									#结果：[10,20,30,40,50,60,'hello','world'] 
  ~~~

- insert指定位置添加：

  > insert有两个参数：start，添加参数

  ~~~python
  lis.insert(2,'1000')
  print(lis)									#结果：[10,20,1000,30,40,50,60,'hello','world']
  ~~~

- 切片在任意位置添加多个元素

  ~~~python
  lis3=['python','777']
  lis4=lis[3:]
  lis[3:]=lis3
  lis[len(lis):]=lis4
  print(lis)								#结果：[10,20,1000,'python','777',30,40,50,60,'hello','world']
  ~~~

### 5.2 删除

|       remove()       |            pop()             |         切片         | clear()  |   del    |
| :------------------: | :--------------------------: | :------------------: | :------: | :------: |
| 一次只能删除一个元素 | 删除一个指定索引位置上的元素 | 一次至少删除一个元素 | 清空列表 | 删除列表 |
| 重复元素只删除第一个 | 不指定索引，删除列表最后一个 |                      |          |          |

- remove删除元素

  ~~~python
  lis=[10,20,30,40,50,60]
  lis.remove(10)
  print(lis)								#结果：[20,30,40,50,60]
  ~~~

- pop删除指定位置元素

  ~~~python
  lis.pop(1)
  print(lis)								#结果：[20,40,50,60]
  ~~~

- 切片删除至少一个元素

  > 该方法会产生一个新的列表。

  ~~~python
  lis[1:2]=[]								#且走后用空元素替代。
  print(lis)								#结果：[20,50,60]
  ~~~

- clear与del

  ~~~python
  lis.clear()								#将列表清空
  del lis									#将列表删除
  ~~~

### 5.3 修改

> 1. 为指定的索引处元素赋予一个新值
> 2. 为指定的切片赋予一个新值

- 指定位置修改

  ~~~python
  lis=[10,20,30,40,50]
  lis[2]=1000
  print(lis)								#结果：[10,20,1000,40,50]
  ~~~

- 切片赋值

  ~~~python
  lis[1:3]=[300,400,500]
  print(lis)								#结果：[10,300,400,500,40,50]
  ~~~

## 6. 列表的排序

|                            sort()                            |               sorted()               |
| :----------------------------------------------------------: | :----------------------------------: |
| 列表中的所有元素进行从小到大排序，可以指定`reverse=Ture`进行降序排序 | 与sort方法使用相同，但不会改变原列表 |

- sort进行排序

  ~~~python
  lis=[10,300,400,500,40,50]
  lis.sort()								#升序
  lis.sort(reverse=Ture)					#降序
  ~~~

- sorted函数进行排序

  ~~~python
  lis=[10,300,400,500,40,50]
  new_lis=sorted(lis)						#升序
  new_lis=sorted(lis,reverse=Ture)		#降序
  ~~~

## 7. 列表生成式

> 该方法可以快速生成一个列表
>
> 语法结构：
>
> 变量=[i	for	i	in	range(start，stop)]
>
> 用`for in`循环将生成的元素赋值给i，再把i赋值给最前面的i(称为：列表元素的表达式)。

~~~python
lis=[i for i in range(1,10)]
print(lis)									#[1,2,3,4,5,6,7,8,9]
~~~

[总结：](https://s4.ax1x.com/2022/01/06/Tzjq39.png)

​					[<img src="https://s4.ax1x.com/2022/01/06/Tzjq39.png" alt="Tzjq39.png" style="zoom:67% " />](https://imgtu.com/i/Tzjq39)

# 七. 字典

> 与列表一样字典是一个可变数列(可执行增删改查操作)
>
> 里面的数据是以键值对的方式存储。且是一个无序的序列
>
> 字典的实现原理：
>
> - 字典的实现原理与查字典类似，查字典是先根据部首或拼音查找应的页码，Python中的字典是根据key查找value所在的位置
>
> 字典的特点：
>
> - 键不允许重复，值可以允许重复
> - 字典是无序的，不能指定位置插入元素
> - 是动态伸缩的，查询速度快，但会浪费较大的内存，是一种用空间换时间的数据结构

## 1. 字典的创建

> - 使用花括号创建：scores={'张三'：99，'李四'：100}
> - 使用函数dict()创建：dict('张三'：99，'李四'：100)

## 2. 字典元素的获取

> 1. 用键来获取：scores['张三']
> 2. 用get方法获取：scores.get('张三')

- 键获取：

  ~~~python
  scores={'张三':99,'李四':100}
  print(scores['张三'])								#结果：99
  ~~~

- get()方法获取

  ~~~python
  scores={'张三':99,'李四':100}
  print(scores.get('李四'))							#结果：100
  ~~~

  > get()方法可以给定默认值，如果输入键不存在，则返回给定的默认值

  ~~~python
  scores={'张三':99,'李四':100}
  print(scores.get('王麻子',60))						#结果：60
  ~~~

## 3. 字典增删改查及判断

### 3.1 字典中键的判断

> 可以用`in`和`not in`来判断元素是否在列表中
>
> - `in`指定的键在字典中存在则返回Ture：'张三'	in	scores
> - `not in`指定的键在字典中不存在则返回Ture：'张三'    not in    scores

### 3.2 del和clear删除字典元素

- del：

  ~~~python
  scores={'张三':99,'李四':100}
  del scores['张三']								#删除张三的键值对
  print(scores)									 #结果：{'李四':100}
  ~~~

- clear()清空字典：

  ~~~python
  scores={'张三':99,'李四':100}
  scores.clear()									#清空字典
  print(scores)									#结果：{}
  ~~~

### 3.3 字典添加元素

> 可以直接对字典进行添加修改的操作

~~~python
scores={'张三':99,'李四':100}
scores['王麻子']=60
print(scores)										#结果：scores={'张三':99,'李四':100,'王麻子':60}
~~~

### 3.4 字典元素的修改

~~~python
scores={'张三':99,'李四':100,'王麻子':60}
scores['王麻子']=80
print(scores)										#结果：scores={'张三':99,'李四':100,'王麻子':80}
~~~

## 4. 获取字典视图

> 可以用三个方法获取字典试图(字典内的整体元素)
>
> 1. keys()方法：获取字典中所有的key
> 2. values()方法：获取字典中所有的value
> 3. items()方法：获取字典中所有的键值对

- keys()方法：

  ~~~python
  scores={'张三':99,'李四':100,'王麻子':80}
  k=scores.keys()
  print(k)										#结果：dict_keys(['张三','李四','王麻子'])
  #将k转换为列表									
  print(list(k))									#结果：['张三','李四','王麻子']
  ~~~

- values()方法

  ~~~python
  scores={'张三':99,'李四':100,'王麻子':80}
  v=scores.values()
  print(v)										#结果：dict_values([99,100,80])
  #将v值转换为列表
  print(list(v))									#结果：[99,100,80]
  ~~~

- items()方法

  > 该方法类型为元组

  ~~~python
  i=scores.items()
  print(i)									#结果：dict_values([('张三',99),('李四',100),('王麻子',80)])
  ~~~

## 5. 字典元素的遍历

> 方法：for	item	in	scores：
>
> ​					print(item)
>
> 注意：该方法获取字典中的键

~~~python
scores={'张三':99,'李四':100,'王麻子':80}
for item in scores:
    print(item)									#结果：张三，李四，王麻子
~~~

获取列表键和值：

~~~python
for item in scores:
    print(item,score[item])						#结果：张三 99，李四 100，王麻子 80
~~~

## 6. 字典生成式

> 可以使用内置函数zip()生成字典

~~~python
items=['Fruits','Books','Others']
prices=[96,78,85]
i={item:price for item,price in zip(items,prices)}
print(i)										#结果：{'Fruits':96,'Books':78,'Others':85}
~~~

[总结：](https://s4.ax1x.com/2022/01/07/79w6jx.png)

​						[<img src="https://s4.ax1x.com/2022/01/07/79w6jx.png" alt="79w6jx.png" style="zoom: 50% " />](https://imgtu.com/i/79w6jx)

# 八. 元组

> 不可变序列：没有增删改操作。如：字符串、元组
>
> 可变序列：有增删改操作，且修改后对象的地址不会发生改变。如：列表、字典
>
> 元组和列表类似，但使用`()`定义的
>
> 元组使用场景：在多任务同时访问操作元组的时候，所有对象都可以直接获取其中的元素，不用像不可变序列只能一个一个操作，其他的要操作的对像需要排队。这也是不可变序列优势。

## 1. 元组的创建方式

> 元组的创建方式由两种：
>
> 1. 直接用小括号创建(可以不写括号)：t=('hello','world',100)
> 2. 使用内置函数tuple()创建：t=tuple(('hello','world',100))
>
> 只包含一个元组的元素需要用到逗号和小括号：t=(10,)

## 2. 元组的获取

> 列表虽然不能修改元素，但可以通过列表中元素的数据结构类型的方法来修改。
>
> 元组也可以向其他数据结构一样用`for in`遍历。

~~~python
t=(10,[20,30],40)
print(t[0])											#结果：10
print(t[1])											#结果：[20,30]
#可以使用列表的结构方法
t[1].append(100)									
print(t[1])											#结果：[20,30,100]
~~~

# 九. 集合

> 与字典结构类似。是没有value的字典
>
> 特点：
>
> 1. 集合中的元素不允许重复

## 1. 集合创建

> 1. 直接用`{}`创建集合
> 2. 使用内置函数set()创建：s=set(range(10))
> 3. 只能使用set()创建空集合

## 2. 集合的相关操作

### 2.1 集合的判断操作

> 1. 在集合中可以使用`in`和`not in`来进行判断
>
> 2. 可以用`==`和`!=`判断集合是否相等
> 3. 用issubset()方法判断一个集合是否是另一个集合的子集：a.issubset(b)    判断集合a是否是b的子集
> 4. 用issuperset()方法判断一个集合是否是另一个集合的超集：a.issuperset(b)    判断集合a是否是b的超集
> 5. 用isdisjoint()方法判断一个集合是否是另一个集合的交集(有交集为Flase，没有则为Ture)：a.isdist(b)    判断集合a是否是b的交集

[集合：](https://s4.ax1x.com/2022/01/07/79cukV.png)

​																	[<img src="https://s4.ax1x.com/2022/01/07/79cukV.png" alt="79cukV.png" style="zoom:50% " />](https://imgtu.com/i/79cukV)

### 2.2 集合的添加

>  集合添加元素有两种方法：
>
> 1. 调用add()方法，一次添加一个元素
> 2. 调用update()方法，一次至少添加一个元素

~~~python
t={10,20,30}
t.add(100)
print(t)									#结果：{10,20,30,100}
t.update(200,300,400)						#结果：{10,20,30,100,200,300,400}
~~~

### 2.3 集合的删除操作

> 1. 调用remove()方法，一次删除一个指定元素，如果指定的元素不存在抛出KeyError
> 2. 调用discard()方法，一次删除一个指定元素， 如果指定的元素不存在不抛异常
> 3. 调用pop()方法， 一次只删除一个任意元素，该方法不能添加参数
> 4. 调用clear()方法， 清空集合

### 2.4 集合的数学操作

- 集合交集操作(intersection()方法和&)

  ~~~python
  s1={10, 20, 30, 40}
  s2={20, 30, 40, 50, 60}
  print (s1. intersection (s2))			#结果：{40,20,30}
  print(s1 & s2)							#intersection()与&等价，交集操作
  ~~~

- 集合的并集操作(union()方法和|)

  ~~~python
  print(s1.union(s2))						#结果：{40,10,50,20,60,30}
  print (s1|s2)							#union与|等价，并集操作
  ~~~

- 集合的差集操作(两集合相减)

  ~~~python
  print (s1.difference(s2))				#结果：{10}
  print (s1-s2)
  ~~~

- 集合的对称差集

  ~~~python
  print (s1.symmetric_difference(s2) )	#结果：{10,50,60}
  print (s1^s2)
  ~~~

## 3. 集合生成式

> 与列表的生成式类似，将列表生成式的[]修改为{}就是集合生成式
>
> {i	for	i	in	range(1,10)}

~~~python 
s={i for i in range(6)}
print(s)									#结果：{0,1,2,3,4,5}
~~~

[本章总结：](https://s4.ax1x.com/2022/01/07/792GIx.png)

​				[<img src="https://s4.ax1x.com/2022/01/07/792GIx.png" alt="792GIx.png" style="zoom:50% " />](https://imgtu.com/i/792GIx)

# 十. 四种数据结构总结

[总结：](https://s4.ax1x.com/2022/01/07/792mGT.png)

​						[<img src="https://s4.ax1x.com/2022/01/07/792mGT.png" alt="792mGT.png" style="zoom:67% " />](https://imgtu.com/i/792mGT)

# 十一. 字符串的基本操作

> 字符串是不可变序列
>
> 字符串的驻留机制：
>
> - 仅保存一份相同且不可变字符串的方法，不同的值被存放在字符串的驻留池中，Python的驻留机制对相同的字符串只保留一份拷贝，后续创建相同字符串时，不会开辟新空间，而是把该字符串的地址赋给新创建的变量。

字符串只会在如下几种情况驻留(==pycharm在任意情况下都可以进行驻留==)：

> 1. 字符串的长度为1或0时
> 2. 字符串符合用户标识符规则时(字符串由：字母、数字、下划线组成时可以驻留)
> 3. 字符串只在编译时进行驻留，运行时不进行驻留
> 4. 数字在[-5，256]之间的整数数字会驻留。

字符串驻留的优缺点：

> 1. 当需要值相同的字符串时，可以直接从字符串池里拿来使用，避免频繁的创建和销毁，提升效率和节约内存，因此拼接字符串和修改字符串是会比较影响性能的。
> 2. 在需要进行字符串拼接时建议使用str类型的join方法， 而非+ ,因为join()方法是先计算出所有字符中的长度，然后再拷贝，只new-次对象，效率要比"+"效率高。

## 1. 字符串的查询

<table>
    <tr>
        <td>功能</td>
        <td>方法名称</td>
        <td>作用</td>
    </tr>
    <tr>
        <td rowspan='4'>查询方法</td>
        <td>index()</td>
        <td>查找子串substr第一次 出现的位置,如果查找的子串不存在时，则抛出ValueError</td>
    </tr>
    <tr>
        <td>ridex()</td>
        <td>查找子串substr最后一次出现的位置， 如果查找的子串不存在时，则抛出ValueError</td>
    </tr>
    <tr>
        <td>find()</td>
        <td>查找子串substr第一次出现的位置,如果查找的子串不存在时，则返回-1</td>
    </tr>
    <tr>
        <td>rfind()</td>
        <td>查找子串substr最后一次出现的位 置，如果查找的子串不存在时，则返回-1</td>
    </tr>
</table>

- 方法展示

  ~~~python
  substr='hello,hello'
  print(substr.index('l0'))					#结果：3
  print(substr.ridex('lo'))					#结果：9
  print(substr.find('lo'))					#结果：3
  print(substr.rfind('lo'))					#结果：9
  ~~~

  [示意图：](https://s4.ax1x.com/2022/01/09/7k8Ydg.png)
									[<img src="https://s4.ax1x.com/2022/01/09/7k8Ydg.png" alt="7k8Ydg.png" style="zoom:67% " />](https://imgtu.com/i/7k8Ydg)

## 2. 字符串大小写转换常用方法

<table>
    <tr>
        <td>功能</td>
        <td>方法名称</td>
        <td>作用</td>
    </tr>
    <tr>
        <td rowspan='5'>大小写转换</td>
        <td>upper()</td>
        <td>把字符串中所有字符都转成大写字母</td>
    </tr>
    <tr>
        <td>lower()</td>
        <td>把字符串中所有字符都转成小写字母</td>
    </tr>
    <tr>
        <td>swapcase()</td>
        <td>把字符串中所有大写字母转成小写字母，把所有小写字母都转成大写字母</td>
    </tr>
    <tr>
        <td>capitalize()</td>
        <td>把第一个字符转换为大写，把其余字符转换为小写</td>
    </tr>
    <tr>
        <td>title()</td>
        <td>把每个单词的第一个字符转换为大写，把每个单词的剩余字符转换为小写</td>
    </tr>
</table>

> 字符串转换后会生成一个新的对象

## 3. 字符串的对齐操作

<table>
    <tr>
        <td>功能</td>
        <td>方法名称</td>
        <td>作用</td>
    </tr>
    <tr>
        <td rowspan='4'>字符串对齐</td>
        <td>center()</td>
        <td>居中对齐，第1个参数指定宽度，第2个参数指定填充符,第2个参数是可选的，默认是空格，如果设置宽度小于实际宽度则则返回原字符串</td>
    </tr>
    <tr>
        <td>ljust()</td>
        <td>左对齐，第1个参数指定宽度，第2个参数指定填充符，第2个参数是可选的，默认是空格如果设置宽度小于实际宽度则则返回原字符串</td>
    </tr>
    <tr>
        <td>rjust()</td>
        <td>右对齐,第1个参数指定宽度，第2个参数指定填充符,第2个参数是可选的，默认是空格如果设置宽度小于实际宽度则则返回原字符串</td>
    </tr>
    <tr>
        <td>zfill()</td>
        <td>右对齐，左边用0填充，有符号则在符号后填充，该方法只接收一个参数，用于指定字符串的宽度，如果指定的宽度小于等于字符串的长度，返回字符串本身</td>
    </tr>
</table>

- 方法演示

  ~~~python
  s='hello,Python'
  #居中对齐
  print(s.center(20,'*' ))				#居中对齐：****hello,Python****
  #左对齐
  print(s.ljust(20,’*’))					#左对齐：hello,Python********
  #右对齐
  print(s.rhust(20,'*'))					#右对齐：********hello,Python
  #0填充对齐
  print(s.zfill(20))						#0填充：00000000hello,Python
  ~~~

## 4. 字符串的分割

<table>
    <tr>
        <td align='center'>功能</td>
        <td align='center'>方法名称</td>
        <td align='center'>作用</td>
    </tr>
    <tr>
        <td rowspan='6'>字符串的分割</td>
        <td rowspan='3'>split()</td>
        <td>从字符串的左边开始劈分，默认的劈分字符是空格字符串,返回的值都是一个列表</td>
    </tr>
    <tr>
        <td>以通过参数sep指定劈分字符串来分割字符</td>
    </tr>
    <tr>
        <td>通过参数maxsplit指定劈分字符串时的最大劈分次数，在经过最大次劈分之后，剩余的子串会单独做为一部分</td>
    </tr>
    <tr>
        <td rowspan='3'>rsplit()</td>
        <td>从字符串的右边开始旁分，默认的劈分字符是空格字符串，返回的值都是一个列表</td>
    </tr>
    <tr>
        <td>以通过参数sep指定劈分字符串是的劈分符</td>
    </tr>
    <tr>
        <td>通过参数maxsplit指定劈分字符串时的最大劈分次数，在经过最大次劈分之后，剩余的子串会单独做为一部分</td>
    </tr>
</table>

- 代码示例：

  ~~~python
  #split默认参数
  s='hello world python'
  print(s.split())						#结果：['hello','wolrd','python']
  #split用参数sep指定分隔符
  s1='hello|world|python'
  print(s1.split(sep='|'))				#结果：['hello','wolrd','python']
  #split指定分割次数
  print(s1.split(sep='|',maxsplit=1))		#结果：['hello','world|python']
  #rsplit指定分割次数
  print(s1.split(sep='|',maxsplit=1))		#结果：['helloworld','python']
  ~~~

## 5. 判断字符串

<table>
    <tr>
        <td>功能</td>
        <td>方法名称</td>
        <td>作用</td>
    </tr>
    <tr>
        <td rowspan='6'>判断字符串</td>
        <td>isidentifier()</td>
        <td>判断指定的字符串是不是合法的标识符</td>
    </tr>
    <tr>
        <td>isspace()</td>
        <td>判断指定的字符串是否全部由空白字符组成(回车、换行，水平制表符)</td>
    </tr>
    <tr>
        <td>isalpha()</td>
        <td>判断指定的字符串是否全部由字母组成</td>
    </tr>
    <tr>
        <td>isdecimal()</td>
        <td>判断指定字符串是否全部由十进制的数字组成</td>
    </tr>
    <tr>
        <td>isnumeric()</td>
        <td>判断指定的字符串是否全部由数字组成</td>
    </tr>
    <tr>
        <td>isalnum()</td>
        <td>判断指定字符串是否全部由字母和数字组成</td>
    </tr>
</table>

> **判断的时候汉字也属于字母**

## 6. 字符串的替换与合并

|     功能     | 方法名称  | 作用                                                         |
| :----------: | :-------: | :----------------------------------------------------------- |
| 字符串的替换 | replace() | 第1个参数指定被替换的子串，第2个参数指定替换子串的字符串，该方法返回替换后得到的字符串，替换前的字符串不发生变化,调用该方法时可以通过第3个参数指定最大替换次 |
|  字符串合并  |  join()   | 将列表或元组中的字符串合并成一个字符串                       |

- replace方法演示

  ~~~python
  s='hello,world'
  print(s.replace('world','python'))		#结果：hello,python
  #三个参数
  s1='hello,world,world,world,world'
  print(s1.replace('world','python',2))	#结果：hello,python,python,world,world'
  ~~~

- join方法演示

  ~~~python
  lis=['hello','world','python']
  print('|'.join(lis))					#结果：hello|world|python
  print('',join(lis))						#结果：helloworldpython
  ~~~

## 7. 字符串的比较操作

  > - 比较运算符：>、<、…………
  >
  > - 比较规则：首先比较两个字符串中的第一个字符，如果相等则继续比较下一个字符，依次比较下去，直到两个字符串中的字符不相等时，其比较结果就是两个字符串的比较结果，两个字符串中的所有后续字符将不再被比较。
  > - 比较原理：两上字符进行比较时，比较的是其ordinalvalue(原始值ascall),调用内置函数`ord()`可以得到指定字符的ordinalvalue。与内置函数ord对应的是内置函数`chr()`,调用内置函数chr时指定ordinalvalue可以得到其对应的字符。其本质是比较Ascall码。

~~~python
str1='hello'
str2='world'
print(str1>str2)							#结果：Flase
~~~

## 8. 字符串的切片操作

> 字符串是不可变序列，所以没有增删改的操作，其他的与列表的切片类似。
>
> 切片语法：变量[start，stop，step]
>
> step为负数是从后往前截取

~~~python
str='hello,world'
str1=str[:5]
str2=str[6:]
newstr=str1+'!'+str2						#结果：hello！world
~~~

## 9. 格式化字符串

> 格式化字符串由两种方式：
>
> 1. %做占位符
>
>    - %s：字符串
>    - %i或%d：整数
>    - %f：小数
>
> 2. {}做占位符：
>
>    [示例：](https://s4.ax1x.com/2022/01/09/7k48Xt.png)
>
>    ​				[<img src="https://s4.ax1x.com/2022/01/09/7k48Xt.png" alt="7k48Xt.png" style="zoom: 67% " />](https://imgtu.com/i/7k48Xt)

- %做占位符

  ~~~python
  name='张三'
  age=20
  print('我叫%s，今年%d岁了'%(name,age))		#结果：我叫张三，今年20岁了
  ~~~

- {}做占位符

  ~~~python
  name='张三'
  age=20
  print('我叫{0}，今年{1}岁，他也叫{0}'.format(name,age))	#结果：我叫张三，今年20岁，他也叫张三
  ~~~

- 最新方法:f——string

  ~~~python
  name='张三'
  age=20
  print(f'我叫{name},今年{age}岁，他也叫{name}')			#结果：我叫张三，今年20岁，他也叫张三
  ~~~

- 浮点数问题

  ~~~python
  print('%10d' % 99) 						#总宽度为10
  print('%.3f' % 3.1415926) 				#3表示是小数点后三位
  #同时表示宽度和精度
  print('%10.3f' % 3.1415926)				#总宽度为10，3表示保留小数点后三位
  print('{:10.3f}'.format(3.1415926))		#总宽度为10，3表示保留小数点后三位
  ~~~

## 10. 字符串的编码和解码

> 为了有效地解决字符出现乱码问题python提供了编码和解码方法：
>
> 1. encode(encoding='字符集')：编码
> 2. decode(encoding='字符集')：解码
>
> 注意：编码和解码字符集一定要相同

~~~python
str='hello.python'
print(encode(encoding='UFT-8'))				#将字符转为二进制UFT-8(编码)
print(decode(encoding='UFT-8'))				#将字符转为UTF-8(解码)
~~~

[本章总结：](https://s4.ax1x.com/2022/01/09/7kTfVx.png)

​					[<img src="https://s4.ax1x.com/2022/01/09/7kTfVx.png" alt="7kTfVx.png" style="zoom: 33% " />](https://imgtu.com/i/7kTfVx)

## 11. f-String

> f-String可以将将一段信息添加到字符串里

使用格式：

~~~python
f'字符串{字符信息}'
~~~

示例：

~~~python
name='shi'
str=f'hello,{name}'
~~~

运行结果：`hello,shi`

# 十二. 函数

## 1. 函数的创建和调用

> 函数创建语法格式：
>
> def	函数名( [输入参数]) :
> 			函数体
> 			[return xxx]
>
> 函数调用语法格式：
>
> 函数名(参数)

~~~python
#函数的定义
def add(a,b):
    return a+b
#函数的调用
num=add(10,20)
print(num)						#结果：30
#也可以指定形参
num2=add(a=20,b=10)
print(num2)						#结果：30
~~~

## 2. 函数的运行结果对变量影响

>  函数也可以不指定return，不指定默认返回None。
>
> 函数可以返回多个值 ，但返回多个数据时，返回的数据类型为**元组**
>
> 函数运行结果变量值是否会变化取决于变量是否为可变数列(==变量结果收函数执行影响==)和不可变数列(结果不会受函数执行影响)

~~~python
def fun(arr,brr):
    arr=100
    brr.append(10)
a=1
b=[90,100,110]
fun(a,b)
print(a,b)						#结果：1	[90,100,110,10]	
~~~

## 3. 函数参数的定义

> - 个数可变的位置参数
>
>   定义函数时，可能无法事先确定传递的位置实参的个数时，使用可变的位置参数，一个函数内只能定义一个。
>
>   - 语法：使用`*`号定义一个位置可变的形参
>   - 结果返回一个元组
>
> - 个数可变的关键字形参
>
>   定义函数时，无法实现确定传递的关键字实参的个数时，使用可变的关键字形参，一个函数内只能定义一个。
>
>   - 语法：使用`**`定义个数可变的关键字形参
>   - 结果返回一个字典

- 个数可变的位置参数：

  ~~~python
  def fun(*arges):
      print(arges)
  fun(10)							#结果：(10,)
  fun(10,20,30)					#结果：(10,20,30)
  ~~~

- 个数可变的关键字形参

  ~~~python
  def fun(**arges):
      print(arges)
  fun(a=10)							#结果：{'a':10}
  fun(a=10,b=20,c=30)					#结果：('a':10,'b':20,'c':30)
  ~~~

> 注意：在一个函数的定义过程中，既有个数可变的关键字形参，也有个数可变的位置形参，要求，个数可变的位置形参，放在个数可变的关键字形参之前

~~~python
def fun(*arges,**brges)
~~~

- 参数传入函数

  > 如果想将参数传入函数：
  >
  > 1. 列表类的只有`value`的可以使用可变位置传入参数，及参数前加`*`
  > 2. 字典类的由键值对的，需要用可变的关键字来传入参数，及参数前加`**`

  ~~~python
  def num(a,b,c):
      print(a)
      print(b)    
      print(c)
  lis=[10,20,30]
  fun(*lis)							#结果：10，20，30
  dic={'a':100,'b':200,'c':300}				
  fun(**dic)							#结果：100，200，300
  ~~~

## 4. 变量的作用域

> - 全局变量：定义在函数外的变量，特点是 在代码的任意位置都可以访问
> - 局部变量：定义在函数体内部的变量，特点是只能在函数内部访问，其他位置不能访问。也可以用`global`将局部变量转换为全局变量

~~~python
def fun():
    global age
    age=20
    print(age)							#结果：20
#函数外也可以访问输出
print(age)								#结果：20
~~~

## 5. 函数的递归

> 优点：思路简单，代码清晰。
>
> 缺点：占用内存多，效率低下。

[计算阶乘思路：](https://s4.ax1x.com/2022/01/10/7VDxLF.png)

​																			[<img src="https://s4.ax1x.com/2022/01/10/7VDxLF.png" alt="7VDxLF.png" style="zoom:50% " />](https://imgtu.com/i/7VDxLF)

~~~python
def fun(n):
    if n==1:
        return 1
    else:
        return n*fun(n-1)
prit(fun(6))							#结果：720
~~~

[本章总结：](https://s4.ax1x.com/2022/01/10/7VcZ9A.png)

​						[<img src="https://s4.ax1x.com/2022/01/10/7VcZ9A.png" alt="7VcZ9A.png" style="zoom:50% " />](https://imgtu.com/i/7VcZ9A)

# 十二. 异常处理机制

## 1. try{}except{}结构

> 结构：
>
> try:
>
> ​		可能出现异常的代码体
>
> except	异常类型：
>
> ​		出错后的操作	
>
> **可以有多个except**

## 2. try{}except{}else{}结构

> - 如果try块中没有拋出异常，则执行else块， 如果try中抛出异常，则执行except块。

~~~python
try:
	n1=int(input('请输入一个整数:'))
	n2=int (input('请输入另一个整数:'))
	result=n1/n2
except BaseException as e:					#as：用于起别名
	print('出错了,',e)						  #出错结果：出错了,invalid literal for int() with base 10:'a'
else:
	print('结果为:’,result)
~~~

## 3. try{}except{}else{}finally结构

> - finally块无论是否发生异常都会被执行，常用来释放try块中申请的资源(文件关闭，数据库链接等)

## 4. 常见异常类型

|     异常类型      |            描述             |
| :---------------: | :-------------------------: |
| ZeroDivisionError | 除(或取模)零(所有数据类型)  |
|    IndexError     |   序列中没有此索引(index)   |
|     KeyError      |      映射中没有这个键       |
|     NameError     | 未声明/初始化对象(没有属性) |
|    SyntaxError    |       Python 语法错误       |
|    ValueError     |       传入无效的参数        |

# 十三. 类与对象

> 类：类是多个类似事物组成的群体的统称。是一个模板。能够帮助我们快速理解和判断事物的性质。一个程序中多个类之间要保留两行空格。
>
> 对象：类的实例化。对象是一组相互关联的变量和函数。这些变量通常称为对象的属性，函数称为对象的行为。在python中一切皆对象。
>
> 类属性：类中方法外的变量称为类属性，被该类的所有对象所共享。
> 类方法：使用@classmethod修饰的方法， 使用类名直接访问的方法。
> 静态方法：使用@staticmethod修饰的主法，使用类名直接访问的方法。

## 1. 类的创建

> 语法格式：
>
> class	student：
>
> ​			def	方法1(self，参数列表)
>
> ​					pass
>
> ​			def	方法2(self，参数列表)
>
> ​					pass
>
> **注意：哪一个对象调用的方法，self就是哪一个方法的引用。**
>
> 类的组成：
>
> 1. 类属性
> 2. 实例方法(在类之外定义的为函数，在类之内定义的叫函数)
> 3. 静态方法
> 4. 类方法

~~~python
class student:
    pace='所在地区'					   #类的属性
    def __init__(self,name,age):	 #self.name称为实体属性，进行了一个赋值的操作，将局部变量的name的值赋给实体属性
        self.name=name
        self.age=age				
	#实例方法
    def eat(self):					 
        print('吃饭')   
	#静态方法
    @staticmethod
    def method():
        print('静态方法')
	#类方法
	@classmethod
    def test(cls):
        print('类方法')
~~~

> 类名有一个或多个单词组成，首字母尽量大写，其余小写。

## 2. 对象的创建

> 语法：实例名=类名()

~~~python
stu1=Student('张三',20)
stu.eat()								#结果：吃饭
#等同于一下代码：
Student.eat(stu1)						#结果：吃饭
~~~

## 3. 初始化方法

> 当使用类名创建对象时，会自动执行一下操做：
>
> 1. 为对象在内存中分配空间--创建对象
> 2. 为对象的属性设置初始值--初始化方法(`init `)
>
> 这个初始化方法就是`__init__`方法，`__init__`是对象的内置方法，这个方法是专门用来定义一个类，具有哪些属性的方法。会在对象实例化时直接执行。类似于Java构造函数。

~~~python
class Cat:
def __init__ (self):
	print("这是一个初始化方法")
#使用类名()创建对象的时候，会自动调用初始化方法init|
tom = Cat()										#结果：这是一个初始化方法 
~~~

- 初始化方法经常使用类型

  ~~~python
  class cat:
      def __init__(self,name):
          self.name=name
      def eat(self):
          pritn('%s 爱吃鱼' % self.name)
  tom=cat('Tom')
  tom.eat()									#结果：Tom 爱吃鱼
  ~~~


## 4. `__del__`方法

> 对象调用后，在**对象内存销毁之前**自动进行调用
>
> 该方法是对象生命周期中最后一个调用的方法。

~~~python
class cat:
	def __init__(self,name):
    	self.name=name
	def __del__(self):
    	print('%s猫'% self.name)
tom=cat('Tom')									#结果：Tom猫
~~~

## 5. `__str__`方法

> 该方法必须返回一个字符串。
>
> 如果在开发中，希望使用`print`输出对象变量时，能够打印自定义的内容，就可以利用`__str__`这个内置方法了。

~~~python
class cat:
    def __init__(self,name):
        self.name=name
    def __str__(self):
        return '我是小猫：%s'%self.name
tom=cat('Tom')								
print(tom)										#结果：我是小猫：Tom
~~~

## 6. 私有属性和私有方法

> - 在实际开发中，对象的某些属性或方法可能只希望在对象的内部被使用，而不希望在外部被访问到
> - 私有属性就是对象不希望公开的属性
>   - 私有方法就是对象不希望公开的方法
>   - **私有属性和私有方法可以在类的内部被访问，而不能在外界访问**
>
> 定义方法：
>
> 在定义属性或方法时，在属性名或者方法名前增加两个下划线，定义的就是私有属性或方法

~~~python
class Person:
    def __init__(self,name):
        self.name =name 
		self.__age =18
    def sercet(self):
        print('%s的年龄%d岁'%(self.name,self.__age))
xiaofang=Person('小芳')
print(xiaofang.__age)						#结果：输出错误
xiaofang.sercet()							#结果：小芳的年龄18岁
~~~

> 但在python中并没有绝对的私有属性和私有方法，可以通过特殊方法在类的外部查看私有属性和方法。
>
> 语法：
>
> `_类名 方法名字/属性名字`

~~~python
print(_Person__age)							#结果：18
~~~

## 7. 类的属性

> 1. 类属性就是给类对象中定义的属性
> 2. 通常用来记录与这个类相关的特征
> 3. 类属性不会用于记录具体对象的特征
>
> 类属性的使用语法：
>
> 类名.属性名

~~~python
class Tools:
    cout=0
    def __init__(self):
        Tools.cout+=1
tools1=Tools()
print(Tools.cout)							#结果：1
tools2=Tools()
print(Tools.cout)							#结果：2
~~~

# ==十四. 封装==

> 1. 封装是面向对象编程的一大特点
> 2. 面向对象编程的第一步——将属性和方法封装到一个抽象的类中
> 3. 外界使用类创建对象，然后让对象调用方法
> 4. 对象方法的细节都被封装在类的内部

~~~python
#封装开始----------------------------------------------------
class person:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __str__(self):
        return '我叫%s，今年%d岁了'%(sel.name,self.age)
    def run(self):
        print('%s'在跑步)
#封装结束----------------------------------------------------
#创建对象peopol
peopol=person('小明',20)
peopol.run()								#结果：我叫小明，今年20岁了。
											#	  小明在跑步
~~~

- 家具练习

  ~~~python
  class HouseItem:
      def __init__(self, name, area):
          self.name = name
          self.area = area
  
      def __str__(self):
          return '[%s] 占地 %.2f' % (self.name, self.area)
  
  
  class House:
      def __init__(self,house_type,area):
          self.house_type = house_type
          self.area = area
          # 剩余面积 
          self.free_area = area
          # 家具名称
          self.item_list = []
  
      def __str__(self):
          return ("户型: %s\n总面积:%.2f[剩余:%.2f]\n家具:%s" %
                  (self.house_type, self.area, self.free_area, self.item_list))
  
      def add_item(self, item):
          # 1.判断家具的面积
          if item.area > self.free_area:
              print("%s的面积太大了，无法添加" % item.name)
          self.item_list.append(item.name)
          # 3.计算剩余面积
          self.free_area -= item.area
  
  
  # 创建家具对象
  bed = HouseItem("席梦思", 20)
  chest = HouseItem("衣柜", 2)
  table = HouseItem("餐桌", 1.5)
  # 创建房子对象
  my_home = House("两室一厅", 60)
  my_home.add_item(bed)
  my_home.add_item(chest)
  my_home.add_item(table)
  print(my_home)
  ~~~

  [运行结果：](https://s4.ax1x.com/2022/01/12/7KUoRI.png)

  ​												[<img src="https://s4.ax1x.com/2022/01/12/7KUoRI.png" alt="7KUoRI.png" style="zoom:67%;" />](https://imgtu.com/i/7KUoRI)

# ==十五. 继承==

  > 继承特性：
  >
  > - 继承实现代码的重用，相同的代码不需要重复的编写
  > - 继承具有传递性(子类不仅继承父类，还继承爷爷类)

  ## 1. 单继承

> 继承概念：子类拥有父类的所有方法和属性。
>
> 语法：
>
> class	要继承的类名`(被继承的类名)`

~~~python
class Animal:
    def eat(self):
        print('吃')
    def drink(self):
        print('喝')

        
class Dog(Animal):
    def sleep(self):
        print('睡觉')
dog=Dog()
dog.eat()
dog.drink()
dog.sleep()
#结果：吃 喝 睡
~~~

  ## 2. 方法重写

> 重写使用场景：
>
> - 需要覆盖父类的方法
> - 对父类的方法需要进行扩展
> - **当父类的方法实现不能满足子类需求时，可以对方法进行重写(override)**

~~~python
class Animal:
    def eat(self):
        print('吃')
    def drink(self):
        print('喝')

        
class Dog(Animal):
    def sleep(self):
        print('睡觉')
        

class TianGou(Dog):
    def sleep(self):
        print('不用睡觉')
tiangou=TianGou()
tiangou.sleep()
#结果:
	#不用睡觉
~~~

## 3. `super`调用父类方法

> 使用场景：
>
> - 如果在开发中，子类的方法实现中包含父类的方法实现
> - 父类原本封装的方法实现是子类方法的一部分
> - 在重写父类方法时，调用在父类中封装的方法实现
>
> 使用步骤：
>
> 1. 在子类中重写父类的方法
> 2. 在需要的位置使用`super()`父类方法来调用父类方法的执行
> 3. 代码其他的位置针对子类的需求，编写子类特有的代码实现
>
> 使用语法：
>
> `super().父类名`

~~~python
class Animal:
    def eat(self):
        print('吃')
    def drink(self):
        print('喝')

        
class Dog(Animal):
    def sleep(self):
        print('睡觉')
        

class TianGou(Dog):
    def sleep(self):
        print('不用睡觉')
        super().sleep()
tiangou=TianGou()
tiangou.sleep()
#结果:
	#不用睡觉
    #睡觉 
~~~

## 4. 多继承

> 多继承特点：
>
> - 子类可以拥有多个父类，并且具有所有父类的属性和方法
> - 多继承可以让子类对象，同时具有多个父类的属性和方法
>
> 语法结构：
>
> class	子类名(父类名1,父类名2...)
> 			pass 

- 多继承注意事项

  > 如果不同的父类中存在同名的方法，子类对象在调用方法时，会调用哪-个父类中的方法呢?这种时候应该避免使用多继承

  ~~~python
  class A:
  	def test(self):
  		print("A --- test方法")
  	def demo(self) :
  		print("A --- demo方法")
  
          
  class B:
  	def test(self) :
  		print("B --- test方法")
  	def demo(self):
  		print("B --- demo 方法")
  
  
  class C(A,B):
      pass
  c=C()
  c.test()
  c.demo()
  #运行结果:
  		# A --- test方法.
      	# B --- demo方法
  
  ~~~

 注意：`__mro__`方法可以用于确定对象调用方法顺序：print(C.`__mro__`)

# ==十六. 多态==

> 不同的子类对象调用相同的父类方法，产生不同的执行结果
>
> 多态特点：
>
> - 多态可以增加代码的灵活度
> - 以继承和重写父类方法为前提
> - 是调用方法的技巧，不会影响到类的内部设计

~~~python
class Dog:
    def __init__(self,name):
        self.name=name
    def game(self):
        print('%s快乐的玩耍' % self.name)


class xiaotianquan(Dog):
    def game(self):
        print('%s 飞到天山去玩耍'%self.name)


class Person:
    def __init__(self,name):
        self.name=name
	def game_with_dog(self,dog):
        print('%s 和 %s快乐的玩耍'%(self.name,dog.name))
        dog.game()
#情况一：
wangcai=Dog('旺财')
#情况二：
wangcai=xiaotianquan('飞天旺财')
xiaoming=Person('小明')
xiaoming.game_with_dog(wangcai)
~~~

# 十七. 类方法和静态方法

## 1. 类方法

> 类方法就是针对类对象定义的方法，在类方法内部可以直接访问类属性或者调用其他的类方法。
>
> 语法：
>
> ~~~python
> @classmethod
> def 类方法名(cls):
> 	pass
> ~~~
>
> 类方法需要用修饰器@classmethod 来标识，告诉解释器这是一个类方法。
>
> 类方法的第一个参数应该是：cls
>
> - 由哪一个类调用的方法，方法内的cls就是哪一个类的引用
> - 这个参数和实例方法的第一个参数和self类似
> - 提示使用其他名称也可以，不过习惯使用cls
>
> 在方法内部
>
> - 可以使用cls，访问类的属性
> - 也可通过cls，调用其他类的方法
> - 该方法可以不创建实例对象直接用类调用。

~~~python
class Tools:
    cout=0
    @classmethod
   	def test(cls):
        print('使用了%d次该类' % cls.cout)
    def __init__(self):
        Tools.cout+=1
tools1=Tools()
tools1.test()								#结果：使用了1次该方法
tools2=Tools()
tools2=test()								#结果：使用了2次该方法
~~~

## 2. 静态方法

> 静态方法使用场景：
>
> 在开发时，如果需要在类中封装一个方法， 那么这个满足方法:
>
> - **既不用访问实例属性**或者调用实例方法
> - **也不需要访问类属性**或者调用类方法
>
> ~~~python
> @staticmethod
> def 静态方法名():
> 	pass
> ~~~
>
> 该方法可以不创建实例对象直接用类调用。`类名.静态方法名`

## 3. 实例方法

> 实例方法是类的默认方法。参数为self
>
> 不用@修饰。

- 综合演练

  ~~~python
  class Game:
      score=0
      @staticmethod
      def show_help():
          print('游戏帮助信息')
  	@classmethod
      def show_top_score(cls):
          print('历史记录%d'% score)	
  	def start_ game(self):
  		print("%S开始游戏啦..." % self. player_ name)
  #显示游戏帮助
  Game. show_help( )					#结果：游戏帮助信息
  # 2.查看历史最高分
  Game. show_top_score( )				#结果：历史记录0分
  # 3.创建游戏对象
  game = Game ("小明")
  game . start_ game( )				#小明开始游戏了...
  ~~~

- 总结

  > - 实例方法----------方法内部需要访问实例属性又需要访问类属性：实例方法内部可以使用`类名.属性名`访问类属性
  > - 类方法------------方法内部只需要访问类属性或只需要调用类方法
  > - 静态方法---------方法内部，不需要访问实例属性和类属性

# 十八. 单例设计模式

> 设计模式：
>
> 使用设计模式是为了可重用代码、让代码更容易被他人理解、保证代码可靠性，是前人根据工作经验总结的解决问题套路。
>
> 单例设计模式：
>
> - 目的：让类创建的对象，在系统中只有唯一的一个实例
> - 每一次执行`类名()`返回的对象，内存地址是相同的

## 1. `__new__`方法

> 该方法主要有两种作用：
>
> 1. 在内存中为对象分配空间
> 2. 返回对象的引用。
>
> 注意：new方法负责给对象分配空间，init方法负责初始化对象

~~~python
class MusicPlayer(object):
	def __new__(cls, *args, **kwargs):
		# 1.创建对象时，new方法会被自动调用
		print("创建对象，分配空间")
		# 2.为对象分配空间
		instance = super().new(cls)
		# 3.返回对象的引用
		return instance
	def_ init_ (self):
		print ("播放器初始化")
#创建播放器对象
player = MusicPlayer()
print (player)
~~~

- 使用单例让多个对象的地址相同

  ~~~python
  class MusicPlayer(object):
      instance = None
      def  __new__(cls,*args,**kwargs):
          if cls.instance is None:
          	cls.instance=super().__new__(cls)
  		return cls.instance
  play1=MusicPlayer()
  play2=MusicPlayer()
  print(play1)
  print(play2)
  #结果；
  	#两个对象内存地址相同
  ~~~

# 十九. 模块

> 模块是程序架构的核心概念
>
> - 模块就好比是工具包，要想使用这个工具包中的工具，就需要导入import这个模块
> - 每一个以扩展名py结尾的Python 源代码文件都是一个模块
> - 在模块中定义的全局变量、函数、类都是模块能够提供给外界直接使用的工具
>
> 模块使用场景：
>
> 主要将一个封装完的函数文件，导入到现在的项目中
>
> 使用语法：
>
> ~~~python
> import 模块1
> ~~~

`分割线.py`文件

~~~python
def Print_line(char,times):
    print(char*times)
def Print_lines(char,times):
    rows=0
    while row<5:
        print_line(char,times)
        row+=1
~~~

`模块介绍.py`文件

~~~python
#导入模块
import 分割线
#使用导入模块的方法
分割线.print_line('*',10)					#结果：**********
~~~

> 注意：文件名即是模块名，所以要遵守用户标识符规则。

## 1. 导入别名

> 如果模块的名字太长，可以使用`as`指定模块的名称，以方便在代码中的使用
>
> 语法：
>
> ~~~python
> import 模块名 as 别名
> ~~~

~~~python
#导入模块
import 分割线 as Test
#使用导入模块的方法
Test.print_line('*',10)					#结果：**********
~~~

## 2. `from import`局部导入

> 如果想从**某一模块中导入部分工具**，可以使用`from import`的形式导入。
>
> 语法：
>
> ~~~python
> from 模块名1 import 工具名
> ~~~
>
> 导入之后可以直接通过`工具名.`的形式进行访问。

~~~python
from 分割线 import Print_line
print(Print_line('*',10))				#结果：**********
~~~

`*`代表导入该模块所有工具方法

~~~python
from 分割线 import *
print(Print_line('*',10))				#结果：**********
~~~

> 如果导入多个文件后发现工具名相同，可以用起别名的方式解决。

## 3. `__name__`解决导入自动执行

> 注意：在导入文件时，文件中所有没有任何缩进的代码都会被执行一遍!
>
> 大部分情况下我们有的代码仅在模块内使用，而被导入到其他文件中不需要执行
>
> `__name__`属性 可以做到，测试模块的代码只在测试情况下被运行，而在被导入时不会被执行。

~~~python
if __name__ == "__main__":
	print(__name__)						#文件被导入时，if下面的代码不会被执行
	print ("小明开发的模块")
~~~

> `__name__` 是 Python的一个内置属性，其只会记录一个字符串：
>
> - 如果是被其他文件导入的，`__name__`记录的 就是 模块名
> - 如果是当前执行的程序`__name__` 记录的是`__main__`

## 4. 包(Package)

> 概念：
>
> - 包是一个包含多个模块的特殊目录
> - 目录下有一个特殊的文件`__init__.py`
> - 包名的命名方式和变量名规则一致。
>
> 可以使用`import 包名`的方式一次性导入包中的所有模块。
>
> 再项目文件中使用包，需要先将`__init__.py`文件中写入`from . import 工具名`才可以再模块中正常引用。
>
> 使用方式是`包名.模块名.方法名`。

`__init__.py`

~~~python
from . import 函数A							# . 表示当前文件夹下的所有文件
~~~

`项目文件`

~~~python
from 包名										# 导入后就可以正常使用封装的函数了
包名.模块名.方法名
~~~

## 5. 使用pip安装第三方模块

> 第三方模块通常是指由知名的第三方团队开发的并且被程序员广泛使用的Python 包/模块
>
> `pip`是一个现代通用的`python`包管理工具。其提供了对Python包的查找、下载、安装和卸载的功能。

安装流程

- Windows进入：`Lib\site-packages`文件夹下(这里是第三方模块库的安装目录)打开CMD输入：

  ~~~python
  pip install 模块名
  ~~~

- 安装完成后输出`python`，然后输入：`import 模块名`。成功安装后此时会显示版本号

  [成功安装：](https://s4.ax1x.com/2022/01/19/7srdVH.png)

  ​                        [<img src="https://s4.ax1x.com/2022/01/19/7srdVH.png" alt="7srdVH.png" style="zoom: 40%;" />](https://imgtu.com/i/7srdVH)

# 二十. 文件操作

> 操作文件需要三个步骤：
>
> 1. 打卡文件
> 2. 读写文件：读：将文件内容读到内存中。写：将内存中的数据写入文件中
> 3. 关闭文件

## 1. 文件操作函数

> 在python中操作文件需要1个函数和三个方法

| 函数/方法 |              说明              |
| :-------: | :----------------------------: |
| open函数  | 打开文件，并且返回文件操作对象 |
| read方法  |      将文件内容读取到内存      |
| write方法 |       将指定内容写入文件       |
| close方法 |            关闭文件            |

## 2. red方法读取文件

> open函数的第一个参数是要打开的文件名(文件名区分大小写)
>
> - 如果文件存在，返回文件操作对象
> - 如果文件不存在，会抛出异常
>
> read方法可以一次性读入并返回文件的所有内容(close方法负责关闭文件）

~~~python
file=open('aaa.txt')							#打开aaa.txt文件
text=file.red()									#读取aaa.txt文件中的内容并赋值给text变量
print(text)										#结果：hello,world
file.close										#一定要关闭文件读写
~~~

> 注意：read方法关闭后，会把**文件指针移动到文件末尾**
>
> 文件指针标记从哪个位置开始读取数据
> 第一次打开文件时，通常文件指针会指向文件的开始位置当执行了read方法后，文件指针会移动到读取内容的末尾。
>
> 此时再对文件进行`read`方法读取时，输出的结果为空。

## 3. 打开文件方式

> `opne`函数默认以只读的方式打开文件。想要以别的方式打开文件语法如下：
>
> ~~~python
> file=('文件名','访问方式')
> ~~~

| 访问方式 |                             说明                             |
| :------: | :----------------------------------------------------------: |
|    r     | 以只读方式打开文件。文件的指针将会放在文件的开头，这是默认模式。如果文件不存在，抛出异常 |
|    w     | 以只写方式打开文件。如果文件存在会被覆盖。如果文件不存在，创建新文件 |
|    a     | 以追加方式打开文件。如果该文件已存在，文件指针将会放在文件的结尾。如果文件不存在，创建新文件进行写入 |
|    r+    | 以读写方式打开文件。文件的指针将会放在文件的开头。如果文件不存在，抛出异常 |
|    w+    | 以读写方式打开文件。如果文件存在会被覆盖。如果文件不存在，创建新文件 |
|    a+    | 以读写方式打开文件。如果该文件已存在，文件指针将会放在文件的结尾。如果文件不存在，创建新文件进行写入 |

~~~python
file=open('aaa.txt','w')						#以写入的方式打开aaa.txt文件
text=file.write('a')							#'a'会覆盖文件所有内容
print(text)										#结果：a
file.close										#一定要关闭文件读写
~~~

## 4. readline方法

> `red`方法默认会把大文件的所有内容一次性全部读取到内存里，这样对内存的依赖非常严重。
>
> `readline`方法可以一次读取一行内容。方法执行后，会把文件指针移动到下一行，准备再次读取。

- 读取大文件的正确方式：

  ~~~python
  file=open('aaa.txt')
  while Ture:
      text=file.readline()
      if not text:							# 文件为空(false),结果为True，则执行退出。 
          break
  	print(text)
  file.close()
  ~~~

## 5. 文件的复制

- 小文件的复制

  ~~~python
  file_read=open('read.txt')
  file_write=open('write.txt')
  text=file_read.read()
  file_write.write(text)
  file_read.close()
  file_write.close()
  ~~~

- 大文件的复制

  ~~~python
  file_read=open('read.txt')
  file_write=open('write.txt')
  while Ture:
      text=file_read.readline()
      if not text:
          break
  	file_write.write(text)
  file_read.close()
  file_write.close()
  ~~~

## 6. `os`模块的简介

> 在终端/文件浏览器、中可以执行常规的 文件/目录管理操作，例如：创建、重命名、删除、改变路径、查看目录内容、.....
> 在Python中，如果希望通过程序实现上述功能，需要导入os模块

- 文件操做

  | 方法名 |    说明    |                实例                |
  | :----: | :--------: | :--------------------------------: |
  | rename | 重命名文件 | os.rename(源文件名,要命名的文件名) |
  | remove |  删除文件  |         os.remove(文件名)          |

- 目录操作

  |   方法名   |      说明      |          实例           |
  | :--------: | :------------: | :---------------------: |
  |  listdir   |    目录列表    |   os.listdir(目录名)    |
  |   mkdir    |    创建目录    |    os.mkdir(目录名)     |
  |   rmdir    |    删除目录    |    os.rmdir(目录名)     |
  |   getcwd   |  获取当前目录  |       os.getcwd()       |
  |   chdir    |  修改工作目录  |   os.chdir(目标目录)    |
  | path.isdir | 判断是否是文件 | os.path.isdir(文件路径) |

## 7. `eval`模块

> `eval`函数十分强大。可以将字符串当成有效的表达式来求值并返回计算结果
>
> - 基本数学计算：eval('1+1')			输出：2
> - 字符串重复：`eval('*'*10)`       输出：`**********`
> - 将字符串转换为列表：type(eval('[1,2,3,4]'))                输出：List
> - 将字符串转换为列表：type(eval('{'name':'xiaoming','age':20}'))                输出：dict

计算机案例：

~~~python
input_text=input('请输入表达式：')
print(eval(input_text))
~~~

# 二十一. GUI界面

> tkinter模块是一个Python内置的GUI专用界面。

## 1. Lable和Button

> Lable可以在视窗中创建一个标签。
>
> Button可以在视窗中创建一个按钮。

~~~python
import tkinter

#创建一个视窗主体对象
windows=tkinter.Tk()
#视窗标题
window.title('mywindow')
#视窗大小
window. geometry('200x 100')
#视窗标签样式
lab= tk.Label(window,text='OMG! this is TK!',bg= 'green', font=('Arial', 12), width=15,height=2)
#标签在哪个位置显示
lab.pack()
lab.place()
#视窗循环
window.mainloop()
~~~

[运行结果：](https://s1.ax1x.com/2022/03/06/bDTmTA.png)

​												[<img src="https://s1.ax1x.com/2022/03/06/bDTmTA.png" alt="bDTmTA.png" style="zoom:50%;" />](https://imgtu.com/i/bDTmTA)

添加Button标签

~~~python
import tkinter

#创建一个视窗主体对象
windows=tkinter.Tk()
#定义一个字符可变的常量
var = tk.StringVar()

#视窗标题
window.title('mywindow')
#视窗大小
window. geometry('200x 100')
#视窗标签样式
lab= tk.Label(window,textvariable=var,bg= 'green', font=('Arial', 12), width=15,height=2)
#标签在哪个位置显示
lab.pack()

#注册按钮并添加点击按钮事件
on_hit =False
def hit_me:
    global on_ hit
	if on_ hit == False:
		on_hit=True
		var.set( 'you hit me' )
	else:
		on_ hit= False
		var.set('')
b = tk. Botton(window, text='hit me', width=15,height=2, command=hit_ me)

#视窗循环
window.mainloop()
~~~

> 上面代码实现了当点击按钮之后会出现`you hit me`字样。当再次点击的时候会消失。

|                             方法                             |                     说明                     |
| :----------------------------------------------------------: | :------------------------------------------: |
|                             Tk()                             |          该方法用于创建一个视窗对象          |
|                      title(String name)                      |                 命名界面标题                 |
|                     geometry(String Big)                     |                   界面大小                   |
| Label(Object,text='String',bg='color',font=('String',size),width,heigth) |  规定标签的样式，宽高是以定义字符大小规定的  |
|                            pack()                            |           规定组件放在界面哪个位置           |
|                           place()                            |         规定组件具体放在界面哪个位置         |
|                          mainloop()                          | 该方法代表将窗口循环显示，是必须要调用的方法 |
| Button(Object,text='String',bg='color',font=('String',size),width,heigth，command= thit_me) |   按钮样式,command是点击后的事件，调用函数   |
|                         textvariable                         |          定义一个文本可见的标签类型          |
|                         StringVar()                          |     一个容器，类型为**可变的**字符串类型     |

## 2. Entry & Text输入和文本框

> Entry 可以用来创建一个输入框。
>
> Text可以创建一个文本框

~~~python
import tkinter

window = tk.Tk()
window.title('my window )
window.geometry('200x200')
#创建一个文本框。
e = tk.Entry(window,show='*')
e.pack()
def insert_point():
 	#获取文本框的值
	var = e.get()
    #在鼠标选中位置追加文本
	t.insert('insert', var)
def insert_end():
	var = e.get()
    #在文本框末尾追加文本
	t.insert('end', var)
b1 = tk. Button(window, text='insert point', width=15,height=2, command=insert_point)
b1.pack()
b2 = tk.Button(window, text='insert end',command=insert_end)
b2.pack()
t = tk.Text(window, height=2)
t.pack()
window.mainloop()
~~~

> 运行结果

|            方法             |                             说明                             |
| :-------------------------: | :----------------------------------------------------------: |
| Entry(Object,show='*'/None) | 传入一个窗体对象，show值有两个`*`用于密码，`None`用于文本输入 |
|  Text(Object,height,width)  |              传入一个窗体对象，宽和高为字符大小              |
|   insert(String insert,i)   |              insert参数为插入方式，i参数为变量               |





