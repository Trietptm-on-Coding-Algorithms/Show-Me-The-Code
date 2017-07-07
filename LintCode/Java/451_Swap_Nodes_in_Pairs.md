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
     * @return a ListNode
     */
    public ListNode swapPairs(ListNode head) {
        // Write your code here
    }
}
```

## 分析

## 解答
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
     * @return a ListNode
     */
    public ListNode swapPairs(ListNode head) {
        // Write your code here
        ListNode new_head = new ListNode(-1);
        new_head.next = head;
        ListNode pre = new_head;
        ListNode cur = head;
        while (cur != null && cur.next != null) {
            pre.next = cur.next;
            ListNode tmp = cur.next;
            cur.next = cur.next.next;
            tmp.next = cur;
            pre = pre.next.next;
            cur = cur.next;
        }
        return new_head.next;
    }
}
```
