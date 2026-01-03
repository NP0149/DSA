# Flattening of Linked List

[Problem link](https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1)

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
