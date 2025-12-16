# Shortest Job

[Problem Link](https://takeuforward.org/plus/dsa/problems/shortest-job-first)


```
class Solution {
    public long solve(int[] arr) {
        //your code goes here
   Arrays.sort(arr);
   int n=arr.length;
   int ans[]=new int[n];
   ans[0]=0;
   for(int i=1;i<arr.length;i++){
    ans[i]=arr[i-1]+ans[i-1];
   }
   int sum=0;
   for(int i=0;i<ans.length;i++){
    sum+=ans[i];
   }
   long s;
   s=sum/n;
   return s;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
