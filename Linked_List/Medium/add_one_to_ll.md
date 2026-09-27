
[Problem Link](https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1)

```
/* Structure of linked list Node
class Node{
    int data;
    Node next;

    Node(int x){
        data = x;
        next = null;
    }
}
*/
class Solution {
   Node reverse(Node head){
            if(head==null){
               return null;
           }
           Node prev=null;
         Node curr=head;
          Node next=curr;
           if(head.next==null){
               return head;
           }
           while(next!=null){
               next=curr.next;
               curr.next=prev;
               prev=curr;
               curr=next;
           }
           return prev;
       }
       Node sum(Node head1,Node head2){
               Node dummy=new Node(-1);
               Node tail=dummy;
               int carry=0;
               while(head1!=null || head2!=null || carry!=0){
                  int sum=0;
                  if(head1!=null){
                   sum+=head1.data;
                   head1=head1.next;
                  }
                  if(head2!=null){
                   sum+=head2.data;
                   head2=head2.next;
                  }
                  sum+=carry;
                  carry=sum/10;
                  Node temp=new Node(sum%10);
                  tail.next=temp;
                  tail=temp;
               }
               return dummy.next;
           }
    public Node addOne(Node head1) {
       head1=reverse(head1);
            Node head2=new Node(1);
            head1=sum(head1,head2);
            head1=reverse(head1);
            return head1;
    }
}
```
