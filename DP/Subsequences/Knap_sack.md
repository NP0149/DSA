#  Knapsack 0 1


## memoisation

```
class Solution {
    
    static int find_rec(int val[],int wt[],int indx,int max_wt,int dp[][]){
        if(indx==0){
            if(wt[0]<=max_wt){
                return val[0];
            }
            return 0;
        }
        if(dp[indx][max_wt]!=-1){
            return dp[indx][max_wt];
        }
        int nottake=find_rec(val,wt,indx-1,max_wt,dp);
        int take=Integer.MIN_VALUE;
        if(wt[indx]<=max_wt){
            take=val[indx]+find_rec(val,wt,indx-1,max_wt-wt[indx],dp);
        }
        return dp[indx][max]=Math.max(nottake,take);
    }
    public int knapsack(int max_wt, int val[], int wt[]) {
        // code here
        int indx=val.length-1;
        int dp[][]=new int[val.length][max_wt+1];
        for(int arr[]:dp){
            Arrays.fill(arr,-1);
        }
        return find_rec(val,wt,indx,max_wt,dp);
    }
}
```
## tabulation


```
   static int find_tab(int val[],int wt[],int max_wt){
        int dp[][]=new int[val.length][max_wt+1];
       for(int i=wt[0];i<=max_wt;i++){
           dp[0][i]=val[0];
       }
        // if(wt[0]<=max_wt){
        //     dp[0][wt[0]]=val[0];
        // }
        for(int i=1;i<val.length;i++){
            for(int j=0;j<=max_wt;j++){
             int nottake=dp[i-1][j];
             int take=Integer.MIN_VALUE;
             if(wt[i]<=j){
                 take=val[i]+dp[i-1][j-wt[i]];
             }
             dp[i][j]=Math.max(take,nottake);
            }
            
        }
        return dp[val.length-1][max_wt];
    }
```


# optimal same as tabulation

```
 static int find_opt(int val[],int wt[],int max_wt){
         int prev[]=new int[max_wt+1];
        for(int i=wt[0];i<=max_wt;i++){
            prev[i]=val[0];
        }
         for(int i=1;i<val.length;i++){
             int curr[]=new int[max_wt+1];
             for(int j=0;j<=max_wt;j++){
                 int nottake=prev[j];
                 int take=Integer.MIN_VALUE;
                 if(wt[i]<=j){
                     take=val[i]+prev[j-wt[i]];
                 }
                 curr[j]=Math.max(take,nottake);
             }
             prev=curr;
         }
         return prev[max_wt];
     }
```
