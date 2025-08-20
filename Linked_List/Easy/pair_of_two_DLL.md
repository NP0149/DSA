# Pair of two linked list equal to the target

# Approach-I(Brute)

1) traverse through the linked list like matrix and when you find the target getting equal then just print them,through arraylis

```
     static ArrayList<List<Integer>> find_pairs_brute(Node head,ArrayList<List<Integer>>al,int target){
        Node temp1=head;
        Node temp2=head;
        while(temp1!=null){
            temp2=temp1.next;
            while(temp2!=null){
                if(temp1.data+temp2.data==target){
                    List<Integer> li=new ArrayList<>();
                    li.add(temp1.data);
                    li.add(temp2.data);
                    al.add(li);
                }
                temp2=temp2.next;
            }
            temp1=temp1.next;
        }
        return al;
    }
   ```

# Complexity Analysis

Time:O(n^2)//traversing through two loops

Space:O(1)//no extra space is used

# Approach-II(Better)

1)keep two pointers one at head position and other at tail position 

2)as the linked list given is sorted then we can take is as advantage and can solve it,if sum value greater than the target,then
move the end pointer backwards and when the sum becomes less than target then move front node to next in this way we can solve the problem

```
 static ArrayList<List<Integer>> find_pairs(Node head,ArrayList<List<Integer>>al,int target){
        Node temp=head;
        while(temp.next!=null){
            temp=temp.next;
        }
        Node tail=temp;
        temp=head;
        System.out.println("the tail data ="+tail.data);
        System.out.println("the temp data ="+temp.data);
        int sum=target;
        while(temp.data<tail.data){
            if(temp.data+tail.data==sum){
                List<Integer> li=new ArrayList<>();
                li.add(temp.data);
                li.add(tail.data);
                al.add(li);
                temp=temp.next;
                tail=tail.prev;
            }
            else if(temp.data+tail.data>sum){
                tail=tail.prev;
            }
            else{
                temp=temp.next;
            }
        }
        return al;
    }
```

# Complexity Analysis

Time:O(n)

Space:O(1)


   
