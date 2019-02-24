06——node js 搭建HTTP静态资源服务器

1. HTTP 服务器的功能：

   - 处理静态资源的请求
   - 处理动态资源的请求
   - ==注意==： 
     1. 请求的==静态资源== 一定 ==有== 后缀名
     2. 请求的==动态资源== 一定 ==没有==  后缀名

2. 概念：

   1. 静态资源：

      一般客户端发送请求到 web 服务器，web 服务器从内存取到相应的文件，返回给客户端，客户端解析并渲染显示出来

   2. 动态资源：

      一般客户端请求的动态资源，先将请求交于 web 容器，web 容器连接数据库，数据库处理数据之后，将内容交给 web 服务器，web 服务器返回给客户端解析并渲染处理

   3. 静态资源、动态资源的区别：

      - 静态资源一般都是设计好的 html 页面，而动态资源依靠设计好的程序来实现按照需求的动态响应
      - 静态资源==交互性差==，动态资源可以根据需求自由实现
      - 在服务器的运行状态不同，静态资源不需要与数据库参与程序处理，动态可能需要多个数据库的参与运算

3. 常见的静态资源及相关的响应头信息：

   1. html 文件： res.writeHead(200,{"Content-type":"text / html ; charset = Utf-8"});
   2. css 文件： res.writeHead(200,{"Content-type" : "text / css;charset = Utf-8"});
   3. js 文件： res.writeHead(200,{"Content-type" : "text / javascript;charset = Utf-8"});
   4. 图片： res.writeHead(200,{"Content-type" : "image / jpeg"});

4. Node.js ——全局对象：

   - JavaScript 中有一个特殊的对象，称为全局对象（Global Object），==它及其所有属性都可以在程序的任何地方访问==，及全局变量
   - 举例：
     1. __dirname：表示当前文件所在的目录
     2. __filename：表示当前文件的完整路径
     3. 其他全局对象：setTimeout、setInterval、console、process

5. path 模块：

   1. path 模块提供了一些工具函数，用于处理文件与目录的路径

   2. 使用方式：

      var path = require("path");

   3. 常见方法：

      - path.join()：使用平台特定的分隔符把全部给定的 path 片段连接到一起，并规范化生成的路径

      - path.nromalize()：会规范化给定的 path ，并解析 '..' 和 ' . ' 片段

      - path.resolve()：会把一个路径或路径片段的序列解析为一个绝对路径

        ==以盘符开头==   var url = path.resolve('/foo','/bar','baz'); // 返回： "G:\bar\baz"

      - path.extname()：返回文件扩展名

        var  ext = path.extname("./app/index.html")；

   4. 读文件时路径的处理：

      错误写法：fs.readFile("./test/txt",function(error,result){})

      ==正确写法==：fs.readFile(path.join(__dirname,"./test.txt"),function(error,result){})

6. mime 模块：

   1. mime 是设定文件类型的

      例：css，html 文件，类型归类是 "text/"

      ​	jpeg 是"image/"

   2. 安装：

      cnpm install mime --save

   3. 使用：

      var mime = require("mime");

      console.log(mime.getType(req.url));