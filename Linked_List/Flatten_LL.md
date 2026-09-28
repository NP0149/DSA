# Flattening of Linked List

[Problem link](https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1)


## consider every list first node as head traverse to the end and add the integer values into the list and then sort tehn create new linked list and return

```
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        List<Integer> li=new ArrayList<>();
        for(ListNode head:lists){
            ListNode temp=head;
            while(temp!=null){
                li.add(temp.val);
                temp=temp.next;
            }
        }
        Collections.sort(li);
        if(li.size()==0){
            return null;
        }
        ListNode head=new ListNode(li.get(0));
        ListNode tail=head;
        for(int i=1;i<li.size();i++){
            ListNode newnode=new ListNode(li.get(i));
            if(head.next==null){
                head.next=newnode;
                tail.next=newnode;
                tail=newnode;
            }
            else{
                tail.next=newnode;
                tail=newnode;
            }
        }
        return head;
    }
}
```


# Approach-I

```
/*
class Node {
    int data;
    Node next;
    Node bottom;

    Node(int x) {
        data = x;
        next = null;
        bottom = null;
    }
}
*/
class Solution {
    public Node flatten(Node root) {
        List<Integer> li=new ArrayList<>();
        Node temp=root;
        while(temp!=null){
          Node down=temp;
            while(down!=null){
               li.add(down.data);
                down=down.bottom;
            }
            temp=temp.next;
        }
        Collections.sort(li);
       Node head=new Node(li.get(0));
      Node temp1=head;
      int i=1;
      while(i<li.size()){
          Node newone=new Node(li.get(i));
          temp1.bottom=newone;
          temp1=newone;
          i++;
      }
      return head;
    }
}
```
