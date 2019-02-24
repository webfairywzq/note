04——vue 生命周期

1. 每个 Vue 实例在被创建时都要经过一系列初始化过程

   如：需要设置数据监听、编译模板、将实例挂载到 Dom 并在数据变化时更新 Dom，在这个过程中也会运行一些叫”生命周期钩子“的函数

2. 生命周期函数就是 Vue 实例在某一个时间点会自动执行的函数

3. demo：

   ```html
   <div id="app">
       {{msg}}
       <span @click="test">span</span>
   </div>
   ```


   data:{

   ​	msg:'hello'

   }

   1. template:'<h2>{{msg}}</h2>'， ==优先级比 el 高，会使模板改变，换成 template==

   2. beforeCreate(){

      ​	console.log(this.msg);  //  undefined

      ​	==vm 实例已经存在，但是 data 数据对象中的属性还没有被注入==

      ​	==此时 vue 才开始初始化，还没有将 data 对象中的属性注入到实例中==

      }，

   3. created(){

      ​	console.log("created",this.msg,this.$el);  //  created hello  undefined

      ​	==这个阶段数据对象中的属性已经注入到 vm 实例中==

      ​	==ajax 获取通常在这个阶段执行，获取数据之后更新 data 对象中的值==

      ​	==初始化过程==

      ​	==挂载阶段还没开始，$el 属性目前不可见==

      }，

   4. beforeMount(){

      ​	console.log("beforeMount",this,$el);  //  beforeMount  <div id="app">.....

      ​	==初始化模板过程==

      ​	==在挂载开始之前被调用，相关的 render 函数首次被调用==

      }，

   5. mounted(){

      ​	console.log("mounted",this.$el);  //  mounted  <div id="app">.....

      ​	==在这个阶段模板编译成功，并且数据已经挂载到模板上了==

      ​	==如果想要操作 Dom ，在这个阶段执行==

      }，

   6. beforeUpdate(){

      ​	console.log("beforeUpdate",this.$el.innerHTML); 

      ​	==数据更新之前执行的钩子函数==

      }，

   7. updated(){

      ​	console.log("updated",this.$el.innerHTML);

      ​	==数据更新之后执行的钩子函数==

      }，

   8. beforeDestory(){

      ​	console.log("beforeDestory",this.$el);

      ​	==实例销毁之前调用==

      ​	==在这一步，实例仍然完全可用==

      }，

   9. destoryed(){

      ​	console.log("destoryed",this.$el);

      ​	==Vue 实例销毁后调用==

      ​	==它的响应式系统不存在了==（Vue 实例指示的所有东西都会解绑，所有的事件监听器会被移除，所有的子实例也会被销毁）

      }

   10. 补充：

       - nextTick():

         比如：当接收数据后，需要重新调用刷新该界面数据

         vue的api中有一个nextTick()，是==将回调函数延迟在下一次dom更新数据后调==，简单的理解是：==当数据有更新，在dom中渲染后，自动执行该函数==

         ```javascript
         //两种写法:
         
         1.//推荐使用这种写法
         this.$nextTick( () => {
             //这里的代码会等待 DOM 更新完成后执行
         })
         
         2.//还可以写成：
          Vue.nextTick( () => {})
         
         //例如： 在 Vue 生命周期的 created() 钩子函数进行的 DOM 操作一定要放在 Vue.nextTick() 回调函数中，理由：
         在 created() 钩子函数执行的时候 DOM 并未进行任何渲染，所以一定要将 js 代码放在 Vue.nextTick() 的回调函数中
         ```
