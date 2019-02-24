es5数组补充-api

1. 大多数情况下，es5的数组方法接受的第一个参数为一个函数，并且对数组的每个元素调用一次该函数。

2. 该函数有三个参数：数组元素，元素的索引和数组本身。

3. 如果有第二个参数，则第一个参数中的this指向第二个参数。

4. var arr = [1,2,3,4,5];

   var result;

5. 数组方法：

   1. foreach() ;

      ```javascript
      // 从头到尾遍历数组，为每个元素调用指定的函数
      // 返回值：undefined 无
      // 原数组不改变
      
      // 计算和：
      var sum = 0;
      arr.foreach(function(val,index,a){
          sum += val;
          console.log(sum,arr);
      })
      console.log(sum,arr);
      
      // 每个数组元素值 +1
      result = arr.foreach(function(val,i){
          arr[i] = val+1;
          //break; // 直接 break 会报错，foreach 中没法终止遍历
      })
      console.log(arr);
      console.log(result);   // undefined 没有赋值
      ```

   2. map() ;

      ```javascript
      // 将调用的数组的每个元素传递给指定的函数，并返回一个数组，它包含该函数的返回值
      // 原数组不改变，而会返回一个新数组
      
      result = arr.map(function(x){
          return x*x   // 一定要有return，否则返回 undefined
      })
      console.log(return,arr); // [1,4,9,16,25]  [1,2,3,4,5]
      ```

   3. flter() ;

      ```javascript
      // filter 方法返回的数组元素是调用的数组的一个子集。传递的函数是用来逻辑判定的。
      // 该函数返回 true 或 false
      // 原数组不改变
      
      var result1 = arr.filter(function(val,index,a){
          return val > 3
      })
      console.log(result1); //[4,5]
      
      var result2 = arr.filter(function(val){
          return val%2
      })
      console.log(result2); // [1,3,5]
      
      // filter 方法可以把稀疏数组中的空元素筛出去
      var arr2 = [1,2,3,,4,,5]
      var result3 = arr2.filter(function(val){
          return val != undefined && val != null;
      })
      console.log(arr2,result3);
      ```

   4. every() 和 some() ;

      ```javascript
      // every 和 some 时数组的逻辑判定：它们对数组元素应用指定的函数进行判定，返回 true 或 false
      // every() 方法就像数学中的“针对所有”的量词：当且仅当针对所有数组中的所有元素调用判定函数都返回 true，它才返回 true
      
      result = arr.every(function(val){
          return val < 10;
      })
      console.log(result); // true
      
      result = arr.every(function(val){
          return val%2===0
      })
      console.log(result); // false
      
      // some() 方法就像数学中的“存在”的量词：当数组中至少有一个元素调用判定函数返回true，它就返回true，并且当且仅当数值中的所有元素调用判定函数都返回false，它才返回 false
      result = arr.some(function(val){
          return val%2===0
      })
      console.log(result); // true
      
      // 一旦every() 和 some() 确认该返回什么值它们就会停止遍历数组元素
      // some 在判定第一个元素返回 true 就停止遍历返回 true，否则遍历整个数组直到遇到 true 为止；
      // every 在判定第一个元素返回 false 就停止遍历，否则就一直遍历直到遇到 false 为止。
      ```

   5. reduce() 和 reduceRight() ;

      ```javascript
      // reduce() 和 reduceRight() 方法使用指定的函数将数组元素进行组合，生成单个值。这在函数式编程中是常见的操作，也可以称为 “注入” 和 “折叠”
      // 返回值为化简函数最后一次返回的结果
      //reduce()========
          // 数组求积
          var product = arr.reduce(function(x,y,z,a){
              console.log(x,y,z,a);
              return x*y
              // x:每次计算后的结果
              // y:数组元素
              // z:数组下标
              // a:数组本身
          })
          console.log(product);
      
          // 数组求和
          var sum = arr.reduce(function(x,y,z,a){
              console.log(x,y,z,a);
              return x+y
          },2) //第二个参数为：指定初始值
          console.log(sum);
      
          // 数组求最大值
          var max = arr.reduce(function(x,y){
              return x>y?x:y
          })
          console.log(max); // 5
      
          // reduce() 需要两个参数，
          // 第一个参数:是执行化简操作的函数。化简函数的任务就是用某种方法把两个值组合或化简为一个值，并					返回化简后的值
          // 第二个参数：是传递给函数的初始值，当不指定初始值时，它将数组元素的第一个值作为其初始值
          // 化简函数 function(初始值或上一次化简函数的返回值，数组元素，元素的索引，数组本身)
      // reduceRigth()=====
      	//reduceRight() 的工作原理和 reduce() 一样，不同的是它按照数组索引从高到低（从左到右）处理函		数
          var product = arr.reduceRight(function(x,y,z,a){
              console.log(x,y,z,a);
              return x*y;
          },1)
          console.log(product)
      ```

   6. indexOf() 和 lastIndexOf() ;

      ```javascript
      // 返回位置index 的方法
      // indexOf() ======
          // indexOf() 方法对大小写敏感
          var result = arr.indexOf(3);
          console.log(result); // 2
          //只写一个参数，表示在数组 arr 中从前往后查找 1 ，并且返回第一次查找到的位置
          var result2 = arr.indexOf(3,2);
          console.log(result2); // 2
          // 如果写两个参数，表示在数组 arr 中从前往后并且从 2 的位置开始查找 1，并且返回第一次查找到的		位置
      // lastIndexOf() =====
          // 用法与 indexOf() 相同，只是 lastIndexOf() 是从后往前查找
          var arr2 = [1,2,3,4,5,3];
          var result = arr2.lastIndexOf(3);
          console.log(result); // 5
      ```


