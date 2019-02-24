30——js JSON

1. 基础：

   1. 定义：指 JavaScript 对象表示法（JavaScript Object Notation），是存储和交换文本信息的语法，类似 XML
   2. 是轻量级的文本数据交换格式
   3. 具有自我描述性，更易理解
   4. JSON 只有两种数据格式：
      - 大括号 { } (对象)
      - 方括号 [ ] (数组)
   5. ==JSON 对象没有 length 属性==

2. 语法：

   1. 语法规则：

      ```javascript
      1.JSON 语法是 JavaScript 对象表示法语法的子集
      2.数据在名称/值对 中
      3.数据由逗号分隔
      4.大括号保存对象
      5.中括号保存数组
      ```

   2. JSON 值：

      ```javascript
      可以是：
      1.数字（整数或浮点数）
      2.字符串（在双引号中）
      3.逻辑值（true 或 false）
      4.数组（在方括号中）
      5.对象（在大括号中）
      6.null
      ```

3. 方法：

   1. JSON.parse()

      ```javascript
      // JSON 通常用于与服务端交换数据
          在接收服务器数据时一般是 字符串
          可以用 JSON.parse() 将数据转换为 JavaScript 对象
      // 语法：
          JSON.parse(str,callback);
          // 第二个参数可选，将为对象的每个成员调用此函数
      ```

   2. JSON.stringify()

      ```javascript
      // 可以将 JavaScript 对象转换为字符串
      	JSON.stringify(value[, replacer [, space]])
          // value:将要序列化成 一个JSON 字符串的值。
          // replacer(可选):如果该参数是一个函数，则在序列化过程中，被序列化的值的每个属性都会经过该函数					  的转换和处理
          // space(可选):指定缩进用的空白字符串，用于美化输出（pretty-print）
      
      JSON.stringify([new Number(1), new String("false"), new Boolean(false)]); 
      // '[1,"false",false]'
      
      ```

   3. eval 函数：

      ```javascript
      eval() 函数可计算某个字符串，并执行其中的代码
      // 语法：
          eval(string); // string 必需
      	// 返回值：通过计算 string 得到的值（慎用）
      // demo：
          var text = '{ "name":"Runoob", "alexa":"function () {return 10000;}",    "site":"www.runoob.com"}'; 
          var obj = JSON.parse(text); 
          obj.alexa = eval("(" + obj.alexa + ")"); 
          document.getElementById("demo").innerHTML = obj.name + " Alexa 排名：" + obj.alexa();
      
          结果显示为：Runoob Alexa 排名：10000
      ```

   4. 异常处理：

      JSON 不能存储 Date 对象，如需，要将其转换为字符串，再将字符串转换为 Date 对象

      ```javascript
      var text = '{"name":"veb","birth":"2018-12-14"}';
      var obj = JSON.parse(text);
      obj.birth = new Date(obj.birth);
      console.log(obj.birth);
      ```

   5. 总结：

      1. JSON.parse() 和 JSON.stringify() 为 es5 新增的方法，如需处理低版本兼容问题：

         引入 json.js

      2. json 字符串的特点：

         ==外面引号脱掉，就是 JSON 格式==
