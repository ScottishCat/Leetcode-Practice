# 20. Valid Parentheses

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Example 1:**

```
Input: "()"
Output: true
```

**Example 2:**

```
Input: "()[]{}"
Output: true
```

**Example 3:**

```
Input: "(]"
Output: false
```

**Example 4:**

```
Input: "([)]"
Output: false
```

**Example 5:**

```
Input: "{[]}"
Output: true
```



**Java**

```Java
class Solution {
    public boolean isValid(String s) {
        LinkedList<Character> stack = new LinkedList<>();
        for (int i = 0; i < s.length(); i++){
            if (stack.isEmpty() || s.charAt(i) == '(' || s.charAt(i) == '{' || s.charAt(i) == '['){
                stack.addLast(s.charAt(i));
            }
            else{
                char top = stack.peekLast();
                if (top == '(' && s.charAt(i) != ')' || top == '{' && s.charAt(i) != '}' || top == '[' && s.charAt(i) != ']'){
                    return false;
                }
                if (!stack.isEmpty()){
                    stack.removeLast();
                }
            }
        }
        return stack.isEmpty();
    }
}
```



**Js**

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    let stack = [], cur = 0;
    while(cur < s.length){
        if (s[cur] === '(' || s[cur] === '{' || s[cur] === '[' || stack.length === 0){
            stack.push(s[cur]);
        }
        else{
            let top = stack[stack.length - 1];
            if (top === '(' && s[cur] !== ')' || top === '{' && s[cur] !== '}' || top === '[' && s[cur] !== ']'){
                return false;
            }
            if (stack.length !== 0){
                stack.pop();
            }
        }
        cur++;
    }
    return stack.length === 0;
};
```
