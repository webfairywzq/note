05——vue 表单的双向绑定-表单应用的修饰符

1. 表单应用的修饰符：

   1. .lazy：

      在默认情况下，v-model 在每次 input 事件触发后将输入框的值与数据进行同步（除输入法组合文字时），可添加 lazy 修饰符，从而转变为使用 change 事件进行同步

      ==在 change 时而非 input 时更新==

      <input v-model.lazy="msg">

   2. .number：

      如果想自动将用户的输入值转为数值类型，可以添加 number 修饰符

      <input v-model.number="age" type="number">{{age+12}}

      ==即使在 type="number" 时，HTML 输入元素的值也总会返回字符串，因此必要时使用 .number

   3. .trim：

      如果想自动过滤用户输入的首尾空白字符，可以添加 trim 修饰符

      <input v-model.trim="msg">{{'--' + msg + '--'}}

2. 表单的双向绑定：

   1. 存在 v-model，对于value，checked，selected 就不起作用

      不存在 v-model，可以使用  ：checked="true"选中  ：checked="false" 未选中

   2. 静态属性    checked="false"  checked="true"  ,只要有checked 属性，都是选中状态，值是什么无所谓

   3. 双向绑定：

      - 改变 dom 状态，影响值：

        1. 多个复选框，多选下拉菜单，绑定的属性值一定是空数组
        2. 多个单选框，单个下拉菜单，绑定的属性值为字符串类型的
        3. 单个复选框，绑定的属性值为 bool 类型，得到的值就是 true，false

      - 设置值也会影响 dom 的状态：

        1. 多个复选框，多选下拉菜单，设置的值是数组类型的，并且里面的值一定跟多选的 value 和下拉菜单的 value 值对应

        2. 多个单选框，单个下拉菜单，设置的值一定是选中的 value 值

        3. 单个单选： value="a"  v-model="v"

           ​	设置的 v 的值一定是 a 才会被选中

        4. 单个多选： 设置的初始值为true 或 false 就可以了

        5. true-value ="yes" ,false-value="no"  设置初始值可以为 yes 或 no