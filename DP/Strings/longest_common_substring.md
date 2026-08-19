
# Longest common substring

```
import java.util.*;

public class lcs {
    public static void main(String args[]){
        String s1="abcd";
        String s2="abzd";
        int m=s1.length();
        int n=s2.length();
    int dp[][]=new int[s1.length()+1][s2.length()+1];
    int ans=0;
    for(int i=1;i<=m;i++){
        for(int j=1;j<=n;j++){
            if(s1.charAt(i-1)==s2.charAt(j-1)){
                dp[i][j]=1+dp[i-1][j-1];
                ans=Math.max(ans,dp[i][j]);
            }
            else{
                dp[i][j]=0;
            }
        }
    }
        System.out.println(ans);
    }
}
```
