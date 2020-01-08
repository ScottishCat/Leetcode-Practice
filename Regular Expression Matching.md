# 10. Regular Expression Matching

Given an input string (`s`) and a pattern (`p`), implement regular expression matching with support for `'.'` and `'*'`.

```
'.' Matches any single character.
'*' Matches zero or more of the preceding element.
```

The matching should cover the **entire** input string (not partial).

**Note:**

- `s` could be empty and contains only lowercase letters `a-z`.
- `p` could be empty and contains only lowercase letters `a-z`, and characters like `.` or `*`.

**Example 1:**

```
Input:
s = "aa"
p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

**Example 2:**

```
Input:
s = "aa"
p = "a*"
Output: true
Explanation: '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

**Example 3:**

```
Input:
s = "ab"
p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
```

**Example 4:**

```
Input:
s = "aab"
p = "c*a*b"
Output: true
Explanation: c can be repeated 0 times, a can be repeated 1 time. Therefore, it matches "aab".
```

**Example 5:**

```
Input:
s = "mississippi"
p = "mis*is*p*."
Output: false
```



**Explanation **

<https://www.cnblogs.com/mfrank/p/10472663.html>



**Java**

```java
class Solution {
    public boolean isMatch(String s, String p) {
        int m = s.length(), n = p.length();
        if (n == 0) return m == 0;
        boolean[][] dp = new boolean[m + 1][n + 1];
        dp[m][n] = true;
        for (int i = m; i >= 0; i--){
            for(int j = n - 1; j >= 0; j--){
                boolean curMatch = i < m && (s.charAt(i) == p.charAt(j) || p.charAt(j) == '.');
                if (j + 1 < n && p.charAt(j + 1) == '*'){
                    dp[i][j] = dp[i][j + 2] || curMatch && dp[i + 1][j];
                }
                else{
                    dp[i][j] = curMatch && dp[i + 1][j + 1];
                }
            }
        }
        return dp[0][0];
    }
}
```

**Js**

```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {boolean}
 */
var isMatch = function(s, p) {
    let m = s.length, n = p.length;
    if (n === 0) return m === 0;
    let dp = [];
    for (let i = 0; i <= m; i++){
        dp.push(new Array());
        for (let j = 0; j <= n; j++){
            dp[i].push(false);
        }
    }
    
    dp[m][n] = true;
    
    for (let i = m; i >= 0; i--){
        for (let j = n - 1; j >= 0; j--){
            let curMatch = i < m && (s[i] === p[j] || p[j] === '.');
            if (j + 1 < n && p[j + 1] == '*'){
                dp[i][j] = curMatch && dp[i + 1][j] || dp[i][j + 2];
            }
            else{
                dp[i][j] = curMatch && dp[i + 1][j + 1];
            }
        }
    }
    return dp[0][0];
};
```

**Note**

逻辑运算符是有”短路效应“的，因此应考虑好与或运算中两个表达式的顺序