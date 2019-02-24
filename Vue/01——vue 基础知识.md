01——vue 基础知识

1. vue 与 angular：

   vue.js 兼具 angular.js 和 react 的特点

   - vue 设计之初参考了很多 angular 的思想
   - vue 相比于 angular 来说更加简单
   - vue 相当于 angular 要小巧很多，运行速度比 angular 快
   - vue 和 angular 绑定都可以用 {{ }}
   - vue 指令用 v-xxx，angular 用 ng-xxx
   - vue 中数据放在 data 对象里面，angular 数据绑定在 $cope 上面
   - vue 有组件化概念，angular 中没有

2. vue 与 react

   - react 和 vue 都是用虚拟 DOM virtual DOM
   - react  和 vue 都提供了响应式（reactive）和组件化（componsable）的视图组件
   - react  和 vue 都将注意力集中保持在核心库，伴随于此，有配套的路由和负责处理全局状态管理的库
   - react  使用了JSX 渲染页面，vue 使用简单的模板
   - vue 比 react  运行更快

3. Vue：

   Vue是一套用于构建用户界面的渐进式框架

   ==Vue的核心==：

   允许采用简洁的模板语法来声明式的将数据渲染进DOM 系统

4. 基础：

   1. var vm = new Vue()；每个Vue 应用都是通过 Vue 函数创建一个新的 Vue 根实例开始的
   2. el:'#app'；==挂载点== 表示 Vue 实例接管了对 id=app 的元素的控制
   3. data：数据
   4. {{ msg }} ：模板中的文本插值，表示此处插入 msg 变量所存储的数据

5. data 数据的响应式：

   在代码中或控制台改变 vm.msg 的值，视图会重新渲染

   - 当一个 Vue 实例被创建时，它向 Vue 的响应式系统中加入了其 data 对象中能找到的所有属性

     当这些属性的值发生改变时，视图将会产生“响应”，即匹配更新为新的值

   - ==只有当实例被创建时 data 中存在的属性才是响应式的==

     如添加一个新属性，vm.b='hi' ，那么对 b 的改动不会触发任何视图更新

   - ==对于某些属性晚些时候才使用的话，可以先设置初始值==

6. Vue 指令：

   1. 

      - 指带有前缀 v- ,以表示它们是 Vue 提供的特殊特性

      - ==指令需要放在标签属性中使用==

      - demo：

        1. <div id="app" v-html="msg">
               将 msg 的值渲染在 div 内部
           </div>

        2. <div id="app" v-html="msg+'good' ">
               指令内部允许使用 js 表达式
           </div>

        3. <div id="app" v-text="msg">
               将 msg 的值渲染在 div 内部，不解析标签
           </div>

        4. <div id="app" v-bind:title="msg">
               元素 title 属性值 即为 msg 属性值
           </div>

        5. ```html
           <div id="app" :title="msg">
               :title 是v-bind：title 的简写
           </div>
           ```

   2. 条件渲染：

      v-if     v-else    v-show

      - demo:

        data:{

        ​	show:true,

        ​	current:'active'

        }

        ```html
        <div id="app">
           	<p v-if="show">红</p>  //show 属性为真 ，元素显示，否则不显示
            <p v-if="current=='active' ">红色</p>  // 可以用表达式
            <p v-else>绿色</p>  // 必须与v-if 紧邻， 当 v-if 为假时显示
            <p v-show="show">蓝色</p>  //show属性为真时，元素显示，否则不显示
        </div>
        ```


        ==v-if 不仅是不显示，而且 dom 不存在；v-show 隐藏（display：none），但 dom 存在==

   3. v-cloak 指令：

      - demo：

      - ```html
        <div id="app">
            <p v-if="show">红色</p>
            <p v-else v-cloak>绿色</p>
        </div>
        ```

      - 解析：

        当 show 为真时，绿色标签不显示，但实际上会先显示，随后 vue 使其隐藏

      - 解决办法：

        ==使用 v-cloak ==

   4. 列表渲染（v-for）：

      1. 遍历数组：

         color:['red','blue','green']

         ```html
         <ul>
             <li v-for="item in color">{{item}}</li> //item 为数组中每项元素（推荐使用这种）
             <li v-for="item of color">{{item}}</li> //等价于上面
             <li v-for="(item,index) in color">{{item}}===={{index}}</li> //元素值，索引值，括号中顺序不能反
         </ul>
         ```

      2. 遍历对象：

         ```javascript
         obj:{
         
         	name:"zs",
         
         	age:21,
         
         	sex:"男"
         
         }
         ```

         ```html
         <ul>
             <li v-for="item in obj">{{item}}</li>
             <li v-for="(value,key,index) in obj">{{value}}===={{key}}</li>
         </ul>
         ```




         注意：

         1. item 为 obj 每个属性对应的值
         2. value 等价于 item
         3. key：每个属性名
         4. index：每个属性的索引

