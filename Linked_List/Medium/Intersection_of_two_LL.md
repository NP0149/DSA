# Intersection of two Linked list

# Approach-I

1)add the first linked list into the map and then traverse second linked list by comparing the values in the 
first linked list,if the value is already there in the map just return that particular node 

```
  static Node find_common(Node head1,Node head2){
       Map<Node,Integer> hm=new HashMap<>();
       Node temp1=head1;
       while(temp1!=null){
           hm.put(temp1,1);
           temp1=temp1.next;
       }
       Node temp2=head2;
       while(temp2!=null){
           if(hm.containsKey(temp2)){
               return temp2;
           }
           temp2=temp2.next;
       }
       return null;
    }
```

# Complexity Analysis

time:O(n1+n2)//because we are traversing two lists

Space:O(n1)//for storing first linked list into map

# Approach-II

1)move temp1 and temp2 simultaneously and then when temp1 reaches end make it point to head2 and when temp2 reaches null make it point to head1,continue the process untill temp1 equals to temp2 and if there are no matching even then they will both become equal at temp1=null and temp2 also equal to null

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode temp1=headA;
         ListNode temp2=headB;
         while(temp1!=temp2){
            if(temp1==null || temp2==null){
                return temp1;
            }
              temp1=temp1.next;
            temp2=temp2.next;
            if(temp1==temp2)
            return temp1;
            if(temp1==null){
                temp1=headB;
            }
            if(temp2==null){
                temp2=headA;
            }
        
         }
      return temp1;
    }
}
```

# Complexity Analysis

Time:O(lenA+lenB)

Space:O(1)
