02————node js 模块系统

1. ==一个 node.js 文件就是一个模块==

2. Node.js 提供了 ==exports==  和 ==require== 两个对象，其中 exports 是模块公开的接口；require 用于从外部获取一个模块的接口，即所获取模块的exports 对象

3. demo1：

   - hello.js 中：

     ```javascript
     exports.world = function(){
     	console.log("Hello world");
     }
     ```

   - main.js 中：

     ```javascript
     var hello =require('./hello');
     hello.world();
     ```

   - 分析： hello.js 通过 exports 对象把 world 作为模块的访问接口，在 main.js 中通过 require('./hello') 假爱这个模块，就可以直接访问hello.js 中的exports 对象的成员函数了

4. demo2：

   - hello.js中：

     ```javascript
     function Hello(){
     	var name;
     	this.setName=function(thyName){
     		name=thyName;
     	};
     };
     module.exports = Hello;
     ```

   - main.js 中：

     ```javascript
     var Hello=require('./hello');
     hello = new Hello();
     hello.setName('BY Void');
     ```

5. 总结：

   - ==exports 暴露函数==
   - ==module.exports 暴露对象==

6. Node.js 4类模块（原生模块和3种文件模块）

   - http 、fs、path等 ————原生模块
   - ./mod 或  ../mod   ————相对路径的文件模块
   - ./pathtomodule/mod ———绝对路径的文件模块
   - mod ——————非原生模块的文件模块