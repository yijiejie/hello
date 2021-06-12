## javascript

javascript：运行在客户端的脚本语言。

js引擎（js执行器）执行代码时逐行解释每一句源码（转换为机器语言），然后由计算机去执行，所以归为脚本语言，为逐行解释执行。（当一行出错后，不会继续往后执行）

**解释型语言（及时执行）**；java是编译型语言（编译完全部然后执行）

js引擎运行js文件：预解析+执行

> 预解析在作用域分两步：
>
> 1.把var声明变量的语句提到前面，把function声明函数的语句提前
>
> 2.再把赋值、函数调用等操作接在后面，对于匿名函数！
>
> 注意！他只提前了var fun，在调用fun()的话，不行！他的function没有被提前fun是变量，还没把函数赋给它！所以出错。
>
> ```javascript
> //案例1
> var num=10;
> fun();
> function fun(){
>     console.log(num);
>     var num=10;
> }
> //预解析
> var num;
> function fun(){
>     var num;//根据就近原则，最后打印的是这个怒骂，就是undefined！仅声明未赋值
>     console.log(num);
>     num=10;
> }
> num=10;
> fun();
> ```
>
> 

#### 书写（js语句内部推荐用单引号）

**js的引入**

* 直接写在元素内部，如按钮的onclick点击事件（行内）

* 写在head部分，用<script>框起来（内嵌）

* 写在js文件中，引入语句

  ```javascript
  <script src="my.js"></script>（他们中间不能写代码）
  ```

**注释**

* 单行注释//，快捷键`ctrl`+`/`
* 多行注释/**/，快捷键`ctrl`+`alt`+`/`

**输入输出语句**

```javascript
//这是一个输入框,返回的就是输入的信息，文字和输入框不在一行
prompt('请输入你的年龄');
//浏览器弹出警示框（输出）
alert('计算的结果是');
//浏览器控制台打印输出信息
console.log('我是程序员能看到的');
```

###  基础知识

* **变量**
  
  * 声明变量：var age；
  * 仅声明，未赋值返回undefined
  * 未声明未赋值，直接使用变量会报错
* 使用驼峰命名
  
* **数据类型**（用typeof返回数据类型）

  * 数字型number
    * 八进制：0<u>数字</u>
    * 十六进制：0x<u>数字</u>
    * Number.MAX_VALUE最大值
    * Number.MIN_VALUE最小值
    * 无穷大：Infinity
    * 无穷小：-Infinity
    * 非数字：NaN；判断非数字的函数boolean isNaN()

  * String类型

    1. 在需要嵌套时，单双引号结合

    2. 转义用\，换行\n，\b空格

    3. length获取字符串的长度

    4. 字符串拼接：任何类型的变量+字符串=变量值+字符串

       > var random=undefined；
       >
       > var str=random+‘hello’；//输出undefinedhello，null同上

  * Boolean类型
  
    > true和false可以和整型数据作运算（0，1）
  >
    > 0是false，但非0是true！加以区分！
  
  * undefined：定义了未定义数据类型
  
    > 与字符串相加：undefind字符串内容（因为字符串和任何相加结果都是字符串）
  >
    > 与数字相加：结果是NaN
  
  * null
  
    > 与数字相加相加：结果是数字（与上面的undefined相区分）
    >
    > 返回数据类型是object

* 数据类型转换
  * 转换为字符串
    * toString()
    * String(num)
    * 加号拼接！num+空字符串！
  * 转换为数字类型（数字出现在前面，而非字符串中间）
    * parseInt(num)：会自当取整，舍单位
    * parseFloat（num）
    * Number（num）
    * js的隐式转换（- * /等操作时），加法🙅‍

* 标识符：未变量、函数起的名字；关键字、保留字
* 运算符号（在+、-运算>=等左右加空格，优化格式）
  * 浮点数，算术运算有问题如0.300000006；所以浮点数之间没法比较
  * ==只比较值，‘18’==18//true
  * ===全等，比较内容和数据类型，‘18’==18//false
  * &&短路，若左右都是表达式，左真，返回右边的内容；左假，返回左边的内容
  * ||短路，若左右都是表达式，左真，返回左边的内容；左假，返回右边的内容

