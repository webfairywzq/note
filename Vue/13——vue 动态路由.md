13——vue 动态路由

1. ==能够提供参数的路由== 即为动态路由

2. 路由地址相同，都是要请求同一个组件，但携带的参数不同，请求数据类型不同

3. demo：

   - 需求：

     图书商品： /goods?type=book

     汽车商品：/goods?type=car

     美食商品：/goods?type=food

   - 步骤：

     1. 定义组件 Goods

        ==在动态路由组件中，接收到动态路由参数==

        ![动态路由-1](E:\wzq\笔记(电子版)\Vue\动态路由-1.PNG)	

        ==当我们把 router 添加到 new Vue 后，在 vue 的每个组件中的 data 中都会有一个 $route==

     2. 配置路由、创建路由对象 router、将router 放入 new Vue 中：

        1. ![动态路由-2](E:\wzq\笔记(电子版)\Vue\动态路由-2.PNG)	

     3. 模板：

        1. ![动态路由-3](E:\wzq\笔记(电子版)\Vue\动态路由-3.PNG)

4. 总结：

   - 当单击“图书商品”时，切换到 /goods 路由，同时将参数值 book 传给路由中的type 参数（即 type=book）
   - 在 router-view 中显示 Goods 组件，同时在组件内部可通过 ==this.$route.params== 得到参数
   - 不论怎么修改 ？ 后的内容，组件都不会再重新触发钩子函数了（==若想在 js 中获取到新的 query 值，需监听 $route 的改变==）

5. 监听路由变化：

   ```javascript
   const Goods={
   	template:``,
   	watch:{
   		'$route':{
   			handler(to){
   				console.log(to.query);
   				//  ==to 是一个路由对象 （$route），可以直接通过 to 获取到新的参数==
   			}
   			immediate:true
   			// immediate:true （默认为 false） 代表是否以当前的初始值执行 handler 的函数
   		}
   	}
   }
   ```