7. key 值：

   - 当 vue.js 使用 v-for 正在更新已渲染过的元素列表时，它默认用==“就地复用”== 策略，

     如果数据项的顺序被改变， vue 将不会移动 dom 元素来匹配数据项的顺序，而是简单复用此处每个元素，并且确保它在特定索引下显示已被渲染过的每个元素

   - ==尽可能在使用 v-for 时提供 key== （除非便利输出的 dom 内容非常简单，或是刻意依赖默认行为以获取性能上的提升）

   - demo：

     data:{login:true}

     ```html
     <div id="app">
         <p v-if="login" :key="1"><input type="text" placeholder="请输入用户名" /></p>
         <p v-else :key="2"><input type="text" placeholder="请注册用户名" /></p>
     </div>
     ```




     ==不加 ：key 时，当在 input 框中输入值，再在控制台改变 login 属性值时，视图不会改变==

     ==加：key 之后，当在 input 框中输入值，再在控制台改变 login 属性值时，视图会更新==

8. 数组更新检测：

   1. 数组元素变化时想要更新视图，使用一下方法：

      - push()

      - pop()

      - shift()

      - unshift()

      - splice()

      - sort()

      - reverse()

      - ==由于 js 的限制，Vue 不能检测以下变动的数组==：

        1. 当利用索引直接设置一个项时：

           vm.items[1] = "x"  //不是响应式的

        2. 当修改数组的长度时：

           vm.items.length = 2; //不是响应式的

        3. ==此时，应用第二种方法  Vue.set==

   2. 更新视图并修改数组：

      vm.$set：该方法时全局方法 Vue.set 的一个别名

      1. 解决第一类问题：

         - Vue.set(vm.items,indexOfItem,newValue)
         - Vue.items.splice(indexOfItem,1,newValue)
         - vm.$set(vm.items,indexOfItem,newValue)

      2. 解决第二类问题：

         vm.items.splice(newLength)

9. 对象更新检测：

   1. 对象上如果更新数据想触发视图更新，必须使用如下方式：

      - Vue.set(obj,key,value)
      - vm.$set(obj,key,value);

   2. 下面这种方式不会触发视图更新：

      vm.obj.newkey = newValue;

10. v-model (双向数据绑定)

    - v-model 可进行双向数据绑定，表单元素值改变，则数据改变，反之同样

    - ==只能加给表单元素==

    - demo：

      data:{user:"zs"}

      ```html
      <div id="app">
          <input type="text" v-model="user" >
          <span>{{user}}</span>
      </div>
      ```

11. 事件绑定（接收参数） v-on

    1. demo:

       <button v-on:click="change("绿色)">改变颜色</button>

       ```javascript
       methods:{
       
       	change(params){
       
       		this.color=params;
       
       	}
       
       }
       ```

    2. 简写方法：

       <button @click="change()"></button>

    3. v-on + 修饰符

       - <input type="text"  @keyup.13="change" />  //按下键值为13（回车键）时触发
       - ==@click.stop=" "   ------组织冒泡==
       - ==@click.prevent=" " -------阻止浏览器默认行为==
       - ==在方法内部使用 this 可直接访问到数据对象的数据==

12. v-once:

    只渲染元素和组件一次，随后的重新渲染，元素 / 组件及其所有的子节点将被视为静态内容并跳过，这可以用于优化更新性能

    - 单个元素：

      <span v-once>Hello : {{msg}}</span>

    - 有子元素：

      ```html
      <div v-once>
          <h1>
              comment
          </h1>
          <p>
              {{msg}}
          </p>
      </div>
      ```






