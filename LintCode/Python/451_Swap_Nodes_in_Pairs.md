# 两两交换链表中的节点
## 描述
给一个链表，两两交换其中的节点，然后返回交换后的链表。

## 样例
给出 1->2->3->4, 你应该返回的链表是 2->1->4->3。

## 挑战
你的算法只能使用常数的额外空间，并且不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

## 标签
链表

## 问题
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param head, a ListNode
    # @return a ListNode
    def swapPairs(self, head):
        # Write your code here
```

## 分析

## 解答
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param head, a ListNode
    # @return a ListNode
    def swapPairs(self, head):
        # Write your code here
        new_head = ListNode(-1)
        new_head.next = head
        cur = head
        pre = new_head
        while cur and cur.next:
            pre.next = cur.next
            tmp = cur.next
            cur.next = cur.next.next
            tmp.next = cur
            pre = pre.next.next
            cur = cur.next
        return new_head.next
```
