Map主要用于存储健值对，根据键得到值，因此不允许键重复（若重复则覆盖），但允许值重复。

| map type      | ordered | special           | nullptr?      | $O(insert)O(find)$ |
| ------------- | ------- | ----------------- | ------------- | ------------------ |
| HashMap       | no      |                   | key&value yes | $O(1)O(1)$         |
| HashTable     | no      |                   | key&value no  | $O(1)O(n^2)$       |
| LinkedHashMap | yes     | insert order      | key&value yes | $O(1)O(log(n))$    |
| TreeMap       | yes     | default ascending | key&value yes | $O(1)O(log(n))$    |


## HashMap
* Hashmap 是一个最常用的Map，它根据键的HashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度。
* 遍历时，取得数据的顺序是完全随机的。
* HashMap最多只允许一条记录的键为Null；允许多条记录的值为 Null。
* HashMap不支持线程的同步，即任一时刻可以有多个线程同时写HashMap，可能会导致数据的不一致。如果需要同步，可以用 Collections的synchronizedMap方法使HashMap具有同步能力，或者使用ConcurrentHashMap。


## Hashtable
Hashtable与 HashMap类似，它继承自Dictionary类，不同的是：　　 
1. 它不允许记录的键或者值为空。 
2. 它支持线程的同步，即任一时刻只有一个线程能写Hashtable，因此也导致了 Hashtable在写入时会比较慢。

## LinkedHashMap
* LinkedHashMap 保存了记录的插入顺序，在用Iterator遍历LinkedHashMap时，先得到的记录肯定是先插入的。在遍历的时候会比HashMap慢，不过有种情况例外，当HashMap容量很大，实际数据较少时，遍历起来可能会比LinkedHashMap慢，因为LinkedHashMap的遍历速度只和实际数据有关，和容量无关，而HashMap的遍历速度和容量有关。

## TreeMap
* TreeMap实现SortMap接口，能够把它保存的记录根据键排序，默认是按键值的升序排序，也可以指定排序的比较器，当用Iterator 遍历TreeMap时，得到的记录是排过序的。
* use red black tree internally

## 比较：
* 一般情况下，我们用的最多的是HashMap，HashMap里面存入的键值对在取出的时候是随机的，它根据键的HashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度。在Map中插入、删除和定位元素，HashMap 是最好的选择。 
* TreeMap取出来的是排序后的键值对。但如果要按自然顺序或自定义顺序遍历键，那么TreeMap会更好。 
* LinkedHashMap是HashMap的一个子类，如果需要输出的顺序和输入的相同，那么用LinkedHashMap可以实现，它还可以按读取顺序来排列，像连接池中可以应用。　