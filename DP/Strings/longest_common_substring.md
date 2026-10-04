
# Longest common substring

```
class Solution {

    int find(String s1, String s2, int i, int j, int count) {

        // Base case
        if (i == s1.length() || j == s2.length()) {
            return count;
        }

        int same = count;

        // If characters match, continue the substring
        if (s1.charAt(i) == s2.charAt(j)) {
            same = find(s1, s2, i + 1, j + 1, count + 1);
        }

        // Start a new substring
        int move1 = find(s1, s2, i + 1, j, 0);
        int move2 = find(s1, s2, i, j + 1, 0);

        return Math.max(same, Math.max(move1, move2));
    }

    public int longestCommonSubstr(String s1, String s2) {
        return find(s1, s2, 0, 0, 0);
    }
}
```



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
