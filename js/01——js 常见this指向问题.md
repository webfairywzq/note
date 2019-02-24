01——js 常见this指向问题

1. 注册事件：

   1. this指向的是 ==dom==对象
   2. addEventListener（fun，）； 函数中的 this 指向的是 dom 对象
   3. attachEvent（fun）；函数中的 this 指向的是 window

   ==引用 call 函数 或 apply 函数修改 this 的指向==

2. 普通函数的调用：

   this 指向的是 window

3. 计时器：

   函数中的 this 指向的是 window（计时器将调用函数（第一个参数）中的 this 指向 window）

4. 创建对象：

   new 的时候，this 指向的是当前对象（构造函数中的 this，指向的是==当前实例对象==）

5. ==函数中的另一个函数的 this 指向 window==：

   ```javascript
   function show() {
       console.log(this);
   }
   btn.onclick=function(){
       show();  // window
   }
   ```


