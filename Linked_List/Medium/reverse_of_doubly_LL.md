# Reverse of a Doubly Linked List

```
import java.util.*;
public class rev_dll {
    static class Node{
        Node prev;
       int data;
       Node next;
       Node(Node prev,int data,Node next){
           this.prev=prev;
           this.data=data;
           this.next=next;
       }
    }
    static Node create_dll(int arr[]){
      Node head=new Node(null,arr[0],null);
        Node prev=head;
        for(int i=1;i<arr.length;i++){
            Node t=new Node(prev,arr[i],null);
            prev.next=t;
            prev=t;
        }
        return head;
    }
    static void print(Node head){
        Node temp=head;
        while(temp!=null){
            System.out.println(temp.data);
            temp=temp.next;
        }
        return;
    }
    static Node rev(Node head){
        Node temp=head;
        Node last=null;
        while(temp!=null){
            last=temp.prev;
            temp.prev=temp.next;
            temp.next=last;
            temp=temp.prev;
        }
       if(last!=null){
          head=last.prev;
       }
       return head;
    }
    public static void main(String[] args) {
        int arr[]={1,2,3,4};
        Node head=create_dll(arr);
        print(head);
        System.out.println("after reversing dll");
        head=rev(head);
        print(head);
    }
}
```
