When array is required for return, I can create a set or list first. Then add elements to an result array.

``` java
Set<Integer> result = new HashSet<>();
// add Integer to result

int[] resultArray = new int[result.size()];
int count = 0;
for (num : result) {
    resultArray[count++] = num;
}
```
---
