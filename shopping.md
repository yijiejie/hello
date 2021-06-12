## 品优购笔记

#### 一些准备工作

* 京东的base.css文件（为网页设置消除边距那些）
* 对于很多个板块会有相同的顶部、底部列表等样式，加个common.css
* 网站favicon.ico图标
  * 把图标切成png图片
  * 把png图片转换为ico图标（利用第三方网站）放在根目录下
  * 在html中写出引入的语句

* 网站TDK三大标签SEO优化

  > title网站标题具有不可替代性
  >
  > description和keywords

#### shortcut部分

* 关于|的打法，如果直接用li会占满整个格子，一般导航条都是li里面用a，直接对a设置边框

#### header部分

* 小气泡用border-radius设置边框，可以为椭圆，另一个用三角制作

#### nav部分

* 导航中鼠标经过li框框整个变颜色，而a中的字体颜色只能通过修改a的样式用：

  > .dd ul li:hover a{}

#### footer部分

* 在div中有ul、p、i标签，他们会同一行显示，记得设置宽度或者边距

#### main部分

* 类似表格一样的边框，采取div>ul>li，li的下边框不好控制，因为宽度会和外面的盒子不适配

  div的宽度是要和上面一致的，那么把ul的宽度设置为能容纳规定数量的li能容纳，最边上的就会超出div，对父盒子加overflow：hidden

* 精灵图（又很多个图标，在线网站http://www.spritecow.com/）

#### tab栏切换（css阶段的要求）

* 准备两个盒子tab_list和tab_content，一一对应，后面用js实现，选选项1时，在几个内容中，展示content1，其他的隐藏，个准备一个class

#### 商品li页

* 鼠标经过给li加个红色边框，应该直接在未点击时就加一个透明的边框，防止抖动。

#### 注册页面

* 表单

  ```html
  <div class="register">
      <ul>
          <li><label for="">手机号：</label><input type="text"><span class="error"><i class="error_icon"></i>手机号码格式不正确，请重新输入</span></li>
          <li class="safe">安全程度<em class="ruo">弱</em><em class="zhong">中</em><em class="qiang">强</em></li><li><input type="text">同意协议并注册<a href="#">《用户协议》</a></li>
                      <li><input type="submit" value="完成注册"></li>
                  </ul>
              </div>
          </div>
  ```

  >用vertical-align:center使行内块元素i和文字对齐
  >
  >label设置宽度，使文字向右靠
  >
  >安全程度这块，不用设置宽高，直接设置padding值高度是文字的高度，然后设置背景颜色就ok

#### 下拉菜单

一行上是一个ul里面包含的几个li包含a，点击a出现ul，然后ul包含几个li