24——js 常用的DOM事件

1. window 事件：

   ```javascript
   1.onload:
       // 当网页加载完毕是发生---window.onload：页面加载完成时执行脚本
   2.onresize:
       // 事件会在窗口被调整大小是发生
   3.onscroll:
       // onscroll 事件在元素滚动条滚动条时触发
   ```

2. 鼠标事件：

   ```javascript
   1.onclick、ondblclick:
       // 当用户单击或双击元素时触发
   2.oncontextmenu:
       // 在用户点击鼠标右键打开上下文菜单时触发
   3.onmousedown、onmouseup:
       // 鼠标按键被按下或松开
   4.onmouseover、onmouseout:
       // 鼠标移动到某元素上或从某元素移开
   5.onmouseover、onmouseout 和 onmouseenter、onmouseleave 的区别：
       // 前一组会冒泡；后一组不会冒泡
   ★--当单击和双击同时存在时，双击不生效，因为单击提前生效！
   ```

3. 键盘事件：

   ```javascript
   1.onkeydown:
       // 键盘按键被按下
   2.onkeypress:
       // 键盘按键被按下并松开
   3.onkeyup:
       // 键盘按键被松开
   ```

4. 表单事件：

   ```javascript
   1.onblur:
       // 元素失去焦点时触发
   2.onchange:
       // 该事件在表单元素的内容改变时触发（失去焦点，并内容有所改变才触发）
   3.onfocus:
       // 元素获取焦点时触发
   4.onreset:
       // 表单重置时触发
   5.onselect:
       // 用户选取文本时触发（input、textarea）
   6.onsubmit:
       // 表单提交时触发
   补充：
    1.tabindex:  按数字顺序（越小权重越高）
    	tabindex="1"
   	tabindex="2"
    2.hidefocus="true": 失去焦点
    ★-- return false; // 可以阻止表单提交
   ```
