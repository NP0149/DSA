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
