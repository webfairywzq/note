CSS————css盒模型

1. 盒模型：
   - 标准盒模型
   - IE盒模型
   - 区别：==IE的内容区 包括：padding 和 border==

2. 盒模型 宽、高

   - 紧贴内容的左上角是宽高的起点
   - 行内元素设置宽、高无效；除非用 ==display:block;== 转为块元素 或  ==display:inline-block;== 转为行内块元素
   - 行内元素不支持上下padding

   - 盒子真实占有的宽度 = 你设置的宽度 + 左右padding + 左右border + 左右margin
   - 盒子真实占有的高度 = 你设置的高度 + 上下padding + 上下border + 上下margin

3. margin-top的穿透问题：

   父级有背景色，第一个子级也有背景色，给第一个子级添加margin-top就会产生穿透；后边子级无影响

   解决方法：

   1. 给父级添加一个border
   2. 使用padding-top代替margin-top（给父级添加padding-top，相应的高度减去padding-top的值）
   3. 使用 overflow:hidden;  添加到父级
      - 这种方法弊端：如果有文字、内容溢出，会被隐藏；

