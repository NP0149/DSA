# Sort of a linked list containing only 0's,1's and 2's

[Problem Link](https://takeuforward.org/practice/dsa/sort-a-ll-of-0's-1's-and-2's?ai=true)

# Approach-I

1)count all 0s,1s and 2s and then modify the data of linked list

```
/* Definition of singly Linked List:
class ListNode {
    int val;
    ListNode next;

    ListNode(int data1) {
        val = data1;
        next = null;
    }

    ListNode(int data1, ListNode next1) {
        val = data1;
        next = next1;
    }
}
*/

class Solution {
    public ListNode sortList(ListNode head) {
        ListNode temp=head;
        int count0=0;
        int count1=0;
        int count2=0;
        while(temp!=null){
            if(temp.val==0){
                count0++;
            }
            else if(temp.val==1){
                count1++;
            }
            else{
                count2++;
            }
            temp=temp.next;
        }
        ListNode t=head;
        while(t!=null){
            if(count0>0){
                t.val=0;
                count0--;
            }
            else if(count1>0){
                t.val=1;
                count1--;
            }
            else{
                t.val=2;
                count2--;
            }
            t=t.next;
        }
        return head;
    }
}

```
# Complexity Analysis

Time:O(n)

Space:O(1)

# Optimal

```
/*
Definition of singly linked list:
class ListNode{
    public int data;
    public ListNode next;
    ListNode() { data = 0; next = null; }
    ListNode(int x) { data = x; next = null; }
    ListNode(int x, ListNode next) { data = x; this.next = next; }
}
*/

class Solution {
    public ListNode sortList(ListNode head) {
       if(head==null){
        return null;
       }
        ListNode zerohead=null;
         ListNode zero=null;
     ListNode onehead=null;
         ListNode  one=null;
        ListNode twohead=null;
        ListNode two=null;
        ListNode  temp=head;
        while(temp!=null){
            ListNode next=temp.next;
            int num=temp.data;
            if(num==0){
                if(zerohead==null){
                    zerohead=temp;
                    zero=zerohead;
                }
                else{
                    zero.next=temp;
                    zero=zero.next;
                }
            }
            else if(num==1){
                if(onehead==null){
                    onehead=temp;
                    one=onehead;
                }
                else{
                    one.next=temp;
                    one=one.next;
                }
            }
            else {
                if (twohead == null) {
                    twohead = temp;
                    two = twohead;
                } else {
                    two.next = temp;
                    two = two.next;
                }
            }
            temp=next;
        }
        if(zero!=null) {
            if(onehead!=null){
                zero.next=onehead;
            }
            else{
              if(twohead!=null){
                zero.next=twohead;
              }
            }
        }
        if(one!=null) {
            one.next = twohead;
        }
        if(two!=null) {
            two.next = null;
        }
       if(zerohead!=null){
           return zerohead;
       }
       else if(onehead!=null){
           return onehead;
       }
       return twohead;
    }
}
```
