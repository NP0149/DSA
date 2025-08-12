# Reversing of a singly Linked List

# Approach

1)store the prev and next as null and then store the temp.next value in the next pointer and then update temp.next with prev value and move
prev to temp and temp to temp.next

```
 public static Node rev(Node head){
     Node prev=null;
     Node temp=head;
     Node next=null;
     while(temp!=null){
         next=temp.next;
         temp.next=prev;
         prev=temp;
         temp=next;
     }
     return prev;
    }
```
# complexity Analysis

Time:O(n)

Space:O(1)
