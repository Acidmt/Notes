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
  	<!--控制器在哪个包下开启注解扫描-->
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


## 2. 通过控制器方法的形参获取请求参数

> 在控制器方法的形参位置，设置和请求参数同名的形参，当浏览器发送请求，匹配到请求映射时，在DispatcherServlet中就会将请求参数赋值给相应的形参

- 在index.html中添加链接

  ~~~html
  <a th:href="@{/testParam(username='admin',password=123456)}">测试获取请求参数-->/testParam</a><br>
  ~~~

- 在HelloController.java类中获取参数

  ~~~java
  @RequestMapping("/testParam")
  public String testParam(String username, String password){
      System.out.println("username:"+username+",password:"+password);
      return "success";
  }
  ~~~

  运行结果：

  ~~~shell
  username:admin,password:123456
  ~~~

- 传递多个请求参数

  > 注：
  >
  > 1. 若请求所传输的请求参数中有多个同名的请求参数，此时可以在控制器方法的形参中设置字符串数组或者字符串类型的形参接收此请求参数
  >
  > 2. 若使用字符串数组类型的形参，此参数的数组中包含了每一个数据
  >
  > 3. 若使用字符串类型的形参，此参数的值为每个数据中间使用逗号拼接的结果

  - index.html中编写form表单

    ~~~html
    <form th:action="@{/testParam}" method="get" >
        用户名: <input type="text" name="username"><br>
        密码: <input type=" password" name="password"><br>
        爱好: <input type="checkbox" name="hobby" va1ue="a">a
        <input type=" checkbox" name="hobby" value="b">b
        <input type= "checkbox" name="hobby" value="c">c<br>
        <input type=" submit" value="提交">
    </form>
    ~~~

  - 在HelloController.java类中使用字符获取多个参数

    ~~~java
    @RequestMapping("/testParam")
    public String testParam(String username, String password,String hobby){
        System.out.println("username:"+username+",password:"+password+",hobby:"+hobby);
        return "success";
    }
    ~~~

    运行结果：

    ~~~shell
    username:admin,password:123,hobby:a,b,c
    ~~~

  - 在HelloController.java类中使用数组获取多个参数

    ~~~java
    @RequestMapping("/testParam")
    public String testParam(String username, String password,String[] hobby){
        System.out.println("username:"+username+
                           ",password:"+password+
                           ",hobby:"+Arrays.toString(hobby));
        return "success";
    }
    ~~~

    运行结果：

    ~~~shell
    username:admin,password:123,hobby:[a, b, c]
    ~~~

## 3. 注解处理请求参数和控制器方法的形参的映射关系

> 这里有三个注解：@RequestParam、@RequestHeader、@CookieValue
>
> 他们分别表示：请求参数和控制器方法的形参创建映射关系、请求头信息和控制器方法的形参创建映射关系、将cookie数据和控制器方法的形参创建映射关系

### 3.1 @RequestParam注解

> 这里要用到@RequestParam注解：
>
> 1. 该注解是将请求参数和控制器方法的形参创建映射关系。如将方法的形参username匹配请求参数中的user_name的值
> 2. @RequestParam注解一共有三个属性

@RequestParam注解三个属性：

|    属性名    |                             描述                             |
| :----------: | :----------------------------------------------------------: |
|    value     |               指定为形参赋值的请求参数的参数名               |
|   required   |           设置是否必须传输此请求参数，默认值为true           |
| defaultValue | 不管required属性值为true或false，当value所指定的请求参数没有传输或传输的值为""时，则使用默认值为形参赋值 |

> 若required设置为true时，则当前请求必须传输value所指定的请求参数，若没有传输该请求参数，且没有设置defaultValue属性，则页面报错400：Required String parameter ‘xxx’ is not present；
>
> 若设置为false，则当前请求不是必须传输value所指定的请求参数，若没有传输，则注解所标识的形参的值为null

- 修改index.html中参数属性名

  ~~~html
  <form th:action="@{/testParam}" method="get" >
      用户名: <input type="text" name="user_name"><br>
      密码: <input type=" password" name="password"><br>
      爱好: <input type="checkbox" name="hobby" va1ue="a">a
      <input type=" checkbox" name="hobby" value="b">b
      <input type= "checkbox" name="hobby" value="c">c<br>
      <input type=" submit" value="提交">
  </form>
  ~~~

  > 第二行username改为user_name

