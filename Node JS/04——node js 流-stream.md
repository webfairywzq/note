04————node js 流--stream

1. 通过 .pipe() 接口来监听其 data  和 end 事件，并把 data.txt （的可读流）拆分成一小块一小块的数据（chunks），像流水一样不断吐给客户端，而 ==不再需要整个文件都加载到内存后才发送数据==

2. stream 是一个抽象接口：

   - 对 http 服务器发起请求的request 对象就是一个 stream
   - stdout（标准输出）也是一个stream

3. 4种标准流类型：

   1. Readable——可读操作
   2. Writable ——可写操作
   3. Duplex ——可读可写操作
   4. Transform——操作被写入数据，然后读出结果

4. 所有 stream 对象都是 EventEmitter 的实例，常用事件有：

   - data——当有数据可读时触发
   - end——没有更多的数据可读时触发
   - error——在接收和写入过程中发生错误时触发
   - finish——所有数据已被写入到底层系统时触发

5. 过程：

   1. 创建可读流：

      ```javascript
      var fs = require("fs");
      var data="";
      var readerStream = fs.createReadStream("input.txt");  // 创建
      readerStream.setEncoding("UTF8");  // 设置编码为 utf8
      // 处理流事件
      readerStream.on('data',function(chunk){
      	data += chunk;
      });
      readerStream.on('end',function(){
      	console.log(data);
      });
      readerStream.on('error',function(){
      	console.log(err.stack);
      });
      console.log("程序执行完毕");
      ```

   2. 管道读写操作：

      1. 读取一个文件内容后写入另一个文件中，会覆盖原有的内容

         ```javascript
         // 创建一个可写流
         var fs = require("fs");
         var readerStream = fs.createReadStream('./file/1.txt');
         var writeSream = fs.createWriteStream('output.txt');
         // 管道读写操作
         // 读取 input.txt 文件内容，并将内容写入到 output.txt 文件中
         readStream.pipe(writeStream);
         console.log("程序执行完毕");
         ```

      2. 读取一个文件后写入另一个文件中，追加在原有内容后

         ```javascript
         // 追加
         var  read = fs.createReadStream('./file/1.txt');
         // 设置第二个参数 append
         var write = fs.createWriteStream('output.txt',{'flags':'a'});
         // 管道流读写操作
         read.pipe(write);
         console.log("执行完毕");
         ```

   3. 压缩

      ```javascript
      var fs = require("fs");
      var zlib = require("zlib");
      fs.createReadStream('input.txt')
      .pipe(zlib.createGzip())
      .pipe(fs.createWriteStream('input.txt.gz'));
      ```

   4. 解压

      ```javascript
      var fs = require("fs");
      var zlib = require("zlib");
      fs.createReadStream("input.txt.gz")
      .pipe(zlib.createGunzip())
      .pipe(fs.createWriteStream("input.txt"));
      ```

