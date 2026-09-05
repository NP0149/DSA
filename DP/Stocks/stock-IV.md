# U can buy and sell for k times


```
class Solution {
    static int find(int arr[],int indx,int buy,int cap){
        if(cap==0){
            return 0;
        }
        if(indx==arr.length){
            return 0;
        }
        int profit=0;
        if(buy==1){
            int take=find(arr,indx+1,0,cap)-arr[indx];
            int nottake=find(arr,indx+1,1,cap);
            profit=Math.max(take,nottake);
        }
        else{
        int take=find(arr,indx+1,1,cap-1)+arr[indx];
        int nottake=find(arr,indx+1,0,cap);
        profit=Math.max(take,nottake);
        }
         
        return profit;

    }
    public int maxProfit(int k, int[] arr) {
        return find(arr,0,1,k);
    }
}
```
# Memoisation
```
class Solution {
    int find(int arr[],int indx,int buy,int k,int dp[][][]){
        if(indx>=arr.length){
            return 0;
        }
        if(k==0){
            return 0;
        }
        if(dp[indx][buy][k]!=-1){
            return dp[indx][buy][k];
        }
        int profit=0;
        if(buy==1){
            int take=find(arr,indx+1,0,k,dp)-arr[indx];
            int nottake=find(arr,indx+1,1,k,dp);
             profit=Math.max(take,nottake);
        }
        else{
            int take=find(arr,indx+1,1,k-1,dp)+arr[indx];
            int nottake=find(arr,indx+1,0,k,dp);
           profit=Math.max(take,nottake);
        }
        return dp[indx][buy][k]=profit;
    }
    public int maxProfit(int k, int[] arr) {
        int dp[][][]=new int[arr.length][2][k+1];
        for(int[][]a:dp){
            for(int[]b:a){
                Arrays.fill(b,-1);
            }
        }
        return find(arr,0,1,k,dp);
    }
}

```
