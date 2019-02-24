03——JQ DOM操作  方法

1. DOM 操作（掌握）：

   ```javascript
   1.// 访问元素内容
   	$().html();
   	$().text();
   	$().val();
   2.// 访问元素的标签属性 <img src="" >
   	$().attr("src");
   	$().attr("src","");
       $().attr({
           "src":""
       });
   	// 针对复选框的 checked 属性
   		$().prop("checked",true);
   3.// 访问元素的样式
   	$().css();
   4.// 访问元素的类名
   	$().addClass().removeClass().toggleClass("cur");
   ```

2. 筛选方法（掌握）：

   ```javascript
   $().eq();
   $().next();
   $().prev();
   $().parent();
   $().children();
   $().siblings();
   $().find();
   $().filter();
   ```

3. 文档处理方法：

   ```javascript
   $().append();
   $().after();
   $().remove();
   $().empty();
   $().clone();
   ```
