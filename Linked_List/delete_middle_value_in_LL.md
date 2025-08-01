# delete middle value from Linked list

[Problem Link](https://leetcode.com/problems/delete-node-in-a-linked-list/submissions/1719870850/)

# Approach-I

```
class Solution {
    public void deleteNode(ListNode node) {
        node.val = node.next.val;       // Copy the next node's value
        node.next = node.next.next;     // Skip over the next node
    }
}

```
# Complexities

Time:O(1)

Space:O(1)
