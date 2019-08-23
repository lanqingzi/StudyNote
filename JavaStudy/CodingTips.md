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
String.split("[,|+]");  

---
sort 2D array
``` java
int[][] envelopes;
Arrays.sort(envelopes, new Comparator<int[]>({
    public int compare(int[] arr1, int[] arr2){
        if(arr1[0] == arr2[0])
            return arr2[1] - arr1[1];
        else
            return arr1[0] - arr2[0];
    } 
});
```
---
``` java
// java.util.Arrays.binarySearch()
public static int binarySearch(int[] a, int key)
public static int binarySearch(int[] a, int fromIndex, int toIndex, int key)
```
Parameters  
* a − This is the array to be searched.
* fromIndex − This is the index of the first element (inclusive) to be searched.
* toIndex − This is the index of the last element (exclusive) to be searched.
* key − This is the value to be searched for.

return the index of key, return -1 otherwise

---