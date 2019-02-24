HTML5————基础知识

1. 实际像素 / 倍率 = 逻辑像素尺寸

   - 只要两个屏幕逻辑像素相同，显示效果就是相同的（决定显示效果的，是逻辑像素尺寸）

2. 移动端必用meta标签

   <meta name="viewport" content="width=device-width,maximum-scale=1.0,minimum-scale=1.0,initial-scale=1.0,user-scalable=no">

   - viewport：浏览器可视区域的大小
   - width=device-width ：视口宽度 = 设备宽度（设备尺寸即逻辑尺寸）
   - user-scalable=no ：禁止缩放

3. 移动端相对长度单位：

   - em：描述相对于应用在当前元素的字体尺寸
   - rem：根元素（html）的font-size
   - vw：viewpoint width：视窗宽度     1vw=视窗宽度的1%
   - vh：viewpoint height ：视窗高度   1vh=视窗高度的1%
   - vmin：vw 和 vh 中较小的那个
   - vmax：vw 和 vh 中较大的那个  如：宽度>高度，则 1vmax = 宽度的1%
   - %：相对于父元素的百分比

4. 注意事项：

   - chrome 浏览器最小字号 12px 若需更小字号 可对装文本的盒子设置：transform：scale（.8）；
   - 背景图片一定要设置 ==background-size==
   - 边框太细在某些小屏手机不显示
   - ==img { vertical-algin：top }==

5. rem的使用：

   - 假设PSD原稿为750px宽，其中banner 为750px 宽，.box中文字为38px

     1. 750px宽屏幕中：html { font-size：100px }

        .banner { width：7.5rem }     .box { font-size：0.38rem }

     2. 375px宽屏幕中：html { font-size：50px } -----------  ==375 / 7.5=50px==

        .banner { width：7.5rem }     .box { font-size：0.38rem }

     3. 360px宽屏幕中：html { font-size：48px }------------- ==360 / 7.5=48px==

6. 低版本IE如何支持HTML5标签：

   ==引入“  html5shiv.js ”==

   html5shiv.js通过javascript来创建HTML5元素

   - <!--[ if It IE 9] >

     <script src="js/html5shiv.js">
     
     </script>

     <![ end if ] -- >

   - ==一定要加在head标签中==