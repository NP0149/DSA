# Minimum absolute sum only for positive

```
import java.util.*;

public class min_abs_diff {
    public static void main(String args[]){
        int arr[]={3,9,7,3};
        int sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }
        int dp[][]=new int[arr.length][sum+1];
        for(int i=0;i<arr.length;i++){
            dp[i][0]=1;
        }
        if(arr[0]<=sum){
            dp[0][arr[0]]=1;
        }
        for(int i=1;i<arr.length;i++){
            for(int j=1;j<=sum;j++){
                if(arr[i]<=j){
                    dp[i][j]=(dp[i-1][j]==1 || dp[i-1][j-arr[i]]==1)?1:0;
                }
                else{
                    dp[i][j]=dp[i-1][j];
                }
            }
        }
        int min_abs=Integer.MAX_VALUE;
        for(int i=0;i<sum+1;i++){
            if(dp[arr.length-1][i]==1){
                int s=i;
                min_abs=Math.min(min_abs,Math.abs(2*s-sum));
            }
        }
        System.out.println(min_abs);
    }
}
```
