# Seggregating odd and even indexed values in a linked list

[Problem Link](https://leetcode.com/problems/odd-even-linked-list/submissions/1738531383/)

# Approach-I(Brute)

1)Consider a list and then jump two steps every time and then add into the list 

2)later just modify the values of linked list

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
    public ListNode oddEvenList(ListNode head) {
       ArrayList<Integer> li=new ArrayList<>();
       ListNode temp=head;
       if(head==null || head.next==null){
        return head;
       }
       while(temp!=null && temp.next!=null){
        li.add(temp.val);
        temp=temp.next.next;
       }
       if(temp!=null){
        li.add(temp.val);
       }
       ListNode t=head.next;
       while(t!=null && t.next!=null){
        li.add(t.val);
        t=t.next.next;
       }
       if(t!=null){
        li.add(t.val);
       }
       ListNode r=head;
       int i=0;
       while(i<li.size()){
        r.val=li.get(i);
        i++;
        r=r.next;
       }
       return head;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)//using arraylist to store values

# Approach-II(optimal)

1)make the odd and even nodes jump by two nodes at last odd.next=evenhead


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
    public ListNode oddEvenList(ListNode head) {
        if(head==null || head.next==null){
            return head;
        }
        ListNode odd=head;
        ListNode even=head.next;
        ListNode evenhead=even;
        while(even!=null && even.next!=null){
            odd.next=odd.next.next;
            even.next=even.next.next;
            odd=odd.next;
            even=even.next;
        }
        odd.next=evenhead;
        return head;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
