# 7. Reverse Integer

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**

```
Input: 123
Output: 321
```

**Example 2:**

```
Input: -123
Output: -321
```

**Example 3:**

```
Input: 120
Output: 21
```

**Note:**
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.



**Java**

```java
class Solution {
    public int reverse(int x) {
        int rev = 0;
        while (x != 0){
            int pop = x % 10;
            x = x / 10;
            if (rev > Integer.MAX_VALUE / 10 || rev < Integer.MIN_VALUE / 10){
                return 0;
            }
            if (rev == Integer.MAX_VALUE / 10 && pop > 7 || rev == Integer.MIN_VALUE / 10 && pop < -8){
                return 0;
            }
            rev = 10 * rev + pop;
        }
        return rev;
    }
}
```

**Js**

JavaScript 中除法是除不准的，需要借助Math.floor()和Math.ceil()来实现整除

```javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    let rev = 0;
        while (x != 0){
            let pop = x % 10;
            x = x >= 0 ? Math.floor(x / 10) : Math.ceil(x / 10);
            if (rev > 214748364 || rev < -214748364){
                return 0;
            }
            if (rev == 214748364 && pop > 7 || rev == -214748364 && pop < -8){
                return 0;
            }
            rev = 10 * rev + pop;
        }
    return rev;
};
```

