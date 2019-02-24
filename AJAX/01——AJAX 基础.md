01——AJAX 基础

1. AJAX = Asynchronous JavaScript and XML （异步的 JavaScript 和 XML）

   XML ：==可扩展标记语言==

2. 通过在后台与服务器进行少量数据交换，AJAX 可以使用网页实现异步更新，意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新

   （传统网页（不使用 AJAX），如需更新内容，必需重载整个网页）

   XMLHttpRequest 是 AJAX 的基础

3. 创建 XMLHttpRequest 对象：

   ```javascript
   var xhr; //处理兼容
   if(window.XMLHttpRequest){
       //code for IE7+,Firefox,Chrome,Opera,Safari
       xhr = new XMLHttpRequest();
   }else{
       //code for IE6 IE5
       xhr = new ActiveXObject("Microsoft.XMLHttp");
   }
   ```

4. open() 方法：

   1. 作用：

      创建一个新的 http 请求，并指定此请求的方法、URL 以及验证信息

   2. 参数：

      - 第一个参数：

        请求方式：（get / post）

      - 第二个参数：

        请求的 URL

        eg1：xhr.open("get","getData.php?user=mike&pwd=123",true);

        eg2：xhr.open("post","getData.php",true);

      - 第三个参数：

        请求同步进行还是异步进行（true 表示异步）

        ==调用 open() 其实只是设置好了参数，仍未发起请求

5. send() 方法：

   1. 作用：调用了 send 方法后才会发起请求

   2. eg：

      ```javascript
      1.// 以 post 方式传递时
       xhr.setRequestHeader("Content-type","application/x-www-from-urlencoded;charset=UTF-8");// 设置请求头（用 post 方法时，必须将这段代码放在 xhr.send() 之前）
       xhr.send("user="+username+" &pwd="+pwd);
      2.// 以 get 方式传递时
       xhr.send();
      ```

6. xhr.abort() 方法：

   ==停止当前请求==

   eg：

   ```javascript
   var timmer = setTimeout(function(){
       xhr.abort();
       console.log("服务器忙");
   },5000);
   // 在对应请求的代码中清除计时器
   // 若 5s 还未请求结束，则放弃此次请求，否则清除计时器
   ```

7. XMLHttpRequest 对象的属性：

   1. onreadystatechange（事件属性）

      存储函数（或函数名），每当 readyState 属性改变时，就调用该函数

   2. readyState：

      存在 XMLHttpRequest 的状态（0-4）

      - 0：请求未初始化（还没有调用 open 方法）
      - 1：服务器连接已建立（open 方法已被调用）
      - 2：请求已接收（send 已被调用）
      - 3：交互中（服务器正在发送响应）
      - 4：请求已完成，且响应已就绪（响应发送完毕）

   3. status：

      1. 200："OK"
      2. 404：未找到页面

   4. xhr.responseText 属性：

      1. 获取服务器响应数据；
      2. responseText 返回字符串形式的响应

8. 创建回调函数：

   ```javascript
   // 监听服务器的响应状态，当条件成立，获取数据
   xhr.onreadystatechange = function(){
       if(xhr.readyState == 4 && xhr.status == 200){
           // 执行的代码;
       }
   }
   ```

9. 补充：

   1. 同步请求（false）：

      即是当前发出请求后，浏览器什么都不能做，必须等到请求完成，返回数据之后，才会执行后续的代码（相当于排队，不能插队）

   2. 异步请求（true）：

      当发出请求的同时，浏览器可以继续做任何事，Ajax 发送请求并不会影响页面的加载与用户的操作（平行线，互不影响）

10. AJAX 执行基本流程：

    1. 对象初始化

    2. 发送请求

    3. 服务器接收

    4. 服务器返回

    5. 客户端接收

    6. 修改客户端页面内容

       ==过程时 异步的==