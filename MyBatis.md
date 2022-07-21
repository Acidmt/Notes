MyBatis

> [官网](https://github.com/mybatis/mybatis-3)

[toc]

# 一. MyBatis

> 简介：
>
> MyBatis最初是Apache的一个开源项目iBatis, 2010年6月这个项目由Apache Software Foundation迁 移到了Google Code。随着开发团队转投Google Code旗下， iBatis3.x正式更名为MyBatis。代码于 2013年11月迁移到Github。
> iBatis一词来源于“internet”和“abatis”的组合，是一个基于Java的持久层框架。 iBatis提供的持久层框架 包括SQL Maps和Data Access Objects(DAO)。

## 1. MyBatis特点

> 1. MyBatis 是支持定制化 SQL、存储过程以及高级映射的优秀的持久层框架
> 2. MyBatis 避免了几乎所有的 JDBC 代码和手动设置参数以及获取结果集
> 3. MyBatis可以使用简单的XML或注解用于配置和原始映射，将接口和Java的POJO(Plain Old Java Objects，普通的Java对象) 映射成数据库中的记录
> 4. MyBatis 是一个 半自动的ORM(Object Relation Mapping。数据库中的表和实体类创建映射关系)框架(JDBC手动)

## 2. MyaBatis下载

- 进入[官网](https://github.com/mybatis/mybatis-3)下拉在最下面点击`Download latest`下载最新版本

  > 使用Maven创建工程可以不用下载jar包，在这里面选择下载全部资源然后找到里面的官方文档即可。不看官方文档的可以跳过这一步。

  [下载最新版本：](https://s1.ax1x.com/2022/07/21/jqTERS.png)                       [<img src="https://s1.ax1x.com/2022/07/21/jqTERS.png" alt="jqTERS.png" style="zoom:67%;" />](https://imgtu.com/i/jqTERS)

- 接着在新打开的网页选择`mybatis-3.5.10.zip`下载
  [MyBatis下载：](https://s1.ax1x.com/2022/07/21/jqT8RU.png)
  [![jqT8RU.png](https://s1.ax1x.com/2022/07/21/jqT8RU.png)](https://imgtu.com/i/jqT8RU)

- 查看下载内容
  [MyBatis目录：](https://s1.ax1x.com/2022/07/21/jq7a6g.png)
                                    [<img src="https://s1.ax1x.com/2022/07/21/jq7a6g.png" alt="jq7a6g.png" style="zoom:50%;" />](https://imgtu.com/i/jq7a6g)

## 3. 和其他持久化层的技术对比

1. JDBC

   > - SQL 夹杂在Java代码中耦合度高，导致硬编码(代码写死)内伤
   >
   > - 维护不易且实际开发需求中 SQL 有变化，频繁修改的情况多见
   > - 代码冗长，开发效率低

2. Hibernate(全自动ORM)和 JPA

   > 1. 操作简便，开发效率高
   > 2. 程序中的长难复杂 SQL 需要绕过框架
   > 3. 内部自动生产的 SQL，不容易做特殊优化
   > 4. 基于全映射的全自动框架，大量字段的POJO 进行部分映射时比较困难。反射操作太多，导致数据库性能下降

3. MyBatis

   > 1. 轻量级，性能出色 SQL 和 Java 编码分开，功能边界清晰。
   > 2. Java代码专注业务、SQL语句专注数据
   > 3. 开发效率稍逊于Hibernate，但是完全能够接受

# 二. 搭建MyBatis示例

## 1. 创建maven工程

- 创建一个普通Java项目，然后在其中新建一个maven工程，名称为mybatis_demo1。项目SDK选择Java 1.8。

  [配置Maven：](https://s1.ax1x.com/2022/07/21/jqvtyV.png)
                  [<img src="https://s1.ax1x.com/2022/07/21/jqvtyV.png" alt="jqvtyV.png" style="zoom:50%;" />](https://imgtu.com/i/jqvtyV)

- 项目右键选择Module..
  [创建项目文件：](https://s1.ax1x.com/2022/07/21/jqxsAg.png)
                     [<img src="https://s1.ax1x.com/2022/07/21/jqxsAg.png" alt="jqxsAg.png" style="zoom:50%;" />](https://imgtu.com/i/jqxsAg)

  > 可以通过模板直接创建文件，也可以手动创建

  [手动创建项目：](https://s1.ax1x.com/2022/07/21/jqxoEF.png)
                      [<img src="https://s1.ax1x.com/2022/07/21/jqxoEF.png" alt="jqxoEF.png" style="zoom:50%;" />](https://imgtu.com/i/jqxoEF)

  [项目目录结构：](https://s1.ax1x.com/2022/07/21/jqv6Qx.png)

​                                                     [<img src="https://s1.ax1x.com/2022/07/21/jqv6Qx.png" alt="jqv6Qx.png" style="zoom:50%;" />](https://imgtu.com/i/jqv6Qx)

## 2. 配置maven打包方式为jar

- 在mybatis_demo1的pom.xml文件中加入：

  ~~~xml
  <groupId>mybatis-demo1</groupId>
  <artifactId>mybatis-demo1</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>jar</packaging>
  ~~~

- 在pom.xml中插入依赖引入mybatis、junit、mysql依赖

  ~~~xml
  <dependencies>
          <!-- Mybatis核心 --> 
       <dependency>
          <groupId>org.mybatis</groupId>
          <artifactId>mybatis</artifactId>
          <version>3.5.7</version>
      </dependency>
      
          <!-- junit测试 --> 
       <dependency>
          <groupId>junit</groupId>
          <artifactId>junit</artifactId>
          <version>4.12</version>
          <scope>test</scope>
      </dependency>
      
          <!-- MySQL驱动 -->
       <dependency>
          <groupId>mysql</groupId>
          <artifactId>mysql-connector-java</artifactId>
          <version>5.1.3</version>
      </dependency>
  </dependencies>
  ~~~

  

