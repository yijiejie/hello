## HTML

### HTML

* 一些基础标签

  > br是换行，hr是分隔线，pre是预留格式，ins插入
  >
  > 空格：&nbsp；
  >
  > 大于：&gt；
  >
  > 小于：&lt；

* 表格

  >标签有：table整个表、tr一行、td一列（即单元格），表格第一行可用th，关于表格有许多标签，如果是table的，border是边框，width、height都是指对于浏览器，可以以百分比显示，也可以是具体的数值。align="center"可以让文字居中。
  >
  >表格中的单元格合并，rowspan标签是两行的两个小单元合并，设置大小，colspan……
  >
  >有thead、tbody、tfoot标签把tr套起来。
  >
  >dl、dt、dd，列表标签
  >
  >```html
  ><dl> 
  >    <dt>标题1</dt> 
  >    <dd>列表1</dd> 
  >    <dd>列表2</dd> 
  >    <dd>列表3</dd> 
  ></dl>
  >```
  >
  >

* bgcolor和backgroud标签一个是背景色，一个是背景图片

  > 图片一般是设置width就行，高度会等比例缩放

  * img标签中，直接/而没有一个结束的反标签，alt用来指定当图片加载失败的提示信息，title是悬停时提示文本

* 超链接

  > 标签可以嵌套，a标签的href属性写链接地址，可以设置为文字，也可以是图片。
  >
  > 内部窗口用iframe标签
  >
  > 锚点链接，在同一页面根据关键词跳到它的板块（参考百度百科）
  >
  > * 在链接文本的href属性中，设置值为“#hobby”
  > * 找到目标位置标签，在里面添加id属性=“hobby”
  >
  > target属性可以设置链接显示在哪个窗口
  >
  > 点击超链接相当于向服务器发送请求（实现了跳转）
  >
  > ```
  > _blank:新窗口
  > _self:当前窗口
  > _parent:当前窗口的父窗口
  > _top:当前窗口的顶级窗口	
  > ```
  >

* 列表

  > 无序列表<ul>列表项<li>列表前面的标志可以改变，type属性       
  >
  > 有序列表<ol>列表项<li>                                                                                                 

* 表单

  > **form表单，**
  >
  > **input**是输入域，type不同，展示样式不同。text表示文本框，password表示密码框，如果是submit，那就是提交按钮，radio代表单选框，要设置一下value值0、1等，checkbox是复选框（checked属性表示默认选中）等选到的时候就可以，reset是重置按钮，为file类型的时候，后端使用IO流的方式来接收；type=hidden的时候是隐藏域，可以为其设置key-value值隐藏提交，maxlength可以限制提交的字符的长度。
  >
  > > input标签中的readonly和disabled都是只读，但只有readonly修饰的value值才能提交给服务器
  >
  > ```
  > <form action="https://www.baidu.com">
  >         用户名：<input type="text" name="username"/><br>
  >         密码：<input type="password" name="password"/><br>
  >         <input type="submit" value="登录"/>
  > </form>
  > ```
  >
  > 输入后，根据action的跳转，https://www.baidu.com/?username=407911147%40qq.com&password=123456，网址变成这样，说明用户名和密码的两个的值就是value，如果不设置默认的时候是空的。
  >
  > **label**标签用于绑定一个表单元素，但点击标签内的文本时，浏览器会自动将焦点转到或选择对应的表单元素上（例如在选择性别男女时，点击文字也可以实现选中的效果）,
  >
  > >```
  > ><form>
  > >        <label for="sex0">男</label>
  > >        <input type="radio" id="sex0" name="sex" value="0"/>
  > >        <label for="sex1">女</label>
  > >        <input type="radio" id="sex1" name="sex" value="1"/>
  > ></form>
  > >```
  > >
  > >注意：绑定时label中的for属性，对应input标签中的id属性；id属性在页面中每个节点都不一样；一定要写name属性，不然就变成了两个单选框，可同时选
  >
  > **select**是下拉列表，里面是option标签(selected是默认选中)
  >
  > size属性可以设置下拉列表一次最多可以显示的个数，mutiple属性可以实现多选
  >
  > ```
  > <select name="degree">
  >          <option value="1">benke</option>
  >          <option value="2">zhuanke</option>
  >          <option value="3" selected>1</option>
  >          <option value="4">2</option>
  > </select>
  > ```
  >
  > textarea是文本域，可以设置行列rows、cols

