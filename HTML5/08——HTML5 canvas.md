HTML5————canvas

1. <canvas>标签定义图形，比如图表和其他图像

2. <canvas>标签只是图形容器，必须使用脚本来绘制图形

3. 使用方法：

   - canvas 绘图API 定义通过画布的 getContext() 方法获得一个"绘图环境"对象
   - var canvas = document.getElementById(id);
   - var context = canvas.getContext("2d")；
   - 默认宽高：300*150

4. 类型：

   1. 画线段：  context.moveTo(x,y)        context.lineTo(x,y)

      前面最好加上：context.beginPath();  //不会与其他影响

   2. 绘制弧度：

      canvas.arcTo(x1,y1,x2,y2,r);     //起点坐标，终点坐标，半径

   3. 绘制贝塞尔曲线：

      quadraticCurveTo(dx,dy,x1,y2)

      开始点：moveTo(20,20)

      控制点：quadraticCurveTo(20,100,200,20)

      结束点：quadraticCurveTo(20,100,200,20)

      ==注意==：二次贝塞尔曲线需要两个点

      第一个点：用于二次贝塞尔曲线计算中的控制点

      第二个点：曲线的结束点

      曲线的开始点是当前路径中最后一个点，如果路径不存在，那么使用beginPath() 和 moveTo() 方法来定义开始点

   4. 画圆弧：

      context.arc(x,y,radius,startAngle,endAngle,anticlockwise)：圆心坐标；半径；开始角度；结束角度；顺时针(false) / 逆时针(true)

   5. 画图象：

      context.drawImage(image,0,0,50,50)  ： 图片，x，y，width，height

      context.drawImage(img,0,0,45,45,0,0,200,200)：(0,0,45,45)：截取图片范围  ；(0,0,200,200)：图片绘制在画布的范围

   6. 绘制文本：

      canvas.font = "4em Arial" ; //字体属性

      canvas.fillStyle = "red" ; //颜色(文本)

      canvas.fillText('60%',90,170);  //绘制文字；