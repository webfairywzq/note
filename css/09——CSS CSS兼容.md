CSS————CSS兼容

1. 上下margin重合问题： 上下外边距合并，会以大的那个值为准

   - 解决方法：  

     ​	

     1. 相邻的margin-top、margin-bottom二选一

2. margin-top：子元素的margin-top 会出现在父元素上方

   - 解决方法：
     1. 给父元素加 overflow：hidden；
     2. 给父元素设：border：1px solid transparent；
     3. 用父元素的padding-top 来代替子元素的margin-top（最佳方案）

3. 行内元素与行内元素、行内块与行内块、行内块与行内元素之间会出现缝隙：

   - 解决方法：
     1. 给行内元素或行内块元素的父元素：font-size：0；，给子元素中心设置字号
     2. 给行内或行内块元素添加浮动

4. 元素设置了：display：inline-block；后，在父元素中垂直位置不对：

   - 解决方法：
     1. 给当前元素添加：vertical-align：top | middle | bottom；

5. display：inline-block；在IE7中不兼容，会导致排版混乱

   - 解决方法;
     1. 凡是用display：inline-block；时，同时加上：*display：inline；*zoom：1； 会触发haslayout 属性，使标签具有布局模式（以*开始的选择器，只有IE6 IE7 会执行，其他浏览器会忽略）

6. 加链接的图片，在低版本IE中显示蓝边框：

   - 解决方法;
     1. img{ border：none；}

7. 块元素中装图片，图片下方会出现一条间隙：

   - 解决方法：
     1. 给 img 添加 display：block；

8. opacticy：不透明度 （不兼容 IE8及以下浏览器）：

   - 解决方法：
     1. filter：alpha（opacticy=50）

9. 伪元素：after：before

   不兼容IE7

10. outline：不兼容IE7

11. input标签的placeholder属性：不兼容IE9以下属性

12. chrome下默认会将小于12px 的文本强制按照12px 来解析：

    - 解决方法：
      1. -webkit-text-size-adjust：none；（谷歌27以下版本可用）
      2. -webkit-transform：scale（0.5）；（css3实现）

