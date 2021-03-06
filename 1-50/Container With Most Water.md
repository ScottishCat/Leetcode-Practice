# 11. Container With Most Water

Given *n* non-negative integers *a1*, *a2*, ..., *an* , where each represents a point at coordinate (*i*, *ai*). *n* vertical lines are drawn such that the two endpoints of line *i* is at (*i*, *ai*) and (*i*, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

**Note:** You may not slant the container and *n* is at least 2.

 

![img](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

 

**Example:**

```
Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```



**Java**

```java
class Solution {
    public int maxArea(int[] height) {
        int max = 0, left = 0, right = height.length - 1;
        while(left < right){
            int cur = Math.min(height[left], height[right]) * (right - left);
            max = Math.max(max, cur);
            if (height[left] < height[right]){
                left++;
            }
            else{
                right--;
            }
        }
        return max;
    }
}
```

**Js**

```javascript
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    let max = 0, left = 0, right = height.length - 1;
    while (left < right){
        let cur = Math.min(height[left], height[right]) * (right - left);
        max = Math.max(max, cur);
        if (height[left] < height[right]){
            left++
        }
        else{
            right--;
        }
    }
    return max;
};
```

