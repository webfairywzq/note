CSS————HTML标签类型

1. 三种类型：

   - 块状元素：<div>   <p>   <h1>   <ul>   <li>
   - 行内元素：<span>  <a>  <label>  <strong>  <em>   <nav>
   - 行内块元素： <img>   <input>

2. 块状元素：

   - 每个块级元素都可以从新的一行开始，并且气候的元素也另起一行（一个块级元素独占一行）
   - 元素宽、高可设置
   - 元素宽度在不设置的情况下，为本身容器的100%

3. 行内元素：

   - 块状元素可通过 display：inline  将元素设置为行内元素
   - 特点：
     1. 一行可以放多个
     2. 元素宽、高不可设置
     3. 元素的宽度就是它包含的文字或图片的宽度（一般a标签可以包含图片），不可改变

4. 行内块元素：

   - 行内块元素同时具备行内元素、块元素的特点
   - display：inline-block 将元素设置为行内块元素
   - 特点：
     1. 和其他元素都在一行上
     2. 元素宽高可设置

5. 显示模式之间的转换：

   - display：block   将行内、行内块元素转为块元素
   - display：inline   将块状元素转为行内（一般不将块元素转为行内）
   - display：inline-block    将块和行内元素转为行内块

6. ==display兼容问题==：会产生4px 间距（因为换行或者空格导致）：

   解决方法：

   ​	

   - 不换行，一行显示

   - 为父元素设置字体大小为 0：font-size：0；

   - 针对IE 的低版本需添加：  

     ​	

     *display：inline；

     zomm：1；