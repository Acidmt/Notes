SpringMVC

[toc]

# 一. SpringMVC

1. 什么MVC

   > MVC是一种软件架构的思想，将软件按照模型、视图、控制器来划分
   >
   > M: Model,模型层，指工程中的avaBean,作用是处理数据
   >
   > JavaBean分为两类：
   >
   > - 一类称为实体类Bean：专门存储业务数据的,如Student、 User等
   > - 一类称为业务处理Bean：指Service或Dao对象，专门用于处理业务逻辑和数据访问。
   >
   > V：View,视图层，指工程中的html或jsp等页面,作用是与用户进行交互,展示数据
   > C：Controller, 控制层,指工程中的servlet,作用是接收请求和响应浏览器
   >
   > MVC的工作流程:
   > 用户通过视图层发送请求到服务器，在服务器中请求被Controller接收，Controller调用相应的Model层处理请求,处理完毕将结果返回到Controller, Controller再根据请求处理的结果找到相应的View视图，渲染数据后最终响应给浏览器。

2. 什么是SpringMVC

   > SpringMVC是Spring的一个后续产品，是Spring的一个子项目
   >
   > SpringMVC是Spring为表述层开发提供的一整套完备的解决方案。在表述层框架历经Strust、WebWork、Strust2等诸多产品的历代更迭之后，目前业界普遍选择了SpringMVC作为Java EE项目表述层开发的首选方案。
   >
   > ==注：三层架构分为表述层(或表示层)、业务逻辑层、 数据访问层，表述层表示前台页面和后台servlet==

3. SpringMVC特点

   > 1. Spring原生产品，与IOC容器等基础设施对接好
   > 2. 基于原生的Servlet,通过了功能强大的前端控制器DispatcherServlet,对请求和响应进行统一处理
   > 3. 表述层各细分领域需要解决的问题全方位覆盖，提供全面解决方案
   > 4. 代码清新简洁，大幅度提升开发效率
   >
   > 5. 内部组件化程度高，可插拔式组件即插即用,想要什么功能配置相应组件即可
   > 6. 性能卓著，尤其适合现代大型、超大型互联网项目要求

## 1. 创建Maven工程

