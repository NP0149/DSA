[Problem Link](https://www.geeksforgeeks.org/problems/knapsack-with-duplicate-items4201/1)

```
class Solution {
    
    int find(int val[],int wt[],int target,int indx){
        if(indx>=val.length){
            return 0;
        }
        int nottake=find(val,wt,target,indx+1);
        int take=0;
        if(wt[indx]<=target){
            take=val[indx]+find(val,wt,target-wt[indx],indx);
        }
        return Math.max(take,nottake);
    }
    public int knapSack(int val[], int wt[], int capacity) {
        // code here
        return find(val,wt,capacity,0);
    }
}
```

```
class Solution {
    public int knapSack(int val[], int wt[], int target) {
        int dp[][]=new int[wt.length][target+1];
        for(int i=0;i<wt.length;i++){
            dp[i][0]=0;
        }
    for(int j=1;j<=target;j++){
            dp[0][j]=(j/wt[0])*val[0];
    }
        for(int i=1;i<wt.length;i++){
            for(int j=1;j<=target;j++){
                int nottake=dp[i-1][j];
                int take=0;
                if(wt[i]<=j){
                    take=val[i]+dp[i][j-wt[i]];
                }
                dp[i][j]=Math.max(take,nottake);
            }
        }
        return dp[wt.length-1][target];
    }
}
```
