[Problem Link](https://takeuforward.org/practice/dsa/sort-a-ll-of-0's-1's-and-2's)


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
      ListNode zeroes=null;
      ListNode ones=null;
      ListNode twos=null;
      ListNode tail0=null;
      ListNode tail1=null;
      ListNode tail2=null;
      ListNode temp=head;
      while(temp!=null){
        if(temp.data==0){
         if(zeroes==null){
          zeroes=temp;
          tail0=temp;
         }
         else{
            tail0.next=temp;
            tail0=temp;
         }
        }
        else if(temp.data==1){
            if(ones==null){
                ones=temp;
                tail1=temp;
            }
            else{
                tail1.next=temp;
                tail1=temp;
            }
        }
        else{
            if(twos==null){
                twos=temp;
                tail2=temp;
            }
            else{
                tail2.next=temp;
                tail2=temp;
            }
        }
        temp=temp.next;
      }
    if(tail0!=null){
        tail0.next=(ones!=null)?ones:twos;
    }
    if(tail1!=null){
        tail1.next=twos;
    }
    if(tail2!=null){
        tail2.next=null;
    }
    if(zeroes!=null){
        return zeroes;
    }
    if(ones!=null){
        return ones;
    }
    return twos;
    }
}
```
