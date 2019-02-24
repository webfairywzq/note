08——vuex 模块---getters

1. 模块中的 getter 和 rootGetter 会放在同一个对象中 (this.$store.getters) ，所以尽量不要用相同的名字

2. 解决上述问题：

   ==使用命名空间： namespaced：true==

   ```javascript
   // 为什么会有命名空间？
   	// 因为 getter 添加不管是哪个模块的，都会被直接添加到 this.$store.getters 中，如果两个getter 命名相同，需要给对应模块添加 namespaced:true
   对应的模块的 getter 就会变成 "模块名/getter名"，全局的 getter 不会有任何变化
   	// 想要获取到对应的 getter
   		this.$store.getters['模块名/getter名']
   // 语法：
   modules:{
       moduleA:{
           getters:{
               getter名 (state,getters,rootState,rootGetters) {
                   // state、getters 表示当前模块的 state 和 getters
                   // rootState 、rootGetters 表示全局中的 state 和 getters 其中包括了各个模块的 state 和 getters
               }
           }
       }
   }
   ```

3. demo：

   ```javascript
   const store = new Vuex.Store({
       getters:{
           getterRoot () {
               return "rootGetters 中的 getter"
           }  
       },
        modules:{
           moduleA:{
               namespaced:true,
               getters:{
                   getterModuleA (state,getters,rootState,rootGetters) {
                       // 加上了 namespaced：true 模块名可以与 rootGetters 中的 getter 同名
   
                       console.log(rootState);
                       console.log(rootGetters);
                       return 'moduleA 中的 getter'
                   }
               }
           },
           moduleB:{
               namespaced:true,
               getters:{
                   getterModuleB () {
                       return "moduleB 中的getter"
                   }
               }
           }
       }
   })
   
   const app = new Vue({
       el:"#app",
       store,
       created () {
           console.log(this.$store.getters["moduleB/getterModuleB"]);
       }
   })
   ```
