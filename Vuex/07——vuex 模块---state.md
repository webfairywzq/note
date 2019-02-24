07——vuex 模块---state

1. 模块中的 state 会变成 rootState 的一个属性，属性名为模块名  （在demo 中打印一下 console.log(this.$store.state) 看一下）,state 不会有任何变化

2. 语法：

   ```javascript
   // rootState
   this.$store.state.xxx
   // 模块中的 state
   this.$store.state.模块名.xxx
   ```

3. demo:

   ```javascript
   const store = new Vuex.Store({
       state:{
           msg:'rootState 中的 msg'
       },
       modules:{
           moduleA:{
               state:{
                   msg:'moduleA 的 msg'
               }
           },
           moduleB:{
               state:{
                   msg:'moduleB 的 msg'
               }
           }
       }
   })
   
   const app = new Vue({
       el:"#app",
       store,
       created(){
           console.log(this.$store.state);
           console.log(this.$store.state.msg);
           console.log(this.$store.state.moduleA.msg);
           console.log(this.$store.state.moduleB.msg);
       }
   })
   ```


