# 5. Longest Palindromic Substring

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example 1:**

```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

**Example 2:**

```
Input: "cbbd"
Output: "bb"
```

**Java**

```java
class Solution{
    public String longestPalindrome(String s) {
        if (s == null || s.length() < 1) return "";
        int start = 0, end = 0;
        for (int i = 0; i < s.length(); i++) {
            int len1 = expandAroundCenter(s, i, i);
            int len2 = expandAroundCenter(s, i, i + 1);
            int len = Math.max(len1, len2);
            if (len > end - start) {
                start = i - (len - 1) / 2;
                end = i + len / 2;
            }
        }
        return s.substring(start, end + 1);
    }

    private int expandAroundCenter(String s, int left, int right) {
        int L = left, R = right;
        while (L >= 0 && R < s.length() && s.charAt(L) == s.charAt(R)) {
            L--;
            R++;
        }
        return R - L - 1;
    }
}
```

**Js**

```javascript
/**
 * @param {string} s
 * @return {string}
 */
let expand = function(s, left, right){
    while (left >= 0 && right < s.length && s[left] === s[right]){
        left--;
        right++;
    }
    return [left + 1, right - 1];
}

var longestPalindrome = function(s) {
    const len = s.length;
    if (len < 1){return "";}
    let left = 0, right = 0;
    let ans = s[0];
    for (let i = 0; i < len - 1; i++){  
        let L, R, L1, R1, L2, R2;
        [L1, R1] = expand(s, i, i + 1);
        [L2, R2] = expand(s, i, i);
        [L, R] = R1 - L1 > R2 - L2 ? [L1, R1] : [L2, R2];
        if (R - L > right - left){
            right = R;
            left = L;
            ans = s.substring(left, right + 1);
        }
    }
    return ans;
};
```

