[toc]

# 数据表的创建、删除与修改

> $[]$种的内容可选，$<>$中的参数必选

## 1. 创建表

~~~sql
create table 表名(
			列名1 数据类型 [约束条件]
			[,列名2 数据类型 [约束条件]]
				...
			表级约束条件);
~~~

## 2. 表的修改

### 新增一列

~~~sql
alter table 表名 add 列名 数据类型 [约束条件];
alter table student add semail varchar(20);
~~~

- 添加主键

  ~~~sql
  alter table 表名 add primary key(列名);
  ~~~

- 添加外键

  ~~~sql
  ALTER table 表名 add foreign key(列名) REFERENCES 表名(列名); 
  ~~~

### 修改列名称 

~~~sql
alter table 表名 change 旧列名 新列名 数据类型;
alter table student change semail se1 varchar(20);
~~~

### 修改列的数据类型

~~~sql
alter table 表名 modify 列名 新数据类型;    
alter table student modify sel char(20);
~~~

- 修改字符集

  ~~~sql
  alter table 表名 modify 列名 数据类型 character set gbk/utf8;
  ~~~

- 处理字符乱码错误

  ~~~sql
  set names gbk/utf8;
  ~~~

### 删除列

~~~sql
alter table 表名 drop 列名;
alter table student drop sel;
~~~

- 删除主键

  ~~~sql
  alter table 表名 drop primary key;
  ~~~

- 删除外键

  ~~~sql
  alter table 表名 drop foreign key 外键名;
  ~~~

### 表的删除

~~~sql
drop table 表名;
~~~

## 3. 索引的创建与删除

### 创建索引

~~~sql
create [unique] index 索引名 on 表名(列名 次序 [,列名 次序]...);
create INDEX s2 on student(sbirthdate asc,smajor desc);
~~~

或者：

~~~sql
alter table 表名 add index 表名(列名 次序);
alter table student add index student(sbirth desc);
~~~

### 查看索引

~~~sql
show index from 表名;
show index from student;
~~~

### 修改索引

> 5.7 版本之前 先删除后新建

5.7 版本之后：

~~~sql
alter table student rename index 旧索引名 to 新索引名;
alter table student rename index s2 to s3;
~~~

### 删除索引

~~~sql
drop index 索引名 on 表名;
alter table 表名 drop index 索引名;
~~~

## 4. 数据更新

首先创建三个表并插入数据

> student表：学生表；属性：sno、sname、ssex、sbirthdate、smajor
>
> course表：课程表；属性：cno、cname、cpno、ccredit(学分)
>
> sc表：学生选课表；属性：sno、cno、grade、Semester、Teachingclass

~~~sql
#学生表
CREATE TABLE Student          
(Sno   CHAR(8) PRIMARY KEY, 
 Sname VARCHAR(20) UNIQUE,            
 Ssex  CHAR(6),
 Sbirthdate   date,
 Smajor  varCHAR(40)
); 

#课程表
create table course
(Cno CHAR(5) PRIMARY KEY,
 Cname CHAR(40) not null,
 Cpno  CHAR(5),
 Ccredit SMALLINT,
 FOREIGN KEY (Cpno) REFERENCES Course(Cno)
); 

#学生选课表
CREATE TABLE SC
(Sno CHAR(8),
 Cno CHAR(5),
 Grade SMALLINT,
 Semester char(5),
 Teachingclass char(8),
 PRIMARY KEY (Sno,Cno),
 FOREIGN KEY (Sno) REFERENCES Student(Sno),
 FOREIGN KEY (Cno)REFERENCES Course(Cno)
);

#数据更新
insert into student values('20180001','李勇','男','2000-3-8','信息安全');
insert into student values('20180002','刘晨','女','1999-9-1','计算机科学与技术');
insert into student values('20180003','王敏','女','2001-8-1','计算机科学与技术');
insert into student values('20180004','张立','男','2000-1-8','计算机科学与技术');
insert into student values('20180005','陈新奇','男','2001-11-1','信息管理与信息系统');
insert into student values('20180006','赵明','男','2000-6-12','数据科学与大数据技术');
insert into student values('20180007','王佳佳','女','2001-12-7','数据科学与大数据技术');


