[Problem Link](https://leetcode.com/problems/distinct-subsequences/description/)

# primary case generate all subseqneces of first string match with second
```
class Solution {
    int find_all_subseq(String s,String t,int indx,StringBuilder sb){
      if(indx>=s.length()){
        if(sb.toString().equals(t)){
            return 1;
        }
        return 0;
      }
      sb.append(s.charAt(indx));
      int naavya=find_all_subseq(s,t,indx+1,sb);
      sb.deleteCharAt(sb.length()-1);
      int navya=find_all_subseq(s,t,indx+1,sb);
      return naavya+navya;
    }
    public int numDistinct(String s, String t) {
        StringBuilder sb=new StringBuilder();
        return find_all_subseq(s,t,0,sb);
    }
}
```
# Recurrsion

```
class Solution {
    int find(String s,String t,int indx1,int indx2){
         if(indx2<0){
            return 1;
        }
        if(indx1<0){
            return 0;
        }
        
        if(s.charAt(indx1)==t.charAt(indx2)){
           return find(s,t,indx1-1,indx2-1)+find(s,t,indx1-1,indx2);
        }
        else{
            return find(s,t,indx1-1,indx2);
        }
    }
    public int numDistinct(String s, String t) {
        return find(s,t,s.length()-1,t.length()-1);
    }
}
```

# Memoisation

```
class Solution {
    int find(String s,String t,int indx1,int indx2,int dp[][]){
         if(indx2<0){
            return 1;
        }
        if(indx1<0){
            return 0;
        }
        if(dp[indx1][indx2]!=-1){
            return dp[indx1][indx2];
        }
        if(s.charAt(indx1)==t.charAt(indx2)){
           return dp[indx1][indx2]=find(s,t,indx1-1,indx2-1,dp)+find(s,t,indx1-1,indx2,dp);
        }
        else{
            return dp[indx1][indx2]=find(s,t,indx1-1,indx2,dp);
        }
    }
    public int numDistinct(String s, String t) {
        int dp[][]=new int[s.length()][t.length()];
        for(int i=0;i<s.length();i++){
            Arrays.fill(dp[i],-1);
        }
        return find(s,t,s.length()-1,t.length()-1,dp);
    }
}
```


