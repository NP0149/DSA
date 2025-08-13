# Doubly Linked List

## Insertion

```
import java.util.*;
public class dll_insert {
    static class Node{
        Node prev;
        int data;
        Node next;
        Node(Node prev,int data,Node next){
            this.prev=prev;
            this.data=data;
            this.next=next;

        }
        Node(int data){
            this.data=data;
            this.prev=null;
            this.next=null;
        }

    }

    static Node create_dll(int arr[]){
        Node head=new Node(arr[0]);
        Node temp=head;
        for(int i=1;i<arr.length;i++){
            Node t=new Node(temp,arr[i],null);
            temp.next=t;
            temp=t;
        }
        return head;
    }
    static void print(Node head){
        Node temp=head;
        while(temp!=null){
            System.out.println(temp.data);
            temp=temp.next;
        }
    }
  public static Node insert_front(Node head,int data){
        Node temp=head;
        Node n=new Node(data);
        n.next=head;
        head=n;
        return head;

  }
  public static Node insert_last(Node head,int data){
        Node temp=head;
        Node n=new Node(data);
        while(temp.next!=null){
            temp=temp.next;
        }
        temp.next=n;
        return head;
  }
 public static Node insert_mid(Node head,int data,int pos){
     Node temp = head;
     int count = 1;

     // Traverse until the node at position pos
     while (count < pos && temp != null) {
         temp = temp.next;
         count++;
     }

     Node n = new Node(data);

     // If inserting at the head
     if (temp != null && temp.prev == null) {
         n.next = temp;
         temp.prev = n;
         head = n;
     }
     else {
         n.prev = temp.prev;
         n.next = temp;
         temp.prev.next = n;
         temp.prev = n;
     }

     return head;
 }


    public static void main(String[] args) {
        int arr[]={1,2,3,4};
        Node head=create_dll(arr);
        print(head);
        System.out.println("after inserting in front");
        head=insert_front(head,0);
        print(head);
        System.out.println("after inserting at last");
        head=insert_last(head,9);
        print(head);
        System.out.println("after inserting at particualr position of linked list");
        head=insert_mid(head,0,3);
        print(head);
    }
}
```

## Deletion

```
import java.util.*;
public class dll_delete {
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
 static Node del(Node head){
        Node temp=head.next;
        head.next=null;
        head=temp;
        return head;
 }
 static Node del_back(Node head){
        Node temp=head;
        while(temp.next!=null){
            temp=temp.next;
        }
    if(temp.prev==null){
        head=null;
    }
    else{
        temp.prev.next=null;
    }
        return head;
 }
static Node del_inbet(Node head,int data){
        Node temp=head;
        while(temp.data!=data){
            temp=temp.next;
        }
        if(temp.next==null){
            temp.prev.next=null;
        }
        else {
            temp.data = temp.next.data;
            temp.next = temp.next.next;
        }
        return head;
}
    public static void main(String[] args) {
        int arr[]={1,2,3,4};
        System.out.println("the creation of doubly linked list");
        Node head=create_dll(arr);
        print(head);
        System.out.println("delete head");
        head=del(head);
        print(head);
        System.out.println("delete at back");
        head=del_back(head);
        print(head);
        System.out.println("delete in between ");
        head=del_inbet(head,2);
        print(head);
    }
}
```
