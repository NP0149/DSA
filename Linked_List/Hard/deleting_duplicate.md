# Need to delete duplicates but one should be there among duplicate nodes

# Approach-I

```
public static Node del_repeate(Node head) {
           Node actualhead=null,actualtail=null;
           Node temp=head;
           while(temp!=null) {
              if(actualhead==null){
                  actualhead=temp;
                  actualtail=temp;
              }
             else if(actualtail.data!=temp.data){
                  actualtail.next=temp;
                  actualtail=temp;
              }
               temp = temp.next;
           }
           if(actualtail!=null){
               actualtail.next=null;
           }
           return actualhead;
        }

```

# Complexity Analysis

time:O(n)

Space:O(1)
