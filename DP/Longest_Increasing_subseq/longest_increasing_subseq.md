# Longest Increasing subsequence

[Problem Link](https://www.geeksforgeeks.org/problems/longest-increasing-subsequence-1587115620/1)

# Recurrsion

```
class Solution {
    int find(int arr[],int indx,int prev){
        if(indx>=arr.length){
            return 0;
        }
       int nottake=find(arr,indx+1,prev);
       int take=0;
       if(prev==-1 || arr[indx]>arr[prev]){
           take=1+find(arr,indx+1,indx);
       }
       return Math.max(take,nottake);
    }
    public int lis(int arr[]) {
        return find(arr,0,-1);
    }
}
```
# memoisation

```
class Solution {
    int find(int arr[],int indx,int prev,int dp[][]){
        if(indx>=arr.length){
            return 0;
        }
        if(dp[indx][prev+1]!=-1){
            return dp[indx][prev+1];
        }
         int take=0;
       if(prev==-1 || arr[indx]>arr[prev]){
           take=1+find(arr,indx+1,indx,dp);
       }
       int nottake=find(arr,indx+1,prev,dp);
       return dp[indx][prev+1]=Math.max(take,nottake);
    }
    public int lis(int arr[]) {
        int dp[][]=new int[arr.length][arr.length+1];
        for(int []a:dp){
            Arrays.fill(a,-1);
        }
        return find(arr,0,-1,dp);
    }
}
```
# Tabulation

```

```
