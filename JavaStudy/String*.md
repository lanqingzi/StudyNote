Convert vector of String to String array
``` java
Vector<String> result = new Vector<>();
result.add("...");
// convert to object array
// return result.toArray();
// new style in Java8
return result.toArray(new String[0]);
// Old style:
// return result.toArray(new String[result.size()]);
```
---
