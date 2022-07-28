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

### ==3.4 实体类类型的参数==

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


### ==3.5 使用@Param标识参数==

> 是第二三种情况的优化。可以通过@Param注解标识mapper接口中的方法参数
>
> 此时，会将这些参数放在map集合中，以`@Param`注解的value属性值为键，以参数为值;；
>
> 只需要通过`${}和#{}`访问map集合的键就可以获取相对应的值， 注意${}需要手动加单引号

- ParameterMapper.java接口

  ~~~java
  public interface ParameterMapper {
      /**
       * 验证登录 （使用@Param）
       */
      User checkLoginByParam(@Param("username") String username, @Param("password") String password);
  }
  ~~~

- 对应在ParameterMapper.xml中配置

  ~~~xml
  <!--    以@Param的值为键，参数为值; 或以"param1"/"param2"为键，参数为值-->
  <!--    User checkLoginByParam(@Param("username") String username, @Param("password") String password);-->
  <select id="checkLoginByParam" resultType="User">
      select * from t_user where username = #{username} and password = #{password}
  </select>
  ~~~

- 编写测试类

  ~~~java
  /**
       * 情况5：使用@Param注解来命名参数
       * 此时MyBatis会将这些参数放在一个map集合中，以两种方式进行存储
       * a》以@Param的值为键，参数为值; @Param(value = "xxx")
       * b》以param0，param1...为键，参数为值
       */
  @Test
  public void testCheckLoginByParam(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      ParameterMapper mapper = sqlSession.getMapper(ParameterMapper.class);
      User user = mapper.checkLoginByParam("admin","123456");
      System.out.println(user);
  }
  ~~~

  运行结果：

  ~~~shell
  User{id=3,username='admin',password= '123456',age=23,sex='男',email='12345@qq.com'}
  ~~~

## 4. @Param源码分析

> sql语句的唯一标识 command name00

分析代码
目的：验证@Param存储参数的两种方式

~~~java
/**
     * 情况5：使用@Param注解来命名参数
     * 此时MyBatis会将这些参数放在一个map集合中，以两种方式进行存储
     * a》以@Param的值为键，参数为值; @Param(value = "xxx")
     * b》以param1，param2...为键，参数为值
     */
@Test
public void testCheckLoginByParam(){
    SqlSession sqlSession = SqlSessionUtils.getSqlSession();
    ParameterMapper mapper = sqlSession.getMapper(ParameterMapper.class);
    User user = mapper.checkLoginByParam("RUOYI","123456");
    System.out.println(user);
}
~~~

