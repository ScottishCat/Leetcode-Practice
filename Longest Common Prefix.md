# 14. Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**Example 1:**

```
Input: ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**

```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Note:**

All given inputs are in lowercase letters `a-z`.



**Js**

```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    const len = strs.length;
    let res = "";
    if (!strs || len === 0) return res;
    for (let i = 0; i < strs[0].length; i++){
        let match = true;
        for (let j = 1; j < len; j++){
            match = match && strs[j - 1][i] === strs[j][i];
            if (!match){
                break;
            }
        }
        if (match){
            res += strs[0][i];
        }
        else{
            break;
        }
    }
    return res;
};
```

