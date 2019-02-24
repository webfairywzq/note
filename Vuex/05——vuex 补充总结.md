05——vuex 补充总结

1. 补充：

   - 扩展运算符（...）

     1. 功能：

        把数组或类数组对象展开成一系列用逗号隔开的值

     2. demo：

        ```javascript
        var arr = [1,2,3,4];
        var arr2 = [7,8,9];
        const arr3 = [...arr2,...arr];
        console.log(arr3); // [7,8,9,1,2,3,4]
        ```

   - 解构：

     1. 作用：

        可以快速取得数组或对象当中的元素或属性，而无需使用 arr[x] 或 obj[key] 等传统方式进行赋值

     2. demo：

        ```javascript
        var arr = ['this is a string',2,3];
        var [a,b,c] = arr;
        console.log(a);  // this is a string
        console.log(b);  // 2
        console.log(c);  // 3
        ```

2. 总结：

   - Vuex 工作流程：

   ![Vuex 工作流程](E:\wzq\笔记(电子版)\Vuex\Vuex 工作流程.png)	

   1. 在 vue 组件中，通过 dispatch 来触发 actions 提交修改数据的操作
   2. 再通过 actions 的 commit 来触发 mutations 来修改数据  ==（将请求到的数据提交给 mutations）==
   3. mutations 接收到 commit 的请求，就会自动通过 mutate 来修改 state （数据中心里面的数据状态）里面的数据
   4. 最后由 state 触发每一个调用它的组件的更新  ==（state 修改后渲染到 Vue 组件）==

   - 具体：

     1. state：用于存储组件数据（状态）

     2. getter：用于从 state 或其他 getter 中获取数据

     3. mutation：修改 state

        需要靠 store.commit('mutation',传递数据)

     4. action：异步请求数据，获取数据后，commit mutation

        需要靠 store.dispatch('action',传递数据)

        dispatch 在组件中调用一般为：

        this.$store.dispatch('action',数据)