## javascript

javascript：运行在客户端的脚本语言。

js引擎（js执行器）执行代码时逐行解释每一句源码（转换为机器语言），然后由计算机去执行，所以归为脚本语言，为逐行解释执行。（当一行出错后，不会继续往后执行）

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
//这是一个输入框,返回的就是输入的信息
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

* **数据类型**

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

  *       Boolean类型