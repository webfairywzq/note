01————node js 基础篇

1. 定义：

   ==Node.js是一个基于谷歌浏览器JavaScript 执行环境（V8引擎）建立的一个平台，让 JavaScript 可以脱离客户端浏览器运行，让 JavaScript 具有服务器语言的能力==

2. 分析 Node.js 的 HTTP 服务器：

   1. 第一行请求（require）Node.js 自带的 http 模块，并且把它赋值给 http 变量：

      // 引入模块

      var http = require("http");

   2. 接下来调用 http 莫开提供的函数：createServer ，这个函数会返回一个对象，这个对象有一个叫做 listen 的方法，这个方法有一个数值参数，制定这个 http 服务器监听的端口号：

      // 创建服务器

      ```javascript
      var server = http.createServer(function(req,res){
      	// req 请求对象  // res  响应对象
      	res.writeHead(200,{"content-type" : "text/html ; chartset=UTF-8"});
      	res.write("<h1>hello world</h1>");
      	res.end();
      });
      //启动服务器
      	server.listen(8000);
      ```

3. 总结：

   1. 传统 php：接收 HTTP 请求并提供 web 页面的需求
   2. 使用 node.js 时，我们不仅仅在实现一个应用，同时还实现了整个 HTTP 服务器，事实上，php 能实现的 nodejs 也能实现
   3. node.js 应用是由哪几部分组成：
      - ==引入 required（依赖）模块==：使用 ==require== 指令来载入 node.js 模块
      - ==创建服务器==：服务器可以监听客户端的请求，类似于 Apache、Nginx等 HTTP 服务器
      - ==接收请求与响应请求==：服务器很容易创建，客户端可以使用浏览器或终端发送 HTTP 请求，服务器接收请求后返回响应数据

