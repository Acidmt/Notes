# Vue2&Vue3

> 可以在vscode中安装三个插件，以便更好的书写代码，提高效率：`Vue 3 Snippets`(hollowtree)

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

### 3. ==常见的Vue实例参数==

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
|         filters          |             包含 Vue 实例可用过滤器来包装数据。              |
|        directives        |             包含 Vue 实例可用的创建自定义指令。              |
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

### 2. ==常见的指令语法==

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
  |    v-text     |                    向所在的标签中插入文本                    |         |

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
| methods： | 里面放如事件函数或者方法，其中可以有多个事件函数，但方法名不能一样。函数可以接收参数 |

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

## 六. 计算属性

> 模板内的表达式非常便利，但是设计它们的初衷是用于**简单运算的**。在模板中放入太多的逻辑会让模板过重且难以维护。
>
> **计算属性的用法**：在一个计算属性里可以完成各种复杂的逻辑，包括运算、函数调用等，只要最终返回一个结果就可以。简单说就是将定义好的属性经过计算加工等生成一个全新的属性。 这里我们需要用到Vue实例参数中的`computed`该属性描述如下：

|  参数名  |                             描述                             |
| :------: | :----------------------------------------------------------: |
| computed | 计算属性允许我们对指定的视图，复杂的值计算。这些值将绑定到依赖项值，只在需要时更新。其中的属性值读取必须要用到`this`关键字 |

#### 4.1 computed内置对象的get()方法：

~~~html
<div id=" root"> 
    姓: <input type="text" v-model="firstName"> <br/><br/>
    名: <input type="text" v -model="lastName"> <br/><br/>
    全名: <span>{{fullName}}</span>
</div>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    const Vm = new Vue({
        el: '#root',
        data:{
            firstName:'张',
            lastName:'三'
        },
        computed:{
            fullName:{
                //get有什么作用?当有人读取ful1Name时，get就会被调用，且返回值就作为fullName的值
                get(){
                    console.log( 'get被调用了')
                    // console. log(this) //此处的this是vm
                    return this.firstName +'-'+ this.lastName
                }
            }
        }
    })
</script>
~~~

执行结果：`张-三`，不管输入什么输出结果都是：`xxx-xxx`的格式。

> 这里的`computed`参数内定义了一个fullName对象，但是和普通的对象调用不同的是，此处直接使用对象名就可以调用`get()`方法。因为Vue示例获取了`get()`方法的返回值，然后绑定到了对象fullName上。所以插值语句直接写`fullName`而不是`fullName.get()`

**注意：get什么时候被调用：1.初次读取fullName时。2.所依赖的数据发生变化时。**

#### 4.2 computed内置对象的set()方法

> 以上的对象中get()方法只能读取值，而当我们需要修改fullName值时，我们就需要用到`set()`方法。
>
> set只有当对象被修改时候才会调用，有一个参数，为接收到的值。

~~~html
<div id=" root"> 
    姓: <input type="text" v-model="firstName"> <br/><br/>
    名: <input type="text" v -model="lastName"> <br/><br/>
    全名: <span>{{fullName}}</span>
</div>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    const Vm = new Vue({
        el: '#root',
        data:{
            firstName:'张',
            lastName:'三'
        },
        computed:{
            fullName:{
                //get有什么作用?当有人读取ful1Name时，get就会被调用，且返回值就作为fullName的值
                get(){
                    console.log( 'get被调用了')
                    // console. log(this) //此处的this是vm
                    return this.firstName +'-'+ this.lastName
                },
                set(value){
                    //切割修改的值
                    arr = value.split('-')
                    this.firstName = arr[0]
                    this.lastName = arr[1]
                }
            }
        }
    })
</script>
~~~

此时运行当我们通过控制台输入：`fullName='李-四'`时候，页面就会进行修改，fullName返回值为`李-四`。

#### 4.3 计算属性的简写

> 大部分时候计算属性是为了将数据加工后展示在页面上，不进行修改的。此时如果你确定你的计算属性是为了在页面上展示数据。那么就可以用到计算机属性的简写。上面的代码可以简写为一下：

~~~html
<div id=" root"> 
    姓: <input type="text" v-model="firstName"> <br/><br/>
    名: <input type="text" v -model="lastName"> <br/><br/>
    全名: <span>{{fullName}}</span>
</div>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    const Vm = new Vue({
        el: '#root',
        data:{
            firstName:'张',
            lastName:'三'
        },
        computed:{
            fu1lName:function( ){
                console.log('get被调用了')
                return this.firstName+'-'+this. lastName
            }
        }
    })
</script>
~~~

#### 4.4 总结

1. 定义:要用的属性不存在，要通过已有属性计算得来。
2. 原理:底层借助了objcet。defineproperty方法提供的getter和setter. 、
3. 优势:与methods 实现相比，内部有缓存机制(复用)，效率更高，调试方便。
4. get函数什么时候执行?
   - 初次读取时会执行一次。
   - 当依赖的数据发生改变时会被再次调用。

5. 备注:
   - 计算属性最终会出现在vm上，直接读取使用即可。
   - 如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起计算时依赖的数据发生改变。

## 七. 监视属性

> 写在Vue对象的`watch`参数中，它的值是配置对象——即属性名。当被监听的属性改变时，回调函数自动调用，进行相关操作。
>
> 监视的属性必须存在，才能进行监视。

watch监视属性详情：

|    参数详情    |                             描述                             |
| :------------: | :----------------------------------------------------------: |
| watch(monitor) | 整个为一个对象，键(方法名)是需要观察的表达式，值(对应监听函数)是对应回调函数 |

### 1. watch内置对象handler()方法

> 和计算属性的computed参数一样，该参数内部方法名为要监听的参数或者方法名。但每个方法中要定义`handler()`方法。该方法有两个参数：`newValue`(修改后的属性值)和`oldvalue`(原先的属性值)。它们分别接受新值和旧值。

~~~html
<body>
    <!-- 准备好一个容器-->
    <div id="root">
        <h2>今天天气很{{info}}</h2>
        <button @click=" changeWeather">切换天气</button>
    </div>
