# 删除链表中的元素

## 描述：
删除链表中等于给定值val的所有节点。

## 样例：
给出链表 `1->2->3->3->4->5->3`, 和 `val = 3`, 你需要返回删除3之后的链表：`1->2->4->5`。

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
    # @param val, an integer
    # @return a ListNode
    def removeElements(self, head, val):
        # Write your code
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
    # @param val, an integer
    # @return a ListNode
    def removeElements(self, head, val):
        # Write your code
        new_head = ListNode(-1)
        new_head.next = head
        cur = head
        pre = new_head
        while cur:
            if cur.val == val:
                pre.next = cur.next
            else:
                pre = pre.next
            cur = cur.next
        return new_head.next
```