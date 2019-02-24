09——vuex 模块---mutations-actions

1. mutations：

   与 getters 相同，添加 namespaced 之后会给对应的 mutation 添加模块名 变成："模块名/mutation 名"

   action 触发 mutation时 ：

   ​	commit('模块名/mutation名'，数据)

   ​	

   ```javascript
   // 模块中的 mutation：
   mutation (state,载荷) {
       // 没有变化
   }
   ```

2. actions：

   与 getters 相同，添加 namespaced 之后会给对应的 action 添加模块名 变成："模块名/action名"

   当通过 dispatch 触发 action 时 ：

   ​	dispatch('模块名/action名',数据)

   ```javascript
   // 模块中的 action：
   action ({commit},数据) {
       // 模块中的 action 里的 commit 只能提交当前模块中的 mutation
   }
   ```

3.  // 模块中的 action 里的 commit 只能提交当前模块中的 mutation：

   ```html
   <div id="app">
       {{$store.state.msg}}
       <br>
       <button @click="handler2">改变 root 中的 msg</button>
       <hr>
       {{$store.state.moduleA.msg}}
       <br>
       <button @click="handler1">改变 moduleA 中的 msg</button>
   </div>
   ```

   ```javascript
   const store = new Vuex.Store({
       state:{
           msg:"rootState 中的值"
       },
       modules:{
           moduleA:{
               namespaced:true,
               state:{
                   msg:"moduleA 中的 msg"
               },
               mutations:{
                   setMsg (state) {
                       state.msg = 'moduleA 改变 moduleA 中的 msg'
                   }  
               },
               actions:{
                   // 这样只能改变对应模块 state 中 msg 的值
                   setMsg ({commit}) {
                       commit('setMsg');
                   }
                   // 加入第三个参数{root：true} 就可以改变 rootState或其他模块 中 msg 的值
                   setMsg ({commit}) {
               		commit('setMsg',null,{root:true})
           		   }
               }
           }
       }
   })
   
   const app = new Vue({
       el:"#app",
       store,
       methods:{
           handler1 () {
               this.$store.dispatch('moduleA/setMsg');
           },
           handler2 () {
               // 点击第一个按钮想通过 moduleA 中的 mutation 改变 rootState 中 msg 的值
               this.$store.dispatch('moduleA/setMsg');
           }
       }
   })
   ```
