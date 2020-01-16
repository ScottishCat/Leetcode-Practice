# 29. Divide Two Integers

Given two integers `dividend` and `divisor`, divide two integers without using multiplication, division and mod operator.

Return the quotient after dividing `dividend` by `divisor`.

The integer division should truncate toward zero.

**Example 1:**

```
Input: dividend = 10, divisor = 3
Output: 3
```

**Example 2:**

```
Input: dividend = 7, divisor = -3
Output: -2
```

**Note:**

- Both dividend and divisor will be 32-bit signed integers.
- The divisor will never be 0.
- Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 231 − 1 when the division result overflows.

**Java**

```java
class Solution {
    public int divide(int dividend, int divisor) {
        if (divisor == 1) return dividend;
        if (dividend == Integer.MIN_VALUE && divisor == -1){
            return Integer.MAX_VALUE;
        }
        int a = dividend < 0 ? -dividend : dividend;
        int b = divisor < 0 ? -divisor : divisor;
        int result = 0, x;
        while (a - b >= 0){
            x = 0;
            while (a - (b<<x) >= 0){
                x++;
            }
            x--;
            result += 1<<x;
            a -= b<<x;
        }
        
        return (dividend >= 0 && divisor > 0 || dividend < 0 && divisor < 0) ? result : -result;
    }
}
```

