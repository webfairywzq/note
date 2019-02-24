16——vue Token验证

1. 设置前端路由跳转：

   ```javascript
   router.beforeEach((to,from,next) => {
       if(to.matched.some(route => route.meta.auth)){
           //判断 token 是否存在，如果存在则正常跳转
           if(localStorage.getItem('token')){
               next();
           }else{
               next('/login');
           }
       }else{
           next();
       }
   })
   ```

2. 登录成功，将 token 存储：

   ```javascript
   login(){
       //发起请求登录
       axios.post('/user/login',this.user).then(res => {
           console.log(res.data);
           //接收到 token 后将 token 存储到 localStorage
           //前缀 “Bearer” 必须要加
           loclStorage.setItem('token',"Bearer "+res.data.res.token);
       })
   }
   ```

3. 设置请求拦截器：

   ==只要有 token 就让每次请求都携带 token==

   ```javascript
   //设置请求拦截器
   axios.interceptors.request.use(config => {
       console.log(config);
       const token = localStorage.getItem('token');
       if(token){
           //将获取到的 token 设置给 headers 中的 Authorization
           config.headers.Authorization = token;
       }
       //if 语句等价于：
      	token ? config.headers.Authorization = token : null;
       
       return config;
   })
   ```

4. 设置响应拦截器：

   ==对响应结果进行处理， token 出现问题，返回一定是 401==

   ```javascript
   //设置响应拦截器
   axios.interceptors.response.use(res => {
       //对结果进行处理
       if(res.data.res_code === 401){
           //跳转登录
           router.replace('/login');
           //删除 token 
           localStorage.removeItem('token');
       }
       
       return res;
   },err => {
       //如果是正常接口，会走 err 这里，err.response,status 值为401 ，进行跳转及删除 token 的操作
       （此案例特殊，因为后台接口设置）
   })
   ```
