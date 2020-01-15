# 24. Swap Nodes in Pairs

Given a linked list, swap every two adjacent nodes and return its head.

You may **not** modify the values in the list's nodes, only nodes itself may be changed.

 

**Example:**

```
Given 1->2->3->4, you should return the list as 2->1->4->3.
```

**Js**

![](https://tva1.sinaimg.cn/large/006tNbRwgy1gawukced4ij30g904uweg.jpg)

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
 * @return {ListNode}
 */
var swapPairs = function(head) {
    if (head === null || head.next === null) return head;
    const start = new ListNode(-1);
    let prev = start, cur = head;
    while(cur !== null && cur.next !== null){
        let first = cur;
        let second = cur.next;
        prev.next = second;
        first.next = second.next;
        second.next = first;
        prev = first;
        cur = first.next;
    }
    return start.next;
};
```
