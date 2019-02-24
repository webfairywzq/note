04——vuex Action

1. action 中就是专门完成异步请求的

2. 发起请求，请求成功后 commit(mutation,请求结果) 将数据发送给 mutation

3. demo：

   ```javascript
   const store = new Vuex.Store({
       state:{
           msg:''
       },
       mutations:{
           setMag(state,msg){
               state.msg = msg;
           }
       },
       actions:{
           //两种写法
           // 1.正常写法
           getMsg(context,payload){
               // context 拥有和 store 完全一样的属性和方法
               setTimeout(() => {
                   const msg ='Hello Vuex!';
                   // 将请求到的 msg 提交给 mutation
                   context.commit('setMsg',msg);
               },1000)
           },
           // 2. 解构 {commit}
           getMsg({commit},payload){
               setTimeout(() => {
                   const msg = 'Hello Vuex!';
                   commit('setMsg',msg)
               },1000)
           }
       }
   })
   
   const app = new Vue({
       el:"#app",
       store,
       computed:{
           msg(){
               return this.$store.state.msg
           }
       },
       created(){
           // 触发 action
           this.$store.state.dispatch('getMsg',1)
       }
   })
   ```
