# Longest palindromic subsequence

# recurrsion

```
class Solution {
    static int find_rec(String s1,String s2,int indx1,int indx2){
        if(indx1<0 || indx2<0){
            return 0;
        }
        if(s1.charAt(indx1)==s2.charAt(indx2)){
            return 1+find_rec(s1,s2,indx1-1,indx2-1);
        }
        return Math.max(find_rec(s1,s2,indx1-1,indx2),find_rec(s1,s2,indx1,indx2-1));
    }
    public int longestPalindromeSubseq(String s1) {
      StringBuilder sb=new StringBuilder(s1).reverse();
      String s2=sb.toString();
      return find_rec(s1,s2,s1.length()-1,s2.length()-1);
    }
}
```

# memosation

```

class Solution {
    static int find_rec(String s1,String s2,int indx1,int indx2,int dp[][]){
        if(indx1==0 || indx2==0){
            return 0;
        }
        if(dp[indx1][indx2]!=-1){
          return dp[indx1][indx2];
        }
        if(s1.charAt(indx1-1)==s2.charAt(indx2-1)){
            return dp[indx1][indx2]=1+find_rec(s1,s2,indx1-1,indx2-1,dp);
        }
        return dp[indx1][indx2]=Math.max(find_rec(s1,s2,indx1-1,indx2,dp),find_rec(s1,s2,indx1,indx2-1,dp));
    }
    public int longestPalindromeSubseq(String s1) {
      StringBuilder sb=new StringBuilder(s1).reverse();
      String s2=sb.toString();
      int dp[][]=new int[s1.length()+1][s2.length()+1];
      for(int arr[]:dp){
        Arrays.fill(arr,-1);
      }
      return find_rec(s1,s2,s1.length(),s2.length(),dp);
    }
}
```

# Tabulation

```
class Solution {
    public int longestPalindromeSubseq(String s1) {
        StringBuilder sb=new StringBuilder(s1).reverse();
        String s2=sb.toString();
        int dp[][]=new int[s1.length()+1][s2.length()+1];
        for(int i=1;i<=s1.length();i++){
            for(int j=1;j<=s2.length();j++){
                if(s1.charAt(i-1)==s2.charAt(j-1)){
                    dp[i][j]=1+dp[i-1][j-1];
                }
                else{
                    dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        return dp[s1.length()][s2.length()];
    }
}
```
# Tabulation without index shifting

```
class Solution {
    public int longestPalindromeSubseq(String s) {
      StringBuilder sb=new StringBuilder(s).reverse();
      String rev=sb.toString();
      int dp[][]=new int[s.length()][rev.length()];
      if(s.charAt(0)==rev.charAt(0)){
        dp[0][0]=1;
      }
      for(int i=1;i<s.length();i++){
        char ch=rev.charAt(0);
       if(s.charAt(i)==ch){
        dp[i][0]=1;
       }
       else{
        dp[i][0]=dp[i-1][0];
       }
      }
      for(int i=1;i<rev.length();i++){
        char ch=s.charAt(0);
        if(rev.charAt(i)==ch){
            dp[0][i]=1+dp[0][i-1];
        }
        else{
            dp[0][i]=dp[0][i-1];
        }
      }
      for(int i=1;i<s.length();i++){
        for(int j=1;j<rev.length();j++){
            if(s.charAt(i)==rev.charAt(j)){
                dp[i][j]=1+dp[i-1][j-1];
            }
            else{
                dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1]);
            }
        }
      }
      return dp[s.length()-1][rev.length()-1];
    }
}
```

# Optimised

```
class Solution {
    public int longestPalindromeSubseq(String s1) {
        StringBuilder sb=new StringBuilder(s1).reverse();
        String s2=sb.toString();
        int prev[]=new int[s2.length()+1];
        for(int i=1;i<=s1.length();i++){
            int curr[]=new int[s2.length()+1];
            for(int j=1;j<=s2.length();j++){
                if(s1.charAt(i-1)==s2.charAt(j-1)){
                    curr[j]=1+prev[j-1];
                }
                else{
                    curr[j]=Math.max(prev[j],curr[j-1]);
                }
            }
            prev=curr;
        }
        return prev[s2.length()];
    }
}
```
