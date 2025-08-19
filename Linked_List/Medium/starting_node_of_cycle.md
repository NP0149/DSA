# Starting node of the cycle in a linked list

[Problem Link](https://leetcode.com/problems/linked-list-cycle-ii/)

# Approach-I

1)tortoise and hare method ,but one logic change that is when slow==fast then we need to place slow at head and then move slow and fast by one step
then you will get the starting node

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
    public ListNode detectCycle(ListNode head) {
        ListNode slow=head;
        ListNode fast=head;
        ListNode prev=fast;
        int count=0;
        while(fast!=null && fast.next!=null){
            slow=slow.next;
            fast=fast.next.next;
            if(slow==fast){
                slow=head;
                while(slow!=fast){
                    slow=slow.next;
                    fast=fast.next;
                }
                return slow;
            }
        }
        return null;
    }
}
```

# Complexity Analysis

time:O(n)

Space:O(1)
