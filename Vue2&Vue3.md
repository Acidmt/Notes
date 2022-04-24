# Vue2&Vue3

[toc]

## 一. Vue概述

> Vue是一套用于构建用户界面的渐进式JavaScript框架
>
> 渐进式：Vue可以自底向上逐层的应用。当开发简单的应用时，只需一个轻量小巧的核心库。当开发复杂应用时，可以引入各式各样的Vue插件。

### 1. Vue的特点：

> 1. 采用组件化模式，提高代码复用率、且让代码更好维护。(网站的每一个模块都封装在Vue文件中)
> 2. 声明式编码，让编码人员无需直接操作DOM，提高开发效率。(如将JSON中的数据转换为页面数据)
> 3. 使用虚拟DOM+优秀的Diff算法，尽量复用DOM节点。(新添加的数据直接进入DOM网页中，而不用重新遍历所有数据)

### 2. Vue的安装：

- 首先进入官网然后左上角学习下拉按钮中选择教程。在教程左侧选择安装。

  [Vue的安装：](https://s1.ax1x.com/2022/04/21/LcRLuV.png)

  ​                 [<img src="https://s1.ax1x.com/2022/04/21/LcRLuV.png" alt="LcRLuV.png" style="zoom: 33%;" />](https://imgtu.com/i/LcRLuV)

- 之后下载开发者版本，下载完成后将文件移动到项目目录中，如果是Java网页开发，则在web目录下新建一个文件夹(js)，然后放入

  [下载好后的Vue.js：](https://s1.ax1x.com/2022/04/21/LcWhKx.png)

  ​                     [<img src="https://s1.ax1x.com/2022/04/21/LcWhKx.png" alt="LcWhKx.png" style="zoom:33%;" />](https://imgtu.com/i/LcWhKx)

### 3. 关闭浏览器调试提示：

> 在开发时，浏览器的调试窗口会一直有警告，这里可以通过下载`Vue tools`工具，和配置警告提示文件解决

~~~JavaScript
//关闭警告提示
Vue.config.productionTip = false 
~~~

### 4. Vue的引入：

~~~JavaScript
<script type= "text/ javascript" src="../js/vue.js"></ script>
//具体路径根据实际情况编写
~~~

## 二. 初始Vue

### 1. Vscode插件引起的错误

> 我们需要注意一个错误，先随便在一个项目中写一段HTML代码，然后运行打开浏览器，这个错误会在浏览器的控制台里显示：

[控制台下的错误：](https://s1.ax1x.com/2022/04/21/Lc4Cgs.png)                         

​								[<img src="https://s1.ax1x.com/2022/04/21/Lc4Cgs.png" alt="Lc4Cgs.png" style="zoom:50%;" />](https://imgtu.com/i/Lc4Cgs)

> 这个错误是因为没有网页图标引起的，但是如果你没有安装Vscode里的`Live Servler`插件，建议安装。这个插件可以模拟Tomcat，将当前的web路径当作根路径在浏览器中显示。
>
> 所以这里解决这个错误很简单，只需要在web项目的根目录下放一张名为favicon.ico的图片即可

[根路径显示为网页：](https://s1.ax1x.com/2022/04/21/LcIAtU.png)

​                               [<img src="https://s1.ax1x.com/2022/04/21/LcIAtU.png" alt="LcIAtU.png" style="zoom:50%;" />](https://imgtu.com/i/LcIAtU)

### 2. 第一个Vue实例

> 我们在使用Vue的时候先要进行实例化。实例化后才能进行接下来的工作。Vue.js 的核心是一个允许采用简洁的模板语法来声明式地将数据渲染进 DOM 的系统，并且参数都是以键值对形式出现：

~~~html
<div id="app">
  {{ message }}
</div>
~~~

~~~JavaScript
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
~~~

输出结果：`Hello Vue!`

简单介绍Vue实例中的参数：

|    参数名    |                             描述                             |
| :----------: | :----------------------------------------------------------: |
| el:selector  | el(Element)用于指定当前Vue实例为哪个容器服务，值通常为css选择器字符串。 |
| data{Object} | data中用于存储数据，数据供el所指定的容器去使用。是以键值对形式存储 |
|   {{name}}   | 插值语句，将data对象中所指定的name插入到el指定容器中，里面形式为表达式 |

### 3. 常见的Vue实例参数

> 注意一个Vue实例不能同时接管多个容器，且一个容器也只能被一个实例接管。所以容器和实例之间的关系是一对一型的。

|          参数名          |                             描述                             |
| :----------------------: | :----------------------------------------------------------: |
|       el:"options"       |  提供一个在页面上已存在的 DOM 元素作为 Vue 实例的挂载目标。  |
| template:"`<tag></tag>`" | 一个字符串模板作为 Vue 实例的标识使用。模板将会 替换 挂载的元素。挂载元素的内容都将被忽略，除非模板的内容有分发 slot |
|  render: (h)=>{h(App)},  | 字符串模板的代替方案，允许你发挥 JavaScript 最大的编程能力。 |
|           data           | Vue实例的数据对象。Vue 将会递归将 data 的属性转换为 getter/setter，从而让 data 的属性能够响应数据变化 |
|         methods          | methods将被混入到 Vue 实例中，可以直接通过 VM 实例访问这些方法，或者在指令表达式中使用,方法中的 this自动绑定为 Vue 实例 |
|          watch           |    整个为一个对象，键是需要观察的表达式，值是对应回调函数    |
|         computed         | vue的计算属性，将被混入到 Vue 实例中。所有 getter 和 setter 的 this 上下文自动地绑定为 Vue 实例 |
|          props           | 用于父子组件的eventbus传值，是数组或对象，props的成员是子组件接收的来自父组件的数据 |
|        propsData         |           创建实例时传递 props。主要作用是方便测试           |
|         filters          |              包含 Vue 实例可用过滤器的哈希表。               |
|        directives        |               包含 Vue 实例可用指令的哈希表。                |
|        components        |  （即该组件的子实例）这里是包含 Vue 实例可用组件的哈希表。   |

### 4. 总结

1. 想让Vue工作，就必须创建一个Vue实例， 且要传入一个配置对象；

2. root容器里的代码依然符合html规范，只不过混入了一些特殊的Vue语法；

3. root容器里的代码被称为[Vue模板] ；

   [Vue模板：](https://s1.ax1x.com/2022/04/21/LcHvsH.png)

   ​                    				 [<img src="https://s1.ax1x.com/2022/04/21/LcHvsH.png" alt="LcHvsH.png" style="zoom: 50%;" />](https://imgtu.com/i/LcHvsH)

4. 注意区分： js表达式和js代码(语句)

   > 1. 表达式：一个表达式会产生一个值， 可以放在任何一个需要值的地方，即可以被变量接收的语句：
   >    - a
   >    - a+b
   >    - demo(1)
   >    - x===y?    'a':'b'
   > 2. js代码(语句)：
   >    - if(){}
   >    - for(){}

5. Vue实例和容器是一一对应的；

6. 真实开发中只有一个Vue实例，并且会配合着组件一起使用；

## 三. Vue模板语法

> 容器内(HTML标签)内的代码被称为
>
> Vue模板语法包含两类：
>
> 1. 插值语法：如上面展示的代码，这种语法用`{{}}`包裹
> 2. 指令语法：(以V-开头)

### 1. 插值语法：

> 功能:用于解析标签体内容。
> 写法: {{xxx}}, xxx是js 表达式，且可以直接读取到data中的所有属性。

~~~html
<body>
    <div id="app">{{ message }}</div>   
</body>
<script>
    var app = new Vue({
        el: '#app',
        data: {
            message: 'Hello Vue!'
        }
    })
</script>
~~~

输出结果：`Hello Vue!`

### 2. 指令语法

> Vue里的指令都是以`V-`开头，如：**`v-bind`指令会将标签属性值作为JavaScript表达式执行**，就会被转译成JavaScript表达式执行。
>
> 功能：用于解析标签(包括:标签属性、标签体内容、绑定事件.....)。
> 举例:：v-bind:href="xxx" 或简写为 :href="xxx", xxx同样可以写js表达式，且可以直接读取到data中的所有属性。
> 备注: Vue中有很多的指令，且形式都是: v-????,此处我们只是拿v-bind举个例子：

~~~html
<body>
    <a v-bind:href="url">点我去百度</a>
</body>
<script>
    new Vue({
        el: '#root',
        data:{
            name:'jack' ,
            url:'http://www.baidu.com'
        }
    })
</script>
~~~

> 上面代码中的`V-bind`指令可以将`href="url"`中的`url`转换为JavaScript表达式执行，即`a`标签中的`url`会获取JavaScript中Vue实例中名字叫url的属性值，赋值给`a`标签的href属性。
>
> 所以在浏览器的元素中查看上面的HTML标签会显示：`<a v-bind:href="http://www.baidu.com">点我去百度</a>`
>
> 注意：上面的Vue指令`V-bind`可以简写为`:`，所以上面案例可以改为：

~~~html
<body>
    <a :href="url">点我去百度</a>
</body>
~~~

- Vue常见指令：

  |    指令名     |                             描述                             |  简写   |
  | :-----------: | :----------------------------------------------------------: | :-----: |
  | v-model:value |                      实现标签的双向绑定                      | v-model |
  |    v-show     |                           显示内容                           |         |
  |    v-hide     |          隐藏内容(给display：none的属性 让它不显示)          |         |
  |     v-if      | 后面的是一个表达式或者也可以是返回true或false的表达式用于**显示与隐藏** （如果值为false，该处内容会被注释掉，已达到不显示效果） |         |
  |   v-else-if   | 必须和 v-if 连用 v-else 必须和 v-if 连用 不能单独使用 否则报错 模板编译错误 |         |
  |     v-for     |           基于数据渲染一个列表，类似于JS中的遍历。           |         |
  |    v-bind     |                           属性绑定                           |    :    |
  |     v-on:     |      给标签绑定函数常用的事件有：click、keyup、keydown       |    @    |
  |    v-text     |                           解析文本                           |         |

### 3. 插值语法与指令语法具体使用情况

> 插值语法往往用于标签体内容，而指令语法往往用于标签属性。

### 4. 双向绑定指令

> 之前我们学习的`v-bind`指令只能实现单向绑定，即网页数据变化，并不会影响Vue实例中变量的变化。如下：

[V-bind单向绑定：](https://s1.ax1x.com/2022/04/23/LWyvdS.png)

​								[<img src="https://s1.ax1x.com/2022/04/23/LWyvdS.png" alt="LWyvdS.png" style="zoom:33%;" />](https://imgtu.com/i/LWyvdS)

> 由上图可知，我们输入框中的内容是`1234`而Vue实例中的name值为`123`，由此可知，Vue实例与页面是单向绑定的，页面的改变影响不了VUe实例的值。但在项目开发中很多时候我们需要进行**双向绑定**。即任何一方发生改变，双方都改变。此时就需要用到
>
> `v-model:`指令，该指令可以解决上述问题：页面和实例数据如果改变，都改变。也可简写为`v-model='value'`下面进行示例：

~~~html
<body>
    <div id="root"> 
        双向数据绑定: <input type="text" v-model:value="name">		<!--这里可以实现相同的效果-->
        双向数据绑定: <input type="text" v-model="name">
    </div>
</body>
<script type="text/javascript">
    Vue. config. productionTip = false //阻止vue在启动时生成生产提示。
    new Vue({
        el: '#root'
        data:{
        name: '123'
    })
</script>
~~~

页面输出时我们在输入框内部输入信息，可以看到Vue示例也跟着变化：

[v-model运行结果：](https://s1.ax1x.com/2022/04/23/LW6gYQ.png)

​									[<img src="https://s1.ax1x.com/2022/04/23/LW6gYQ.png" alt="LW6gYQ.png" style="zoom:33%;" />](https://imgtu.com/i/LW6gYQ)

注意：`v-model:`指令只能用在表单类元素(输入类元素)上

### 5. el和data的两种写法

> 这里Vue示例里的`el`和`data`参数可以有两种写法，上面的示例展示的是第一种写法，我们还有较为简便灵活的写法

- el的第二种写法

  > 格式：变量.$mount('选择器')
  >
  > 通过这种写法也可以实现Vue实例与容器绑定，更多的用在代码执行部分后实现容器内容改变。

  ~~~javascript
  Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
  //e1的两种写法
  const v = new Vue({
      data:{
          name:'hello'
      }
  })
  v.$mount('#root') //第二种写法
  ~~~

- data的第二种写法(函数式写法)

  > 格式：data：function(){return{key:value}}
  >
  > 多应用于组件部分

  ~~~JavaScript
  Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
  //e1的两种写法
  const v = new Vue({
      el:'#root',
      data:function(){
          return{
              key:value
          }
      }
  })
  ~~~

- 总结

  > 1. e1有2种写法：
  >    - new Vue时候配置e1属性。
  >    - 先创建Vue实例，随后再通过vm.$mount('#root')指定e1的值。
  > 2. data有2种写法
  >    - 对象式
  >    - 函数式：如何选择:目前哪种写法都可以，以后学习到组件时，data必须使用函数式，否则会报错。
  > 3. 一个重要的原则：由Vue管理的函数，一定不要写箭头函数，一旦写了箭头函数，this就不再是Vue实例，而是Windows实例。

## 四. MVVM模型与数据代理

> MVVm模型是Vue实例的原理，数据代理通过一个对象代理对另一个对象中属性的操作（读/写）

### 1.  MVVM模型概述

> 1. M:模型(Model) :对应data中的数据
>
> 2. V:视图(View) :HTML中的模板语句
> 3. VM:视图模型(ViewModel) : Vue 实例对象

[MVVM模型：](https://s1.ax1x.com/2022/04/23/Lf3IM9.png)

​											[<img src="https://s1.ax1x.com/2022/04/23/Lf3IM9.png" alt="Lf3IM9.png" style="zoom: 50%;" />](https://imgtu.com/i/Lf3IM9)

~~~html
<body> 
    <!--准备好一个容器-->
    <div id="root"> 
        <h1>学校名称: {{name}}</h1>
        <h1>学校地址: {{address}}</h1>
    </div> 
</body>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    const vm = new Vue({
        el:'#root',
        data:{
            name: 'shi',
            address: '北京'
        })
</script>
~~~

[MVVM模型介绍：](https://s1.ax1x.com/2022/04/23/LfJfG8.png)

​										[<img src="https://s1.ax1x.com/2022/04/23/LfJfG8.png" alt="LfJfG8.png" style="zoom: 50%;" />](https://imgtu.com/i/LfJfG8)

- 总结：

  > MVVM模型
  > 1. M:模型(Model) : data中的数据
  > 2. V:视图(View) :模板代码
  > 2. VM: 视图模型(ViewModel): Vue实例
  >
  > 观察发现:
  >
  > 1. data中所有的属性，最后都出现在了vm身上。
  > 2. vm身上所有的属性及Vue原型上所有属性，在Vue模板中都可以直接使用。

### 2. 数据代理

> vue 数据代理： 通过vm对象来代理data中所有属性的操作，更方便精确操作data中的数据
>
> 其本质是通过一个对象代理另一个对象中的属性的操作（读 / 写 ）

#### 2.1 Object.defineProperty()方法

> 该方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回此对象，但要注意新添加的属性不能参与遍历。
>
> 语法如下：

~~~JavaScript
Object.defineProperty(obj, prop, descriptor)
~~~

|   参数名   |               描述                |
| :--------: | :-------------------------------: |
|    obj     |        要定义属性的对象。         |
|    prop    | 要定义或修改的属性的名称或 Symbol |
| descriptor |    要定义或修改的属性描述符。     |

有两种属性描述符：数据属性描述符、存取属性描述符

|   描述符名   |                             说明                             |                           默认情况                           |
| :----------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| configurable | 示属性是否可以通过delete删除，是否可以修改特性，是否可以将它修改为存取属性 | 当我们直接在一个对象上定义某个属性时，它的默认值是true，而当我们通过属性描述符进行定义属性时，它的默认值是false |
|  enumerable  |    表示属性是否可以通过for-in遍历或者Object.keys返回属性     | 当我们直接在一个对象上定义某个属性时，他的默认值是true，而当我们通过属性描述符进行定义属性时，他的默认值是false |
|   writable   |                     表示是否可以修改属性                     | 当我们直接在一个对象上定义某个属性时，他的默认值是true，而当我们通过属性描述符进行定义属性时，他的默认值是false |
|    value     | 属性的value值，当读取属性时会返回value，修改属性时会修改value |                  默认情况下value是undefined                  |
|     get      |                     获取属性时执行的函数                     |                       默认为undefined                        |
|     set      |                设置或者修改属性值时执行的函数                |                       默认为undefined                        |

**注意：writable、value不能和get、set一起使用**

~~~javascript
let Person = {name: '张',sex:'男'}
Object.defineProperty(Person, 'age', {
    value: '18',
    writable: true,		// 变量是否可以改变
    enumerable:truem,	//控制属性是否可以枚举，默认值是false
    configurable:true,	//控制属性是否可以被删除，默认值是false   
    get(){				//当有人读取person的age属性时，get函数(getter)就会被调用，且返回值就是age的值
        console.log('有人读取age属性了')
        return number 
    },    
    set(value){			//当有人修改person的age属性时，set函数(setter)就会被调用，且会收到修改的具体值
        console.log('有人修改了age属性，且值是',value)
        number=value
    }
})
Person.name='rose' 
console.log (Person.name)
//结果：rose
~~~

#### 2.2 数据代理演示

~~~javascript
let obj = {x:100}
let obj2 = {y:200}
0bject.defineProperty(obj2,'x',{
    get(){
        return obj.X
    },
    set(value){
        obj.x = value
    }
})
~~~

> 上面的代码是一个经典的数据代理案例。其中`get`方法在obj2中追加一个属性`x`，并且值为obj里的x值。所以当有人访问obj2时，其实就相当于访问obj中的`x`值。
>
> `set`方法是当有人想修改obj2中`x`的值，就等于修改obj中的`x`值。由于obj2中`x`的值是obj中的`x`值，所以这里的set方法就是修改obj中的`x`值。已达到修改obj2中`x`的值 

[数据代理图示：](https://s1.ax1x.com/2022/04/24/L4LNut.png)								[<img src="https://s1.ax1x.com/2022/04/24/L4LNut.png" alt="L4LNut.png" style="zoom: 50%;" />](https://imgtu.com/i/L4LNut)

- 总结：

  > 1. Vue中的数据代理:：
  > 通过vm对象来代理data对象中属性的操作(读/写)
  > 1. Vue中数据代理的好处：
  > 更加方便的操作data中的数据
  > 1. 基本原理：
  > 通过Object.defineProperty( )把data对象中所有属性添加到vm上。
  > 为每一个添加到vm上的属性，都指定一个getter/setter方法。
  > 在getter/setter内部去操作(读/写) data中对应的属性。

## 五. 事件处理

> Vue简写了事件处理方式，要注意的是事件处理只能在Vue实例中定义。

### 1. 点击事件

> 可以用`v-on:click`(也可简写为：`@click='functionName'`)在容器中实现点击事件的绑定。同时，在vue实例中需要将事件函数写入`methods`参数中。参数methods介绍如下：

|  参数名   |                             描述                             |
| :-------: | :----------------------------------------------------------: |
| methods： | 里面放如事件函数，其中可以有多个事件函数，但方法名不能一样。函数可以接收参数 |

`v-on:click`指令介绍：

|           指令名            |                             描述                             |
| :-------------------------: | :----------------------------------------------------------: |
| v-on:click课简写为：@click= | 值为一个与methods中相对应的事件函数名。可以加入参数，但注意加入参数时用`$event`参数占位，用来接收事件参数event。 |

~~~html
<body>
    <!--准备好一个容器--> 
    <div id="root"> 
        <h2>欢迎来到{{name}}学习</h2>
        <!-- <button v-on : click="showInfo">点我提示信息</button> -->
        <button @click= "showTnfo1" >点我提示信息1</button>
        <button @click=" showInfo2(666,$evnet)">点我提示信息2</button>
    </div>
</body>
<script type="text/javascript">
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    const Vm = new Vue({
        el:'#root',
        data:{
            name: 'shi'
        },
        methods:{
            showTnfo1(event){
                // console . log(event . target。innerText)
                // console. log(this) // 此处的this是vm
                alert('同学你好')
            },
            showTnfo2(event,number){
                console.log(event,number)
                // console.log(this) // 此处的this是vm
            }
        }
    })
</script>
~~~

[点击提示信息2结果：](https://s1.ax1x.com/2022/04/24/L59jaR.png)									[<img src="https://s1.ax1x.com/2022/04/24/L59jaR.png" alt="L59jaR.png" style="zoom: 50%;" />](https://imgtu.com/i/L59jaR)

- 总结：

  > 1. 使用v-on:XXx或@xxx绑定事件，其中xxx是 事件名；
  > 2. 事件的回调需要配置在methods对象中，最终会在vm上；
  >
  > 3. methods中配置的函数，不要用箭头函数!否则this就不是vm了；
  > 4. methods中配置的函数，都是被Vue所管理的函数，this的指向是vm或组件实例对象；
  > 5. @click="demo"和@click="demo($event)"效果一致， 但后者可以传参；

### 2. 事件修饰符

> 为了更纯粹的数据逻辑，vue提供了很多事件修饰符，来代替处理一些 DOM 事件细节。常用的Vue事件修饰符如下：

| 修饰符名 |                       描述                        |
| :------: | :-----------------------------------------------: |
| prevent  |               阻止默认事件(常用) ;                |
|   stop   |                阻止事件冒泡(常用)                 |
|  once:   |              事件只触发一次(常用) ;               |
| capture: |                使用事件的捕获模式;                |
|  self:   |   只有event.target是当前操作的元素时才触发事件;   |
| passive: | 事件的默认行为立即执行，无需等待事件回调执行完毕; |

- stop

  > 防止事件冒泡，通俗来说就是阻止事件向父元素传递，阻止任何父事件处理程序被执行，等同于JavaScript中的event.stopPropagation()。

  ~~~html
  <div id="app">
      <div @click="outer">
          <div  @click="middle">
              <button @click="inner">点击</button>
          </div>
      </div>
  </div>
  <script>
      const Vm = new Vue({
          methods:{
              inner: function () {
                  console.log ('inner')
              },
              middle: function () {
                  console.log ('middle')
              },
              outer: function () {
                  console.log ('outer')
              }
          }
      })
  </script>
  ~~~

  运行结果：

  ```html
  inner  
  middle  
  outer
  ```

  > 从上面的结果我们可以观察到，在button标签外包了两层div，每层都绑定了监听器，监听click事件，这时候我们点击最内层的按钮，外面两层对应的点击事件也会被触发。
  >
  > 解决办法：内层按钮的事件绑定加上stop修饰符，就不会向上冒泡了

  ~~~HTML
  <button @click.stop="inner">点击</button>
  ~~~

- prevent

  > preventDefault缩写某些标签拥有自身的默认事件，比如`<a>`标签点击后会进行页面的跳转。这类默认事件虽然是冒泡后开始的，但不会因为stop而停止执行。阻止执行这类预设的行为，prevent就派上用场了。

  ~~~html
  <a href="http://www.baidu.com" @click.prevent>点击跳转</a>
  ~~~

- capture

  > 捕获冒泡，即冒泡发生时，有.capture修饰符的dom元素会优先执行。

  ~~~html
  <div @click="outer">
      <div @click.capture="middle">
          <button @click="inner">点击</button>
      </div>
  </div>
  <script>
      const Vm = new Vue({
          methods:{
              inner: function () {
                  console.log ('inner')
              },
              middle: function () {
                  console.log ('middle')
              },
              outer: function () {
                  console.log ('outer')
              }
          }
      })
  </script>
  ~~~

  运行结果：

  ~~~JavaScript
  middle
  inner   
  outer
  ~~~

  > 这时候打印顺序发生改变了，中间层的信息被优先打印出来，然后再按正常顺序执行触发的事件。我们将外层的点击事件加上.capture修饰符，结果：

  ```html
  <div @click.capture="outer">
      <div @click.capture="middle">
          <button @click="inner">点击</button>
      </div>
  </div>
  <!--运行结果：
  outer
  middle
  inner  
  -->
  ```

  > 我们可以观察到：带修饰符的从外到内依次执行，然后再按正常顺序执行触发的事件。

- self

  > 将事件绑定到自身，只有自身才能触发，通常用于避免冒泡事件的影响。

  ~~~html
  <div id="demo">
      <div @click="outer">
          <div  @click.self="middle">
              <button @click="inner">点击</button>
          </div>
      </div>
  </div>
  <!--运行结果：
  inner
  outer
  -->
  ~~~

  > 给中间的div加上self修饰符，然后点击里层的按钮，发现中间层的事件没有被触发，直接跳过了。
  >
  > 而直接点中间层div对应的区域，才能触发其事件：

  ~~~html
  middle
  outer
  ~~~

- once

  > 这个比较好理解，加上once修饰符以后事件只触发一次，但是不影响事件的冒泡，上层的事件仍然会被触发，并且页面刷新后这个次数会重置。

  ```html
  <div @click="outer">
      <div @click="middle">
          <button @click.once="inner">点击</button>
      </div>
  </div>
  ```

  连续点击按钮三次结果：

  ~~~JavaScript
  inner
  middle
  outer
  
  middle
  outer
  
  middle
  outer
  ~~~

- passive

  > passive是2.3.0 新增的修饰符，是用来告诉浏览器你不想阻止事件的默认行为。
  >
  > 使用.passive就可以提前告诉浏览器，我们没有用preventDefault阻止默认动作，你也不用反复去判断了，从而提高性能解决卡顿。如：如果滑轮滚动绑定的有事件，则会等待绑定事件完成后进行默认滚动，而加了该事件修饰符后，会限制性滚动，在进行滚动事件。

### 3. 键盘事件

> Vue中常用的按键别名：

| 案件名称 |               别名                |
| :------: | :-------------------------------: |
|   回车   |               enter               |
|   删除   |   delete (捕获“删除”和“退格”键)   |
|   退出   |                esc                |
|   空格   |               space               |
|   换行   | tab (特殊，必须配合keydown去使用) |
|    上    |                up                 |
|    下    |               down                |
|    左    |               left                |
|    右    |               right               |

> 1. Vue未提供的别名按键，可以使用按键原始的key值去绑定，但注意要转为kebab-case(短横线命名)
> 2. 系统修饰键(用法特殊) : ctrl、 alt、 shift、 meta(Windows徽标键)
>    - 配合keyup使用:按下修饰键的同时，再按下其他键，随后释放其他键，事件才被触发。
>    - 配合keydown使用:正 常触发事件。
> 3. 也可以使用keyCode去指定具体的按键(不推荐)
> 4. Vue.config.keyCodes 自定义键名 = 键码，可以去定制按键别名(也不建议使用)
> 5. 语法格式如下：

~~~JavaScript
//以下代码表明当按下要触发事件的按键后，会触发后面绑定的函数
@keyup.按键名="要触发的函数"
//定义别名语法：
Vue.config.keyCodes.huiche = 13 //定义了一个 别名按键
~~~

示例：

~~~html
<div id="root">
    <input type= "text" placeholder="按下回车提示输入" @keyup.enter="showInfo">
</div>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    new Vue({
        methods: {
            showInfo(e){
                console.log(e.target.value) 
            }
        }
    })
</script>
~~~

> 以上代码是当用户在浏览器输入框内输入文字后，按下回车键，触发事件函数，会将输入框内的文字输出在控制台。
>
> 也可以定义一个组合按键，如定义ctrl+i为：

~~~html
<input type= "text" placeholder="按下回车提示输入" @keyup.ctrl.i="showInfo">
~~~

- 总结：

  > 事件的基本使用:
  >
  > 1. 使用v-on:Xx或xxx绑定事件，其中xxx是事件名;
  > 2. 事件的回调需要配置在methods对象中，最终会在vm上;
  >
  > 3. methods中配置的函数，不要用箭头函数!否则this就不是vm了;
  > 4. methods中配置的函数，都是被Vue所管理的函数，this的指向是vm或组件实例对象;
  > 5. @click="demo"和@click="demo($event)" 效果一致， 但后者可以传参;

### 4. 计算属性

> 模板内的表达式非常便利，但是设计它们的初衷是用于**简单运算的**。在模板中放入太多的逻辑会让模板过重且难以维护。
>
> **计算属性的用法**：在一个计算属性里可以完成各种复杂的逻辑，包括运算、函数调用等，只要最终返回一个结果就可以。 













