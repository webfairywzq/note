06——vue 组件

1. 为什么学习组件？

   任何一个应用都是由小组件构成的，一个个组件构成的组件树就构成了一个大型的应用

2. 组件（component）：

   是 Vue.js 最强大的功能之一，可以扩展 HTML 元素，封装可重用的代码

   （更高层面来说，组件就是自定义元素，vue.js 的编译器为它添加特殊功能）

3. 两种注册组件类型：

   - 全局注册
   - 局部注册

4. 全局注册组件：

   ```javascript
   const com={
   	template:`
   		<div></div>    // ==只能有一个根元素==
   	`
   }
   Vue.component('自定义组件名'，com);
   
   // 因为组件时可复用的 Vue 实例，所以它们与 new Vue 接收相同的选项，如：data，computed，watch，methods及生命周期钩子等，例外是像 el 这样的根实例
   
   // 可以将组件任意次数的复用
   
   // 一个组件的 data 选项必须是一个函数，因此每个实例可以维护一份被返回对象的独立的拷贝
   ```

5. 局部注册：

   ```javascript
   const buttonCounter = {
   	template:`
   		<div> <h2> 内容</h2><div>
   	`
   }
   
   const vm = new Vue({
   	el:"#app",
       components:{
               buttonCounter 或
               buttonCounter:buttonCounter
           }
   })
   ```
