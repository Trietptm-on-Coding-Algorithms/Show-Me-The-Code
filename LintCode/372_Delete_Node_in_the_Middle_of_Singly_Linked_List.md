# 在O(1)时间复杂度删除链表节点

## 描述
给定一个单链表中的一个等待被删除的节点(非表头或表尾)。请在在O(1)时间复杂度删除该链表节点。

## 样例
Linked list is `1->2->3->4`, and given node `3`, delete the node in place `1->2->4`

## 标签
链表

## 分析

## 解答
### Python
```Python
"""
Definition of ListNode
class ListNode(object):

    def __init__(self, val, next=None):
        self.val = val
        self.next = next
"""
class Solution:
    # @param node: the node in the list should be deleted
    # @return: nothing
    def deleteNode(self, node):
        # write your code here
        if node.next:
            node.val = node.next.val
            node.next = node.next.next
        else:
            node = None
```

### Java
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
     * @param node: the node in the list should be deleted
     * @return: nothing
     */
    public void deleteNode(ListNode node) {
        // write your code here
        if (node.next != null) {
            node.val = node.next.val;
            node.next = node.next.next;
        } else {
            node = null;
        }
    }
}
```
