HTML5————SVG

1. svg：基于XML（可扩展标记语言）描述的矢量图形格式

   （ Scalable Vector  Graphics：可伸缩矢量图形）

2. 与其他图像相比，优势：

   - 可被非常多的工具读取和修改（如记事本）
   - 与JPEG和GIF相比，尺寸更小，可压缩性更强
   - 可伸缩的
   - 可在任何的分辨率下被高质量地打印
   - 可在图像质量不下降的情况下被放大
   - 图像中的文本是可选的，也可搜索（适合制作地图）
   - 可与Java 技术一起运行
   - 是开放的标准
   - SVG 文件是纯粹的 XML 

3. 使用方式：

   - 浏览器直接打开（.svg文件）
   - 在HTML中使用<img>标签引用
   - 直接HTML中使用SVG标签
   - 作为CSS背景

4. SVG预定的形状元素

   - <rect> 矩形
   - <circle>圆形
   - <ellipse>椭圆
   - <line>线
   - <polyline>折线
   - <polygon>多边形
   - <path>路径

5. 基本属性：

   - fill：填充
   - stroke：描边
   - stroke-width：指定宽度
   - transform：变换

6. 路径：

   path元素的形状通过属性 "d" 定义 d的值是一个‘命令+参数’的序列

7. ==学习网址==：

   justcode.ikeepstudying.com/2015/07/svg矢量绘图-path路径详解