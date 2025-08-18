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

# Approach-II

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
    static  ListNode find_median( ListNode head){
         ListNode slow=head;
         ListNode fast=head.next;
        while(fast!=null && fast.next!=null){
            slow=slow.next;
            fast=fast.next.next;
        }
        return slow;
    }
    static  ListNode merge( ListNode left, ListNode right){
        if(left==null) return right;
        if(right==null) return left;
         ListNode result;
        if(left.val<=right.val){
            result=left;
            result.next=merge(left.next,right);
        }
        else{
            result=right;
            result.next=merge(left,right.next);
        }
        return result;
    }
    static  ListNode sort( ListNode head){
        if(head==null || head.next==null){
            return head;
        }
         ListNode middle=find_median(head);
          ListNode nextofmiddle=middle.next;
          middle.next=null;
        ListNode left=sort(head);
         ListNode right=sort(nextofmiddle);
          ListNode result=merge(left,right);
          return result;
    }
    public ListNode sortList(ListNode head) {
        ListNode result=sort(head);
        return result;
    }
}
```

# Complexities

Time:O(n log n)

Space:O(log n)
