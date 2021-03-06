#  链表倒数第n个节点

## 描述
找到单链表倒数第n个节点，保证链表中节点的最少数量为n。

## 样例
给出链表 `3->2->1->5->null`和`n = 2`，返回倒数第二个节点的值1.

## 标签
链表

## 分析

## 解答
### Python
```Python
"""
Definition of ListNode
class ListNode(object):

    def __init__(self, val, next=None):
        self.val = val
        self.next = next
"""
class Solution:
    """
    @param head: The first node of linked list.
    @param n: An integer.
    @return: Nth to last node of a singly linked list.
    """
    def nthToLast(self, head, n):
        # write your code here
        cur = head
        tmp = head
        for i in range(n):
            tmp = tmp.next
        while tmp:
            cur = cur.next
            tmp = tmp.next
        return cur
```

### Java
```Java
/**
 * Definition for ListNode.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) {
 *         this.val = val;
 *         this.next = null;
 *     }
 * }
 */
public class Solution {
    /**
     * @param head: The first node of linked list.
     * @param n: An integer.
     * @return: Nth to last node of a singly linked list.
     */
    ListNode nthToLast(ListNode head, int n) {
        // write your code here
        ListNode cur = head;
        ListNode tmp = head;
        for (int i=0; i<n; i++) {
            tmp = tmp.next;
        }
        while (tmp != null) {
            cur = cur.next;
            tmp = tmp.next;
        }
        return cur;
    }
}
```
