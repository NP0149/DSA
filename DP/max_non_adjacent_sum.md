# Maximum Non adjacent sum

[Problem Link](https://leetcode.com/problems/house-robber/submissions/1753778914/)

## Usual approach

```
class Solution {
    static int fun(int n,int arr[]){
        if(n<0){
            return 0;
        }
        if(n==0){
            return arr[n];
        }
        int pick=arr[n]+fun(n-2,arr);
        int notpick=0+fun(n-1,arr);
        return Math.max(pick,notpick);
    }
    public int rob(int[] arr) {
        int n=arr.length;
        return fun(n-1,arr);
    }
}
```
## Complexity Anaysis

Time:O(2^n)//exponential time complexity

Space:O(n)//recurrsive stack

## Memoisation

```
class Solution {
    static int fun(int n,int arr[],int dp[]){
        if(n<0){
            return 0;
        }
        if(n==0){
            return arr[n];
        }
        if(dp[n]!=-1){
            return dp[n];
        }
        int pick=arr[n]+fun(n-2,arr,dp);
        int notpick=0+fun(n-1,arr,dp);
        return dp[n]=Math.max(pick,notpick);
    }
    public int rob(int[] arr) {
        int n=arr.length;
        int dp[]=new int[n];
        for(int i=0;i<n;i++){
            dp[i]=-1;
        }
        return fun(n-1,arr,dp);
    }
}
```

## Complexity Anaysis

Time:O(n)

Space:O(n)

## Tabulation

```
class Solution {
    static int fun(int n,int arr[],int dp[]){
        if(n==0){
            return 0;
        }
        if(n==1) return arr[0];
        if(arr.length==2){
            return Math.max(arr[0],arr[1]);
        }
       dp[0]=arr[0];
       dp[1]=Math.max(arr[0],arr[1]);
       int pick=0;
       int notpick=0;
     for(int i=2;i<n;i++){
         notpick=dp[i-1];
       if(i-2>=0){
        pick=arr[i]+dp[i-2];
       }
        dp[i]=Math.max(pick,notpick);
    }
    return dp[n-1];
    }
    public int rob(int[] arr) {
        int n=arr.length;
        int dp[]=new int[n];
        for(int i=0;i<n;i++){
            dp[i]=-1;
        }
        return fun(n,arr,dp);
    }
}
```
## Complexity Analysis

Time:O(n)

Space:O(n)

## Optimal approach

```
class Solution {
    static int fun(int n,int arr[],int dp[]){
        if(n==1) return arr[0];
        if(arr.length==2){
            return Math.max(arr[0],arr[1]);
        }
       int prev2=0;
       int prev1=arr[0];
       int pick=0;
       int notpick=0;
       int curr=0;
     for(int i=1;i<n;i++){
         notpick=prev1;
        pick=arr[i]+prev2;
        curr=Math.max(pick,notpick);
        prev2=prev1;
        prev1=curr;
    }
    return prev1;
    }
    public int rob(int[] arr) {
        int n=arr.length;
        int dp[]=new int[n];
        for(int i=0;i<n;i++){
            dp[i]=-1;
        }
        return fun(n,arr,dp);
    }
}
```

## Complexity Analysis

Time:O(n)

Space:O(1)
