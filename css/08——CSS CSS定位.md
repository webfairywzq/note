CSS————CSS定位

1. 定位属性：

   - position：static；（默认值）

     无定位，在HTML文档中默认的位置

   - position：absolute；（绝对定位）

     脱离文档流，不占位，参照浏览器窗口进行位置的确定

     这条语句的作用：

     ​		将元素从文档流中拖出来，然后使用left 、right、top、bottom属性相对于其最接近的一个具有          定位属性的祖先元素进行绝对定位，如不存在这样的元素，则相对于body元素

   - position：relative；（相对定位）

     相对于它在正常文档流的位置进行定位，参照自身原来的位置进行移动

   - position：fixed；（固定定位）

     不随页面的滚动而滚动（不动），相对于浏览器窗口进行定位，（某一些页数需求，固定定位可以和绝对定位搭配使用

2. 定位的使用：

   - 绝对定位的元素完全脱离标准流（在文档流中不占位置），它完全漂浮在标准流上方
   - ==相对定位在文档流中是占有位置的==，不管怎么移动，原来的位置保留
   - ==子元素绝对定位，父元素相对定位==
   - 定位的特性：
     1. 行内元素添加了绝对定位可以和字节给宽、高不用转换
     2. 块元素添加了绝对定位，如果没有指定宽度，会自动收缩到内容的宽度
     3. 绝对定位的盒子不受父盒子padding的影响
     4. ==父元素有绝对定位，可以不需要清浮动==（因为绝对定位脱离文档流）

3. 堆叠属性：

   z-index：规定属性的堆叠顺序

   - 拥有更高堆叠顺序的元素总会处于堆叠顺序较低的元素前面

   - 元素可拥有==负的==z-index属性值

   - z-index默认值为  0  

   - ==仅能在定位元素行奏效==

   - 该属性设置一个定位元素沿 z 轴的位置，z 轴定义为垂直延伸到显示区的轴，如果为正数则离用户更近，为负数，则离用户更远

   - 页面布局，用浮动；局部定位，用定位

   - 如果父元素的层级一样，子元素的层级，取值越大，放的越靠上

   - 如果父元素的层级不一样，子元素的层级再高也没有效果：

     例如：a元素层级比  b 元素层级高，b 元素的子级想覆盖 a 元素的话，层级再高也不行