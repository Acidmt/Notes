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


## 3. 建立sql表单

- 在sqlyong中创建一个表单
  [建立sql表单：](https://s1.ax1x.com/2022/07/22/jOEdVs.png)
                         [<img src="https://s1.ax1x.com/2022/07/22/jOEdVs.png" alt="jOEdVs.png" style="zoom: 67%;" />](https://imgtu.com/i/jOEdVs)

## 4. 创建MyBatis的核心配置文件

> 习惯上命名为mybatis-config.xml，这个文件名只是建议，并非强制要求。将来整合Spring之后，这个配置文件可以省略，所以大家操作时可以直接复制、粘贴。
>
> 核心配置文件主要用于配置连接数据库的环境以及MyBatis的全局配置信息
> 核心配置文件存放的位置是src/main/resources目录下

- 在main的resources目录下新建一个`mybatis-config.xml`文件

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE configuration
          PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-config.dtd">
  <configuration>
      <!--设置连接数据库的环境--> 
      <environments default="development">
          <environment id="development">
              <transactionManager type="JDBC"/>
              <dataSource type="POOLED">
                  <property name="driver" value="com.mysql.jdbc.Driver"/>
                  <property name="url"
                            value="jdbc:mysql://localhost:3306/mybatis"/>
                  <!--注意：如果在建sql表单的时候选了字符集（如utf8），
               这里的value要改成：value="jdbc:mysql://localhost:3306/mybatis?characterEncoding=utf8"-->
                  <property name="username" value="root"/>
                  <property name="password" value="这里写你的sql root的密码"/>
              </dataSource>
          </environment>
      </environments>
      <!--引入映射文件--> 
      <mappers>
          <mapper resource="mappers/UserMapper.xml"/>
      </mappers>
  </configuration>
  ~~~

  > 文件的第22行到24行，路径是Mapper接口的映射文件路径。

## 5. 创建Mapper接口和MyBatis的映射文件

> MyBatis中的mapper接口相当于以前的dao。
> 区别在于：mapper仅仅是接口，我们不需要提供实现类。
>
> MyBatis面向接口编程的两个一致：
>
>  * 映射文件namespace和Mapper接口的全类名一致
>  * 映射文件中sql语句的id和mapper接口中的方法一致

### 5.1 实体类创建

- 创建User类pojo，对应表单t_user

  > User类中，包括private类型的对应字段、一个有参构造器、一个无参构造器、所有字段的getter和setter

  ~~~java
  public class User {
      private Integer id;
      private String username;
      private String password;
      private Integer age;
      private String gender;
      private  String email;
  
      public User() {
      }
      public User(Integer id, String username, String password, Integer age, String gender, String email) {
          this.id = id;
          this.username = username;
          this.password = password;
          this.age = age;
          this.gender = gender;
          this.email = email;
      }
  
  
      @Override
      public String toString() {
          return "User{" +
                  "id=" + id +
                  ", username='" + username + '\'' +
                  ", password='" + password + '\'' +
                  ", age=" + age +
                  ", gender='" + gender + '\'' +
                  ", email='" + email + '\'' +
                  '}';
      }
  
      public Integer getId() {
          return id;
      }
  
      public void setId(Integer id) {
          this.id = id;
      }
  
      public String getUsername() {
          return username;
      }
  
      public void setUsername(String username) {
          this.username = username;
      }
  
      public String getPassword() {
          return password;
      }
  
      public void setPassword(String password) {
          this.password = password;
      }
  
      public Integer getAge() {
          return age;
      }
  
      public void setAge(Integer age) {
          this.age = age;
      }
  
      public String getGender() {
          return gender;
      }
  
      public void setGender(String gender) {
          this.gender = gender;
      }
  
      public String getEmail() {
          return email;
      }
  
      public void setEmail(String email) {
          this.email = email;
      }
  }
  ~~~

### 5.2 创建接口文件

- 创建UserMapper.java接口

  ~~~java
  public interface UserMapper {
      /**
       * 添加用户信息
       * sql写在映射文件中
       */
      int insertUser();
  
      /**
       * 修改用户信息
       */
      void updateUser();
  
      /**
       * 删除用户信息
       */
      void deleteUser();
  
      /**
       * 根据id查询用户信息
       */
      User getUserById();
  
      /**
       * 查询所有的用户信息
       */
      List<User> getAllUser();
  }
  ~~~

### 5.3 创建接口的映射文件

> 相关概念:**ORM(Object Relationship Mapping)对象关系映射**。
>
> - 对象:Java的实体类对象
> - 关系:关系型数据库
> - 映射:二者之间的对应关系

映射对应关系：

| Java概念 |   数据库概念    |
| :------: | :-------------: |
|    类    |   对应**表**    |
|   属性   | 对应**字段/列** |
|   对象   | 对应**记录/行** |

> 1. 映射文件的命名规则:
>    表所对应的实体类的类名+Mapper.xml
>    例如：表t_user，映射的实体类为User，所对应的映射文件为UserMapper.xml (一张表一个映射文件)
>    因此一个映射文件对应一个实体类，对应一张表的操作MyBatis映射文件用于编写SQL，访问以及操作表中的数据。
>
>    MyBatis映射文件存放的位置是src/main/resources/mappers目录下
>
> 2. MyBatis中可以面向接口操作数据，要保证两个一致:
>    - ==mapper接口的全类名和映射文件的命名空间(namespace)保持一致==
>    - ==mapper接口中方法的方法名和映射文件中编写SQL的标签的id属性保持一致==

- 根据UserMapper.java在src/main/resources下，创建UserMapper.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <mapper namespace="com.atguigu.mybatis.mapper.UserMapper">
      <!--int insertUser();-->
      <insert id="insertUser">
          insert into t_user values(null, "marina", "456",23,'f',"153456@qq.com")
      </insert>
  
      <!--void updateUser();-->
      <update id="updateUser">
          update t_user set username = "RUOYI" where id = 4
      </update>
  
      <!--void deleteUser();-->
      <delete id="deleteUser">
          delete from t_user where id = 5
      </delete>
  
      <!--User getUserById();-->
      <!--
          查询功能的标签必须设置resultType或者resultMap
          resultType：设置默认的映射关系(字段名和映射名一致)
          resultMap：设置自定义的映射关系（字段名和表头不一样）
      -->
      <select id="getUserById" resultType="com.atguigu.mybatis.pojo.User">
          select * from t_user where id = 4
      </select>
  
      <!--List<User> getAllUser();-->
      <select id="getAllUser" resultType="com.atguigu.mybatis.pojo.User">
          select * from t_user
      </select>
  
  </mapper>
  ~~~

  在UserMapper.xml中，namespace为”com.atguigu.mybatis.mapper.UserMapper”，定位到这个com.atguigu.mybatis.mapper.UserMapper.java类。
  根据元素id，例如`<insert id="insertUser">`，找到UserMapper.java类中的UserMapper.insertUser()方法。

  > resultType：属性值为实体类的路径。

## 6. 通过junit进行测试

> 在src/test下建立com.atguigu.mybatis.test包，创建MyBatisTest.java测试类。

~~~java
public class MyBatisTest {
    /**
     * sqlsession默认不自动提交事务，如果需要自动提交事务，可以使用SqlSessionFactory.openSession(true);
     * @throws IOException
     */
    @Test
    public void testInsertUser() throws IOException {
        //加载核心配置文件
        InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
        //获取sqlsessionfactorybuilder
        SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();
        //获取factory
        SqlSessionFactory sqlSessionFactory = sqlSessionFactoryBuilder.build(is);
        //获取sqlsession，并设置自动提交事务
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        //获取mapper接口对象
        UserMapper mapper = sqlSession.getMapper(UserMapper.class); //代理模式

        //测试功能
        int result = mapper.insertUser();

        //执行后要提交事务（写的type是JDBC）
        //sqlSession.commit();
        System.out.println("result: " + result);
    }

    @Test
    public void testUpdateUser() throws IOException {
        InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        UserMapper mapper = sqlSession.getMapper(UserMapper.class);

        mapper.updateUser();
        System.out.println("updating...");

    }

    @Test
    public void testDeleteUser() throws IOException {
        InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        UserMapper mapper = sqlSession.getMapper(UserMapper.class);

        mapper.deleteUser();
        System.out.println("deleteUser-...");

    }

    @Test
    public void testSelectUser() throws IOException {
        InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        UserMapper mapper = sqlSession.getMapper(UserMapper.class);

        /**
         * 如果不在UserMapper.xml中配置：
         * <select id="getAllUser" resultType="com.atguigu.mybatis.pojo.User">
         * 
         * 会报错：A query was run and no Result Maps were found
         *           for the Mapped Statement 'com.atguigu.mybatis.mapper.UserMapper.getUserById'
         *          It's likely that neither a Result Type nor a Result Map was specified.
         *
         * com.atguigu.mybatis.mapper.UserMapper.getUserById： 命名空间.方法名
         *
         * 因此，要设置一个a Result Type nor a Result Map，这个type就是返回来的对应的类（要写全类名）
         *
         * 在UserMapper里进行设置
         */
        User user = mapper.getUserById();
        System.out.println(user);

        List<User> allUser = mapper.getAllUser();
        allUser.forEach(user1 -> System.out.println(user1));
    }
}
~~~

> - SqlSession：代表Java程序和数据库之间的会话。(HttpSession是Java程序和浏览器之间的会话)
> - SqlSessionFactory：是生产SqISession的工厂。
> - 工厂模式：如果创建某一个对象，使用的过程基本固定，那么我们就可以把创建这个对象的相关代码封装到一个“工厂类”中,以后都使用这个工厂类来”生产"我们需要的对象。
> - sqlsession默认不自动提交事务，如果需要自动提交事务，可以使用`SqlSessionFactory.openSession(true);`

[查询所有数据结果：](https://s1.ax1x.com/2022/07/22/jOG5vj.png)

​										[<img src="https://s1.ax1x.com/2022/07/22/jOG5vj.png" alt="jOG5vj.png" style="zoom:50%;" />](https://imgtu.com/i/jOG5vj)

## 7. 加入log4j日志功能

> 日志功能可以记录测试的sql语句、参数、结果

[日志的作用：](https://s1.ax1x.com/2022/07/22/jO86tU.png)												[<img src="https://s1.ax1x.com/2022/07/22/jO86tU.png" alt="jO86tU.png" style="zoom:50%;" />](https://imgtu.com/i/jO86tU)

- 引入依赖，在pom.xml中加入：

  ~~~xml
  <!-- log4j日志 --> <dependency>
      <groupId>log4j</groupId>
      <artifactId>log4j</artifactId>
      <version>1.2.17</version>
  </dependency>
  ~~~

- 加入log4j的配置文件
  在src/main/resources目录下，创建log4j.xml文件，加入配置信息：

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE log4j:configuration SYSTEM "log4j.dtd">
  <log4j:configuration xmlns:log4j="http://jakarta.apache.org/log4j/">
      <appender name="STDOUT" class="org.apache.log4j.ConsoleAppender">
          <param name="Encoding" value="UTF-8" />
          <layout class="org.apache.log4j.PatternLayout">
              <param name="ConversionPattern" value="%-5p %d{MM-dd HH:mm:ss,SSS}
                                                     %m  (%F:%L) \n" />
          </layout>
      </appender>
      <!--日志级别-->
      <logger name="java.sql">
          <level value="debug" />
      </logger>
      <logger name="org.apache.ibatis">
          <level value="info" />
      </logger>
      <root>
          <level value="debug" />
          <appender-ref ref="STDOUT" />
      </root>
  </log4j:configuration>
  ~~~

  > 日志的级别：
  > FATAL(致命)>ERROR(错误)>WARN(警告)>INFO(信息)>DEBUG(调试)
  > 从左到右打印的内容越来越详细，即，如果选择DEBUG级别，一定会打印出前面几种级别的信息。

# 三. 核心配置文件参数详解

> 在SSM整合期间，核心配置文件可以不写，交给Spring管理。

## 1. mybatis-config.xml中标签及属性

| 标签名                 |                             作用                             |      标签属性       |                          属性值作用                          |
| ---------------------- | :----------------------------------------------------------: | :-----------------: | :----------------------------------------------------------: |
| `<environments/>`      | 用于设置连接数据库的环境，可以有很多个`<environment/>`，但只能用其中一个作为项目的数据库连接 |       default       |                 设置多个数据库默认使用哪一个                 |
| `<transactionManager>` |                       设置事务管理方式                       | type="JDBC/MANAGED" | JDBC: 在当前环境中，执行sql时，使用的是jdbc原生的事务管理方式，需要手动的提交和回滚事务<br/> MANAGED：被管理，例如Spring |

environments标签：

~~~xml
<!--设置连接数据库的环境--> 
<environments default="development">
    <!--每一个environment都是具体连接数据库的环境-->
    <!--
        一个项目中只会用一个环境，default用于使用默认使用的环境：
        id：表示连接数据库的环境的唯一标识 不能重复

    -->
    <environment id="development">
~~~

transactionManager标签：

~~~xml
<transactionManager type="JDBC"/>
~~~

## 2. 动态写入信息

> 我们之前的链接数据库的配置文件都是写死的。如果像动态地写数据库驱动的信息，可以新建一个配置文件（jdbc.properties），文件类型为resource bundle。

- 在`jdbc.properties`文件中，以字符串形式定义各个属性。

  每个属性最好以有意义的标识作前缀，如`jdbc.xxx`。

  ~~~properties
  jdbc.driver=com.mysql.jdbc.Driver
  jdbc.url=jdbc:mysql://localhost:3306/mybatis
  jdbc.username=root
  jdbc.password=123456
  ~~~

- 在`mybatis-config.xml`文件中，添加`<properties>`元素，将资源文件引入配置文件。

  ~~~xml
  <properties resource="jdbc.properties"></properties>
  ~~~

- 在`mybatis-config.xml`文件的`<dataSource>`标签中，使用`${xxx}`格式，引入对应的属性

  ~~~xml
  <!--        dataSource：配置数据源
              属性"
                  type：设置数据源的类型
                  type="POOLED/UNPOOLED/JNDI"
                  POOLED:表示使用数据库连接池缓存数据库连接
                  UNPOOLED：表示不实用数据库连接池
                  JNDI：表示使用上下文中的数据源
  -->
  <dataSource type="POOLED">
      <!--设置连接数据库的驱动-->
      <property name="driver" value="${jdbc.driver}"/>
      <!--设置连接地址-->
      <property name="url"
                value="${jdbc.url}"/>
      <!--用户名和密码-->
      <property name="username" value="${jdbc.username}"/>
      <property name="password" value="${jdbc.password}"/>
  </dataSource>
  ~~~

## 3. 设置某个类型的别名

> UserMapper.xml中的typeAlias标签属性：
>
> - type: 设置需要设置别名的类型
> - alias: 设置某个类型的别名，如果不设置该属性，那么该类型拥有默认的类名，且不区分大小写

实例：我们可以使用`User`作为`com.atguigu.mybatis.pojo.User`的别名，可以在mapper的配置文件中直接使用User来代表这个类。

~~~xml
<typeAliases>
    <typeAlias type="com.atguigu.mybatis.pojo.User"></typeAlias>
</typeAliases>

<!--List<User> getALLUser();-->
<select id="getAlLUser" resuLtType="User">
    seLect * from t_user
</select>
~~~

也可以使用`<package>`(常用)来表示，以该包为单位，将包下所有的类型设置默认的类型别名且不区分大小写。

~~~xml
<typeAliases>
    <!--以包为单位，将包下所有的类型设置默认的类型别名且不区分大小写-->
    <package name="com.atguigu.mybatis.pojo"/>
</typeAliases>
~~~

## 4. mappers：引入映射文件

> 以包为单位引入映射文件，要求：
>
> 1. mapper接口所在的包要和映射文件所在的包一致
> 2. mapper接口要和映射文件的名字一致
>
> 如我们的mapper接口在`com.atguigu.mybatis.mapper`包下，则映射文件也要在resources文件下创建`com.atguigu.mybatis.mapper`相同的包来进行映射。

- 在resources资源文件下选择Direstory创建一个包：com.atguigu.mybatis.mapper
  [资源文件下创建包：](https://s1.ax1x.com/2022/07/23/jXPPns.png)
  								[<img src="https://s1.ax1x.com/2022/07/23/jXPPns.png" alt="jXPPns.png" style="zoom: 50%;" />](https://imgtu.com/i/jXPPns)

- 注意包名不能写为com.atguigu.mybatis.mapper创建包时要用/分隔写为：==com/atguigu/mybatis/mapper==这样才是目录，否则这整一个就只是文件夹名字而已，就不能正确映射，会报错：

  ~~~shell
  # 报错
  BindingException: Type interface com.atguigu.mybatis.mapper.UserMapper is not known to the MapperRegistry.
  ~~~

- 在mybatis.xml中配置映射文件路径

  ~~~xml
  <!--引入映射文件--> 
  <mappers>
      <!--<mapper resource="mappers/UserMapper.xml"/>-->
      <package name="com.atguigu.mybatis.mapper"/>
  </mappers>
  ~~~

## 5. mybatis.xml文件汇总

~~~xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <!--MyBatis核心配置文件，标签的顺序
        properties?,settings?,typeAliases?,typeHandlers?,
        objectFactory?,objectWrapperFactory?,reflectorFactory?,
        plugins?,environments?,databaseIdProvider?,mappers?-->


    <properties resource="jdbc.properties"></properties>

    <!--设置类型别名，大小写不敏感。
        如果不设置alias，则默认为类名（大小写不敏感）-->

    <typeAliases>
        <!--
            typeAlias: 设置某个类型的别名
            属性：
                type 设置需要设置别名的类型
                alias 设置某个类型的别名，如果不设置该属性，那么该类型拥有默认的类名，且不区分大小写
        -->
        <typeAlias type="com.atguigu.mybatis.pojo.User" alias="User"></typeAlias>

        <!--以包为单位，将包下所有的类型设置默认的类型别名且不区分大小写-->
        <package name="com.atguigu.mybatis.pojo"/>
    </typeAliases>


    <!--设置连接数据库的环境--> <environments default="development">
    <!--每一个environment都是具体连接数据库的环境-->
    <!--
        一个项目中只会用一个环境，default用于使用默认使用的环境：
        id：表示连接数据库的环境的唯一标识 不能重复

    -->
    <environment id="development">
        <!--
        transactionmanager:设置事务管理方式
        属性：
            type="JDBC/MANAGED"
            JDBC: 在当前环境中，执行sql时，使用的时jdbc原声的事务管理方式，需要手动的提交和回滚事务
            MANAGED：被管理，例如Spring
        -->
        <transactionManager type="JDBC"/>

        <!--dataSource：配置数据源
            属性"
                type：设置数据源的类型
                type=""
                POOLED:表示使用数据库连接池缓存数据库连接
                UNPOOLED：表示不实用数据库连接池
                JNDI：表示使用上下文中的数据源
-->
        <dataSource type="POOLED">
            <!--设置连接数据库的驱动-->
            <property name="driver" value="${jdbc.driver}"/>
            <!--设置连接地址-->
            <property name="url"
                      value="${jdbc.url}"/>
            <!--用户名和密码-->
            <property name="username" value="${jdbc.username}"/>
            <property name="password" value="${jdbc.password}"/>
        </dataSource>
    </environment>
    </environments>

    <!--引入映射文件--> 
    <mappers>
        <!--<mapper resource="mappers/UserMapper.xml"/>-->
        <!--BindingException: Type interface com.atguigu.mybatis.mapper.UserMapper is not known to the MapperRegistry.
            没有成功建立映射关系
            以包为单位引入映射文件，要求：
                1。 mapper接口所在的包要和映射文件所在的包一致
                2。 mapper接口要和映射文件的名字一致-->
        <!--com.atguigu.mybatis.mapper创建包时要用/分隔，这样才是目录，否则这整一个就只是文件夹名字而已-->
        <package name="com.atguigu.mybatis.mapper"/>
    </mappers>
</configuration>
~~~

# ==四. MyBatis获取参数值==

> 动态获取数据执行sql语句

## 1. 设置mybatis-config.xml配置文件模版

- 通过idea设置添加模板
  [配置mybatis模板：](https://s1.ax1x.com/2022/07/23/jXkWKe.png)

  ​						[<img src="https://s1.ax1x.com/2022/07/23/jXkWKe.png" alt="jXkWKe.png" style="zoom: 33%;" />](https://imgtu.com/i/jXkWKe)

- 配置模板内容

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE configuration
          PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-config.dtd">
  <configuration>
  
      <properties resource="jdbc.properties"></properties>
  
      <typeAliases>
          <package name=""></package>
      </typeAliases>
  
      <!--设置连接数据库的环境-->
      <environments default="development">
          <environment id="development">
              <transactionManager type="JDBC"/>
              <dataSource type="POOLED">
                  <property name="driver" value="${jdbc.driver}"/>
                  <property name="url" value="${jdbc.url}"/>
                  <property name="username" value="${jdbc.username}"/>
                  <property name="password" value="${jdbc.password}"/>
              </dataSource>
          </environment>
      </environments>
      <!--引入映射文件-->
      <mappers>
          <package name=""/>
      </mappers>
  </configuration>
  ~~~

- 配置Mapper.xml文件模板内容

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <mapper namespace="">
  
  </mapper>
  ~~~

- 创建SqlSessionUtils.java文件封装获取sqlsession对象

  ~~~java
  public static sqlSession getsqlSession(){
      sqlSession sqlSession = null;
      try {
          InputStream is = Resources.getResourceAsstream("mybatis-config.xml");
          SqlSessionFactory sqlSessionFactory = new sqlSessionFactoryBuilder().build(is);
          sqlSession = sqlSessionFactory.openSession(true);
      } catch (IOException e) {
          e.printStackTrace();
          return sqlSession;
      }
  }
  ~~~

- 创建Test.java获取sqlsession对象进行测试

  ~~~java
  public class ParameterMapperTest {
      @Test
      public void testGetAllUser(){
          sqlSession sqlSession = sqlSessionJtils.getSqlSession();
          ParameterMapper mapper = sqlSession.getMapper(ParameterMapper.class);
          List<User> list = mapper.getAlluser();
          list.forEach(user -> system.out.println(user));
      }
  }
  ~~~

  运行结果：

  ~~~shell
  User{id=3, username='admin', password='123456', age=23, sex='男',email='12345@qq.com'}
  User{id=4, username='张三',password='123456', age=23, sex='男',email='12345@qq.com'}
  ~~~

## 2. 获取参数值

### 2.1 JDBC原生的获取参数值的方式

> 有两种：
>
> - 字符串拼接
> - 占位符拼接

~~~java
@Test
public void testJDBC() throws SQLException, ClassNotFoundException {
    String username = "lisi";
    Class.forName("");
    Connection connection = DriverManager.getConnection("", "", "");
    // 1. 字符串拼接 ->获得预编译对象 -> sql注入问题
    PreparedStatement preparedStatement = connection.prepareStatement(
        "select * from t_user where username = '" + username + "'");

    // 2. ?占位符(较为常用)
    PreparedStatement ps2 = connection.prepareStatement("select * from t_user where username = ?");
    // 给第一个?占位符赋值
    ps2.setString(1, username);
}
~~~

### ==2.2 MyBatis获取参数值的两种方式==

> MyBatis获取参数值的两种方式:${}和#{}
>
> - ${}的本质就是字符串拼接(常用)
> - \#{}的本质就是占位符赋值
>
> ${}使用字符串拼接的方式拼接sql，若为字符串类型或日期类型的字段进行赋值时，需要手动加单引号;
> #{}使用占位符赋值的方式拼接sql，此时为字符串类型或日期类型的字段进行赋值时，可以自动添加单引号（尽量使用这一种）。

## 3. MyBatis获取参数值的五种情况

### 3.1 单个字面量类型的参数

> 若mapper接口中的方法参数为单个的字面量类型，此时可以使用`${}`和`#{}`以任意的名称获取参数的值，注意`${}`需要手动加单引号。

- 创建接口类ParameterMapper.java

  ~~~java
  public interface ParameterMapper {
      /**
       * 单个的字面量类型:
       * 根据用户名查询用户信息
       */
      User getUserByUserName(String username);
  }
  ~~~

- 对应在ParameterMapper.xml中配置。

  配置一：

  ~~~xml
  <!--User getUserByUserName(String username);-->
  <!--使用#{}，里面内容可以随便写，都是传进来的username的值-->
  <select id="getUserByUserName" resultType="User">
      select * from t_user where username = #{username}
  </select>
  ~~~

  配置二：

  ~~~xml
  <!--User getUserByUserName(String username);-->
  <select id="getUserByUserName" resultType="User">
      <!-- 
         select * from t_user where username = ${username}
            如果使用这种方式，得到的sql语句是：
            Preparing: select * from t_user where username = RUOYI
            而其中username的值'RUOYI'没有单引号，语句不正确，会报错。
            因此要手动添加单引号
         -->
      select * from t_user where username = '${username}'
  </select>
  ~~~

- 创建测试类ParameterMapperTest.java

  ~~~java
  /**
       * MyBatis获取参数值的各种情况：
       * 情况1： mapper接口方法的参数为单个字面量的参数
       * 可以通过${} #{}以任意的字符串获得参数值，但需要注意${}的单引号问题
       */
  @Test
  public void testgetUserByUserName(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      ParameterMapper mapper = sqlSession.getMapper(ParameterMapper.class);
      User user = mapper.getUserByUserName("admin");
      System.out.println(user);
  }
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/07/23/jXdKHJ.png)
                            [<img src="https://s1.ax1x.com/2022/07/23/jXdKHJ.png" alt="jXdKHJ.png" style="zoom: 50%;" />](https://imgtu.com/i/jXdKHJ)

### 3.2 多个字面量类型的参数

> 若mapper接口中的方法参数为多个时：
>
> 此时MyBatis会自动将这些参数放在一个map集合中，以arg0,arg1…为键，以参数为值；以 param1,param2…为键，以参数为值；
>
> 因此只需要通过`${}`和`#{}`访问map集合的键就可以获取相对应的值，注意${}需要手动加单引号。

- ParameterMapper.java接口

  ~~~java
  public interface ParameterMapper {
      /**
       * 验证登录
       */
      User checkLogin(String username, String password);
  }
  ~~~

- 对应在ParameterMapper.xml中配置

  ~~~xml
  <!--    User checkLogin(String username, String password);-->
  <select id="checkLogin" resultType="User">
      <!--
          写：select * from t_user where username = #{username} and password = #{password}
          会报错：Parameter 'username' not found. Available parameters are [arg1, arg0, param1, param2]
          因为sql语句没有解析成功以map集合形式存储，arg0->param1, arg1->param2，这时直接用键arg访问就好了，用param		访问也行。以下两种方式选一个：-->
      select * from t_user where username = #{arg0} and password = #{arg1}
      select * from t_user where username = '${param1}' and password = '${param2}'
  </select>
  ~~~

- 创建ParameterMapperTest.java类

  ~~~java
  /**
       * 情况2：mapper接口方法的参数为多个时
       * 此时MyBatis会将这些参数放在一个map集合中，以两种方式进行存储
       * a》以arg0，arg1..为键，参数为值
       * b》以param0，param1..为键，参数位置
       * 因此只需要通过#{}和${}以键的方式访问值即可，但需要注意${}的单引号问题
       */
  @Test
  public void testCheckLogin(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      ParameterMapper mapper = sqlSession.getMapper(ParameterMapper.class);
      User user = mapper.checkLogin("admin","123456");
      System.out.println(user);
  }
  ~~~

  运行结果：

  ~~~shell
  User{id=3,username='admin',password= '123456',age=23,sex='男',email='12345@qq.com'}
  ~~~

### 3.3 map集合类型的参数

> 若mapper接口中的方法需要的参数为多个时，此时可以手动创建map集合，将这些数据放在map中只需要通过`${}和#{}`访问map集合的键就可以获取相对应的值，注意${}需要手动加单引号。

- 创建ParameterMapper.java接口

  ~~~java
  public interface ParameterMapper {
      /**
       * 验证登录
       */
      User checkLoginByMap(Map<String, Object> map);
  }
  ~~~

- 对应在ParameterMapper.xml中配置

  ~~~xml
  <!--User checkLoginByMap(Map<String, Object> map);-->
  <select id="checkLoginByMap" resultType="User">
      select * from t_user where username = #{username} and password = #{password}
  </select>
  ~~~

- 测试类ParameterMapperTest.java

  ~~~java
  /**
       * 情况3：若mapper接口方法的参数有多个时，可以手动将这些参数放在一个map中存储
       * 只需要通过#{} ${}以键的方式访问值即可，但是需要注意${}的单引号问题
       */
  @Test
  public void testCheckLoginByMap(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      ParameterMapper mapper = sqlSession.getMapper(ParameterMapper.class);
  
      Map<String, Object> map = new HashMap<>();
      map.put("username","admin");
      map.put("password","123456");
  
      User user = mapper.checkLoginByMap(map);
      System.out.println(user);
  }
  ~~~

  运行结果：

  ~~~shell
  User{id=3,username='admin',password= '123456',age=23,sex='男',email='12345@qq.com'}
  ~~~

### 3.4 实体类类型的参数

> 若mapper接口中的方法参数为实体类对象时 此时可以使用`${}和#{}`，通过访问实体类对象中的==属性名==获取属性值，注意${}需要手动加单引号

- ParameterMapper.java接口

  ~~~java
  public interface ParameterMapper {
      /**
       * 添加用户信息
       */
      int insertUser(User user);
  }
  ~~~

- 对应在ParameterMapper.xml中配置

  ~~~xml
  <!--int insertUser(User user);-->
  <!--找到相对应的get方法，如username->找getUsername()，看get/set方法-->
  <insert id="insertUser">
      insert into t_user values(null, #{username}, #{password}, #{age}, #{gender}, #{email})
  </insert>
  ~~~

- 创建测试类ParameterMapperTest.java

  ~~~java
  /**
       * 情况4：mapper接口方法的参数是实体类类型的参数（web从control层传过来的）
       * 只需要通过#{} ${}以属性的方式访问属性值即可，但是需要注意${}的单引号问题
       */
  @Test
  public void testInsertUser(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      ParameterMapper mapper = sqlSession.getMapper(ParameterMapper.class);
  
      User user = new User(null, "lisi", "123456", 18, "man", "123@qq.com");
      mapper.insertUser(user);
  }
  ~~~

  
