HTML5————离线存储之Application Cache

1. 什么是应用缓存？【Web App 为了模仿原生App】，又叫“离线缓存”

   意味着web应用可进行缓存，并可在没有网络连接时进行访问

2. 应用缓存的优势：

   - 离线浏览：用户可以在离线状态下浏览网站内容
   - 速度：因为数据被存储在本地，所以速度会更快
   - 减少服务器负载：浏览器只会下载在服务器上发生改变的资源

3. 更新缓存的方式：

   - 更新manifest 文件：

     1. ==要刷新两次==：
        - appcache 更新了缓存，重新从网络上拉取需要cache 的文件
        - 想看到改变，要再次刷新浏览器（更新到浏览器）
     2. 浏览器发现manifest 文件本身发生变化，便会根据新的manifest 文件获取新的资源进行缓存
     3. 当manifest 文件列表并没有变化时，通常通过修改manifest 注释的方式来改变文件，从而实现更新

   - 通过javascript 操作：

     通过对于application Cache 对象的操作达到更新缓存的目的

     ```javascript
     window.addEventListener("load",function(e){
     	window.applicationCache.addEventListener("updateready",function(e){
     		if(window.applicationCache.status==window.applicationCache.UPDATEREADY){
     			window.applicationCache.swapCache();//该方法即可将原缓存换成新缓存
     			window.location.reload();
     		}
     	},false);
     },false);
     ```

   - 清除浏览器缓存

4. 注意事项：

   1. 站点离线存储的容量限制是==5M==
   2. 如果manifest 文件或内部列举的某一个文件不能正常下载，整个过程视为失效，浏览器继续全部使用老的缓存
   3. 引用manifest 的 html 必须与manifest 文件同源，在同一个域下（同源策略）
   4. FALLBACK中的资源必须和manifest 文件同源
   5. 当一个资源被缓存后，该浏览器直接请求这个绝对路径也会访问缓存中的资源
   6. 当manifest 文件发生改变时，资源请求本身也会触发更新
   7. app cache 不能跨浏览器使用

5. 应用：

   manifest文件：

   1. CACHE   MANIFEST  ==必须有，且放在首行==

   2. #version   1.3     ：版本号

   3. CACHE（必须）：

      标识出哪些文件需要缓存，可以是相对路径，也可是绝对路径 如：aa.css

   4. NETWORK（可选）：

      是绕过缓存直接读取的文件，可以使用通配符 * （除了cache文件，剩下的文件每次都要重新拉取）

   5. FALLBACK（可选）：

      指定了一个后备页面，当资源无法访问时，浏览器会使用该页面

      该段落的每条记录都列出两个URI：第一个表示资源，第二个表示后备页面

      两个URI都必须使用相对路径，并且与清单文件同源，（也可使用通配符 * ）

   6. 检测设备是否在线：

      ```javascript
      if(navigator.online){
      	alert("online");
      }else{
      	alert("offline");
      }
      ```