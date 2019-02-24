03——vuex Mutation

1. 修改 state 只能用 mutation 去进行修改

2. 语法：

   ```javascript
   1.
   mutations:{
       mutation(state){
           // 因为 mutation 要修改 state，所以它的第一个参数为 state
           // mutation 想要被调用，需要在一些地方调用 this.$store.commit('mutation')
       }
   }
   2.触发 mutation
   store.commit('mutation');
   3.大部分情况我们需要给 mutation 提交数据
   	store.commit('mutation',数据)
     所以，mutation 中第二个参数就是 commit 过来的数据
     mutations:{
         mutation(state,payload){
             // payload 就是 commit 过来的数据
         }
     }
   ```

3. demo：

   ```javascript
   const store = new Vuex.Store({
       state:{
           count:1
       },
       mutations:{
           add(state){
               state.count++;
           },
           addn(state,num){
               console.log(num);
               state.count += num;
           }
       }
   })
   
   const app = new Vue({
       el:"#app",
       store,
       computed:{
           count(){
               return this.$store.state.count
           }
       },
       methods:{
           add(){
               // 提交 mutation
               this.$store.commit('add');
           },
           addn(){
               // 生成一个随机数
               const num = Math.floor(Math.Random() * 10) + 1;
               1.正常方式
               this.$store.commit('addn',num);
               2.可以传对象
               this.$store.commit({
                   type:'addn',
                   num
               })
           }
       }
   })
   ```

   ```html
   <div id="app">
       {{count}}
       <button @click="add">+1</button>
       <button @click="addn">+n</button>
   </div>
   ```
