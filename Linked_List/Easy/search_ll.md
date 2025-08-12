# Search in a Linked list

```
/* Defination of ListNoode
class ListNode {
    int val;
    ListNode next;

    ListNode(int value) {
        this.val = value;
        this.next = null;
    }
}
*/


class Solution {
    public boolean searchKey(ListNode head, int key) {
        // Your code goes here
        ListNode temp=head;
        while(temp!=null){
            if(temp.val==key){
                return true;
            }
            temp=temp.next;
        }
        return false;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(1)
