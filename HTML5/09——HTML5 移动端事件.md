HTML5————移动端事件

1. 事件：

   - touchstart   ： 手指刚接触屏幕时触发
   - touchmove ：  手指在屏幕上移动
   - touchend    ：  手指从屏幕上移开时触发
   - ==需要用DOM对象添加时间侦听的方式添加touch事件（在少部分浏览器通过标签属性或DOM属性添加touch事件会不成功）==
   - （ box.addEventListener("touchstart",function(){},false) ）

2. event对象

   每个触摸事件被触发后，会生成一个event对象，event对象中额外包括以下三个触摸列表：

   1. touches：当前屏幕上所有手指的列表（touchend下此属性length为0）

   2. targetTouches：当前dom元素上手指的列表（touchend下此属性length为0）

   3. changedTouches：涉及当前事件的手指的列表

      ==event.touches：用数组的访问方式读取==

3. touch对象属性

   这些列表里的每次触摸由touch对象组成，touch对象里包含着触摸信息

   - 属性：
     1. clientX / clientY：触摸点相对浏览器窗口的位置
     2. pageX / pageY：触摸点相对于页面的位置
     3. screenX / screenY：触摸点相对于屏幕的位置
     4. identifier：touch对象里的ID
     5. target：当前的dom元素

4. 判断支不支持touch事件：

   ```javascript
   function hasTouch(){
         var touchObj = {};
         touchObj.isSupportTouch="ontouchend" in document?true : false;
         touchObj,isEvent=touchObj.isSupportTouch?"touchstart" : "click";	
         return touchObj.isEvent;
   }
   $(".box").addEventListener(hasTouch(),function(){});
   ```