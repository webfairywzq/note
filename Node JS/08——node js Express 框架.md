08——node js Express 框架

参考网址： http://www.expressjs.com.cn/

1. 使用 express 可以快速搭建一个完整功能的网站

2. Express 框架核心特性：

   - 可以设置中间件来相应 http 请求
   - 定义了路由表用于执行不同的 http 请求动作
   - 可以通过模板传递参数来动态渲染 HTML 页面

3. Express 应用生成器

   通过应用生成器工具 express 可以快速创建一个应用的骨架

   步骤：

   1. 安装 express 的应用生成器

      cnpm install express-generator  -g

   2. 初始化一个带 ejs 模板引擎的项目

      express -h   帮助

      express -e myapp （-e 指：ejs 模板引擎，myapp指：应用目录名）

   3. 生成目录后：

      cd myapp （进入 myapp 目录）

   4. 安装项目依赖包

      cnpm install

   5. 启动项目

      npm start  （打开 http://localhost:3000/   网址就可以看到这个应用了）

      ==补充： 若想要热更新，需修改 package.json：==

      将 "start":"node  ./bin.www" 改成   "start":"nodemon  ./bin/www"  （前提是要安装了 nodemon）

   6. 操作：

      1. 添加模板：添加到 myapp/view 下

      2. 添加路由：添加到 myapp/routes 下（路由分模板，放在不同的路由文件下）

      3. 跟客户端交互，获取 get 和 post 的数据：

         ==get：req.query==

         ==post：req.body==

      4. 跟客户端交互，获取cookie数据：

         ==req.cookies   //可以获取cookie数据==

      5. 连接数据库  conn.js

      6. 在 app.js 中：

         - 引入当前项目相关的路由文件
         - app.use()；调用中间件的方法；

      7. 补充：

         ==中间件==（middleware）：就是处理 HTTP 请求的函数，用来完成各种特定的任务（比如检查用户是否登录，分析数据，以及其他在需要最终将数据发送给用户之前完成的任务）

   7. 补充：

      1. 路由中的 url 可以出现正则 * + ? ( ) ，使得路由匹配更灵活

         （访问 localhost:3000/product/abcd）

         router.get("/ab*cd",function(req,res){

         ​	res.send("/ab*cd");

         })

      2. 路由中可以传参数

         （访问 localhost:3000/product/detail/1234/5678）

         ```javascript
         router.all("/detail/:pid/:pdesc",function(req,res){
         	console.log(req.params); // 获取是路由路径传入的参数     //  { pid:'1234', pdesc:'5678' }
         	console.log(req.query); //获取 ? 后的查询字符串传入的参数，得到的是 get 请求传入的参数
         	res.send("/detail/"+req.params.pid+"/"+req.params.pdesc);
         })
         //req.body:得到的是 post 请求传入的参数，post 请求的编码必须是 enctype="application/x-www-form-urlencode"
         ```

      3. 路由方法：

         1. router.get()：查询
         2. router.post()：增加
         3. router.all()：（针对所有的任何形式的请求）
         4. router.put()：修改
         5. router.delete()：删除

      4. 上传文件：

         1. 上传单个文件：

            ```javascript
            router.post("/form",upload.single('==files=='),function(req,res){
            	res.json(req.body);
            	// files 与 input 的name 属性相对应
            })
            ```

         2. 上传多个文件：

            ```javascript
            router.post("/form",upload.array('files,==5=='),function(req,res){
            	res.json(req.body);
            	console.log(req.files); // 上传文件的信息，==类型是数组==
            	console.log( path.extname(req.files[0].originalname) ); // 得到文件的后缀名
            	//  5 代表：限制最大上传文件数
            })
            ```

      5. multer 模板：

         - 应用前提：

           form 表单中 enctype =" multipart/form-data " , methods = "post"

         - 步骤：

           1. 安装 multer 模板：

              cnpm  install  multer  --save

           2. 引入模板：

              const multer = require("multer");

           3. 配置上传文件的临时目录：

              var upload = multer({ dest : ' public/uploads/ ' });

           4. 上传文件：

              router.post(路径，upload.array/upload.single，function(){})；

           5. 得到上传文件信息：

              ```javascript
              router.post("/form",upload.array(' files ',5),function(req,res){
              	console.log(req.files); // 得到上传文件信息
              6. 文件重命名：
                 req.files.forEach(function(file){
                 	var extname = path.extname(req.files[0].originalname);
                 	fs.rename(file.path,file.destination + "upload_" + newDate() * 1 + extname,function(err){
                 		if(err){
                 			res.send("重命名错误");
                 		}else{
                 			res.send("文件上传成功");
                 		}
                 	})
                 })
              }) 
              ```

      6.路由中  Response methods：

      1. 原来的 res 上的方法依然可以使用：

         res.writeHead();

         res.write();

         res.end();

      2. express 给对象上添加了一些有用的方法：

         - res.download()：下载文件

         - res.redirect()：重定向

         - res.render()：渲染模板

         - res.send()：向浏览器发送数据

         - res.sendFile()；

         - res.sendStatus()：状态码

           200：“ok”

           403：“Forbidden” （没有权限，禁止访问）

           404：“not found” （找不到）

           405：（服务器错误）

      7.连接数据库：

      1. 建一个数据文件夹，建一个 ”conn.js “ 数据池

      2. 引入模板：

         const  conn = require("../db/conn");

      3. 连接数据库：

         ```javascript
         router.get("/db",function(req,res){
         	conn.query("select * from tejia",[ ] , function(results){
         		//res.json(results);
         		console.log(results);
         		res.render("index",{ "list":results, "title":"express" });
         	})
         })
         ```

   8. 处理 cookie:

      1. 引入模板：

         var cookieParse = require("cookie-parse");

      2. 处理 cookie：

         ```javascript
         app.get("/cookie",function(req,res){
         	console.log(req.cookies);
         	res.json(req.cookies);
         })
         ```


    