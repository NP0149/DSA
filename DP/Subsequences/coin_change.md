# Coin change problem


# Using recurrsion

```
class Solution {
    static int find_rec(int arr[],int indx,int target){
        if(indx==0){
            if(target%arr[indx]==0){
                return target/arr[indx];
            }
            else{
                return (int)1e9;
            }
        }
        int nottake=find_rec(arr,indx-1,target);
        int take=Integer.MAX_VALUE;
        if(arr[indx]<=target){
            take=1+find_rec(arr,indx,target-arr[indx]);
        }
        return Math.min(take,nottake);
    }
    public int coinChange(int[] arr, int target) {
       int ans=find_rec(arr,arr.length-1,target);
       if(ans>=(int)1e9){
          return -1;
       }
       return ans;
    }
}
```
# Using memoisation

```
class Solution {
    static int find_mem(int arr[],int indx,int target,int dp[][]){
        if(indx==0){
            if(target%arr[indx]==0){
                return target/arr[indx];
            }
            else{
                return (int)1e9;
            }
        }
        if(dp[indx][target]!=-1){
         return dp[indx][target];
        }
        int nottake=find_mem(arr,indx-1,target,dp);
        int take=Integer.MAX_VALUE;
        if(arr[indx]<=target){
            take=1+find_mem(arr,indx,target-arr[indx],dp);
        }
        return Math.min(take,nottake);
    }
    public int coinChange(int[] arr, int target) {
        int dp[][]=new int[arr.length][target+1];
        for(int a[]:dp){
            Arrays.fill(a,-1);
        }
       int ans=find_mem(arr,arr.length-1,target,dp);
       if(ans>=(int)1e9){
          return -1;
       }
       return ans;
    }
}
```

# Using Tabulation

```
class Solution {
    public int coinChange(int[] arr, int target) {
        int dp[][]=new int[arr.length][target+1];
        for(int i=0;i<=target;i++){
          if(i%arr[0]==0){
            dp[0][i]=i/arr[0];
          }
          else{
        dp[0][i]=(int)1e9;
          }
        }
        for(int i=1;i<arr.length;i++){
            for(int j=0;j<=target;j++){
                int nottake=dp[i-1][j];
                int take=Integer.MAX_VALUE;
                if(arr[i]<=j){
                    take=1+dp[i][j-arr[i]];
                }
                dp[i][j]=Math.min(nottake,take);
            }
        }
        if(dp[arr.length-1][target]>=(int)1e9){
            return -1;
        }
        return dp[arr.length-1][target];
    }
}
```
