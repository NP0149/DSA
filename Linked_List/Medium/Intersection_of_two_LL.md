# Intersection of two Linked list

# Approach-I

1)add the first linked list into the map and then traverse second linked list by comparing the values in the 
first linked list,if the value is already there in the map just return that particular node 

```
  static Node find_common(Node head1,Node head2){
       Map<Node,Integer> hm=new HashMap<>();
       Node temp1=head1;
       while(temp1!=null){
           hm.put(temp1,1);
           temp1=temp1.next;
       }
       Node temp2=head2;
       while(temp2!=null){
           if(hm.containsKey(temp2)){
               return temp2;
           }
           temp2=temp2.next;
       }
       return null;
    }
```

# Complexity Analysis

time:O(n1+n2)//because we are traversing two lists

Space:O(n1)//for storing first linked list into map
