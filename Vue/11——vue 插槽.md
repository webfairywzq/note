11——vue 插槽

1. 作用：

   用来向子组件传递 DOM

   直接在模板中使用<slot></slot>

2. 插槽的默认内容：

   当子组件没有定制插槽内容时，显示默认值

3. 具名插槽：

   当需要为子组件定义多个插槽时，要使用具名插槽

   demo：

   ```javascript
   <com>
   	<h1 slot="header">插入 header 的内容</h1>
   	<h1 slot="footer">插入 footer 的内容</h1>
   </com>
   const com={
       template:`
   		<div>
   			<slot name="header"></slot>
   			<p>子组件的内容不变</p>
   			<slot name="footer"></slot>
   		</div>
   	`
   }
   ```

4. 作用域插槽：

   1. 可以让我们在创建组件时给 slot 添加一些数据

   2. 组件的使用者，可以根据对应组件去获取到组件的作者留在 slot 上的数据，并且做渲染或其他操作使用

   3. 语法使用：

      ```javascript
      1.创建组件中：
          template:`
              <div>
                  <slot a="1" b="2"></slot>
              </div>
          `
      2.使用组件时：
          <组件名>
              <template slot-scope="自定义名字(如：scope)">{{scope.a}}   {{scope.b}}</template>
          </组件名>
          或者使用解构赋值：
          <组件名>
              <template slot-scope="{a,b}">{{a}}   {{b}}</template>
          </组件名>
      ```
