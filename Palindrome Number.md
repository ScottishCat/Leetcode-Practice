# 9. Palindrome Number

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

**Example 1:**

```
Input: 121
Output: true
```

**Example 2:**

```
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

**Example 3:**

```
Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

**Follow up:**

Coud you solve it without converting the integer to a string?

**Hint**

Remember *Reverting Integer* ?

Revert half of the string and see if

reverted == remain (when string has even characters)

or

reverted / 10 == remain (when string has odd characters)  

The central character does not mater.

**Java**

```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || x % 10 == 0 && x != 0) return false;
        int num = x, reversed = 0, pop;
        while (num != 0 && reversed < num){
            pop = num % 10;
            num = num / 10;
            reversed = reversed * 10 + pop;
        }
        return reversed == num || reversed / 10 == num;
    }
}
```

**Js**

```javascript
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    if(x < 0 || x % 10 === 0 && x !== 0){
        return false;
    }
    let reversed = 0;
    while(x != 0 && reversed < x){
        let pop = x % 10;
        x = Math.floor(x / 10);
        reversed = reversed * 10 + pop;
    }   
    return reversed === x || Math.floor(reversed / 10) === x;
};
```

