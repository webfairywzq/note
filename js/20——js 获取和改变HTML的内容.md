20——js 获取和改变HTML的内容

1. DOM 对象是一个对象，能够操作对象的方式就可以操作 DOM 对象

   DOM 对象中一些属性和页面相关联

2. 获取和改变 HTML 元素的内容：

   ```javascript
   1.获取页面上的内容：
   	DOM.innerHTML;
   	DOM.innerText;
   2.改变页面上的内容：
   	DOM.innerHTML = "新的内容";
   	DOM.innerText = "新内容";
   3.innerHTML,innerText 区别：
   	★.在获取内容时：
   		// 在使用 innerHTML 时，可以获取到对应的 DOM 对象中包含的标签及内容
   		// 在使用 innerText 时，只能获取到对应的 DOM 对象中的文本
   	★.在改变内容时：
   		// 在使用 innerHTML 时，可以将对应内容中的 html 标签渲染至页面作为标签使用
   		// 在使用 innerText 时，对应的标签只会被当做纯文本显示在页面上
   4.补充：
   	（outerHTML、outerText）----不兼容 Firefor 浏览器
       ★.在获取内容时：
   		innerHTML 和 outerHTML 相比：少了相关的 DOM 对象的标签（outerHTML 可以获取到相关的 DOM 对								   象标签）
            innerText 和 outerText 没有任何区别
       ★.在改变内容时：
   		 outerHTML 会替换对应的设置该属性的 DOM 对象，innerHTML 不会；
             innerText 和 outerText 相比：outerText 会替换掉相关的 DOM 元素
   ```

3. 获取和改变表单元素的内容：

   ★.通过 DOM.value ：可以获取相关表单元素中的内容

   ★.通过 DOM.value="新的内容"：可以设置表单元素中的内容