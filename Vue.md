<img src="D:\img\image-20210624144832163.png" alt="image-20210624144832163" style="zoom:50%;" />

# 一、Vue概述

## 1.1 认识Vuejs

- Vue是一套用于构建用户界面的**渐进式框架**。
  - 渐进式意味着你可以将Vue作为你应用的一部分==嵌入其中==，拥有更丰富的交互体验。
  - 如果希望用Vue实现更多的业务多级，可以使用Vue核心库及生态系统：Core+Vue-router+Vuex
- Vue 被设计为可以自底向上逐层应用。
- Vue 的核心库只关注视图层。

## 1.2 Vuejs安装方式

- 直接CDN进入

  - 开发环境版本
  - 生产环境版本

  <img src="D:\img\image-20210624153614112.png" alt="image-20210624153614112" style="zoom:50%;" />

- 下载和引入

  ![image-20210624153707675](D:\img\image-20210624153707675.png)

- NPM安装（推荐）

  在用 Vue 构建大型应用时推荐使用 npm 安装[[1\]](https://v3.cn.vuejs.org/guide/installation.html#footnote-1) 。npm 能很好地和诸如 [webpack](https://webpack.js.org/) 或 [Rollup](https://rollupjs.org/) 模块打包器配合使用。

  

## 1.3 Vuejs初体验

### 案例一：

①下载并引入vue.js

![image-20210624154906867](D:\img\image-20210624154906867.png)②创建vue实例，挂载并解析元素，在data中找对应属性并注入到元素

```html
<body>
    <div id="app">
        {{message}}
    </div>
    <script src="../js/vue.js"></script>
    <script>
        //不需要该这个实例，所以用常亮表示
        const app=new Vue({
            el:"#app",//用于挂在要管理的元素
            data:{
                message:"hello"
            }
        });
    </script>
</body>
```

- 创建Vue对象的时候，传入了一些options。

  - el属性：决定了Vue对象挂载到哪个元素上。

    ```
    el:"#app"
    ```

    ==类名.	id#==

  - data属性：储存数据，可以是自定义的，也可以是从服务器加载的。

  - methods：定义处理函数



### 案例二：vue的列表展示

```html
<body>
    <div id="app">
        <ul>
            <li v-for="item in foods">
                {{item}}
            </li>
        </ul>
    </div>
    <script src="../js/vue.js"></script>
    <script>
        const app=new Vue({
            el:"#app",
            data: {
                foods:['apple','pork','milk']
            }
        });
    </script>
</body>
```

循环v-for

### 案例三：计数器

```html
<body>
<div id="app">
    <h2>当前计数：{{counter}}</h2>
    <button v-on:click="add">+</button>
<!--    @ 是 v-on: 的简写-->
    <button @click="sub">-</button>
</div>
<script src="../js/vue.js"></script>
<script>
    const app=new Vue({
        el:"#app",
        data:{
            counter: 0
        },
        methods:{
            add:function(){
                this.counter++;
            },
            sub:function(){
                this.counter--;
            }
        }
    })
</script>
</body>
```

==@ 是 v-on: 的简写==：代表监听事件

### 1.4 mvvm

![![image-20210624094647822](D:\img\image-20210624094647822.png)](D:\img\image-20210624085839164.png)

![image-20210624094647822](D:\img\image-20210624094647822.png)

![image-20210624170224821](D:\img\image-20210624170224821.png)

























1.4 Vuejs的MVVM







































