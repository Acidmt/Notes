SSM整合

[toc]

# 一. 创建项目

- 首先配置tomcat

  [配置tomcat：](https://gitee.com/Acido/images/raw/master/image/202210022214347.png)

<img src="C:\Users\Acid\OneDrive\图片\本机照片\code\配置tomat.png" alt="配置tomat" style="zoom: 50%;" />

- 通过maven创建web项目，创建完成后补全目录

  [完整目录结构：](https://gitee.com/Acido/images/raw/master/image/202210022216651.png)

  <img src="C:\Users\Acid\OneDrive\图片\本机照片\code\项目完整目录结构.png" alt="项目完整目录结构" style="zoom:67%;" />

## 1. 加载pom.xml文件

~~~xml
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>org.example</groupId>
  <artifactId>Blogss</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>war</packaging>

  <name>Blogss Maven Webapp</name>
  <!-- FIXME change it to the project's website -->
  <url>http://www.example.com</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.7</maven.compiler.source>
    <maven.compiler.target>1.7</maven.compiler.target>
    <spring.version>5.3.1</spring.version>
  </properties>

  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-context</artifactId>
      <version>${spring.version}</version>
    </dependency>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-beans</artifactId>
      <version>${spring.version}</version>
    </dependency>
    <!--springmvc-->
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-web</artifactId>
      <version>${spring.version}</version>
    </dependency>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-webmvc</artifactId>
      <version>${spring.version}</version>
    </dependency>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-jdbc</artifactId>
      <version>${spring.version}</version>
    </dependency>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-aspects</artifactId>
      <version>${spring.version}</version>
    </dependency>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-test</artifactId>
      <version>${spring.version}</version>
    </dependency>
    <!-- Mybatis核心 -->
    <dependency>
      <groupId>org.mybatis</groupId>
      <artifactId>mybatis</artifactId>
      <version>3.5.7</version>
    </dependency>
    <!--mybatis和spring的整合包-->
    <dependency>
      <groupId>org.mybatis</groupId>
      <artifactId>mybatis-spring</artifactId>
      <version>2.0.6</version>
    </dependency>
    <!-- 连接池 -->
    <dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>druid</artifactId>
      <version>1.0.9</version>
    </dependency>
    <!-- junit测试 -->
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.13.2</version>
      <scope>test</scope>
    </dependency>
    <!-- MySQL驱动 -->
    <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.16</version>
    </dependency>
    <!-- log4j日志 -->
    <dependency>
      <groupId>log4j</groupId>
      <artifactId>log4j</artifactId>
      <version>1.2.17</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/com.github.pagehelper/pagehelper -->
    <dependency>
      <groupId>com.github.pagehelper</groupId>
      <artifactId>pagehelper</artifactId>
      <version>5.2.0</version>
    </dependency>
    <!-- 日志 -->
    <dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
      <version>1.2.3</version>
    </dependency>
    <!-- ServletAPI -->
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <version>3.1.0</version>
      <scope>provided</scope>
    </dependency>
    <dependency>
      <groupId>com.fasterxml.jackson.core</groupId>
      <artifactId>jackson-databind</artifactId>
      <version>2.12.1</version>
    </dependency>
    <dependency>
      <groupId>commons-fileupload</groupId>
      <artifactId>commons-fileupload</artifactId>
      <version>1.3.1</version>
    </dependency>
    <!-- Spring5和Thymeleaf整合包 -->
    <dependency>
      <groupId>org.thymeleaf</groupId>
      <artifactId>thymeleaf-spring5</artifactId>
      <version>3.0.12.RELEASE</version>
    </dependency>
  </dependencies>

  <build>
    <finalName>Blogss</finalName>
    <pluginManagement><!-- lock down plugins versions to avoid using Maven defaults (may be moved to parent pom) -->
      <plugins>
        <plugin>
          <artifactId>maven-clean-plugin</artifactId>
          <version>3.1.0</version>
        </plugin>
        <!-- see http://maven.apache.org/ref/current/maven-core/default-bindings.html#Plugin_bindings_for_war_packaging -->
        <plugin>
          <artifactId>maven-resources-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.8.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-surefire-plugin</artifactId>
          <version>2.22.1</version>
        </plugin>
        <plugin>
          <artifactId>maven-war-plugin</artifactId>
          <version>3.2.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-install-plugin</artifactId>
          <version>2.5.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-deploy-plugin</artifactId>
          <version>2.8.2</version>
        </plugin>
      </plugins>
    </pluginManagement>
  </build>
</project>
~~~

## 2. 配置spring.xml

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context" xmlns:tx="http://www.springframework.org/schema/tx"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx.xsd">

    <!--扫描组件-->
    <context:component-scan base-package="com.atguigu.ssm">
        <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
    </context:component-scan>
    <!-- 引入jdbc.properties -->
    <context:property-placeholder location="classpath:jdbc.properties"></context:property-placeholder>
    <!-- 配置Druid数据源 -->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="${jdbc.driver}"></property>
        <property name="url" value="${jdbc.url}"></property>
        <property name="username" value="${jdbc.username}"></property>
        <property name="password" value="${jdbc.password}"></property>
    </bean>

    <!--配置事务管理器-->
    <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource"></property>
    </bean>

    <!--
        开启事务的注解驱动
        将使用注解@Transactional标识的方法或类中的所有方法进行事务管理
    -->
    <tx:annotation-driven transaction-manager="transactionManager"></tx:annotation-driven>

    <!-- 配置用于创建SqlSessionFactory的工厂bean,可以直接在spring的IOC中获取SqlSessionFactory -->
    <bean class="org.mybatis.spring.SqlSessionFactoryBean">
        <!-- 设置MyBatis配置文件的路径（可以不设置） -->
        <property name="configLocation" value="classpath:mybatis-config.xml"></property>
        <!-- 设置数据源 -->
        <property name="dataSource" ref="dataSource"></property>
        <!-- 设置类型别名所对应的包 -->
        <property name="typeAliasesPackage" value="com.atguigu.ssm.pojo"></property>
        <!--设置映射文件的路径 ,若映射文件所在路径和mapper接口所在路径一致，则不需要设置-->
        <!--<property name="mapperLocations" value="classpath:mapper/*.xml"></property>-->
    </bean>

    <!--
        配置mapper接口的扫描配置
        由mybatis-spring提供，可以将指定包下所有的mapper接口创建动态代理
        并将这些动态代理作为IOC容器的bean管理
    -->
    <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <property name="basePackage" value="com.atguigu.ssm.mapper"></property>
    </bean>

</beans>
~~~

最后的mapper接口扫描，我们可以轻松替代sqlsessionfactory对象的获取操作，即自动获取IOC工厂对象。`multipartResolver`必须要精确到mapper包下

## 3. 配置springmvc.xml

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/mvc https://www.springframework.org/schema/mvc/spring-mvc.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd">

    <!--扫描组件-->
    <context:component-scan base-package="com.atguigu.ssm.controller">
    </context:component-scan>
    <!--配置视图解析器-->
    <bean id="viewResolver"
          class="org.thymeleaf.spring5.view.ThymeleafViewResolver">
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
                        <property name="characterEncoding" value="UTF-8"/>
                    </bean>
                </property>
            </bean>
        </property>
    </bean>

    <!-- 配置默认的servlet处理静态资源 -->
    <mvc:default-servlet-handler/>
    <!-- 开启MVC的注解驱动 -->
    <mvc:annotation-driven/>

    <!-- 配置访问首页的视图控制 -->
    <mvc:view-controller path="/" view-name="index"></mvc:view-controller>

    <!--必须通过文件解析器的解析才能将文件转换为MultipartFile对象-->
    <bean id="multipartResolver"
          class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
    </bean>

</beans>
~~~

## 4. 配置mybatis-config.xml

~~~xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>

    <!--
        MyBatis核心配置文件中，标签的顺序：
        properties?,settings?,typeAliases?,typeHandlers?,
        objectFactory?,objectWrapperFactory?,reflectorFactory?,
        plugins?,environments?,databaseIdProvider?,mappers?
    -->

    <settings>
        <!--将下划线映射为驼峰-->
        <setting name="mapUnderscoreToCamelCase" value="true"/>
        <!--开启延迟加载-->
        <setting name="lazyLoadingEnabled" value="true"/>
        <!--按需加载-->
        <setting name="aggressiveLazyLoading" value="false"/>
    </settings>



    <plugins>
        <!--设置分页插件-->
        <plugin interceptor="com.github.pagehelper.PageInterceptor"></plugin>
    </plugins>

    <!--
        environments：配置多个连接数据库的环境
        属性：
        default：设置默认使用的环境的id
    -->


</configuration>
~~~

## 5. 配置日志文件log4j.xml

~~~xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE log4j:configuration SYSTEM "log4j.dtd">
<log4j:configuration xmlns:log4j="http://jakarta.apache.org/log4j/">
    <appender name="STDOUT" class="org.apache.log4j.ConsoleAppender">
        <param name="Encoding" value="UTF-8"/>
        <layout class="org.apache.log4j.PatternLayout">
            <param name="ConversionPattern" value="%-5p %d{MM-dd HH:mm:ss,SSS}
%m (%F:%L) \n"/>
        </layout>
    </appender>
    <logger name="java.sql">
        <level value="debug"/>
    </logger>
    <logger name="org.apache.ibatis">
        <level value="info"/>
    </logger>
    <root>
        <level value="debug"/>
        <appender-ref ref="STDOUT"/>
    </root>
</log4j:configuration>
~~~

## 6. 配置jdbc.properties

~~~properties
jdbc.driver=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/ssm?serverTimezone=UTC
jdbc.username=root
jdbc.password=abc123
~~~

## 7. 配置web.xml

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <!-- 配置Spring的编码过滤器 -->
    <filter>
        <filter-name>CharacterEncodingFilter</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <init-param>
            <param-name>forceEncoding</param-name>
            <param-value>true</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>CharacterEncodingFilter</filter-name>
        <!--<filter-name>encodingFilter</filter-name>-->
        <url-pattern>/*</url-pattern>
    </filter-mapping>

    <!-- 配置处理请求方式PUT和DELETE的过滤器 -->
    <filter>
        <filter-name>HiddenHttpMethodFilter</filter-name>
        <filter-class>org.springframework.web.filter.HiddenHttpMethodFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>HiddenHttpMethodFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>

    <!-- 配置SpringMVC的前端控制器 -->
    <servlet>
        <servlet-name>DispatcherServlet</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <!-- 设置SpringMVC的配置文件的位置和名称 -->
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:springmvc.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>DispatcherServlet</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>

    <!-- 设置Spring的配置文件的位置和名称 -->
    <context-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>classpath:spring.xml</param-value>
    </context-param>

    <!-- 配置Spring的监听器 -->
    <listener>
        <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener>
</web-app>
~~~

# 二. 在java目录下创建包

## 1. 创建pojo层

该层主要放实体类

## 2. 创建dao(mapper)层

在该层写接口，里面主要为操作数据库各种方法。

## 3. 创建controller层

控制层用于控制请求，类似与servlet。该层调用service层。

## 4. 创建service层(业务层)

service层实现接口层具体方法，所以service(业务层)调dao层。这两层统称为Model。

# 三. recouse目录下放置静态资源

## 1. 放置和dao接口层相同包名的映射文件

# 四. 项目环境搭建

开发编辑器：IDEA

Tomcat版本：9.0.58

Mysql版本：8.0

Maven版本：1.7

## 1. 配置jar包

添加jar包方式很多种，这里我们用Maven仓，通过配置`pom.xml`配置文件方式添加jar包，Maven在联网状态下会自动下载所需要的jar包。首先在本地仓库中找，找不到就在网上进行下载。这样省去网上找jar包时间，节省来发流程。并且Maven核心优势是会自动将被依赖的jar包导进来。这样省去寻找依赖包繁琐流程。同时也可以借助Maven可以将一个项目拆分成多个工程。

### 1.1 项目所需jar包

导入Spring核心jar包

| 包名                             | 简介           |
| -------------------------------- | -------------- |
| `spring-context`、`spring-beans` | Spring核心模块 |

配置SpringMVC相关jar包

| 包名                          | 简介                                       |
| ----------------------------- | ------------------------------------------ |
| `spring-web`、`spring-webmvc` | SpringMVC的核心运行环境                    |
| `spring-jdbc`                 | 虽然我们用了MyBatis，但事务管理需要用到    |
| `spring-aspects`              | 管理切面                                   |
| `javax.servlet-api`           | SpringMVC的前端控制器DispatcherServlet父类 |

junit测试模块

| 包名          | 简介                 |
| ------------- | -------------------- |
| `spring-test` | 整合Spring和测试模块 |
| `junit`       | 测试模块所需包       |

MyBatis核心依赖

| 包名                   | 简介                                                |
| ---------------------- | --------------------------------------------------- |
| `mybatis-spring`       | Spring整合MyBatis，工厂Bean可以直接在配置文件中实现 |
| `mybatis`              | MyBatis核心依赖                                     |
| `mysql-connector-java` | MySql驱动                                           |

数据库连接池

| 包名    | 简介                         |
| ------- | ---------------------------- |
| `druid` | 数据写入量大，数据压缩效果好 |

日志配置和视图解析器配置

| 包名                | 简介                    |
| ------------------- | ----------------------- |
| `logback-classic`   | log4j依赖文件           |
| `thymeleaf-spring5` | Spring和Thymeleaf整合包 |

### 1.2 pom.xml完整代码

~~~xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>${spring.version}</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-beans</artifactId>
        <version>${spring.version}</version>
    </dependency>
    <!--springmvc-->
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-web</artifactId>
        <version>${spring.version}</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>${spring.version}</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-jdbc</artifactId>
        <version>${spring.version}</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-aspects</artifactId>
        <version>${spring.version}</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-test</artifactId>
        <version>${spring.version}</version>
    </dependency>
    <!-- Mybatis核心 -->
    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis</artifactId>
        <version>3.5.7</version>
    </dependency>
    <!--mybatis和spring的整合包-->
    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis-spring</artifactId>
        <version>2.0.6</version>
    </dependency>
    <!-- 连接池 -->
    <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>druid</artifactId>
        <version>1.0.9</version>
    </dependency>
    <!-- junit测试 -->
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.13.2</version>
        <scope>test</scope>
    </dependency>
    <!-- MySQL驱动 -->
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.16</version>
    </dependency>
    <!-- log4j日志 -->
    <dependency>
        <groupId>log4j</groupId>
        <artifactId>log4j</artifactId>
        <version>1.2.17</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/com.github.pagehelper/pagehelper -->
    <dependency>
        <groupId>com.github.pagehelper</groupId>
        <artifactId>pagehelper</artifactId>
        <version>5.2.0</version>
    </dependency>
    <!-- 日志 -->
    <dependency>
        <groupId>ch.qos.logback</groupId>
        <artifactId>logback-classic</artifactId>
        <version>1.2.3</version>
    </dependency>
    <!-- ServletAPI -->
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>3.1.0</version>
        <scope>provided</scope>
    </dependency>
    <!--    处理JSON数据-->
    <dependency>
        <groupId>com.fasterxml.jackson.core</groupId>
        <artifactId>jackson-databind</artifactId>
        <version>2.12.1</version>
    </dependency>
    <!--    文件上传依赖-->
    <dependency>
        <groupId>commons-fileupload</groupId>
        <artifactId>commons-fileupload</artifactId>
        <version>1.3.1</version>
    </dependency>
    <!-- Spring5和Thymeleaf整合包 -->
    <dependency>
        <groupId>org.thymeleaf</groupId>
        <artifactId>thymeleaf-spring5</artifactId>
        <version>3.0.12.RELEASE</version>
    </dependency>
</dependencies>
~~~

这里我们可以通过**配置自定义属性管理版本**

~~~xml
<properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.7</maven.compiler.source>
    <maven.compiler.target>1.7</maven.compiler.target>
    <spring.version>5.3.1</spring.version>
</properties>
~~~

[项目完整jar包：](https://gitee.com/Acido/images/raw/master/image/202210231605688.png)

<img src="https://gitee.com/Acido/images/raw/master/image/202210231605688.png" alt="项目完整jar包" style="zoom: 57%;" />

## 2. 项目核心配置文件

### 2.1 web.xml配置

 `web.xml`是`JavaWeb`中极其关键的文件，用来**初始化配置信息**。web项目启动的时候,首先对`web.xml`文件进行一个加载，只有此文件没有异常的时候,我们加载的web项目才算是真正的跑起来，而`web.xml`文件的内容加载也是由一定的顺序的。顺序如下：

 ServletContext$\Longrightarrow$context-param$\Longrightarrow$listener$\Longrightarrow$filter$\Longrightarrow$servlet$\Longrightarrow$spring

- 配置Spring的编码过滤器

  这里一定要先配置Spring的编码过滤器，因为在设置编码的之前，获取过其他请求参数，那么这时得到的参数就会出现乱码问题。所以该配置项一定要在所以配置之前配置。

  ~~~xml
  <filter>
      <filter-name>CharacterEncodingFilter</filter-name>
      <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
      <init-param>
          <param-name>encoding</param-name>
          <param-value>UTF-8</param-value>
      </init-param>
      <init-param>
          <param-name>forceEncoding</param-name>
          <param-value>true</param-value>
      </init-param>
  </filter>
  <filter-mapping>
      <filter-name>CharacterEncodingFilter</filter-name>
      <url-pattern>/*</url-pattern>
  </filter-mapping>
  ~~~

  上面代码中5`~`6行设置自定义编码来处理请求编码，8`~`10配置设置后，既能处理响应编码，又能处理请求编码。13~16，配置编码处理范围为整个web项目。

- 配置处理请求方式PUT和DELETE的过滤器

  该配置项是将网页请求方式扩展了PUT和DELETE请求。应用与`RESTful`风格(表现层资源状态转移)，使代码前后端分离。易于后期维护。此时对于服务器资源分类分别对应四种基本操作：GET 用来获取资源，POST 用来新建资源，PUT 用来更新资源，DELETE 用来删除资源。配置如下：

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

  REST 风格提倡 URL 地址使用统一的风格设计，从前到后各个单词使用斜杠分开，不使用问号键值对方式携带请求参数，而是将要发送给服务器的数据作为 URL 地址的一部分，以保证整体风格的一致性。

- 配置SpringMVC的前端控制器`DispatcherServlet`

  `DispatcherServlet`是Spring MVC最核心的类，是前端控制器（Front Controller）设计模式的实现，正是这个核心组件接收所有传输到Web应用的HTTP请求。其作用：

  - 把一个HTTP request交给它真正的处理方法
  - 解析HTTP request的header和body中的数据，并把它们转换为DTO(数据传输对象)
  - Model-View-Controller三方的交互
  - 再把业务逻辑返回的DTO转换成HTTP response
  - 渲染具体的视图等；

  ~~~xml
  <servlet>
      <servlet-name>DispatcherServlet</servlet-name>
      <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
      <!-- 设置SpringMVC的配置文件的位置和名称 -->
      <init-param>
          <param-name>contextConfigLocation</param-name>
          <param-value>classpath:springmvc.xml</param-value>
      </init-param>
      <load-on-startup>1</load-on-startup>
  </servlet>
  <servlet-mapping>
      <servlet-name>DispatcherServlet</servlet-name>
      <url-pattern>/</url-pattern>
  </servlet-mapping>
  ~~~

  上面第5`~`8行设置SpringMVC的配置文件的位置和名称。第9行代码将`DispatcherServlet`的初始化时间提前到服务器启动时。后面的`<servlet-mapping>`同样将处理域作用到整个web项目。

- 配置Spring的监听器

  其作用是可以在服务器启动时加载Spring配置文件

  ~~~xml
  <listener>
      <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
  </listener>
  ~~~

- 设置Spring的配置文件的位置和名称

  ~~~xml
  <context-param>
      <param-name>contextConfigLocation</param-name>
      <param-value>classpath:spring.xml</param-value>
  </context-param>
  ~~~

到此web.xml文件的配置就完成了。

### 2.2 配置springmvc.xml

该文件主要是配置处理器映射信息和视图解析器。

处理器映射器有两种配置方式，一种是基于 XML 的资源配置，也就是常说的非注解方式。另外一种方式是基于 Annotation 注解方式的配置。 

SpringMVC的一个重要特性：将控制器中处理请求的逻辑 和 视图中渲染实现 解耦。 控制器方法和视图实现 只会在模型内容上保持一致，这是两者最大的关联。每种视图解析器对应不同的web解析技术，这里我们用thymeleaf解析器。

- 扫描控制层组件

  用来扫描控制层的映射处理器，将所有的映射处理加载到SpringMVC中。

  ~~~xml
  <context:component-scan base-package="com.blog.cn"></context:component-scan>
  ~~~

  `com.blog.cn`是本次项目的主目录包

- 配置视图解析器

  用于解析页面视图，将结果以视图的形式呈现在页面。

  ~~~xml
  <bean id="viewResolver"
        class="org.thymeleaf.spring5.view.ThymeleafViewResolver">
      <property name="order" value="1"/>
      <property name="characterEncoding" value="UTF-8"/>
      <property name="templateEngine">
          <bean class="org.thymeleaf.spring5.SpringTemplateEngine">
              <property name="templateResolver">
                  <bean class="org.thymeleaf.spring5.templateresolver.SpringResourceTemplateResolver">
                      <!-- 视图前缀 -->
                      <property name="prefix" value="/WEB-INF/view/"/>
                      <!-- 视图后缀 -->
                      <property name="suffix" value=".html"/>
                      <property name="templateMode" value="HTML5"/>
                      <property name="characterEncoding" value="UTF-8"/>
                  </bean>
              </property>
          </bean>
      </property>
  </bean>
  ~~~

  以上核心代码为8`~`15行，其分别使用`prefix`和`suffix`代表视图前缀和视图后缀。前缀值为静态网页存放目录。

- 其他配置

  由于SpringMVC的可拔插性，我们可以根据自己的需求进行配置。

  ~~~xml
  <!-- 配置默认的servlet处理静态资源 -->
  <mvc:default-servlet-handler/>
  
  <!-- 配置访问首页的视图控制 -->
  <mvc:view-controller path="/" view-name="index"></mvc:view-controller>
  
  <!-- 开启MVC的注解驱动 -->
  <mvc:annotation-driven/>
  ~~~

  上面我们配置处理静态资源配置项，配置访问首页的视图控制，首页视图会默认为`/`请求。之后开启MVC的注解驱动，使注解和配置项可以同时使用，否则SpringMVC就只能处理首页请求，其他在control层中的请求映射将全部失效。

- 配置文件上传

  由于用户需要上传自己的博客文件，所以我们还需要配置文件上传解析器。

  ~~~xml
  <bean id="multipartResolver"
        class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
  </bean>
  ~~~

  必须通过文件解析器的解析才能将文件转换为`MultipartFile`对象

### 2.3 配置Spring.xml文件

- 配置组件扫描

  有时候通过配置文件的方式创建Bean对象过于繁琐，我们还可以通过注解方式简化配置，针对Bean管理中创建对象提供以下注解：

  | 注解        |               说明                |
  | ----------- | :-------------------------------: |
  | @Component  |   推荐使用在类上用于实例化Bean    |
  | @Controller | 推荐使用在web层类上用于实例化bean |
  | @Service    |  推荐使用在service用于实例化bean  |
  | @Repository | 推荐使用在dao层类上用于实例化bean |

  ==注意：这四个注解的功能是一样的都可以用来创建bean实例，用哪个都可以，只是为了区分，我们使用相对应的。==

  ~~~xml
  <!--扫描组件-->
  <context:component-scan base-package="com.blog.cn">
      <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
  </context:component-scan>
  ~~~

  同样扫面范围为整个`com.blog.cn`包下，里面的`<context:exclude-filter>`为不扫描控制层组件，因为控制层已经在springmvc.xml中进行扫描了。

- 配置数据库连接池

  为了简化数据库连接配置，和后期可维护性，我们通常将数据库的连接属性写在一个jdbc.properties文件中：

  ~~~properties
  jdbc.driver=com.mysql.cj.jdbc.Driver
  jdbc.url=jdbc:mysql://localhost:3306/blogs?serverTimezone=UTC&useSSL=true&useUnicode=true&characterEncoding=utf8&zeroDateTimeBehavior=round
  jdbc.username=root
  jdbc.password=123456
  ~~~

  这里要注意数据库版本在8.0以上要设置字符集和时区。否则会导致数据库异常。

  数据库连接池这里选用Druid连接池，因为其强大的监控特性，通过Druid提供的监控功能，可以清楚知道连接池和SQL的工作情况。监控SQL的执行时间、ResultSet持有时间、返回行数、更新行数、错误次数、错误堆栈信息。监控连接池的物理连接创建和销毁次数、逻辑连接的申请和关闭次数、非空等待次数、PSCache命中率等。其次，方便扩展。Druid提供了Filter-Chain模式的扩展API，可以自己编写Filter拦截JDBC中的任何方法，可以在上面做任何事情，比如说性能监控、SQL审计、用户名密码加密、日志等等。配置Druid连接池如下：

  ~~~xml
  <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
      <property name="driverClassName" value="${jdbc.driver}"></property>
      <property name="url" value="${jdbc.url}"></property>
      <property name="username" value="${jdbc.username}"></property>
      <property name="password" value="${jdbc.password}"></property>
  </bean>
  ~~~

- 配置用于创建SqlSessionFactory的工厂bean

  SqlSessionFactory是Mybatis的关键对象，它是个单个数据库映射关系经过编译后的内存镜像。SqlSessionFactory对象的实例可以通过SqlSessionFactoryBuilder对象类获得，而SqlSessionFactoryBuilder则可以从XML配置文件或者一个预先定制的Configuration的实例构建出SqlSessionFactory的实例。每一个Mybaits的应用给程序都以一个SqlSessionFactory对象的实例为核心，同时SqlSessionFactory也是线程安全的，SqlSessionFactory一旦被创建，应该在应用执行期间都存在，在应用运行期间不要重复创建多次，建议使用单例模式。SqlSessionFactory是创建SqlSession的工厂。我们通过配置文件配置可以直接在spring的IOC中获取SqlSessionFactory。这样我们就不需要用传统方式获取，我们可以直接在IOC容器中自动装配一个SqlSessionFactory对象。

  ~~~xml
  <bean class="org.mybatis.spring.SqlSessionFactoryBean">
      <!-- 设置MyBatis配置文件的路径（可以不设置） -->
      <property name="configLocation" value="classpath:mybatis-config.xml"></property>
      <!-- 设置数据源 -->
      <property name="dataSource" ref="dataSource"></property>
      <!-- 设置类型别名所对应的包 -->
      <property name="typeAliasesPackage" value="com.blog.cn"></property>
      <!--设置映射文件的路径 ,若映射文件所在路径和mapper接口所在路径一致，则不需要设置-->
      <!--<property name="mapperLocations" value="classpath:mapper/*.xml"></property>-->
  </bean>
  ~~~

  实际上我们简化了mybatis-config.xml配置，将核心配置文件中配置转移到了这里，用spring整合。其中`configLocation`设置MyBatis配置文件的路径（可以不设置)。`dataSource`引用之前Druid连接池数据源。`typeAliasesPackage`设置类型别名所对应的包

- 设置映射文件的路径

  如果若映射文件所在路径和mapper接口所在路径不一致，则需要设置

  ~~~xml
  <property name="mapperLocations" value="classpath:mapper/*.xml"></property>
  ~~~

- 配置mapper接口的扫描配置

  之前配置用于创建SqlSessionFactory的工厂bean，获取对象方式仍然很麻烦，所以这里我们有一种更加简便方式。我们可以轻松替代sqlsessionfactory对象的获取操作，即自动获取IOC工厂对象。我们直接自动装配即可。但必须要精确到mapper包下。即可以将指定包下所有的mapper接口创建动态代理并将这些动态代理作为IOC容器的bean管理。

  ~~~xml
  <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
      <property name="basePackage" value="com.blog.cn.primer.mapper,com.blog.cn.register.mapper"></property>
  </bean>
  ~~~

  Control中可直接设置自动注入，生活获取工厂对象等一系列操作

  ~~~java
  @Controller
  public class RegisterControl {
      @Autowired
      private RegisterService registerService;
      @Autowired
      private BlogPathService blogPathService;
      @Autowired
      private BlogMessageService blogMessageService;
  }
  ~~~

### 2.4 配置mybatis-config.xml文件

- 配置全局配置

  由于数据库字段会和实体类字段不一致，此时我们需要在mybatis中用到resultMap，为了简化代码，我们可以设置驼峰映射，将web应用字段中的下划线转换为驼峰命名。

  ~~~xml
  <settings>
      <!--将下划线映射为驼峰-->
      <setting name="mapUnderscoreToCamelCase" value="true"/>
      <!--开启延迟加载-->
      <setting name="lazyLoadingEnabled" value="true"/>
      <!--按需加载-->
      <setting name="aggressiveLazyLoading" value="false"/>
  </settings>
  ~~~

至此我们已将整个项目环境和配置文件搭建完毕。







