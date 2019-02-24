19——js DOM 基础

1. DOM：即 Document Object Model（文档对象模型）

2. 主要作用：

   可以通过 JavaScript 动态修改相关的元素

3. HTML  DOM树：

   1. DOM 会将整个文档抽象为 DOM 树，所有在 DOM 树上的元素都可以被选择

   2. JavaScript 可以完成这些操作：

      1. 能够改变页面中的所有 HTML 元素
      2. 能够改变页面中的所有 HTML 属性 
      3. 能够改变页面中的所有 CSS 样式
      4. 能够对页面中的所有事件做出反应

      为了做这些事情，必须首先找到该元素（即建立元素的 DOM 对象）

      5种方法：

      1. 通过 id 找到 HTML 元素

      2. 通过标签名找到 HTML 元素

      3. 通过 name 属性（只针对有 name 属性的表单元素）找到 HTML 元素

      4. 通过类名找到 HTML 元素

      5. document.querySelector():

         querySelector()：仅仅返回匹配的指定选择器的第一个元素，如果需要返回所有的元素，需用 querySelectorAll();

         浏览器支持：IE8.0 ，chrome：4.0，FF：3.5

4. 改变 HTML元素的样式：

   1. 访问行内样式：

      obj.style.CSS样式名 = 新值

   2. 访问元素类名：

      obj.className = "类名"；// 修改、添加、删除类名，去掉一个类名

   3. 可以通过 DOM.style 获取所有的样式（改变、获取样式）==（只能获取或修改 HTML 行内样式）==

      1. DOM.style.属性名 ：获取对应的属性名的属性值

      2. DOM.style.css属性名：只能访问行内样式

      3. DOM.style.css属性名 = “值”：可以给对应的元素添加相关属性名（样式）

      4. DOM.style.css属性名 = “新值”

         获取：DOM.style.css属性名

         修改：DOM.style.css属性名 = “新值”

         新增：DOM.style.css属性名 = “值”

   4. 通过修改 className 来修改元素样式 （只能修改固定的样式）：

      ```javascript
      // 首先对某个 class 添加样式
      .className{
          color:red;
      }
      // 给对应的元素添加对应的 className：
      DOM.className = "className";
      
      ```

5. 如果想要获取到样式表中的样式（只读、只能获取相关样式）：

   获取计算后的样式，即在对应的 chrome 下或者其他浏览器下的开发者工具中，找到对应样式里的 computed 属性，可以看到所有的计算后的样式，那里的样式是我们要获取的样式

   ```javascript
   1.W3C 标准方式(兼容FF,Chrome,Safari)（IE9以上也可）：
   	getComputedStyle(DOM,null).属性名
    // null 填写不同的形式，可以获取到不同的伪元素的样式；
    // 如果 null 改为“after”，则获取after 伪元素的样式
   2.IE中：
   	DOM.currentStyle["属性名"]
   	DOM.currentStyle.属性名；
   // 在 IE 中对应颜色为关键字，但是其他浏览器为 rgb 形式
   ```
