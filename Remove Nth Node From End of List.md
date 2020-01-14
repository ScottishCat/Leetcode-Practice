# 19. Remove Nth Node From End of List

Given a linked list, remove the *n*-th node from the end of list and return its head.

**Example:**

```
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
```

**Note:**

Given *n* will always be valid.

**Follow up:**

Could you do this in one pass?



**Js**

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    if (head.next === null) return null;
    let slow = head, fast = head;
    while (n > 0){
        fast = fast.next;
        n--;
    }
    while(fast !== null){
        fast = fast.next;
        slow = slow.next;
    }
    if (slow.next === null){
        let pre = head;
        while(pre.next != slow){
            pre = pre.next;
        }
        pre.next = null;
    }
    else{
        slow.val = slow.next.val;
        slow.next = slow.next.next;
    }
    return head;
};
```
