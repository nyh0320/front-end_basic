# 1函数

​	函数为了更好的封装，封装为了**更好的复用**

## 1.概念

​	

## 2.使用

​	封装了一段

## 3.参数

## 4.返回值

5.arguments的使用

6.函数案例

7.两种声明方式











































# 作用域





## 1.作用域

- 作用域（scope），程序设计概念，通常来说，一段程序代码中所用到的名字并不总是有效/可用的，而限定这个名字的可用性的代码范围就是这个名字的作用域。
- 作用域的使用提高了程序逻辑的局部性，增强程序的可靠性，减少名字冲突。

- 全局作用域：
  - 整个script标签或者一个单独的JS文件
- 局部作用域
  - 在函数内部就是局部作用域

## 2.变量的作用域

- 全局变量
  - 在全局作用域下的变量，在任何位置都可以使用
  - 在函数内部没有声明直接赋值的变量，函数调用后，也属于全局变量
  - 当浏览器关闭才会销毁
- 局部变量
  - 在局部作用域下的变量
  - 函数的形参也是局部变量
  - 当函数结束销毁

## 3.作用域链

- 用域链：内部函数访问外部函数的变量采取的是链式查找方式来决定取哪个值

- 就近原则，由里及表，一层层往外找

  ```html
  <script>   
      function fun3(){
          var num=123
          function fun4(){
              console.log(num);//一层层往外找
          }
          fun4();
      }
  
      var num=555
      fun3();
  </script>
  ```

  预解析

  变量预解析与函数预解析

  

  

















# DOM

## 1.DOM简介

### 1.1什么是DOM

- DOM，全称Document Object Model,==文档对象模型==，是HTML的标准==编程接口==；
- JS通过DOM接口来对HTML文档进行操作，改变网页的内容、结构和样式。





### 1.2 DOM树

<img src="D:\img\image-20210622141910129.png" alt="image-20210622141910129" style="zoom:50%;" />

- 文档
  - 文档表示整个HTML页面文档
- 对象
  - 网页中的每一个部分都转化为了一个对象（一切皆对象，便于操作）
- 模型
  - 使用模型来表示对象之间的关系，方便我们获取对象
- 元素
  - 网页中所有的==标签==都是元素（element）
- ==节点==

<img src="D:\img\image-20210622110056676.png" alt="image-20210622110056676" style="zoom:50%;" />

<img src="D:\img\image-20210622111830433.png" alt="image-20210622111830433" style="zoom:50%;" />

一切皆对象，节点也看做是对象。

<img src="D:\img\image-20210622112221011.png" alt="image-20210622112221011" style="zoom:50%;" />

## 2.获取元素

​		想要操作某个元素，首先要获取。获取方式如下：

### 2.1 根据ID获取

