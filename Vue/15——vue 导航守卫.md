15——vue 导航守卫

参考网址：https://router.vuejs.org/zh/

1. 参数或查询的改变并不会触发进入 / 离开的导航守卫

2. 全局守卫：

   - 前置守卫：

     1. 当一个导航触发时，全局前置守卫按照创建顺序调用

     2. 每个守卫方法接收三个参数：

        router.beforeEach((to,from,next) => {})

        1. to：即将要进入的目标路由对象
        2. from：表示从哪个路由跳转过来的
        3. next：守卫可以通过 next 控制下一步的跳转（如果写 next() ，则表示直接跳转到 to 的位置

     3. 如果想要在路由对象上携带一些信息，可以使用 meta：

        ``` javascript
        {
            path:'/path',
            component:组件,
            meta:{
            	key:value        
            }
        }
        ```

     4. 从哪跳转登录后再返回原地址：

        // 设置 导航守卫：

        ```javascript
        router.beforeEach((to,from,next) => {
            //获取信息
            const login = localStorage.getItem('login');
            // 判断路由对象中的 matched 中是否有一个对象包含 meta
            if(to.matched.some(route => route.meta.auth)){ //判断是否需要验证
                if(login){
                    next();
                }else{
                    //跳转时需在 url 后添加一个 query 参数，参数值为要返回的 url 路径
                    next('/login?returnURL='+ to.path)；
                }
            }else{
                next();
            }
        })
        ```

     5. 对应的 methods 方法中实现功能：

        ```javascript
        login(){
            localStorage.setItem('login','wzq');
            //根据当前的 url 中的 query 参数，returnURL 进行路由的跳转
            const url = this.$route.query.returnURL;
            //利用 js 实现页面跳转操作
            this.$router.push(url);
        }
        ```

3. 生命式导航和编程式导航

   1. 声明式导航用在直接渲染到页面（ <router-link to='/url' >）

   2. 编程式导航用于在 js 中处理逻辑后需要进行页面跳转

   3. 声明式导航中的 to 怎么写，那么编程式导航中的参数就怎么写

      this.$router.push();

      ==this,$router 其实就是 router，vue 为了方便我们在组件中使用 router，才添加了 this.$router==

      1. this.$router.push();

         会进行页面跳转，==同时会在历史记录上留下记录==

      2. this.$router.replace();

         与 push 功能相同，==但是会替换当前页出现在历史记录中==

      3. this.$router.go(数字);

         表示距离当前页在历史记录上的页数

      4. this.$router.back();

         返回到上一页

      5. this.$router.forward();

         前进到下一页

      6. next 中参数写法与 push() 相同