# Minimum rope cost

[Problem Link](https://www.geeksforgeeks.org/problems/minimum-cost-of-ropes-1587115620/1)

```
class Solution {
    public static int minCost(int[] arr) {
   PriorityQueue<Integer> pq=new PriorityQueue<>();
   for(int i=0;i<arr.length;i++){
      pq.add(arr[i]);
   }
   int sum=0;
   while(pq.size()>1){
       int res=pq.poll();
       res+=pq.poll();
       sum+=res;
       pq.add(res);
   }
   return sum;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
