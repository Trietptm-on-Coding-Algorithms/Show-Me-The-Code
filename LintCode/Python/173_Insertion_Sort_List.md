# 链表插入排序
## 描述
用插入排序对链表排序

## 样例
Given `1->3->2->0->null`, return `0->1->2->3->null`

## 挑战
你的算法只能使用常数的额外空间，并且不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

## 标签
链表

## 问题
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
    @return: The head of linked list.
    """
    def insertionSortList(self, head):
        # write your code here
```

## 分析
## 解答
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
    @return: The head of linked list.
    """
    def insertionSortList(self, head):
        # write your code here
        new_head = ListNode(-1)
        while head:
            pre = new_head
            tmp = head.next
            while pre.next and head.val > pre.next.val:
                pre = pre.next
            head.next = pre.next
            pre.next = head
            head = tmp
        return new_head.next
```
