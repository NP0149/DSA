
# Target sum
# recurrsion

```
class Solution {
   static int find_rec(int arr[],int indx,int target){
    if(indx==0){
       if(target==arr[0]){
        return 1;
       }
       else{
        return 0;
       }
    }
    if(target==0){
        return 1;
    }
    int nottake=find_rec(arr,indx-1,target);
    int take=0;
    if(arr[indx]<=target){
        take=find_rec(arr,indx-1,target-arr[indx]);
    }
    return take+nottake;
   }
    public int findTargetSumWays(int[] arr, int target) {
        int sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }
        if(Math.abs(target)>sum){
            return 0;
        }
        if((sum+target)%2!=0){
            return 0;
        }
           int need=(sum+target)/2;
        return find_rec(arr,arr.length-1,need);
    }
}
```

# memoisation

```
class Solution {
   static int find_rec(int arr[],int indx,int target,int dp[][]){
    if(indx==0){
        if(target==0 && arr[0]==0){
            return 2;
        }
       if(target==0 || target==arr[0]){
        return 1;
       }
       else{
        return 0;
       }
    }
    if(dp[indx][target]!=-1){
        return dp[indx][target];
    }
    int nottake=find_rec(arr,indx-1,target,dp);
    int take=0;
    if(arr[indx]<=target){
        take=find_rec(arr,indx-1,target-arr[indx],dp);
    }
    return dp[indx][target]=take+nottake;
   }
    public int findTargetSumWays(int[] arr, int target) {
        int sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }
        if(Math.abs(target)>sum){
            return 0;
        }
        if((sum+target)%2!=0){
            return 0;
        }
           int need=(sum+target)/2;
           int dp[][]=new int[arr.length][need+1];
           for(int a[]:dp){
            Arrays.fill(a,-1);
           }
        return find_rec(arr,arr.length-1,need,dp);
    }
}
```

# Tabulation

```
class Solution {
    static int find_tab(int arr[],int target){
        int sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }
        int dp[][]=new int[arr.length][sum+1];
        for(int i=0;i<arr.length;i++){
            dp[i][0]=1;
        }
        if(Math.abs(target)>sum){
            return 0;
        }
        int need=(sum+target)/2;
        if((sum+target)%2!=0){
            return 0;
        }
        if(target>sum){
            return 0;
        }
        if(arr[0]<=need){
            dp[0][arr[0]]+=1;
        }
        for(int i=1;i<arr.length;i++){
            for(int j=0;j<=sum;j++){
                int nottake=dp[i-1][j];
                int take=0;
                if(arr[i]<=j){
                    take=dp[i-1][j-arr[i]];
                }
                 dp[i][j]=take+nottake;
            }
        }
        return dp[arr.length-1][need];
    }
    public int findTargetSumWays(int[] arr, int target) {
        return find_tab(arr,target);
    }
}
```
