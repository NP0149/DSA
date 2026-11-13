[Problem Link](https://takeuforward.org/practice/dsa/delete-the-middle-node-in-ll)

```
/*Definition of singly linked list:
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
    int find_len(ListNode head){
        ListNode temp=head;
        int count=0;
        while(temp!=null){
            count++;
            temp=temp.next;
        }
        return count;
    }
    public ListNode deleteMiddle(ListNode head) {
        if(head==null || head.next==null){
            return null;
        }
    int len=find_len(head);
    int mid=len/2;
    ListNode temp=head;
    int i=0;
    while(i<mid-1){
        temp=temp.next;
        i++;
    }
    temp.next=temp.next.next;
    return head;
    }
}
```
