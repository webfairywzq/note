HTML5————本地存储

1. 客户端存储数据的方法：

   - cookie 方法
   - localStorage 方法
   - sessionStorage 方法

2. localStorage：

   - 存储特点：

     存储的数据没有时间限制（不能跨浏览器读取数据）

   - API ：

     1. 保存数据：

        localStorage.setItem(key,value);

        localStorage.key=value;

     2. 读取：

        localStorage.getItem(key);

        localStorage.key;

     3. 删除：

        - 单个：localStorage.removeItem(key);
        - 所有：localStorage.clear();

3. sessionStorage：

   - 存储特点：

     针对一个session进行数据存储

     当用户关闭浏览器窗口后，数据会被删除

   - API：同上

4. ==sessionStorage、localStorage、cookie的区别==：

   - 共同点： 都是保存在浏览器端，且都是同源的
   - 区别：
     1. ==与服务器的数据交换方式不同==：
        - cookie：数据始终在同源的 http 请求中携带与服务器进行交换（即使不需要）
        - localStorage+sessionStorage：不会自动把数据发给服务器，仅在本地保存
     2. ==存储大小限制不同==：
        - cookie：不能超过==4k==，只适合保存少量数据（如会话标识）
        - localStorage+sessionStorage：可以达到5M或更大
     3. ==数据有效期不同==：
        - cookie：（会话cookie+持久cookie）  只在设置的cookie过期时间之前有效
        - localStorage：始终有效（用作持久数据），除非清缓存删除或通过removeItem和clear删除
        - sessionStorage：当关闭浏览器窗口，自动销毁
     4. ==作用域不同==：
        - cookie、localStorage、sessionStorage在不同的浏览器窗口之间不共享
        - cookie：在同一个浏览器的不同窗口之间是共享的，但是跟创建cookie的页面有关
        - localStorage：在同一个浏览器的不同标签窗口之间是共享的
        - sessionStorage：在同一个浏览器的不同标签窗口之间（如果是通过链接跳过去的sessionStorage是共享的，如果是直接在地址栏中输入地址，那是不共享的）

