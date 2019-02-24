21——js 改变HTML属性

1. 获取 HTML  属性的情况：

   ```javascript
   1.HTML 属性不是关键字或保留字，同时，是 HTML 原生的属性：
   	DOM.属性名
   2.HTML 属性是关键字或保留字，可以找到相关的别名：
   	DOM.className
   3.HTML 属性是关键字或保留字，同时没有相关别名：
   	DOM.getAttribute('属性名')
   4.HTML 自定义属性：
   	DOM.getAttribute('自定义属性名')
   ```

2. 设置 HTML 相关属性：

   ```javascript
   1.清空 className
   	DOM.className="";
   2.设置多个 className：
   	DOM.className = "box1 box2 box3";
   3.如果属性是 HTML 原生属性，可以直接改变 DOM 对应的属性名来改变对应的 HTML 属性：
   	DOM.HTML属性名 = "新的属性值";
   4.如果属性是原生属性，但是属性在 js 中属于关键字或保留字：
   	DOM.别名 = "新的属性值";
   5.如果属性是 HTML 原生属性，同时属性是js 中的关键字或保留字，而且 DOM 中没有相关别名：
   	DOM.setAttribute('属性名','属性值');
   6.如果属性不是 HTML 的原生属性：
   	DOM.setAttribute('自定义属性名','属性值');
   7.可以给对应的 DOM 对象所对应的 HTML 元素中添加相关属性：
   	DOM.自定义属性名 = '属性值';
   // 补充：
    DOM.className = 'box4'; // 添加类名，覆盖原本存在的类名；若本无类名，则直接添加
    DOM.className = DOM.className + " " + cname; // （cname 新类名） 原类名不会被覆盖'
   ```

