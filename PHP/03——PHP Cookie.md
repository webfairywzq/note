03——PHP Cookie

1. 用来识别用户（存储的是一些数据，都是以键值对的形式进行存储 key=value）

2. cookie 时存储于访问者的计算机中的变量（每当同一台计算机通过浏览器请求某个页面时，就会发送这个 cookie）

3. 浏览器允许每个域名所包含的 cookie 数：

   1. Microsoft 指出 IE8 增加 cookie 限制为每个域名 50 个（IE7 也允许）
   2. Firefox：每个域名 cookie 限制为 50 个
   3. Opera：每个域名 cookie 限制为 30 个
   4. Safari / Webkit：没有 cookie 限制
   5. ==如果 cookie 很多，则会使 header 大小超过服务器的处理的限制，会导致错误发生==

4. 属性：

   1. Expires：

      - 过期时间，定 cookie 的生命周期（具体值是过期日期）：

        1. 持久 cookie
        2. 会话cookie

      - 如果想让 cookie 的存在期限超过当前浏览器会话时间，就必须使用这个属性

        当过了到期日期时，浏览器就可以删除 cookie 文件，没有任何影响

        ==删除 cookie 可以设置 expires = -1==

        ```javascript
        var date = new Date();
        date.setTime(date.getTime() + 10000);
        document.cookie = 'userId=100;expires=' + date.toGMTstring();
        console.log(document.cookie);
        ```

   2. Path：

      - 路径，指定与 cookie 关联的 web 页；
      - 值 可以是一个目录，或是一个路径
      - 如果想让 /head/filters/ 和 /head/stories/ 共享 cookies 就要把 path 设置为：" /head "

   3. Domain：

      1. 域，指定关联的 web 服务器或域

      2. 默认情况下，一个主机创建的 cookie 在另一个主机下是不能被访问的，但可以通过 domain 参数来实现对其的控制

      3. ==指定访问主机名 一定要在域名下进去访问==

      4. ```javascript
         // 以 google 为例，实现跨主机访问：
         document.cookie = "name=value;domain=.google.com";
         ```

      5. setcookie：

         将 cookie 写到 客户端响应头信息中（在服务器端执行）

   4. Secure：

      - 安全，指定 cookie 的值通过网络如何在用户和 web 服务器之间传递
      - 值为 "secure" 或 为空

5. 注意：

   1. 浏览器端、服务器端都可以写入 cookie

   2. ==不同终端的 cookie 信息在任何情况下都不能共享==

   3. ==同一终端的不同浏览器的 cookie 信息不能共享==

   4. 服务器端写入（了解）：

      浏览器向服务器发送请求时，服务器会将少量的数据返回给浏览器（该数据以 set-cookie 消息头的形式返回给浏览器），浏览器会将这些数据存放到硬盘或者内存上，当浏览器下次再次访问服务器时，会将之前存放的数据发送给服务器（以 cookie 消息头的形式发送给服务器），通过这种方式，可以记录浏览器与服务器之间交互的数据，也就是状态

   5. cookie 跟域有关，当前页面只能访问存储在当前域名和父级域名（cookie 的域前面有" . " 的）下的 cookie