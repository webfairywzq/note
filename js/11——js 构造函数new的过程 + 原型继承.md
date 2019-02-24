11——js 构造函数new的过程 + 原型继承

1. 构造函数 new 实例化对象的过程：

   1. 先在内存中创建一个空的实例对象

   2. 让构造函数的 this 指向该实例化对象

   3. 执行构造函数：

      若构造函数中属性为： this.say = function(){}; 该过程为：

      先定义函数，将该函数的地址存入 this.say 中，调用时根据地址去执行该函数

   4. 返回该实例化对象

2. 原型继承 ==（十分重要）==

   每个函数 Sub 都有一个属性 prototype，prototype 指向一个原型对象，原型对象中也有一个指向函数的属性 constructor，通过 new 一个函数 Sub 可以产生实例 instance，调用这个 instance 的某个属性或方法时，instance 会先查找自身是否有这个方法或属性。没有的话就会去实例的构造函数 Sub 的原型 prototype 中查找，即 Sub.prototype，如果给原型对象 Sub.prototype 赋予另一个类型的实例 superInstance，则是在 superInstance 中查找的，这个 superInstance 中也有属性 prototype 指向某个原型对象。以此一级级往上最终到 Object.prototype，这样就形成了原型继承。

