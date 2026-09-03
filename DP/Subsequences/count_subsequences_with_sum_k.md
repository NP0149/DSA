# count subsequences with sum K
 
[Problem Link](https://takeuforward.org/plus/dsa/problems/count-subsets-with-sum-k)

# recurrsion

```
class Solution {
    
   static int find(int arr[],int target,int indx){
        if(indx==0){
            if(target==0 && arr[0]==0){
                return 2;
            }
            if(target==0 || arr[indx]==target){
                return 1;
            }
            return 0;
        }
        int nottake=find(arr,target,indx-1);
        int take=0;
        if(arr[indx]<=target){
            take=find(arr,target-arr[indx],indx-1);
        }
        return take+nottake;
    }
    static int perfectSum(int[] arr, int target) {
        return find(arr,target,arr.length-1);
    }
}
```

# Complexity Analysis

Time:O(2^n)

Space:O(n)

# Memoisation

```
class Solution {
    
   static int find(int arr[],int target,int indx,int dp[][]){
        if(indx==0){
            if(target==0 && arr[0]==0){
                return 2;
            }
            if(target==0 || arr[indx]==target){
                return 1;
            }
            return 0;
        }
        if(dp[indx][target]!=-1){
            return dp[indx][target];
        }
        int nottake=find(arr,target,indx-1,dp);
        int take=0;
        if(arr[indx]<=target){
            take=find(arr,target-arr[indx],indx-1,dp);
        }
        return dp[indx][target]=take+nottake;
    }
    static int perfectSum(int[] arr, int target) {
        int dp[][]=new int[arr.length][target+1];
        for(int i=0;i<arr.length;i++){
        Arrays.fill(dp[i],-1);
        }
        return find(arr,target,arr.length-1,dp);
    }
}
```


# Tabulation

```
class Solution {
    static int perfectSum(int[] arr, int target) {
    int dp[][]=new int[arr.length][target+1];
   if(arr[0]==0){
       dp[0][0]=2;
   }
   else{
       dp[0][0]=1;
       if(arr[0]<=target){
           dp[0][arr[0]]=1;
       }
   }
    for(int i=1;i<arr.length;i++){
        for(int j=0;j<=target;j++){
            int nottake=dp[i-1][j];
            int take=0;
            if(arr[i]<=j){
                take=dp[i-1][j-arr[i]];
            }
            dp[i][j]=take+nottake;
        }
    }
    
    return dp[arr.length-1][target];
    }
}
```
