# Delete median of Linked List

[Problem Link](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)

# Approach-I

1)by tortoise method we can find the middle value but keep track of the prev value of slow and then just do prev.next=prev.next.next
to delete the median value of Linked List
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        ListNode fast=head;
        ListNode slow=head;
        ListNode prev=slow;
        if(head==null || head.next==null){
            return null;
        }
        while(fast!=null && fast.next!=null){
            prev=slow;
           slow=slow.next;
            fast=fast.next.next;
        }
        prev.next=prev.next.next;
        return head;
    }
}
```

# complexity Analysis

time:O(n)

Space:O(1)