​		`Document`的方法 `getElementById()`返回一个匹配特定 [ID](https://developer.mozilla.org/en-US/docs/Web/API/Element/id)的元素. 由于元素的 ID 在大部分情况下要求是独一无二的，这个方法自然而然地成为了一个高效查找特定元素的方法。

==语法：==

```html
var element = document.getElementById(id);
```

==参数：==

- **`element`**是一个 [Element](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 对象。如果当前文档中拥有特定ID的元素不存在则返回null.
- **`id`**是大小写敏感的字符串，代表了所要查找的元素的唯一ID.

==返回值：==

返回一个匹配到 ID 的 DOM `Element`对象，若在当前Document下没有找到，则返回null

`console.dir`可以打印返回的元素对

### 2.2 根据标签名获取

- `getElementsByTagName`获取，返回的是获取的元素对象的集合，以伪数组形式存储，可以采取遍历方式依次打印。

```html
for (let i = 0; i < 3; i++) {
	console.log(lis[i])
 }
```

- 如果页面中没有这个元素，返回空的伪数组

- 还可以获取某个父元素内部所有指定标签名的子元素（==父元素必须是单个对象==）

  ```
  var ol=document.getElementById("ol");
  console.log(ol.getElementsByTagName("li"));
  ```

  

### 2.3 H5新增的方法获取

- 根据类名返回元素对象集合（`getElementsByClassName`）

  ```
  var boxs=document.getElementsByClassName("box");
  ```

- 返回指定选择器的==第一个元素==（`querySelector`）

  ```
  var fristBox=document.querySelector(".box");
  ```

  ==注意==输入的选择器参数需要加符号--类.  id#

- 返回指定选择器的==所有元素==对象集合（`querySelectorAll`）

  ```
  var boxs=document.querySelectorAll(".box");
  ```

### 2.4 获取body和html元素

- 获取body元素

  ```
  document.body;//返回body元素对象
  ```

- ==获取html元素==

  ```
  document.documentElement;
  ```

## 3.事件基础

### 3.1 事件概述

​		页面中的每个元素都可以产生某些可以出发JS的事件，如点击按钮时产生某些事件，然后执行某些操作。

​		可以理解为：==触发-----响应机制==



**事件三要素：**

```html
<button id="btn">唐伯虎</button>
<script>
    //事件源：被触发的对象（如按钮）
    var btn=document.getElementById("btn");

    //事件类型：如何触发，什么事件（如鼠标点击onclick）

    //事件处理程序：通过函数赋值
    btn.onclick=function(){
        alert("点秋香");
    }
</script>
```

### 3.2 执行事件的步骤

①获取事件源

②注册（绑定）事件

③添加事件处理程序（采取函数赋值形式）



学会分析事件的三要素，如：

下拉菜单

关闭广告

### 3.3 常见的鼠标事件

![image-20210622154337277](D:\img\image-20210622154337277.png)

## 4.元素操作









### 4.1 改变元素内容

①`element.innerText`：

​		从起始位置到终止位置的内容，但去除==html标签、空格和换行==。

②`element.innerHTML`

​		起始位置到终止位置的内容（==能识别HTML标签==）。

两个属性都是可读写的：

```html
<script>
    var p=document.querySelector("p");
    console.log(p.innerText);
</script>
```



==案例：==

①点击按钮，显示当前系统时间

```html
<script>
    //需求：点击了按钮，div文字会变化
    //获取元素（两个）
    var btn=document.querySelector("button");
    var div=document.querySelector("div");
    //注册事件
    btn.onclick=function(){
        //添加事件处理程序
        //调用函数获取当前时间（字符串格式，修改标签内容）
        div.innerText=getDate();
    }

    //获取当前时间的函数
    function getDate(){
        var date=new Date();
        var year=date.getFullYear();
        var month=date.getMonth()+1;//返回值是0-11
        var dates=date.getDate();
        var arr=['星期日','星期一','星期二','星期三','星期四','星期五','星期六'];
        var day=date.getDay();
        return '今天是：'+year+'年'+month+'月'+dates+'日'+arr[day];
    }
</script>
```

②打开页面即显示当前时间

```
//打开页面即显示当前时间（不添加事件）
var p=document.querySelector("p");
p.innerText=getDate();
```

### 4.2 常用元素的属性操作

①点击按钮修改图片：修改src内容

```html
<body>
    <button id="lv">绿色</button>
    <button id="huang">黄昏</button>
    <img src="../images/1.png" alt="">

    <script>
        //修改元素属性src
        //1.获取元素（三个）
        var lv=document.getElementById("lv");
        var huang=document.getElementById("huang");
        var img=document.querySelector("img");
        //2.注册事件
        huang.onclick=function(){
            //3.处理程序
            img.src="../images/2.png";
        }
        lv.onclick=function(){
            //3.处理程序
            img.src="../images/1.png";
        }
    </script>
</body>
```

②分时问候案例：分时显示不同图片，不同问候语

```html
<body>
    <img src="../images/1.png" alt="">
    <div>绿色山谷，早上好！</div>
    <script>
        //1.获取元素
        var img=document.querySelector("img");
        var div=document.querySelector("div");
        //2.得到当前的小时数
        var date=new Date();
        var hours=date.getHours();
        //3.判断小时数，改变图片和问候语
        if(hours<12){
            img.src="../images/1.png";
            div.innerHTML="绿色山谷，早上好！";
        }else if (hours<18) {
            img.src="../images/2.png";
            div.innerHTML="黄昏小镇，下午好！";
        } else {
            img.src="../images/3.png";
            div.innerHTML="钟楼，下午好！"; 
        }

    </script>
</body>
```

### 4.3 表单元素的属性操作

​	利用DOM可以操作如下表单元素的属性：

```
type、value、checked、selected、disabled
```

```html
<body>
    <button>按钮</button>
    <input type="text" value="输入内容">
    <script>
        //1.获取元素
        var btn=document.querySelector("button");
        var input=document.querySelector("input");
        //2.注册事件
        btn.onclick=function(){
            //表单的文字在value属性中
            input.value="呵呵哒";
            //想要表单只能提交一次（即按钮只使用一次）
            //btn.disabled=true;
            this.disabled=true;//this指函数调用者
        }
    </script>
</body>
```

<img src="D:\img\image-20210622182030550.png" alt="image-20210622182030550" style="zoom:50%;" />



**案例：显示隐藏密码明文案例**

<img src="D:\img\image-20210622182122037.png" alt="image-20210622182122037" style="zoom:50%;" />

思路：

①点击眼睛按钮，把密码框类型修改为文本框（即修改元素属性）

②一个按钮两个状态（利用flag来记录状态）

```html
<body>
    <div class="box">
        <img src="../images/开眼.jpg" alt="显示密码" id="eye">
        <label for=""></label>
        <input type="password" name="" id="pwd">
    </div>

    <script>
        //1.获取元素
        var eye=document.getElementById("eye");
        var pwd=document.getElementById("pwd");
        //2.注册事件
        var flag=0;
        eye.onclick=function(){
            if(flag==0){
                pwd.type="text";
                eye.src="../images/闭眼.jpg";
                eye.alt="隐藏密码";
                flag=1;
            }else{
                pwd.type="password";
                eye.src="../images/开眼.jpg";
                eye.alt="显示密码";
                flag=0;
            }
        }
    </script>
</body>
```

### 4.4 修改样式属性

​		可以通过JS修改元素的大小、颜色、位置等样式。

#### ①行内样式操作（element.style）

​		==样式少，功能简单的情况下使用。==

```html
<script>
    var div=document.querySelector("div");
    div.onclick=function(){
        //属性是驼峰命名
        this.style.backgroundColor='purple';
        this.style.width="400px";
    }
</script>
```

JS里面的样式采取驼峰命名法

案例练习：

①仿淘宝关闭二维码

②循环精灵图

③显示隐藏文本框内容

#### ②类名样式操作

​		给元素（先获取元素对象）添加类名，将样式抽取到css（根据类名）。适合样式多或者功能复杂的情况（==解耦思想==）。

​		如果元素已经有类型，则会覆盖。

```html
<body>
    <div>文本</div>
    <script>
        var div=document.querySelector("div");
        div.onclick=function(){
            this.className="change";
        }
    </script>
</body>
```

案例练习：

①密码框格式提示错误信息

### 4.5 小结

![image-20210623082701761](D:\img\image-20210623082701761.png)

==用这种方法总结！！！==

案例：

①排他思想

②百度换肤效果

③表格隔行变色

④表单全选/取消全选

### 4.6 自定义属性的操作

#### 1.获取属性值

element.属性	或者   element.getAttribute('属性')

```html
<script>
    //获取元素的属性值
    var div=document.querySelector("div");
    console.log(div.id);
    console.log(div.getAttribute("id"));
</script>
```

区别：

- element.属性：获取内置属性值
- element.getAttribute('属性')：主要获取自定义属性

#### 2.设置属性值

```html
<script>
    //修改元素的属性值
    var div=document.querySelector("div");
    div.id="demo1";
    console.log(div.id);
    div.setAttribute("id","demo2");
    console.log(div.getAttribute("id"));
</script>
```

案例：

tab栏切换布局

### 4.7 H5自定义属性

​		目的：为了保存并使用数据，不需要经过数据库。

#### 1.设置H5自定义属性

​		H5规定自定义属性  ==data-==开头作为属性名并且赋值。如：

```html
<div data-index="2"></div>
```

#### 2.获取H5自定义属性

①兼容性获取	element.getAttribute('data-index');

②H5新增div.dataset.index或者div.dataset['index']

```html
<script>
    //获取自定义属性值
    var div=document.querySelector("div");
    console.log(div.getAttribute('data-index'));
    console.log(div.dataset.index);
    console.log(div.dataset['index']);
    console.log(div.dataset.listName);
</script>
```

- dataset是一个集合，存放着data开头的自定义属性。

- 如果自定义属性里有多个短横线链接的单词，获取的时候采取驼峰命名法

  ```html
  <div  data-list-name='food'></div>
  <script>
      console.log(div.dataset.listName);
  </script>
  ```

## 5.节点操作

<img src="D:\img\image-20210623091250463.png" alt="image-20210623091250463" style="zoom:50%;" />

### 5.1 节点概述

- 页面中==所有内容都是节点==，可以分为元素节点、属性节点、文档节点、文本节点（包括空格回车等）。

- 节点至少拥有nodeType、nodeName、nodeValue三个属性

  ![image-20210623091953741](D:\img\image-20210623091953741.png)

- 各节点nodeType
  - 元素节点---1
  - 属性节点---2
  - 文本节点---3
- 开发中主要操作的是==元素节点==

### 5.2 节点层级

​		利用DOM树可以将节点划分为  ==父子兄==  层级关系。

<img src="D:\img\image-20210623092501324.png" alt="image-20210623092501324" style="zoom:50%;" />

#### 1.父节点

- parentNode属性可以发返回某节点的父节点，没有则null

```html
<script>
    var son=document.querySelector(".son");
    console.log(son.parentNode);
</script>
```



#### 2.子节点

- `parent.childNodes`返回了指定节点的子节点集合，包括元素节点、文本节点等
- `parent.children`返回所有==子元素==节点（开发常用）

```html
<body>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
    </ul>
    <script>
        var ul=document.querySelector("ul");
        console.log(ul.childNodes);//7个，包括四个文本节点（换行）
        console.log(ul.children);//3个
    </script>
</body>
```

#### 3.兄弟节点

- `node.nextSibling`返回当前元素的下一个节点，包括==所有类型==的节点，没有则返回null；
- `node.previousSibling`返回上一个兄弟节点，包括所有类型的节点，没有则返回null；

==获取元素兄弟节点：==

- `nextElementSibling`：下一个兄弟元素节点
- `previousElementSibling`：上一个兄弟元素节点 

### 5.3 创建节点

- 创建

  ```
  var li=document.createElement("li");
  ```

  

- ==添加==

  - `node.appendChild(child);`---------将一个节点添加到父节点的子节点列表末尾,追加元素，类似于数组中的pasu;

  ```
  ul.appendChild(li);
  ```

  - `node.insertBefore(child,指定元素)`可以讲一个节点添加到指定元素前面

  ```
  ul.insertBefore(li,ul.children[0]);
  ```

  ==案例：==

  简单版发布留言案例

### 5.4 删除节点

### 5.5 复制节点

















5.6 案例：动态生成表格

5.7 三种动态创建元素的区别





## 6.重点核心

​		



# 事件高级篇

![image-20210623110422014](D:\img\image-20210623110422014.png)

## 1.注册事件（绑定事件）

​		给元素添加事件，称为注册事件；注册事件有两种方式：

- 传统注册方式
  - 利用 on 开头的事件（onclick）
  - 特点：注册事件的==唯一性==
  - 同一个元素同一个事件只能设置一个处理函数，后面注册的处理函数会覆盖前面的（==唯一性==）

- 监听注册事件（==推荐==）

  - 有兼容性问题（ie9后支持），ie9以前使用`attachEvent`代替。

  - 同一元素同一事件可以添加多个监听器

  ![image-20210623144742023](D:\img\image-20210623144742023.png)

  

```html
<body>
    <button>传统注册事件</button>
    <button>方法监听注册事件</button>

    <script>
        var btns=document.getElementsByTagName("button");
        //1.传统方式-----事件唯一性
        btns[0].onclick=function(){
            alert("hello")
        }
        btns[0].onclick=function(){
            alert("well")
        }

        //2.事件监听注册---同一元素同一事件可以添加多个监听器
        //addEventListener里面的事件类型时字符串，且不要带on
        btns[1].addEventListener('click',function(){
            alert("yes");
        })
        btns[1].addEventListener('click',function(){
            alert("no");
        })
    </script>
</body>
```

## 2.删除事件（解绑事件）

- 传统方式解绑

```
evenTarget.onclick=null;
```

- 监听注册事件解绑

```
evenTarget.removeEventListener(type, listener[,useCapture]);
```



```html
<body>
    <div>1</div>
    <div>2</div>

    <script>
        var divs=document.getElementsByTagName("div");
        //1.传统
        divs[0].onclick=function(){
            alert("hello");
            divs[0].onclick=null;
        }

        //2.监听方式解绑
        divs[1].addEventListener('click',fn)//调用函数不需要加小括号

        function fn(){
            alert("yes");
            divs[1].removeEventListener('click', fn);
        }
    </script>
</body>
```

## 3.DOM事件流

- 事件流描述页面中接收事件的顺序（即==事件传播的顺序==）
- 事件发生时会在元素节点之间按照特定的顺序传播

<img src="D:\img\image-20210623152744373.png" alt="image-20210623152744373" style="zoom:50%;" />

<img src="D:\img\image-20210623152836882.png" alt="image-20210623152836882" style="zoom:50%;" />

#### 代码验证

- JS代码中只能执行补货或者冒泡其中一个阶段
- onclick和attachEvent只能得到冒泡阶段

- `evenTarget.removeEventListener(type, listener[,useCapture]);`
  - 第三个参数如果是true，表示在事件捕获阶段调用事件处理程序
  - 第三个参数如果是false（默认），表示在事件冒泡阶段调用事件处理程序

```html
<body>
    <div class="father">
        <div class="son">son盒子 </div>
    </div>

    <script>
        var son=document.querySelector(".son");
        son.addEventListener('click',function(){
            alert("son");
        },true);
        var father=document.querySelector(".father");
        father.addEventListener('click',function(){
            alert("father");
        },true);
    </script>
</body>
```

以上代码在事件捕获阶段调用事件处理程序，点击son盒子先弹出 father ，在弹出 son 。

## 4.事件对象

### 4.1 什么是事件对象

    eventTarget.onclick=function(even){}
    
    eventTarget.addEventListener('click',function(even){})
    
    这个even就是事件对象，也可以写成e

解释：

- even对象代表==事件的状态==，如鼠标的位置、按钮状态，键盘按键状态等。
- 事件发生后，跟==事件相关的一系列信息数据的集合==都放到这个对象里，里面有很多方法和属性

### 4.2 事件对象的使用语法

```
eventTarget.onclick=function(even){}
```

- 这个even是形参，系统帮我们设定为事件对象，不需要传递实参过去。
- 当我们注册事件时，even对象就会==被系统自动创建==，并依次传递给事件监听器（事件处理函数）。

### 4.3 事件对象常见的属性和方法

![image-20210623155827329](D:\img\image-20210623155827329.png)















































## 5.阻止事件冒泡

## 6.事件委托（代理、委派）

## 7.常用鼠标事件

## 8.常用键盘事件







# BOM    267-287

![image-20210623110357280](D:\img\image-20210623110357280.png)

## 1.BOM概述

### 1.1 BOM

- 浏览器对象模型（Browser Object Model, BOM），它提供了独立于内容而与==浏览器窗口进行交互的对象==，核心对象是window。
- BOM有一系列对象构成。

​		比如：在浏览器前进、后退、刷新、拉动滚动条等。

- DOM与BOM

  BOM包含DOM

  ![image-20210623162318709](D:\img\image-20210623162318709.png)

  ![image-20210623162048790](D:\img\image-20210623162048790.png)

### 1.2 BOM构成

- window对象是浏览器的==顶级对象==，它具有双重角色。

  - 它是JS访问浏览器窗口的一个接口。
  - 它是一个==全局对象==：定义在全局作用域中的变量、函数都会编程window对象的属性和方法。
  - 在调用的时候可以省略window，如前面的alert() document等。

  <img src="D:\img\image-20210623163838332.png" alt="image-20210623163838332" style="zoom:50%;" />

## 2.window对象的常见事件

### 2.1 窗口加载事件

```
window.onload=function(){}
或者
window.addEventListener("load",function(){})
```

- window.onload是窗口加载事件，当文档内容加载完会触发该事件。
- 有了window.onload就可以将JS代码写到页面元素上方。
- window.onload传统注册事件方式==只能写一次==（只加载最后一个）。



```
document.addEventListener("DOMContentLoaded",function(){})
```

- DOMContentLoaded事件触发时，仅当DOM加载完成。不包括样式表、图片、flash等。
- 如果页面图片很多，则用户从访问到onload触发需要较长时间，此时适合用DOMContentLoaded事件。

### 2.2 调整窗口大小事件

`window.onresize`是调整窗口大小加载事件，触发时调用处理函数：

```html
<body>
    <script>
        //窗口尺寸发生变化就会触发
        window.addEventListener("resize",function(){
            alert("change");
        })
    </script>
</body>
```

- 窗口大小发生像素变化就会触发。
- 可以利用该事件完成响应式布局。`window.innerWidth`表示当前屏幕宽度

案例：

==当窗口元素小于某值时隐藏元素，大于时显示==

```html
<body>
    <script>
        //窗口尺寸发生变化就会触发
        // window.addEventListener("resize",function(){
        //     console.log(window.innerWidth);
        //     console.log("change");
        // })
        
        //浏览器窗口小于800px时，隐藏div

        window.addEventListener("load",function(){
            var div=document.querySelector("div");
            window.addEventListener("resize",function(){
                console.log(window.innerWidth);
                if(window.innerWidth<800){
                    //display:none：
                    div.style.display="none";
                }else{
                    div.style.display="block";
                }
            })
        })    

    </script>
    <div>aaa</div>
</body>
```

## 3.定时器

**window对象提供了两种对象定时器**

### 3. 1 setTimeout()定时器

`setTimeout()`

- ```
  window.setTimeout(调用函数,[延迟毫秒数]);
  //window对象可以省略；毫秒数默认0
  //调用函数可以直接写函数或函数名，也可以写'函数名()'。
  ```

- `setTimeout()`用于设置一个定时器，==定时器到期后执行调用函数。==

- 定时器过多时，可以取标识符区分，有利于开发。

- `setTimeout()`的调用函数也称为回调函数---callback







**代码案例**

①定时器到期后改变div背景颜色

```html
<body>
    <script>
        //定时器到期后改变div背景颜色
        window.addEventListener("load",function(){
            setTimeout(fn,[3000]);

            function fn(){
                //更改div样式
                var div=document.querySelector("div");
                div.style.backgroundColor="purple";
            }
        })
    </script>
    <div></div>
</body>
```

②5秒后自动关闭广告







### 3.2 setInterval()定时器











## 4.JS执行队列

## 5.location对象

## 6.navigator对象

## 7.history对象

























# PC端网页特效

