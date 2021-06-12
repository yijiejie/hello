## Dom（操作元素）

web api：浏览器提供的一套草错浏览器功能和页面元素的api

Dom：文档，dom树，一个页面就是一个文档：document，标签都是元素element（也称为文档对象模式，得到的都是对象）

dom操作：改变网页内容、结构和样式，也可以改变元素内部的属性等。

* 一些api：

  > document.getElementById(id值)；//返回标签（对象）
  >
  > document.getElementsByTagName('li');//返回元素对象集合（伪数组）
  >
  > console.dir(对象名);//打印该对象的一些属性
  >
  > //很明显document是对于整个文档来说的，
  >
  > element.getElementById()；element是对象

* h5新增的

  >document.getElementByClassName();
  >
  >document.querySelector('选择器')；//各种选择器都可以，但是需要区分，class用.box，相应地id用#box 
  >
  >document.querySelectorAll();//若是嵌套的，标签之间用>，id或class选择器用空格，包含xx属性的li就是‘li[xx]’;document.querySelectorAll('ul')*？？？/没用*

* 事件

  > 1. 事件源：即哪个标签触发
  > 2. 事件类型：如何触发，点击onclick或者是鼠标经过？
  > 3. 事件处理程序：匿名函数赋值

* 操作元素

  * 改变元素内容

    > elment.innerText;//从起始位置到终止位置的内容，但它去除标签，空格和换行也去掉
    >
    > 应用场景：点击某个按钮后，div内的文字发生变化，1.事件源：button，2.经过了onclick事件，3.div中的文字发生变化，赋值语句：div.innerText='我变啦!'，也可以直接写
    >
    > 它不识别标签，如对其中文字进行加粗等操作
    >
    > element.innerHtml识别标签！(使用更多)直接把div标签中的所有内容显示出来，对其赋值也有相应的效果
    >
    > ```js
    > div.innerHtml='<strong>hhh</strong>'
    > ```
    >
    > 这俩标签可读写！不仅可赋值，还可以读取内容

  * 修改元素属性：如src、href等

    >```javascript
    >zxy.onclick=function(){
    >   img.src='images/···';
    >}
    >```

  * 表单元素的属性操作

    >```javascript
    >btn.onclick=function(){
    >    input.value='被点击了';//input显示的内容在value里面！
    >    btn.disbaled=true;//设置btn被点击过后就禁用，不能再重复点击了，用this.也可以
    >}
    >```

  * 样式属性操作

    >element.style    行内样式操作
    >
    >element.className 类名样式操作
    >
    >className的使用方法，是在方法内部，给标签添加一个类名，然后再对这个类做操作，若该类本来就有类名，用多类名！直接给他拼接一个新的类名
    >
    >注意：1. js里面的样式采取驼峰命名
    >
    >2. js修改style样式操作，产生的是行内样式，css权重更高（style就是写在内部的那个css）
    >
    >   操作精灵图（精灵图）：坐标怎么写：element.style.backgroundPosition='0  -44px'
    >
    >   '0 -'+变量名+'px'        **要用到变量的时候就是字符串的拼接**

  * 排他思想

    > 把其他所有的设置后，再设置需要改变的那一个
    >
    > 把其他所有的该样式都清除，再设置这一个的。
    >
    > 对于设置表格一行经过时颜色改变，用for循环，可以对他们加背景色，或者用一个类名，给该类设置样式（可能样式不止一种），然后给该行添加该类名。

  * 自定义属性操作

    >element.属性  获取内置属性值（元素本身自带的属性）
    >
    >element.属性=值；
    >
    >element.getAttribute('属性')；获得自定义属性值
    >
    >element.setAttribute('属性'，'值')；//主要针对自定义属性
    >
    >element.removeAttribute('属性');
    >
    >**H5新增**
    >
    >*规范化：用data-xxx来设定自定义属性，这样的话，也可以通过div.dataset.xxx来查看该自定义属性（其中dataset就是自定义属性的集合），当然也可以div.dataset['xxx']*
    >
    >*若自定义的名字是data-list-name，用的时候是div.listName，驼峰命名！*
    >
    >记住！在html里面的class，在js里面是className设置class属性时：
    >
    >element.className=''

