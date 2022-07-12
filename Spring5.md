Spring5

> Spring5[官网](https://spring.io/)
>
> Spring5下载[网址](https://repo.spring.io/ui/native/libs-release-local/org/springframework/spring/5.3.21/)(5.3.21)

[toc]

# 一. Spring5

## 1. 框架概述

1. Spring是一个轻量级的开源JAVAEE框架

2. Spring框架可以解决企业应用开发的复杂性

3. Spring有两个重要部分：**IOC**和**Aop**

   > IOC：控制反转，把创建对象的过程交给Spring管理。
   >
   > AOP：面向切面，不修改源代码的情况下，进行功能增强。

4. Spring特点：

   > 1. 方便解耦，简化开发
   > 2. AOP编程支持好(不改变源代码)
   > 3. 方便程序的测试
   > 4. 方便和其他框架进行整合(如：mybatis)
   > 5. 方便进行事务操作
   > 6. 降低API开发难度(如：JDBC)

## 2. 入门案例

### 2.1 Spring下载

- 进入网址选择下载版本

  [Spring下载：](https://s1.ax1x.com/2022/06/27/jZAwPe.png)

  ​						[<img src="https://s1.ax1x.com/2022/06/27/jZAwPe.png" alt="jZAwPe.png" style="zoom:25%;" />](https://imgtu.com/i/jZAwPe)

  [选择下载版本：](https://s1.ax1x.com/2022/06/27/jZE3FS.png)

  ​						[<img src="https://s1.ax1x.com/2022/06/27/jZE3FS.png" alt="jZE3FS.png" style="zoom: 33%;" />](https://imgtu.com/i/jZE3FS)

  > 在这里可以选择GA(稳定版)，之后点击右上角的github图标

- 点击Access to Binaries点击网址

  [Spring下载：](https://s1.ax1x.com/2022/06/27/jZEhTK.png)

  ​						[<img src="https://s1.ax1x.com/2022/06/27/jZEhTK.png" alt="jZEhTK.png" style="zoom: 50%;" />](https://imgtu.com/i/jZEhTK)

- 网页打开后下滑到最下面找到网页下载地址

  [Spring网页下载地址：](https://s1.ax1x.com/2022/06/27/jZE7SH.png)

  ​                         [<img src="https://s1.ax1x.com/2022/06/27/jZE7SH.png" alt="jZE7SH.png" style="zoom:33%;" />](https://imgtu.com/i/jZE7SH)

- 点击点击左边的展开按钮找到Artifacts图标

  [Artifacts下载目录：](https://s1.ax1x.com/2022/06/27/jZVDBt.png)

  ​						[<img src="https://s1.ax1x.com/2022/06/27/jZVDBt.png" alt="jZVDBt.png" style="zoom: 33%;" />](https://imgtu.com/i/jZVDBt)

- 展开后点击      libs-release-local -->org -->springframework-->spring，下面有spring到目前为止的所有framework的版本，你只需要下载你自己需要的就行。例如你要下载5.3.21版本，只需要选中后复制URL即可。

  [选择下载版本：](https://s1.ax1x.com/2022/06/27/jZVOgJ.png)

  ​                         [<img src="https://s1.ax1x.com/2022/06/27/jZVOgJ.png" alt="jZVOgJ.png" style="zoom: 33%;" />](https://imgtu.com/i/jZVOgJ)

- 选择下载压缩包

  [压缩包下载：](https://s1.ax1x.com/2022/06/27/jZZgVx.png)

  ​                         [<img src="https://s1.ax1x.com/2022/06/27/jZZgVx.png" alt="jZZgVx.png" style="zoom:33%;" />](https://imgtu.com/i/jZZgVx)

### 2.2 Spring案例编写

> 1. 打开IDEA，创建一个基本的项目。
>
> 2. Spring项目依赖于五个包：**spring-beans-5.3.21.jar**、**spring-context-5.3.21.jar**、**spring-core-5.3.21.jar**、
>
>    ​											   **spring-expression-5.3.21.jar**和日志包：commons-logging-1.1.1.jar([下载地址](https://repo1.maven.org/maven2/commons-logging/commons-logging/1.1.1/))
>
> 3. 最后在项目中导入这五个包即可

4. 创建一个类编写一个基本方法，然后用Spring方式创建一个对象继承该类的方法

   User.java

   ~~~java
   public class User {
       public void add() {
           System.out.println("add.....");
       }
   }
   ~~~

5. 创建Spring配置文件，在配置文件配置创建的对象。注意：Spring 配置文件使用xml格式。

   bean.xml

   ~~~xml
   <beans>
       <!--配置User对象创建-->
       <bean id="user" class="com.atguigu.spring5.User"></bean>
   </beans>
   ~~~

   bean标签格式如下：

   ~~~xml
   <bean id="对象名" class="对象要继承的类路径"></bean>
   ~~~

6. 使用Test单元测试框架测试代码

   TestSpring.java

   ~~~java
   public class TestSpring {
       @Test
       public void testAdd(){
           //1.加载spring配置文件
           ApplicationContext context =
               new ClassPathXmlApplicat ionContext ("bean.xml");
           //2.获取配置创建的对象
           User user = context.getBean("user",User.class);
           System.out.println(user);
           user.add();
       }
   }
   ~~~

   [案例运行结果：](https://s1.ax1x.com/2022/06/27/jZmqC8.png)

   ​                            [![jZmqC8.png](https://s1.ax1x.com/2022/06/27/jZmqC8.png)](https://imgtu.com/i/jZmqC8)

# 二. IOC容器

> 1. 什么是IOC：
>    - IOC是控制反转，它把对象创建和对象之间的调用过程，交给Spring管理。
>    - 使用IOC目的：为了降低代码的耦合度。
>    - 之前的入门案例就是IOC的实现。
> 2. IOC底层原理：
>    - XML解析、工厂模式、反射

## 1. 工厂模式简介
- 先创建一个UserDao类，里面编写一个Add方法

  ~~~java
  class UserDao {
      add (){}
  }
  ~~~

- 之后编写工厂类UserFactory，用于获取UserDao对象

  ~~~java
  class UserFactory {
      public static UserDao getDao() {
          return new UserDao();
      }
  }
  ~~~

- 最后创建一个UserService类，用来通过工厂类调用UserDao中的Add方法

  ~~~java
  class UserService {
      execute () {
          //通过工厂类获取UserDao对象
          UserDao dao = UserFadotry.getDao();
          dao.add();
      }
  }
  ~~~

[工厂模式图示：](https://s1.ax1x.com/2022/06/28/jesfeJ.png)

​						[<img src="https://s1.ax1x.com/2022/06/28/jesfeJ.png" alt="jesfeJ.png" style="zoom:33%;" />](https://imgtu.com/i/jesfeJ)

> 该模式的目的是为降低代码的耦合度，但该方法不是最优解。而最优方法是用IOC。

## 2. IOC模式实现过程

> IOC需要用到XML解析、工厂模式和反射
>
> 其作用是为了进一步降低代码耦合度

[IOC实现过程：](https://s1.ax1x.com/2022/06/28/jeyo7j.png)

​			[<img src="https://s1.ax1x.com/2022/06/28/jeyo7j.png" alt="jeyo7j.png" style="zoom:50%;" />](https://imgtu.com/i/jeyo7j)

## 4. IOC接口

> 1. IOC思想基于IOC容器完成，IOC容器底层就是对象工厂
> 2. Spirng提供IOC容器实现两种方式(两个接口)

IOC两种接口：

|         接口名         |                             描述                             |                             特点                             |
| :--------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|      BeanFactory       | IOC容器基本实现，是Spring内部的使用接口，不提供开发人员进行使用。 | 加载配置文件时候不会创建对象，在获取对象(使用)才去创建对象。 |
| ==ApplicationContext== | BeanFactory接口的子接口，提供更多更强大的功能，一般由开发人员进行使用。 |          加载配置文件时候就会把配置文件对象进行创建          |

ApplicationContext常用类：

|                类名                |                           描述                           |
| :--------------------------------: | :------------------------------------------------------: |
|  FileSystemXmlApplicationContext   |               可以加载磁盘路径下的配置文件               |
| ==ClassPathXmlApplicationContext== | 可以加载类路径下的配置文件，要求配置文件必须在类路径下面 |
| AnnotationConfigApplicationContext |                     读取注解创建容器                     |

- FileSystemXmlApplicationContext实现

  ~~~java
  public class Client {
      public static void main(String[] args) {
          ApplicationContext context = 
  			new FileSystemXmlApplicationContext("C:\\Users\\ghh\\Desktop\\bean.xml");
          //AccountService service = context.getBean("accountService", AccountService.class);
          //AccountDao accountDao = context.getBean("accountDao", AccountDao.class);
          //System.out.println(service);
          //System.out.println(accountDao);
          User user = context.getBean("user",User.class);
          System.out.println(user);
      }
  }
  ~~~

- ClassPathXmlApplicationContext实现

  ~~~java
  public class Client {
      public static void main(String[] args) {
          ApplicationContext context =
                  new ClassPathXmlApplicationContext("bean.xml");
          AccountService service = context.getBean("accountService", AccountService.class);
          AccountDao accountDao = context.getBean("accountDao", AccountDao.class);
          System.out.println(service);
          System.out.println(accountDao);
      }
  }
  ~~~

## 5. Bean管理

> IOC的Bean管理指的是两个操作：
>
> 1. Spring创建对象
> 2. Spring注入属性
>
> Bean管理操作的两种方式：
>
> 1. 基于XML配置文件方式实现
> 2. 基于注解方式实现

### 5.1 Bean的作用域和生命周期

1. 作用域

   > **作用域：用于确定Spring创建Bean的实例个数。**默认情况下Spring的实例对象是单实例(每次调用实例对象的地址相同)。

   | 作用域类别     |                             描述                             |
   | :------------- | :----------------------------------------------------------: |
   | singleton      | 单例的（默认的），使用singleton定义的Bean是单例的，每次调用getBean都是调用的同一个对象。只要IOC容器一创建就会创建Bean的实例。 |
   | prototype      | 多例的，每次通过Spring IOC容器获取prototype定义的Bean时，容器都将创建一个新的Bean实例。创建时不会实例该Bean，只有调用getBean方法时，才会实例化。 |
   | request        | 作用于web的请求范围，在每一次HTTP请求时，容器会返回Bean的同一个实例，对不同的HTTP请求则会产生一个新的Bean，而且该Bean仅在当前HTTP Request内有效。 |
   | session        | 作用于web的会话范围，在一次HTTP Session中，容器会返回该Bean的同一个实例，对不同的HTTP请求则会产生一个新的Bean，而且该Bean仅在当前HTTP Session内有效。 |
   | global-session | 作用于集群环境的会话范围（全局会话范围），在一个全局的HTTP Session中，容器返回Bean的同一个实例。当不是集群环境时，它就是session。 |

2. 如何设置多实例：

   > 设置为多实例需要用到scope属性，并且属性值设为"prototype"。这样就是多例的，每次通过Spring IOC容器获取prototype定义的Bean时，容器都将创建一个新的Bean实例。创建时不会实例该Bean，只有调用getBean方法时，才会实例化。

   - 以bean.xml为例

     ~~~xml
     <?xml version="1.0" encoding="UTF-8"?>
     <beans xmlns="http://www.springframework.org/schema/beans"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xmlns:util="http://www.springframework.org/schema/util"
            xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                                http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd">
     
     
         <!--设置为单实例,不写默认的就是这种类型：scope="singleton"-->
         <!--设置为多实例：scope="prototype"-->
         <bean id="book" class="com.Keafmd.spring5.collectiontype.Book" scope="prototype">
             <property name="list" ref="bookList"></property>
         </bean>
     </beans>
     ~~~

     > 可以看到上面`<bean>`标签中scope属性值为prototype，代表此对象已修改作用域。

   - 当我们测试用例时会发现实例化的对象地址不一样，证明是多实例的。

     ~~~shell
     com.Keafmd.spring5.collectiontype.Book@376b4233
     com.Keafmd.spring5.collectiontype.Book@2fd66ad3
     
     Process finished with exit code 0
     ~~~

3. Bean的生命周期

   > 生命周期是指：从对象创建到对象的销毁的过程。
   >
   > bean的生命周期分为以下五步：
   >
   > 1. 通过构造器创建bean实例（调用无参的构造函数）
   > 2. 为bean的属性设置值和对其它bean引用（调用set方法）
   > 3. 调用bean的初始化方法（初始化方法需要配置）
   > 4. bean的使用（获取到对象）
   > 5. 容器关闭，调用bean的销毁的方法（销毁方法需要进行配置）

   - 创建一个Orders.java类，用来配置方法

     ~~~java
     package com.Keafmd.spring5.bean;
     
     public class Orders {
     
         private String oname;
     
         //无参的构造函数，为了看到调用构造函数的过程我们把这个无参的构造函数写出来
         public Orders() {
             System.out.println("第一步：执行无参构造。");
         }
     
     	//set方法
         public void setOname(String oname) {
             this.oname = oname;
             System.out.println("第二步：调用set方法，设置属性值。");
         }
     
         //创建一个初始化的执行的方法
         public void initMethod(){
             System.out.println("第三步：执行初始化的方法。");
         }
     
         //创建一个销毁的执行的方法
         public void destoryMethod(){
             System.out.println("第五步：执行销毁的方法。");
         }
     }
     ~~~

     **我们自己写的初始化方法和销毁方法只有配置后才会被bean识别为初始化化方法和销毁方法，在bean中这样配置：`init-method="initMethod" destroy-method="destoryMethod"`。**

   - 创建bean.xml文件，绑定实例，之后绑定初始化方法和销毁方法

     ~~~xml
     <?xml version="1.0" encoding="UTF-8"?>
     <beans xmlns="http://www.springframework.org/schema/beans"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
     
     	<!--进行配置-->
         <bean id="orders" class="com.Keafmd.spring5.bean.Orders" init-method="initMethod" destroy-method="destoryMethod">
             <property name="oname" value="手机"></property>
         </bean>
     </beans>
     ~~~

   - 编写测试类

     ~~~java
     package com.Keafmd.spring5.testdemo;
     
     import com.Keafmd.spring5.bean.Orders;
     import org.junit.Test;
     import org.springframework.context.ApplicationContext;
     import org.springframework.context.support.ClassPathXmlApplicationContext;
     
     public class TestSpring5demo1 {
     
         //演示生命周期
         @Test
         public void test4(){
     
             ApplicationContext context = new ClassPathXmlApplicationContext("bean4.xml");
             Orders orders = context.getBean("orders",Orders.class);
             System.out.println("第四步：获取创建bean实例对象。");
             //System.out.println(orders);
             
             //手动让bean的实例销毁
             ((ClassPathXmlApplicationContext)context).close();
     
         }
     }
     ~~~

     测试结果

     ~~~shell
     第一步：执行无参构造。
     第二步：调用set方法，设置属性值。
     第三步：执行初始化的方法。
     第四步：获取创建bean实例对象。
     第五步：执行销毁的方法。
     
     Process finished with exit code 0
     ~~~

4. bean的更完整的生命周期

   > 加上bean的后置处理器后bean的生命周期就变成了七步，多出来的两步分别是在执行初始化方法前和执行初始化方法后各多出一步。
   >
   > bean的更完整的生命周期分为以下七步：
   >
   > 1. 通过构造器创建bean实例（调用无参的构造函数）
   > 2. 为bean的属性设置值和对其它bean引用（调用set方法）
   > 3. 把bean实例传递到bean后置处理器的方法
   > 4. 调用bean的初始化方法（初始化方法需要配置）
   > 5. 把bean实例传递到bean后置处理器的方法
   > 6. bean的使用（获取到对象）
   > 7. 容器关闭，调用bean的销毁的方法（销毁方法需要进行配置）

   - 在上面代码的基础我们需要添加一个bean的后置处理器并进行配置。创建个MyBeanPost.java类实现BeanPostProcessor接口。

     ~~~java
     package com.Keafmd.spring5.bean;
     
     import org.springframework.beans.BeansException;
     import org.springframework.beans.factory.config.BeanPostProcessor;
     import org.springframework.lang.Nullable;
     
     public class MyBeanPost implements BeanPostProcessor {
     
         @Nullable
         public Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
             System.out.println("第三步 Before...");
             return bean;
         }
     
         @Nullable
         public Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException {
             System.out.println("第三步 After...");
             return bean;
         }
     
     }
     
     ~~~

     > 上面的两个对象方法**配置bean的后置处理器。**

   - 编写bean.xml文件

     ~~~xml
     <?xml version="1.0" encoding="UTF-8"?>
     <beans xmlns="http://www.springframework.org/schema/beans"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
     
         <bean id="orders" class="com.Keafmd.spring5.bean.Orders" init-method="initMethod" destroy-method="destoryMethod">
             <property name="oname" value="手机"></property>
         </bean>
     
         <!--为当前所有的bean都加上了-->
         <!--配置后置处理器-->
         <bean id="myBeanPost" class="com.Keafmd.spring5.bean.MyBeanPost"></bean>
     
     </beans>
     ~~~

     > 上面的文件我们可以看到配置后置处理器后，相当于为所有的bean都叫上了两个后置方法。

   - 编写测试类

     ~~~java
     package com.Keafmd.spring5.testdemo;
     
     import com.Keafmd.spring5.bean.Orders;
     import org.junit.Test;
     import org.springframework.context.ApplicationContext;
     import org.springframework.context.support.ClassPathXmlApplicationContext;
     
     public class TestSpring5demo1 {
     
         //演示生命周期
         @Test
         public void test4(){
     
             ApplicationContext context = new ClassPathXmlApplicationContext("bean4.xml");
             Orders orders = context.getBean("orders",Orders.class);
             System.out.println("第四步：获取创建bean实例对象。");
             //System.out.println(orders);
             
             //手动让bean的实例销毁
             ((ClassPathXmlApplicationContext)context).close();
     
     
         }
     }
     ~~~

     测试结果

     ~~~shell
     第一步：执行无参构造。
     第二步：调用set方法，设置属性值。
     第三步 Before...
     第三步：执行初始化的方法。
     第三步 After...
     第四步：获取创建bean实例对象。
     第五步：执行销毁的方法。
     
     Process finished with exit code 0
     ~~~

### 5.2 Bean基于XML方式创建对象和注入属性

>  之前入门案例里用`<bean>`标签，来创建对象，该标签有很多属性，改标签在创建对象的时候也会默认执行无参构造方法。

bean标签属性：

|  属性名   |                    描述                    |
| :-------: | :----------------------------------------: |
|  id属性   |         唯一标识，即给对象起的名字         |
| class属性 |                 类的全路径                 |
|   name    | 功能类似于ID属性，但改属性可以添加特殊符号 |

#### 5.2.1 基于XML方式创建对象

bean.xml

~~~xml
<beans>
    <!--配置User对象创建-->
    <bean id="user" class="com.atguigu.spring5.User"></bean>
</beans>
~~~

#### 5.2.2 set方式注入属性

> DI：依赖注入，就是注入属性。有两种注入属性方式：set注入和有参构造注入

- set方法注入
  先创建一个Book类并对属性添加set方法

  ~~~java
  public class Book {
      //创建属性.
      private String bname;
      private String bauthor; 
      //创建属性对应的set方法
      public void setBname(String bname){
          this.bname = bname;
      }
      public void setBauthor (String bauthor) {
          this. bauthor = bauthor ;
      }
      public static void main(String[] args) {
          Book book = new Book() ;
          book. setBname("abc") ;
      }
      public void testDemo(){
          System. out. println (bname+"::"+bauthor);
      }
  }
  ~~~

- 使用XML方式注入属性，编写bean.xml文件

  ~~~xml
  <beans>
      <bean id="book" class ="com.atguigu.spring5.Book">
          <property name="bname" value="易筋经"></ property>
          <property name="bauthor" value="达摩老祖"></ property>
      </bean>
  </beans>
  ~~~

  |  标签名  |                             描述                             |
  | :------: | :----------------------------------------------------------: |
  | property | name:类里面属性名称<br/>value:向属性注入的值<br/>ref：向属性注入对象值 |

- 编写测试对象TestSpring.java

  ~~~java
  @Test
  public void testBook1 () {
      //1加载spring配置文件
      Appl icat ionContext context =
          new ClassPathXmlApplicat ionContext ( configLocation: "bean1. xml");
      //2获取配置创建的对象
      Book book = context.getBean("book",Book.class) ;
      System.out.println (book) ;
      book.testDemo() ;
  }
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/06/28/je7NlQ.png)

  ​                                                             [<img src="https://s1.ax1x.com/2022/06/28/je7NlQ.png" alt="je7NlQ.png" style="zoom: 67%;" />](https://imgtu.com/i/je7NlQ)

#### 5.2.3 有参构造注入

- 先创建一个Orders.java类并对属性添加有参构造方法

  ~~~java
  public class Orders {
      private String oname;
      private String addrress;
      //有参数构造
      public Orders (String oname, String address){
          this. oname = oname;
          this. address=address;
      }
      public void TestOrders(){
          System. out. println (oname+"::"+address);
      }
  }
  ~~~

- 使用XML方式注入属性，编写bean.xml文件

  ~~~xml
  <beans>
      <bean id="orders" class="com.atguigu.spring5.Orders">
          <constructor-arg name="oname" value="电脑"></constructor-arg>
          <constructor-arg name="address" value="China"></constructor-arg>
      </bean>
  </beans>
  ~~~

  > `<constructor-arg>`属性同`<property>`
  >
  > 但该标签还有一个index属性，即可以通过索引值指定有参构造中的属性值

- 编写TestSpring.java类进行测试

  ~~~java
  public void testOrders() {
      //1 加载spring配置文件
      Applicat ionContext context =
          new ClassPathXmlApplicationContext ("bean1.xml");
      //2获取配置创建的对象
      Orders orders = context. getBean("orders",Orders.class) ;
      System. out. println (orders) ; 
      orders. ordersTest() ;
  }
  ~~~

  输出结果：**电脑::China**

#### 5.2.4 p名称空间注入

> 使用p名称空间注入，可以简化set方式注入中`<property>`标签使用过多的现象。

- 添加一个p名称空间在配置文件上面
  [p名称空间：](https://s1.ax1x.com/2022/06/28/jebFPK.png)
  										[<img src="https://s1.ax1x.com/2022/06/28/jebFPK.png" alt="jebFPK.png" style="zoom:50%;" />](https://imgtu.com/i/jebFPK)

- 修改bena.xml文件

  ~~~xml
  <bean id= "book" class="com.atguigu.spring5.Book" p:bname="易筋经" p:bauthor="达摩老祖">
  </bean>
  ~~~

#### 5.2.5 注入其他类型属性

1. 注入空值
   在bean.xml中，要想给属性设置空值，需要用到`<null>`标签

   ~~~xml
   <bean id="book" class ="com.atguigu.spring5.Book">
       <property name="bname" value="易筋经"></ property>
       <property name="bauthor">
           <null/>
       </property>
   </bean>
   ~~~

2. 注入值中包含一些特殊符号

   在bean.xml中，要想给属性设置特殊符号，可以用转移符号，也可以用CDATA实现

   ~~~xml
   <property name-" address" >
       <value><![CDATA[<<南京>>]]></value>
   </property>
   ~~~


#### 5.2.6 注入外部Bean

> 创建外部Bean
>
> 1. **创建两个类service类和dao类。**
> 2. **在service调用dao里面的方法。**
> 3. **在spring配置文件中进行配置。**

- UserDao接口

  ~~~java
  package com.Keafmd.spring5.dao;
  
  /**
   * Keafmd
   *
   * @ClassName: UserDao
   * @Description:
   * @author: 牛哄哄的柯南
   * @date: 2021-01-15 9:30
   */
  
  public interface UserDao {
  
      public void updat();
  }
  ~~~

- UserDaoimp.java，是UserDao接口的实现类

  ~~~java
  package com.Keafmd.spring5.dao;
  
  /**
   * Keafmd
   *
   * @ClassName: UserDaoImpl
   * @Description: 实现类
   * @author: 牛哄哄的柯南
   * @date: 2021-01-15 9:31
   */
  public class UserDaoImpl implements UserDao{
      @Override
      public void updat() {
          System.out.println("dao updat.....");
      }
  }
  ~~~

- UserService.java

  ~~~java
  package com.Keafmd.spring5.service;
  import com.Keafmd.spring5.dao.UserDao;
  import com.Keafmd.spring5.dao.UserDaoImpl;
  
  public class UserService {
  
      //创建UserDao类型属性，生成set方法
      private  UserDao userDao;
  
      public void setUserDao(UserDao userDao) {
          this.userDao = userDao;
      }
  
      
      public void add(){
          System.out.println("service add.....");
          
          //1、原始方式
          //创建UserDao对象
         /* UserDao userDao = new UserDaoImpl();
          userDao.updat();*/
          
          //调用dao中的updat方法
          userDao.updat();
  
      }
      
  }
  ~~~

- Bean.xml，编写XML文件注入对象

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
      <!--外部bean-->
      <!--1 service 和 dao的对象创建-->
      <bean id="userService" class="com.Keafmd.spring5.service.UserService">
          <!--注入userDao对象
              name属性:类里面的属性名称
              ref属性：创建UserDao对象bean标签id值
          -->
          <property name="userDao" ref="userDaoImpl"></property>
      </bean>
      <bean id="userDaoImpl" class="com.Keafmd.spring5.dao.UserDaoImpl"></bean>
  </beans>
  ~~~

- 编写测试类Test.java

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.User;
  import com.Keafmd.spring5.bean.Emp;
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestBean {
      @Test
      public void testBean1(){
          //1、载Spring的配置文件
          ApplicationContext applicationContext = new ClassPathXmlApplicationContext("Bean.xml");
          //2、获取配置文件中创建的对象  默认是执行无参的构造方法创建
          UserService userservice =applicationContext.getBean("userService", UserService.class);
          //System.out.println(userservice);
          userservice.add();
      }
  }
  ~~~

  输出结果：

  ~~~shell
  service add.....
  dao updat.....
  
  Process finished with exit code 0
  ~~~

  > 我们可以看到调用Service的add方法后，会执行`userDao.updat()`，之后输出`UserDaoimp`类中的updat方法。由此可见UserDaoimp实例化对象被赋值给了`userDao`

#### 5.2.7 注入内部Bean

> **一对多的关系：部门和员工。**
>
> **在实体类之间表示一对多的关系，员工表示所属部门，使用对象类型属性进行表示。**

- 创建Dept类，用于存储部门名称

  ~~~java
  package com.Keafmd.spring5.bean;
  
  public class Dept {
  
      private String dname;
  
      public void setDname(String dname) {
          this.dname = dname;
      }
  
      @Override
      public String toString() {
          return "Dept{" +
                  "dname='" + dname + '\'' +
                  '}';
      }
  }
  ~~~

- 创建Emp.java类，标识每个员工信息，和他所属的部门

  ~~~java
  package com.Keafmd.spring5.bean;
  
  /**
   * Keafmd
   *
   * @ClassName: Emp
   * @Description: 员工类
   * @author: 牛哄哄的柯南
   * @date: 2021-01-15 9:53
   */
  public class Emp {
  
      private String ename;
      private String gender;
  
      //表示员工属于某一个部门,使用对象的形式表示
      private Dept dept;
  
  
      public void setDept(Dept dept) {
          this.dept = dept;
      }
  
      public void setEname(String ename) {
          this.ename = ename;
      }
  
      public void setGender(String gender) {
          this.gender = gender;
      }
  
      public void add(){
          System.out.println(ename+" "+gender+" "+dept);
      }
  }
  ~~~

- 编写Bean.xml，进行内部属性注入

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
  
      <!--内部bean-->
      <bean id="emp" class="com.Keafmd.spring5.bean.Emp">
          <!--先设置两个普通的属性-->
          <property name="ename" value="小明"></property>
          <property name="gender" value="男"></property>
  
          <!--对象类型的属性-->
          <property name="dept">
              <bean id="dept" class="com.Keafmd.spring5.bean.Dept">
                  <property name="dname" value="安保部"></property>
              </bean>
          </property>
      </bean>
  </beans>
  ~~~

  > 可以看到我们用内部嵌套`<bean>`标签的方式，完成了对Emp类中dept属性的赋值。
  >
  > **我们是把部门bean写到员工bean里的，这就是内部bean。**

- 编写测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.User;
  import com.Keafmd.spring5.bean.Emp;
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestBean {
  
      @Test
      public void testBean2(){
          //1、载Spring的配置文件
          ApplicationContext applicationContext = new ClassPathXmlApplicationContext("bean3.xml");
  
          //2、获取配置文件中创建的对象  默认是执行无参的构造方法创建
          Emp emp =applicationContext.getBean("emp", Emp.class);
  
  		//System.out.println(userservice);
          emp.add();
  
      }
  }
  ~~~

  测试结果：

  ~~~shell
  小明 男 Dept{dname='安保部'}
  
  Process finished with exit code 0
  ~~~

#### 5.2.8 级联赋值

第一种写法：

> **Dept类和Emp类都不变。写个新的配置文件bean4.xml，改变配置文件的内容。**

- bean4.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
  
      <!--级联赋值第一种写法-->
      <bean id="emp" class="com.Keafmd.spring5.bean.Emp">
          <!--先设置两个普通的属性-->
          <property name="ename" value="小红"></property>
          <property name="gender" value="女"></property>
  
          <!--级联赋值-->
          <property name="dept" ref ="dept"></property>
      </bean>
  
      <bean id="dept" class="com.Keafmd.spring5.bean.Dept">
          <property name="dname" value="财务部"></property>
      </bean>
  
  </beans>
  ~~~

  > 我们可以看到级联复制和外部bean注入方式很类似。

- 编写测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.User;
  import com.Keafmd.spring5.bean.Emp;
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestBean {
  
      //级联赋值第一种方法测试
      @Test
      public void testBean3(){
          //1、载Spring的配置文件
          ApplicationContext applicationContext = new ClassPathXmlApplicationContext("bean4.xml");
  
          //2、获取配置文件中创建的对象  默认是执行无参的构造方法创建
          Emp emp =applicationContext.getBean("emp", Emp.class);
  
  		//System.out.println(userservice);
          emp.add();
  
      }
  
  }
  ~~~

  测试结果：

  ~~~shell
  小红 女 Dept{dname='财务部'}
  
  Process finished with exit code 0
  ~~~

第二种写法

> **Dept类不变，Emp类多加个生成dept的get方法，改变配置文件的内容，在配置文件中加上`<property name="dept.dname" value="技术部"></property>`语句。**

- 在Emp中加入dept的get方法

  ~~~java
  package com.Keafmd.spring5.bean;
  
  /**
   * Keafmd
   *
   * @ClassName: Emp
   * @Description: 员工类 级联赋值的第二种写法
   * @author: 牛哄哄的柯南
   * @date: 2021-01-15 9:53
   */
  public class Emp {
  
      private String ename;
      private String gender;
  
      //表示员工属于某一个部门,使用对象的形式表示
      private Dept dept;
  
  
       // 级联赋值的第二种办法加的语句，生成dept的get方法
      public Dept getDept() {
          return dept;
      }
  
      public void setDept(Dept dept) {
          this.dept = dept;
      }
  
      public void setEname(String ename) {
          this.ename = ename;
      }
  
      public void setGender(String gender) {
          this.gender = gender;
      }
  
      public void add(){
          System.out.println(ename+" "+gender+" "+dept);
      }
  }
  ~~~

- bean4.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
  
      <!--级联赋值-->
      <bean id="emp" class="com.Keafmd.spring5.bean.Emp">
          <!--先设置两个普通的属性-->
          <property name="ename" value="小红"></property>
          <property name="gender" value="女"></property>
  
          <!--级联赋值-->
          <property name="dept" ref ="dept"></property>
  
  
  
          <!--级联赋值第二种办法的语句，需要get方法-->
          <property name="dept.dname" value="技术部"></property>
  
  
      </bean>
  
  
      <bean id="dept" class="com.Keafmd.spring5.bean.Dept">
  		<!--<property name="dname" value="财务部"></property>-->
      </bean>
  
  </beans>
  ~~~

  > 可以看到通过直接给`<property>`标签给dept的dname属性赋值来完成对整个部门名称对象的赋值

- 编写测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.User;
  import com.Keafmd.spring5.bean.Emp;
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestBean {
  
      //级联赋值第二种方法测试
      @Test
      public void testBean3(){
          //1、载Spring的配置文件
          ApplicationContext applicationContext = new ClassPathXmlApplicationContext("bean4.xml");
  
          //2、获取配置文件中创建的对象  默认是执行无参的构造方法创建
          Emp emp =applicationContext.getBean("emp", Emp.class);
  
  		//System.out.println(userservice);
          emp.add();
  
      }
  
  }
  ~~~

  测试结果：

  ~~~shell
  小红 女 Dept{dname='技术部'}
  
  Process finished with exit code 0
  ~~~

### 5.3 注入集合属性

> 通过Bean管理还可以给集合注入属性。

#### 5.3.1 注入集合(数组、List、Map、Set)类型属性

> **（1）创建类，定义数组，list，map，set类型属性，并且生成对应的set方法。
> （2）在spring配置文件中进行配置。**

- 创建Stu.java类存放各种集合

  ~~~java
  package com.Keafmd.spring5.collectiontype;
  
  import java.util.Arrays;
  import java.util.List;
  import java.util.Map;
  import java.util.Set;
  
  public class Stu {
  
      //1、数组类型属性
      private String[] courses;
  
      //2、list集合类型属性
      private List<String> list;
  
      //3、map集合类型属性
      private Map<String,String> maps;
  
      //4、set集合类型属性
      private Set<String> sets;
  
  
      //学生所学的多门课程
      private List<Course> courseList;
  
      public void setCourseList(List<Course> courseList) {
          this.courseList = courseList;
      }
  
      public void setCourses(String[] courses) {
          this.courses = courses;
      }
  
      public void setList(List<String> list) {
          this.list = list;
      }
  
      public void setMaps(Map<String, String> maps) {
          this.maps = maps;
      }
  
      public void setSets(Set<String> sets) {
          this.sets = sets;
      }
  
      public void test(){
          System.out.println(Arrays.toString(courses));
          System.out.println(list);
          System.out.println(maps);
          System.out.println(sets);
          System.out.println(courseList);
      }
  }
  ~~~

- 创建Course.java类，设置设置课程名称

  ~~~java
  public class Course{
      private String cname; //课程名称
      public void setCname (String cname){
          this.cname = cname;
      }
  }
  ~~~

- 创建bean.xml给集合设置值

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
  
      <!--集合类型属性注入-->
      <bean id="stu" class="com.Keafmd.spring5.collectiontype.Stu">
          <!--数组类型属性注入-->
          <property name="courses">
              <array>
                  <value>Java</value>
                  <value>C++</value>
                  <value>Python</value>
              </array>
          </property>
  
          <!--list类型属性注入-->
          <property name="list">
              <list>
                  <value>小明</value>
                  <value>小红</value>
              </list>
          </property>
  
          <!--map类型属性注入-->
          <property name="maps">
              <map>
                  <entry key="Java" value="java"></entry>
                  <entry key="C++" value="c++"></entry>
              </map>
          </property>
  
          <!--set类型属性注入-->
          <property name="sets">
              <set>
                  <value>北京</value>
                  <value>上海</value>
              </set>
          </property>
  
          <!--注入list集合类型，值是对象-->
          <property name="courseList">
              <list>
                  <ref bean="course1"></ref>
                  <ref bean="course2"></ref>
              </list>
          </property>
      </bean>
      
      
      <!--创建多个course对象-->
      <bean id="course1" class="com.Keafmd.spring5.collectiontype.Course">
          <property name="cname" value="Spring5框架"></property>
      </bean>
  
      <bean id="course2" class="com.Keafmd.spring5.collectiontype.Course">
          <property name="cname" value="MyBatis框架"></property>
      </bean>
  </beans>
  ~~~

  这里注意各集合标签使用

  | 集合名称 |      集合标签       |
  | :------: | :-----------------: |
  |   数组   | `<array>`或`<list>` |
  |   list   |      `<list>`       |
  |   map    |       `<map>`       |
  |   set    |       `<set>`       |

  使用集合对象时要使用`<ref bean>`标签

- 创建测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.bean.Orders;
  import com.Keafmd.spring5.collectiontype.Book;
  import com.Keafmd.spring5.collectiontype.Course;
  import com.Keafmd.spring5.collectiontype.Stu;
  import com.Keafmd.spring5.factorybean.MyBean;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestSpring5demo1 {
  
      @Test
      public void testCollection1(){
  
          ApplicationContext context = new ClassPathXmlApplicationContext("bean1.xml");
          Stu stu = context.getBean("stu",Stu.class);
          stu.test();
      }
  
  }
  ~~~

  输出结果：

  ~~~shell
  [Java, C++, Python]
  [小明, 小红]
  {Java=java, C++=c++}
  [北京, 上海]
  [Course{cname='Spring5框架'}, Course{cname='MyBatis框架'}]
  
  Process finished with exit code 0
  ~~~

#### 5.3.2 把集合注入公共部分提取出来

> （1）在spring配置文件中引入名称空间util（
> 在配置信息中添加xmlns:util="http://www.springframework.org/schema/util"和http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd"）。
> （2）提取list集合类型属性注入。
> （3）把提取的list集合类型属性注入使用。
>
> 注意：引入名称空间时，只需要`xsi:schemaLocation`内的值复制一份，然后将里面的`bean`字段改为`util`即可

- 编写Book.java类

  ~~~java
  package com.Keafmd.spring5.collectiontype;
  
  import java.util.List;
  
  public class Book {
      private List<String> list;
  
      public void setList(List<String> list) {
          this.list = list;
      }
      public void test(){
          System.out.println(list);
      }
  }
  ~~~

- 编写bean.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:util="http://www.springframework.org/schema/util"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd">
  
      <!--把集合注入部分提取出来-->
  
      <!--1、提取list集合类型属性注入-->
      <util:list id="bookList">
          <value>老人与海</value>
          <value>平凡的世界</value>
          <value>阿甘正传</value>
      </util:list>
  
      <!--2、提取list集合类型属性注入使用-->
      <bean id="book" class="com.Keafmd.spring5.collectiontype.Book">
          <property name="list" ref="bookList"></property>
      </bean>
  
  </beans>
  ~~~

  > 可以看到我们将list属性的公共部分提取出来用`<util:list>`标签包裹，其他集合方式一样。里面也可以用`<ref bean="">`方式注入对象值。
  >
  > 之后再用`<property>`标签的ref属性将值绑定到公共部分id值即可。

- 编写测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.bean.Orders;
  import com.Keafmd.spring5.collectiontype.Book;
  import com.Keafmd.spring5.collectiontype.Course;
  import com.Keafmd.spring5.collectiontype.Stu;
  import com.Keafmd.spring5.factorybean.MyBean;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestSpring5demo1 {
  
      @Test
      public void testCollection2(){
  
          ApplicationContext context = new ClassPathXmlApplicationContext("bean2.xml");
          Book book = context.getBean("book",Book.class);
          book.test();
  
      }
  
  }
  ~~~

  测试结果：

  ~~~shell
  [老人与海, 平凡的世界, 阿甘正传]
  
  Process finished with exit code 0
  ~~~

### 5.4 工厂Bean

> Spring有两种类型bean,一种普通bean,另外一 种工厂bean ( FactoryBean)
>
> 1. 普通bean:在配置文件中定义bean类型就是返回类型。如bean标签中的class属性值：com.Keafmd.spring5.collectiontype.Book。的返回值就只能是Book类型。
> 2. bean: 在配置文件定义bean类型可以和返回类型不一样

- 创建一个工厂类MyBean.java，作为工厂Bean，其要实现FactoryBean接口。在实现的方法中，定义返回的bean类型。

  ~~~java
  public class MyBean implements FactoryBean<Course> {
      //定义返回bean
      @0verride
      public Course getObject() throws Exception {
          Course course = new Course() ;
          course.setCname ("abc");
          return course;
      }
  }
  ~~~

  > 上面将MyBean对象的返回类型改为了Course类型。

- 编写bean.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:util="http://www.springframework.org/schema/util"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd">
      
  <!--如果不设置返回类型此时默认就是MyBean类型-->
  <bean id="myBean" class="com.atguigu.spring5.factorybean.MyBean" >
  
  </beans>
  ~~~

- 编写测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.bean.Orders;
  import com.Keafmd.spring5.collectiontype.Book;
  import com.Keafmd.spring5.collectiontype.Course;
  import com.Keafmd.spring5.collectiontype.Stu;
  import com.Keafmd.spring5.factorybean.MyBean;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestSpring5demo1 {
  
      @Test
      public void testCollection2(){
  
          Appl icat ionContext context =
              		new ClassPathXmlApplicat ionContext ( configLocation: "bean.xml");
          Course course = context.getBean("myBean",Course.class) ;
          System.out.println (course) ;
      }
  }
  ~~~

  测试结果：

  ~~~shell
  Course {cname='abc'}
  
  Process finished with exit code 0
  ~~~


### 5.5 XML自动装配

> 我们之前通过的ref属性或者value注入属性属于手动装配属性。
>
> **自动装配分为两种方式：根据属性名称自动注入，根据属性类型自动注入。**
>
> 自动装配需要用到bean标签属性 `autowire`

autowire常用属性值有两个

| 属性值 |                             描述                             |
| ------ | :----------------------------------------------------------: |
| byName | 根据属性名称自动注入 ，要注入的那个值bean的id值要和类里面属性名称一样 |
| byType |           根据属性类型自动注入，该值不适合多值注入           |

- 创建一个Dept.java类，用于返回一段字符串

  ~~~java
  package com.Keafmd.spring5.autowire;
  
  public class Dept {
      @Override
      public String toString() {
          return "Dept{}";
      }
  }
  ~~~

- 编写Emp.java类，用于获取字符串

  ~~~java
  package com.Keafmd.spring5.autowire;
  
  public class Emp {
  
      private Dept dept; // id和这里保持一致
  
      public void setDept(Dept dept) {
          this.dept = dept;
      }
  
      @Override
      public String toString() {
          return "Emp{" +
                  "dept=" + dept +
                  '}';
      }
  
      public void test(){
          System.out.println(dept);
      }
  }
  ~~~

  > 注意下面的xml文件注入对象id要和这里的属性名称一致

- 配置bean.xml文件

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
  
      <!--自动装配
      bean标签属性 autowire ，配置自动装配
      autowire属性常用的两个值：
      byName 根据属性名称自动注入 ，要注入的那个值bean的id值要和类里面属性名称一样
      byType：根据属性类型自动注入
      -->
      <bean id="emp" class="com.Keafmd.spring5.autowire.Emp" autowire="byType">
      </bean>
  
      <bean id="dept" class="com.Keafmd.spring5.autowire.Dept"></bean>
  
      <!--根据属性类型注入，多写这行就会报错，类型匹配到了两个bean,byName不会错-->
      <!--<bean id="dept1" class="com.Keafmd.spring5.autowire.Dept"></bean>-->
  
  </beans>
  ~~~

  > 上面的`autowire`属性值为`byType`所以只能匹配一个值，如果同时注入多个值，会报错。

- 编写测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.autowire.Emp;
  import com.Keafmd.spring5.bean.Orders;
  import com.Keafmd.spring5.collectiontype.Book;
  import com.Keafmd.spring5.collectiontype.Course;
  import com.Keafmd.spring5.collectiontype.Stu;
  import com.Keafmd.spring5.factorybean.MyBean;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestSpring5demo1 {
  
      @Test
      public void test5(){
  
          ApplicationContext context = new ClassPathXmlApplicationContext("bean5.xml");
          Emp emp = context.getBean("emp",Emp.class);
          System.out.println(emp);
  
      }
  }
  ~~~

  测试结果：

  ~~~shell
  Emp{dept=Dept{}}
  
  Process finished with exit code 0
  ~~~

### 5.6 Spring引入外部属性文件配置

1. 直接配置数据库的信息

   - xml配置文件直接配置：

     ~~~xml
     <?xml version="1.0" encoding="UTF-8"?>
     <beans xmlns="http://www.springframework.org/schema/beans"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xmlns:p="http://www.springframework.org/schema/p"
            xmlns:util="http://www.springframework.org/schema/util"
            xmlns:context="http://www.springframework.org/schema/context"
            xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                                http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd
                                http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
     
         <!--直接配置连接池-->
         <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
     
             <property name="driverClassName" value="com.mysql.jdbc.Driver"></property>
             <property name="url" value="jdbc:mysql://localhost:3306/userDb"></property>
             <property name="username" value="root" ></property>
             <property name="password" value="root" ></property>
         </bean>
     </beans>
     ~~~

     > 上面同样要创建名称空间，和之前一样修改xmls和xsi
     >
     > 我们一般不会这样用，不便于修改，我们看下面的引入外部属性文件配置的方法

2. 引入外部属性文件配置数据库连接

   - 导入进来一个druid-1.0.9.jar

     [导入jar包](https://s1.ax1x.com/2022/07/02/j3artJ.png)							[<img src="https://s1.ax1x.com/2022/07/02/j3artJ.png" alt="j3artJ.png" style="zoom: 67%;" />](https://imgtu.com/i/j3artJ)

   - 引入到当前项目。
     [引入当前项目：](https://s1.ax1x.com/2022/07/02/j3a5Ae.png)                         [![j3a5Ae.png](https://s1.ax1x.com/2022/07/02/j3a5Ae.png)](https://imgtu.com/i/j3a5Ae)

     [引入当前项目2：](https://s1.ax1x.com/2022/07/02/j3aqjP.png)

     [![j3aqjP.png](https://s1.ax1x.com/2022/07/02/j3aqjP.png)](https://imgtu.com/i/j3aqjP)

   - 配置德鲁伊连接池，新建一个jdbc.properties文件，写数据库的相关信息。

     ~~~properties
     jdbc.driverClass=com.mysql.jdbc.Driver
     jdbc.url=jdbc:mysql://127.0.0.1:3306/userDb?characterEncoding=utf8&useUnicode=true&useSSL=false
     jdbc.username=root
     jdbc.password=root
     ~~~

   - 创建bean.xml文件配置数据库连接

     ~~~xml
     <?xml version="1.0" encoding="UTF-8"?>
     <beans xmlns="http://www.springframework.org/schema/beans"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xmlns:p="http://www.springframework.org/schema/p"
            xmlns:util="http://www.springframework.org/schema/util"
            xmlns:context="http://www.springframework.org/schema/context"
            xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                                http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd
                                http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
     
     
         <!--引入外部的属性文件-->
         <context:property-placeholder location="classpath:jdbc.properties"/>
     
         <!--配置连接池-->
         <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
     
             <property name="driverClassName" value="${jdbc.driverClass}"></property>
             <property name="url" value="${jdbc.url}" ></property>
             <property name="username" value="${jdbc.username}" ></property>
             <property name ="password" value="${jdbc.password}" ></property>
     
         </bean>
     
     </beans>
     ~~~

     > 此时数据库连接就完成了

## ==6. 基于注解方式实现对象创建==

> 什么是注解：
>
> 1. 注解是代码特殊标记，格式: @注解名称(属性名称=属性值,属性名称=属性…)
> 2. 使用注解，注解作用在类上面，方法上面，属性上面。
> 3. 使用注解目的:简化xml配置。

针对Bean管理中创建对象提供的注解

| 注解        |               说明                |
| ----------- | :-------------------------------: |
| @Component  |   推荐使用在类上用于实例化Bean    |
| @Controller | 推荐使用在web层类上用于实例化bean |
| @Service    |  推荐使用在service用于实例化bean  |
| @Repository | 推荐使用在dao层类上用于实例化bean |

==注意：这四个注解的功能是一样的都可以用来创建bean实例，用哪个都可以，只是为了区分，我们使用相对应的。==

- 要想使用注解，要先把spring-aop-5.2.6.RELEASE.jar引入到项目中。拷贝到lib目录下

  [导入依赖包：](https://s1.ax1x.com/2022/07/02/j30fBV.png)					[![j30fBV.png](https://s1.ax1x.com/2022/07/02/j30fBV.png)](https://imgtu.com/i/j30fBV)

  [引入到项目中：](https://s1.ax1x.com/2022/07/02/j3079J.png)

  ​					[<img src="https://s1.ax1x.com/2022/07/02/j3079J.png" alt="j3079J.png" style="zoom:67%;" />](https://imgtu.com/i/j3079J)

- 编写bean.xml文件，开启组件扫描

  > 要使用注解，先配置XML告诉注解扫描文件范围
  >
  > - 如果要扫描多个包，多个包用逗号隔开
  > - 直接写到上层目录

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
  
      <!--开启组件扫描
      1、如果要扫描多个包，多个包用逗号隔开
      2、直接写到上层目录
      -->
      <context:component-scan base-package="com.Keafmd"></context:component-scan>
  
  </beans>
  ~~~

- 创建UserService.java类，在该类中实例化自己

  ~~~java
  package com.Keafmd.spring5.service;
  
  import org.springframework.stereotype.Service;
  
  //在注解里的value值可以不写，默认就是类的首字母小写 userService
  // @Component(value = "userService")  //<bean id="userService" class=".."/>
  @Service
  public class UserService {
  
      public void add(){
          System.out.println("service add......");
      }
  }
  =
  ~~~

  > 在注解里的value值可以不写，默认就是类的首字母小写。
  >
  > 上面的代码等效于之前XML注入中的`<bean id="userService" class=".."/>`

- 创建测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestSpring5Demo1 {
      @Test
      public void testService(){
          ApplicationContext context = new ClassPathXmlApplicationContext("bean1.xml");
          UserService userService = context.getBean("userService",UserService.class);
          System.out.println(userService);
          userService.add();
      }
  }
  ~~~

  测试结果：

  ~~~shell
  com.Keafmd.spring5.service.UserService@436a4e4b
  service add......
  
  Process finished with exit code 0
  ~~~


### 6.1 组件扫描配置

> **默认的情况就是都扫描。**但是可以通过配置注解的方式选择扫面范围

|            设置             |                   说明                   |
| :-------------------------: | :--------------------------------------: |
| use-default-filters=“false” | 表示现在不使用默认fifter，自己配置fifter |
|   context:include-filter    |             设置扫描哪些内容             |
|   context:exclude-filter    |            设置不扫描哪些内容            |

- 设置扫描哪些内容，创建bena1.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
  
      <!--
          use-default-filters="false"  表示现在不使用默认fifter，自己配置fifter
          context:include-filter 设置扫描哪些内容
  
          下面这个代表只扫描 Controller注解
      -->
      <context:component-scan base-package="com.Keafmd" use-default-filters="false">
          <context:include-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
  
      </context:component-scan>
  </beans>
  ~~~

  > `use-default-filters=false`表示不使用默认扫描
  >
  > `context:include-filter`表示设置扫描哪些内容

- 设置不扫描哪些内容，创建bean2.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
  
      <!--
      	context:exclude-filter 设置不扫描哪些内容
          下面这个代表 不扫描 Controller注解，其它的扫描
      -->
      <context:component-scan base-package="com.Keafmd">
          <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
  
      </context:component-scan>
  
  </beans>
  ~~~

  > `context:exclude-filter` 设置不扫描哪些内容

### 6.2 注解方式实现属性注入

> 同XML注入一样，注解注入也同样可以使用多种方式

注解注入四种方式：

|    注解名称    |                     说明                     |
| :------------: | :------------------------------------------: |
| **@AutoWired** |           **根据属性类型自动装配**           |
| **@Qualifier** | **根据属性的名称注入要和@AutoWired一起使用** |
| **@Resource**  |    **可以根据类型输入也可以根据名称注入**    |
|   **@Value**   |             **注入普通类型属性**             |

> 上面的前三种是注入对象的，@Value是注入普通类型属性的（如String）。

1. 注入对象类型属性方式：

   > 第一步：把service和dao对象创建，在service和dao类添加创建对象的注解。 
   >
   > 第二步：在service注入dao对象。

- 创建UserDao.java接口：

  ~~~java
  package com.Keafmd.spring5.dao;
  
  public interface UserDao {
      public void add();
  }
  ~~~

- 创建UserDaoImpl.java类：

  ~~~java
  package com.Keafmd.spring5.dao;
  
  import org.springframework.stereotype.Repository;
  
  @Repository("userDaoImpl01")
  public class UserDaoImpl implements UserDao{
      @Override
      public void add() {
          System.out.println("dao add ...");
      }
  }
  ~~~

- 编写UserService.java类用于实现前三种方法

  ~~~java
  package com.Keafmd.spring5.service;
  
  import com.Keafmd.spring5.dao.UserDao;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.beans.factory.annotation.Qualifier;
  import org.springframework.beans.factory.annotation.Value;
  import org.springframework.stereotype.Repository;
  import org.springframework.stereotype.Service;
  
  import javax.annotation.Resource;
  
  @Service
  public class UserService {
  
      //定义dao类型属性 ,不需要添加set方法了
      //添加注入属性的注解
     /* @Autowired
      @Qualifier(value = "userDaoImpl01")  // 要和@AutoWired一起使用 ,填写value值是为了解决有多个实现类，根据类型的话就没法区分
      private UserDao userDao;*/
  
  //    @Resource  //根据类型注入
      @Resource(name = "userDaoImpl01")  // 根据名称注入
      private UserDao userDao;
  
      public void add(){
          System.out.println("service add......");
          userDao.add();
      }
  }
  ~~~

  > 上面代码中：
  >
  > 如果接口只有一个实现类可以用：`@Autowired`
  >
  > 如果接口有多个实现类则用：` @Qualifier(value = "userDaoImpl01")`指定对象实例化名称
  > `@Resource`既可以进行类型注入，也可以进行名称注入

- 编写测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestSpring5Demo1 {
      @Test
      public void testService(){
          ApplicationContext context = new ClassPathXmlApplicationContext("bean1.xml");
          UserService userService = context.getBean("userService",UserService.class);
          System.out.println(userService);
          userService.add();
      }
  }
  ~~~

  测试结果：

  ~~~shell
  com.Keafmd.spring5.service.UserService@7ea37dbf
  service add......
  dao add ...
  
  Process finished with exit code 0
  ~~~

2. 注入普通类型属性

   > 修改UserService类，添加一个String类型的属性，并使用@Value注解对普通类型的属性进行注入，在添加一个输出语句方便测试。

   - 修改UserService类：

     ~~~java
     package com.Keafmd.spring5.service;
     
     import com.Keafmd.spring5.dao.UserDao;
     import org.springframework.beans.factory.annotation.Autowired;
     import org.springframework.beans.factory.annotation.Qualifier;
     import org.springframework.beans.factory.annotation.Value;
     import org.springframework.stereotype.Repository;
     import org.springframework.stereotype.Service;
     
     import javax.annotation.Resource;
     
     @Service
     public class UserService {
     
         @Value(value = "Keafmd")
         private String name;
     
         //定义dao类型属性 ,不需要添加set方法了
         //添加注入属性的注解
        /* @Autowired
         @Qualifier(value = "userDaoImpl01")  // 要和@AutoWired一起使用 ,填写value值是为了解决有多个实现类，根据类型的话就没法区分
         private UserDao userDao;*/
     
     //    @Resource  //根据类型注入
         @Resource(name = "userDaoImpl01")  // 根据名称注入
         private UserDao userDao;
     
         public void add(){
             System.out.println("name:"+name);
             System.out.println("service add......");
             userDao.add();
         }
     }
     ~~~

     > 上面`@Value(value = "Keafmd")`给属性name进行赋值，其他代码不变

   - 测试结果

     ~~~shell
     com.Keafmd.spring5.service.UserService@7ea37dbf
     name:Keafmd
     service add......
     dao add ...
     
     Process finished with exit code 0
     ~~~

### 6.3 完全注解开发

> 完全注解开发的意思就是不使用xml配置文件，之前我们可以用使用注解方式替代xml配置文件方式完成很多事情，但是还是要在配置文件中开启组件扫描，现在我们创建一个配置类来完全代替配置文件，在配置类中完成开启组件扫描的操作。

- 创建配置类，替代xml配置文件

  > @Configuration： 把当前类作为配置类，替代xml配置文件

- 编写SpringConfig类来作为XML文件的替代类

  ~~~java
  package com.Keafmd.spring5.config;
  
  import org.springframework.context.annotation.ComponentScan;
  import org.springframework.context.annotation.Configuration;
  
  @Configuration //把当前类作为配置类，替代xml配置文件
  @ComponentScan(basePackages = {"com.Keafmd"}) //替代配置文件中的<context:component-scan base-package="com.Keafmd"></context:component-scan>
  public class SpringConfig {
  }
  ~~~

  > `@Configuration`：表示这是一个XML的替代类
  >
  > `@ComponentScan(basePackages = {"com.Keafmd"})`：替代配置文件中的开启注解扫描

- 编写测试类

  ~~~java
  package com.Keafmd.spring5.testdemo;
  
  import com.Keafmd.spring5.config.SpringConfig;
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.annotation.AnnotationConfigApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestSpring5Demo1 {
      
      @Test
      public void testService2(){
          // 加载配置类
          ApplicationContext context = new AnnotationConfigApplicationContext(SpringConfig.class);
          UserService userService = context.getBean("userService",UserService.class);
          System.out.println(userService);
          userService.add();
      }
  }
  ~~~

  > 第15行代码表示获取XML替代类文件

  测试结果：

  ~~~shell
  com.Keafmd.spring5.service.UserService@7ce3cb8e
  name:Keafmd
  service add......
  dao add ...
  
  Process finished with exit code 0
  ~~~

# 三. AOP讲解

> AOP为Aspect Oriented Programming的缩写，意为：面向切面编程，通过预编译方式和运行期间动态代理实现程序功能的统一维护的一种技术。AOP是OOP的延续，是软件开发中的一个热点，也是Spring框架中的一个重要内容，是函数式编程的一种衍生范型。

## 1. Aop基本概念

> 利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。
>
> ==通俗描述：就是不通过修改源代码方式添加新的功能，这个过程就叫做AOP。==

我们通过一个具体的登录功能的例子来通俗的理解AOP的意思：

[登录功能图解：](https://s1.ax1x.com/2022/07/03/jGldG6.png)						

​					[<img src="https://s1.ax1x.com/2022/07/03/jGldG6.png" alt="jGldG6.png" style="zoom:50%;" />](https://imgtu.com/i/jGldG6)

## 2. AOP底层原理

> AOP底层使用动态代理，分为以下两种情况。

- 有接口的情况，使用JDK动态代理。

  > 创建接口实现类代理对象，增强类的方法。

  [JDK动态代理](https://s1.ax1x.com/2022/07/04/jY1uTJ.png)

  [![jY1uTJ.png](https://s1.ax1x.com/2022/07/04/jY1uTJ.png)](https://imgtu.com/i/jY1uTJ)

- 没有接口的情况，使用CGLIB动态代理。

  > 创建子类的代理对象，增强类的方法。

  [CGLIB动态代理](https://s1.ax1x.com/2022/07/04/jY1UTH.png)

  [![jY1UTH.png](https://s1.ax1x.com/2022/07/04/jY1UTH.png)](https://imgtu.com/i/jY1UTH)

## ==3. JDK动态代理实现==

> JDK动态代理使用Proxy类里面的newProxyInstance方法创建代理对象。

Proxy类方法介绍

|     类型      |                             描述                             |
| :-----------: | :----------------------------------------------------------: |
| static Object | newProxyInstance(ClassLoader loader, 类<?>[] interfaces, InvocationHandler h)返回指定接口的代理类的实例，该接口将方法调用分派给指定的调用处理程序。 |

Proxy方法参数解析：

|       参数名        |                             介绍                             |
| :-----------------: | :----------------------------------------------------------: |
| ClassLoader loader  |                          类加载器。                          |
| 类<?>[] interfaces  |       增强方法所在类，这个类实现的接口，支持多个接口。       |
| InvocationHandler h | 实现这个接口InvocationHandler创建代理的对象，在这个类里写增强的方法。 |

代码实现

> 1. 创建接口，定义方法。
> 2. 创建接口实现类，实现方法。
> 3. 使用Proxy类创建接口代理对象。

- 创建UserDao.java接口

  ~~~java
  package com.Keafmd.spring5;
  
  public interface UserDao {
  
      public int add(int a,int b);
  
      public String updat(String id);
  }
  ~~~

- 创建UserDaoImpl.java实现类

  ~~~java
  package com.Keafmd.spring5;
  
  public class UserDaoImpl implements UserDao{
      @Override
      public int add(int a, int b) {
          System.out.println("add执行中...");
          return a+b;
      }
  
      @Override
      public String updat(String id) {
          System.out.println("updat执行中...");
          return id;
  
      }
  }
  ~~~

- 创建JDKProxy.java代理类

  ~~~java
  package com.Keafmd.spring5;
  
  import java.lang.reflect.InvocationHandler;
  import java.lang.reflect.Method;
  import java.lang.reflect.Proxy;
  
  public class JDKProxy {
      public static void main(String[] args) {
          //创建接口实现类代理对象
          Class[] interfaces = {UserDao.class};
          
          /*Proxy.newProxyInstance(JDKProxy.class.getClassLoader(), interfaces, new InvocationHandler() {
              @Override
              public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
                  return null;
              }
          });*/
  
          UserDaoImpl Userdaoimpl = new UserDaoImpl();
          UserDao dao = (UserDao) Proxy.newProxyInstance(JDKProxy.class.getClassLoader(), interfaces, new UserDaoProxy(Userdaoimpl));
  
          System.out.println("-----------对add方法进行增强----------");
          int result = dao.add(1, 2);
          System.out.println("result:" + result);
  
          System.out.println("------------不增强updat方法------------");
  
          String res = dao.updat("Keafmd");
          System.out.println("res:" + res);
  
      }
  }
  
  //创建代理对象代码
  class UserDaoProxy implements InvocationHandler {
  
      //获取UserDaoImpl
      //有参构造传递
      private Object obj;
  
      public UserDaoProxy(Object obj) {
          this.obj = obj;
      }
  
      //增强的逻辑
      @Override
      //proxy是代理对象
      public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
  
          if ("add".equals(method.getName())) { //通过判断实现对不同方法的增强
  
  
              //方法执行之前
              System.out.println("方法之前执行..." + method.getName());
  
              //被增强的方法执行
              Object res = method.invoke(obj, args);
  
              //方法执行之后
              System.out.println("方法之后执行" + obj);
  
              return res;
  
          } else { //不增强
  
              Object res = method.invoke(obj, args);
              return res;
  
          }
      }
  }
  ~~~

  执行结果

  ~~~shell
  -----------对add方法进行增强----------
  方法之前执行...add
  add执行中...
  方法之后执行com.Keafmd.spring5.UserDaoImpl@5e481248
  result:3
  ------------不增强updat方法------------
  updat执行中...
  res:Keafmd
  
  Process finished with exit code 0
  ~~~

  > 上面的代码第10行获取要增强的方法所在类即UserDao的路径，是`Proxy.newProxyInstance`方法的第二个参数，第一个参数是获取当前代理对象的路径。第19行我们获取了UserDaoImpl对象用于增强其中的方法。并作为第三个参数方法中有参构造的参数来使用。当运行到23行时，就会调用`UserDaoProxy`中的增强方法，对add方法进行增强。

## 4. AOP核心概念术语的通俗理解

> 假设我们有一个User类，类中有下面的这些方法，我么就根据这个类来具体通俗的理解连接点、切入点、通知、切面这四个核心概念术语。

- 连接点(JoinPoint)

  > User类中的四个方法都可以被增强（加一些功能），哪些方法可以被增强，那这些方法就可以被称为连接点，所以这四个方法都可以被称为连接点。

- 切入点(Pointcut)

  > 在User类中有四个方法，假如我们只增强某个方法，那这些实际被我们增强的方法就称为切入点，真正增强的方法才成为切入点，没有实际增强（可以被增强但是没有增强）的不是。

- 通知（增强）(Advice)

  > 假如我们要在add方法进行之后做一些其它操作，那我们在方法进行后添加的代码部分就称为增强（通知），也就是说实际增加的逻辑部分就称为通知。

  通知有多种类型：

  |   类型   |                             介绍                             |
  | :------: | :----------------------------------------------------------: |
  | 前置通知 |              想在add方法的前面执行的逻辑部分。               |
  | 后置通知 |              想在add方法的后面执行的逻辑部分。               |
  | 环绕通知 |            想在add方法的前面后面执行的逻辑部分。             |
  | 异常通知 |              当add方法发生异常执行的逻辑部分。               |
  | 最终通知 | 相当于java代码中的try-catch-finally中fianlly部分，如果add方法代码有异常那么后置通知就不会执行了，但是最终通知有没有异常都还是会执行。 |

- 切面(Aspect)

  > 切面指的是一个动作或过程，指的就是把通知应用到切入点的过程，假如我们想对add方法加上增强，我们把增强的部分加上去的过程就叫切面。

# 四. AOP操作

> Spring 框架一般都是基于 AspectJ 实现 AOP 操作。
> 需要注意的是：AspectJ 不是 Spring 组成部分，独立 AOP 框架，一般把 AspectJ 和 Spirng 框架一起使用，进行 AOP 操作。

## 1. AspectJ 实现 AOP 操作准备工作

> 在项目工程里面引入 AOP 相关依赖。

[AOP相关依赖：](https://s1.ax1x.com/2022/07/04/jY0itK.png)

​													[<img src="https://s1.ax1x.com/2022/07/04/jY0itK.png" alt="jY0itK.png" style="zoom: 50%;" />](https://imgtu.com/i/jY0itK)

> 如果是maven项目，使用pom.xml代替引入jar包的过程（注意）

pom.xml

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.Keafmd</groupId>
    <artifactId>day04_eesy_01jdbctemplate</artifactId>
    <version>1.0-SNAPSHOT</version>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>7</source>
                    <target>7</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
    <packaging>jar</packaging>

    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>5.2.6.RELEASE</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>5.2.7.RELEASE</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-tx</artifactId>
            <version>5.2.7.RELEASE</version>
        </dependency>

        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.46</version>
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
            <version>1.1.10</version>
        </dependency>

        <dependency>
            <groupId>org.aspectj</groupId>
            <artifactId>aspectjweaver</artifactId>
            <version>1.8.9</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>compile</scope>
        </dependency>
    </dependencies>

</project>
~~~

- 切入点表达式的使用

  > 切入点表达式作用（通俗的讲）：知道对哪个类里面的哪个方法进行增强。
  >
  > 语法结构： ==execution([权限修饰符] [返回类型] [类全路径] [方法名称] ([参数列表]) )==

  ~~~java
  //例 1：对 com.atguigu.dao.BookDao 类里面的 add 进行增强
  execution( * com.atguigu.dao.BookDao.add(…))
      
  //例 2：对 com.atguigu.dao.BookDao 类里面的所有的方法进行增强
  execution( * com.atguigu.dao.BookDao. * (…))
      
  //例 3：对 com.atguigu.dao 包里面所有类，类里面所有方法进行增强
  execution( * com.atguigu.dao. * . * (…))
  ~~~

## 2. AOP 操作（AspectJ 注解）

- 创建User.java类，在类里面定义方法

  ~~~java
  package com.Keafmd.spring5.aopanno;
  
  import org.springframework.stereotype.Component;
  
  @Component
  public class User {
  
      public void add(){
  //        int i = 10/0;
          System.out.println("add....");
      }
  
  }
  ~~~

- 创建增强类（编写增强逻辑）UserProxy.java，在增强类里面，创建方法，让不同方法代表不同通知类型

  ~~~java
  package com.Keafmd.spring5.aopanno;
  
  import org.aspectj.lang.ProceedingJoinPoint;
  import org.aspectj.lang.annotation.*;
  import org.springframework.core.annotation.Order;
  import org.springframework.stereotype.Component;
  
  @Component
  @Aspect //生成代理对象
  @Order(3)
  public class UserProxy {
  
  
      //相同的切入点抽取
      @Pointcut(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void pointdemo(){
  
      }
  
      //前置通知
      //@Before注解就表示前置通知
      @Before(value = "pointdemo()")
      public void beafor(){
          System.out.println("before...");
      }
  
      //最终通知
      @After(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void after(){
          System.out.println("after...");
      }
  
      //后置通知（返回通知）
      @AfterReturning(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void afterReturning(){
          System.out.println("afterReturning...");
      }
  
      //异常执行
      @AfterThrowing(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void afterThrowing(){
          System.out.println("afterThrowing...");
      }
  
      //环绕通知
      @Around(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void around(ProceedingJoinPoint proceedingJoinPoint) throws Throwable {
          System.out.println("around-before...");
  
          //被增强的方法执行
          proceedingJoinPoint.proceed();
  
          System.out.println("around-after...");
      }
  
  }
  ~~~

- 进行通知的配置

  > 1. 在 spring 配置文件中，开启注解扫描
  > 2. 使用注解创建 User 和 UserProxy 对象
  > 3. 在增强类上面添加注解 @Aspect
  > 4. 在 spring 配置文件中开启生成代理对象

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xmlns:aop="http://www.springframework.org/schema/aop"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
      http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd
      http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop.xsd">
  
  
      <!--开启注解扫描-->
      <context:component-scan base-package="com.Keafmd.spring5.aopanno"></context:component-scan>
  
      <!--开启AspectJ生成代理对象-->
      <aop:aspectj-autoproxy></aop:aspectj-autoproxy>
  
  </beans>
  ~~~

- 配置不同类型的通知

  > 在增强类的里面，在作为通知方法上面添加通知类型注解，使用切入点表达式配置。

  UserProxy 类

  ~~~java
  package com.Keafmd.spring5.aopanno;
  
  import org.aspectj.lang.ProceedingJoinPoint;
  import org.aspectj.lang.annotation.*;
  import org.springframework.core.annotation.Order;
  import org.springframework.stereotype.Component;
  
  @Component
  @Aspect //生成代理对象
  @Order(3)
  public class UserProxy {
  
  
      //相同的切入点抽取
      @Pointcut(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void pointdemo(){
  
      }
  
      //前置通知
      //@Before注解就表示前置通知
      @Before(value = "pointdemo()")
      public void beafor(){
          System.out.println("before...");
      }
  
      //最终通知
      @After(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void after(){
          System.out.println("after...");
      }
  
      //后置通知（返回通知）
      @AfterReturning(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void afterReturning(){
          System.out.println("afterReturning...");
      }
  
      //异常执行
      @AfterThrowing(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void afterThrowing(){
          System.out.println("afterThrowing...");
      }
  
      //环绕通知
      @Around(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void around(ProceedingJoinPoint proceedingJoinPoint) throws Throwable {
          System.out.println("around-before...");
  
          //被增强的方法执行
          proceedingJoinPoint.proceed();
  
          System.out.println("around-after...");
      }
  
  }
  ~~~


### 2.1 抽取公共切入点

> 上面的代码还可以进行修改，我们可以把`execution`表达式相同部分抽去出来做一个公共方法。

~~~java
//相同的切入点抽取
@Pointcut(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
public void pointdemo(){

}

//前置通知
//@Before注解就表示前置通知
@Before(value = "pointdemo()")
public void beafor(){
    System.out.println("before...");
}
~~~

> 可以看到我们用`Pointcut`注解来抽取出来公共的表达式，并定义一个方法。此时我们`@Before`注解值就直接调用方法就可以了

### 2.2 设置增强类优先级

> 有多个增强类多同一个方法进行增强，可以设置增强类优先级
>
> ==在增强类上面添加注解 @Order(数字类型值)，数字类型值越小优先级越高。==

- 以PersonProxy类为例

  ~~~java
  package com.Keafmd.spring5.aopanno;
  
  import org.aspectj.lang.annotation.AfterReturning;
  import org.aspectj.lang.annotation.Aspect;
  import org.aspectj.lang.annotation.Before;
  import org.springframework.core.annotation.Order;
  import org.springframework.stereotype.Component;
  
  @Component
  @Aspect
  @Order(1) //越小优先级越高
  public class PersonProxy {
  
      //前置通知
      //@Before注解就表示前置通知
      @Before(value = "execution(* com.Keafmd.spring5.aopanno.User.add(..))")
      public void beafor(){
          System.out.println("Person before...");
      }
  
  }
  ~~~

  > 通过@Order设置后PersonProxy 的前置通知就会比UserProxy 的前置通知先执行。

### 2.3 完全使用注解开发

> 创建配置类，这样就不需要使用 xml 配置文件了。

- 创建配置类ConfigAop.java

  ~~~java
  package com.Keafmd.spring5.config;
  
  import org.springframework.context.annotation.ComponentScan;
  import org.springframework.context.annotation.Configuration;
  import org.springframework.context.annotation.EnableAspectJAutoProxy;
  
  @Configuration
  @ComponentScan(basePackages = {"com.Keafmd"})  //开启注解扫描
  @EnableAspectJAutoProxy(proxyTargetClass = true)  //开启AspectJ生成代理对象
  public class ConfigAop {
  }
  ~~~

- 创建测试文件

  ~~~java
  package com.Keafmd.spring5.test;
  
  import com.Keafmd.spring5.aopanno.User;
  import com.Keafmd.spring5.config.ConfigAop;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.annotation.AnnotationConfigApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestAop {
  
      @Test
      public void testAOPnno(){
          ApplicationContext context = new ClassPathXmlApplicationContext("bean2.xml");
          User user = context.getBean("user",User.class);
          user.add();
      }
  
      //完全注解
      @Test
      public void testAOPnno2(){
          ApplicationContext context = new AnnotationConfigApplicationContext(ConfigAop.class);
          User user = context.getBean("user",User.class);
          user.add();
      }
  }
  ~~~

  运行结果：

  ~~~shell
  Person before...
  around-before...
  before...
  add....
  around-after...
  after...
  afterReturning...
  
  Process finished with exit code 0
  ~~~

# 五. JdbcTemplate操作数据库

> 1、什么是JdbcTemplate
> Spring 框架对JDBC进行封装，使用JdbcTemplate方便实现对数据库操作。

## 1. JdbcTemplate准备工作

- 引入相关jar包
  [JdbcTemplate相关jar包](https://s1.ax1x.com/2022/07/05/jNorBn.png)

  ​												[<img src="https://s1.ax1x.com/2022/07/05/jNorBn.png" alt="jNorBn.png" style="zoom:50%;" />](https://imgtu.com/i/jNorBn)

- 如果是maven项目，使用pom.xml代替引入jar包的过程（注意）

  pom.xml：

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <project xmlns="http://maven.apache.org/POM/4.0.0"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
  
      <groupId>com.Keafmd</groupId>
      <artifactId>day04_eesy_01jdbctemplate</artifactId>
      <version>1.0-SNAPSHOT</version>
      <build>
          <plugins>
              <plugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-compiler-plugin</artifactId>
                  <configuration>
                      <source>7</source>
                      <target>7</target>
                  </configuration>
              </plugin>
          </plugins>
      </build>
      <packaging>jar</packaging>
  
      <dependencies>
          <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-context</artifactId>
              <version>5.2.6.RELEASE</version>
          </dependency>
  
          <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-jdbc</artifactId>
              <version>5.2.7.RELEASE</version>
          </dependency>
  
          <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-tx</artifactId>
              <version>5.2.7.RELEASE</version>
          </dependency>
  
          <dependency>
              <groupId>mysql</groupId>
              <artifactId>mysql-connector-java</artifactId>
              <version>5.1.46</version>
          </dependency>
          <dependency>
              <groupId>com.alibaba</groupId>
              <artifactId>druid</artifactId>
              <version>1.1.10</version>
          </dependency>
  
          <dependency>
              <groupId>org.aspectj</groupId>
              <artifactId>aspectjweaver</artifactId>
              <version>1.8.9</version>
          </dependency>
          <dependency>
              <groupId>junit</groupId>
              <artifactId>junit</artifactId>
              <version>4.12</version>
              <scope>compile</scope>
          </dependency>
      </dependencies>
  
  
  </project>
  ~~~

- 配置bean.xml配置文件

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:p="http://www.springframework.org/schema/p"
         xmlns:util="http://www.springframework.org/schema/util"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
  
      <!--开启组件扫描-->
      <context:component-scan base-package="com.Keafmd"></context:component-scan>
  
      <!--引入外部的属性文件-->
      <context:property-placeholder location="classpath:jdbc.properties"/>
  
      <!--配置连接池-->
      <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
  
          <property name="driverClassName" value="${jdbc.driverClass}"></property>
          <property name="url" value="${jdbc.url}" ></property>
          <property name="username" value="${jdbc.username}" ></property>
          <property name ="password" value="${jdbc.password}" ></property>
  
      </bean>
  
      <!--创建jdbcTemplate对象-->
      <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
          <!--注入DataSource-->
          <property name="dataSource" ref="dataSource"></property>
  
      </bean>
  
  </beans>
  ~~~

  > 在 spring 配置文件配置数据库连接池，配置 JdbcTemplate 对象，注入 DataSource。配置时用的是引用外部配置文件，所以还需要引入外部的属性文件，同时创建对象时是基于注解的所以还要开启组件扫描。

- 配置连接数据库的外部属性文件jdbc.properties

  ~~~properties
  jdbc.driverClass=com.mysql.jdbc.Driver
  jdbc.url=jdbc:mysql://127.0.0.1:3306/user_db?characterEncoding=utf8&useUnicode=true&useSSL=false
  jdbc.username=root
  jdbc.password=root
  ~~~

- 创建service类，创建dao类，在dao注入jdbcTemplate对象

  - 创建BookService.java文件

    ~~~java
    @Service
    public class BookService {
        //注入dao
        @Autowired
        private BookDao bookDao;
    }
    ~~~

  - 创建BookDaoImp.java文件

    ~~~java
    @Repository
    public class BookDaoImpl implements BookDao {
        //注入JdbcTemplate
        @Autowired
        private JdbcTemplate jdbcTemplate;
    }
    ~~~

  - 创建BookDao文件

    ~~~java
    public interface BookDao{
    }
    ~~~

## 2. JdbcTemplate对数据库进行添加操作

- 首先创建t_book表

  [t_book表及字段：](https://s1.ax1x.com/2022/07/05/jN7tSS.png)

  ​												[<img src="https://s1.ax1x.com/2022/07/05/jN7tSS.png" alt="jN7tSS.png" style="zoom:50%;" />](https://imgtu.com/i/jN7tSS)

- 创建实体类Book.java

  ~~~java
  public class User {
      private String userId;
      private Str ing username;
      private String ustatus;
      
      public void setUserId (String userId){
          this. userId = userId;
      }
      public void setUsername (String username){
          this. username = username;
      }
      public void setUstatus (String ustatus) {
          this. ustatus = ustatus;
      }
      public String getUserId() {
          return userId;
      }
  }
  ~~~

- 创建BookServ.java实现添加书籍对象的操作

  ~~~java
  @Service
  public class BookService {
      //注入dao
      @Autowired
      private BookDao bookDao;
      //添加的方法
      public void addBook (Book book) {
          bookDao.add(book) ;
      }
  }
  ~~~

- 在BookDao.java中添加add方法接口

  ~~~java
  public interface BookDao {
      //添加的方法
      void add (Book book) ;
  }
  ~~~

- 之后在BookDaoImp.java中实现add方法

  ~~~java
  @Repository
  public class BookDaoImpl impl ements BookDao {
      //注入JdbcTemplate
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
      //实现添加方法
      @Override
      public void add (Book book) {
          //1创建sq1语句
          String sql = "insert into t_book values(?, ?,?)" ;
          //2调用方法实现
          0bject[] args = {book.getUserId(),book.getUsername (),book.getUstatus()} ;
          int update = jdbcTemplate. update (sql, args) ;
          System. out. println (update) ;
  
      }
  }
  ~~~

  > `jdbcTemplate`中的update方法可以实现对数据库的：增加，修改和删除操作。

  jdbcTemplate的两个参数：

  |     参数      |                    描述                    |
  | :-----------: | :----------------------------------------: |
  |  String sql   |               执行的sql语句                |
  | Object.. args | 可变参数，设置sql语句的值,即实体类中的属性 |

- 创建测试类

  ~~~java
  public class TestBook {
      @Test
      public void testJdbcTemplate() {
          ApplicationContext conηtext =
              new ClassPathXmlApplicationContext ("bean.xml");
          BookService bookService = context. getBean("bookService",BookService.class) ;
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("java");
          book. setUstatus("a") ;
          bookService. addBook (book) ;
      }
  }
  ~~~

  运行结果：

  ~~~shell
  1
  #表示的是影响的行数，这里添加成功
  ~~~

## 3. JdbcTemplate实现数据库的修改和删除操作

- 在BookService.java中再添加两个方法(修改和删除)

  ~~~java
  @Service
  public class BookService {
      //注入dao
      @Autowired
      private BookDao bookDao;
      //添加的方法
      public void addBook (Book book) {
          bookDao.add(book) ;
      }
  
      //修改的方法
      public void updateBook (Book book) {
          bookDao. updateBook (book) ; 
      }
      
      //删除的方法
      public void deleteBook (String id){
          bookDao. delete(id) ;
      }
  
  }
  ~~~

- 在BookDao中添加两种方法的接口

  ~~~java
  public interface BookDao {
      //添加的方法
      void add (Book book) ;
  
      //修改的方法
      void updateBook (Book book) ;
      
      //删除的方法
      void delete(String id) ;
  
  }
  ~~~

- 在实现类BookDaoImpt.java中编写实现两种方法

  ~~~java
  @Repository
  public class BookDaoImpl impl ements BookDao {
      //注入JdbcTemplate
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
      //实现添加方法
      @Override
      public void add (Book book) {
          //1创建sq1语句
          String sql = "insert into t_book values(?, ?,?)" ;
          //2调用方法实现
          0bject[] args = {book.getUserId(),book.getUsername (),book.getUstatus()} ;
          int update = jdbcTemplate. update (sql, args) ;
          System. out. println (update) ;
      }
  
      //实现修改方法
      @Override
      public void updateBook (Book book){
          String sql = "update t_book set username=?, ustatus=? where user_id=?" ;
          Object[] args = {book.getUsername (),book.getUstatus(),book.getUserId()};
          int update = jdbcTemplate. update (sql,args);
          System. out. println (update) ;
      }
  
      //实现删除方法
      @0verride
      public void delete (String id) {
          String sql = "delete from t_book where user_id=?";
          int update = jdbcTemplate. update(sql,id) ;
          System.out. println(update) ;
      }
      
  }
  ~~~

- 编写测试类

  ~~~java
  public class TestBook {
      @Test
      public void testJdbcTemplate() {
          ApplicationContext conηtext =
              new ClassPathXmlApplicationContext ("bean.xml");
          BookService bookService = context. getBean("bookService",BookService.class) ;
          
          //添加
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("java");
          book. setUstatus("a") ;
          bookService. addBook (book) ;
          
          //修改
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("javaupup");
          book. setUstatus("atguigu") ;
          bookService.addBook (book) ;
          
          //删除
          bookService.deleteBook("1");
      }
  }
  ~~~

  修改运行结果：

  [修改结果：](https://s1.ax1x.com/2022/07/05/jNqIkn.png)

  ​                                            [![jNqIkn.png](https://s1.ax1x.com/2022/07/05/jNqIkn.png)](https://imgtu.com/i/jNqIkn)

## 4. JdbcTemplate实现数据库的查询操作

### 4.1 查询返回某个值

> 查询表里面有多少条记录，返回是某个值。

- 在BookService.java中编写查询表记录方法

  ~~~java
  @Service
  public class BookService {
      //注入dao
      @Autowired
      private BookDao bookDao;
      //添加的方法
      public void addBook (Book book) {
          bookDao.add(book);
      }
  
      //修改的方法
      public void updateBook (Book book) {
          bookDao. updateBook (book); 
      }
  
      //删除的方法
      public void deleteBook (String id){
          bookDao. delete(id);
      }
  
      //查询表记录数
      public int findCount (){
          return bookDao. selectCount();
      }
  
  }
  ~~~

- 在BookDao.java中编写查询接口

  ~~~java
  public interface BookDao {
      //添加的方法
      void add (Book book) ;
  
      //修改的方法
      void updateBook (Book book) ;
      
      //删除的方法
      void delete(String id) ;
      
      //查询表记录
      int selectCount();
  
  }
  ~~~

- 在BookDaoImpt.java中编写具体实现类

  ~~~java
  @Repository
  public class BookDaoImpl impl ements BookDao {
      //注入JdbcTemplate
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
      //实现添加方法
      @Override
      public void add (Book book) {
          //1创建sq1语句
          String sql = "insert into t_book values(?, ?,?)" ;
          //2调用方法实现
          0bject[] args = {book.getUserId(),book.getUsername (),book.getUstatus()} ;
          int update = jdbcTemplate. update (sql, args) ;
          System. out. println (update) ;
      }
  
      //实现修改方法
      @Override
      public void updateBook (Book book){
          String sql = "update t_book set username=?, ustatus=? where user_id=?" ;
          Object[] args = {book.getUsername (),book.getUstatus(),book.getUserId()};
          int update = jdbcTemplate. update (sql,args);
          System. out. println (update) ;
      }
  
      //实现删除方法
      @0verride
      public void delete (String id) {
          String sql = "delete from t_book where user_id=?";
          int update = jdbcTemplate. update(sql,id) ;
          System.out. println(update) ;
      }
  
      //查询表记录数
      @Override
      public int selectCount() {
          String sql =" select count(*) from t_ book" ;
          Integer count = jdbcTemplate. queryFor0bject (sql,Integer.class) ;
          return count;
      }
  
  }
  ~~~

  > 上面编写的方法中用到了`jdbcTemplate`的新方法`queryFor0bject`该方法需要传递两个参数。具体用法如下

  |    参数名    |               描述                |
  | :----------: | :-------------------------------: |
  |  String sql  |              sql语句              |
  | requiredType | 返回类型的Class(如：string.class) |

- 编写测试类

  ~~~java
  public class TestBook {
      @Test
      public void testJdbcTemplate() {
          ApplicationContext conηtext =
              new ClassPathXmlApplicationContext ("bean.xml");
          BookService bookService = context. getBean("bookService",BookService.class) ;
  
          //添加
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("java");
          book. setUstatus("a") ;
          bookService. addBook (book) ;
  
          //修改
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("javaupup");
          book. setUstatus("atguigu") ;
          bookService.addBook (book) ;
  
          //删除
          bookService.deleteBook("1");
  
          //查询表数据
          int count = bookService.findCount();
          System.out.println(count);
  
      }
  }
  ~~~

  运行结果

  ~~~shell
  2 
  # 这就表示t_book表中有两条数据
  ~~~

### 4.2 查询返回对象

> 使用场景：淘宝查询一个图书的详情页

- 在BookService.java中编写查询返回对象的方法

  ~~~java
  @Service
  public class BookService {
      //注入dao
      @Autowired
      private BookDao bookDao;
      //添加的方法
      public void addBook (Book book) {
          bookDao.add(book);
      }
  
      //修改的方法
      public void updateBook (Book book) {
          bookDao. updateBook (book); 
      }
  
      //删除的方法
      public void deleteBook (String id){
          bookDao. delete(id);
      }
  
      //查询表记录数
      public int findCount (){
          return bookDao. selectCount();
      }
  
      //查询返回对象	
      public Book find0ne(String id){	
          return bookDao. findBookInfo(id) ;
      }
  
  }
  ~~~

- 在BookDao.java中创建方法接口

  ~~~java
  public interface BookDao {
      //添加的方法
      void add (Book book) ;
  
      //修改的方法
      void updateBook (Book book) ;
      
      //删除的方法
      void delete(String id) ;
      
      //查询表记录
      int selectCount();
      
      //查询返回对象
      Book findBookInfo(String id);
  
  }
  ~~~

- 在实现类BookDaoImpt.java中实现方法

  ~~~java
  @Repository
  public class BookDaoImpl impl ements BookDao {
      //注入JdbcTemplate
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
      //实现添加方法
      @Override
      public void add (Book book) {
          //1创建sq1语句
          String sql = "insert into t_book values(?, ?,?)" ;
          //2调用方法实现
          0bject[] args = {book.getUserId(),book.getUsername (),book.getUstatus()} ;
          int update = jdbcTemplate. update (sql, args) ;
          System. out. println (update) ;
      }
  
      //实现修改方法
      @Override
      public void updateBook (Book book){
          String sql = "update t_book set username=?, ustatus=? where user_id=?" ;
          Object[] args = {book.getUsername (),book.getUstatus(),book.getUserId()};
          int update = jdbcTemplate. update (sql,args);
          System. out. println (update) ;
      }
  
      //实现删除方法
      @0verride
      public void delete (String id) {
          String sql = "delete from t_book where user_id=?";
          int update = jdbcTemplate. update(sql,id) ;
          System.out. println(update) ;
      }
  
      //查询表记录数
      @Override
      public int selectCount() {
          String sql =" select count(*) from t_ book" ;
          Integer count = jdbcTemplate. queryFor0bject (sql,Integer.class) ;
          return count;
      }
  
      //查询返回对象
      @Override
      public Book findBookInfo (String id){
          String sql =" select * from t_book where user_id=?" ;
          //调用方法.
          Book book = 
              jdbcTemplate. queryFor0bject (sql,new BeanPropertyRowMapper<Book>(Book.class),id);
          return book;
      }
  
  }
  ~~~

  > 这里我们仍然用到`queryForObject`方法，但要用到另一个结构，这里需要传递三个参数

  |   参数名   |                             描述                             |
  | :--------: | :----------------------------------------------------------: |
  | String sql |                           sql语句                            |
  | RowMapper  | 本质是一个接口，可以针对返回不同类型的数据，使用这个接口的是实现类完成数据的封装 |
  |    args    |                      传递sql语句中的值                       |

- 创建测试对象

  > 这里数据映射类已经重写了toString方法

  ~~~java
  public class TestBook {
      @Test
      public void testJdbcTemplate() {
          ApplicationContext conηtext =
              new ClassPathXmlApplicationContext ("bean.xml");
          BookService bookService = context. getBean("bookService",BookService.class) ;
          
          //添加
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("java");
          book. setUstatus("a") ;
          bookService. addBook (book) ;
          
          //修改
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("javaupup");
          book. setUstatus("atguigu") ;
          bookService.addBook (book) ;
          
          //删除
          bookService.deleteBook("1");
          
          //返回查询对象
          Book book=bookService.find0ne("1");
  		System. out. println (book) ;
          
      }
  }
  ~~~

  运行结果：

  ~~~shell
  Book{userId='1',username='aaa',ustatus='a'} 
  ~~~

### 4.3 查询返回集合

> 场景：查询图书列表分页

- 在BookService.java中创建查询返回集合方法

  ~~~java
  @Service
  public class BookService {
      //注入dao
      @Autowired
      private BookDao bookDao;
      //添加的方法
      public void addBook (Book book) {
          bookDao.add(book);
      }
  
      //修改的方法
      public void updateBook (Book book) {
          bookDao. updateBook (book); 
      }
  
      //删除的方法
      public void deleteBook (String id){
          bookDao. delete(id);
      }
  
      //查询表记录数
      public int findCount (){
          return bookDao. selectCount();
      }
  
      //查询返回对象	
      public Book find0ne(String id){	
          return bookDao. findBookInfo(id) ;
      }
  
      //查询返回结合
      public List<Book> findAll() {
          return bookDao.findA11Book();
      }
  
  }
  ~~~

- 在BookDao中创建方法

  ~~~java
  public interface BookDao {
      //添加的方法
      void add (Book book) ;
  
      //修改的方法
      void updateBook (Book book) ;
  
      //删除的方法
      void delete(String id) ;
  
      //查询表记录
      int selectCount();
  
      //查询返回对象
      Book findBookInfo(String id);
  
      //查询返回集合
      List<Book> findAllBook();
  
  }
  ~~~

- 在BookDaoImpt.java中编写实现类

  ~~~java
  @Repository
  public class BookDaoImpl impl ements BookDao {
      //注入JdbcTemplate
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
      //实现添加方法
      @Override
      public void add (Book book) {
          //1创建sq1语句
          String sql = "insert into t_book values(?, ?,?)" ;
          //2调用方法实现
          0bject[] args = {book.getUserId(),book.getUsername (),book.getUstatus()} ;
          int update = jdbcTemplate. update (sql, args) ;
          System. out. println (update) ;
      }
  
      //实现修改方法
      @Override
      public void updateBook (Book book){
          String sql = "update t_book set username=?, ustatus=? where user_id=?" ;
          Object[] args = {book.getUsername (),book.getUstatus(),book.getUserId()};
          int update = jdbcTemplate. update (sql,args);
          System. out. println (update) ;
      }
  
      //实现删除方法
      @0verride
      public void delete (String id) {
          String sql = "delete from t_book where user_id=?";
          int update = jdbcTemplate. update(sql,id) ;
          System.out. println(update) ;
      }
  
      //查询表记录数
      @Override
      public int selectCount() {
          String sql =" select count(*) from t_ book" ;
          Integer count = jdbcTemplate. queryFor0bject (sql,Integer.class) ;
          return count;
      }
  
      //查询返回对象
      @Override
      public Book findBookInfo (String id){
          String sql =" select * from t_book where user_id=?" ;
          //调用方法.
          Book book = 
              jdbcTemplate. queryFor0bject (sql,new BeanPropertyRowMapper<Book>(Book.class),id);
          return book;
      }
  
      //查询返回结合
      @Override
      public List<Book> findAllBook() {
          String sql ="select * from t_book";
          //调用方法
          List<Book> bookList = 
              jdbcTemplate.query(sql,new BeanPropertyRowMapper<Book>(Book.class)) ;
          return bookList ;
      }
  
  
  }
  ~~~

  > 这里我们调用的是`query`方法，该方法有三个参数，具体如下：

  |   参数名   |                             描述                             |
  | :--------: | :----------------------------------------------------------: |
  | String sql |                           sql语句                            |
  | RowMapper  | 本质是一个接口，可以针对返回不同类型的数据，使用这个接口的是实现类完成数据的封装 |
  |    args    |                      传递sql语句中的值                       |

- 编写测试类

  ~~~java
  public class TestBook {
      @Test
      public void testJdbcTemplate() {
          ApplicationContext conηtext =
              new ClassPathXmlApplicationContext ("bean.xml");
          BookService bookService = context. getBean("bookService",BookService.class) ;
  
          //添加
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("java");
          book. setUstatus("a") ;
          bookService. addBook (book) ;
  
          //修改
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("javaupup");
          book. setUstatus("atguigu") ;
          bookService.addBook (book) ;
  
          //删除
          bookService.deleteBook("1");
  
          //返回查询对象
          Book book=bookService.find0ne("1");
          System. out. println (book) ;
  
          //查询返回集合
          List<Book> all = bookService. findAll();
          System. out. println(all) ;
  
      }
  }
  ~~~

  运行结果：

  ~~~shell
  [Book {userId='1',username='aaa',status='a' }, 
  Book {userId='2',username='bbb',ustatus='b'}]
  
  ~~~

## 5. JdbcTemplate实现对数据库的批量添加操作

> 批量操作：操作表里面多条记录。
>
> 要实现批量添加、修改和删除功能，需要用到`batchUpdate`方法。该方法有两个参数，具体说明如下：

|           参数名           |            描述            |
| :------------------------: | :------------------------: |
|         String sql         |          sql语句           |
| `List<Object[]>` batchArgs | List集合，添加多条记录数据 |

- 在BookService.java中添加批量添加方法

  ~~~java
  @Service
  public class BookService {
      //注入dao
      @Autowired
      private BookDao bookDao;
      //添加的方法
      public void addBook (Book book) {
          bookDao.add(book);
      }
  
      //修改的方法
      public void updateBook (Book book) {
          bookDao. updateBook (book); 
      }
  
      //删除的方法
      public void deleteBook (String id){
          bookDao. delete(id);
      }
  
      //查询表记录数
      public int findCount (){
          return bookDao. selectCount();
      }
  
      //查询返回对象	
      public Book find0ne(String id){	
          return bookDao. findBookInfo(id) ;
      }
  
      //查询返回结合
      public List<Book> findAll() {
          return bookDao.findA11Book();
      }
  
      //批量添加
      public void batchAdd (List<0bject[]> batchArgs) {
          bookDao. batchAddBook(batchArgs) ;
      }
  
  
  }
  ~~~

- 在BookDao.java中创建批量添加接口

  ~~~java
  public interface BookDao {
      //添加的方法
      void add (Book book) ;
  
      //修改的方法
      void updateBook (Book book) ;
  
      //删除的方法
      void delete(String id) ;
  
      //查询表记录
      int selectCount();
  
      //查询返回对象
      Book findBookInfo(String id);
  
      //查询返回集合
      List<Book> findAllBook();
      
      //批量添加
      void batchAddBook (List<Object[]> batchArgs) ;
  
  }
  ~~~

- 在BookDaoImpt中实现批量添加犯法

  ~~~java
  @Repository
  public class BookDaoImpl impl ements BookDao {
      //注入JdbcTemplate
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
      //实现添加方法
      @Override
      public void add (Book book) {
          //1创建sq1语句
          String sql = "insert into t_book values(?, ?,?)" ;
          //2调用方法实现
          0bject[] args = {book.getUserId(),book.getUsername (),book.getUstatus()} ;
          int update = jdbcTemplate. update (sql, args) ;
          System. out. println (update) ;
      }
  
      //实现修改方法
      @Override
      public void updateBook (Book book){
          String sql = "update t_book set username=?, ustatus=? where user_id=?" ;
          Object[] args = {book.getUsername (),book.getUstatus(),book.getUserId()};
          int update = jdbcTemplate. update (sql,args);
          System. out. println (update) ;
      }
  
      //实现删除方法
      @0verride
      public void delete (String id) {
          String sql = "delete from t_book where user_id=?";
          int update = jdbcTemplate. update(sql,id) ;
          System.out. println(update) ;
      }
  
      //查询表记录数
      @Override
      public int selectCount() {
          String sql =" select count(*) from t_ book" ;
          Integer count = jdbcTemplate. queryFor0bject (sql,Integer.class) ;
          return count;
      }
  
      //查询返回对象
      @Override
      public Book findBookInfo (String id){
          String sql =" select * from t_book where user_id=?" ;
          //调用方法.
          Book book = 
              jdbcTemplate. queryFor0bject (sql,new BeanPropertyRowMapper<Book>(Book.class),id);
          return book;
      }
  
      //查询返回结合
      @Override
      public List<Book> findAllBook() {
          String sql ="select * from t_book";
          //调用方法
          List<Book> bookList = 
              jdbcTemplate.query(sql,new BeanPropertyRowMapper<Book>(Book.class)) ;
          return bookList ;
      }
      //批量添加
      public void batchAddBook (List<0bject[]> batchArgs){
          String sql = "insert into t_book values(?, ?,?)" ;
          int[] ints = jdbcTemplate. batchUpdate (sql,batchArgs) ;
          System. out. println (Arrays. toString(ints));
      }
  
  }
  ~~~

- 编写测试类

  ~~~java
  public class TestBook {
      @Test
      public void testJdbcTemplate() {
          ApplicationContext conηtext =
              new ClassPathXmlApplicationContext ("bean.xml");
          BookService bookService = context. getBean("bookService",BookService.class) ;
  
          //添加
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("java");
          book. setUstatus("a") ;
          bookService. addBook (book) ;
  
          //修改
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("javaupup");
          book. setUstatus("atguigu") ;
          bookService.addBook (book) ;
  
          //删除
          bookService.deleteBook("1");
  
          //返回查询对象
          Book book=bookService.find0ne("1");
          System. out. println (book) ;
  
          //查询返回集合
          List<Book> all = bookService. findAll();
          System. out. println(all) ;
  
          //批量添加
          List<0bject[]> batchArgs = new ArrayList<>() ;
          0bject[] o1 = {"3","java","a"} ;
          0bject[] o2 = {"4", "c++","b"} ;
          Object[] o3 = {"5", "MySQL","c"};
          batchArgs. add(o1);
          batchArgs. add(o2);
          batchArgs. add(o3);
          //调用批量添加
          bookService. batchAdd (batchArgs);
  
  
      }
  }
  ~~~

  测试结果：

  [批量添加结果：](https://s1.ax1x.com/2022/07/06/jdZjMT.png)

  ​                                      [![jdZjMT.png](https://s1.ax1x.com/2022/07/06/jdZjMT.png)](https://imgtu.com/i/jdZjMT)

## 6. 实现批量修改操作

- 在BookService.java中创建批量修改方法

  ~~~java
  @Service
  public class BookService {
      //注入dao
      @Autowired
      private BookDao bookDao;
      //添加的方法
      public void addBook (Book book) {
          bookDao.add(book);
      }
  
      //修改的方法
      public void updateBook (Book book) {
          bookDao. updateBook (book); 
      }
  
      //删除的方法
      public void deleteBook (String id){
          bookDao. delete(id);
      }
  
      //查询表记录数
      public int findCount (){
          return bookDao. selectCount();
      }
  
      //查询返回对象	
      public Book find0ne(String id){	
          return bookDao. findBookInfo(id) ;
      }
  
      //查询返回结合
      public List<Book> findAll() {
          return bookDao.findA11Book();
      }
  
      //批量添加
      public void batchAdd (List<0bject[]> batchArgs) {
          bookDao. batchAddBook(batchArgs) ;
      }
  
      //批量修改
      public void batchUpdate (List<Object[]> batchArgs) {
          bookDao. batchUpdateBook (batchArgs) ;
      }
  
  }
  ~~~

- 在BookDao.java中创建批量修改接口

  ~~~java
  public interface BookDao {
      //添加的方法
      void add (Book book) ;
  
      //修改的方法
      void updateBook (Book book) ;
  
      //删除的方法
      void delete(String id) ;
  
      //查询表记录
      int selectCount();
  
      //查询返回对象
      Book findBookInfo(String id);
  
      //查询返回集合
      List<Book> findAllBook();
      
      //批量添加
      void batchAddBook (List<Object[]> batchArgs);
      
      //批量修改
  	void batchUpdateBook (List<Object[]> batchArgs);
  }
  ~~~

- 在BookDaoImpt.java中实现批量修改方法

  ~~~java
  @Repository
  public class BookDaoImpl impl ements BookDao {
      //注入JdbcTemplate
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
      //实现添加方法
      @Override
      public void add (Book book) {
          //1创建sq1语句
          String sql = "insert into t_book values(?, ?,?)" ;
          //2调用方法实现
          0bject[] args = {book.getUserId(),book.getUsername (),book.getUstatus()} ;
          int update = jdbcTemplate. update (sql, args) ;
          System. out. println (update) ;
      }
  
      //实现修改方法
      @Override
      public void updateBook (Book book){
          String sql = "update t_book set username=?, ustatus=? where user_id=?" ;
          Object[] args = {book.getUsername (),book.getUstatus(),book.getUserId()};
          int update = jdbcTemplate. update (sql,args);
          System. out. println (update) ;
      }
  
      //实现删除方法
      @0verride
      public void delete (String id) {
          String sql = "delete from t_book where user_id=?";
          int update = jdbcTemplate. update(sql,id) ;
          System.out. println(update) ;
      }
  
      //查询表记录数
      @Override
      public int selectCount() {
          String sql =" select count(*) from t_ book" ;
          Integer count = jdbcTemplate. queryFor0bject (sql,Integer.class) ;
          return count;
      }
  
      //查询返回对象
      @Override
      public Book findBookInfo (String id){
          String sql =" select * from t_book where user_id=?" ;
          //调用方法.
          Book book = 
              jdbcTemplate. queryFor0bject (sql,new BeanPropertyRowMapper<Book>(Book.class),id);
          return book;
      }
  
      //查询返回结合
      @Override
      public List<Book> findAllBook() {
          String sql ="select * from t_book";
          //调用方法
          List<Book> bookList = 
              jdbcTemplate.query(sql,new BeanPropertyRowMapper<Book>(Book.class)) ;
          return bookList ;
      }
      //批量添加
      public void batchAddBook (List<0bject[]> batchArgs){
          String sql = "insert into t_book values(?, ?,?)" ;
          int[] ints = jdbcTemplate. batchUpdate (sql,batchArgs) ;
          System. out. println (Arrays. toString(ints));
      }
  
      //批量修改
      public void batchUpdateBook (List <0bject[]> batchArgs) {
          String sql = "update t_book set username=?, ustatus=? where user_id=?";
          int[] ints = jdbcTemplate.batchUpdate (sql,batchArgs);
          System. out. println (Arrays.toString(ints));
      }
  
  
  }
  ~~~

- 编写测试类

  ~~~java
  public class TestBook {
      @Test
      public void testJdbcTemplate() {
          ApplicationContext conηtext =
              new ClassPathXmlApplicationContext ("bean.xml");
          BookService bookService = context. getBean("bookService",BookService.class) ;
  
          //添加
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("java");
          book. setUstatus("a") ;
          bookService. addBook (book) ;
  
          //修改
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("javaupup");
          book. setUstatus("atguigu") ;
          bookService.addBook (book) ;
  
          //删除
          bookService.deleteBook("1");
  
          //返回查询对象
          Book book=bookService.find0ne("1");
          System. out. println (book) ;
  
          //查询返回集合
          List<Book> all = bookService. findAll();
          System. out. println(all) ;
  
          //批量添加
          List<0bject[]> batchArgs = new ArrayList<>() ;
          0bject[] o1 = {"3","java","a"} ;
          0bject[] o2 = {"4", "c++","b"} ;
          Object[] o3 = {"5", "MySQL","c"};
          batchArgs. add(o1);
          batchArgs. add(o2);
          batchArgs. add(o3);
          //调用批量添加
          bookService. batchAdd (batchArgs);
  
          //批量修改
          List<Object[]> batchArgs = new ArrayList<>() ;
          0bject[] ol = {"java0909","a3","3"};
          0bject[] o2 = {"c++1010","b4","4"};
          0bject[] o3 = {"MySQL1111","c5","5"};
          batchArgs. add(o1) ;
          batchArgs. add(o2) ;
          batchArgs. add(o3) ;
          //调用方法实现批量修改
          bookService. batchUpdate (batchArgs);
  
      }
  }
  ~~~

  > 注意集合属性的顺序要和实现类中sql语句中字段顺序一样

  运行结果：

  [批量修改运行结果：](https://s1.ax1x.com/2022/07/06/jdmKnU.png)

  ​                                            [![jdmKnU.png](https://s1.ax1x.com/2022/07/06/jdmKnU.png)](https://imgtu.com/i/jdmKnU)

## 7. 实现批量删除

- 在BookService.java中创建删除方法

  ~~~java
  @Service
  public class BookService {
      //注入dao
      @Autowired
      private BookDao bookDao;
      //添加的方法
      public void addBook (Book book) {
          bookDao.add(book);
      }
  
      //修改的方法
      public void updateBook (Book book) {
          bookDao. updateBook (book); 
      }
  
      //删除的方法
      public void deleteBook (String id){
          bookDao. delete(id);
      }
  
      //查询表记录数
      public int findCount (){
          return bookDao. selectCount();
      }
  
      //查询返回对象	
      public Book find0ne(String id){	
          return bookDao. findBookInfo(id) ;
      }
  
      //查询返回结合
      public List<Book> findAll() {
          return bookDao.findA11Book();
      }
  
      //批量添加
      public void batchAdd (List<0bject[]> batchArgs) {
          bookDao. batchAddBook(batchArgs) ;
      }
  
      //批量修改
      public void batchUpdate (List<Object[]> batchArgs) {
          bookDao. batchUpdateBook (batchArgs) ;
      }
  
      //批量删除
      public void batchDelete (List<0bject[]> batchArgs){
          bookDao.batchDeleteBook (batchArgs) ;
      }
  
  
  }
  ~~~

- 编写BookDao.java方法，创建接口

  ~~~java
  public interface BookDao {
      //添加的方法
      void add (Book book) ;
  
      //修改的方法
      void updateBook (Book book) ;
  
      //删除的方法
      void delete(String id) ;
  
      //查询表记录
      int selectCount();
  
      //查询返回对象
      Book findBookInfo(String id);
  
      //查询返回集合
      List<Book> findAllBook();
      
      //批量添加
      void batchAddBook (List<Object[]> batchArgs);
      
      //批量修改
  	void batchUpdateBook (List<Object[]> batchArgs);
      
      //批量删除
      void batchDeleteBook (List<Object[]> batchArgs);
  }
  ~~~

- 在BookDaoImpt.java中编写批量删除方法

  ~~~java
  @Repository
  public class BookDaoImpl impl ements BookDao {
      //注入JdbcTemplate
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
      //实现添加方法
      @Override
      public void add (Book book) {
          //1创建sq1语句
          String sql = "insert into t_book values(?, ?,?)" ;
          //2调用方法实现
          0bject[] args = {book.getUserId(),book.getUsername (),book.getUstatus()} ;
          int update = jdbcTemplate. update (sql, args) ;
          System. out. println (update) ;
      }
  
      //实现修改方法
      @Override
      public void updateBook (Book book){
          String sql = "update t_book set username=?, ustatus=? where user_id=?" ;
          Object[] args = {book.getUsername (),book.getUstatus(),book.getUserId()};
          int update = jdbcTemplate. update (sql,args);
          System. out. println (update) ;
      }
  
      //实现删除方法
      @0verride
      public void delete (String id) {
          String sql = "delete from t_book where user_id=?";
          int update = jdbcTemplate. update(sql,id) ;
          System.out. println(update) ;
      }
  
      //查询表记录数
      @Override
      public int selectCount() {
          String sql =" select count(*) from t_ book" ;
          Integer count = jdbcTemplate. queryFor0bject (sql,Integer.class) ;
          return count;
      }
  
      //查询返回对象
      @Override
      public Book findBookInfo (String id){
          String sql =" select * from t_book where user_id=?" ;
          //调用方法.
          Book book = 
              jdbcTemplate. queryFor0bject (sql,new BeanPropertyRowMapper<Book>(Book.class),id);
          return book;
      }
  
      //查询返回结合
      @Override
      public List<Book> findAllBook() {
          String sql ="select * from t_book";
          //调用方法
          List<Book> bookList = 
              jdbcTemplate.query(sql,new BeanPropertyRowMapper<Book>(Book.class)) ;
          return bookList ;
      }
      //批量添加
      public void batchAddBook (List<0bject[]> batchArgs){
          String sql = "insert into t_book values(?, ?,?)" ;
          int[] ints = jdbcTemplate. batchUpdate (sql,batchArgs) ;
          System. out. println (Arrays. toString(ints));
      }
  
      //批量修改
      public void batchUpdateBook (List <0bject[]> batchArgs) {
          String sql = "update t_book set username=?, ustatus=? where user_id=?";
          int[] ints = jdbcTemplate.batchUpdate (sql,batchArgs);
          System. out. println (Arrays.toString(ints));
      }
  
      //批量删除
      @Override
      public void batchDeleteBook (List<0bject[]> batchArgs) {
          String sql. ="delete from t_book where user_id=?";
          int[] ints = jdbcTemplate. batchUpdate(sql,batchArgs) ; 
          System. out. println (Arrays. toString(ints));
      }
  
  }
  ~~~

- 编写测试类

  ~~~java
  public class TestBook {
      @Test
      public void testJdbcTemplate() {
          ApplicationContext conηtext =
              new ClassPathXmlApplicationContext ("bean.xml");
          BookService bookService = context. getBean("bookService",BookService.class) ;
  
          //添加
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("java");
          book. setUstatus("a") ;
          bookService. addBook (book) ;
  
          //修改
          Book book = new Book() ;
          book. setUserId("1") ;
          book. setUsername("javaupup");
          book. setUstatus("atguigu") ;
          bookService.addBook (book) ;
  
          //删除
          bookService.deleteBook("1");
  
          //返回查询对象
          Book book=bookService.find0ne("1");
          System. out. println (book) ;
  
          //查询返回集合
          List<Book> all = bookService. findAll();
          System. out. println(all) ;
  
          //批量添加
          List<0bject[]> batchArgs = new ArrayList<>() ;
          0bject[] o1 = {"3","java","a"} ;
          0bject[] o2 = {"4", "c++","b"} ;
          Object[] o3 = {"5", "MySQL","c"};
          batchArgs. add(o1);
          batchArgs. add(o2);
          batchArgs. add(o3);
          //调用批量添加
          bookService. batchAdd (batchArgs);
  
          //批量修改
          List<Object[]> batchArgs = new ArrayList<>() ;
          0bject[] ol = {"java0909","a3","3"};
          0bject[] o2 = {"c++1010","b4","4"};
          0bject[] o3 = {"MySQL1111","c5","5"};
          batchArgs. add(o1) ;
          batchArgs. add(o2) ;
          batchArgs. add(o3) ;
  
          //调用方法实现批量修改
          bookService. batchUpdate (batchArgs);
  
          //批量删除
          List<Object[]> batchArgs = new ArrayList<>();
          Object[] o1 = {"3"};
          0bject[] o2 = {"4"};
          batchArgs. add(o1) ;
          batchArgs. add(o2) ;
          //调用方法实现批量修改
          bookService. batchDelete (batchArgs);
      }
  }
  ~~~

  运行结果：

  [批量删除结果：](https://s1.ax1x.com/2022/07/06/jdKkAe.png)

  ​                                               [![jdKkAe.png](https://s1.ax1x.com/2022/07/06/jdKkAe.png)](https://imgtu.com/i/jdKkAe)

# 六. 事务操作

> 事务的概念：事务是数据库操作最基本单元，逻辑上一组操作，要么都成功，如果有一个失败所有操作都失败。
>
> 典型场景：银行转账（这两件事必须都成功或都不成功）
> lucy 转账 100 元 给 mary
> lucy 少 100，mary 多 100
>
> 事务四个特性（ACID）
> （1）原子性：这个过程不可分割，要么都成功，要么都失败。
> （2）一致性：操作之前和操作之后的总量不变。
> （3）隔离性：多事务操作时不会相互参生影响。
> （4）持久性：事务提交后数据库数据会发生变化。

## 1. 搭建事务操作环境

[搭建事务环境：](https://s1.ax1x.com/2022/07/07/j0QMfe.png)

​											[<img src="https://s1.ax1x.com/2022/07/07/j0QMfe.png" alt="j0QMfe.png" style="zoom:50%;" />](https://imgtu.com/i/j0QMfe)

- 创建数据库表，添加记录

  [创建数据库表字段：](https://s1.ax1x.com/2022/07/07/j0Qhp4.png)										[<img src="https://s1.ax1x.com/2022/07/07/j0Qhp4.png" alt="j0Qhp4.png" style="zoom:67%;" />](https://imgtu.com/i/j0Qhp4)

  [添加数据信息：](https://s1.ax1x.com/2022/07/07/j0QTn1.png)

  ​												[![j0QTn1.png](https://s1.ax1x.com/2022/07/07/j0QTn1.png)](https://imgtu.com/i/j0QTn1)、

- 代码演示

  > 1. 创建 service，搭建 dao，完成对象创建和注入关系。
  > 2. service 注入 dao，在 dao 注入 JdbcTemplate，在 配置文件中在JdbcTemplate 中注入 DataSource。
  > 3. 在 dao 创建两个方法：多钱和少钱的方法，在 service 创建方法（转账的方法）。

- 编写数据配置文件jdbc.properties

  ~~~properties
  jdbc.driverClass=com.mysql.jdbc.Driver
  jdbc.url=jdbc:mysql://127.0.0.1:3306/user_db?characterEncoding=utf8&useUnicode=true&useSSL=false
  jdbc.username=root
  jdbc.password=18044229
  ~~~

- 编写配置文件bean.xml，开启数据库连接，并注入jdbcTemplate对象

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:p="http://www.springframework.org/schema/p"
         xmlns:util="http://www.springframework.org/schema/util"
         xmlns:tx="http://www.springframework.org/schema/tx"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd
                             http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
  
      <!--开启组件扫描-->
      <context:component-scan base-package="com.Keafmd"></context:component-scan>
  
      <!--引入外部的属性文件-->
      <context:property-placeholder location="classpath:jdbc.properties"/>
  
      <!--配置连接池-->
      <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
  
          <property name="driverClassName" value="${jdbc.driverClass}"></property>
          <property name="url" value="${jdbc.url}" ></property>
          <property name="username" value="${jdbc.username}" ></property>
          <property name ="password" value="${jdbc.password}" ></property>
  
      </bean>
  
      <!--创建jdbcTemplate对象-->
      <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
          <!--注入DataSource-->
          <property name="dataSource" ref="dataSource"></property>
  
      </bean>
  
  </beans>
  ~~~

- 编写UserDao.java接口

  ~~~java
  package com.Keafmd.spring5.dao;
  
  public interface UserDao {
  
      //多钱
      public void addMoney();
  
      //少钱
      public void reduceMoney();
  }
  ~~~

- 创建接口实现类UserDaoImpl.java

  ~~~java
  package com.Keafmd.spring5.dao;
  
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.jdbc.core.JdbcTemplate;
  import org.springframework.stereotype.Repository;
  
  import javax.sql.rowset.JdbcRowSet;
  
  @Repository
  public class UserDaoImpl implements UserDao{
  
      @Autowired
      private JdbcTemplate jdbcTemplate;
  
  
      //少钱
      @Override
      public void reduceMoney() {
          String sql = "update t_account set money =money-? where username =?";
          jdbcTemplate.update(sql,100,"Lucy");
      }
  
  
      //多钱
      @Override
      public void addMoney() {
          String sql = "update t_account set money =money+? where username =?";
          jdbcTemplate.update(sql,100,"Mary");
      }
  
  
  }
  ~~~

- 编写UserService.java类调用方法

  ~~~java
  package com.Keafmd.spring5.service;
  
  import com.Keafmd.spring5.dao.UserDao;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.stereotype.Service;
  import org.springframework.transaction.annotation.Transactional;
  
  @Service
  public class UserService {
  
      //注入dao
      @Autowired
      private UserDao userDao;
  
      //转账的方法
      public void accountMoney(){
          
          // Lucy 少100
          userDao.reduceMoney();
  
          //Mary多100
          userDao.addMoney();
  
      }
  
  }
  ~~~

- 测试类

  ~~~java
  package com.Keafmd.spring5.test;
  
  import com.Keafmd.spring5.config.TxConfig;
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.annotation.AnnotationConfigApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestAccount {
  
      @Test
      public void test1(){
          ApplicationContext context = new ClassPathXmlApplicationContext("bean1.xml");
          UserService userService = context.getBean("userService",UserService.class);
          userService.accountMoney();
      }
  }
  ~~~

  运行结果：
  [事务运行结果：](https://s1.ax1x.com/2022/07/07/j0GAZn.png)

  ​                                                      [![j0GAZn.png](https://s1.ax1x.com/2022/07/07/j0GAZn.png)](https://imgtu.com/i/j0GAZn)

- 如果在UserService.java转账中间出现错误，则会出现失败情况。此时要用事务解决

  ~~~java
  package com.Keafmd.spring5.service;
  
  import com.Keafmd.spring5.dao.UserDao;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.stereotype.Service;
  import org.springframework.transaction.annotation.Transactional;
  
  @Service
  public void accountMoney() {
      try {
          //第一步开启事务
          //第二步进行业务操作
          //1ucy少100.
          userDao. reduceMoney() ;
          //模拟异常
          int i = 10/0;
          //mary多100
          userDao. addMoney();
          //第三步没有发生异常，提交事务
      } catch(Exception e) {
          //第四步出现异常，事务回滚
      }
  
  }
  ~~~

## 2. 事务管理介绍

> 1. 事务添加到 JavaEE 三层结构里面 Service 层（业务逻辑层）
> 2. 在 Spring 进行事务管理操作有两种方式：
>    （1）编程式事务管理（不方便）
>    （2）声明式事务管理（使用）
> 3. 声明式事务管理
>    （1）基于注解方式（简单方便）
>    （2）基于 xml 配置文件方式
> 4. 在 Spring 进行声明式事务管理，底层使用 AOP 原理
> 5. Spring 事务管理 API提供一个接口，代表事务管理器，这个接口针对不同的框架提供不同的实现类：
>    Spring中使用的是DataSourceTransactionManager

[事务管理接口结构：](https://s1.ax1x.com/2022/07/07/j0Ujaj.png)

​										[<img src="https://s1.ax1x.com/2022/07/07/j0Ujaj.png" alt="j0Ujaj.png" style="zoom: 67%;" />](https://imgtu.com/i/j0Ujaj)

## 3. 注解声明式事务管理

> 1. 在 spring 配置文件配置事务管理器
> 2. 在 spring 配置文件，开启事务注解
> 3. 在 spring 配置文件引入名称空间 tx
> 4. 开启事务注解

- 编写bena.xml文件，配置事务管理器

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:p="http://www.springframework.org/schema/p"
         xmlns:util="http://www.springframework.org/schema/util"
         xmlns:tx="http://www.springframework.org/schema/tx"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd
                             http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
  
      <!--开启组件扫描-->
      <context:component-scan base-package="com.Keafmd"></context:component-scan>
  
      <!--引入外部的属性文件-->
      <context:property-placeholder location="classpath:jdbc.properties"/>
  
      <!--配置连接池-->
      <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
  
          <property name="driverClassName" value="${jdbc.driverClass}"></property>
          <property name="url" value="${jdbc.url}" ></property>
          <property name="username" value="${jdbc.username}" ></property>
          <property name ="password" value="${jdbc.password}" ></property>
  
      </bean>
  
      <!--创建jdbcTemplate对象-->
      <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
          <!--注入DataSource-->
          <property name="dataSource" ref="dataSource"></property>
  
      </bean>
  
      <!--创建事务管理器-->
      <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
          <!--注入数据源-->
          <property name="dataSource" ref="dataSource"></property>
  
      </bean>
  
  
      <!--开启事务注解-->
      <tx:annotation-driven transaction-manager="transactionManager"></tx:annotation-driven>
  
  </beans>
  ~~~

  > 第36行之后，创建了事务管理器，及开启事务注解
  >
  > 在 service 类上面（或者 service 类里面方法上面）添加事务注解：
  >
  > 1. @Transactional，这个注解添加到类上面，也可以添加方法上面
  > 2. 如果把这个注解添加类上面，这个类里面所有的方法都添加事务
  > 3. 如果把这个注解添加方法上面，为这个方法添加事务

- 编写UserService.java类

  ~~~java
  package com.Keafmd.spring5.service;
  
  import com.Keafmd.spring5.dao.UserDao;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.stereotype.Service;
  import org.springframework.transaction.annotation.Transactional;
  
  @Service
  @Transactional  // @Transactional，这个注解添加到类上面
  public class UserService {
  
      //注入dao
      @Autowired
      private UserDao userDao;
  
      //转账的方法
      public void accountMoney(){
  
          // Lucy 少100
          userDao.reduceMoney();
  
          //手动添加异常，事务回滚
          int i =100/0;
  
          //Mary多100
          userDao.addMoney();
  
      }
  
  }
  ~~~

  > 第9行添加了事务注解

  现在我们添加事务后带着异常运行测试类：

  [测试前的数据：](测试后的数据)

  ​															[![j0wV81.png](https://s1.ax1x.com/2022/07/07/j0wV81.png)](https://imgtu.com/i/j0wV81)

  [测试后的数据：](https://s1.ax1x.com/2022/07/07/j0GAZn.png)
  															[![j0GAZn.png](https://s1.ax1x.com/2022/07/07/j0GAZn.png)](https://imgtu.com/i/j0GAZn)

  > 很明显的看到测试后的数据没有变化，是因为发生了异常，进行了事务回滚，所以数据库中的数据都没有改变。

## 4. 声明式事务管理参数配置

> 在 service 类上面添加注解@Transactional，在这个注解里面可以配置事务相关参数：

[Transactional注解参数：](https://s1.ax1x.com/2022/07/07/j0ByuV.png)

​											[<img src="https://s1.ax1x.com/2022/07/07/j0ByuV.png" alt="j0ByuV.png" style="zoom:67%;" />](https://imgtu.com/i/j0ByuV)

### 4.1 propagation(事务传播行为)

> 事务传播行为：多事务方法直接进行调用，这个过程中事务 是如何进行管理的。

[事务传播行为：](https://s1.ax1x.com/2022/07/07/j0BTu6.png)

​							[<img src="https://s1.ax1x.com/2022/07/07/j0BTu6.png" alt="j0BTu6.png" style="zoom:67%;" />](https://imgtu.com/i/j0BTu6)

> 我们在add方法加了事务，update没有加，当我们的add调用update的时候，事务会怎么处理，这个过程就叫做事务的传播行为。有事务的方法调用没事务的，还有就是都有事务并且调用这些情况发生的时候事务会怎么处理，这些过程就叫做事务的传播行为。
> 事务的传播行为可以由传播属性指定。Spring 定义了7种类传播行为。

[七种传播属性：](https://s1.ax1x.com/2022/07/07/j0BO4H.png)

​								[<img src="https://s1.ax1x.com/2022/07/07/j0BO4H.png" alt="j0BO4H.png" style="zoom:67%;" />](https://imgtu.com/i/j0BO4H)

> 介绍两种最常见事务：
> REQUIRED：如果add方法本身有事务，调用update方法之后，update使用当前add方法里面事务。
> 					   如果add方法本身没有事务，调用update方法之后，创建新事务。
>
> REQUIRED_NEW：使用add方法调用update方法，如果add无论是否有事务，都创建新的事务。
>
> ==默认的是REQUIRED：@Transactional(propagation = Propagation.REQUIRED)相当于：@Transactional==

### 4.2 ioslation(事务隔离级别)

> 1. 事务有特性成为隔离性，多事务操作之间不会产生影响。不考虑隔离性产生很多问题
> 2. 有三个读问题：脏读、不可重复读、虚（幻）读

- 脏读（致命问题）：一个未提交事务读取到另一个未提交事务的数据
  [脏读：](https://s1.ax1x.com/2022/07/09/jrfZP1.png)

  ​										[<img src="https://s1.ax1x.com/2022/07/09/jrfZP1.png" alt="jrfZP1.png" style="zoom:50%;" />](https://imgtu.com/i/jrfZP1)

  > 我们可以看到事务B修改事务提交后被未提交的事务A读取

- 不可重复读（现象）：一个未提交事务读取到另一提交事务修改数据

  [不可重复读：](https://s1.ax1x.com/2022/07/09/jrfKKO.png)

  ​									[<img src="https://s1.ax1x.com/2022/07/09/jrfKKO.png" alt="jrfKKO.png" style="zoom:67%;" />](https://imgtu.com/i/jrfKKO)

- 虚读（现象）：一个未提交事务读取到另一提交事务添加数据

  > 不可重复读的重点是修改了数据，同样的条件 , 你读取过的数据 , 再次读取出来发现值不一样了。
  > 幻读的重点是新增或者删除了数据 , 第 1 次和第 2 次读出来的记录数不一样。

==解决==：通过设置事务隔离级别，解决读问题。

[事务隔离级别：](https://s1.ax1x.com/2022/07/09/jrfYGt.png)

​									[<img src="https://s1.ax1x.com/2022/07/09/jrfYGt.png" alt="jrfYGt.png" style="zoom:67%;" />](https://imgtu.com/i/jrfYGt)

> 设置隔离级别方式：@Transactional(isolation = Isolation.REPEATABLE_READ)，这种可重复读是mysql默认的设置方式。

### 4.3 其他参数

- timeout：超时时间

  > （1）事务需要在一定时间内进行提交，如果不提交进行回滚
  > （2）默认值是 -1 ，设置时间以秒单位进行计算
  >
  > 设置方式：`@Transactional(timeout = 5)`

- readOnly：是否只读

  > （1）读：查询操作，写：添加修改删除操作
  > （2）readOnly 默认值 false，表示可以查询，可以添加修改删除操作
  > （3）设置 readOnly 值是 true，设置成 true 之后，只能查询
  >
  > 设置方式：`@Transactional(readOnly = true)`

- rollbackFor：回滚

  > 设置出现哪些异常进行事务回滚
  >
  > 设置方式：`@Transactional(rollbackFor=Exception.class)`

- noRollbackFor：不回滚

  > 设置出现哪些异常不进行事务回滚
  >
  > 设置方式：`@Transactional(notRollbackFor=RunTimeException.class)`

## 5. XML声明式事务管理（不常用）

> 第一步：配置事务管理器
> 第二步：配置通知
> 第三步：配置切入点和切面

- 创建bean2.xml文件，配置事务管理器和通知及切入点切面

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:p="http://www.springframework.org/schema/p"
         xmlns:aop="http://www.springframework.org/schema/aop"
         xmlns:util="http://www.springframework.org/schema/util"
         xmlns:tx="http://www.springframework.org/schema/tx"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd
                             http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop.xsd
                             http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx.xsd
                             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
  
      <!--开启组件扫描-->
      <context:component-scan base-package="com.Keafmd"></context:component-scan>
  
      <!--引入外部的属性文件-->
      <context:property-placeholder location="classpath:jdbc.properties"/>
  
      <!--配置连接池-->
      <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
  
          <property name="driverClassName" value="${jdbc.driverClass}"></property>
          <property name="url" value="${jdbc.url}" ></property>
          <property name="username" value="${jdbc.username}" ></property>
          <property name ="password" value="${jdbc.password}" ></property>
  
      </bean>
  
      <!--创建jdbcTemplate对象-->
      <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
          <!--注入DataSource-->
          <property name="dataSource" ref="dataSource"></property>
  
      </bean>
  
      <!--创建事务管理器-->
      <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
          <!--注入数据源-->
          <property name="dataSource" ref="dataSource"></property>
  
      </bean>
  
  
      <!--2 配置通知-->
      <tx:advice id="txadvice">
          <!--配置事务参数-->
          <tx:attributes>
              <!--指定哪种规则的方法上面添加事务-->
              <tx:method name="accountMoney" propagation="REQUIRED"/>
              <!--<tx:method name="account*"/>-->
          </tx:attributes>
      </tx:advice>
      <!--3 配置切入点和切面-->
      <aop:config>
          <!--配置切入点-->
          <aop:pointcut id="pt" expression=
                        "execution(* com.Keafmd.spring5.service.UserService.*(..))"/>
          <!--配置切面-->
          <aop:advisor advice-ref="txadvice" pointcut-ref="pt"/>
      </aop:config>
  
  </beans>
  ~~~

- 把UserService的@Transactional注解注释掉，其它不变，新建个测试类：

  ~~~java
  package com.Keafmd.spring5.test;
  
  import com.Keafmd.spring5.config.TxConfig;
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.annotation.AnnotationConfigApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestAccount {
  
      @Test
      public void test2(){
          ApplicationContext context = new ClassPathXmlApplicationContext("bean2.xml");
          UserService userService = context.getBean("userService",UserService.class);
          userService.accountMoney();
      }
  
  }
  ~~~

  此时运行结果和之前一样。

## 6. 完全注解声明式事务管理

> 在注解声明式事务管理我们也是需要使用bean1.xml配置文件，我们也可以不使用配置文件，创建个配置类，和注解声明式事务管理相比其它类都不变。

- 创建TxConfig.java类，将xml文件执行内容迁移值代码中

  ~~~java
  package com.Keafmd.spring5.config;
  
  import com.alibaba.druid.pool.DruidDataSource;
  import org.springframework.context.annotation.Bean;
  import org.springframework.context.annotation.ComponentScan;
  import org.springframework.context.annotation.Configuration;
  import org.springframework.jdbc.core.JdbcTemplate;
  import org.springframework.jdbc.datasource.DataSourceTransactionManager;
  import org.springframework.transaction.annotation.EnableTransactionManagement;
  
  import javax.sql.DataSource;
  
  @Configuration //配置类
  @ComponentScan(basePackages = "com.Keafmd")  //组件扫描
  @EnableTransactionManagement  // 开启事务
  public class TxConfig {
  
      //创建数据库连接池
      @Bean
      public DruidDataSource getDruidDataSource(){
          DruidDataSource dataSource = new DruidDataSource();
          dataSource.setDriverClassName("com.mysql.jdbc.Driver");
          dataSource.setUrl("jdbc:mysql://127.0.0.1:3306/user_db?characterEncoding=utf8&useUnicode=true&useSSL=false");
          dataSource.setUsername("root");
          dataSource.setPassword("18044229");
          return dataSource;
      }
  
      //创建jdbcTemplate对象
      @Bean
      public JdbcTemplate getJdbcTemplate(DataSource dataSource){
          //到ioc容器中根据类型找到dataSource
          JdbcTemplate jdbcTemplate = new JdbcTemplate();
          //注入dataSouece
          jdbcTemplate.setDataSource(dataSource);
          return jdbcTemplate;
      }
  
      //创建事务管理器
      @Bean
      public DataSourceTransactionManager getDataSourceTransactionManager(DataSource dataSource){
          DataSourceTransactionManager transactionManager = new DataSourceTransactionManager();
          transactionManager.setDataSource(dataSource);
          return transactionManager;
      }
  
  }
  ~~~

  > 注解中使用`@Bean`创建bean实例。

- 创建测试类

  ~~~java
  package com.Keafmd.spring5.test;
  
  import com.Keafmd.spring5.config.TxConfig;
  import com.Keafmd.spring5.service.UserService;
  import org.junit.Test;
  import org.springframework.context.ApplicationContext;
  import org.springframework.context.annotation.AnnotationConfigApplicationContext;
  import org.springframework.context.support.ClassPathXmlApplicationContext;
  
  public class TestAccount {
  
  	//使用配置类
      @Test
      public void test3(){
          ApplicationContext context = new AnnotationConfigApplicationContext(TxConfig.class);
          UserService userService = context.getBean("userService",UserService.class);
          userService.accountMoney();
      }
  
  }
  ~~~

  运行结果和之前一样。

# 七. Spring5 新功能

> 整个Spring5框架的代码基于Java8, 运行时兼容JDK9，许多不建议使用的类和方法在代码库中删除。

## 1. 整合日志框架

> 1. Spring5 已经移除Log4jConfigListener, 官方建议使用Log4j2。
> 2. Spring5框架整合Log4j2十分快捷实用。

- 引入jar包
  [日志jar包：](https://s1.ax1x.com/2022/07/09/jrobrV.png)

  ​													[![jrobrV.png](https://s1.ax1x.com/2022/07/09/jrobrV.png)](https://imgtu.com/i/jrobrV)

  > 之后子啊IDEA中导入jar包

- 创建log4j2.xml文件(文件名字固定不能更改)

  ~~~xml
  <?xml version="1.0" encoding= "UTF-8"?>
  <!--日志级别以及优先级排序: 0FF >> FATAL >> ERROR >> WARN >> INFO >> DEBUC >> TRACE >> ALL-->
  <!--Configuration后面的status用于设置1og4j2自身内部的信息输出，可以不设置，当设置成trace时， 可以看到1og4j2内部各种详细输出-->
  <configuration status=" INF0">
      <!--先定义所有的appender-->
      <appenders>
          <!--输出日志信息到控制台-->
          <console name= ="Console" target="SYSTEM_OUT">
              <!--控制日志输出的格式-->
              <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss.SSS} [%t] %-5level %logger{36}-%msg%n"/>
          </console>
      </appenders>
      <!-- -然后定义logger,只有定义了1ogger并引入的appender, appender才会生效 - ->
  	<!--root:用于指定项目的根日志，如果没有单独指定Logger,则会使用root作为默认的日志输出-->
      <loggers>
          <root level="info" >
              < appender ref ref="Console"/>
          </root>
      </loggers>
  </configuration>
  ~~~

- 创建UserLog.java类，手动输出日志

  ~~~java
  import org.slf4j.Logger;
  import org.slf4j.LoggerFactory;
  public class UserLog {
      private static final Logger log = LoggerFactory.getLogger(UserLog.class);
      public static void main(String[] args) {
          log.info("hello log4j2") ;
          log.warn("hello log4j2") ;
      }
  }
  ~~~

  运行结果：

  [日志输出结果：](https://s1.ax1x.com/2022/07/09/jrHDC4.png)

  ​                                    [<img src="https://s1.ax1x.com/2022/07/09/jrHDC4.png" alt="jrHDC4.png" style="zoom: 50%;" />](https://imgtu.com/i/jrHDC4)

## 2. 支持Nullable注解和函数式注册对象

### 2.1 支持Nullable注解

> @Nullable注解可以使用在方法、属性、参数上面，分别表示可以返回空方法、参数、和属性。

- 该注解用在方法上，表示方法可以返回为空

  ~~~java
  @Nullable
  String getId(){}
  //getId方法可以返回null
  ~~~

- 注解使用在方法参数里面，方法参数可以为空。

  ~~~java
  public <T> void registerBean (@Nullable String beanName){}
  //beanName参数可以写为null
  ~~~

- 注解使用在属性上面，表示属性可以为空。

  ~~~java
  @Nullable
  private String bookName;
  // bookName属性可以为null
  ~~~

### 2.2 支持函数式风格 GenericApplicationContext

~~~java
//函数式风格创建对象，交给spring进行管理
@Test
public void tes tGenericApplicationContext() {
    //1 创建GenericApplicationContext对象
    GenericApplicationContext context = new GenericApplicat ionContext() ;
    //2调用context的方法对象注册
    context.refresh();
    context.registerBean("user1",User.class,()->new User()); 
    //3获取在spring注册的对象
    // User user = (User) context. getBean ( "com. atguigu. spring5. test. User”);
    User user = (User) context.getBean("user1");
    System.out.println(user);
}
~~~

运行结果

~~~shell
com.atguigu.spring5.test.User@7c29daf3
~~~

## 3. 整合JUnit5单元测试框架

### 3.1 JUnit5单元测试框架基本演示

1. 引入相关依赖：spring-test-5.2.6.RELEASE.jar
   [以及Junit4依赖：](https://s1.ax1x.com/2022/07/10/jsoXkD.png)
   													[![jsoXkD.png](https://s1.ax1x.com/2022/07/10/jsoXkD.png)](https://imgtu.com/i/jsoXkD)

2. 创建测试Jtest4.java类，使用注解方式完成

   ~~~java
   @RunWith(SpringJUnit4ClassRunner.class) //单元测试框架
   @ContextConfiguration ("classpath:bean1.xml") //加载配置文件
   public class JTest4 {
       @Autowired
       private UserService userService;
       @Test
       public void test1() {
           userService. accountMoney();
       }
   }
   ~~~

### 3.2 Spring5 整合JUnit5

[引入依赖jar包：](https://s1.ax1x.com/2022/07/10/jsTuXq.png)

​														[![jsTuXq.png](https://s1.ax1x.com/2022/07/10/jsTuXq.png)](https://imgtu.com/i/jsTuXq)

创建测试Jtest5.java类，使用注解完成：

~~~java
@ExtendWith (SpringExtension.class)
@ContextConfiguration("classpath:bean1.xm1")
public class JTest5 {
    @Autowired
    private UserService userService;
    //Test要换位Junit5
    @Test	
    public void test1(){
        userService.accountMoney();
    }
} 
~~~

使用复合注解替代上面两个注解完成整合

~~~java
@SpringJUnitConfig (locations ="classpath:bean1.xm1")
public class JTest5 {
    @Autowired
    private UserService userService;
    @Test
    public void test1() {
        userService. accountMoney() ;
    }
}
~~~

## 4. SpringWebFlux

