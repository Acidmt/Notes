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

## 2. 配置web.xml

> 配置方式有两种：
>
> 1. 默认配置方式
> 2. 扩展配置方式(常用)

- 默认配置方式

  > 此配置作用下，SpringMVC的配置文件默认在WEB-INF下，默认名称为`<servlet-name>-servlet.xml`, 例如，以下配置所对应SpringMVC的配置文件位于WEB-INF下，文件名为`springMVC-servlet.xml`

  配置web.xml

  ~~~xml
  <!--配置Spr ingMVC的前端控制器，对浏览器发送的请求统一进行处理-->
  <servlet>
      <servlet-name>springMVC </servlet-name>
      <servlet-class>org.springframework.web.serv1et.DispatcherServ1et</servlet-class>
  </serv1et>
  <servlet-mapping>
      <servlet-name>springMVC </servlet-name>
      <!--设置springMVC的核心控制器所能处理的请求的请求路径/所匹配的请求可以是:
  		/login或.html或.js或.css方式的请求路径
  		但是/不能匹配. jsp请求路径的请求-->
      <ur1-pattern>/</ur1-pattern>
  </servlet-mapping>
  ~~~

- 扩展配置方式

  > 可通过`init-param`标签设置SpringMVC配置文件的位置和名称，通过`load-on-startup`标签设置SpringMVC前端控
  > 制器`DispatcherServlet`的初始化时间

  先在resources目录下创建springMVC.xml文件，作为springMVC的默认配置文件

  [创建SpringMVC：](https://s1.ax1x.com/2022/07/11/j6Fg1A.png)                                             [<img src="https://s1.ax1x.com/2022/07/11/j6Fg1A.png" alt="j6Fg1A.png" style="zoom: 50%;" />](https://imgtu.com/i/j6Fg1A)

  之后在web.xml中配置springMVC文件的位置和名称

  ~~~xml
  <!--配置SpringMVC的前端控制器，对浏览器发送的请求统一进行处理-->
  <servlet>
      <servlet-name>springMVC </servlet-name>
      <servlet-class>org.springframework.web.serv1et.DispatcherServ1et</servlet-class>
      <!--配置SpringMVC配置文件的位置和名称-->
  	<init-param>
  		<param-name>contextConfigLocation</ param-name>
  		<param-value>classpath:springMVC.xml</param-value>
  	</init-param>
  	<!--将前端控制器DispatcherServlet的初始化时间提前到服务器启动时-->
  	<load-on-startup>1</load-on-startup>
  </serv1et>
  <servlet-mapping>
      <servlet-name>springMVC </servlet-name>
      <ur1-pattern>/</ur1-pattern>
  </servlet-mapping>
  ~~~

  > `load-on-startup`标签将前端控制器DispatcherServlet的初始化时间提前到服务器启动时

## 3. 创建控制器并访问主页

> 由于前端控制器对浏览器发送的请求进行了统一的处理， 但是具体的请求有不同的处理过程，因此需要创建处理具体请求的类，即请求控制器，请求控制器中每一个处理请求的方法成为控制器方法。
>
> 因为SpringMVC的控制器由一个POJO (普通的Java类)担任，因此需要通过`@Controller`注解将其标识为一个控制层组件，交给Spring的IOC容器管理，此时SpringMVC才能够识别控制器的存在。

- 在java目录下创建一个包，包下创建HelloController.java类

  ~~~java
  @Controller
  public class HelloController {
      
      // "/"-->/WEB-INF/templates/index.html
      
      @RequestMapping(value ="/")
      public string index(){
          //返回视图名称
          return "index";
      }
  }
  ~~~

  > `@RequestMapping`注解表示处理请求地址映射
  >
  > return的返回值要是跳转页面的名称，不用加后缀和前缀。
  >
  > 当浏览器发送的请求是上下文路径时，就会执行`@RequestMapping`注解所标识的方法。

- 在springMVC.xml文件中开启注解扫描

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
  
      <context:component-scan base-package="com.atguigu.mvc.controller"></context:component-scan>
      
      <!-- 配置Thymeleaf视图解析器 -->
      <bean id="viewResolver" class="org.thymeleaf.spring5.view.ThymeleafViewResolver">
          <property name="order" value="1"/>
          <property name="characterEncoding" value="UTF-8"/>
          <property name="templateEngine">
              <bean class="org.thymeleaf.spring5.SpringTemplateEngine">
                  <property name="templateResolver">
                      <bean class="org.thymeleaf.spring5.templateresolver.SpringResourceTemplateResolver">
  
                          <!-- 视图前缀 -->
                          <property name="prefix" value="/WEB-INF/templates/"/>
  
                          <!-- 视图后缀 -->
                          <property name="suffix" value=".html"/>
                          <property name="templateMode" value="HTML5"/>
                          <property name="characterEncoding" value="UTF-8" />
                      </bean>
                  </property>
              </bean>
          </property>
      </bean>
  
      <!-- 
     处理静态资源，例如html、js、css、jpg
    若只设置该标签，则只能访问静态资源，其他请求则无法访问
    此时必须设置<mvc:annotation-driven/>解决问题
   -->
      <mvc:default-servlet-handler/>
  
      <!-- 开启mvc注解驱动 -->
      <mvc:annotation-driven>
          <mvc:message-converters>
              <!-- 处理响应中文内容乱码 -->
              <bean class="org.springframework.http.converter.StringHttpMessageConverter">
                  <property name="defaultCharset" value="UTF-8" />
                  <property name="supportedMediaTypes">
                      <list>
                          <value>text/html</value>
                          <value>application/json</value>
                      </list>
                  </property>
              </bean>
          </mvc:message-converters>
      </mvc:annotation-driven>
  </beans>
  ~~~

  > 上面配置文件的第20行代码配置试图前缀，`/WEB-INF/templates/`，第23行配置试图后缀`.html`。这就表示我们在`WEB-INF/templates`目录下的以`.html`结尾的文件作为视图文件进行访问呈现。所以我们要在`WEB-INF/templates`目录下创建`index.html`文件。

  [WEB-INF/templates目录下创建index文件：](https://s1.ax1x.com/2022/07/11/j6VeEV.png)

  ​                                                      [![j6VeEV.png](https://s1.ax1x.com/2022/07/11/j6VeEV.png)](https://imgtu.com/i/j6VeEV)

- 接着编写index.html文件

  > 因为Thymeleaf试图解析器需要在html文件中编写名称空间。所以我们可以通过配置代码模板自动生成

  [配置Thymeleaf代码模板：](https://s1.ax1x.com/2022/07/11/j6Vhvj.png)															[<img src="https://s1.ax1x.com/2022/07/11/j6Vhvj.png" alt="j6Vhvj.png" style="zoom: 50%;" />](https://imgtu.com/i/j6Vhvj)

  ~~~html
  <!DOCTYPE html>
  <html lang="en" xmlns:th="http://www.thymeleaf.org">
      <head>
          <meta charset="UTF-8">
          <title>Title</tit1e>
      </head>
      <body>
          <h1>首页</h1>
      </body>
  </html>
  ~~~

- 之后配置Tomcat访问页面
  [访问首页：](https://s1.ax1x.com/2022/07/11/j6mLPf.png)

  ​                                              [<img src="https://s1.ax1x.com/2022/07/11/j6mLPf.png" alt="j6mLPf.png" style="zoom:50%;" />](https://imgtu.com/i/j6mLPf)

  > 通过查看日志我们可以看到映射方法匹配到了刚刚控制器中编写的index()方法，返回视图名称，配上视图解析器中的前缀和后缀，就是我们访问到的index.html页面了

## 4. 访问指定页面

- 改写index.html文件，页面中我们可以通过链接跳转到指定页面

  ~~~html
  <!DOCTYPE html>
  <html lang="en" xmlns:th="http://www.thymeleaf.org">
      <head>
          <meta charset="UTF-8">
          <title>Title</tit1e>
      </head>
      <body>
          <h1>首页</h1>
          <a th:href="@{/target}">访问目标页面target.html</a>
      </body>
  </html>
  ~~~

  > 第9行我们使用绝对路径，但路径要连接上下文路径，即要写为：`"/springMVC/target"`上下文路径就是我们配置tomcat时自定义的默认路径，但这样不够灵活，因为我们已经有了视图解析器，所以可以使用视图解析器来解决。通过以上代码的写法，就可以让视图解析器匹配到合适的路径。

- 创建target.html

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title></title>
  	</head>
  	<body>
  		HelloWorld
  	</body>
  </html>
  ~~~

- 在HelloController.java类中添加跳转方法

  ~~~java
  @Controller
  public class HelloController {
  
      // "/"-->/WEB-INF/templates/index.html
  
      @RequestMapping(value ="/")
      public string index(){
          //返回视图名称
          return "index";
      }
  
      @RequestMapping("/target")
      public string toTarget( ){
          return "target";
      }
  }
  ~~~

  我们启动项目打开浏览器访问首页后点击连接访问：

  [访问跳转页面：](https://s1.ax1x.com/2022/07/11/j6lAKS.png)

  ​                                                   [<img src="https://s1.ax1x.com/2022/07/11/j6lAKS.png" alt="j6lAKS.png" style="zoom:67%;" />](https://imgtu.com/i/j6lAKS)

  > ` @RequestMapping`中的路径一定要是请求访问的路径这里表示，如果浏览器默认请求的是index页面那么这里方法会解析成：
  >
  > `http://localhost:8080/springMVC/WEB-INF/templates/index.html`
  >
  > 如果访问的是跳转页面target那么这里方法会解析成：
  >
  > `http://localhost:8080/springMVC/WEB-INF/templates/target.html`
  >
  > 因为我们使用了视图解析器所以路径前缀和后缀被前端控制器==进行转发==以上两个路径就变为：
  >
  > `http://localhost:8080/springMVC/`和`http://localhost:8080/springMVC/target`

## 5. 总结

> 浏览器发送请求，若请求地址符合前端控制器的url-pattern, 该请求就会被前端控制器DispatcherServlet处理。
> 前端控制器会读取SpringMVC的核心配置文件，通过扫描组件找到控制器，将请求地址和控制器中
> @RequestMapping注解的value属性值进行匹配，若匹配成功，该注解所标识的控制器方法就是处理请求的方
> 法。处理请求的方法需要返回一一个字符串类型的视图名称，该视图名称会被视图解析器解析，加上前缀和后缀组成
> 视图的路径，通过Thymeleaf对视图进行渲染，最终转发到视图所对应页面

# 二. RequestMapping注解

> 从注解名称上我们可以看到，@RequestMapping注解的作用就是将请求和处理请求的控制器方法关联起来,建立映射关系。
> SpringMVC接收到指定的请求,就会来找到在映射关系中对应的控制器方法来处理这个请求。
>
> 一定要保证注解和请求映射之间关系的唯一性。即一个请求只能对应一个映射方法。

## 1. @RequestMapping注解的位置

> @RequestMapping标识一个类：设置映射请求的请求路径的初始信息
> @RequestMapping标识一个方法：设置映射请求请求路径的具体信息

- 先创建一个文件HelloController.java

  ~~~java
  @Controller
  @RequestMapping("/hello")
  public class RequestMappingController {
  
  	//此时请求映射所映射的请求的请求路径为：/hello/testRequestMapping
      @RequestMapping("/testRequestMapping")
      public String testRequestMapping(){
          return "success";
      }
  
  }
  ~~~

- 之后创建index.html页面进行跳转

  ~~~html
  <!DOCTYPE html>
  <html lang="en" xmlns:th="http://www.thymeleaf.org">
      <head>
          <meta charset="UTF-8">
          <title>Title</tit1e>
      </head>
      <body>
          <h1>首页</h1>
          <a th:href="@{/testRequestMapping}">访问目标页面success.html</a>
      </body>
  </html>
  ~~~

- 创建success.html文件

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title></title>
  	</head>
  	<body>
  		HelloWorld
  	</body>
  </html>
  ~~~

  这时我们启动tomcat访问跳转页面，会发现404，这是因为我们在类上添加了`@RequestMapping("/hello")`注解。所以我们跳转的链接就要写为`@{/hello/testRequestMapping}`，代表hello请求下的testRequestMapping请求。

- 修改index.html页面跳转信息

  ~~~html
  <!DOCTYPE html>
  <html lang="en" xmlns:th="http://www.thymeleaf.org">
      <head>
          <meta charset="UTF-8">
          <title>Title</tit1e>
      </head>
      <body>
          <h1>首页</h1>
          <a th:href="@{/hello/testRequestMapping}">访问目标页面success.html</a>
      </body>
  </html>
  ~~~

  启动服务器再次访问：

  [类注解设置访问：](https://s1.ax1x.com/2022/07/11/j6tKw8.png)
                                                                 [<img src="https://s1.ax1x.com/2022/07/11/j6tKw8.png" alt="j6tKw8.png" style="zoom:50%;" />](https://imgtu.com/i/j6tKw8)

## 2. @RequestMapping注解的value属性

> 1. 注解的value属性通过请求的请求地址匹配请求映射
> 2. 注解的value属性是一个==字符串类型的数组==，表示该请求映射能够匹配多个请求地址所对应的请求
> 3. 注解的value属性必须设置，至少通过请求地址匹配请求映射

- 在index.html页面设置多个链接

  ~~~html
  <a th:href="@{/testRequestMapping}">测试@RequestMapping的value属性-->/testRequestMapping</a><br>
  <a th:href="@{/test}">测试@RequestMapping的value属性-->/test</a><br>
  ~~~

- HelloController.java注解配置多个请求映射

  ~~~java
  @Controller
  //@RequestMapping("/hello")
  public class RequestMappingController {
  
  	//此时请求映射所映射的请求的请求路径为：/hello/testRequestMapping
      @RequestMapping( value = {"/testRequestMapping", "/test"})
      public String testRequestMapping(){
          return "success";
      }
  
  }
  ~~~

  运行服务器后可以看到两个链接都能匹配成功。

## 3. @RequestMapping注解的method属性

> 1. 注解的method属性通过请求的请求方式（get或post）匹配请求映射
> 2. 注解的method属性是一个RequestMethod类型的数组，表示该请求映射能够匹配多种请求方式的请求
> 3. 若当前请求的请求地址满足请求映射的value属性，但是请求方式不满足method属性，则浏览器报错405：Request method ‘POST’ not supported。所以说如果设置两个属性，则都要满足

- 在index.html中添加表单提交

  ~~~html
  <a th:href="@{/test}">测试@RequestMapping的value属性-->/test</a><br>
  <form th:action="@{/test}" method="post">
      <input type="submit">
  </form>
  ~~~

- 在HelloController.java类的注解中添加method属性

  ~~~java
  @Controller
  //@RequestMapping("/hello")
  public class RequestMappingController {
  
  	//此时请求映射所映射的请求的请求路径为：/hello/testRequestMapping
      @RequestMapping( value = {"/testRequestMapping", "/test"},
                     method = {RequestMethod.GET, RequestMethod.POST})    
      public String testRequestMapping(){
          return "success";
      }
  
  }
  ~~~

  此时运行可以看到post和get请求都可以访问。

- 派生注解

  > 1. 对于处理指定请求方式的控制器方法，SpringMVC中提供了@RequestMapping的派生注解
  >
  >    处理get请求的映射–>@GetMapping
  >
  >    处理post请求的映射–>@PostMapping
  >
  >    处理put请求的映射–>@PutMapping
  >
  >    处理delete请求的映射–>@DeleteMapping
  >
  > 2. 常用的请求方式有get，post，put，delete
  >
  >    但是目前浏览器只支持get和post，若在form表单提交时，为method设置了其他请求方式的字符串（put或delete），则按照默认的请求方式get处理，若要发送put和delete请求，则需要通过spring提供的过滤器HiddenHttpMethodFilter，在RESTful部分会讲到

  - 使用@GetMapping注解例子

    ~~~java
    @GetMapping("/testGetMapping")
    public string testGetMapping(){
        return "success";
    }
    ~~~

    > `@GetMapping("/testGetMapping")`等同于`@RequestMapping( value = {"/testGetMapping"}, method = {RequestMethod.GET})`

## 4. @RequestMapping注解的params属性（了解）

> 1. 注解的params属性通过请求的请求参数匹配请求映射，如果属性含有多个值，==则都要满足==
> 2. 注解的params属性是一个字符串类型的数组，可以通过四种表达式设置请求参数和请求映射的匹配关系

四种表达式：

|     表达式     |                             描述                             |
| :------------: | :----------------------------------------------------------: |
|    “param”     |        要求请求映射所匹配的请求必须携带param请求参数         |
|    “!param”    |      要求请求映射所匹配的请求必须不能携带param请求参数       |
| “param=value”  |  要求请求映射所匹配的请求必须携带param请求参数且param=value  |
| “param!=value” | 要求请求映射所匹配的请求必须携带param请求参数但是param!=value |

- 在index.html中添加a标签

  ~~~html
  <a th:href="@{/test(username='admin',password=123456)">测试@RequestMapping的params属性-->/test</a><br>
  ~~~

- 在HelloController.java类配置params参数

  ~~~java
  @RequestMapping(
          value = {"/testRequestMapping", "/test"}
          ,method = {RequestMethod.GET, RequestMethod.POST}
          ,params = {"username","password!=123456"}
  )
  public String testRequestMapping(){
      return "success";
  }
  ~~~

  > 若当前请求满足@RequestMapping注解的value和method属性，但是不满足params属性，此时页面回报错：
  >
  > 400：Parameter conditions “username, password!=123456” not met for actual request parameters: username={admin}, password={123456}
  >
  > 如果密码不为123456，username有属性，则成功跳转到success.html页面

## 5. @RequestMapping注解的headers属性（了解）

> 1. 注解的headers属性通过请求的请求头信息匹配请求映射
> 2. 注解的headers属性是一个字符串类型的数组，可以通过四种表达式设置请求头信息和请求映射的匹配关系

四种表达式：

|     表达式      |                             描述                             |
| :-------------: | :----------------------------------------------------------: |
|    “header”     |       要求请求映射所匹配的请求必须携带header请求头信息       |
|    “!header”    |     要求请求映射所匹配的请求必须不能携带header请求头信息     |
| “header=value”  | 要求请求映射所匹配的请求必须携带header请求头信息且header=value |
| “header!=value” | 要求请求映射所匹配的请求必须携带header请求头信息且header!=value |

- 在HelloController.java类配置params参数

  ~~~java
  @RequestMapping(
          value = {"/testRequestMapping", "/test"},
      	headers {"Host=localhost:8081"}
  )
  public String testRequestMapping(){
      return "success";
  }
  ~~~

  > 上面的第3行代码表示：请求头或者响应头中必须包含`Host`属性，且值为`localhost:8081`否则无法访问。
  >
  > 若当前请求满足@RequestMapping注解的value和method属性，但是不满足headers属性，此时页面显示404错误，即资源未找到

## 6. 服务器报错代码

| 错误代码 |                            描述                             |
| :------: | :---------------------------------------------------------: |
|   404    | 没有一个RequestMapping的value属性匹配，或者请求头匹配不成功 |
|   405    |             请求方式在RequestMapping中匹配不到              |
|   400    |                      请求参数匹配不到                       |

## 7. SpringMVC支持ant风格的路径(模糊匹配)

> 1. ？：表示任意的单个字符
> 2. *：表示任意的0个或多个字符
> 3. **：表示任意的一层或多层目录
>
> 注意：在使用`**`时，只能使用`/**/xxx`的方式，不能在`**`前后加字符。如：`/a**/xxx`这种方式不行

- 在index.html中创建新链接

  ~~~html
  <a th:href="@{/a1a/testAnt}">测试@RequestMapping可 以匹配ant风格的路径--></a>
  <a th:href="@{/aaaaaa/testAnt}">测试@RequestMapping可 以匹配ant风格的路径--></a>
  <a th:href="@{/a/a/a/aa/a/testAnt}">测试@RequestMapping可 以匹配ant风格的路径--></a>
  ~~~

- 在HelloController.java类配置value参数

  ~~~java
  @RequestMapping("/a?a/testAnt")
  @RequestMapping("/a*a/testAnt")
  @RequestMapping("/**/testAnt")
  public String testRequestMapping(){
      return "success";
  }
  ~~~

  > 上面的代码分别对应三种匹配方式。

## ==8. SpringMVC支持路径中的占位符==

> 原始传递参数方式：`/deleteUser?id=1`
>
> rest方式：`/deleteUser/1`
>
> SpringMVC路径中的占位符常用于RESTful风格中，当请求路径中将某些数据通过路径的方式传输到服务器中，就可以在相应的@RequestMapping注解的value属性中通过占位符{id}表示传输的数据，再通过@PathVariable注解，将占位符所表示的数据赋值给控制器方法的形参

- 在index.html中添加a标签

  ~~~html
  <a th:href="@{/testPath/1}" >测试@RequestMapping支持路径中的占位符-->/testPath</a><br>
  ~~~

- 在HelloController.java类配置

  ~~~java
  @RequestMapping("/testPath/{id}")
  public string testPath(@PathVariable("id")Integer id){
      System.out.println("id:"+id);
      return "success";
  }
  ~~~

  > 上面的代码第一行获取index.html中`testPath`路径后的值`1`，在第1行使用占位符`{id}`接收，即id=1。再第二行方法参数中使用注解`PathVariable`将获取到的id值赋值给后面的`Integer id`。所以这里的方法有一个默认的参数`id=1`。
  >
  > 注意：这里`/testPath/{id}`表示后面必须跟一个参数，否则会报错404。

  运行结果：

  ~~~shell
  id:1
  ~~~

多层传值

- index.html

  ~~~html
  <a th:href="@{/testPath/1/admin}" >测试@RequestMapping支持路径中的占位符-->/testPath</a><br>
  ~~~

- HelloController.java

  ~~~java
  @RequestMapping("/testPath/{id}/{username}")
  public string testPath(@PathVariable("id")Integer id , @PathVariable("username")String username){
      System.out.println("id:"+id+",username:"+username);
      return "success";
  }
  ~~~

  运行结果：

  ~~~shell
  id:1,username:admin
  ~~~

# 三. SpringMVC获取请求参数

> SpringMVC将一系列的获取参数的方法简化

## 1. 通过ServletAPI获取(原始方法)

> 将HttpServletRequest作为控制器方法的形参，此时HttpServletRequest类型的参数表示封装了当前请求的请求报文的对象

- 在index.html中创建链接并设置请求参数

  ~~~html
  <a th:href="@{/testPath(username='admin',password=123456)}" >
      测试@RequestMapping支持路径中的占位符-->/testPath
  </a><br>
  ~~~

- HelloController.java类中获取参数

  ~~~java
  @RequestMapping("/testParam")
  public String testParam(HttpServletRequest request){
      String username = request.getParameter("username");
      String password = request.getParameter("password");
      System.out.println("username:"+username+",password:"+password);
      return "success";
  }
  ~~~

  运行结果：

  ~~~shell
  username:admin,password:123456
  ~~~

  