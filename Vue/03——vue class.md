03——vue class

1. 使用方法：

   demo：

   ```css
   .avtive{
   		background:pink;
   	}
   	.normal{
   		background:grey;
   	}
   	.red{
   		color:red;
   	}
   ```

   ​	

   data:{

   ​	index:1

   }

   ```html
   <div id="app">
       ==:class 动态属性，可以使用表达式返回字符串结果，但容易出错，不建议使用==
       ==三元运算法：==
       <h1 class="red" :class="index==1?'active' : '' ">一级标题</h1>
       ==对象法==
       <h1 class="red" :class="{active:index==1,normal:index != 1}">一级标题</h1>
       <h1 class="red" :class="calssObj">一级标题</h1>
   </div>
   ```


```javascript
// ==绑定返回对象的计算属性==

   computed:{
   	return {
   		active:this.index==1,
   		normal:this.index != 1
   	}
   }
```