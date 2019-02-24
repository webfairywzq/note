02——vue 计算属性-方法-监听器

1. 

2. 计算属性：

   - demo：

     ```html
     <div id="app">
         <p>messasge:{{msg}}</p>
         <p>reversemessasge:{{reversemsg}}</p>
         <span>{{firstName}}</span>
         <span>{{lastName}}</span>
         <p>{{name}}</p>
     </div>
     ```

     ```javascript
     data:{
     	msg:"hello world",
     	firstName:"张",lastName:"三"
     },   //==对于复杂的逻辑运算，应写入计算属性==
         
     computed:{
     	reversemsg:function(){  //对应的是计算属性中的 get 方法
            return this,msg.split(' ').reverse().join(' ');  // ==一定有返回值，返回计算后的值==
     	},
         name:{
             //name 为计算属性
             get:function(){
             //  ==get 方法一定要有返回值==
             return  this.firstName+ ' ' + this.lastName;			
         },
         set : function(newValue){
             //  set 方法可以将依赖的数据属性同时更改
             var  names = newValue.split(' ');
             this.firstName = names[0];
             this.lastName = names[names.length-1];
         }
     
     }
     ```

   - 计算属性使用场景（总结）：
     1. 当属性值需要经过复杂运算才能得到的时候用计算属性
     2. 计算属性的属性值为对象的话，对象中一定有 set 或 get 属性，属性名不能改变
     3. 计算属性的属性值为函数的话，对应的就是 get 方法
     4. get 方法一定有返回值
     5. 如果想要对计算属性设置新值，一定要有 set 方法，set 方法一定会有对依赖属性的赋值

3. computed 与 methods：

   看例子

   ```html
   <div id="app">
      	<p> message:{{msg}} </p>
       <p> reversemessage:{{revermsg}} </p> // 对应 computed
       <p> reversemessage:{{revermsg()}} </p> // 对应 methods
       <span>{{firstName}}</span>
       <p> {{now}} </p>
   </div>
   ```

   ```javascript
   data:{
   	msg:'hello world',
   	firstName:'张',
   	lastName:'三'
   }，
   
   //对于 methods 来说，只要模板中的值发生改变， methods 就会执行一遍，若 methods 中是复杂的运算，每次就会重新计算，耗计算资源
   methods:{
   	reversemsg(){
   	return this.msg.split(' ').reverse().join(' ');
   	}
   }
   //计算属性只有当计算属性以来的 data 属性发生改变时，才会重新计算值，否则直接从缓存中拿，节省计算资源
    computed:{
   	reversemsg: function(){
   	return this.msg.split(' ').reverse().join(' ');
   },
   now(){    
   	// ==得到的总是第一次计算的时间==
   	return Date.now();  
   	}
   }
   ```

4. watch 与 computed:

   - watch：指当某个属性发生变化的时候，执行相应的函数

   - demo：

     ```html
     <div id="app">
         {{fullName}}
     </div>
     ```

     ```javascript
     data:{
         firstName:'Foo',
         lastName:'Bar',
         fullName:'Foo Bar'     //  ==对应 watch 中的 this.fullName==	
     }
     
     //  ==data 属性发生改变时，执行相应的函数==
     watch:{
     	//==watch 中的属性名一定在 data 中存在==
     	firstName(){
     	this.fullName = this.firstName + " "+ this.lastName;
     	},
     	lastName(){
     		this.fullName = this.firstName + " "+ this.lastName;
     	}
     }
     ```

```javascript
 // ==对比显示，computed 属性能够解决大部分的情况==

 computed:{
 	//==计算属性中的属性名与 data 中的属性名不能重名==
 	fullName(){
 		return this.fullName = this.firstName + " "+ this.lastName;
 	}
 }
```

4. 函数节流、函数防抖（节约计算资源）

   1. 函数节流（throttle）：

      指定时间间隔内只会执行一次任务

      （就是每隔一段时间去执行一次原本需要无时无刻不在执行的函数）

   2. 函数防抖（debounce）：

      任务频繁触发的情况下，只有任务触发的间隔超过指定间隔的时候，任务才会执行

   3. demo：

      ```html
      <div id="app">
          <input type="search" v-model="keyword">
      </div>
      ```

      ```javascript
      data:{
          keyword:" ",
          flag:true
      }
      
      watch:{
      	keyword(){
      		if(this.flag){
      			this.flag=false;
      			setTimeout(()=>{
      				console.log(this.keyword);
      				this.flag=true;
      			},500)  // 500ms 后执行
      		}
      	}
      }
      ```





​	







