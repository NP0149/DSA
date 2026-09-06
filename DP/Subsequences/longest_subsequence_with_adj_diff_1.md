[Problem Link](https://www.geeksforgeeks.org/problems/longest-sub-sequence-such-that-difference-between-adjacents-is-one2558/1)

```
class Solution {
    int lis(int arr[],int indx,int prev){
        if(indx>=arr.length){
            return 0;
        }
        int take=0;
        if(prev==-1 || Math.abs(arr[indx]-arr[prev])==1){
            take=1+lis(arr,indx+1,indx);
        }
        int nottake=lis(arr,indx+1,prev);
        return Math.max(take,nottake);
    }
    public int longestSubseq(int[] arr) {
        // code here
        return lis(arr,0,-1);
    }
}

```

```
class Solution {
    int lis(int arr[],int indx,int prev,int dp[][]){
        if(indx>=arr.length){
            return 0;
        }
        if(dp[indx][prev+1]!=-1){
            return dp[indx][prev+1];
        }
        int take=0;
        if(prev==-1 || Math.abs(arr[indx]-arr[prev])==1){
            take=1+lis(arr,indx+1,indx,dp);
        }
        int nottake=lis(arr,indx+1,prev,dp);
        return dp[indx][prev+1]=Math.max(take,nottake);
    }
    public int longestSubseq(int[] arr) {
        // code here
        int dp[][]=new int[arr.length][arr.length+1];
        for(int []a:dp){
            Arrays.fill(a,-1);
        }
        return lis(arr,0,-1,dp);
    }
}

```
