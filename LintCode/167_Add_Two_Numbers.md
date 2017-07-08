# 链表求和

## 描述
你有两个用链表代表的整数，其中每个节点包含一个数字。数字存储按照在原来整数中相反的顺序，使得第一个数字位于链表的开头。写出一个函数将两个整数相加，用链表形式返回和。

## 样例
给出两个链表 `3->1->5->null` 和 `5->9->2->null`，返回 `8->0->8->null`

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
    # @param l1: the first list
    # @param l2: the second list
    # @return: the sum list of l1 and l2
    def addLists(self, l1, l2):
        # write your code here
        n1, n2 = 0, 0
        k = 0
        while l1:
            n1 += l1.val * pow(10, k)
            k += 1
            l1 = l1.next
        k = 0
        while l2:
            n2 += l2.val * pow(10, k)
            k += 1
            l2 = l2.next
        n3 = str(n1 + n2)
        tmp = ListNode(n3[0])
        if len(n3) > 1:
            for i in n3[1:]:
                node = ListNode(int(i))
                node.next = tmp
                tmp = node
        else:
            node = tmp
        return node
```

```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param l1: the first list
    # @param l2: the second list
    # @return: the sum list of l1 and l2
    def addLists(self, l1, l2):
        # write your code here
        new_head = ListNode(-1)
        cur = new_head
        n = 0
        while l1 or l2:
            if l1:
                n += l1.val
                l1 = l1.next
            if l2:
                n += l2.val
                l2 = l2.next
            cur.next = ListNode(n % 10)
            n = n / 10
            cur = cur.next
        if n == 1:
            cur.next = ListNode(1)
        return new_head.next
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
     * @param l1: the first list
     * @param l2: the second list
     * @return: the sum list of l1 and l2
     */
    public ListNode addLists(ListNode l1, ListNode l2) {
        // write your code here
        ListNode new_head = new ListNode(-1);
        ListNode cur = new_head;
        int n = 0;
        while (l1 != null || l2 != null) {
            if (l1 != null) {
                n += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                n += l2.val;
                l2 = l2.next;
            }
            cur.next = new ListNode(n % 10);
            n = n / 10;
            cur = cur.next;
        }
        if (n == 1) {
            cur.next = new ListNode(1);
        }
        return new_head.next;
    }
}
```
