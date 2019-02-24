18——vue 递归获取对应权限的路由

1. 路由权限验证原理：

   ![路由权限验证原理](E:\wzq\笔记(电子版)\Vue\路由权限验证原理.png)

2. 分析：

   1. 有两个路由表：
      1. routes： (创建vue-router 路由实例的配置项，用来配置多个 route 路由对象)

         ```javascript
         const routes = [];
         const router = new Router({
             routes
         })
         ```

      2. asyncRoutes：未来根据登录的用户动态的添加到对应的路由表中的路由表（这个路由表需要经过筛选）

         ```javascript
         const asyncRoutes = [
             {
                 path:'/',
                 children:[
                     {
                         path:''
                     },{
                         path:'a',
                         meta:{
                             roles:['a']
                         }
                     }
                 ]
             }
         ]
         ```

   2. 判断当前的用户是否有该路由的权限：

      ```javascript
      const user = [
          role:['a']
      ]
      routes.filter(route => route.meta.roles.includes(user.role))
      // 路由本身需要有对应的权限
      // roles : 是用户的权限表,[]-----可以有多种权限
      // route : 是对应的路由配置中的路由对象
      
      // demo：
      roles:['a','b']
      route.meta.roles:['c']
      那么：
      roles 会被循环两次：
      	// 第一次：role 是 'a'
      		判断 a 是否在 route.meta.roles 中
          // 第二次：role 是 'b'
               判断 b 是否在 route.meta.roles 中
          // 最终 some 的结果为 false
      ```

3. 封装 递归函数：

   1. 封装一个函数 去验证某个用户的权限是否可以使用某个路由

      ```javascript
      function hasPermission(roles,route){
          // 如果路由上有 meta，并且 meta 中有 roles，那么我们就需要判断权限
          if(route.meta && route.meta.roles){
              // 判断当前的用户是否拥有访问当前路由的权限
              return roles.some(role => route.meta.roles.indexOf(role) >= 0)
              // 或者
              return roles.some(role => route.meta.roles.includes(role))
          }else{
              // 如果没有 meta 属性，则直接让他通过
              return true
          }
      }
      ```

   2. 封装函数筛选出 asyncRoutes 里符合对应用户权限的路由表

      ```javascript
      function filterAsyncRouter(routes,roles){
          const accessedRoutes = routes.filter(route => {
              // 判断当前路由是否符合权限
              if(hasPermission(roles,route)){
                  // 判断符合条件的路由是否包含子路由
                  if(route.children && route.children.length){
                      // 再对子路由进行筛选，并将筛选出的数组替换原本的 children
                      route.children = filterAsyncRouter(route.children,roles);
                  }
                  return true;
              }
          })
      }
      ```

4. 完整案例参考 文件夹 wzq 下的 vuex 的 auth 例子