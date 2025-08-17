# Sort of a linked list containing only 0's,1's and 2's

# Approach-I

1)count all 0s,1s and 2s and then modify the data of linked list

```
/* Definition of singly Linked List:
class ListNode {
    int val;
    ListNode next;

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
    public ListNode sortList(ListNode head) {
        ListNode temp=head;
        int count0=0;
        int count1=0;
        int count2=0;
        while(temp!=null){
            if(temp.val==0){
                count0++;
            }
            else if(temp.val==1){
                count1++;
            }
            else{
                count2++;
            }
            temp=temp.next;
        }
        ListNode t=head;
        while(t!=null){
            if(count0>0){
                t.val=0;
                count0--;
            }
            else if(count1>0){
                t.val=1;
                count1--;
            }
            else{
                t.val=2;
                count2--;
            }
            t=t.next;
        }
        return head;
    }
}

```
# Complexity Analysis

Time:O(n)

Space:O(1)