* 循环
  
* 三元运算符应用：秒杀时，不足10在前面补0
  
* 数组（**length随着元素增多，动态增加**）

  * 创建数组

    > var array=new Array(3);//3是数组长度若为（2，3）那么2和3就是数组元素
    >
    > var arr=[];//直接创建一个空数组
    >
    > 数组里面可以同时存多种不同类型的数据

  * console.log(array)；打印数组的所有内容以及length

  * instanceof和isArray都可以用来检测数据类型是否为数组

    > arr instanceof Array
    >
    > Array.isArray(arr)

  * 数组新增元素

    * 直接修改array.length
    * 直接追加元素（length是会变化的；在遇到用k时，直接用newArray.length代替）
    
  * 添加删除数组元素的方法

    * 添加arr.push(若是多个元素，用,隔开);返回新数组长度
    * 在数组头部添加arr.unshift();返回新数组长度
    * 删除是pop，一次只能删除一个元素，返回删除的元素内容

  * 自带方法：

    > arr.reverse();
    >
    > arr.sort();//排序只会排前面那一位11在7前面，改写
    >
    > ```
    > arr.sort(function(a,b){
    >   return a-b;
    > })
    > ```
    >
    > arr.indexof();//在数组中查找看是否有该元素，若有返回第一个找到的索引，找不到返回-1
    >
    > arr.lastIndexof();
    >
    > arr.toString();//把数组内容转换为字符串输出，用逗号分隔
    >
    > arr.join(分隔符，默认为逗号);//
    >
    > arr1.cancat(arr2);//返回一个合并了arr1和arr2的新数组
    >
    > arr.slice();//若只有一个参数就拷贝该索引号到数组结束的所有元素；否则拷贝[begin,end)的元素；
    >
    > arr.splice(index,0/1,元素)；//0代表在索引处插入，1代表在索引处替换

* **函数**

  1. 声明（两种方式）：function 函数名( 形参，形参...){    }或者：

     var fun=function( 形参，形参...){     }
  
     > function：声明函数的关键字，小写
     >
     > 函数名一般是动词（完成某项任务）
   >
     > 形参是没有声明的变量！（默认的undefined）
   >
     > 第一种中有函数名在function后面，第二中没有函数名！称为匿名函数，调用方式前者函数名（）；后者变量名（）；

  2. 调用：函数名（实参，实参...）；
  
  3. 函数形参、实参个数不一致
  
     > 即使是数组形参也直接写成arr
   >
     > 若实参多于形参个数，那就取实参的前几个取和形参匹配
   >
     > 若实参少于形参个数，那就是未匹配上的就是undefined
  
  4. 函数可以用return来写返回值，没有return就返回undefined，return 1，2；//2返回结果是最后一个值，像返回多个值

     ```javascript
   return [2,4,5];//利用数组来实现
     ```
  
  5. arguments的使用
  
     > 当我们不确定有多少个参数传递时，可以用arguments来获取
     >
     > ```javascript
     > function fun(){
     >     console.log(arguments);//存储了所有传递过来的实参
     > }
     > fn(1,2,3)
     > ```
     >
     > arguments是伪数组：
   >
     > 1. 具有数组的length属性
     > 2. 按照索引的方式进行存储
     > 3. 没有真正数组的一些方法
  
  6. 函数可以调用另外的函数

* 作用域：起作用的范围（ES6开始有块级作用域{}）
  * 全局作用域：整个script标签，或者单独一个js文件内
  * 局部作用域（函数作用域）
  * 作用域链：内部函数访问外部函数的变量，采取的是链式查找的方式来确定，外面没有，再找外面一层。（就近原则，即使函数内部是var num并未赋值，也满足就近原则！）

* 全局变量、局部变量

  > 全局变量有两种：1. 在全局作用域下声明的变量
  >
  > 2. *在函数内部，未声明直接赋值的变量*

