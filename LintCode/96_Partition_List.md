# 链表划分

## 描述
给定一个单链表和数值x，划分链表使得所有小于x的节点排在大于等于x的节点之前。

你应该保留两部分内链表节点原有的相对顺序。

## 样例
给定链表 `1->4->3->2->5->2->null`，并且 `x=3`

返回 `1->2->2->4->3->5->null`

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
    @param x: an integer
    @return: a ListNode
    """
    def partition(self, head, x):
        # write your code here
        t1 = l1 = ListNode(-1)
        t2 = l2 = ListNode(-1)
        while head:
            node = ListNode(head.val)
            if head.val < x:
                t1.next = node
                t1 = t1.next
            else:
                t2.next = node
                t2 = t2.next
            head = head.next
        t1.next = l2.next
        return l1.next
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
     * @param x: an integer
     * @return: a ListNode
     */
    public ListNode partition(ListNode head, int x) {
        // write your code here
        ListNode l1 = new ListNode(-1);
        ListNode l2 = new ListNode(-1);
        ListNode t1 = l1;
        ListNode t2 = l2;
        while (head != null) {
            ListNode node = new ListNode(head.val);
            if (head.val < x) {
                t1.next = node;
                t1 = t1.next;
            } else {
                t2.next = node;
                t2 = t2.next;
            }
            head = head.next;
        }
        t1.next = l2.next;
        return l1.next;
    }
}
```
