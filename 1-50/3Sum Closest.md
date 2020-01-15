# 16. 3Sum Closest

Given an array `nums` of *n* integers and an integer `target`, find three integers in `nums` such that the sum is closest to `target`. Return the sum of the three integers. You may assume that each input would have exactly one solution.

**Example:**

```
Given array nums = [-1, 2, 1, -4], and target = 1.

The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

**Js**

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var threeSumClosest = function(nums, target) {
    let dist = Number.MAX_VALUE;
    nums = nums.sort((a, b) => a - b);
    let sum;
    for (let i = 0; i < nums.length - 2; i++){
        if (i > 0 && nums[i] === nums[i - 1]) continue;
        for (let j = i + 1, k = nums.length - 1; j < k;){
            let tempS = nums[i] + nums[j] + nums[k];
            let tempD = Math.abs(target - tempS);
            sum = tempD < dist ? tempS : sum;
            dist = tempD < dist ? tempD : dist;
            if (tempS === target){
                return sum;
            }
            else if (tempS > target){
                k--;
            }
            else{
                j++;
            }
        }
    }
    return sum;
};
```
