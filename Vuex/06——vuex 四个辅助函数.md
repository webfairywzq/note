06——vuex 四个辅助函数

mapState，mapGetters，mapMutations，mapActions

1. 引入辅助函数

   ```javascript
   import {mapState,mapGetters,mapMutations,mapActions} from 'vuex'
   
   // 需要谁引入谁，不需要全部都引入，但就算引入单个也需加括号
   import {mapState} from 'vuex'
   ```

2. mapState 和 mapGetters 写在 computed 中，用于获取  state 中的数据

3. mapMutations 和 mapActions 写在 methods 中，用于修改数据

4. 语法：

   ```html
   <div id="app">
       {{msg}}
       {{m}}
       {{getter名字}}
       {{数据别名}}
   </div>
   ```

   1. mapState 、mapGetters ：写在 computed 中

      ```javascript
      computed:{
          // 1. mapState
        	   // 没有模块时：
              ...mapState(['msg'])
              //相当于：
              msg () {
                  return this.$store.state.msg
              }
      
              ...mapState({
                  m:'msg'  // 改名字
              })
              // 相当于
              m () {
                  return this.$store.state.msg
              }
       	 // 有模块时：
              ...mapState('模块名',{
                  自定义数据名:'state数据名'
              })   或者
              ...mapState('模块名',['state数据名1','state数据名2'])
         // 2. mapGetters
         	 // 没有模块时：
              ...mapGetters(['getter名字'])
                  ...mapGetters({
                      数据别名:'getter名字'
               })
           // 有模块时：
              ...mapGetters('模块名',{
                  自定义数据名:'getter数据名'
              })
          	...mapGetters('模块名',['getter数据名1','getter数据名2'])
      }
      ```

   2. mapMutations、mapActions ：写在 methods 中

      ```javascript
      methods:{
        // 1. mapMutations
          ...mapMutations(['mutation名字'])
          // 相当于：
          mutation名字 () {
              this.$store.commit('mutation名字')
          }
          
          ...mapMutations({
              '别名':'mutation名字'
          })
          // 相当于：
          别名 () {
              this.$store.commit('mutation名字')
          }
          
       // 2. mapActions
          ...mapActions(['action名字'])
          // 相当于：
          action名字 () {
              this.$store.dispatch('action名字')
          }
          
          ...mapActions({
              '别名':'action名字'
          })
          // 相当于：
          别名 () {
              this.$store.dispatch('action名字')
          }
      }
      
      // mapMutations 、mapActions 只适合： 某个函数中只有分发 action 或提交 mutation 的操作
      例如：
      函数 () {
          this.$store.dispatch('action名');
          // 没有其他代码
      }
      函数 () {
          this.$store.commit('mutation名');
          // 没有其他代码
      }
      ```

5. 使用常量替代 Mutation 事件类型

   将这些常量放在单独的文件中可以让代码合作者对整个 app 包含的 mutation 一目了然

   ```javascript
   //1. /store/mutation-types.js
   export const MUTATION_NAME1 = "otherMutation1"
   //2. /store/mutation.js
   import {MUTATION_NAME1} from './mutation-type'
   export default {
       [MUTATION_NAME1] () {
           //执行的代码
       }
   }
   ```
