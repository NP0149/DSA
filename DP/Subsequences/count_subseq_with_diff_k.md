# Count sub sequences with diff is k

```
class Solution {
    int find(int arr[],int diff){
        int total=0;
        for(int i=0;i<arr.length;i++){
            total+=arr[i];
        }
        int target=(diff+total)/2;
        if((diff+total)%2!=0){
            return 0;
        }
        int dp[][]=new int[arr.length][target+1];
        dp[0][0]=1;
       if(arr[0]==0){
           dp[0][0]=2;
       }
        else{
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
    public int countPartitions(int[] arr, int diff) {
     return find(arr,diff);
    }
}


```
