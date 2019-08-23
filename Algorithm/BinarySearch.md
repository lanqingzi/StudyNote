length of LIS

O($n^2$) 解法：

Dp[i] 表示以第i个数字为结尾的最长上升子序列的长度。
对于每个数字，枚举前面所有小于自己的数字 j，Dp[i] = max{Dp[j]} + 1. 如果没有比自己小的，Dp[i] = 1;

O($nlogn$)解法：

使用一个辅助空间B数组。
B[i]存储Dp值为i的最小的数字。（有多个位置，以这些位置为结尾的LIS长度都为i， 则这些数字中最小的一个存在B[i]中）
则B数组严格递增。且下标表示LIS长度，也是严格递增，可以在B数组中进行二分查找。

对于每个位置i，我们要找，所有小于A[i], 且Dp值最大的那个。这个操作在B数组中二分查找。

$O(n^2)$ solution
``` java
public int longestIncreasingSubsequence(int[] nums) {
    int []f = new int[nums.length];
    int max = 0;
    for (int i = 0; i < nums.length; i++) {
        f[i] = 1;
        for (int j = 0; j < i; j++) {
            if (nums[j] < nums[i]) {
                f[i] = f[i] > f[j] + 1 ? f[i] : f[j] + 1;
            }
        }
        if (f[i] > max) {
            max = f[i];
        }
    }
    return max;
}
```

$O(nlogn)$ solution
``` java
public int lengthOfLIS(int[] nums) {
    if (nums == null || nums.length == 0) {
        return 0;
    }
    // minLast[-1] is alwyas Integer.MAX_VALUE
    int[] minLast = new int[nums.length + 1];
    for (int i = 0; i <= nums.length; i++) {
        minLast[i] = Integer.MAX_VALUE;
    }

    for (int i = 0; i < nums.length; i++) {
        int index = binarySearch(minLast, nums[i]);
        minLast[index] = nums[i];
    }

    return binarySearch(minLast, Integer.MAX_VALUE);
}
```
---
find Kth element in two sorted array  

```java
private int findKth(int[] A, int startA, int[] B, int startB, int k) {
    if (startA >= A.length) {
        return B[startB + k - 1];
    }
    if (startB >= B.length) {
        return A[startA + k - 1];
    }

    if (k == 1) return Math.min(A[startA], B[startB]);

    int halfKthOfA = startA + k/2 - 1 < A.length
                        ? A[startA + k/2 - 1]
                        : Integer.MAX_VALUE;
    int halfKthOfB = startB + k/2 - 1 < B.length
                        ? B[startB + k/2 - 1]
                        : Integer.MAX_VALUE;

    if (halfKthOfA < halfKthOfB) {
        return findKth(A, startA + k/2, B, startB, k - k/2);
    } else {
        return findKth(A, startA, B, startB + k/2, k - k/2);
    }
}
```