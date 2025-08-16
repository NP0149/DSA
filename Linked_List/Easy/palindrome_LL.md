# Palindrome linked list

[Problem Link](https://leetcode.com/problems/palindrome-linked-list/description/)

# Approach-I

1)traverse through the linked list and store in arraylist

2)consider two pointers from start and from end and if the value of i and j return 0 and return 1

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
    public static int check(ArrayList<Integer> arr){
        int i=0;
        int j=arr.size()-1;
        while(i<j){
            if(arr.get(i)!=arr.get(j)){
                return 0;
            }
            i++;
            j--;
        }
        return 1;
    }
    public boolean isPalindrome(ListNode head) {
        ArrayList<Integer> arr=new ArrayList<>();
        ListNode temp=head;
        while(temp!=null){
            arr.add(temp.val);
            temp=temp.next;
        }
       int m=check(arr);
       if(m==0){
        return false;
       }
       else{
        return true;
       }
    }
}
```

# Complexities

Time:O(n)

Space:O(n)

# Approach-II

1)find the median of ll

2)by using fast and slow method

3)if fast not equals to null then it may be odd so move slow to the next node

4)reverse from slow to end,that is second half of linked list

5)compare the one half with other in linked list

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
    static ListNode rev(ListNode head){
        ListNode temp=head;
        ListNode prev=null;
        ListNode next=null;
        while(temp!=null){
            next=temp.next;
            temp.next=prev;
            prev=temp;
            temp=next;
        }
        return prev;
    }
    public boolean isPalindrome(ListNode head) {
        if(head==null || head.next==null){
            return true;
        }
        ListNode temp=head;
        ListNode slow=head;
        ListNode fast=head;
        while(fast!=null && fast.next!=null){
            slow=slow.next;
            fast=fast.next.next;
        }
        if(fast!=null){
            slow=slow.next;
        }
        ListNode second=rev(slow);
        while(temp.next!=slow){
            temp=temp.next;
        }
        temp.next=second;
        ListNode t=head;
        while(t!=null && second!=null){
            if(t.val!=second.val){
                return false;
            }
            t=t.next;
           second=second.next;
        }
        return true;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