- 打断点，进入debug模式
  [断点位置：](https://s1.ax1x.com/2022/07/25/jvsA3j.png)

  ​					[<img src="https://s1.ax1x.com/2022/07/25/jvsA3j.png" alt="jvsA3j.png" style="zoom: 50%;" />](https://imgtu.com/i/jvsA3j)		

- 选择step into进行调试
  [调试过程：](https://s1.ax1x.com/2022/07/25/jvs38J.png)      ![jvs38J.png](https://s1.ax1x.com/2022/07/25/jvs38J.png)](https://imgtu.com/i/jvs38J)
- Mapper底层使用代理模式创建，我们按step into进入缓存cachedInvoker的invoke()方法
  [方法：](https://imgtu.com/i/jvsRVf)					[![jvsRVf.png](https://s1.ax1x.com/2022/07/25/jvsRVf.png)](https://imgtu.com/i/jvsRVf)									

- 进入了invoke()，再进一步进入了mapperMethod的execute()方法（step into）
  [进入mapperMethod的execute()方法：](https://s1.ax1x.com/2022/07/25/jvs5GQ.png)         [![jvs5GQ.png](https://s1.ax1x.com/2022/07/25/jvs5GQ.png)](https://imgtu.com/i/jvs5GQ)

- execute()方法中包含一个switch语句，分别对应增删改查等关键字对应的处理流程。
  [execute()方法：](https://s1.ax1x.com/2022/07/25/jvsoxs.png) [![jvsoxs.png](https://s1.ax1x.com/2022/07/25/jvsoxs.png)](https://imgtu.com/i/jvsoxs)

- 点击step over跳进switch语句内部，光标放在command上，点击加号，查看command内容。name为该sql语句的唯一标识，type为对应操作，即SELECT。
  [switch语句内部：](https://s1.ax1x.com/2022/07/25/jvsHrq.png)   [![jvsHrq.png](https://s1.ax1x.com/2022/07/25/jvsHrq.png)](https://imgtu.com/i/jvsHrq)

  [完整代码：](https://s1.ax1x.com/2022/07/25/jvsXIU.png)        [<img src="https://s1.ax1x.com/2022/07/25/jvsXIU.png" alt="jvsXIU.png" style="zoom:50%;" />](https://imgtu.com/i/jvsXIU)

- 再点击step into，发现convertArgsToSqlCommandParam()方法是由paramNameResolver参数名称解析器中的getNamedParams()获取命名参数方法解析的，进一步step into进这个方法。
  [convertArgsToSqlCommandParam()方法：](https://s1.ax1x.com/2022/07/25/jvySz9.png)          [<img src="https://s1.ax1x.com/2022/07/25/jvySz9.png" alt="jvySz9.png" style="zoom:50%;" />](https://imgtu.com/i/jvySz9)

- 进入getNamedParams()方法，查看names，发现names是一个map集合，包含了传进来的"username"、"password" 参数。
  [getNamedParams()方法：](https://s1.ax1x.com/2022/07/25/jvyPqx.png)
    [<img src="https://s1.ax1x.com/2022/07/25/jvyPqx.png" alt="jvyPqx.png" style="zoom:50%;" />](https://imgtu.com/i/jvyPqx)

- 由结果再翻上去看@Param的解析过程。
  [@Param的解析过程：](https://s1.ax1x.com/2022/07/25/jvyViD.png)         [<img src="https://s1.ax1x.com/2022/07/25/jvyViD.png" alt="jvyViD.png" style="zoom:50%;" />](https://imgtu.com/i/jvyViD)

- 回到getNamedParams()方法，继续step over
  [getNamedParams()方法：](https://s1.ax1x.com/2022/07/25/jvy1df.png)                [<img src="https://s1.ax1x.com/2022/07/25/jvy1df.png" alt="jvy1df.png" style="zoom:50%;" />](https://imgtu.com/i/jvy1df)

- 两次循环entrySet后，发现param集合中得到两种映射

  - 以@Param的value作为key，参数值为value

  - 以param1, param2...作为key，参数值为value

    [结果：](https://s1.ax1x.com/2022/07/25/jvyhex.png)
                                   [<img src="https://s1.ax1x.com/2022/07/25/jvyhex.png" alt="jvyhex.png" style="zoom:50%;" />](https://imgtu.com/i/jvyhex)       

  至此，@Param源码分析完毕，印证结论：可以使用#{param1}和#{username}两种方式获得参数值。

# 五. MyBatis的查询功能

## 1. 查询一个实体类对象和多个数据

> MyBatis查询功能：
>
> 1. 若查询出的数据只有一条，可以通过实体类对象、list集合、与map集合来接收
> 2. 若查询处的数据有多条，可以用ist集合、与map集合来接收。一定不能通过实体类对象来接收，此时会抛出TooManyResultsException

- SelectMapper.java接口

  ~~~java
  public interface SelectMapper {
      /**
       * 根据id查询用户信息
       */
      User getUserById(@Param("id") Integer id);
      //查询多条数据
      List<User> getAllUser();
  }
  ~~~

- 配置SelectMapper.xml文件

  ~~~xml
  <!--User getUserById(@Param("id") Integer id);-->
  <select id="getUserById" resultType="User">
      select * from t_user where id = #{id}
  </select>
  
  <!--List<User> getAllUser();查询多条数据-->
  <select id="getAlluser" resultType= "User">
      select * from t_ user
  </select>
  ~~~

- 编写测试类

  ~~~java
  /**
       * MyBatis的各种查询功能：
       * 1。 若查询出的数据只有一条，可以通过实体类对象 /list集合/map集合来接收
       * 2。 若查询处的数据有多条，一定不能通过实体类对象来接收，此时会抛出TooManyResultsException
       */
  @Test
  public void testGetUserById(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      SelectMapper mapper = sqlSession.getMapper(SelectMapper.class);
      User userById = mapper.getUserById(4);
      System.out.println(userById);
  }
  
  //查询多条数据
  @Test
  public void testGetAllUser(){
      SqlSession sqlSession = sqlSessionUtils.getSqlSession();
      SelectMapper mapper = sqlSession.getMapper(SelectMapper.class);
      System.out.println(mapper.getAllUser()) ;
  }
  ~~~

  运行结果

  ~~~shell
  User{id=3,username= 'admin',password= '123456',age=23,sex='男',email= '12345@qq.com'}
  ~~~

  多条数据运行结果：

  ~~~shell
  [User{id=3,username= 'admin',password= '123456',age=23,sex='男',email= '12345@qq.com'},
  User{id=4,username= 'lisi',password= '123456',age=18,sex='男',email= '122325@qq.com'}]
  ~~~

## 2. 查询单个数据

> xml中sql标签的resultType属性值有别名。
>
> 如：
>
> java. Lang. Integer-->int, integer
> int-->_ int,_ integer
> Map- - >map
> String-->string

[完整别名：](https://s1.ax1x.com/2022/07/25/jvfFcF.png)

​									[<img src="https://s1.ax1x.com/2022/07/25/jvfFcF.png" alt="jvfFcF.png" style="zoom: 67%;" />](https://imgtu.com/i/jvfFcF)

[别名：](https://s1.ax1x.com/2022/07/25/jvfQ1O.png)

​									[<img src="https://s1.ax1x.com/2022/07/25/jvfQ1O.png" alt="jvfQ1O.png" style="zoom: 67%;" />](https://imgtu.com/i/jvfQ1O)

- SelectMapper.java接口

  ~~~java
  public interface SelectMapper {
      /**
       * 查询用户信息的总记录数
       */
      Integer getCount();
  }
  ~~~

- 配置文件

  ~~~xml
  <!--Integer getCount();-->
  <!--integer写大小写都可以，写 Integer/integer/_int/_integer  都可以，都是java.lang.Integer的别名-->
  <select id="getCount" resultType="java.lang.Integer">
      select count(*) from t_user
  </select>
  ~~~

- 编写测试类

  ~~~java
  /**
       * 获取记录数
       *
       * MyBatis中设置了默认的类型别名
       * Java.lang.Integer -> int, integer
       * int -> _int, _integer
       * Map -> map
       * List -> list
       */
  @Test
  public void testGetCount(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      SelectMapper mapper = sqlSession.getMapper(SelectMapper.class);
      System.out.println(mapper.getCount());
  }
  ~~~

  运行结果：

  ~~~shell
  2
  # 数据库有两条数据
  ~~~

## 3. 查询数据为map集合

> 如果我们查询的表没有实体类对象，就把它映射成map集合。例如把它传到网页端，就映射成json对象，所以转成map很常用。
>
> 要注意map集合是以表的字段为键。

- SelectMapper.java接口

  ~~~java
  public interface SelectMapper {
      /**
       * 根据id查询用户信息为一个map集合
       */
      Map<String, Object> getUserByIdToMap(Integer id);
  }
  ~~~

- 配置xml文件

  ~~~xml
  <!--Map<String, Object> getUserByIdToMap(Integer id);-->
  <select id="getUserByIdToMap" resultType="map">
      select * from t_user where id = #{id}
  </select>
  ~~~

- 编写测试类

  ~~~java
  /**
       * 如果没有实体类对象，就把它映射成map集合
       * 从数据库中查询数据，将其映射为map集合
       * 例如把它传到网页端，就映射成json对象，所以转成map很常用
       *
       * 以字段为键
       */
  @Test
  public void testgetUserByIdToMap(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      SelectMapper mapper = sqlSession.getMapper(SelectMapper.class);
      System.out.println(mapper.getUserByIdToMap(4));
  }
  ~~~

  运行结果：

  ~~~shell
  {password=123456, sex=男,id=3,age=23,email=12345@qq.com,username=admin}
  ~~~

## 4. 查询多条数据为map集合

> 因为查询的数据有多个，而map集合一次只能接收一个。所以这里有两种解决方法：
>
> 1. 创建一个Map类型的List集合。
> 2. 使用@MapKey注解，此时就可以将每条数据转换的map集合作为值，以某个字段作为键(一般选择不重复的字段。如：id)

- SelectMapper接口

  ~~~java
  public interface SelectMapper {
      /**
       * 查询所有用户信息为map集合，每一条记录是一个map
       */
      //方式一：
      List<Map<String, Object>> getAllUserToMap();
  
      //方式二：
      @MapKey("id")
      Map<String, Object> getAllUserToMap();
  }
  ~~~

- 编写xml配置文件

  ~~~xml
  <!--Map<String, Object> getAllUserToMap();-->
  <select id="getAllUserToMap" resultType="map">
      select * from t_user
  </select>
  ~~~

- 编写测试类

  ~~~java
  @Test
  public void testGetAllUserToMap(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      SelectMapper mapper = sqlSession.getMapper(SelectMapper.class);
      system.out.println(mapper.getAlluserToMap());
  }
  ~~~

  List方式运行结果：

  ~~~shell
  [{id=3,username= 'admin',password= '123456',age=23,sex='男',email= '12345@qq.com'},
  {id=4,username= 'lisi',password= '123456',age=18,sex='男',email= '122325@qq.com'}]
  ~~~

  注解方式运行结果：

  ~~~shell
  {
  3={id=3,username= 'admin',password= '123456',age=23,sex='男',email= '12345@qq.com'},
  4={id=4,username= 'lisi',password= '123456',age=18,sex='男',email= '122325@qq.com'}
  }
  ~~~

# 六. 特殊SQL的执行

## 1. 模糊查询

> 实现有三种方式：
>
> 1. 通过`${}`方式
> 2. 通过`('%',#{username},'%')`这种拼接方式
> 3. 第三种是推荐方法：`"%"#{username}"%"`

- SQLMapper类

  ~~~java
  public interface SQLMapper {
      /**
       * 根据用户名模糊查询用户信息
       */
      List<User> getUserByLike(@Param("username") String username);
  }
  ~~~

- SQLMapper.xml

  ~~~xml
  <!--List<User> getUserByLike(@Param("username") String username);-->
  <!--使用#{}，因为包括在单引号里，会被认为是字符串的一部分:
  			select * from t_user where username like '%#{username}%'-->
  <!--三种方式-->
  <select id="getUserByLike" resultType="User">
      <!--第一种 select * from t_user where username like '%${username}%'
      <!--第二种 select * from t_user where username like concat('%', #{username}, '%')-->
      <!--第三种 推荐使用-->
      select * from t_user where username like "%"#{username}"%"
  </select>
  ~~~

- 编写测试类

  ~~~java
  @Test
  public void testGetUserByLike(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      SQLMapper mapper = sqlSession.getMapper(SQLMapper.class);
      List<User> user = mapper.getUserByLike("RUOYI");
      System.out.println(user);
  }
  ~~~

  运行结果：

  ~~~shell
  [User{id=3, username='admin' , password= '123456', age=23, sex='男', email='12345@qq.com'}]
  ~~~

## 2. 批量删除

> 不能使用#{}，因为他会自动添加单引号，变成delete from t_user where id in ('9，10，11')

- SQLMapper.java类

  ~~~java
  public interface SQLMapper {
      /**
       * 批量删除
       */
      int deleteMore(String ids);
  }
  ~~~

- SQLMapper.xml

  ~~~xml
  <!--int deleteMore(String ids);-->
  <!--不能使用#{}，因为他会自动添加单引号，变成delete from t_user where id in ('9，10，11')-->
  <delete id="deleteMore">
      delete from t_user where id in (${ids})
  </delete>
  ~~~

- 测试类

  ~~~java
  @Test
  public void testDeleteMore(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      SQLMapper mapper = sqlSession.getMapper(SQLMapper.class);
      int result = mapper.deleteMore("12, 13");
      System.out.println(result);
  }
  ~~~

  运行结果：

  ~~~shell
  1
  # 表明成功删除了一条数据
  ~~~

## 3. 动态设置表名

> 获取表名参数时候只能使用`${}`。因为表名不能有引号

- SQLMapper.java类

  ~~~java
  public interface SQLMapper {
      /**
       * 查询指定表中的数据
       */
      List<User> getUserByTableName(String tableName);
  }
  ~~~

- SQLMapper.xml

  ~~~xml
  <!--List<User> getUserByTableName(String tableName);-->
  <select id="getUserByTableName" resultType="User">
      select * from ${tableName}
  </select>
  ~~~

- 测试类

  ~~~java
  @Test
  public void testGetUserByTableName(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      SQLMapper mapper = sqlSession.getMapper(SQLMapper.class);
      List<User> t_user = mapper.getUserByTableName("t_user");
      System.out.println(t_user);
  }
  ~~~

  运行结果：

  ~~~shell
  [User{id=3,username= 'admin',password= '123456',age=23,sex='男',email= '12345@qq.com'},
  User{id=4,username= 'lisi',password= '123456',age=18,sex='男',email= '122325@qq.com'}]
  ~~~

## 4. 添加功能获取自增主键

> 使用场景：在给学生分配班级时，获取班级id
>
> 需要用到sql标签两个属性：
>
> 1. useGeneratedKeys：设置当前标签中的sql使用了自增的主键 (id)
> 2. keyProperty：将自增的主键的值 赋值给 传输到映射文件中的参数的某个属性（user.id）

- SQLMapper.java类

  ~~~java
  public interface SQLMapper {
      /**
       * 添加用户
       */
      void insetUser(User user);
  }
  ~~~

- SQLMapper.xml

  ~~~xml
  <!--void insetUser(User user);-->
  <!--方法的返回值是固定的
          useGeneratedKeys    设置当前标签中的sql使用了自增的主键 (id)
          keyProperty         将自增的主键的值 赋值给 传输到映射文件中的参数的某个属性（user.id）
  -->
  <insert id="insetUser" useGeneratedKeys="true" keyProperty="id">
      insert into t_user values(null, #{username}, #{password},#{age},#{gender},#{email})
  </insert>
  ~~~

- 编写测试类

  ~~~java
  @Test
  public void testInsetUser(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      SQLMapper mapper = sqlSession.getMapper(SQLMapper.class);
      mapper.insetUser(new User(null, "wangwu","123",18,"man","123@163.com"));
  }
  ~~~


 # 七. 自定义映射resultMap

> 字段名与属性名不一致，或者处理多对一一对多的关系。

## 1. 准备工作

- 新建一个`t_emp`表，用来存放用户信息。

  [创建t_emp表：](https://s1.ax1x.com/2022/07/26/jxzLQg.png)
                                  [<img src="https://s1.ax1x.com/2022/07/26/jxzLQg.png" alt="jxzLQg.png" style="zoom:67%;" />](https://imgtu.com/i/jxzLQg)

  > 最后的did字段与`t_dept`表绑定

- 创建一个`t_dept`表，模拟部门数据库。
  [创建t_dept表：](https://s1.ax1x.com/2022/07/26/jxzwL9.png)
                                  [<img src="https://s1.ax1x.com/2022/07/26/jxzwL9.png" alt="jxzwL9.png" style="zoom: 67%;" />](https://imgtu.com/i/jxzwL9)

- 插入一些测试数据

  [t_emp测试数据：](https://s1.ax1x.com/2022/07/26/jzSiSU.png)
                                   [<img src="https://s1.ax1x.com/2022/07/26/jzSiSU.png" alt="jzSiSU.png" style="zoom: 80%;" />](https://imgtu.com/i/jzSiSU)

  [t_dept测试数据：](https://s1.ax1x.com/2022/07/26/jzSVm9.png)
                                    [<img src="https://s1.ax1x.com/2022/07/26/jzSVm9.png" alt="jzSVm9.png" style="zoom:80%;" />](https://imgtu.com/i/jzSVm9)

  > 上面添加了三个部门。`t_emp`表中的数据用`did`字段与`t_dept`表绑定。

## 2. 建立mapper、pojo、映射文件

- 在pojo包下创建数据库映射类Emp.java映射`t_emp`表

  ~~~java
  package com.atguigu.mybatis.pojo;
  
  /**
   * @author Chen Ruoyi
   * @date 2022/3/1 9:07 PM
   */
  public class Emp {
      private Integer eid;
      private String empName;
      private Integer age;
      private String sex;
      private String email;
  	
      public Emp() {
      }
  
      public Emp(Integer eid, String empName, Integer age, String sex, String email) {
          this.eid = eid;
          this.empName = empName;
          this.age = age;
          this.sex = sex;
          this.email = email;
      }
  
      @Override
      public String toString() {
          return "Emp{" +
              "eid=" + eid +
              ", empName='" + empName + '\'' +
              ", age=" + age +
              ", sex='" + sex + '\'' +
              ", email='" + email + '\'' +
              '}';
      }
  
      public Integer getEid() {
          return eid;
      }
  
      public void setEid(Integer eid) {
          this.eid = eid;
      }
  
      public String getEmpName() {
          return empName;
      }
  
      public void setEmpName(String empName) {
          this.empName = empName;
      }
  
      public Integer getAge() {
          return age;
      }
  
      public void setAge(Integer age) {
          this.age = age;
      }
  
      public String getSex() {
          return sex;
      }
  
      public void setSex(String sex) {
          this.sex = sex;
      }
  
      public String getEmail() {
          return email;
      }
  
      public void setEmail(String email) {
          this.email = email;
      }
  }
  ~~~

- 接着在pojo包下创建数据库映射类Dept.java映射`t_dept`表

  ~~~java
  package com.atguigu.mybatis.pojo;
  
  public class Dept {
      private Integer did;
      private String deptName;
  
      @Override
      public String toString() {
          return "Dept{" +
              "did=" + did +
              ", deptName='" + deptName + '\'' +
              '}';
      }
  
      public Integer getDid() {
          return did;
      }
  
      public void setDid(Integer did) {
          this.did = did;
      }
  
      public String getDeptName() {
          return deptName;
      }
  
      public void setDeptName(String deptName) {
          this.deptName = deptName;
      }
  
      public Dept() {
      }
  
      public Dept(Integer did, String deptName) {
          this.did = did;
          this.deptName = deptName;
      }
  }
  ~~~

- 创建EmpMapper.java接口和DeptMapper.java接口

  ~~~java
  public interface EmpMapper {
  }
  ~~~

  ~~~java
  public interface DeptMapper {
  }
  ~~~

- 创建接口的xml文件
  DeptMapper.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <mapper namespace="com.atguigu.mybatis.mapper.DeptMapper">
  
  </mapper>
  ~~~

  EmpMapper.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <mapper namespace="com.atguigu.mybatis.mapper.EmpMapper">
  
  </mapper>
  ~~~

[项目结构：](https://s1.ax1x.com/2022/07/26/jzCxjU.png)

​      									 	[<img src="https://s1.ax1x.com/2022/07/26/jzCxjU.png" alt="jzCxjU.png" style="zoom:50%;" />](https://imgtu.com/i/jzCxjU)		

## 3. 映射实体类属性与字段不对应情况

>  我们的Emp.java中的实体类名`empName`和数据库中的`emp_Name`字段不一致。此时通过EmpMapper.xml接口查询数据库不会报错

- EmpMapper.java

  ~~~java
  public interface EmpMapper {
  	//查询t_emp表数据
  	List<Emp> getAllEmp();
      
  }
  ~~~

- EmpMapper.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <mapper namespace="com.atguigu.mybatis.mapper.EmpMapper">
      <!--List<Emp> getAllEmp();-->
      <select id="getAllEmp" resultType="Emp">
          select * from t_emp
      </select>
  </mapper>
  ~~~

- 测试类

  ~~~java
  @Test
  public void testGetAllEmp(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      EmpMapper mapper = sqlSession.getMapper(EmpMapper.class);
      List<Emp> list = mapper.getAllEmp();
      list.forEach(emp->System.out.println(emp));
  }
  ~~~

  运行结果：

  ~~~shell
  Emp{eid=1, empName= 'null', age=23, sex='男', email=' 123@qq.com'}
  Emp{eid=2, empName=' null', age=32, sex='女', email='123@qq. com'}
  Emp{eid=3, empName= 'null', age=12, sex='男', email='123@qq.com' }
  Emp{eid=4, empName='null', age=34, sex='女', email='123@qq.com'}
  Emp{eid=5, empName=' null', age=28, sex='男', email='123@qq. com'}
  
  ~~~

  > 我们可以看到当映射字段不对应时，会出现实体类属性为`null`情况。

## 4. resultMap处理字段和属性的映射关系

> 我们可以通过以下两种方式处理字段名和实体类中的属性的映射关系：
>
> 1. 可以通过为字段起别名的方式，保证和实体类中的属性名保持一致
> 2. 可以在MyBatis的核心配置文件中设置一个全局配置信息mapUnderscoreToCamelCase，可以在查询表中数据时，自动将`xx_xx`类型的字段名转换为驼峰
>    例如:字段名user_name，设置了mapUnderscoreToCamelCase，此时字段名就会转换为 userName

### 4.1 用起别名的方式保证字段名与属性名一致

> 和sql中一样，用`字段名 属性名`（如`emp_name empName`）来给字段起别名使二者一致。

EmpMapper.xml

~~~xml
<!--List<Emp> getAllEmp();-->
<select id="getAllEmp" resultType="Emp">
    select eid, emp_name empName, age, sex, email from t_emp
</select>
~~~

此时再运行：

~~~shell
Emp{eid=1, empName='张三',age=23,sex='男',email='123@qq.com'}
Emp{eid=2, empName='李四',age=32,sex='女',email='123@qq.com'}
Emp{eid=3, empName='王五',age=12,sex='男',email='123@qq.com'}
Emp{eid=4, empName='赵六',age=34,sex='女',email='123@qq.com'}
Emp{eid=5, empName='田七',age=28,sex='男',email='123@qq.com'}
~~~

可以看到`empName`不再为null

### 4.2 配置核心文件自动映射

> 我们可以在mybatis-config.xml中配置文件将字段名中`_`自动转换为驼峰

mybatis-config.xml

~~~xml
<!--设置MyBatis的全局配置-->
<settings>
    <!--将_自动映射为驼峰-->
    <setting name="mapUnderscoreToCamelCase" value="true"/>
</settings>
~~~

此时就会将带`_`的字段名自动转换为驼峰。

### 4.3 通过resultMap设置自定义的映射关系

> 在映射文件sql标签中通过resultMap属性可以自定义映射关系。resultMap属性需要绑定一个映射关系。
>
> resultMap：设置自定义映射关系
>         id：唯一标识
>         type：映射的实体类型
>
> 子标签：id：设置主键的映射关系， result设置其他的映射关系
>     	property：设置映射关系中的属性名，必须是type属性所设置的实体类类型的属性名
>     	column：设置映射关系中的字段名，必须是sql语句查询出来的字段名
>
> 如果使用resultMap，就需要设置所有属性

- 在EmpMapper.xml中设置

  ~~~xml
  <!--
          resultMap设置自定义映射关系
          id      唯一标识
          type    映射的实体类型
  
          子标签：id 设置主键的映射关系， result设置其他的映射关系
              property    设置映射关系中的属性名，必须是type属性所设置的实体类类型的属性名
              column      设置映射关系中的字段名，必须是sql语句查询出来的字段名
  
          如果使用resultMap，就所有属性都需要设置
  -->
  <resultMap id="empResultMap" type="Emp">
      <id property="eid" column="eid"></id>
      <result property="empName" column="emp_name"></result>
      <result property="age" column="age"></result>
      <result property="sex" column="sex"></result>
      <result property="email" column="email"></result>
  </resultMap>
  
  <select id="getAllEmp" resultMap="empResultMap">
      select * from t_emp
  </select>
  ~~~

## 5. 多对一映射关系

> 应用场景：查询员工信息以及员工所对应的部门信息(对应对象)
>
> 有三种解决方式。下面详解：

### 5.1 级联方式处理映射关系

> 在员工实体类中添加`private Dept dept`字段，并创建get、set方法。
>
> 目的：查询员工以及员工所对应的部门信息。此时我们可以看到这是一(dept)对多(did、deptName)。

- EmpMapper.xml

  ~~~xml
  <!--    多对一映射关系，方式一：级联属性赋值-->
  <resultMap id="getEmpAndDeptResultMapOne" type="Emp">
      <id property="eid" column="eid"></id>
      <result property="empName" column="emp_name"></result>
      <result property="age" column="age"></result>
      <result property="sex" column="sex"></result>
      <result property="email" column="email"></result>
      <result property="dept.did" column="did"></result>
      <result property="dept.deptName" column="dept_name"></result>
  </resultMap>
  
  <!--Emp getEmpAndDept(@Param("eid") Integer eid);-->
  <select id="getEmpAndDept" resultMap="getEmpAndDeptResultMapOne">
      select * from t_emp left join t_dept on t_emp.eid = t_dept.did WHERE t_emp.eid = #{eid}
  </select>
  ~~~

  > 在第8行代码中用`dept.did`方式映射did字段。第9行同第8行。

- EmpMapper.java类中

  ~~~java
  public interface EmpMapper {
      /**
       * 查询员工及其所对应的部门信息
       */
      Emp getEmpAndDept(@Param("eid") Integer eid);
  }
  ~~~

- 测试类

  ~~~java
  /**
       * 处理多对一的映射关系
       * a> 级联属性赋值
       * b> association
       * c> 分步查询
       */
  @Test
  public void testGetEmpAndDept(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      EmpMapper mapper = sqlSession.getMapper(EmpMapper.class);
      Emp empAndDept = mapper.getEmpAndDept(3);
      System.out.println(empAndDept);
  }
  ~~~

  运行结果：

  ~~~shell
  Emp{eid=1,empName= '张王',age=23, sex='男',email= '123@qq.com',dept=Dept{did=1,deptName= 'A'}}
  ~~~

### 5.2 使用association处理映射关系

> association专门用于处理多对一映射关系。标签可以替代上面两行`dept.deptName`和`dept.did`。其属性如下：

association标签属性：

|  属性名  |                             描述                             |
| :------: | :----------------------------------------------------------: |
| property | 处理多对一所对应的属性，需要处理多对一的实体类映射关系的属性名 |
| javaType |                      property属性的类型                      |

association子标签属性：

| 标签名 |                             描述                             |
| :----: | :----------------------------------------------------------: |
|   id   | 主要用于主键。property属性用于映射和column属性值为被映射字段 |
| result |        property属性用于映射和column属性值为被映射字段        |

- EmpMapper.xml

  ~~~xml
  <resultMap id="empDeptMap" type="Emp">
      <id column="eid" property="eid"></id>
      <result column="ename" property="ename"></result>
      <result column="age" property="age"></result>
      <result column="sex" property="sex"></result>
      <association property="dept" javaType="Dept">
          <id column="did" property="did"></id>
          <result column="dname" property="dname"></result>
      </association>
  </resultMap>
  <!--Emp getEmpAndDeptByEid(@Param("eid") int eid);-->
  <select id="getEmpAndDeptByEid" resultMap="empDeptMap">
      select * from t_emp left join t_dept on t_emp.eid = t_dept.did WHERE t_emp.eid = #{eid}
  </select>
  ~~~

  运行结果：

  ~~~shell
  Emp{eid=3, empName= '王五',age=12, sex='男',email='123@qq.com',dept=Dept{did=3,deptName='C'}
  ~~~

### 5.3 分步查询(常用)

> 主要分为两步：
>
> 1. 查询员工信息
> 2. 根据员工所对应的部门id查询部门信息

- 查询员工信息

  - EmpMapper.java类

    ~~~java
    public interface EmpMapper {
        /**
    	* 通过分步查询查询员工信息 * @param eid
    	* @return
    	*/
        Emp getEmpByStep(@Param("eid") int eid);
    }
    ~~~

  - EmpMapper.xml

    ~~~xml
    <!--com.atguigu.mybatis.mapper.DeptMapper.getEmpAndDeptByStepTwo是这条sql语句的全类名-->
    <resultMap id="getEmpAndDeptByStepResultMap" type="Emp">
        <id property="eid" column="eid"></id>
        <result property="empName" column="emp_name"></result>
        <result property="age" column="age"></result>
        <result property="sex" column="sex"></result>
        <result property="email" column="email"></result>
        <!--
            select: 设置分步查询的sql的唯一标识（namespace.SQLId或mapper接口的全类名.方法名）
            column：分步查询的条件
            fetchType: 当开启了全局的延迟记载后，可通过此属性手动控制延迟加载的效果
            fetchType："lazy/eager" lazy表示延迟加载，eager表示立即加载
    -->
        <association property="dept"
                     select="com.atguigu.mybatis.mapper.DeptMapper.getEmpAndDeptByStepTwo"
                     column="did"
                     fetchType="eager">
        </association>
    </resultMap>
    
    <!--Emp getEmpAndDeptByStepOne(@Param("eid") Integer eid);-->
    <select id="getEmpAndDeptByStepOne" resultMap="getEmpAndDeptByStepResultMap">
        select * from t_emp where eid = #{eid}
    </select>
    ~~~

    > association属性：
    >
    > - property：将select查询结果赋值给此属性值。处理多对一所对应的属性，需要处理多对一的实体类映射关系的属性名
    > - select: 设置分步查询的sql的唯一标识（namespace.SQLId或mapper接口的全类名.方法名）即是哪个sql语句查询出来的。
    > - column：分步查询的条件，指定将哪一列的值传给这个方法，select指定方法。
    > - fetchType: 当开启了全局的延迟记载后，可通过此属性手动控制延迟加载的效果
    > - fetchType："lazy/eager" lazy表示延迟加载，eager表示立即加载
    >
    > 当我们执行到id为`getEmpAndDeptByStepOne`的sql标签时，通过resultMap的`getEmpAndDeptByStepResultMap`找到对应的映射关系。在执行到第14行时通过association的`select`指定运行`DeptMapper.xml`文件中`select`与之对应的id标签。查询条件是`column`的属性值，在这里是`did`，即将员工的did字段值赋值给`did`，然后查找对应的Emp(部门)。查询到之后将值赋值给`property`的属性值。

- 根据员工所对应的部门id查询部门信息

  - DeptMapper.java接口

    ~~~java
    public interface DeptMapper {
    	/**
    	* 分步查询的第二步:根据员工所对应的did查询部门信息
    	*/
    	Dept getEmpDeptByStep(@Param("did") int did);
    }
    ~~~

  - DeptMapper.xml

    ~~~xml
    <!--Dept getEmpAndDeptByStepTwo(Integer did);-->
    <!--分步查询可以实现懒加载-->
    <select id="getEmpAndDeptByStepTwo" resultType="Dept">
        select * from t_dept where did = #{did}
    </select>
    ~~~

- 编写测试文件

  ~~~java
  @Test
  public void testGetEmpAndDeptBystep(){
      SqlSession sqlSession = SqlSessionUtils .getSqlSession();
      EmpMapper mapper = sqlSession. getMapper(EmpMapper.class);
      Emp emp = mapper . getEmpAndDeptBystepOne(3);
      System. out . println(emp);
  }
  ~~~

  运行结果：
  [分布查询执行结果：](https://s1.ax1x.com/2022/07/26/jzqwFS.png)
                               [<img src="https://s1.ax1x.com/2022/07/26/jzqwFS.png" alt="jzqwFS.png" style="zoom:50%;" />](https://imgtu.com/i/jzqwFS)

### 5.4 分布查询的优点

> 优点：可以实现延迟加载(按需加载)，但是必须在核心配置文件中设置全局配置信息：
>
> - lazyLoadingEnabled：延迟加载的全局开关。当开启时，所有关联对象都会延迟加载
> - aggressiveLazyLoading：当开启时，任何方法的调用都会加载该对象的所有属性。 否则，每个属性会按需加载。所以属性值为false(默认)。
>
> 此时就可以实现按需加载，获取的数据是什么，就只会执行相应的sql，也成为延迟加载。可通过association和 collection中的fetchType属性设置当前的分步查询是否使用延迟加载，fetchType=“lazy(延迟加载)|eager(立即加载)”

- 在mybatis-config.xml中开启全局延迟加载

  ~~~xml
  <settings>
      <!--开启延迟加载-->
      <setting name="lazyLoadingEnabled",value="true"/>
  </settings>
  ~~~

- 在association.xml中设置是否开启延迟加载(lazy(延迟加载)|eager(立即加载))

  ~~~xml
  <association property="dept"
               select="com.atguigu.mybatis.mapper.DeptMapper.getEmpAndDeptByStepTwo"
               column="did"
               fetchType="lazy">
  </association>
  ~~~


- 修改测试文件

  ~~~java
  @Test
  public void testGetEmpAndDeptBystep(){
      SqlSession sqlSession = SqlSessionUtils .getSqlSession();
      EmpMapper mapper = sqlSession. getMapper(EmpMapper.class);
      Emp emp = mapper.getEmpAndDeptBystepOne(3);
      System.out.println(emp.getEmpName());
  }
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/07/26/jzjt1g.png)
                                       [<img src="https://s1.ax1x.com/2022/07/26/jzjt1g.png" alt="jzjt1g.png" style="zoom: 50%;" />](https://imgtu.com/i/jzjt1g)    

  > 我们可以看到当我们只是获取员工名字时，并没有加载`getEmpAndDeptByStepTwo`。而只执行了`getEmpAndDeptByStepOne`。这就是延迟加载(按需加载)。

## 6. 一对多映射关系

> 场景：根据部门id查找部门以及部门中的员工信息(对应集合)
>
> 需要查询一对多、多对一的关系，需要在“一”的pojo中加入List<多>属性，在“多”的pojo中加入“一”。
> 也就是说，在Dept类中，要加入`private List<Emp> emps;`，在Emp类中，要加入`private Dept dept;`。然后给他们各自添加get、set方法，重写构造器和toString()

### 6.1 通过collection解决一堆过的问题

- 现在Dept.java中添加一个集合`private List<Emp> emps`，之后重写toString()方法和get()、set()方法。

- DeptMapper.java接口

  ~~~java
  public interface DeptMapper {
      /**
       * 获取部门以及部门中所有的员工信息
       */
      Dept getDeptAndEmp(@Param("did") Integer did);
  }
  ~~~

- DeptMapper.xml

  ~~~xml
  <resultMap id="deptAndEmpResultMap" type="Dept">
      <id property="did" column="did"></id>
      <result property="deptName" column="dept_name"></result>
      <!--
              collection：处理一对多的映射关系
              ofType：表示该属性对应的集合中存储数据的类型
  	-->
      <collection property="emps" ofType="Emp">
          <id property="eid" column="eid"></id>
          <result property="empName" column="emp_name"></result>
          <result property="age" column="age"></result>
          <result property="sex" column="sex"></result>
          <result property="email" column="email"></result>
      </collection>
  </resultMap>
  <!--Dept getDeptAndEmp(@Param("did") Integer did);-->
  <select id="getDeptAndEmp" resultMap="deptAndEmpResultMap">
      select * from t_dept left join t_emp on t_dept.did = t_emp.did where t_dept.did = #{did}
  </select>
  ~~~

  collection属性介绍：

  |  属性名  |                 描述                 |
  | :------: | :----------------------------------: |
  | property |               对应集合               |
  |  ofType  | 表示该属性对应的集合中存储数据的类型 |

- 编写测试类

  ~~~java
  @Test
  public void testGetDeptAndEmp(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      DeptMapper mapper = sqlSession.getMapper(DeptMapper.class);
      Dept dept = mapper.getDeptAndEmp(1);
      System.out.println(dept);
  }
  ~~~

  > 查询did为1的部门及部门的员工信息。

  运行结果：

  ~~~shell
  Dept{
  	did=1, deptName='A', emps=[
  		Emp{eid=1, empName=' 张三'，age=23, sex='男', email='123@qq.com', dept=null}, 
  		Emp{eid=4, empName= '赵六'，age=34, sex='女' ，email='123@qq.com', dept=null}
  	]
  }
  ~~~

### 6.2 分步查询

- 查询部门信息

  - DeptMapper.java接口

    ~~~java
    public interface DeptMapper {
        /**
         * 分步查询 查询部门及其所有的员工信息
         * 第一步  查询部门信息
         */
        Dept getDeptAndEmoByStepOne(@Param("did") Integer did);
    }
    ~~~

  - DeptMapper.xml

    ~~~xml
    <!--分步查询-->
    <resultMap id="deptAndEmoByStepOneMap" type="Dept">
        <id property="did" column="did"></id>
        <result property="deptName" column="dept_name"></result>
        <collection property="emps"
                    select="com.atguigu.mybatis.mapper.EmpMapper.getDeptAndEmpByStepTwo"
                    column="did">
        </collection>
    </resultMap>
    <!--Dept getDeptAndEmoByStepOne(@Param("did") Integer did);-->
    <select id="getDeptAndEmoByStepOne" resultMap="deptAndEmoByStepOneMap">
        select * from t_dept where did = #{did}
    </select>
    ~~~

- 根据部门id查询部门中的所有员工

  - EmpMapper.java

    ~~~java
    public interface EmpMapper {
        /**
         * 分步查询 查询部门及其所有的员工信息
         * 第一步  查询部门信息
         * 第二步  根据查询员工信息
         */
        List<Emp> getDeptAndEmpByStepTwo(@Param("did") Integer did);
    }
    ~~~

  - EmpMapper.xml

    ~~~xml
    <!--分步查询-->
    <!--List<Emp> getDeptAndEmpByStepTwo(@Param("did") Integer did);-->
    <select id="getDeptAndEmpByStepTwo" resultType="Emp">
        select * from t_emp where did = #{did}
    </select>
    ~~~

- 编写测试类

  ~~~java
  @Test
  public void testGetDeptAndEmpBySteps(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      DeptMapper mapper = sqlSession.getMapper(DeptMapper.class);
      Dept dept = mapper.getDeptAndEmoByStepOne(2);
      System.out.println(dept.getDeptName());
      System.out.println("-----****************======分割线=======-----****************");
      System.out.println(dept);
  }
  ~~~

  运行结果：

  ~~~shell
  Dept{
  	did=1, deptName='A', emps=[
  		Emp{eid=1, empName=' 张三'，age=23, sex='男', email='123@qq.com', dept=null}, 
  		Emp{eid=4, empName= '赵六'，age=34, sex='女' ，email='123@qq.com', dept=null}
  	]
  }
  ~~~

> 同时也可以使用延时加载。

# 八. 动态SQL

> Mybatis框架的动态SQL技术是一种根据特定条件动态拼装SQL语句的功能，它存在的意义是为了解决拼接SQL语句字符串时的痛点问题。往往用在多条件查询。如：条件筛选。

## 1. if

> if标签可通过test属性的表达式进行判断，若表达式的结果为true，则标签中的内容会执行。反之标签中的内容不会执行。

| 参数名 |   描述   |
| :----: | :------: |
|  text  | 条件语句 |

- 在mapper包下创建一个DynamicSqlMapper.java接口

  ~~~java
  public interface DynamicSQLMapper {
      /**
       * 多条件查询
       */
      List<Emp> getEmpByCondition(Emp emp);
  }
  ~~~

- 创建对应的映射文件DynamicSqlMapper.xml

  ~~~xml
  <!--List<Emp> getEmpByCondition(Emp emp);-->
  <!--加上1=1使得：即使emp_name为空，也不会导致sql语句变成：where and xxx-->
  <select id="getEmpByCondition" resultType="Emp">
      select * from t_emp where 1=1
      <if test="empName != null and empName != ''">
          and emp_name = #{empName}
      </if>
      <if test="age != null and age != ''">
          and age = #{age}
      </if>
      <if test="email != null and email != ''">
          and email = #{email}
      </if>
      <if test="sex != null and sex != ''">
          and sex = #{sex}
      </if>
  </select>
  ~~~

  > 上面查询条件`1=1`是为了解决当`empName`属性为空，后面的`and`关键字拼接问题。

- 创建测试类

  ~~~java
  /**
       * 动态sql
       * 1： if： 根据标签中test属性所对应的内容决定标签中的内容是否拼接在sql语句中
       */
  @Test
  public void testGetEmpByCondition(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      DynamicSQLMapper mapper = sqlSession.getMapper(DynamicSQLMapper.class);
      // 各信息都不为null空字符串
      List<Emp> emp1 = mapper.getEmpByCondition(new Emp(null, "Apple", 22, "女", "123@gmail.com"));
      // 中间存在查询出来是空，可能导致"select * from t_emp where emp_name= ? and and sex = ?..."的and和and在一起的情况
      List<Emp> emp2 = mapper.getEmpByCondition(new Emp(null, "Apple", null, null, null));
      // 第一个查询条件为空字符串，可能导致"select * from t_emp where and age = ? and ..."的where和and在一起的情况
      List<Emp> emp3 = mapper.getEmpByCondition(new Emp(null, null, null, null, null));     
      System.out.println(emp1);
      System.out.println(emp2);
      System.out.println(emp3);
  }
  ~~~

  运行结果：

  ~~~shell
  [Emp{eid=1, empName= '张三',age=23, sex='男', email='123@qq.com', dept=null}]
  ~~~

  输出语句：

  ~~~sql
  # emp1
  select * from t_emp where 1=1 and emp_name=? and age=? and sex=? and email=?
  
  # emp2
  select * from t_emp where 1=1 and emp_name=? 
  
  # emp3
  select * from t_emp where 1=1
  ~~~

## 2. where

> 语句不加`WHERE`。当`<whele>`标签中`<if>`有一个条件为true时，能自动生成`WHELE`关键字，同时还能取消条件成立时==前面==的`and`或者`or`关键字。
>
> 注意：where标签不能将判断语句内容后的`and`或者`or`关键字去掉。

- DynamicSqlMapper.java接口

  ~~~java
  public interface DynamicSQLMapper {
      /**
       * 多条件查询
       */
      List<Emp> getEmpByCondition(Emp emp);
  }
  ~~~

- DynamicSqlMapper.xml

  ~~~xml
  <!--    where标签中，如果有内容，则添加关键字，如果没有内容，则把and/or去掉-->
  <select id="getEmpByCondition" resultType="Emp">
      select * from t_emp
      <where>
          <if test="empName != null and empName != ''">
              and emp_name = #{empName}
          </if>
          <if test="age != null and age != ''">
              and age = #{age}
          </if>
          <if test="email != null and email != ''">
              and email = #{email}
          </if>
          <if test="sex != null and sex != ''">
              and sex = #{sex}
          </if>
      </where>
  </select>
  ~~~

- 编写测试类

  ~~~java
  /**
       * 2、where：
       *      当where标签中有内容时，会自动生成where关键字，并将内容前多余的and或or去掉
       *      当where标签中没有内容时，此时where标签没有任何效果
       *      注意：where标签不能将其中内容后面多余的and或or去掉
       */
  @Test
  public void testGetEmpByCondition2(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      DynamicSQLMapper mapper = sqlSession.getMapper(DynamicSQLMapper.class);
      List<Emp> emp1 = mapper.getEmpByCondition(new Emp(null, "Apple", 22, "女", "123@gmail.com"));
      List<Emp> emp2 = mapper.getEmpByCondition(new Emp(null, "Apple", null,null, null));
      List<Emp> emp3 = mapper.getEmpByCondition(new Emp(null, null, null, null,null));     
      System.out.println(emp1);
      System.out.println(emp2);
      System.out.println(emp3);
  }
  ~~~

  输出语句：

  ~~~sql
  # emp1
  select * from t_emp WHERE emp_name=? and age=? and sex=? and email=?
  
  # emp2
  select * from t_emp WHERE emp_name=?
  
  # emp3
  select * from t_emp 
  ~~~

## 3. trim

> 若标签中有一条判断结果为true时，会合适的去掉标签属性指定的字段，以保证sql语句正确。如果标签中语句都为false，那么或去掉`WHERE`关键字。

trim标签的属性：

| 属性名          |                             描述                             |
| :-------------- | :----------------------------------------------------------: |
| prefix          | 将trim标签中内容前面或后面添加指定内容。可以指定指定多个值，多个值之间用`|`分隔 |
| suffix          | 将trim标签中内容前面或后面添加指定内容。可以指定指定多个值，多个值之间用`|`分隔 |
| suffixOverrides | 将trim标签中内容前面或后面去掉指定内容。可以指定指定多个值，多个值之间用`|`分隔 |
| prefixOverrides | 将trim标签中内容前面或后面去掉指定内容。可以指定指定多个值，多个值之间用`|`分隔 |

- DynamicSqlMapper.java接口

  ~~~java
  public interface DynamicSQLMapper {
      /**
       * 多条件查询
       */
      List<Emp> getEmpByCondition(Emp emp);
  }
  ~~~

- DynamicSqlMapper.xml

  ~~~xml
  <select id="getEmpByCondition" resultType="Emp">
      select * from t_emp
      <trim prefix="where" suffixOverrides="and|or">
          <if test="empName != null and empName != ''">
              emp_name = #{empName} and
          </if>
          <if test="age != null and age != ''">
              age = #{age} or
          </if>
          <if test="email != null and email != ''">
              email = #{email} and
          </if>
          <if test="sex != null and sex != ''">
              sex = #{sex}
          </if>
      </trim>
  </select>
  ~~~

- 测试类

  ~~~java
  /**
       * 2、where：
       *      当where标签中有内容时，会自动生成where关键字，并将内容前多余的and或or去掉
       *      当where标签中没有内容时，此时where标签没有任何效果
       *      注意：where标签不能将其中内容后面多余的and或or去掉
       */
  @Test
  public void testGetEmpByCondition2(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      DynamicSQLMapper mapper = sqlSession.getMapper(DynamicSQLMapper.class);
      List<Emp> emp1 = mapper.getEmpByCondition(new Emp(null, "Apple", 22, "女", "123@gmail.com"));
      List<Emp> emp2 = mapper.getEmpByCondition(new Emp(null, "Apple", null,null, null));
      List<Emp> emp3 = mapper.getEmpByCondition(new Emp(null, null, null, null,null));     
      System.out.println(emp1);
      System.out.println(emp2);
      System.out.println(emp3);
  }
  ~~~

  输出语句：

  ~~~sql
  # emp1
  select * from t_emp WHERE emp_name=? and age=? and sex=? and email=?
  
  # emp2
  select * from t_emp WHERE emp_name=?
  
  # emp3
  select * from t_emp 
  ~~~

## 4. choose-when-otherwise

> 相当于Java中的`Switch-case-default`。特点是，有一个条件成立就不会执行后面的判断。
>
> when至少要有一个，otherwise最多只能有一个

- DynamicSqlMapper.java接口

  ~~~java
  public interface DynamicSQLMapper {
      /**
       * 测试choose when otherwise
       */
      List<Emp> getEmpByChoose(Emp emp);
  }
  ~~~

- DynamicSqlMapper.xml

  ~~~xml
  <!--List<Emp> getEmpByChoose(Emp emp);-->
  <select id="getEmpByChoose" resultType="Emp">
      select * from t_emp
      <where>
          <choose>
              <when test="empName != null and empName != ''">
                  emp_name = #{empName}
              </when>
              <when test="age != null and age != ''">
                  age = #{age}
              </when>
              <when test="sex != null and sex != ''">
                  sex = #{sex}
              </when>
              <when test="email != null and email != ''">
                  email = #{email}
              </when>
              <otherwise>
                  did = 2
              </otherwise>
          </choose>
      </where>
  </select>
  ~~~

  > 如果满足`<when>`中的条件，就加上，但不会执行后面的判断。如果都不满足，则查询`did=1`的员工。

- 测试类

  ~~~java
  /**
       * 2、where：
       *      当where标签中有内容时，会自动生成where关键字，并将内容前多余的and或or去掉
       *      当where标签中没有内容时，此时where标签没有任何效果
       *      注意：where标签不能将其中内容后面多余的and或or去掉
       */
  @Test
  public void testGetEmpByCondition2(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      DynamicSQLMapper mapper = sqlSession.getMapper(DynamicSQLMapper.class);
      List<Emp> emp1 = mapper.getEmpByCondition(new Emp(null, "Apple", 22, "女", "123@gmail.com"));
      List<Emp> emp2 = mapper.getEmpByCondition(new Emp(null, null, 23,null, "123@gmail.com"));
      List<Emp> emp3 = mapper.getEmpByCondition(new Emp(null, null, null, null,null));     
      System.out.println(emp1);
      System.out.println(emp2);
      System.out.println(emp3);
  }
  ~~~

  输出语句：

  ~~~sql
  # emp1
  select * from t_emp WHERE emp_name=?
  
  # emp2
  select * from t_emp WHERE age=?
  
  # emp3
  select * from t_emp WHERE did=1
  ~~~

## 5. foreach

foreach标签内置属性

| 属性名     |                 描述                 |
| :--------- | :----------------------------------: |
| collection | 遍历的数组或者集合，即接口传递的参数 |
| item       |            传递属性变量名            |
| separator  |         每次遍历以什么做分隔         |
| open       |       遍历内容以什么作为开始符       |
| close      |       遍历内容以什么作为结束符       |

### 5.1 实现批量删除

> 通过数组实现批量删除。 

- DynamicSqlMapper.java接口

  ~~~java
  public interface DynamicSQLMapper {
      /**
       * 通过数组实现批量删除
       */
      int deleteMoreByArray(@Param("eids") Integer[] eids);
  }
  ~~~

- 编写测试类

  ~~~java
  /**
       * 5、foreach
       */
  @Test
  public void testDeleteMoreByArray(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      DynamicSQLMapper mapper = sqlSession.getMapper(DynamicSQLMapper.class);
      int result = mapper.deleteMoreByArray(new Integer[]{7, 8, 9});
      System.out.println(result);
  }
  ~~~

- DynamicSqlMapper.xml

  - 方法一

    ~~~xml
    <!--int deleteMoreByArray(Integer[] eids);-->
    <!--没加@Param时，
        报错：Parameter 'eids' not found. Available parameters are [array, arg0]
        因此最好都加上@Param-->
    <!--int deleteMoreByArray(@Param("eids") Integer[] eids);-->
    <delete id="deleteMoreByArray">
        delete from t_emp where eid in
        <foreach collection="eids" item="eid" separator="," open="(" close=")">
            #{eid}
        </foreach>
    </delete>
    ~~~

    输出语句

    ~~~sql
    delete from t_emp where eid in(7,8,9)
    ~~~

    > 此时就会在数据库删除`eid`字段为7，8，9的员工。

  - 方法二：

    ~~~xml
    <!--int deleteMoreByArray(Integer[] eids);-->
    <delete id="deleteMoreByArray">
        <!--方法2：-->
        delete from t_emp where
        <foreach collection="eids"  item="eid" separator="or">
            eid = #{eid}
        </foreach>
    </delete>
    ~~~

    输出语句：

    ~~~sql
    from t_ emp where eid=7 or eid=8 or eid=9
    ~~~

### 5.2 实现批量添加

> 通过list集合实现批量添加

- DynamicSqlMapper.java接口

  ~~~java
  public interface DynamicSQLMapper {
      /**
       * 通过list集合实现批量添加
       */
      int insertMoreByList(@Param("emps") List<Emp> emps);
  }
  ~~~

- DynamicSqlMapper.xml

  ~~~xml
  <!--int insertMoreByList(List<Emp> emps);-->
  <!--不加注解会报错：Parameter 'emps' not found. Available parameters are [arg0, collection, list]-->
  <!--int insertMoreByList(@Param("emps") List<Emp> emps);-->
  <insert id="insertMoreByList">
      insert into t_emp values
      <foreach collection="emps" item="emp" separator=",">
          (null, #{emp.empName}, #{emp.age}, #{emp.sex}, #{emp.email}, null)
      </foreach>
  </insert>
  ~~~

- 编写测试类

  ~~~java
  /**
       * 5、foreach
       *      collection  需要循环的数组或集合
       *      item        表示数组或集合中的每一个数据
       *      separator   循环体之间的分隔符
       *      open        foreach标签所循环的所有内容的开始符
       *      close       foreach标签所循环的所有内容的结束符
       */
  @Test
  public void testInsertMoreByList(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      DynamicSQLMapper mapper = sqlSession.getMapper(DynamicSQLMapper.class);
      Emp emp1 = new Emp(null, "Mary", 23, "女", "11111@qq.com");
      Emp emp2 = new Emp(null, "Linda", 23, "女", "1144111@qq.com");
      Emp emp3 = new Emp(null, "Jackoline", 23, "女", "1122111@qq.com");
      List<Emp> emps = Arrays.asList(emp1, emp2, emp3);
      System.out.println(mapper.insertMoreByList(emps));
  }
  ~~~

  执行语句：

  ~~~sql
  insert into t_emp values (null,?,?,?,?,null),(null,?,?,?,?null),(null,?,?,?,?null)
  ~~~

## 6. SQL片段

> SQL片段可以将我们开发时较为常用的字段保存起来，方便引用。

- DynamicSqlMapper.xml

  ~~~xml
  <!--设置SQL片段-->
  <sql id="empColumns">eid,emp_name,age,sex,email</sq1>
  <select id=" getEmpByCondition" resultType=" Emp">
      <!--引用SQL片段-->
      select <include refid="empColumns"></include> from t_emp
  </select>
  ~~~

  输出语句

  ~~~sql
   select eid,emp_name,age,sex,email from t_emp
  ~~~

# 九. MyBatis缓存

> 缓存就是将查询的数据记录下来，下次再次查询数据时，就不用访问数据库。能提高查询速度。只针对查询功能有效。

## 1. MyBatis的一级缓存与失效

> 一级缓存是SqlSession级别的，通过同一个SqlSession查询的数据会被缓存，下次查询相同的数据，就会从缓存中直接获取，不会从数据库重新访问。一级缓存默认开启。
>
> 使一级缓存失效的四种情况:
>
> 1. 不同的SqlSession对应不同的一级缓存
> 2. 同一个SqlSession但是查询条件不同
> 3. 同一个SqlSession两次查询期间执行了任何一次增删改操作
> 4. 同一个SqlSession两次查询期间手动清空了缓存

- 不同的SqlSession对应不同的一级缓存，在测试类中添加查询方法

  > 只要不重新获取sqlSession，缓存就存在

  ~~~java
  @Test
  public void testCache(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      CacheMapper mapper = sqlSession.getMapper(CacheMapper.class);
      Emp emp1 = mapper.getEmpById(3);
      System.out.println(emp1);
      System.out.println("========第二次调用========从缓存中取数据");
      Emp emp2 = mapper.getEmpById(3);
      System.out.println(emp2);
  
      System.out.println("\n========即使用的不是同一个Mapper，也同样从缓存中取(同一个sqlsession)========");
      CacheMapper mapper2 = sqlSession.getMapper(CacheMapper.class);
      Emp empByMapper2 = mapper2.getEmpById(3);
      System.out.println(empByMapper2);
  
      System.out.println("\n========一级缓存的范围在sqlsession中，换一个新的sqlsession就会再次用sql读取数据========");
      SqlSession sqlSession2 = SqlSessionUtils.getSqlSession();
      CacheMapper mapper2BySqlSession2 = sqlSession2.getMapper(CacheMapper.class);
      System.out.println(mapper2BySqlSession2.getEmpById(3));
  }
  ~~~

  运行结果：
  [SqlSession对应不同的一级缓存：](https://s1.ax1x.com/2022/07/27/vpkk8A.png)
                           [<img src="https://s1.ax1x.com/2022/07/27/vpkk8A.png" alt="vpkk8A.png" style="zoom: 33%;" />](https://imgtu.com/i/vpkk8A)

- 同一个SqlSession但是查询条件不同

  > 查询两个不同id，与数据库建立两次链接。所以一级缓存失效。

  ~~~java
  @Test
  public void testCache3(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      CacheMapper mapper = sqlSession.getMapper(CacheMapper.class);
  
      System.out.println("=====第一次获取数据=====");
      Emp emp1 = mapper.getEmpById(3);
      System.out.println(emp1);
  
      System.out.println("\n=====查询条件不同=====");
      Emp emp2 = mapper.getEmpById(5);
      System.out.println(emp2);
  }
  ~~~

  运行结果：
  [同一个SqlSession但是查询条件不同：](https://s1.ax1x.com/2022/07/27/vpk18s.png)
                          [<img src="https://s1.ax1x.com/2022/07/27/vpk18s.png" alt="vpk18s.png" style="zoom:33%;" />](https://imgtu.com/i/vpk18s)

- 同一个SqlSession两次查询期间执行了任何一次增删改操作

  > 下面的代码可以看出当我们在同一个SqlSession情况下执行力增删改操作。缓存就会失败。

  ~~~java
  @Test
  public void testCache2(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      CacheMapper mapper = sqlSession.getMapper(CacheMapper.class);
  
      System.out.println("=====第一次获取数据=====");
      Emp emp1 = mapper.getEmpById(3);
      System.out.println(emp1);
      Emp emp2 = mapper.getEmpById(3);
      System.out.println(emp2);
  
      System.out.println("\n=====进行增删改操作=====");
      mapper.insetEmp(new Emp(null, "Joey", 44, "男", "8888@gmai.com"));
  
      System.out.println("\n=====同一个sqlsession，再获取数据=====");
      Emp emp3 = mapper.getEmpById(3);
      System.out.println(emp3);
  }
  ~~~

  运行结果：
  [两次查询期间执行了任何一次增删改操作：](https://s1.ax1x.com/2022/07/27/vpk0PJ.png)
                         [<img src="https://s1.ax1x.com/2022/07/27/vpk0PJ.png" alt="vpk0PJ.png" style="zoom: 33%;" />](https://imgtu.com/i/vpk0PJ)

- 同一个SqlSession两次查询期间手动清空了（一级）缓存

  > 可以通过` sqlSession.clearCache();`方法手动清空sqlSession。之后再次查询缓存就会失效。

  ~~~java
  @Test
  public void testCache4(){
      SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      CacheMapper mapper = sqlSession.getMapper(CacheMapper.class);
  
      System.out.println("=====第一次获取数据=====");
      Emp emp1 = mapper.getEmpById(3);
      System.out.println(emp1);
  
      System.out.println("\n=====两次查询期间手动清空缓存=====");
      sqlSession.clearCache();
  
      System.out.println("\n=====再次查询id=3的emp=====");
      Emp emp2 = mapper.getEmpById(3);
      System.out.println(emp2);
  }
  ~~~

  运行结果：
  [手动清空了一级缓存再查询：](https://s1.ax1x.com/2022/07/27/vpEFXt.png)

  ​                    [<img src="https://s1.ax1x.com/2022/07/27/vpEFXt.png" alt="vpEFXt.png" style="zoom:33%;" />](https://imgtu.com/i/vpEFXt)

## 2. MyBatis的二级缓存

> 二级缓存是SqlSessionFactory级别，通过同一个SqlSessionFactory创建的SqlSession查询的结果会被缓存；此后若再次执行相同的查询语句，结果就会从缓存中获取。
>
> 二级缓存开启的条件：
>
> 1. 在核心配置文件中，设置全局配置属性`cacheEnabled=“true"`，默认为true，不需要设置
> 2. 在映射文件中设置标签`<cache />`
> 3. 二级缓存必须在SqlSession关闭或提交之后有效
> 4. 查询的数据所转换的实体类类型必须实现序列化的接口
>
> 使二级缓存失效的情况：**两次查询之间执行了任意的增删改**，会使一级和二级缓存同时失效。没有提交sqlsession时，数据会保存在一级缓存中，提交后，会保存在二级缓存中。

- 在接口对应映射文件CacheMapper.xml中开启缓存

  ~~~xml
  <cache />
  ~~~

  [开启二级缓存：](https://s1.ax1x.com/2022/07/28/v9Qqf0.png)
                                  [<img src="https://s1.ax1x.com/2022/07/28/v9Qqf0.png" alt="v9Qqf0.png" style="zoom:50%;" />](https://imgtu.com/i/v9Qqf0)

- 在接口对应的实体类Emp.java中实现序列化接口

  > 实体类中实现`Serializable`接口。

  ~~~java
  public class Emp implements Serializable{
   ...   
  }
  ~~~

- 编写测试类

  ~~~java
  @Test
  public void testCacheTwo(){
      // 这里不能用工具类了，因为每次都会创建新的sqlsessionfactory
      // SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      // CacheMapper mapper = sqlSession.getMapper(CacheMapper.class);
      //只要是同一个sqlsessionfactory获得的sqlsession就可以
      try {
          InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
          SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
          SqlSession sqlSession1 = sqlSessionFactory.openSession(true);
          CacheMapper mapper1 = sqlSession1.getMapper(CacheMapper.class);
          System.out.println(mapper1.getEmpById(1));
  
          System.out.println("Cache Hit Ratio：缓存命中率，指的是在缓存中有没有这条数据");
          System.out.println("=====二级缓存未打开，没从缓存中获取数据=====");
          SqlSession sqlSession2 = sqlSessionFactory.openSession(true);
          CacheMapper mapper2 = sqlSession2.getMapper(CacheMapper.class);
          System.out.println(mapper2.getEmpById(1));
      } catch (IOException e) {
          e.printStackTrace();
      }
  }
  ~~~

  > 上面的代码执行后，控制台缓存命中率为0(没有二级缓存)。这是因为，我们在每个工厂SqlSessionFactory创建对象sqlSession查询数据后没有手动关闭sqlsession对象。所以二级缓存失效。

  [二级缓存为打开：](https://s1.ax1x.com/2022/07/28/v9YgHO.png)
                     [<img src="https://s1.ax1x.com/2022/07/28/v9YgHO.png" alt="v9YgHO.png" style="zoom: 33%;" />](https://imgtu.com/i/v9YgHO)

- 手动关闭sqlsession使二级缓存生效

  ~~~java
  @Test
  public void testCacheTwo(){
      // 这里不能用工具类了，因为每次都会创建新的sqlsessionfactory
      // SqlSession sqlSession = SqlSessionUtils.getSqlSession();
      // CacheMapper mapper = sqlSession.getMapper(CacheMapper.class);
      //只要是同一个sqlsessionfactory获得的sqlsession就可以
      try {
          InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
          SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
          SqlSession sqlSession1 = sqlSessionFactory.openSession(true);
          CacheMapper mapper1 = sqlSession1.getMapper(CacheMapper.class);
          System.out.println(mapper1.getEmpById(1));
          JYOLCIITUULOPI -ITL CIISIaPpCI- .gC LCpuy-ulCide一
  		System.out.printLn("\n=====关闭sqLSession1=====") ;
          //把sqlSession1关闭，数据保存到二级缓存
  		sqlSession1.cLose();		
  
  
          System.out.println("Cache Hit Ratio：缓存命中率，指的是在缓存中有没有这条数据");
          System.out.println("=====二级缓存未打开，没从缓存中获取数据=====");
          SqlSession sqlSession2 = sqlSessionFactory.openSession(true);
          CacheMapper mapper2 = sqlSession2.getMapper(CacheMapper.class);
          System.out.println(mapper2.getEmpById(1));
          sqlSession2.cLose();
      } catch (IOException e) {
          e.printStackTrace();
      }
  }
  ~~~

  [开启二级缓存后的运行结果：](https://s1.ax1x.com/2022/07/28/v9Btk6.png)
                            [<img src="https://s1.ax1x.com/2022/07/28/v9Btk6.png" alt="v9Btk6.png" style="zoom: 33%;" />](https://imgtu.com/i/v9Btk6)

## 3. 二级缓存的相关配置

> 上面的`<cache />`可以配置一些属性：
>
> 1. eviction属性:缓存回收策略
>    - LRU(Least Recently Used) – 最近最少使用的：移除最长时间不被使用的对象。
>    - FIFO(First in First out) – 先进先出：按对象进入缓存的顺序来移除它们。
>    - SOFT – 软引用:移除基于垃圾回收器状态和软引用规则的对象。
>    - WEAK –弱引用:更积极地移除基于垃圾收集器状态和弱引用规则的对象。
>    - 默认的是 LRU。
> 2. flushInterval属性：刷新间隔，单位毫秒
>    - 默认情况是不设置，也就是没有刷新间隔，缓存仅仅调用语句（增删改） 时刷新
> 3. size属性：引用数目，正整数
>    - 代表缓存最多可以存储多少个对象，设置太大容易导致内存溢出
> 4. readOnly属性：只读，true/false
>    - true:只读缓存; 会给所有调用者返回缓存对象的相同实例。因此这些对象不能被修改。这提供了很重要的性能优势。【性能好】
>    - false:读写缓存; 会返回缓存对象的拷贝(通过序列化)。这会慢一些，但是安全，因此默认是 false。【安全】

## 4. MyBatis缓存查询的顺序

> 1. 先查询二级缓存，因为二级缓存中可能会有其他程序已经查出来的数据，可以拿来直接使用。
> 2. 如果二级缓存没有命中，再查询一级缓存
> 3. 如果一级缓存也没有命中，则查询数据库
> 4. SqlSession**关闭之后，一级缓存中的数据会写入二级缓存**。

## 5. 整合第三方缓存EHCache

> 该第三方库只能代替二级缓存

- 在`pom.xml`中添加依赖

  ~~~xml
  <!-- Mybatis EHCache整合包 --> 
  <dependency>
      <groupId>org.mybatis.caches</groupId>
      <artifactId>mybatis-ehcache</artifactId>
      <version>1.2.1</version>
  </dependency>
  
  <!-- slf4j日志门面的一个具体实现类 --> 
  <dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
      <version>1.2.3</version>
  </dependency>
  ~~~

  [各种jar包的功能：](https://s1.ax1x.com/2022/07/28/v9T6fg.png)

  ​                               [<img src="https://s1.ax1x.com/2022/07/28/v9T6fg.png" alt="v9T6fg.png" style="zoom:50%;" />](https://imgtu.com/i/v9T6fg)

- 创建EHCache的配置文件ehcache.xml(名字必须为ehcache.xml)

  ~~~xml
  <?xml version="1.0" encoding="utf-8" ?>
  <ehcache xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="../config/ehcache.xsd">
  <!-- 磁盘保存路径 -->
  <diskStore path="这里改成你需要保存缓存的磁盘路径"/>
      <defaultCache
              maxElementsInMemory="1000"
              maxElementsOnDisk="10000000"
              eternal="false"
              overflowToDisk="true"
              timeToIdleSeconds="120"
              timeToLiveSeconds="120"
              diskExpiryThreadIntervalSeconds="120"
              memoryStoreEvictionPolicy="LRU">
      </defaultCache>
  </ehcache>
  ~~~

  > `"../config/ehcache.xsd"`报错，则创建这个文件。

  [配置文件说明：](https://s1.ax1x.com/2022/07/28/v97ruR.png)

  ​                                 [<img src="https://s1.ax1x.com/2022/07/28/v97ruR.png" alt="v97ruR.png" style="zoom: 50%;" />](https://imgtu.com/i/v97ruR)

- 在接口映射文件中设置二级缓存类型

  ~~~xml
  <cache type="org.mybatis.caches.ehcache.EhcacheCache"/>
  ~~~

- 加入logback日志

  > 存在SLF4J时，作为简易日志的log4j将失效，此时我们需要借助SLF4J的具体实现logback来打印日志。

  创建logback的配置文件logback.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <configuration debug="true"> <!-- 指定日志输出的位置 -->
      <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
          <encoder>
              <!-- 日志输出的格式 -->
              <!-- 按照顺序分别是:时间、日志级别、线程名称、打印日志的类、日志主体内容、换行 -->
              <pattern>[%d{HH:mm:ss.SSS}] [%-5level] [%thread] [%logger] [%msg]%n</pattern>
          </encoder>
      </appender>
      <!-- 设置全局日志级别。日志级别按顺序分别是:DEBUG、INFO、WARN、ERROR -->
      <!-- 指定任何一个日志级别都只打印当前级别和后面级别的日志。 -->
      <root level="DEBUG">
          <!-- 指定打印日志的appender，这里通过“STDOUT”引用了前面配置的appender -->
          <appender-ref ref="STDOUT" />
      </root>
      <!-- 根据特殊需求指定局部日志级别 -->
      <logger name="com.atguigu.mybatis.mapper" level="DEBUG"/>
  </configuration>
  ~~~

  > 此时再次运行之前编写的测试文件，会发现缓存保存在了磁盘上。

  [数据保存至磁盘：](https://s1.ax1x.com/2022/07/28/v97vvj.png)
                                  [<img src="https://s1.ax1x.com/2022/07/28/v97vvj.png" alt="v97vvj.png" style="zoom: 67%;" />](https://imgtu.com/i/v97vvj)

# ==十. MyBatis的逆向工程(MBG)==

> 正向工程与你想工程概念：
>
> 1. 正向工程：先创建Java实体类，由框架负责根据实体类生成数据库表。Hibernate是支持正向工程的。
> 2. 逆向工程：先创建数据库表,由框架负责根据数据库表,反向生成如下资源：
>    - Java实体类
>    - Mapper接口
>    - Mapper映射文件
>
> MyBatis逆向工程指的是根据一张sql表单，借助Maven和MBG直接创建pojo、mapper接口（xxxMapper）、映射文件（xxxMapper.xml）。就不需要我们自己一个一个创建文件去配置。

## 1. 创建逆向工程MyBatis3Simple(简洁版)的步骤

### 1.1 创建MyBatis核心配置文件

- 创建`t_dept`和`t_emp`表单
  [t_dept表：](https://s1.ax1x.com/2022/07/28/v9q9hT.png)
                        [<img src="https://s1.ax1x.com/2022/07/28/v9q9hT.png" alt="v9q9hT.png" style="zoom:50%;" />](https://imgtu.com/i/v9q9hT)

  [t_emp表：](https://s1.ax1x.com/2022/07/28/v9qlge.png)
                   [<img src="https://s1.ax1x.com/2022/07/28/v9qlge.png" alt="v9qlge.png" style="zoom:50%;" />](https://imgtu.com/i/v9qlge)

- 添加依赖和插件：在pom.xml中添加依赖和插件，更新maven

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <project xmlns="http://maven.apache.org/POM/4.0.0"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
  
      <groupId>org.example</groupId>
      <artifactId>MyBatis_MBG</artifactId>
      <version>1.0-SNAPSHOT</version>
  
      <properties>
          <maven.compiler.source>8</maven.compiler.source>
          <maven.compiler.target>8</maven.compiler.target>
      </properties>
  
      <!-- 依赖MyBatis核心包 -->
      <dependencies>
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
          <!-- log4j日志 -->
          <dependency>
              <groupId>log4j</groupId>
              <artifactId>log4j</artifactId>
              <version>1.2.17</version>
          </dependency>
          <dependency>
              <groupId>org.junit.jupiter</groupId>
              <artifactId>junit-jupiter</artifactId>
              <version>RELEASE</version>
              <scope>test</scope>
          </dependency>
  
      </dependencies>
      <!-- 控制Maven在构建过程中相关配置 -->
      <build>
          <!-- 构建过程中用到的插件 -->
          <plugins>
              <!-- 具体插件，逆向工程的操作是以构建过程中插件形式出现的 -->
              <plugin>
                  <groupId>org.mybatis.generator</groupId>
                  <artifactId>mybatis-generator-maven-plugin</artifactId>
                  <version>1.3.0</version>
                  <!-- 插件的依赖 -->
                  <dependencies>
                      <!-- 逆向工程的核心依赖 -->
                      <dependency>
                          <groupId>org.mybatis.generator</groupId>
                          <artifactId>mybatis-generator-core</artifactId>
                          <version>1.3.2</version>
                      </dependency>
                      <!-- 数据库连接池 -->
                      <dependency>
                          <groupId>com.mchange</groupId>
                          <artifactId>c3p0</artifactId>
                          <version>0.9.2</version>
                      </dependency>
                      <!-- MySQL驱动 -->
                      <dependency>
                          <groupId>mysql</groupId>
                          <artifactId>mysql-connector-java</artifactId>
                          <version>5.1.8</version>
                      </dependency>
                  </dependencies>
              </plugin>
          </plugins>
      </build>
  </project>
  ~~~

- 创建MyBatis的核心配置文件

  > 在src/main/resources下创建mybatis-config.xml

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE configuration
          PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-config.dtd">
  <configuration>
  
      <properties resource="jdbc.properties"></properties>
  
      <!--设置连接数据库的环境-->
      <environments default="development">
          <environment id="development">
              <transactionManager type="JDBC"/>
              <dataSource type="POOLED">
                  <property name="driver" value="${jdbc.driver}"/>
                  <property name="url"
                            value="${jdbc.url}"/>
                  <property name="username" value="${jdbc.username}"/>
                  <property name="password" value="${jdbc.password}"/>
              </dataSource>
          </environment>
      </environments>
  
  </configuration>
  ~~~

- 创建jdbc.properties文件

  ~~~properties
  jdbc.driver=com.mysql.jdbc.Driver
  jdbc.url=jdbc:mysql://localhost:3306/mybatis?characterEncoding=utf8
  jdbc.username=root
  jdbc.password=写你的数据库密码
  ~~~

- 创建log4j.xml日志配置文件

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE log4j:configuration SYSTEM "log4j.dtd">
  <log4j:configuration xmlns:log4j="http://jakarta.apache.org/log4j/"
                       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                       xsi:schemaLocation="http://jakarta.apache.org/log4j/ ">
      <appender name="STDOUT" class="org.apache.log4j.ConsoleAppender">
          <param name="Encoding" value="UTF-8"/>
          <layout class="org.apache.log4j.PatternLayout">
              <param name="ConversionPattern" value="%-5p %d{MM-dd HH:mm:ss,SSS}
                                                     %m  (%F:%L) \n"/>
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

### 1.2 创建逆向工程的配置文件

> 注意：文件名必须是：generatorConfig.xml。mac环境下，\要修改为/，windows才是targetProject="./src/main/java

generatorConfig.xml

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE generatorConfiguration
        PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">
<generatorConfiguration>

    <!--
    	targetRuntime: 执行生成的逆向工程的版本
        MyBatis3Simple: 生成基本的CRUD(清新简洁版)
        MyBatis3: 生成带条件的CRUD(奢华尊享版)
    -->
    <context id="DB2Tables" targetRuntime="MyBatis3Simple"> <!-- 数据库的连接信息 -->
        <jdbcConnection driverClass="com.mysql.jdbc.Driver"
                        connectionURL="jdbc:mysql://localhost:3306/mybatis"
                        userId="root"
                        password="123456">
        </jdbcConnection>
        <!--javaBean的生成策略-->
        <javaModelGenerator targetPackage="com.atguigu.mybatis.pojo"
                            targetProject=".\src\main\java">
            <property name="enableSubPackages" value="true"/>
            <property name="trimStrings" value="true"/>
        </javaModelGenerator>
        <!-- SQL映射文件的生成策略 -->
        <sqlMapGenerator targetPackage="com.atguigu.mybatis.mapper"
                         targetProject=".\src\main\resources">
            <property name="enableSubPackages" value="true"/>
        </sqlMapGenerator>
        <!-- Mapper接口的生成策略 -->
        <javaClientGenerator type="XMLMAPPER"
                             targetPackage="com.atguigu.mybatis.mapper" targetProject=".\src\main\java">
            <property name="enableSubPackages" value="true"/>
        </javaClientGenerator>
        <!-- 逆向分析的表 -->
        <!-- tableName设置为*号，可以对应所有表，此时不写domainObjectName --> 
        <!-- domainObjectName属性指定生成出来的实体类的类名 -->
        <table tableName="t_emp" domainObjectName="Emp"/>
        <table tableName="t_dept" domainObjectName="Dept"/>
    </context>
</generatorConfiguration>
~~~

### 1.3 执行MBG插件的generate目标

- 执行generate目标
  [生成文件：](https://s1.ax1x.com/2022/07/28/v9jpqJ.png)
                             [<img src="https://s1.ax1x.com/2022/07/28/v9jpqJ.png" alt="v9jpqJ.png" style="zoom: 33%;" />](https://imgtu.com/i/v9jpqJ)   

  [操作前的文件目录：](https://s1.ax1x.com/2022/07/28/v9jeMD.png)
                                [<img src="https://s1.ax1x.com/2022/07/28/v9jeMD.png" alt="v9jeMD.png" style="zoom: 67%;" />](https://imgtu.com/i/v9jeMD)

  [操作后的文件目录：](https://s1.ax1x.com/2022/07/28/v9jGz8.png)
                                      [<img src="https://s1.ax1x.com/2022/07/28/v9jGz8.png" alt="v9jGz8.png" style="zoom:50%;" />](https://imgtu.com/i/v9jGz8)

- Mapper接口中自动生成基础增删改查功能

  ~~~java
  public interface EmpMapper {
      int deleteByPrimaryKey(Integer eid);
  
      int insert(Emp record);
  
      Emp selectByPrimaryKey(Integer eid);
  
      List<Emp> selectAll();
  
      int updateByPrimaryKey(Emp record);
  }
  ~~~

- Mapper映射文件中自动生成相对应方法的配置信息

  ~~~xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
  <mapper namespace="com.atguigu.mybatis.mapper.EmpMapper" >
      <resultMap id="BaseResultMap" type="com.atguigu.mybatis.pojo.Emp" >
          <!--
        WARNING - @mbggenerated
        This element is automatically generated by MyBatis Generator, do not modify.
        This element was generated on Wed Mar 02 16:05:18 CST 2022.
      -->
          <id column="eid" property="eid" jdbcType="INTEGER" />
          <result column="emp_name" property="empName" jdbcType="VARCHAR" />
          <result column="age" property="age" jdbcType="INTEGER" />
          <result column="sex" property="sex" jdbcType="CHAR" />
          <result column="email" property="email" jdbcType="VARCHAR" />
          <result column="did" property="did" jdbcType="INTEGER" />
      </resultMap>
      <delete id="deleteByPrimaryKey" parameterType="java.lang.Integer" >
          <!--
        WARNING - @mbggenerated
        This element is automatically generated by MyBatis Generator, do not modify.
        This element was generated on Wed Mar 02 16:05:18 CST 2022.
      -->
          delete from t_emp
          where eid = #{eid,jdbcType=INTEGER}
      </delete>
      <insert id="insert" parameterType="com.atguigu.mybatis.pojo.Emp" >
          <!--
        WARNING - @mbggenerated
        This element is automatically generated by MyBatis Generator, do not modify.
        This element was generated on Wed Mar 02 16:05:18 CST 2022.
      -->
          insert into t_emp (eid, emp_name, age, 
          sex, email, did)
          values (#{eid,jdbcType=INTEGER}, #{empName,jdbcType=VARCHAR}, #{age,jdbcType=INTEGER}, 
          #{sex,jdbcType=CHAR}, #{email,jdbcType=VARCHAR}, #{did,jdbcType=INTEGER})
      </insert>
      <update id="updateByPrimaryKey" parameterType="com.atguigu.mybatis.pojo.Emp" >
          <!--
        WARNING - @mbggenerated
        This element is automatically generated by MyBatis Generator, do not modify.
        This element was generated on Wed Mar 02 16:05:18 CST 2022.
      -->
          update t_emp
          set emp_name = #{empName,jdbcType=VARCHAR},
          age = #{age,jdbcType=INTEGER},
          sex = #{sex,jdbcType=CHAR},
          email = #{email,jdbcType=VARCHAR},
          did = #{did,jdbcType=INTEGER}
          where eid = #{eid,jdbcType=INTEGER}
      </update>
      <select id="selectByPrimaryKey" resultMap="BaseResultMap" parameterType="java.lang.Integer" >
          <!--
        WARNING - @mbggenerated
        This element is automatically generated by MyBatis Generator, do not modify.
        This element was generated on Wed Mar 02 16:05:18 CST 2022.
      -->
          select eid, emp_name, age, sex, email, did
          from t_emp
          where eid = #{eid,jdbcType=INTEGER}
      </select>
      <select id="selectAll" resultMap="BaseResultMap" >
          <!--
        WARNING - @mbggenerated
        This element is automatically generated by MyBatis Generator, do not modify.
        This element was generated on Wed Mar 02 16:05:18 CST 2022.
      -->
          select eid, emp_name, age, sex, email, did
          from t_emp
      </select>
  </mapper>
  ~~~

## 2. 创建逆向工程MyBatis3(多功能)版本

- 更改版本generatorConfig.xml
  [修改配置文件版本：](https://s1.ax1x.com/2022/07/28/v9vFmQ.png)
                              [<img src="https://s1.ax1x.com/2022/07/28/v9vFmQ.png" alt="v9vFmQ.png" style="zoom:50%;" />](https://imgtu.com/i/v9vFmQ)

- 自动生成的Mapper接口中的方法

  ~~~java
  public interface EmpMapper {
      // 根据条件计数
      int countByExample(EmpExample example);
  
      //根据条件删除
      int deleteByExample(EmpExample example);
      //根据主键删除
      int deleteByPrimaryKey(Integer eid);
  
      //普通插入
      int insert(Emp record);
      //选择性插入：没写的就是null
      int insertSelective(Emp record);
  
      //根据条件查询
      List<Emp> selectByExample(EmpExample example);
      //根据主键查询
      Emp selectByPrimaryKey(Integer eid);
  
      //根据条件选择性修改：
      int updateByExampleSelective(@Param("record") Emp record, @Param("example") EmpExample example);
      //根据条件修改
      int updateByExample(@Param("record") Emp record, @Param("example") EmpExample example);
      //根据主键选择性修改
      int updateByPrimaryKeySelective(Emp record);
      //根据主键修改
      int updateByPrimaryKey(Emp record);
  }
  ~~~

  > 选择性修改指的是如果某个字段为NULL，则不修改此字段。

### 2.1 测试方法自动查询方法

> 如果报错Cannot find class: com.mysql.jdbc.Driver
>
> 解决方法：
>
> 1. 检查jdbc.properties中driver最后会不会多写了一个空格
> 2. 检查引用格式会不会出错，把${jdbc.driver}改成普通的”com.mysql.jdbc.Driver"
> 3. 最后发现是pom.xml里面配置错了，没加sql依赖。注意看清楚一个是给项目加的，一个是给插件加的，pom.xml里有两个配置sql的地方。
>
> 给Emp和Dept 的pojo重写toString()，再加一个空参构造器、一个有参构造器，然后就可以开始测试了。

测试代码汇总：

~~~java
@Test
public void test(){
    try {
        InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
        SqlSession sqlSession = sqlSessionFactory.openSession();
        EmpMapper mapper = sqlSession.getMapper(EmpMapper.class);

        //查询所有数据
        System.out.println("\n--------->查询所有数据");
        List<Emp> emps = mapper.selectByExample(null); // 没有查询条件就相当于查询所有数据
        emps.forEach(emp -> System.out.println(emp));

        //根据条件查询 QBC: Query by Criteria
        EmpExample example = new EmpExample();

        //名字叫Bela的
        System.out.println("\n--------->根据条件查询");
        example.createCriteria().andEmpNameEqualTo("Bela");
        List<Emp> emps1 = mapper.selectByExample(example);
        emps1.forEach(emp -> System.out.println(emp));

        //链式添加条件
        System.out.println("\n--------->链式添加条件");
        example.createCriteria().andEmpNameEqualTo("Bela").andAgeEqualTo(33);
        List<Emp> emps2 = mapper.selectByExample(example);
        emps2.forEach(emp -> System.out.println(emp));

        //两个条件用or连接
        System.out.println("\n--------->两个条件用or连接");
        example.createCriteria().andAgeLessThan(30);
        example.or().andDidIsNotNull();
        List<Emp> emps3 = mapper.selectByExample(example);
        emps3.forEach(emp -> System.out.println(emp));
    } catch (IOException e) {
        e.printStackTrace();
    }
}
~~~

- 查询所有数据
  对应sql语句为：

  ~~~sql
  seLect eid emp_name,age,sex,email,did from t_emp 
  ~~~

  运行结果：
  [查询所有数据：](https://s1.ax1x.com/2022/07/28/v9x02V.png)

  ​                          [<img src="https://s1.ax1x.com/2022/07/28/v9x02V.png" alt="v9x02V.png" style="zoom:50%;" />](https://imgtu.com/i/v9x02V)   

- 根据条件查询

  对应sql语句：

  ~~~sql
  seLect eid, emp_name,age,sex,email, did from t_emp WHERE (emp_name='Bela')
  ~~~

  运行结果：

  ~~~shell
  Emp{eid=2,empName='Bela',age=33,sex='女',email= '123@gmail.com',did=1}
  ~~~

- 链式添加条件
  对应sql语句：

  ~~~sql
  seLect eid, emp_name,age,sex,email, did from t_emp WHERE (emp_name='Bela') AND (age=33)
  ~~~

  查询结果：

  ~~~shell
  Emp{eid=2，empName='BeLa',age=33,sex='女',email='123@gmail.com',did=1}
  ~~~

- 两个条件用or连接
  对应sql语句

  ~~~sql
  seLect eid, emp_name,age,sex,email, did from t_emp WHERE (emp_name='Bela') OR did is not null
  ~~~

  查询结果：

  ~~~shell
  Emp{eid=1, empName= 'AppLe', age=22， sex='女' , email= '123@gmail.com', did=1}
  Emp{eid=2，empName='BeLa', age=33, sex='女'， email=' 123@gmail.com', did=1}
  Emp{eid=3, empName= 'Cherry', age=21, sex='女'， email=' 123@gmail.com' , did=2}
  Emp{eid=4, empName= 'David', age=55, sex='男'， email='123@gmail. com', did=2}
  Emp{eid=5，empName='Eve', age=24, sex='男'， email= '123@gmail. com'did=3}
  Emp{eid=6，empName= 'Feman', age=31, sex='男'， email=' 123@gmail.com', did=3}
  ~~~

### 2.2 测试修改方法

添加代码汇总：

~~~java
@Test
public void test2(){
    try {
        InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
        SqlSession sqlSession = sqlSessionFactory.openSession();
        EmpMapper mapper = sqlSession.getMapper(EmpMapper.class);

        // 根据主键修改
        mapper.updateByPrimaryKey(new Emp(2,"改1",55,"男","6789@gamil.com",null));
        System.out.println("\n-----> 根据主键修改----->" + mapper.selectByPrimaryKey(1));

        // 根据主键选择性修改
        mapper.updateByPrimaryKeySelective(new Emp(2,"改2",55,null,"6789@gamil.com",null));
        System.out.println("\n-----> 根据主键选择性修改----->" + mapper.selectByPrimaryKey(1));

    } catch (IOException e) {
        e.printStackTrace();
    }
}
~~~

[修改方法运行结果：](https://s1.ax1x.com/2022/07/28/vCCDHS.png)
                          [<img src="https://s1.ax1x.com/2022/07/28/vCCDHS.png" alt="vCCDHS.png" style="zoom: 33%;" />](https://imgtu.com/i/vCCDHS)

# 十一. 分页插件的使用

> 实现原理：
>
> - index：当前页的起始索引
> - pagesize：每页显示的条数
> - pageNum：当前页的页码
> - index= (pageNum 1) *pagesize

[分页插件目的：](https://s1.ax1x.com/2022/07/28/vC9aeU.png)

​                            [<img src="https://s1.ax1x.com/2022/07/28/vC9aeU.png" alt="vC9aeU.png" style="zoom:50%;" />](https://imgtu.com/i/vC9aeU)

## 1. 分页插件的配置

- 在pom.xml中添加依赖

  ~~~xml
  <!-- https://mvnrepository.com/artifact/com.github.pagehelper/pagehelper -->
  <dependency>
      <groupId>com.github.pagehelper</groupId>
      <artifactId>pagehelper</artifactId>
      <version>5.2.0</version>
  </dependency>
  ~~~

- 在MyBatis的核心配置文件中配置插件

  ~~~xml
  <plugins>
      <!--设置分页插件-->
      <plugin interceptor="com.github.pagehelper.PageInterceptor"></plugin>
  </plugins>
  ~~~

## 2. 分页插件的使用

[分页插件的使用：](https://s1.ax1x.com/2022/07/28/vCkrMn.png)

​                    [<img src="https://s1.ax1x.com/2022/07/28/vCkrMn.png" alt="vCkrMn.png" style="zoom:50%;" />](https://imgtu.com/i/vCkrMn)

[分页插件的使用：](https://s1.ax1x.com/2022/07/28/vCk2IU.png)

​                    [<img src="https://s1.ax1x.com/2022/07/28/vCk2IU.png" alt="vCk2IU.png" style="zoom: 50%;" />](https://imgtu.com/i/vCk2IU)

- 在查询功能之前使用PageHelper.startPage(int pageNum, int pageSize)开启分页功能

  |  属性名  |      描述      |
  | :------: | :------------: |
  | pageNum  |  当前页的页码  |
  | pageSize | 每页显示的条数 |

- 在查询获取list集合之后，使用PageInfo pageInfo = new PageInfo<>(List list, int navigatePages)获取分页相关数据

  |    属性名     |                描述                |
  | :-----------: | :--------------------------------: |
  |     list      |           分页之后的数据           |
  | navigatePages | 展示导航分页的总页码数，一般为奇数 |

- 分页相关数据

  |           属性名            |            描述             |
  | :-------------------------: | :-------------------------: |
  |           pageNum           |        当前页的页码         |
  |          pageSize           |       每页显示的条数        |
  |            size             |    当前页显示的真实条数     |
  |            total            |          总记录数           |
  |            pages            |           总页数            |
  |           prePage           |        上一页的页码         |
  |          nextPage           |        下一页的页码         |
  |   isFirstPage/isLastPage    |    是否为第一页/最后一页    |
  | hasPreviousPage/hasNextPage |    是否存在上一页/下一页    |
  |        navigatePages        |      导航分页的页码数       |
  |      navigatepageNums       | 导航分页的页码，[1,2,3,4,5] |

- 测试代码

  ~~~java
  /**
       * 通过索引获得数据
       *
       * 使用MyBatis的分页插件，实现分页功能：
       * 1。需要在查询功能之前开启分页
       * PageHelper.startPage(2, 4);
       * 
       * 2。在查询功能之后获取分页相关信息
       *   PageInfo<Emp> pages = new PageInfo<>(emps, 5); 5表示导航分页的数量
       */
  @Test
  public void test2(){
      try {
          InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
          SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
          SqlSession sqlSession = sqlSessionFactory.openSession();
          EmpMapper mapper = sqlSession.getMapper(EmpMapper.class);
  
          System.out.println("\n查询功能前开启分页");
          PageHelper.startPage(2, 4);
          List<Emp> emps = mapper.selectByExample(null);
          emps.forEach(emp -> System.out.println(emp));
  
          System.out.println("\n");
          PageInfo<Emp> pages = new PageInfo<>(emps, 5);
          System.out.println("PageInfo----->"+pages);
      } catch (IOException e) {
          e.printStackTrace();
      }
  }
  ~~~

  

