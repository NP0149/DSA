[Problem Link](https://leetcode.com/problems/edit-distance/description/)


```
class Solution {
    static int find(String s1,String s2,int i,int j,int dp[][]){
      if(i==s1.length()){
        return s2.length()-j;
      }
      if(j==s2.length()){
        return s1.length()-i;
      }
      if(dp[i][j]!=-1){
        return dp[i][j];
      }
        if(i<0) return j+1;
        if(j<0) return i+1;

        if(s1.charAt(i)==s2.charAt(j)){
            return find(s1,s2,i+1,j+1,dp);
        }
        int insert=find(s1,s2,i,j+1,dp);
        int replace=find(s1,s2,i+1,j+1,dp);
        int delete=find(s1,s2,i+1,j,dp);
        return dp[i][j]=1+Math.min(insert,Math.min(replace,delete));
    }
    public int minDistance(String s1, String s2) {
        int dp[][]=new int[s1.length()+1][s2.length()+1];
        for(int i=0;i<=s2.length();i++){
            dp[s1.length()][i]=s2.length()-i;
        }
        for(int i=0;i<=s2.length();i++){
            dp[i][s2.length()]=s1.length()-i;
        }
         for(int i=s1.length();i>=0;i--){
          for(int j=s2.length();j>=0;j--){
            if(s1.charAt(i-1)==s2.charAt(j-1)){
                dp[i][j]=dp[i-1][j-1];
            }
            else{
                int del=dp[i-1][j];
                int rep=dp[i-1][j-1];
                int insert=dp[i][j-1];
                dp[i][j]=Math.min(del,Math.min(rep,insert));
            }
          }
         }
         return dp[0][0];
    }
}
```
