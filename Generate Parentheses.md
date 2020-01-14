# 22. Generate Parentheses

Given *n* pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given *n* = 3, a solution set is:

```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```

**Java**

```java
class Solution {
    public List<String> output = new LinkedList<>();
    public int len;
    public void backtrack(String cur, int left, int right){
        if (cur.length() == len){
            output.add(cur);
            return;
        }
        if (left > 0){
            backtrack(cur + '(', left - 1, right);
        }  
        if (right > left){
            backtrack(cur + ')', left, right - 1);
        }
    }
    public List<String> generateParenthesis(int n) {
        len = 2 * n;
        backtrack("", n, n);
        return output;
    }
}
```

**Js**

```javascript
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
    const max = 2 * n, res = [];
    let backtrack = function(cur, left, right){
        if (cur.length === max){
            res.push(cur);
            return;
        }
        if (left > 0){
            backtrack(cur + '(', left - 1, right);
        }
        if (right > left){
            backtrack(cur + ')', left, right - 1);
        }
    }
    backtrack("", n, n);
    return res;
};
```
