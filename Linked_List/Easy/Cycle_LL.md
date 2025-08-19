# Linked List Cycle

[Problem Link](https://leetcode.com/problems/linked-list-cycle/submissions/1737949513/)


# Approach-I(Brute)

1)Create a Map and then put these nodes in it if we have encountered any node that already visited ,then just return true;

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
     ListNode temp1=head;
     if(head==null ||head.next==null){
        return false;
     }
     Map< ListNode ,Integer> hm=new HashMap<>();
     while(temp1!=null){
        if(!hm.containsKey(temp1)){
            hm.put(temp1,1);
        }
        else{
            return true;
        }
        temp1=temp1.next;
     }
     return false;
    }
}
```

# Complexity Analysis

Time:O(N)

Space:O(n)//using map

# Approach-II

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
