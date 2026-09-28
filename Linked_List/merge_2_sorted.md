[Problem Link](https://leetcode.com/problems/merge-two-sorted-lists/submissions/2156412493/)


```
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy=new ListNode(-1);
        ListNode tail=dummy;
        while(list1!=null && list2!=null){
            if(list1.val<=list2.val){
                ListNode newnode=new ListNode(list1.val);
                tail.next=newnode;
                tail=newnode;
                list1=list1.next;
            }
            else{
               ListNode newnode=new ListNode(list2.val);
                tail.next=newnode;
                tail=newnode;
                list2=list2.next;
            }
        }
        while(list1!=null){
          ListNode newnode=new ListNode(list1.val);
                tail.next=newnode;
                tail=newnode;
                 list1=list1.next;
        }
    while(list2!=null){
          ListNode newnode=new ListNode(list2.val);
                tail.next=newnode;
                tail=newnode;
                list2=list2.next;
    }
        return dummy.next;
    }
}
```
