# Count sub sequences with diff is k

```
class Solution {
    
    static int find(int arr[],int k){
        int sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }
           int need=(sum-k)/2;
        int dp[][]=new int[arr.length][sum+1];
        for(int i=0;i<arr.length;i++){
            dp[i][0]=1;
        }
        if (k > sum) {
            return 0;
        }
        if ((sum - k) % 2 != 0) {
            return 0;
        }
        dp[0][0]=1;
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
                dp[i][j]=nottake+take;
            }
        }
        return dp[arr.length-1][need];
    }
    public int countPartitions(int[] arr, int diff) {
        // code here
        return find(arr,diff);
    }
}

```
