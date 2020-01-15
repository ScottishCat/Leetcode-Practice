# 1. Two Sum

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the *same* element twice.

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```



**Solution:**

**Cpp**

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> m;
        vector<int> res(2,0);
        for (int i = 0; i < nums.size(); i++){
            if (m.count(target - nums[i]) != 0){
                res[0] = i;
                res[1] = m[target - nums[i]];
                return res;
            }
            m[nums[i]] = i;
        }
        return res;
    }
};
```

**Js**

```javascript
var twoSum = function(nums, target) {
    const map = new Map();
    for (let i = 0; i < nums.length; i++){
        let temp = map.get(target - nums[i]);
        if (temp !== undefined){
            return [temp, i];
        }
        
        map.set(nums[i],i);
    }
    return res;
};
```

