# Linked List Cycle

[Problem Link](https://leetcode.com/problems/linked-list-cycle/submissions/1737949513/)

# Approach-I

1)every time check adjacent nodes by slow and fast method

```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow=head;
        ListNode fast=head;
        while(fast!=null && fast.next!=null){
            slow=slow.next;
            fast=fast.next.next;
            if(slow==fast){
                return true;
            }
        }
    return false;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
