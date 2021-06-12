### Java语法

* 没有引用类型，都是直接传值

  > 在递归过程中，即使把修改了的path传到list中，在递归过程中path改变了，他在res中的 地址也会改变，所以在list.add(new ArrayList<>(path))，原因是之前传的其实就是地址，该地址的数据变了，所以……

* Integer和 int

  > Integer可以为null或0，int只能为0；
  >
  > Integer有一些自己的方法可以使用。（将整数转化为二进制）

* 队列

  > Queue<Object> queue=new LinkedList<>();
  >
  > 添加：add和**offer**，删除:remove（返回值）  判空：isEmpty
  >
  > Deque<Integer> path = new ArrayDeque();//双端队列

* 栈

  >Stack<Object> stk=new Stack();
  >
  >Deque<Integer> stack = new ArrayDeque();
  >
  >常见：push,pop
  >
  >stk.peek();//返回栈顶元素，但不出栈它。
  >
  >

* 数组：java定义数组的方法有：1、【数组类型[] 数组名 = new 数组类型[数组长度]】；2、【数组类型[] 数组名 = {数组元素}】；3、【数组类型[] 数组名 = new 数组类型[] {数组元素}】

  > 对于二维数组，a[1]指第二行的地址
  >
  > 排序：Arrays.sort(list)，
  >
  > Arrays.sort(int[] a, int fromIndex, int toIndex)；//是把从fromIndex,到toIndex-1的元素排序。

* 集合

  > 
  >
  > 将数组转化成List集合:Arrays.asList("a","b","c")**(长度不可变，删除添加不适)**
  >
  > Collections.sort(stus, (s1,s2)->(s1.getAge()-s2.getAge()));
  >
  > 对stus比较大小，排序，结果<0，是
  >
  > s1在前，否则s2在前；
  >
  > 集合的add方法，add(index,a);把a元素插到该位置，其他元素自动后移

