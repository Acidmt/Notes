# Java web技术

> JavaWeb是指，所有通过**Java语言编写可以通过浏览器访问的程序**的总称，叫JavaWeb。
> JavaWeb是基于请求和响应来开发的。

[请求响应关系图：](https://s4.ax1x.com/2022/02/24/bixJ1I.png)

​							[<img src="https://s4.ax1x.com/2022/02/24/bixJ1I.png" alt="bixJ1I.png" style="zoom:50%;" />](https://imgtu.com/i/bixJ1I)

[toc]

## 一. XML

> xml是可扩展的标记性语言，其作用**主要用于保存数据**，也可以**用于项目或者模块的配置文件**，**还可以作为网络传输数据的格式**(现在主要以JSON为主)。

### 1. xml的文档声明

> 与HTML一样，编写xml文件的时候需要在第一行进行声明。

声明格式：

~~~xml
<?xml version='1.0' encoding='UFT-8' ?>
~~~

> version="1.0"				version表示xmL 的版本
> encoding= "utf-8"		encoding表示xmL文件本身的编码

### 2. xml的标签(元素)

#### 2.1 标签的命名规范

> XML元素指的是从(且包括)开始标签直到( 且包括)结束标签的部分。元素可包含其他元素、文本或者两者的混合物。元素也可以拥有属性。

[XML示例：](https://s4.ax1x.com/2022/02/21/HvcJdP.png)

​				[<img src="https://s4.ax1x.com/2022/02/21/HvcJdP.png" alt="HvcJdP.png" style="zoom: 67%;" />](https://imgtu.com/i/HvcJdP)

> XML 元素必须遵循以下命名规则：
>
> - 名称可以含字母、数字以及其他的字符
> - 名称不能以数字或者标点符号开始
> - 名称不能包含空格

#### 2.2 单标签和双标签

> 单标签只要在`>`前加上`/`即可

~~~xml
<books>
    <book sn='SN132'>
        <name>自传</name>
        <author>张三</author>
        <price>80</price>
    </book>
    <book sn='SN13424' name='自传' author='张三' price='80'/>
</books>
~~~

> 上面的代码中两个`<book>`标签表示的功能一样。

#### 2.3 XMl的内部属性

> 标签内部也可以**包含属性和值**
>
> 在标签上可以书写属性:
>
> - 一个标签上可以书写多个属性。每个属性的值必须使用引号引起来。
> - 与HTML的规则和标签的书写规则一致。

#### 2.4 XML根元素

> XML必须要有根元素。
>
> 根元素就是顶级元素，没有父标签的元素,叫顶级元素，与HTML中的跟标签`html`类似。

### 3. 文本区域(CDATA区)

> CDATA语法可以告诉xml解析器，CDATA里的文本内容，只是纯文本，不需要xml语法解析。
>
> 常用于大量符号(>,<[]等)要被转译为文本

~~~xml
<![CDATA[>,<<<<<>>>>>]>
~~~

### 4. ==XML的解析(未完成)==

> 可以使用w3c组织制定的dom技术来解析。其解析结构与HTML的DOM类似。
>
> document对象表示的是整个文档(可以是html文档，也可以是xml文档)

[DOM结构：](https://s4.ax1x.com/2022/02/21/HvWdkq.png)

​					[<img src="https://s4.ax1x.com/2022/02/21/HvWdkq.png" alt="HvWdkq.png" style="zoom:67%;" />](https://imgtu.com/i/HvWdkq)

#### 4.1 DOM4j解析技术

> 需要进入[DOM4j官网](https://dom4j.github.io/)下载压缩包。下载之后解压

获取document步骤：

- 将解压以后目录下的jar包复制到项目文件夹`lib`下

  [复制后选中jar包右键点击选中部分：](https://s4.ax1x.com/2022/02/21/HvhJds.png)

​									[<img src="https://s4.ax1x.com/2022/02/21/HvhJds.png" alt="HvhJds.png" style="zoom: 50%;" />](https://imgtu.com/i/HvhJds)

- 

### 5. DTD约束

>  DTD(Document Type Definition)文档类型定义，用来约束xml文档。规定xml文档中元素的名称，子元素的名称及顺序，元素的属性等等。

#### 5.1 DTD引入

- 引入本地DTD文件

  ~~~xml
  <!DOCTYPE 根元素名称 SYSTEM '外部DTD文件的URL'>
  ~~~

  > 外部DTD文件的URL：本地DTD文件存放的位置

- 引入公共的DTD文件

  ~~~xml
  <!DOCTYPE 根元素名称 PUBLIC 'DTD名称' '外部DTD文件的URL'>
  ~~~

  > DTD名称：这里的名称由开发者提供，应用这直接复制即可

- 内嵌式

  > 内嵌式定义在声明之下

  ~~~xml
  <?xml version='1.0' encoding='UFT-8' ?>
  <!DOCTYPE 根元素名称[
  	DTD定义语句
  ]>
  ~~~

#### 5.2 DTD约束语法

> 元素是xml文档中不可缺少的一部分，在DTD定义的每一条<!ELEMENT...>语句用于定义一个元素，基本格式如下：

~~~xml
<!ELEMENT 元素名称 元素内容>
~~~

> 元素名称：被约束的xml文档中的元素
>
> 元素内容：包含数据类型和符号两个部分

元素内容的七种表现形式：

- 如果元素中的内容是纯文本的内容，使用**#PCDATA**定义：

  ~~~xml
  <!ELEMENT name #PCDATA>
  ~~~

- 在XML中元素中可以有子元素，我们可以通过DTD来定义某个元素中可以包含哪些子元素，为了顶一个元素中可以包含哪些子元素，我们只需将子元素名写在父元素后边的`()`中。例如如果一个students标签中只允许有一个student元素，则定义如下：

  ~~~xml
  <!ELEMENT students (student)>
  ~~~

- 事实上在students元素中是可以出现多个student的，只需要在`()`后边多加一个`*`，如下：

  ~~~xml
  <!ELEMENT students (student)*>
  ~~~

  > 还可以使用其他符合?表示一次或零次，+表示一次或多次，*表示零次或多次。

- 在student标签中可以有name、age、gender、address，则可以在()中编写都给元素名，使用,分割。使用`,`分割代表子元素必须按照这样的顺序出现，即age必须在name后，gender必须在age后，address必须在gender后。如下：

  ~~~xml
  <!ELEMENT student (name , age , gender , address)>
  ~~~

- 如果不要求子元素的顺序可以使用`|`分割子标签：

  ~~~xml
  <!ELEMENT student (name|age|gender|address)>
  ~~~

- 如果元素仅仅是一个空元素，也称为自结束标签我们可以使用**EMPTY**来定义：

  ~~~xml
  <!ELEMENT br EMPTY>
  ~~~

- **ANY**表示在元素中可以定义任意内容：

  ~~~xml
  <!ELEMENT test ANY>
  ~~~

元素内容包含符号一览：

| 符号 |            作用             |
| :--: | :-------------------------: |
|  ？  | 表示该对象可以出现0次或1次  |
|  *   | 表示该对象可以出现0次或多次 |
|  +   | 表示该对象可以出现1次或多次 |
|  \|  | 表示在列出的对象中选择一个  |
|  ，  | 表示对象必须按照指定的出现  |
| （） |     用于对元素进行分组      |

#### 5.3 DTD属性定义

> 在DTD文档中，在定义元素的同时，还可以为元素定义属性，DTD属性定义的基本语法格式如下：

~~~xml
<!ATTLIST 元素名
	属性名1 属性类型 设置说明
	属性名2 属性类型 设置说明
	......
>
~~~

> 元素名：	属性所属元素的名字
>
> 属性名：	属性的名称
>
> 属性类型：用于指定该属性属于哪种类型
>
> 设置说明：用于说明该属性是否必须出现

- 定义元素的时候有四种说明可进行选择

  | 设置说明  |                             含义                             |
  | :-------: | :----------------------------------------------------------: |
  | #REQUIRED |                  表示该元素的属性值是必须的                  |
  | #IMPLIED  |          表示元素可以包含该属性，也可以不包含该属性          |
  |  #FIXED   | 表示一个固定的属性默认值，设置后，如果用户不为该元素设置值，则为默认值。默认值设置后不可修改 |
  |  默认值   |      与`FIXED`一样，不同的是，该默认值会被新的值覆盖。       |
  
- 属性类型：在DTD定义元素属性时，有十种属性类型可以选择，在此介绍常用的

  1. CDATA表明属性的类型是字符数据，元素内容说明中的`#PCDATA`相同。

  2. 枚举类型(Enumerated)。在声明属性是，可以限制属性值只能从给出的列表中选择。

     ~~~xml
     <?xml version='1.0' encoding='UFT-8' ?>
     <!DOCTYPE 购物篮[
     	<!ELEMENT 购物篮 ANY>
     	<!ELEMENT 肉 EMPTY>
     	<!ATTLIST 肉 品种 (牛肉|鸡肉|鱼肉) '鸡肉'>
     ]>
     <购物篮>
     	<肉 品种='鱼肉'/>    
     	<肉 品种='牛肉'/>    
     	<肉 />    
     </购物篮>
     ~~~

     > 其中`(牛肉|鸡肉|鱼肉)`就是Enumerated。默认值是"鸡肉"。所以最后一次的`<肉 /> `,等同于`<肉 品种='鸡肉'/>`

  3. ID。一个ID用于标识唯一元素，而且ID属性类型必须设置为`#IMPLIED`和`#REQUIRED`。

     ==注意：对ID类型设置默认值毫无意义==

     ~~~xml
     <?xml version='1.0' encoding='UFT-8' ?>
     <!DOCTYPE 联系人列表[
     	<!ELEMENT 联系人列表 ANY>
     	<!ELEMENT 联系人 (姓名,EMAIL)>
     	<!ELEMENT 姓名 (#PCDATA)>
     	<!ELEMENT EMAIL (#PCDATA)>
     	<!ATTLIST 联系人 编号 ID #REQUIRED>
     ]>
     <联系人列表>
         <联系人 编号='ID1'>
             <姓名>张三</姓名>    
             <EMAIL>zahng@163.com</EMAIL>    
         </联系人>   
         <联系人 编号='ID2'>
             <姓名>李四</姓名>    
             <EMAIL>lisi@163.com</EMAIL>    
         </联系人> 
     </联系人列表>
     ~~~
  
  4. IDREF和IDREFS。在上面的代码中张三和李四没有任何关联。如果想要建立起联系就可以用到`IDREF`类型，**该类型属性值必须为一个已存在的ID值，这样才能将两个元素建立一对一的关联。**
  
     ~~~xml
     <?xml version='1.0' encoding='UFT-8' ?>
     <!DOCTYPE 联系人列表[
     	<!ELEMENT 联系人列表 ANY>
     	<!ELEMENT 联系人 (姓名,EMAIL)>
     	<!ELEMENT 姓名 (#PCDATA)>
     	<!ELEMENT EMAIL (#PCDATA)>
     	<!ATTLIST 联系人 
     				编号 ID #REQUIRED
     				上司 IDREF #IMPLIED>
     ]>
     <联系人列表>
         <联系人 编号='ID1'>
             <姓名>张三</姓名>    
             <EMAIL>zahng@163.com</EMAIL>    
         </联系人>   
         <联系人 编号='ID2' 上司='ID1'>					<!--张三的上司是李四-->
             <姓名>李四</姓名>    
             <EMAIL>lisi@163.com</EMAIL>    
         </联系人> 
     </联系人列表>
     ~~~
  
     > 如果对应关系为一对多时，可以使用`IDREFS`。
  
     ~~~xml
     <!ATTLIST 联系人 
     				编号 ID #REQUIRED
     				上司 IDREFS #IMPLIED>
     ]>
     
     <联系人 编号='ID2' 上司='ID1 ID2 ID3'>
     ~~~
### 6. Schema约束

> 同DTD一样，XML Schema也是一种用于定义文档结构内容模式的语言，其出现是为了克服 DTD 的局限性。

DTD与Schema的不同：

> XML Schema符合XML语法结构。 
> DOM、SAX等XML API很容易解析出XML Schema文档中的内容。 
> XML Schema对名称空间支持得非常好。 
> XML Schema比XML DTD支持更多的数据类型，并支持用户自定义新的数据类型。 
> XML Schema定义约束的能力非常强大，可以对XML实例文档作出细致的语义限制。
> XML Schema不能像DTD一样定义实体，比DTD更复杂，但Xml Schema现在已是w3c组织的标准，它正逐步取代DTD。  

#### 6.1 名称空间

> 一个xml文档可以引用多个约束文档，但文档中极有可能出现代表不同含义的同名元素或属性，导致名称发生冲突。为此名称空间诞生了，他可以唯一标识一个元素或者属性。
>
> 在使用名称空间时需要声明，格式如以下：

~~~xml
<元素名 xmlns:prefixname='URL'>
~~~

> 元素名：指在哪一个元素上声明名称空间。在这个元素上声明的名称空间适用于声明它的所有元素和属性，

#### 6.2 Schema约束文件引入

- 使用名称空间一如Schema文档

  > 在使用名称空间引入XML Schema文档时，需要通过属性 sischemaLocation来声明名称空间的文档.
  >
  > xsisechemalorcation属性是在标准名称空间“http://www.w3.ng/2001/XMLSchema-instance”中定义的，在该属性中包含了两个URI，这两个URI之间用空白符分隔。
  >
  > 其中，第一个URI是名称空间的名称，第二个URI是文档的位置。

  ~~~xml
  <?xml version="1.1" encoding="UTF-8"?>
  <书架 xmlns="http://www.it315.org/xmlbook/schema"
  		xmlns:xsi="http://www.w3.org/2001/XMLScheema-instance"
  		xsi:schemaLocation="http://www.it315.org/xmlbook/schema
  							http://www.it315.or/xmlbook.xsd">
  	<书>
  		<书名>Java基础案例教程</书名>
  		<作者>黑马程序员</作者>
  		<售价>54.00元</售价>
  	</书>
  </书架>
  ~~~

  > schemaLocation：属性用于指定名称空间所对应Schema文档的位置
  >
  > xmlns:xsi="URL"：因为schemaLocation属性是在另一个标准的名称空间种定义的，所以在使用该属性时，必须声明该属性的名								 称空间。
  >
  > 需要注意的是，一个XML实例文档可能引用多个名称空间，这时可以在schemalocation属性值中包含多个名称空间与它们所对应的XMLSchema文档的存储位置，每一个名称空间的设置信息之间采用空格分隔 。

  ~~~xml
  <?xml version="1.1" encoding="UTF-8"?>
  <书架 xmlns="http://www.it315.org/xmlbook/schema"
  		xmlns:demo="http://www.it315.org/demo/schema"
  		xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     		xsi:schemaLocation="http://www.it315.org/xmlbook/schema		
                              http://www.it315.org/xmlbook.xsd		
                              http://www.it315.org/demo/schema	
                              http://www.it315.org/demo.xsd">		
  	<书>
  		<书名>Java 基础案例教程</书名>
  		<作者>黑马程序员</作者>
  		<售价 demo:币种="人民币">54.00元</售价>
  	</书>
  </书架>
  ~~~


- 通过xsi:noNamespaceSchemalocation属性直接指定

  > 在XML文档中引入XML Schema文档，还可以通过`xsi:noNamespaceSchemaLocation`属性直接指定。`xsi:noNamespaceSchemaLocation`属性也是在标准名称空间“http://www.w3.org/2001/XMLSchema-instance”中定义的，它用于定义指定文档的位置。

  ~~~xml
  <?xml version="1.1" encoding="UTF-8"?>
  <书架 xmlns:xsi="http://www.w3.org/2001/XMLScheema-instance"
  		xsi:noNamespaceSchemalocation="xmlbook.xsd">
  	<书>
  		<书名>Java基础案例教程</书名>
  		<作者>黑马程序员</作者>
  		<售价>54.00元</售价>
  	</书>
  </书架>
  ~~~

#### 6.3 Schema语法

##### (1). 元素定义

> Schema与DTD一样，可以定义xml文档中的元素。

定义格式：

~~~xml
<xs:element name='名称' type='类型'/>
~~~

> element：用于声明一个元素。
>
> 名称：		是指元素的名称。
>
> 类型：		是指元素的类型。

在Schema种有很多内置的数据类型，常用的有以下几种：

|  数据类型   |      说明      |
| :---------: | :------------: |
|  xs:string  | 表示字符串类型 |
| xs:decimal  |  表示小数类型  |
| xs:integer  |  表示整数类型  |
| xs:boolenan |  表示布尔类型  |
|   xs:date   |  表示日期类型  |
|   xs:time   |  表示时间类型  |

示例：

~~~xml
<xs:element name="lastname" type="xs:string"/>
<xs:element name="age" type="xs:integer"/>
<xs:element name="dateborn" type='xs:date'/>
<!--对应的xml约束代码如下-->
<lastname>Smith</lastname>
<age>28</age>
<dateborn>1980-03-27</dateborn>
~~~

##### (2). 属性的定义

> 在Schema文档种，属性的定义方法如下：

~~~xml
<xs:attribute name='xxx' type='yyy'>
~~~

> name：是指属性的名称
>
> type：  是指属性的数据类型

示例：

~~~xml
<xs:element name="lastname" type="xs:string"/>
<xs:attribute name='lang' type='xs:string'/>
<!--对应的xml约束代码如下-->
<lastname lang='EN'>smith</lastname>
~~~

##### (3). 简单类型

> 在Schema中，只包含字符数据的元素都是简单类型。使用`xs:simpleType`元素来定义。如果想对现有的元素内容的类型进行限制，则需要使用`xs:restriction`元素。

下面介绍如何对简单类型元素的内容进行限定：

- `xs:minInclusive`和`xs:maxInclusive`

  > 可以限定元素的取值范围等

  ~~~xml
  <xs:element name='age'>
  <xs:simpleType>
      <xs:restriction base='xs:integer'>
      	<xs:minInclusive value='18'/> 		<!--将年龄限制在18~60之间-->
      	<xs:maxInclusive value='60'/> 
      </xs:restriction>	   	
  </xs:simpleType>
  </xs:element>
  ~~~

- `xs:enumeration`

  > 将元素的内容限制为一组可接受的值。

  示例：

  ~~~xml
  <xs:element name='car'>
  <xs:simpleType>
      <xs:restriction base='xs:integer'>
      	<xs:enumeration value='A'/> 		<!--car的值只能为A和B中-->
      	<xs:enumeration value='B'/> 
      </xs:restriction>	   	
  </xs:simpleType>
  </xs:element>
  ~~~

- `xs:pattern`

  > 如果希望把xml元素的内容限制为一些列可使用的数字或者字母，可以使用该属性

  示例：

  ~~~xml
  <xs:element name='letter'>
  <xs:simpleType>
      <xs:restriction base='xs:integer'>
      	<xs:pattern value='[a-z]'/> 		<!--letter的值只能为a~z之间-->
      </xs:restriction>	   	
  </xs:simpleType>
  </xs:element>
  ~~~

- `xs:whiteSpace`

  > 该属性可以对空白字符进行处理。值`replace`表示移除所有的空白字符、`collapse`表示将所有的空白字符缩减为单一字符。
  >
  > `preserve`表示不对空白字符进行任何处理。

  示例：

  ~~~xml
  <xs:element name='address'>
  <xs:simpleType>
      <xs:restriction base='xs:integer'>
      	<xs:whiteSpace value='preserve'/> 	<!--xml处理器不会对address值中的空格进行处理-->
      </xs:restriction>	   	
  </xs:simpleType>
  </xs:element>
  ~~~


##### (4). 复杂类型(复合元素)

> 在定义复杂类型时，需要用到`xs:complexType`其可接受如下两种子元素：
>
> 1. `xs:simpleContent`	用于定义*包含简单内容的复杂类型*。
> 2. `xs:complexContext`用于定义*包含复杂内容的复杂类型*

复合类型有四种基本类型：

- 空元素。指不包含内容，只包含属性的元素

  ~~~xml
  <xs:element name='product'>
  <xs:complexType>
      <xs:attribute name='prodid' type='xs:positiveInteger'/>	 <!--positiveInteger正整数类型--> 	
  </xs:complexType>
  </xs:element>
  <!--对应的xml约束代码如下-->
  <product prodid='10'/>
  ~~~

- 元素中包含其他元素的

  > 要使用`sequence`元素要求组中的元素以指定的顺序出现在包含元素中。每个子元素可出现 0 次到任意次数。

  ~~~xml
  <xs:element name="person">
  	<xs:complexType>
  		<xs:sequence>
  			<xs:element name="firstname" type="xs:string"/>
  			<xs:element name="lastname" type="xs:string"/>
  		</xs;sequence>
      </xs:complexType>
  </xs:element>
  <!--对应的xml约束代码如下-->
  <person>
  	<firstname>Johnk</firstname>
  	<lastname>Smith</lastname>
  </person>
  ~~~

- 仅包含文本的元素

  > 对于仅包含文本的复合元素，需要使用`smpleContnt`元素添加内容。在使用简易内容时，必须在smpleContnt元素内定义扩展或限定。这时需要使用`extension`或`testiction`元素来扩展或限制元素的基本简易类型。

  ~~~xml
  <xs:element name="shoesize">
  	<xs:complexType>
  		<xs:simpleContent>
  			<xs:extension base="xs:integer">
  				<xs:attribute name="country" type="xs:string">
  			</xs:extension>
  		</xs:simpleContent>
  	</xs:complexType>
  </xs:element>
  <!--对应的xml约束代码如下-->
  <shoesize country="france">35</shoesize>
  ~~~

- 包含元素和文本的元素

  > 在XML文档中，某些元素经常需要包含文本以及其他元素。

  例如：

  ~~~xml
  <letter>
  Dear Mr.<name>John Smith</name>.
  Your order <orderid>1032</orderid>
  will be shipped on <shipdate>2001-07-13</shipdate>.
  </letter>
  ~~~

  上述这段XML文档在Schema文档中对应的定义方式如下：

  ~~~xml
  <xs:element name="letter"
  	<xs:complexType mixed="true">
  		<xs:sequence>
  			<xs:element name="name" type="xs:string"/>
  				<xs:elementname="orderid"type="xs:positiveInteger"/>
  			<xs:element name="shipdate"type="xs:date"/>
  		</xs:sequence>
  	</xs:complexType>
  </xs:element>
  ~~~

  > 需要注意的是，为了使字符数据可以出现在letter元素的子元素之间，使用了`mixed`属性。该属性用于规定是否允许字符数据出现在复杂类型的子元素之间，默认情况下`mixed`的值为false。

## 二. Tomcat服务器

> web资源按实现的技术和呈现的效果的不同，又分为静态资源和动态资源两种。
>
> 1. 静态资源：html、Css、 js、 txt、 mp4视频， jpg图片等
> 2. 动态资源：jsp页面、Servlet 程序等
>
> Tomcat是现在市面上流行的服务器。

### 1. Tomcat安装

下载后解压，然后配置环境：

- [配置JAVA_HOME环境：](https://s4.ax1x.com/2022/02/24/bF9lrt.png)

  > 变量值为jdk安装目录

​												[<img src="https://s4.ax1x.com/2022/02/24/bF9lrt.png" alt="bF9lrt.png" style="zoom: 50%;" />](https://imgtu.com/i/bF9lrt)

- 配置好环境变量后就可以直接在`bin`目录中点击`startup.bat`启动服务器。

  [启动成功如下所示：](https://s4.ax1x.com/2022/02/24/bFCQW4.png)

​										[<img src="https://s4.ax1x.com/2022/02/24/bFCQW4.png" alt="bFCQW4.png" style="zoom: 50%;" />](https://imgtu.com/i/bFCQW4)

之后通过浏览器输入：http://localhost:8080访问成功即可完成。

### 2. Tomcat目录介绍

- bin目录

  > 主要是用来存放tomcat的命令，主要有两大类，一类是以.sh结尾的（linux命令），另一类是以.bat结尾的（windows命令）。
  >
  > 很多环境变量的设置都在此处，例如可以设置JDK路径、tomcat路径。
  >
  > **startup 用来启动tomcat**，**shutdown 用来关闭tomcat**。修改catalina可以设置tomcat的内存

- conf目录

  > 主要是用来存放tomcat的一些配置文件。
  >
  > server.xml**可以设置端口号、设置域名或IP、默认加载的项目、请求编码**。
  >
  > web.xml可以设置tomcat支持的文件类型。
  >
  > context.xml可以用来配置数据源之类的。
  >
  > tomcat-users.xml用来配置管理tomcat的用户与权限。
  >
  > 在Catalina目录下可以设置默认加载的项目

- lib目录

  > lib目录主要用来存放tomcat运行需要加载的jar包。
  >
  > 例如，像连接数据库的jdbc的包我们可以加入到lib目录中来。

- logs目录

  > logs目录用来存放tomcat在运行过程中产生的日志文件，非常重要的是在控制台输出的日志。
  >
  > 在windows环境中，控制台的输出日志在catalina.xxxx-xx-xx.log文件中。
  > 在linux环境中，控制台的输出日志在catalina.out文件中。

- temp目录

  > temp目录用户存放tomcat在运行过程中产生的临时文件。（清空不会对tomcat运行带来影响）

- ==webapps目录==

  > webapps目录用来存放应用程序，当tomcat启动时会去加载webapps目录下的应用程序。可以以文件夹、war包、jar包的形式发布应用。当然，你也可以把应用程序放置在磁盘的任意位置，在配置文件中映射好就行。
  >
  > webapps目录下的ROOT目录介绍：
  >
  > tomcat的webapps目录下有个默认的ROOT目录，也可以把项目war包**解压开放入ROOT目录**，同样可以运行项目。但放在ROOT目录下之后访问项目方式就会变为：**ip+端口号**。所以项目放在webapps目录和放在ROOT目录的区别是webapps不需要解压，ROOT需要解压；webapps访问项目需要加项目名，ROOT不需要加项目名。

- work目录

  > work目录用来存放tomcat在运行时的编译后文件，例如JSP编译后的文件。
  > 清空work目录，然后重启tomcat，可以达到清除缓存的作用。~

**注意：http默认端口号为80**

### 3. 如何部署web项目到Tomcat服务器

> 在Tomcat下建立web工程文件有两种方式

1. 拷贝目录

   > 只需要把web工程的目录拷贝到Tomcat的webapps目录下即可。

2. 创建配置文件

   > 到tomcat文件夹的conf目录下的Catalina\localhost目录下，建立xml文件。

   文件内容如下：

   ~~~xml
   <Context path="/abc" docBase= "E: \IdeaProjects\JavaWeb\out \artifacts\web03_ war_ exploded"/>
   <!--Context表示一个工程上下文
   path表示工程的在网站上的访问路径:/abc
   docBase表示你的工程目录在哪里
   -->
   ~~~

   > 比如：将一个名为student.html的文件复制到docBase所示的路径。则搜索http://localhost:8080/abc/student.html即可访问。
   >
   > 如果没有资源文件名，则默认先寻找访问index.html文件。`http://localhost:8080/abc`==`http://localhost:8080/abc/index.html`


### 4. Maven仓及IDEA中的Maven操作

> 在Javaweb开发中，需要使用大量的jar包，我们手动去导入;Maven可以自动帮我导 入和配置这个jar包。
> 我们目前用来就是方便导入jar包的。

#### 4.1 配置环境变量

> - M2_ HOME		 	   	maven目录下的bin目录
> - MAVEN_ HOME			maven的目录
> - 在系统的path中配置	%MAVEN_ HOME%\bin

#### 4.2 建立本地仓库

> Maven有一个本地仓库，远程仓库和中央仓库。默认在用户文件下`${user.home}`。可以修改配置。
>
> conf目录下的settings.xml文件，找到其中的localRepository修改仓库位置

~~~xml
<localRepository>/path/to/local/repo</localRepository>
<!--这里修改为D:\Tomcat\apache-maven-3.8.4\Maven-repo-->
<localRepository>D:\Tomcat\apache-maven-3.8.4\Maven-repo</localRepository>
~~~

#### 4.3 IDEA中的Maven操作

- 新建项目，选择Maven项目，在新打开的Maven原型中找到`org.apache.maven.archetypes:maven-archetype -webapp`使用它。

  [图解示例：](https://s4.ax1x.com/2022/02/24/bkC25T.png)

​						[<img src="https://s4.ax1x.com/2022/02/24/bkC25T.png" alt="bkC25T.png" style="zoom:50%;" />](https://imgtu.com/i/bkC25T)

- 然后配置Maven地址和`setting.xml`文件的地址

  [配置如图：](https://s4.ax1x.com/2022/02/24/bkCXGD.png)

​						[<img src="https://s4.ax1x.com/2022/02/24/bkCXGD.png" alt="bkCXGD.png" style="zoom:50%;" />](https://imgtu.com/i/bkCXGD)

- 同时也可以不选用模板直接创建，创建后的项目文件目录如下

  [一个干净的Maven项目：](https://s4.ax1x.com/2022/02/24/bkZk0H.png)

​									[<img src="https://s4.ax1x.com/2022/02/24/bkZk0H.png" alt="bkZk0H.png" style="zoom: 50%;" />](https://imgtu.com/i/bkZk0H)

[模板创建出来的项目：](https://s4.ax1x.com/2022/02/24/bkZN90.png)

​								[<img src="https://s4.ax1x.com/2022/02/24/bkZN90.png" alt="bkZN90.png" style="zoom: 67%;" />](https://imgtu.com/i/bkZN90)

> 可以对比出使用模板创建的web项目`main`目录下少了`java`和`resources`两个文件夹，我们可以手动创建补全项目文件。
>
> 之后通过标记文件功能标记`java`为源码目录，`resources`为资源目录。

[文件标记功能：](https://s4.ax1x.com/2022/02/24/bke95n.png)

​										[<img src="https://s4.ax1x.com/2022/02/24/bke95n.png" alt="bke95n.png" style="zoom:50%;" />](https://imgtu.com/i/bke95n)

#### 4.4 配置Tomcat

- 点击窗口右上角添加配置

  [添加配置：](https://s4.ax1x.com/2022/02/24/bkeosU.png)

​											[<img src="https://s4.ax1x.com/2022/02/24/bkeosU.png" alt="bkeosU.png" style="zoom:50%;" />](https://imgtu.com/i/bkeosU)

- 点击窗口左上角+号添加新配置

  [添加新配置：](https://s4.ax1x.com/2022/02/24/bkezQK.png)

​									[<img src="https://s4.ax1x.com/2022/02/24/bkezQK.png" alt="bkezQK.png" style="zoom:50%;" />](https://imgtu.com/i/bkezQK)

- 找到`Smart Tomcat`没有的话可以去插件库下载

  [Smart Tomcat：](https://s4.ax1x.com/2022/02/24/bkm8Wq.png)

​															[<img src="https://s4.ax1x.com/2022/02/24/bkm8Wq.png" alt="bkm8Wq.png" style="zoom:50%;" />](https://imgtu.com/i/bkm8Wq)

- [编辑配置如图所示：](https://s4.ax1x.com/2022/02/24/bkuEKf.png)

​												[<img src="https://s4.ax1x.com/2022/02/24/bkuEKf.png" alt="bkuEKf.png" style="zoom: 33%;" />](https://imgtu.com/i/bkuEKf)

- 点击确定，之后右上角运行，等待服务器启动。最后打开浏览器输出http://localhost:8080/web即可访问

  [访问成功如图所示：](https://s4.ax1x.com/2022/02/24/bkugde.png)

​											[<img src="https://s4.ax1x.com/2022/02/24/bkugde.png" alt="bkugde.png" style="zoom: 25%;" />](https://imgtu.com/i/bkugde)

#### 4.5 web项目中的pom.xml文件

> pom.xml是maven的核心配置文件，里面的常用标签结构及说明如下：

|       标签       |                     说明                     |
| :--------------: | :------------------------------------------: |
|    properties    |          maven仓的版本及字符编码等           |
|      build       |            maven仓用到的插件文件             |
| ==dependencies== | jar包构建地址，可以自动下载相关的jar包和依赖 |

#### 4.6 Maven仓库的使用

> 在javaweb项目中使用一些包后，`ALT+回车`，本地Maven仓中没有找到该包，这时候就要去官方仓库下载。

[仓库中没有该包：](https://s4.ax1x.com/2022/02/25/bAWlo6.png)

​							[<img src="https://s4.ax1x.com/2022/02/25/bAWlo6.png" alt="bAWlo6.png" style="zoom:50%;" />](https://imgtu.com/i/bAWlo6)

- 百度进入Maven仓库官网。之后搜索该包。

  [找到后可以下载jar包，也可以使用Macen配置pox.xml：](https://s4.ax1x.com/2022/02/25/bAhjJK.png)

​											[<img src="https://s4.ax1x.com/2022/02/25/bAhjJK.png" alt="bAhjJK.png" style="zoom:50%;" />](https://imgtu.com/i/bAhjJK)

- 将代码复制进`pom.xml`文件的`<dependencies>`标签之间

  [pom.xml文件配置：](https://s4.ax1x.com/2022/02/25/bA5JAI.png)

​									[<img src="https://s4.ax1x.com/2022/02/25/bA5JAI.png" alt="bA5JAI.png" style="zoom:50%;" />](https://imgtu.com/i/bA5JAI)

==注意：`<scope>`标签是作用域的意思，可以直接删除，删除后该jar包应用于所有文件。==

## 三. HTTP协议

> `HTTP`协议(超文本传输协议HyperText Transfer Protocol)，它是基于TCP协议的应用层传输协议，简单来说就是客户端和服务端进行数据传输的一种规则。**其规范了浏览器和服务器交互或通信规则。**
>
> `HTTP` 是一种**无状态** (stateless) 协议, `HTTP`协议本身不会对发送过的请求和相应的通信状态进行持久化处理。这样做的目的是为了保持HTTP协议的简单性，从而能够快速处理大量的事务, 提高效率。
>
> `HTTPS`：基于HTTP实现，比HTTP更安全，提供了身份验证和通信内容加密.

### 1. http1.0和http2.0的区别

[http1.0和2.0区别：](https://s4.ax1x.com/2022/02/25/bAqoQ0.jpg)

​								[<img src="https://s4.ax1x.com/2022/02/25/bAqoQ0.jpg" alt="bAqoQ0.jpg" style="zoom: 25%;" />](https://imgtu.com/i/bAqoQ0)

### 2. http请求

> 请求过程：客户端(发送请求Request)———>服务器
>
> ==http请求可以分为三部分：==
>
> 1. 请求行：由**请求方式**，**请求资源地址**和**请求协议与版本号**。这三部分构成。
> 2. 请求头：`host：`有请求资源主机IP地址和端口号、`referer：`请求从什么地方发起、`User-Agent：`浏览器版本内核等
> 3. 请求正文：该信息只会在请求方式是`post`方式下产生。

- 当我们向一个网站发送访问请求，会产生请求行：

  ~~~java
  Request URL :https://www. bai du. com/
  Request Method:GET
  Status code:200 OK
  Remote Address:14. 215.177.39:443
  Referrer Policy:no-referrer-when-downgrade
  ~~~

  请求行说明：

  |    名称     |     说明     |
  | :---------: | :----------: |
  | Request URL |   请求地址   |
  |   Method    |   请求方法   |
  | Status code |    状态码    |
  |   Remote    | 域名解析地址 |

- 同时也会产生请求头

  ~~~java
  Accept: text/htm1
  Accept- Encoding:gzip，deflate, br
  Accept -Language:zh-CN,zh;q=0.9
  Cache-Contro1 :max-age=0
  Connecti on:keep-alive
  ~~~

- ==Referer==

  > `Referer`是防盗链。用来判断访问地址从什么地方发起。如果不是自己的网站发起，则不予访问。
  >
  > 如：从腾讯视频网站无法下载爱奇艺视频资源。

### 3. 响应过程

> 响应过程：服务器端(响应)———>客户端下
>
> ==http响应页可以分为三部分：==
>
> 1. 响应行信息：有http协议和版本号、状态码、访问状况。
> 2. 响应头信息：`server`：对应自己电脑的IP地址。
> 3. 响应正文信息：相应成功后的网页代码。

当服务器收到客户端的请求时，会产生响应头：

~~~java
cache-Contro1 :private								
connection :Keep-Alive 
Content-Encoding:gzip
content-Type : text/htm1
~~~

|       名称       |   说明   |
| :--------------: | :------: |
|  cache-Contro1   | 缓存控制 |
|    connection    |   连接   |
| Content-Encoding |   编码   |
|   content-Type   |   类型   |

### 4. 常用的状态码
| 状态码 |           说明            |
| :----: | :-----------------------: |
|  200   |      请求响应成功200      |
|  3xx   |        请求重定向         |
|  4Xx   | 找不到资源404(资源不存在) |
|  5xx   |     服务器代码错误500     |
|  502   |         网关错误          |

==重定向:你重新到我给你新位置去;==

## 四. Servlet

> Servlet就是用来开发动态web的一门技术。
>
> Sun在这些API中提供一个接口叫做: Servlet, 如果你想开发一个Servlet程序, 只需要完成两个小步骤:
>
> 1. 编写一个类,实现Servlet接口
> 2. 把开发好的ava类部署到web服务器中。
>
> 我们把实现了Servlet接口的Java程序叫做，Servlet

### 1. 第一个Servlet程序环境搭建

- 先构建一个普通的Maven项目，删掉里面的`src`文件，剩下的文件是必须要的配置文件，这就是一个空的Mave项目。

  [空的Maven项目：](https://s4.ax1x.com/2022/02/26/bZU191.png)

  ​																						[<img src="https://s4.ax1x.com/2022/02/26/bZU191.png" alt="bZU191.png" style="zoom:80%;" />](https://imgtu.com/i/bZU191)

- 之后在`pom.xml`文件的`<dependencies>`标签之间添加Servlet和jsp的依赖

  ~~~xml
  <dependencies>
          <!-- https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api -->
          <dependency>
              <groupId>javax.servlet</groupId>
              <artifactId>javax.servlet-api</artifactId>
              <version>4.0.1</version>
          </dependency>
  
          <!-- https://mvnrepository.com/artifact/javax.servlet.jsp/javax.servlet.jsp-api -->
          <dependency>
              <groupId>javax.servlet.jsp</groupId>
              <artifactId>javax.servlet.jsp-api</artifactId>
              <version>2.3.3</version>
          </dependency>
  </dependencies>
  ~~~

  > 注意：如果添加后jar包无法下载，则可以去Maven的官网下载对应的jar包，之后将jar包手动添加到web项目里即可。

- 之后在刚刚建好的空的Maven项目中新建一个模块，选择Maven添加`org.apache.maven.archetypes:maven-archetype -webapp`即可。也就是在空的Mavenweb(父项目)项目下，再建立一个mavenweb(子项目)项目

  [新建模块：](https://s4.ax1x.com/2022/02/26/bZ0JGd.png)

​													[<img src="https://s4.ax1x.com/2022/02/26/bZ0JGd.png" alt="bZ0JGd.png" style="zoom:50%;" />](https://imgtu.com/i/bZ0JGd)

​		[Maven添加webapp：](https://s4.ax1x.com/2022/02/26/bZ0TJJ.png)

​										[<img src="https://s4.ax1x.com/2022/02/26/bZ0TJJ.png" alt="bZ0TJJ.png" style="zoom:50%;" />](https://imgtu.com/i/bZ0TJJ)

- 关于Maven父子工程的说明：

  父项目中会有：

  ~~~xml
  <modules>
  	<module>serv1et-01</modu1e>
  </modules>
  ~~~

  子项目中会有：

  ~~~xml
  <parent>
  	<artifactId>javaweb-02-serv1et</artifactId>
  	<groupId>com.kuang</groupId>  
  	<version>1.0-SNAPSHOT</version>
  </parent>
  ~~~

- 之后在新建的子项目(serv1et-01)创建`java`源码目录和`resources`资源目录。

  [最后项目结构：](https://s4.ax1x.com/2022/02/26/bZDaE8.png)

​																			[<img src="https://s4.ax1x.com/2022/02/26/bZDaE8.png" alt="bZDaE8.png" style="zoom:50%;" />](https://imgtu.com/i/bZDaE8)

#### 1.1 Servlet程序的编写

- 编写一个普通类：在子项目的`java`源码目录中新建一个包，包下建立一个类

  [搭建好的Servlet目录：](https://s4.ax1x.com/2022/02/26/bZDLVK.png)

​																			[<img src="https://s4.ax1x.com/2022/02/26/bZDLVK.png" alt="bZDLVK.png" style="zoom:50%;" />](https://imgtu.com/i/bZDLVK)

- 实现Servlet接口：我们可以直接继承`HttpServlet`这个类

  ~~~java
  package com.kuang.servlet;
  import javax.servlet.http.HttpServlet;
  public class HelloServlet extends HttpServlet {
      
  }
  ~~~

  [关于Servlet类的结构：](https://s4.ax1x.com/2022/02/26/bZ5YWt.png)

​												[<img src="https://raw.githubusercontent.com/Acidmt/A_cind/master/20220327155059.png" alt="bZ5YWt.png" style="zoom:50%;" />](https://imgtu.com/i/bZ5YWt)

- 重写Servlet的doGet ，doPost方法

  ~~~java
  pub1ic class HelloServlet extends HttpServ1et {
  //由于get或者post只是请求实现的不同的方式，可以相互调用，业务逻辑都一样;
  	@Override
  	protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
  		//ServletoutputStream outputStream = resp. getoutputStream() ;
  		PrintWriter writer = resp. getWriter(); //响应流
  		writer.print("Hello,Serlvet");
  }
  	@Override
  	protected void doPost(HttpServletRequest req,HttpServletResponse resp) throws Serv1etException,IOException {
  		doGet(req，resp);
  	}
  }
  ~~~

#### 1.2 编写servlet的映射

> 因为我们写的是java程序，但要通过浏览器访问，而浏览器需要连接web服务器，所以需要在web服务器中注册我们写的servlet。同时还需要给他一个浏览器能够访问的路径。

- 在web.xml文件的`<web-app>`中编写：1. 注册servlet。2. 编写servlet的请求路径。

  ~~~xml
  <!--注册Servlet-->
  <serv1et>
  	<servlet-name>hello</servlet-name>			<!--映射路径注册的servlet位置-->
  	<servlet-class>com.kuang.servlet.HelloServ1et</servlet-class>
  </serv7et>
  <!--Servlet的请求路径-->
  <servlet-mapping>
  	<servlet-name>he11o</serv1et-name>
  	<url-pattern>/he11o</url-pattern>			<!--映射路径-->
  </serv1et-mapping>
  ~~~

- 配置Tomcat，如上文所示。之后启动Tomcat。

  启动完Tomcat后输入地址    http://localhost:8080/hello

  [输出：](https://s4.ax1x.com/2022/02/26/bZXw34.png)

​																					[<img src="https://s4.ax1x.com/2022/02/26/bZXw34.png" alt="bZXw34.png" style="zoom: 67%;" />](https://imgtu.com/i/bZXw34)

### 2. Servlet原理

> Servlet是由Web服务器调用，web服务器在收到浏览器请求之后，会：
>
> 1. 如果请求是第一次访问，会产生一个Servlet类
> 2. web容器(Tomcat)会产生两个对象：Request(请求)和Response(响应)
> 3. 之后Servlet会调用`service`的两个方法，在`service`中有一个ServletRequest方法(用于处理请求)和 ServletResponse方法(用于处理响应)
> 4. 也就是Request会从service(请求方法)中拿到请求。并且把请求之后的响应交给Response
> 5. 最后Response把再把响应消息提交个web容器。
>
> 我们自己编写的实现类，重写这些方法是为了：
>
> 1. 接收并处理请求
> 2. 给出响应的信息

[Servlet原理图解：](https://s4.ax1x.com/2022/02/27/bnlJZd.png)

​											[<img src="https://s4.ax1x.com/2022/02/27/bnlJZd.png" alt="bnlJZd.png" style="zoom:50%;" />](https://imgtu.com/i/bnlJZd)

### 3. Mapping问题

> `servlet-mapping`可以用来设置映射路径。

#### 3.1 一个Servlet可以指定一个路径

~~~xml
<servlet-mapping>
	<servlet-name>he11o</serv1et-name>
	<url-pattern>/he11o</url-pattern>			<!--映射路径-->
</serv1et-mapping>
~~~

#### 3.2 一个Servlet可以指定多个映射路径

~~~xml
<servlet-mapping>
	<servlet-name>he11o</serv1et-name>
	<url-pattern>/he11o1</url-pattern>			
</serv1et-mapping><servlet-mapping>
	<servlet-name>he11o</serv1et-name>
	<url-pattern>/he11o2</url-pattern>			
</serv1et-mapping><servlet-mapping>
	<servlet-name>he11o</serv1et-name>
	<url-pattern>/he11o3</url-pattern>			
</serv1et-mapping>
~~~

> 服务器启动后http://localhost:8080/hello1和http://localhost:8080/hello2或http://localhost:8080/hello3都可以访问

#### 3.3 一个Servlet可以指定通用映射路径

~~~xml
<servlet-mapping>
	<servlet-name>he11o</serv1et-name>
	<url-pattern>/he11o/*</url-pattern>			<!--映射路径-->
</serv1et-mapping>
~~~

> 映射路径后加任意路径都可以访问。如：http://localhost:8080/hello/dwads

#### 3.4 可以自定义后缀实现请求映射

~~~xml
<servlet-mapping>
	<servlet-name>hello</servlet-name>
	<url-pattern>*.shi</url-pattern>
</servlet-mapping>
~~~

> IP+端口号+只要以.shi结尾的都可以访问。如：http://localhost:8080/dfawd.shi
>
> 注意：映射的`*`前不能加项目映射路径

#### 3.5 自定义404界面

> 新建一个类用于网页出错后的展示界面
>
> 使用通配符表示输入路径错误时候调用新建的类，展示自定义的404界面

~~~java
public class ErrorServlet extends HttpServlet {
	@Override
	protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		resp.setContentType( "text/html" );
		resp.setCharacterEncoding("utf-8");
		PrintWriter writer = resp.getWriter();
		writer.print("<h1>404</h1>");
	@Override
	protected void doPost (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {doGet(req, resp);}
}
~~~

web.xml文件：

~~~xml
<servlet>
	<servlet-name>error</ servlet-name>
	<servlet-class>com.kuang.servlet.ErrorServ1et</servlet-class>
</servlet>
<servlet-mapping>
	<servlet-name>error</ servlet-name>
	<url-pattern>/*</url-pattern>
</serv1et-mapping>
~~~

> 只要输入任何路径就会出现自定义的404界面。

### 4. ServletContext对象

> ServletContext是一个全局的储存信息的空间，服务器开始就存在，服务器关闭才释放。
>
> 我们可以把ServletContext当成一个公用的空间，可以被所有的客户访问，其他Servlet都可以访问。因此Servlet对象之间可以通过ServletContext对象来实现通讯。

[ServletContext结构：](https://s4.ax1x.com/2022/02/27/bnDJeI.png)

​										[<img src="https://s4.ax1x.com/2022/02/27/bnDJeI.png" alt="bnDJeI.png" style="zoom: 67%;" />](https://imgtu.com/i/bnDJeI)

#### 4.1 ServletConfig接口

> 当Tomcat初始化一个Servlet时，会将该Servlet的配置信息(如：wen.xml)封装到ServletConfig对象中，ServletConfig定义了一系列获取配置信息的方法：

|               方法说明               |                          功能描述                           |
| :----------------------------------: | :---------------------------------------------------------: |
| String getInitParameter(String name) |           根据初始化参数名返回对应的初始化参数值            |
| Enumeration getInitParameterNames()  |   返回一个 Enumeration 对象，其中包含了所有的初始化参数名   |
|  ServletContext getServletContext()  |       返回一个代表当前 Web 应用的 ServletContext 对象       |
|       String getServletName()        | 返回 Servlet 的名字，即 web.xml 中 `<servlet-name>`元素的值 |

#### 4.2 ServletContext简单应用

> 当servlet容器启动时，会为每个web应用创建唯一的一个ServletContext对象代表当前的web应用。该对象不仅封装了当前web应用的所有信息，而且实现了多个servlet之间的数据共享。
|                             方法                             |                      说明                       |
| :----------------------------------------------------------: | :---------------------------------------------: |
| setAttribute(name,value);name是String类型，value是Object类型； | 往域对象里面添加数据，添加时以key-value形式添加 |
|                     getAttribute(name);                      |        根据指定的key读取域对象里面的数据        |
|                    removeAttribute(name);                    |        根据指定的key从域对象里面删除数据        |

- 编写一个设置会话信息的类

  SetServlet.java

  ~~~java
  pub1ic class HelloServlet extends HttpServlet {
  	@override
  	protected void doGet (HttpServletRequest req,HttpServ1etResponseresp) throws ServletExcepti on，IOException {
  		ServletContext context = this. getServletcontext() ;
  		string username = "shi"; 						//数据
  		context. setAttribute ("username",username); 	//将一个数据保存在 了
  	}
      	protected void doPost (HttpServletRequest req,HttpServletResponseresp) throws ServletExcepti on，IOException {
  		doGet(req，resp);
  	}
  }
  ~~~

- 编写一个读取会话的类

  GetServlet.java

  ~~~java
  pub1ic class GetServlet extends HttpServlet {
  	@override 
  	protected void doGet (HttpServletRequest req,HttpServletResponse resp) throws ServletExcepti on，IOException {
  		ServletContext context = this.getServletContext();
  		String username = (String) context.getAttribute ("username");
  		resp. setContentType ("text/html") ;			//设置编码
  		resp. setCharacterEncoding("utf-8");
  		resp. getWriter().print("名字"+username);
      }
  	@override
  	protected void doPost (HttpServletRequest req,HttpServletResponseresp) throws ServletExcepti on，IOException {
  		doGet(req，resp);
  	}
  }
  ~~~

- 最后配置web.xml

  ~~~xml
  <!--SetServlet-->
  <servlet>
  	<servlet-name>he11o</servlet-name>
  	<serv1et-class>com. kuang. serv1et. SetServ1et</serv1et-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>he11o</servlet-name>
  	<ur1-pattern>/he11o</ur1-pattern>
  </servlet-mapping>
  
  <!--GetServlet-->
  <serv1et>
  	<servlet-name>getc</servlet-name>
  	<servlet-class>com. kuang. servlet. GetServ1et</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>getc </servlet-name>
  	<ur1-pattern>/getc</ur1-pattern>
  </servlet-mapping>
  ~~~

- 启动Tomcat访问http://localhost:8080/hello再访问http://localhost:8080/getc页面即可出现：`名字shi`

#### 4.3 ServletContext会话应用

> 如下是ServletContext获取初始化参数操作：

- 编写一个ServletDemo类，里面调用getServletContext方法获取Servlet中的上下文(即web.xml文件中的上下文)。

  ~~~java
  protected void doGet (HttpServletRequest req,HttpServletResponse resp)
  throws ServletException,IoException {
  	Servletcontext context = this.getServletContext();
  	string ur1 = context.getInitparameter("url");		//获取web.xml文件中的url值
  	resp.getwriter().print(ur1);
  }
  ~~~

- 配置web.xml

  ~~~xml
  <!--使用ServletContext可以获取标签<param-name>url里的信息-->
  <context-param>
  	<param-name>ur1</param-name>
  	<param-value>jdbc:mysq1://localhost:3306/mybatis</param-value>
  </context-param>
  <!--ServletDemo-->
  <serv1et>
  	<servlet-name>getc</servlet-name>
  	<servlet-class>com.kuang.servlet. ServletDemo</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>get </servlet-name>
  	<ur1-pattern>/get</ur1-pattern>
  </servlet-mapping>
  ~~~

  > 访问http://localhosrhost:8080/get之后会出现`jdbc:mysq1://localhost:3306/mybatis`字样。

#### 4.4 请求转发

> 请求转发是ServletContext的常用操作。指的是页面读取显示另一个页面的内容。

- 编写一个ServletDemo2类，和上面的ServletDemo类似，但此时实现的主要作用是转发ServletDemo页面的内容

  ~~~java
  protected void doGet (HttpServletRequest req,HttpServletResponse resp)
  throws ServletException,IoException {
  	Servletcontext context = this.getServletContext();
      //RequestDispatcher requestDispatcher = context.getRequestDispatcher("/get"); //转发的请求路径
      //requestDispatcher.forward(req,resp); 									//调用forward实现请求转发
  	context.getRequestDispatcher("/get").forward(req,resp);					//获取get映射页面的内容
  }
  ~~~

  >  **forward**：是服务器请求资源，服务器直接访问目标地址的URL，把那个URL的响应内容读取过来，然后把这些内容再发给浏览					器，浏览器根本不知道服务器发送的内容是从哪儿来的，所以它的地址栏中还是原来的地址。

- 编写web.xml

  ~~~xml
  <!--使用ServletContext可以获取标签<param-name>url里的信息-->
  <context-param>
  	<param-name>ur1</param-name>
  	<param-value>jdbc:mysq1://localhost:3306/mybatis</param-value>
  </context-param>
  <!--ServletDemo-->
  <serv1et>
  	<servlet-name>get</servlet-name>
  	<servlet-class>com.kuang.servlet. ServletDemo</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>get </servlet-name>
  	<ur1-pattern>/get</ur1-pattern>
  </servlet-mapping>
  <!--ServletDemo2-->
  <serv1et>
  	<servlet-name>gets</servlet-name>
  	<servlet-class>com.kuang.servlet. ServletDemo2</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>gets </servlet-name>
  	<ur1-pattern>/gets</ur1-pattern>
  </servlet-mapping>
  ~~~

  > 启动Tomcat输入http://localhost:8080/gets之后会显示和http://localhost:8080/get一样的内容。这时候便实现了对http://localhost:8080/get的转发。虽然实现了转发，但路径仍然不会变。

  [实现原理(图片上方的模型)：](https://s4.ax1x.com/2022/02/28/bM1HeS.png)

​												[<img src="https://s4.ax1x.com/2022/02/28/bM1HeS.png" alt="bM1HeS.png" style="zoom:67%;" />](https://imgtu.com/i/bM1HeS)

#### 4.5 读取资源文件

> ServletContext提供了一些接口专门用来读取资源信息

|                   方法说明                   |                           功能描述                           |
| :------------------------------------------: | :----------------------------------------------------------: |
|      Set getResourcePaths(String path)       | 返回一个 Set 集合，集合中包含资源目录中子目录和文件的路径名 称。参数 path 必须以正斜线（/）开始，指定匹配资源的部分路径 |
|       String getRealPath(String path)        | 返回资源文件在服务器文件系统上的真实路径（文件的绝对路径）。参数 path 代表资源文件的虚拟路径，它应该以正斜线（/）开始，/ 表示当前 Web 应用的根目录，如果 Servlet 容器不能将虚拟路径转换为文 件系统的真实路径，则返回 null |
|         URL getResource(String path)         | 返回映射到某个资源文件的 URL 对象。参数 path 必须以正斜线（/）开始，/ 表示当前 Web 应用的根目录 |
| InputStream getResourceAsStream(String path) | 返回映射到某个资源文件的 InputStream 输入流对象。参数 path 的传递规则和 getResource() 方法完全一致 |

- 在资源目录`resources`下建立db.properties文件，里面填写信息

  ~~~properties
  username=root
  password=123456
  ~~~

  > 此时如果启动Tomcat，会发现打包的db.properties会在classes文件夹下。我们俗称这个路径为类路径(classpath)

  [程序运行后db.properties位置：](https://s4.ax1x.com/2022/02/28/bMtHe0.png)

​														[<img src="https://s4.ax1x.com/2022/02/28/bMtHe0.png" alt="bMtHe0.png" style="zoom: 67%;" />](https://imgtu.com/i/bMtHe0)

- 新建一个类文件ServletDemo3里面对实现db.propertie文件内容读取操作

  ~~~java
  public class ErrorServlet extends HttpServlet {
  	@Override
  	protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {																								InputStream is = this.getServletContext().getResourceAsStream("/WEB-	INF/classes/db.properties");									//获取db.properties文件内容
  		Properties prop = new Properties();
          prop.load(is);											//将获取到的内容传输给load方法
  		String user = prop.getProperty( "username");
  		String pwd = prop.getProperty("password");
  		resp.getWriter().print(user+":"+pwd);
  	@Override
  	protected void doPost (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {doGet(req, resp);}
  }
  ~~~

- 配置web.xml

  ~~~xml
  <serv1et>
  	<servlet-name>out</servlet-name>
  	<servlet-class>com.kuang.servlet.ServletDemo3</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>out </servlet-name>
  	<ur1-pattern>/out</ur1-pattern>
  </servlet-mapping>
  ~~~

  > 启动服务器输入地址即可看到结果：`root:123456`

### 5. ==HttpServletResponse==

> web服务器接收到客户端的http请求，针对这个请求，分别创建一个代表请求的HttpServletRequest对象，和代表响应的一个HttpServletResponse对象。
>
> - 如果要获取客户端请求过来的参数:找HttpServletRequest
> - 如果要给客户端响应一-些信息:找HttpServletResponse

#### 5.1 发送状态码相关方法

> 当Servlet向客户端送响应消息时，需要在响应消息中设置状态码，HttpServletResponse定义了3种发送状态码的方法。

- setStatus(int status)方法

  > `setStatus(int status)`方法用于设置HTTP响应消息的状态码，并生成响应状态行。在正常状态下服务器会默认产生一个200的状态行。

- sendError(int sc)方法

  > 该方法用于表述错误信息的状态码。例如：404状态码表示服务器找不到客户端请求的资源。

- sendError(int code, String message)方法

  > 该方法除了可以用于设置状态行外，还会像客户端发送一条错误信息。该信息就是第二个参数`message`所指定的文本信息。

#### 5.2 发送响应消息头的方法

> 当Servlet向客户端发送响应消息时，HttpServletResponse定义了一系列设置HTTP响应头的字段方法。

[发送响应消息头方法：](https://s4.ax1x.com/2022/03/04/bUK16e.jpg)

​													[<img src="https://s4.ax1x.com/2022/03/04/bUK16e.jpg" alt="bUK16e.jpg" style="zoom:50%;" />](https://imgtu.com/i/bUK16e)

> 上面的方法，add开头的多用于设置各种头字段。set开头的用于设置字符编码，这些设置字符编码的方法可以有效得到解决中文字符乱码的问题。

#### 5.3 发送响应消息体的方法

- getOutputStream()方法

  > 该方法所获取的字节输出流对象，为ServletOutputStream类型。由于ServletOutputStream是Outputstream的子类，所以要想输出二进制格式的响应正文，就需要调用该方法。

  ~~~java
  protected void doGet (HttpServletRequest req,HttpServletResponse resp)
  throws ServletException,IoException {
  	String data="1234";
      Outputstream out=resp.getOutputStream();
      out.write(data.getBytes());
  }
  ~~~

  在web.xml中配置号文件后，启动Tomcat输入网址，网页便会出现：1234

- getWriter()方法

  > 该方法所获取的字符输出流对象，为PrintWrite类型。而PrintWrite可以直接输出文本的内容，所以要想输出的内容为**字符文本的网页**可以使用getWriter()方法。

  ~~~java
  protected void doGet (HttpServletRequest req,HttpServletResponse resp)
  throws ServletException,IoException {
  	String data="1234";
      PrintWrite prt=resp.getWriter();
      prt.write(data);
  }
  ~~~

  在web.xml中配置号文件后，启动Tomcat输入网址，网页便会出现：1234

#### 5.4 HttpServletResponse应用

##### 5.4.1 ==实现重定向==

> 在某些情况下，针对客户端的请求，一个servlet类可能无法完成全部工作。这时，可以使用请求重定向来完成。所谓请求重定向，是
> 指web服务器接收到客户端的请求后，可能由于某些条件限制，不能访问当前请求的地址，但服务器制定了一个新的地址。让客户端访问。
>
> 为了实现请求重定向，HttpServletResponse接口定义了一个`sendRedirect()`方法，该方法用于生成302响应码和Location响应头，从而通知客户端访问Location响应头中指定的URL
>
> 该方法使用如下：
>
> sendRedirect(String location)

[重定向原理：](https://s4.ax1x.com/2022/03/04/baLST1.jpg)

​									[<img src="https://s4.ax1x.com/2022/03/04/baLST1.jpg" alt="baLST1.jpg" style="zoom:50%;" />](https://imgtu.com/i/baLST1)

- 在web目录下建立用户登录页面，和用户登陆成功界面。

  login.html

  ~~~html
  <body>
      <from action='/java/LoginServlet' method='post'>
      	用户名：<input type='text' name='username' /><br/>
          密码：<input type='password' name='password'/><br/>
          <input type='submit' value='登录' />
      </from>
  </body>
  ~~~

  welcome.html(用于登录成功显示界面)

  ~~~html
  <body>欢迎登陆</body>
  ~~~

- 在java源码目录包下建立LoginServlet类

  LoginServlet.java

  ~~~java
  protected void doGet (HttpServletRequest req,HttpServletResponse resp)
  throws ServletException,IoException {
      //设置并通知浏览器将编码设置为'utf-8'
  	response.setContentType("text/html;charset=utf-8");
      //用HttpServletRequest对象的getParameter()方法获取用户名和密码
      String username = request.getParameter("username"); 
      String password = request.getParameter("password");
      //假设用户名和密码分别为itcast 和123,如果用户名和密码正确，重定向到welcome.html
      if(("itcast").equals (username)&&("123").equals (password)){
          /*重定向原理
          resp.setHeader( "Location","/r/img");
  		resp.setStatus(302);*/
          response.sendRedirect("/web/welcome.html");
      }else{
          //如果用户名和密码错误，重定向到login.html
  		response.sendRedirect("/web/login.html");
      }
  }
  ~~~

- 注册web.xml文件

  ~~~xml
  <serv1et>
  	<servlet-name>out</servlet-name>
  	<servlet-class>com.kuang.servlet.LoginServlet</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>out </servlet-name>
  	<ur1-pattern>/out</ur1-pattern>
  </servlet-mapping>
  ~~~

> 启动Tomcat服务器后输入：http://localhost:8080/login.html输入用户名和密码后点击登录。如果密码正确则重复定向到welcome.html页面。

##### 5.4.2 使用HttpServletRespons创建下载连接

- 首先在web工程的resoures目录下放置一张图片。之后在java源码目录下创建FileServlet类

  ~~~java
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
  	// 1.要获取下载文件的路径,如果获取不到直接用绝对路径即可
  	String realPath = this. getServ1etContext(). getRealPath("/1.png");
  	System.out.print1n("下载文件的路径: "+realPath);
  	// 2.下载的文件名是啥?
  	String fileName = realPath. substring( realPath.1astIndexOf("\\") + 1);
  	// 3.设置想办法让浏览器能够支持(Content -Disposition)下载我们需要的东西
  	resp. setHeader("Content-Disposition", "attachment;filename=" +fileName);
  	// 4.获取下载文件的输入流
  	FileInputStream in = new FileInputStream(realPath) ;
  	// 5.创建缓冲区
  	int 1en = 0;
  	byte[] buffer = new byte[1024];
  	// 6.获取0utputStream对象
  	ServletOutputStream out = resp. getOutputStream( );
  	// 7.将FileOutputStream流 写入到buffer缓冲区,使用outputStream将缓冲区中的数据输出到客户端!
  	while ( (1en=in. read(buffer))>0){
  		out.write(buffer, 0,len);
      }
  	in.close();
  	out.close();	
  }
  ~~~

- 注册web.xml文件

  ~~~xml
  <serv1et>
  	<servlet-name>out</servlet-name>
  	<servlet-class>com.kuang.servlet.FileServlet</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>out </servlet-name>
  	<ur1-pattern>/out</ur1-pattern>
  </servlet-mapping>
  ~~~


#### 5.4.3 实现验证码

~~~java
protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
	//如何让浏览器3秒自动刷新一次;
	resp. setHeader( "refresh", "3");
	//在内存中创建一个图片指定宽高
	BufferedImage image = new BufferedImage( width: 80, height: 20, BufferedImage.TYPE_ _INT_ RGB);
	//得到图片
	Graphics2D g = (Graphics2D) image.getGraphics(); //笔
	//设置图片的背景颜色
	g. setColor(Color.white);
	g. fillRect( x:0, y:0, width: 80，height: 20);
	//给图片写数据
	g. setColor(Color.BLUE);
	g. setFont(new Font( name: null, Font. BOLD, size: 20));
	g. drawString(makeNum(), x:0, y:20);
	//告诉浏览器，这个请求用图片的方式打开
	resp. setContentType("image/jpeg");
	//网站存在缓存，不让测览器缓存
	resp. setDateHeader( "expires", -1);
	resp. setHeader( "Cache-Control", "no-cache");
	resp. setHeader("Pragma","no-cache");
	//把图片写给测览器
	ImageIO. write(image, formatName: "jpg", resp.getOutputStream());
}
//生成随机数
private String makeNum(){
	Random random = new Random();
    //生成不超过七位数的的数字用于做验证码
	String num = random.nextInt( bound: 9999999) +"";
	StringBuffer sb = new StringBuffer();
    //如果生成的数字不够七位则在后面补0
	for (int i = 0; i < 7-num.1ength() ; i++) {
		sb.append("0");
    }
	num = sb.toString() + num;
	return num;
}
~~~

### 6. ==HttpServletRequest==

> HttpServletRequest接口，专门用于封装Http请求消息。方法主要分为两种：

#### 6.1 获取请求行信息的相关方法

> 当访问servlet时，请求消息的请求行中会包含请求方法、请求资源名、请求路径等信息。我们可以通过如下方法获取信息。

|             方法             |                             说明                             |
| :--------------------------: | :----------------------------------------------------------: |
|      String getMethod()      |   该方法用于获取HTTP请求消息中的请求方式（如GET、POST等）    |
|    String getReauestURI()    | 该方法用于获取请求行中资源名称部分，即位于URL的主机和端口之后、参数部分之前的部分 |
|   String getQueryString()    | 该方法用于获取请求行中的参数部分，也就是资源路径后问号（？）以后的所有内容 |
|     String getProtocol()     | 该方法用于获取请求行中的协议名和版本，例如，HTTP/1.0 或 HTTP/1.1 |
|   String getContextPath()    | 该方法用于获取请求URL中属于WEB应用程序的路径，这个路径以"/"开头，表示相对于整个WEB站点的根目录，路几个结尾不含“/”。如果请求URL属于web站点的根目录，那么返回结果为空字符串“” |
|   String getServletPath()    |       该方法用于获取Servlet的名称或Servlet所映射的路径       |
|    String getRemoteAddr()    | 该方法用于获取请求客户端的IP地址，其格式类似于"192.168.0.3"  |
|    String getRemoteHost()    | 该方法用于获取请求客户端的完整主机名，其格式类似于"pc1.xxxx.cn"。需要注意的是，如果无法解析出客户机的完整主机名，该方法会返回客户端的IP地址 |
|     int getRemotePort()      |           该方法用于获取请求客户端网络连接的端口号           |
|    String getLocalAddr()     |    该方法用于获取Web服务器上接收当前请求网络连接的IP地址     |
|    String getLocalName()     |  该方法用于获取Web服务器上接收当前网络连接IP所对应的主机名   |
|      int getLocalPort()      |      该方法用于获取Web服务器上接收当前网络连接的端口号       |
|    String getServerName()    | 该方法用于获取当前请求所指向的主机名，即HTTP请求消息中HOST头字段所对应的主机名部分 |
|     int getServerPort()      | 该方法用于获取当前请求所连接的服务器端口号，即如果HTTP请求消息中HOST头字段所对应的端口号部分 |
|      String getScheme()      |       该方法用于获取请求的协议名，例如http、https或ftp       |
| StringBuffer getRequestURL() | 该方法用于获取客户端发出请求时的完整URL，包括协议、服务器名、端口号、资源路径等信息，但不包括后面的查询参数部分。注意，getRequestRUL()方法返回的时StringBuffer类型，而不是String类型。 |

如下案例是对以上方法的总结运用：

~~~java
public void doGet(HttpServletRequest request,HttpServletResponse response)throws ServletException, IOException{
    response.setContentType("text/html;charset=utf-8");
	PrintWriter out =response.getWriter();
    // 获取请求行的相关信息
	out.println("getMethod :"+ request.getMethod()+"<br />");
    out.println("getRequestURI:"+ request.getRequestURI()+"<br/>");
    out.println("getQueryString:"+request.getQueryString()+"<br/>"); 
    out.printin("getProtocol:"+ request.getProtocol()+"<br/>");
    out.println("getContextPath:"+request.getContextPath() + "<br />");
    out.println("getPathInfo:"+ request.getPathInfo()+ "<br />");
    out.printin("getPathTranslated:"+ request.getPathTranslated()+"<br/>");
	out.println("getServletPath:"+request.getServletPath() +"<br/>"); 
    out.println("getRemoteAddr :"+ request.getRemoteAddr()+"<br/>"); 
    out.println("getRemoteHost:"+ request.getRemoteHost()+"<br />");
    out.println("getRemotePort : "+ request.getRemotePort() + "<bx />");
    out.println("getLocalAddr:"+ request.getLocalAddr()+"<br />");
    out.print1n("getLocalName :"+request.getLocalName() + "<br />");
    out.printin("getLocalPort:"+ request.getLocalPort() +"<br />");
    out.printin("getServerName :"+request.getServerName() +"<br />");
    out.println("getServerPort:"+ request.getServerPort()+ "<bx/>"); 
    out.println("getScheme :"+ request.getScheme()+"<br/>"); 
    out.printin("getRequestURL:"+ request.getRequestURL()+"<br />");
}
~~~

[运行结果：](https://s4.ax1x.com/2022/03/05/bwsoin.jpg)

​									[<img src="https://s4.ax1x.com/2022/03/05/bwsoin.jpg" alt="bwsoin.jpg" style="zoom: 25%;" />](https://imgtu.com/i/bwsoin)

#### 6.2 获取请求头的相关方法

> 当请求servlet时需要通过请求头向服务器传递附加信息，例如客户端可以接收的数据类型、压缩方式、语言等 。为此该接口定义了一系列用于获取HTTP请求头字段的方法 。

|              方法声明               |                           功能描述                           |
| :---------------------------------: | :----------------------------------------------------------: |
|    String getHeader(String name)    | 该方法用于获取一个指定头字段的值，如果请求消息中没有包含指定的头字段，则 getHeader() 方法返回 null；如果请求消息中包含多个指定名称的头字段，则 getHeader() 方法返回其中第一个头字段的值 |
| Enumeration getHeaders(String name) | 该方法返回一个 Enumeration 集合对象，该集合对象由请求消息中出现的某个指定名称的所有头字段值组成。在多数情况下，一个头字段名在请求消息中只出现一次，但有时可能会出现多次 |
|    Enumeration getHeaderNames()     |   该方法用于获取一个包含所有请求头字段的 Enumeration 对象    |
|    int getIntHeader(String name)    | 该方法用于获取指定名称的头字段，并且将其值转为 int 类型。需要注意的是，如果指定名称的头字段不存在，则返回值为 -1；如果获取到的头字段的值不能转为 int 类型，则将发生 NumberFormatException 异常 |
|   long getDateHeader(String name)   | 该方法用于获取指定头字段的值，并将其按 GMT 时间格式转换为一个代表日期/时间的长整数，该长整数是自 1970 年 1 月 1 日 0 时 0 分 0 秒算起的以毫秒为单位的时间值 |
|       String getContentType()       |  该方法用于获取 Content-Type 头字段的值，结果为 String 类型  |
|       int getContentLength()        |  该方法用于获取 Content-Length 头字段的值，结果为 int 类型   |
|    String getCharacterEncoding()    | 该方法用于返回请求消息的实体部分的字符集编码，通常是从 Content-Type 头字段中进行提取，结果为 String 类型 |

如下案例是对以上方法的总结运用：

~~~java
public void doGet(HttpServletRequest reque,HttpServletResponse response)throws ServletException, IOException{
    response.setContentType("text/html;charset=utf-8");
	PrintWriter out = response.getWriter()
	//获取请求消息中所有头字段
	Enumeration headerNames = request.get
	//使用循环遍历所有请求头，并通过getHeader()获取一个指定名称的头字段
	while (headerNames.hasMoreElements()){
        String headerName = (String)headerNames.nextElement();
        out.print(headerName + ":" + request.getHeader(headName)+"<br />")
    }
}
~~~

[运行结果：](https://s4.ax1x.com/2022/03/05/bwcRsK.jpg)

​												[<img src="https://s4.ax1x.com/2022/03/05/bwcRsK.jpg" alt="bwcRsK.jpg" style="zoom:25%;" />](https://imgtu.com/i/bwcRsK)

#### 6.3 ==实现请求转发==

> 如果想实现用户实现登录后跳转到另一个界面，则需要用到RequestDispatcher接口的实例对象实现。HttpServletRequest接口提供了getRequestDispatcher()方法用于获取RequestDispatcher对象，getRequestDispatcher()方法实现格式如下：

~~~java
RequestDispatcher getRequestDispatcher(String Path)//path必须以'/'开头
~~~

> 获取到RequestDispatcher对象后，该接口还提供了另一个方法：forward()方法，该方法可以将当前的请求传递给其他web资源，由其他资源做出相应，这种方式称为请求转发。forward()方法如下：

~~~java
forward(ServletRequest request,ServletResponse response)
~~~

下面以一个例子讲解：

- 在java源码目录下建立ResponseforwardServlet.class文件

  ~~~java
  public void doGet(HttpServletRequest request,HttpServletResponseresponse)throws ServletException, IOException{
  	response.setContentType("text/html;charset=utf-8");
  	request.setAttribute("username","张三");// 将数据存储到request对象中
      RequestDispatcher dispatcher = request.getRequestDispatcher("/ResultServlet"); 	
      dispatcher.forward(request,response);
  }
  ~~~

- 之后建立ResultServlet.class文件用于获取ResponseforwardServlet中的数据

  ~~~java
  public void doGet(HttpServletRequest request,HttpServletResponseresponse)throws ServletException, IOException{
  	response.setContentType("text/html;charset=utf-8");
  	PrintWriter out = response.getWriter()
  	String username = (String) request.getAttribute("username");
  	if (username !== null){
          out.println("用户名：" + username+ "<br/>");
      }
  }
  ~~~

- 最后配置web.xml文件

  ~~~xml
  <serv1et>
  	<servlet-name>out</servlet-name>
  	<servlet-class>com.kuang.servlet.ResponseforwardServlet</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>out </servlet-name>
  	<ur1-pattern>/out</ur1-pattern>
  </servlet-mapping>
  
  <serv1et>
  	<servlet-name>set</servlet-name>
  	<servlet-class>com.kuang.servlet.ResultServlet</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>set </servlet-name>
  	<ur1-pattern>/set</ur1-pattern>
  </servlet-mapping>
  ~~~

最后启动Tomcat输入：http://localhost:8080/ResponseforwardServlet/out会出现`用户名：张三`字样。可知浏览器中仍然是ResponseforwardServlet的请求路径。但浏览器却输出了ResultServlet中的内容。这就是请求转发。

#### 6.4 获取前端请求参数

|                     方法                     |                             说明                             |
| :------------------------------------------: | :----------------------------------------------------------: |
|     ==String getParameter(String name)==     |                   通过指定名称获取参数值；                   |
| ==String[] getParameterValues(String name)== | 通过指定名称获取参数值数组，有可能一个名字对应多个值，例如表单中的多个复选框使用相同的name时； |
|       Enumeration getParameterNames()        |                     获取所有参数的名字；                     |
|            Map getParameterMap()             |   获取所有参数对应的Map，其中key为参数名，value为参数值。    |

这里实现一个简单的客户端数据获取

- 首先在web的跟目录下建立一个login.html的文件，这里以login.jsp文件为例子。

  ~~~jsp
  <div sty1e="text-align: center">
  	<%--这里表单表示的意思:以post方式提交表单，提交到我们的本目录下的Login请求--%>
  	<form action="${pageContext.request.contextPath}/login" method="post">
  		用户名: <input type="text" name="username"> <br>
  		密码: <input type="password" name="password"> <br>
  		爱好:
  		< input type=" checkbox" name= "hobbys" value=" 女孩">女孩
  		<input type=" checkbox" name= "hobbys" value="代码">代码
  		<input type="checkbox" name="hobbys" value="唱歌">唱歌
  		<input type="checkbox" name= "hobbys" value="电影">电影
  		<br>
  		<input type=" submit">
  	</form>
  </div>
  ~~~

- 之后在java源码目录下编写LoginServlet.class文件

  ~~~java
  protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws Serv1etException, IOException {
      //后台接收中文乱码问题
  	req. setCharacterEncoding("utf-8");
      resp. setCharacterEncoding("utf-8");
  	String username = req . getParameter( S: "username");
  	String password = req. getParameter( S: "password");
  	String[] hobbys = req. getParameterValues( s: "hobbys");
  	System.out.print1n("==========================");	
  	System.out.println(username);
  	System.out.println(password);
  	System.out.print1n(Arrays. toString(hobbys));
  	System.out.print1n("==========================");
  	//通过请求转发
  	req.getRequestDispatcher(req. getContextPath()+"/success.jsp").forward(req,resp);
  }
  ~~~

- 之后配置success.jsp文件

  ~~~jsp
  <body>
      <h1>登陆成功</h1>
  </body>
  ~~~

- 最后配置web.xml

  ~~~xml
  <serv1et>
  	<servlet-name>out</servlet-name>
  	<servlet-class>com.kuang.servlet.LoginServlet</servlet-class>
  </serv1et>
  <servlet-mapping>
  	<servlet-name>out </servlet-name>
  	<ur1-pattern>/out</ur1-pattern>
  </servlet-mapping>
  ~~~

连接tomcat输入：http://localhost:8080/LoginServlet/out 会出现login.html页面，输入信息，提交后会出现登录成功界面。控制台会打印处用户的输入信息。

[输入：](https://s4.ax1x.com/2022/03/05/b0Y5Hx.png)

​																	[<img src="https://s4.ax1x.com/2022/03/05/b0Y5Hx.png" alt="b0Y5Hx.png" style="zoom:33%;" />](https://imgtu.com/i/b0Y5Hx)

[结果：](https://s4.ax1x.com/2022/03/05/b0YTUK.png)

​																	[<img src="https://s4.ax1x.com/2022/03/05/b0YTUK.png" alt="b0YTUK.png" style="zoom:50%;" />](https://imgtu.com/i/b0YTUK)

#### 6.5 Request对象

- setAttribute(String name,Object o)方法

  > 该方法用于将一个对象与一个name属性关联后存储进ServletRequest对象中。

- setAttribute(String name)方法

  > 该方法用于将从ServletRequest对象中返回指定名称的属性对象。

- removeAttribute(String name)方法

  > 该方法用于从ServletRequest对象中删除指定名称的属性

- getAttributeNames()方法

  ~~~java
  Enumeration getAttributeNames()
  ~~~

  > 该方法返回ServletRequest对象中的所有属性名的Enumeration对象。可进行遍历。

## 五. Cookie

> 什么是Cookie
>
> Cookie 是浏览器访问服务器后，服务器传给浏览器的一段数据。 浏览器需要保存这段数据，不得轻易删除。此后每次浏览器访问该服务器，都必须带上这段数据。是一种客户端会话技术。

### 1. Cookie的常用方法

|                    方法                    |                             说明                             |
| :----------------------------------------: | :----------------------------------------------------------: |
|              String getName()              |                       返回Cookie的名称                       |
|       void setValue(String newValue)       |                   用于为Cookie设置一个新值                   |
|             String getValue()              |                       用于返回Cookie值                       |
|       ==void setMaxAge(int expiry)==       |         用于设置Cookie在浏览器客户端上保存的有效秒数         |
|            ==int getMaxAge()==             |         用于返回Cookie在浏览器客户端上保存的有效秒数         |
|        ==void setPath(String uri)==        |               用于设置该Cookie项的有效目录路径               |
|            ==String getPath()==            |               用于返回该Cookie项的有效目录路径               |
|     ==void setDomain(String pattern)==     |                    用于设置Cookie的有效域                    |
|           ==String getDomain()==           |                    用于返回Cookie的有效域                    |
|           void setVersion(int v)           |                 用于设置Cookie采用的协议版本                 |
|              int getVersion()              |                 用于返回Cookie采用的协议版本                 |
|      void setComment(String purpose)       |                  用于设置Cookie项的注解部分                  |
|            String getComment()             |                  用于返回Cookie项的注解部分                  |
|        void setSecure(boolean flag)        |          用于设置Cookie项是否只能使用安全协议的传送          |
|            Boolean getSecure()             |          用于返回Cookie项是否只能使用安全协议的传送          |
|       new cookie(String key，value)        | 用于创建一个cookie对象，key为cookie的名子，value为cookie要保存的数据 |
|  URLEncoder.encode(String str,String enc)  |         用于给数据编码，str为编码数据，enc为编码格式         |
| URLDecoder.decode (String str,String enc） |   用于给数据解码，和URLEncoder使用常用于解决cookie乱码问题   |

- setMaxAge和getMaxAge方法

  > 两个方法分别用于设置和返回Cookie在浏览器保持有效的秒数。
  >
  > 如果设置为一个正整数，则会将浏览器保存在本地硬盘中。从当前的时间开始，在没有超过指定的秒数之前这个cookie一直保持有效。如果设置的值为负整数，则浏览器会将Cookie保存的信息存储在浏览器的缓存中，当浏览器关闭时，cookie信息会被删除。如果设置为0时。则浏览器会立即删除这个Cookie信息。

- setPath和getPath

  > 这两个方法是针对Cookie的Path属性的。如果创建的cookie对象没有设置Path属性，那么该Cookie只对当前访问路径的目录及其子目录有效。如果想让某个Cookie项对站点的所有目录下的访问路径都有效，应调用Cookie对象的setPath()方法。将其setPath()属性设置为"/"

- setDomain和getDomain方法

  > 该方法是用于针对Cookie的domain属性的。domain属性用于指定浏览器的访问域。设置该属性时，其值必须以"."开头。值不区分大小写，默认情况下值为当前主机名。

### 2. Cookie实现登录记忆

可以使用Cookie技术显示用户上次访问时间。

- 创建CookieDemo.class文件

  ~~~java
  protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
      //服务器，告诉你，你来的时间，把这个时间封装成为一一个信件，你下次来，我就知道你来了
      //解决中文乱码
      req. setCharacterEncoding("utf-8");
      resp. setCharacterEncoding("utf-8"); 
      PrintWriter out = resp. getWriter();
      //Cookie,服务器端从客户端获取;
      Cookie[] cookies = req.getCookies(); //这 里返回数组，说明Cookie 可能存在多个
      //判断iCookie是否存在
      if (cookies !=nu1l){
          //如果存在怎么办
          out.write( s: "你上一次访问的时间是:");
          for (int i = e; i < cookies.1ength; i++) {
              Cookie cookie = cookies[i];
              //获取cookie的名字
              if (cookie.getName().equals("lastLoginTime")){
                  //获取cookie中的值
                  long lastLoginTime = Long. parseLong( cookie.getValue());
                  Date date = new Date(lastLoginTime);
                  out.write(date.toLocaleString());
              }
          }
      }else {
          out.write( s: "这是您第一次访问本站");
      }
      //服务给客户端响应一个cookie;
      Cookie cookie = new Cookie( name: "lastLoginTime",value: System.currentTimeMillis()+"");
      //Cookie cookie = new Cookie( name: "lastLoginTime",value: 		String.valueOf(System.currentTimeMillis()));	//valueOf可以将数据转换成字符串。
      //cookie有效期为一天
      cookie.setMaxAge( 24*60*60);
      //将创建的Cookie添加到客户端
      resp.addCookie(cookie);                                                  
  }
  ~~~

  > 用户访问网站后如果Cookie里没有值，则从`out.write( s: "这是您第一次访问本站");`开始执行。如果用户再次访问网站，这时候cookie里有值，直接输出。之后再继续执行26行之后的代码。

- 注册web.xml文件

  ~~~xml
  <serv1et>
      <servlet-name>CookieDemo</servlet-name>
      <servlet-class>com.kuang.servlet.CookieDemo</servlet-class>
  </serv1et>
  <servlet-mapping>
      <servlet-name>CookieDemo </servlet-name>
      <ur1-pattern>/out</ur1-pattern>
  </servlet-mapping>
  ~~~


将地址输入浏览器后即可看到上一次的访问时间。

## 六. ==session==

> 什么是session：
>
> 1. session可以将会话数据保存在服务器中，可以存储大量的数据。
> 2. 服务器会给每一个用户(浏览器)，创建一个session对象
> 3. 一个session独占一个浏览器对象，只要浏览器不关闭，这个session就一直存在
> 4. 用户登录之后整个网站都可以访问到他。

### 1. session方法介绍：

|                    方法                     |                             说明                             |
| :-----------------------------------------: | :----------------------------------------------------------: |
|               String getId()                |           用于返回当前HttpSession对象的会话标识号            |
|           long getCreationTime()            |         用于返回Session创建的时间，是以时间戳的方式          |
|         long getLastAccessedTime()          | 返回客户端最后一次发送Session相关的时间请求，是以时间戳的形式 |
|  long setMaxInactiveInterval(int interval)  | 设置当前HTTPSession对象可空闲的以秒为单位的最长时间，其实就是设置当前会话的默认超时间隔 |
|               boolean isNew()               |            判断当前HttpSession对象是否为新创建的             |
|               void invalidate               |                    强制使session对象无效                     |
|     ServletContext getServletContext()      | 返回Httpsession对象所属于的web应用程序对象，即代表当前web应用程序的ServletContext 对象。 |
| void setAttribute(String name,Object value) | 用于将一个对象与一个名称关联后存储到当前的HttpSession对象中  |
|            String getAttribute()            |        用于从当前的HttpSession对象中返回指定名称的值         |
|      void removeAttribute(String name)      |        用于从当前的HttpSession对象中删除指定名称的值         |

### 2. Session用法

> 将数据保存到Session并获取，入下是将一个值存入session再取出。

- 在包下创建一个类SessionDemo01用来设置session的值

  ~~~java
  protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
      //解决乱码问题
      req.setCharacterEncoding( "UTF-8");
      resp.setCharacterEncoding("UTF-8");
      resp.setContentType( "text/html ; charset=utf-8");
      //得到Session
      HttpSession session = req. getSession();
      //给Session中存东西
      session.setAttribute( name: "name", value: "史");
      //获取Session的ID
      String sessionId = session. getId();
      //判断iSession,是不是新创建
      if (session.isNew()){
          resp.getWriter().write( s: "session创建成功, ID: "+sessionId);
      }else
          resp.getWriter().write( s: "session以及在服务器中存在了, ID:"+sessionId);
  }
  //Session创建的时候做了什么事情;
  //Cookie cookie = new cookie( "JSESSIONID", sessionId);
  //resp.addCookie(cookie);
  ~~~

- 之后再创建一个SessionDemo02获取SessionDemo01中的值

  ~~~java
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
      //解决乱码问题
      req.setCharacterEncoding("UTF-8");
      resp.setCharacterEncoding("UTF-8");
      resp.setContentType("text/htm1; charset=utf-8");
      //得到Session
      HttpSession session = req.getSession();
      String name = ( String) session.getAttribute( name: "name");
      System.out.print1n(name);
  }
  ~~~

- 最后注册web.xml文件

  ~~~xml
  <serv1et>
      <servlet-name>set</servlet-name>
      <servlet-class>com.kuang.servlet.SessionDemo01</servlet-class>
  </serv1et>
  <servlet-mapping>
      <servlet-name>set </servlet-name>
      <ur1-pattern>/set</ur1-pattern>
  </servlet-mapping>
  
  
  <serv1et>
      <servlet-name>out</servlet-name>
      <servlet-class>com.kuang.servlet.SessionDemo02</servlet-class>
  </serv1et>
  <servlet-mapping>
      <servlet-name>out </servlet-name>
      <ur1-pattern>/out</ur1-pattern>
  </servlet-mapping>
  ~~~

在浏览器输入地址，先登录SessionDemo01将值保存再session中。之后再登录SessionDemo02将值取出。控制台打印处：`史`

### 3. 将对象存入session

> session与cookie最大的区别就是session可以存储对象。

- 建立一个Person类，记录年龄和名字

  ~~~java
  public class Person {
      private String name;
      private int age;
      public Person() {}
      public Person(String name, int age) {
          this. name = name;
          this.age = age;
      }
      public String getName() {
          return name ;
      }
      public void setName(String name) {
          this. name = name;
      }
      public int getAge() {
          return age ;
      }
      public void setAge(int age) {
          this.age = age;
      }
      public String toString( ) {
          return	"Person{" +
              	"name=' "+name+'\'+
             		",age="+age+
              	'}' ;
      }
  }
  ~~~

- 修改SessionDemo01中的`setAttribute`方法

  ~~~java
  protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
      //解决乱码问题
      req.setCharacterEncoding( "UTF-8");
      resp.setCharacterEncoding("UTF-8");
      resp.setContentType( "text/html ; charset=utf-8");
      //得到Session
      HttpSession session = req. getSession();|
      //给Session中存东西
      session.setAttribute( name: "name", new Person("史",20));
      //获取Session的ID
      String sessionId = session.getId();
      //判断iSession,是不是新创建
      if (session. isNew()){
          resp. getWriter() .write( s: "session创建成功, ID: "+sessionId);
      }else
          resp . getWriter() . write( s: "session以及在服务器中存在了, ID:"+sessionId);
  }
  //Session创建的时候做了什么事情;
  //Cookie cookie = new cookie( "JSESSIONID", sessionId);
  //resp. addCookie(cookie);
  ~~~

- 修改SessionDemo02中的`getAttribute`方法

  ~~~java
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
      //解决乱码问题
      req.setCharacterEncoding("UTF-8");
      resp.setCharacterEncoding("UTF-8");
      resp.setContentType("text/htm1; charset=utf-8");
      //得到Session
      HttpSession session = req.getSession();
  	Person person = (Person) session.getAttribute( name: "name" ) ;
      System.out.println(person.toString());
  }
  ~~~


启动Tomcat输入地址，和上次一样，先登录SessionDemo01，再登录SessionDemo02，在控制会打印出`Person{name='史',age=20}`

### 4. session和cookie

区别：

> - Cookie是把用户的数据写给用户的浏览器，浏览器保存(可以保存多个)
> - Session把用户的数据写到用户独占Session中，服务器端保存(保存重 要的信息，减少服务器资源的浪费)
> - Session对象由服务创建;

session使用场景：

> - 保存一一个登录用户的信息;
> - 购物车信息;
> - 在整个网站中经常会使用的数据，我们将它保存在Session中;

cookie中的JSESSIONID

> 每次会话(如用户登录)，我们想让HTTP有记忆，就需要用到session的id来还原上次会话。但session的id如果存在服务器的内存中，太多会造成服务器崩溃，所以我们一般会将session的id存放在cookie中，名为`JSESSIONID`。然后设置cookie存在时间和session存活时间一致(默认30分钟)。此时当我们下一次用同样的浏览器访问时，请求头request会自动将cookie中的JSESSIONID提交到服务器，实现上次对话。

会话自动过期：

- 需要在web.xml文件中配置

  ~~~xml
  <!--设置Session默认的失效时间-->
  <session-config>
      <!--15分钟后Session自动失效，以分钟为单位-->
      < session-timeout>15</ session-timeout>
  </session-config>
  ~~~

[Session流程图：](https://s1.ax1x.com/2022/03/09/bW4Ch4.png)

​									[<img src="https://s1.ax1x.com/2022/03/09/bW4Ch4.png" alt="bW4Ch4.png" style="zoom:50%;" />](https://imgtu.com/i/bW4Ch4)

## 七. JSP

> JSP(Java Server Pages)是Servlet更高级别的扩展。在JSP文件中，HTML与java代码共存。JSP可以帮助简化页面的编写。
>
> HTML用于实现网页中静态内容，Java代码用于实现网页中动态内容显示。最终，JSP文件会通过Web服务器的Web容器编译成一个Servlet，用于处理各种请求。
>
> JSP特点：
>
> 1. 跨平台
> 2. 业务代码相分离：JSP可以将页面的开发与应用程序的开发分离。
> 3. 组件重用：JSP中可以使用JavaBean编写业务组件，在整个开发中都可以重用这个JavaBean。
> 4. 预编译：用户在第一次访问页面时，服务器对JSP页面编译一次。之后，编译好的代码会被保存，用户在下一次访问网页时，会直接执行编译好的代码。

### 1. JSP执行原理

> 执行过程：
>
> 1. 客户端发出请求
> 2. web容器将jsp转化为servlet代码（.java）
> 3. web容器将转化为servlet代码编译（.class）
> 4. web容器加载编译后的代码并执行
> 5. 将执行结果响应给客户端
>
> 其实JSP就是一个Servlet

[执行原理图：](https://s1.ax1x.com/2022/03/10/bhql0H.png)

​									[<img src="https://s1.ax1x.com/2022/03/10/bhql0H.png" alt="bhql0H.png" style="zoom:50%;" />](https://imgtu.com/i/bhql0H)

### 2. JSP基础语法

> 一个JSP页面可以包含指令标识、HTML代码、JavaScript代码、嵌入的Java代码、注释和JSP动作标识等内容。

下面介绍一个简单的JSP项目：

- 首先需要导入项目所需要的包，在web.xml文件中导入`Servlet-api`、`javax.servlet.jsp-api`、`jstl-api`及他的依赖包`standard`包

  ~~~xml
  <dependencies>.
      <!--Servlet-->
      <dependency>
          <groupId>javax . serv1et</ groupId>
          <artifactId>servlet-api< /artifactId>
          <version>2.5</version>
      </dependency>
      <dependency>
         <groupId>javax. servlet . jsp</ groupId>
         <artifactId>javax. servlet. jsp-api</artifactId>
         <version>2.3.3</version>
      </ dependency>
      <!-- https://mvnrepository. com/artifact/javax. servlet. jsp. jstl/jstl-api -->
      <dependency>
          <groupId>javax . serv1et . jsp. jst1</ groupId>
          <artifactId>jst1-api</artifactId>
          <version>1.2</version>
       </dependency>
       <!-- https ://mvnrepository. com/artifact/tagl ibs/standard -->
       <dependency>
          <groupId>taglibs</ groupId>
          <artifactId>standard</ artifactId>
          <version>1.1.2</version>
       </dependency>
   </dependencies>
  ~~~

  > Servlet-api：Servlet依赖
  >
  > javax.servlet.jsp-api：JSP依赖
  >
  > jstl-api：JSTL表达式的依赖
  >
  > standard：standard标签库
  >
  > 后两个之后会介绍用途

- 之后创建一个index.jsp文件

  ~~~jsp
  <%@ page contentType="text/html ; charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>$Tit1e$</title>
      </head>
      <body>
          hello
      </body>
  </html>
  ~~~

之后启动Tomcat输入地址页面会出现：`hello`字样。

#### 2.1 JSPScriptlets

> JSPScriptlets是一个脚本片段，我们可以将，java代码嵌入到`JSP`中。

嵌入语法：

~~~jsp
<% java代码(可以是变量、方法、表达式) %>
~~~

示例：

~~~jsp
<%@ page contentType="text/html ; charset=UTF-8" language="java" %>
<html>
    <head>
        <title>$Tit1e$</title>
    </head>
    <body>
        <% 
        	int a=1,b=2;
        	out.println(a+b)
        %>
    </body>
</html>
~~~

启动Tomcat页面输入结果为：`3`

也可以嵌套：

~~~jsp
<%@ page contentType="text/html ; charset=UTF-8" language="java" %>
<html>
    <head>
        <title>$Tit1e$</title>
    </head>
    <body>
		<%
			for(inti=0;i<5;i++){
    	%>
			<h1>He11o, World <%=i%>< /h1>
    	<%
    		}
   		%>
    </body>
</html>
~~~

[运行结果：](https://s1.ax1x.com/2022/03/10/b4rrcV.png)

​																	[<img src="https://s1.ax1x.com/2022/03/10/b4rrcV.png" alt="b4rrcV.png" style="zoom:33%;" />](https://imgtu.com/i/b4rrcV)

#### 2.2 声明标识

> 在JSPScriptlets中可以进行属性的定义，也可以输出内容，**但不能进行方法的定义**。如果想进行方法定义可以使用声明标识定义全局变量和方法。声明的作用域比JSPScriptlets更高。

声明标识格式：

~~~jsp
<%!
	定义变量或方法
%>
~~~

> 在JSP中定义的都是成员方法、成员变量、静态方法、静态变量、静态代码块等。

示例：

~~~jsp
<%@ page contentType="text/html ; charset=UTF-8" language="java" %>
<html>
    <head>
        <title>$Tit1e$</title>
    </head>
    <body>
        <%! 
        	public int print(){
                int a=1,b=2;
                return a+b;
            }
        %>
    	</br>
    	<%
    		out.println(print());
    	%>
    </body>
</html>
~~~

启动Tomcat页面输入结果为：`3`

==注意：==声明标识`<%! %>`是用来定于属性和方法的，JSPScriptlets`<% %>`主要是用于输出内容的。

#### 2.3 JSP表达式

> JSP表达式用于向页面输出信息。

格式如下：

~~~jsp
<%= expression %>
~~~

> 上述语法中`expression`可以是java语言中任意完整的表达式。该表达式的最终运算结果将被转化成一个字符串。

示例：

~~~jsp
<%@ page contentType="text/html ; charset=UTF-8" language="java" %>
<html>
    <head>
        <title>$Tit1e$</title>
    </head>
    <body>
        <%
        	int a=1,b=2;	
        %>
    </body>
    	<%= a+b %></br>
</html>
~~~

启动Tomcat输入地址会出现以下内容：`3`

#### 2.4 JSP注释

> JSP的注释和java一样，但同时又多了隐藏注释。主要用于在客户端页面不显示代码注释，以提高安全性。

注释方法：

~~~jsp
<%--注释内容--%>
~~~

### 3. JSP指令

> 为了设置JSP页面中的一些信息，JSP定义了`page`、`include`、`taglib`3种指令。

#### 3.1 page指令

> 在JSP页面中，经常需要对某些特性进行描述。例如页面的编码方式、JSP页面采用的语言等。这些特性可以通过page指令实现。

~~~jsp
<%@ page 属性名1="属性值1" 属性名2="属性值2"....... %>
~~~

> page：声明指令名称
>
> 属性：用于指定JSP页面的某些特征。page指令提供一系列与JSP页面相关的属性。

page指令的常用属性：

|   属性名称   |       取值范围        |                             描述                             |
| :----------: | :-------------------: | :----------------------------------------------------------: |
|   language   |         java          |            指定JSP页面所用的脚本语言，默认为java             |
|    import    |    任何包名、类名     | 指定在JSP页面翻译成Servlet源文件中导入的包或类。该指令是唯一一个可以声明多次的page指令。且可以引用多个类，中间用英文逗号隔开 |
|   session    |      true、false      | 指定该JSP是否内置Session对象，如果为true，则说明内置Session对象，可以直接使用，否则没有内置Session对象。默认为true。 |
| isErrorPage  |      true、false      | 指定该页面是否为错误处理页面，为true，则JSP内置一个Exception对象的exception，可直接使用。默认情况下为false |
|  errorPage   | 某个JSP页面的相对路径 | 指定一个错误页面，如果该JSP程序抛出一个未捕捉的异常，则转到errorPage指定的页面。errorPage指定页面isErrorPage属性值为true，且内置的Exception对象为未捕捉的异常 |
| contentType  |    有效的文档类型     | 指定当前JSP页面的MIME类型和字符编码。如：HTML为text/html；纯文本格式为text/plain；JPG图像为image/jpeg；GIF图像为image/gif；Word文档为application/msword |
| pageEncoding |       当前页面        |                       指定页面编码格式                       |

示例：

~~~jsp
<%@ page language="java" contentType=“text/html; charset="UTF-8" pageEncoding="UTF-8" %>
<%@ page import="java.awt.*" %>
~~~

自定义错误界面：

- 自定义404和500界面，首先配置error404.jsp文件

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>404</title>
      </head>
      <body>
          <img src="${pageContext.request.contextPath}/image/404.png">
      </body>
  </html>
  ~~~

- 接着配置error500.jsp文件

  ~~~jsp
  <%@ page contentType="text/html; charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>500</title>
      </head>
      <body>
          <img src="${pageContext.request.contextPath}/image/error500.png">
      </body>
  </html>
  ~~~

- 配置错误的index.jsp文件

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>404</title>
      </head>
      <body>
          <% int a=1/0 %>
      </body>
  </html>
  ~~~

  > 因为除数不能为0，所以代码会报错

- 最后配置web.xml文件

  ~~~xml
  <?xml version="1.0" encoding="UTF-8"?>
  <web-app xmlns="http://java.sun.com/xml/ns/javaee"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://xmnls.jcp.org/xml/ns/javaee
                               http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
           version="4.0"
           metadata-complete="true">
      <error-page>
          <error-code>500</error-code>
          <location>/error/error500.jsp</location>
      </error-page>
  
      <error-page>
          <error-code>404</error-code>
          <location>/error/error404.jsp</location>
      </error-page>
  </web-app>
  ~~~

最后启动Tomcat输入：http://localhost:8080/index.jsp显示如下

[500错误界面：](https://s1.ax1x.com/2022/03/10/b4Hy79.png)

​										[<img src="https://s1.ax1x.com/2022/03/10/b4Hy79.png" alt="b4Hy79.png" style="zoom:50%;" />](https://imgtu.com/i/b4Hy79)

随便输入一个界面会显示资源不存在(404)。如下

[404错误界面：](https://s1.ax1x.com/2022/03/10/b4Htkn.png)

​													[<img src="https://s1.ax1x.com/2022/03/10/b4Htkn.png" alt="b4Htkn.png" style="zoom:50%;" />](https://imgtu.com/i/b4Htkn)

#### 3.2 include指令

> 实际开发时，JSP页面有时需要包含包含另一 个JSP页面，这时可以通过include指令实现。

include具体语法格式如下：

~~~jsp
<%@ include file="被包含的文件地址" %>
~~~

> 需要注意的是插入文件的路径一般不以"/"开头，而是使用相对路径

示例：

- 先创建一个header.jsp,用于放一个网站公共的头部

  ~~~jsp
  <%@ page contentType=" text/html ; charset=UTF-8" language="java" %>
  <h1>我是header< /h1>
  ~~~

- 再创建一个footer.jsp页面用于公共页面底部

  ~~~jsp
  <%@ page contentType=" text/html;charset=UTF-8" language="java" %>
  <h1>我是Footer< /h1>
  ~~~

- 创建一个index.jsp用于存放网页主体，然后引用公共的header.jsp和footer.jsp

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          <%@ include file="common/header.jsp"%>
          <h1>网页主体</h1>
          <%@ include file=" common/footer.jsp"%>
      </body>
  </html>
  ~~~

最后启动Tomcat输入地址显示一下结果

[include引用公共样式结果：](https://s1.ax1x.com/2022/03/10/b4q3Is.png)

​													[<img src="https://s1.ax1x.com/2022/03/10/b4q3Is.png" alt="b4q3Is.png" style="zoom:33%;" />](https://imgtu.com/i/b4q3Is)

需要注意的是`include`指令是将页面合二为一。我们更多是使用一下方法：

~~~jsp
<jsp: include page="/common/header.jsp"/>
<h1>网页主体</h1>
<jsp: include page="/common/ footer.jsp"/> 
~~~

运行后结果和上面一样。但该方法是将页面拼接起来。这个方法用的比较多。

#### 3.3 taglib指令

> 在JSP文件中可以通过taglib指令标识该页面中所有使用的标签库，同时引用标签库并指定标签的前缀。在页面中引用标签库后，就可以通过前缀来引用标签库中的标签。

指令格式如下：

~~~jsp
<%@ taglib prefix="tagPrefix" uri="tagURI" %>
~~~

> prefix：用于指定标签的前缀，该前缀不能命名为：jsp、jspx、java、sun、servle和sunw
>
> uri：用于指定标签库文件的存放位置。

在页面中引用JSTL中的核心标签库：

~~~jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
~~~

### 4. JSP动作元素

> JSP动作元素用于控制JSP的行为，执行一些常见的的JSP页面动作。通过动作元素可以实现使用多行Java代码才能实现的效果。例如：包含页面文件、实现请求转发等。

#### 4.1 包含文件元素

> 再JSP页面中，`<jsp:include>`动作元素用于向当前页面引入其他文件，被引入的文件可以是动态文件，也可以是静态文件。效果类似与`include指令`

具体语法格式如下：

~~~jsp
<jsp:include page="URL" flush="true/false" />
~~~

> page：用于指定被引文件的相对路径。
>
> flush：用于指定是否将当前页面的输出内容刷新到客户端。默认为false

#### 4.2 请求转发元素

> `<jsp:forward>`动作元素可以将当前请求转发到其他web资源(如：HTML页面、JSP页面、和Servlet等)，执行请求转发后，当前页面将不再执行，而是执行该元素指定的目标页面。

`<jsp:forward>`格式如下：

~~~jsp
<jsp:forward page="relativeURL"/>
~~~

> 在上述语法中，page属性用于指定请求转发到的资源的相对路径，该目录的目标文件必须是当前应用的内部资源。

示例：

- 先编写一个实现转发功能的`jspforword.jsp`文件。

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          <jsp:forward page="welcom.jsp"/>        
      </body>
  </html>
  ~~~

- 之后编写`welcome.jsp`文件

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          你好，欢迎进入首页，当前时间是：
          <%out.print(new java.util.Date()); %>
      </body>
  </html>
  ~~~

启动Tomcat输入：http://localhost:8080/Demo/jspforword.jsp后界面显示：`你好，欢迎进入首页，当前时间是：Sat Jun 27 16:50:08`

由此可知jspforword.jsp转发了welcome.jsp的内容

#### 4.3 param子标签

> 该标签是forward的子标签，表示请求转发后会将param标签中的值跟在地址后面

创建一个为jsptag.jsp的文件：

~~~jsp
<jsp: forward page= "/jsptag2.jsp">
    <jsp: param name="name" value= "shi"></jsp:param>
    <jsp:param name="age" value="20"></jsp:param>
</jsp:forward>
~~~

启动Tomcat输入地址后地址会变为http://localhost:8080/jsptag.jsp?name=shi&age=20

### 5. JSP隐式对象

> 再JSP页面中，有一些对象需要频繁使用，如果每次都重新创建这些对象会很麻烦，所以JSP提供了9个隐式(内置)对象，它们是JSP默认创建的，可以直接在JSP页面中使用。

9个隐式对象如下：

|  **对象**   |                           **描述**                           |
| :---------: | :----------------------------------------------------------: |
|   request   |                **HttpServletRequest**类的实例                |
|  response   |               **HttpServletResponse**类的实例                |
|     out     |       **PrintWriter**类的实例，用于把结果输出至网页上        |
|   session   |                   **HttpSession**类的实例                    |
| application | **ServletContext**类的实例，与应用上下文有关，所有用户的共享信息 |
|   config    |                  **ServletConfig**类的实例                   |
| pageContext | **PageContext**类的实例，提供对JSP页面所有对象以及命名空间的访问 |
|    page     |                  类似于Java类中的this关键字                  |
|  Exception  | **Exception**类的对象，代表发生错误的JSP页面中对应的异常对象 |

 #### 5.1 out对象

> out对象是 javax.servlet.jsp.JspWriter 类的实例，用来在response对象中写入内容。
>
> 可以在page指令中使用buffered='false'属性来轻松关闭缓存。
>
> JspWriter类包含了大部分java.io.PrintWriter类中的方法。不过，JspWriter新增了一些专为处理缓存而设计的方法。还有就是，JspWriter类会抛出IOExceptions异常，而PrintWriter不会。

out对象方法：

|           **方法**           |         **描述**         |
| :--------------------------: | :----------------------: |
|  **out.print(dataType dt)**  |     输出Type类型的值     |
| **out.println(dataType dt)** | 输出Type类型的值然后换行 |
|       **out.flush()**        |        刷新输出流        |

> 注意：out和PrintWrite区别是，out对象通过print语句写入数据后，直到整个JSP页面结束，才会将输入缓冲区中的数据真正写入servlet引擎。而`respond.getWrite().print()`则是把数据直接写入Servlet引擎缓冲区，Servlet引擎按照缓冲区中的数据存放顺序输出。

而有时候我们需要将`out`对象中的数据直接写入缓存区，这时候就要用到`page`指令来设置缓存区大小为`0kb`。这样就可以直接将数据写入Servlet引擎缓存。

~~~jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" buffer="0kb" %>
<html>
    <head>
        <title>Tit1e</title>
    </head>
    <body>
        
        <% out.println("第一行<br/>");
    		response.getWrite().println("第二行<br />");
    	%>
    </body>
</html>
~~~

> 这样out对象就会比`respond.getWrite().print()`语句先输出。

#### 5.2 pageContext

> 再JSP页面中，使用pageContext对象可以获取JSP的其他8个隐式对象。它代表了当前JSP页面的运行环境，并提供了一系列用于获取其他隐式对象的方法。方法如下：

|                方法                |           说明            |
| :--------------------------------: | :-----------------------: |
|         JspWriter getOut()         |   用于获取out的隐式对象   |
|          Object getPage()          |  用于获取Page的隐式对象   |
|    ServletRequest getRequest()     |  用于获取Request隐式对象  |
|   ServletResponse getResponse()    | 用于获取Response隐式对象  |
|      HttpSession getSession()      |  用于获取session隐式对象  |
|      Exception getException()      | 用于获取exception隐式对象 |
|  ServletConfig getServletConfig()  |  用于获取config隐式对象   |
| ServletContext getServletContext() |  获取application隐式对象  |

**注意：**`application`和`servletContext`，是一样的，但application用在jsp中，servletContext用在servlet中。

但是更多的时候我们会用到pageContext存储数据方法：

|                        方法                         |                  说明                  |
| :-------------------------------------------------: | :------------------------------------: |
| void setAttribute(String name,Object obj,int scope) |     用于设置pageContext对象的属性      |
|     Object getAttribute(String name,int scope)      |     用于获取pageContext对象的属性      |
|          void removeAttribute(String name)          | 用于删除**所有**范围内名称为name的属性 |
|     void removeAttribute(String name,int scope)     |   用于删除指定范围内名称为name的属性   |
|          Object findAttribute(String name)          | 用于从4个域对象中查找名称为name的属性  |

> 上表列举了pageContext对象的属性操作相关方法，其中，name是指定的属性名称，参数scope指定的是属性的作用范围。而pageContext对象作用范围有4个值：

|           作用域名            |        说明         |
| :---------------------------: | :-----------------: |
|    pageContext.PAGE_SCOPE     |    表示页面范围     |
|   pageContext.REQUEST_SCOPE   |    表示请求范围     |
|   pageContext.SESSION_SCOPE   |    表示会话范围     |
| pageContext.APPLICATION_SCOPE | 表示web应用程序范围 |

#### 5.3 四大作用域的属性和作用域范围

- **pageContext（page域）：**

  > 1. page域指当前的jsp页面,作用范围是整个JSP页面，是四大作用域中最小的一个。
  > 2. 在pageContext中可以存数据，可利用setAttribute(String name,Object value,int scope)。
  > 3. pageContex的生命周期是这个页面的运行时间，若你关掉这个页面，页面运行结束，pageContext就会消亡，数据也会失效。
  >
  > 使用情况：只适合在一个页面中使用，在一个页面中定义变量，和保存在此页面中有用的数据。

- **request(request域):**

  > 1. request是指一次请求，即当用户访问web服务器的时候，web服务器会生成request和response对象，然后在service方法调用，完成用户的请求和对用户的响应。作用范围整个请求链。
  > 2. **request域中可以存数据**，可利用setAttribute(String name,Object value,int scope)。
  > 3. **request的生命周期是请求的周期**，若请求一直转发下去，其生命并不会结束。当整个请求结束，request生命结束。在request保存的数据也会失效。
  >
  > 使用情况：用于一次请求在不同页面间的操作及参数传递，如表单的参数传递。

- **session(session域)：**

  > 1. session是指一次会话，当用户首次访问服务器时，服务器会根据每一个浏览器的请求创建一个session对象，每个用户有每个的session对象，相当于身份证，保存在服务器中。借助cookie技术来传递id属性，就可以在每次访问中找到自己的session。作用范围是一次会话。
  > 2. **session域中可以存数据**，可利用setAttribute(String name,Object value,int scope)。
  > 3. session的生命周期是在服务器正常的情况下，在第一次调用request.getSession()方法时到销毁该session时结束。默认情况是30分钟。当然也可以设置session的maxage来改变生命周期。生命结束，数据会丢失。
  >
  > 使用情况：主要是网站用户的信息，购物车。

- **application(ServletContext）：**

  > 1. application即是servlet中的ServeltContext。application作用范围：整个Web应用。
  > 2. **ServletContext可以存数据，只要设置一次，整个web应用都可以访问到数据。**
  > 3. ServletContext生命周期在服务器启动时创建，在服务器关闭时销毁。
  >
  > 使用情况：每个用户都可以访问的数据，或者多个客户端共享数据。例如购物网站的首页，商品页等。

==作用域从小到大为：==**PageContext（jsp页面），ServletRequest（一次请求），HttpSession（一次会话），ServletContext（整个web应用）。**

## 八. EL表达式

> EL可以简化JSP开发中的对象引用，从而规范页面代码，增强程序的可读性和可维护性。
>
> EL除了语法简单和使用方便外，还具有以下特点：
>
> - EL可以与JavaScript语句结合使用。
> - EL可以自动进行类型转换。如果想通过EL获取两个字符串数值(例如 numberl和number2)的和，可以直接通过“+”符号进行连接(例如$(numberl+number2；)。
> - EL不仅可以访问一般变量，还可以访问JavaBean中的属性、嵌套属性和集合对象。
> - 在EL中，可以执行算术运算、逻辑运算、关系运算和条件运算等。
> - 在EL中，可以获取pageContext对象，进而获取其他内置对象。
> - 在使用EL进行除法运算时，如果除数为0，则返回表示无穷大的Infinity，而不返回错误。
> - 在EL中，可以访问JSP的作用域(request、 session、application和page)。

### 1. EL语法格式

> EL以`${}`为标签进行书写

格式：

~~~jsp
${表达式}
~~~

示例：

- 首先建立一个Myservlet存储用户的账号和密码

  ~~~java
  protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
      //解决乱码问题
      req.setCharacterEncoding( "UTF-8");
      resp.setCharacterEncoding("UTF-8");
      resp.setContentType( "text/html ; charset=utf-8");
      req.setAttribute("username","itcast")
      req.setAttribute("password","123")
      RequestDispatcher dispacher=request.geRequestDispatcher("/myjsp.jsp")
      dispacher.forward(request,reposen)
  }
  ~~~

- 在web目录下建立一个myjsp的jsp文件，用来该页面输出Myservlet所存储的信息。

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          用户名：<%=request,getAttribute("username")%><br/>
          密码：<%=request,getAttribute("password")%><br/>
      </body>
  </html>
  ~~~

启动Tomcat服务器输入地址：http://localhost:8080/serv/Myservlet之后页面输出：`用户名：itcast 密码：123`

- 对myjsp.jsp文件进行修改，使用EL表达式

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          用户名：${username}<br/>
          密码：${passwod}<br/>
      </body>
  </html>
  ~~~

启动Tomcat服务器输入地址：http://localhost:8080/serv/Myservlet之后页面输出：`用户名：itcast 密码：123`。可以看出代码简化了不少。

#### 1.1 EL中的标识符

> 在EL中，经常要使用一些符号标记一些名称，如变量名、自定义函数名等。EL中的标识符可以由**大小写字母，数字和下划线组成**。
>
> 遵循一下规范：
>
> 1. 不能以数字开头
> 2. 不能是EL中的关键字。
> 3. 不能是EL中的隐式对象。
> 4. 不能包含单引号、双引、减号和正斜线(/)等特殊字符

#### 1.2 EL中的关键字

|  关键字名  | 说明 |
| :--------: | :--: |
|    and     |      |
|     or     |      |
|    not     |      |
|     eq     |      |
|     ne     |      |
|     lt     |      |
|     gt     |      |
|     le     |      |
|     ge     |      |
|    true    |      |
|   false    |      |
|    null    |      |
| instanceof |      |
|   empty    |      |
|   empty    |      |
|    div     |      |
|    mod     |      |

#### 1.3 EL中的变量

> EL中的变量就是一个基本的存储单元。不用事先定义就可以直接使用。EL可将变量映射到一个对象上

~~~jsp
${product}
~~~

> product就是一个变量，通过表达式${product}就可以访问变量product的值

#### 1.4 EL中的常量

> EL中的常量又称为字面量，指不可修改的数据。

- 布尔常量

  > 常用来区分一个事物的正反两面。它有两个值，分别是true和false

- 整型常量

  > 整型常量与Java中的十进制整型常量相同。他的取值范围是java语言中定义的常量范围。

- 浮点数常量

  > 浮点数常量用整数部分加小数部分表示，也可以用指数形式表示。如1.2和1.2E4都是合法的浮点数常量。

- 字符串常量

  > 字符串常量是用单引号或双引号引起来的一连串字符。因为字符串常量需要用单引号或双引号引起来。所以字符串本身包含的引号需要用反斜杠`(\)`进行转义。即`\"`表示的就是双引号。
  >
  > 注意：如果被双引号引起来，则字符串里双引号需要转义。如`"ab'4c\"d5\\e"`表示的字符串时`ab'4c"d5\e`。
  >
  > ​			如果被单引号引起来，则字符串里的单引号需要转义。如`'ab\'4c"d5\\e`表示的字符串是`ab'4c"d5\e`

- Null常量

  > Null常量用于表示变量引用的对象为空，它只有一个值，用null表示

#### 1.5 EL访问数据

> EL提供了两种运算符的操作数据，分别是点运算符`.`和方括号运算符`[]`，并且这两种运算符的功能相同。

- 点运算符`.`

  > 该运算符用于访问JSP页面中的某些对象的属性，例如JavaBean对象中的属性、List集合中的属性、Array数组中的属性等。
  >
  > 点运算符作用就是访问对象的属性值。

  用法如下：

  ~~~jsp
  ${customer.name}
  ~~~

- 中括号运算符`[]`

  > EL中的中括号运算符与点运算符功能相同，都用于访问JSP页面中的某些对象属性。当获取的属性名中包含一些特殊符号，例如"+"、"-"等非字母数字的符号，就只能使用中括号运算符访问该属性。

  ~~~jsp
  ${user["My-name"]}
  ~~~

这两种运算符在实际运用情况如下：

- 点运算符和中括号运算符在某种情况下可以互换，例如`${student.name}`等价于`${student["name"]}`。
- 中括号运算符还可以访问List集合或数组中指定索引的某个元素，例如`${uesers[0]}`用于访问集合或数组中第一个元素。
- 中括号运算符和点运算符可以互相使用，例如表达式`${users[0].ueserName}`可以访问集合或数组中的第一个元素的userName属性

#### 1.6 EL中的运算符

> EL支持简单的运算，例如(+)、(-)、等。为此，在EL中提供了多种运算符。根据运算方式的不同。EL中的运算符包括一下几种。

- 算术运算符

  > EL中的算术运算符用于对整数和浮点数的值进行算数运算。

  | 算数运算符 | 说明 |     算数表达式     | 结果 |
  | :--------: | :--: | :----------------: | :--: |
  |     +      |  加  |      ${10+2}       |  12  |
  |     -      |  减  |      ${10-2}       |  8   |
  |     *      |  乘  |      ${10*2}       |  20  |
  |   /(div)   |  除  | ${10/2}或`$`{10/2} |  5   |
  |   %(mod)   | 取模 | ${10%2}或`$`{10%2} |  0   |

- 比较运算符

  > 可以用来比较两个操作数的大小，操作数可以是各种常量、EL表达式、EL变量等。

  | 算数运算符 |   说明   |       算数表达式       | 结果  |
  | :--------: | :------: | :--------------------: | :---: |
  |   ==(eq)   |   等于   | ${10==2}或`$`{10 eq 2} | false |
  |   !=(ne)   |  不等于  | ${10!=2}或`$`{10 ne 2} | true  |
  |   <(lt)    |   小于   | ${10<2}或`$`{10 lt 2}  | false |
  |   >(gt)    |   大于   | ${10>2}或`$`{10 gt 2}  | true  |
  |   <=(le)   | 小于等于 | ${10<=2}或`$`{10 le 2} | false |
  |   >=(ge)   | 大于等于 | ${10>=2}或`$`{10 ge 2} | true  |

  > 为了避免与JSP页面的标签产生冲突，我们通常使用括号内的表示方式。但要注意，如果运算符后面是数字，在运算符和数字之间至少有一个空格，如`${1lt 2}`。如果运算符后面有其他符号，则不能加空格，例如`${1lt(2+1)}`

- 逻辑运算符

  > EL中的逻辑运算符用于对结果为布尔类型的表达式进行运算，运算的结果仍然是布尔类型。

  | 算数运算符 |  说明  |             算数表达式              | 结果  |
  | :--------: | :----: | :---------------------------------: | :---: |
  |  &&(and)   | 逻辑与 | ${true&&false}或`$`{true and false} | false |
  |  \|\|(or)  | 逻辑或 | ${true||false}或`$`{true or false}  | true  |
  |  ！(not)   | 逻辑非 |       ${!true}或`$`{not true}       | false |

- empty运算符

  > 在EL中，判断对象是否为空，可以通过empy运算符实现，该运算符是一个前缀运算符，即empty运算符位于操作数前方，用于确定一个对象或变量是否为空。

  empy运算符的语法格式如下：

  ~~~jsp\
  ${empty expression}
  ~~~

  > expression用于指定要判断的变量或对象。定义两个request范围内的变量user和user1，分别设置他们的值为bull和" "如：

  ~~~jsp
  <%request.setAttribute("user","");%>
  <%request.setAttribute("user1",null);%>
  <%--通过empty运算符判断user和user1是否为空--%>
  ${empty user}
  ${empty user1}
  ~~~

  一个变量或对象为null或空，代表的意义是不同的。null表示这个变量没有指明任何对象，而空表示这个变量所属的对象内容为空，例如空字符串、空的数组或者空的list容器。

- 条件运算符

  > EL中的条件运算符(?:)用于执行某种条件的判断，它类似与Java语言中的if-else语句。语法格式如下：

  ~~~jsp
  ${A?B:C}
  ~~~

  > 如果A的结果为true，就执行表达式B，否则就执行表达式C。

### 2. EL隐式对象

> 为了能够获得Web应用程序中的相关数据，EL提供了11个隐式对象，这些对象类似于JSP的内置对象，可以直接通过对象名进行各种操作。在EL隐式对象中，除了PageContext是JavaBean对象，相对于javax.jsp.PageContext类型，其他隐式对象都相对于java.util.Map类型。这些隐式对象可以分为页面上下文对象、访问作用于范围的隐式对象和访问环境信息的隐式对象3种。

|   隐式对象名称   |                             描述                             |
| :--------------: | :----------------------------------------------------------: |
|   pageContext    |               对应于JSP页面中的pageContext对象               |
|    pageScope     |              代表page域中用于保存属性的Map对象               |
|   requestScope   |             代表request域中用于保存属性的Map对象             |
|   sessionScope   |             代表session域中用于保存属性的Map对象             |
| applicationScope |           代表application域中用于保存属性的Map对象           |
|      param       |             表示一个保存了所有请求参数的Map对象              |
|   paramValues    | 表示一个保存了所有请求参数的Map对象，它对于某个请求参数， 返回的是一个string类型数组 |
|      header      |          表示一个保存了所有http请求头字段的Map对象           |
|   headerValues   | 表示一个保存了所有http请求头字段的Map对象，返回string类型数组 |
|      cookie      |              表示一个保存了所有cookie的Map对象               |
|    initParam     |         表示一个保存了所有web应用初始化参数的map对象         |

> pageContext可以获取其他10个隐式对象，pageScope、requestScope、sessionScope、applicationScope是用于获取指定域的隐式对象；param和paramValues是用于获取请求参数的隐式对象；header和headerValues是用于获取HTTP请求响应头的隐式对象；cookie是用于获取Cookie信息的隐式对象；initParam是用于获取Web应用初始化信息的隐式对象。

#### 2.1 pageContext对象

> 为了获取JSP页面的隐式对象，可以使用EL中的pageContext隐式对象。pageContext隐式对象用法：

~~~jsp
${pageContext.response.characterEncoding}
~~~

> pageContext对象用于获取response对象中的characterEncoding属性

#### 2.2 Web域相关对象

>   EL表达式中的`pageScope`、`requestScope`、`sessionScope`和`applicationScope`四个隐式对象分别用于访问JSP页面的page、request、session、application四个域中的属性。例如，表达式`${pageScope.userName}`返回page作用域中的userName属性的值，表达式${sessionScope.bookName}返回session作用域中的bookName属性的值。
>
> ==注意：==在EL表达式中也可以不使用这些隐式对象来指定查找域，而是直接引用这些域中的属性名称。例如，表达式${userName}就会在page、request、session、application这四个作用域内按顺序依次查找userName属性，直到找到为止。

#### 2.3 访问环境信息的隐式对象

>  EL表达式中的隐式对象param和paramValues用于获取客户端访问JSP页面时传递的请求参数的值，由于HTTP协议允许使用一个请求参数名出现多次，即一个请求参数可能会有多个值，所以，EL表达式提供了param和paramValues这两个隐式对象来分别获取请求参数的某个值和所有值。
>
> Param隐式对象用于返回一个请求参数的某个值，如果同一个请求参数有多个值，则返回第一个参数的值。paramValues隐式对象用于返回一个请求参数的所有值，返回结果为该参数的所有值组成的字符串数组，例如表达式${paramValues.username[0]}用于返回数组中第一个元素的值。

示例：

创建一个param.jsp文件

~~~jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>Tit1e</title>
    </head>
    <body>
        <form action="${pageContext.request.contextPath}/param.jsp">
            num1:<input type="text" name="num1" /><br/>
            num2:<input type="text" name="num" /><br/>
            num3:<input type="text" name="num" /><br/><br/>
            <input type="submit" name="提交" /><&emsp>
            <input type="submit" name="重置" /><hr/>
            num1:${param.num1}<br/>
            num2:${paramValues.num[0]}<br/>
            num3:${paramValues.num[1]}<br/>
        </form>
    </body>
</html>
~~~

启动Tomcat输入地址http://localhost:8080/Demo/param.jsp访问页面。之后输入三个数字，分别是10、20、30，然后点击提交按钮，

[param结果：](https://s1.ax1x.com/2022/03/15/bxoRC6.jpg)

​												[<img src="https://s1.ax1x.com/2022/03/15/bxoRC6.jpg" alt="bxoRC6.jpg" style="zoom:33%;" />](https://imgtu.com/i/bxoRC6)

#### 2.4 cookie隐式对象

> EL表达式中的隐式对象cookie是一个代表所有Cookie信息的Map集合，Map集合中元素的关键字为各个Cookie的名称，值则为对应的Cookie对象。使用cookie隐式对象可以访问某个Cookie对象，这些Cookie对象则是通过调用HTTPServletRequest.getCookies()方法得到的，如果多个Cookie共用一个名称，则返回Cookie对象数组中的第一个Cookie对象。例如，要访问一个名为userName的Cookie对象，可以使用表达式${cookie.userName}。

cookie对象用法示例如下：

~~~jsp
获取cookie对象的信息：${cookie.userName}					
获取cookie对象的名称：${cookie.userName.name}
获取cookie对象的值：${cookie.userName.value}
~~~

#### 2.5 initParam隐式对象

> EL表达式中的initParam是一个代表Web应用程序中的所有初始化参数的Map对象，每个初始化参数的值是ServletContext.getInitParameter(String name)方法返回的字符串。使用initParam获取参数代码如下：

~~~jsp
${initParam.参数名}
~~~

使用方法如下：

- 在Demo项目中配置web.xml文件，配置一个初始化参数author：

  ~~~xml
  <context-param>
      <param-name>author</param-name>
      <param-value>author的值为：</param-value>   
  </context-param>
  ~~~

- 在项目的web目录下创建名为initParams的jsp文件

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          author的值为：${initParam.author}
      </body>
  </html>
  ~~~

启动Tomcat输入地址访问initParams.jsp文件，窗口会显示：`author的值为：hello`

## 九. JSTL

> JSTL包含5类标准标签库，分别是`核心标签库`、`国际化\格式化标签库`、`SQL标签库`、`XML标签库`和`函数标签库`
>
> 在使用JSTL之前需要将`jstl-api`及他的依赖包`standard`包导入至`WEB-INF`的`lib`目录下。
>
> 在Tomcat的lib目录下也要引入`standard`包和`jstl`包，否则可能会无法执行。

### 1. 核心标签库

> 核心标签是最常用的 JSTL标签。引用核心标签库的语法如下：

~~~jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
~~~

标签：

|        标签         |                             描述                             |
| :-----------------: | :----------------------------------------------------------: |
|    ==`<c:out>`==    |              用于在JSP中显示数据，就像<%= ... >              |
|    ==`<c:set>`==    |                         用于保存数据                         |
|  ==`<c:remove>`==   |                         用于删除数据                         |
|     `<c:catch>`     |      用来处理产生错误的异常状况，并且将错误信息储存起来      |
|    ==`<c:if>`==     |                 与我们在一般程序中用的if一样                 |
|  ==`<c:choose>`==   |        本身只当做`<c:when>`和`<c:otherwise>`的父标签         |
|   ==`<c:when>`==    | `<c:choose>`的子标签，用来判断条件是否成立，与switch语句一样 |
| ==`<c:otherwise>`== | `<c:choose>`的子标签，接在`<c:when>`标签后，当`<c:when>`标签判断为false时被执行 |
|    `<c:import>`     |        检索一个绝对或相对 URL，然后将其内容暴露给页面        |
|  ==`<c:forEach>`==  |                基础迭代标签，接受多种集合类型                |
|   `<c:forTokens>`   |             根据指定的分隔符来分隔内容并迭代输出             |
|     `<c:param>`     |               用来给包含或重定向的页面传递参数               |
|   `<c:redirect>`    |                     重定向至一个新的URL.                     |
|    ==`<c:url>`==    |               使用可选的查询参数来创造一个URL                |

#### 1.1 表达式标签

> JSTL的核心标签库包含了很多表达式标签，比较常用的两个表达式标签为`<c:out>`和`<c:remove>`标签。

- `<c:out>`标签

  > 在JSP页面中，最后常见的操作就是向页面输出一段文本信息，`<c:out>`标签作用就是将一段文字内容或表达式的结果输出到客户端。如果`<c:out>`标签输出的文本内容中包含需要进行转义的特殊文字，`<c:out>`或默认对他们进行HTML编码转换后再输出。

  该标签的使用方法如下：

  |   属性    |                             说明                             |
  | :-------: | :----------------------------------------------------------: |
  |   value   |                    用于指定输出的文本内容                    |
  |  default  | 用于指定当value属性为null时所输出的默认值，如果没有默认值则输出空字符串，该属性是可选的(方括号中的属性都是可选的) |
  | escapeXml | 属性用于指定是否将>、<、&等特殊字符进行HTML编码转换后输出，默认为true |

  该标签有两种表示方法：

  1. 在没有标签体的情况

     ~~~jsp
     <c:out value="value" [default="defaultvalue"] [escapeXml="{true|false}"] />
     ~~~

  2. 有标签体的情况

     ~~~jsp
     <c:out value="value" [escapeXml="{true|false}"] >defaultvalue</c:out>
     ~~~

  示例Demo.jsp：

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          userName属性的值为：
          <c:out value="${param.userName}" default="unknow"/><br/>
          <%--<c:out value="${param.userName}"/>unknow</c:out>--%>
      </body>
  </html>
  ~~~

  > 在启动Tomcat后输入地址后两个都会显示`userName属性的值为：unknow`。如果将地址换为http://localhost:8080/Demo.jsp?userName=admin浏览则会显示`userName属性的值为：admin`

- `<c:remove>`标签

  > 该标签用于移除指定的JSP范围内的变量。

  | 属性  |                             描述                             |
  | :---: | :----------------------------------------------------------: |
  |  var  |                    用于指定要移除的变量名                    |
  | scope | 用于指定变量的有效范围，可选值有page、request、session、和applicabtion，默认值为page。如果在该标签中没有指定变量的有效范围，那么将在page、request、session、和applicabtion的范围内查找要移除的变量并移除。例如，在一个页面中，存在不同范围的两个同名变量，当不指定范围时移除该变量，这两个范围内的变量都将被移除。因此，在移除变量时最好指定变量的有效范围。 |

  ~~~jsp
  <c:remove var="name" [scope="范围"]/>
  ~~~

#### 1.2 流程控制标签

>  该系列标签用于使用控制语句进行条件判断。如果要在jsp页面中进行条件判断，就需要使用`<c:if>`标签。该标签专用于判断。

该标签有两种使用方式：

该标签的使用方法如下：

| 属性  |                  说明                   |
| :---: | :-------------------------------------: |
| test  |           用于设置逻辑表达式            |
|  var  |      用于指定逻辑表达式中的变量名       |
| scope | 用于指定var变量的作用域范围，默认为page |

1. 没有标签体的情况：

   ~~~jsp
   <c:if test="testCondition" var="result" [scope="{page|request|session|application}"]/>
   ~~~

2. 有标签体的情况：

   ~~~jsp
   <c:if test="testCondition" var="result" [scope="{page|request|session|application}"]>
   	body content
   </c:if>
   ~~~

示例coreif.jsp：

~~~jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>Title</title>
    </head>
    < body>
        <h4>if测试</h4>
        <hr>
        <form action="coreif.jsp" method="get">
            <%--EL表达式获取表单中的数据${param.参数名}--%>
            <input type= "text" name= "username" value="${param.username }"/>
            <input type= "submit" value="登 录"/>
        </form>

        <%--判断如果提交的用户名是管理员，则登录成功--%>
        <c:if test="${param.username=='admin'}" var="isAdmin">
            <c:out value="管理员欢迎您! "/>
        </c:if>
        <%--自闭合标签--%>
        <c:out value="${isAdmin}"/>
    </body>
</html>
~~~

启动Tomcat输入地址后显示如下内容：

[运行结果：](https://s1.ax1x.com/2022/03/18/qk3BuT.png)

​													[<img src="https://s1.ax1x.com/2022/03/18/qk3BuT.png" alt="qk3BuT.png" style="zoom:50%;" />](https://imgtu.com/i/qk3BuT)

#### 1.3 流程控制标签2(switch标签)

> `<c:choose>`标签用于指定多个条件选择的组合边界、它必须与`<c:when>`、`<c:otherwise>`标签一起使用。

- `<c:choose>`标签

  > `<c:choose>`标签没有属性，在它的标签体中只能嵌套一个或多个`<c:when>`标签、零个或一个`<c:otherwise>`标签，并且同一个`<c:choose>`标签中所有的`<c:when>`子标签必须出现在`<c:otherwise>`标签之前，其语法格式如下：

  ~~~jsp
  <c:choose>
  	Body(<when> and <otherwise> subtags)
  </c:choose>
  ~~~

- `<c:when>`标签(相当于switch中的case)

  > 该标签只有一个test属性，该属性的值为布尔类型。test属性支持动态值，其值可以是一个条件表达式，如果条件表达式的值为true，就执行这个`<c:when>`标签的内容

  ~~~jsp
  <c:when>Body content</c:when>
  ~~~

- `<c:otherwise>`标签(相当于switch中的 default)

  > 该标签没有属性，它必须作为`<c:choose>`、标签最后的分支出现，当所有`<c:when>`标签的test条件都不成立时，才执行和输出该标签体的具体内容。

  ~~~jsp
  <c:otherwise>conditional block</c:otherwise>
  ~~~

三种标签综合案例

~~~jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>Tit1e</title>
    </head>
    <body>
        <c:choose>
            <%--通过 empty 运算符，可以实现在 EL 表达式中判断对象是否为空。该运算符用于确定一个对象或者变量是否为 null 或空。若为空或者 null，返回空字符串、空数组，否则返回 false。--%>
            <c:when test=${empty param.username}>
                unKonw user
            </c:when>
            <c:when test=${param.username=='itcast'}>
                ${param.username} is manage
            </c:when>
            <c:otherwise>
                ${param.username} is employee
            </c:otherwise>
        </c:choose>
    </body>
</html>
~~~

启动Tomcat输入地址：http://localhost:8080/Demo/index.jsp访问该网页，此时浏览器窗口会显示：`unKnow user`。这是因为在访问该页面时并没有给页面传递参数，如果输入http://localhost:8080/Demo/index.jsp?username=itcast，

则页面会输出：`itcast is manage `

#### 1.4 循环标签

> 在JSP页面经常要用到对集合对象进行循环迭代操作，为此，Coer标签库提供了一个`<c:foreEach>`标签。该标签专门用于迭代集合对象中的元素，并且能够重复执行标签体中的内容。

两种语法格式：

- 迭代包含多个对象的集合：

  ~~~jsp
  <c:forEach [var="varName"] items="coollection" [varStatus="varStatName"] [begin="begin"] [end="end"] 
             [step="step"]>
      body content
  </c:forEach>
  ~~~

- 迭代指定范围内的集合

  ~~~jsp
  <c:forEach [var="varName"] [varStatus="varStatusName"] begin="begin" end="end" [step="step"]>
      body conten
  </c:forEach>
  ~~~

> 在上述语法中，可以看到该标签有多个属性
>
> - var属性：用于将当前迭代到的元素保存到page域中的名称。
> - items属性：用于指定将要迭代的集合对象
> - varStatus属性：用于指定将当前迭代状态信息的对象保存到page域中的名称，使用该属性会得到一下信息：
>   - count：表示元素在集合中的序号，从1开始计数
>   - idnex：表示当前元素在集合中的索引，从0开始
>   - first：表示当前是否为集合中的第一个元素
>   - last：表示当前是否为集合中的最后一个元素
> - begin属性：用于指定从集合中的第几个元素开始遍历。
> - step属性：用于指定迭代的步长。
> - end属性：指定集合迭代结束位置。

示例：

~~~jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib uri="http://java.sun.com/jsp/jst1/core" prefix="c"%>
<html>
    <head></head>
    <body>
        <% String[] fruits = {"apple","orange","grape", "banana"};%> 
        String数组中的元素：
        <br/>
        <c:forEach var="name" items="<%=fruits%>">
            ${name}<br/>
        </c:forEach>
        <%
        Map userMap = new HashMap();
        userMap.put("Tom"，"123") ;
        userMap.put("Lina", "123") ;
        userMap.put("Make","123");
        %>
        <hr/>
        HashMap集合中的元素：
        <br/>
        <c:forEach var="entry" items="<%=userMap%>">
            ${entry.key}&emsp;${entry.value}<br/>
        </c:forEach>
    </body>
</html>
~~~

启动Tomcat输入：http://localhost:8080/Demo/each.jsp后输出结果如下：
[forEach遍历结果：](https://s1.ax1x.com/2022/03/23/q3A4EV.jpg)

​							[<img src="https://s1.ax1x.com/2022/03/23/q3A4EV.jpg" alt="q3A4EV.jpg" style="zoom: 25%;" />](https://imgtu.com/i/q3A4EV)

示例(步长迭代)：

~~~jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib uri="http://java.sun.com/jsp/jst1/core" prefix="c"%>
<html>
    <head></head>
    <body>
        colorsList集合(指定迭代范围和步长)<bx/>
        <%
        List colorsList=new ArrayList();
        colorsList.add("red");
        colorsList.add("yellow");
        colorsList.add("blue");
        colorsList.add("green");
        colorsList.add("black");
        %>
        <c:forEach var="color" items="<%=colorsList%>" begin="1" end="3" step="2">
            ${color}&nbsp;
        </c:forEach>
    </body>
</html>
~~~

## 十. JavaBean

> 什么是JavaBean？
>
> 首先明确的是JavaBean是一种Java类，而且是一种特殊的、可重用的类。
>
> 必须具有无参数的构造器，所有的属性都是private的，通过提供setter和getter方法来实现对成员属性的访问。
>
> JavaBean的种类按照功能可以划分为可视化和不可视化两类。可视化的JavaBean就是拥有GUI图形用户界面的，对最终用户是可见的。不可视化的JavaBean不要求继承，它更多的被使用在JSP中，通常情况下用来**封装业务逻辑**、**数据分页逻辑**、**数据库操作**和**事物逻辑**等，这样可以实现业务逻辑和前台程序的分离，提高了代码的可读性和易维护性，使系统更健壮和灵活。随着JSP的发展，JavaBean更多的应用在非可视化领域，并且在服务器端应用方面表现出了越来越强的生命力。
>
> JavaBeans是Java中一种特殊的类，可以将多个对象封装到一个对象（bean）中。特点是可序列化，提供无参构造器，提供getter方法和setter方法访问对象的属性。名称中的“Bean”是用于Java的可重用软件组件的惯用叫法。

代码示例：

- User.java

  ~~~java
  package com.jyroy.javaBean;
  
  public class StudentsBean implements java.io.Serializable{
     private String firstName = null;
     private String lastName = null;
     private int age = 0;
  
     public StudentsBean() {
     }
     public String getFirstName(){
        return firstName;
     }
     public String getLastName(){
        return lastName;
     }
     public int getAge(){
        return age;
     }
  
     public void setFirstName(String firstName){
        this.firstName = firstName;
     }
     public void setLastName(String lastName){
        this.lastName = lastName;
     }
     public void setAge(int age) {
        this.age = age;
     }
  }
  ~~~

- 在web文件夹下创建一个index.jsp文件用于输入并提交数据

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <%@ taglib uri="http://java.sun.com/jsp/jst1/core" prefix="c"%>
  <html>
      <head>
          <title>登录界面</title>
      </head>
      <body>
          <form action="result.jsp"method="post">
              <table align="center" width="300" border="1" height="150">
                  <tr>
                      <td colspan="2"align="center"><b>登录页面</b></td>
                  </tr>
                  <tr>
                      <td align="right">用户姓：<input type="text" name="firstName"></input></td>
              	</tr>
          		<tr>
              		<td align="right">用户名：<input type="text" name="lastName"></input></td>
      			</tr>
  				<tr>
              		<td align="right">年龄：<input type="text" name="age"></input></td>
      			</tr>
  				<tr>
      				<td colspan="2" align="center"><input type="submit"/></td>
  				</tr>
  			</table>
  		</form>
  	</body>
  </html>
  ~~~

- 创建一个result.jsp文件用于接收index.jsp文件的内容，包括对用户验证名和密码的认证。

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <%@ taglib uri="http://java.sun.com/jsp/jst1/core" prefix="c"%>
  <html>
      <head></head>
      <body>
          <div alight="center">
          	<%
              	//String firstName=request.getParameter("firstName");
              	//String lastName=request.getParameter("lastName");
              	String firstName=${"firstName"};
              	String lastName=${"lastName"};
              	int age=${"age"};
              	User user=new User(firstName,lastName,age);
              	if(!user.getFirstName().eqyals("")&&!user.getLastName().eqyals("")&&!user.getAge().eqyals("")){
                      ${"恭喜您，登录成功"};
                  }else{
  					${"请输入正确的信息"}
                  }
              %>
          </div>
      </body>
  </html>
  ~~~

  启动Tomcat输入：http://localhost:8080/Demo/index.jsp页面会显示用户输入框，输入不为空的信息就会出现：`恭喜您，登录成功`如果输入空信息，就会出现：`请输入正确的信息`界面。

> 总的来说：
>
> 　JavaBean的编码规范
>
> - 　　提供一个公有的无参构造函数。
> - 　　需要被序列化并且实现了java.io.Serializable接口。
> - 　　该类的属性一般是私有（private）修饰的。
> - 　　可能有一系列的公有的"getter"或"setter"的访问器方法。
> - 　　该类是一个公有类，并且用package语句声明属于某一个包

### 1. 获取JavaBean属性信息

> 在JavaBean对象中，为了防止外部直接对JavaBean属性的调用，通常将JavaBean中的属性设置为私有属性。
>
> 在jsp页面中可以使用`<jsp:useBean>`标签示例化对象。通过`<jsp:getProperty>`标签获取JavaBean中的属性信息。通过`<jsp:setProperty>`标签设置属性值。

使用标签说明如下：

|       标签名        |                      描述                      |
| :-----------------: | :--------------------------------------------: |
|   `<jsp:useBean>`   | 标签示例化对象，设置获取属性值前需要示例化对象 |
| `<jsp:getProperty>` |            获取JavaBean中的属性信息            |
| `<jsp:setProperty>` |                   设置属性值                   |

标签使用方法如下：

- `<jsp:useBean>`标签

  ~~~jsp
  <jsp:useBean id="实例化类名" class="类路径"></jsp:useBean>
  ~~~

  > 其标签属性名有三个：
  >
  > id:代表jsp页面中的实例对象 通过这个对象引用类中的成员，如，id="wq", wq.成员();
  >
  > class: 代表JavaBean类，如： class="com.Test",引用com包中的Test类
  >
  > scope：指明了javabean的生存范围

- `<jsp:getProperty>`标签

  ~~~jsp
  <jsp:getProperty name="类名" property="属性名"></jsp:getProperty>
  ~~~

  > name属性用于指定JavaBean实例对象的名称，其值应与`<jsp:useBean>`标签的id属性值相同。
  >
  > property属性用于指定JavaBean实例对象的属性名。

- `<jsp:setProperty>`标签

  ~~~jsp
  <jsp:setProperty name="类名" property="属性名" value="属性值"></jsp:setProperty>
  ~~~

  > name属性用于指定JavaBean对象的名称。
  > property属性用于指定JavaBean实例对象的属性名。其值如果为`*`的意思就是将从页面中收集来的全部信息传递给javabean。
  >
  > value属性用于指定JavaBean对象的某个属性的值，value的值可以是字符串，也可以是表达式。为字符串时，该值会自动转化为JavaBean属性相应的类型，如果value的值是一个表达式，那么该表达式的计算结果必须与所要设置的JavaBean属性的类型一致。
  > param属性用于将JavaBean实例对象的某个属性值设置为一个请求参数值，该属性值同样会自动转换成要设置的JavaBean属性的类型。

示例：

- 创建People.java文件封装信息

  ~~~java
  public class People {
      private int id;
      private String name;
      private int age;
      private String address;
      public Peop1e() {}
      public People(int id, String name, int age, String address) {
          this.id = id;
          this.name = name;
          this.age = age;
          this. address = address;
      }
      public int getId() {
          return id;
      }
      public void setId(int id) {
          this.id = id;
      }
      public String getName() {
          return name;
      }
       public void setName(int id) {
          this.name = name;
      }
      public void setAge(String age) {
          this. name = name;
      }
       public String getAge() {
          return name;
      }
      public void setAddress(String address) {
          this. address = address;
      }
      public String getAddress(String address) {
          return address;
      }
  }
  ~~~

- 创建一个javabean.jsp获取和设置user.java文件中的信息

  ~~~jsp
  <%@ page import="com.Demo.pojo.People" %>
  <%@ page contentType= "text/html;charset=UTF-8" language= "java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          <%
          //People people = new People();
          //people.setAddress();
          //people.setId();
          //people.setAge();
          //people.setName();
          %>
          <jsp:useBean id="people" class="com.Demo.pojo.People" scope=" page" />
          <jsp:setProperty name="people" property="address" value="西安"/>
          <jsp:setProperty name=" people" property="id" value="1"/>
          <jsp:setProperty name="people" property="age" value="3"/>
          <jsp:setProperty name="people" property="name" value="shi"/>
  
          姓名: <jsp:getProperty name="people" property="name"/>
          id: <jsp:getProperty name="people" property="id"/>
          年龄: <jsp:getProperty name="peop1e" property="age"/>
          地址: <jsp:getProperty name="people" property="address"/>
      </body>
  </html>
  ~~~

启动Tomcat输入：http://localhost:8080/Demo/javabean.jsp页面显示结果如：`姓名:shi id:1 年龄:3 地址:西安`

==注意：可以使用 `<jsp:setProperty property="*"/>`的形式接收所有参数。==

### 2. JavaBean属性信息应用

#### 2.1 实现图书录入功能

- 首先在Demo的包下创建一个为Book的类，实现对图书的封装。该类相当于图书信息对象的JavaBean。

  ~~~java
  public class Book{
      private String bookName;
      private double price;
      private String author;
      public String getBookName(){
          return bookName;
      }
      public void setBookName(String bookName){
          this.bookName = bookName;
      }
      public double getPrice(){
          return price;
      }
      public void setPrice(double price){
          this.price =price;
      }
      public String getAuthor(){
          return author;
      }
      public void setAuthor(String author) {
          this.author = author;
      }
  }
  ~~~

- 在该项目的web目录下创建图书信息添加页面add.jsp，用于编写录入图书信息所需的表单。

  ~~~jsp
  <%@ page contentType= "text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>图书信息添加</title>
      </head>
      <body>
          <form action="info.jsp" method="post">
              <table align="center" width="400" height="200" border="1">
                  <tr＞
                       <td align="center" colspan="2" height="40"><b>添加图书信息</b></td>
              </tr>
          <tr>
              <td align="center">
                  名称：<input type="text"name="bookName">
              </td> 
          </tr>
          <tr>
              <td align="center">
                  价格：<input type="text" name="price"> 
              </td>
          </tr>
          <tr>
              <td align="center">
                  作者：<input type="text"name="author"> 
              </td>
          </tr>
          <tr>
              <td align="center" colspan="2">
                  <input type="submit"value="添加">
              </td>
          </tr>
          </table>
      </form>
  </body>
  </html>
  ~~~

  ==注意：可以使用 `<jsp:setProperty property="*"/>`的形式接收所有参数。==

- 在web目录下再编写一个名为info.JSP页面，用于接收index.jsp页面表单中的数据，将获取的数据输入到页面

  ~~~jsp
  <%@ page contentType= "text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>title</title>
      </head>
      <body>
          <%request.setCharacterEncoding("UTF-8");%>
          <jsp:useBean id="book" class="cn.itcast.Book" scope="page">
              <!--这里的*表示将add.jsp页面传递的参数全部传给类示例对象-->
              <jsp:setProperty name="book" property="*"></jsp:setProperty>
              <!--相当于下面的代码-->
              <jsp:setProperty name="book" property="bookName"></jsp:setProperty>
              <jsp:setProperty name="book" property="price"></jsp:setProperty>
              <jsp:setProperty name="book" property="author"></jsp:setProperty>
          </jsp:useBean>
          <table align="center" width="400">
              <tr>
                  <td align="center">名称：<jsp:getProperty property="bookName" name="book"/>
                  </td>
              </tr＞
              <tr>
              	<td align="center">价格：<jsp:getProperty property="price" name="book"/>
              	</td>
              </tr>
         		 <tr>
      			<td align="center">作者：<jsp:getProperty property="author" name="book"/>
      		</td>
     			</tr>
  		</table>
  	</body>
  </html>                                                              
  ~~~

启动Tomcat后，再浏览器页面输入：http://localhost:8080/Demo/add.jsp访问并输入信息，结果如下图所示：
[图书录入结果：](https://s1.ax1x.com/2022/03/27/q032ad.jpg)

​										[<img src="https://s1.ax1x.com/2022/03/27/q032ad.jpg" alt="q032ad.jpg" style="zoom:33%;" />](https://imgtu.com/i/q032ad)

#### 2.2 判断用户名是否有效

- 先创建一个为Username.java的类，用于封装用户信息。

  ~~~java
  public class Username{
      String reg="[a-zA-Z]";
      String regx="[a-zA-Z0-9_]";
      String username;
      Boolean isval;
      String tip;
      public String getTip(){
          return tip;
      }       	
  
      public void setTip(String tip){
          this.tip = tip;
      }
  
      public String getUsername(){
          return username;
      }
  
      public Boolean getIsval(){
          return isValid();
      }
  
      public void setIsval(Boolean isval){
          this.isval = isval;
      }
      public void setUsername(String username) {
          this.username = username;
      }
  
      public boolean isValid(){
          String name = getUsername();
          String firstname = String.valueOf(name.charAt(0));
          //首字符为字母
          if(firstname.matches(reg)){
              for(int i=1;i<name.length();i++) {
                  if(!String.valueOf(name.charAt(i)).matches(regx)){
                      setTip("用户姓名错误，只能由字母、数字和下画线组成！");
                      return false;
                  }
              }
              setTip("用户格式正确！");
              return true;
  
          }else{
              setrip("用户姓名错误，首字符必须为字母！")；
                  return false;
          }
      }
  }
  ~~~

- 编写用户输入用户名页面login.jsp

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java"%>
  <html>
      <head>
          <title>用户输入用户名页面</title>
      </head>
      <body>
          <form action="judge.jsp" method="post" style="font-size: 20px;">
              <1i>请输入用户名：<input type="text"name="username"/>只能由字母、数字或者下画线组成</li>
                  
              <li><input type="submit" name="submit" value="验证"/></li>
          </form>
      </body>
  </html>
  ~~~

- 编写用户名验证反馈界面`judge.jsp`，该页面判断用户名是否有效，并给出反馈

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java"%>
  <jsp:useBean id = "username" class ="cn.itcast.Username" scope="page">
      <jsp:setProperty name ="username" property="*"/>
  </jsp:useBean>
  <html>
      <head>
          <title>验证反馈页面</title>
      </head>
      <body>
          <ul style="font-size:20px;">
              <1i>输入的用户名为：<jsp:getProperty property= "username" name = "username"/></1i>
              <1i>&nbsp;&nbsp;&nbsp;是否有效：<jsp:getProperty property ="isval" name ="username"/> </li>
              <1i>&nbsp;&nbsp;&nbsp;提示信息：<jsp:getProperty property ="tip" name ="username"/></1i>
          </ul>
      </body>
  </html>
  ~~~

启动Tomcat然后访问：http://localhost:8080/Demo/login.jsp访问页面，输出结果如下：
[用户名判断运行结果：](https://s1.ax1x.com/2022/03/27/q0hvfs.jpg)										[![q0hvfs.jpg](https://s1.ax1x.com/2022/03/27/q0hvfs.jpg)](https://imgtu.com/i/q0hvfs)

### 3. MVC设计模式

> MVC设计模式将软件程序分为三个核心模块：`模型、试图、控制器`

- 模型(model)：

  > 负责业务处理(Service)：负责管理应用程序的业务数据、定义访问控制以及修改这些数据的业务规则。当模型的状态发生改变时，它会通知试图，发生改变、并为试图提供查询模型状态的方法。
  >
  > 数据持久层：负责增删改查(CRUD)，CRUD也会添加一个Dao层

- 试图(view)：

  > 负责展示数据：负责与用户进行交互，他从模型中获取数据向用户展示，同时也能将用户请求传递给控制器进行处理。当模型状态发生改变时，试图会对用户进行同步更新，从而保持与模型数据的一致性。
  >
  > 提供链接发起Servlet请求(a, form, im..)

- 控制器(controlle)：

  > 接收用户的请求(req:请求参数、Session信息...)：负责应用程序中处理用户交互的部分，它从试图中读取数据，控制用户输入，并向模型发送数据
  >
  > 之后交给业务层处理对应的代码，并控制试图跳转。

[MVC三层架构业务图：](https://s1.ax1x.com/2022/03/29/q6LFCn.png)

​								[<img src="https://s1.ax1x.com/2022/03/29/q6LFCn.png" alt="q6LFCn.png" style="zoom:50%;" />](https://imgtu.com/i/q6LFCn)

[MVC三个模块关系与功能：](https://s1.ax1x.com/2022/03/29/q6v9s0.jpg)									[<img src="https://s1.ax1x.com/2022/03/29/q6v9s0.jpg" alt="q6v9s0.jpg" style="zoom: 50%;" />](https://imgtu.com/i/q6v9s0)

#### 3.1 MVC模式编写用户注册程序

- 首先再项目的src目录下创建一个包，包下创建一个UserBean类用于封装用户信息。

  ~~~java
  public class UserBean{
      private String name //定义用户名
          private String password; //定义密码
      private String email; //定义邮箱
      public String getName(){
          return name;
      }
  
      public void setName(String name){
          this.name = name;
      }
  
      public String getPassword(){
          return password;
      }
  
      public void setPassword(String password){
          this.password = password;
      } 
      public String getEmail(){
          return email;
      }
  
      public void setEmail(String email){
          this.email = email;
      }
  
  }
  ~~~
  
- 编写一个RegisterFormBean.java类，用于封装注册表单信息。

  ~~~java
  import java.util.HashMap;
  import java.util.Map; 
  public class RegisterFormBean{
      private String name;//定义用户名
      private String password; //定义密码
  
      private String password2;//定义确认密码
      private String email; //定义邮箱
  
  
      //定义成员变量errors，用于封装表单验证时的错误信息
      private Map<String, String> errors = new HashMap<String, String>(); 
      public String getName(){
          return name;
      }
  
      public void setName(String name){
          this.name = name;
      }
  
      public String getPassword(){
          return password;
      }
  
      public void setPassword(String password){
          this.password = password;
      }
  
      public String getPassword2(){
          return password2;
      }
  
      public void setPassword2(String password2){
          this.password2 = password2;
      }
  
      public String getEmail() {
          return email;
      }
  
      public void setEmail(String email) {
          this.email = email;
      }
  
      public boolean validate() {
          boolean flag = true;
  
  
          if (name == null|| name.trim().equals("")) {
              errors.put("name"，"请输入姓名.");
              flag = false;
          }
  
  
          if(password == null || password.trim().equals("")){
              errors.put("password","请输入密码.");
              flag = false;
          }
          else if (password.length()>12|| password.length()<6){
              errors.put("password"，"请输入6-12个字符.");
              flag = false;
          }
  
          if(password != null && !password.equals(password2)){
              errors.put("password2"，"两次输入的密码不匹配.")；
                  flag = false;
          }
  
          // 对email 格式的校验采用了正则表达式
          if (email == null ||email.trim().equals("")){
              errors.put("email"，"请输入邮箱.");
              flag = false;
          }else if(!email.matches("[a-zA-20-9_-]+@[a-zA-20-9_-]+(\\.[a-zA-Z0-9_-]+)+")){
              errors.put("email"，"邮箱格式错误.")；
                  flag = false;
          }
          return flag;
      }
  
  
      // 向Map集合 errors 中添加错误信息
      public void setErrorMsg(String err,String errMsg){
          if ((err l= null) && (errMsg l= null)){
              errors.put(err, errMsg);
          }
      }
  
      //获取errors集合
      public Map<String, String> getErrors(){
          return errors;
      }
  
  }
  ~~~

  > 该JavaBean中除了定义了一些属性和成员变量外，还定义了三个方法。其中，setErrorMsg()方法用于向errors集合中存放错误信息，getErrors()方法用于获取封装错误信息的error集合，validate()方法用于对注册表单内个字段所填写的数据进行校验

- 创建一个工具类DBUtil.java

  ~~~java
  import java.util.HashMap;
  import cn.itcast.chapter08.model2.domain.UserBeani;
  public class DBUtil {
      private static DBUtil instance = new DBUtil();
      //定义users集合，用于模拟数据库
      private HashMap<String,UserBean> users = new HashMap<String,UserBean>(); 
      private DBUtil(){
          UserBean userl = new UserBean(); 
          // 向数据库(users)中存入两条数据
          user1.setName("Jack");
          userl.setPassword("12345678");
          userl.setEmail("jack@it315.org");
          users.put("Jack",user1);
          UserBean user2 = new UserBean();
          user2.setName("Rose");
          user2.setPassword("abcdefg");
          user2.setEmail("rose@it315.org");
          users.put("Rose ",user2) ;
      }
  
  
      public static DBUtil getInstance(){
          return instance; 
      }
  
      // 获取数据库(users)中的数据
      public UserBean getUser(String userName){
          UserBean user = (UserBean)users.get (userName) ;
          return user;
      }
  
      //向数据库(users)中插入数据
      public boolean insertUser(UserBean user){
          if(user == null){
              return false;
          }
  
          String userName=user.getName();
          if(users.get(userName)!=null){
              return false;
          }
          users.put(userName,user);
          return true;
      }
  }
  ~~~

  > DBUtil是一个单例类，它实现了两个功能：第一个功能是定义一个HashMap集合users，用于模拟数据库，并向数据库中存入两条学生信息；第二个功能是定义getUser()方法和insertUser()方法来操作数据库，其中getUser()方法用于获取数据库中的用户信息，insertUser()方法用于向数据库插入用户信息。需要注意的是，再insertUser()方法中，进行插入操作之前会先判断数据库中是否存在同名的学生信息。如果存在则不执行插入操作，返回false；如果不存在，则表示插入成功，返回true。

- 定义一个ControllerServlet.java类，用于处理用户请求

  ~~~java
  import java.io.IoException;
  import servletException;
  import 3sct htto.HttpServlet;
  import tavawcesvler htto.httpservletRequest;
  import javax.servlet.http.HttpServletResponse;
  import cn.itcast.chapter08.model2.domain.RegisterFormBean;
  import cn.itcast.chapter08.model2.domain.UserBean;
  import cn.itcast.chapter08.model2.util.DBUtil;
  import javax.servlet.annotation.WebServlet;
  @WebServlet (name="Contro_lerServlet",urlPatterns="/ControllerServlet") 
  public class ControllerServlet extends HttpServlet{
      public void doGet (HttpServletRequestrequest,
                         HttpServletResponse response)throws ServletException，IOException{
          this.doPost(request, response)
      };
      public void doPost(HttpServletRequest request,
                         HttpServletResponse response) throws ServletException, IOException {
          response.setHeader("Content-type","text/html;charset=GBK"); 
          response.setCharacterEncoding("GBK");
          // 获取用户注册时表单提交的参数信息
          String name = request.getParameter("name");
          String password=request.getParameter("password");
          String password2=request.getParameter("password2");
          String email=request.getParameter("email");
          // 将获取的参数封装到注册表单相关的RegisterFormBean 类中
          RegisterFormBean formBean = new RegisterFormBean();
          formBean.setName (name);
          formBean.setPassword(password);
          formBean.setPassword2(password2) ;
          formBean.setEmail(email);
          // 验证参数填写是否符合要求，如果不符合，转发到register.jsp重新填写
          if(!formBean.validate()){
              request.setAttribute("formBean",formBean) ;
              request.getRequestDispatcher("/register.jsp").forward(request, response);
              return;
          }
  
          //如果参数填写符合要求，则将数据封装到UserBean类中
          UserBean userBean = new UserBean();
          userBean.setName (name);
          userBean.setPassword(password);
          userBean.setEmail(email);
          //调用DBUtil类中的insertUser()方法执行添加操作，并返回一个boolean类型的标志
          boolean b= DBUtil.getInstance().insertUser(userBean);
          //如果返回false，表示注册的用户已存在，则重定向到register.jsp重新填写
          if(!b){
              request.setAttribute("DBMes"，"你注册的用户已存在")；
                  request.setAttribute("formBean",formBean);
              request.getRequestDispatcher("/register.jsp").forward(request, response);
              return;            
          }
  
          response.getWriter().print("恭喜你注册成功，3秒钟自动跳转")；
              // 将成功注册的用户信息添加到Session 中
              request.getSession().setAttribute("userBean", userBean);
          //注册成功后，3秒钟跳转到登录成功页面loginSuccess.jsp
          response.setHeader("refresh","3;url=loginSuccess.jsp");
      }
  }
  ~~~

  > 第27行代码创建的RegisterFormBean对象用于封装表单提交的信息，第33～53行代码是对RegisterFormBean对象进行校验，如果校验失败，则程序跳转到register.jsp注册页面，让用户重新填写注册信息；如果校验通过，那么注册信息就会封装到UserBean对象中，并通过DBUtil的insertUser( )方法将UserBean对象插入数据库。insertUser()方法有一个boolea类型的返回值，如果返回false，表示插入操作失败；如果返回 true，表示用户登录成功。第56行代码是将成功注册的用户信息添加到Session中。第58行代码是延时3秒跳转到登录成功页面loginSuccess.jsp。

- 编写register.jsp文件，该文件是用户注册的表单页面，用于接收用户的注册信息。

  ~~~jsp
  <%@page anguage="java" pageEncoding="GBK"%>
  <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01
  Transitional//EN" "http://www.w3.org/TR/htm14/loose.dtd">
  <html>
      <head>
          <title>用户注册</title>
          <style type="text/css">
              h3{
                  margin-left：100px;
              }
  
              #outer{
                  width：750px;
              }
  
              span{
                  color：#ff0000;
              }
  
              div{
                  height:20px; 
                  margin-bottom:10px;
              }
  
  
              .ch{
                  width:80px;
                  text-align: right;
                  float:left;
              }
  
              .ip{
                  width：500px;
                  float:left;
              }
              .ip>input{
                  margin-right：20px;
              }
  
              #bt{
                  margin-left:50px;
              }
  
              #bt>input{
                  margin-right:30px;
              }
  
          </style>
      </head>
      <body>
          <form action="/chapter08/ControllerServlet" method="post"y
                <h3>用户注册</h3>
      <div id="outer">
          <div>
              <div class="ch">姓名：</div>
              <div class="ip">
                  <input type="text" name="name" value="${formBean.name}"/>
                  <span>${formBean.errors.name}${DBMes}</span>
  
              </div>
          </div>
          <div>
  
              <div class="ch">密码：</div>
              <div class="ip">
                  <input type="text" name="password">
                  <span>${formBean.errors.password}</span>
              </div>
          </div>
          <div> 
              <div class="ch">确认密码：</div>
              <div class="ip">
                  <input type="text" name="password2">
                  <span>${formBean.errors.password2}</span>
              </div>
          </div>
          <div>
              <div class="ch">邮箱：</div>
              <div class="ip">
                  <inputtype="text" name="email" value="${formBean.email}">
                      <span>${formBean.errors.email}</span>
                      </div>
              </div>
              <div id="bt">
                  <input type="reset" value="重置"/>
                  <input type="submit" value="注册"/>
              </div>
          </div>
          </form>
      </body>
  </html>
  ~~~

- 创建名为loginSuccess.jsp文件，该文件是用户登录成功的显示页面

  ~~~jsp
  <%@ page language="java" pageEncoding="GBK" import="cn.itcast.chapter08.mode12.domain.UserBean" %>
  <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/htm14/loose.dtd">
  <html>
      <head>
          <title>login successfully</title>
          <style type="text/css">
              #main{
                  width：500px;
                  height:auto;
              }
              #main div{
                  width:200px;
                  height:auto;
              }
  
              ul{
                  padding-top:1px;
                  padding-left:1px;
                  list-style：none;
              }
  
          </style>
      </head>
      <body>
          <%
          if (session.getAttribute("userBean") == null){
              %>
          <jsp:forward page="register.jsp"/>
          <%
          return;
          }
          %>
          <div id="main">
              <div id="welcome">恭喜你，登录成功</div>
              <hr/>
              <div>您的信息</div>
              <div>
                  <ul>
                      <li>您的姓名：${userBean.name}</li>
                      <li>您的邮箱：${userBean.email}</li>
                  </ul>
              </div>
          </div>
      </body>
  </html>
  ~~~

  > 第25~32行代码是判断session域中是否存在以"userBean"为名称的属性，如果不存在，说明用户没有注册而直接访问这个页面，程序会跳转到register.jsp页面进行注册，否则表示用户注册成功。第33`~`43行代码是用户注册成功时在页面会显示注册用户的信息。

启动Tomcat输入：http://localhost:8080/Demo/register.jsp访问register.jsp注册页面，如果用户输入不规范，点击注册后会重新跳转该页面，并提示注册信息错误。如下图，用户输入两次密码不一致，且邮箱格式错误：

[用户输入错误信息：](https://s1.ax1x.com/2022/03/31/qWOEv9.jpg)

​												[<img src="https://s1.ax1x.com/2022/03/31/qWOEv9.jpg" alt="qWOEv9.jpg" style="zoom: 25%;" />](https://imgtu.com/i/qWOEv9)

当用户输入正确的信息注册成功后的界面如下：
[用户成功注册界面：](https://s1.ax1x.com/2022/03/31/qWOD2Q.jpg)												[<img src="https://s1.ax1x.com/2022/03/31/qWOD2Q.jpg" alt="qWOD2Q.jpg" style="zoom:25%;" />](https://imgtu.com/i/qWOD2Q)

当用户注册后，在以相同的用户名进行注册程序会跳转到register.jsp页面，并提示"你注册的用户已经存在"。

[用户重复注册结果：](https://s1.ax1x.com/2022/03/31/qWXiZt.jpg)

​											[<img src="https://s1.ax1x.com/2022/03/31/qWXiZt.jpg" alt="qWXiZt.jpg" style="zoom:25%;" />](https://imgtu.com/i/qWXiZt)

## 十一. Servlet高级特性

> 在Servlet高级特性中，Filter被称为过滤器，它位于客户端和处理程序之间，能够对请求和响应进行检查和修改，通常将请求拦截后进行一些通用操作，例如，过滤一些敏感词汇，统一进行字符编码和实施安全控制等。Filter好比现实中的污水净化设备，专门用于过滤污水杂志。

[Filter原理图：](https://s1.ax1x.com/2022/04/01/q5mjot.png)

​								[<img src="https://s1.ax1x.com/2022/04/01/q5mjot.png" alt="q5mjot.png" style="zoom:50%;" />](https://imgtu.com/i/q5mjot)

[Filter原理图：](https://s1.ax1x.com/2022/04/01/q5nW6g.jpg)							[<img src="https://s1.ax1x.com/2022/04/01/q5nW6g.jpg" alt="q5nW6g.jpg" style="zoom:25%;" />](https://imgtu.com/i/q5nW6g)

> 当客户端对服务器资源发送请求时，服务器会根据过滤器进行检查，如果客户的请求满足过滤规则，则对客户请求进行拦截，对请求头和请求数据进行检查或修改，并依次通过Filter链，最后把过滤后的请求交给处理程序。请求信息在过滤器链中可以被修改，也可以根据客户端的请求条件不将请求发往处理程序。
>
> 除了以上拦截功能外，Filter还可以提高程序得到性能，在web开发时，不同的web资源中的过滤操作可以放在同一个Filter中完成，这样可以不用多次编写重复的代码，从而提高程序的性能。

### ==1. Filter API==

Filter接口是编写过滤器必须要实现的接口，该接口定义了init()、doFilter()、destroy()、方法。下面介绍Filter方法。

|                           方法声明                           |                             描述                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|               init(FilterConfig filterConfig)                | init()方法是Filter的初始化方法，创建Filter实例后将调用init()方法。该方法的参数filterConfig用于读取Filter的初始化参数 |
| doFilter(ServletRequest request，ServletResponse response，FilterChain chain) | doFilter()方法用于完成实际的过滤操作，当客户的请求满足过滤规则时，Servlet容器将调用过滤器的doFilter()方法完成实际的过滤操作。doFilter()方法有多个参数，其中，参数request和response为web服务器或Filter链中的上一个Filter传递过来的请求和响应对象；参数chain代表当前Filter链的对象 |
|                          destroy()                           | 该方法用于释放被Filter对象打开的资源，例如关闭数据库的IO流。destroy()方法在Web服务器释放Filter对象之前被调用。 |

FilterConfig接口

> FilterConfig接口用于封装Filter的配置信息，在Filter初始化时，服务器将FilterConfig对象作为参数传递给Filter对象的初始化方法。FilterConfig接口的方法如下：

|               方法声明               |                      描述                      |
| :----------------------------------: | :--------------------------------------------: |
|        String getFilterName()        |                返回Filter的名称                |
|  ServletContext getServletContext()  | 返回FilterConfig对象中封装的ServletContext对象 |
|    String getinitParameterNames()    |           返回名为name的初始化参数值           |
| Enumeration getInitParameterNames()· |       返回Filter所有初始化参数名称的枚举       |

FilterChain接口

> FilterChain接口的doFilter()方法用于调用Filter链中的下一个过滤器，如果这个过滤器是链上的最后一个过滤器，则将请求提交给处理程序或将响应发送给客户端。

#### 1.2 Filter的声明周期

> Filter的生命周期可以分为：创建、执行、销毁三个阶段。

- 创建阶段

  > Web服务器启动的时候会创建Filter实例对象，并调用init()方法，完成对象的初始化。在一次完整的请求中，Filter对象只会被创建一次，init()方法也只会被执行一次。

- 执行阶段

  > 当客户端请求目标资源时，服务器会筛选出符合映射条件的Filter，并按照类名的先后顺序依次执行doFilter()方法。doFilter()方法可以被执行多次。

- 销毁阶段

  > 服务器关闭时，web服务器调用destroy()方法销毁Filter对象

#### 1.3 Filter实现

- 在包下创建一个名为Myservlet的类

  ~~~java
  import java.io.*;
  import javax.servlet.*;
  import javax.servlet.annotation.WebServlet;
  import javax.servlet.http.*;
  @WebServlet(name="MyServlet",urlPatterns="/MyServlet")
  public class MyServlet extends HttpServlet{
      public void doGet(HttpServletRequest request,HttpServletResponse response)
      throws ServletException, IOException{
          response.getWriter().println("Hello MyServlet");
      }
      
      public void doPost(HttpServletRequest request, HttpServletResponse response)
      throws ServletException, IOException{
          doGet(request, response);
      }
      
  }
  ~~~

- 在包下创建一个名为MyFilter的Filter的类，用于拦截MyServlet程序。

  ~~~java
  import java.io,*;
  importjavax.servlet.Filter;
  importjavax.servlet.*;
  import javax.servlet.annotation.WebFilter;
  @WebFilter(filterName ="MyFilter",urlPatterns="/MyServlet") 
  public class MyFilter implements Filter {
      public void init(FilterConfig fConfig) throws ServletException {
          // 过滤器对象在初始化时调用，可以配置一些初始化参数
      }
      public void doFilter(ServletRequest request,
                           ServletResponse response, 
                           FilterChain chain) throws IOException，ServletException{
          //用于拦截用户的请求，如果和当前过滤器的拦截路径匹配，该方法会被调用PrintWriter 
          response.getWrite().Write("Hello MyFilter");
      }
  
  }
  ~~~

启动Tomcat后输入：http://localhost:8080/Demo/Myservlet后页面输出如下：`Hello MyFilter`

==注意：当urlPatterns值为`*`时，表示该Web工程下的所有请求都会被拦截。==

> 可以看到用注解拦截了名叫`MyServlet`的程序。并将输出替换为MyFilter中的内容。注解`@WebFilter`常用属性如下：

|     属性名      |      类型      |                             描述                             |
| :-------------: | :------------: | :----------------------------------------------------------: |
|   filterName    |     String     |             指定过滤器名称，默认是过滤器类的名称             |
|   urlPatterns   |    String[]    |                 指定一组过滤器的URL匹配模式                  |
|      value      |    String[]    | 该属性等价于urlPatterns属性，urlPatterns和value属性不能同时使用 |
|  servletNames   |    String[]    | 指定过滤器将应用于哪些Servlet，取值必须是@WebServlet中的name属性的取值 |
| dispatcherTypes | DispatcherType | 指定过滤器的转发模式，具体取值包括：ERROR、FORWARD、INCLUDE、REQUEST |
|   initParams    | WebInitParam[] |                  指定过滤器的一组初始化数据                  |

拦截不同访问方式的请求

- REQUEST

  > 过滤器设置dispatcherTypes属性值为REQUEST时，如果用户通过RequestDispatcher对象的include()方法或forward()方法访问目标资源、那么过滤器不会被调用。

- INCLUDE

  > 如果用户通过RequestDispatcher对象的include()方法访问目标资源、那么过滤器将被调用。

- FORWARD

  > 如果用户通过RequestDispatcher对象的forward()方法访问目标资源、那么过滤器将被调用。

  - ERROR

  > 如果通声明式异常处理机制调用目标资源时，那么过滤器将会被调用。

- 使用方法

  ~~~java
  @WebFilter(filterName="Forward",urlPatterns="/out",dispatcherTypes=DispatcherType.FORWARD)
  ~~~

#### 1.4 Filter链

> 在一个Web应用程序中可以注册多个Filter，每个Filter都可以对某一个URL的请求进行拦截。如果多个Filter都对同一个URL的请求进行拦截，那么这些Filter就组成一个Filter链。Filter链使用FilterChain对象表示，FilterChain对象提供了一个 doFilter()方法，该方法的作用是让Filter链上的当前过滤器放行，使请求进入下一个Filter。

[Filter链拦截过程：](https://s1.ax1x.com/2022/04/02/qoHFkq.jpg)									[<img src="https://s1.ax1x.com/2022/04/02/qoHFkq.jpg" alt="qoHFkq.jpg" style="zoom:25%;" />](https://imgtu.com/i/qoHFkq)

> 当浏览器访问Web服务器中的资源时需要经过两个过滤器Filter1和Filter2，首先Filter1会对这个请求进行拦截，在Filter1过滤器中处理好请求后，通过调用Filter1的doFilter()方法将请求传递给Filter2，Filter2将用户请求处理后同样调用doFilter()方法，最终将请求发送给目标资源。当Web服务器对这个请求做出响应时，响应结果也会被过滤器拦截，拦截顺序与之前相反，最终响应结果被发送给客户端。

示例：

- 在包中创建两个过滤器`MyFilter1`,`MyFilter2`,这两个过滤器的实现如下

  ~~~java
  import java.io.;
  importjavax.servlet.*;
  importjavax.servlet.annotation.WebFilter;
  @WebFilter(filterName="MyFilter01",urlPatterns ="/MyServlet")
  public class MyFilter01 implements Filter{
      public void init(FilterConfig fConfig) throws ServletException {
          //过滤器对象在初始化时调用，可以配置一些初始化参数
      }
      public void doFilter(ServletRequest request, ServletResponse response,
                           FilterChain chain) throwsIOException,ServletException{
          //用于拦截用户的请求，如果和当前过滤器的拦截路径匹配，该方法会被调用
          PrintWriter out=response.getWriter();
          out.println("Hello MyFilter01");
          chain.doFilter(request,response);
      } 
      public void destroy(){
          //过滤器对象在销毁时自动调用，释放资源
      }
  
  }
  ~~~

- MyFilter2

  ~~~java
  import java.io.;
  importjavax.servlet.*;
  importjavax.servlet.annotation.WebFilter;
  @WebFilter(filterName="MyFilter02",urlPatterns ="/MyServlet")
  public class MyFilter01 implements Filter{
      public void init(FilterConfig fConfig) throws ServletException {
          //过滤器对象在初始化时调用，可以配置一些初始化参数
      }
      public void doFilter(ServletRequest request, ServletResponse response,
                           FilterChain chain) throwsIOException,ServletException{
          //用于拦截用户的请求，如果和当前过滤器的拦截路径匹配，该方法会被调用
          PrintWriter out=response.getWriter();
          out.println("MyFilter02 Before");
          chain.doFilter(request,response);
          out.println("MyFilter02 After");
      } 
      public void destroy(){
          //过滤器对象在销毁时自动调用，释放资源
      }
  
  }
  ~~~

> 在IDEA中重新启动Tomcat服务器，在浏览器地址栏中输入 http://localhost:8080/chapter09/MyServlet 访问 MyServlet类，浏览器窗口中显示的结果为：
>
> ~~~java
> Hello MyFilter01
> MyFilter02 Before
> Hello MyServlet
> MyFilter02 After
> ~~~
>
> MyServlet的请求首先被MyFilter01拦截，浏览器显示出 MyFilter01中的内容，然后请求又被MyFilter02拦截，直到MyServlet的请求被MyFilter02放行后，浏览器才显示出MyServlet中的内容。

#### 1.5 Filter统一处理乱码问题

- 在包下建立一个ShowServlet.java用于用于向网页输出信息。

  ~~~java
  @WebServlet("/show")
  public class ShowServlet extends HttpServlet {
      @Override
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
          //使用中文网页会显示乱码
          resp. getWriter().write( s: "你好呀，世界! |");
      }
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
          doGet(req,resp);
      }
  }
  ~~~

- 在建立一个ShowServlet2.java用于显示网页被拦截处理后的网页

  ~~~java
  @WebServlet("/Servlet/show")
  public class ShowServlet extends HttpServlet {
      @Override
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
          //使用中文网页会显示乱码
          resp. getWriter().write( s: "你好呀，世界! |");
      }
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
          doGet(req,resp);
      }
  }
  ~~~

- 编写一个EncodingFilter.java的类用来处理ShowServlet里的乱码

  ~~~java
  import java.io.;
  importjavax.servlet.*;
  importjavax.servlet.annotation.WebFilter;
  @WebFilter(filterName="MyFilter02",urlPatterns ="/Servlet/show")
  public class MyFilter01 implements Filter{
      public void init(FilterConfig fConfig) throws ServletException {
          //过滤器对象在初始化时调用，可以配置一些初始化参数
      }
      public void doFilter(ServletRequest request, ServletResponse response,
                           FilterChain chain) throwsIOException,ServletException{
          request. setCharacterEncoding("utf-8");
          response . setCharacterEncoding("utf-8"); 
          response. setContentType("text/html; charset=UTF-8");
          System. out . print1n( "CharacterEncodingFilter执行前....");
          chain. doFilter(request, response); //让我们的请求继续走，如果不写，程序到这里就被拦截挝
          System. out . print1n("CharacterEncodingFilter执行后....");
  
      } 
      public void destroy(){
          //过滤器对象在销毁时自动调用，释放资源
      }
  }
  ~~~

启动Tomcat输入：http://localhost:8080/Demo/show网页此时会显示乱码。当输入：http://localhost:8080/Demo/Servlet/show时网页会输出：`你好 世界`。

### 2. Listener监听

> 在web开发中Servlet提供了Listener(监听器)，专门用于监听Servlet时间。Listener在监听过程中会涉及几个重要的组成部分。具体如下：
>
> 1. 事件：用户的一个操作。例如：点击一个按钮、调用一个方法、创建一个对象等。
> 2. 事件源：产生事件的对象
> 3. 事件监听器：负责监听发生在事件源上的事件
> 4. 事件处理器：监听器的成员方法，当事件发生的时候会触发对应的处理器(成员方法)。当用户执行一个操作触发事件源上的事件时，该事件会被事件监听器听到，当监听到事件发生时，相应的事件处理器就会对发生的事件进行处理。
>
> 事件监听器的工作过程可以分为一下几个步骤：
>
> 1. 将监听器绑定到事件源，也就是注册监听器
> 2. 监听器监听到的事件发生时，会调用监听器的成员方法，将事件对象传递给事件处理器，即触发事件处理器。
> 3. 事件处理器通过事件对象获得事件源，并对事件源进行处理。、

#### 2.1 Listener API

> Listener有8个不同的监听器接口，分别监听不同的对象

|            接口类型             |                             描述                             |
| :-----------------------------: | :----------------------------------------------------------: |
|     ServletContextListener      |          用于监听ServletContext对象的创建与销毁过程          |
|       HttpSessionListener       |           用于监听HttpSession对象的创建和销毁过程            |
|     ServletRequestListener      |          用于监听ServletRequest对象的创建和销毁过程          |
| ServletContextAttributeListener |            用于监听ServletContext对象中的属性变更            |
|  HttpSessionAttributeListener   |             用于监听HttpSession对象中的属性变更              |
| ServletRequestAttributeListener |            用于监听ServletRequest对象中的属性变更            |
|   HttpSessionBindingListener    |     用于监听JavaBean对象绑定到HttpSession对象解绑的事件      |
|  HttpSessionActivationListener  | 用与监听HttpSession中对象活化(从硬盘到内存)和钝化(从内存到硬盘)的过程 |

*活化和钝化*：其实就是在用户访问的时候，假如服务器突然关闭了，这个时候，用户的session就不存在了，假如是购物网站，也就相当于，用户好不容易选好的物品，刚刚添加到购物车，结果，因为服务器的突然关闭一下，什么都没了，这样很不好，于是我们就需要实现会话的持久化。可以让我们在重新启动服务器之后用户的session还在服务器中存在！即用户session的东西还全部在。因为我们服务器在关闭的时候把用户的session存储到硬盘了(钝化)，在重新启动服务器之后，我们又从硬盘中恢复到内存中！（注意，只要用户还没关闭浏览器，那个session会一直存在用户的客户端的）然后启动后，用户的信息就不会丢失！

- Listener根据监听事件的不同可以分为三类：

  - 用于监听域对象创建和销毁的监听器：ServletContextListener接口、HttpSessionListener接口和ServletRequestListener接口
  - 用于监听域对象属性增加和删除的监听器：ServletContextAttributeListener接口、HttpSessionAttributeListener接口和ServletRequestAttributeListener接口
  - 用于监听绑定到HttpSession域中某个对象状态的事件监听器：HttpSessionBindingListener接口和HttpSessionActivationListener接口。

  在Servlet规范中，这三类事件监听器都定义了相应的接口，在编写监听器程序时只需要实现对应的接口即可。Web服务器会根据监听器所实现的接口把它注册到被监听的对象上，当被监听的对象触发监听器的事件处理器时。Web服务器就会调用监听器相关方法对事件进行处理。

#### 2.2 监听器事件用户统计

- 创建一个LinstenerCout.java用来监听在线人数

  ```java
  //注解不用写web.xml，这里表示在服务器启动后告诉Tomcat这是一个监听器。
  @WebListener
  public class OnlineCountListener implements HttpSessionListener {
      //创建session监听:看你的 -举-动
      //一旦创建Session就会触发一次这个事件!
          public void sessionCreated(HttpSessionEvent se) {
          ServletContext ctx = se. getSession() . getServletContext();
          System. out . println(se . getSession(). getId());
          Integer onlineCount = (Integer) ctx . getAttribute( name: "OnlineCount" );
          if (onlineCount==nu11){
              onlineCount = new Integer( value: 1);
          }else 
              int count = onlineCount.intValue( );
          onlineCount = new Integer( value: count+1);
          ctx. setAttribute( name: "OnlineCount",onlineCount );
  
          //销毁session监听
          // -旦销毁Session就会触发一次这个事件!
          public void sess ionDestroyed(HttpSess ionEvent se) {
              Serv1etContext ctx = se. getSession(). getServletContext();
              Integer onlineCount = (Integer) ctx. getAttribute( name: "OnlineCount"); 
              if (onlineCount==nu11){
                  onlineCount = new Integer( value: 0);
              }else {
                  int count = onlineCount . intValue();
                  onlineCount = new Integer( value: count-1);
              }
              ctx. setAttribute( name: "OnlineCount" , onlineCount);
          }
          /*
  Session销
  1.手动销毁getSession(). invalidate();
  2.自动销毁
  */
      }
  }
  ```

- 创建一个Show.jsp用来显示当前访问人数

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>$Tit1e$</title>
      </head>
      <body>
          <h1>当前有<span><%=this.getServletConfig().getServletContext().getAttribute(name:"OnlineCount")%></span>人在线</h1>
      </body>
  </html>
  ~~~

启动Tomcat输入：http://localhost:8080/Demo/Show.jsp页面显示结果如下：

[Listener监听访问人数：](https://s1.ax1x.com/2022/04/03/qT6UQx.png)

​																	[<img src="https://s1.ax1x.com/2022/04/03/qT6UQx.png" alt="qT6UQx.png" style="zoom:33%;" />](https://imgtu.com/i/qT6UQx)

#### 2.3 设置用户访问权限

- 首先在web目录下创建一个Login.jsp的文件用于获取用户信息

  ~~~jsp
  <%@ page contentType= "text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          <h1>登录</h1>
          <form action="/Servlet/login" method="post">
              <input type= "text" name= "username" >
              <input type=" submit">
          </form>
      </body>
  </html>
  ~~~

- 由于我们要大量用到用户登录的JSESSIONID所以我们要建立一个Constant.java类用来存储常量

  ~~~java
  public class Constant {
      public final static String USER_SESSION = "USER_SESSION";
  }
  ~~~

- 创建一个LoginServlet.java用于判断用户是否登录成功

  ~~~java
  @WebServlet("/Servlet/login")
  public class ShowServlet extends HttpServlet {
      @Override
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
          String username = req. getParameter( name: "username");
          if (username. equals(" admin")){ //登录成功，将SessionID标识存入会话
              req.getSession().setAttribute(Constant.USER_SESSION,req.getSession().getId());
              resp.sendRedirect( location: "/sys/success.jsp");
          }else { //登录失败
              resp. sendRedirect( location: "/error.jsp");
          } 
      }
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
          doGet(req,resp);
      }
  }
  ~~~

- 如果LoginServlet.java判断用户是admin则登录成功跳转至success.jsp页面

  ~~~jsp
  <%@ page contentType= "text/html ;charset=UTF-8" language= "java”%>
  <html>
      <head>
          <title>Tit1e</title>
      </head>
      <body>
          <h1>主页</h1>
          <p><a href="/servlet/logout">注销</a></p>
      </body>
  </html>
  ~~~

- 创建一个ServletLoginout.java的类用于实现注销账号(移除Session会话中的USER_SESSION)

  ~~~java
  @WebServlet("/Servlet/logout")
  public class ShowServlet extends HttpServlet {
      @Override
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
          Object user_session = req. getSession().getAttribute( name: USER_SESSION);
          if (user_session! =nu11){
              req.getSession().removeAttribute(name: USER_SESSION);
              resp.sendRedirect( location: "/Login.jsp");
          }
      }
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
          doGet(req,resp);
      }
  }
  ~~~

- 如果LoginServlet.java判断用户不是admin则跳转至error.jsp页面

  ~~~jsp
  <%@ page contentType="text/html ; charset=UTF-8" language="java" %>
  <html >
      <head>
          <title>Title</title>
      </head>
      <body>
          <h1>错误</h1>
          <h3>没有权限，用户名错误</h3>
          <a href="/Login.jsp">返回登录页面</a>
      </body>
  </html>
  ~~~

  > 此时用户可以直接粘贴success.jsp路径，跳转至登录成功界面，这显然不符合项目规则，所以我们要编写一个过滤器判断用户是否成功登录

- 创建一个SysFilter.java拦截重定向的success.jsp页面，判断用户是否的登录

  ~~~java
  import java.io.;
  import javax.servlet.*;
  import javax.servlet.annotation.WebFilter;
  @WebFilter("/Sys/*")
  public class MyFilter01 implements Filter{
      public void init(FilterConfig fConfig) throws ServletException {
          //过滤器对象在初始化时调用，可以配置一些初始化参数
      }
      public void doFilter(ServletRequest request, ServletResponse response,
                           FilterChain chain) throwsIOException,ServletException{
          // ServletRequest
          HttpServletRequest request = (HttpServletRequest) req; 
          HttpServletResponse response = (HttpServletResponse) resp;
          //判断用户是否已经登陆
          if (request.getSession().getAttribute(Constant.USER_SESSION)==nu11){
              response.sendRedirect( location: "/error.jsp");
              chain. doFilter(request,response);
          } 
          public void destroy(){
              //过滤器对象在销毁时自动调用，释放资源
          }
      }
  }
  ~~~

启动Tomcat输入：http://localhost:8080/Login.jsp进入登录界面，此时用户输入除`admin`以外的内容均会出现error.jsp页面

[用户输入进入错误界面：](https://s1.ax1x.com/2022/04/03/q7EFnH.png)

​																		[<img src="https://s1.ax1x.com/2022/04/03/q7EFnH.png" alt="q7EFnH.png" style="zoom:33%;" />](https://imgtu.com/i/q7EFnH)

如果用户输入正确则进入success.jsp页面

[输入正确进入页面：](https://s1.ax1x.com/2022/04/03/q7EU3T.png)

​																		[<img src="https://s1.ax1x.com/2022/04/03/q7EU3T.png" alt="q7EU3T.png" style="zoom:33%;" />](https://imgtu.com/i/q7EU3T)

如果用户没有输入账户，而是通过直接输入：http://localhost:8080/success.jsp进入页面则通过过滤器判断用户没有登录同样会出现error.jsp页面。

## 十二. JDBC

> 主要用于Java连接数据库

### 1. JDBC常用的API <a id="JDBC">#</a>

> JDBC API主要位于java.sal中，该包定义了一系列访问数据的接口和类。在IDEA中配置JDBC Web项目环境方法如下：
>
> 连接JDBC需要jar包支持：
>
> - java.sql
> - javax.sql
> - mysql-connector-java

- 配置项目中pom.xml文件

  ~~~xml
  <dependencies>
      <!--mysqL的驱动-->
      <dependency>
          <groupId>mysq1</ groupId>
          <artifactId>mysql-connector-java</ artifactId>
          <version>5.1.47</version>
          </dependency>
  </dependencies>
  ~~~

- 步骤如下

  [JDBC连接数据库步骤：](https://s1.ax1x.com/2022/04/06/qjGjpt.png)

  ​                                               [<img src="https://s1.ax1x.com/2022/04/06/qjGjpt.png" alt="qjGjpt.png" style="zoom: 50%;" />](https://imgtu.com/i/qjGjpt)

- 配置Mysql

  [配置Mysql：](https://s1.ax1x.com/2022/04/06/qjJYjK.png)

  ​                                               [<img src="https://s1.ax1x.com/2022/04/06/qjJYjK.png" alt="qjJYjK.png" style="zoom:50%;" />](https://imgtu.com/i/qjJYjK)

  [配置数据库进行连接：](https://s1.ax1x.com/2022/04/06/qjJgu8.png)

  ​                                               [<img src="https://s1.ax1x.com/2022/04/06/qjJgu8.png" alt="qjJgu8.png" style="zoom:50%;" />](https://imgtu.com/i/qjJgu8)

  [配置数据库结构：](https://s1.ax1x.com/2022/04/06/qjJqDU.png)

  ​                                              [<img src="https://s1.ax1x.com/2022/04/06/qjJqDU.png" alt="qjJqDU.png" style="zoom:50%;" />](https://imgtu.com/i/qjJqDU)

- 连接成功后可以看到Mysql中创建好的表

  [连接成功：](https://s1.ax1x.com/2022/04/06/qjY5ZD.png)

​                                                    [<img src="https://s1.ax1x.com/2022/04/06/qjY5ZD.png" alt="qjY5ZD.png" style="zoom:50%;" />](https://imgtu.com/i/qjY5ZD)

#### 1.1 DriverManage类

>  DriverManage类用于加载JDBC驱动并且创建与数据库的连接。在DriverManage类中定义了两个比较重要的静态方法：

|                     方法名称                     |                   功能描述                   |
| :----------------------------------------------: | :------------------------------------------: |
|          registerDriver(Driver driver)           | 该方法用于向DriverManage中注册给定的JDBC程序 |
| getConnection(String url,String user,String pwd) |         该方法用于建立与数据库的连接         |

#### 1.2 Driver类

> Driver接口是所有JDBC驱动程序必须实现的接口，该接口专门提供给数据库厂商使用。需要注意的是，在编写JDBC程序时，必须要把所有的数据库驱动程序或类库加载到项目的`classpath`中(这里指Mysql驱动的jar包)

#### 1.3 Connection接口

> Connection接口表示Java程序和数据库的连接，只有获得该连接对象后才能访问数据库，并操作数据表。该接口定义了一系列方法

|           方法名称           |                           功能描述                           |
| :--------------------------: | :----------------------------------------------------------: |
|        getMetaData()         |        用于返回表示数据库元数据的DatabaseMetaData对象        |
|      createStatement()       |       用于创建一个Statement对象并将sql语句发送到数据库       |
| prepareStatement(String sql) | 用于创建一个PreparedStatement对象并将参数化的sql语句发送到数据库 |
|   prepareCall(String sql)    |    用于创建一个CallableStatement对象来调用数据库存储过程     |

#### 1.3 Statement接口

> Statement接口用于执行静态的sql语句，并返回一个结果对象。Statement接口的对象通过Connection接口的createStatement()方法获得。利用Statement接口把静态的sql语句发送到数据库编译执行，然后返回数据库的处理结果。Statement接口提供了执行SQL语句的3中常用方法

|         方法名称          |                           功能描述                           |
| :-----------------------: | :----------------------------------------------------------: |
|    execute(String sql)    | 用于执行各种SQL语句，该方法返回一个布尔类型的值，如果为true，则表示所执行的SQL语句有查询结果，可通过Statement的getResultSet()方法获得查询结果 |
| executeUpdate(String sql) | 用于执行SQL中的insert、update和delete语句。该方法返回一个int类型的值，表示数据库中受该SQL语句影响的记录条数。 |
| executeQuery(String sql)  | 用于执行SQL中的select语句，该方法返回一个表示查询结果的ResultSet对象。 |

#### 1.4 PreparedStatement接口

> Satement 接口封装了JDBC执行 SQL语句的方法，可以完成Java程序执行SQL语句的操作。然而在实际开发过程中往往需要将程序中的变量作为SQL语句的查询条件，而使用Statement接口操作这些SQL语句会过于烦琐，并且存在安全方面的问题。针对这一问题，JDBC API提供了扩展的PreparedStatement接口。
> PreparedStatement是Statement的子接口，用于执行预编译的SQL语句。PreparedStatement接口扩展了带有参数的SQL语句的执行操作，应用该接口中的SQL语句可以使用占位符“？”代替参数，然后通过setter()方法为SQL语句的参数赋值。PreparedStatement接口提供了一些常用方法。

|                           方法名称                           |                           功能描述                           |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|                       executeUpdate()                        | 在此PreparedStatement对象中执行SQL语句，该语句必须是一个DML语句或者无返回内容的SQL语句。例如DDL语句 |
|                        executeQuery()                        | 在此PreparedStatement对象中执行SQL查询，该方法返回值是ResuktSet对象 |
|             setInt(int PreparedStatement,int x)              |                 将指定参数设置为给定的int值                  |
|           setFloat(int PreparedStatement,float x)            |                将指定参数设置为给定的float值                 |
|          setString(int PreparedStatement,String x)           |                将指定参数设置为给定的String值                |
|            setDate(int PreparedStatement,Date x)             |                 将指定参数设置为给定的Date值                 |
|                          addBatch()                          |    将一组参数添加到此PreparedStatement对象的批处理命令中     |
| setCharacterStream(int PreparedStatementIndex,java.io.Reader reader,int length) |             将指定的输入流写入数据库的文本字段中             |
| setBinaryStream(int PreparedStatementIndex,java.io.InputStream x,int length) |             将二进制的输入流数据写入二进制字段中             |

需要注意的是上面方法中的setDate方法可以设置日期内容，但参数Date的类型是java.sql.Date，而不是java.util.Date

在通过setter()方法为SQL语句中的参数赋值时，可以采用参数与SQL类型相匹配的方法(例如，如果参数类型为Integer，那么应该使用setInt()方法)。也可以通过setObject()方法设置多种类型的输入参数。

通过setter()方法为SQL语句的参数赋值：

~~~java
String sql="INSERE INTO user(id,name,email) VALUES(?,?,?)";
PreparedStatement pre=conn.preparedStatement(sql);
pre.setInt(1,1);				//使用参数与SQL类型相匹配的方法
pre.setString(2,"zhangsan");	//使用参数与SQL类型相匹配的方法
pre.setObject(3,"zs@sina.com"); //使用setObject()方法设置参数
pre.executeUpdate();
~~~

#### 1.5 ResultSet接口

> ResultSet接口用于保存JDBC执行查询时返回的结果集，该结果集封装在一个逻辑表格中。在ResultSet接口内部有一个指向表格数据行的游标(指针)，ResultSet对象初始化时游标在表格的第一行之前，调用next()方法可将游标移动到下一行。如果下一行没有数据，则返回false。在应用程序中经常调用next()方法作为while循环的条件来迭代ResultSet结果集。

|          方法名称          |                           功能描述                           |
| :------------------------: | :----------------------------------------------------------: |
| getString(int columnIndex) | 用于获取指定字段的String类型的值，参数columnIndex代表字段的索引 |
| getString(int columnName)  | 用于获取指定字段的String类型的值，参数columnName代表字段名称 |
|  getInt(int columnIndex)   |  用于获取指定字段的int类型的值，参数columnIndex代表字段索引  |
| getInt(String columnName)  | 用于获取指定字段的String类型的值，参数columnName代表字段名称 |
|  getDate(int columnIndex)  | 用于获取指定字段的int类型的值，参数columnIndex代表字段索引值 |
| getDate(String columnName) | 用于获取指定字段的String类型的值，参数columnName代表字段的名称 |
|           next()           |                 将游标从当前位置向下移动一行                 |
|     absolute(int row)      |             将游标移动到此ResultSet对象的指定行              |
|        afterLast()         |      将游标移动到此ResultSet对象的末尾，及最后一行之后       |
|       beforeFirst()        |       将游标移动到此ResultSet对象的开头，即第一行之前        |
|         previous()         |             将游标移动到此ResultSet对象的上一行              |
|           last()           |            将游标移动到此ResultSet对象的最后一行             |

ResultSet接口中定义了大量的getter()方法，而采用哪种getter()方法获取数据，取决于字段的数据类型。程序既可以通过字段的名称获取指定数据，也可以通过字段的索引获取指定的数据，字段的索引从1开始编号。例如，数据表的第一列字段为id，字段类型为int，那么即可以调用getInt(1)，以字段索引的方式获取该列的值，也可以调用getInt("id")，以字段名称的方式获取该列的值。

### 2. 实现JDBC接口

通常JDBC实现需要实现一下几个步骤：

1. 加载并注册数据库驱动

   ~~~java
   DriverManager.registerDriver(Driver driver);
   //或者
   Class forName("DriverName");
   ~~~

2. 通过DriverManager获取数据库连接,获取数据库连接的具体方式如下：

   ~~~java
   comection conn = DriverManager.getConnection(String url, String user, String pwd);
   ~~~

   > getConnection()方法有3个参数，它们分别表示连接数据库的URL地址、登录数据库的用户名和密码。以MySQL数据库为例，MySQL5.5及之前版本的URL地址的书写格式如下：

   ~~~java
   jdbe:mysql://hostname:port/databasename
   ~~~

   > MySQL5.6及之后版本的MySQL数据库的时区设定比中国时间早8小时，需要在URL地址后面指定时区，具体代码如下：

   ~~~java
   jabc:mysql://hostname:port/databasename?serverTimezone=GMT2B8
   ~~~

   > 在上述代码中，jdbc:mysql:是固定的写法，mysql是指MySQL数据库，hostname是指主机的名称(如果数据库在本机中，hostname可以为localhost或127.0.0.1；如果要连接的数据库在其他计算机上，hostname为所要连接计算机的IP), port是指连接数据库的端口号(MySQL端口号默认为3306)， databasename是指MySQL中相应数据库的名称。

3. 通过 Connection 对象获取 Statement对象

   > 通过Connetion对象获取Statement对象的方式有以下三种。

   - 调用createStatement()方法：创建基本的Statement对象
   - 调用PrepareStatement()方法：创建PrepareStatement对象
   - 调用prepareCall()方法：创建CallableStatement对象

   以创建基本的Statement对象为例：

   ~~~java
   Statement stmt=conn.createStatement();
   ~~~

4. 使用Statement 对象执行SQL语句

   > 所有的Statement对象都有以下三种执行SQL语句的方法。

   - execute( )：可以执行任何SQL语句。
   - executeQuery()：通常执行查询语句，执行后返回代表结果集的ResultSet对象。
   - executeUpdate()：主要用于执行DML和DDL语句。执行DML语句(例如INSERT、UPDATE或DELETE)时，返回受SQL语句影响的行数，执行DDL语句则返回0。

   以executeQuery()方法为例，其使用方式如下：

   ~~~java
   //执行SQL语句，获取结果集ResultSet
   ResultSet rs = stmt.executeQuery(sql);
   ~~~

5. 操作 ResultSet 结果集

   > 如果执行的SQL语句是查询语句，执行结果将返回一个ResultSet对象，该对象保存了SQL语句查询的结果。程序可以通过操作该ResultSet对象获取查询结果。

6. 关闭连接，释放资源

   > 每次操作数据库结束后都要关闭数据库连接，释放资源，包括ResultSet、Statement和Connection等资源。

### 3. JDBC程序实例

> 下面依照上面所讲解的步骤演示JDBC的使用。编写JDBC程序从users表中读取数据，并将结果打印在控制台，具体步骤如下。

- 搭建数据库环境

  > 在Mysql中创建一个名为jdbc的数据库，然后创建一个users表。

  ~~~mysql
  CREATE DATABASE jdbc;
  USB jdbc;
  CREATE TABLE users(
  id INTPRIMARY KEY AUTO INCREMENT,
  name VARCHAR(40),
  password VARCHAR(40) ,
  email VARCHAR(60),
  birthday DATE
  )CHARACTER SET utf8 COLLATE utf8_general_ci;
  ~~~

  > 创建好数据库和users表后，向users表中插入3条数据

  ~~~mysql
  INSERT INTO users (NAME,PASSWORD,email,birthday)
  VALUES('z8','123456','zs@sina.com','1980-12-04')；
  INSERT INTO users (NAME, PASSWORD,email,birthday)
  VALUES ('lisi',11234561,'lisi@sina.com','1981-12-04')
  INSERT INTO users (NAME, PASSWORD,email,birthday)
  VALUES('wangwu','123456', 'wangwu@sina.com', '1979-12-04');
  ~~~

  > 创建成功后使用`SELECT * FROM users`查询表中数据。

  [表中的数据如下：](https://s1.ax1x.com/2022/04/07/qz3dij.jpg)

  ​							[<img src="https://s1.ax1x.com/2022/04/07/qz3dij.jpg" alt="qz3dij.jpg" style="zoom:33%;" />](https://imgtu.com/i/qz3dij)

- 创建项目环境，导入数据库驱动

   这里创建项目连接数据库的方式在[JDBC常用的API](#JDBC)中以进行演示。

- 在web项目包下建立一个ShowUser类，用于获取数据库数据

  ~~~java
  import java.sql.Connection;
  import java.sql.DriverManager;
  import java.sql.ResultSet;
  import java.sql.SQLException;
  importjava.sql.Statement;
  import java.sql,Date;
  public class Example01{
      public static void main(Stringl) args)throws SQLException{
          Statement stmt = null;
          ResultSet rs = null;
          Connection conn = null;
          try{
              // 1.注册数据库的驱动
              Class.forName("com.mysql.cj.jdbc.Driver");
              // 2.通过DriverManager 获取数据库连接
              string url ="jdbc:mysql://localhost:3306/jdbc?serverTimezone=GMT2B8";
              String username= "root";
              String password ="root";
              conn DriverManager.getConnection (url, username, password);
              // 3.通过Connection对象获取 Statement对象
              stmt=conn.createStatement();
              // 4.使用 Statement 执行 SQL语句
              String sql="selectfrom users";
              rs= stmt.executeQuery(sql);
              //5、操作ResultSet 结果集 
              System.out.printin("id | name | password | email | birthday");
              while (rs.next()){
                  int id =rs.qetInt("id");//通过列名获取指定字段的值
                  String name = ts.getString("name");
                  String psw =rs.getstring("password");
                  String email rs.getString("emai1");
                  Date birthday= rs.getDate("birthday");
                  System.out,print1n(id+"|" + name+"|"+psw+"|"+ birthday);
              }
  
          }catch(ClassNotFoundException e){
              e.printStackTrace();
          }finallyl{
              // 6.回收数据库资源
              if(rs！=null){
                  try {
                      rs.close();
                  } catch (SQLException e){
                      e.printStackTrace();
                  }
                  rs =null;
              }
  
  
              if(stmt!=null){
                  try {
                      stmt.close();
                  } catch (SQLException e){
                      e.printStackTrace();
                  }
  
                  stmt = null;
              }
              if(conn!=null){
                  try {
                      conn.close();
                  }catch (SQLException e){
                      e.printStackTrace()
                  }
  
                  conn = null;
              }
  
          }
      }
  }
  ~~~

  > 第15行代码注册MySQL数据库驱动；第17～19行代码创建数据库的url、username、password等连接参数。第20～23行代码通过DriverManager获取一个Connection对象，然后使用Conmection对象创建一个Statemen对象；第26行代码通过 Sutement对象调用executeQuer()方法执行SOL语句，并返回结果集ResultSet；第29～36行代码遍历ResullSet结果集并打印；
  > 第42～65行代码关闭连接，回收了数据库资源。

启动程序运行结果如下所示：

[JDBC运行结果：](https://s1.ax1x.com/2022/04/07/qzBhff.jpg)									[<img src="https://s1.ax1x.com/2022/04/07/qzBhff.jpg" alt="qzBhff.jpg" style="zoom:33%;" />](https://imgtu.com/i/qzBhff)

### 4. PreparedStatement对象

> 在之前SQL语句执行是通过Statement对象实现的。Statement对象每次执行SQL语句时，都会对其进行编译。当相同的SQL语句执行多次时，Statement对象就会使数据库频繁编译相同的SQL语句，从而降低数据库的访问效率。此时，Statement的子类**PreparedStatement**对象可以对SQL语句进行预编译，预编译的信息会存储在**PreparedStatement**对象中。当相同的SQL语句再次执行时，程序会使用**PreparedStatement**对象中的数据，而不需要对SQL语句再次编译去查询数据库，这样就大大提高了数据的访问效率。

示例：

- 在web项目的包下建立一个名为Example.java的类

  ~~~java
  import java.sql.Connection;
  import java.sql.DriverManager;
  import java.sql.PreparedStatement;
  import java.sql.SQLException; 
  public class Example {
      public static void main(String[] args) throws SQLException{
          Connection conn = null;
          PreparedStatement preStmt = null;
          try{
              // 加载数据库驱动
              Class.forName("com.mysql.cj.jdbc.Driver");
              String url = "jdbc:mysql://localhost:3306/jdbc?serverTimezone=GMT&2B8";
              String username ="root";
              String password = "root";
              // 创建应用程序与数据库连接的Connection对象
              conn = DriverManager.getConnection (url, username, password);
              //执行的SQL语句
              String sql ="INSERT INTO users (name,password,email,birthday)"+ "VALUES(?,?, ?, ?) ";
              // 1.创建执行SQL语句的PreparedStatement对象
              preStmt = conn.prepareStatement(sql);
              // 2.为SQL语句中的参数赋值
              preStmt.setString(1,"zl");
              preStmt.setString(2, "123456");
              preStmt.setString(3,"zl@sina.com");
              preStmt.setString(4,"1989-12-23");
              //3.执行SQL
              preStmt.executeUpdate();
          }catch (ClassNotFoundException e){
              e.printStackTrace();
          }finally{
              if(preStmt!=null){
                  try{
                      preStmt.close();
                  }catch(SQLException e){
                      e.printStackTrace();
                  }
                  preStmt=null;
              }
              if(coon!=null){
                  try{
                      coon.close();
                  }cath(SQLException e){
                      e.printStackTrace();
                  }
                  conn=null;
              }
          }
  
      }
  }
  ~~~

  > 第12~15行代码创建数据库的连接参数；第17行代码创建应用程序与数据库连接的Connection对象；第19行和第20行代码声明需要执行的SQL语句；第22行`~`27行代码首先通过Connection对象调用prepareStatement()方法生成PreparedStatement对象的setter()方法，给SQL语句中的参数赋值，最后调用executeUpdate()方法执行SQL语句；第33`~`48行代码关闭连接，回收了数据库资源。

执行上面代码后会在users表中插入一条数据。在Mysql上用`SELECT * FROM user`会显示如下：

[使用预编译插入数据：](https://s1.ax1x.com/2022/04/08/L9TJ4x.jpg)

​												[<img src="https://s1.ax1x.com/2022/04/08/L9TJ4x.jpg" alt="L9TJ4x.jpg" style="zoom:33%;" />](https://imgtu.com/i/L9TJ4x)

### 5. ResultSet对象

> ResultSet对象主要用于存储结果集，可以通过next()方法由前向后逐个获取结果集中的数据，如果向获取结果集中任意位置的数据，则需要在创建Statement对象时设置两个ResultSet定义的常量，具体设置方法如下：

~~~java
Statement st=coon.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE,ResultSet.CONCUR_READ_ONLY);
ResultSet rs=st.excuteQuery(sql);
~~~

上述方法中，常量`ResultSet.TYPE_SCROLL_INSENSITIVE`表示结果集可以滚动，常量`ResultSet.CONCUR_READ_ONLY`表示以只读形式打开结果集。

- 这里介绍一个如何使用ResultSet对象滚动读取结果集中的数据。在包下创建一个名为Example.java文件

  ~~~java
  import java.sql.Connection;
  import java.sql.DriverManager;
  import java.sql.SQLException; 
  import java.sql.ResultSet;
  import java.sql.Statement;
  public class Example {
      public static void main(String[] args) throws SQLException{
          Connection conn = null;
          Statement stmt = null;
          try{
              // 加载数据库驱动
              Class.forName("com.mysql.cj.jdbc.Driver");
              String url = "jdbc:mysql://localhost:3306/jdbc?serverTimezone=GMT&2B8";
              String username ="root";
              String password = "root";
              // 创建应用程序与数据库连接的Connection对象
              conn = DriverManager.getConnection (url, username, password);
              //执行的SQL语句
              String sql ="SELECT * FROM users";
              //创建Statement对象并设置常量
              stmt=coon.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE,ResultSet.CONCUR_READ_ONLY);
              // 1.创建执行SQL语句的PreparedStatement对象
              ResultSet rs = stmt.executeQuery(sql);
              //取出ResultSet 中指定数据的信息
              System.out.print("第2条数据的name值为：");
              rs.absolute(2); 						//将指针定位到结果集中第2条数据
              System.out.println(rs.getString("name"));
              System.out.print("第1条数据的name值为：");
              rs.beforeFirst();						//将指针定位到结果集中第1条数据之前
              rs.next(); 								//将指针向后滚动
              System.out.println(rs.getString("name"));
              System.out.print("第4条数据的name值为：");
              rs.afterLast(); 						//将指针定位到结果集中最后一条数据之后
              rs.previous(); 							//将指针向前滚动
              System.out.println(rs.getString("name"));
  
          }catch (ClassNotFoundException e){
              e.printStackTrace();
          }finally{
              if(stmt!=null){
                  try{
                      stmt.close();
                  }catch(SQLException e){
                      e.printStackTrace();
                  }
                  stmt=null;
              }
              if(coon!=null){
                  try{
                      coon.close();
                  }cath(SQLException e){
                      e.printStackTrace();
                  }
                  conn=null;
              }
          }
  
      }
  }
  ~~~

  > 第26行代码通过ResultSet对象调用absolute()方法获取ResultSet结果集中的第二条数据；第29行代码和第30行代码获取ResultSet结果集中的第1条数据；第33行和34行代码获取ResultSet结果集中的第四条数据

[ResultSet对象运行结果为：](https://s1.ax1x.com/2022/04/08/L9vFDf.jpg)											[![L9vFDf.jpg](https://s1.ax1x.com/2022/04/08/L9vFDf.jpg)](https://imgtu.com/i/L9vFDf)

### 6. JDBC完成数据库的增删改查

- **创建JavaBean**在web项目包下创建一个用户信息的实体类User.java类

  ~~~java
  import java.util.Date;
  
  public class User{
      private int id;
      private String username;
      private String password;
      private String email;
      private Date birthday;
      public int getId(){
          return id;
      }
  
      public void setId(int id){
          this.id = id;
      }
  
      public String getUsername (){
          return username;
      }
  
      public void setUsername(String username){
          this.username = username;、
      }
      public String getPassword(){
          return password;
      }
  
      public void setPassword(String password){
          this.password = password;
      }
      public String getEmail(){
          return email;
      }
  
      public void setEmail(String email){
          this.email = email;
      }
  
      public Date getBirthday(){
          return birthday;
      }
  
      public void setBirthday(Date birthday){
          this.birthday =birthday;
      }
  }
  ~~~

- **创建工具类**，由于每次操作数据库需要加载数据库驱动、建立数据库连接和关闭数据库连接，为了避免重复书写代码，下面建立一个专门用于操作数据库的工具类：JDBCUtils.java <a id="2">#</a>

  ~~~java
  import java.sql.Connection;
  import java.sql.DriverManager;
  import java.sql.ResultSet;
  import java.sql.SQLException;
  import java.sql.Statement;
  public class JDBCUtils {
      //加载驱动，并建立数据库连接
      public static Connection getConnection() throws SQLException, ClassNotFoundException{
          Class.forName("com.mysql.cj.jdbc.Driver");
          String url ="jdbc:mysql://localhost:3306/jdbc?serverTimezone";
          String username ="root";
          String password ="root";
          Connection conn = DriverManager.getConnection(url,usernamer password);
          return conn;
      }
  
  
      // 关闭数据库连接，释放资源
      public static void release(Statement stmt, Connection conn) {
          if (stmt != null) {
              try {
                  stmt.close(); 
              }catch (SQLException e){
                  e.printStackTrace();
              }
              stmt = null;
          }
          if (conn != null){
              try{
                  conn.close();
              }catch(SQLException e){
                  e.printStackTrace();
              }
              conn = null;
          }
  
      }
  
      public static void release (ResultSet rs, Statement stmt,Connection conn){
          if(rs!= null){
              try{
                  rs.close();
              } catch (SQLException e){
                  e.printStackTrace(); 
              }
              rs = null;
          }
          release(stmt, conn)
      }
  }
  ~~~

- **创建DAO**，包中创建一个名为UserDao.java的类，该类主要用于程序与数据库建立交互，在该类中封装了对数据库表users的添加、查询、删除和更新等操作。

  ~~~java
  import java.sql.Connection;
  import java.sql.ResultSet;
  import java.sql.Statement;
  import java.sql.Statement;
  import java.text.SimpleDateFormat;
  import java.util.ArrayList;
  //如果类不在同一个包内将上面的类导入
  import cn.itcast.jdbc.example.domain.User; 
  import cn.itcast.jdbc.example.utils.JDBCUti1s;
  public class UsersDao{
      //添加用户的操作
      public boolean insert(User user){
          Connection conn=null;
          Statement stmt= nutl:
          ResultSet rs=null;
          try{
              //获得数据的连接
              conn= JDBCUtils.getConnection();
              //获得Statement 对象
              stmt =conn.createStatement();
              //发送SQL语句
              SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd") ;
              String birthday = sdf,format(user.getBirthday());
              String sql ="INSERT INTO users(id,name,password,email,birthday"+"VALUES("+user.getId()
                  +"','"+user.getUsername ()+"','"+user.getPassword()+"','"+user.getEmail()+"','"
                  +birthday+"')'";
              int num = stmt.executeUpdate(sql);
              if (num > 0){
                  return true;
              }
              return false;
          }catch (Exception e){
              e.printStackTrace();
          }finally{
              JDBCUtils.release(rs, stmt, conn);
          }
          return false;
      }
  
      //查询所有的User对象
      public ArrayList<User> findAll(){
          Connection conn = null;
          Statement stmt = null;
          ResultSet rs = null;
          ArrayList<User> list = new ArrayList<User>();
          try{
              //获得数据的连接
              conn = JDBCUtils.getConnection();
              // 获得 Statement 对象
              stmt = conn.createStatement();
              //发送 SQL 语句
              String sql ="SELECT * FROM users";
              rs=stmt.executeQuery(sql);
              //处理结果集 
              while(rs.next()){
                  User user = new User();
                  user.setId(rs.getInt("id"));
                  user.setUsername(rs.getString("name"));
                  user.setPassword(rs.getString("pasaword"));
                  user.setEmail(rs.getstring("email"));
                  user.setBirthday(rs.getDate("birthday"));
                  list.add(user);             
  
              }
              return list;
          } catcn(Exception e){
              e.printStackIrace();
          }finally{
              JDBCUtils.release(rt, stmt, conn);
          }
          return null;
      }
      //根据 id查找指定的user
      public User find(int id){
          Connection conn = null;
          Statement stmt = null;
          ResultSet rs = null;
          try{		// 获得数据的连接
              conn = JDBCUtils.getConnection();
              // 获得Statement对象
              stmt = conn.createStatement();
              // 发送SQL语句
              String sql ="SELECT *FROM users WHERE id="+ id; 
              rs = stmt.executeQuery(sql);
              //处理结果集
              while (rs.next()){
                  User user = new User();
                  user.setId(rs.getInt("id"));
                  user.setUsername(rs.getString("name"));
                  user.setPassword(rs.getString("password")); 
                  user.setEmail(rs.getString("email"));
                  user.setBirthday(rs.getDate("birthday"));
                  return user;
              }
              return null;
          } catch (Exception e){
              e.printStackTrace();
          }finally{
              JDBCUtils.release(rs, stmt, conn);
          }
          return null;
      }
  
      // 删除用户
      public boolean delete(int id){
          Connection conn = null;
          Statement stmt = null;
          ResultSet rs =null;
          try{
              // 获得数据的连接
              conn = JDBCUtils.getConnection();
              // 获得 Statement 对象
              stnt = conn.createStatement();
              // 发送 SOL 语句
              String sql = "DELETE FROM users WHERE id="+ id;
              int num = stmt.executeUpdate(sql);
              if (num >0){
                  return true;
              }
              return false;
          } catch (Exception e){      
              e.printStackTrace();
          } finally{
              JDBCUtils.release(rs, stmt, conn); 
          }
          return false;
      }
      //修改用户
  
      Public boolean update (User user){
          Connection conn = null;
          Statement stmt=null;
          ResultSet rs=null;
          try{
              //获得数据的连接
              conn=JDBCUtils.getConnection();
              //获得Statement 对象
              stmt=conn.createStatement();
              //发送SQL语句
              SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
              String birthday=sdf.format(user.getBirthday());
              String sql="UPDATE users set name='"+ user.getUsername() +"',password='"
                  +user.getPassword +"',email='"+user.getEmail()
                  +"', birthday='" + birthday+"'WHERE id="+user.getId();
              int num=stmt,executeUpdate(sql);
              if (num>0){
                  return true;
              }
              return false;
  
          }catch(Exceptione){
              e.printStackTrace();
          }finally{
              JDBCUtils.release(rs, stmt, conn);
          }
  
          return false;
      }
  }
  ~~~

- 创建一个测试类JdbcInsertTest.java，用于实现向users表中添加数据的操作

  ~~~java
  import java.util.Date;
  import cn.itcast.jdbc.example.dao.UsersDao; 
  import cn.itcast.jdbc.example.domain.User; 
  public class JdbcInsertTest{
      public static void main(String[] args){//向users表插入一个用户信息
          UsersDao ud = new UsersDao();
          User user=newUser();
          user.setId(5);
          user.setUsername("hl");
          user.setPassword("123");
          user.setEmail("hl@sina.com");
          user.setBirthday(new Date());
          boolean b=ud.insert(user);
          System.out.println(b);
      }
  }
  ~~~

  操作成功后打印台输出true则表明成功。在Mysql客户端使用SELECT查看表信息，如下图：

  [Users表数据：](https://s1.ax1x.com/2022/04/10/LA2xG6.jpg)                          [<img src="https://s1.ax1x.com/2022/04/10/LA2xG6.jpg" alt="LA2xG6.jpg" style="zoom:25%;" />](https://imgtu.com/i/LA2xG6)

- 再次创建一个测试类FindALLUsersTest.java用于实现读取users表中的所有数据

  ~~~java
  package cn.itcast.jdbc.example;
  import java.util.ArrayList;
  import cn.itcast.jdbc.example.dao.UsersDao;
  import cn.itcast.jdbc.example.domain.User;
  public class FindAllUsersTest{
      public static void main(String[] args){
          //创建一个名称为usersDao的对象
          UsersDao usersDao = new UsersDao();
          //将UsersDao对象的findA11()方法执行后的结果放入1ist集合
          ArrayList<User> list= usersDao.findAl1();
          //循环输出集合中的数据
          for(int i = 0; i < list.size(); i++){
              System.out.println("第”+(1 + 1)+"条数据的username值为：”) + list.get(i).getUsername());
          }
      }
  }
  ~~~

  运行程序后控制台会打印处users数据库中所有信息

  [Users表中信息：](https://s1.ax1x.com/2022/04/10/LAWnt1.jpg)

  [<img src="https://s1.ax1x.com/2022/04/10/LAWnt1.jpg" alt="LAWnt1.jpg" style="zoom:33%;" />](https://imgtu.com/i/LAWnt1)

- 再创建一个FindUserByIdTest.java类用于实现读取users表中指定数据

  ~~~java
  package cn.itcast.jdbc.example;
  import cn.itcast.jdbc.example.dao.UsersDao;
  import cn.itcast.jdbc.example.domain.User;
  public class FindUserByIdTestt{
      public static void main(String[] args){
          UsersDao usersDao = new UsersDao();
          User user = usersDao.find(1);
          System.out.println("id为1的User对象的name值为："+user.getUsername());
      }
  }
  ~~~

  输出结果为：`id为1的User对象的name值为：zs`

- 再创建一个为UpdateUserTest.java的类，实现修改users表中的操作

  ~~~java
  packagecn.itcast.jdbc.example;
  importjava.util.Date;
  import cn.itcast.jdbc.example.dao.UsersDao; 
  import cn.itcast,jdbc,example,domain.User;
  public class UpdateUserTest{
      public static void main(String[] args){//修改User对象的数据
          UsersDao usersDao =new UsersDao();
          Useruser User= new User();
          user.setId(4);
          user.setUsername（"zhaoxiaoliu");
          user.setPassword("456");
          user.setEmail("zhaoxiaoliu@sina.com");
          user.setBirthday(newDate());
          boolean b=usersDao.update(user);
          System.out.println(b);
      }
  }
  ~~~

  运行程序后控制太打印true，说明修改users表成功。这时进入Mysql数据库，使用SELECT语句查看数据库如下：

  [修改users数据：](https://s1.ax1x.com/2022/04/10/LAfLZQ.jpg)

  [<img src="https://s1.ax1x.com/2022/04/10/LAfLZQ.jpg" alt="LAfLZQ.jpg" style="zoom: 33%;" />](https://imgtu.com/i/LAfLZQ)

- 创建测试类DeleteUserTest.java类，该类实现删除users表中的数据操作。

  ~~~java
  package cn.itcast.jdbc.example;
  import cn.itcast.jdbc.example.dao.UsersDao;
  public class DeleteUserTest{
      public static void main(String[] args){
          //删除操作
          UsersDao usersDao = new UsersDao();
          boolean b = usersDao.delete(4);
          System.out.println(b);
      }
  }
  ~~~

  运行程序后控制太打印true，说明删除users表数据成功。这时进入Mysql数据库，使用SELECT语句查看数据库如下：

  [删除Users表中指定数据：](https://s1.ax1x.com/2022/04/10/LA424A.jpg)

  [<img src="https://s1.ax1x.com/2022/04/10/LA424A.jpg" alt="LA424A.jpg" style="zoom:33%;" />](https://imgtu.com/i/LA424A)

### 7. 使用JDBC实现网页用户登录功能

>  本项目实现一个用户登录的功能，再用户登录时，需要再数据库中判断是否存在该用户的信息并验证用户信息的正确性。
>
> 本项目实现具体步骤：
>
> 1. 获取登录页面的username和password
> 2. 遍历数据库中的tb_user表，是否存在username，存在则继续执行程序，不存在则结束程序
> 3. 遍历数据库中的tb_user表，查找对应username的password，判断password是否与登录页面的password一致，一致则完成，不一致则退出。

- 在数据库中创建一个tb_user表，并在tb_user表中插入一条用户数据

  ~~~MySQL
  USE jdbc;
  create table tb_user (
      id int not null primary key auto_increment,-- id主键
      username varchar(40) not null,-- 账户名称，设置不为空
      password varchar(40) not null,-- 密码，设置不为空
      name varchar(40) default null,-- 用户真实姓名，默认为空
      gender varchar(20) default null,-- 用户性别，默认为空
      phonenumber varchar(30) default null,-- 用户手机号码，默认为空
      identitycode varchar(30) default nu1l-- 用户身份证号码，默认为空
  );
  insert into tb_user VALUES
  (1,'张三','123','张三','male','13888888888','110202107075023');
  ~~~

- **编写登录界面**，在web目录下创建一个login.jsp的文件，在该文件中添加用户登录时输入用户信息的表单元素。

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java5" %>
  <html>
      <head>
          <title>登录页面</title>
      </head>
      <style>
          *{
              margin: 0;
              padding: 0;
          }
          form {
              display: block;
              height: auto;
              width：450px;
              margin:100px auto;
          }
  
          form table tr{
              height:40px;
              form tabletrtd
              height:40px;
              width:280px;
              line-height：40px; 
          }
  
          form table tr td input{
              height:32px;
              border:1px solid#BABABA;
              border-radius:6px;
          }
  
          .alignRight{
              text-align:right;
              line-height:40px;  
              font-size:16px;
              font-family:"Monaco";
              width:200px;
          }
  
          .submit{
              display：block;
              height:40px;
              width:250px;
              color: white;
              font-weight:bold;
              font-size:18px;
              background-color:#98ECAC;
              border-radius:8px;
              margin:15px auto;
          }
  
      </style>
      <body>
          <form action="LoginServlet" method="post">
              <table>
                  <tr>
                      <td class="alignRight">
                          Username:
                      </td>
                      <td>
                          <input type="text" name="username"/>
                      </td>
                  </tr>
                  <tr>
                      <td class="alignRight">
                          Password:
                      </td>
                      <td>
                          <input type="password"name="password" >
                      </td>
                  </tr>
              </table>
              <input type="submit" value="登录”class="submit” />
          </form>
      </body>
  </html>
  ~~~

- **编写工具类**，我们为了避免重复书写代码，要建立一个专门用于操作数据库的工具类，GetConnection.java

  ~~~java
  package cn.itcast;
  importjava.sql.Connection;
  importjava.sql.DriverManager;
  import java.sql.SQLException;
  public class GetConnection{
      Connection conn = null;
      public Connection getConnection() throws ClassNotFoundException{
          String driver="com.mysql.cj.jdbc.Driver"; //驱动路径
          //数据库地址
          String url="jdbc:mysql://localhost:3306/jdbc?serverTimezone="+"GMT2B8&useUnicode=true&characterEncoding=utf-8"; 
          String user="root"; //访问数据库的用户名
          String password="root"; //用户密码
          Class.forName(driver);
          try {
              conn=DriverManager.getConnection(url,user,password);
          }catch (SQLException e){
              e.printStackTrace();
          }
          //返回Connection对象
          return conn;
      }
  } 
  ~~~

  > 上面的代码第8~12行代码定义了数据库连接的驱动路径、数据库地址、数据库用户名和密码等属性；第13行代码用于加载驱动类；第15行代码用于获取数据库连接；第20行代码用于返回数据库连接对象。

- **编写用于实现登录类型的servlet**，在包下创建一个名为LoginServlet.java类，用于封装用户的登录信息并对用户信息进行校验。

  ~~~java
  package cn.itcast;
  import javax.serviet.ServletException;
  import javax.servlet.annotation.webServlet;
  import javax.servlet.http.HttpServiet;
  import javax.sezviet:http.HctpservletRequest;
  import javax.servIet.http.ittpservletResponse;
  import java.io.printWriter;
  import java.io.IOException;
  import java.sql.*;
  import java.util.ArrayList;
  import java.util.List;
  @WebServlet(name="LoginServlet",urlPatterns="/LoginServlet")
  public class LoginServlet extends HttpServlet {
      protected void dopost (HttpServletRequest request, HttpServletResponse
                             response)throws ServletException, IOException{
          //设置请求编码、响应方式和编码方式
          request.setCharacterEncoding("UTF-8");
          response.setCharacterEncoding("UTE-8");
          response.setContentType("text/html");
          PrintWriter out = response.getWriter();
          Connection conn = null;
          Statement st = null;
          ResultSet rs = null;
          PreparedStatement ptst = null;
          //获取登录页面提交的数据
          String loginName = request.getParameter("username");
          String loginPassword = request,getParameter("password");
          //sql 语句
          String selectUsername = "select username from tb_user";
          String selectPassword = "select password from tb_user where username =?";
          try {
              //获取与数据库的连接
              conn = new GetConnection().getConnection();
              //遍历to user表，将数据库中所有username存入集合中
              st = conn.createStatement();
              rs = st.executeQuery(selectUsername);
              List<String> usernameList -new ArrayList<String>();
              while (rs.next()){
                  usernameList.add(rs.getString(1)); 
              }
              //关闭连接
              if(ra !=nu1l){
                  rs.close(); 
              }
              if(st != null){
                  st.close(); 
              }
              //判断集合中是否存在所要登录的username
              if (usernameList.contains(loginName)){
                  //查找username对应的password
                  List<String> passwordList =new ArrayList<String>(); 
                  ptst =(PreparedStatement)conn.prepareStatement(selectPassword);
                  //设置ptst参数
                  ptst.setString(1, loginName);
                  rs = ptst.executeQuery();
                  while (rs.next)){
                      passwordList.add(rs.getString(1));
                  }
                  //判断数据库与登录页面提交的password是否一致
                  if (passwordList.get(0).equals(loginPassword)){
                      out.print1n("欢迎登录。");
                  }else{
                      out.println("密码错误，请重新输入。");
                  }
                  if(rs != null){
                      rs.close();
                  }
                  if(ptst != null){
                      ptst.close(); 
                  }
              }else{
                  out.println("用户名不存在"); 
              }
          }catch (ClassNotFoundException e){
              e.printStackTrace(); 
          }catch (SQLException e){
              e.printStackTrace(); 
          }finally{
              //关闭连接
              if (conn!= null){
                  try {
                      conn.close();  
                  }catch (SQLException e){
                      e.printStackTrace();  
                  }
              } 
          }
          out.flush();
          out.close();
      }
  }
  ~~~

  > 第17~19行代码设置请求编码、响应方式和编码方式。第26行和第27行代码获取用户输入的用户名、密码等属性的值。第29行和第30行代码用于从数据库中查询是否有该用户的信息第35`~`40行代码遍历tb_user表，将数据库中所有的username存入集合中。第42`~`71行代码判断集合中是否含有登录的用户名，如果有，则判断密码是否正确，密码正确则输出"欢迎登录"，否则提示"密码错误，请重新登录"。如果用户名不存在则提示"用户名不存在"。

运行项目启动Tomcat，并在浏览器中输入：http://localhost/Demo/login.jsp，进入用户登录界面，并输入用户名和密码。`用户名：张三，密码：123`。登录成功如下所示：

[JDBC实现网页登录：](https://s1.ax1x.com/2022/04/11/LVPBZD.jpg)           [<img src="https://s1.ax1x.com/2022/04/11/LVPBZD.jpg" alt="LVPBZD.jpg" style="zoom:25%;" />](https://imgtu.com/i/LVPBZD)

### 8. Junit单元测试

> JUnit 是一个 Java 编程语言的单元测试框架。JUnit 在测试驱动的开发方面有很重要的发展，是起源于 JUnit 的一个统称为 xUnit 的单元测试框架之一。
>
> 好处：
>
> 1. 可以书写一系列的测试方法，对项目所有的接口或者方法进行单元测试。
> 2. 启动后，自动化测试，并判断执行结果, 不需要人为的干预。
> 3. 只需要查看最后结果，就知道整个项目的方法接口是否通畅。
> 4. 每个单元测试用例相对独立，由Junit 启动，自动调用。不需要添加额外的调用语句。
> 5. 添加，删除，屏蔽测试方法，不影响其他的测试方法。 开源框架都对JUnit 有相应的支持。
>
> **注意**：@Test注解只有在方法上有效

我们可以使用Maven导入所需要的包

~~~xml
<!-- https://mvnrepository.com/artifact/junit/junit -->
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <scope>test</scope>
</dependency>
~~~

之后创建测试类,此时我们不需要编写main方法，程序依然可以运行。

~~~java
import org.junit.Test;
public class TestJDBC3{
    @Test
    pub1jc void test(){
        System. out. println("Hello");
    }
}
//运行结果：hello
~~~

 ### 9. ACID(事务管理原则)

> 事务指定的是数据库的数据在执行过程中，要么都成功，要么都失败。
>
> 常用地方：如果A要给B转账，如果A扣钱之后因为其他原因转账失败，这时候整个程序应该执行失败，所以会执行回滚(即撤销)。下面建立一个项目实现转账操作

- 首先在数据库中添加用户信息

  ~~~MySQL
  CREATE TABLE account (
  	id INT PRIMARY KEY AUTO_NCREMENT,
      `name` VARCHAR (40),
  	money FLOAT
  );
  INSERT INTO account (`name`,money) VALUES( 'A', 1000);
  INSERT INTO account (`name`, money) VALUES ( 'B',1000);
  INSERT INTO account (`name`, money) VALUES( 'C' , 1000);
  ~~~

- 在java中实现事务转账

  ~~~Java
  import org.junit.Test;
  public class TestJDBC3{
      @Test
      pub1jc void test(){
          String url="jdbc:mysql://localhost:3306/jdbc?serverTimezone="+"GMT2B8&useUnicode=true&characterEncoding=utf-8"; 
          String username = "root";
          String password = "123456";
          Connection connection = null;
          try {
              Class.forName("com.mysql .jdbc.Driver");
              //2.连接数据库,代表数据库
              connection = DriverManager. getConnection(ur1, username, password);
              //3.通知数据库开启事务, false开启
              connection.setAutoCommit(false);
              String sql = "update account set money = money-100 where name = 'A'";
              connection.prepareStatement(sq1) . executeUpdate();
              //制造错误.
              int i = 1/0;
              String sq12 = "update account set money = money+100 where name ='B'" ;
              connection.prepareStatement(sq12). executeUpdate( );
              connection.commit();//以上两条SQL都执行成功了，就提交事务!
              System.out.println("success");
          } catch (Exception e) {
              try {
                  //如果出现异常，就通知数据库回滚事务
                  connection . rol1back();
              } catch (SQLException e1) {
                  e1. printStackTrace(); 
              }
              e. printStackTrace();
          }finally {
              try {
                  connection.close();
              } catch (SQLException e) {
                  e. printStackTrace();
              }
          }
      }
  }
  ~~~

  当我们运行代码因为第18行制造了一个错误，所以代码会进行异常进行回滚操作。当我们注释到此行代码，此时运行代码再查询数据库就会看到A=900，B=1100

## 十三. 数据库连接池

> 使用JDBC每次创建和断开Connection对象都会消耗一定的时间和IO资源。如果某个网站每日访问量为十万次，则需要建立十万次断开与连接，可能导致数据崩溃。为了避免频繁的连接断开数据库，数据库连接池技术应运而生。数据库连接池技术负责分配、管理和释放数据库连接，它允许应用程序重复使用现有的数据库连接，而不是重新建立。其原理是为数据库建立一个"缓冲池"。预先在"缓冲池"中放入一定量的数据，当需要建立数据库连接时，只需要从"缓冲池"中取出一个，使用完毕后在放回"缓冲池"即可。                  

[数据库连接池原理：](https://s1.ax1x.com/2022/04/14/L1PNFI.jpg)											[![L1PNFI.jpg](https://s1.ax1x.com/2022/04/14/L1PNFI.jpg)](https://imgtu.com/i/L1PNFI)

> 上图数据库连接池在初始化时将创建一定数量的数据库连接放到连接池中，当应用程序访问数据库时并不是直接创建Connection而是向连接池"申请"一个Connection。如果连接池中有空闲的Connection，则返回一个连接给应用程序，否则应用程序需要创建新的Connection。使用完毕后，连接池会将Connection回收，重新放入连接池，以供其他线程使用，从而减少创建和断开数据库的次数，提高数据库的访问效率。

### 1. DataSource接口

> 为了获取数据库连接对象(Connection)，JDBC提供了javax.sql.DataSource接口，javax.sql.DataSource接口负责与数据库建立连接，并定义返回值为Connection对象的方法。

~~~java
Connection getConnection()
Connection getConnection(String username,String password)
~~~

> 上述两个重载的方法都能用于获取Connection对象。不同的是，第一个方法是通过无参的方式建立与数据库的连接，第二个方法是通过传入登录信息的方式建立与数据库的连接。
> 接口通常都会有实现类，javaxsql.DataSouree接口也不例外，通常习惯把实现了javax.sql.DataSource接口的类称为数据源。顾名思义，数据源即数据的来源。每创建一个数据库连接，这个数据库连接信息都会存储到数据源中。
> 数据源用于管理数据库连接池。如果数据是水，数据库就是水库，数据库连接池就是连接到水库的管道，终端用户看到的数据集是管道里流出来的水。一些开源组织提供了数据库连接池的独立实现，常用的有DBCP数据库连接池和C3PO数据库连接池，这两种数据库连接池将会在后面小节进行详细讲解。

### 2. DBCP数据库连接池

> DBCP是Tomcat服务器使用的数据库连接池组件，使用DBCP数据库连接池时，需要在应用程序中导入`commons-dbcp2.jar`和`commons-pool2.jar`两个包。

- commons-dbcp2.jar包

  > commons-dbep2.jar包是DBCP数据库连接池的实现包，包含所有操作数据库连接信息和数据库连接池初始化信息的方法，并实现了DataSource接口的getConnection()方法。

- commons-pool2.jar包

  > commons-pool2.jar包是commons-dbep2.jar包的依赖包，为commons-dbep2.jar包中的方法提供了支持。一旦缺少该依赖包，commons-dbep2.jar包中的很多方法就没有办法实现。
  > 这两个JAR包可以在Apache 官网下载。其中，commons-dbcp2.jar 包含两个核心类，分别是BasieDataSourceFactory和BasicDataSource，它们都包含获取DBCP数据库连接池对象的方法。

  BasicDataSource是DataSource接口的实现类，该类的常用方法如下：

  |                    方法名称                     |             功能描述             |
  | :---------------------------------------------: | :------------------------------: |
  | void setDriverClassName(String driverClassName) |     设置连接数据库的驱动名称     |
  |             void setUrl(String ur)              |       设置连接数据库的路径       |
  |        void setUsername(String username)        |       设置数据库的登录账号       |
  |        void setPassword(String password)        |       设置数据库的登录密码       |
  |      void setInitialSize(int initialSize)       | 设置数据库连接池初始化的连接数目 |
  |          void setMinIdle(int minldle)           | 设置数据库连接池最小闲置连接数目 |
  |           Connection getConnection( )           |   从连接池中获取一个数据库连接   |

  > 上面方法中`void setDriverClassName() `、`setUrl()`、`setUsername()`、`setPassword()`等方法都是设置数据库连接信息的方法。`setInitialSize()`、`setMinIdle()`等方法都是设置数据库连接池初始化值的方法；`getConnection()`方法可以从DBCP数据库连接池中获取一个数据库连接。

  BasieDataSourceFactory是创建BasieDataSource对象的工厂类，它包含一个返回值为BasieDataSource类型的方法createDataSource()，该方法通过读取配置文件的信息生成数据源对象并返回给调用者。把数据库的连接信息和数据源的初始化信息提取出来写进配置文件，这样让代码看起来更加简洁。

#### 2.1 通过BasieDataSource类直接创建数据源对象

> 在使用DBCP数据库连接池时，首先要创建数据源对象，创建方式有两种，这里先以第一种为例子
>
> 在使用BasieDataSource类创建数据源对象时，需要手动给数据源对象设置属性值，然后获取数据库连接对象。

- 创建一个Web项目，并在包中创建一个Demo.java类，该类采用手动方式获取数据库的连接信息和数据源的初始化信息。

  ~~~java
  package cn.itcast.chapter11.example;
  import java.sql.Connection;
  import java.sql.DatabaseMetaData;
  import java.sql.SQLException;
  import javax.sql.DataSource;
  import org.apache.commons.dbcp2.BasicDataSource;
  public class Demo{
      publicstatic DataSource ds = null;
      static{
  
          //获取DBCP 数据库连接池实现类对象
          BasicDataSource bds = new BasicDataSource();
          //设置连接数据库需要的配置信息
          bds.setDriverClassName("com.mysql.cj.jdbc.Driver");
          bds.setUrl("jdbc:mysql://localhost:3306/jdbc?serverTimezone=GMT2B8");
          bds.setUsername ("root") ;
          bds.setPassword("root");
          //设置连接池的初始化连接参数
          bds.setinitlalSize(5);
          ds = bds;
      }
      public static void nain(Stringl) args)throws SQLException{
          //获取数据库连接对象
          Connection conn ds.getConnection();
          //获取数据库连接信息
          DatabaseMetaData metaData= conn.getMetaData();
          //打印数据库连接信息
          System.out.printin(metaData.getURL()+",UserName="+metaData.getUserName()
                             +","+metaData.getDriverName());
      }
  }
  ~~~

  [BasieDataSource类运行结果：](https://s1.ax1x.com/2022/04/14/L1YZ0H.jpg)																[<img src="https://s1.ax1x.com/2022/04/14/L1YZ0H.jpg" alt="L1YZ0H.jpg" style="zoom:33%;" />](https://imgtu.com/i/L1YZ0H)

#### 2.2 通过读取配置文件创建数据源对象

> 除了使用BasieDataSource直接创建数据源对象外，还可以使用BasieDataSourceFactory工厂类读取配置文件，创建数据源对象，然后获取数据库连接对象。

- 在项目下创建一个dbcpconfig.properties文件，该文件用于设置数据库的连接信息和数据源的初始化信息。

  ~~~properties
  #连接设置
  driverClassName=com.mysql.cj.jdbc.Driver
  url=jdbc:mysql://localhost:3306/jdbc?serverTimezone=GMT2B8
  username=root
  password=root
  #初始化连接
  initialSize=5
  #最大空闲连接
  maxIdle=10
  ~~~

- 在包下创建一个Demo02.java类，该类从配置文件中获取数据库的连接信息和数据源的初始化信息。

  ~~~java
  import java.io.InputStream;
  import java.sql.Connection;
  import java.sql.DatabaseMetaData;
  import java.sql.SQLException;
  inport java.util.Properties;
  import javax.sql.DataSource;
  import org.apache.commons.dbcp2.BasicDataSourceFactory;
  public class Demo02{
      public static DataSource ds = null;
      static {
          //新建一个配置文件对象
          Properties prop = new Properties();
          try{
              //通过类加载器找到文件路径，读取配置文件
              InputStream in = new Example02().getClass().getClassLoader()
                  .getResourceAsStream("dbepconfig.properties");
              //把文件以输入流的形式加载到配置对象中
              prop.load(in);
              //创建数据源对象
              ds = BasicDataSourceFactory.createDataSource(prop);
          }catch (Exception e){
              throw new ExceptionInInitializerError(e);
          }
      }
      public static void main(String[] args)throws SQLException{
          //获取数据库连接对象
          Connection conn = ds.getConnection();
          //获取数据库连接信息
          DatabaseMetaData metaData= conn.getMetaData();
          //打印数据库连接信息
          System.out.printin(metaData.getURL()+",UserName="+metaData.getUserName()
                             +","+metaData.getDriverName());
      }
  }
  ~~~

  运行后结果与上面案例结果一致

### 3. C3P0数据库连接池

> C3P0是目前流行的开源数据库连接池之一，它实现了DataSource数据源接口，支持JDBC2和JDBC3的标准规范，易于扩展且性能优越，在使用C3P0数据库连接池开发时，需要了解C3P0中DataSource接口的实现类ComboPooledDataSource，它是C3P0的核心类，提供了数据源对象的相关方法，该类相关方法如下：

|          方法名称           |             功能描述             |
| :-------------------------: | :------------------------------: |
|   void setDriverClass( )    |     设置连接数据库的驱动名称     |
|     void setJdbcUrI( )      |       设置连接数据库的路径       |
|       void setUser( )       |       设置数据库的登录账号       |
|     void setPassword( )     |       设置数据库的登录密码       |
|   void setMaxPooISize( )    |   设置数据库连接池最大连接数目   |
|   void setMinPoolSize( )    |   设置数据库连接池最小连接数目   |
| void setlnitialPoolSize( )  | 设置数据库连接池初始化的连接数目 |
| Connection getConnection( ) |   从数据库连接池中获取一个连接   |

> 上表中的方法和DBCP所提供的方法大部分功能相同，都包含了设置数据库连接信息的方法和数据库连接池初始化的方法，以及DataSource接口中的getConnection()方法。
>
> 当使用C3P0数据库连接池时，首先需要创建数据源对象，创建数据源对象可以通过调用ComboPooledDataSource类的构造方法实现。ComboPooledDataSource类有两个构造方法，分别是`ComboPooledDataSource()`和`ComboPooledDataSource(String configName)`

#### 3.1 通过ComboPooledDataSource()构造方法创建数据源对象

> 调用ComboPooledDataSource()构造方法创建数据源对象，需要手动给数据源对象设置属性值，然后获取数据库连接对象。

- 在项目中导入`c3p0-0.9.2.1.jar`和`mchange-commons-java-0.2.3.4.jar`，然后在包下创建一个Demo03.java类，该类采用C3P0数据库连接池，并使用C3P0数据库连接池对象获取Connection对象。

  ~~~java
  import java.sql.SQLException;
  import javax.sql.DataSource;
  import com.mchange.v2.c3p0.ComboPooledDataSource;
  public class Example03 {
      public static DataSource ds = null;
      // 初始化 C3PO 数据库连接池
      static {
          ComboPooledDataSource cpds = new ComboPooledDataSource();
      }
  
      //设置连接数据库需要的配置信息
      try {
          cpds.setDriverClass("com.mysql.cj.jdbc.Driver");
          cpds.setJdbcUr1("jdbc:mysql://localhost:3306/jdbc?"+
                          "serverTimezone=GMT2B8");
          cpds.setUser("root");
          cpds.setPassword("root");
          //设置连接池的参数
          cpds.setInitialPoolSize(5);
          cpds.setMaxPoo1Size(15);
          ds = cpds; 
      }catch(Exception e) {
          throw new ExceptionInInitializerError(e);
      }
      public static void main(String[] args) throws SQLException{
          // 获取数据库连接对象
          System.out.println(ds.getConnection());
      }
  }
  ~~~

  运行结果为：`com.mchange.v2.c3p0.impl.NewProxyConnection@5577140b`，此时我们可以看到C3P0数据库连接池对象成功获取到了数据库连接对象。

#### 3.2 通过ComboPooledDataSource(String configName)构造方法创建数据源对象

> 调用ComboPooledDataSource(String configName)构造方法可以读取c3p0-config.xml配置文件，在根据配置文件中的配置信息创建数据源对象，然后获取数据库连接对象。

- 在项目的src目录下创建一个名为c3p0-config.xml的文件，用于设置数据库的连接信息和数据源的初始化信息。

  ~~~xml
  <?xml version="1.0" encoding=“UTF-8"?>
  <c3p0-config>
      <default-config>
          <property name="driverClass">com.mysql.cj.jdbc.Driver</property>
          <property name="jdbcUrl">
              jdbe:mysql://localhost:3306/jdbc?serverTimezone=GMT82B8
          </property>
          <property name="user">root</property>
          <property name="password">root</property>
          <property name="checkoutTimeout">30000</property>
          <property name="initialPoolSize">10</property>
          <property name="maxIdleTime">30</property>
          <property name="maxPoolSize">100</property>
          <property name="minPoolSize">10</property>
          <property name="maxStatements">200</property>
      </default-config>
      <named-config name="itcast">
          <property name="driverClass">com.mysql.cj.jdbc.Driver</property>
          <property name="jdbcUrl">
              jdbc:mysql://localhost:3306/jdbc?serverTimezone=GMT82B8
          </property>
          <property name="user">root</property>
          <property name="password">root</property>
          <property name="initialPoolSize">5</property>
          <property name="maxPoolSize">15</property>
      </named-config>
  </c3p0-config>
  ~~~

  > 上面代码中，c3p0-config.xml配置了两套数据源，`<default-contig>...</default-config>`中的信息是默认配置，在没有指定配置信息时默认使用该配置信息创建C3PO数据库连接池对象；`<named-config>...</named-config>`中的信息是自定义配置，一个配置文件中可以有零个或多个自定义配，当用户需要使用自定义配置时，调用ComboPooledDataSource (String configName)方法，传入`<named-config>`节点中 name 属性的值即可创建对应的C3P0 数据库连接池对象。这种设置的好处是，当程序在后期更换数据源配置时，只需要修改构造方法中对应的 name 值即可。

- 在包下创建一个Demo04.java类，该类中使用C3P0数据库连接池从配置文件中获取Connection对象。

  ~~~java
  import java.sql.SQLException;
  import javax.sql.DataSource;
  import com.mchange.v2.c3p0.ComboPooledDataSource;
  public class Example04 {
      public static DataSource ds = null;
      // 初始化 C3PO 数据库连接池
      static{
          // 使用c3p0-config.xml 配置文件中的named-config节点中name属性的值
          ComboPooledDataSource cpds = new ComboPooledDataSource("itcast"); 
          ds = cpds;
      }
      public static void main(String[] args) throws SQLException{
          System.out.println(ds.getConnection());
      }
  }
  ~~~

  运行结果为：`com.mchange.v2.c3p0.impl.NewProxyConnection@4f47d241`，此时我们可以看到C3P0数据库连接池对象成功获取到了数据库连接对象。需要注意的是在使用`ComboPooledDataSource(String configName)`方法创建数据源对象时必须遵循以下两点：

  1. 配置文件名称必须为`c3p0-config.xml`或者`c3p0.properties`，并且位于该项目的src根目录下。
  2. 当传入的configName值为空或者不存在时，使用默认配置信息创建数据源。

## 十四. DBUtils工具

> 为了更加简便地使用JDBC，我们还可以使用DBUtils工具，它是操作数据库的一个组件，实现了对JDBC的简单封装，可以在不影响数据库访问性能的情况下简化JDBC的编码工作量。DBUtils工具具有三个作用：
>
> 1. 写数据。DBUtils可以通过编写SQL语句对象数据表进行增、删、改操作
> 2. 读数据。DBUtils工具可以将从数据表中读取的数据结果集转换为Java常用类集合，以方便对结果进行处理
> 3. 优化性能。在使用DBUtils工具的基础上，程序可以使用数据源、JNDI、数据库连接池等技术减少代码冗余。
>
> DBUtils核心类库主要包括`DBUtils类`、`QueryRunner类`、`ResultSetHandler接口`、DBUtls工具主要通过这三个核心API进行JDBC操作。

- DBUtils工具的使用

  > DBUtils就是JDBC的简化开发工具包。需要项目导入commons-dbutils-1.6.jar才能够正常使用DBUtils工具。同时为类方便我们还需要将之前创建的`JDBCUtils.java`工具类导入到项目的包下<a href="#2">#</a>

- DBUtils类

  > 改类主要用于加载JDBC驱动、关闭资源的方法。DBUtils类中的方法一般为静态方法，可以直接使用类名进行调用。DBUtils类常用方法如下：

  |                   方法名                   |                             描述                             |
  | :----------------------------------------: | :----------------------------------------------------------: |
  |        void close(Connection conn)         |                   当连接不为null，关闭连接                   |
  |         void close(Statement stat)         |                   当声明不为null，关闭声明                   |
  |          void close(ResultSet rs)          |                 当结果集不为null，关闭结果集                 |
  |     void closeQuietly(Connection conn)     |  当连接不为 null，关闭连接，并隐藏一些在程序中抛出的SQL异常  |
  |     void closeQuietly(Statement stat)      | 当声明不为null时，关闭声明，并隐藏一些在程序中抛出的SQL异常  |
  |      void closeQuietly(ResultSet rs)       | 当结果集不为 null，关闭结果集，并隐藏一些在程序中抛出的SQL异常 |
  | void commitAndCloseQuietly(Connectionconn) |     提交连接后关闭连接，并隐藏一些在程序中抛出的SQL 异常     |
  | Boolean loadDriver(String driverClassName) |         装载并注册 JDBC驱动程序，如果成功就返回true          |

### 1. QueryRunner核心类

> 该类简化了执行SQL语句的代码，它与ResultSetHandler配合就能完成大部分的数据库操作，大大减少了编码量。
>
> QueryRunner类提供了带有一个参数的构造方法，改方法以javax.sql.DataSource的实例对象作为参数传递到QueryRunner的构造方法中，以此来获取Connection对象，针对不同的数据库操作，QueryRunner类提供了不同的方法。常用方法如下：

|                            方法名                            |                             描述                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| Object query(Connection conn，String sql，ResultSetHandler rsh，Object[] params) |          执行查询操作，传入的Connection对象不能为空          |
| Object query (String sql，ResultSetHandler rsh，Object[ ] params) |                         执行查询操作                         |
| Object query(Connection conn，String sql，ResultSetHandler rsh ) | 执行一个不需要置换参数的查询操作(conn为连接到的数据库对象，sql为执行数据库的预编译指令，rsh 这里可以看作一个对象集合) |
| int update(Connection conn, String sql, ResultSetHandler rsh) |              执行一个更新(插入、删除、更新)操作              |
|           int update(Connection conn, String sql)            |               执行一个不需要置换参数的更新操作               |
|   int batch(Connection conn，String sql， Object[] params)   |                     批量添加、修改、删除                     |
|            int batch(String sql，Object[] params)            |                     批量添加、修改、删除                     |

> 上面方法可以总结为：
>
> 1. update(Connection conn, String sql, Object... params) ，用来完成表数据的增加、删除、更新操作
>
> 2. query(Connection conn, String sql, ResultSetHandler rsh, Object... params) ，用来完成表数据的查询操作
> 3. int batch(Connection conn，String sql， Object[] params)   批量执行增、删、改操作

#### 1. 1 QueryRunner实现添加、更新、删除操作

> update(Connection conn, String sql, Object... params) ，用来完成表数据的增加、删除、更新操作

- 添加

  ~~~java
  public void insert(){
     try {
         //获取一个用来执行SQL语句的对象   QueryRunner
         QueryRunner qr = new QueryRunner();
         
         String sql = "INSERT INTO zhangwu(name,money,parent) VALUES(?,?,?)";
         Object[] params = {"股票收入", 5500, "收入"};
         // JDBCUtils这个工具是上篇所提到的工具类
         Connection conn = JDBCUtils.getConnection();
         int line = qr.update(conn,sql,params);// 用来完成表数据的增加、删除、更新操作
         //结果集处理
         System.out.println("line = " + line);
         
     } catch (SQLException e) {
         throw new RuntimeException(e);
     }
  }
  ~~~

- 更新（改）

  ~~~java
  public void update(){
     try {
         //创建一个QueryRunner对象，用来完成SQL语句的执行
         QueryRunner qr = new QueryRunner();
         //执行SQL语句
         String sql = "UPDATE zhangwu SET money = money+1000 WHERE name=?";
         Object[] params = {"股票收入"};
         Connection conn = JDBCUtils.getConnection();
         int line = qr.update(conn, sql, params);
         //结果集的处理
         System.out.println("line="+line);
         
     } catch (SQLException e) {
         throw new RuntimeException(e);
     }
  }
  ~~~

- 删除

  ~~~java
  public void delete(){
     try {
         //创建一个QueryRunner对象，用来完成SQL语句的执行
         QueryRunner qr = new QueryRunner();
         //执行SQL语句
         String sql = "DELETE FROM zhangwu WHERE name = ?";
         Object[] params = {"股票收入"};
         Connection conn = JDBCUtils.getConnection();
         int line = qr.update(conn, sql, params);
         //结果集的处理
         System.out.println("line="+line);
         
     } catch (SQLException e) {
         throw new RuntimeException(e);
     }
  }
  ~~~

### 2. ResultSetHandler接口及它的实现类

> 该接口用于处理结果集ResultSet，它可以将结果集中的数据转换为不同的形式。根据结果集中不同的数据类型，ResultSetHandler接口提供了以下集中实现类：
>
> - BeanHandler：将结果集中的第一行数据封装到一个对应的JavaBean实例中
> - BeanListHandler：将结果集中的每一行数据都封装到一个对应的JavaBean实例中，并存放到List里。
> - ColumnListHandler：将某列属性的值封装到List集合中
> - ScalarHandler：讲结果集中某一条记录的某一列数据存储成Object对象。

#### 2.1 BeanHandler类和BeanListHandler类

> BeanHandler类和BeanListHandler类是将结果集中的数据封装到对应的JavaBean中。在封装时，表中的数据的字段和JavaBean的属性是相互对应的，一条数据记录被封装进一个对应的JavaBean对象中。这两个实现类的对比如下：

|      类名       |            相同点            |                            不同点                            |
| :-------------: | :--------------------------: | :----------------------------------------------------------: |
|   BeanHandler   | 都要先将结果集封装进JavaBean |  封装单条数据，把结果集的第一条数据的字段放入一个JavaBean中  |
| BeanListHandler | 都要先将结果集封装进JavaBean | 封装多条数据，把每条数据的字段值各放入一个JavaBean中，再把所有JavaBean都放入List集合中 |

示例：

- 在名为jdbc的数据库中创建数据表user

  ~~~Mysql
  USE jdbc;
  CREATE TABLE user(
      id INT(3) PRIMARY KEY AUTO INCREMENT,
      name VARCHAR(20) NOT NULL,
      password VARCHAR(20) NOT NULL
  );
  ~~~

- 向user表插入三条数据

  ~~~MySQL
  INSERT INTO user(name,password) VALUES ('zhangsan','123456');
  INSERT INTO user(name,password) VALUES ('lisi','123456');
  INSERT INTO user(name,password) VALUES ('wangwu','123456');
  ~~~

- 再包下创建一个BaseDao.java文件，在类中编写一个统用的查询方法

  ~~~java
  import java.sql.Connection;
  import java.sql.PreparedStatement;
  import java.sql.ResultSet;
  import java.sql.SQLException;
  
  import org.apache.commons.dbuti1s.ResultSetHandler;
  public class BaseDao {
      //优化查询
      public static Object query(String sql, ResultSetHandler<?> rsh,Object... params) throws SQLException{
          Connection conn =null;
          PreparedStatement pstmt = null;
          ResultSet rs = null;
          try{
              // 获得连接
              conn = JDBCUtils.getConnection();
              // 预编译 sql
              pstmt= conn.prepareStatement(sql);
              //将参数设置进去
              for(int i = 0; params!= null && i< params.length;i++){
                  pstmt.setObject(i + 1, params[i]); 
              }
  
              // 发送sql
              rs = pstmt.executeQuery();
              // 让调用者去实现对结果集的处理
              Object obj = rsh.handle(rs);
              return obj;
  
          }catch(Exception e) {
              e.printStackTrace();
          }finally{
              //释放资源
              JDBCUtils.release(rs, pstmt, conn);
          }
          return;
      }
  }
  ~~~

- 创建一个实体类User.java用于封装User对象。

  ~~~java
  package cn.itcast.chapter1l.example;
  public class User {
      private int id;
      private String name;
      private String password;
      public int getId(){
          return id;  
      }
      public void setId(intid){
          this.id = id;
      }
  
      public String getName(){
          return name;
      }
      public void setName(String name){
          this.name = name;
      }
  
      public String getPassword(){
          return password;
      }
      public void setPassword(String password){
          this.password = password;
      } 
  }
  ~~~

- 在包下创建一个ResultSetTest01.java类，用于演示BeanHandler类对结果集的处理。

  ~~~java
  package cn.itcast.chapter1l.example;
  import java.sql.SQLException;
  import org.apache.commons.dbutils.handlers.BeanHandler;
  public class ResultSetTest01{
      public static void testBeanHandler() throws SQLException{
          BaseDao basedao = new BaseDao();
          String sql = "select * from user where id=?";
          User user = (User) basedao.query(sql,new BeanHandler(User.class),1);
          System.out.print("id为1的User对象的name值为："+user.getName());
      }
      public static void main(String[] args) throws SQLException{
          testBeanHandler(); 
      }
  }
  ~~~

运行ResultSetTest01结果入下：

[ResultSetTest01运行结果：](https://s1.ax1x.com/2022/04/17/LUQEy6.jpg)

​								[<img src="https://s1.ax1x.com/2022/04/17/LUQEy6.jpg" alt="LUQEy6.jpg" style="zoom: 25%;" />](https://imgtu.com/i/LUQEy6)

- 在包下创建一个ResultSetTest02.java类，用于演示BeanListHandler类对结果集的处理

  ~~~java
  package cn.itcast.chapter11.example;
  import java.sql.SQLException;
  import java.util.ArrayList;
  import org.apache.commons.dbutils.handlers.BeanListHandler;
  public class ResultSetTest2 {
      @Test
      public static void testBeanListHandler() throws SQLException {
          BaseDao basedao = new BaseDao();
          String sql = "select * from user";
          ArrayList<User> list = (ArrayList<User>) basedao.query(sql,new BeanListHandler(User.class));
          for (int i = 0; i< list.size(); i++){
              System.out.println("第" +(i + 1)+ "条数据的username值为："+ list.get(i).getName());   
          }
      }
  }
  ~~~

此时运行ResultSetTest02结果为：

[ResultSetTest02运行结果：](https://s1.ax1x.com/2022/04/17/LU1mPH.jpg)																					[<img src="https://s1.ax1x.com/2022/04/17/LU1mPH.jpg" alt="LU1mPH.jpg" style="zoom:25%;" />](https://imgtu.com/i/LU1mPH)

#### 2.2 ColumnListHandle和ScalarHandler类

> ColumnListHandle和ScalarHandler类可以对指定的列表数据进行封装，在封装时查询指定列数据，然后将获得的列数据封装到容器中。ColumnListHandle和ScalarHandler类对比如下：

|       类名       |              相同点              |                            不同点                            |
| :--------------: | :------------------------------: | :----------------------------------------------------------: |
| ColumnListHandle | 都是对指定列的查询结果集进行封装 |        封装指定列的所有数据，将他们放入一个List集合中        |
|  ScalarHandler   | 都是对指定列的查询结果集进行封装 | 封装单条列数据，也可以封装类似count、avg、max、min、sum等聚合函数的执行结果 |

> 由上表可知ColumnListHandle可以对指定列的所有数据进行封装，ScalarHandler主要对单行单列的数据进行封装。
>
> 在使用DBUtils工具操作数据库时，如果需要输出结果集中所有数据的值，可以使用ColumnListHandle类，下面演示该类的使用：

- 在包下创建一个ResultSetTest03.java类，用于演示ColumnListHandle类的使用方法

  ~~~java
  package cn.itcast.chapter11.example;
  import java.sql.SQLException;
  import org.apache.commons.dbutils.handlers.ColumnListHandler; 
  public class ResultSetTest03 {
      @Test
      public static void testColumnListHandler() throws SQLException{
          BaseDao basedao = new BaseDao();
          String sql="select*from user";
          Object arr=(Object)basedao.query(sql,new ColumnListHandler("name"));
          System.out.println(arr);
      }
  }
  ~~~

运行ResultSetTest03结果为：

[ResultSetTest04运行结果：](https://s1.ax1x.com/2022/04/17/LUYJ8e.jpg)

​												[<img src="https://s1.ax1x.com/2022/04/17/LUYJ8e.jpg" alt="LUYJ8e.jpg" style="zoom:25%;" />](https://imgtu.com/i/LUYJ8e)

> 在使用DBUtils工具操作数据库时，如果需要输出结果集中一行数据的指定字段值，可以使用ScalarHandler类。

- 在包下创建一个ResultSetTest04.java类，用于演示ScalarHandler类。

  ~~~java
  package cn.itcast.chapter11.example;
  import java.sql.SQLException;
  import org.apache.commons.dbutils.handlers.ScalarHandler; 
  public class ResultSetTest04{
      @Test
      public static void testScalarHandler() throws SQLException {
          BaseDao basedao = new BaseDao();
          String sql="select*from user where id=?";
          Object arr = (Object) basedao.query(sql,new ScalarHandler("name"),1) ;
          System.out.println(arr);   
      }
  }
  ~~~

运行ResultSetTest04结果如下：
[ResultSetTest04运行结果：](https://s1.ax1x.com/2022/04/17/LUY0VP.jpg)

​												[<img src="https://s1.ax1x.com/2022/04/17/LUY0VP.jpg" alt="LUY0VP.jpg" style="zoom:25%;" />](https://imgtu.com/i/LUY0VP)

> 由输出结果可知ScalarHandler类成功将id为1的用户的name列存成一个对象arr

### 3. 使用DBUtils实现增删改查

> 由于每次操作数据库时，都需要加载数据库驱动、建立数据库连接和关闭数据库连接，为了避免重复书写代码，需要建立一个专门用于操作数据库的工具类。
>
> 使用DBUtils工具对数据库中的用户信息进行增删改查操作，首先需要创建用户实体类User类，与数据库user表中的数据进行映射；然后创建一个工具类，用于创建数据源对象；最后创建增删改查操作的DAO类，在各DAO类中编写其对应的增删改查逻辑。

- **创建表**，本项目需要用到BeanHandler类和BeanListHandler类小节中创建的user表。

- **创建JavaBean，**在包下创建User.java的JavaBean用来做实体对象

  ~~~java
  package cn.itcast.chapter1l.example;
  public class User {
      private int id;
      private String name;
      private String password;
      public int getId(){
          return id;  
      }
      public void setId(intid){
          this.id = id;
      }
  
      public String getName(){
          return name;
      }
      public void setName(String name){
          this.name = name;
      }
  
      public String getPassword(){
          return password;
      }
      public void setPassword(String password){
          this.password = password;
      } 
  }
  ~~~

- **创建C3p0Utils工具类**，在包下创建一个C3p0Utils.java类，用于创建数据源。

  ~~~java
  package cn.itcast.jdbc.utils;
  import javax.sql.DataSource;
  import com.mchange.v2.c3p0.ComboPooledDataSource;
  public class C3p0Utils {
      private static DataSource ds;
      static {
          ds = new ComboPooledDataSource();
  
      }
      public static DataSourcegetDataSource(){
          return ds;
      }
  }
  ~~~

- **创建InsertDao类**，在包下创建一个InsertDao.java类，实现对user表插入数据操作。

  ~~~java
  package cn.itcast.jdbc.dao;
  import java.sql.SQLException;
  import org.apache.commons.dbutils.QueryRunner;
  public class InsertDao {
      public static void main(String[] args)throws SQLException{
          // 创建QueryRunner 对象
          QueryRunner runner = new QueryRunner(C3p0Utils.getDataSource());
          String sql = "insert into user(name, password) values('hello1',123456)";
          int num = runner.update(sql);
          if (num > 0){
              System.out.print1n("添加成功！");
          }else{
              System.out.println("添加失败！");
          }
      }
  }
  ~~~

  > 上面代码中第7行创建QueryRunner对象；第8行声明了一条插入的sql语句；第9行~第12行执行插入语句并判断插入是否成功。

  运行InsertDao结果如下：
  [InsertDao运行结果：](https://s1.ax1x.com/2022/04/17/LUdCkt.jpg)

  [<img src="https://s1.ax1x.com/2022/04/17/LUdCkt.jpg" alt="LUdCkt.jpg" style="zoom:25%;" />](https://imgtu.com/i/LUdCkt)

- **创建UpdateDao类**，在包下创建一个UpdateDao.java类用于实现对表的修改操作

  ~~~java
  import org.apache.commons.dbutils.QueryRunneri;
  import java.sql.SQLException;
  public class UpdateDao {
      public static void main(String[] args)throwsSQLException {
          // 创建QueryRunner 对象
          QueryRunner runner = new QueryRunner(C3p0Utils.getDataSource());
          //写SQL语句
          String sql ="update user set name=hel1o2,password=111111 where name=hel1o1";
          // 调用方法
          int num = runner.update(sql);
          if(num > 0){
              System.out.print1n("修改成功！")
          }
          else{
              System.out.println("修改失败！");
          }
      }
  }
  ~~~

  运行UpdateDao结果如下：

  [UpdateDao结果：](https://s1.ax1x.com/2022/04/17/LUw9u4.jpg)                                [![LUw9u4.jpg](https://s1.ax1x.com/2022/04/17/LUw9u4.jpg)](https://imgtu.com/i/LUw9u4)

- **创建DeletDao类**，创建DeletDao.java类进行删除操作

  ~~~java
  import org.apache.commons.dbutils.QueryRunner;
  import java.sql.SQLException;
  public class DeleteDao {
      public static void main(String[] args)throws SQLException{
          //创建QueryRunner对象
          QueryRunner runner = new QueryRunner(C3p0Utils.getDataSource());
          //写SQL 语句
          String sql ="delete from user where name='hello2'";
          // 调用方法
          int num = runner.update(sql);
          if(num > 0){
              System.out.println("删除成功！");
          }else{
              System.out.println("删除失败！");
          }
      }
  }
  ~~~

  > 第6行代码创建了QueryRunner对象；第8行代码定义了一条删除语句。

  运行DeleteDao结果如下：

  [DeleteDao运行结果：](https://s1.ax1x.com/2022/04/17/LUwhZ9.jpg)                                        [<img src="https://s1.ax1x.com/2022/04/17/LUwhZ9.jpg" alt="LUwhZ9.jpg" style="zoom:25%;" />](https://imgtu.com/i/LUwhZ9)

- **创建QueryDao类**，在包下创建！QueryDao.java类，实现对user表中单条数据的查询操作。

  ~~~java
  import org.apache.commons.dbutils.QueryRunner;
  import org.apache.commons.dbutils.handlers.BeanHandler;
  import java.sql.SQLException;
  public class QueryDao {
      public static void main(String[] args)throws SQLException{
          // 创建QueryRunner 对象
          QueryRunner runner = new QueryRunner(C3p0Utils.getDataSource());
          // 写 SQL 语句
          String sql = "select  from user where id=2";
          // 调用方法
          User user = (User)runner.query(sql,new BeanHandler(User.class));
          System.out.println(user.getId()+","+user.getName()+", "tuser.getPassword());
      }
  }
  ~~~

  运行QueryDao结果如下：
  [QueryDao运行结果：](https://s1.ax1x.com/2022/04/17/LUGJIO.jpg)

  ​                                    [<img src="https://s1.ax1x.com/2022/04/17/LUGJIO.jpg" alt="LUGJIO.jpg" style="zoom:25%;" />](https://imgtu.com/i/LUGJIO)

- 上一个Dao是查询一条数据，我们更多的时候是需要查询一个表中的所有数据我们对QueryDao.java进行修改

  ~~~java
  import org.apache.commons.dbutils.QueryRunner;
  import org.apache.commons.dbutils.handlers.BeanListHandler;
  import java.sql.SQLException;
  import java.util.List;
  public class QueryDao {
      public static void main(String[] args)throws SQLException{
          // 创建QueryRunner 对象
          QueryRunner runner = new QueryRunner(C3p0Utils.getDataSource());
          //写SQL语句
          String sql ="select*from user";
          // 调用方法
          List<User> list = (List)runner.query(sql,new BeanListHandler(User.class));
          for(User user : list){
              System.out.println(user.getId()+","tuser.getName ()+", "+user.getPassword());
          }
      }
  }
  ~~~

  > 上面的第12~14行代码将全部数据查询并输出

  运行以上代码结果如下：
  [修改后QueryDao结果如下：](https://s1.ax1x.com/2022/04/17/LUJ51H.jpg)

​                                                      [<img src="https://s1.ax1x.com/2022/04/17/LUJ51H.jpg" alt="LUJ51H.jpg" style="zoom:25%;" />](https://imgtu.com/i/LUJ51H)

> 至此DBUtils工具对数据库中数据进行增删改查的操作已全部完成，需要注意的是，在查询方法中，用到BeanHandler和BeanListHandler实现类来处理结果集。查询一条数据使用能够处理一行数据的BeanHandler类，查询所有数据使用能处理所有数据的BeanListHandler类，切勿错误使用。

## 十五. Ajax

> Ajax(异步的Javascript和Xml)技术可以实现页面的局部更新，数据异步交互的方式给用户带来了极大的便利。使用JavaScript可以实现Ajax的操作，但比较复杂。开发不方便。Jquery对JavaScript进行了二次封装，重新也对Ajax的操作重新进行了整理和封装。

- Ajax概述

  > Ajax是一种Web应用技术，该技术史在Javascript、DOM、服务器配合下，实现浏览器向服务器发送异步请求。
  >
  > 传统方式是在页面跳转或者刷新时发出请求，每次发出请求都会请求一个新的页面。即使刷新页面也要重新加载当前页面。而Ajax异步请求方式不同于传统请求方式，通过Ajax异步请求方式向服务武器发出请求，得到数据后再更新页面(通过DOM操作修改页面内容)，整个过程不会发生页面跳转或者刷新操作。
  >
  > 传统请求方式和Ajax的请求方式对比如下：

  [传统请求方式：](https://s1.ax1x.com/2022/04/19/LBrOqx.jpg) 
  
  ​                          [<img src="https://s1.ax1x.com/2022/04/19/LBrOqx.jpg" alt="LBrOqx.jpg" style="zoom:25%;" />](https://imgtu.com/i/LBrOqx)                                                 

​		[Ajax请求方式：](https://s1.ax1x.com/2022/04/19/LBsJoT.jpg)                                  	[<img src="https://s1.ax1x.com/2022/04/19/LBsJoT.jpg" alt="LBsJoT.jpg" style="zoom:25%;" />](https://imgtu.com/i/LBsJoT)

- 两种方式区别：

  |       方式       | 遵循协议 |         请求发出方式         |             数据展示方式              |
  | :--------------: | :------: | :--------------------------: | :-----------------------------------: |
  |   传统请求方式   |   HTTP   |       页面连接跳转发出       |            重新载入新页面             |
  | Ajax异步请求方式 |   HTTP   | 由XMLHttpRequest实例发出请求 | Javascript和DOM技术把数据更新到本页面 |

- Ajax异步请求优势：
  1. 请求数据量少：因为Ajax请求只需要得到必要数据，对不需要更新的数据不做请求，所以数据量少，传输时间较短
  2. 请求分数：Ajax是按需要请求的额，请求是异步执行的，可在任意时刻发出，所以请求不会集中爆发，一定程度上减轻了服务器的压力，响应速度比较快
  3. 用户体验优化：Ajax数据请求响应时间短，数据传送速度快，已经很大程度上提升了用户的使用体验。又由于Ajax是异步请求，不会刷新页面，故页面上用户行为得到了有效保留。

### 1. JQuery框架

> 要使用Ajax需要使用JavaScript和DOM技术，相对较复杂，所以我们最常用就是框架，这里先以JQuery为例。
>
> JQuery是一款跨浏览器的开源JavaScript库，它使DOM、事件处理、Ajax等功能的实现代码更加简洁，有效提搞了程序开发效率。

#### 1.1 JQuery下载和使用

> 登录JQuery官网，进行下载。这里建议选择下载压缩版本

- 引入JQuery

  > 在项目中引入Jquery时，只需要把下载好的JQuery文件保存到项目的Web目录中，在项目的HTML或JSP文件中使用`<script>`标签引入即可

  ~~~html
  <script src="jquery-3.6.0.js"></script>
  ~~~

  > 除了引入下载好的JQuery文件，许多网站还提供了静态资源公共库，通过导入静态资源地址也可以引入JQuery文件，如下：

  ~~~html
  <script src="https://code.jquery.com/jquery-3.6.0.js"></script>
  ~~~

#### 1.2 JQuery的常用操作

> 常用操作包括选择器的使用、元素对象的操作、事件的绑定、链式编程等。

- 选择器的使用

  JQuery选择器用于获取网页元素对象。JQuery选择器以"$"符号开头，语法示例如下：

  ~~~html
  <div id="myId"></div>
  <script>									
  	$('#myId');						//获取id值为myId的元素对象
  </script>
  ~~~

- 元素对象的操作

  JQuery中对获取的元素对象可以进行一列操作，例如元素的取值、赋值、属性的设置等，语法示例如下：

  ~~~html
  <div id="myId">content</div>
  <script>
  	var html=$('myId').html();		//获取id为"myId"元素里的文本信息
      alert(html);
      
      $('myId').html("hello")			//执行后，id为'myId'元素里的内容变为'hello'
  </script>
  ~~~

- 事件的绑定

  在JQuery中，事件一般直接绑定在元素上。例如，为指定元素对象绑定单击事件，语法示例如下：

  ~~~html
  <button>hello</button>
  <script>
      $('button').click(function(){
          alert('hello')
      });
      //或者如下代码：
      $('button').addEventListener('click',function(){
          alert('hello')
      });
  </script>
  ~~~
  
- 链式编程

  JQuery中支持多个链式编程方法，在完成相同功能的情况下，开发者可以编写最少的代码。多个方法链式调。用语法示例如下：

  ~~~html
  <ul>
      <li>0</li>
      <li>1</li>
      <li>2</li>
      <li>3</li>
  </ul>
  <script>
      //多个方法调用，将ul中索引为2的li元素的内容设置为hello
  	$('ul').find('li').eq(2).html('hello');
  </script>
  ~~~

#### 1.3 JQuery中的load()方法

> 由于XMLHttprequest对象发送Ajax请求操作较为繁琐，因此JQuery对这些操作做了一些列的封装简化，提供了一系列向服务器请求数据的方法。JQuery提供的方法大致可以分为两类，一类是用于发送请求的`$.get()`和`$.post()`方法；另一类适用于获取与不同格式数据的`load()`方法、`$.getJOSN()`方法、`$.getScript()`方法。

在JQuery的Ajax请求方法中，load()方法可以请求HTML内容，并使用获得的数据替换指定元素的内容。语法示例如下：

~~~JavaScript
load(url,data,callback);
~~~

参数说明：

|  参数名  |            描述            |
| :------: | :------------------------: |
|   url    | 必须的，指定加载资源的路径 |
|   data   |  可选，发送至服务器的数据  |
| callback | 可选，请求完成时执行的函数 |

下面进行几个方法示例：

- 请求HTML文件

  > load()方法最基本的用法是远程请求莫格页面的文档内容(JSP、HTML等)，并将获取到的内容插入本页面的某个部分，下面是项目示例：

  首先在项目的web目录下创建load.jsp的文件。

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
          <%--导入JQuery的JAR包，在导入时使用下面语句取出部署的应用程序名--%>
          <script src="${pageContext.request.contextpaht}/jquery-3.6.0.js"></script>
      </head>
      <body>
          <button id="btn">加载数据</button>
          <div id='box'></div>
          <script>
          	$('#btn').click(function(){
                  <%--触发按钮时候执行的事件：利用id值为'box'的元素对象调用load()方法，加载target.jsp文件--%>
                 $('#box').load('http://localhost:8080/Demo/target.jsp');
              });
          </script>
      </body>
  </html>
  ~~~

  之后在相同目录下创建一个名为target.jsp的文件

  > 下面pre标签：标签可定义预格式化的文本。被包围在 `<pre> `标签 元素中的文本通常会保留空格和换行符。而文本也会呈现为等宽字体。

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>target</title>
      </head>
      <body>
          <h3>静夜思</h3>
          <h6>唐 李白</h6>
          <pre>
          	床前明月光，
          	疑是地上霜。
          	低头望明月，
          	低头思故乡。
          </pre>
      </body>
  </html>
  ~~~

  启动Tomcat在浏览器上输入：http://localhost:8080/Demo/load.jsp单击加载数据按钮，会在id为`box`的盒子中显示出target文件中的内容。浏览器局部更新了数据。在局部更新的后面是使用load()方法，从target文件中获取数据，并将数据作为JSP内容插入id为box的目标元素内。

#### 1.4 向服务器发送数据

> load()方法在发送请求时，可以附带一些数据，要附带的数据可以通过第二个参数传递。下面通过示例演示：

- 在项目的web目录下创建名为load2.jsp的文件。

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
          <%--导入JQuery的JAR包，在导入时使用下面语句取出部署的应用程序名--%>
          <script src="${pageContext.request.contextpaht}/jquery-3.6.0.js"></script>
      </head>
      <body>
          <button id="btn">加载数据</button>
          <div id='box'></div>
          <script>
          	$('#btn').click(function(){
                  <%--触发按钮时候执行的事件：利用id值为'box'的元素对象调用load()方法，加载target.jsp文件--%>
                 $('#box').load('http://localhost:8080/Demo/target.jsp',
                                {username:'itcast',password:'123'});
              });
          </script>
      </body>
  </html>
  ~~~

  > 上面load()方法的第2个参数是对象类型的数据，该数据将被发送到Servlet服务器

- 编写一个Load2Servlet.java的文件，用于获取load2.jsp文件发送的数据

  ~~~java
  import javax.servlet.ServletException;
  import javax.servlet.annotation.WebServlet;
  import javax.servlet.http.HttpServlet;
  import javax.servlet.http.HttpServletRequest;
  import javax.servlet.http.HttpServletResponse;
  import java.io.IOException;
  @WebServlet(name ="Load2Servlet",urlPatterns="/Load2Servlet")
  public class Load2Servlet extends HttpServlet{
      public void doGet(HttpServletRequest request, HttpServletResponse
                        response) throws ServletException, IOException{
          response.setContentType("text/html;charset=utf-8");
          //获取1oad2.jsp页面的username与password值
          String username=request.getParameter("username");
          String password=request.getParameter("password");
          response.getWriter().print1n("注册成功！<br/>用户名："+username+"<br/>密码："+password);
      }
      public void doPost(HttpServletRequest request, HttpServletResponse
                         response) throws ServletException, IOException{
          doGet (request, response) ;
      }
  }
  ~~~

  启动Tomcat浏览器访问：http://localhost:8080/Demo/load2.jsp之后点击页面上的`加载数据`按钮结果如下：

  [locad启动结果：](https://s1.ax1x.com/2022/04/19/LDGYQO.jpg)

  ​                             [<img src="https://s1.ax1x.com/2022/04/19/LDGYQO.jpg" alt="LDGYQO.jpg" style="zoom:25%;" />](https://imgtu.com/i/LDGYQO)

#### 1.5 回调函数

> load()函数第三个参数是回调函数，该函数在请求数据加载完成后执行。回调函数用于获取本次请求的相关信息，他又三个默认参数，分别表示响应数据、请求状态和XMLHttpRequest对象。

下面对回调函数进行演示：

~~~jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>Tit1e</title>
        <%--导入JQuery的JAR包，在导入时使用下面语句取出部署的应用程序名--%>
        <script src="${pageContext.request.contextpaht}/jquery-3.6.0.js"></script>
    </head>
    <body>
        <button id="btn">加载数据</button>
        <div id='box'></div>
        <script>
            $('#btn').click(function(){
                <%--触发按钮时候执行的事件：利用id值为'box'的元素对象调用load()方法，加载target.jsp文件--%>
                $('#box').load('http://localhost:8080/Demo/target.jsp',
                               {username:'itcast',password:'123'},function(resopnData,status,xhr){
                    console.log(resopnData);
                    console.log(status);
                    console.log(xhr);                   
               });
            });
        </script>
    </body>
</html>
~~~

> 上面代码作用是在控制台输出load()方法回调函数中的参数，即请求的结果数据、请求状态和XMLHttpRequest对象。其中status参数五种状态为：success(成功)、notmodified(未修改)、error(错误)、timeout(超时)、parsererror(解析错误)。

启动Tomcat在浏览器中输入：http://localhost:8080/Demo/load2.jsp后再单击加载数据按钮，页面效果如下：

[修改后的load效果如下：](https://s1.ax1x.com/2022/04/19/LDNA74.jpg)

​                                         [<img src="https://s1.ax1x.com/2022/04/19/LDNA74.jpg" alt="LDNA74.jpg" style="zoom:25%;" />](https://imgtu.com/i/LDNA74)

如上图所示，请求结果依次是：请求的结果数据(load2.jsp的文档内容)、请求状态和请求对应的XMLHttpRequest对象。

#### 1.6 发送GET和POST请求

> JQuery提供了`$.get()`方法和`$.post()`方法，分别用于发送GET请求和POST请求。下面对这两个方法进行详解：

##### 1.6.1 `$.get()`方法

> JQuery中的$.get()方法用于向服务器发送GET请求。该方法是JQuery的静态方法，语法格式如下：

~~~JavaScript
$.get(url,data,function(data,status,xhr),dataType)
~~~

$.get()方法参数含义如下：

|           参数            |                             描述                             |
| :-----------------------: | :----------------------------------------------------------: |
|            url            |                 必须，要请求的服务器文件路径                 |
|           data            |               可选，发送至服务器请求文件的数据               |
| function(data,status,url) | 可选，请求成功时执行的函数，其参数含义如：data(表示从服务器返回的数据)、status(表示请求的状态值)、xhr(表示当前请求相关的XMLHttpRequest对象) |
|         dataType          | 可选，预期的服务器相应的数据类型(xml、html、text、script、jsonp) |

- 在项目的web目录下创建名称为get.jsp的文件，在该文件中调用$.get()方法请求之前编写的target.jsp文件，并将返回的数据显示到页面指定位置

  ~~~html
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
          <%--导入JQuery的JAR包，在导入时使用下面语句取出部署的应用程序名--%>
          <script src="${pageContext.request.contextpaht}/jquery-3.6.0.js"></script>
      </head>
      <body>
          <button id="btn">加载数据</button>
          <div id='box'></div>
          <script>
              $('#btn').click(function(){
                  <%--第二个参数为请求成功后执行的回调函数。回调函数的参数data表示服务器返回的数据。--%>
                  $.get('http://localhost:8080/Demo/target.jsp',function(data){
                      <%--将返回的数据替换到id为box的元素中--%>
                      $('#box').html(data);
                  },'html');
              });
          </script>
      </body>
  </html>
  ~~~

  启动Tomcat在浏览器中输入：http://localhost:8080/Demo/get.jsp出现页面后点击`加载数据`按钮，输出结果如下：

  [get.jsp运行结果：](https://s1.ax1x.com/2022/04/21/L67Pq1.jpg)

  ​                                   [<img src="https://s1.ax1x.com/2022/04/21/L67Pq1.jpg" alt="L67Pq1.jpg" style="zoom:25%;" />](https://imgtu.com/i/L67Pq1)

- 调用$.get()方法发送数据

  > 调用该方法发送数据时，需要将数据作为$.get()方法的参数。

  创建一个名为get2.jsp的文件

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
          <%--导入JQuery的JAR包，在导入时使用下面语句取出部署的应用程序名--%>
          <script src="${pageContext.request.contextpaht}/jquery-3.6.0.js"></script>
      </head>
      <body>
          <button id="btn">加载数据</button>
          <div id='box'></div>
          <script>
              $('#btn').click(function(){
                  var userData={username:'itcast',password:123};
                  <%--第二个参数userData表示向服务器发送请求时携带的数据--%>
  				$.get('http://localhost:8080/Demo/Load2Servlet.java',userData,function(data){
                      $('$box').html(data);
                  },'html');
              });
          </script>
      </body>
  </html>
  ~~~

  编写一个Load2Servlet.java的文件，用于获取get2.jsp文件发送的数据

  ~~~java
  import javax.servlet.ServletException;
  import javax.servlet.annotation.WebServlet;
  import javax.servlet.http.HttpServlet;
  import javax.servlet.http.HttpServletRequest;
  import javax.servlet.http.HttpServletResponse;
  import java.io.IOException;
  @WebServlet(name ="Load2Servlet",urlPatterns="/Load2Servlet")
  public class Load2Servlet extends HttpServlet{
      public void doGet(HttpServletRequest request, HttpServletResponse
                        response) throws ServletException, IOException{
          response.setContentType("text/html;charset=utf-8");
          //获取1oad2.jsp页面的username与password值
          String username=request.getParameter("username");
          String password=request.getParameter("password");
          response.getWriter().print1n("注册成功！<br/>用户名："+username+"<br/>密码："+password);
      }
      public void doPost(HttpServletRequest request, HttpServletResponse
                         response) throws ServletException, IOException{
          doGet (request, response) ;
      }
  }
  ~~~

  启动Tocmat并在浏览器中输入：http://localhost:8080/Demo/get2.jsp后点击页面`加载数据`按钮，显示结果如下：

  [get2运行结果：](https://s1.ax1x.com/2022/04/21/L6bXIP.jpg)

  ​                               [<img src="https://s1.ax1x.com/2022/04/21/L6bXIP.jpg" alt="L6bXIP.jpg" style="zoom:25%;" />](https://imgtu.com/i/L6bXIP)

##### 1.6.2 $.post()方法

> 在JQuery中发送POST请求要掉用$.post()方法。这与之前的get方法使用完全相同。替换两者的方法名即可在JQuery中使用。

示例：

- 修改get2.jsp文件中的get方法

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Tit1e</title>
          <%--导入JQuery的JAR包，在导入时使用下面语句取出部署的应用程序名--%>
          <script src="${pageContext.request.contextpaht}/jquery-3.6.0.js"></script>
      </head>
      <body>
          <button id="btn">加载数据</button>
          <div id='box'></div>
          <script>
              $('#btn').click(function(){
                  var userData={username:'itcast',password:123};
                  <%--第二个参数userData表示向服务器发送请求时携带的数据--%>
  				$.post('http://localhost:8080/Demo/Load2Servlet.java',userData,function(data){
                      $('$box').html(data);
                  },'html');
              });
          </script>
      </body>
  </html>
  ~~~

  启动Tomcat后运行和get2.jsp运行结果一样。

### 2. JSON数据格式

> 前面的get和post方法发送Ajax请求，这些方法都可以获取服务器返回的数据。在实际开发中，服务器返回的数据都会遵循一定的的格式，例如XML、JSON和TEXT等。按照一定的格式保存数据，可以确保JavaScript程序能够正确解析，识别这些数据。在Ajax请求中，最常用的数据格式为JSON。
>
> JSON是一种键值对存储数据的格式。类似于JavaScript的对象格式。它的优势在于数据能被处理成对象。方便获取信息字段。JSON的数据格式如下：

~~~json
[
    {
        "name":"Java 基础”,
        "author":"黑马程序员”,
        "price":"$30"
    },{
        "name":"Java进阶",
        "author":"黑马程序员",
        "price":"$20"
    }
]
~~~

> JSON数组数据都存储在一对[]中，在[]中每一组数据用{}分开。多个组之间用逗号分割。需要注意的是，如果值为String类型，则需要使用双引号引起来，如果为number、object、boolean和数组的话，可以不适用双引号。下面是以一个案例：

- 首先需要下载JAR包并导入

  > 这里需要使用6个JAR包，分别是：`json-lib-2.4-jdk15.jar`、`ezmorph-1.0.6.jar`、`commons-logging-1.1.1.jar`、`commons-lang-2.5.jar`、`commons-collections-3.2.1.jar`、`commons-beanutils-1.8.0.jar`。这些JAR包可以在Maven官网下载。下载后将这6个包复制到WEB-INF下的lib目录下。

- 实现Servlet发送JSON格式的数据

  > 在项目的src目录下新建名为Book.java的类，在其中定义3个变量，用于存储Book实例的书名、价格和作者。

  ~~~java
  public class Book{
      private String name; 			//书名
      private double price; 			//价格
      private String author; 			//作者
      public String getName(){
          return name; 
      }
  
      public void setName(String name){
          this.name = name;
      }
  
      public double getPrice(){
          return price;
      }
  
      public void setPrice(double price){
          this.price = price; 
      }
  
      public String getAuthor(){
          return author; 
      }
  
      public void setAuthor(String author){
          this.author = author;
      }
  }
  ~~~

- 在src目录下新建名称为JSONServlet.java的类，用于向前端页面传递JSON数据。

  ~~~java
  import net.sf.json.JSONArray;
  import javax.servlet.ServletException;
  import javax.servlet.annotation.WebServlet;
  import javax.servlet.http.HttpServlet;
  import javax.servlet.http.HttpServletRequest;
  import javax.servlet.http.HttpServletResponse;
  import java.io.IOException;
  import java.io.PrintWriter;
  import java.util.ArrayList;
  import java.util.List;
  @WebServlet(name="JsoNServlet",urlPatterns="/JSONServlet")
  public class JSONServlet extends HttpServlet{
      public vold doGet (HttpServletRequest request, HttpservletResponse
                         response) throws ServletException, IOException{
          //创建1ist集合
          List<Book> Books= new ArrayList<Book>();
          Book b =new Book();
          b.setName("Java基础");
          b.setAuthor("黑马程序员");
          b.setPrice(78.20);
          Books.add(b);
          Book bl =new Book();
          bl.setName("Java 进阶");
          bl.setAuthor("itcast");
          bl.setPrice(68.20);
          Books.add(b1);
          //创建JSONArray 对象,并调用fromObject()方法将Books集合转换为JSON格式的数据
          JSONArray jsonArray=JSONArray.fromObject(Books);
          response.setContentType("text/html;charset=utf-8");
          PrintWriter out =response.getWriter();
          out.print(jsonArray);
          out.flush();
          out.close();
      }
      public void doPost(HttpServletRequest request, HttpServletResponse
                         response) throws ServletException, IOException{
          doGet(request,response);
      }
  }
  ~~~

- 实现JSP页面获取JSON格式的数据，在项目web目录下创建一个JSON.jsp文件，用于获取JSON格式的数据

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8"language="java"%>
  <html>
      <head>
          <title>JSON</title>
          <script type="text/javascript" src="${pageContext.request.contextPath}/jquery-3.6.0.js">
          </script>
      </head>
      <body>
          <button id="btn">加载数据</button>
          <table id="dataTable" border="1" cellpadding="0" cellspacing="0">
              <tr>
                  <th>作者</th>
                  <th>书名</th>
                  <th>价格</th>
              </tr>
          </table>
          <script type="text/javascript">
              $('#btn').click(function(){
                  $.getJSON('http://localhost:8080/chapter12/JSONServlet',function(data){
                      var html ='';
                      //通过循环遍历方式获取JSONServlet文件中的数据
                      //并解析获取相应的信息，将获取的信息拼接成html字符串
                      for (var Book in data){
                          html+='<tr>';
                          for (var key in data[Book]){
                              html+= '<td>’+ data[Book][key] + '</td>';
                          }
                          html +='</tr>';
                      }
                      //调用append()方法将拼接的JSP内容插入页面中。
                      $('#dataTable').append(html);             
                  });
              });
          </script>
      </body>
  </html>
  ~~~

  启动Tomcat并在浏览器中输入：http://localhost:8080/Demo/JSON.jsp显示页面后点击`加载数据`按钮，页面效果如下：

  [获取JSON数据结果：](https://s1.ax1x.com/2022/04/21/LcCNqK.jpg)

  ​                                      [<img src="https://s1.ax1x.com/2022/04/21/LcCNqK.jpg" alt="LcCNqK.jpg" style="zoom:25%;" />](https://imgtu.com/i/LcCNqK)

### 3. Ajax的基础操作

> 在JQuery中，向服务器请求数据的方法有很多。其中，基本的方法是`$.ajax()`，它可以精确的控制Ajax请求。例如，在请求出错时执行某些操作，设置请求字符集和超时时间等。
>
> `$.ajax()`方法是JQuery中底层的Ajax方法，前面的`$.get()`和`$.post()`方法就是对`$.ajax()`方法的进一步封装。这两个方法的实际封装代码如下：

~~~JavaScript
jQuery.each(［"get", "post" ], function( i, method) {
    jQuery[ method ] = function( url, data, callback, type){
        if(jQuery.isFunction(data)){
            type = type || callback;
            callback = data;
            data = undefined;
        }
        //从这里可以看出这两个方法都是在底层调用$.ajax()实现相应功能的
        return jQuery.ajax({
            url:url,
            type:method,
            dataType:type,
            data:data,
            success: callback
        });
    }
});
~~~

$.ajax()方法可以实现所有关于Ajax的操作，其语法格式如下：

~~~JavaScript
$.ajax(option)
	$.ajax(url,option)
~~~

> url表示请求的URL，options对象以键值对的形式将Ajax请求需要的设置包含在参数中，`$.ajax()`参数设置如下：

|           参数名           |                             描述                             |
| :------------------------: | :----------------------------------------------------------: |
|            url             |                   请求地址，默认是当前页面                   |
|            data            |                      发送至服务器的数据                      |
|            xhr             |              用于创建 XMLHttpRequest 对象的函数              |
|      beforeSend(xhr)       |                     发送请求前执行的函数                     |
| success(result,status,xhr) |                     请求成功时执行的函数                     |
|  error(xhr,status,error)   |                     请求失败时执行的函数                     |
|    complete(xhr,status)    | 请求完成时执行的函数(请求成功或失败时都会调用，顺序在success和error函数之后) |
|          callback          |                     请求完成时执行的函数                     |
|          dataType          |                  预期的服务器响应的数据类型                  |
|            type            |                     请求方式(GET或POST)                      |
|           cache            |           是否允许浏览器缓存被请求页面，默认为true           |
|          timeout           |              设置本地的请求超时时间（以毫秒计）              |
|           async            |                 是否使用异步请求，默认为true                 |
|          username          |               在HTTP访问认证请求中使用的用户名               |
|          password          |                在HTTP访问认证请求中使用的密码                |
|        contentType         | 发送数据到服务器时所使用的内容类型，默认为“application/x-www-form-urlencoded” |
|        processData         |       是否将请求发送的数据转换为查询字符串，默认为true       |
|          context           |              为所有Ajax相关的回调函数指定this值              |
|    dataFiter(data,type)    |             用于处理 XMLHttpRequest 原始响应数据             |
|           global           |        是否为请求触发全局Ajax事件处理程序，默认为true        |
|         ifModified         | 是否仅在最后一次请求后响应发生改变时才请求成功，默认为false  |
|        traditional         |           是否使用传统方式序列化数据，默认为false            |
|       scriptCharset        |                         请求的字符集                         |

案例：

- 在web目录中创建一个名为ajax.jsp的文件，用于实现Ajax的异步登录。

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>Ajax</title>
          <script type="text/javascript" src="$(pageContext.request.contextPath)/jquery-3.6.0.js"></script>
          <script type="text/javascript">
              //在页面加载完后有限执行ready()方法内的代码
              $(document).ready(function(){
                  $("button").click(function(){
                      $.ajax({
                          type:"post", //提交方式
                          //请求的Servlet地址
                          url:'http://localhost:8080/chapter12/AJAXServlet',
                          data:{
                              userName:$("#userName").val(),
                              password:$("#password").val()
  
                          },//data中的内容会自动添加到ur1 后面
                          dataType:"text", //设置返回数据的格式
                          success:function(a){ //请求成功后执行的函数
                              if(a==true) {
                                  $('#suss').html("登录成功！");
                              }else{
                                  $('#suss').html("登录失败！");
                              }
  
                          },
                          error:function(){ //请求失败后执行的函数
                              alert("请求失败");
                          },
                      });
                  });
              });    
          </script>
      </head>
      <body>
          <div>
              <div>
                  <ul>
                      <1i>用户名：</1i>
                      <li><input id="userName" name="userName" type="text"/></li>
                  </ul>
              </div>
              <div>
                  <ul>
                      <li>密码：</li>
                      <li><input id-"password"name="password" type="password"/></li>
                  </ul>
              </div>
              <div>
                  <ul>
                      <li><button>登录</button></1i>
                  </ul>
          </div>
          <div id="suss"></div>
          </div>
      </body>
  </html>
  ~~~

- 编写Servlet代码。在项目的src目录下创建一个名为AJAXServlet.java的类，用于判断用户输入的账号和密码是否正确

  ~~~java
  import javax.servlet.ServletException;
  import javax.servlet.annotation.WebServlet;
  import javax.servlet.http.HttpServlet;
  import javax.servlet.http.HttpServletRequest;
  import javax.servlet.http.HttpServletResponse;
  import java.io.IOException;
  import java.io.PrintWriter;
  @WebServlet(name="AJAXServlet",urlPatterns="/AJAXServlet") 
  public class AJAXServlet extends HttpServlet{
      public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException，IOException{
          booleanflag = false;
          if((request.getParameter("userName")).equals("itcast")
             &&request.getParameter("password").equals("123")){
              flag = true; //登录成功标志
          }else{
              flag=false;
          }
          response.setContentType("text/html;charset=utf-8");//使用PrintWriter方法打印登录结果
          PrintWriter out = response.getWriter();
          out.print(flag);
          out.flush();
          out.close();
      }
      public void doPost (HttpServletRequest request, HttpServletResponse response)throws ServletException,IOException {
          doGet(request,response);
      }
  }
  ~~~

  启动Tomcat后在浏览器输入：http://localhost:8080/Demo/ajax.jsp出现页面后填写用户名：`itcast`和密码：`123`点击登录按钮后结果如下：

  [ajax运行结果：](https://s1.ax1x.com/2022/04/22/L2fyex.jpg)

  ​                              [<img src="https://s1.ax1x.com/2022/04/22/L2fyex.jpg" alt="L2fyex.jpg" style="zoom:33%;" />](https://imgtu.com/i/L2fyex)

### 4. 实时显示公告信息

> 本案例使用Ajax实现无刷新动态获取实时信息，具体是每隔十分钟从数据库获取依次最新公告，并显示。

- 准备

  > 创建名为char12的数据库，并在数据库中新建表名为info的公告表，在info表中包含了id和title字段。
  >
  > 创建项目在项目中导入项目所需的JQuery和MySql包：`mysql-connector-java-8.0.15.jar`该包为MySql所需的包，`jQuery-3.6.0.js`为JQuery所需要的文件。

- 创建index主页面

  > 在项目的web目录下创建一个名称为index.jsp的文件，在该文件中显示最新公告的相关内容，主要利用Ajax异步提交请求的方式来定时读取数据库中最新的商品信息。实现定时读取的关键是通过Javascript的window对象的`setInterval()`方法来调用Ajax请求服务器的方法，并且设置每隔10分钟调用一次，即可实现最新公告信息的显示。具体如下：

  ~~~jsp
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>index</title>
          <script type="text/javascript" 
                  src="$(pageContext.request.contextPath)/jquery-3.6.0.js"></script>
          <script language="JavaScript">
              function getInfo(){
                  $.get("http://localhost:8080/chapter12/getInfo.jsp?nocache="+newDate().getTime(),function(data){
                      $("#showInfo").html(data); 
                  });
              }
              $ (document).ready(function(){
                  getInfo()；//调用getInfo()方法获取公告信息
                  window.setInterval("getInfo()",600000);
              });
          </script>
      </head>
      <body>
          <section>
              <marquee direction="up" scrollamount="3">
              </marquee>
          </section>
      </body>
  </html>
  ~~~

- 创建getInfo.jsp页面。用于从数据库查询数据

  ~~~jsp
  <%@ page language="java" contentType="text/html;charset=UTF-8" pageEncoding="UTF-8"%>
  <%@ page import="java.sql.*" %>
      <jsp:useBean id="conn" class="cn.itcast.dao.ConnDB" scope="page"></jsp:useBean>
  <ul>
      <%
      ResultSet rs=conn.executeQuery("select title from info order by id desc"); 			
      if(rs.next()){
          do{
              out.print("<li>"+rs.getString(1)+"</1i>");
          }while (rs.next());
      }else{
          out.print("<li>暂无公告信息！</1i>");
      }
      %>
  </ul>
  ~~~

- 编写数据库连接类。在`cn.itcast.dao`包下创建名称为ConnDB.java类，用于与数据进行交互。

  ~~~Java
  package cn.itcast.dao;
  import java.io.InputStream;
  import java.sql.*;
  import java.util.Properties;
  public class ConnDB{
      public Connection conn =null; 	//声明 Connection 对象的实例
      public Statement stmt = null; 	//声明 Statement 对象的实例
      public ResultSet rs = null; 	//声明 ResultSet 对象的实例
      //指定资源文件保存的位置
      private static String propFileName="cn/itcast/dao/connDB.properties";
      //创建并实例化Properties对象
      private static Properties prop=new Properties();
      //定义并保存数据库驱动的变量
      private static String dbClassName="com.mysql.cj.jdbc.Driver"; 
      private static String dbUrl="bc:mysql://127.0.0.1:3306/char12?user=rootspassword=root?useUnicode=true&characterEncoding=utf-8&useSSL=false";
      //构造方法
      public ConnDB(){
          try{
              //将Properties 文件读取到InputStream对象中
              InputStream in=getClass().getResourceAsStream(propFileName);
              prop.load(in);
              dbClassName =prop.getProperty("DB_CLASS_NAME"); //获取数据库驱动
              dbUrl = prop.getProperty("DB_URL",dbUrl); //获取 URL 
          }catch(Exception e){
              e.printStackTrace(); //输出异常信息
          }
      }
      
      //连接数据库
      public static Connection getConection(){
          Connection conn=null;
          try{ 
              Class.forName(dbClassName),newInstance();//装载数据库驱动
              //建立与数据库 URL 中定义的数据库的连接
              conn = DriverManager.getConnection(dbUrl);
          }catch(Exception ee){
              ee.printStackTrace();    
          }
          if(conn==null) {
              System.err.print("连接失败");
          }
          return conn;
      }
      
      
      //执行查询
      public ResultSet executeQuery(String sql){
          try{ 
              conn=getConection();
              stmt =conn.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE,ResultSet,CONCUR_READ_ONLY);
              //执行SQL语句，并返回一个ResultSet对象rs
              rs =stmt.executeQuery(sql);
  
          }catch(SQLException ex){
              System.err.print(ex.getErrorCode());
          }
          return rs;
      }
      
      
      //更新语句
      public int executeUpdate(String sql){
          int result =0;
          try{
              conn=getConection();
              stmt =conn.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE,ResultSet.CONCUR_UPDATABLE); 
              //执行更新操作
              result=stmt.executeUpdate(sql); 
  
          }catch(SQLException ex){
              result=0;
          }
          return result;
      }
      
      
      //关闭数据库连接
      public void close(){
          try{
              if(rs!=null){
                  rs.close();
              }
              if(stmt!=null){
                  stmt.close();
              }
              if(coon!=null){
                  conn.close();
              }
          }catch(Except e){
              e.printStackTrace();
          }
      }
  }
  ~~~

- 使用properties包作为数据库连接数据，需要在`in.itcast.dao`包下创建名称为coonDB.properties文件。

  ~~~properties
  DB_CLASS_NAME=com.mysql.cj.jdbc.Driver
  DB_URL =jdbc:mysql://127.0.0.1:3306/char12?useUnicode=true&characterEncoding=utf-8&useSSL=fa1se
  user =root
  pass =root
  ~~~

至此，使用Ajax实时显示公告信息的代码已全部完成。启动Tomcat，浏览器中访问：http://localhost:8080/Demo/index.jsp结果如下：

[index运行结果：](https://s1.ax1x.com/2022/04/22/L2LmGt.jpg)

​									[<img src="https://s1.ax1x.com/2022/04/22/L2LmGt.jpg" alt="L2LmGt.jpg" style="zoom: 33%;" />](https://imgtu.com/i/L2LmGt)



​                         

​                                   
