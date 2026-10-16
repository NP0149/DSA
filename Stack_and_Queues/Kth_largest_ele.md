[Problem Link](https://leetcode.com/problems/kth-largest-element-in-an-array/submissions/2173695928/?envType=study-plan-v2&envId=top-interview-150)


```
class Solution {
    public int findKthLargest(int[] arr, int k) {
        PriorityQueue<Integer> pq=new PriorityQueue<>(Collections.reverseOrder());
        for(int i=0;i<arr.length;i++){
            pq.add(arr[i]);
        }
        while(k>1){
            pq.poll();
            k--;
        }
        return pq.peek();
    }
}
```
