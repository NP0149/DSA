# House Robber-II

[Problem Link](https://leetcode.com/problems/house-robber-ii/)


## Approach-I

same as house robber I just we need to run the function twice with last and without first and with first and without last
elements at the same time,as they are adjacent

```
class Solution {
    static int find(int n,int arr[]){
        if(n==0){
            return 0;
        }
        if(n==1){
            return arr[0];
        }
        if(n==2){
            return Math.max(arr[0],arr[1]);
        }
        int prev1=arr[0];
        int prev2=0;
        int curr=0;
        int pick=0;
        int notpick=0;
        for(int i=1;i<n;i++){
            pick=arr[i]+prev2;
            notpick=prev1;
            curr=Math.max(pick,notpick);
            prev2=prev1;
            prev1=curr;
        }
        return prev1;
    }
    public int rob(int[] arr) {
        int n=arr.length;
        int arr1[]=new int[n];
        int arr2[]=new int[n];
        int idx=0;
        int t=0;
        for(int i=0;i<n;i++){
      if(i!=0){
        arr1[idx++]=arr[i];
      }
      if(i!=n-1){
        arr2[t++]=arr[i];
      }
        }
        if(n==1){
            return arr[0];
        }
        return Math.max(find(n,arr1),find(n,arr2));
    }
}
```

## Complexity Analysis

Time:O(n)

Space:O(n)

