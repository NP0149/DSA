[Problem Link](https://leetcode.com/problems/intersection-of-two-linked-lists/submissions/2156353385/)


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
    int find_len(ListNode head){
        ListNode temp=head;
        int count=0;
        while(temp!=null){
            count++;
            temp=temp.next;
        }
        return count;
    }

    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        int len1=find_len(headA);
        int len2=find_len(headB);
        int diff=(int)Math.abs(len1-len2);
        if(len1>len2){
            while(diff>0){
                diff--;
                headA=headA.next;
            }
        }
       else if(len2>len1){
        while(diff>0){
            diff--;
            headB=headB.next;
        }
       }
        if(headA==null || headB==null){
            return null;
        }
        while(headA!=null && headB!=null){
            if(headA==headB){
                return headA;
            }
            headA=headA.next;
            headB=headB.next;
        }
       return null;
    }
}
```
