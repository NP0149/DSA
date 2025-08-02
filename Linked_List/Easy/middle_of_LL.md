# Middle value of the Linked List

[Problem Link](https://leetcode.com/problems/middle-of-the-linked-list/description/)

# Approach-I

1)iterate through all the nodes of LL and then find the count,perform count/2,so will get middle value find that particular node and then

point head to that particular node ,so previous nodes will be erased

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
    public ListNode middleNode(ListNode head) {
        ListNode temp=head;
        int count=0;
        while(temp.next!=null){
            count++;
            temp=temp.next;
        }
        count++;
        int g=count/2;
        int i=0;
        ListNode n=head;
        ListNode prev=n;
        while(i<=g){
            prev=n;
            n=n.next;
            i++;
        }
        head=prev;
        return head;
    }
}
```
# Complexities

Time:O(n)

Space:O(1)
