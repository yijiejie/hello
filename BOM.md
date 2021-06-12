## BOM

BOM:浏览器对象模型，与浏览器窗口进行交互的对象，核心对象：window

> 1. js访问浏览器窗口的一个接口
>
> 2. 它是一个全局对象，定义在全局作用域的变量和函数都会变成window的属性、昂发
>
>    如：window.num  window.fn()
>
>    注意：声明变量不能用name！name有特殊意义

* 窗口加载事件

  > 对于一般的我们都要把html写在前面，js写在后面，但有了窗口加载事件，可以在页面加载好之后才触发（图像、css、flash）：window.onload=function（）{}；//这种形式具有唯一性，所以有多个的话，只显示最后一个，可以用addEventListener（‘load’，fun……）
  >
  > 而DomContentLoaded事件比load加载快！，因为它仅仅是把dom加载完毕，不包括图片、flash等

* 调整窗口大小事件 

  >window.innerWidth 当前屏幕宽度
  >
  >窗口大小发生变化时触发

* 定时器

  * window.setTimeout(调用函数，延迟的ms数)

    >事件中调用函数无小括号！
    >
    >第二个参数可省略，默认我0
    >
    >window可省略
    >
    >一般会为这个定时器取个名字var timer=setTimeout（……）加以区分

  * 回调函数

    > 上一件事干完，再回头调用这个函数，如鼠标事件中要先点击才会调用，如定时器，要时间过完才会调用

  * 停止setTimeout定时器：clearTimeout（timeoutID）；//这个id即为定时器设置的标识符

  * window.setInterval（调用函数，延迟的ms数）

    > *两个定时器的区别：setTimeout是在时间过完之后只执行一次，一次执行完*
    >
    > *而setInterval是每间隔多少个ms数，执行一次*
    >
    > *京东倒计时案例*：利用之前学Date时计算时、分、秒。
    >
    > 利用window.setInterval实现每一秒钟就调用一次函数，
    >
    > 注意：button是特殊的表单元素，它的内容用innerHtml来写入不是value。对于倒计时，他总是会停几秒再执行，解决方法：把匿名函数的内容写在函数中，先把函数调用一次i，再执行。
    >
    > 发短信案例：每隔10s按钮可以继续点击，每秒还会出现倒计时

  * clearInterval

* 同步和异步（）

  > 执行过程：主线程执行栈放同步任务，任务队列放异步任务（回调函数），把同步任务执行完后，取任务队列，把其中的异步任务放到执行

* location对象：获取或设置窗体的url，并且可以用于解析url，这个属性返回的是一个对象

  > | location对象属性    | 返回值                                 |
  > | ------------------- | -------------------------------------- |
  > | **location.href**   | 获取或者设置 整个url                   |
  > | location.host       | 返回主机（域名）                       |
  > | location.port       | 返回端口号 若无返回空字符串            |
  > | location.pathname   | 返回路径                               |
  > | **location.search** | 返回参数（？name=……）                  |
  > | location.hash       | 返回片段 #后面内容 吃NGJI能与链接 锚点 |
  >
  > 