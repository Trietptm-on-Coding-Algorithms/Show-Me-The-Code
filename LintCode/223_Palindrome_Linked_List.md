# 回文链表

## 描述
设计一种方式检查一个链表是否为回文链表。

## 样例
`1->2->1` 就是一个回文链表。

## 挑战
O(n)的时间和O(1)的额外空间。

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
    # @param head, a ListNode
    # @return a boolean
    def isPalindrome(self, head):
        # Write your code here
        is_palindrome = True
        if head:
            if head.next:
                if head.next.next==None:
                    if head.val != head.next.val:
                        is_palindrome = False
                else:
                    mid = head
                    last = head.next
                    while last:
                        if last.next:
                            mid = mid.next
                            last = last.next.next
                        else:
                            last = last.next
                    head2 = mid.next
                    mid.next = None
                    dummy = ListNode(-1)
                    if head2:
                        while head2:
                            node = head2
                            head2 = head2.next
                            node.next = dummy.next
                            dummy.next = node
                        head2 = dummy.next
                    while head and head2:
                        if head.val == head2.val:
                            head = head.next
                            head2 = head2.next
                        else:
                            is_palindrome = False
                            break
        return is_palindrome
```

```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param head, a ListNode
    # @return a boolean
    def isPalindrome(self, head):
        # Write your code here
        if head==None or head.next==None:
            return True
        mid = head
        last = head
        while last.next and last.next.next:
            mid = mid.next
            last = last.next.next
        head2 = mid.next
        mid.next = None
        dummy = ListNode(head2.val)
        while head2.next:
            tmp = ListNode(head2.next.val)
            tmp.next = dummy
            dummy = tmp
            head2 = head2.next
        while head and dummy:
            if head.val != dummy.val:
                return False
            head = head.next
            dummy = dummy.next
        return True
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
     * @return a boolean
     */
    public boolean isPalindrome(ListNode head) {
        // Write your code here
        if (head==null || head.next==null) {
            return true;
        }
        ListNode mid = head;
        ListNode last = head;
        while (last.next!=null && last.next.next!=null) {
            mid = mid.next;
            last = last.next.next;
        }
        ListNode head2 = mid.next;
        mid.next = null;
        ListNode dummy = new ListNode(head2.val);
        while (head2.next != null) {
            ListNode tmp = new ListNode(head2.next.val);
            tmp.next = dummy;
            dummy = tmp;
            head2 = head2.next;
        }
        while (head!=null && dummy!=null) {
            if (head.val != dummy.val) {
                return false;
            }
            head = head.next;
            dummy = dummy.next;
        }
        return true;
    }
}
```