insert into course(cno,cname,ccredit,cpno) values('81001','程序设计基础与C语言',4,NULL);
insert into course(cno,cname,ccredit,cpno) values('81007','离散数学',4,NULL);
insert into course(cno,cname,ccredit,cpno) values('81002','数据结构',4,'81001');
insert into course(cno,cname,ccredit,cpno) values('81005','操作系统',4,'81001');
insert into course(cno,cname,ccredit,cpno) values('81003','数据库系统概论',4,'81002');
insert into course(cno,cname,ccredit,cpno) values('81006','Python语言',3,'81002');
insert into course(cno,cname,ccredit,cpno) values('81004','信息系统概论',4,'81003');
insert into course(cno,cname,ccredit,cpno) values('81008','大数据技术概论',4,'81003');


insert into sc     values('20180001','81001',85,'20192','81001-01');
insert into sc     values('20180001','81002',96,'20201','81002-01');
insert into sc     values('20180001','81003',87,'20202','81003-01');
insert into sc     values('20180002','81001',80,'20192','81001-02');
insert into sc     values('20180002','81002',98,'20201','81002-01');
insert into sc     values('20180002','81003',71,'20202','81003-02');
insert into sc     values('20180003','81001',81,'20192','81001-01');
insert into sc     values('20180003','81002',76,'20201','81002-02');
insert into sc     values('20180004','81001',56,'20192','81001-02');
insert into sc     values('20180004','81002',97,'20201','81002-02');
insert into sc     values('20180005','81003',68,'20202','81003-01');
~~~

### 插入数据

- sql插入语句

  ~~~sql
  insert into 表名[(列名1...)]  VALUES(常量1....);
  insert into student values
  		('20180009','张三','男','2000-10-1','软件工程');
  insert into student(sno,sname,ssex,sbirthdate,smajor) values
  		('20180010','李红','女','2005-10-1','软件工程');
  insert into student(sname,sno) values('王五','20180011'),('20180010','李红','女','2005-10-1','软件工程');
  ~~~

- 插入子查询的值，子查询：以查询到的结果集合作为插入条件

  ~~~sql
  insert into 表名[(列名1...)] select 子句;
  insert into xs select sno from student; #将student表数据插入到sx表中
  #insert into xs(sno) select sno from student;
  ~~~

### 修改数据

~~~sql
update 表名 set 列名1=值|表达式.... [where 条件];
update student set smajor='软件工程',ssex='男' where sno='20180011';
~~~

例题1：将计算机科学与技术专业的学生成绩置$0$；

~~~sql
update sc set grade=0 where sno IN
		(SELECT sno from student where smajor='计算机科学与技术');
~~~

例题2：将选修数据结构的计算机科学与技术专业的同学的生日都改成$2023-10-8$；

~~~sql
update student set sbirthdate='2023-10-8' where smajor='计算机科学与技术'
		and sno in(SELECT sno from sc where cno IN
				(SELECT cno from course where cname='数据结构'));
~~~

### 删除数据

~~~sql
delete from 表名 [where 条件];
delete from student; 
#等价于:
truncate table student;
~~~

例题1：删除计算机科学与技术专业所有学生的选课记录；

~~~sql
delete from sc where sno in(select sno from student where smajor='计算机科学与技术');
~~~

例题2：删除数据库系统概论的选课信息；

~~~sql
delete from sc where cno in(select cno from course where cname='数据库系统概论');
~~~

## 5. 数据查询

三张表同上

### 5.1 单表查询

- 选择指定列

  ~~~sql
  select sno,sname from student;
  ~~~

- 选择所有列

  ~~~sql
  select sno,sname,ssex,sbirthdate,smajor from student;
  select * from student;
  ~~~

- 查询经过计算的值，查询所有学生的学号，姓名，年龄：

  ~~~sql
  #根据学生出生年月计算学生年龄
  select sno,sname,year(now())-year(sbirthdate) from student;
  ~~~

### 5.2 选择表中的若干元组

#### 消除重复行

`distinct`：消除重复行

~~~sql
#查询选课的学生学号
select distinct sno from sc;
~~~

#### 查询满足条件的元组

查询满足指定条件的元组通过`where`字句实现。`where`字句常用的查询条件如下：

| 查询条件           |                   关键字                    |
| ------------------ | :-----------------------------------------: |
| 比较               | $=,>,<,>=,<=,!=,<>,!>,!<;$ `NOT`+上述运算符 |
| 确定范围           |      `BETWEEN AND`、`NOT BETWEEN AND`       |
| 确定集合           |               `IN`、`NOT IN`                |
| 字符匹配           |             `LIKE`、`NOT LIKE`              |
| 空值               |          `IS NULL`、`IS NOT NULL`           |
| 多重条件(逻辑运算) |             `AND`、`OR`、`NOT`              |

