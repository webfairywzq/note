31——js 异常处理 try

1. try / catch / finally ：

   用于处理代码中可能出现的错误信息

   （错误可能是语法错误，通常是程序员造成的编码错误或错别字，也可能是拼写错误或语言中缺少的功能，可能由于浏览器差异）

2. 具体：

   ```javascript
   1.try:语句允许我们定义在执行是进行错误测试的代码
   2.catch:允许我们定义当try 代码块发生错误是，所执行的代码块
   3.finally:在try 和 catch 之后无论有无异常都会执行
   // catch 和 finally 语句都是可选的，但在使用 try语句时至少使用一个
   ```

3. 语法：

   ```javascript
   try{
       //尝试执行代码块
   }catch{
       // 捕获错误的代码块
   }finally{
       // 无论 try/catch 结果如何都会执行的代码块
   }
   ```
