28——js BOM 基础

1. BOM：browser object model，（浏览器对象模型）

2. 作用：获取浏览器信息，操作浏览器

3. 核心对象：window

4. 组成 BOM 的对象：

   1. window 对象：

      window 对象是BOM 的顶层对象，其他对象都是该对象的子对象

      ```javascript
      1.所有浏览器都支持 window 对象，它表示 浏览器窗口
      2.所有 JavaScript 全局对象、函数以及变量均自动称为 window 对象的成员：
      	★. 全局变量是 window 对象的属性
      	★. 全局函数是 window 对象的方法
      3.JavaScript可以通过window对象来获取浏览器窗口的宽度和高度（浏览器的视口，不包括工具栏和滚动条）。
      	★.对于Internet Explorer、Chrome、Firefox、Opera 以及 Safari 使用：
          	window.innerHeight----浏览器窗口的内部高度
              window.innerWidth-----浏览器窗口的内部宽度
      	★.对于 Internet Explorer 8、7、6、5 使用：
          	document.documentElement.clientHeight;
      		document.documentElement.clientWidth;
      	  或
            	document.body.clientHeight;
      	    document.body.clientWidth;
      	★. 结合为：
      	 	var width = window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth;
      		var height = window.innerHeight || document.documentElement.clientHeight || document.body.clientHeight
      ```

   2. history 对象：

      1. 存放浏览器当前窗口的访问历史

      2. 常用方法：

         ```javascript
         1.window.history.go(-1); 
             // 访问浏览器窗口的历史，负数为后退，正数为前进，0导致页面刷新 如果参数对应的history对象里面没页面的话，页面不发生任何变化
         2.window.history.back(); 
             // 同上，无参数
         3.window.history.forward(); 
             // 同上，无参数
         4.window.history.length;
             // 可以查看历史中的页面数（history对象中存储的页面数）
         ```

   3. location 对象：

      1. 用于获取当前页面的地址（URL）信息、页面重定向等场景

      2. 常用属性和方法（修改会导致页面重载）

         ```javascript
         1.location.href 
             //当前载入页面的完整URL
         2.location.pathname 
             //URL中主机名后的部分，如/pictures/index.htm 
         3.location.search 
             //执行GET请求的URL中的问号后的部分，又称查询字符串，如?param=xxxx ,参数的传递
         4.location.hash 
             //如果URL包含#，返回该符号之后的内容，如#anchor1 
         5.location.reload(true | false); 
             //重新载入当前页面，为false时从浏览器缓存中重载，为true时从服务器端重载，默认为false
         ```

   4. navigator 对象：

      1. 存放有关 web 浏览器的信息，在检测浏览器及操作系统方面非常有用

      2. 常用方法：

         ```javascript
         ★★ 1.navigator.userAgent 
                 //用户代理头的字符串表示
         	2.navigator.appName 
                 //官方浏览器名的字符串表示 
         	3.navigator.cookieEnabled 
                 //如果启用cookie返回true，否则返回false 
         ```

   5. screen 对象：

      1. 存放有关显示浏览器屏幕的信息

      2. 常用属性：

         ```javascript
         1.availHeight:属性返回访问者屏幕的高度，以像素计，减去界面特性，比如窗口任务栏;
         2.availWidth:属性返回访问者屏幕的宽度，以像素计，减去界面特性，比如窗口任务栏;
         3.height:返回屏幕区域的实际高度 /*跟电脑分辨率一致*/;
         4.width:返回屏幕区域的实际宽度屏幕分辨率的宽高 /*跟电脑分辨率一致*/
         ```

