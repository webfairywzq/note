02——PHP Session

1. session 变量存储单一的用户信息，并且对于应用程序中的所有页面都是可用的

2. session 的工作机制：

   为每个访客创建一个唯一的 id（UID），并基于这个 UID 来存储变量

3. 存储 session：

   ```javascript
   session_start(); // 存储 session 数据 ======必须放在 <html> 标签之前
   $_SESSION["views"]=1；
   ```

4. 销毁 session：

   1. unset()：

      用于释放指定的 session 变量

      unset($_SESSION['views'])；

   2. session_destroy()：

      彻底销毁 session

5. cookie 和 session 的区别：

   ```javascript
   1.// cookie 是保留在客户端的，每次发出页面请求时，都会把里面的数据发送给服务器端
   2.// cookies 适合做保存用户的个人设置、爱好等
     // session 适合做客户的身份验证
   3.// session 保存在服务器，客户端不知其中的信息
     // cookie 保存在客户端，服务器能知道其中的信息
   4.// session 需借助 cookie 才能正常工作，（如客户端完全禁止 cookie，则session将失效）
   5.// cookie 不是很安全（别人可分析放在本地的 cookie 进行欺骗）
     // session 比较安全
   ```

6. 补充：

   ==使用 smarty 模板，不可使用内嵌的 css 和 js，一定要独立==
