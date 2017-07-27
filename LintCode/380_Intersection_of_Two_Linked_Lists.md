# 两个链表的交叉

## 描述
请写一个程序，找到两个单链表最开始的交叉节点。

注意事项
 - 如果两个链表没有交叉，返回null。
 - 在返回结果后，两个链表仍须保持原有的结构。
 - 可假定整个链表结构中没有循环。


## 样例
```
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
```
在节点 c1 开始交叉。

## 挑战
需满足 O(n) 时间复杂度，且仅用 O(1) 内存。

## 标签
链表

## 分析

## 解答
### Python
超出时间限制，failed：
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param headA: the first list
    # @param headB: the second list
    # @return: a ListNode
    def getIntersectionNode(self, headA, headB):
        # Write your code here
        if headA and headB:
            h1 = headA
            while h1:
                h2 = headB
                while h2:
                    if h1 == h2:
                        return h2
                    h2 = h2.next
                h1 = h1.next
        return None
```

正确：
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param headA: the first list
    # @param headB: the second list
    # @return: a ListNode
    def getIntersectionNode(self, headA, headB):
        # Write your code here
        if headA and headB:
            h1 = headA
            h2 = headB
            while h1 and h2:
                h1 = h1.next
                h2 = h2.next
                if h2 == None:
                    headA, headB = headB, headA
                    h1, h2 = h2, h1
            h3 = headB
            h1 = headA
            while h2:
                h2 = h2.next
                h3 = h3.next
            while h1 != h3:
                h1 = h1.next
                h3 = h3.next
            return h3
        return None
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
     * @param headA: the first list
     * @param headB: the second list
     * @return: a ListNode
     */
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        // Write your code here
        if (headA != null && headB != null) {
            ListNode h1 = headA;
            ListNode h2 = headB;
            while (h1 != null && h2 != null) {
                h1 = h1.next;
                h2 = h2.next;
                if (h2 == null){
                    ListNode tmp = headA;
                    headA = headB;
                    headB = tmp;
                    tmp = h1;
                    h1 = h2;
                    h2 = tmp;
                }
            }
            ListNode h3 = headB;
            h1 = headA;
            while (h2 != null) {
                h2 = h2.next;
                h3 = h3.next;
            }
            while (h1 != h3) {
                h3 = h3.next;
                h1 = h1.next;
            }
            return h3;
        }
        return null;
    }
}
```
