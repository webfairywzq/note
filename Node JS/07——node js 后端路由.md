07———node js 后端路由

1. 路由：就是URL 到函数（相应的业务逻辑）的映射

   例：下面就是条路由：

   ​	/users ===> getAllUsers()

   ​	当访问 /users 时，会执行 getAllUsers() 函数（业务逻辑）

2. 服务器端路由（后端路由）

   - 后端路由多指 ==动态资源的请求==
   - 可以认为，所有 URL 的映射函数就是一个文件读取操作

3. 路由：

   我们要为路由提供请求的 URL 和其他需要的 GET 及 POST 参数，因此我们需要查看 HTTP 请求，从中提取出请求的 URL 以及 GET/POST 参数

   ==URL模块：解析 url：==

   console.log(url.parse(req.url));