# 4. Median of Two Sorted Arrays

There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume **nums1** and **nums2** cannot be both empty.

**Example 1:**

```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```

**Example 2:**

```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```



A good explanation of this problem:

<https://medium.com/@hazemu/finding-the-median-of-2-sorted-arrays-in-logarithmic-time-1d3f2ecbeb46>



**Cpp**

```c++
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        
        int n1 = nums1.size(), n2 = nums2.size();
        
        if (n1 > n2){
            return findMedianSortedArrays(nums2, nums1);
        }
        
        int n = (n1 + n2 + 1) / 2;
        int left = 0, right = n1;
        
        while(left <= right){
            int count_1 = left + (right - left) / 2;
            int count_2 = n - count_1;
            if (count_1 > 0 && nums1[count_1 - 1] > nums2[count_2]){
                right = count_1 - 1;
            }
            else if (count_1 < n1 && nums2[count_2 - 1] > nums1[count_1]){
                left = count_1 + 1;
            }
            else{
                double mid1 = count_1 == 0 ? nums2[count_2 - 1] :
                count_2 == 0 ? nums1[count_1 - 1] :
                max(nums1[count_1 - 1], nums2[count_2 - 1]);
                
                if ((n1 + n2) % 2 != 0){
                    return mid1;
                }
                
                double mid2 = count_1 == n1 ? nums2[count_2] :
                count_2 == n2 ? nums1[count_1] :
                min(nums1[count_1], nums2[count_2]);
                
                return (mid1 + mid2) / 2;
            }
        }
        return 0.0;
    }
};
```

**Js**

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var findMedianSortedArrays = function(nums1, nums2) {
    
    const n1 = nums1.length, n2 = nums2.length;
    
    if (n1 > n2){
        return findMedianSortedArrays(nums2, nums1);
    }
    
    const n = Math.floor((n1 + n2 + 1) / 2);
    let left = 0, right = n1;
    
    while(left <= right){
        let count_1 = Math.floor((left + right) / 2);
        let count_2 = n - count_1;
        if (count_1 > 0 && nums1[count_1 - 1] > nums2[count_2]){
            right = count_1 - 1;
        }
        else if (count_1 < n1 && nums2[count_2 - 1] > nums1[count_1]){
            left = count_1 + 1;
        }
        else{
            let mid1 = count_1 === 0 ? nums2[count_2 - 1] :
            count_2 === 0 ? nums1[count_1 - 1] : 
            Math.max(nums1[count_1 - 1], nums2[count_2 - 1]);
            
            if ((n1 + n2) % 2 !== 0){
                return mid1;
            }
            
            let mid2 = count_1 === n1 ? nums2[count_2] :
            count_2 === n2 ? nums1[count_1] :
            Math.min(nums1[count_1], nums2[count_2]);
            
            return (mid1 + mid2) / 2
        }
    }
    return 0.0;
};
```

