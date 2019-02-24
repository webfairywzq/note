06——css3 背景background-image

1. background-size（指定背景图像的大小）：

   值： length | percentage | cover | contain

   ```javascript
   1. length: 设置背景图片 宽、高；// 如果只给一个值，另一个值为 auto
   2. percentage: 计算相对于背景定位区域的百分比； // 同上
   3. cover: 此时会保持图像的横纵比，并将图像缩放成'完全覆盖背景定位区域'的 '最小' 大小
   4. contain: 会保持图像的横纵比，并将图像缩放成'适合背景定位区域'的 '最大' 大小
   ```

2. background-origin （从哪个部分开始平铺图片）：

   值： padding-box | border-box | content-box

   ```javascript
   1. padding-box: 背景图像从 '内边距左上角' 开始填充
   2. border-box: 背景图像从 '边框左上角' 开始填充
   3. content-box: 背景图像从 '内容左上角' 开始填充
   ```

3. background-clip （只平铺盒模型的哪一部分内容）：

   值： border-box | padding-box | content-box

   ```javascript
   1. border-box: (默认值) 背景绘制在边框方框内（剪切成边框方框）
   2. padding-box: 背景绘制在衬距方框内（剪切成衬距方框）'从 padding 算，不算 border'
   3. content-box: 背景绘制在内容方框内（剪切成内容方框）
   
   观察效果时：
   	1.设所有 div 为：background-origin:border-box
   	2.注意和 background-origin 的区别：
       	后者是背景图位置发生变化；为该属性是背景图位置完全一样，只是有些区域被减掉不显示
   ```

4. 补充：

   ```javascript
   repeat 和 no-repeat 时效果有区别：
   	// 一定放在背景图片设置之后才有效
   ```


