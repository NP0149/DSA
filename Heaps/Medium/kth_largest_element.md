# kth largest element

[Problem Link](https://leetcode.com/problems/kth-largest-element-in-an-array/)

```
class Solution {
    public int findKthLargest(int[] arr, int k) {
        PriorityQueue<Integer> pq=new PriorityQueue<>(Collections.reverseOrder());
        for(int i=0;i<arr.length;i++){
            pq.add(arr[i]);
        }
        while(!pq.isEmpty() && k>1){
            pq.poll();
            k--;
        }
        return pq.poll();
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
