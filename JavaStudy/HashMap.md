how to create a hashmap with two keys  
* String concate concatenation  
**easy, clean, fast**
``` java
String key = key1.toString() + "|" + key2.toString();
```
* Map of maps  
not a good way, hard to write/read, complicate syntax
``` java
Map<Integer, Map<Integer, V>> map = //...
//...
map.get(2).get(5);
```
* Wrap key object  
need to override **equals()** and **hashCode()** function, very time comsuming
``` java
public class Key {

    private final int x;
    private final int y;

    public Key(int x, int y) {
        this.x = x;
        this.y = y;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Key)) return false;
        Key key = (Key) o;
        return x == key.x && y == key.y;
    }

    @Override
    public int hashCode() {
        int result = x;
        result = 31 * result + y;
        return result;
    }

}

Map<Key, V> map = //...
map.get(new Key(2, 5));
```
* Table from Guava  
need extra library to support, use map of maps underneath
```java
Table<Integer, Integer, V> table = HashBasedTable.create();
//...

table.get(2, 5);
```
---
Iterate through hashMap
``` java
public static void printMap(Map mp) {
    Iterator it = mp.entrySet().iterator();
    while (it.hasNext()) {
        Map.Entry pair = (Map.Entry)it.next();
        System.out.println(pair.getKey() + " = " + pair.getValue());
        it.remove(); // avoids a ConcurrentModificationException
    }
}
```
---
Iterate through map of maps
``` java
Map<String,Map<String,List<String>>> m = new HashMap<String, Map<String,List<String>>>();

for(String k : m.keySet()) {
    Map<String,List<String>> m1 = m.get(k);

    for(String k1 : m1.keySet()) {
        List<String> l = m1.get(k1);

        for (String s : l){
        }
    }
}
```
---