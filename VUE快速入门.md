![image-20210624085839164](D:\img\image-20210624085839164.png)

## MVVM

![image-20210624094647822](D:\img\image-20210624094647822.png)

双向绑定







## 1.第一个vue程序

```html
<body>
<div id="app">
    {{message}}
</div>

<!--导入vue.js-->
<script src="https://unpkg.com/vue/dist/vue.js"></script>
<script>
    var vm=new Vue({
        //document.getElementById，绑定元素
        el:"#app",
        //data是调用后端接口后拿到的数据
        data:{
            message:"hello vue"
        }
    });
</script>
</body>
```

在控制台对对象属性操作，界面可以实时更新





## 2.vue基本语法

​		前端拿到数据：①判断后显示；②循环显示

```html
<body>
    <div id="app">
        <!-- 将message属性通过v-bind绑定到title -->
        <span v-bind:title="message">
            查看动态绑定信息
        </span>
    </div>
    
    <!--导入vue.js-->
    <script src="https://unpkg.com/vue/dist/vue.js"></script>
    <script>
        var vm=new Vue({
            //document.getElementById
            el:"#app",
            //data是调用后端接口后拿到的数据
            data:{
                message:"页面加载于"+new Date().toLocaleString()
            }
        });
    </script>
</body>
```

- v-bind等被称为指令，指令一般带有前缀v-.

- ```html
  <span v-bind:title="message">
  ```

  该指令的意思是：将这个元素节点的title特性和Vue实例里的massage属性保持一致

- data:里面的属性不要加;



### 2.1 判断(v-if)

```html
<body>
    <div id="app">
        <!-- 判断---循环 -->
        <h1 v-if="type==='A'">A</h1>
        <h1 v-else-if="type==='B'">B</h1>
        <h1 v-else="type==='C'">C</h1>
    </div>
    
    <!--导入vue.js-->
    <script src="https://unpkg.com/vue/dist/vue.js"></script>
    <script>
        var vm=new Vue({
            //document.getElementById
            el:"#app",
            //data是调用后端接口后拿到的数据
            data:{
                type:"A"
            }
        });
    </script>
</body>
```

### 2.2 循环(v-for)

```html
<body>
    <div id="app">
        <li v-for="item in items">
            {{item.message}}
        </li>
    </div>
    
    <!--导入vue.js-->
    <script src="https://unpkg.com/vue/dist/vue.js"></script>
    <script>
        var vm=new Vue({
            //绑定元素
            el:"#app",
            data:{
                items:[
                    {message:"1"},
                    {message:"2"},
                    {message:"3"}
                ]
            }
        });
    </script>
</body>
```

### 2.3 绑定事件

#### 监听事件：

​		我们可以使用 `v-on` 指令 (通常缩写为 `@` 符号) 来监听 DOM 事件，并在触发事件时执行一些 JavaScript。用法为 `v-on:click="methodName"` 或使用快捷方式 `@click="methodName"`

#### 定义方法

​		方法必须定义在Vue的method对象中。



















3.Vue绑定事件

4.Vue双向绑定

5.Vue组件



















