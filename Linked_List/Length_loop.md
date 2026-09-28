[Problem Link](https://takeuforward.org/practice/dsa/length-of-loop-in-ll)


```

 class Solution {
    ListNode find_loop(ListNode head){
        ListNode slow=head;
        ListNode fast=head.next;
        while(fast!=null && fast.next!=null){
            if(slow==fast){
                return slow;
            }
            slow=slow.next;
            fast=fast.next.next;
        }
        return null;
    }
     public int findLengthOfLoop(ListNode head) {
        if(head==null){
            return 0;
        }
        if(head.next==null){
          return 0;
        }
     ListNode needed=find_loop(head);
     if(needed==null){
        return 0;
     }
     ListNode slow=needed;
     ListNode fast=slow.next;
     int count=1;
     while(slow!=fast){
      count++;
      fast=fast.next;
     }
     return count;
     }
 }
```
