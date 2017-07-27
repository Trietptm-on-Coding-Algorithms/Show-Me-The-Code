# 复制带随机指针的链表

## 描述
给出一个链表，每个节点包含一个额外增加的随机指针可以指向链表中的任何节点或空的节点。

返回一个深拷贝的链表。

## 样例

## 挑战
可否使用O(1)的空间

## 标签
链表

## 分析

## 解答
### Python
```Python
# Definition for singly-linked list with a random pointer.
# class RandomListNode:
#     def __init__(self, x):
#         self.label = x
#         self.next = None
#         self.random = None
class Solution:
    # @param head: A RandomListNode
    # @return: A RandomListNode
    def copyRandomList(self, head):
        # write your code here
        cur = head
        while cur:
            n = RandomListNode(cur.label)
            n.next = cur.next
            n.random = cur.random
            cur.next = n
            cur = n.next
        cur = head
        new_head = cur.next
        tmp = cur.next
        while tmp.next:
            if tmp.random:
                tmp.random = tmp.random.next
            tmp = tmp.next.next
        cur = head
        tmp = new_head
        while cur:
            cur.next = tmp.next
            cur = cur.next
            if cur:
                tmp.next = cur.next
                tmp = tmp.next
        return new_head
```

### Java
```Java
/**
 * Definition for singly-linked list with a random pointer.
 * class RandomListNode {
 *     int label;
 *     RandomListNode next, random;
 *     RandomListNode(int x) { this.label = x; }
 * };
 */
public class Solution {
    /**
     * @param head: The head of linked list with a random pointer.
     * @return: A new head of a deep copy of the list.
     */
    public RandomListNode copyRandomList(RandomListNode head) {
        // write your code here
        RandomListNode cur = head;
        while (cur != null) {
            RandomListNode n = new RandomListNode(cur.label);
            n.next = cur.next;
            n.random = cur.random;
            cur.next = n;
            cur = n.next;
        }
        cur = head;
        RandomListNode new_head = cur.next;
        RandomListNode tmp = new_head;
        while (tmp.next != null) {
            if (tmp.random != null) {
                tmp.random = tmp.random.next;
            }
            tmp = tmp.next;
        }
        cur = head;
        tmp = new_head;
        while (cur != null) {
            cur.next = tmp.next;
            cur = cur.next;
            if (cur != null) {
                tmp.next = cur.next;
                tmp = tmp.next;
            }
        }
        return new_head;
    }
}
```
