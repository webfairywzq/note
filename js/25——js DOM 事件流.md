25——js DOM 事件流

1. DOM 0级事件流：

   1. 冒泡型事件流：

      事件的传播是从最特定的事件目标到最不特定的事件目标。即从 DOM 树的叶子到根

      （从里往外走：事件目标target-----> body）

   2. 捕获型事件流：

      事件的传播是从最不特定的事件目标到最特定的事件目标。即从 DOM 树的根到叶子

      （从外往里走：body-----> 事件目标target）

2. 标准事件流（DOM 2级）：

   1. DOM 标准采用 捕获 + 冒泡，两种事件流都会触发 DOM 的所有对象，从 document 对象开始，也在 document 对象结束。

   2. 标准的事件流分为三个过程：

      ★.捕获阶段：从 window---text

      ★.目标阶段

      ★.冒泡阶段：从 text----window

      ★★标准事件流中，先捕获，后到事件源，最后才是冒泡阶段

      （捕获面试中会提问，平时项目中用到冒泡较多）

3. 阻止事件冒泡：

   ```javascript
   1.W3C 标准用法：
   	e.stopPropagation(); // IE8 以下不兼容
   2.IE8 以下(Chrome,Firefox):
   	e.cancelBubble = true;
   3.兼容处理：
   function stopPropagation(e){
       e = e || window.event;
       if(e.stopPropagation){
           e.stopPropagation();
       }else{
           e.cancelBubble = true;
       }
   }
   ```

4. 阻止浏览器默认行为：

   ```javascript
   1.  e.preventDefault();
   2.  e.returnValue = false;
   3.兼容处理：
   DOM.onclick = function() {
       return false; // 阻止相关的默认行为
   }
   function stopDefault(e){
       e = e || window.event;
       if(e.preventDefault){
           e.preventDefault();
       }else{
           e.returnValue = false;
       }
   }
   ```

