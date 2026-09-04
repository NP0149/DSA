[Problem Link](https://leetcode.com/problems/distinct-subsequences/description/)


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
