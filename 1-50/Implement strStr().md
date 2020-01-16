# 28. Implement strStr()

Implement [strStr()](http://www.cplusplus.com/reference/cstring/strstr/).

Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

**Example 1:**

```
Input: haystack = "hello", needle = "ll"
Output: 2
```

**Example 2:**

```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

**Clarification:**

What should we return when `needle` is an empty string? This is a great question to ask during an interview.

**Js**

```javascript
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    if (needle === "") return 0;
    if (haystack === "") return needle === "" ? 0 : -1;
    
    let move = [];
    const pLen = needle.length, tLen = haystack.length;
    for (let i = 0; i < 128; i++){
        move.push(pLen + 1);
    }
    for (let i = 0; i < pLen; i++){
        move[needle[i].charCodeAt(0)] = pLen - i;
    }
    let tp = 0, match;
    while (tp <= tLen - pLen){
        match = 0;
        while (haystack[tp + match] === needle[match]){
            match++;
            if (match >= pLen){
                return tp;
            }
        }
        if (tp + pLen >= tLen) return -1;
        tp = tp + move[haystack[tp + pLen].charCodeAt(0)];
    }
    return -1;
};
```

