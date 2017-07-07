# 删除链表中倒数第n个节点

## 描述
给定一个链表，删除链表中倒数第n个节点，返回链表的头节点。

## 样例
给出链表1->2->3->4->5->null和 n = 2.

删除倒数第二个节点之后，这个链表将变成1->2->3->5->null.

## 挑战
O(n)时间复杂度

## 标签
链表

## 问题
```C++
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
     * @param n: An integer.
     * @return: The head of linked list.
     */
    ListNode removeNthFromEnd(ListNode head, int n) {
        // write your code here
    }
}
```

## 分析

## 解答
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
     * @param n: An integer.
     * @return: The head of linked list.
     */
    ListNode removeNthFromEnd(ListNode head, int n) {
        // write your code here
        ListNode new_head = new ListNode(-1);
        new_head.next = head;
        ListNode pre = new_head;
        ListNode cur = head;
        ListNode tmp = head;
        for (int i=0; i<n; i++) {
            tmp = tmp.next;
        }
        while (tmp != null) {
            tmp = tmp.next;
            pre = pre.next;
            cur = cur.next;
        }
        pre.next = cur.next;
        return new_head.next;
    }
}
```
