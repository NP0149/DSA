# Sorting a linked list

[Problem Link](https://leetcode.com/problems/sort-list/description/)

# Approach-I

1)add all elements in the linked list to a array list then sort the linked list and again rewrite the data of the linked list

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode sortList(ListNode head) {
        ListNode temp=head;
        ArrayList<Integer> li=new ArrayList<>();
        while(temp!=null){
            li.add(temp.val);
            temp=temp.next;
        }
        Collections.sort(li);
        int i=0;
        ListNode t=head;
        while(t!=null && i<li.size()){
            t.val=li.get(i);
            t=t.next;
            i++;
        }
        return head;
    }
}
```

# Complexity Analysis

Time:O(nlogn)

Space:O(n)//due to the usage of arraylist
