[toc]

> 本文根据《数据库系统概论》(第6版)中的`student`，`coutse`，`sc`三张表作为数据源。并详细探讨`EXISTS`谓词作用，用法及原理。

[student表：](https://image.sybblogs.fun/img-common/202311061414932.png)

<img src="https://image.sybblogs.fun/img-common/202311061414932.png" alt="student表" style="zoom:43%;" />

[course表：](https://image.sybblogs.fun/img-common/202311061415331.png)

<img src="https://image.sybblogs.fun/img-common/202311061415331.png" alt="course表" style="zoom:43%;" />

[sc表：](https://image.sybblogs.fun/img-common/202311061415848.png)

<img src="https://image.sybblogs.fun/img-common/202311061415848.png" alt="sc表" style="zoom:43%;" />

# 一. 带有$EXISTS$谓词的子查询

## EXISTS谓词作用

`EXISTS`代表存在量词$\exists$。带有`EXISTS`谓词的子查询不返回任何数据，只产生逻辑真值$true/false$，所以查询列名用`*`即可。

查询所有选修了81001号课程的学生姓名。

~~~sql
select sname from student where exists (select * from sc where sno=student.sno and cno='81001'); 
~~~

> 本查询中子查询条件依赖于外层父查询的某个属性值(student的sno值)，因此也是相关子查询。处理过程如下：
>
> 首先取外层查询中$student$表的第一个元组，根据它与内层查询相关的属性值(sno值)处理内层查询，若where子句返回值为真，则取外层查询中该元组的sname放入结果表，然后再取student表的下一个元组。重复这一过程，直到外层student表全部检查完为止。

$\Large 例1:$查询选修了全部课程的学生姓名

~~~sql
SELECT sname FROM student WHERE NOT EXISTS 
	(SELECT * FROM course WHERE NOT EXISTS 
     	(SELECT * FROM sc WHERE sc.sno=student.sno AND sc.cno=course.cno));  
~~~

$\Large 例2:$查询至少选修了学生20180002选修的全部课程的学生的学号(不存在这样的课程$y$，学生$21080002$选修了$y$，而学生$x$没有选修)

~~~sql
SELECT sno FROM student WHERE NOT EXISTS 
	(SELECT * FROM sc WHERE sno='20180002' AND NOT EXISTS 
     	(SELECT * FROM sc X WHERE x.sno=student.sno AND x.cno=sc.cno));
~~~

# 二. ==EXISTS原理==

## 1. 书中定义

> EXISTS(包括 NOT EXISTS )子句的返回值是一个BOOL值。 EXISTS内部有一个子查询语句(SELECT ... FROM...)， 我将其称为EXIST的内查询语句。其内查询语句返回一个结果集。 EXISTS子句根据其内查询语句的结果集空或者非空，返回一个布尔值。

一种通俗的可以理解为：将外查询表的每一行，代入内查询作为检验，如果内查询返回的结果取非空值，则EXISTS子句返回TRUE，这一行行可作为外查询的结果行，否则不能作为结果。

~~~sql
SELECT *FROM student WHERE EXISTS(SELECT cno FROM course WHERE cno='81009')
~~~

上句因为$exists$始终返回的是$false$（没有`81009`这门课程），所以外层查询始终无效，也就不会产生数据。

> 分析器会先看语句的第一个词，当它发现第一个词是`SELECT`关键字的时候，它会跳到`FROM`关键字，然后通过`FROM`关键字找到表名并把表装入内存。并通过指针找到第一条记录，接着是找`WHERE`关键字计算它的条件表达式，如果找不到则返回到`SELECT`字段解析。如果找到`WHERE`，则分析其中的条件，如果为真那么把这条记录装到一个虚表当中，指针再指向下一条记录。如果为假那么指针直接指向下一条记录，而不进行其它操作。一直检索完整个表，并把检索出来的虚拟表返回给用户。完成后再回到`SELECT`分析字段。最后形成一张我们要的虚表。
>
> 　　`WHERE`关键字后面的是条件表达式。条件表达式计算完成后，会有一个返回值，即非0或0，非0即为真(true)，0即为假(false)。同理`EXISTS`后面的条件也有一个返回值，真或假，来确定接下来执不执行`SELECT`。

`EXISTS`与`IN`的使用效率的问题，通常情况下采用`exists`要比`in`效率高，但要看实际情况具体使用：`IN`适合于外表大而内表小的情况；`EXISTS`适合于外表小而内表大的情况。

MySQL相关子查询执行顺序如下：

1. 首先执行一次外部查询
2. 对于外部查询中的每一行分别执行一次子查询，而且每次执行子查询时都会引用外部查询中当前行的值。

3. 使用子查询的结果来确定外部查询的结果集。

==总结：==总的来说`Exists`执行的流程`Exists`首先执行外层查询，再执行内存查询，与`IN`相反。 流程为首先取出外层中的第一元组， 再执行内层查询，将外层表的第一元组代入，若内层查询为真，即有结果时。返回外层表中的第一元组，接着取出第二元组，执行相同的算法。一直到扫描完外层整表 。

## 2. 将相关子查询转换为C++语言

再来看看：查询选修了全部课程的学生姓名

~~~sql
SELECT sname FROM student WHERE NOT EXISTS 
	(SELECT * FROM course WHERE NOT EXISTS 
     	(SELECT * FROM sc WHERE sc.sno=student.sno AND sc.cno=course.cno));  
~~~

全面分析这句话，首先在题目上，题目可以转换为：**不存在一门课程这个学生没有选修**。因为没有MySQL没有`任意一个`这样的谓词， 只能用`EXISTS`或者`NOT EXISTS`来表示。这也是`EXISTS`存在意义。

所以外层查询语句代表`SELECT sname FROM student WHERE NOT EXISTS(一门课程这个学生没有选修) `接下来就是把course表中的课程依次拿出来找出没有选修的。因为`NOT EXISTS`子查询中找不到的提交结果集。`NOT EXISTS`查询的本质还是相关查询，所以只要把在最后一个`select`中`sc.sno=student.sno AND sc.cno=course.cno`满足这个就可以将这个同学选课信息通过sc表和crouse的课程连接一遍，找到连接不上的，即： 没有选修的。这样就找到了一门课这个学生没有选修，也即存在没有选修的课，那么该学生被去掉，进行下一个同学的判断 。

这样可以形成一个结构：

1. 第一个`select`就是 你要选的就是学生
   SELECT Sname
   FROM Student
2. 第二个 select 就是课程
3. 第三个select就是学生和课程发生关系的表：SC选修表让他们连接起来

再从程序结构上解析这句话：`EXISTS`的**相关子查询语句**就是一个嵌套循环，内层循环对应外层循环。转化为C++代码结构如下：

~~~C++
for(i=1;i<student.length( 学生的总人数); i++){
    bool notExitst=true;						//notExitst同上面NOT EXISTS
    for(i=j;j<Crouse.length(总的课门数); j++){
        for(sc=1;sc<sc.length(sc表总记录数);sc++){
            if(sc.sno=student.sno AND sc.cno=course.cno){
         //如果该学生这门课在sc表中找到对应,那么第二个NOT EXISTS为false不返回任何结果,第二层course进入下一个循环	
                notExitst=false;
                break;
            }
        } 
//如果sc表遍历完还没有找到,则第二个NOT EXISTS为true,返回该学生元组,但下面15行第一个NOT EXISTS取反就变为false
       if(notExitst) break; 
    }
 //这是第一个NOT EXISTS,如果学生选课信息表sc都能对应课程号course.cno,即内层为notExitst=false,那么该学生信息放入结果集
    if(!notExitst){将sname放入结果集;}	//只有内层notExitst=false时才将sname放入结果集
}
~~~

> 从这里可以看出`EXISTS`语句效率取决于外层表元组大小，所以`EXISTS`适合外表小，内表大的查询。这是与`IN`在效率上本质区别。
>
> 同时也不难理解`EXISTS`只有两种情况会为上层传递返回值：①当`EXISTS`谓词判定为`true`时；②内层表所有元组遍历完时。

## 3. MySQL相关子查询代码逻辑

MySQL代码逻辑是这样的：

1. 先将student表放入内存中并将指针指向第一个元组，即学号为$20180001$学生；course表也是一样操作指针指向第一个元组$81001$课程号，再将最内层sc表通过`sc.sno=student.sno AND sc.cno=course.cno`条件连接起来。
2. 当sc表中找到满足(`and`谓词)学号是$20180001$课程号是$81001$元组时，内层`NOT EXISTS`不为`NULL`，返回`false`，即第二层course表不返回任何数据给第一层的student，而是继续将course表指针指向下一个元组81002课程号。重复此操作，直到当course中指针指向最后一个课程号，此时由于是最后一次循环，必定有返回值，如果为false则外层取反即该学生选修所有课程，将该学生保存至结果集中。最外层student指向第二个元组，即学号是$20180002$学生。
3. 重复上述操作，如果当course中指针指向一个元组的课程号，而学号和该课程号没有在sc中找到对应记录时，证明该学生没有学习这门课程，此时第二层course的`NOT EXISTS`返回`true`，将该学生信息传递给第一层的`NOT EXISTS`，而外层取反变为`false`，该记录值对应学号的学生不被保留。
4. student表继续指向下一个学生号，重复上述三步操作。

关于`EXISTS`与`NOT EXISTS`什么时候用：当题中涉及到，"全部"、"任意一个"这样的谓词时，应该转化为$\exists$谓词，使用`EXISTS`语句。一般来说`NOT EXISTS(select *From 表2)`修饰的谓词要遍历`表2`内所有元组，当所有元组遍历完后仍不满足条件，即为`NULL`时，`NOT EXISTS`才返回`true`。而`EXISTS`谓词只需要在`表二`中找到满足条件的元组，即可返回`true`。

> 更多内容请参考[这里](https://sybblogs.fun/)