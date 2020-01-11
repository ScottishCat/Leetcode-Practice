# 18. 4Sum

Given an array `nums` of *n* integers and an integer `target`, are there elements *a*, *b*, *c*, and *d* in `nums` such that *a* + *b* + *c* + *d* = `target`? Find all unique quadruplets in the array which gives the sum of `target`.

**Note:**

The solution set must not contain duplicate quadruplets.

**Example:**

```
Given array nums = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```



**Js**

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[][]}
 */
let TwoSum = (nums, target) => {
    const res = [];
    let left = 0, right = nums.length - 1;
    while(left < right){
        if (nums[left] + nums[right] === target){
            res.push([nums[left], nums[right]]);
            left++;
            right--;
            while(left < right && nums[left] === nums[left - 1]){
                left++;
            }
            while(left < right && nums[right] === nums[right + 1]){
                right--;
            } 
        }
        else if (nums[left] + nums[right] < target){
            left++;
            while(left < right && nums[left] === nums[left - 1]){
                left++;
            }
        }
        else{
            right--;
            while(left < right && nums[right] === nums[right + 1]){
                right--;
            }
        }
    }
    return res;
}

//Recursive Function
let Nsum = (nums, target, n) => {
    if (n === 2){
        return TwoSum(nums, target);
    }
    else{
        const res = [];
        for (let i = 0; i < nums.length - n + 1; i++){
            while(nums[i] === nums[i - 1]) i++;
            Nsum(nums.slice(i + 1), target - nums[i], n - 1).forEach(innerRes => res.push([nums[i], ...innerRes]));
        }
        return res;
    }
}

var fourSum = function(nums, target) {
    nums = nums.sort((a, b) => a - b);
    return Nsum(nums, target, 4);
};
```


