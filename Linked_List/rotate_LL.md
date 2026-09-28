[Problem Link](https://leetcode.com/problems/rotate-list/description/)

```
class Solution {
    int find_len(ListNode head){
        ListNode temp=head;
        int count=0;
        while(temp!=null){
            count++;
            temp=temp.next;
        }
        return count;
    }
    ListNode del_last(ListNode head){
        ListNode temp=head;
        ListNode prev=temp;
        while(temp.next!=null){
            prev=temp;
            temp=temp.next;
        }
        prev.next=null;
        return temp;
    }
    ListNode insert_front(ListNode temp,ListNode head){
        temp.next=head;
        head=temp;
        return head;
    }
    public ListNode rotateRight(ListNode head, int k) {
        if(head==null){
            return null;
        }
        int len=find_len(head);
        k=k%len;
        while(k>0){
            ListNode tobeadded=del_last(head);
            head=insert_front(tobeadded,head);
            k--;
        }
        return head;
    }
}
```