* 对象：具体的事物（wcx）

  创建对象的三种方式：

  * 字面量{ }

    ```javascript
    var obj={
       uname:'xx',//属性
       sayHi:function(){
       
       } //方法
    }
    //key-value形式
    //方法后是匿名函数
    //调用：obj.uname或者obj['uname']
    ```

  * 用new Object创建
  
    ```
    var obj=new Object();
    obj.uname='xx';
    obj.sayHi=function (){
    
    }
    ```
  
  * 构造函数创建
  
    > 构造函数的语法格式：
    >
    > ```javascript
    > function 构造函数名(){
    >     this.属性名=值；
    >     this.方法=function (){ 
    >     }
    > }
    > ```
    >
    > ```javascript
    > //创建对象
    > var 变量名=new 构造函数名('zs',18);
    > //参数对应构造函数的形参，构造函数中的this指的是调用他的那个对象，如此时的变量名
    > //构造函数名类似java中的class，所以首字母大写
    > //构造函数不需要return，就可以返回整个对象；
    > ```
    >
    > *利用构造函数创建对象的过程称为对象的实例化*
    >
    > new的过程：
    >
    > > 1. 创建空对象（内存中）
    > > 2. this指向新对象
    > > 3. 执行构造函数，给新对象添加……
    > > 4. 返回新对象

> 对对象进行遍历(for in)
>
> ```
> for(var k in  obj){
>    log(k);//输出属性名，因为k就是表示这个对象里面的变量
>    log(obj[k]);//属性值
> }
> ```
>

#### 内置对象(js自带可直接使用)MDN文档

* Math对象（不是构造函数，所以无需new）
  * Math.floor()
  * Math.ceil()
  * Math.round();//四舍五入，在.5问题上，四舍五入的结果就是大的数
  
* Date对象
  
  * new Date();//返回当前时间
  
  * getMonth（）；getDate();
  * getDay();//返回周几，如周日：0，在输出时用一个数组[“星期天”，……]
  * 时间戳：通过valueof（），getTime（）得到此时此刻距离1970年1.1总的毫秒数；或者是**var date=+new  Date(也可为用户输入的时间);**H5新增的Date.now();

> 秒杀倒计时案例：利用时间戳，将来的时间毫秒数减去当前的时间毫秒数。再转化为时、分、秒
>
> 输入的要是标准时间格式（‘2019-9-5 18:00:00’）
>
> ![image-20210520211700993](C:\Users\tracy\AppData\Roaming\Typora\typora-user-images\image-20210520211700993.png)

* 字符串

  > var str=‘andy’；//str有length属性，简单数据类型也有属性？它是基本包装类型，事实上进行了var str=new String ('andy')；
  >
  > **字符串不可变！**给str重新赋值时，是开辟了新的地址空间
  >
  > str.indexOf(字符)；//返回索引号，若为(字符，index)从index开始找字符
  >
  > str.charAt(index);//返回字符
  >
  > str.charCodeAt(index);返回ASCII码，一般应用于针对用户键入来进行操作
  >
  > ***H5新增***：str[index]
  >
  > eg：对于判断字符串中字符的出现次数
  >
  > 类比object.age我们在字符串上用str.a。
  >
  > var chars=str.charAt(i);//返回的chars就是一个字符，也是str的某个属性名，对o[chars]就是属性值，参考之前遍历对象时的o[k]

  * 一些方法
  
    >str.substr(起始位置，截取的字符个数)；//截取字符串，若字符个数省略了，那就是整个字符串
    >
    >str.replace(被替换的字符，替换为的字符)；//若只进行一次，只会替换第一个碰到的
    >
    >str.split();//join是把数组合成字符串

* 数据类型和堆栈

  * var a=null;//a的类型是object，适用于在像存一个object类型，但不确定具体值。

  * 简单数据类型

    > 如var a=10;会在栈内开辟空间存储10，变量a指向它，若修改a的值，是修改10为其他的值；若为复杂数据类型数组，则栈内存储数组的首地址，arr指向它，而数组的具体每一项的值存储在堆；若为一个对象，则栈内存储数组的首地址，o指向它，关于他的属性等都存储在堆中，当修改了直接在堆中修改，若给另一个变量赋值，则是给他赋地址。
    >
    > 有参的函数调用的过程，就相当于定义了一个变量和实参变量a存储的内容相同。
    
  * 对于js来说，简单数据类型传值，复杂数据类型传地址