- 在HelloController.java类中使用@RequestParam匹配参数

  ~~~java
  @RequestMapping("/testParam")
  public String testParam(@RequestParam(value="user_name",required=false,defaultValue="lisi")String username, 
                          String password,
                          String[] hobby){
      System.out.println("username:"+username+
                         ",password:"+password+
                         ",hobby:"+Arrays.toString(hobby);
      return "success";
  }
  ~~~

  此时形参username就可以匹配到user_name的值了

  传递username参数运行结果：

  ~~~shell
  username:admin,password:123,hobby:[a, b, c]
  ~~~

  不传递username参数，不设置defaultValue值运行结果：

  ~~~shell
  username:null,password:123,hobby:[a, b, c]
  ~~~

  不传递username参数，设置defaultValue值运行结果：

  ~~~shell
  username:lisi,password:123,hobby:[a, b, c]
  ~~~

### 3.2 @RequestHeader注解

> 1. 将请求头信息和控制器方法的形参创建映射关系
> 2. 注解一共有三个属性：value、required、defaultValue，用法同@RequestParam

- 在HelloController.java类中使用@RequestHeader匹配参数

  ~~~java
  @RequestMapping("/testParam")
  public String testParam(@RequestParam(value="user_name",required=false,defaultValue="lisi")String username, 
                          String password,
                          String[] hobby,
                         @RequestHeader(value="Host",required="false",defaultValue="kong")String host){
      System.out.println("host:"+host);
      return "success";
  }
  ~~~

  > 上面的第5行代码是将请求头中的Host属性的值复制给host参数。

  运行结果：

  ~~~shell
  host:localhost:8080
  ~~~

### 3.3 @CookieValue注解

> 1. 将cookie数据和控制器方法的形参创建映射关系
> 2. 注解一共有三个属性：value、required、defaultValue，用法同@RequestParam

- 在HelloController.java类中创建又给session模拟cookie(创建session时会将一个属性名为JSESSIONID的属性存在cookie中)

  ~~~java
  @RequestMapping("/testServ1etAPI")
  //形参位置的request表示当前请求
  public string testServletAPI(HttpServletRequest request){
      HttpSession session = request.getSession();
      return "success";
  }
  
  @RequestMapping("/testParam")
  public String testParam(@RequestParam(value="user_name",required=false,defaultValue="lisi")String username, 
                          String password,
                          String[] hobby,
                         @RequestHeader(value="Host",required="false",defaultValue="kong")String host,
                         @CookieValue(value="JSESSIONID")String sessionid){
      System.out.println("sessionid:"+sessionid);
      return "success";
  }
  ~~~

- index.html不用动

  ~~~html
  <a th:href="@{/testPath(username='admin',password=123456)}">
      测试@RequestMapping支持路径中的占位符-->/testPath
  </a><br>
  ~~~

  运行结果：

  ~~~shell
  sessionid:PBE437229E25FA34093EAC709CFBE4E1
  ~~~

## 4. 通过POJO获取请求参数

> 可以在控制器方法的形参位置设置一个实体类类型的形参，此时若浏览器传输的请求参数的参数名和实体类中的属性名一致，那么请求参数就会为此属性赋值

- 在index.html中编写一个表单

  ~~~html
  <form th:action="@{/testpojo}" method="post">
      用户名：<input type="text" name="username"><br>
      密码：<input type="password" name="password"><br>
      性别：<input type="radio" name="sex" value="男">男<input type="radio" name="sex" value="女">女<br>
      年龄：<input type="text" name="age"><br>
      邮箱：<input type="text" name="email"><br>
      <input type="submit">
  </form>
  ~~~

- 创建实体类User.java

  > 注意实体类中的字段要和表单中的字段对应。

- 在HelloController.java类中接收表单提交的参数

  ~~~java
  @RequestMapping("/testBean")
  public string testBean(User user,User userInfo){
      System.out.println(user);
      return "success";
  }
  ~~~

  运行结果：

  ~~~shell
  User{id=null, username='admin',password='123',age=23,sex='男',email='123@qq.com'}
  ~~~

  > 注意：userInfo对象输出结果和user一样，这表示SpirngMVC的控制器会把实体参数默认传给多个形参。

## ==5. 解决获取请求参数的乱码问题==(编码过滤器)

> 在SpringMVC中处理乱码问题，不能通过request对象设置字符集解决，因为在字符集生效之前，SpringMVC的前端控制器DispatcherServlet已经获取上下文。所以我们只能通过==监听器(最早进行初始化)或这过滤器来进行设置==，一般都是用过滤器。SpringMVC中已经提供过滤器方法，所以我们只需要在web.xml进行配置就可以使用。

- 配置web.xml设置编码

  ~~~xml
  <!--配置springMVC的编码过滤器-->
  <filter>
      <filter-name>CharacterEncodingFilter</filter-name>
      <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
      <!--设置请求编码-->
      <init-param>
          <param-name>encoding</param-name>
          <param-value>UTF-8</param-value>
      </init-param>
      <!--设置响应编码-->
      <init-param>
          <param-name>forceResponseEncoding</param-name>
          <param-value>true</param-value>
      </init-param>
  </filter>
  <filter-mapping>
      <filter-name>CharacterEncodingFilter</filter-name>
      <url-pattern>/*</url-pattern>
  </filter-mapping>
  ~~~

# 四. 域对象获取共享数据

四种域对象

|     对象名     |                             描述                             |
| :------------: | :----------------------------------------------------------: |
|  pageContext   |                  page域，范围是一个jsp页面                   |
|    request     |                        范围是一次会话                        |
|    session     | 范围是浏览器窗口关闭，与服务器是否关闭没有关系(因为有活化和钝化) |
| ServletContext |     范围是整个服务器开启到关闭，与浏览器是否关闭没有关系     |

## 1. request域对象共享数据

### 1.1 使用ServletAPI向request域对象共享数据

- 在index.html中创建链接访问

  ~~~html
  <body>
      <h1>首页</h1>
      <a th:href="@{/testRequesitByServletAPI}">通过servletAPI向request域对象共享数据</a>
  </body>
  ~~~

- 在success.html中获取request域的值

  ~~~html
  <body>
      success<br>
      <p th:text="${testRequestScope]}"></p>
  </body>
  ~~~

- 在HelloController.java类放入request域值

  ~~~java
  //使用servLetAPI向request域对象共享数据
  @RequestMapping("/testRequestByServletAPI")
  public string testRequestByServletAPI(HttpServletRequest request){
      request. setAttribute("testRequestScope","hello, servletAPI");
      return "success";
  }
  ~~~

  运行结果：

  [request域取值结果：](https://s1.ax1x.com/2022/07/13/jRTTKg.png)
                                      [<img src="https://s1.ax1x.com/2022/07/13/jRTTKg.png" alt="jRTTKg.png" style="zoom:50%;" />](https://imgtu.com/i/jRTTKg)

### 1.2 使用ModelAndView向request域对象共享数据(官方推荐)

> 1. 方法返回值必须是ModelAndView对象。
> 2. 向request域共享数据的四种方法本质上都是ModelAndView模型
> 3. Model主要用于向请求域共享数据，View主要用于设置视图，实现页面跳转

- 在index.html中创建超链接

  ~~~html
  <a th:href="@{/testModelAndView}">通过ModelAndView向request域对象共享数据</a><br>
  ~~~

- 编写HelloController.java类获取request对象数据

  ~~~java
  @RequestMapping("/testModelAndView")
  public ModelAndView testModelAndView(){
      /**
       * ModelAndView有Model和View的功能
       * Model主要用于向请求域共享数据
       * View主要用于设置视图，实现页面跳转
       */
      ModelAndView mav = new ModelAndView();
      //向请求域共享数据
      mav.addObject("testScope","hello,ModelAndView");
      //设置视图，实现页面跳转
      mav.setViewName("success");
      return mav;
  }
  ~~~

  > 第10行代码是Model层，使用`addObject`方法向request域中添加一对数据
  >
  > 第12行代码是View层，主要用于跳转到success页面。相当于之前的`return "success"`

  运行结果：

  [mav获取request域对象值：](https://s1.ax1x.com/2022/07/13/jR7bQO.png)

  ​                                            [<img src="https://s1.ax1x.com/2022/07/13/jR7bQO.png" alt="jR7bQO.png" style="zoom:50%;" />](https://imgtu.com/i/jR7bQO)

### 1.3 使用Model向request域对象共享数据

- 在index.html中添加链接

  ~~~html
  <a th:href="@{/testModel}">通过Model向request域对象共享数据</a><br>
  ~~~

- 编写HelloController.java类获取request对象数据

  ~~~java
  @RequestMapping("/testModel")
  public String testModel(Model model){
      model.addAttribute("testScope", "hello,Model");
      return "success";
  }
  ~~~

  运行结果：

  [Model运行结果：](https://s1.ax1x.com/2022/07/14/jfi1Ld.png)

  ​                                                 [<img src="https://s1.ax1x.com/2022/07/14/jfi1Ld.png" alt="jfi1Ld.png" style="zoom:50%;" />](https://imgtu.com/i/jfi1Ld)

### 1.4 使用map向request域对象共享数据

- index.html

  ~~~html
  <a th:href="@{/testMap}" >通过map向request域对象共享数据</a><br>
  ~~~

- 编写HelloController.java类获取request对象数据

  ~~~java
  @RequestMapping("/testMap")
  public String testMap(Map<String, Object> map){
      map.put("testScope", "hello,Map");
      return "success";
  }
  ~~~

  运行结果：
  [map获取数据：](https://s1.ax1x.com/2022/07/14/jfiyoq.png)

  ​                                                                 [<img src="https://s1.ax1x.com/2022/07/14/jfiyoq.png" alt="jfiyoq.png" style="zoom:50%;" />](https://imgtu.com/i/jfiyoq)

### 1.5 使用ModelMap向request域对象共享数据

- index.html

  ~~~html
  <a th:href="@{/testModelMap}" >通过ModelMap向request域对象共享数据</a><br>
  ~~~

- 编写HelloController.java类获取request对象数据

  ~~~java
  @RequestMapping("/testModelMap")
  public String testModelMap(ModelMap modelMap){
      modelMap.addAttribute("testScope", "hello,ModelMap");
      return "success";
  }
  ~~~

  运行结果：
  [ModelMap获取数据：](https://s1.ax1x.com/2022/07/14/jfiIm9.png)
                                                         [<img src="https://s1.ax1x.com/2022/07/14/jfiIm9.png" alt="jfiIm9.png" style="zoom:50%;" />](https://imgtu.com/i/jfiIm9)

### 1.6 Model、ModelMap、Map的关系

> Model、ModelMap、Map类型的参数其实本质上都是 BindingAwareModelMap 类型的

~~~java
public interface Model{}            									//是一个接口
public class ModelMap extends LinkedhashMap<String,Object>{}            //继承了LinkedHashMap
public class ExtendedModelMap extends MOdelMap implements Model{}       //继承了ModelMap又实现了Model接口
public class BindingAwareModelMap{}  				//这个类对应的子类，就可以去实例化ModelMap也可以实例化Model
//因为ModelMap继承了LinkedHashMap所以说，BindingAwareModelMap也可以实例化Map集合
~~~

> 总结：
> 无论哪一种获取共享数据的方法都是ModelAndView模型。其返回结果是model：网页名称(success)和view：网页内容。

[ModelAndView模型：](https://s1.ax1x.com/2022/07/14/jfkKDH.png)

​								[<img src="https://s1.ax1x.com/2022/07/14/jfkKDH.png" alt="jfkKDH.png" style="zoom: 67%;" />](https://imgtu.com/i/jfkKDH)

## 2. 向session域共享数据

> 虽然SpringMVC提供了session共享数据的方法，但比较麻烦。所以这里建议使用原生SevletAPI

- index.html中添加链接

  ~~~html
  <a th: href="@{/testSession}">通过servletAPI向session域对象共享数据</a><br>
  ~~~

- 在success.html中呈现session中存放的数据

  ~~~html
  <body>
      success<br>
      <p th:text="${session.testSessionScope)}"></p>
  </body>
  </html>
  ~~~

  > 注意在thy中获取session域值要使用`session.数据名`的方式。

- 编写HelloController.java类获取request对象数据

  ~~~java
  @RequestMapping( "/testSession")
  public String testSession(HttpSession session){
      session.setAttribute("testSessionScope","hello, session");
      return "success";
  }
  ~~~

  [获取session域数据：](https://s1.ax1x.com/2022/07/14/jfAcFI.png)
                                                   [<img src="https://s1.ax1x.com/2022/07/14/jfAcFI.png" alt="jfAcFI.png" style="zoom:50%;" />](https://imgtu.com/i/jfAcFI)

## 3. 向application域(ServletContext)共享数据

- index.html

  ~~~html
  <a th:href="@{/testApplication}">通过servletAPI向application域对象共享数据</a><br>
  ~~~

- 编写HelloController.java类获取request对象数据

  ~~~java
  @RequestMapping("/testApplication")
  public String testApplication(HttpSession session){
  	ServletContext application = session.getServletContext();
      application.setAttribute("testApplicationScope", "hello,application");
      return "success";
  }
  ~~~

  运行结果：
  [ServletContext域获取对象：](https://s1.ax1x.com/2022/07/14/jfEkp6.png) 

  ​                                               [<img src="https://s1.ax1x.com/2022/07/14/jfEkp6.png" alt="jfEkp6.png" style="zoom:50%;" />](https://imgtu.com/i/jfEkp6)

# 五. SpringMVC的视图

> SpringMVC中的视图是View接口，视图的作用渲染数据，将模型Model中的数据展示给用户。
>
> SpringMVC视图的种类很多，默认有转发视图和重定向视图，但当工程引入jstl的依赖，转发视图会自动转换为JstlView。
>
> 若使用的视图技术为Thymeleaf，在SpringMVC的配置文件中配置了Thymeleaf的视图解析器，由此视图解析器解析之后所得到的是ThymeleafView

## 1. ThymeleafView

> 当控制器方法中所设置的视图名称==没有任何前缀时==，此时的视图名称会被SpringMVC配置文件中所配置的视图解析器解析，视图名称拼接视图前缀和视图后缀所得到的最终路径，会通过转发的方式实现跳转

- 在index.html中创建链接

  ~~~html
  <a th:href="@{/testThymeleafView}">测试ThymeleafView</a><br>
  ~~~

- 编写HelloController.java类创建ThymeleafView视图

  ~~~java
  @RequestMapping("/testHello")
  public String testHello(){
      return "hello";
  }
  ~~~

  > 上面的return直接返回hello没有前缀，所以使用的是ThymeleafView视图

## 2. 转发视图

> SpringMVC中默认的转发视图是InternalResourceView
>
> 当控制器方法中所设置的视图名称==以"forward:"为前缀时==，创建InternalResourceView视图，此时的视图名称不会被SpringMVC配置文件中所配置的视图解析器解析，而是会将前缀"forward:"去掉，剩余部分作为最终路径通过转发的方式实现跳转
>
> 如：例如"forward:/"，“forward:/employee”

- index.html

  ~~~html
  <a th:href="@{/testForward}">测试InternalResourceView</a><br>
  ~~~

- 编写HelloController.java类创建测试InternalResourceView视图

  ~~~java
  @RequestMapping("/testHello")
  public String testHello(){
      return "hello";
  }
  
  @RequestMapping("/testForward")
  public String testForward(){
      return "forward:/testHello";
  }
  ~~~

  > 当我们进行testForward请求时，会通过testForward()方法转发testHello请求。
  >
  > 所以此时启动服务器访问testForward会发现地址是testForward但内容是testHello页面的。

## 3. 重定向视图

> SpringMVC中默认的重定向视图是RedirectView。
>
> 当控制器方法中所设置的视图名称以"redirect:"为前缀时，创建RedirectView视图，此时的视图名称不会被SpringMVC配置文件中所配置的视图解析器解析，而是会将前缀"redirect:"去掉，剩余部分作为最终路径通过重定向的方式实现跳转。
>
> 例如："redirect:/"，“redirect:/employee”

- index.html

  ~~~html
  <a th:href="@{/testRedirect}" >测试RedirectView</a><br>
  ~~~

- 编写HelloController.java类创建测试测试RedirectView视图

  ~~~java
  @RequestMapping("/testHello")
  public String testHello(){
      return "hello";
  }
  
  @RequestMapping("/testRedirect")
  public String testRedirect(){
      return "redirect:/testHello";
  }
  ~~~

  > 此时访问testRedirect请求会将页面请求转发为testHello请求。此时地址也会改变。
  >
  > 注：重定向视图在解析时，会先将redirect:前缀去掉，然后会判断剩余部分是否以/开头，若是则会自动拼接上下文路径


## 4. 视图控制器view-controller

> 当控制器方法中，仅仅用来实现页面跳转，即只需要设置视图名称时，没有其他的处理方法时可以将处理器方法使用view-controller标签进行表示

以下可以用`view-controller`替代

~~~java
@RequestMapping("/")
public String testHello(){
    return "index";
}
~~~

替换配置要在SpringMVC.xml文件中配置

~~~xml
<beans>
    <mvc:view-controller path="/" view-name="index"></mvc:view-controller>
</beans>
~~~

> path：设置处理的请求地址
>
> view-name：设置请求地址所对应的视图名称
>
> 当SpringMVC中设置任何一个view-controller时，其他控制器中的请求映射将全部失效，此时需要在SpringMVC的核心配置文件中设置开启mvc注解驱动的标签：`<mvc:annotation-driven />`来开启MVC的注解驱动。

~~~xml
<beans>
    <mvc:view-controller path="/" view-name="index"></mvc:view-controller>
    <!--开启MVC的注解驱动-->
    <mvc:annotation-driven />
</beans>
~~~

## 5. 视图解析器：InternalResourceViewResolver

> SpringMVC解析JSP视图需要在SpringMVC.xml文件中配置InternalResourceViewResolver解析器

- SpringMVC.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
      <!--控制器在哪个包下生效-->
      <context:component-scan base-package="com.atguigu.mvc.controller"></context:component-scan>
  
      <!--配置JSP视图解析器-->
      <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
          <property name="prefix" value="/WEB-INF/templates/*"></property>
          <property name="suffix" value=".jsp"></property>
      </bean>
  
  </beans>
  ~~~

- 编写index.jsp

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Title</title>
      </head>
      <body>
          <h1>首页</h1>
          <a href= "${pageContext.request.contextPathi}/success">success.jsp</a>
      </body>
  </html>
  ~~~

  > 第8行使用EL表达式发送请求。

- 编写JspController.java类，处理访问success.jsp请求页面

  ~~~java
  @Controller
  public class JspController {
      @RequestMapping("/success")
      public string success(){
          return "success"
      }
  }
  ~~~

- 编写success.jsp页面

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Title</title>
      </head>
      <body>
          成功
      </body>
  </html>
  ~~~

  运行结果：

  [JSP视图运行结果：](https://s1.ax1x.com/2022/07/15/jhZ4r8.png)

  ​                                                     [<img src="https://s1.ax1x.com/2022/07/15/jhZ4r8.png" alt="jhZ4r8.png" style="zoom:50%;" />](https://imgtu.com/i/jhZ4r8)

# 六. RESTful

> 简介：REST：Representational State Transfer，表现层资源状态转移。是一种项目工程风格。
>
> 其有三类：
>
> 1. 资源：资源是一种看待服务器的方式，即，将服务器看作是由很多离散的资源组成。每个资源是服务器上一个可命名的抽象概念。因为资源是一个抽象的概念，所以它不仅仅能代表服务器文件系统中的一个文件、数据库中的一张表等等具体的东西，可以将资源设计的要多抽象有多抽象，只要想象力允许而且客户端应用开发者能够理解。与面向对象设计类似，资源是以名词为核心来组织的，首先关注的是名词。一个资源可以由一个或多个URI来标识。URI既是资源的名称，也是资源在Web上的地址。对某个资源感兴趣的客户端应用，可以通过资源的URI与其进行交互。
> 2. 资源的表述：资源的表述是一段对于资源在某个特定时刻的状态的描述。可以在客户端-服务器端之间转移（交换）。资源的表述可以有多种格式，例如HTML/XML/JSON/纯文本/图片/视频/音频等等。资源的表述格式可以通过协商机制来确定。请求-响应方向的表述通常使用不同的格式。
> 3. 状态转移：状态转移说的是：在客户端和服务器端之间转移（transfer）代表资源状态的表述。通过转移和操作资源的表述，来间接实现操作资源的目的。

## 1. RESTful的实现

> 具体说，就是 HTTP 协议里面，四个表示操作方式的动词：GET、POST、PUT、DELETE。
>
> 它们分别对应四种基本操作：GET 用来获取资源，POST 用来新建资源，PUT 用来更新资源，DELETE 用来删除资源。
>
> REST 风格提倡 URL 地址使用统一的风格设计，从前到后各个单词使用斜杠分开，不使用问号键值对方式携带请求参数，而是将要发送给服务器的数据作为 URL 地址的一部分，以保证整体风格的一致性。

RESTful风格：

|   操作   |     传统方式     |        REST风格        |
| :------: | :--------------: | :--------------------: |
| 查询操作 | getUserById?id=1 |  user/1–>get请求方式   |
| 保存操作 |     saveUser     |   user–>post请求方式   |
| 删除操作 | deleteUser?id=1  | user/1–>delete请求方式 |
| 更新操作 |    updateUser    |   user–>put请求方式    |

## 2. HiddenHttpMethodFilter发送put和delete请求

> 由于浏览器只支持发送get和post方式的请求，我们需要用HiddenHttpMethodFilter来发送put和delete请求。
>
> 处理put和delete请求的条件：
>
> 1. 当前请求的请求方式必须为post
> 2. 当前请求必须传输请求参数_method
>
> 满足以上条件，HiddenHttpMethodFilter 过滤器就会将当前请求的请求方式转换为请求参数`_method`的值，因此请求参数`_method`的值才是最终的请求方式

在web.xml中注册HiddenHttpMethodFilter：

~~~xml
<filter>
    <filter-name>HiddenHttpMethodFilter</filter-name>
    <filter-class>org.springframework.web.filter.HiddenHttpMethodFilter</filter-class>
</filter>
<filter-mapping>
    <filter-name>HiddenHttpMethodFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
~~~

> ==小技巧：可以编写一个filter的实现类，然后通过控制器继承实现类，然后调用实现类中的dofilter方法，实现偷梁换柱。==

- 编写index.html

  ~~~html
  <body>
      <form th: action="@{/user}" method="post">
          < input type="hidden" name=" method" value="PUT" >
          用户名: <input type= "text" name= "username"><br>
          密码: <input type="password" name= "password"><br>
          <input type="submit" value="修改"><br>
      </form>
  </body>
  ~~~

- 编写HelloController.java类获取PUT请求

  ~~~java
  @RequestMapping(value ="/user",method = RequestMethod.PUT)
  public string updateuser(String username, String password){
      System.out.println("修改用户信息："+username+","+password);
      return" success" ;
  }
  ~~~

  运行结果：

  ~~~shell
  修改用户信息：admin,123
  ~~~

  > 注意：目前为止，SpringMVC中提供了两个过滤器：CharacterEncodingFilter和HiddenHttpMethodFilter。在web.xml中注册时，必须先注册CharacterEncodingFilter，再注册HiddenHttpMethodFilter

# ==七. RESTful案例==

> 我们用RESTful实现增删改查

## 1. 准备工作

功能清单

| 功能                | URL 地址    | 请求方式 |
| ------------------- | ----------- | -------- |
| 访问首页√           | /           | GET      |
| 查询全部数据√       | /employee   | GET      |
| 删除√               | /employee/2 | DELETE   |
| 跳转到添加数据页面√ | /toAdd      | GET      |
| 执行保存√           | /employee   | POST     |
| 跳转到更新数据页面√ | /employee/2 | GET      |
| 执行更新√           | /employee   | PUT      |

### 1.1 配置项目文件

- 配置web.xml文件

  ~~~xml
  <web-app>
      <!--配置编码过滤器-->
      <filter>
          <filter-name>CharacterEncodingFilter</ filter-name>
          <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
          <init- param>
              <param- name>encoding</ param-name>
              <param-va1ue>UTF-8</ param-value>
              </init-param>
          <init-param>
              <param- name>forceResponseEncoding</ param-name>
              <param-value>true</ param-value>
          </init-param>
      </filter>
      <filter-mapping>
          <filter-name>CharacterEncodingFilter</filter-name>
          <url-pattern>/*</url-pattern>
      </filter-mapping>
  
      <!--配置处理请求方式put和delete的Hi ddenHt tpMethodFilter-->
      <filter>
          <filter-name>HiddenHttpMethodFilter</ filter-name>
          <filter-class>org.springframework.web.filter.HiddenHttpMethodFilter</filter-class>
      </filter>
      <filter-mapping>
          <filter-name>HiddenHttpMethodFilter</ filter-name>
          <url-pattern>/*</url-pattern>
      </filter-mapping>
  
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
  </web-app>
  ~~~

- 配置SpringMVC.xml文件

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
      <!--控制器在哪个包下开启注解扫描-->
      <context:component-scan base-package="com.atguigu.mvc.controller,com.atguigu.mvc.dao">
      </context:component-scan>
  
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
  
      <!--配置视图控制器-->
      <mvc:view-controller path= "/" view-name="index"></mvc:view-controller>
      <!--开启mvc注解驱动-->
      <mvc:annotation-driven/>
  
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

### 1.2 创建bean层

- 编写实体类Employee.java

  ~~~java
  package com.atguigu.mvc.bean;
  
  public class Employee {
  
     private Integer id;
     private String lastName;
  
     private String email;
     //1 male, 0 female
     private Integer gender;
     
     public Integer getId() {
        return id;
     }
  
     public void setId(Integer id) {
        this.id = id;
     }
  
     public String getLastName() {
        return lastName;
     }
  
     public void setLastName(String lastName) {
        this.lastName = lastName;
     }
  
     public String getEmail() {
        return email;
     }
  
     public void setEmail(String email) {
        this.email = email;
     }
  
     public Integer getGender() {
        return gender;
     }
  
     public void setGender(Integer gender) {
        this.gender = gender;
     }
  
     public Employee(Integer id, String lastName, String email, Integer gender) {
        super();
        this.id = id;
        this.lastName = lastName;
        this.email = email;
        this.gender = gender;
     }
  
     public Employee() {
     }
  }
  ~~~

### 1.3 创建Dao层

- 编写工具类EmployeeDao.java

  ~~~java
  package com.atguigu.mvc.dao;
  
  import java.util.Collection;
  import java.util.HashMap;
  import java.util.Map;
  
  import com.atguigu.mvc.bean.Employee;
  import org.springframework.stereotype.Repository;
  
  
  @Repository
  public class EmployeeDao {
  
     private static Map<Integer, Employee> employees = null;
     
     static{
        employees = new HashMap<Integer, Employee>();
  
        employees.put(1001, new Employee(1001, "E-AA", "aa@163.com", 1));
        employees.put(1002, new Employee(1002, "E-BB", "bb@163.com", 1));
        employees.put(1003, new Employee(1003, "E-CC", "cc@163.com", 0));
        employees.put(1004, new Employee(1004, "E-DD", "dd@163.com", 0));
        employees.put(1005, new Employee(1005, "E-EE", "ee@163.com", 1));
     }
     
     private static Integer initId = 1006;
     //添加用户信息
     public void save(Employee employee){
        if(employee.getId() == null){
           employee.setId(initId++);
        }
        employees.put(employee.getId(), employee);
     }
     //获取所有员工信息
     public Collection<Employee> getAll(){
        return employees.values();
     }
     //获取某个员工信息
     public Employee get(Integer id){
        return employees.get(id);
     }
     //删除某个员工信息
     public void delete(Integer id){
        employees.remove(id);
     }
  }
  ~~~

### 1.4 创建controller

- 编写EmployeeController.java

  ~~~java
  @Controller
  public class EmployeeController {
      @Autowired
      private EmployeeDao employeeDao ;
  }
  ~~~
  
  > @Controller：告知Spring这是一个控制器
  >
  > @Autowired：自动装配

## 2. 具体功能

- 在templates目录下创建index.html页面作为主页

  ~~~html
  <!DOCTYPE html>
  <html lang="en" xmlns:th="http://www.thymeleaf.org">
      <head>
          <meta charset="UTF-8">
          <title>首页</title>
      </head>
      <body>
          <h1>首页</h1>
          <a th:href="@{/employee}">查看员工信息</a>
      </body>
  </html>
  ~~~

- 在SpringMVC.xml中配置视图控制器，开启MVC注解驱动。(可以直接访问首页，不用写控制器)

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
      <!--控制器在哪个包下开启注解扫描-->
      <context:component-scan base-package="com.atguigu.mvc.controller,com.atguigu.mvc.dao">
      </context:component-scan>
  
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
  
      <!--配置视图控制器-->
      <mvc:view-controller path= "/" view-name="index"></mvc:view-controller>
  
      <!--开放对静态资源的访问-->
      <mvc:default-servlet-handler/>
      
      <!--开启mvc注解驱动-->
      <mvc:annotation-driven/>
  
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

### 2.1 查询所有员工数据

- 在EmployeeController.java中编写控制器方法

  ~~~java
  @Controller
  public class EmployeeController {
      @Autowired
      private EmployeeDao employeeDao;
      @RequestMapping(value = "/employee", method =RequestMethod.GET)
      public String getAllEmployee(){
          collection<Employee> employeelist = employeeDao.getAll();
          model.addAttribute("employeeList",employeelist);
          return "emp1oyee_list";
      }
  }
  ~~~
  
- 创建emp1oyee_list.html页面展示员工信息查询结果

  ~~~html
  <!DOCTYPE html>
  <html lang="en" xmlns:th="http://www.thymeleaf.org">
      <head>
          <meta charset="UTF-8">
          <title>Employee Info</title>
      </head>
      <body>
          <table border= "1" cellspacing="0" cel1padding="0" style="text-align:center;" id="dataTable">
              <tr>
                  <th colspan="5">Employee Info</th>
              </tr>
              <tr>
                  <th>id</th>
                  <th> lastName</th>
                  <th>email</th>
                  <th>gender</th>
                  <th>options</th>
              </tr>
              <tr th:each="employee:${employeelist}">
                  <td th:text="${employee.id}"></td>
                  <td th:text="${employee.lastName}"></td>
                  <td th:text="${employee.email}"></td>
                  <td th:text="${employee.gender}"></td>
                  <td>
                      <a href="">delete</a>
                      <a href="">update</a>
                  </td>
              </tr>
          </table>
          
      </body>
  </html>
  ~~~

  点击`查看员工信息`链接显示结果

  [案例查询员工结果：](https://s1.ax1x.com/2022/07/16/j5BPfJ.png)

  ​                                                    [<img src="https://s1.ax1x.com/2022/07/16/j5BPfJ.png" alt="j5BPfJ.png" style="zoom: 67%;" />](https://imgtu.com/i/j5BPfJ)

### 2.2 删除指定员工信息

- 在emp1oyee_list.html页面25行添加代码完善删除请求功能

  ~~~html
  <a th:href="@{'employee/'+${employee.id}}">delete</a>
  <!--或者写为以下形式：-->
  <a th:href="@{'/employee/'+${employee.id}}">delete</a>
  ~~~

  接着在第30行编写form表单，因为`DELETE`请求必须传递参数，所以这里使用隐藏表单在点击超链接的同时提交表单。

  ~~~html
  <!-- 作用：通过超链接控制表单的提交，将post请求转换为delete请求 -->
  <form id="delete_form" method="post">
      <!-- HiddenHttpMethodFilter要求：必须传输_method请求参数，并且值为最终的请求方式 -->
      <input type="hidden" name="_method" value="delete"/>
  </form>
  ~~~

- 超链接绑定点击事件，这里用vue

  在编写的表单后面引入vue.js

  ~~~html
  <script type="text/javascript" th:src="@{/static/js/vue.js}"></script>
  ~~~

  接着在后面编写vue处理点击提交事件

  ~~~html
  <script type="text/javascript">
      var vue = new Vue({
          el:"#dataTable",
          methods:{
              //event表示当前事件
              deleteEmployee:function (event) {
                  //通过id获取表单标签
                  var delete_form = document.getElementById("delete_form");
                  //将触发事件的超链接的href属性为表单的action属性赋值
                  delete_form.action = event.target.href;
                  //提交表单
                  delete_form.submit();
                  //阻止超链接的默认跳转行为
                  event.preventDefault();
              }
          }
      });
  </script>
  ~~~

- EmployeeController.java中编写控制器

  ~~~java
  @RequestMapping(value = "/employee/{id}", method = RequestMethod.DELETE)
  public String deleteEmployee(@PathVariable("id") Integer id){
      employeeDao.delete(id);
      return "redirect:/employee";
  }
  ~~~

- 因为导入了新的静态资源，所以项目重新打包
  [项目重新打包：](https://s1.ax1x.com/2022/07/16/j5sqEV.png)                           [<img src="https://s1.ax1x.com/2022/07/16/j5sqEV.png" alt="j5sqEV.png" style="zoom: 50%;" />](https://imgtu.com/i/j5sqEV)

  同时在SpringMVC.xml中开放对静态资源的访问

  ~~~xml
  <!--开放对静态资源的访问-->
  <mvc: default-servlet-handler/>
  ~~~

  运行结果：

  [删除id为1001后表格：](https://s1.ax1x.com/2022/07/16/j5sjCF.png)
                                                             [<img src="https://s1.ax1x.com/2022/07/16/j5sjCF.png" alt="j5sjCF.png" style="zoom:50%;" />](https://imgtu.com/i/j5sjCF)

### 2.3 跳转到添加数据页面

- 在SpringMVC.xml的第35行添加页面请求控制器

  ~~~xml
  <mvc:view-controller path="/toAdd" view-name="employee_add"></mvc:view-controller>
  ~~~

- 创建employee_add.html

  ~~~html
  <!DOCTYPE html>
  <html lang="en" xmlns:th="http://www.thymeleaf.org">
      <head>
          <meta charset="UTF-8">
          <title>Add Employee</title>
      </head>
      <body>
  
          <form th:action="@{/employee}" method="post">
              lastName:<input type="text" name="lastName"><br>
              email:<input type="text" name="email"><br>
              gender:<input type="radio" name="gender" value="1">male
              <input type="radio" name="gender" value="0">female<br>
              <input type="submit" value="add"><br>
          </form>
  
      </body>
  </html>
  ~~~

- 控制器方法

  ~~~java
  @RequestMapping(value = "/employee", method = RequestMethod.POST)
  public String addEmployee(Employee employee){
      employeeDao.save(employee);
      return "redirect:/employee";
  }
  ~~~

  运行结果：
  [添加用户信息：](https://s1.ax1x.com/2022/07/16/j5yG8g.png)
                                                                      [<img src="https://s1.ax1x.com/2022/07/16/j5yG8g.png" alt="j5yG8g.png" style="zoom:50%;" />](https://imgtu.com/i/j5yG8g)

  [完成添加后的表格：](https://s1.ax1x.com/2022/07/16/j5yJ2Q.png)

​                                                                      [<img src="https://s1.ax1x.com/2022/07/16/j5yJ2Q.png" alt="j5yJ2Q.png" style="zoom:50%;" />](https://imgtu.com/i/j5yJ2Q)

### 2.4 跳转到更新数据页面

- 在emp1oyee_list.html的第26行添加修改信息请求

  ~~~html
  <a th:href="@{'/employee/'+${employee.id}}">update</a>
  ~~~

- 编写控制器方法

  ~~~java
  @RequestMapping(value = "/employee/{id}", method = RequestMethod.GET)
  public String getEmployeeById(@PathVariable("id") Integer id, Model model){
      Employee employee = employeeDao.get(id);
      model.addAttribute("employee", employee);
      return "employee_update";
  }
  ~~~

- 跳转到employee_update.html页面

  ~~~html
  <!DOCTYPE html>
  <html lang="en" xmlns:th="http://www.thymeleaf.org">
  <head>
      <meta charset="UTF-8">
      <title>Update Employee</title>
  </head>
  <body>
  
  <form th:action="@{/employee}" method="post">
      <input type="hidden" name="_method" value="put">
      <input type="hidden" name="id" th:value="${employee.id}">
      lastName:<input type="text" name="lastName" th:value="${employee.lastName}"><br>
      email:<input type="text" name="email" th:value="${employee.email}"><br>
      gender:<input type="radio" name="gender" value="1" th:field="${employee.gender}">male
      <input type="radio" name="gender" value="0" th:field="${employee.gender}">female<br>
      <input type="submit" value="update"><br>
  </form>
  
  </body>
  </html>
  ~~~

  > `th:field="${employee.gender}"`可用于单选框或复选框的回显。若单选框的value和employee.gender的值一致，则添加`checked="checked"`属性。其余的都是根据请求域回显设置默认值。

- 编写控制器执行更新

  ~~~java
  @RequestMapping(value = "/employee", method = RequestMethod.PUT)
  public String updateEmployee(Employee employee){
      employeeDao.save(employee);
      return "redirect:/employee";
  }
  ~~~

  运行结果：
  [修改id为1001信息前：](https://s1.ax1x.com/2022/07/16/j56Go6.png)

  ​                                               [<img src="https://s1.ax1x.com/2022/07/16/j56Go6.png" alt="j56Go6.png" style="zoom:50%;" />](https://imgtu.com/i/j56Go6)

  [修改信息：](https://s1.ax1x.com/2022/07/16/j56YFK.png)

  ​                                               [<img src="https://s1.ax1x.com/2022/07/16/j56YFK.png" alt="j56YFK.png" style="zoom:50%;" />](https://imgtu.com/i/j56YFK)

  [修改成功后表格：](https://s1.ax1x.com/2022/07/16/j56NWD.png)

  ​                                               [<img src="https://s1.ax1x.com/2022/07/16/j56NWD.png" alt="j56NWD.png" style="zoom:50%;" />](https://imgtu.com/i/j56NWD)

# 八. HttpMessageConverter

> HttpMessageConverter，报文信息转换器，将请求报文转换为Java对象，或将Java对象转换为响应报文
>
> HttpMessageConverter提供了两个注解和两个类型：@RequestBody，@ResponseBody，RequestEntity，ResponseEntity
>
> 其中相应信息较为常用

## 1. @RequestBody(获取请求体)

> @RequestBody可以获取请求体，需要在控制器方法设置一个形参，使用@RequestBody进行标识，当前请求的请求体就会为当前注解所标识的形参赋值

- 编写index.html

  ~~~html
  <form th:action="@{/testRequestBody}" method="post">
      用户名：<input type="text" name="username"><br>
      密码：<input type="password" name="password"><br>
      <input type="submit">
  </form>
  ~~~

- 编写HttpController.java控制器

  ~~~java
  @RequestMapping("/testRequestBody")
  public String testRequestBody(@RequestBody String requestBody){
      System.out.println("requestBody:"+requestBody);
      return "success";
  }
  ~~~

- 编写获取请求体成功后跳转界面success.html

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title></title>
  	</head>
  	<body>
  		success
  	</body>
  </html>
  ~~~

  运行结果：

  ~~~shell
  requestBody:username=admin&password=123456
  ~~~


## 2. RequestEntity(获取请求报文)

> RequestEntity封装请求报文的一种类型，需要在控制器方法的形参中设置该类型的形参，当前请求的请求报文就会赋值给该形参，可以通过getHeaders()获取请求头信息，通过getBody()获取请求体信息

- 在index.html中编写form表单

  ~~~html
  <form th:action="@{/testRequestEntity" method="post">
      <input type= "text" name= "username">
      <input type= "text" name= "password">
      <input type= "submit" value="测试@testRequestEntity">
  </form>
  ~~~

- 在HttpController.java控制器中编写请求方法

  ~~~java
  @RequestMapping("/testRequestEntity")
  public String testRequestEntity(RequestEntity<String> requestEntity){
      //当前requestEnity表示整个请求报文的信息
      System.out.println("requestHeader:"+requestEntity.getHeaders());
      System.out.println("requestBody:"+requestEntity.getBody());
      return "success";
  }
  ~~~

  输出结果：

  ~~~shell
  requestHeader:[host:“localhost:8080”, connection:“keep-alive”, content-length:“27”, cache-control:“max-age=0”, sec-ch-ua:"" Not A;Brand";v=“99”, “Chromium”;v=“90”, “Google Chrome”;v=“90"”, sec-ch-ua-mobile:"?0", upgrade-insecure-requests:“1”, origin:“http://localhost:8080”, user-agent:“Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Safari/537.36”]
  requestBody:username=admin&password=123
  ~~~

## 3. 通过HttpServletResponse响应浏览器数据

- 在HttpController.java控制器中编写响应方法

  ~~~java
  @RequestMapping("/testResponse")
  public void testResponse(Ht tpServletResponse response ) throws IQException {
      response. getWriter().print("hello,response");
  }
  ~~~

- 在index.html中编写超链接

  ~~~html
  <a th:href="@{/testResponse}" >通过servletAPI的response对象响应浏览器数据</a>
  ~~~

  访问后结果：

  ~~~shell
  hello,response
  ~~~

## ==4. @ResponseBody(发送响应体)==

> @ResponseBody用于标识一个控制器方法，可以将该方法的返回值直接作为响应报文的响应体响应用到浏览器

- 在HttpController.java控制器中编写响应方法

  ~~~java
  @RequestMapping("/testResponseBody")
  @ResponseBody
  public String testResponseBody(){
      return "success1";
  }
  ~~~

- 在index.html中编写超链接

  ~~~html
  <a th:href="@{/testResponseBody}">通过@ResponseBody响应浏览器数据</a>
  ~~~

  运行结果：

  ~~~shell
  success1
  ~~~

## 5. @ResponseBody处理json数据

> JSON：JavaScript中的一种数据交互格式

- 在pom.xml中添加配置文件导入jar包

  ~~~xml
  <dependency>
      <groupId>com.fasterxml.jackson.core</groupId>
      <artifactId>jackson-databind</artifactId>
      <version>2.12.1</version>
  </dependency>
  ~~~

  [导入jar包后：](https://s1.ax1x.com/2022/07/17/jIU3WR.png)
  												[<img src="https://s1.ax1x.com/2022/07/17/jIU3WR.png" alt="jIU3WR.png" style="zoom:50%;" />](https://imgtu.com/i/jIU3WR)

- 在SpringMVC.xml中开启mvc的注解驱动

  > 此时在HandlerAdaptor中会自动装配一个消息转换器：MappingJackson2HttpMessageConverter，可以将响应到浏览器的Java对象转换为Json格式的字符串

  ~~~xml
  <mvc:annotation-driven/>
  ~~~

- 在HttpController.java控制器中进行标识

  > 将Java对象直接作为控制器方法的返回值返回，就会自动转换为Json格式的字符串

  ~~~java
  @RequestMapping("/testResponseUser")
  @ResponseBody
  public User testResponseUser(){
      return new User(1001,"admin","123456",23,"男");
  }
  ~~~

- 在index.html中添加链接访问

  ~~~html
  <a th:href="@{/testResponseUser}">通过@ResponseBody响应浏览器User对象</a><br>
  ~~~

  运行结果：

  ~~~json
  {"id":1001,"username":"admin","password":"123456","age":23,"sex":"男"}
  ~~~

## 6. SpringMVC处理ajax

- 在资源目录下导入axios.js和vue.js。之后重新打包。

  [导入静态资源：](https://s1.ax1x.com/2022/07/17/jIaRjx.png)
                                                               [<img src="https://s1.ax1x.com/2022/07/17/jIaRjx.png" alt="jIaRjx.png" style="zoom:50%;" />](https://imgtu.com/i/jIaRjx)

  

- 在index.html中编写容器，并使用vue取消链接默认跳转

  ~~~html
  <div id="app">
      <a th:href="@{/testAxios}">SpringMVC处理ajax</a>
  </div>
  <script type="text/javascript" th:src="@{/static/js/vue.js}"></script>
  <script type="text/javascript" th:src="@{/static/js/axios.min.js}"></script>
  <script type="text/javascript">
      var vue = new Vue({
          el:"#app",
          methods:{
              testAjax:function (event) {
                  axios({
                      method:"post",
                      url:event.target.href,
                      <!--往服务器传输的数据-->
                      params:{
                          username:"admin",
                          password:"123456"
                      }
                  }).then(function (response) {		<!--执行成功后执行的函数-->
                      alert(response.data);			<!--弹窗输出数据-->
                  });
                  event.preventDefault();
              }
          }
      });
  </script>
  ~~~

- 在HttpController.java中编写控制器

  ~~~java
  @RequestMapping("/testAjax")
  @ResponseBody
  public String testAjax(String username, String password){
      System.out.println("username:"+username+",password:"+password);
      return "hello,ajax";
  }
  ~~~

  运行结果：
  [SpringMVC处理ajax：](https://s1.ax1x.com/2022/07/17/jIdMG9.png)                                                [<img src="https://s1.ax1x.com/2022/07/17/jIdMG9.png" alt="jIdMG9.png" style="zoom: 50%;" />](https://imgtu.com/i/jIdMG9)

## 7. @RestController注解

> @RestController注解是springMVC提供的一个复合注解，标识在控制器的类上，就相当于为类添加了@Controller注解，并且为其中的每个方法添加了@ResponseBody注解

## 8. ResponseEntity

> ResponseEntity用于控制器方法的返回值类型，该控制器方法的返回值就是响应到浏览器的响应报文

# 九. 使用ResponseEntity进行文件下载和上传

## 1. 文件下载

> 使用ResponseEntity实现下载文件的功能

~~~java
@RequestMapping("/testDown")
public ResponseEntity<byte[]> testResponseEntity(HttpSession session) throws IOException {
    //获取ServletContext对象
    ServletContext servletContext = session.getServletContext();
    //获取服务器中文件的真实路径
    String realPath = servletContext.getRealPath("/static/img/1.jpg");
    //创建输入流
    InputStream is = new FileInputStream(realPath);
    //创建字节数组
    byte[] bytes = new byte[is.available()];
    //将流读到字节数组中
    is.read(bytes);
    //创建HttpHeaders对象设置响应头信息
    MultiValueMap<String, String> headers = new HttpHeaders();
    //设置要下载方式以及下载文件的名字
    headers.add("Content-Disposition", "attachment;filename=1.jpg");
    //设置响应状态码(200)
    HttpStatus statusCode = HttpStatus.OK;
    //创建ResponseEntity对象。bytes为响应体、headers为响应头、statusCode为响应状态码
    ResponseEntity<byte[]> responseEntity = new ResponseEntity<>(bytes, headers, statusCode);
    //关闭输入流
    is.close();
    return responseEntity;
}
~~~

## 2. 文件上传

> 文件上传要求form表单的请求方式必须为`post`，并且添加属性`enctype=“multipart/form-data”`
>
> SpringMVC中将上传的文件封装到MultipartFile对象中，通过此对象可以获取文件相关信息

- 在pom.xml中配置依赖

  ~~~xml
  <!-- https://mvnrepository.com/artifact/commons-fileupload/commons-fileupload -->
  <dependency>
      <groupId>commons-fileupload</groupId>
      <artifactId>commons-fileupload</artifactId>
      <version>1.3.1</version>
  </dependency>
  ~~~

- 在SpringMVC.xml的配置文件中添加配置

  ~~~xml
  <!--必须通过文件解析器的解析才能将文件转换为MultipartFile对象，该bean是通过类型注入-->
  <bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
  </bean>
  ~~~

- 编写控制器方法

  > 文件上传需要用到`MultipartFile`来接收表单传递的文件数据

  ~~~java
  @RequestMapping("/testUp")
  public String testUp(MultipartFile photo, HttpSession session) throws IOException {
      //获取上传的文件的文件名
      String fileName = photo.getOriginalFilename();
      //处理文件重名问题
      String hzName = fileName.substring(fileName.lastIndexOf("."));
      fileName = UUID.randomUUID().toString() + hzName;
      //获取服务器中photo目录的路径
      ServletContext servletContext = session.getServletContext();
      String photoPath = servletContext.getRealPath("photo");
      File file = new File(photoPath);
      //判断路径是否存在
      if(!file.exists()){
          file.mkdir();
      }
      String finalPath = photoPath + File.separator + fileName;
      //实现上传功能
      photo.transferTo(new File(finalPath));
      return "success";
  }
  ~~~

  [上传文件：](https://s1.ax1x.com/2022/07/17/jIrfKA.png)
                       [<img src="https://s1.ax1x.com/2022/07/17/jIrfKA.png" alt="jIrfKA.png" style="zoom:50%;" />](https://imgtu.com/i/jIrfKA)

 ## 3. 解决文件重命名问题

> SpringMVC默认是文件==追加的模式==，当上传文件到服务器后，由于服务器有重名文件，这就会导致现有文件覆盖原有的文件 。 

- 修改控制器方法

  ~~~java
  @RequestMapping("/testUp")
  public String testUp(MultipartFile photo, HttpSession session) throws IOException {
      //获取上传的文件的文件名
      String fileName = photo.getOriginalFilename();
      //处理文件重名问题
      String hzName = fileName.substring(fileName.lastIndexOf("."));
      fileName = UUID.randomUUID().toString() + hzName;
      //获取服务器中photo目录的路径
      ServletContext servletContext = session.getServletContext();
      String photoPath = servletContext.getRealPath("photo");
      File file = new File(photoPath);
      //判断路径是否存在
      if(!file.exists()){
          file.mkdir();
      }
      String finalPath = photoPath + File.separator + fileName;
      //实现上传功能
      photo.transferTo(new File(finalPath));
      return "success";
  }
  ~~~

# 十. 拦截器

> SpringMVC的处理器拦截器,类似于Servlet开发中的过滤器Filter，用于对处理器进行预处理和后处理。

过滤器和拦截器区别

> 过滤器：依赖于servlet容器。在实现上基于函数回调，可以对几乎所有请求进行过滤，但是缺点是一个过滤器实例只能在容器初始化时调用一次。使用过滤器的目的是用来做一些过滤操作，比如：在过滤器中修改字符编码；在过滤器中修改HttpServletRequest的一些参数，包括：过滤低俗文字、危险字符等。
>
> 拦截器：依赖于web框架，在实现上基于Java的反射机制，属于面向切面编程（AOP）的一种运用。由于拦截器是基于web框架的调用，因此可以使用Spring的依赖注入（DI）进行一些业务操作，同时一个拦截器实例在一个controller生命周期之内可以多次调用。

## 1. 拦截器的使用

> 需要继承HandlerInterceptor接口，重写其中3个回调方法。同时还要在SpringMVC.xml中配置拦截器。
>
> 拦截器一个有3个回调方法：
>
> 1. preHandle：==在控制器方法执行前执行。==预处理回调方法，实现处理器的预处理（如登录检查），第三个参数为响应的处理器返回值：true表示继续流程（如调用下一个拦截器或处理器）；false表示流程中断（如登录检查失败），不会继续调用其他的拦截器或处理器，此时我们需要通过response来产生响应；
> 2. postHandle：==在控制器方法执行之后执行。==后处理回调方法，实现处理器的后处理（但在渲染视图之前），此时我们可以通过modelAndView（模型和视图对象）对模型数据进行处理或对视图进行处理，modelAndView也可能为null。
> 3. afterCompletion：==在视图渲染之后执行。==整个请求处理完毕回调方法，即在视图渲染完毕时回调，如性能监控中我们可以在此记录结束时间并输出消耗时间，还可以进行一些资源清理，类似于try-catch-finally中的finally，但仅调用处理器执行链中preHandle返回true的拦截器才会执行afterCompletion。

- 在index.html中编写链接

  ~~~html
  <a th:href="@{/testInterceptor}"></a>
  ~~~

- 编写请求成功页面success.html

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title></title>
  	</head>
  	<body>
  		success
  	</body>
  </html>
  ~~~

- 编写TestController.java处理页面请求

  ~~~java
  @Component
  @RequestMapping("/**/testInterceptor")
  public string testInterceptor(){
      return "success";
  }
  ~~~

  > @Component注解启用拦截器中`<ref>`标签。

- 编写拦截器FirstInterceptor.java

  ~~~java
  public class MyHandlerInterceptor implements HandlerInterceptor {
  
      @Override
      public boolean preHandle(HttpServletRequest request, HttpServletResponse response, 
                               Object handler)throws Exception {
          System.out.println("MyHandlerInterceptor->preHandle");
          //true放行
          return true;
      }
  
      @Override
      public void postHandle(HttpServletRequest request, HttpServletResponse response, 
                             Object handler,ModelAndView modelAndView) throws Exception {
          System.out.println("MyHandlerInterceptor->postHandle");
      }
  
      @Override
      public void afterCompletion(HttpServletRequest request, HttpServletResponse response, 
                                  Object handler, Exception ex)throws Exception {
          System.out.println("MyHandlerInterceptor->afterCompletion");
      }
  
  }
  ~~~

- 在SpringMVC.xml中配置拦截器

  ~~~xml
  <mvc:interceptor>
      <bean class="com.atguigu.interceptor.FirstInterceptor"></bean>
      <ref bean="firstInterceptor"></ref>
  </mvc:interceptor>
  <!-- 以上两种配置方式都是对DispatcherServlet所处理的所有的请求进行拦截 -->
  <mvc:interceptor>
      <mvc:mapping path="/**"/>
      <mvc:exclude-mapping path="/testRequestEntity"/>
      <ref bean="firstInterceptor"></ref>
  </mvc:interceptor>
  <!-- 
   以上配置方式可以通过ref或bean标签设置拦截器，通过mvc:mapping设置需要拦截的请求，通过mvc:exclude-mapping设置需要排除的请求，即不需要拦截的请求
  -->
  ~~~

  > `<bean>`和`ref`标签会拦截DispatcherServlet所处理的所有的请求。
  >
  > 这里`<mvc:mapping>`标签表示拦截所有请求， `<mvc:exclude-mapping>`表示不拦截服务器请求index页面。

  `<mvc:interceptor>`拦截器方法

  |              方法名               |      描述      |
  | :-------------------------------: | :------------: |
  |    `<mvc:mapping path="/*"/>`     |  拦截请求路径  |
  | `<mvc:exclude-mapping path="/"/>` | 不拦截请求路径 |

  [测试拦截器：](https://s1.ax1x.com/2022/07/19/jTwN0P.png)

  ​                                    [<img src="https://s1.ax1x.com/2022/07/19/jTwN0P.png" alt="jTwN0P.png" style="zoom:50%;" />](https://imgtu.com/i/jTwN0P)

## 2. 多个拦截器顺序

> 1. 若每个拦截器的preHandle()都返回true
>
>    此时多个拦截器的执行顺序和拦截器在SpringMVC的配置文件的配置顺序有关：==preHandle()会按照配置的顺序执行，而postHandle()和afterComplation()会按照配置的反序执行==
>
> 2. 若某个拦截器的preHandle()返回了false
>
>    一个preHandle()返回false，那么它和它之前的拦截器的preHandle()都会执行，postHandle()都不执行，返回false拦截器之前的afterComplation()会执行(不包括返回false的拦截器)

# 十一. 异常处理器

> SpringMVC提供了一个处理控制器方法执行过程中所出现的异常的接口：HandlerExceptionResolver
>
> HandlerExceptionResolver接口的实现类有：DefaultHandlerExceptionResolver和==SimpleMappingExceptionResolver==
>
> SpringMVC提供了自定义的异常处理器SimpleMappingExceptionResolver

## 1. 使用配置文件处理异常

- 在SpringMVC.xml中配置异常处理

  ~~~xml
  <bean class="org.springframework.web.servlet.handler.SimpleMappingExceptionResolver">
      <property name="exceptionMappings">
          <props>
          	<!--
          		properties的键表示处理器方法执行过程中出现的异常
          		properties的值表示若出现指定异常时，设置一个新的视图名称，跳转到指定页面
          	-->
              <prop key="java.lang.ArithmeticException">error</prop>
          </props>
      </property>
      <!--
      	exceptionAttribute属性设置一个属性名，将出现的异常信息在请求域中进行共享
      -->
      <property name="exceptionAttribute" value="ex"></property>
  </bean>
  ~~~

- 编写error.html错误页面

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title></title>
  	</head>
  	<body>
  		出现错误
  	</body>
  </html>
  ~~~

- 编写TestController.java制造异常

  ~~~java
  @RequestMapping("/testExceptionHandler")
  public string testExcept ionHandler(){
      System.out.println(1/0);
      return" success" ;
  }
  ~~~

- index.html中添加测试链接

  ~~~html
  <a th:href="@{/testExcept ionHandler}">测试异常处理</a><br>
  ~~~

  运行结果：

  [测试异常页面：](https://s1.ax1x.com/2022/07/19/jT2drF.png)
                                                 [<img src="https://s1.ax1x.com/2022/07/19/jT2drF.png" alt="jT2drF.png" style="zoom: 67%;" />](https://imgtu.com/i/jT2drF)

- 在SpringMVC.xml中的exceptionAttribute属性设置一个属性名，将出现的异常信息在请求域中进行共享

  ~~~xml
  <property name="exceptionAttribute" value="ex"></property>
  ~~~

  运行结果：
  [出现错误信息：](https://s1.ax1x.com/2022/07/19/jT2vZQ.png)
                                                  [<img src="https://s1.ax1x.com/2022/07/19/jT2vZQ.png" alt="jT2vZQ.png" style="zoom:67%;" />](https://imgtu.com/i/jT2vZQ)

## 2. 使用注解处理异常

>  `@ControllerAdvice`将当前类标识为异常处理的组件。方法上的`@ExceptionHandler`用于设置所标识方法处理的异常。
>
> 方法参数的ex表示当前请求处理中出现的异常对象。

- 编写异常处理请求器

  ~~~java
  //@ControllerAdvice将当前类标识为异常处理的组件
  @ControllerAdvice
  public class ExceptionController {
  
      //@ExceptionHandler用于设置所标识方法处理的异常
      @ExceptionHandler(ArithmeticException.class)
      //ex表示当前请求处理中出现的异常对象
      public String handleArithmeticException(Exception ex, Model model){
          model.addAttribute("ex", ex);
          return "error";
      }
  
  }
  ~~~

  运行结果：

  [出现错误信息：](https://s1.ax1x.com/2022/07/19/jT2vZQ.png)
                                                  [<img src="https://s1.ax1x.com/2022/07/19/jT2vZQ.png" alt="jT2vZQ.png" style="zoom:67%;" />](https://imgtu.com/i/jT2vZQ)

# 十二. 注解配置SpringMVC.xml

> 使用配置类和注解代替web.xml和SpringMVC配置文件的功能

## 1. 创建SpringConfig配置类，代替spring的配置文件

~~~java
@Configuration
public class SpringConfig {
	//ssm整合之后，spring的配置信息写在此类中
}
~~~

## 2. 创建初始化类，代替web.xml

> 在Servlet3.0环境中，容器会在类路径中查找实现javax.servlet.ServletContainerInitializer接口的类，如果找到的话就用它来配置Servlet容器。
>
> Spring3.2引入了一个便利的WebApplicationInitializer基础实现，名为==AbstractAnnotationConfigDispatcherServletInitializer==，当我们的类扩展了AbstractAnnotationConfigDispatcherServletInitializer并将其部署到Servlet3.0容器的时候，容器会自动发现它，并用它来配置Servlet上下文。

- 在WebInti.java中创建配置类用来代替web.xml

  ~~~java
  public class WebInit extends AbstractAnnotationConfigDispatcherServletInitializer {
  
      /**
       * 指定spring的配置类
       * @return
       */
      @Override
      protected Class<?>[] getRootConfigClasses() {
          return new Class[]{SpringConfig.class};
      }
  
      /**
       * 指定SpringMVC的配置类
       * @return
       */
      @Override
      protected Class<?>[] getServletConfigClasses() {
          return new Class[]{WebConfig.class};
      }
  
      /**
       * 指定DispatcherServlet的映射规则，即url-pattern
       * @return
       */
      @Override
      protected String[] getServletMappings() {
          return new String[]{"/"};
      }
  
      /**
       * 添加过滤器
       * @return
       */
      @Override
      protected Filter[] getServletFilters() {
          CharacterEncodingFilter encodingFilter = new CharacterEncodingFilter();
          encodingFilter.setEncoding("UTF-8");
          encodingFilter.setForceRequestEncoding(true);
          HiddenHttpMethodFilter hiddenHttpMethodFilter = new HiddenHttpMethodFilter();
          return new Filter[]{encodingFilter, hiddenHttpMethodFilter};
      }
  }
  ~~~

  四个类方法介绍

  |         方法名          |                      描述                      |
  | :---------------------: | :--------------------------------------------: |
  |  getRootConfigClasses   |       指定spring的配置类，一般在SSM时用        |
  | getServletConfigClasses |             指定springMVC的配置类              |
  |   getServletMappings    | 指定DispatcherServlet的映射规则，即url-pattern |
  |    getServletFilters    |                   添加过滤器                   |

## 3. 在WebConfig.java中移植SpringMVC.xml中的内容

> 添加内容：扫描组件、视图解析器、view- controller、default- servlet- handler、mvc注解驱动、文件上传解析器、异常处理
> 、拦截器
>
> default- servlet- handler、view- controller、拦截器、异常处理和文件上传解析器需要通过实现WebMvcConfigurer接口实现

~~~java
@Configuration
//扫描组件
@ComponentScan("com.atguigu.mvc.controller")
//开启MVC注解驱动
@EnableWebMvc
public class WebConfig implements WebMvcConfigurer {

    //使用默认的servlet处理静态资源
    @Override
    public void configureDefaultServletHandling(DefaultServletHandlerConfigurer configurer) {
        configurer.enable();
    }

    //配置文件上传解析器
    @Bean
    public CommonsMultipartResolver multipartResolver(){
        return new CommonsMultipartResolver();
    }

    //配置拦截器
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        FirstInterceptor firstInterceptor = new FirstInterceptor();
        registry.addInterceptor(firstInterceptor).addPathPatterns("/**");
    }
    
    //配置视图控制view- controller
    
    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        registry.addViewController("/").setViewName("index");
    }
    
    //配置异常映射
    @Override
    public void configureHandlerExceptionResolvers(List<HandlerExceptionResolver> resolvers) {
        SimpleMappingExceptionResolver exceptionResolver = new SimpleMappingExceptionResolver();
        Properties prop = new Properties();
        prop.setProperty("java.lang.ArithmeticException", "error");
        //设置异常映射
        exceptionResolver.setExceptionMappings(prop);
        //设置共享异常信息的键
        exceptionResolver.setExceptionAttribute("ex");
        resolvers.add(exceptionResolver);
    }

    //配置生成模板解析器
    @Bean
    public ITemplateResolver templateResolver() {
        WebApplicationContext webApplicationContext = ContextLoader.getCurrentWebApplicationContext();
        // ServletContextTemplateResolver需要一个ServletContext作为构造参数，可通过WebApplicationContext 的方法获得
        ServletContextTemplateResolver templateResolver = new ServletContextTemplateResolver(
                webApplicationContext.getServletContext());
        templateResolver.setPrefix("/WEB-INF/templates/");
        templateResolver.setSuffix(".html");
        templateResolver.setCharacterEncoding("UTF-8");
        templateResolver.setTemplateMode(TemplateMode.HTML);
        return templateResolver;
    }

    //生成模板引擎并为模板引擎注入模板解析器，ITemplateResolver自动装配
    @Bean
    public SpringTemplateEngine templateEngine(ITemplateResolver templateResolver) {
        SpringTemplateEngine templateEngine = new SpringTemplateEngine();
        templateEngine.setTemplateResolver(templateResolver);
        return templateEngine;
    }

    //生成视图解析器并为解析器注入模板引擎
    @Bean
    public ViewResolver viewResolver(SpringTemplateEngine templateEngine) {
        ThymeleafViewResolver viewResolver = new ThymeleafViewResolver();
        viewResolver.setCharacterEncoding("UTF-8");
        viewResolver.setTemplateEngine(templateEngine);
        return viewResolver;
    }
}
~~~

> 由于使用Thymeleaf视图解析器，所以在SpringMVC.xml中我们观察Thymeleaf视图解析器的`bean`结构，外部`bean`依赖于内部`bean`。所以我们要在配置类中配置三个`bean`方法。顺序对应SpringMVC.xml中`<bean>`从内到外。

## 4. 测试功能

创建TestController.java进行测试

~~~java
@Controller
public class TestController {
    @RequestMapping("/")
    public String index(){
        return "index";
    }
}
~~~

# 十三. SpringMVC执行流程

## 1. SpringMVC常用组件

| 组件名            |                    描述                    |                             作用                             |
| :---------------- | :----------------------------------------: | :----------------------------------------------------------: |
| DispatcherServlet |  前端控制器，不需要工程师开发，由框架提供  | 统一处理请求和响应，整个流程控制的中心，由它调用其它组件处理用户的请求 |
| HandlerMapping    | 处理器映射器，不需要工程师开发，由框架提供 |     根据请求的url、method等信息查找Handler，即控制器方法     |
| Handler           |       处理器(控制器)，需要工程师开发       |  在DispatcherServlet的控制下Handler对具体的用户请求进行处理  |
| HandlerAdapter    | 处理器适配器，不需要工程师开发，由框架提供 |       通过HandlerAdapter对处理器（控制器方法）进行执行       |
| ViewResolver      |  视图解析器，不需要工程师开发，由框架提供  | 进行视图解析，得到相应的视图，例如：ThymeleafView、InternalResourceView、RedirectView |
| View              |                    视图                    |                 将模型数据通过页面展示给用户                 |

## 2. DispatcherServlet初始化过程

>  Spring MVC源码的核心就是DispatcherServlet前端控制器。
>
> 从客户端传过来的所有请求都需要通过DispatcherServlet来进行分发、处理，然后把响应结果返回给客户端。DispatcherServlet的本质就是一个Servlet，和Servlet有着同样的生命周期，初始化->运行->销毁。

[运行图解：](https://s1.ax1x.com/2022/07/20/jbSTfA.png)

​										[<img src="https://s1.ax1x.com/2022/07/20/jbSTfA.png" alt="jbSTfA.png" style="zoom: 67%;" />](https://imgtu.com/i/jbSTfA)

- DispatcherServlet的初始化工作并没有在DispatcherServlet这个类里面进行初始化，而是在HttpServletBean这个类里面重写了init()方法。下面是HttpServletBean.init()方法

  ~~~java
  public final void init() throws ServletException {
     if (logger.isDebugEnabled()) {
        logger.debug("Initializing servlet '" + getServletName() + "'");
     }
  	/**
  	 *加载web.xml中的init-param进行初始化参数
  	 *ServletConfigPropertyValues是HttpServletBean的一个内部类，
  	 *用于解析web.xml定义中<servlet>元素的子元素<init-param>中的参数值
  	 */
     // Set bean properties from init parameters.
     PropertyValues pvs = new ServletConfigPropertyValues(getServletConfig(), this.requiredProperties);
     if (!pvs.isEmpty()) {
        try {
           //将Servlet转化成BeanWrapper，便于值的注入
           BeanWrapper bw = PropertyAccessorFactory.forBeanPropertyAccess(this);
           ResourceLoader resourceLoader = new ServletContextResourceLoader(getServletContext());
           bw.registerCustomEditor(Resource.class, new ResourceEditor(resourceLoader, getEnvironment()));
           //模板方法
           initBeanWrapper(bw);
           //把初始配置设置给DispatcherServlet
           bw.setPropertyValues(pvs, true);
        }
        catch (BeansException ex) {
           if (logger.isErrorEnabled()) {
              logger.error("Failed to set bean properties on servlet '" + getServletName() + "'", ex);
           }
           throw ex;
        }
     }
  
     // Let subclasses do whatever initialization they like.
     initServletBean();
  
     if (logger.isDebugEnabled()) {
        logger.debug("Servlet '" + getServletName() + "' configured successfully");
     }
  }
  ~~~


- 初始化WebApplicationContext.java
  所在类：org.springframework.web.servlet.FrameworkServlet

  ~~~java
  protected WebApplicationContext initWebApplicationContext() {
      WebApplicationContext rootContext =
          WebApplicationContextUtils.getWebApplicationContext(getServletContext());
      WebApplicationContext wac = null;
  
      if (this.webApplicationContext != null) {
          // A context instance was injected at construction time -> use it
          wac = this.webApplicationContext;
          if (wac instanceof ConfigurableWebApplicationContext) {
              ConfigurableWebApplicationContext cwac = (ConfigurableWebApplicationContext) wac;
              if (!cwac.isActive()) {
                  // The context has not yet been refreshed -> provide services such as
                  // setting the parent context, setting the application context id, etc
                  if (cwac.getParent() == null) {
                      // The context instance was injected without an explicit parent -> set
                      // the root application context (if any; may be null) as the parent
                      cwac.setParent(rootContext);
                  }
                  configureAndRefreshWebApplicationContext(cwac);
              }
          }
      }
      if (wac == null) {
          // No context instance was injected at construction time -> see if one
          // has been registered in the servlet context. If one exists, it is assumed
          // that the parent context (if any) has already been set and that the
          // user has performed any initialization such as setting the context id
          wac = findWebApplicationContext();
      }
      if (wac == null) {
          // No context instance is defined for this servlet -> create a local one
          // 创建WebApplicationContext
          wac = createWebApplicationContext(rootContext);
      }
  
      if (!this.refreshEventReceived) {
          // Either the context is not a ConfigurableApplicationContext with refresh
          // support or the context injected at construction time had already been
          // refreshed -> trigger initial onRefresh manually here.
          synchronized (this.onRefreshMonitor) {
              // 刷新WebApplicationContext
              onRefresh(wac);
          }
      }
  
      if (this.publishContext) {
          // Publish the context as a servlet context attribute.
          // 将IOC容器在应用域共享
          String attrName = getServletContextAttributeName();
          getServletContext().setAttribute(attrName, wac);
      }
  
      return wac;
  }
  ~~~

- 创建WebApplicationContext
  所在类：org.springframework.web.servlet.FrameworkServlet

  ~~~java
  protected WebApplicationContext createWebApplicationContext(@Nullable ApplicationContext parent) {
      Class<?> contextClass = getContextClass();
      if (!ConfigurableWebApplicationContext.class.isAssignableFrom(contextClass)) {
          throw new ApplicationContextException(
              "Fatal initialization error in servlet with name '" + getServletName() +
              "': custom WebApplicationContext class [" + contextClass.getName() +
              "] is not of type ConfigurableWebApplicationContext");
      }
      // 通过反射创建 IOC 容器对象
      ConfigurableWebApplicationContext wac =
          (ConfigurableWebApplicationContext) BeanUtils.instantiateClass(contextClass);
  
      wac.setEnvironment(getEnvironment());
      // 设置父容器
      wac.setParent(parent);
      String configLocation = getContextConfigLocation();
      if (configLocation != null) {
          wac.setConfigLocation(configLocation);
      }
      configureAndRefreshWebApplicationContext(wac);
  
      return wac;
  }
  ~~~

- DispatcherServlet初始化策略

  > FrameworkServlet创建WebApplicationContext后，刷新容器，调用onRefresh(wac)，此方法在DispatcherServlet中进行了重写，调用了initStrategies(context)方法，初始化策略，即初始化DispatcherServlet的各个组件
  >
  > 所在类：org.springframework.web.servlet.DispatcherServlet

  ~~~java
  protected void initStrategies(ApplicationContext context) {
     initMultipartResolver(context);
     initLocaleResolver(context);
     initThemeResolver(context);
     initHandlerMappings(context);
     initHandlerAdapters(context);
     initHandlerExceptionResolvers(context);
     initRequestToViewNameTranslator(context);
     initViewResolvers(context);
     initFlashMapManager(context);
  }
  ~~~

## 3. DispatcherServlet调用组件处理请求

- processRequest()

  > FrameworkServlet重写HttpServlet中的service()和doXxx()，这些方法中调用了processRequest(request, response)
  >
  > 所在类：org.springframework.web.servlet.FrameworkServlet

  ~~~java
  protected final void processRequest(HttpServletRequest request, HttpServletResponse response)
      throws ServletException, IOException {
  
      long startTime = System.currentTimeMillis();
      Throwable failureCause = null;
  
      LocaleContext previousLocaleContext = LocaleContextHolder.getLocaleContext();
      LocaleContext localeContext = buildLocaleContext(request);
  
      RequestAttributes previousAttributes = RequestContextHolder.getRequestAttributes();
      ServletRequestAttributes requestAttributes = buildRequestAttributes(request, response, previousAttributes);
  
      WebAsyncManager asyncManager = WebAsyncUtils.getAsyncManager(request);
      asyncManager.registerCallableInterceptor(FrameworkServlet.class.getName(), new RequestBindingInterceptor());
  
      initContextHolders(request, localeContext, requestAttributes);
  
      try {
  		// 执行服务，doService()是一个抽象方法，在DispatcherServlet中进行了重写
          doService(request, response);
      }
      catch (ServletException | IOException ex) {
          failureCause = ex;
          throw ex;
      }
      catch (Throwable ex) {
          failureCause = ex;
          throw new NestedServletException("Request processing failed", ex);
      }
  
      finally {
          resetContextHolders(request, previousLocaleContext, previousAttributes);
          if (requestAttributes != null) {
              requestAttributes.requestCompleted();
          }
          logResult(request, response, failureCause, asyncManager);
          publishRequestHandledEvent(request, response, startTime, failureCause);
      }
  }
  ~~~

- doService()

  所在类：org.springframework.web.servlet.DispatcherServlet

  ~~~java
  @Override
  protected void doService(HttpServletRequest request, HttpServletResponse response) throws Exception {
      logRequest(request);
  
      // Keep a snapshot of the request attributes in case of an include,
      // to be able to restore the original attributes after the include.
      Map<String, Object> attributesSnapshot = null;
      if (WebUtils.isIncludeRequest(request)) {
          attributesSnapshot = new HashMap<>();
          Enumeration<?> attrNames = request.getAttributeNames();
          while (attrNames.hasMoreElements()) {
              String attrName = (String) attrNames.nextElement();
              if (this.cleanupAfterInclude || attrName.startsWith(DEFAULT_STRATEGIES_PREFIX)) {
                  attributesSnapshot.put(attrName, request.getAttribute(attrName));
              }
          }
      }
  
      // Make framework objects available to handlers and view objects.
      request.setAttribute(WEB_APPLICATION_CONTEXT_ATTRIBUTE, getWebApplicationContext());
      request.setAttribute(LOCALE_RESOLVER_ATTRIBUTE, this.localeResolver);
      request.setAttribute(THEME_RESOLVER_ATTRIBUTE, this.themeResolver);
      request.setAttribute(THEME_SOURCE_ATTRIBUTE, getThemeSource());
  
      if (this.flashMapManager != null) {
          FlashMap inputFlashMap = this.flashMapManager.retrieveAndUpdate(request, response);
          if (inputFlashMap != null) {
              request.setAttribute(INPUT_FLASH_MAP_ATTRIBUTE, Collections.unmodifiableMap(inputFlashMap));
          }
          request.setAttribute(OUTPUT_FLASH_MAP_ATTRIBUTE, new FlashMap());
          request.setAttribute(FLASH_MAP_MANAGER_ATTRIBUTE, this.flashMapManager);
      }
  
      RequestPath requestPath = null;
      if (this.parseRequestPath && !ServletRequestPathUtils.hasParsedRequestPath(request)) {
          requestPath = ServletRequestPathUtils.parseAndCache(request);
      }
  
      try {
          // 处理请求和响应
          doDispatch(request, response);
      }
      finally {
          if (!WebAsyncUtils.getAsyncManager(request).isConcurrentHandlingStarted()) {
              // Restore the original attribute snapshot, in case of an include.
              if (attributesSnapshot != null) {
                  restoreAttributesAfterInclude(request, attributesSnapshot);
              }
          }
          if (requestPath != null) {
              ServletRequestPathUtils.clearParsedRequestPath(request);
          }
      }
  }
  ~~~

- doDispatch()

  所在类：org.springframework.web.servlet.DispatcherServlet

  ~~~java
  protected void doDispatch(HttpServletRequest request, HttpServletResponse response) throws Exception {
      HttpServletRequest processedRequest = request;
      HandlerExecutionChain mappedHandler = null;
      boolean multipartRequestParsed = false;
  
      WebAsyncManager asyncManager = WebAsyncUtils.getAsyncManager(request);
  
      try {
          ModelAndView mv = null;
          Exception dispatchException = null;
  
          try {
              processedRequest = checkMultipart(request);
              multipartRequestParsed = (processedRequest != request);
  
              // Determine handler for the current request.
              /*
              	mappedHandler：调用链
                  包含handler、interceptorList、interceptorIndex
              	handler：浏览器发送的请求所匹配的控制器方法
              	interceptorList：处理控制器方法的所有拦截器集合
              	interceptorIndex：拦截器索引，控制拦截器afterCompletion()的执行
              */
              mappedHandler = getHandler(processedRequest);
              if (mappedHandler == null) {
                  noHandlerFound(processedRequest, response);
                  return;
              }
  
              // Determine handler adapter for the current request.
             	// 通过控制器方法创建相应的处理器适配器，调用所对应的控制器方法
              HandlerAdapter ha = getHandlerAdapter(mappedHandler.getHandler());
  
              // Process last-modified header, if supported by the handler.
              String method = request.getMethod();
              boolean isGet = "GET".equals(method);
              if (isGet || "HEAD".equals(method)) {
                  long lastModified = ha.getLastModified(request, mappedHandler.getHandler());
                  if (new ServletWebRequest(request, response).checkNotModified(lastModified) && isGet) {
                      return;
                  }
              }
  			
              // 调用拦截器的preHandle()
              if (!mappedHandler.applyPreHandle(processedRequest, response)) {
                  return;
              }
  
              // Actually invoke the handler.
              // 由处理器适配器调用具体的控制器方法，最终获得ModelAndView对象
              mv = ha.handle(processedRequest, response, mappedHandler.getHandler());
  
              if (asyncManager.isConcurrentHandlingStarted()) {
                  return;
              }
  
              applyDefaultViewName(processedRequest, mv);
              // 调用拦截器的postHandle()
              mappedHandler.applyPostHandle(processedRequest, response, mv);
          }
          catch (Exception ex) {
              dispatchException = ex;
          }
          catch (Throwable err) {
              // As of 4.3, we're processing Errors thrown from handler methods as well,
              // making them available for @ExceptionHandler methods and other scenarios.
              dispatchException = new NestedServletException("Handler dispatch failed", err);
          }
          // 后续处理：处理模型数据和渲染视图
          processDispatchResult(processedRequest, response, mappedHandler, mv, dispatchException);
      }
      catch (Exception ex) {
          triggerAfterCompletion(processedRequest, response, mappedHandler, ex);
      }
      catch (Throwable err) {
          triggerAfterCompletion(processedRequest, response, mappedHandler,
                                 new NestedServletException("Handler processing failed", err));
      }
      finally {
          if (asyncManager.isConcurrentHandlingStarted()) {
              // Instead of postHandle and afterCompletion
              if (mappedHandler != null) {
                  mappedHandler.applyAfterConcurrentHandlingStarted(processedRequest, response);
              }
          }
          else {
              // Clean up any resources used by a multipart request.
              if (multipartRequestParsed) {
                  cleanupMultipart(processedRequest);
              }
          }
      }
  }
  ~~~

- processDispatchResult()

  ~~~java
  private void processDispatchResult(HttpServletRequest request, HttpServletResponse response,
                                     @Nullable HandlerExecutionChain mappedHandler, @Nullable ModelAndView mv,
                                     @Nullable Exception exception) throws Exception {
  
      boolean errorView = false;
  
      if (exception != null) {
          if (exception instanceof ModelAndViewDefiningException) {
              logger.debug("ModelAndViewDefiningException encountered", exception);
              mv = ((ModelAndViewDefiningException) exception).getModelAndView();
          }
          else {
              Object handler = (mappedHandler != null ? mappedHandler.getHandler() : null);
              mv = processHandlerException(request, response, handler, exception);
              errorView = (mv != null);
          }
      }
  
      // Did the handler return a view to render?
      if (mv != null && !mv.wasCleared()) {
          // 处理模型数据和渲染视图
          render(mv, request, response);
          if (errorView) {
              WebUtils.clearErrorRequestAttributes(request);
          }
      }
      else {
          if (logger.isTraceEnabled()) {
              logger.trace("No view rendering, null ModelAndView returned.");
          }
      }
  
      if (WebAsyncUtils.getAsyncManager(request).isConcurrentHandlingStarted()) {
          // Concurrent handling started during a forward
          return;
      }
  
      if (mappedHandler != null) {
          // Exception (if any) is already handled..
          // 调用拦截器的afterCompletion()
          mappedHandler.triggerAfterCompletion(request, response, null);
      }
  }
  ~~~

## 4. SpringMVC的执行流程

> 1. 用户向服务器发送请求，请求被SpringMVC 前端控制器 DispatcherServlet捕获。
> 2. DispatcherServlet对请求URL进行解析，得到请求资源标识符（URI），判断请求URI对应的映射：

- 不存在

  - 再判断是否配置了mvc:default-servlet-handler

  - 如果没配置，则控制台报映射查找不到，客户端展示404错误
    [客户端展示404错误：](https://s1.ax1x.com/2022/07/21/jqhbp4.png)
                           [<img src="https://s1.ax1x.com/2022/07/21/jqhbp4.png" alt="jqhbp4.png" style="zoom:50%;" />](https://imgtu.com/i/jqhbp4)

  - 如果有配置，则访问目标资源（一般为静态资源，如：JS,CSS,HTML），找不到客户端也会展示404错误
    [资源路径未找到：](https://s1.ax1x.com/2022/07/21/jq4P9e.png)
                             [<img src="https://s1.ax1x.com/2022/07/21/jq4P9e.png" alt="jq4P9e.png" style="zoom:50%;" />](https://imgtu.com/i/jq4P9e)

- 存在则执行下面的流程
  3. 根据该URI，调用HandlerMapping获得该Handler配置的所有相关的对象（包括Handler对象以及Handler对象对应的拦截器），最后以HandlerExecutionChain执行链对象的形式返回。
  4. DispatcherServlet 根据获得的Handler，选择一个合适的HandlerAdapter。
  5. 如果成功获得HandlerAdapter，此时将开始执行拦截器的preHandler(…)方法【正向】
  6. 提取Request中的模型数据，填充Handler入参，开始执行Handler（Controller)方法，处理请求。在填充Handler的入参过程中，根据你的配置，Spring将帮你做一些额外的工作：
- HttpMessageConveter： 将请求消息（如Json、xml等数据）转换成一个对象，将对象转换为指定的响应信息
- 数据转换：对请求消息进行数据转换。如String转换成Integer、Double等

- 数据格式化：对请求消息进行数据格式化。 如将字符串转换成格式化数字或格式化日期等
- 数据验证： 验证数据的有效性（长度、格式等），验证结果存储到BindingResult或Error中
  7. Handler执行完成后，向DispatcherServlet 返回一个ModelAndView对象。
  8. 此时将开始执行拦截器的postHandle(…)方法【逆向】。
  9. 根据返回的ModelAndView（此时会判断是否存在异常：如果存在异常，则执行HandlerExceptionResolver进行异常处理）选择一个适合的ViewResolver进行视图解析，根据Model和View，来渲染视图。
  10. 渲染视图完毕执行拦截器的afterCompletion(…)方法【逆向】。
  11. 将渲染结果返回给客户端。





