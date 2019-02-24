02——vuex Getter

1. 从 state 中 或 其他 getter 中分出其他数据（分类）

2. 具体：

   1. ==getters 中的所有 getter 都是函数==

   2. 每个 getter 中都有 第一个参数 state

   3. 每个 getter 中都有 第二个参数 getters

   4. getter 返回的除了数据之外还可以返回函数，这样可以通过传参的方式，得到对应的数据

      ```javascript
      1.直接返回数据
      computed:{
          数据名 () {
              return this.$store.getters.getter名
          }
      }
      2.返回的是函数
      computed:{
          数据名 () {
              return this.$store.getters.getter名(参数)
          }
      }
      ```

   5. demo：

      ```javascript
      const store = new Vuex.Store({
          state:{
              stus:[
                  {
                      name:"小明",
                      sex:"男",
                      age:18
                  },{
                      name:"张三",
                      sex:"男",
                      age:23
                  },{
                      name:"王五",
                      sex:"女",
                      age:16
                  }
              ]
          },
          getters:{
              // 得到男生 
              boys(state){
                  return state.stus.filter(stu => stu.sex === '男')
              }
              // 得到 男生的长度
              boysLength(state,getters){
          		return getter.boys.length
      		}
              ageGtNum(state){
          		//过滤出年龄大于等于 18 的
          		// return state.stus.filter(stu => stu.age >=18) 
          		// 传参，过滤出 年龄大于等于 传入数据 的
          		return  state.stus.filter(stu => stu.age >= num)
      		}
          }
      })
      
      const app = new Vue({
          el:"#app",
          store,
          computed:{
              boys () {
                  return this.$store.getters.boys
              },
              boysLength () {
                  return this.$store.getters.boysLength
              },
              stus () {
                  return this.$store.getters.ageGtNum(22)
              }
          }
      })
      ```

      ```html
      <div id="app">
          {{boys}}
          {{boysLength}}
          <br>
          {{stus}}
      </div>
      ```
