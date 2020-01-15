# 23. Merge k Sorted Lists

Merge *k* sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

**Example:**

```
Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
```



**Java**

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        int n = lists.length;
        int interval = 1;
        while(interval < n){
            for (int i = 0; i < n - interval; i = i + interval * 2){
                lists[i] = mergeLists(lists[i], lists[i + interval]);
            }
            interval = interval * 2;
        }
        return n > 0 ? lists[0] : null;
    }
    
    public ListNode mergeLists(ListNode list1, ListNode list2){
        ListNode head = new ListNode(-1);
        ListNode cur = head;
        while (list1 != null && list2 != null){
            if (list1.val <= list2.val){
                cur.next = list1;
                list1 = list1.next;
            }
            else{
                cur.next = list2;
                list2 = list2.next;
            }
            cur = cur.next;
        }
        cur.next = list1 != null ? list1 : list2;
        return head.next;
    }
}
```

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
 * @param {ListNode[]} lists
 * @return {ListNode}
 */
var mergeKLists = function(lists) {
    const n = lists.length;
    let interval = 1;
    let mergeList = (list1, list2) => {
        let cur = new ListNode(-1);
        let pre = cur;
        while(list1 !== null && list2 !== null){
            if (list1.val <= list2.val){
                cur.next = list1;
                list1 = list1.next;
            }
            else{
                cur.next = list2;
                list2 = list1;
                list1 = cur.next.next;
            }
            cur = cur.next;
        }
        cur.next = list1 === null ? list2 : list1;
        return pre.next;
    }
    
    while(interval < n){
        for (let i = 0; i < n - interval; i = i + interval * 2){
            lists[i] = mergeList(lists[i], lists[i + interval]);
        }
        interval = interval * 2;
    }
    return lists[0] === undefined ? null : lists[0]
};
```
