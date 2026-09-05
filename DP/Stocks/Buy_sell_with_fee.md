# Buy and sell with fee

# Recussion 

```
class Solution {
    static int find(int arr[],int indx,int buy,int fee){
        if(indx==arr.length){
            return 0;
        }
        int profit=0;
        if(buy==1){
            int take=find(arr,indx+1,0,fee)-arr[indx];
            int nottake=find(arr,indx+1,1,fee);
            profit=Math.max(take,nottake);
        }
        else{
            int take=find(arr,indx+1,1,fee)+arr[indx]-fee;
            int nottake=find(arr,indx+1,0,fee);
            profit=Math.max(take,nottake);
        }
        return profit;
    }
    public int maxProfit(int[] arr, int fee) {
        return find(arr,0,1,fee);
    }
}
```
# memoisation

```
class Solution {
    int find(int arr[],int indx,int buy,int fee,int dp[][]){
        if(indx>=arr.length){
            return 0;
        }
        if(dp[indx][buy]!=-1){
            return dp[indx][buy];
        }
        int profit=0;
        if(buy==1){
            int take=find(arr,indx+1,0,fee,dp)-arr[indx];
            int nottake=find(arr,indx+1,1,fee,dp);
            profit=Math.max(take,nottake);
        }
        else{
            int take=find(arr,indx+1,1,fee,dp)+arr[indx]-fee;
            int nottake=find(arr,indx+1,0,fee,dp);
           profit=Math.max(take,nottake);
        }
        return dp[indx][buy]=profit;
    }
    public int maxProfit(int[] arr, int fee) {
        int dp[][]=new int[arr.length][2];
        for(int[]d:dp){
            Arrays.fill(d,-1);
        }
        return find(arr,0,1,fee,dp);
    }
}
```
