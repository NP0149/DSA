# minimum number of insertions need to do make a string palindrome
  ===length of string-(longest palindrome sequence)


  ```
class Solution {
    static int find_pal(String s1,String s2){
        int dp[][]=new int[s1.length()+1][s2.length()+1];
        int ans=0;
        for(int i=1;i<=s1.length();i++){
            for(int j=1;j<=s2.length();j++){
                if(s1.charAt(i-1)==s2.charAt(j-1)){
                 dp[i][j]=1+dp[i-1][j-1];
                 ans=Math.max(ans,dp[i][j]);
                }
                else{
                    dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        return ans;
    }
    public int minInsertions(String s1) {
        int n=s1.length();
        StringBuilder sb=new StringBuilder(s1).reverse();
        String s2=sb.toString();
        int ans=find_pal(s1,s2);
        return n-ans;
    }
}

```