* 节点操作（节点：网页中的所有内容）

  利用父子兄节点关系获取元素，逻辑性强，但兼容性稍差

  * 节点至少拥有节点类型（nodeType）、节点名称（nodeName）和节点值（nodeValue）这三个基本属性

    > 元素节点的nodeType：1，属性节点的nodeType：2，文本节点nodeType：3（文本节点包含文字、空格、换行等）
    
  *    父子节点

      >下拉菜单：一行上是一个ul里面包含的几个li包含a，点击a出现ul，然后ul包含几个li
      >
      >设置onmouseover事件和onmouseout事件
      
      * 父节点：node.parentNode（得到的是离元素最近的父级节点，无就为null）
      * 子节点：node.childNodes(包含文本节点和子元素节点)
      * **子元素节点：node.children（包含所有的子元素节点）**
      * 第一个子节点，最后一个子节点，父节点.firstChild|lastChild（包含文本节点）
      * 第一个、最后一个子元素节点firstElementChild|lastElementChild
      
  * 兄弟节点

    * 下一个兄弟节点：nextSibling（包含元素节点或文本节点）
    * 上一个兄弟节点：previousSibling

  * 创建节点

    > document.createElement('tagName')

  * 添加节点

    >node.appendChild(child);//直接追加元素
    >
    >node.insertBefore(child,node.children[0]);//插入到第一个元素前面

  * 删除节点

    > ul.removeChild(ul.children[0])
    >
    > 记住!innerHtml可以识别标签！所以在文本中加标签，在html中也会反应出来
    >
    > **有些情况下的添加、删除在页面内进行，且页面除了该处不发生改变，一般用a，而阻止链接跳转，需要给href属性添加javascript:void(0);或者javascript:;**

  * 克隆节点

    >node.cloneNode()
    >
    >注意：1. 如果括号中的参数为空或者false，则是浅拷贝，即只克隆复制节点本身，不克隆里面的子节点。
    >
    >2. 如果括号中的参数为true，则是深拷贝，把标签完全拿过来

  * 动态添加表格的demo

    ```javascript
    //利用构造函数来创建对象
    function student(name, subject, score) {
                this.name = name;
                this.subject = subject;
                this.score = score;
            };
            var stu = new Array(2);
    //这个语句记得要new
            stu[0] = new student('卫英络', 'Javascript', 100);
            stu[1] = new student('傅亨', 'Javascript', 98);
            var tbody = document.querySelector('tbody');
            console.log(stu[0]);
    //对每个student添加tr
            for (var i = 0; i < stu.length; i++) {
                var tr = document.createElement('tr');
                tbody.appendChild(tr);
                for (var j = 0; j < 4; j++) {
                    var td = document.createElement('td');
                    tr.appendChild(td);
                }
                console.log(stu[i]);
                tr.children[0].innerHTML = stu[i].name;
                tr.children[1].innerHTML = stu[i].subject;
                tr.children[2].innerHTML = stu[i].score;
                tr.children[3].innerHTML = '<a href="javascript:void(0);">删除</a>';
                //每个a都需要添加！
                var a = tbody.querySelector('a');
                a.onclick = function() {
                    tbody.removeChild(a.parentNode.parentNode);
                }
            }
    ```

    

* 三种创建元素方式区别
  * document.write()创建元素，会使页面重绘
  * innerHtml通过标签语句加标签；创建多个元素的时候效率更好（不要拼接字符串，采取数组形式拼接）
  * createElement

![image-20210604211054726](C:\Users\tracy\AppData\Roaming\Typora\typora-user-images\image-20210604211054726.png)

* 注册事件

  * 传统方式element.onclick=function（）{}；后面的事件会覆盖前面的（唯一性）

  * 方法监听注册方式：element.addEventListener（type,listener[,useCapture]）

    同一个元素 同一个事件可以添加多个监听器（事件处理程序）

    >type:事件型字符串，比如click、mouseover，注意这里不带on
    >
    >listener:事件处理函数，事件发生时，会调用该监听函数(用匿名函数写)
    >
    >useCapture：可选参数，是boolean类型

