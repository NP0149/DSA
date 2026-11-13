[Problem Link](https://takeuforward.org/practice/dsa/find-middle-of-linked-list)


```

/*Definition for Singly Linked List
class ListNode {
    int val;
    ListNode next;

    ListNode() {
        val = 0;
        next = null;
    }

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
    public ListNode middleOfLinkedList(ListNode head) {
   List<ListNode> li=new ArrayList<>();
   ListNode temp=head;
   while(temp!=null){
    li.add(temp);
    temp=temp.next;
   }
   int n=li.size();
   int mid=n/2;
    return li.get(mid);
    }
}

```
