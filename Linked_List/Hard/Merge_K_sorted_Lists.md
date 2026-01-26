# Merge k sorted Lists

[Problem Link](https://leetcode.com/problems/merge-k-sorted-lists/description/)

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
    static void find(List<Integer> li,ListNode head){
        ListNode temp=head;
        while(temp!=null){
            li.add(temp.val);
            temp=temp.next;
        }
    }
    public ListNode mergeKLists(ListNode[] lists) {
        List<Integer> li=new ArrayList<>();
     for(ListNode node:lists){
       find(li,node);
     }
     Collections.sort(li);
     if(li.size()==0){
        return null;
     }
     ListNode head=new ListNode(li.get(0),null);
     int i=1;
     ListNode temp=head;
     while(i<li.size()){
       ListNode newnode=new ListNode(li.get(i));
       temp.next=newnode;
       temp=newnode;
       i++;
     }
     return head;
    }
}
```

# Complexity Analysis

Time:O(NlogN)

Space:O(N)
