## same as reversal of singly linked list but u need to take a node prev for head

```
import java.util.*;

public class rev_dll {
    static class Node{
        Node prev;
        Node next;
        int data;
        Node(int data){
            this.data=data;
        }
    }
    static void display(Node head){
        Node temp=head;
        while(temp!=null){
            System.out.print(temp.data+" ");
            temp=temp.next;
        }
    }
    static Node reverse(Node head){
        Node next=head;
        Node curr=head;
        Node prev=null;
        while(next!=null){
            prev=curr;
            next=curr.next;
            curr.next=curr.prev;
            curr.prev=next;
            curr=next;
        }
        return prev;
    }
    public static void main(String args[]){
        int arr[]={1,2,3,4,5};
        Node head=new Node(arr[0]);
        Node tail=head;
        for(int i=1;i<arr.length;i++){
            Node newnode=new Node(arr[i]);
            if(head.next==null){
                head.next=newnode;
                newnode.prev=head;
                tail.next=newnode;
                tail=newnode;
            }
            else{
                newnode.prev=tail;
                tail.next=newnode;
                tail=newnode;
            }
        }
        display(head);
        System.out.println("after rev");
        head=reverse(head);
        display(head);
    }
}
```
