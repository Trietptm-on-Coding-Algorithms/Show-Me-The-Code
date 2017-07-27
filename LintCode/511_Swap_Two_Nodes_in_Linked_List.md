# 交换链表当中两个节点

## 描述
给你一个链表以及两个权值v1和v2，交换链表中权值为v1和v2的这两个节点。保证链表中节点权值各不相同，如果没有找到对应节点，那么什么也不用做。

你需要交换两个节点而不是改变节点的权值

## 样例
给出链表 `1->2->3->4->null`，以及 `v1 = 2`， `v2 = 4`

返回结果 `1->4->3->2->null`。

## 标签
链表

## 分析

## 解答
### Python
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param {ListNode} head, a ListNode
    # @oaram {int} v1 an integer
    # @param {int} v2 an integer
    # @return {ListNode} a new head of singly-linked list
    def swapNodes(self, head, v1, v2):
        # Write your code here
        dummy = ListNode(-1)
        dummy.next = head
        cur = dummy
        while cur.next:
            if cur.next.val == v1:
                p1 = cur
            elif cur.next.val == v2:
                p2 = cur
            cur = cur.next
        if 'p1' in dir() and 'p2' in dir(): # 判断变量是否有定义
            n1 = p1.next
            n2 = p2.next
            n3 = n2.next
            if n1.next == n2:
                p1.next = n2
                n2.next = n1
                n1.next = n3
            elif n2.next == n1:
                p2.next = n1
                n3 = n1.next
                n1.next = n2
                n2.next = n3
            else:
                p1.next = n2
                n2.next = n1.next
                p2.next = n1
                n1.next = n3
        return dummy.next
```

### Java
```Java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    /**
     * @param head a ListNode
     * @oaram v1 an integer
     * @param v2 an integer
     * @return a new head of singly-linked list
     */
    public ListNode swapNodes(ListNode head, int v1, int v2) {
        // Write your code here
        ListNode dummy = new ListNode(-1);
        dummy.next = head;
        ListNode cur = dummy;
        ListNode p1 = null;
        ListNode p2 = null;
        while (cur.next != null) {
            if (cur.next.val == v1) {
                p1 = cur;
            }
            else if (cur.next.val == v2) {
                p2 = cur;
            }
            cur = cur.next;
        }
        if (p1 != null && p2 != null) {
            ListNode n1 = p1.next;
            ListNode n2 = p2.next;
            ListNode n3 = n2.next;
            if (n1.next == n2) {
                p1.next = n2;
                n2.next = n1;
                n1.next = n3;
            } else if (n2.next == n1) {
                p2.next = n1;
                n3 = n1.next;
                n1.next = n2;
                n2.next = n3;
            } else {
                p1.next = n2;
                n2.next = n1.next;
                p2.next = n1;
                n1.next = n3;
            }
        }
        return dummy.next;
    }
}
```
