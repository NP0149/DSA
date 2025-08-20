# Deleteing key in doubly Linked list

# Approach-I

1)at first traverse through every element in the linked list and then if temp.value equals to key then just delete it

2)we need to store the temp previous and temp next in seperate nodes to access later and then when data becomes equal to the key
then just do temp.prev.next=temp.next and temp.next.prev=temp.prev

```
    static Node del_key(int key,Node head){
        Node temp=head;
        while(temp!=null){
            if(temp.data==key){
                if(temp==head){
                    head=head.next;
                }
                Node nextnode=temp.next;
                Node prevnode=temp.prev;
               if(prevnode!=null) prevnode.next=nextnode;
               if(nextnode!=null) nextnode.prev=prevnode;
            }
            temp=temp.next;
        }
        return head;
    }
```

# Complexity Analysis

Time:O(n)//traversing through the linked list

Space:O(1)