- 项目右键选择Module
  [maven项目创建：](https://s1.ax1x.com/2022/07/10/jypwz6.png)

  ​						[<img src="https://s1.ax1x.com/2022/07/10/jypwz6.png" alt="jypwz6.png" style="zoom:67%;" />](https://imgtu.com/i/jypwz6)

- 选择下一步，手动创建项目
  [maven项目创建：](https://s1.ax1x.com/2022/07/10/jyphSP.png)

  ​						[<img src="https://s1.ax1x.com/2022/07/10/jyphSP.png" alt="jyphSP.png" style="zoom: 33%;" />](https://imgtu.com/i/jyphSP)

- 设置项目名修改配置后点击完成

  [maven项目创建：](https://s1.ax1x.com/2022/07/10/jypxyT.png)

  ​						[<img src="https://s1.ax1x.com/2022/07/10/jypxyT.png" alt="jypxyT.png" style="zoom: 33%;" />](https://imgtu.com/i/jypxyT)

- 配置pom.xml文件

  ~~~xml
  <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
      <groupId>aws</groupId>
      <artifactId>attendance</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      <packaging>war</packaging>
  
      <dependencies>
  
          <!-- ServletAPI -->
          <dependency>
              <groupId>javax.servlet</groupId>
              <artifactId>javax.servlet-api</artifactId>
              <version>3.1.0</version>
              <scope>provided</scope>
          </dependency>
  
          <!-- Spring5和Thymeleaf整合包 -->
          <dependency>
              <groupId>org.thymeleaf</groupId>
              <artifactId>thymeleaf-spring5</artifactId>
              <version>3.0.12.RELEASE</version>
          </dependency>
  
  
          <!-- spring需要的jar包 -->
          <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-context</artifactId>
              <version>3.2.4.RELEASE</version>
              <type>jar</type>
          </dependency>
  
          <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-core</artifactId>
              <version>3.2.4.RELEASE</version>
              <type>jar</type>
          </dependency>
  
          <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-beans</artifactId>
              <version>3.2.4.RELEASE</version>
              <type>jar</type>
          </dependency>
  
          <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-webmvc</artifactId>
              <version>3.2.4.RELEASE</version>
              <type>jar</type>
          </dependency>
  
          <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-orm</artifactId>
              <version>3.2.4.RELEASE</version>
              <type>jar</type>
          </dependency>
  
          <!-- hibernate需要的jar包 -->
          <dependency>
              <groupId>org.hibernate</groupId>
              <artifactId>hibernate-validator</artifactId>
              <version>5.1.3.Final</version>
          </dependency>
  
          <dependency>
              <groupId>org.hibernate</groupId>
              <artifactId>hibernate-core</artifactId>
              <version>4.2.16.Final</version>
              <type>jar</type>
          </dependency>
  
          <!-- hibernate ehcache需要的jar包 -->
          <dependency>
              <groupId>org.hibernate</groupId>
              <artifactId>hibernate-ehcache</artifactId>
              <version>4.3.8.Final</version>
          </dependency>
  
          <!-- 连接MySQL数据库需要的jar包 -->
          <dependency>
              <groupId>mysql</groupId>
              <artifactId>mysql-connector-java</artifactId>
              <version>5.1.34</version>
          </dependency>
  
          <!-- dbcp连接池需要的jar包 -->
          <dependency>
              <groupId>commons-dbcp</groupId>
              <artifactId>commons-dbcp</artifactId>
              <version>1.4</version>
          </dependency>
  
          <!-- jstl需要的jar包 -->
          <dependency>
              <groupId>jstl</groupId>
              <artifactId>jstl</artifactId>
              <version>1.2</version>
          </dependency>
  
          <!-- log4j需要的jar包 -->
          <dependency>
              <groupId>log4j</groupId>
              <artifactId>log4j</artifactId>
              <version>1.2.17</version>
          </dependency>
  
          <!-- 文件上传需要的jar包 -->
          <dependency>
              <groupId>commons-fileupload</groupId>
              <artifactId>commons-fileupload</artifactId>
              <version>1.2.1</version>
          </dependency>
  
          <dependency>
              <groupId>commons-io</groupId>
              <artifactId>commons-io</artifactId>
              <version>1.4</version>
          </dependency>
  
          <!-- 单元测试需要的jar包 -->
          <dependency>
              <groupId>junit</groupId>
              <artifactId>junit</artifactId>
              <version>3.8.1</version>
              <scope>test</scope>
          </dependency>
  
          <dependency>
              <groupId>javax.servlet.jsp</groupId>
              <artifactId>jsp-api</artifactId>
              <version>2.2</version>
              <type>jar</type>
          </dependency>
  
          <dependency>
              <groupId>javax.validation</groupId>
              <artifactId>validation-api</artifactId>
              <version>1.1.0.Final</version>
          </dependency>
  
          <dependency>
              <groupId>org.apache.ant</groupId>
              <artifactId>ant</artifactId>
              <version>1.7.0</version>
          </dependency>
  
      </dependencies>
  </project>
  ~~~

  > ServletAPI的provided参数表示项目打包成war包后，servlet由Tomcat容器提供，项目的jar包不用放进war包

- 添加Web.xml文件

  [选择项目结构：](https://s1.ax1x.com/2022/07/10/jyCNgx.png)

  ​                                                                             [<img src="https://s1.ax1x.com/2022/07/10/jyCNgx.png" alt="jyCNgx.png" style="zoom:33%;" />](https://imgtu.com/i/jyCNgx)

  [选择项目：](https://s1.ax1x.com/2022/07/10/jyC5Vg.png)                                    

  ​                  [<img src="https://s1.ax1x.com/2022/07/10/jyC5Vg.png" alt="jyC5Vg.png" style="zoom: 50%;" />](https://imgtu.com/i/jyC5Vg)

  [添加web.xml文件：](https://s1.ax1x.com/2022/07/10/jyCjqU.png)
                    [<img src="https://s1.ax1x.com/2022/07/10/jyCjqU.png" alt="jyCjqU.png" style="zoom:50%;" />](https://imgtu.com/i/jyCjqU)

  [配置路径：](https://s1.ax1x.com/2022/07/10/jyP9i9.png)

  ​                                                       [<img src="https://s1.ax1x.com/2022/07/10/jyP9i9.png" alt="jyP9i9.png" style="zoom:50%;" />](https://imgtu.com/i/jyP9i9)

  > 注意路径一定要补全项目路径

  [项目结构：](https://s1.ax1x.com/2022/07/10/jyPKJA.png)
                                                                         [<img src="https://s1.ax1x.com/2022/07/10/jyPKJA.png" alt="jyPKJA.png" style="zoom:50%;" />](https://imgtu.com/i/jyPKJA)