01——PHP 基础

1. 全局变量不能在函数内部访问

2. 函数内部的变量不能在外部访问

3. 常量：

   - 一旦定义后期不可更改

   - 定义语法：

     ```javascript
     define('rootDir','http://www.baiyun.com',false);
     //true : 不区分大小写
     //false: 区分大小写
     ```

   - 读取：

     ```javascript
     echo rootDir;
     ```

4. 如果在 php 中使用 date() 函数，则会提醒定义时区：

   ```javascript
   date_default_timezone_set("PRC"); // 设置中国时区
   ```

5.  if...elseif...

   ==elseif 中间没有空格==

6. 数组：

   1. 数值数组：

      ```javascript
      $cars = array("Volvo","BMW","Toyota");
      // $cars[0] = "Volvo";
      // $cars[1] = "BMW";
      // $cars[2] = "Toyota;
      
      //读取：
      echo $car[1];
      //遍历：
      for($i = 0; $i < count($cars); $i++){
          echo $cars[$i];
      }
      ```

   2. 关联数组：

      ```javascript
      $person = array("nickname" => "John", "age" => 23);
      
      //读取：
      echo $person["age"];
      
      //遍历：
      foreach($person as $key => $value){
          echo $key."========".$value;
          echo "<br/>";
      }
      ```

7. 超级全局变量：$_SERVER

   ```javascript
   $_SERVER["PHP_SELF"]：获取当前文档的根目录
   
   __File__：获取当前文档的绝对路径
   
   // 如果客户端以 post 方式提交数据，应用 $_POST 获取；
   // 如果客户端以 get 方式提交数据，应用 $_GET 获取；
   
   // 目前掌握的 客户端向服务端传递数据的方式：
   1.表单以 get 方式传递数据
   2.表单以 post 方式传递数据
   3.以超链接方式，将数据附加在链接地址后，传递给服务端
   ```

8. 函数：

   1. isset()：

      一般用来检测变量是否设置

      - 若变量不存在 ====> false
      - 若变量 存在 且 值为 NULL ====> false
      - 若变量 存在 且 值 不为 NULL ====> true

   2. empty()：

      判断值是否为空

      - 若变量不存在 ====> true
      - 若变量 存在 且 值为 " ",0,"0",NULL, ,false,array 以及 没有任何属性的对象 ====> false

   3. var_dump()：

      返回变量的 ==数据类型和值==

   4. htmlspecialchars()：

      把一些预定义的字符转换为 HTML 实体

      demo：

      - &(和号)：&amp
      - " "(双引)：&quot
      - ' '(单引)：&#039
      - <(小于)：&lt
      - (大于)>：&gt

9. 魔术常量（可不区分大小写）

   ```javascript
   1.__LINE__：文件中当前行号
   2.__FILE__：文件的完整路径和文件名，（如果用在被包含文件中，则返回被包含的文件名）
   3.__DIR__：文件所在的目录，如果用在被包括文件中，则返回被包括的文件所有的目录
   ```

10. 页面之间传递数据的方式：

    1. 表达的形式
    2. url 地址后的查询字符串（<a>）
    3. cookie
    4. session