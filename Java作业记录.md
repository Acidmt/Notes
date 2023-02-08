## SSM框架整合

题量: 15 满分: 100

作答时间:*11-23 09:47*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=24328488&type=2)

*86.8*分

## 一. 单选题（共5题，33分）

### 1. (单选题)下列选项中，不需要配置在web.xml中的是（ ）。

- A.

  Spring的监听器

- B.

  编码过滤器

- C.

  视图解析器

- D. 前端控制器

*我的答案:* C*正确答案:* C

*6.6*分

### 2. (单选题)下列选项中，属于Spring MVC所必须的JAR包的是（ ）。

- A.

  spring-web-4.3.6.RELEASE.jar

- B.

  spring-webmvc-portlet-4.3.6.RELEASE.jar

- C.

  spring-webmvc-4.3.6.RELEASE-javadoc.jar

- D. spring-websocket-4.3.6.RELEASE.jar

*我的答案:* C*正确答案:* A

*0*分

### 3. (单选题)下列选项中，不属于SSM整合时所需的JAR包的是（ ）。

- A.

  spring-web-4.3.6.RELEASE.jar

- B.

  spring-webmvc-4.3.6.RELEASE.jar

- C.

  ant-1.9.6.jar

- D. xwork-core-2.3.24.jar

*我的答案:* C*正确答案:* D

*0*分

### 4. (单选题)下列关于SSM框架的整合说法错误的是（ ）。

- A.

  Spring MVC与Spring之间不存在整合的问题。

- B.

  SSM框架的整合就涉及到Spring与MyBatis的整合。

- C.

  SSM框架的整合就涉及到Spring MVC与MyBatis的整合。

- D.

  SSM框架的整合就涉及到Spring MVC与Spring之间的整合。

*我的答案:* D*正确答案:* D

*6.6*分

### 5. (单选题)下面选项中，不属于整合SSM框架所编写的配置文件的是（ ）。

- A.

  db.properties

- B.

  applicationContext.xml

- C.

  mybatis-config.xml

- D. struts.xml

*我的答案:* D*正确答案:* D

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)SSM框架整合主要是【   】的整合，以及【   】的整合。 

- *我的答案：**6.6*分

  (1) Spring与MyBatis 

  (2) Spring MVC与MyBatis 

- *正确答案：*

  (1)Spring与MyBatis 

  (2) Spring MVC与MyBatis

### 7. (填空题)为了避免Spring配置文件中的信息过于臃肿，通常会将Spring配置文件中的信息按照【   】分散在多个配置文件中。

- *我的答案：**6.6*分

  (1) 不同的功能 

- *正确答案：*

  (1) 不同的功能

### 8. (填空题)@Transactional注解主要是针对数据的【   】、【   】、【   】进行事务管理。

- *我的答案：**6.6*分

  (1) 增加 

  (2) 修改 

  (3) 删除 

- *正确答案：*

  (1) 增加

  (2) 修改

  (3) 删除

### 9. (填空题)在整合项目中，db.properties文件主要用于【   】。

- *我的答案：**6.6*分

  (1) 配置数据库常量 

- *正确答案：*

  (1) 配置数据库常量

### 10. (填空题)Spring与MyBatis框架的整合时，可以通过Spring【   】，然后调用实例对象中的查询方法来执行MyBatis映射文件中的【   】，如果能够正确查询出数据库中的数据，就可以认为Spring与MyBatis框架整合成功。

- *我的答案：**6.6*分

  (1) 实例化Bean 

  (2) SQL语句 

- *正确答案：*

  (1)实例化Bean   

  (2) SQL语句

## 三. 判断题（共5题，34分）

### 11. (判断题)在实际开发时，为了避免Spring配置文件中的信息过于臃肿，通常会将Spring配置文件中的信息按照不同的功能分散在多个配置文件中。

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 12. (判断题)@Autowired注解需要标注在Service层的实现类上，这样才能实现依赖注入。

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 13. (判断题)@Transactional注解主要是针对数据的增加、修改、删除和查询进行事务管理。

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 14. (判断题)Spring与Spring MVC，Spring MVC与MyBatis需要相互整合。

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 15. (判断题)在Spring MVC的配置文件中，视图解析器是必须配置的。

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*7.6*分

## 拦截器

题量: 15 满分: 100

作答时间:*11-23 09:46*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=24328473&type=2)

*86.8*分

## 一. 单选题（共5题，33分）

### 1. (单选题)以下有关Spring MVC配置文件中拦截器的配置说法错误的是（ ）。

- A.

  要使用Spring MVC中拦截器，要先自定义拦截器还需要在配置文件中进行配置。

- B.

  `<mvc:interceptors>`元素用于配置一组拦截器，其子元素<bean>中定义的是指定路径的拦截器。

- C.

  `<mvc:interceptors>`元素中可以同时配置多个<`mvc:interceptor`>子元素。

- D.

  <mvc:exclude-mapping>元素用于配置不需要拦截的路径请求。

*我的答案:* B*正确答案:* B

*6.6*分

### 2. (单选题)下面不属于拦截器类中的方法的是（ ）。

- A.

  preHandler()

- B.

  postHandle()

- C.

  afterCompletion()

- D. afterpletion()

*我的答案:* D*正确答案:* D

*6.6*分

### 3. (单选题)以下（ ）方法可以定义Spring MVC中的拦截器。

- A.

  继承HandlerInterceptor