* 快速生成HTML

  * 生成标签，直接使用tab键，生成多个相同的标签，div×*3，若是div{$}*×5，就是demo1到demo5
  * 有父子关系的如ul>li
  * 有兄弟关系的，div+p
  * 有类名或者id的，加.demo或者#two，再Tab键
  * 给同一列相同位置加元素，可shift+alt+鼠标
  
* id属性

  > 任何一个节点都有id属性，不能重复。后期要通过javascript对html进行增删改，id则提供了方便。通过id在javascript中获取到该节点，然后对其进行操作，最终产生网页的动态效果。


* * 

### HTML5新特性

* 新增多媒体标签

  * 视频<video>：尽量使用mp4格式，兼容性高

    >```html
    ><video src="文件地址" controls="controls”></video>
    >```
    >
    >常见属性：
    >
    >| 属性     | 值         | 描述                                              |
    >| -------- | ---------- | ------------------------------------------------- |
    >| autoplay | autoplay   | 视频就绪自动播放（谷歌禁了，添加muted属性可设置） |
    >| controls | controls   | 向用户显示播放控件                                |
    >| width    |            | 设置播放器宽度                                    |
    >| height   |            | 设置播放器高度                                    |
    >| loop     |            | 播放完是否继续播放该视频                          |
    >| preload  | auto\|none | 预加载                                            |
    >| poster   | imgurl     | 加载等待的画面图片                                |
    >| muted    |            | 静音播放                                          |

  * 音频<audio>

    > 常见属性：（谷歌禁了自动播放，只能通过js来操作）
    >
    > | 属性     | 值       | 描述               |
    > | -------- | -------- | ------------------ |
    > | autoplay | autoplay | 视频就绪自动播放   |
    > | controls | controls | 向用户显示播放控件 |
    > | loop     | loop     | 循环播放           |

  * 


*  html5新增的input类型

  > | 属性值        | 说明                        |
  > | ------------- | --------------------------- |
  > | type=“email”  | 限制用户输入必须为Email类型 |
  > | type=“url”    | 限制用户输入必须为URL类型   |
  > | type=“date”   | 限制用户输入必须为日期类型  |
  > | type=“time”   | 限制用户输入必须为时间类型  |
  > | type=“month”  | 限制用户输入必须为月类型    |
  > | type=“week”   | 限制用户输入必须为周类型    |
  > | type=“number” | 限制用户输入必须为数字类型  |
  > | type=“tel”    | 手机号码                    |
  > | type=“search” | 搜索框                      |
  > | type="color"  | 生成一个颜色选择表单        |
  >
  > 点击提交按钮可以验证表单

* 新增的表单属性

  > | 属性         | 值        | 说明                                                         |
  > | ------------ | --------- | ------------------------------------------------------------ |
  > | required     | required  | 表单拥有该属性表示其内容不能为空，必填                       |
  > | placeholder  | 提示文本  | 表单的提示信息，存在默认值将不显示                           |
  > | autofocus    | autofocus | 自动聚焦属性，页面加载完成自动聚焦到指定表单                 |
  > | autocomplete | off/on    | 当用户在字段开始键入时，浏览器基于之前键入过的值，应该显示出在字段中填写的选项。默认已经打开为on，关闭为off，需要放在表单内，同时加上name属性，同时成功提交 |
  > | multiple     | multiple  | 可以多选文件提交                                             |
  >
  