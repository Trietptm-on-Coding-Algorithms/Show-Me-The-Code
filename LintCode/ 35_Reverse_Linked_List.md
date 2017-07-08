# 翻转链表

## 描述
翻转一个链表

## 样例
给出一个链表`1->2->3->null`，这个翻转后的链表为`3->2->1->null`

## 挑战
在原地一次翻转完成

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
    @return: You should return the head of the reversed linked list.
                  Reverse it in-place.
    """
    def reverse(self, head):
        # write your code here
        dummy = ListNode(-1)
        while head:
            node = head
            head = head.next
            node.next = dummy.next
            dummy.next = node
        return dummy.next
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
     * @return: The new head of reversed linked list.
     */
    public ListNode reverse(ListNode head) {
        // write your code here
        ListNode dummy = new ListNode(-1);
        while (head != null) {
            ListNode node = head;
            head = head.next;
            node.next = dummy.next;
            dummy.next = node;
        }
        return dummy.next;
    }
}
```
