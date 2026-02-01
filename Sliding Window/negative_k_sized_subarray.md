# Negative Numbers in k sized subarray

[Problem Link](https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1)

```
class Solution {
    static List<Integer> firstNegInt(int arr[], int k) {
        // write code here
        List<Integer> li=new ArrayList<>();
        Deque<Integer> dq=new ArrayDeque<>();
        for(int i=0;i<arr.length;i++){
            while(!dq.isEmpty() && dq.peekFirst()<=i-k){
                dq.pollFirst();
            }
            while(!dq.isEmpty() && arr[dq.peekLast()]>0){
                dq.pollLast();
            }
            if(arr[i]<0){
                dq.addLast(i);
            }
            if(i>=k-1){
                if(dq.peekFirst()!=null){
                    li.add(arr[dq.peekFirst()]);
                }
                else{
                    li.add(0);
                }
            }
        }
        return li;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
