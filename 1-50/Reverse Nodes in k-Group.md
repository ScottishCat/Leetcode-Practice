# 25. Reverse Nodes in k-Group

Given a linked list, reverse the nodes of a linked list *k* at a time and return its modified list.

*k* is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of *k* then left-out nodes in the end should remain as it is.



**Example:**

Given this linked list: `1->2->3->4->5`

For *k* = 2, you should return: `2->1->4->3->5`

For *k* = 3, you should return: `3->2->1->4->5`

**Note:**

- Only constant extra memory is allowed.
- You may not alter the values in the list's nodes, only nodes itself may be changed.

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
 * @param {number} k
 * @return {ListNode}
 */
var reverseKGroup = function(head, k) {
    if (head === null) return head;
    let reverse = (head)=>{
        let cur = head, prev = null;
        while (cur !== null){
            let next = cur.next;
            cur.next = prev;
            prev = cur;
            cur = next;
        }
        return [prev, head];
    }
    const start = new ListNode(-1);
    let cur = head, prev = start, next = cur.next;
    while (cur !== null){
        // Cut the list 
        let temp = cur;
        for (let i = 0; i < k - 1; i++){
            if (temp === null){
                break;
            }
            temp = temp.next;
        }
        // If the remain part is less than k
        if (temp === null){
            prev.next = cur;
            return start.next;
        }
        else{
            next = temp.next;
            temp.next = null;
            // Reverse current part
            let res = reverse(cur);
            prev.next = res[0];
            prev = res[1];
            cur = next;
        }
    }
    return start.next;
};
```
