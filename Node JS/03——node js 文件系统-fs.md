03————node js 文件系统-fs 

1. 文件系统（fs 模块）

   1. 定义：用来对服务器端的文件进行处理

   2. 功能：读取文件、写入文件、删除文件、创建目录、删除目录

   3. 实例：

      - ==var fs =require("fs");== // 别忘了写

      1. 读取文件：

         - 异步操作：

           ```javascript
           var fs = require("fs");
           fs.readFile("./file/1.txt",function(err,data){
           	if(err){
           		console.log("读取错误");
           	}else{
           		//==toString() 可转换二进制显示中文==
           		console.log(data.toString());
           	}
           })
           console.log("后面的")；
           ```

         - 同步操作：

           ```javascript
           var fs = require("fs");
           var data = fs.readFileSync("./file/1.txt");
           console.log(data.toString());
           console.log("后面的");
           ```

      2. 写入文件（会覆盖原有文件内容）：

         ```javascript
         fs.writeFile("./file/1.txt","0000",function(err){
         	if(err){
         		console.log("写入错误");
         	}else{
         		console.log("写入成功");
         	}
         })
         console.log("后面的");
         ```

      3. 重命名:

         ```javascript
         fs.rename("./file/1.txt","./file/333.txt",function(err){
         	if(err){
         		console.log("error");
         	}
         })
         ```

      4. 删除文件：

         ```javascript
         fs.unlink("./file/out.txt",function(){
         	console.log("del");
         })
         ```

      5. 获取文件信息：

         ```javascript
         fs.stat("./file/1.txt",function(err,stats){
         // 1. 获取文件大小
            console.log(==stats.size==);
         // 2. 获取文件最后一次访问时间
            console.log(==stats.atime.toLocaleString()==);
         // 3. 文件创建时间
            console.log(==stats.birthtime.toLocaleString()==);
         // 4. 文件最后一次修改时间
            console.log(==stats.mtime.toLocaleString()==);
         // 5. 判断是否是文件：是true；否false
            console.log(==stats.isFile()==);
         // 6. 判断是否是目录：是true；否false
            console.log(==stats.isDirectory()==);
         })
         ```

      6. 创建目录：

         ```javascript
         fs.mkdir("./file/test",function(err){
         	if(err){
         		return console.log(err);
         	}
         	console.log("创建成功");
         })
         ```

      7. 读取目录：

         ```javascript
         fs.readdir("./file/",function(err,files){
         	if(err){
         		return console.log(err);
         	}
         	files.forEach(function(file){
         		console.log(file);
         	})
         })
         ```

      8. 删除目录：

         ```javascript
         fs.rmdir("./file/test",function(){});
         ```

​	