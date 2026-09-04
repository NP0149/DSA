# Rod cutting

[Problem Link](https://www.geeksforgeeks.org/problems/rod-cutting0840/1)

# RECURRSION
```
class Solution {
    int find(int arr[],int n,int indx){
        if(indx==0){
            return n*arr[indx];
        }
        int nottake=find(arr,n,indx-1);
        int take=Integer.MIN_VALUE;
        if(indx+1<=n){
            take=arr[indx]+find(arr,n-(indx+1),indx);
        }
        return Math.max(take,nottake);
    }
    public int cutRod(int[] arr) {
      int n=arr.length;
      return find(arr,n,arr.length-1);
    }
}
```

# Memoisation

```
class Solution {
    int find(int arr[],int target,int indx,int dp[][]){
        if(indx==0){
            return target*arr[indx];
        }
        if(dp[indx][target]!=-1){
            return dp[indx][target];
        }
        int nottake=find(arr,target,indx-1,dp);
        int take=Integer.MIN_VALUE;
        if(indx+1<=target){
            take=arr[indx]+find(arr,target-(indx+1),indx,dp);
        }
        return dp[indx][target]=Math.max(take,nottake);
    }
    public int cutRod(int[] arr) {
      int n=arr.length;
      int dp[][]=new int[arr.length][n+1];
      for(int i=0;i<arr.length;i++){
          Arrays.fill(dp[i],-1);
      }
      return find(arr,n,arr.length-1,dp);
    }
}
```
