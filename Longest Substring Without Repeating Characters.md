# 3. Longest Substring Without Repeating Characters

Given a string, find the length of the **longest substring** without repeating characters.

**Example 1:**

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

**Example 2:**

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Cpp**

```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int n = s.length();
        if (n == 0){
            return 0;
        }
        int left = 0, right = 1, res = 1;
        unordered_map<char, int> m;
        m[s[0]] = 0;
        while(right < n){
            if (m.find(s[right]) != m.end() && m.at(s[right]) >= left){
                left = m[s[right]] + 1;
            }
            m[s[right]] = right;
            right++;
            res = max(res, right - left);
        }
        return res;
    }
};
```

**Js**

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    
    if (s.length === 0) return 0;
    
    let left = 0, right = 1, res = 1;
    let map = new Map();
    const size = s.length;
    
    map.set(s[0], 0);
    
    while(right < size){
        if (map.has(s[right]) && map.get(s[right]) >= left){
            left = map.get(s[right]) + 1;
        }
        
        map.set(s[right], right);
        right++;
        res = Math.max(res, right - left);
    }
    return res;
};
```

