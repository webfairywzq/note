14——vue axios

1. axios 是一个基于 Promise 用于浏览器和 nodejs 的 HTTP 客户端

2. 特征：

   1. 从浏览器中创建 XMLHttpRequest

   2. 从 node.js 发出 http 请求

   3. 支持 Promise  API

   4. 拦截请求和响应

   5. 转换请求和相应数据

   6. 取消请求

   7. 自动转换 JSON 数据

   8. 客户端支持防止 CSRF / XSRF：

      CSRF：（Cross-site request forgery）跨站请求伪造 缩写为 CSRF 或 XSRF

      CSRF 通过伪装来自受信任用户的请求来利用受信任的网站

3. 语法：

   1. 

      ```javascript
      axios.get("url",{params:{key:value}})
      .then((res) => {
      	console.log(res.data);  //  数据
      })
      .catch(function(err){});
      ```

   2. 

      ```javascript
      axios.post("url",{key:value})
      .then((res) => {
      	console.log(res.data);
      })
      .catch(function(err){})
      ```

4. 拦截器（全局配置）：

   1. 添加请求拦截器

      ```javascript
      axios.interceptors.request.use(function(config){
      	//显示 loading
      	return config;
      })
      ```

   2. 添加响应拦截器

      ```javascript
      axios.interceptors.response.use(function(response){
      	//隐藏 loading
      	return  response;
      })
      ```

   3. 通常放在 vue 的 created 的钩子函数中