- B.

  实现WebRequestInterceptor

- C.

  实现HandlerInterceptorAdapter

- D.

  继承WebRequestInterceptor

*我的答案:* D*正确答案:* D

*6.6*分

### 4. (单选题)下列关于拦截器的执行流程说法错误的是（ ）。

- A.

  程序首先会执行拦截器类中的preHandle()方法。

- B.

  如果preHandle()方法的返回值为true，则程序会继续向下执行处理器中的方法，否则将不再向下执行。

- C.

  在业务处理器（即控制器Controller类）处理完请求后，会执行preHandle()方法。

- D.

  在DispatcherServlet处理完请求后，才会执行afterCompletion()方法。

*我的答案:* C*正确答案:* C

*6.6*分

### 5. (单选题)关于用户权限验证的执行流程，说法错误的是。（ ）

- A.

  只有登录后的用户才能访问系统中的主页面。

- B.

  如果没有登录系统而直接访问主页面，则拦截器会将请求拦截，并转发到登录页面。

- C.

  如果用户名或密码错误，会在登录页面给出相应的提示信息。

- D.

  当已登录的用户在系统主页中单击“退出”链接时，系统会回到主页面。

*我的答案:* D*正确答案:* D

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)Spring MVC单个拦截器执行顺序中，在【   】处理完请求后，才会执行afterCompletion()方法。

- *我的答案：**6.6*分

  (1) DispatcherServlet 

- *正确答案：*

  (1) DispatcherServlet

### 7. (填空题)Spring MVC中的拦截器（Interceptor）类似于Servlet中的【   】，它主要用于拦截用户请求并作相应的处理。

- *我的答案：**6.6*分

  (1) 过滤器或Filter 

- *正确答案：*

  (1) 过滤器或Filter

### 8. (填空题)用于如果没有登录系统而直接访问主页面，拦截器会将请求拦截，并转发到【    】。

- *我的答案：**0*分

  (1) 登陆页面 

- *正确答案：*

  (1) 登录页面 

### 9. (填空题)当有多个拦截器同时工作时，它们的【    】方法会按照配置文件中拦截器的配置顺序执行。

- *我的答案：**6.6*分

  (1) preHandle() 

- *正确答案：*

  (1) preHandle()

### 10. (填空题)如果拦截器类中的preHandle()方法的返回值为【   】，则程序会继续向下执行处理器中的方法。

- *我的答案：**6.6*分

  (1) true 

- *正确答案：*

  (1) true

## 三. 判断题（共5题，34分）

