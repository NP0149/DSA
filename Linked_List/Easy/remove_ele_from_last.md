# Remove element from the last

[Problem Link](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

# Approach-I

1) at first we need to create a dummy node ,which points to head
   
2)we need to consider two pointers first and second,and intially both should point to dummy 

3)we need to traverse n+1 times with first node 

4)after that unill first node reaches null,we need to move second pointer

5)second.next=second.next.next

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode temp=head;
        ListNode dummy=new ListNode(0);
        dummy.next=head;
        ListNode first=dummy;
        ListNode second=dummy;
        for(int i=0;i<=n;i++){
            first=first.next;
        }
        while(first!=null){
            first=first.next;
            second=second.next;
        }
        second.next=second.next.next;
        return dummy.next;
    }
}
```

# Complexity Analysis

Time:O(L)//length of the linked list

Space:O(1)
