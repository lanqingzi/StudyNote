Greatest Common Divisor GCD
``` java
private int GCD(int a, int b) {
    if (b == 0) return a;
    return a % b == 0 ? b : GCD(b, a%b);
}
```
---
主要利用异或运算来完成
异或运算有一个别名叫做：不进位加法
那么a ^ b就是a和b相加之后，该进位的地方不进位的结果
然后下面考虑哪些地方要进位，自然是a和b里都是1的地方
a & b就是a和b里都是1的那些位置，a & b << 1 就是进位
之后的结果。所以：a + b = (a ^ b) + (a & b << 1)
令a' = a ^ b, b' = (a & b) << 1
可以知道，这个过程是在模拟加法的运算过程，进位不可能
一直持续，所以b最终会变为0。因此重复做上述操作就可以
求得a + b的值。
``` java
public int aplusb(int a, int b) {
    while (b != 0) {
        int _a = a ^ b;
        int _b = (a & b) << 1;
        a = _a;
        b = _b;
    }
    return a;
}
```
---
trailingZeros  
可以将每个数拆分成其素因子的乘积，可以发现，0是由2*5产生的，而5的数量一定小于2的数量，因此5的个数决定了结尾0的个数。
只要计算n的阶乘中，5这个素因子出现多少次即可。

---
Lintcode 141
``` java
public int sqrt(int x) {
    if (x == 0 || x == 1) return x;
    int start = 1;
    int end = x/2;
    int mid;

    while (start + 1 < end) {
        mid = start + (end - start)/2;
        if (mid > x/mid) {
            end = mid;
        } else {
            start = mid;
        }
    }

    if (end < x/end) return end;
    else return start;
}
```
use `mid*mid > x` may cause overflow. use `mid > x/mid` instead to avoid using `long`.  

---
