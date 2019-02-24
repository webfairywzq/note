07——vue 组件通信

1. 父组件向子组件传值：

   各司其职：父组件传值，子组件没接收 -----------不报错；

   ​		  父组件没传值，子组件接收了---------不报错

   - ==在父组件的模板中向子组件的标签中添加属性==
   - ==子组件通过 props 来接收==
   - ==不要在子组件内部直接改变 props 的值==
   - 只要子组件标签上有属性，那么在子组件中就一定能接收
   - 数据是由父组件传向子组件的

   - 具体步骤：

     1. 父组件：传数据：

        找到父组件模板中的子组件标签

        在子组件标签上添加 属性=属性值

        prop名字 = "值"

        <子标签 a="1"></子标签>

     2. 子组件：接收数据

        找到子组件的组件配置对象

        添加 props 属性

         props ：['prop名字1','prop名字2']

         props：{   //  推荐使用这种方法 

        ​	（props 定义要尽量详细，至少要定义类型）

        ​	prop名字1: 类型

        }

        prop 当做 data 使用即可

2. 子组件向父组件传值：

   只要组件标签上绑定了事件，那么一定是自定义事件

   如果想要在组件上绑定原生事件：@click.native=‘函数’

   - 具体步骤：

     1. 子组件：触发：

        需要在子组件中的对应元素上绑定原生事件

        在组件中的methods 里添加对应的事件函数

        在对应的事件函数中触发自定义事件

     2. 父组件 ：接收：

        找到父组件模板中的子组件标签

        在子组件标签上绑定自定义事件

        ​	<子组件标签 @自定义事件="父methods中函数"></子组件标签>

        在父组件 methods 中添加函数

        methods: {

   ​                函数 (data) {

   ​                  data就是子组件中传递过来的数据

   ​                }

   ​              }

3. 非父子通信：

   定义一个全局的空实例作为 ==中央事件总线==

   （需要一个公共的实例对象）

   const bus = new Vue()

   1. 需要传值的组件中：

      bus.$emit ('自定义事件', 数据)

   2. 需要接收值的组件中：

      bus.$on('自定义事件', data => {

      ​	data 就是上面的数据;

      })

   3. 补充：

      每个 Vue 实例都实现了事件接口（Events interface）,即：

      1. 使用 $on(eventName)   监听事件
      2. 使用 $emit(eventName)  触发事件
      3. 在 vue 生命周期中，beforeCreate 之前已经实现了事件接口（即 vue 的事件系统构建完毕），所以在这个阶段可以注册事件
      4. 在事件处理函数中使用箭头函数可以得到子组件中的数据对象， this 指向子组件，由于函数的调用是在触发时才调用，而这个时候子组件早已经初始化完毕，所以可以直接调用

4. v-bind的修饰符：

   1. .sync :同步

   2. 父组件向子组件中传递数据，子组件的操作也可以修改这个数据，同时==子组件仅操作该数据时==：组件上的自定义事件函数中的 $event 是触发该自定义事件时的第二个参数（也就是子组件传递过来的数据）

   3. 语法：

      ```javascript
      <组件标签 :子组件prop.sync="父组件data"></组件标签>
      相当于：
      <组件标签 :子组件prop="父组件data" @update:子组件prop="父组件data= $event"></组件标签>
      那么子组件中一定有 this.$emit('update:prop名字','数据');// 这个数据就是未来的 $event
      ```

   4. demo：

      1. 正常的子父通信

         ```html
         <div id="app">
             <child :msg="msg" @update:msg="getMsg"></child>
         </div>
         ```

         ```javascript
         const child = {
             template:`
         		<div>
         			{{msg}}
         			<button @click="changeMsg>按钮</button>
         		</div>
         	`,
             methods:{
                 changeMsg(){
                     this.$emit('update:msg','子组件中修改后的msg');
                 }
             }
         }
         
         const app = new Vue({
             el:'#app',
             components:{
                 child
             },
             data:{
                 msg:'父组件中的数据'
             },
             methods:{
                 getMsg(msg){
                     this.msg = msg;
                 }
             }
         })
         ```

      2. .sync 修饰符：

         ```html
         <div id="app">
             1. .sync
             <child :msg.sync="msg"></child>
             2.  等价于上面
             <child :msg="msg" @update:msg="msg=$event"></child>  
             // 事件函数中的 $event 是触发该自定义事件时的第二个参数（也就是子组件传递过来的数据）
         </div>
         ```

         ```javascript
         const child = {
             template:`
         		<div>
         			{{msg}}
         			<button @click="changeMsg>按钮</button>
         		</div>
         	`,
             methods:{
                 changeMsg(){
                     this.$emit('update:msg','子组件中修改后的msg');
                 }
             }
         }
         
         const app = new Vue({
             el:'#app',
             components:{
                 child
             },
             data:{
                 msg:'父组件中的数据'
             }
         })
         ```
