# All Operations of Singly linked list

# Insertion

```
import java.util.*;
public class ll_insert {
    static class Node{
        int data;
        Node next;
        Node(int data,Node next){
            this.data=data;
            this.next=next;
        }
        Node(int data){
            this.data=data;
            next=null;
        }
    }
    public static Node createll(int []arr){
        Node head=new Node(arr[0]);
        Node temp=head;
        for(int i=1;i<arr.length;i++){
            Node t=new Node(arr[i]);
            temp.next=t;
            temp=temp.next;
        }
         return head;
    }
    public static Node insert(int data,int pos,Node head){
        Node temp=head;
        int count=0;
        Node n=new Node(data,null);
        Node prev=temp;
        while(count<pos-1) {
            prev=temp;
            temp = temp.next;
            count++;
        }
      prev.next=n;
        n.next=temp;
        return head;
    }
    public static Node insertbefore(Node head,int data){
        Node temp=head;
        Node n=new Node(data);
        n.next=head;
        head=n;
        return head;
    }
    public static Node insertLast(Node head,int data){
        Node temp=head;
        Node last=new Node(data);
        while(temp.next!=null){
            temp=temp.next;
        }
        temp.next=last;
        return head;
    }
    public static void print(Node head){
        Node temp=head;
        while(temp!=null){
            System.out.println(temp.data);
            temp=temp.next;
        }
    }

    public static void main(String[] args) {
        int arr[]={1,2,3,4};
         Node head=createll(arr);
//         Node temp=head;
//       while(temp!=null){
//           System.out.println(temp.data);
//          temp=temp.next;
//       }
        System.out.println("after insertion");
        head=insert(6,3,head);
//        Node temp=head;
//        while(temp!=null){
//            System.out.println(temp.data);
//            temp=temp.next;
//        }
        System.out.println("head insertion");
        head=insertbefore(head,3);
       print(head);
        System.out.println("tail insertion");
        head=insertLast(head,5);
        print(head);
     }
}

```

# All operations related to delete

```
import java.util.*;
public class ll_delete {
    static class Node{
        int data;
        Node next;
        Node(int data,Node next){
            this.data=data;
            this.next=next;
        }
        Node(int data){
            this.data=data;
            next=null;
        }
    }
    public static Node createll(int arr[]){
        Node head=new Node(arr[0]);
        Node temp=head;
        for(int i=1;i<arr.length;i++){
            Node t=new Node(arr[i]);
            temp.next=t;
            temp=t;
        }
        return head;
    }
    public static void print(Node head){
        Node temp=head;
        while(temp.next!=null){
            System.out.println(temp.data);
          temp=temp.next;
        }
        System.out.println(temp.data);
    }
static Node del_first(Node head){
        Node temp=head;
        head=head.next;
        return head;
}
public static Node del_end(Node head){
        Node temp=head;
        Node prev=temp;
        while(temp.next!=null){
            prev=temp;
            temp=temp.next;
        }
       prev.next=null;
        return head;
}
public static Node del_bet(Node head,int pos){
        Node temp=head;
        int count=0;
        Node prev=temp;
        while(count<pos-1){
            prev=temp;
            temp=temp.next;
            count++;
        }
    prev.next=temp.next;
        return head;
}
    public static void main(String[] args) {
        int arr[]={1,2,3,4,5};
        Node head=createll(arr);
        print(head);
        System.out.println("after deletion");
        head=del_first(head);
        print(head);
        System.out.println("after deleteion at end");
        head=del_end(head);
        print(head);
        System.out.println("deleting in middle by passing a position");
        head=del_bet(head,2);
        print(head);
    }
}
```
