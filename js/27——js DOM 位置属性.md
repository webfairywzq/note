27——js DOM 位置属性

1. 鼠标位置：

   Event 对象(事件对象)属性：

   1. clientX(Y)：相对浏览器窗口(可视区)的 x (y)坐标位置  ------（没有兼容问题）
   2. offsetX(Y)：设置或者是得到鼠标相对于目标事件的父元素的内边界在 x(y) 坐标上的位置（FF不支持）
   3. screenX(Y)：鼠标相对于用户屏幕 ----（没有兼容问题）

2. 滚动对象属性：

   1. scrollLeft：设置或获取位于对象左边界和窗口中目前可见内容的最左端之间的距离

        		（指当元素内容超过其宽度时，==元素被卷起的宽度==------就是滚出去的宽度）

   2. scrollTop：设置或获取位于对象对顶端和窗口中可见内容的最顶端之间的距离

      ​		 （指当元素内容超过其高度时，==元素被卷起的高度==-----就是滚出去的高度）

   3. scrollWidth、scrollHeight（只读）：（有兼容问题）

      元素的内容区域加上它的内边距再加上任何溢出的尺寸

   4. 获取页面滚动高度兼容处理：

      ```javascript
      if(document.documentElement.scrollTop){
          x = document.documentElement.scrollTop; // IE
      }else{
          x = document.body.scrollTop; // Chrome,Firefox
      }
      ```

   5. 封装好的：

      ```javascript
      // 获取 scrollTop
          function getScrollTop(){
              var scrollTop = document.body.scrollTop || document.documentElement.scrollTop || window.pageYOffset;
              window.pageYOffset = scrollTop;
              return scrollTop;
          }
      // 设置 scrollTop
          function setScrollTop(top){
              document.body.scrollTop = top;
              if(window.pageYOffset){
                  window.pageYOffset = top;
              }
              document.documentElement.scrollTop = top;
          }
      ```

3. 普通DOM对象属性：

   1. offsetLeft：当前元素，相对于其 offsetParent 左边距离

   2. offsetTop：当前元素，相对于其 offsetParent 上边距离

   3. offsetParent：

      指的是当前元素的离自己最近的具有定位的父级元素（只要是它的父元素就可以），该父元素就是     当前元素的 offsetParent，如果找不到，那么当前元素的 offsetParent为 body

   4. offsetWidth、offsetHeight（只读）（无兼容问题）：

      指元素的 border + padding + content 的宽度和高度

   5. clientWidth、clientHeight(只读) （没有兼容问题）：

      指元素的可视部分宽度和高度。即 content + padding ，不包含边框

      1. 没有滚动条：直接为 content + padding
      2. 有滚动条：content + padding - 滚动条宽(高) 度

   6. clientTop、clientLeft（只读）：

      通常情况下等于 左边和上面的边框高度（用的较少）

      对于行内元素，获取到为 0；

   7. 封装好的：

      ```javascript
      // 获取 offsetTop
          function getOffsetTop(obj){
              var offset_top = obj.offsetTop;
              var offset_parent = obj.offsetParent;
              if(offset_parent){
                  offset_top+=offset_parent.offsetTop;
                  offset_parent = offset_parent.offsetParent;
              }
              return offset_top;
          }
      ```

4. 偏移量：获取元素相对于浏览器窗口的偏移量 （没有兼容问题）

   1. getBoundingClientRect()：返回一个对象，包含 left、top、right、bottom,分别表示 元素距离浏览器左上角的距

   2. demo：

      ```javascript
      // 计算子元素到父元素的 边框（外侧）的距离：
      child.getBoundingClientRect().left - parent.getBoundingClientRect().left;
      ```
