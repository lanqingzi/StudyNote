Greatest Common Divisor GCD
``` java
private int GCD(int a, int b) {
    if (b == 0) return a;
    return a % b == 0 ? b : GCD(b, a%b);
}
```
---
