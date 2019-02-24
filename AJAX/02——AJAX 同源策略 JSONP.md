02——AJAX 同源策略 JSONP

为什么  AJAX 有跨域问题呢？ ----------- 同源策略

1. 同源策略：

   在 javascript 中，有一个很重要的安全性限制，被称为"Same-Origin Policy" （同源策略）

   这一策略对 JavaScript 代码通过 ajax 能够访问的页面内容做了很重要的限制，即（JavaScript 通过 AJAX 只能访问与包含它的文档在同一域名下的数据）

2. 同源策略的优 / 缺 点：

   1. 优点：

      安全性相对较高

   2. 缺点：

      当进行较深入的前端编程的时候，不可避免地需要进行跨域操作

   3. 可跨域请求的标签：

      ```javascript
      1.<script src=""></script>
      2.<img src="" >
      3.<ifram src="" >
      ```

   4. hosts 文件地址： C:\Windows\System32\driver\etc\hosts

3. 如何解决同源策略的问题：

   ```javascript
   1.跨域资源共享（CORS)
    // 同域名下面的 AJAX 接口做一个代理（在后端页面加入允许 AJAX 访问数据的指令）
    // 加在 php 处理页面的第一行：
    header("Access-Control-Allow-Origin:*");
    // * 代表允许跨域的文件
   2.JSONP :
   // 在 web 页面中插入动态脚本元素，该页面源指向其他域中的 url 并且在自身脚本中获取数据（即利用在页面中创建 <script> 节点的方法向不同域提交 HTTP 请求），这种技术称为 JSONP
   ```

4. JSONP 和 JSON 的区别

   ```javascript
   1.JSON：
   	// JSON 是一种基于文本的数据交换方式，或者叫做数据描述格式
   	// JSON 只有两种数据格式：
   		1.大括号 {}（对象）
            2.数组 []
   2.JSONP：
   	// JSONP （JSON with Padding）是一个非官方的协议，主要解决跨域问题
   	// 在客户端事先定义号一个处理函数
   	// 通过 script 标签的 src 属性发起一个跨域的请求
   	// 目标文件会以 函数调用的形式 传回数据，触发本地处理函数的执行，数据是以函数参数的形式传递回来的
   	（它允许在服务器端集成 script tags 返回至客户端，通过 javascript callback 的形式实现跨域访问
   ```

5. JSONP 基本原理：

   ==动态==添加一个 <script> 标签，==（而 script 标签 的 src 属性 时没有跨域限制的）==

   JSONP 执行过程： 

   ```javascript
   // 以 JSONP 接口 http://www.b.com/search.html?jsonp=jsonpCallback 为例
   1.// 首先在客户端注册一个 callback（回调函数），然后将 callback 的名字传给服务器
   2.// 服务器先生成 json 数据，然后 以 JavaScript 语法的方式，生成一个 function，function 的名字就是传递上来的参数 jsonp 的值，function 的参数为服务器生成好的 json 数据，然后用该语法写好的内容返回给客户端（语法：callback(json数据))
   3.// 客户端浏览器，解析 script 标签，并执行返回的 javascript 文档，此时数据作为参数，传入到了客户端预先定义好的 callback 函数（动态执行回调函数）
   ```

6. 补充：

   - 字符串编码函数：
     1. escape
     2. encodeURI
     3. encodeURIComponent
   - 对应的解码函数：
     1. unescape
     2. decodeURI
     3. decodeURIComponent

