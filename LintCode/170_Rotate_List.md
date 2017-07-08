# 旋转链表

## 描述
给定一个链表，旋转链表，使得每个节点向右移动k个位置，其中k是一个非负数

## 样例
给出链表`1->2->3->4->5->null`和`k=2`

返回`4->5->1->2->3->null`

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
    # @param head: the list
    # @param k: rotate to the right k places
    # @return: the list after rotation
    def rotateRight(self, head, k):
        # write your code here
        num = 0
        tmp = head
        while tmp:
            num += 1
            tmp = tmp.next
        if head:
            for i in range(k % num):
                tmp = head.next
                pre = head
                while tmp.next:
                    tmp = tmp.next
                    pre = pre.next
                tmp.next = head
                pre.next = None
                head = tmp
        return head
```

### Java
```Java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    /**
     * @param head: the List
     * @param k: rotate to the right k places
     * @return: the list after rotation
     */
    public ListNode rotateRight(ListNode head, int k) {
        // write your code here
        int num = 0;
        ListNode tmp = head;
        while (tmp != null) {
            num += 1;
            tmp = tmp.next;
        }
        if (head != null) {
            for (int i=0; i<(k%num); i++) {
                tmp = head.next;
                ListNode pre = head;
                while (tmp.next != null) {
                    tmp = tmp.next;
                    pre = pre.next;
                }
                tmp.next = head;
                pre.next = null;
                head = tmp;
            }
        }
        return head;
    }
}
```
