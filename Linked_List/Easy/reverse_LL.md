# Reverse of a Linked List

[Problem Link](https://leetcode.com/problems/reverse-linked-list/description/)

# Approach-I

1)here we are using iterative method

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
    public ListNode reverseList(ListNode head) {
        ListNode temp=head;
        ListNode prev=null;
        ListNode next=null;
        while(temp!=null){
          next=temp.next;
          temp.next=prev;
          prev=temp;
          temp=next;
        }
        return prev;
    }
}
```

# Complexities

Time:O(n)

Space:O(1)


# Approach-II

1)here we are using recurrsive method


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
    public ListNode reverseList(ListNode head) {
        if(head==null || head.next==null){
            return head;
        }
        ListNode newNode =reverseList(head.next);
       ListNode front=head.next;
       front.next=head;
       head.next=null;
       return newNode;
    }
}
```

# Complexity Analysis

time:O(n)

Space:O(n)//because we are using stack for recurrsion
