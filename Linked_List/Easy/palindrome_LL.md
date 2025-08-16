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
