# 2. Add Two Numbers

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```



**Cpp**

```c++
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        
        auto head = l1;
        int carry = 0;
        int sum;
        
        while (l1|| l2|| carry == 1){      
            sum = l1->val + l2->val + carry;
            l1->val = sum % 10;
            carry = sum / 10;

            if ((!l1->next && l2->next) || (l1->next && !l2->next) || carry == 1){
                if (l1->next == 0){
                    l1->next = new ListNode(0);
                }
                if (l2->next == 0){
                    l2->next = new ListNode(0);
                }
            }
            
            l1 = l1->next;
            l2 = l2->next;
        }
        
        return head;
    }
};
```

**Js**

```javascript
var addTwoNumbers = function(l1, l2) {
    let carry = 0;
    const head = l1;
    let sum;
    while (l1 || l2 || carry === 1){
        sum = l1.val + l2.val + carry;
        l1.val = sum % 10;
        carry = Math.floor(sum / 10);
        
        if ((!l1.next && l2.next) || (l1.next && !l2.next) || carry === 1){
            l1.next = l1.next ? l1.next : new ListNode(0);
            l2.next = l2.next ? l2.next : new ListNode(0);
        }
        
        l1 = l1.next;
        l2 = l2.next;
    }
    return head;
};
```

