CSS————CSS样式

1. 背景
   - css允许应用纯色作为背景，也允许使用背景图像创建相当复杂的效果
   - 背景属性：
     1. background ： 简写属性，作用是将背景属性设置在一个声明中
     2. background-attachment（fixed + scroll）：背景图像是否固定或随着页面的其余部分滚动；默认值为scroll，默认情况下会随文档滚动
     3. background-color：设置元素的背景颜色
     4. background-image：将图像设为背景
     5. background-position：设置背景图像的起始位置（水平：left，center，right；垂直：top，center，bottom）
     6. background-repeat（平铺）：设置背景图像是否及如何平铺（repeat-x，repeat-y，repeat，no-repeat）
2. 文本
   - 可定义文本的外观
   - 文本属性：
     1. color：设置文本颜色
     2. direction：设置文本方向
     3. line-height：设置行高（一般用来设置垂直居中）
     4. letter-spacing：设置字符间距
     5. text-align：对齐元素中的文本（用来设置水平居中）
     6. text-decoration：向文本添加修饰
     7. text-indent：缩进元素中文本的首行
     8. text-transform：控制元素中的字母
     9. white-space：设置元素中空白的处理方式
     10. word-spacing：设置字间距
   - 字符转换：
     - text-transform：处理文本大小写，有4个值：
       1. none：不做改动，使用源文档中大小写
       2. uppercase：全大写
       3. lowercase：全小写
       4. capitalize：只对每个单词首字母大写
   - 水平对齐：
     - text-align：==不会控制元素的对齐，只影响内部内容==3个值（left，center，right）
     - "center"：不仅影响文本，还会把整个元素居中
   - 字间隔：
     - word-spacing：可以改变字（单词）之间的标准间隔，其默认值==normal==与设置值为0是一样的
   - 字母间隔：
     - letter-spacing：与word-spacing区别在于：字母间隔修改的是字符或字母之间的间隔
   - 文本装饰：
     - text-decoration：5个值：
       1. none：关闭原本应用到一个元素上的所有修饰
       2. underline：对元素加下划线
       3. overline：在文本的顶端画上一个下划线
       4. line-through：在文本中间画一个贯穿线
       5. blink：会让文本闪烁
   - 处理空白符：
     - white-space：4个值：
       1. normal：会合并所有的空白符，并忽略换行符
       2. pre：浏览器不会合并空白符，也不会忽略换行符
       3. pre-wrap：浏览器不仅会保留空白符，并保留换行符，还允许自动换行
       4. pre-line：浏览器会保留换行符，并允许自动换行，但是会合并空白符
   - ==vertical-align==：图片文字的对齐方式，默认是基线对齐（top，middle…）
3. 字体：
   - 定义文本的字体系列、大小、加粗、风格（如斜体）和变形（如小型大写字母）
   - 字体属性：
     1. font-family：设置字体系列
     2. font-size：设置字体尺寸
     3. font-style：设置字体风格
        - normal：文本正常显示
        - italic：文本斜体显示
        - oblique：文本倾斜显示
     4. font-variant：（small-caps）以小型大写字体或正常字体显示文本
     5. font-weight：设置字体的粗细 （normal；bold）
4. 列表：
   - 列表属性允许你放置、改变列表项标志、或者将图像作为列表项标志
   - 列表类型：list-style-type：设置列表项标志的类型（5个值）：
     1. none：无标记
     2. disc：默认，标记为实心圆
     3. circle：标记为空心圆
     4. square：标记为实心方块
     5. decimal：标记为数字
   - 列表项图像：list-style-image：将图像设置为列表项标志（3个值）：
     1. URL：图像的路径
     2. none：默认值，无图形被显示
     3. inherit：规定应该从父元素继承list-style-image属性的值
   - 列表项标志位置：list-style-position：设置列表中列表项标志的位置（3个值）：
     1. inside：放置在文本以内，且环绕文本根据标记对齐
     2. outside：默认值，保持标记于文本左侧，放置在文本以外，且环绕文本根据标记对齐
     3. inherit：规定应该从父元素继承list-style-image属性的值
5. 表格：
   - 表格属性可以极大改善表格的外观
   - table 属性：
     1. border-collapse：设置是否把表格边框合并为单一的边框
     2. border-spacing：设置分隔单元格边框的距离
     3. caption-side：设置表格标题的位置
     4. empty-cells：设置是否显示表格中的空单元格
     5. table-layout：设置显示单元格、行和列的算法
6. 轮廓（outline）：
   - 是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用
   - 边框属性：
     1. outline：在一个声明中设置所有的轮廓属性
     2. outline-color：轮廓颜色
     3. outline-style：轮廓样式
     4. outline-width：轮廓宽度

- ==补充==：文本溢出生成省略号

  white-space：nowrap；    表示文字强制不换行

  text-overflow：ellipsis；    表示文本溢出的处理方式（ellipsis：以省略号显示）

  overflow：hidden；           溢出处理

  ==三个结合一起用==

