## List
List列表类，顺序存储任何对象（顺序不变），可重复。
List是继承于Collection的接口，不能实例化。实例化可以用:
* `ArrayList`(实现动态数组)，查询快（随意访问或顺序访问），增删慢。整体清空快，线程不同步(非线程安全)。数组长度是可变的百分之五十延长
* `LinkedList`（实现链表），查询慢，增删快。
* `Vector`（实现动态数组），都慢，被ArrayList替代。长度任意延长。线程安全（同步的类，函数都是synchronized）
* `Stack`（实现堆栈）继承于Vector，先进后出。
* `TreeList`  [Intro](https://commons.apache.org/proper/commons-collections/javadocs/api-4.4/org/apache/commons/collections4/list/TreeList.html)

所以，快速访问ArrayList，快速增删LinkedList，单线程都可以用，多线程只能用同步类Vector

## List 基本操作:  
    插入：add()  
    查找：get()  
    删除：remove(int index)  
    修改：set()  
    清空表：clear()  
    遍历：用Iterator迭代器遍历每个元素  

| |get|add|insert|iterate|remove|
|-|-|-|-|-|-|
|TreeList|3|5|1|2|1|
|ArrayList|1|1|40|1|40|
|LinkedList|5800|1|350|2|325|