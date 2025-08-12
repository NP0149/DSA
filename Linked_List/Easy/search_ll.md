# Search in a Linked list

```
class Solution {
    public int getLength(ListNode head) {
        // Your code goes here
        ListNode temp=head;
        int count=0;
        while(temp!=null){
            count++;
            temp=temp.next;
        }
        return count;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(1)
