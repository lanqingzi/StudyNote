## Set
|set type|order|special|nullptr?|$O(add)O(find)$|
|-|-|-|-|-|
|HashSet|no||maximum one|$O(1)O(1)$|
|LinkedHashSet|yes|insert order|maximum one|$O(1)O(1)$|
|TreeSet|yes|default acsending|no|$O(log(n))O(log(n))$|

* 通常不能记住元素的添加顺序，与Collection基本相同，没有提供任何额外的方法，只是不允许重复而已。
* Set的实现类主要有HashSet和TreeSet  
* Set中的对象不按特定方式排序，并且没有重复对象。但它的有些实现类能对集合中的对象按特定方式排序，例如TreeSet类，它可以按照默认排序，也可以通过实现java.util.Comparator接口来自定义排序方式。 

## Set的功能方法 　　 
* Set : 存入Set的每个元素都必须是唯一的，因为Set不保存重复元素。加入Set的元素必须定义equals()方法以确保对象的唯一性。Set与Collection有完全一样的接口。Set接口不保证维护元素的次序。 
* HashSet : 为快速查找设计的Set。存入HashSet的对象必须定义hashCode()。
* TreeSet : 保存次序的Set, 底层为树结构。使用它可以从Set中提取有序的序列。
* LinkedHashSet : 具有HashSet的查询速度，且内部使用链表维护元素的顺序(插入的次序)。于是在使用迭代器遍历Set时，结果会按元素插入的次序显示

## Set性能分析
TreeSet  
* HashSet性能要好于TreeSet(特别是最常用的添加、查询元素等操作)
* 原因：因为TreeSet需要额外的红黑树算法维护集合元素的次序。只有需要一个保持排序的Set时，才应该使用TreeSet，否则都应该使用HashSet。

LinkedHashSet
* HashSet 还有一个子类：LinkedHashSet，对于普通的插入，删除操作，
* 链表用于维护插入的顺序
* LinkedHashSet比HashSet要略微慢一点，这是由维护链表所带来的额外开销造成的，但由于有了链表，遍历LinkedHashSet会更快。