* 删除事件

  * 传统方式element.onclick=null;

  * element.removeEventListener（type,listener[,useCapture]）

    > 对于删除事件，肯定要写明删除的是哪一个，所以不用匿名函数，此时绑定事件时，应
    >
    > div.addEventListener（'click',fn）;这是绑定，这里的fn也没有小括号！
    >
    > 把事件处理函数写在外面，在删除时需要调用，也不写小括号！

* **事件流**
  * JS代码中只能执行捕获或者**冒泡**其中的一个阶段
  * onclick和attachEvent（老版本的事件监听）只能得到冒泡阶段
  * 捕获阶段，如果addEventListener第三个参数是true则处于捕获阶段（document->html->body）
  * 如果addEventListener第三个参数是false则处于冒泡阶段（son->father->body->html）
  * 注意：有的事件没有冒泡，如onmouseover等
  * 阻止事件冒泡:在son那里加e.stopPropagation();那么father……都不会触发

* 事件对象

  > div.onclick=function(event) {
  >
  > ​      console.log(event);//event不是形参！若为函数，应该是function 函数名（形参）
  >
  > }
  >
  > //1. event就是一个事件对象写到我们侦听函数的小括号里面当形参来看
  > //2. 事件对象只有有了事件才会存在，它是系统给我们自动创建的，不需要我们传递参数
  > //3. 事件对象是我们事件的一系列相关数据的集合跟事件相关的比如鼠标点击里面就包含了鼠标的相关信息，鼠标坐标啊，如果是键盘事件里面就包含的键盘事件的信息比如判断用户按下了那个键
  >
  > eg：当点击了屏幕一下，就会返回此时的操作是click、绑定的是div、鼠标点击的坐标是……
  >
  > 可以不写成event，写成其他的，如e也没问题

  * e.target返回的是触发事件的对象，this是绑定事件的对象，e.type返回事件类型（不带on），阻止默认行为：e.preventDefault();(比如对于链接，暂时不让它点击了就跳转)

* 事件委托：不给每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡来影响设置每个子节点

  > 案例：给ul注册点击事件，然后利用事件对象的target周到当前点击的li，因为点击li，事件会冒泡到ul上，ul有注册时间，就会触发事件监听器

* 鼠标事件

  * 禁止鼠标右键菜单

    ```javascript
    document.addEventListener('contextmenu',function(e){
       e.preventDefault();//阻止默认事件
    })
    ```

  * 禁止选中文字

    ```javascript
    document.addEventListener('contextmenu',function(e){
       e.preventDefault();//阻止默认事件
})
    ```
    
  * 鼠标移动事件
  
    ```
    //小天使
    //鼠标不断移动，使用鼠标移动事件：mousemove，在页面中移动，给document注册事件
    //图片要移动距离，而且不占位置，使用绝对定位！
    //注意：得到的x、y都是值，没有加px，记得拼接px！默认的鼠标都是在图片的左上角，所以在设
    //置图片坐标时，把图片的左移上移半个图片的距离
    ```
  
    
  
  * 鼠标事件对象（即MouseEvent对应的）
  
    * clientx、clientY：针对页面的可视区来说的，
    * pageX、pageY：针对文档来说的（离上部和左侧的距离，一般页面比较长，这个更适用）
  
  * 常用的键盘事件
  
    * keyup、keydown、keypress
  
      > keyup是键盘弹起时触发，keydown、keypress是键盘按下时触发，其中keypress不识别功能键（`ctrl`、`shift`等），这些事件类似键盘的click事件
      >
      > 执行顺序：keydown>keypress>keyup
      >
      > keyup、keydown不识别大小写keypress识别
  
    * 键盘事件的属性值
  
      > key是按下的键，keyCode是按下的键的ASCII码值
      >
      > *搜索框案例*：（在键盘按下s后，光标停在搜索框，用到foucs函数，失焦是blur）
      >
      > 使用keyup，即按键盘完成后触发！如果使用keydown，s会出现在搜索框内
      >
      > *京东快递案例*：（输入订单编号，会出现放大的框）
      >
      > 用keyup！不用keydown、keypress的原因：针对他们在文本框中的特点，他们在按下的时候就触发，此时文字还落入文本框，而keyup是在弹起时触发，那么获得的就是触发键盘事件后的文本。