- 查询计算机科学与技术专业年龄大于22岁的学生的学号，姓名，年龄；

  ~~~sql
  select sno,sname,year(now())-year(sbirthdate) from student 
  	where smajor="计算机科学与技术" and year(now())-year(sbirthdate)>22;
  ~~~

- [not] `between....and....`

  查询成绩是良好（80-90）的学生的学号，成绩；

  ~~~sql
  select sno,grade from sc where grade between 80 and 90;
  #不在80~90之间的学生
  select sno,grade from sc where grade not between 80 and 90; 
  ~~~

- 确定集合：`in`

   查询计算机科学与技术和信息安全专业的同学的信息；

  ~~~sql
  select * from student where smajor in ('计算机科学与技术','信息安全');
  #等价于：
  select * from student where smajor='计算机科学与技术' or smajor='信息安全';
  ~~~

- 字符匹配：关键字`like`

  |   符号   |       功能       |
  | :------: | :--------------: |
  |   `_`    |   任意单个字符   |
  |   `%`    |   任意多个字符   |
  | `escape` | 声明一个转义字符 |

  ~~~sql
  select * from student where sname like '刘%'; 	#查询学生姓刘的学生，任意多个字符：刘某某
  select * from student where sname like '王%';   #查询学生姓王的学生，单个字符：王
  ~~~

   查询开头三`DB_`的课程信息：

  ~~~sql
  select * from course where sname like 'DB#_%' escape '#';
  ~~~

  > `#`被`escape`声明变为转义字符，`#`后面的第一个字符将变为普通的字符使用，不再有通配符意义。注意`\`不能声明为转义字符

- 空值判断：`is null`、`is not null`

   查询先修课`cpno`为空的课程信息：

  ~~~sql
  select * from course where cpno is null;
  #不为空的课程信息
  select * from course where cpno is not null;
  ~~~

- 多重条件查询：`and`、`or`、`not`

   查询成绩在90分以上的学分为4的课程信息：

  ~~~sql
  select * from course where ccredit=4 and cno in(select cno from sc where grade>90);
  ~~~

   查询成绩在90分以上的计算机科学与技术专业的男生同学的信息：

  ~~~sql
  select * from student where smajor='计算机科学与技术' 
  		and ssex='男' and sno in(select sno from sc where grade>90);
  ~~~

   查询数据结构和程序设计基础与c语言的选课成绩：

  ~~~sql
  SELECT Grade FROM sc WHERE Cno IN
  	(SELECT Cno FROM course WHERE cname in('数据结构','程序设计基础与c语言'));
  ~~~

#### ORDER BY排序

`ORDER BY`后面跟列名[表达式]，参数`asc`升序(默认)，`desc`降序

 在学生表中，将学生的信息按照年龄的升序排列

~~~sql
select * from student ORDER BY year(now())-year(sbirthdate) asc;
select * from student ORDER BY sbirthdate desc;			#运行结果同上
~~~

将计算机科学与技术的同学按照其选课的平均成绩进行降序排列：

~~~sql
SELECT sno, avg(grade) FROM sc where sno in 
	(SELECT sno from student where smajor='计算机科学与技术') GROUP BY sno ORDER BY avg(grade) desc;
select * from student where smajor='计算机科学与技术' 
	order by (select avg(grade) from sc where student.sno=sc.sno GROUP BY sno) desc;
~~~

#### 聚集函数

SQL提供了许多聚集函数，主要有：

|            函数名            | 作用                           |
| :--------------------------: | :----------------------------- |
|           COUNT(*)           | 统计元组个数                   |
| COUNT([DISTINCT\|ALL]<列名>) | 统计一列中值的个数             |
|  SUM([DISTINCT\|ALL]<列名>)  | 计算一列值得总和(此列为数值型) |
|  AVG([DISTINCT\|ALL]<列名>)  | 计算一列值得平均值             |
|  MAX([DISTINCT\|ALL]<列名>)  | 求一列值中的最大值             |
|  MIN([DISTINCT\|ALL]<列名>)  | 求一列值中的最小值             |

~~~sql
#查询学生来自几个专业
select count(DISTINCT smajor) 专业数目 from student;
#查询选课的学生人数
select count(DISTINCT sno) 选课人数 from sc;
#查询学生选课成绩的最大值和最小值
select MAX(grade),MIN(grade) from sc;
~~~

#### limit子句

`limit m`查询出$m$个元组

`limit m,n`查询从$m+1$行开始的$n$个元组

 查询成绩在前五名的学生学号：

~~~sql
select sno,grade from sc order by grade dsec limit 5;
~~~

 查询成绩在6-10名的学生学号，成绩；

~~~sql
select sno,grade from sc order by grade desc limit5,5;
~~~

#### ==GROUP BY==

`GROUP BY`子句将查询结果按某一列或多列的值分组，值相等的为一组，如果是多列，则先对第一列的值进行分组，然后对每一组中的值按照第二列值分组，依次类推。结果集中如果有重复的列组值，则将其合并为一行输出。

`GROUP BY`有个分组筛选条件`HAVING` 后面跟判断表达式

例：对表A，B两列进行如下分组

|  A   |  B   |
| :--: | :--: |
|  1   |  2   |
|  1   |  2   |
|  1   |  3   |
|  2   |  4   |

最后的分组结果为：

|  A   |  B   |
| :--: | :--: |
|  1   |  2   |
|  1   |  3   |
|  2   |  4   |

> 对查询结果分组的目的之一是细化聚集函数的作用对象，如果未对查询结果分组，聚集函数将作用于整个查询结果，分组后聚集函数将**作用于每一组**，即每组都有一个聚集函数的值。

查询学生的学号，平均成绩

~~~sql
select cno,count(sno) from sc group by cno;
~~~

> 该语句对查询结果按`Cno`的值进行分组，所有具有相同`cno`值的元素为一组，然后对每一组应用聚集函数`COUNT`进行计算，求得改组的学生人数

 查询课程的课程号，平均成绩，并按照平均成绩降序排列

~~~sql
select sno,avg(grade) from sc group by cno order by avg(grade) desc;
~~~

查询学生的平均年龄大于20岁的专业名

~~~sql
select smajor,avg(year(now())-year(sbirthdate)) 
	from student group by smajor having avg(year(now())-year(sbirthdate))>20;
~~~

> 先用`group by`对smajor进行分组，再用`having`来过滤平均年龄大于$20$的数据

查询$2019$年第$2$学期选修课程数超过$10$门的学生学号

~~~sql
select sno from sc 
	where semester=20192 		#先求出2019年第二学期选课的所有学生
	group by sno 				#用group b字句按sno进行分组
	having count(*)>10;			#用聚集函数count对每一组进行计数
~~~

> 这里`having`语句给出了选择组的条件，只有满足条件(即一个组中元组的个数$>10$，表示此学生$2019$年第$2$学期选修课程超过$10$门)的组才会被选出来

==注意：==关系数据库管理系统在处理SQL语句时，先处理`WHERE`子句，根据条件选出合格元组，生成一个临时表，上例中选出了$2019$年第$2$学期选课的所有学生，再使用`GROUP BY`子句对临时表按照学号进行分组，最后用`HAVING`条件中的聚集函数`COUNT`对每一组进行计数，选出`COUNT>10`的组，输出该组的`sno`。

`where`和`having`子句的==区别：==

1. 作用的对象不同。`WHERE`子句作用于表和视图，`HAVING`子句作用于组。

2. `WHERE`在分组和聚集计算之前选取输入行(因此，它控制哪些行进入聚集计算)， 而`HAVING`在分组和聚集之后选取分组的行。因此，**`WHERE`子句不能包含聚集函数**。以下写法是错误的：

   ~~~sql
   SELECT smajor,AVG(YEAR(NOW())-YEAR(sbirthdate)) age FROM student 
   	where AVG(YEAR(NOW())-YEAR(sbirthdate))>20;			#where后面不能跟聚集函数avg
   ~~~

   聚集函数是从确定的结果集中整列数据进行计算的 ，而`where`子句则是对数据行进行过滤的，所以`where`子句后面跟聚集函数毫无意义。 相反，`HAVING`子句总是包含聚集函数，严格说来，可以写不使用聚集的`HAVING`子句，但这样做效率不高，因为同样的条件可以更有效地用于`WHERE`进行过滤。

3. `WHERE`子句在聚合前先筛选记录，也就是说作用在`GROUP BY`子句和`HAVING`子句前．

   而`HAVING`子句在聚合后对组记录进行筛选。  



