[Problem Link](https://leetcode.com/problems/linked-list-cycle-ii/description/)


```
public class Solution {
    public ListNode detectCycle(ListNode head) {
       HashSet<ListNode> hs=new HashSet<>();
       ListNode temp=head;
       while(temp!=null){
        if(hs.contains(temp)){
            return temp;
        }
        hs.add(temp);
        temp=temp.next;
       }
      return null;
    }
}
```


```

```
