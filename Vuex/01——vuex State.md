01——vuex State

1. state 是数据

2. vuex 中有一个构造函数是 store

   想要创建 vuex 实例就需要 new 这个 store

   ```javascript
   const store = new Vuex.Store({
       state:{
           // 相关的数据，写在 state 中即可
           msg:"Hello Vuex!"
       }
   })
   ```

3. 将 store 放入 vue 的配置对象后，该 store 实例会注入到跟组件下的所有子组件中

4. 在获取 state 中的值时，在组件中写 computed

   ```javascript
   computed:{
       数据名 () {
           return this.$store.state.数据名
       }
   }
   
   // demo:
   const store = new Vuex.Store({
       state:{
           // 相关的数据，写在 state 中即可
           msg:"Hello Vuex!"
       } 
   })
   
   const app = new Vue({
       el:"#app",
       store,
       // 如果想要在组件中获取数据，建议放在 computed 中
       computed:{
           msg () {
               return this.$store.state.msg
           }
       },
       created () {
           console.log(this.$store);
           console.log(store);
       }
   })
   ```
