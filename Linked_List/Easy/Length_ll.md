# length of a linked List

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
# complexities

time:O(n)

Space:O(1)
