# after selling stock cool it down for one day 

# Recurrsion

```
class Solution {
    static int find(int arr[],int indx,int buy){
        if(indx>=arr.length){
            return 0;
        }
        int profit=0;
        if(buy==1){
            int take=find(arr,indx+1,0)-arr[indx];
            int nottake=find(arr,indx+1,1);
            profit=Math.max(take,nottake);
        }
        else{
            int take=find(arr,indx+2,1)+arr[indx];
            int nottake=find(arr,indx+1,0);
            profit=Math.max(take,nottake);
        }
        return profit;
    }
    public int maxProfit(int[] arr) {
        return find(arr,0,1);
    }
}
```
# Memoisation

```
class Solution {
    int find(int arr[],int indx,int buy,int dp[][][],int cool){
        if(indx>=arr.length){
            return 0;
        }
        if(dp[indx][buy][cool]!=-1){
            return dp[indx][buy][cool];
        }
        int profit=0;
        if(buy==1){
            int take=find(arr,indx+1,0,dp,0)-arr[indx];
            int nottake=find(arr,indx+1,1,dp,1);
            profit=Math.max(take,nottake);
        }
        else{
            int take=find(arr,indx+2,1,dp,0)+arr[indx];
            int nottake=find(arr,indx+1,0,dp,1);
            profit=Math.max(take,nottake);
        }
        return dp[indx][buy][cool]=profit;
    }
    public int maxProfit(int[] arr) {
        int dp[][][]=new int[arr.length][2][2];
        for(int [][]a:dp){
            for(int []b:a){
                Arrays.fill(b,-1);
            }
        }
        return find(arr,0,1,dp,1);
    }
}
```

# Tabulation

```
class Solution {

    public int maxProfit(int[] arr) {

        int n = arr.length;

        int[][][] dp = new int[n + 2][2][2];

        for (int indx = n - 1; indx >= 0; indx--) {

            for (int cool = 0; cool <= 1; cool++) {

                // buy == 1
                int take = dp[indx + 1][0][0] - arr[indx];
                int nottake = dp[indx + 1][1][1];

                dp[indx][1][cool] = Math.max(take, nottake);

                // buy == 0
                take = dp[indx + 2][1][0] + arr[indx];
                nottake = dp[indx + 1][0][1];

                dp[indx][0][cool] = Math.max(take, nottake);
            }
        }

        return dp[0][1][1];
    }
}
```