### 11. (判断题)在实现用户登录权限验证中，需要定义一个登录拦截器，并在拦截器的postHandle()方法中编写业务逻辑进行登录控制。

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 12. (判断题)配置拦截器时，必须将path的属性值设置为/**。 

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 错

*0*分

### 13. (判断题)多个拦截器时，postHandle()方法和afterCompletion()方法则会按照配置顺序执行。

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 14. (判断题)全局拦截器和指定路径下的拦截器不能够同时配置，否则运行时会报错。

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 15. (判断题)`<mvc:interceptor>`中的子元素可以按照任意位置编写。

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

## Spring MVC的核心类和注解

题量: 15 满分: 100

作答时间:*11-23 09:46*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=24328458&type=2)

*86.8*分

## 一. 单选题（共5题，33分）

### 1. (单选题)下面关于请求处理方法返回类型说法错误的是（ ）。

- A.

  常见的返回类型是ModelAndView、String和void

- B.

  ModelAndView类型中可以添加Model数据，并指定视图

- C.

  String类型的返回值可以跳转视图，但不能携带数据

- D.

  void类型主要在异步请求时使用，它既返回数据，又跳转视图

*我的答案:* D*正确答案:* D

*6.6*分

### 2. (单选题)下面类型中，不属于请求处理方法参数类型的是（ ）。

- A. javax.servlet.http.HttpSession

- B.

  @MatrixVariable

- C.

  org.springframework.ui.Model

- D. void

*我的答案:* D*正确答案:* D

*6.6*分

### 3. (单选题)下面关于组合注解的说法正确的是（ ）。

- A.

  组合注解是Spring3.x版本中的新特性

- B.

  组合注解可以简化常用的HTTP方法的映射

- C.

  在所有的Spring项目中，使用组合注解可以替代@RequestMapping注解

- D.

  @GetMapping注解可以用来匹配GET和POST方式的请求

*我的答案:* B*正确答案:* B

*6.6*分

### 4. (单选题)下面关于@RequestMapping注解说法错误的是（ ）。

- A.

  @RequestMapping注解的默认属性是value

- B.

  @RequestMapping注解的value属性值可以省略

- C.

  @RequestMapping注解的value属性名可以省略

- D.

  @RequestMapping注解的value属性必须标注

*我的答案:* D*正确答案:* D

*6.6*分

### 5. (单选题)下面关于`<load-on-startup>`元素说法错误的是（ ）。

- A.

  如果`<load-on-startup>`元素的值为1，则在应用程序启动时会立即加载该Servlet

- B.

  如果`<load-on-startup>`元素不存在，则应用程序会在第一个Servlet请求时加载该Servlet

- C.

  如果`<load-on-startup>`元素的值为1，则在应用程序启动时会延迟加载该Servlet

- D.

  `<load-on-startup>`元素是可选的

*我的答案:* C*正确答案:* C

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)RequestMapping注解类型用于映射【   】。 

- *我的答案：**6.6*分

  (1) 一个请求或一个方法 

- *正确答案：*

  (1) 一个请求或一个方法

### 7. (填空题)在使用Spring MVC的注解开发时，除了需要引入Spring的核心JAR包、Commons-logging的JAR包以及Spring MVC的2个JAR包外，还需要引入【   】的JAR包。

- *我的答案：**6.6*分

  (1) Spring AOP 

- *正确答案：*

  (1) Spring AOP

### 8. (填空题)在视图解析器配置中，可以设置视图的【   】。

- *我的答案：**6.6*分

  (1) 前缀和后缀 

- *正确答案：*

  (1) 前缀和后缀

### 9. (填空题)如果没有通过`<init-param>`元素配置，则应用程序会默认去【   】寻找配置文件。

- *我的答案：**0*分

  (1) 一 

- *正确答案：*

  (1) WEB-INF目录下

### 10. (填空题)如果`<load-on-startup>`元素不存在，则应用程序会【   】加载该Servlet。

- *我的答案：**0*分

  (1) 一 

- *正确答案：*

  (1) 在第一个Servlet请求时

## 三. 判断题（共5题，34分）

### 11. (判断题)在控制器类中，每一个请求处理方法都可以有多个不同类型的参数，以及一个多种类型的返回结果。

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 12. (判断题)@RequestMapping的method属性必须使用。 

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 13. (判断题)@RequestMapping(method = RequestMethod.GET)可以缩写为@GetMapping。 

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 14. (判断题)@RequestMapping注解的属性都是可选属性。 

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 15. (判断题)Web.xml文件中必须使用`<load-on-startup>`元素和`<init-param>`元素，否则文件会报错。 

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

## MyBatis与Spring的整合

题量: 15 满分: 100

作答时间:*11-23 09:37*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=24328441&type=2)

*86.8*分

## 一. 单选题（共5题，33分）

### 1. (单选题)MapperFactoryBean是MyBatis-Spring团队提供的用于根据Mapper接口生成Mapper对象的类，该类在Spring配置文件中可以配置的参数不包括

- A. mapperInterface
- B. SqlSessionFactory
- C. SqlSessionTemplate
- D. basePackage

*我的答案:* D*正确答案:* D

*6.6*分

### 2. (单选题)MapperScannerConfigurer类在Spring配置文件中使用时，可以配置的属性及说明错误的是

- A. basePackage：指定映射接口文件所在的包路径，当需要扫描多个包时可以使用分号或逗号作为分隔符
- B. annotationClass：指定了要扫描的注解名称，只有被注解标识的类才会被配置为映射器
- C. sqlSessionFactoryBeanName：指定在Spring中定义的SqlSessionFactory的Bean名称
- D. sqlSessionTemplateBeanName：指定在Spring中定义的SqlSessionTemplate的Bean名称。如果定义此属性，则sqlSessionFactoryBeanName将起作用

*我的答案:* A*正确答案:* D

*0*分

### 3. (单选题)在MyBatis+Spring的项目中，以下有关事务的相关说法正确的是

- A. 在MyBatis+Spring的项目中，事务是由MyBatis来管理的
- B. 在项目中，数据访问层既是处理业务的地方，又是管理数据库事务的地方
- C. 进行注解开发时，需要在配置文件中配置事务管理器并开启事务注解
- D. 进行注解开发时，需要使用@Transactional注解来标识表现层中的类

*我的答案:* D*正确答案:* C

*0*分

### 4. (单选题)以下不属于MapperScannerConfigurer类，在Spring配置文件中使用时需要配置的属性的是

- A. basePackage
- B. annotationClass
- C. sqlSessionFactoryBeanName
- D. mapperInterface

*我的答案:* D*正确答案:* D

*6.6*分

### 5. (单选题)以下有关采用传统DAO开发方式进行MyBatis与Spring框架的整合的说法错误的是

- A. 采用传统DAO开发方式进行MyBatis与Spring框架的整合时，只需要编写DAO接口
- B. 采用传统DAO开发方式进行MyBatis与Spring框架的整合时，需要向DAO实现类中注入SqlSessionFactory，然后在方法体内通过SqlSessionFactory创建SqlSession
- C. 可以使用mybatis-spring包中所提供的SqlSessionTemplate类或SqlSessionDaoSupport类来实现在类中注入SqlSessionFactory
- D. SqlSessionDaoSupport是一个抽象支持类，它继承了DaoSupport类，主要是作为DAO的基类来使用。可以通过SqlSessionDaoSupport类的getSqlSession()方法来获取所需的SqlSession

*我的答案:* A*正确答案:* A

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)在MyBatis+Spring的项目中，事务是由【】来管理的

- *我的答案：**6.6*分

  (1) Spring 

- *正确答案：*

  (1) Spring

### 7. (填空题)MyBatis-Spring团队提供了一种自动扫描的形式来配置MyBatis中的映射器——采用【】

- *我的答案：**6.6*分

  (1) MapperScannerConfigurer 

- *正确答案：*

  (1) MapperScannerConfigurer

### 8. (填空题)【】是MyBatis-Spring团队提供的一个用于根据Mapper接口生成Mapper对象的类

- *我的答案：**6.6*分

  (1) MapperFactoryBean 

- *正确答案：*

  (1) MapperFactoryBean

### 9. (填空题)SqlSessionDaoSupport是一个抽象支持类，可以通过SqlSessionDaoSupport类的【】方法来获取所需的SqlSession

- *我的答案：**6.6*分

  (1) getSqlSession() 

- *正确答案：*

  (1) getSqlSession()

### 10. (填空题)在进行Spring与MyBatis整合时，Spring框架所需要准备的JAR包共10个，其中包括：4个核心模块JAR，AOP开发使用的JAR，【】和事务的JAR

- *我的答案：**6.6*分

  (1) JDBC 

- *正确答案：*

  (1) JDBC

## 三. 判断题（共5题，34分）

### 11. (判断题)MapperFactoryBean的参数SqlSessionTemplate用于指定SqlSessionTemplate。如果与SqlSessionFactory同时设定，则只会启用SqlSessionFactory

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 12. (判断题)MyBaits与Spring进行整合时，Dao层开发可以使用传统的DAO方式的开发整合，以及Mapper接口方式的开发整合

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 13. (判断题)可以使用mybatis-spring包中所提供的SqlSessionTemplate类或SqlSessionDaoSupport类来实现向DAO实现类中注入SqlSessionFactory

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 14. (判断题)在实际的项目开发中，Spring与MyBatis都是整合在一起使用的

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 15. (判断题)MapperFactoryBean是MyBatis-Spring团队提供的一个用于根据Mapper接口生成Mapper对象的类

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

## Spring MVC入门

题量: 15 满分: 100

作答时间:*11-20 12:22*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=24246431&type=2)

*93.4*分

## 一. 单选题（共5题，33分）

### 1. (单选题)下面关于Spring MVC特点说法错误的是

- A. 灵活性强，但不易于与其他框架集成
- B. 可自动绑定用户输入，并能正确的转换数据类型
- C. 支持国际化
- D. 使用基于XML的配置文件，在编辑后，不需要重新编译应用程序

*我的答案:* A*正确答案:* A

*6.6*分

### 2. (单选题)Spring MVC中的后端控制器是指

- A. HandlerAdapter
- B. DispatcherServlet
- C. ViewReslover
- D. Handler

*我的答案:* D*正确答案:* D

*6.6*分

### 3. (单选题)用户通过浏览器向服务器发送请求时，负责拦截用户请求的是

- A. 处理器
- B. 处理器映射器
- C. 处理器适配器
- D. 前端控制器

*我的答案:* D*正确答案:* D

*6.6*分

### 4. (单选题)入门程序中，不是必须引入的JAR包是

- A. Spring的4个核心JAR包
- B. commons-logging的JAR包
- C. spring-web和spring-webmvc的JAR包
- D. log4j的JAR

*我的答案:* D*正确答案:* D

*6.6*分

### 5. (单选题)Spring MVC是Spring提供的一个实现了（）设计模式的轻量级Web框架

- A. Web MVC
- B. Web
- C. 单例
- D. 工厂

*我的答案:* A*正确答案:* A

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)前端控制器拦截请求后，会调用【】

- *我的答案：**6.6*分

  (1) HandlerMapping 

- *正确答案：*

  (1) HandlerMapping

### 7. (填空题)Spring MVC支持多种视图技术，包括【】、Velocity和FreeMarker等

- *我的答案：**6.6*分

  (1) JSP 

- *正确答案：*

  (1) JSP

### 8. (填空题)Spring MVC的配置文件中，可以配置处理器映射、处理器映射器、处理器适配器和【】

- *我的答案：**6.6*分

  (1) 视图解析器 

- *正确答案：*

  (1) 视图解析器

### 9. (填空题)Spring MVC提供了一个前端控制器【】，使开发人员无需额外开发控制器对象

- *我的答案：**6.6*分

  (1) DispatcherServlet 

- *正确答案：*

  (1) DispatcherServlet

### 10. (填空题)在Spring MVC的执行流程中，Controller执行完成后，会返回一个【】对象

- *我的答案：**6.6*分

  (1) ModelAndView 

- *正确答案：*

  (1) ModelAndView

## 三. 判断题（共5题，34分）

### 11. (判断题)HandlerAdapter将ModelAndView对象返回给ViewReslover

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 12. (判断题)Spring4.3版本的配置文件中，必须要配置处理器映射器、处理器适配器和视图解析器，否则程序将无法运行

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 13. (判断题)元素中的1表示容器在启动时立即加载这个Servlet

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 对

*0*分

### 14. (判断题)Spring MVC支持JSP、Velocity、XML和FreeMarker等视图技术

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 15. (判断题)Spring MVC的灵活性比较弱，易于与其他框架集成

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

## Spring的事务管理

题量: 15 满分: 100

作答时间:*11-20 12:22*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=24246429&type=2)

*93.4*分

## 一. 单选题（共5题，33分）

### 1. (单选题)以下关于Transactional注解可配置的参数信息及秒正确的是

- A. value用于指定需要使用的事务管理器，默认为""；
- B. read-only用于指定事务是否只读，默认为true；
- C. isolation用于指定事务的隔离级别，默认为Isolation.READ_COMMITTED；
- D. propagation用于指定事务的传播行为，默认为Propagation.SUPPORTS；

*我的答案:* A*正确答案:* A

*6.6*分

### 2. (单选题)以下基于XML方式的声明式事务管理配置文件中tx:advice元素的子元素tx:method属性描述错误的是

- A. name：该属性为必选属性，它指定了与事务属性相关的方法名
- B. propagation：用于指定事务的传播行为，它的默认值为SUPPORTS
- C. isolation：该属性用于指定事务的隔离级别，其默认值为DEFAULT
- D. read-only：该属性用于指定事务是否只读，其默认值为false

*我的答案:* A*正确答案:* B

*0*分

### 3. (单选题)以下有关事务管理方式相关说法错误的是

- A. Spring中的事务管理分为两种方式：一种是传统的编程式事务管理，另一种是声明式事务管理。
- B. 编程式事务管理：是通过AOP技术实现的事务管理，就是通过编写代码实现的事务管理，包括定义事务的开始、正常执行后的事务提交和异常时的事务回滚。
- C. 声明式事务管理：其主要思想是将事务管理作为一个“切面”代码单独编写，然后通过AOP技术将事务管理的“切面”代码植入到业务目标类中。
- D. 声明式事务管理最大的优点在于开发者无需通过编程的方式来管理事务，只需在配置文件中进行相关的事务规则声明，就可以将事务规则应用到业务逻辑中。

*我的答案:* B*正确答案:* B

*6.6*分

### 4. (单选题)以下有关Spring事务管理及核心接口说法错误的是

- A. PlatformTransactionManager接口是Spring提供的平台事务管理器，主要用于管理事务。
- B. TransactionDefinition接口是事务定义（描述）的对象，该对象中定义了事务规则，并提供了获取事务相关信息的方法。
- C. TransactionStatus接口是事务的状态，它描述了某一时间点上事务的状态信息。
- D. 在事务管理过程中，传播行为可以控制是否需要创建事务以及如何创建事务，通常情况下，对于数据的查询、插入、更新和删除操作，必须进行事务管理。

*我的答案:* D*正确答案:* D

*6.6*分

### 5. (单选题)下列选项中，哪一个不是Spring中事务管理的核心接口

- A. PlatformTransactionManager
- B. TransactionDefinition
- C. TransactionStatus
- D. TransactionManager

*我的答案:* D*正确答案:* D

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)使用基于注解方式的事务管理需要在使用事务的SpringBean类或者Bean类的方法上添加注解【】

- *我的答案：**6.6*分

  (1) @Transactional 

- *正确答案：*

  (1) Transactional

### 7. (填空题)Spring的声明式事务管理可以通过两种方式来实现，一种是基于XML的方式，另一种是基于【】的方式

- *我的答案：**6.6*分

  (1) Annotation 

- *正确答案：*

  (1) Annotation

### 8. (填空题)Spring2.0以后，提供了tx命名空间来配置事务，tx命名空间下提供了【】元素来配置事务的通知（增强处理）

- *我的答案：**6.6*分

  (1) <tx:advice> 

- *正确答案：*

  (1) tx:advice

### 9. (填空题)在Spring的所有JAR包中，包含一个名为【】的JAR包，该包就是Spring提供的用于事务管理的依赖包

- *我的答案：**6.6*分

  (1) spring-tx.RELEASE.jar 

- *正确答案：*

  (1) spring-tx.RELEASE.jar

### 10. (填空题)声明式事务管理：是通过【】实现的事务管理

- *我的答案：**6.6*分

  (1) AOP技术 

- *正确答案：*

  (1) AOP技术

## 三. 判断题（共5题，34分）

### 11. (判断题)基于XML方式的声明式事务管理是通过在配置文件中配置事务规则的相关声明来实现的

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 12. (判断题)编程式事务管理是通过编写代码实现的事务管理，包括定义事务的开始、正常执行后的事务提交和异常时的事务回滚

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 13. (判断题)Spring的事务管理简化了传统的事务管理流程，并且在一定程度上减少了开发者的工作量

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 14. (判断题)Spring的声明式事务管理可以通过两种方式来实现，一种是基于XML的方式，另一种是基于Annotation的方式

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 15. (判断题)Responsebody注解与RequestMapping注解配合使用时，页面中将可以获取到方法的返回值

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

## Spring的数据库开发

题量: 15 满分: 100

作答时间:*11-17 20:37*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=24185269&type=2)

*93.4*分

## 一. 单选题（共5题，33分）

### 1. (单选题)Spring JDBC模块主要由4个包组成，其中不包括

- A. core（核心包）
- B. dataSource（数据源包）
- C. driverClass（数据库驱动包）
- D. support（支持包）

*我的答案:* C*正确答案:* C

*6.6*分

### 2. (单选题)JdbcTemplate的直接父类是

- A. JdbcAccessor
- B. JdbcOperations
- C. JdbcSupper
- D. Object

*我的答案:* A*正确答案:* A

*6.6*分

### 3. (单选题)JdbcTemplate类包含在Spring JDBC模块的哪个包中

- A. 核心包
- B. 数据源包
- C. 对象包
- D. 支持包

*我的答案:* A*正确答案:* A

*6.6*分

### 4. (单选题)下面关于update()方法描述错误的是

- A. update()方法可以完成插入、更新、删除和查询数据的操作
- B. 在JdbcTemplate类中，提供了一系列的update()方法
- C. update()方法执行后，会返回受影响的行数
- D. update()方法返回的参数是int类型

*我的答案:* A*正确答案:* A

*6.6*分

### 5. (单选题)下面描述中，关于query()方法说法错误的是

- A. List query(String sql, RowMapper rowMapper)会执行String类型参数提供的SQL语句，并通过RowMapper返回一个List类型的结果。
- B. List query（String sql, PreparedStatementSetter pss, RowMapper rowMapper）会根据String类型参数提供的SQL语句创建PreparedStatement对象，通过RowMapper将结果返回到List中。
- C. List query（String sql, Object[] args, RowMapper rowMapper）会将args参数绑定到SQL语句中，并通过RowMapper返回一个Object类型的单行记录。
- D. queryForList（String sql,Object[] args, class elementType）可以返回多行数据的结果，但必须是返回列表，elementType参数返回的是List元素类型。

*我的答案:* C*正确答案:* C

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)JdbcTemplate类中还提供了大量的【】方法来处理各种对数据库表的查询操作

- *我的答案：**6.6*分

  (1) query() 

- *正确答案：*

  (1) query()

### 7. (填空题)JdbcTemplate类中的【】方法可以完成插入、更新和删除数据的操作

- *我的答案：**6.6*分

  (1) update() 

- *正确答案：*

  (1) update()

### 8. (填空题)【】就是Junit4用来测试的注解，要测试哪个方法，只需要在相应测试的方法上添加此注解即可

- *我的答案：**6.6*分

  (1) @Test 

- *正确答案：*

  (1) @Test

### 9. (填空题)JDBC连接数据库时需要4个基本属性，包括有【】、url、username和password

- *我的答案：**6.6*分

  (1) driverClassName 

- *正确答案：*

  (1) driverClassName

### 10. (填空题)JdbcTemplate类的继承关系十分简单。它继承自抽象类【】，同时实现了JdbcOperations接口

- *我的答案：**0*分

  (1) driverClassName;JdbcAccessor 

- *正确答案：*

  (1) JdbcAccessor

## 三. 判断题（共5题，34分）

### 11. (判断题)在使用Junit进行单一测试时，JUnit视图窗口的进度条为绿色表明运行结果正确；如果进度条为红色则表示有错误，并且会在窗口中显示所报的错误信息

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 12. (判断题)定义jdbcTemplate时，需要将dataSource注入到jdbcTemplate中

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 13. (判断题)JdbcOperations接口定义了在JdbcTemplate类中可以使用的操作集合，包括添加、修改、查询和删除等操作

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 14. (判断题)JdbcTemplate类中还提供了大量的query()方法来处理各种对数据库表的查询操作

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 15. (判断题)在JdbcTemplate类中，提供了大量的更新和查询数据库的方法，我们就是使用的这些方法来操作数据库的

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

## Spring AOP

题量: 15 满分: 100

作答时间:*11-10 12:01*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=23961985&type=2)

*80.2*分

## 一. 单选题（共5题，33分）

### 1. (单选题)以下不属于ProxyFactoryBean类中的常用可配置属性的是

- A. target
- B. proxyInterfaces
- C. targetClass
- D. interceptorNames

*我的答案:* C*正确答案:* C

*6.6*分

### 2. (单选题)以下哪种类型不是Spring中的通知类型

- A. 异常通知
- B. 前置通知
- C. 后置通知
- D. 最终通知

*我的答案:* D*正确答案:* D

*6.6*分

### 3. (单选题)关于AspectJ注解的介绍，说法错误的是

- A. @Aspect用于定义一个切面
- B. @Pointcut用于定义切入点表达式
- C. @Before用于定义前置通知，相当于BeforeAdvice
- D. @After用于定义后置通知，相当于AfterReturningAdvice

*我的答案:* D*正确答案:* D

*6.6*分

### 4. (单选题)以下有关CGLIB代理相关说法正确的是

- A. CGLIB代理的使用非常简单，但它还有一定的局限性——使用动态代理的对象必须实现一个或多个接口。
- B. 如果要对没有实现接口的类进行代理，那么可以使用CGLIB代理。
- C. CGLIB是一个高性能开源的代码生成包，在使用时需要另外导入CGLIB所需要的包。
- D. Spring中的AOP代理，可以是JDK动态代理，也可以是CGLIB代理。

*我的答案:* C*正确答案:* C

*6.6*分

### 5. (单选题)以下关于Spring AOP的介绍错误的是

- A. A: AOP的全称是Aspect-Oriented Programming，即面向切面编程（也称面向方面编程）。
- B. AOP采取横向抽取机制，将分散在各个方法中的重复代码提取出来，这种采用横向抽取机制的方式，采用OOP思想是无法办到的。
- C. 虽然AOP是一种新的编程思想，采取横向抽取机制，是OOP的升级替代品。
- D. 目前最流行的AOP框架有两个，分别为Spring AOP和AspectJ。

*我的答案:* B*正确答案:* C

*0*分

## 二. 填空题（共5题，33分）

### 6. (填空题)AspectJ框架中注解【】用于定义切入点表达式，在使用时还需定义一个包含名字和任意参数的方法签名来表示切入点名称

- *我的答案：**6.6*分

  (1) @Pointcut 

- *正确答案：*

  (1) @Pointcut

### 7. (填空题)在Spring配置文件中， 子元素的pointcut-ref属性用于指定一个已经存在的【】

- *我的答案：**0*分

  (1) bean  

- *正确答案：*

  (1) 切入点名称

### 8. (填空题)在Spring的配置文件中，配置切面使用的是【】元素

- *我的答案：**0*分

  (1) <aop:aspect> 

- *正确答案：*

  (1)

### 9. (填空题)在Spring中，使用【】是创建AOP代理的基本方式

- *我的答案：**6.6*分

  (1) ProxyFactoryBean 

- *正确答案：*

  (1) ProxyFactoryBean

### 10. (填空题)AOP术语中【】表示AOP框架在特定的切入点执行的增强处理，即在定义好的切入点处所要执行的程序代码

- *我的答案：**6.6*分

  (1) Advice 

- *正确答案：*

  (1) Advice

## 三. 判断题（共5题，34分）

### 11. (判断题)如果在同一个连接点有多个通知需要执行，那么在同一切面中，目标方法之前的前置通知和环绕通知的执行顺序是未知的，目标方法之后的后置通知和环绕通知的执行顺序也是未知的

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 12. (判断题)AspectJ框架中的注解@After用于定义最终final通知，不管是否异常，该通知都会执行

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 13. (判断题)Spring配置文件中的 元素下可以包含多个 元素，一个 元素中又可以包含属性和子元素，其子元素包括 、 和

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 14. (判断题)Spring中的AOP代理默认就是使用CGLIB代理的方式来实现的

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 15. (判断题)Spring 3.0以后，Spring AOP引入了对AspectJ的支持，并允许直接使用AspectJ进行编程，而Spring自身的AOP API也尽量与AspectJ保持一致

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

## Spring中的Bean

题量: 15 满分: 100

作答时间:*11-03 18:35*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=23757949&type=2)

*100*分

## 一. 单选题（共5题，33分）

### 1. (单选题)Spring的  元素中的autowire属性取值不包括以下

- A. default
- B. byName
- C. byType
- D. byId

*我的答案:* D*正确答案:* D

*6.6*分

### 2. (单选题)以下有关Bean的装配方式说法正确的是

- A. Spring容器支持多种形式的Bean的装配方式，如基于XML的装配、基于注解（Annotation）的装配和自动装配（其中最常用的是基于XML的装配）；
- B. Spring提供了3种基于XML的装配方式：设值注入、构造注入和属性注入；
- C. 在Spring实例化Bean的过程中，Spring首先会调用Bean的默认构造方法来实例化Bean对象，然后通过反射的方式调用setter方法来注入属性值；
- D. 设值注入要求一个Bean必须提供一个有参构造方法并且为需要注入的属性提供对应的setter方法。

*我的答案:* C*正确答案:* C

*6.6*分

### 3. (单选题)以下哪些不属于Spring4.3版本中Bean的作用域

- A. application
- B. request
- C. response
- D. globalSession

*我的答案:* C*正确答案:* C

*6.6*分

### 4. (单选题)Spring中定义了一系列的注解，以下有关其常用的注解说明错误的是

- A. @Autowired用于对Bean的属性变量、属性的setter方法及构造方法进行标注，配合对应的注解处理器完成Bean的自动配置工作，默认按照Bean的名称进行装配。
- B. @Repository用于将数据访问层（DAO层）的类标识为Spring中的Bean。
- C. @Service通常作用在业务层（Service层），用于将业务层的类标识为Spring中的Bean。
- D. @Controller通常作用在控制层（如Spring MVC的Controller），用于将控制层的类标识为Spring中的Bean。

*我的答案:* A*正确答案:* A

*6.6*分

### 5. (单选题)下列选项中，不属于Spring中实例化Bean的方式的是

- A. 构造器实例化
- B. 静态工厂方式实例化
- C. 实例工厂方式实例化
- D. 抽象方法实例化

*我的答案:* D*正确答案:* D

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)所谓自动装配，就是将一个Bean自动的注入到到其他Bean的【】中

- *我的答案：**6.6*分

  (1) Property 

- *正确答案：*

  (1) Property

### 7. (填空题)@Controller通常作用在控制层，如Spring MVC的【】，用于将控制层的类标识为Spring中的Bean，其功能与@Component 相同

- *我的答案：**6.6*分

  (1) Controller 

- *正确答案：*

  (1) Controller

### 8. (填空题)【】注解用于将数据访问层（DAO层）的类标识为Spring中的Bean，其功能与@Component 相同

- *我的答案：**6.6*分

  (1) @Repository 

- *正确答案：*

  (1) @Repository

### 9. (填空题)对于【】作用域的Bean，Spring只负责创建，当容器创建了Bean实例后，Bean的实例就交给客户端代码来管理，Spring容器将不再跟踪其生命周期

- *我的答案：**6.6*分

  (1) prototype 

- *正确答案：*

  (1) prototype

### 10. (填空题)实例工厂方式采用直接创建Bean实例的方式，在配置文件中，需要实例化的Bean是通过【】属性指向配置的实例工厂，然后使用factory-method属性确定使用工厂中的哪个方法

- *我的答案：**6.6*分

  (1) factory-bean 

- *正确答案：*

  (1) factory-bean

## 三. 判断题（共5题，34分）

### 11. (判断题)@Component注解用于描述Spring中的Bean，它是一个泛化的概念，仅仅表示一个组件，并且可以作用在任何层次，使用时只需将该注解标注在相应方法上即可

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 12. (判断题)Spring提供了3种基于XML的装配方式：设值注入、构造注入和属性注入

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 13. (判断题)每次客户端请求singleton作用域的Bean时，Spring容器都会创建一个新的实例，并且不会管那些被配置成singleton作用域的Bean的生命周期

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 14. (判断题)Spring中使用prototype定义的Bean在Spring容器中将只有一个实例，也就是说，无论有多少个Bean引用它，始终将指向同一个对象

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 15. (判断题)对于prototype作用域的Bean，Spring只负责创建，当容器创建了Bean实例后，Bean的实例就交给客户端代码来管理，Spring容器将不再跟踪其生命周期

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

## Spring的基本应用

题量: 15 满分: 100

作答时间:*10-18 18:04*至

[智能分析](https://stat2-ans.chaoxing.com/study-knowledge/ans?courseid=219121847&cpi=166216350&clazzid=59682467&ut=s&relationId=23201148&type=2)

*93.4*分

## 一. 单选题（共5题，33分）

### 1. (单选题)以下关于Spring核心容器相关说法错误的是

- A. Spring框架的所有功能都是通过其核心容器来实现的。
- B. 创建BeanFactory实例时，需要提供Spring所管理容器的详细配置信息，这些信息通常采用XML文件形式来管理。
- C. ApplicationContext不仅包含了BeanFactory的所有功能，还添加了对国际化、资源访问、事件传播等方面的支持。
- D. 通常在Java项目中，会采用通过ClassPathXmlApplicationContext类来实例化ApplicationContext容器的方式，而在Web项目中，ApplicationContext容器的实例化工作会交由Web服务器来完成。

*我的答案:* A*正确答案:* A

*6.6*分

### 2. (单选题)以下有关Spring的四个基础包说法正确的是

- A. Spring的四个基础包，它们分别对应Spring Web容器的四个模块。
- B. Spring的四个基础包有spring-core.RELEASE.jar、spring-beans-.RELEASE.jar、spring-context-.RELEASE.jar和spring-aop-.RELEASE.jar。
- C. spring-context-.RELEASE.jar是所有应用都要用到的JAR包，它包含访问配置文件以及进行IoC或者DI操作相关的所有类。
- D. spring-core.RELEASE.jar包含Spring框架基本的核心工具类，Spring其它组件都要用到这个包里的类，是其它组件的基本核心。

*我的答案:* A*正确答案:* D

*0*分

### 3. (单选题)以下有关Spring框架优点的说法正确的是

- A. Spring具有简单、可测试和松耦合等特点，从这个角度出发，Spring就是应用于任何Java应用的开发中；
- B. Spring提供了对AOP的支持，它允许将一些通用任务，如安全、事务、日志等进行集中式处理，从而提高了程序的复用性
- C. Spring就是一个大工厂，可以将所有对象的创建和依赖关系的维护工作都交给Spring容器管理，杜绝了组件之间的耦合性
- D. Spring增加了Java EE开发中一些API的使用难度

*我的答案:* B*正确答案:* B

*6.6*分

### 4. (单选题)Spring的核心容器是其他模块建立的基础，以下哪个不是该容器的组成模块

- A. Beans模块
- B. Core模块
- C. Context模块
- D. AOP模块

*我的答案:* D*正确答案:* D

*6.6*分

### 5. (单选题)下列选项中，不属于Spring框架优点的是

- A. 提供强大的、可以有效减少页面代码的标签
- B. 声明式事务的支持。
- C. 方便解耦、简化开发
- D. 方便集成各种优秀框架

*我的答案:* A*正确答案:* A

*6.6*分

## 二. 填空题（共5题，33分）

### 6. (填空题)依赖注入的作用就是在使用Spring框架创建对象时，动态的将其所依赖的对象注入到【】组件中

- *我的答案：**6.6*分

  (1) Bean 

- *正确答案：*

  (1) Bean

### 7. (填空题)在使用Spring框架之后，对象的实例不再由调用者来创建，而是由【】来创建，Spring容器会负责控制程序之间的关系，而不是由调用者的程序代码直接控制

- *我的答案：**6.6*分

  (1) Spring容器 

- *正确答案：*

  (1) Spring容器

### 8. (填空题)在Spring入门程序中只需将Spring的4个基础包以及【】的JAR包复制到lib目录中，并发布到类路径下即可

- *我的答案：**6.6*分

  (1) commons-logging 

- *正确答案：*

  (1) commons-logging

### 9. (填空题)简单来说，BeanFactory就是一个管理Bean的工厂，它主要负责初始化各种Bean，并调用它们的【】方法

- *我的答案：**6.6*分

  (1) 生命周期 

- *正确答案：*

  (1) 生命周期

### 10. (填空题)Spring开发所需的JAR包分为两个部分【】和【】

- *我的答案：**6.6*分

  (1) Spring框架包 

  (2) 第三方依赖包 

- *正确答案：*

  (1) Spring框架包

  (2) 第三方依赖包

## 三. 判断题（共5题，34分）

### 11. (判断题)Spring中基于构造方法的依赖注入通过调用带参数的构造方法来实现，每个参数代表着一个依赖

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 12. (判断题)通常在Java项目中，会采用通过FileSystemXmlApplicationContext类来实例化ApplicationContext容器的方式

- A. 对
- B. 错

*我的答案:* 错*正确答案:* 错

*6.6*分

### 13. (判断题)初学者学习Spring框架时，只需将Spring的4个基础包以及commons-logging.jar复制到项目的lib目录，并发布到类路径中即可

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 14. (判断题)依赖注入的作用就是在使用Spring框架创建对象时，动态的将其所依赖的对象注入到Bean组件中

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对

*6.6*分

### 15. (判断题)Spring框架采用的是分层架构，它一系列的功能要素被分成20个模块

- A. 对
- B. 错

*我的答案:* 对*正确答案:* 对