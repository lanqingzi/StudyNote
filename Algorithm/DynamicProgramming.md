Related problem: [length of LIS](./BinarySearch.md) 
* 信封存在两个维度，首先贪心按照其中一个维度将信封排序，一个维然后在另度上面寻找最长上升子序列。
* 此处使用二分优化最长上升子序列，在dp数组中二分查找envelope[1]的位置，当envelope[1]超出范围时会返回-（maxlength+1）需要特殊处理，dp[index] = envelope[1]，当返回的位置为最后为len时，说明插入位置为len，则长度可以+1。

```java
/**
 * @param envelopes a number of envelopes with widths and heights
 * @return the maximum number of envelopes
 */
public int maxEnvelopes(int[][] envelopes) {
    // Write your code here
    if(envelopes == null || envelopes.length == 0 
        || envelopes[0] == null || envelopes[0].length != 2)
        return 0;
    Arrays.sort(envelopes, new Comparator<int[]>(){
        public int compare(int[] arr1, int[] arr2){
            if(arr1[0] == arr2[0])
                return arr2[1] - arr1[1];
            else
                return arr1[0] - arr2[0];
        } 
    });
    int dp[] = new int[envelopes.length];
    int len = 0;
    for(int[] envelope : envelopes){
        int index = Arrays.binarySearch(dp, 0, len, envelope[1]);
            if(index < 0)
                index = -index - 1;
        dp[index] = envelope[1];
        if (index == len)
            len++;
    }
    return len;
}
```