</body>
<script type="text/javascript" >
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    const Vm = new Vue({
        el:'#root',
        data:{
            isHot:true,
        },
        computed:{
            info(){
                return this.isHot? '炎热':'凉爽';
            },
            methods: {
                changeWeather(){
                    this.isHot = !this.isHot 
                }
            },
            watch:{
                isHot:{
                    //handler什么时候调用?当isHot发 生改变时。
                    handler(){
                        console. log('isHot被修改了')
                    }
                }
            }
        })
</script>
</body>
~~~

> 上面代码能达到点击按钮实现天气效果切换效果。watch内的参数表示当isHot值改变时，就会触发handler()方法。

### 2. watch内置对象的immediate方法

>  handler特点是：最初绑定时不会执行，等到 监听的值改变时才执行监听计算。如果想要一开始就让他在最初绑定的时候就执行监听函数，就需要用到immediate。该参数介绍如下：

|         方法名         |                             描述                             |
| :--------------------: | :----------------------------------------------------------: |
| immediate(true\|false) | 参数为true时，当事件被绑定时直接执行。参数为false时，当事件被调用时候才会执行。其作用主要是初始化时让handler()调用以下。 |

对以上案例进行修改：

~~~html
<body>
    <!-- 准备好一个容器-->
    <div id="root">
        <h2>今天天气很{{info}}</h2>
        <button @click=" changeWeather">切换天气</button>
    </div>
</body>
<script type="text/javascript" >
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    const Vm = new Vue({
        el:'#root',
        data:{
            isHot:true,
        },
        computed:{
            info(){
                return this.isHot? '炎热':'凉爽';
            },
            methods: {
                changeWeather(){
                    this.isHot = !this.isHot 
                }
            },
            watch:{
                isHot:{
                    immediate:true,
                    //handler什么时候调用?当isHot发 生改变时。
                    handler(){
                        console. log('isHot被修改了')
                    }
                }
            }
        })
</script>
</body>
~~~

上面代码的watch也可以写为：

~~~JavaScript
Vm.$watch('isHot',{
    immediate:true, //初始化时让handler调用一下
    //handler什么时候调用?当isHot发生改变时。
    handler (newValue,oldValue){
        console.log('isHot被修改了',newValue ,oldValue)
    }
})
~~~

- watche总结：

  > 监视属性watch:
  >
  > 1. 当被监视的属性变化时，回调函数自动调用，进行相关操作
  > 2. 监视的属性必须存在，才能进行监视! !
  > 3. 监视的两种写法:
  >    - new Vue时传入watch配置
  >    - 通过vm. $watch()监视

### 3. 深度监视

> Vue中的watch默认不监测对象内部值得改变。因为检测的是对象内的地址，当修改对象内的值时，对象的地址不会发生变化，从而Vue的watch属性会默认认为对象内部没有发生变化，就会导致我们检测失败。如果想要检测对象内部值的变化就要用到深度监测：配置`deep:true`可以监测对象内部值改变。
>
> 注意：监听的属性需要字符串形式，因为原本就是字符串的简写，但是此处特定要体现出来。如上面watch内的`isHot()`其应该写为`'isHot()'`。

**监视data中对象的一个数据**：

~~~html
<body>
    <!-- 准备好一个容器-->
    <div id="root">
        <h2>今天天气很{{info}}</h2>
        <button @click=" changeWeather">切换天气</button>
    </div>
</body>
<script type="text/javascript" >
    var vm = new Vue({
        el: "#root",
        data: {
            isHot: true,
            numbers:{
                a:1,
                b:2
            }
        },
        methods: {
            changeWeather() {
                this.isHot = !this.isHot
            }
        },
        computed: {
            info() {
                if (this.isHot) {
                    return "炎热"
                } else {
                    return "寒冷"
                }
            }
        },
        watch: {
            number:{
                deep:true,
                handler(){
                    console.log("1")
                }
            }
        }
    })
</script>
</body>
~~~

> 此时就可以监视data参数内`numbers`对象内部的值变化

- 深度监视总结：

  深度监视:

  1. Vue中的watch默认不监测对象内部值的改变(-层)。
  2. 配置deep:true可以监测对象内部值改变(多层)。

  备注:

  1. Vue自身可以监测对象内部值的改变，但Vue提供的watch默认不可以!
  2. 使用watch时根据数据的具体结构，决定是否采用深度监视。

### 4. 监视的简写形式

> 前提：不需要`immediate`和`deep`属性，函数当作handler方法写

~~~JavaScript
watch:{
    isHot(){
        ....
    }
}
~~~

或者为：

~~~JavaScript
vm.$watch("isHot", function(){
    ...
})
~~~

### 5. watch和computed属性对比

两者区别：

1. computed能完成的功能，watch都可以完成
2. watch能完成的，computed不一定能完成，例如：watch可以进行异步操作

两个小原则：

1. 所被Vue管理的函数，最好写成普通函数，这样this的指向才是vm或者组件实例对象
2. 所有不被Vue所管理的函数（定时器的回调函数、ajax的回调函数，Promise回调函数等），最好写成箭头函数，这样this的指向才是vm或者组件实例对象

## 八. Class、Style绑定与样式渲染

> 我们使用Vue的Class和Style可以更好的绑定样式，更有利于页面代码的维护。
>
> 操作元素的 class 列表和内联样式(Style)是数据绑定的一个常见需求。因为它们都是属性，所以我们可以用 `v-bind` 处理它们：只需要通过表达式计算出字符串结果即可。不过，字符串拼接麻烦且易错。因此，在将 `v-bind` 用于 `class` 和 `style` 时，Vue.js 做了专门的增强。表达式结果的类型除了字符串之外，还可以是对象或数组。

### 1. 绑定Class样式三种写法

> 给标签元素动态添加类名可以有三种写法：字符串赋值、数组赋值、对象赋值。

#### 11. 绑定Class样式字符串写法

> 字符串写法，适用于样式的类名不确定，需要动态指定。

~~~html
<!--这里假设Style标签中有：'happy'、'sad'、'normal'三种样式-->
<body>
    <div class= "basic" :class= "mood" @click=" changeMood" >{{name}}</div>
</body>
<script>
    Vue. config. productionTip = false
    new Vue({
        el: '#root',
        data:{
            name:'shi',	
            mood:'normal'
        },
        methods: {
            changeMood(){
                constarr=['happy','sad','normal']
                const index = Math.floor (Math.random( )*3)
                this.mood = arr[index]
            }
        },
    })
</script>
~~~

> 以上代码当我们点击div盒子后，Vue示例会通过点击事件，将`v-bind`(:后的内容)绑定的值修改为mood的值，然后传递给class。
>
> 当我们运行上面代码时：会随即向`basic`后追加一个style值。

#### 1.2. 绑定Class样式数组写法

> 适用于：要绑定的样式个数不确定、名字也不确定。

~~~html
<!--这里假设Style标签中有：'happy'、'sad'、'normal'三种样式-->
<body>
    <div class="basic" :class="classArr">{{name}}</div>
</body>
<script>
    Vue.config.productionTip = false
    new Vue({
        el: '#root',
        data:{
            name:'shi',	
            classArr:['atguigu1','atguigu2','atguigu3']
        },
    })
</script>
~~~

> 以上代码执行后class会同时拥有：`basic、atguigu1、atguigu2、atguigu3`三个类名

#### 1.3. 绑定Class样式对象写法

> 适用于：要绑定的样式个数确定、名字也确定，但要动态决定用不用。

~~~html
<body>
    <div class= "basic" :class= "classObj" >{{name}}</div>
</body>
<script>
    Vue.config.productionTip = false
    new Vue({
        el: '#root',
        data:{
            name:'shi',
            classObj:{
                atguigu1:false,
                atguigu2:false, 
            }
        },
    })
</script>
~~~

> 上面代码显示中class中的`atguigu1`和`atguigu2`都是false，表示不启用。改为true后，可以启用。

### 2. 绑定Style样式

> 我们可以在Style标签进行行内样式的动态书写。写法是：`v-bind:style=""`(:style="")。写法有两种：对象样式、数组样式。其中的**键名是央视对象**(名字与css中的键名书写格式要一致)。
>
> 这两种不常用，但要注意键名字母一定不要拼写错误，两个单词的第二个单词首字母要大写。和css格式差不多。案例如下：

~~~html
<body>
    <div class="basic" :style="sty1e0bj">{{name}}</div>
</body>
<script>
    Vue.config.productionTip = false
    new Vue({
        el: '#root',
        data:{
            name:'shi',
            sty1e0bj:{
                fontSize: '40px',
                color:'red',
                backgroundColor:'orange'
            }
        },
    })
</script>
~~~

- Class与Style绑定样式总结：

  绑定样式:
  1. class样式
  写法:class="xxx" Xxx可以是字符串、对象、数组。
  字符串写法适用于:类名不确定，要动态获取。
  对象写法适用于:要绑定多个样式，个数不确定，名字也不确定。
  数组写法适用于:要绑定多个样式，个数确定，名字也确定，但不确定用不用。
  2. style样式
  :style="{fontSize: xx}"其中xxx是动态值。
  :style="[a,b]"其中a、b是样式对象。

## 九. 页面渲染

> 页面渲染值得是，通过一些判断规则决定页面节点是否要显示。

### 1. 条件渲染

> 我们使用模板指令来进行条件渲染，用来显示或者隐藏标签节点。指令有两个：`v-show`、和`v-if`。

#### 1.1 v-show指令

> 该指令是一个类型为布尔值的表达式，用来判断是否隐藏标签。
>
> 如果表达式返回结果为true，则显示节点。如果为false，则将节点的`display`属性改为`none`。

示例：

~~~html
<body>
    <div id='root'>
        <!-- 使用v-show做条件渲染-->
        <h2 v-show="false">欢迎来到{{name}}</h2> 
        <h2 v-show="1 === 1">欢迎来到{{name}}</h2> 
    </div>
</body>
~~~

上面的代码第一个`h2`标签会隐藏，而第二个`h2`标签会显示

#### 1.2 v-if指令

> 该指令和`v-show`指令一样，同样用来判断节点是否被隐藏。不同的是当表达式返回的结果为false时，**节点会直接被删除**。

示例：

~~~html
<body>
    <div id='root'>
        <!-- 使用v- if做条件渲染-->
        <h2 v-if="false">欢迎来到{{name}}</h2> 
        <h2 v-if="1===1">欢迎来到{{name}}</h2> 
    </div>
</body>
~~~

同样，上面代码第一个节点会直接删除，第二个节点会正常显示。

#### 1.3 渲染案例

> 我们先准备一个按钮，在准备一个变量。点击按钮变量会+1。当变量等与一个值时，会先是对应标签

~~~html
<body>
    <div id="root">
        <h2>当前的n值是:{{n}}</h2>
        <button @click="n++">点我n+1</ button>
        <div v-show="n===1" >Angular</div>
        <div v-show="n===2">React</div>
        <div v-show="n===3">Vue</ div>
        <!--下面用v-if实现-->
        <div v-if="n===1" >Angular</div>
        <div v-if="n===2">React</div>
        <div v-if="n===3">Vue</ div>
    </div>
</body>
~~~

上面的`v-if`和`v-show`都可以实现显示或者隐藏节点，但不同的是`v-if`会直接将页面的节点删除。所以我们节点操作频率高的时候尽量用`v-show`，频率低时用`v-if`。

#### 1.4 v-else-if指令

> 该指令与JavaScript中的用法类似，但必须要配合`v-if`标签一起使用。

~~~html
<body>
    <div id="root">
        <h2>当前的n值是:{{n}}</h2>
        <button @click="n++">点我n+1</ button>
        <div v-if="n===1" >Angular</div>
        <div v-else-if="n===2">React</div>
        <div v-else-if="n===3">Vue</ div>
    </div>
</body>
~~~

上面代码是当n等于1时，后面的两个div不再执行。当第一个div标签结果为false时，再判断后面两个标签。其运行结果和上面的`v-if`运行一样。但其效率更高。

#### 1.5 v-else指令

> 该指令和JavaScript中的else一样。当前面的判断都不生效时，就输出else指令控制的标签。

~~~html
<body>
    <div id="root">
        <h2>当前的n值是:{{n}}</h2>
        <button @click="n++">点我n+1</ button>
        <div v-if="n===1" >Angular</div>
        <div v-else-if="n===2">React</div>
        <div v-else-if="n===3">Vue</ div>
        <div v-else>text</ div>
    </div>
</body>
~~~

上面代码是当`v-if`和`v-else-if`都判断为false时，执行`v-else`控制的标签。注意`v-if`、`v-else-if`和`v-else`一起做判断时，中间不要添加其他节点。如下：

~~~html
<body>
    <div id="root">
        <h2>当前的n值是:{{n}}</h2>
        <button @click="n++">点我n+1</ button>
        <div v-if="n===1" >Angular</div>
        <div v-else-if="n===2">React</div>
        <div>11</div>
        <div v-else-if="n===3">Vue</ div>
        <div v-else>text</ div>
    </div>
</body>
~~~

> 这段代码只能判断前两个div标签，后面的被`<div>11</div>`节点打断，节点无法进行解析，控制台报错

#### 1.6 v-if和template节点

> template节点为模板节点，可以把列表项放入template标签中，然后进行批量渲染，选然后template节点会消失，节点内的标签正常显示，好处是不改变页面标签结构。但要注意该节点只能和`v-if`标签配合使用。

~~~html
<body>
    <div id="root">
        <h2>当前的n值是:{{n}}</h2>
        <button @click="n++">点我n+1</ button>
        <!-- v-if与template的配合使用-->
        <template v-if="n ===1">
            <h2>你好</h2>
            <h2>shi</h2>
            <h2>北京</h2>
        </template>
    </div>
</body>
~~~

> 运行后页面没有`<template>`节点，直接显示三个`<h2>`节点。好处是不用再每个`h2`节点种写上判断。提高编码效率。

- 条件渲染总结：

  条件渲染:

  1. v-if
     写法：

     - v-if="表达式”
     - v-else-if="表达式"
     - v-else="表达式”

     适用于:切换频率较低的场景。
     特点:不展示的DOM元素直接被移除。
     注意: v-if可以和:v-else-if、v-else起使用， 但要求结构不能被“打断”。

  2. v-show 
  写法: v-show="表达式"
  适用于：切换频率较高的场景。
  特点：不展示的DOM元素未被移除，仅仅是使用样式隐藏掉
  3. 备注：使用v-if的时，元素可能无法获取到，而使用v-show 定可以获取到。

### 2. 列表渲染

> 用 v-for 指令基于一个**数组**来渲染一个列表。
>
> v-for 指令需要使用 **item in items** 形式的特殊语法，其中 items 是源数据数组。其用法和JavaScript的`for in`循环一致。
>
> 为了给 Vue 一个提示，以便它能跟踪每个节点的身份，从而重用和重新排序现有元素，需要为每项提供一个唯一 key属性。

#### 2.1 使用for..in遍历数组

> 可以在数组种定义几组对象，来进行遍历取值，放进容器中。但记得for...in循环指令中一定要绑定一个`key`值，用作每个节点的id。

~~~html
<body>
    <div>
        <h2>人员列表</h2>
        <ul>
            <li v-for="(p,index) of persons" :key="index">
                {{p.name}}-{{p.age}}
            </li>
        </ul>
    </div>
</body>
<script>
    Vue . config . productionTip = false
    new Vue({
        el: '#root',
        data:{
            persons:[
                {id:'001',name:'张三',age :18},
                {id:'002',name: '李四',age:19},
                {id:'003',name:'王五',age :20}
            ],
        }
    })
</script>
~~~

以上代码运行结果：

[for...in循环运行结果：](https://s1.ax1x.com/2022/04/26/LHXjDe.png)

​																			[<img src="https://s1.ax1x.com/2022/04/26/LHXjDe.png" alt="LHXjDe.png" style="zoom:50%;" />](https://imgtu.com/i/LHXjDe)

#### 2.2 使用for..in遍历对象

> for...in可以用于遍历对象，需要注意的是遍历对象时第一个接收的参数是对象的值，第二个参数是对象名。

~~~html
<body>
    <div>
        <h2>汽车信息</h2>
        <ul>
            <li v-for="(value,k) in car" :key="k">
                {{a}}--{{b}} 
            </li>
        </ul>
    </div>
</body>
<script>
    Vue.config.productionTip = false
    new Vue({
        el: '#root',
        data:{
            car:{
                name:'奥迪A8',
                price:'70万',
                color:'黑色'
            }
        })
</script>
~~~

运行结果：

[for...in遍历对象结果：](https://s1.ax1x.com/2022/04/26/LHxLvV.png)

​																[<img src="https://s1.ax1x.com/2022/04/26/LHxLvV.png" alt="LHxLvV.png" style="zoom: 50%;" />](https://imgtu.com/i/LHxLvV)

- 列表渲染总结：

  v-for指令:

  1. 用于展示列表数据
  2. 语法: v-for="(item, index) in xx" : key="yyy"
  3. 可遍历:数组、对象、字符串(用的很少)、指定次数(用的很少)

#### 2.3 ==for...in循环中key的作用==

> 当 Vue.js 用`v-for`正在更新已渲染过的元素列表时，它默认用“就地复用”策略。如果数据项的顺序被改变，Vue 将不会移动 DOM 元素来匹配数据项的顺序， 而是简单复用此处每个元素，并且确保它在特定索引下显示已被渲染过的每个元素。
>
> 此时会导致两个问题：
>
> 1. 效率低下
> 2. 索引值对比算法(diff算法)出错

- 问题引入：

  ~~~html
  <body>
      <!--准备好一个容器-->
      <div id="root">
          <!--遍历数组-->
          <h2>人员列表(遍历数组) </h2>
          <button @click . once=" add">添加一个老刘</ button>
          <ul> 
              <li v-for="(p,index) of persons" :key="index">
                  {{p.name}}-{{p.age}}
                  <inputr type="text"/>
              </li>
          </ul>
      </div>
  </body>
  <script>
      Vue.config.productionTip = false
      new Vue({
          el:'#root',
          data:{
              persons:[
                  {id:'001',name: '张三' ,age:18},
                  {id:'002',name:'李四',age:19},
                  {id:'003',name:'王五',age:20}
              ],
              methods: {
                  add(){
                      const p = {id:'004',name:'老刘',age :40}
                      this.persons.unshift(p)
                  }
              },
          })
  </script>
  ~~~

  以下问题导致的原因是`key`的值为index，如果将`key`的值改为`p.id`用对象里的唯一标识id就可以解决这个问题

  上面代码运行后在输入框内输入信息后点击按钮将`老王`节点添加到页面，此时就会出现问题：

  [key出现的问题：](https://s1.ax1x.com/2022/04/26/Lb9wRA.png)

​													[<img src="https://s1.ax1x.com/2022/04/26/Lb9wRA.png" alt="Lb9wRA.png" style="zoom:50%;" />](https://imgtu.com/i/Lb9wRA)

- key的分析

  > 可以没有值，默认为index值。当key用index做值时：

  [key分析图：](https://s1.ax1x.com/2022/04/26/Lbkb8g.png)                        [<img src="https://s1.ax1x.com/2022/04/26/Lbkb8g.png" alt="Lbkb8g.png" style="zoom: 50%;" />](https://imgtu.com/i/Lbkb8g)

  > 由上图我们观察到：
  >
  > 1. Vue先拿到data中的初始数据person中的值。
  > 2. 根据数据生成虚拟DOM，再将虚拟的DOM，在虚拟的DOM中节点有`key`值，这个值是给Vue后续做对比用的。之后会转换为真实DOM，取消`key`值。
  > 3. 之后我们向输入框内输出文字后，再点击按钮，会添加一个`老王`节点。
  > 4. 此时，Vue会生成新的实例，在这个实例中老王会被放在节点的最上面。
  > 5. 根据最新生成的数据生成新的虚拟DOM，在这个虚拟DOM中由于我们指定的`key`值为`index`值，所以`老王`节点的key值为0，之后依次递增。
  > 6. 这时，Vue会使用diff算法和之前旧的虚拟DOM进行数据对比，如果两个虚拟DOM中的数据一样，就会直接拿来用，当不一样时，就会将新的值替代旧的值。
  > 7. 因为我们在输入框中输入的数据实在真实DOM中体现的。所以Vue会将两个虚拟DOM中的`<input>`节点当作一样的数据进行输出。

  以下是用key的id做值：

  [key用id做值：](https://s1.ax1x.com/2022/04/26/LbEspD.png)                                  [<img src="https://s1.ax1x.com/2022/04/26/LbEspD.png" alt="LbEspD.png" style="zoom: 50%;" />](https://imgtu.com/i/LbEspD)

  > 以上是节点在前面加入，当我们把代码中的`this.persons.unshift(p)`改为`this.persons.push(p)`

- key作用总结

  > react、vue中的key有什么作用? ( key的内部原理)

  1. 虚拟DOM中key的作用:
     key是虚拟DOM对象的标识，当状态中的数据发生变化时，Vue会根据[新数据]生成[新的虚拟DOM]，随后Vue进行[新虚拟DOM]与[旧虚拟DOM]的差异比较，比较规则如下。

  2. 对比规则:
     (1) .旧虚拟DOM中找到了与新虚拟DOM相同的key:

     - 若虚拟DOM中内容没变，直接使用之前的真实DOM!
     - 若虚拟DOM中内容变了，则生成新的真实DOM，随后替换掉页面中之前的真实DOM。

     (2).旧虚拟DOM中未找到与新虚拟DOM相同的key

     - 创建新的真实DOM，随后渲染到到页面。

  3. 用index作 为key可能会引发的问题:
     (1). 若对数据进行:逆序添加、逆序删除等破坏顺序操作:

     - 会产生没有必要的真实DOM更新==>界面效果没问题，但效率低。

     (2). 如果结构中还包含输入类的DOM:

     - 会产生错误DOM更新==>界面有问题。

  4. 开发中如何选择key?：

     - 最好使用每条数据的唯一标识作为key,比如id、手机号、身份证号、学号等唯一值。
     - 如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，使用index作为key是没有问题的。
  
### 3. 列表过滤案例

> 我们需要准备一段数据，并在网页中实现模糊查询的效果。

- 监听属性实现代码如下：

  ~~~html
  <body>
      <div id= "root">
          <h2>人员列表</h2>
          < input type="text" placeholder="请输入名字"v-model="keyWord">
          <ul>
              <li v-for="(p,index) of filPerons" :key= "index">
                  {{p.name}}-{{p.age}}-{{p.sex}}
              </li>
          </ul>
      </div>
  </body>
  <script>
      //用watch实现
      new Vue({
          el:'#root',
          data:{
              keyWord:' ',
              persons:[
                  {id:'001',name:'马冬梅',age:19,sex:'女'},
                  {id:'002',name:'周冬雨',age:20,sex:'女'},
                  {id:'003',name:'周杰伦',age:21,sex:'男'},
                  {id:'004',name:'温兆伦',age:22, sex:'男'}
              ],
              filPerons:[]
          },
          watch:{
              keyWord:{
                  immediate: true, 
                  handler(val){
                      this.filPerons = this.persons.filter((p)=>{
                          return p.name.indexOf(val)!== -1
                      })
                  }
              }
          })
  </script>
  ~~~

  > 上面一段代码可以实习对`persons`中的数据进行模糊查询并展示在页面的效果。
  >
  > 其中`watch`中的代码是：监听与文本框绑定的keyword变量有没有改变，即当用户在用户框中输入信息时，keyword的值就会改变。如果改变监听函数就会对`persons`数组中的数据进行查询匹配，如果未匹配则返回结果`-1`，匹配成功返回数组下标。` this.persons.filter`会将返回的下标数组筛选出来传给`filePerons`数组，并在页面中列表中通过`v-for`遍历`filePerons`输出到页面。

- 这里也可以用计算属性写：

  ~~~html
  <body>
      <div id= "root">
          <h2>人员列表</h2>
          < input type="text" placeholder="请输入名字"v-model="keyWord">
          <ul>
              <li v-for="(p,index) of filPerons" :key= "index">
                  {{p.name}}-{{p.age}}-{{p.sex}}
              </li>
          </ul>
      </div>
  </body>
  <script>
      new Vue({
          el:'#root',
          data:{
              keyWord:'',
              persons:[
                  {id:'001',name:'马冬梅',age:19,sex:'女'},
                  {id:'002',name:'周冬雨',age:20,sex:'女'},
                  {id:'003',name:'周杰伦',age:21,sex:'男'},
                  {id:'004',name:'温兆伦',age:22, sex:'男'}
              ]
          },
          computed:{
              filPerons(){
                  return this.persons.filter((p)=>{
                      return p.name.indexOf(this.keyWord) !== -1
                  })
              }
          }
      })
  </script>
  ~~~

  > 使用计算属性较为简单，我们只需要关注`keyWord`变量，也就是只用关注用户的输入字符即可。

### 4. 列表排序案例

> 我们在上个案例中实现了模糊搜索数据的操作，这里我们再添加一个实现搜索后排序的功能。排序有升序、降序和原顺序。

~~~html
<body>
    <div id= "root">
        <h2>人员列表</h2>
        <input type="text" placeholder="请输入名字" v-model="keyWord"/>
        <button @click="sortType=2">年龄升序</button>
        <button @click="sortType=1">年龄降序</button>
        <button @click="sortType=0">原顺序</button>
        <ul>
            <li v-for="(p,index) of filPerons" :key= "p.id">
                {{p.name}}-{{p.age}}-{{p.sex}}
            </li>
        </ul>
    </div>
</body>
<script>
    new Vue({
        el:'#root',
        data:{
            keyWord:'',
            sortType:0, //0代表原顺序 1降序 2升序
            persons:[
                {id:'001',name:'马冬梅',age:19,sex:'女'},
                {id:'002',name:'周冬雨',age:20,sex:'女'},
                {id:'003',name:'周杰伦',age:21,sex:'男'},
                {id:'004',name:'温兆伦',age:22, sex:'男'}
            ]
        },
        computed:{
            filPerons(){
                const arr=this.persons.filter((p)=>{
                    return p.name.indexOf(this.keyWord) !== -1
                })
                if(this.sortType){
                    arr.sort((p1,p2)=>{
                        return this. sortType === 1 ? p2.age-p1.age : p1.age-p2.age
                    })
                }
                return arr
            }
        }
    })
</script>
~~~

> 这个案例中我们只需要创建一个标记变量`sortType`用来判断变量值是否需要排序。再根据需求进行排序即可。

### 5. Vue检测数据的原理

> - 在对象中检测原理：
>
>   在Vue的设计中对对象的数据进行了一个递归，查找对象中的每一个属性，并且对其进行数据代理，给每一个属性设有`get`和`set`方法，这样子当对象中的数据发生改变，那么Vue就会察觉并修改页面中的数据
>
> - 在数组中检测原理：
>
>   通过包裹数组更新元素的方式实现，本质就是做了两件事：
>
>   1. 调整原生对应的方法对数组进行更新
>   2. 重新解构模型，进而更新页面
>
> 在修改数组的时候，我们只有通过数组的修改方法才能达到页面响应的效果。这是因为Vue将能改变原数组的的方法进行了包装，所以当我们调用这些方法才可以进行试图更新。修改方法有`push`、`pop`、`shift`、`unshift`、`splice`、`sort`、`reverse`。
>
> **在修改对象或者数组的时候，我们也可以用Vue给我们提供的`set`API来进行添加数据。**

**注意：Vue.set()和vm.set() 不能给vm或者vm的根数据对象添加属性(如：data、vm)**

#### 5.1 Vue的无法监听对象的情况

- 问题引入：

  ~~~html
  <body>
      <div id="root">            
          <button @click="updata">更新周冬雨的信息</button>
          <ul>
              <li v-for="p in persons" :key="p.id">
                  {{p.name}}---{{p.age}}
              </li>
          </ul>
      </div>
  </body>
  <script>
      var vm = new Vue({
          el:"#root",
          data:{
              persons:[
                  {id:"001", name:"周冬雨", age:19},
                  {id:"002", name:"周杰伦", age:30},
                  {id:"003", name:"夏雨", age:2},
                  {id:"004", name:"温兆伦", age:22}
              ]
          },
          methods: {
              updata(){
                  this.persons[0].name = "周老师"
                  this.persons[0].age = 40
              }
          }
      })
  </script>
  ~~~

  以上方法使用给数组属性赋值的方式可以实现页面数据变化。当我们点击页面按钮后显示数据就会改为下面的：

  [Vue监视页面原理：](https://s1.ax1x.com/2022/04/28/LXm9DU.png)

  ​																	[<img src="https://s1.ax1x.com/2022/04/28/LXm9DU.png" alt="LXm9DU.png" style="zoom:50%;" />](https://imgtu.com/i/LXm9DU)

- 但如下代码却不能完成修改页面数据的操作。

  ~~~html
  <body>
      <div id="root">            
          <button @click="updata">更新周冬雨的信息</button>
          <ul>
              <li v-for="p in persons" :key="p.id">
                  {{p.name}}---{{p.age}}
              </li>
          </ul>
      </div>
  </body>
  <script>
      var vm = new Vue({
          el:"#root",
          data:{
              persons:[
                  {id:"001", name:"周冬雨", age:19},
                  {id:"002", name:"周杰伦", age:30},
                  {id:"003", name:"夏雨", age:2},
                  {id:"004", name:"温兆伦", age:22}
              ]
          },
          methods: {
              updata(){
                 	this.persons[0] = {id:"001", name:"周老师", age:40}
              }
          }
      })
  </script>
  ~~~

  分批对一个对象的属性进行修改，这样产生的效果是对的，**但是我们修改一整条数据（对象），并没有产生我们预想中的效果**，但此时我们打开控制台去看到数据已经修改：

  [Vue监测数据控制台改变：](https://s1.ax1x.com/2022/04/28/LXmjde.png)

  ​                                        [<img src="https://s1.ax1x.com/2022/04/28/LXmjde.png" alt="LXmjde.png" style="zoom:50%;" />](https://imgtu.com/i/LXmjde)

  我们可以用如下方法进行修改：

  ~~~JavaScript
  this.persons.splice(0,1,{name:'周老师',age:50})
  ~~~

  这时我们再点击按钮就可以达到修改第一行数据的效果。

#### 5.2 Vue的两个setAPI

> 由于上面的赋值属性导致Vue无法做到监听页面的效果，这是由于属性的没有`setter`方法导致的，所以我们在给页面追加属性的时候可以使用Vue的两个API来达到给页面添加元素的同时追加`getter`和`setter`方法。该方法可以向响应式对象中添加一个属性。

~~~html
<body>
    <button @click="addSex">添加一个性别属性，默认值是男</button> 
    <h2> v-if="student.sex">性别：{{student.sex}}</h2> 
</body>
<script>
    const Vm = new Vue({
        el: '#root',
        data:{
            name:'shi',
            address:'北京',
            student:{
                name:'Tom',
                age:{
                    rAge:40,
                    sAge :29,
                },
                friends:[
                    {name:'jerry',age:35},
                    {name:'tony',age:36}
                ]
            }
        },
        methods: {
            addSex(){
                Vue.set(this.student,'sex','男')
            }
        }
    })
</script>
~~~

> 上面的`Vue.set(this.student,'sex','男')`代码用于在点击按钮后往页面添加一个性别的属性。如果不适用set方法，则Vue就无法做到页面监听，从而页面就不会有该项属性。
>
> 这里也可以写为：`Vue.$set(this.student,'sex','男')`
>
> 注意：set不能给Vue的data实例追加属性，只能给data内的对象或者数组追加。

## 十. 收集表单数据

> 我们之前的`v-model`指令可以做到收集用户输出框内信息的效果。但却不能收集用户选框内的数据。如下：

[from中选框收集不到数据：](https://s1.ax1x.com/2022/04/29/LvqDSA.png)

​													[<img src="https://s1.ax1x.com/2022/04/29/LvqDSA.png" alt="LvqDSA.png" style="zoom:50%;" />](https://imgtu.com/i/LvqDSA)

上图所示我们勾选了性别为女，但Vue示例绑定属性却显示为`null`。所以数据收集失败。解决办法就是给每个选框设置`value`值。勾选时，获取`value`值数据即可。

### 1. 收集用户信息完整代码：

~~~html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8"/>
        <title>收集表单数据</title>
        <script type="text/javascript" src="../js/vue.js"></script>
    </head>
    <body>
        <div id="root">
            <form @submit.prevent="demo1">
                <label for="demo">账号：</label>
                <input type="text" id="demo" v-model.trim="userInfo.account"><br/><br/>
                密码： <input type="password" v-model="userInfo.password"><br/><br/>
                年龄： <input type="number" v-model.number="userInfo.age"><br/><br/>
                性别：
                男<input type="radio" name="sex" value="male" v-model="userInfo.sex">
                女<input type="radio" name="sex" value="female" v-model="userInfo.sex"><br/><br/>
                爱好：
                学习<input type="checkbox" v-model="userInfo.hobby" value="study">
                打游戏<input type="checkbox" v-model="userInfo.hobby" value="game">
                听音乐<input type="checkbox" v-model="userInfo.hobby" value="music"><br/><br/>
                所属校区:
                <select v-model="userInfo.city">
                    <option value="">请选择校区</option>
                    <option value="beijing">北京</option>
                    <option value="shanghai">上海</option>
                    <option value="shenzhen">深圳</option>
                    <option value="guangzhou">广州</option>
                </select><br/><br/>
                其他信息：
                <textarea v-model.lazy="userInfo.other"></textarea><br/><br/>
                <input type="checkbox" v-model="userInfo.agree">阅读并接受 <a href="https://www.hnu.edu.cn/">《用户协议》</a><br/><br/>
                <button>提交</button>
            </form>
        </div>
    </body>

    <script type="text/javascript">
        Vue.config.productionTip = false

        const vm = new Vue({
            el:'#root',
            data:{
                userInfo:{
                    account:'',
                    password:'',
                    age:'',
                    sex:'',
                    hobby:[],
                    city:'',
                    other:'',
                    agree:'',
                },
            },
            //以JSON格式输出用户填写的信息。
            methods: {
                demo1(){
                    console.log(JSON.stringify(this.userInfo))
                }
            }
        })
    </script>
</html>
~~~

[表单数据收集成功：](https://s1.ax1x.com/2022/04/29/LvvkDI.png)										[<img src="https://s1.ax1x.com/2022/04/29/LvvkDI.png" alt="LvvkDI.png" style="zoom: 50%;" />](https://imgtu.com/i/LvvkDI)

### 2. v-model修饰符

|     修饰符     |                             描述                             |
| :------------: | :----------------------------------------------------------: |
|  v-model.lazy  | 使用lazy修饰符来进行限定。只有当用户的input中失去焦点或者用户点击回车按钮时，才会将后台的数据进行修改。 |
| v-model.number | 当用户在input中输入数字时，浏览器会默认将输入的数字转化为string类型，使用number修饰符来将输入的数字转为number类型。一般配合`input`中的`type='number'`使用 |
|  v-model.trim  | 用户可能输入的字符串中含有空格，这样系统在处理时可能会出现错误。使用trim修饰符来去掉字符串首部或者尾部的所有空格。 |

### 3. 总结

收集表单数据:
若：` <input type="text"/>`, 则v -model收集的是value值，用户输入的就是value值。
若： `<input type="radio"/>`, 则v-model收集的是value值，且要给标签配置value值。
若： `<input type="checkbox"/>`

1. 没有配置input的value属性，那么收集的就是checked(勾选or未勾选，是布尔值)
2. 配置input的value属性:
   - v-mode1的初始值是非数组，那么收集的就是checked (勾选or未勾选，是布尔值)
   - v-mode1的初始值是数组，那么收集的的就是value组成的数组

## 十一. 过滤器

> 功能：对要显示的数据进行特定格式化后再显示
> 注意：并没有改变原本的数据,是产生新的对应的数据。

### 1. 过滤器使用位置

> 过滤器可以用在两个地方：**双花括号插值和 `v-bind` 表达式** (后者从 2.1.0+ 开始支持)，用字符串`|`标识从这里开始是一个过滤器

~~~html
<!--在双花括号中-->
{{ rawId | filterformatId }}

<!--在v-bind中。v-bind可省略，以简写--> 
<div v-bind:id="rawId | filter formatId"></div> 
~~~

完整写法：

~~~html
<template>
    <div class="test">
        <div :id="rawId">{{rawId}}</div>
        <!--以下v-bind可省略，即v-bind:id可简写为:id -->
        <div v-bind:id="rawId |filter formatId">{{rawId | filter formatId}}</div>
    </div>
    </ template>
<script>
    export default {
        data() {
            return {
                rawId: 1
            };
        },
        filters: {
            filterformatId(value) {
                return value * 10; 
            }
        }
    };
</script>
~~~

[运行结果：](https://s1.ax1x.com/2022/04/29/Lxigv8.png)

​												[<img src="https://s1.ax1x.com/2022/04/29/Lxigv8.png" alt="Lxigv8.png" style="zoom: 50%;" />](https://imgtu.com/i/Lxigv8)

### 2. 全局过滤器、局部过滤器

- 全局过滤器，要用到`filter`方法，该方法接收两个参数：第一个参数是方法名，第二个参数是具体方法

  ~~~JavaScript
  Vue.filter('filteraddPricePrefix', function (value) {
    return "¥" + value;
  })
  ~~~

- 局部过滤器，我们正常再Vue实例中编写的filters叫局部方法，也叫局部过滤器

  ~~~html
  <template>
      <div class="test">
          <p>{{price}}</p>
          <p>{{price | filter_addPricePrefix}}</p>
      </div>
  </template>
  
  <script>
      export default {
          data() {
              return {
                  price: 100
              };
          },
          filters: {
              filter_addPricePrefix(value) {
                  return "¥" + value;
              }
          }
      };
  </script>
  
  <style lang="scss" scoped>
      .test {
          color: black;
      }
  </style>
  ~~~

### 3，过滤器中的参数

> 以下代码中，`filterA` 被定义为接收三个参数的过滤器函数。其中 `message` 的值作为第一个参数，普通字符串 `'arg1'` 作为第二个参数，表达式 `arg2` 的值作为第三个参数。

~~~javascript
{{ message | filterA('arg1', arg2) }}
~~~

实例：

~~~html
<template>
    <div class="test">
        <!-- 要过滤的数据，永远是第一个参数；通过filter函数，传递的参数，依次排在后面。 -->
        <p>{{ new Date() | filter_dateFormat }}</p>
        <p>{{ new Date() | filter_dateFormat('YYYY-MM-DD') }}</p>
        <p>{{ new Date() | filter_dateFormat('YYYY-MM-DD', count) }}</p>
    </div>
</template>
<script src="https://cdn.bootcss.com/moment.js/2.24.0/moment.js"></script>
<script>
    export default {
        data() {
            return {
                count: 10
            };
        },
        filters: {
            filter_dateFormat(date, format, count) {
                return (
                    moment(date).format(format || "YYYY-MM-DD HH:mm:ss") +(count ? " -- " + count : "")
                );
            }
        }
    };
</script>
~~~

[运行结果：](https://s1.ax1x.com/2022/04/29/LxkSeg.png)

​																			[![LxkSeg.png](https://s1.ax1x.com/2022/04/29/LxkSeg.png)](https://imgtu.com/i/LxkSeg)

### 4. 多个过滤器串联

> 如下代码：`filterA` 被定义为接收单个参数的过滤器函数，表达式 `message` 的值将作为参数传入到函数中。然后继续调用同样被定义为接收单个参数的过滤器函数 `filterB`，将 `filterA` 的结果传递到 `filterB` 中。

~~~JavaScript
{{ message | filterA | filterB }}
~~~

完整示例：

~~~html
<template>
    <div class="test">
        <p>{{price}}</p>
        <p>{{price | filter_addPricePrefix}}</p>
        <p>{{price | filter_addPricePrefix |filter_addPriceSuffix}}</p>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                price: 100
            };
        },
        filters: {
            filter_addPricePrefix(value) {
                return "¥" + value;
            },
            filter_addPriceSuffix(value) {
                return value + "元";
            }
        }
    };
</script>

<style lang="scss" scoped>
    .test {
        color: black;
    }
</style>
~~~

[运行结果：](https://s1.ax1x.com/2022/04/29/LxkUTH.png)

​																			[![LxkUTH.png](https://s1.ax1x.com/2022/04/29/LxkUTH.png)](https://imgtu.com/i/LxkUTH)

### 5. 总结

过滤器：
定义：对要显示的数据进行特定格式化后再显示(适用于一些简单逻辑的处理)。
语法:

1. 注册过滤器: Vue . filter(name, callback)或new Vue{filters;{}}
2. 使用过滤器: {{ xxx|过滤器名}} 或v-bind:属性 ='xxx|过滤器名”

备注:

1. 过滤器也可以接收额外参数、多个过滤器也可以串联
2. 并没有改变原本的数据，是产生新的对应的数据

## 十二. 其他Vue指令介绍

> 经过之前的学习我们已经学习了Vue的大部分指令，这里在对几个较为常用的指令进行介绍

### 1. v-text指令

> 向所在的标签中插入文本，其与插值语法的区别在于，该指令会直接替换容器中的内容。

~~~html
<body>
    <div>你好，{{name}}</div>
    <div v-text="name">你好</div>
</body>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    new Vue({
        el: '#root',
        data:{
            name:'shi'
        }
    })
</script>
~~~

运行结果：`你好，shi`，`shi`

- 总结：

  作用：向其所在的节点中渲染文本内容。
  与插值语法的区别： v-text会 替换掉节点中的内容，{{xx}}则不会。

### 2. v-html指令

> 与v-text的功能一致，但`v-html`可以进行结构解析。即可以将定义的字符标签转换为HTML。

~~~html
<body>
    <!--准备好一个容器--> 
    <div id="root">
        <div v-html= "str"></div>
    </div>
</body>
<script type= "text/javascript" >
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    new Vue({
        el:'#root'，
        data:{
        name: 'shi',
        str:'<p>你好啊! </p>'
</script>
~~~

运行后页面输出：**`你好啊！`**

~~~html
<a href=javascript:location.href= "http:/ /www. baidu . com?"+document.cookie></a>
~~~

- 总结

  v-htm1指令：

  1. 作用:向指定节点中渲染包含html1结构的内容。
  2. 与插值语法的区别:
     - v-html会替换掉节点中所有的内容，{{xx}}则不会。
     - v-htm1可以识别htm1结构。
  3. 严重注意: v-htm1有 安全性问题! ! ! !
     - 在网站上动态渲染任意HTML是非常危险的，容易导致XSS攻击。
     - 一定要在可信的内容上使用v-html，永不要用在用户提交的内容上!

### 3. v-cloak指令

> v-cloak指令常常用在插值表达式的标签中，因为它可以解决当网络加载很慢时，或者频繁渲染时候，页面就会显示出源代码的情况。
>
> v-cloak原理是先通过样式隐藏内容，然后在内存中进行值的替换，将替换的内容再反馈给界面，数据渲染完场之后，v-cloak 属性会被自动去除。

~~~html
<style type="text/css">
    [v-cloak]{
        display: none;
    }
</style>
<h3 v-cloak>{{name}}</h3>
~~~

以上代码会在服务器加载完毕后在将v-cloak移除，达到显示标签的效果。

v-cloak指令(没有值) :

1. 本质是一个特殊属性，Vue实 例创建完毕并接管容器后，会删掉v-cloak属性。
2. 使用css配合v-cloak可以解决网速慢时页面展示出{ {x}}的问题。

### 4. v-once指令

> v-once指令: 
>
> 1. v-once所在节点在初次动态渲染后，就视为静态内容了。
> 2. 以后数据的改变不会引起v-once所在结构的更新，可以用于优化性能。

~~~html
<body>
    <div id="root">
        <h2 v-once>初始化的n值是:{{n}</h2>
        <h2>当前的n值是:{{n}}</h2>
        <button @click= "n++">点我n+1</button>
    </div>
</body>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    new Vue({
        el: '#root',
        data:{
            n:1
        }
    })
</script>
~~~

以上代码执行之后，第一个`<h2>`标签只会读取一次n的值，后来n++不会对绑定`v-once`指令的标签造成影响。

### 5. v-pre指令

> v-pre指令:
>
> 1. 跳过其所在节点的编译过程。
> 2. 可利用它跳过:没有使用指令语法、没有使用插值语法的节点，会加快编译。

~~~html
<body>
    <div id="root">
        <h2 v-pre>初始化的n值是:{{n}</h2>
        <h2 v-pre>当前的n值是:{{n}}</h2>
        <button @click= "n++">点我n+1</button>
    </div>
</body>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    new Vue({
        el: '#root',
        data:{
            n:1
        }
    })
</script>
~~~

运行结果：`初始化的n值是:{{n}`、`当前的n值是:{{n}}`页面不会进行编译，而是直接渲染。

## 十三. Vue的自定义指令

> 自定义指令需要在标签后以`v-指令名='表达式'`的形式绑定标签。之后要在Vue实例中用`directives`参数，书写指令表达式(自定义指令要干什么)。`directives`参数内的指令默认可以接收两个参数。也可以有两种写法：对象式和函数式。`directives`参数介绍如下：

|   参数名    |                      描述                       |
| :---------: | :---------------------------------------------: |
| element参数 | 获取网页绑定自定义标签的真实DOM(即获得绑定标签) |
| binding参数 |          绑定标签时表达式的值或者对象           |

### 1. 自定义指令的函数式写法

> 我们有一个需求：定义一个v-big指令,和v-text功能 类似，但会把绑定的数值放大10倍。代码如下：

~~~html
<body>
    <div id="root">
        <h2>当前的n值是: <span v-text="n"></span></h2>
        <h2>放大10倍后的n值是: <span v-big="n"></span></h2>
        <button @click="n++">点我n+1</button>
    </div>
</body>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    new Vue({
        el:'#root',
        data:{
            n:1
        },
        directives :{
            //big函数何时会被调用?1.指令与元素成功绑定时(一上来)。2.指令所在的模板被重新解析时。
            big(element, binding){
                element.innerText = binding.value*10
            }
        }
    })
</script>
~~~

> 以上代码会在浏览器页面输出放大10倍后的n值。
>
> 其中我们在第4行给`<span>`标签绑定了一个自定义指令`v-big`并传递了一个参数n，在`directives`中定义指令语法。其中`big`的第一个参数为`<span>`节点元素，第二参数为data中的n对象。第18行代码让`<span>`标签中显示n*10后的值。
>
> big函数调用时机：
>
> 1. 指令与元素成功绑定时(一上来就调用)
> 2. 指令所在的模板被重新解析时。即Vue中的任何数据修改时。

### 2. 自定义指令的对象式写法

> 定义一个`v-fbind`指令，和v-bind功能类似，但可以让其所绑定的input元素默认获取焦点。因为函数式的代码在刚上来的就被调用，此时`input`没有被Vue实例插入到页面，所以获取焦点会失败，这时我们就要用到对象式写法，以更精确的控制代码插入的时机。以下是代码：

~~~html
<body>
    <div id="root">
        <h2>当前的n值是: <span v-text="n"></span></h2>
        <h2>放大10倍后的n值是: <span v-big="n"></span></h2>
        <button @click="n++">点我n+1</button>
        <input type= "text" v-fbind:value="n">
    </div>
</body>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
    new Vue({
        el:'#root',
        data:{
            n:1
        },
        directives :{
            fbind:{
                //指令与元素成功绑定时(一上来)
                bind(element,binding){
                    element.value = binding. value 
                },
                //指令所在元素被插入页面时
                inserted(element,binding){
                    element.focus()
                },
                //指令所在的模板被重新解析时
                update(element,binding){
                    element.value = binding.value
                }
            }
        }
    })
</script>
~~~

此时我们就可以做到打开网页就获取输入框的焦点。

> 上面的代码中对象式的写法中默认有三个方法需要我们重写，分别是：`bind`、`inserted`、`update`他们详细说明如下：

|          方法名           |                描述                |
| :-----------------------: | :--------------------------------: |
|   bind(element,binding)   | 指令与元素成功绑定时(一上来就执行) |
| inserted(element,binding) |      指令所在元素被插入页面时      |
|  update(element,binding)  |     指令所在的模板被重新解析时     |

其中`bind`和`update`执行功能基本一致。我们有特殊业务的情况下是在`inserted`中配置业务。

### 3. 定义全局指令

> 与之前的定义过滤器的方法一样，我们要用到`Vm.directive('方法名',函数{})`

~~~JavaScript
//对象式
Vue.directive('fbind' ,{
    //指令与元素成功绑定时(一上来)
    bind(element , binding){
        element.value = binding 。value
    },
    //指令所在元素被插入页面时
    inserted(element , binding){
        element. focus( )
    },
    //指令所在的模板被重新解析时
    update(element, binding){
        element.value = binding. value
    }
}) 
//函数式
Vue.directive('big',function(element , binding){
    console.log('big' ,this) //注意此处的this是window
    element.innerText = binding.value*10
})
~~~

- 总结

  自定义指令总结:
  一. 定义语法:

  - 局部指令:
    directives:{指令名:配置对象}或directives:{指令名:回调函数}
  - 全局指令:
    Vue.directive(指令名，配置对象)或Vue. directive(指令名，回调函数)

  二、 配置对象中常用的3个回调:

  - bind:指令与元素成功绑定时调用。
  - inserted:指 令所在元素被插入页面时调用。
  - update:指令所在模板结构被重新解析时调用。

  三、备注:

  1. 指令定义时不加v-，但使用时要加V-
  2. 指令名如果是多个单词，要使用kebab-case命名方式，不要用camelCase命名。

## 十四. Vue的生命周期

> 生命周期:
>
> 1. 又名:生命周期回调函数、生命周期函数、生命周期钩子。
> 2. 是什么：Vue在关键时刻帮我们调用的一些特殊名称的函数。
> 3. 生命周期函数的名字不可更改，但函数的具体内容是程序员根据需求编写的。
> 4. 生命周期函数中的this指向是vm或组件实例对象
>
> 生命周期方法：
>
> 1. 
>    创建期间生命周期方法      beforeCreate:     created:      beforeMount      mounted
> 2. 运行期间生命周期方法      beforeUpdate      updated
> 3. 
>    销毁期间的生命周期方法    beforeDestroy     destroyed

生命周期方法：

|    方法名    |                             描述                             |
| :----------: | :----------------------------------------------------------: |
| beforeCreate | 生命周期、事件，数据代理还未开始。此时：无法通过vm访问到data中的数据、methods中的方法。 |
|   created    | 数据检测，数据代理开始，此时：可以通过vm访问到data中的数据、methods中配置的方法。 |
| beforeMount  | 页面呈现的是未经Vue编译的DOM结构。此时所有对DOM的操作，最终都不奏效。 |
|   mounted    | 页面中呈现的是经过Vue编译的DOM。此时对DOM的操作均有效(尽可能避免)。<br/>至此初始化过程结束，一般在此进行:开启定时器、发送网络请求、订阅消息、</br>绑定自定义事件、等初始化操作。 |

[Vue生命周期图：](https://s1.ax1x.com/2022/04/30/OpJBqS.png)

​		[<img src="https://s1.ax1x.com/2022/04/30/OpJBqS.png" alt="OpJBqS.png" style="zoom:50%;" />](https://imgtu.com/i/OpJBqS)



