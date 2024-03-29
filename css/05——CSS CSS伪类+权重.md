CSS————CSS伪类+权重

1. CSS 分类（classification）

   - 分类属性允许你规定如何以及在何处显示元素
   - 分类属性：
     1. clear：设置一个元素的侧面是否允许其他的浮动元素
     2. cursor：规定当指向某元素之上时显示的指针类型
     3. display：设置是否及如何显示元素
     4. float：定义元素在哪个方向浮动
     5. position：把元素放置到一个静态的、相对的、绝对的或固定的位置中
     6. visibility：设置元素是否可见或不可见

2. 伪类（Pseudo-classes）：

   - CSS伪类用于向某些选择器添加特殊的效果

   - 语法：

     选择器：伪类{属性：属性值}

   - 锚伪类：

     1. a：link    未访问的连接（没有点击）
     2. a：visited  已访问的连接 （点击过后）
     3. a：hover   鼠标悬停状态 （悬浮时）
     4. a ：active  选定时 （点击时）
     5. 顺序：==l v h a==
     6. 伪类：focus    用于拥有键盘输入焦点的元素（IE8及以上才支持）

3. CSS的三大特性：

   - 层叠性
   - 继承性
   - 优先级（权重高的生效）

   1. ==层叠性==：同义元素的同一属性同一权重，写在后边的生效

      层叠的条件：有冲突才会层叠

   2. ==继承性==：如果子元素没哟定义样式，那么它默认会以父元素的样式来继承

      可继承的： 字体系列（font-）、文字系列（text-）、color、行高；

      ==a链接的样式不能通过继承实现，必须作用在他自己身上==

   3. 选择器权重：

      - id > 类 > 子代 > 后代 > 标签 > 通配符 > 继承的样式权重

      - 群组选择器是有基础选择器组成的，不参与权重计算

      - ==！important==：最高权重

      - 权重规则：

        1. 标签选择器权值：1
        2. 类、伪类、属性选择器权值：10
        3. id选择器权值：100
        4. 行内样式权值：1000
        5. 通过继承而来的权重为 0 ，继承的优先级程度比自身优先级==低==！

      - ==注意==：

        同一元素有多个css样式的话，当这些css样式有共同属性时，先比较权值，权值不同的话，权值大的共有属性值生效；权值相同的话，按照层叠的规则，最后面的css生效