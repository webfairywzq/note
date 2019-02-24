04——JQ 核心方法 CSS方法

1. jquery 的核心方法：

   ```javascript
   $.each(数据集合,function(index,val){
       // 如果是 DOM 集合的遍历， val 代表每个原生 dom 对象
       $(val);
   })
   
   $().size();
   $().index();
   $().data();
   	// 如何自定义 dom 属性
   		$().data("index",1);
   	// 如何获取自定义 dom 属性或自定义标签属性
   		<div data-type="goods">...</div>
   		var result = $().data("type");
   ```

2. jquery 的 CSS 方法：

   ```javascript
   $().offset().top;   $().offset().left;
   $().positon().top;
   $("p").scrollTop();
   $("window").scrollTop();
   $("p").scrollTop(300);
   $("p").animate({
       scrollTop:0
   }); // 针对窗口滚动的过渡动画
   
   $("html,body").animate({
       scrollTOp:0
   })
   
   $().width();
   $(window).width();
   
   $().innerWidth();
   $().outerWidth();
   ```
