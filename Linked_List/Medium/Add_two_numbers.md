# Add two numbers

[Problem Link](https://leetcode.com/problems/add-two-numbers/submissions/1734397705/)

# Approach-I

1)we need to consider temporary node containing 0 and then traverse using that particualr node and then sum =x+y+carry

2)sum=sum%10;

3)carry=sum/10;

4)then just move to the next nodes of two linked list

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
     ListNode t=new ListNode(0);
        ListNode temp=t;
        int carry=0;
        while(carry!=0 || l1!=null || l2!=null){
            int x=(l1!=null)?l1.val:0;
            int y=(l2!=null)?l2.val:0;
            int sum=x+y+carry;
            ListNode newNode=new ListNode(sum%10);
            temp.next=newNode;
            temp=temp.next;
            carry=sum/10;
            if(l1!=null){
                l1=l1.next;
            }
            if(l2!=null){
                l2=l2.next;
            }
        }
        return t.next;
    }
}
```

# Complexity Analysis

Time:O(1)

Space:O(max(n,m))//n is the length of first linked list and m is the length of second linked list

