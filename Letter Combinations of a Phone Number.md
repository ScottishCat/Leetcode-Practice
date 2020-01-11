# 17. Letter Combinations of a Phone Number

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![img](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**Example:**

```
Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.



**Js**

```javascript
/**
 * @param {string} digits
 * @return {string[]}
 */

var letterCombinations = function(digits) {
    let res = [];
    const map = new Map();
    map.set("2", "abc");
    map.set("3", "def");
    map.set("4", "ghi");
    map.set("5", "jkl");
    map.set("6", "mno");
    map.set("7", "pqrs");
    map.set("8", "tuv");
    map.set("9", "wxyz");
    
    // Recursive function
    let backtrack = (combination, next_iter) => {
        if (next_iter.length === 0){
            res.push(combination); 
        }
        else{
            let letters = map.get(next_iter[0]);
            for (let i = 0; i < letters.length; i++){
                let letter = letters[i];
                backtrack(combination + letter, next_iter.substring(1));
            }
        }
    }

    if (digits.length !== 0){
        backtrack("", digits);
    }
    return res;
};
```

