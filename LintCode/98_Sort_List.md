# 链表排序

## 描述
在 O(n log n) 时间复杂度和常数级的空间复杂度下给链表排序。

## 样例
给出 `1->3->2->null`，给它排序变成 `1->2->3->null`.

## 挑战
分别用归并排序和快速排序做一遍。

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
    @param head: The first node of the linked list.
    @return: You should return the head of the sorted linked list,
                  using constant space complexity.
    """
    def sortList(self, head):
        # write your code here
        if head==None or head.next==None:
            return head
        mid = head
        last = head.next
        while last and last.next:
            last = last.next.next
            mid = mid.next
        head2 = mid.next
        mid.next = None
        return self.mergeTwoLists(self.sortList(head), self.sortList(head2));

    def mergeTwoLists(self, head1, head2):
        head3 = ListNode(-1)
        cur = head3
        while head1 and head2:
            if head1.val > head2.val:
                cur.next = head2
                head2 = head2.next
            else:
                cur.next = head1
                head1 = head1.next
            cur = cur.next
        cur.next = head1 if head2==None else head2
        return head3.next
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
     * @param head: The head of linked list.
     * @return: You should return the head of the sorted linked list,
                    using constant space complexity.
     */
    public ListNode sortList(ListNode head) {  
        // write your code here
        if (head == null || head.next == null) {
            return head;
        }
        ListNode mid = head;
        ListNode last = head.next;
        while (last != null && last.next != null) {
            mid = mid.next;
            last = last.next.next;
        }
        ListNode head2 = mid.next;
        mid.next = null;
        return mergeTwoLists(sortList(head), sortList(head2));
    }

    public ListNode mergeTwoLists(ListNode head1, ListNode head2) {
        ListNode head3 = new ListNode(-1);
        ListNode cur = head3;
        while (head1 != null && head2 != null) {
            if (head1.val > head2.val) {
                cur.next = head2;
                head2 = head2.next;
            } else {
                cur.next = head1;
                head1 = head1.next;
            }
            cur = cur.next;
        }
        cur.next = head1==null ? head2 : head1;
        return head3.next;
    }
}
```
